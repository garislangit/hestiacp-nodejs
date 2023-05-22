# hestiacp-nodejs
Running nodejs application in Hestia Control Panel or how to enable NodeJS support in hestia control panel. 

Note : i am unable to run via sock mode (app.sock not created) however port mode (3000) is worked

# Requirements
Install PM2 npm i pm2@latest -g

Install NVM see [https://nvm.sh]

# Installations

Do the following steps in order to work :
1) Clone this repository
2) Copy those files (except app.js) to the directory /usr/local/hestia/data/templates/web/nginx/
3) Open your hestiacp control panel, edit the website configuration setting that you are going to use as nodejs hosting, and choose NodeJs3000 for Proxy Template field
4) upload app.js file to the directory /home/admin/web/your-website-address/nodeapp 
5) Open your website address, you should see the output from your node js application otherwise check the log files

# Example Testing script (app.js)
<code>
var http = require("http");
http.createServer(function (request, response) {
   // Send the HTTP header 
   // HTTP Status: 200 : OK
   // Content Type: text/plain
   response.writeHead(200, {'Content-Type': 'text/plain'});
   
   // Send the response body as "Hello World"
   response.end('Hello World\n');
}).listen(3000);
</code>

# Reference 
https://help.clouding.io/hc/es/articles/360016993480-C%C3%B3mo-usar-Node-js-en-HestiaCP
