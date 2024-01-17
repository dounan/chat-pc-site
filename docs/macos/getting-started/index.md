# MacOS Getting Started

Follow the instructions below to get started.
- [Install the MacOS Application](#install-the-macos-application)
- [Acccessing settings](#acccessing-settings)
- [Permissions](#permissions)
- [Adding actions](#adding-actions)
- [Interacting with the ChatPC AI assistant](#interacting-with-the-chatpc-ai-assistant)
- [Using the Chat UI](#using-the-chat-ui)
- [Subscription plans](#subscription-plans)
- [FAQ](#faq)
- [Support](#support)

## Install the MacOS Application

1. **[Download](https://github.com/dounan/chat-pc-site/releases/download/v0.22/ChatPC.v0.22.zip) the MacOS ChatPC application (requires MacOS 13.0 and higher)**

1. Unzip the .zip file.

1. Move the extracted `ChatPC` application file to your `Applications` folder.

    ![move app to applications folder](/images/macos-getting-started/move-app.png)

1. Go to your `Applications` folder and open the `ChatPC` application.

1. The app should appear in the MacOS menu bar at the top right of your screen.

    ![opened app](/images/macos-getting-started/opened_app_arrow.png)

1. The settings window should automatically open. If it does not, right-click (or control-click) the ChatPC menu bar icon, and click `Settings` > `General`.

    ![settings](/images/macos-getting-started/signup-settings.png)

1. Click the `Sign up` button and click `Continue` in the popup. This will open a sign up window in your web browser.

    ![sign up](/images/macos-getting-started/signup-alert.png)

1. Follow the instructions on the sign up page.

## Acccessing settings

To access settings and other options, right-click (or control-click) the ChatPC menu bar icon.

## Permissions

1. ChatPC requires certain permissions in order to provide a convenient and simple user experience for you.

1. These permissions will be prompted for at the time they are needed.

1. To chat with the current selected text, ChatPC needs access to:

    1. `System Events`

        ![system events permission alert](/images/macos-getting-started/system-events-alert.png)

    1. `Accessibility features` (you can change this setting anytime in your Mac's `System Settings` > `Privacy & Security` > `Accessibility`)

        ![accessibility permission alert](/images/macos-getting-started/accessibility-alert.png)

        ![accessibility permission alert](/images/macos-getting-started/accessibility-enable.png)

## Adding actions

Actions allow ChatPC to interact with your local computer and interact with other native applications. The ChatPC AI assistant will determine which actions to run based on your prompts.

To add actions, go to the `Actions` tab in the [ChatPC settings](#acccessing-settings).

Note that all added actions are sent to the AI assistant in every message and will consume credits.

### Shortcuts actions

1. ChatPC can run Shortcuts from your Mac's Shortcuts application.

1. The ChatPC AI assistant will decide when to call your Shortcut based on its description, which defaults to the Shortcut name.

1. If your Shortcut takes a text input, add a description for what input the AI assistant should pass in as the input, including what format the input should be in (e.g. `JSON array of fruit names`).

1. If your Shortcut produces a text output, add a description for the output, including the format of the output, so the AI assistant knows how to use it.

### AppleScripts actions

ChatPC can also run arbitrary AppleScript that you provide, with a few requirements:

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

You can [download and unzip more example scripts here](/releases/example-scripts.zip).

### Folder actions

ChatPC will only manage folders you have explicitly given it permission to access. Once you have added one or more folders, the following actions become available:

- List the contents of the folder or a sub folder
- Read a file's contents
- Extract key sentences from a file. This can be used to help summarize very long files.
- Append text to a file
- Find and replace text in a file
- Create a file or folder
- Move a file or folder
- Rename a file or folder
- Open a file with its default application

#### Controlling permissions

Once you've added a folder you can control the read and write permissions for the folder.

- __Read__ permissions control all actions that _read_ data from the folder, such as listing files or viewing the contents of a specific file
- __Write__ permissions control all actions that _write_ data to the folder, such as creating new files, or updating existing ones

For each permission type, you can select one of the following options:
- __Allow__ - always allow these actions without asking you for permission
- __Ask__ - ask for permission before executing an action. Actions pending review will pop up as notifications and can also be found in the `Pending` settings tab.
- __Block__ - always reject these actions

#### Limitations

- Only text based files (UTF-8) can be read and written to with the standard file actions. AppleScript actions may be able to provide more advanced functionality.
- There is a limit to the number of files that can be listed in a folder when listing or searching for files. Files beyond this limit will simply be ignored. This limit should be sufficiently high for most use cases and will change over time. Please reach out to support if you think you are impacted by this limit.
- There is a limit to the size of file that can be read. Reading a file that exceeds this limit will result in an error.
- Be mindful of the LLM's context window size, especially when reading large files.

## Interacting with the ChatPC AI assistant

You can interact and prompt the ChatPC AI assistant in different ways.

1. Chat through the built in [chat UI](#using-the-chat-ui). The AI model can be selected when starting a new conversation. The following models are supported:

    1. `gpt-3.5-turbo` - uses 1 credit per token

    1. `gpt-3.5-turbo-16k` - uses 2 credits per token

    1. `gpt-4` - uses 20 credits per token. This model will give the best results, especially for more complex tasks.

    1. For more information on these models, see the [OpenAI documentation](https://platform.openai.com/docs/models/overview).

1. Prompt it as part of a Shortcut.

    ![prompt via Shortcuts](/images/macos-getting-started/prompt-via-shortcuts.png)

1. Prompt it as part of an AppleScript. The model parameter is optional and defaults to `gpt-3.5-turbo`.

```
tell application "ChatPC"
	log (prompt with message "write me a short poem")
	log (prompt "gpt-4" with message "write me a better poem")
end tell
```

## Using the Chat UI

### Basic chats
1. Open the chat window by clicking the menu bar icon or using the global shortcut `Control-Space` (can be changed under `Settings` > `Chat`).

1. Type your request for your AI assistant. New lines can be inserted with `Option-Return`.

    ![empty chat](/images/macos-getting-started/empty-chat.png)

1. Press `Return` or click the arrow button to send your message.

1. Close the chat window by hitting the `esc` key, or clicking anywhere outside the chat window.

### Chat with selection

ChatPC allows you to chat with selected text.

1. Select some text in any application

1. Open the chat window with `Control-Space`.

1. Once the chat window is open, you can see your selected text.

    ![import selected text](/images/macos-getting-started/import-selected-text.png)

1. If needed, you can edit the selected text.

1. Use one of the one click actions, or write your own message like a normal chat.

### Using the AI response

1. You can copy the AI response with a click of a button.

1. You can even insert the AI response into the frontmost app! Click the insert button of the response you want to insert, or use `Command-Return` to insert the latest response.

    ![chat response](/images/macos-getting-started/chat-response.png)

### Custom one-click prompts

1. You can add your own custom one-click prompts for selected text under `Settings` > `Chat`. Drag and drop the prompts to reorder.

    ![custom prompts settings](/images/macos-getting-started/custom-prompts-settings.png)

    ![custom prompts example](/images/macos-getting-started/custom-prompts-example.png)

    ![custom prompts usage](/images/macos-getting-started/custom-prompts-in-chat.png)

### Managing previous chats

1. Use the title bar to view previous chats, delete chats, and start a new chat.

    ![chat management](/images/macos-getting-started/chat-management.png)

1. The delete button reveals 3 options:

    1. **Delete current chat** - Delete the current active chat (only visible if there is an active chat).
    1. **Delete older chats** - Delete all chats older than the current active chat (only visible if there is an active chat).
    1. **Delete all chats** - Delete all chats.

### Keyboard shortcuts

| Action | Shortcut |
| - | - |
| Open chat window | `Control-Space` (default) |
| Send message | `Return` |
| Insert new line in message | `Option-Return` |
| Insert last AI response into frontmost app | `Command-Return` |
| New chat | `Command-N` |
| Go to next chat | `Command-J` |
| Go to previous chat | `Command-K` |
| Delete current chat | `Command-D` |

## Subscription plans

The default free plan has a lifetime token limit as well as other limitations. You can manage your subscription plan in the app settings.

Check out the different subscription plans at https://chatpc.ai/plans!

With a subscription plan, you can enter your own OpenAI API key to avoid using credits or if you run out of credits. You can set your OpenAI API key under `Chat` settings.

## FAQ

Coming soon

## Support

If you run into any issues or have any questions, please reach out to us at support@chatpc.ai.
