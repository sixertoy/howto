# Howto Node

> Some howtos

## How to generate Markdown Documentation

##### Command line

```bash
npm install -g install gh-markdown-cli generate-github-markdown-css
mdown --input "./src/docs/**/*.md" --output ./build/docs --header "./src/docs/assets/header.html" --footer "./src/docs/assets/footer.html"
github-markdown-css > ./build/docs/github-markdown.css
```

##### Links

- [gh-markdown-cli](https://github.com/millermedeiros/gh-markdown-cli)
- [generate-github-markdown-css](https://github.com/sindresorhus/generate-github-markdown-css)
