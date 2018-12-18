# VS Code Goodies

VS Code is a pretty awesome editor. It can save you a $4!t-ton of time.

## Extensions

If you look on the left-menu, there is a square looking icon that gives you a list of extensions that you can search for an enable. See the [VS Code docs](https://code.visualstudio.com/docs/editor/extension-gallery) for more info.

Some of those that I have used (and I'm finding more every day):

- **markdownlint**: tells you when your Markdown syntax is incorrect.
- **Nunjucks Templates**: gives you syntax highlighting for Nunjucks pages. Needs a little configuration to work with our First Graphics App pages. See Preferences below.
- **Excel Viewer**: is something to help preview csv files. Not essential, but helpful when working with data.

## Preferences

The way preferences worked changed in the middle of the semester. There is a user interface to change some settings, but in the end it just edits a JSON file. I have a set of useful settings that you can add to your own preferences by following these steps.

- Go to the Code > Preferences > Settings.
- At the top right of the code editor are a series of icons, including `{}`. If you click on the `{}` it will open the JSON verson of the settings.
- In the new pane that opens on the right, make sure you are on the "User settings".
- In the pane on the left, you can search through the different settings that are possible to change. You essentially copy the code and add it to your settings on the right. HOWEVER, you might instead copy all the settings I have below and paste them into the pane on the right.

The user settings I used to set up:

```javascript

{
    "editor.fontSize": 16,
    "terminal.integrated.fontSize": 14,
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
    "editor.minimap.enabled": false,
    "files.associations": {
        "*.html": "html"
    },
    "emmet.includeLanguages": {
        "njk": "html",
        "nunjucks": "html"
    },
}
```

If you look through the JSON, you might be able to figure out what some of these do. This isn't a full description of them, but ...

- I set default size of text in the editor. I'm old, so I make it bigger so it's easier to read.
- I set make the text in the terminal window bigger. Still old.
- I set the editor to show spaces that aren't between words. This makes intending code easier to see.
- I set the tab character to insert two spaces. This is a common coding default.
- I remove the minimap thing that shows by default at the right side of an open file. I find it more of a hassle than useful.

There are more. They will be helpful.
