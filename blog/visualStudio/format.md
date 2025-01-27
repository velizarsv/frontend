We will start by installing the Prettier extension for VS Code. Once you have installed it, you can use it with CTRL + CMD + P (MacOS) or CTRL + Shift + P (Windows) to manually format a file or a selection of code.
<br/><br/>
If you don't want to format your file with the given shortcut manually every time, you can format it on save as well. Therefore you need to open your VS Code user's settings/preferences as JSON and enter the following configuration:<br/><br/>
// enable globally (here: format on save)<br/>
"editor.formatOnSave": true<br/>
// enable per-language (here: Prettier as formatter)<br/>
"[javascript]": {<br/>
    "editor.defaultFormatter": "esbenp.prettier-vscode"<br/>
}<br/><br/>

<br/>
Afterward, a JavaScript file should format automatically once you save it. Now you don't need to worry about your code formatting anymore, because Prettier takes care of it. Prettier comes with a few options which you can apply globally too; which I like to do for my personal projects:
