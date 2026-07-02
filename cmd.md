|linux|powershell|windowscmd|
|:--:|:--:|:--:|
|clear||cls|
|cd|
|pwd||cd|
|code|
|open|start|start|
|.|
|..|
|/|
|~|
||
|mkdir|
|rmdir|
|ls||dir|
||
|touch|ni|type nul >|
|rm||del|
|cat|cat|type|
||
|cp|
|mv|
|sudo|

#### vim
|op|shell|
|:--:|:--:|
|EditMode|i|
|NormalMode|esc|
|CtrlMode|:|
|Save|:w|
|Exit|:q /:q!|
|S&E|:wq /:x|

#### Nginx
Ubuntu@IP
**install**
1. sudo apt update
2. sudo apt install nginx -y
3. systemctl status nginx

**setting**
1. ./etc/nginx/sites-available/default
2. ./var/www/html/index.nginx-debian.html
3. sudo vim