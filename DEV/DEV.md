<a id="top"></a>
<h3 align="center">Development Environment Setup</h3>

---
There are two projects that use the data files from the BibleDB project. All the data and source code for each of these projects is in the public domain and free of copyrights, therefore it's free for you to use in your own ministry or Bible project. If you use or alter any of this data or source code, please change the name of your project so people don't get confused.

##### Bible Code Project Links:

1. [American Computerized Bible Project](https://github.com/ACB-Bible/AmericanComputerizedBible) - Source code for the American Computerized Bible project website.
2. [BibleDB](https://github.com/ACB-Bible/BibleDB) - The master SQLite3 database and other data files for multiple versions of the Bible, which is the foundation of the Bible Code Project.
3. [New Christian Bible Project](https://github.com/ACB-Bible/NCB)  - Source code for the New Christian Bible project website.
4. [Bible Code Project Documentation](https://github.com/ACB-Bible/DOC) - Complete documentation for all Bible Code Project development projects.
5. [Twenty-First Century Version Project](https://github.com/ACB-Bible/TWF)  - SQLite3 database for the Twenty-First Century Version translation project. The Twenty-First Century Version database is edited seperately from the master BibleDB SQLite3 database. It's imported later into the master BibleDB SQLite3 database.

---

<br>

##### Table of Contents
1. [Downloads for Bible Code Development Environment](#downloads-for-Bible-code-development-envirnment)
2. [Setup the LiveServer Debugger](#setup-the-liveserver-debugger)
3. [Create and Install the localhost SSL Certificate](#create-and-install-the-localhost-ssl-certificate)
4. [Miscellaneous](#miscellaneous)

---

##### Downloads for Bible Code Development Envirnment
1. [DB Browser](https://sqlitebrowser.org/) - DB Browser is a graphical User Interface for editing SQLite3 databases. With it's point & click interface it makes editing the databases much simpler.
2. [Microsoft Store](https://apps.microsoft.com/home?hl=en-US&gl=US) - The Microsoft Store needs no explanation, it's listed here just in case you need to download tools from Microsoft.
3. [NodeJS](https://nodejs.org/en) - NodeJS is a server-side Javascript interpreter and lightweight server. It's used extensively in the Bible Code Projects.
4. [SQLite3](https://www.sqlite.org/download.html) - SQLite3 is a lightweight database engine, and it can be used for editing the TWF.db datadase with the Windows Terminal, Command Prompt, or Powershell. Editing the database this way requires knowledge of the SQLite3 version of the SQL database language.
5. [VSCode](https://code.visualstudio.com/download) - Visual Studio Code is my chosen editor for editing the source code in all the projects in the Bible Code Project.




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

* Create a Self-signed SSL certificate:
    ```bash
        New-SelfSignedCertificate -NotBefore (Get-Date) -NotAfter (Get-Date).AddYears(5) -Subject "CN=localhost" -KeyAlgorithm "RSA" -KeyLength 2048 -HashAlgorithm "SHA256" -CertStoreLocation "Cert:\CurrentUser\My" -FriendlyName "HTTPS Development Certificate" -TextExtension @("2.5.29.19={text}","2.5.29.17={text}DNS=localhost") $pwd = convertTo-SecureString -String "PassfN2" -Force -AsPlainText
    ```
<br>

* Install the localhost pfx Certificate:

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

The VS-Profile.code-profile - A VSCode profile is located in the VSCode folder and it can be imported into VSCode. This profile contains the settings and extensions that I find most helpful working on all the Bible Code projects located in the VSCode folder in the Bible-Code Documentation project.

[Back to Top](#top)

---

<br>
   
#### The Bible Code Project

[Bible Code Project Documentation for Developers](https://github.com/ACB-Bible/Bible-Code/)
The "Bible Code Project" is a collection of GitHub repositories containing source code and data that can be used to develop your own computerized Bible project. All of the data and source code for each of these projects is in the public domain and free of copyrights, therefore it's free for you to use. The technical documentation for all of these projects is available in the Bible Code Project GitHub repository. If you to use any of the source code or data files in your own ministry or Bible project, please change the name of it, so people don't get confused.

[Back to Top](#top)

---

<br><br>
<p align="center">
    <p align="center">
    <em>God loves you, Jesus loves you, I love you, and this is God's free gift to you .....</em>
</p>    
</p>