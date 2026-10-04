# Linux

## 1. Command

#### 0. `help`

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
|`ls`|list `-a` `-l`|
|`cd [path]`|change directory -  . (cur) <br> .. (back) <br> / (root) <br> ~ (home)|
|`mkdir [dir name]`|make|
|`rmdir [dir name]`|remove|
|`touch [doc name]`|make|
|`rm [doc name]`|delete|
|`cat [doc name]`|read|
|`less [doc name]`|`[cmd 2>&1]\|less`scroll output <br> `q` quit|
|`vim [doc name]`|edit|
|`cp [src doc] [dist doc]`|copy|
|`mv [src doc] [dist doc]`|move / rename|
|`pwd`|path|
|`code`|vscode|
|`open`|html|
|`clear`||

#### 4. Compile & Run C
|cmd|note|
|:-:|:-:|
|**Stage**|
|`gcc -E hello.c -o hello.i` (`-E` Preprocessing) <br> `gcc -S hello.c -o hello.s` (`-S` Compilation) <br> `gcc -c hello.c -o hello.o` (`-c` Assembly) <br> `gcc hello.c -o hello` (Linking)| `gcc [src1] [src2] ... -o [out]` (`-c .c``.o -o`in a way) <br> `-E/-S/-c [src]` (out file stage) <br> `-o [out]` (out file name)|
|`./[out]`|run|
|**Insert**|`gcc -Wall -g -c hello.c`|
|`-g`|debug info|
|`-Wall`|warning|

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

1. **Configure:** VitualBox - Ubuntu ISO (CD drive) - Install
2. **Test**

|content|cmd|
|:-:|:-:|
|**Network**|`ping -c 4 baidu.com`|
|**SystemUpdate**|`sudo apt update` <br> `sudo apt upgrade -y`|
|**InstallTool**|`sudo apt install [tool name] -y` <br> `build-esstential` (compile) <br> `gdb valgrind` (debug) <br> `vim ` (edit) <br> `make` (auto build)|
|**Verify**|`gcc --version` <br> `g++ --version` <br> `make --version`|

## 3. Vim

|op|shell|
|:--:|:--:|
|EditMode|`i`|
|SearchMode|`/`|
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

* **Page Configure**

1. **default** `etc/nginx/sites-available/default` -- `var/www/html/index.nginx-debian.html`
2. **web addr (IP + port + doc)**: http://127.0.0.1:8080
3. **personal configure**: `sudo vim /etc/nginx/sites-enabled/default`: `root /var/www/html` -- `root /home/[user dir]/[new dir]`
4. **reload**: `sudo nginx -t`, `sudo systemctl reload nginx`
5. **permission**: `sudo chmod o+x /home/[name]`

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
|`git clone git@github.com:[name]/[repo name].git`|**clone** to server|
|`git pull`||
|`git checkout`|discard not committed|

## 6. Make
* **Rule Edit**

**1. base** 
```
# Makefile
exe:src1.c src2.c header.h
    gcc src1.c src2.c -o exe
```
**2. template**

```
# Makefile
# Configure Field (Modify)
CC = gcc                # compiler
CFLAGS = -Wall -g       # warning + debug
TARGETS = main child     # out files name
HEADERS = common.h      # pulic header file
MAIN_EXE = main         # run file

# Rule Field (Tab)
.PHONY: all clean run

all: $(TARGETS)         #default dest

%: %.c $(HEADERS)		# `make (xxxx)`
    $(CC) $(CFLAGS) $< -o $@

clean:
    rm -f $(TARGETS)

run: all
    ./$(MAIN_EXE)
```

* **Pack Build**

|cmd (defined)|op|
|:-:|:-:|
|`make`|compile all|
|`make clean`|clean all|
|`make run`|run all|
|`make [out]`|run one|

## 7. tmux

* **Enter** `Ctrl + B`

|op|cmd|
|:-:|:-:|
|horizontal|`%`|
|vertical|`"`|
|switch window|`[arrow key]`|
|close|`exit`|

## 8. mysql

**link DB:** mysql -u[username] -p[password] (-h127.0.0.1)

### 8.1 database
|op|code|
|:-:|:-:|
|create|`create database [DB name]`|
|check|`show databases`|
|locate|`use [DB name]`|

### 8.2 table

**CRUD**

|op|code|note|
|:-:|:-:|:-:|
|**table**|
|create|`create table [TB name] ([D name] [D type] [constraint], ...)`|`default charset=utf8`|
|constraint|`(constraint [PK name]) primary key ([D name])` <br> `unique` <br> `not null` <br> `default [val]` <br> `auto_increment` <br> `constraint [FK name] foreign key ([D name]) references [TB name] ([RK name])` <br> `check([D name] = [val1] or ...)`|append definition|
|index|`index [Idx name] (D name)`|create|
|check|`show tables`|
|read|`describe [TB name]` <br> `show create table [TB name] \G`|
|del table|`drop table [TB name]`|
|rename table|`alter table [TB name] rename [new name]`|
|**field (col) with alter**|
|change field def|`alter table [TB name] change [D name] [new name] [D type]`|
|modify field seq|`alter table [TB name] modify [D name] [new type] (first / after [RD name])`|
|add field|`alter table [TB name] add [D name] [D type] [constraint] (first / after [RD name])`|`add constraint [PK name] primary key (D name)`|
|del field|`alter table [TB name] drop [D name]`|
|del FK|`alter table [TB name] drop foreign key [FK name]`|
|constranint|`alter table [TB name] add constraint [C name] [C sentence]`|
|**row**|
|insert|`insert into [TB name]([D name1], ...) values(val1, ...), ...`|
|update|`update [TB name] set [D name1] = [val1], ...`|`where`|
|del row|`delete [alias] from [TB name] [alias]`|`where exists (select(select))`|
|del all|`truncate table [TB name]`|
|**view**|
|create|`create view [V name]([D name], ...) as select(table)`|
|del|`drop view [V name]`|
|**index**|
|create|`create (unique) index [Idx name] on [Tb name](D name1, ...)` <br> `alter table [TB name] add index / unique [Idx name](D name1, ...)`|`create table TB (id int(11) not null auto_increment, primary key(id))`|
|del|`drop index [Idx name] on [TB name]` <br> `alter table [Tb name] drop index [Idx name]`|
|read|`show index from [TB name]`|

###### `with tmp as(select)`

### 8.3 select

* **flow:** from / join - where - group by - aggregate func - having - select - order by - limit

```
select (distinct) [fields] as [alias]
from [tables] [alias]
[left / right / inner] join [tables] on [conds]
where [conds]
group by [fields - index]
having [conds]
order by [field] [asc / desc]
limit [offset], [row num]
(union (all) / intersect / except select)
```

|flag|code|
|:-:|:-:|
|**select**|
|`[field]`|`*` `[D name1], ...` `if([cond], '[name1]', [name2])` `[val]` `case`|
|`[table]`|`[TB name]` `(select)`|
|**subselect**|
|`[val]`|`select [aggregate func]`|
|`[col]`|`select [field]`|
|`[table]`|`select [field(s)]`|
|`[page]`|`select [id] from [table] where id >= (select [id] from [table] limit [offset], 1) order by id limit [row num];`|

|cond|note|
|:-:|:-:|
|`if` `ifnull` `case`|`if([cond], [v1], [v2])` - `[cond]?[v1]:[v2]` <br> `ifnull(a, b)` - `a != NULL?a:b` <br> `case when [cond1] then [v1], ..., else [vn] end`|
|`in` (or) <br> `between and` (range) <br> `like` <br> `is (not) null`|`in ([vals]: [val1], [val2], ...)` <br> `in ([cols]: [TB1].[D1], [TB1].[D2], ..)` <br> `like [% / _]`|
|`and` `or` `not`|
|`op: > < >= <= <> !=`|
|`all` `any`|`(not) ([op] / in) (all / any) [(col / set)]`|
|`exists`|`not exists (select 1 where not exists)`|

|func|note|
|:-:|:-:|
|**aggregate func**|
|`count`|`* / 1`, `if([cond], 1, null) / case`|
|`sum` `avg`|`* / [digit]`, `if([cond], [num], 0) / case`|
|`max` `min`|
|**string func**|
|`length`|`length('str')` - 3|
|`concat` <br> `concat_ws`|`concat(s1, s2, ...)` - s1 + s2 <br> `concat('f', 's1', 's2', ...)` - 's1-s2-...'|
|`left` <br> `right` <br> `substring`|`left('string', 3)` - 'str' <br> `right('string', 3)` - 'ing' <br> `substring('12345', 3, 5)` - '345' <br> `substring('12345', 3)` - '345' <br> `substring_index('11-22-33', '-', -1)` - '33'|
|`trim` <br> `ltrim` <br> `rtrim`|`trim(' 1 2 3 ')` - '1 2 3' <br> `ltrim(' 1 2 3 ')` - '1 2 3 ' <br> `rtrim(' 1 2 3 ')` - ' 1 2 3'|
|`replace`|`replace('123', '23', '')` - '1' <br> `replace('123', '23', '45') - '145'`|
|`lower` `upper`|
|**digital func**|
|`ceil` `floor` <br> `round` `truncate`|`round(3.1415, 3)` - 3.142 <br> `round(3.1415)` - 3 <br> `truncate(3.1415, 3)` - 3.141|
|`power` `sqrt` `abs`|
|`div` (c - `/`) <br> `mod` (c -`fmod`)|`3 / 4` - 0.75, `3 div 4` - 0 <br> `5 % 3` - 2, `5.2 % 3` - 2.2|
|**time func**|
|`now` `curdate` `curtime` <br> `year` `month` `week`|
|`date_add` <br> `datediff`|`date_add('xxxx-xx-xx', interval + / - n year / months / week / day)` <br> `datediff('2026-10-01', '2026-09-30')` - 1|
|`date_format('xxxx-xx-xx', %m / %d / %Y) - mm / dd / yyyy`|`%H %h %s %T`|

### 8.4 user

|op|code|
|create|`create user '[uname]'@'[IP]' identified by '[password]'`|
|del|`drop user '[uname]'@'[IP]'`|
|rename|`rename user '[uname]'@'[IP]' to '[new name]'@'[IP]'`|
|reset password|`set password for '[uname]'@'[IP]' = Password('[new password]')`|
|check grants|`show grants for '[uname]'@'[IP]'`|
|grant|`grant [all / select / insert / update]([D names]) on [DB].[TB] to '[uname]'@'[IP]' identified by '[password]'` <br> `flush privileges`|
|revoke|`revoke [list] on [DB].[TB] from '[uname]'@'[IP]'`|

**function**

```
delimiter // -- end flag
[global var]
create [function / procedure] [func name]([params name] [params type]) returns [ret type]
begin
    [var op]
    return [ret val]
end;
//
delimiter ;
```

|op|code|
|:-:|:-:|
|def global var|`set @g_user_var := init_val`|
|def local var|`declare [var name] [var type] (default [init val])`|
|create one line func|`create funcion [FN]([DN] [DT]) returns [RT] return [RV];`|
|del func|`drop function [FN]`|
|call|`call [proc name]`|
|check|`show procedure status where db = '[DB name]` <br> `show create procedure [DB name].[proc name]`|
|del proc|`drop procedure [DB name].[proc name]`|