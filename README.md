# Parallels-Desktop-Crack
cracked pd version 18.0.2-53077
破解方法来自github上一个大佬 somebasj 521（github已和谐）somebasj备用 58,全面支持intel和arm芯片(M1&M2)

准备工作
下载PD并安装
https://download.parallels.com/desktop/v18/18.0.2-53077/ParallelsDesktop-18.0.2-53077.dmg 279
来源：PD官网

ParallelsDesktop-18.0.2.dmg 739
来源：百度网盘 | 提取码：lfbn

下载破解补丁
ParallelsDesktopCrack-18.0.2.zip 521
来源：GitHub | github地址已封

ParallelsDesktopCrack-18.0.2.zip 739
来源：百度网盘 | 提取码：lfbn

ParallelsDesktopCrack-18.0.2.zip 221
来源：资源潭 | 阿里网盘直链下载

激活方式1自动
下载破解补丁后解压，然后cd进入解压后的目录，然后执行

chmod +x ./install.sh && sudo ./install.sh

ps：执行该命令会需要输入密码以授权。

激活方式2手动
如果安装过pd17或者更早版本，可以完全卸载以确保之后能成功激活。（可选，不卸载也行，不过可能会有坑）
建议使用 App Cleaner 来卸载，这样卸载的比较干净
ps：卸载之前请先备份好自己的虚拟机，不然卸载完就啥都没了，虚拟机文件存放目录为 ~/Parallels。

下载pd18安装文件，安装，安装之后到激活那一步就不用继续走了，退出pd。

下载破解补丁到 下载目录 ，也就是 ~/Downloads, 然后解压缩，不要修改解压后的文件夹名称，这样操作都是为了保障后续执行脚本路径正确。

打开终端，开始执行命令破解

进入破解补丁的目录
cd ~/Downloads/ParallelsDesktopCrack-main
杀掉pd的进程
 killall -9 prl_client_app
 killall -9 prl_disp_service
复制破解补丁文件到pd目录 (执行命令时提示要输入密码的话就输入自己电脑的密码然后回车)
sudo cp -f prl_disp_service "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
sudo chown root:wheel "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
sudo chmod 755 "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
复制licenses
sudo cp -f licenses.json "/Library/Preferences/Parallels/licenses.json"
sudo chown root:wheel "/Library/Preferences/Parallels/licenses.json"
sudo chmod 444 "/Library/Preferences/Parallels/licenses.json"
sudo chflags uchg "/Library/Preferences/Parallels/licenses.json"
sudo chflags schg "/Library/Preferences/Parallels/licenses.json"
重新签名
sudo codesign -f -s - --timestamp=none --all-architectures --entitlements ParallelsService.entitlements "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
配置host屏蔽pd检测（以防万一）
补丁作者原话：

Parallels Desktop may upload client info or logs to server.
You can use a firewall block there domains.
Or use Hosts, AdGuardHome filter DNS resolve.

大概就是说pd服务器可能会检测你本地的pd状态，最好使用防火墙屏蔽掉pd的检测，以防哪天破解失效。

编辑host文件

sudo vim /etc/hosts

在文件最后面加上以下配置

127.0.0.1 download.parallels.com
127.0.0.1 update.parallels.com
127.0.0.1 desktop.parallels.com
127.0.0.1 download.parallels.com.cdn.cloudflare.net
127.0.0.1 update.parallels.com.cdn.cloudflare.net
127.0.0.1 desktop.parallels.com.cdn.cloudflare.net
127.0.0.1 www.parallels.cn
127.0.0.1 www.parallels.com
127.0.0.1 reportus.parallels.com
127.0.0.1 parallels.com
127.0.0.1 parallels.cn
127.0.0.1 pax-manager.myparallels.com
127.0.0.1 myparallels.com
127.0.0.1 my.parallels.com
然后 esc + :wq 保存修改即可

PD会自动修改hosts文件，可以用命令行锁定hosts文件

sudo chflags uchg /etc/hosts
sudo chflags schg /etc/hosts
激活出错的情况
有一些朋友激活时遇到无权限的问题，我这边始终没法复现，不过遇到报错之后可以尝试一下以下方案

文件赋予最高的权限
#如果当前目录不是破解补丁所在目录，则需要先cd进入破解补丁所在目录，比如  
cd ~/Downloads/ParallelsDesktopCrack-main
chmod 777 *
给予终端全盘访问权限
设置-安全性与隐私-隐私-完全磁盘访问权限

这个里面勾上终端，没有的话点击左下角加号手动添加一下终端

效果展示

Usage
Install Parallels Desktop 18.0.2-53077.

https://download.parallels.com/desktop/v18/18.0.2-53077/ParallelsDesktop-18.0.2-53077.dmg

Exit parallels account.

Download this repo file.

Extract and run Terminal in this directory.

chmod +x ./install.sh && sudo ./install.sh
