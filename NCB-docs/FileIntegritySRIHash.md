<h3 align="center">Integrity Attribute</h3>

---

#### Generate an SRI hash on Cloudflare
Use This Code With Caution:
1.  Search for the Javascript file that you want to generate an SRI hash for.
2. Click on the "SRI" button to generate the SHA-256 or SHA-512 hash for the resource.
3. Copy the SRI hash, and paste it into your code by adding the following HTML attribute to the script or link elements for the file:

Examples:
```html
<script src="myscript.js" integrity="sha256-The-copied-SRI-hash"></script>
<link src="myscript.js" integrity="sha512-The-copied-SRI-hash"></link>
```
---

#### Generate an SRI hash with the terminal
1. Download and install openssl.
2. Generate the SRI hash with the following for a JavaScript file with this openssl command in the terminal to create an SRI hash:
```
openssl sha256 -r myscript.js
```
3. Encode the hash to Base64 using openssl in the terminal with the following openssl command:
openssl enc -base64 -in myscript.js.sha256
This will produce an output string similar to the following:
```
sha256-123456 7890abcdef1 234567890abcdef1 2345678
```
4. Add this SRI hash to the ```<script>``` element that references the JavaScript file.

Example HTML:
```
<script src="myscript.js" integrity="sha256-1234567890abcdef1234567890abcdef12345678"></script>
```