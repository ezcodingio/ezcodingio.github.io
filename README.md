# ezcoding.io

Company website for EasyCoding, built with [Hugo](https://gohugo.io/).

## Development

```sh
hugo server          # live-reload dev server at http://localhost:1313
hugo --gc --minify   # production build into ./public
```

Site copy lives in `data/*.yaml` (services, client engagements) and `hugo.toml` (`[params]`).
Layouts are hand-rolled (no theme) in `layouts/`, styling in `assets/css/main.css`.
