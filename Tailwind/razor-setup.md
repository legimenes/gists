# Tailwind setup in Razor Pages

## Without npm

At the project root, create following folders structure:

```
Tools/tailwind/scripts
```

Inside the directory *Tools/tailwind*, create the Tailwind configuration file *tailwind.config.js* with following initial content:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
	content: [
		"./Pages/*.cshtml",
		"./Pages/**/*.cshtml",
	],
	darkMode: false,
	theme: {
		extend: {},
	},
	plugins: [],
}
```

And also, create the CSS directives file *input.css* with following initial content:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### Tailwind CLI

The Tailwind installation in the Razor Pages project will be done using its CLI through automated scripts. These scripts must be created inside the *Tools/tailwind/scripts* directory.

The script to download the Tailwind will be the *bootstrap.sh* (for Unix and Mac) or *bootstrap.ps1* (for Windows) with the following content:

**bootstrap.sh**
```sh
#! /usr/bin/env bash

set -e # Exit on error

OS=""
case "$(uname -s)" in
	"Linux")  OS="linux";;
	"Darwin") OS="macos";;
esac

ARCH=""
case "$(uname -m)" in
	"x86_64")  ARCH="x64";;
	"amd64")   ARCH="x64";;
	"arm64")   ARCH="arm64";;
	"aarch64") ARCH="arm64";;
	"armv7l")  ARCH="armv7";;
esac

PACKAGE="tailwindcss-${OS}-${ARCH}"
OUTPUT="Tools/tailwind/bin/${PACKAGE}"
DOWNLOAD_URL="https://github.com/tailwindlabs/tailwindcss/releases/latest/download/${PACKAGE}"

if [ ! -e "$OUTPUT" ]; then
	echo "Bootstraping Tailwindcss"

	mkdir -p "$(dirname ${OUTPUT})"
	curl -sL -o "${OUTPUT}" "${DOWNLOAD_URL}"
	chmod +x "${OUTPUT}"
fi

```

**bootstrap.ps1**
```ps1
# Exit on error
$ErrorActionPreference = "Stop"

$OS = "windows"

# Detect CPU architecture
$Architecture = switch ($env:PROCESSOR_ARCHITECTURE) {
    "AMD64" { "x64" }
    "ARM64" { "arm64" }
    Default { "x86" }
}

$Package = "tailwindcss-${OS}-${Architecture}.exe"
$Output = "Tools\tailwind\bin\$Package"
$DownloadUrl = "https://github.com/tailwindlabs/tailwindcss/releases/latest/download/$Package"

if (-not (Test-Path $Output)) {
    Write-Output "Bootstraping Tailwindcss"

    $null = New-Item -ItemType Directory -Force (Split-Path $Output)
    Invoke-WebRequest -Uri $DownloadUrl -OutFile $Output
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
    Unblock-File $Output
}
```

The script to run and build the CLI will be the *run.sh* (for Unix and Mac) or *run.ps1* (for Windows) with the following content:

**run.sh**
```sh
#! /usr/bin/env bash

set -e # Exit on error

OS=""
case "$(uname -s)" in
    "Linux")  OS="linux";;
    "Darwin") OS="macos";;
esac

ARCH=""
case "$(uname -m)" in
    "x86_64")  ARCH="x64";;
    "amd64")   ARCH="x64";;
    "arm64")   ARCH="arm64";;
    "aarch64") ARCH="arm64";;
    "armv7l")  ARCH="armv7";;
esac

PACKAGE="tailwindcss-${OS}-${ARCH}"
BIN="Tools/tailwind/bin/${PACKAGE}"

CONFIG="Tools/tailwind/tailwind.config.js"
INPUT="AssetsTools/tailwind/input.css"
OUTPUT="wwwroot/lib/tailwind/tailwind.min.css"

echo "Running Tailwindcss build"

# Tailwindcli
$BIN -i "${INPUT}" -o "${OUTPUT}" -c "${CONFIG}" -m
```

**run.ps1**
```ps1
# Exit on error
$ErrorActionPreference = "Stop"

$OS = "windows"

# Detect CPU architecture
$Architecture = switch ($env:PROCESSOR_ARCHITECTURE) {
    "AMD64" { "x64" }
    "ARM64" { "arm64" }
    Default { "x86" }
}

$Package = "tailwindcss-${OS}-${Architecture}.exe"
$Bin = "Tools\tailwind\bin\$Package"

$Config = "Tools\tailwind\tailwind.config.js"
$Input = "Tools\tailwind\input.css"
$Output = "wwwroot\lib\tailwind\tailwind.min.css"

Write-Output "Running Tailwindcss build"

# Tailwind CLI
& $Bin -i $Input -o $Output -c $Config -m
```

### Run the scripts manually

Inside the project root folder run:

```bash

```

### Automation in project build

Optionally, to automate the project build process, add the targets below to the .csproj:

```csproj
<Target Name="TailwindRestore" BeforeTargets="Restore">
	<Exec Command="bash Tools/tailwind/scripts/bootstrap.sh" Condition=" '$(OS)' == 'Unix'" />
	<Exec Command="powershell -File Tools/tailwind/scripts/bootstrap.ps1" Condition=" '$(OS)' == 'Windows_NT'" />
</Target>
<Target Name="TailwindRun" BeforeTargets="Build">
	<Exec Command="bash ./Tools/tailwind/scripts/run.sh" Condition=" '$(OS)' == 'Unix'" />
	<Exec Command="powershell -File ./Tools/tailwind/scripts/run.ps1" Condition=" '$(OS)' == 'Windows_NT'" />
</Target>
```

To restore the project, in the root project run the following command:

```bash
dotnet restore
```

### Adding css to the header

The *tailwind.min.css* css file will be created in the *wwwroot/lib/tailwind* directory. It is necessary to add the reference to this css in the html header: 

```html
<link rel="stylesheet" href="~/lib/tailwind/tailwind.min.css" />
```

### Troubleshoot

On Windows, a script execution permission issue may occur when executing scripts:

```bash
File C:\<directory>\lfin\src\WebApp\Assets\scripts\tailwind\run.ps1 cannot be loaded because the execution of scripts is disabled on this system. Please see "get-help about_signing" for more details.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170 or https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4.
```

If this occurs, it will be necessary to adjust the script execution policy for the user:

```bash
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser
```

Most likely, the default policy was previously *Undefined*. To check the current permissions policy, simply run the folowing command:

```bash
Get-ExecutionPolicy -List
```
