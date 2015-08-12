# ...generate Markdown Documentation

## Modules

- [gh-markdown-cli](https://github.com/millermedeiros/gh-markdown-cli)
- [generate-github-markdown-css](https://github.com/sindresorhus/generate-github-markdown-css)

## Command line

```bash
npm install -g install gh-markdown-cli generate-github-markdown-css
mdown --input "./src/docs/**/*.md" --output ./build/docs --header "./src/docs/assets/header.html" --footer "./src/docs/assets/footer.html"
github-markdown-css > ./build/docs/github-markdown.css
```

## Files

- [assets/header.html]()
- [assets/footer.html]()
