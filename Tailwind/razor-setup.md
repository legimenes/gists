# Tailwind setup in Razor Pages

1) In the root directory of the web project, run:

```
npm init -y
```

2) Install Tailwind CSS:

```
npm install -D tailwindcss @tailwindcss/cli
```

When Tailwind CLI builds the CSS, it internally uses *postcss* to process the Tailwind directives and *autoprefixer* to including vendor prefixing. So there is no need to explicitly install or configure *postcss* or *autoprefixing* for basic usage.

3) In the folder wwwroot/css create app.css file with this content:

```
@import "tailwindcss";
```

4) In the package.json add:
```
"scripts": {
  "css:build": "npx @tailwindcss/cli -i ./wwwroot/css/app.css -o ./wwwroot/css/site.css --minify"
}
```

5) In the .csproj add item groups file for building the css before deploying:
```
<ItemGroup>
  <UpToDateCheckBuilt Include="wwwroot/css/app.css" Set="Css" />
</ItemGroup>

<Target Name="Tailwind" BeforeTargets="Build">
  <Exec Command="npm run css:build"/>
</Target>
```
