# VS Code Goodies

VS Code is a pretty awesome editor. It can save you a $4!t-ton of time.

## Extensions

If you look on the left-menu, there is a square looking icon that gives you a list of extentions that you can search for an enable.

Some of those that I have used (and I'm finding more every day):

- **HTML Boilerplate**: Gives you a base HTML5 document. Note it won't work unless the file is already created and saved with an `.html` extension.
- **markdownlint**: tells you when your Markdown syntax is incorrect.
- **Nunjucks**: gives you syntax highlighting for Nunjucks pages. Needs a little configuration to work with our First Graphics App pages. See Preferences below.

## Preferences

The way preferences worked changed in the middle of the semester. The list below can be a guide to find and change settings, but the JSON object itself is useless now.

- Go to the Code > Preferences > Settings.
- On the space with the sames "User settings" and "Workspace settings", there is a triple dot `...` to the right. Click on that and choose `open settings.json`.
- You'll get two windows. On the left are all the default settings. You can search for different settings, and then copy them into the JavaScript array on the right and then override them.

The user settings I used to set up:

```javascript
{
    "editor.fontSize": 16,
    "terminal.integrated.fontSize": 14,
    "editor.renderWhitespace": "boundary",
    "cSpell.userWords": [
        "repo"
    ],
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
        "nunjucks": "html",
        "njk": "html"
    },
    "editor.minimap.enabled": false,
}
```