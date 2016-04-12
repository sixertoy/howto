# Markdown Documentation

## Install

```bash
npm install -g install gh-markdown-cli generate-github-markdown-css
```

## Command line

```bash
mdown --input "./src/docs/**/*.md" --output ./build/docs --header "./src/docs/assets/header.html" --footer "./src/docs/assets/footer.html"
github-markdown-css > ./build/docs/github-markdown.css
```

## Files

- [docs/assets/header.html](./../files/docs_assets_header.html)
- [docs/assets/footer.html](./../files/docs_assets_footer.html)

## Modules

- [gh-markdown-cli](https://github.com/millermedeiros/gh-markdown-cli)
- [generate-github-markdown-css](https://github.com/sindresorhus/generate-github-markdown-css)
