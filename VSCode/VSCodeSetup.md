<a id="top"></a>
<h3 align="center">VSCode Development Environment Setup</h3>

---
There are two projects that use the data files from the "BibleDB" project. All the data and source code for each of these projects is in the public domain and free of copyrights, therefore it's free for you to use in your own ministry or Bible project. If you use or alter any of this data or source code, please change the name of your project so people don't get confused.

##### Bible Code Project Links:

1. [American Computerized Bible Project](https://github.com/ACB-Bible/AmericanComputerizedBible) - Source code for an online Bible.
2. [BibleDB](https://github.com/ACB-Bible/BibleDB) - The master SQLite3 database and other data files for multiple versions of the Bible.
3. [New Christian Bible Project](https://github.com/ACB-Bible/NCB)  - Source code for an online Bible.
4. [Bible Code Project Documentation](https://github.com/ACB-Bible/DOC) - Complete documentation for all projects.

---

<br>

##### Table of Contents
1. [Downloads for Bible Code Development Envirnment](#downloads-for-bible-code-development-envirnment)
2. [Setup the LiveServer Debugger](#setup-the-liveserver-debugger)
3. [Create and Install the localhost SSL Certificate](#create-and-install-the-localhost-ssl-certificate)
4. [Miscellaneous](#miscellaneous)

---

##### Downloads for Bible Code Development Envirnment
1. Microsoft Store:
https://apps.microsoft.com/home?hl=en-US&gl=US
2. NodeJS:
https://nodejs.org/en
3. VSCode:
https://code.visualstudio.com/download
4. SQLite3:
https://www.sqlite.org/download.html
5. DBBrowser:
https://sqlitebrowser.org/

* Once these apps have been downloaded, install them by double-clicking on their icon and follow the prompts.

* After these apps have been installed, open VSCode and create a new terminal and install SQLite3 modules and node modules locally to your project from the terminal with this command:
* "DB Browser for SQLite" for Windows is a graphical user interface(GUI) editor that can be used to edit SQLite3 database files. It's a point and click graphical user interface that simplifies the editing of the BibleDB SQLite3 master database.
```bash
npm install node
npm install SQLite3
```
[Back to Top](#top)

---

<br>

##### Setup the LiveServer Debugger
1. Click on the VSCode gear icon in the lower left hand corner of the VSCode editor to open settings. Search for and edit the "liveServer.settings.chromeDebuggingAttachment" property and set it to true. This enables the Chrome debugger attachment feature.

```json
"liveServer.settings.ChromeDebuggingAttachment": true
```

2. Create a .vscode folder in your project's top level folder, then create a launch.json file in the .vscode folder. Edit the launch.json file with the following configurations for localhost and Nodejs. Save the launch.json file and start LiveServer by clicking on the **Go Live** button at the bottom right hand corner of the VSCode editor.

```json
// Copy and paste this code to your lounch.json file

{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Chrome Example Launch with localhost",
            "url": "http://localhost:5500",
            "webRoot": "${workspaceFolder}"
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Nodejs Example Launch Javascript.js",
            "program": "${workspaceFolder}/PathTo/Nodejs-Example.js",
            "skipFiles": [ "<node_internals>/**" ],
        }
    ]
}
```

[Back to Top](#top)

---

<br>

##### Create and Install the localhost SSL Certificate

* <a style="color: crimson;">Create a Self-signed SSL certificate:</a>
    ```bash
        New-SelfSignedCertificate -NotBefore (Get-Date) -NotAfter (Get-Date).AddYears(5) -Subject "CN=localhost" -KeyAlgorithm "RSA" -KeyLength 2048 -HashAlgorithm "SHA256" -CertStoreLocation "Cert:\CurrentUser\My" -FriendlyName "HTTPS Development Certificate" -TextExtension @("2.5.29.19={text}","2.5.29.17={text}DNS=localhost") $pwd = convertTo-SecureString -String "PassfN2" -Force -AsPlainText
    ```
<br>

* <a style="color: crimson;">Install the localhost pfx Certificate:</a>

    * 1. Right click on the pfx file
    Click >> Install Pfx
        The certificate install wizard will popup
        Select Current User or Local Machine
    * 2. Click >> Next
        Select or change the pfx file you want to import
    * 3. Click >> Next
        Enter the certificate password
        Select Import options
    * 4. Click >> Next
        Certificate Store
        Then Select Trusted Root Store for the pfx
    * 5. Click >> Next
    * 6. Click >> Finish >> OK

---

<br>

##### Miscellaneous

1. An example of a pre-generated SSL pfx certificate for the localhost created by the Windows Terminal located in the VSCode folder in the Bible-Code Documentation project.

2. VS-Profile.code-profile - A VSCode profile that can be imported into VSCode. This profile contains the settings and extensions that I find most helpful working on all the Bible Code projects located in the VSCode folder in the Bible-Code Documentation project.

[Back to Top](#top)

---

<br>

<h6 align="center" title="God's Word Is Not For Sale">Bible Code Project - Copyright © Free - Inspired by God</h3>
<h6 align="center">Good luck with your efforts!</h6>