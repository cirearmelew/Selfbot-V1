Markdown# Discord Bot Source Code Usage Guide

Below is a detailed guide, reorganized for easier following. I've improved the structure with clear headings, lists, and code formatting to enhance readability and aesthetics. Read each section carefully before implementing!

## Basic Configuration Methods

### Method 1: Configuring the `.env` File
The `.env` file stores sensitive information like tokens and prefixes.

1. Open the `.env` file and update `DISCORD_TOKEN` with your Discord token.  
   *(See the [How to Get DISCORD_TOKEN](#how-to-get-discord_token) section at the end of the guide for instructions).*

2. Change `prefix =` to your desired prefix character (e.g., `prefix = !`).  
   - **Note**: If hosting the bot, use the command `<prefix>prefixset <new_prefix>` for temporary changes. After restarting the bot, it will revert to the `.env` value.

3. Update `ID_DISCORD =` with your Discord ID. This enables the AFK command in `index.js`.

### Method 2: Configuring the `AllowUserIDs.js` File
This file controls the list of users allowed to use the bot.

- Find the line:  
  ```javascript
  AllowUserIDs: ['ID_User_1', 'ID_User_2']

Replace ID_User_1 with your ID (recommended to place it first).
To add others: Replace ID_User_2 with a new ID, or add more like this:JavaScriptAllowUserIDs: ['ID_User_1', 'ID_User_2', 'ID_User_3']
For personal use only: Remove extras, e.g.:JavaScriptAllowUserIDs: ['ID_User_1']

Method 3: The cmds Folder (Note: Master All Commands!)
The cmds folder contains all bot commands. Each category has a note.md file with detailed explanations.
Recommendation: Read all note.md files before using to avoid errors!
Method 4: Customizing the abuse.txt File
This file is used for the abuse command (custom insults or content).

Open the file and add content as desired, one item per line:textContent 1
Content 2
Content 3
...
You can write anything (humorous, memes, etc.).

Method 5: Running the Source Code
Requirements: Ensure Node.js is installed and added to your environment variables (PATH). If not, search YouTube: "Install Node.js on Windows/Mac".

Open the folder containing the source (e.g., C:\Users\mewza\Desktop\project 2).
Open Command Prompt (CMD) in that folder:
Run npm install to install dependencies.
Close CMD and reopen the source in VSCode.

In VSCode, open the Terminal (Ctrl + Shift + `).
Run node index.js.
If the bot runs without errors, success! If errors occur, contact support.


What is an Alias?
In programming, an alias (or nickname) is a short substitute name for a long command or module, making code more readable. Example: Instead of typing commands, use cmds.
Method 6: Adding Aliases to Commands
If a command is too long (e.g., commands), add an alias to shorten it.

Locate the command file (e.g., cmds/Help/commands.js).
Add the line aliases: ['alias_name'] to the command object:JavaScript{
  name: 'commands',
  description: 'Displays the list of command categories.',
  aliases: ['cmds']  // Now use !cmds instead of !commands
}
Tip: Choose short, related aliases (e.g., commands → cmds).


How to Get Required Items for the Source
1. Getting DISCORD_TOKEN {#how-to-get-discord_token}
The token is the key for the bot to connect to Discord. Never share your token with anyone!

Open your browser and log in to your Discord account.
Press F12 (or Ctrl + Shift + I) to open Developer Tools.
Switch to the Console tab.
Paste the following code into the Console:JavaScript(webpackChunkdiscord_app.push([
    [""],
    {},
    (e) => {
        for (let t in ((m = []), e.c)) m.push(e.c[t]);
    },
]),
m)
    .find((e) => e?.exports?.default?.getToken !== void 0)
    .exports.default.getToken();
If you see a "allow pasting" warning (in yellow), type allow pasting into the Console.
If the token doesn't appear, paste the code from step 4 again.
The token will display as a red string in single quotes ('...') or double quotes ("...").
Copy the token and paste it into the .env file at DISCORD_TOKEN=.


Note: If you encounter errors, try refreshing the page or enabling Developer Mode in Discord (User Settings > Advanced > Developer Mode).
