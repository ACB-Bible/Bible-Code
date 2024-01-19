<h3 align="center">Cloudflare Compression</h3>

---

<br>
Use This Code With Caution:

Brotli compression is disabled by default for Cloudflare Business plan domains, but it's automatically enabled for all other domain plans. Brotli compression is applied to all assets on your site, including HTML, CSS, JavaScript, and image files. Cloudflare requires a minimum file size to apply compresssion. The minimum size for GZIP responses is 48 bytes. For Brotli responses the files must have a minimum size of 50 bytes. When both Gzip and Brotli are enabled, the server will send the compressed response in Brotli format if the client supports it. If the client is older and does not support Brotli, the server will send the compressed response in Gzip format .

---

<br>

##### Setup Cloudflare Compression:
1. Log in to your Cloudflare account.
2. To Enable brotli, gzip, or both brotli and gzip compression or compression for your Business plan:
   > A. Click on the Speed tab.
   > B. Under Optimization, click on Content Optimization.
   > C. For both Brotli and Gzip, toggle the switch to On.
---

<br>

#### CLoudflare CDNJS