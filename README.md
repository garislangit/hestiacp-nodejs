# hestiacp-nodejs
Running nodejs application in Hestia Control Panel or how to enable NodeJS support in hestia control panel. 

Note : i am unable to run via sock mode (app.sock is not created) however port mode (3000) is working

# Requirements
Install PM2 npm i pm2@latest -g

Install NVM see [https://nvm.sh]

# Installation

Do the following steps in order to work :
1) Clone this repository
2) Copy those files (except app.js) to the directory /usr/local/hestia/data/templates/web/nginx/
3) Give permission to shell script, chmod +x /usr/local/hestia/data/templates/web/nginx/nodejs3000.sh
4) Open your hestiacp control panel, edit the web domain setting , and choose NodeJs3000 for Proxy Template field
5) upload app.js file to the directory /home/admin/web/your-website-address/nodeapp 
6) Open your website address, you should see the output from your node js application otherwise check the log files . Make sure node service is listening on port 3000 (check via command netstat -nlp | grep 3000 )

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
