<a id="top"></a>
<h3 align="center">VSCode Development Environment Setup</h3>

---
There are two projects that use the data files from the BibleDB project. All the data and source code for each of these projects is in the public domain and free of copyrights, therefore it's free for you to use in your own ministry or Bible project. If you use or alter any of this data or source code, please change the name of your project so people don't get confused.

##### Links to the example projects:

1. [American Computerized Bible Project](https://github.com/ACB-Bible/AmericanComputerizedBible) - Source code for an online Bible.
2. [BibleDB](https://github.com/ACB-Bible/BibleDB) - The master SQLite3 database and other data files for multiple versions of the Bible.
3. [New Christian Bible Project](https://github.com/ACB-Bible/NCB)  - Source code for an online Bible.
4. [Bible Code Project Documentation](https://github.com/ACB-Bible/DOC) - Complete documentation for all projects.

---

<br>

##### Table of Contents
1. [Downloads from Microsoft Store](#downloads-from-microsoft-store)
2. [Setup DB Browser for BibleDB](#setup-db-browser-for-bibledb)
3. [Setup the LiveServer Debugger](#setup-the-liveserver-debugger)
4. [Create and Install an SSL Certificate for LocalHost](#create-and-install-an-ssl-certificate-for-localhost)

---

#### Downloads from Microsoft Store
1. Microsoft Store:
https://apps.microsoft.com/home?hl=en-US&gl=US
2. NodeJS:
https://nodejs.org/en
3. VSCode:
https://code.visualstudio.com/download
4. SQLite3:
https://www.sqlite.org/download.html

* Once these apps have been downloaded, install them by double-clicking on them and follow the prompts.

* After these apps have been installed, open VSCode and create a new terminal and install SQLite3 modules and node modules locally to your project from the terminal with this command:
```bash
npm install node
npm install SQLite3
```
---

##### Setup DB Browser for BibleDB
"DB Browser for SQLite" for Windows is a graphical user interface(GUI) editor that can be used to edit SQLite3 database files that uses a point and click graphical user interface, and it can be installed from the Microsoft Store. You can use VSCode, which is an open source code Integrated Development Environment(IDE) to edit the code. You can also install NodeJS to debug, test, and run the .js Javascript files.

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

---

<br>

##### Create and Install an SSL Certificate for LocalHost

***Create:***
```bash
    New-SelfSignedCertificate -NotBefore (Get-Date) -NotAfter (Get-Date).AddYears(5) -Subject "CN=localhost" -KeyAlgorithm "RSA" -KeyLength 2048 -HashAlgorithm "SHA256" -CertStoreLocation "Cert:\CurrentUser\My" -FriendlyName "HTTPS Development Certificate" -TextExtension @("2.5.29.19={text}","2.5.29.17={text}DNS=localhost") $pwd = convertTo-SecureString -String "PassfN2" -Force -AsPlainText
```
<br>

***Install the localhost pfx Certificate:***

* Right click on the pfx file
    * Click >> Install Pfx
        The certificate install wizard will popup
        Select Current User or Local Machine
    * Click >> Next
        Select or change the pfx file you want to import
    * Click >> Next
        Enter the certificat password
        Select Import options
    * Click >> Next
        Certificate Store
        Select Trusted Root Store for the pfx
    * Click >> Next
    * Click >> Finish >> OK
    ---

<br>

[Back to Top](#top)

<h6 align="center" title="God's Word Is Not For Sale">Bible Code Project - Copyright © Free - Inspired by God ... 2023</h3>
<h6 align="center">Good luck with your efforts!</h6>