>这次是修改一台不知道密码的服务器的root用户的密码

## 开机在启动菜单按“e”，进入编辑模式
![b272d70039581e3c9120a3190f70543e.png](../assets/images/quote/2022-09-02-modify-root-password/Image.png)

## 在里面找到 "ro"  将 "ro" 修改为 " rw init=/sysroot/bin/bash "；
![54b3db47f653fd0f0f7c31c316b09ebf.png](../assets/images/quote/2022-09-02-modify-root-password/Image[1].png)

修改后的内容如下：
![ba61769460f285e06bd0e34238c9094d.png](../assets/images/quote/2022-09-02-modify-root-password/Image[2].png)
## 修改完成之后，同时按下 " ctrl + x "，进入单用户模式；
![185b30cbc66f60de25e3675ab569cb1f.png](../assets/images/quote/2022-09-02-modify-root-password/Image[3].png)

## /sysroot &quot; 命令进入系统；
![ed39ba2673a00c300d87371cdf529f10.png](../assets/images/quote/2022-09-02-modify-root-password/Image[4].png)

## 在终端上输入 passwd root  重置root密码;
![de790110350ff2c666b16a6489cd2708.png](../assets/images/quote/2022-09-02-modify-root-password/Image[5].png)

## 用  touch /.autorelabel 更新SELinux信息;
![c102fc9b1bedb438da614022382c5dd3.png](../assets/images/quote/2022-09-02-modify-root-password/Image[6].png)

> 我这里试了很多次只能关闭selinux才能重启成功
vi /etc/selinux/config
修改
SELINUX=disabled

## 输入 exit 退出 chroot ;
![7577a503d206441d96b8320eca811582.png](../assets/images/quote/2022-09-02-modify-root-password/Image[7].png)

## 用 reboot -f 重启系统，用新密码登录验证；
![5f68e5c28b7567eac830e2314e93c3eb.png](../assets/images/quote/2022-09-02-modify-root-password/Image[8].png)

>如果上面是关闭了selinux，这里直接reboot即可

至此修改完成root密码，系统完美登录。^_^
![dd122d8dae3b4a176339081bd6750e7c.png](../assets/images/quote/2022-09-02-modify-root-password/Image[9].png)
