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

`syntaxes/loveletter.tmLanguage.json` lists the scopes (you can also use the command palette > "developer: inspect editor tokens and scopes" for this), which you can change the colors of in your `settings.json`. vsc is super annoying and can only use textmate rules in one place at a time, so check if you don't have anything in the _workspace_ settings.json [^1]. if you do, you might wanna copy them over to the _user_ settings so things are neater. just search `@id:editor.tokenColorCustomizations` on the settings search bar and look at both.

[^1]: the renpy extension put a bunch of settings over there for some reason.

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

if you're curious my comments are `#887876`, but those i applied globally, which you can do by putting `"comments": "#887876",` before `"textMateRules"`. notice that the names are different. i hope this helps you understand why such a simple extension took so much of my time and patience.

i also like having colored brackets, specifically `[]` so i can easily find placeholders. i do this like so, still under `"editor.tokenColorCustomizations"`:

```json
"workbench.colorCustomizations": {
        "editorBracketHighlight.foreground1": "#77dab4",
		"editorBracketHighlight.foreground2": "#77dab4",
		"editorBracketHighlight.foreground3": "#77dab4",
		"editorBracketHighlight.foreground4": "#77dab4",
		"editorBracketHighlight.foreground5": "#77dab4",
		"editorBracketHighlight.foreground6": "#77dab4"
        
    },
    "editor.bracketPairColorization.enabled": false,
    "[loveletter]": {
        "editor.bracketPairColorization.enabled": true,
        "editor.language.colorizedBracketPairs": [
		["[", "]"]
	]
    }
```
