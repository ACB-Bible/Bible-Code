<h3 align="center">Pako gzip Compression Tool</h3>

---

Pako can be used with Nodejs and it can also be used in the browser by linking to it in the browser.

Node Example:
Website: https://www.npmjs.com/package/install
1. First Install pako using npm:
```npm install pako```
2. Javascript to use pako in the browser:
```javascript
const pako = require('pako');

zipJson('path to file to compress or zip);
async function zipJson(path) {

    var file = fs.readFileSync(`${path}Verses.json`, 'utf8');
    const verses = JSON.stringify(await JSON.parse(file));
    let zipped = pako.gzip(verses, { to: 'string' });
    if (zipped) { writeFile(`${path}Verses.json.gz`, zipped) }
};

zipJson('path to file to decompress or unzip);
async function unzipJson(path) {

    var file = fs.readFileSync(`${path}Verses.json.gz`);
    let unzipped = pako.ungzip(file, { to: 'string' });
    let json = await JSON.parse(unzipped);
    let saveFile = JSON.stringify(json);
    if (saveFile) { writeFile(`${path}Versesun.json`, saveFile) };
};

async function writeFile(path, file) {

    return new Promise((resolve, reject) => {
        fs.writeFile(path, file, 'binary', err => {
            if (err) { console.error(err.message); reject(false); } else { resolve(true); };
        });
    });
};
```
---

Browser Example:
Click the "Download Zip" button to download the pako-master folder from the following GitHub repository https://github.com/nodeca/pako The pako.min.js file is located in the dist folder, and this is the file that contains all the compression functionality to compress and decompress files in the browser. It can be added to an HTML page and used in the following way:

HTML:
```html
<script src="pako.js"></script>

<script>

    compressStr("string to compress")
    function compressStr(str) {
        var zipped = pako.gzip(str, { to: 'string' });
        return zipped;
    };

    decompressStr("string to decompress")
    function decompressStr(str) {
        var unzipped = pako.ungzip(str, { to: 'string' });
        return unzipped;
    };
</script>
```