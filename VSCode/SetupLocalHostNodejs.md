<h3 align="center">Setup Localhost for VSCode</h3>

---

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