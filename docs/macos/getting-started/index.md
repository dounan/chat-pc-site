# MacOS Getting Started

ChatPC enables **safe and secure** interaction between ChatGPT and your computer. It gives ChatGPT the ability to read and modify local files and interact with native applications, all while upholding strict access controls. You have the power to control precisely what actions ChatPC can perform and what data it can access.

Follow the instructions below to get started.
- [1. Install the ChatGPT plugin](#1-install-the-chatgpt-plugin)
- [2. Email support@chatpc.ai to get access to the beta](#2-email-supportchatpcai-to-get-access-to-the-beta)
- [3. Install the MacOS Application](#3-install-the-macos-application)
- [4. Give ChatPC access to desired folders](#4-give-chatpc-access-to-desired-folders)
- [5. Add AppleScripts (and JXA) to enable advanced functionality](#5-add-applescripts-and-jxa-to-enable-advanced-functionality)
- [Helpful prompts](#helpful-prompts)
- [FAQ](#faq)
- [Support](#support)

## 1. Install the ChatGPT plugin

__⚠️ NOTE:__ ChatPC is currently in private beta. The plugin can only be installed only if you have ChatGPT plugin developer access.

1. In the ChatGPT UI, go to `Plugin Store` > `Install an unverified plugin`
1. Input the following URL: `app.chatpc.ai`
1. Follow the instructions to install the plugin
1. After installing, you will be redirected to a login page. Register for an account and login.

## 2. Email support@chatpc.ai to get access to the beta
Let us know the email address you signed up with so we can approve your account for the beta.

## 3. Install the MacOS Application

__⚠️ NOTE:__ Requires MacOS 13.0 and higher. Please email support@chatpc.ai if you have an older version of MacOS.

1. [Download](/releases/ChatPC%200.6.dmg) the MacOS ChatPC application

1. Open the .dmg file. This will mount the image to your Desktop and should automatically open it. If not, double click the ChatPC image on your Desktop.

1. Drag the ChatPC application file into your `Applications` folder

    ![install app](/images/macos-getting-started/install_app.png)

1. Open the ChatPC application

1. The app should appear in the MacOS menu bar at the top right of your screen.

    ![opened app](/images/macos-getting-started/opened_app_arrow.png)

1. The app should open a window with a login button. If it does not:
    1. Click the ChatPC menu bar icon
    1. Click `Settings`
    1. Click `General`

1. Click the `Login` button which will open a login window in your web browser

1. Follow the instructions on the login page

## 4. Give ChatPC access to desired folders

To ensure you are in control, ChatPC can only access folders that you explicitly give it access to. When you give ChatPC access to a folder, it can perform the following actions in the folder:

- List all files and folders
- List matching files (by regex)
- Read a file's contents
- Append text to a file
- Find and replace text in a file
- Create a file or folder
- Move a file or folder (can also be used to rename)
- Open a file with its default application

### Adding a folder

1. Click the ChatPC menu bar icon
1. Click `Settings`
1. Click `Folders`
1. Click the `+` button on the bottom left of the settings window

### Controlling permissions

Once you've added a folder you can control the read and write permissions for the folder.

- __Read__ permissions control all actions that _read_ data from the folder, such as listing files or viewing the contents of a specific file
- __Write__ permissions control all actions that _write_ data to the folder, such as creating new files, or updating existing ones

For each permission type, you can select one of the following options:
- __Allow__ - always allow these actions without asking you for permission
- __Ask__ - ask for permission before executing an action. Actions pending review can be found in the `Pending` settings page.
- __Block__ - always reject these actions

### Test it out!

Try out the following prompts in ChatGPT with the DeskopGPT plugin enabled:

> List my local folders

> List the files in the ___ folder

> Write me a joke and save it in a new file in the ___ folder

__PRO TIP__: when specifying a folder, you don't need to write out the entire path to the folder. The AI is smart enough to figure out the full folder path as long as it has seen all available folders already. For example, the following folder `/Users/fakeuser/Documents/ChatPC_sandbox` can simply be referred to as "the sandbox folder".

### Limitations

- The number of folders that can be added varies based on your subscription.
- Only text based files (UTF-8) can be read and written to with the standard file actions. AppleScript actions may be able to provide more advanced functionality.
- There is a limit to the number of files that can be listed in a folder when listing or searching for files. Files beyond this limit will simply be ignored. This limit should be sufficiently high for most use cases and will change over time. Please reach out to support if you think you are impacted by this limit.
- There is a limit to the size of file that can be read. Reading a file that exceeds this limit will result in an error.
- Be mindful of the LLM's context window size, especially when reading large files.

## 5. Add AppleScripts (and JXA) to enable advanced functionality

ChatPC can execute AppleScript files that you add, which allows you to utilize ChatPC to do anything on your computer that AppleScript can.

### Adding a script

You can [download and unzip ChatPC's official example scripts](/releases/example-scripts.zip) or write your own script using the MacOS `Script Editor` (instructions below).

To install a script:
1. Click the ChatPC menu bar icon
1. Click `Settings`
1. Click `Scripts`
1. Click the `Manage` button on the bottom left of the settings window. This will open up the scripts folder
1. Move your script files into the scripts folder

### Adding existing scripts

[Download official ChatPC example scripts](/releases/example-scripts.zip)

Coming soon: instructions on where to find 3rd party scripts

__⚠️ Warning__: make sure you trust any 3rd party scripts you add. Adding untrusted and unverfieid scripts can cause harm to your computer and should be avoided.

### Write your own script

ChatPC expects any added script files to abide by the following format:

1. The script should begind with a comment block at the top of the file:
    - `(* ... *)` for AppleScript
    - `/* ... */` for JavaScript (JXA)
2. The comment block should contain the following tags that describe the script:
    - `@summary - Short summary of what the script does`
    - `@description - Longer description of what the script does`
    - `@param {type} name - Description of the parameter` for each parameter (in order)
        - Type can be `boolean`, `number`, or `string`
    - `@return {type} - Description of the return value`
        - Type can be `boolean`, `number`, `string`, or `void`
        - The description is optional if the type is `void`
3. The script should contain an entry point function that has the same name as the script. This function should take in the parameters described in the comment block (in the same order) and return the value as described in the comment block.
4. The script may have other helper functions as needed.

Here is an example of a valid script:

```
/*
@summary Search contacts
@description Search through all contacts by all fields and returns a vCard representation for each matching contact
@param {string} searchString - The string to search for
@return {string} JSON array of vCard strings of matching contacts
*/
function searchContacts(searchString) {
    let app = Application("Contacts");
	const vcards = app.people()
		.map(p => p.vcard())
	    .filter(vcard => vcard.toLowerCase().includes(searchString.toLowerCase()));
	return JSON.stringify(vcards);
}
```

__PRO TIP__: You can ask ChatGPT to write scripts for you, but the results can be hit or miss. Use the [helper prompt below](#ask-chatgpt-to-generate-chatpc-compatible-applescript-and-jxa) to teach ChatGPT how to write ChatPC compatible AppleScript and JXA.

### Limitations

- There is a limit on the size of the script's return value. Returning a value that is larger than this limit will result in an error.
- Be mindful of the LLM's context size, especially when return large values such as long strings.

## Helpful prompts

### Ask ChatGPT for the list of all available actions

> What are the available actions for the ChatPC plugin?

### Ask ChatGPT to generate ChatPC compatible AppleScript (and JXA)

> Here are the requirements for a ChatPC compatible script.
>
> The beginning of the script must be a block comment. The block comment must have the following content:
> 1. `@summary Short summary of what the script does`
> 2. `@description Slightly longer description of what the script does`
> 3. For every input parameter, there should be a `@param {type} Name - Description of the parameter`. The type can only be one of `string`, `number`, or `boolean`
> 4. `@return {type} Optional description of the return value if the type is not void`. The type can only be one of `string`, `number`, `boolean`, or `void`
>
> The script must contain a function named the same as the file name with function parameters that match the order of parameters defined in the block comment.
>
> Here is an example of a valid ChatPC JXA script:
>
> ```
> /*
>  * @summary List open applications
>  * @description List all local applications that are currently open
>  * @return {string} CSV list of open applications
>  */
> function listOpenApplications() {
>   // implementation
> }
> ```
>
> Here is an example of a valid ChatPC AppleScript script:
>
> ```
> (*
> @summary Add two numbers
> @description Adds two numbers together and returns the sum
> @param {number} num1 First number to add
> @param {number} num2 Second number to add
> @return {number} Sum of the two numbers
> *)
> on addTwoNumbers(num1, num2)
> 	return num1 + num2
> end addTwoNumbers
> ```
>
> Respond witih "I understand" if you understand.

## FAQ

Coming soon

## Support

If you run into any issues or have any questions, please reach out to us at support@chatpc.ai.
