# Prompt Strings

Date: March 14, 2022
Lecture #: 2
Lecture URL: https://youtu.be/UBjENhxwpcU
Notion URL: https://21f1003586.notion.site/Prompt-Strings-3cb3d692ac084eb7bd2d1c3fbe22209f
Type: π Lecture
Week #: 8

### `bash` prompts

- PS1 β primary prompt string: `$`
- PS2 β secondary prompt for multi-line input: `>`
- PS3 β prompt string in select loops: `#?`
- PS4 β prompt string for execution trace: `+`

### Escape Sequences

![Untitled](Prompt%20Strings%2017dd36f320e44e00851314ebebf5e5ae/Untitled.png)

`\u@\h:\w\$` π

Username @ Machine name : **Current Directory** *Prompt Symbol*

### Python command line

- `ps1` and `ps2` are defined in the module `sys`
- Change `sys.ps1` and `sys.ps2` if needed
- Override `__str__` method to have dynamic prompt

`>>>`

![Untitled](Prompt%20Strings%2017dd36f320e44e00851314ebebf5e5ae/Untitled%201.png)

Modify the PS1 prompt by

`PS1=β\#:\$β`

If we want to go back to the default prompt β `source .bashrc`

Modify the PS2 prompt

`PS2=βHey \u, close the string: β`

Similar for PS3 and PS4