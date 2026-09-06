# Linux

## 1. Command

#### 1. SystemInfo
|cmd|note|
|:-:|:-:|
|`uname -a`|kernel|
|`lsb_release -a`|version|
|`df -h`|disk|
|`free -h`|memory|

#### 2. Software
|cmd|note|
|:-:|:-:|
|`sudo apt update`|app list|
|`sudo apt upgrade`|upgrade app|
|`sudo apt install [pack name]`|install|
|`sudo apt remove [pack name]`|uninstall|
|`apt search [key word]`||

#### 3. Document Operation
|cmd|note|
|:--:|:--:|
|`ls -a`|list|
|`cd [path]`|. (cur) <br> .. (back) <br> / (root) <br> ~ (home)|
|`mkdir [dir name]`|make|
|`rmdir [dir name]`|remove|
|`touch [doc name]`|make|
|`rm [doc name]`|delete|
|`cat [doc name]`|read|
|`vim [doc name]`|edit|
|`cp [src doc] [dist doc]`|copy|
|`mv [src doc] [dist doc]`|move / rename|
|`pwd`|path|
|`code`|vscode|
|`open`|html|
|`clear`||

#### 4. Compile & Run
|cmd|note|
|:-:|:-:|
|`gcc [src].c -o [out]`|compile|
|`./[out]`|run|
|`gcc -g [src].c -o [out]`|compile with debug|
|`gcc -wall [src].c -o [out]`|compile with warning|

#### 5. Process Management
|cmd|note|
|:-:|:-:|
|`ps anx`|read all|
|`ps -ef \| grep [process name]`|read specific|
|`kill PID`|terminate|
|`top`|realtime read|
|`jobs`|read back|
|Ctrl + Z|stop front|
|`bg`|to back|
|`fg`|to front|

## 2. Virtual Machine

1. **Configure:** VitualBox - Ubuntu ISO (CD drive) - Install Ubuntu
2. **Test**

|content|cmd|
|:-:|:-:|
|**Network**|`ping -c 4 baidu.com`|
|**SystemUpdate**|`sudo apt update` <br> `sudo apt upgrade -y`|
|**InstallTool**|`sudo apt install build-esstential -y` <br> `sudo apt install gdb valgrind -y` <br> `sudo apt install vim -y`|
|**verify**|`gcc --version` <br> `g++ --version` <br> `make --version`|

## 3. Vim

|op|shell|
|:--:|:--:|
|EditMode|`i`|
|NormalMode|`esc`|
|CtrlMode|`:`|
|Save|`:w`|
|Exit|`:q` /`:q!`|
|S&E|`:wq` /`:x`|

## 4. Nginx

* **Web Listen**

|cmd|note|
|:-:|:-:|
|`ssh Ubuntu@IP`|cloud server|
|`sudo apt update`||
|`sudo apt install nginx -y`|port 80|
|`sudo systemctl start nginx`|run|
|`sudo systemctl status nginx`||
|`sudo systemctl enable nginx`, `sudo systemctl disable nginx`|auto start|

* **Page**

1. etc/nginx/sites-available/default
2. var/www/html/index.nginx-debian.html
3. virtual machine: http://127.0.0.1:8080

## 5. Git

|cmd|note|
|:-:|:-:|
|**local**|
|`sudo apt install git -y`||
|`git config --global user.name [name]`<br>`git config --global user.email [email]`||
|`git init`|`cd [content]`, `.git`|
|`git status`||
|`git add [doc name]`|track, `git add .` for all|
|`git commit -m "description"`||
|`git log`||
|**remote**|**SSH:** `git@github.com:[name]/[repository name].git`|
|`ssh-keygen -t ed25519 -C [email]` (generate key) <br> `cat ~/.ssh/id_ed25519.pub` (public key)|**add ssh key**: GitHub - Settings - SSH and GPG keys - New SSH key|
|`ssh -T git@github.com`|**verify ssh** available|
|`git remote add origin git@github.com:[name]/[dir name].git` <br> `git remote -v`|**link** remote repo|
|`git branch`|branch name `main`/`master`|
|`git push -u origin [branch name]`|`-u` first time <br> **add - commit - push**|