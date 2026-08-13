# love letter syntax highlighter

basic syntax highlighter for the [love letter engine](https://github.com/solflo/loveletter) language. it has one color for comments, one for image / audio commands and one for dialogue tags. and that's it. expects `.txt` and `.letter` files. the engine itself only takes in `script.txt`, and i don't think i'll change that, but i have my reasons to create a "fake" filetype extension ok.

## installation

### .vsix 

- open the extension menu (`ctrl + shift + x`)
- open the meatball menu and pick "install from .vsix"

### from source

- download this repo or the latest release (source)
- open the vscode command palette (`ctrl + shift + p`)
- type in "Developer: Install Extension from Location"
- select the folder and it should work :)

## color customization

`syntaxes/loveletter.tmLanguage.json` lists the scopes (you can also use the command palette > "developer: inspect editor tokens and scopes" for this), which you can change the colors of in your `settings.json`. know that if it doesn't work with the _user_ settings, you'll need to change these in the _workspace_ settings, because visual studio sucks ASS. just search `@id:editor.tokenColorCustomizations` on the settings search bar and look at both.

you'll add these under `editor.tokenColorCustomizations`, and then `textMateRules`, prefaced by `source.txt.loveletter keyword`:

- `comment` is self-explanatory
- `keyword` are the dialogue tags
- `keyword.control` covers image and audio commands

this is what my settings look like (well, without the renpy chaff the extension put in there) (yes it's hideous) (not the colors, those i like):

```json
"editor.tokenColorCustomizations": {
    "textMateRules": [
        {
            "scope": "source.txt.loveletter keyword",
            "settings": { "foreground": "#f1bfcc" }
        },
        {
            "scope": "source.txt.loveletter keyword.control",
            "settings": { "foreground": "#965e6b" }
        }
    ]
}
```
