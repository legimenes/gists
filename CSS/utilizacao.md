## Utilização de CSS nas páginas

### Importando de referência externa (external css)

```
<head>
  <link rel="stylesheet" type="text/css" href="assets/css/stylesheets.css" />
</head>
```

### Definindo dentro da própria página (internal css)

```
<head>
  <style>
    body {
      background-color: #ffcccc
    }
    h1 {
      color: #000000;
      margin-left: 40px
    } 
  </style>
</head>
```

### Definindo dentro da própria tag (inline css)

```
<h1 style="color:#00ffcc;margin-left:30px">Título da página</h1>
```
