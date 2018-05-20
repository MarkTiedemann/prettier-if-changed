# prettier-if-modified

**Run `prettier` only on modified files.**

## Usage

```sh
# Before
prettier --write "**/*.js"

# After
prettier-if-modified "**/*.js" -- prettier --write

# After (with .prettierignore)
prettier-if-modified "**/*.js" --ignore .prettierignore -- prettier --write
```

## Algorithm

```js
// DANGEROUSLY_SIMPLIFIED_PSEUDO_CODE

var allFiles = find("**/*.js");

var modifiedFiles = allFiles.filter(file => {
  lastModified = getAttribute(file, "last-modified");
  lastFormatted = getAttribute(file, "last-formatted");
  return lastModified > lastFormatted;
});

prettier(modifiedFiles);

var lastFormatted = Date.now();
modifiedFiles.forEach(file => {
  setAttribute(file, "last-formatted", lastFormatted);
});
```

## Development

```sh
# Install dependencies
yarn install

# Format source code
yarn format
```

## License

MIT © [Mark Tiedemann](https://marksweb.site)
