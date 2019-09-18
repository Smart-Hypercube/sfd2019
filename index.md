---
title: 开源密码管理器 KeePass
template: default
---
.title[开源密码管理器 KeePass]
.author[王子博]
.footnote[
  [源文件](https://github.com/Smart-Hypercube/sfd2019)
  [幻灯片](https://0x01.me/sfd2019/)
  [寻找存档](https://lug.ustc.edu.cn/)
]



---
# 土制密码管理方案

--
## 处处使用同一个密码：`HyperCube!`

--
- 能被不良小网站直接获取，一旦泄漏，危及所有账号

--
- 密码格式要求不同，不得不记住许多变种：`HyperCube!1` `HyperCube` `12345678`


--
## 基于账号简称生成密码：`HyperCube-QQ`

--
- 能避免机器人用泄漏的密码自动登录其他账号，但仍然会被聪明的人一眼看穿

--
- 容易记不清每个账号的简称

--
- 仍然需要许多变种来适应不同的格式


--
## 基于账号简称、密码格式、哈希算法生成密码
`sha1('HyperCube-QQ') -> f9f69625173740cf9c3df633...`  
如果要求 8 位任意：`f9f69625`  
如果要求 8 位数字：`96962517`

--
- 登录界面不一定会显示密码格式要求



---
# 其他密码管理需求

--
- 易于在各种设备和环境使用

--
- 记录自己有哪些账号

--
- 按计划定期更换所有密码

--
- 记录由他人创建或与他人共享的密码

--
- 易于将所有账号的最新密码传给继承人


--
## 密码管理方案必须存储任意设置的密码
（而不能仅仅用规则生成密码）


--
## 为什么密码管理器能提高你的账号安全性？
???
虽然一个主密码解锁所有密码，但这个主密码可以非常复杂，并且从来没交给不可信的人

密码管理器使得每个账号都使用随机密码、定期更换成为可能

与其把密码写在纸上，密码管理器更方便使用，使用时也更安全



---
# 主流密码管理器

## [KeePass](https://keepass.info/)
- 自由软件
- 在本地存储数据，可以配置云同步

## [1Password](https://1password.com/)
- 专有软件
- 每月 3～5 美元
- 在本地存储数据，可以配置云同步

## [dashlane](https://www.dashlane.com/)
- 专有软件
- 每月 0～10 美元
- 在本地存储数据，可以配置云同步

## [LastPass](https://lastpass.com/)
- 专有软件
- 每月 0～3 美元
- 在云端存储数据

## […](https://en.wikipedia.org/wiki/List_of_password_managers)



---
# 演示
???
-   主密钥
    -   可以用多种组合
    -   警告：丢失后无法恢复
-   分组
-   自动生成密码
    -   强度指示器
-   自动输入
    -   该怎么配置好自动输入——设置是否可以自动输入（可继承）、规则、匹配窗口名/URL 的规则



---
# 设计

--
## 只靠密码学算法保证数据库安全
- 单文件数据库 + 加密保存
- 手工指定合适的主密钥迭代次数
- 主密钥不设尝试次数上限
- 可以随意分发加密后的数据库来备份


--
## 利用多种方法保证读写过程安全
- 内存加密、禁止换页、退出前擦除
- 在安全桌面和安全控件中输入密码
- 双通道自动填写密码
- 使用不同来源的熵自动生成密码


--
## 不防御针对性间谍软件
如果电脑上有针对 KeePass 的间谍软件，它甚至可以用自己换掉 KeePass，此时 KeePass 无法进行任何防御！



---
# 跨平台使用

--
## Mono（Debian: `keepass2`）
- 通过 Mono 工具可以在 Linux 各大发行版上运行 KeePass 官方版本
- 与操作系统集成不佳


--
## [KeePassXC](https://keepassxc.org/)（Debian: `keepassxc`）
- 非官方，原生支持 Linux，与操作系统集成良好
- 砍掉了一些复杂的功能，如插件、触发器、自动同步等
- 我的选择


--
## [KeePassDroid](http://www.keepassdroid.com/)（F-Droid: [`com.android.keepass`](https://f-droid.org/packages/com.android.keepass/)）
- 非官方的安卓客户端
- 只能用剪贴板输入密码
- 界面和功能简陋


--
## [Keepass2Android](https://github.com/PhilippC/keepass2android)（未上架 F-Droid）
- 非官方的安卓客户端
- 通过提供一个输入法来自动填写密码
- Material Design


--
## […](https://keepass.info/download.html)



---
# 高级功能

--
- 通过浏览器插件自动填写密码

--
- 作为 SSH Agent 自动填写密码

--
- 一次性密码和两步验证码

--
- 插件

--
- 触发器

--
- 字段引用



---
# 不足

--
- 无法多用户使用
???
建议创建一个组专门存储和别人共享的密码，以防管理自己的账号时不小心影响到

--
- 无法分级解锁
???
在不信任的设备上没法用

一旦泄漏需要全部修改

注意泄漏后的正确应对策略



---
# 分享两个工具

--
## [onetimesecret.com](https://onetimesecret.com/)
阅后即焚的密码发送渠道

--
## [haveibeenpwned.com](https://haveibeenpwned.com/)
检查自己的账号和密码是否泄漏



---

.title[谢谢大家]
