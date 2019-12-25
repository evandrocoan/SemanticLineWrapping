Semantic Word Wrap for Sublime Text
===================================

This Sublime Text plugin inserts new line characters
between words while typing obtaining an hard-wrapped file.
The difference with normal hard-wrapping is
that the new lines are inserted in more natural places than
what happens in a hard-wrap at a certain width:
newlines are inserted preferably near punctuation
giving to the text a natural rhythm.


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
   wait few seconds until the installation finishes up
1. Now,
   Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Go to the menu **`Tools -> Command Palette...
   (Ctrl+Shift+P)`**
1. Type **`Preferences:
   Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
   find the following setting on your **`Package Control.sublime-settings`** file:
   ```js
       "channels":
       [
           "https://packagecontrol.io/channel_v3.json",
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
       ],
   ```
1. And,
   change it to the following, i.e.,
   put the **`https://raw.githubusercontent...`** line as first:
   ```js
       "channels":
       [
           "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
           "https://packagecontrol.io/channel_v3.json",
       ],
   ```
   * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
     you will not install this forked version of the package,
     but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
   go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
search for **`SemanticLineWrap`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## Settings

`semantic_wrap`

Enables or disables semantic hard-wrapping.
Can be toggled with the `Edit > Semantic Wrap` menu.

`semantic_wrap_min_words`

The minimum number of words on the current line to justify
a break.

`semantic_wrap_max_words`

The maximum number of words tolerated on the current line.
Some presets can be selected from the `Edit > Semantic Wrap`
menu.

## Customisation

The keymap installed by the plugin is pretty self explanatory:

```json
[
    {
        "keys": [" "],
        "args": {"characters": "\n"},
        "command": "insert",
        "context": [
            {"key": "setting.semantic_wrap"},
            {"key": "semantic_wrap"},
            {
                "key": "preceding_text",
                "operand": "[.,;!?:]$",
                "operator": "regex_contains"
            }
        ]
    },
    {
        "keys": [" "],
        "args": {"characters": "\n"},
        "command": "insert",
        "context": [{"key": "semantic_wrap_words"}]
    }
]
```

You can customise it in your user keymap in various ways:
you can change which punctuation is considered suitable for a break,
or which character has to be inserted to end a line;
if you wish to enable the binding only for certain syntaxes
you can replace `{"key": "setting.semantic_wrap"}` with
`{"key": "selector", "operator": "equal", "operand": "YOUR.SCOPE"}`.
