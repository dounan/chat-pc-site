---
layout: macos-docs
---

# Add custom actions

- [Shortcuts](#shortcuts)
- [AppleScript](#applescripts)

## Shortcuts

1. ChatPC can run Shortcuts from your Mac's Shortcuts application.

1. The ChatPC AI assistant will decide when to call your Shortcut based on its description, which defaults to the Shortcut name.

1. If your Shortcut takes a text input, add a description for what input the AI assistant should pass in as the input, including what format the input should be in (e.g. `JSON array of fruit names`).

1. If your Shortcut produces a text output, add a description for the output, including the format of the output, so the AI assistant knows how to use it.

## AppleScript

ChatPC can also run arbitrary AppleScript files that you place in the designated folder found at `Settings > Actions > AppleScripts > Show in Finder`.

The script must follow the following rules:

1. The script must begind with a comment block at the top of the file:
    - `(* ... *)` for AppleScript
    - `/* ... */` for JavaScript (JXA)
2. The comment block must contain the following tags that describe the script:
    - `@permission {permissionType}`
        - Permission type can be `allow`, `ask`, `block` (to disable the script)
    - `@summary - Short summary of what the script does`
    - `@description - Longer description of what the script does`
    - `@param {type} name - Description of the parameter` for each parameter (in order)
        - Type can be `boolean`, `number`, or `string`
        - Type can be followed by a `?` to indicate it is optional (for example `string?`)
    - `@return {type} - Description of the return value`
        - Type can be `boolean`, `number`, `string`, or `void`
        - The description is optional if the type is `void`
3. The script must contain an entry point function that has the same name as the script. This function should take in the parameters described in the comment block (in the same order) and return the value as described in the comment block.
4. The script may contain other helper functions as needed.

Here is an example of a valid script named `openFile.scpt`:

```
(*
@permission {ask}
@summary Open a file by its URL
@description This script opens a file located at a specified URL
@param {string} fileURL - The URL of the file to be opened
@return {void}
*)
on openFile(fileURL)
	tell application "Finder"
		open location fileURL
	end tell
end openFile
```

You can [download more example scripts here](/releases/example-scripts.zip).
