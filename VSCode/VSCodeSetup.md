<h3 align="center">VSCode Environment Setup</h3>

---
There are two other projects that use the data files from the Bible Code project. All the data and source code for each of these projects is in the public domain and free of copyrights, therefore it's free for you to use in your own ministry or Bible project. If you use or alter any of this data or source code, please change the name of your project so people don't get confused.

The links to the example projects.

1. [The American Computerized Bible](https://github.com/ACB-Bible/AmericanComputerizedBible)

2. [The New Christian Bible](https://github.com/ACB-Bible/NCB)

---

<br>

##### Table of Contents:{#toc}
1. [Setup the Bible Code Project Environment](#stbcpe)
2. [Setup the LiveServer Debugger](#stld)
---

[Setup the Bible Code Project Environment:](#toc){#stbcpe}
The Bible Code Project contains many different public Domain versions of the Bible, including the BibleDB project. The BibleDBproject contains many different public domain Bible versions that are located under the DATA folder. Each version is organized in a folder using its popular title abreviation as the title of the folder. The file types in these folders include CSV, Js Javascript array file, Json, Jsonc, plain text, and an SQLite3.db.

"DB Browser for SQLite" for Windows is a graphical user interface(GUI) editor that can be used to edit SQLite3 database files that uses a point and click graphical user interface, and it can be installed from the Microsoft Store. You can use VSCode, which is an open source code Integrated Development Environment(IDE) to edit the code. You can also install NodeJS to debug, test, and run the .js Javascript files.

1. Microsoft Store:
https://apps.microsoft.com/home?hl=en-US&gl=US
2. Install NodeJS:
https://nodejs.org/en
3. Install VSCode:
https://code.visualstudio.com/download
4. Install SQLite3:
https://www.sqlite.org/download.html
5. Open VSCode and create a new terminal and install SQLite3 modules and node modules locally to your projaect from the terminal with this command:
```
npm install node
npm install SQLite3
```
5. Learning Curve - not too bad.
<br>

[Setup the LiveServer Debugger](#toc){#stld}
1. Edit the **Live Server** extension settings.json file to set **chromeDebuggingAttachment** to true, like this: `"liveServer.settings.ChromeDebuggingAttachment": true`. This enables the Chrome debugger attachment feature.

2. Install the **Debugger for Chrome** extension in VSCode. This will allow you to debug your web applications in Chrome from VSCode.

3. Create a launch.json file in your project folder with the following configuration:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:5500",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```

4. Save the launch.json file and start the Live Server by clicking on the **Go Live** button at the bottom of the VSCode editor.