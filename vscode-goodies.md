# VS Code Goodies

VS Code is a pretty awesome editor. It can save you a $4!t-ton of time.

## Extensions

If you look on the left-menu, there is a square looking icon that gives you a list of extentions that you can search for an enable.

Some of those that I have used (and I'm finding more every day):

- **HTML Boilerplate**: Gives you a base HTML5 document. Note it won't work unless the file is already created and saved with an `.html` extension.
- **markdownlint**: tells you when your Markdown syntax is incorrect.
- **Nunjucks**: gives you syntax highlighting for Nunjucks pages. Needs a little configuration to work with our First Graphics App pages. See Preferences below.

## Preferences

Go to the Code > Preferenes > Settings and you'll get two windows. On the left are all the default settings. You can search for different settings, and then copy them into the JavaScript array on the right and then override them.

The user settings I have right now:

```javascript
{
    "editor.fontSize": 18,
    "terminal.integrated.fontSize": 16,
    "editor.renderWhitespace": "boundary",
    "editor.tabSize": 2,
    "[md]": {
        "editor.insertSpaces": true,
        "editor.tabSize": 2,
    },
    "editor.renderControlCharacters": true,
    "highlight-matching-tag.style": {
        "backgroundColor": "rgba(63, 191, 63, 0.20)"
    },
    "editor.wordWrap": "on",
    "window.zoomLevel": 0,
    "emmet.includeLanguages": {
        "nunjucks": "html"
    },
    "editor.minimap.enabled": false,
}
```