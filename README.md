# 雀魂MAX

雀魂解锁全角色、皮肤、装扮等，基于[mitmproxy](https://github.com/mitmproxy/mitmproxy)的中间人攻击方式，支持网页版和客户端/Steam端。

同时支持将雀魂的牌局发到[日本麻将助手mahjong-helper](https://github.com/EndlessCheng/mahjong-helper)，不支持牌谱分析。

本工具完全免费、开源，如果您为此付费，说明您被骗了！

#### 🧭当前雀魂各服版本（实时更新）  

![CHINESE](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fgame.maj-soul.com%2F1%2Fversion.json&label=CHINESE&query=$.version&color=FF8C00&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAACXBIWXMAAA7EAAAOxAGVKw4bAAACsklEQVQ4ja2Tf0zMcRjHX9/7Ud0l59RCFssWmemGom5mNysbLb+GuM2G8mOMCGu0rD9aNuRHymxnNqbGqcwMG1lrRLmkRXOESoit311X1/34+MO37YY/vf96Pu89z+f5fJ73+5H4G1nAWWAPkAzoZL4LeAiU+SdLfrESKAZOAzeAVpl3AiogABgD5gImwPNn5yYgDngAXANKgZbbFw+J+jsnBdAJvA8KUNnNqUYBaP2LrwFXgQrAAtjmzAwfFG23RHtNkUhNinMaYiJ7gI6c3SkeoA4Q/l+oAdqB/mPpSVsLTu3US6FpXwDF9nVL9RmbVwSHaCTcPiV5xZUj96oaPsp1lSpg/vSwENdhc+KGyHCdtmvIKxYkZA51PyucUf36Kxv3n+uKmBqqWGVapPGM9JG5KUFzr6ohWJ7NAQnIBmI1geoge/mh9f29fdR+HPZGTZ2kmBwRKRmiI3jywi6Mi2ZL+oXbPztsRbOiV+b2dnUPdAIxKmBKmE4b8qgwLZUxF0XWl+4Rj9LF4hiNVxGkvPGuQxgXRkt371f7ANWrNx84l71Jv/mopRMYVAE/50TqjZ9+OCi50+i+cnytOj79yvDwqMtRaUnR2Vvs0r7cy85qW2s3oG77Nugzxc1UAG5gIrJ0pUBFaU6KAL5PC9P1lOWbReaWZaOXcs2eoaarwmErEsD36yczPG+tBwXQCAyMy/gcsALNQFNZvlkAn0ae5ouHJXt98fOi+svPZIhtqxOd9ttZotayS8hS5qnkC6xALBBoWhA1wdnf7QUCghRuQrWSlGQI11Q+fuk4f2TNhJp6OxesdX3AEiDB30x1QEvBjqVe+XnNQGN6imFsoOqEuHlijVApFe2ATbZxqL+RxmEBlgOjgE/mBOAC1PLZAIz74J9IloczCgzLcScwxO8N/b/4BZ4sCAP6Ouu4AAAAAElFTkSuQmCC&logoWidth=16) ![ENGLISH](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fmahjongsoul.game.yo-star.com%2Fversion.json&label=ENGLISH&query=$.version&color=FF8C00&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAACXBIWXMAAA7EAAAOxAGVKw4bAAADT0lEQVQ4jUXN2WtcVQDA4d+520xmsbOkM5OYNJkak5hJNQtE2mCgkj6ILUVEoTSIG0KVgpT4oIjig4qi5k0U8cWttr5IoUGoFBrRSilN1DRdNBMbkzTNNklmJplz7tx7fPDB7x/4BMDJZ0/kDw4fznquj1/1AM3Ia5/hyQpVDQDzi7OkExl2ptLUJOKcuzbO2V8vCOv1x+s/MKans3LuIyIdRynd0ly7uoTcKpPt7mN2coKqlLRm2/B8jTYExcIa+1v28Ol7J7TIf9hRCaVigfDunQR2JHA3lxl+qYxhaBKpDCuLC3QPPgJas3j9KoZpQjhMOl1H+K4Y1sJs0agrCUztM/zxGMeH2gjYEaSSzM3O4FgO4+dGEQLC4Si1u5qRrqK0WUQrhTW3IrmnM45lC159vp1kMoowobauntvzc9i2hVKKUDiMcl0W/84jXUm5JowhQIzk7leTRW0fGfA4m0/QfsegIRpgNKDJZOqZmvmdvs5u1gvbuK6ivFXGlRLbMBGAtb5hkAraXPzRZSkh6acGUXbZdMu8eWyIny63MDVxk3+W5onVxHBxaWxuZGlhhYrcRjzduU/llGl3KY0SJnlHcysTx/VW+eP6DZoMh0LI4eT571GywtTYz1y8fIWp8VlCdg1W0AkS3VYULJMzVolUIkMgaPHOyLv8cPo8k59/SeqhfRTXitS2t/DgkQYSjfWE1Rl+ufIXljAMqgEHp1RBahfTsdHKRxgWj77wBLmeNpr2H0AIF9Bow+C7T74l29fL1tgkVkVJNu7OMDjQT/TUN6B9TMNEBwJQkTQ/cB+itASRHSAEIGgtbhOrzbArlUYcasqpunjSLhTXiIaieNojFkvSmmvj2NvHwXbAMEEDAnTVhdI6zww+RyaewPJ9g9urKwRtC9NyuLO6zuDe3RSki7YCCK1B6/92IRCmBaEohmUQb85iKe2vVIqbdenaDOubCoFg8OWnyJ8eRXo+QeGDAIQBmOAp3nrxDfDgz/wMAuDeUFL31LewXZGEgkFeOfoYyT2NLE/cxGpvpuvQAbTvUcXgyd6H0VWH3q5+Jm78tiH431pnvCGeSzZxsKODvQM9mKEwSkne/+Ir5pYXiVgRpCoSCcY4NX3paw1D/wJx5WDqjkxa0wAAAABJRU5ErkJggg==&logoWidth=16) ![JAPANESE](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fgame.mahjongsoul.com%2Fversion.json&label=JAPANESE&query=$.version&color=FF8C00&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAACXBIWXMAAA7EAAAOxAGVKw4bAAADT0lEQVQ4jUXN2WtcVQDA4d+520xmsbOkM5OYNJkak5hJNQtE2mCgkj6ILUVEoTSIG0KVgpT4oIjig4qi5k0U8cWttr5IoUGoFBrRSilN1DRdNBMbkzTNNklmJplz7tx7fPDB7x/4BMDJZ0/kDw4fznquj1/1AM3Ia5/hyQpVDQDzi7OkExl2ptLUJOKcuzbO2V8vCOv1x+s/MKans3LuIyIdRynd0ly7uoTcKpPt7mN2coKqlLRm2/B8jTYExcIa+1v28Ol7J7TIf9hRCaVigfDunQR2JHA3lxl+qYxhaBKpDCuLC3QPPgJas3j9KoZpQjhMOl1H+K4Y1sJs0agrCUztM/zxGMeH2gjYEaSSzM3O4FgO4+dGEQLC4Si1u5qRrqK0WUQrhTW3IrmnM45lC159vp1kMoowobauntvzc9i2hVKKUDiMcl0W/84jXUm5JowhQIzk7leTRW0fGfA4m0/QfsegIRpgNKDJZOqZmvmdvs5u1gvbuK6ivFXGlRLbMBGAtb5hkAraXPzRZSkh6acGUXbZdMu8eWyIny63MDVxk3+W5onVxHBxaWxuZGlhhYrcRjzduU/llGl3KY0SJnlHcysTx/VW+eP6DZoMh0LI4eT571GywtTYz1y8fIWp8VlCdg1W0AkS3VYULJMzVolUIkMgaPHOyLv8cPo8k59/SeqhfRTXitS2t/DgkQYSjfWE1Rl+ufIXljAMqgEHp1RBahfTsdHKRxgWj77wBLmeNpr2H0AIF9Bow+C7T74l29fL1tgkVkVJNu7OMDjQT/TUN6B9TMNEBwJQkTQ/cB+itASRHSAEIGgtbhOrzbArlUYcasqpunjSLhTXiIaieNojFkvSmmvj2NvHwXbAMEEDAnTVhdI6zww+RyaewPJ9g9urKwRtC9NyuLO6zuDe3RSki7YCCK1B6/92IRCmBaEohmUQb85iKe2vVIqbdenaDOubCoFg8OWnyJ8eRXo+QeGDAIQBmOAp3nrxDfDgz/wMAuDeUFL31LewXZGEgkFeOfoYyT2NLE/cxGpvpuvQAbTvUcXgyd6H0VWH3q5+Jm78tiH431pnvCGeSzZxsKODvQM9mKEwSkne/+Ir5pYXiVgRpCoSCcY4NX3paw1D/wJx5WDqjkxa0wAAAABJRU5ErkJggg==&logoWidth=16)  

## 📢用前须知

> 注意：解锁人物仅在本地有效，别人还是只能看到你原来的角色，发表情也是原来角色的表情。<br />比如使用新角色发第3个表情，实际上其他人看到的是原来角色的第3个表情。  

> 魔改千万条，安全第一条。<br />使用不规范，账号两行泪。<br />本插件仅供学习参考交流，请使用者于下载24小时内自行删除，不得用于商业用途，否则后果自负。<br />本插件仅供学习参考交流，请使用者于下载24小时内自行删除，不得用于商业用途，否则后果自负。<br />本插件仅供学习参考交流，请使用者于下载24小时内自行删除，不得用于商业用途，否则后果自负。  

> 警告：<br />雀魂游戏官方可能会检测并封号！<br />如产生任何后果与作者无关！<br />使用本脚本则表示同意此条款！  

![放铳放铳](https://memeprod.ap-south-1.linodeobjects.com/user-gif-post/1647655593730.gif)  

### ✈️Telegram频道&交流群

[![频道 https://t.me/Mahjong_Soul](https://s2.loli.net/2022/11/08/4vS2BLMGhudkXQy.jpg)](https://t.me/Mahjong_Soul)[![交流 https://t.me/Mahjong_Soul_Chat](https://s2.loli.net/2022/11/08/KL8A7U9fDsZEmjp.jpg)](https://t.me/Mahjong_Soul_Chat)

可以直接点击图片进入，也可以通过扫码进入。

### ☕请作者喝咖啡

[点我为作者发电（爱发电，支持微信/支付宝）](https://afdian.net/a/Avenshy)

[点我为作者发电（Patreon，支持信用卡/Paypal）](https://patreon.com/Avenshy)

再次重申：本程序完全免费使用，没有收费功能，请喝咖啡完全自愿，作者非常感谢您！

## 🥰当前功能

程序包含两部分：`mod`和`helper`，可以说是[雀魂mod_plus](https://github.com/Avenshy/majsoul_mod_plus)和[mahjong-helper-majsoul-mitmproxy](https://github.com/Avenshy/mahjong-helper-majsoul-mitmproxy)的融合。

程序默认配置为启用`mod`、禁用`helper`。如需自定义，请修改`.\config\settings.yaml`中的`plugin_enable`。

### `mod`功能

- 解锁所有角色与皮肤
- 解锁所有装扮
- 解锁所有语音（报菜名）
- 解锁所有称号
- 解锁所有加载CG
- 解锁所有表情（不推荐开启）
- 强制启用便捷提示
  - 由于雀魂本身代码限制，王座无法正常启用便捷提示，因此，**开启此功能后进入王座对局，左上角会变成“玉之间”**。请注意，这不是BUG！
- 支持星标角色
- 自定义名称
- 显示玩家所在服务器
- 显示主播/Pro标识
- TODO……

### `helper`功能

- 将对局发送到[mahjong-helper（雀魂小助手）](https://github.com/EndlessCheng/mahjong-helper)
  
### 打开一个cmd界面，执行命令

> 需要打开多个cmd界面时，bat文件中添加多行就行。

```start cmd /k “命令”```

#### 一个cmd界面执行多个命令

1. 以“&”隔开多个命令，不管前面的命令是否成功，后面的都会执行：
   ```start cmd /k  "命令1 & 命令2 & 命令3"```
1. 以“&&”隔开多个命令，前面命令执行成功时，后面才会执行：
   ```start cmd /k  "命令1 && 命令2 && 命令3"```
1. 以“||”隔开多个命令，前面命令执行失败时，后面才会执行：
   ```start cmd /k  "命令1 || 命令2 || 命令3"```

### 更简单的新使用方法

1. **要下载Proxy SwitchyOmega浏览器插件**
1. 设置代理模式将网页流量代理到 ```http://127.0.0.1:23410``` , 使用全皮肤程序前先选择设定好的代理模式
1. 全选并复制 ```._用txt里面的命令启动_要把所有edge关了才能用.txt``` 文件里的所有命令
1. 打开cmd粘贴即可
1. mahjong-helper的**源代码**在./mahjong-helper-src文件夹里面
1. ~~默认不能使用代理科学上网，要用代理科学上网[见Q&A🤔](#qa)~~

### 新使用方法

1. **要把所有edge关了才能用**，先把edge所有页面关掉，把edge后台进程也都杀掉，再从快捷方式启动，如果正常的话应该能看到一行字“你使用的是不受支持的命令行标志……”，这样就是成功了。[见Q&A🤔](#qa)
1. 全选并复制 ```._用txt里面的命令启动_要把所有edge关了才能用.txt``` 文件里的所有命令
1. 打开cmd粘贴即可
1. mahjong-helper的**源代码**在./mahjong-helper-src文件夹里面
1. ~~默认不能使用代理科学上网，要用代理科学上网[见Q&A🤔](#qa)~~

## 🧐使用说明

### 视频教程

[雀魂MAX使用教程，2分钟解锁所有角色皮肤装扮等](https://www.bilibili.com/video/BV12F4m1w7d9/)

### 文字教程

1. 启动程序
    - 方式1（懒人模式）：在[Releases](https://github.com/Avenshy/MajsoulMax/releases/latest)里下载，解压后直接运行`run.exe`（Windows限定）
    - 方式2（源码运行）：通过`git clone`或其他方式下载源码到本地，在`Python>=3.10`环境下，打开命令行，在当前目录运行`mitmdump -p 23410 -s addons.py`启动程序（首次运行需`pip install -r requirements.txt`安装依赖）
1. 关闭程序，修改配置
    - 根据程序提示和自身需求修改
1. 需要安装mitmproxy证书，访问mitm.it下载并安装证书 或 google搜索：mitmproxy 安装证书 或 用[Akagi项目](https://github.com/shinkuan/Akagi/tree/main)的懒人包安装证书
1. 再次启动程序
1. 启动游戏，分为网页版和客户端/Steam端。
    - 如果要启动网页版：（限`Chrome`/`Edge`）
       - 在浏览器中禁用所有雀魂相关插件和脚本，**彻底禁用或卸载**代理相关插件（如`Proxy SwitchyOmega`）
       - 使用浏览器正常进入游戏一次
       - 关闭所有浏览器窗口，用任务管理器查看后台确保无进程残留
       - 将Chrome或者Edge的快捷方式 `复制->粘贴` 出现一个副本，对快捷方式副本 `右键->属性->目标` 的后面按一个空格后添加`--proxy-server=127.0.0.1:23410 --ignore-certificate-errors https://game.maj-soul.com/1/` （如果要玩其他服务器则修改对应网址）
    - 如果要启动客户端/Steam端：
       - 启动到登录界面，不要登录
       - 如果已经自动登录进入，点击游戏右上角设置登出账号，回到登录界面
       - 运行[Proxifier](https://www.proxifier.com/)并配置
          - `Profile` > `Proxy Servers` > `Add`
          - `Address`: `127.0.0.1`
          - `Port`: `23410`
          - `Protocol`: `HTTPS`
          - 填写完后点击Check，确保看到`Test 1`下显示绿色的`Test passed`，其他的不用管
          - `OK`
       - `Profile` > `Proxification Rules` > `Add`
          - `Name`: 随便起个名字
          - `Enabled`: ✅
          - `Applications`: 根据你运行游戏的应用填写，例如Steam客户端填写`jantama_mahjongsoul.exe`
          - `Action`: `Proxy HTTPS 127.0.0.1`
          - `OK`
1. 登录游戏开始享受

## 🤔Q&A

1. 为什么要自动更新liqi和lqc.lqbin？更新失败有什么影响？
    - liqi：
       - 共有3个文件，包括`liqi.json`和根据其生成的`liqi.proto`和`liqi.pb2.py`，用于解析雀魂protobuf消息
       - 如果更新失败，可能会导致消息无法解析（如新活动的消息）
    - lqc.lqbin：
       - 用于获取全部角色、装扮、物品等游戏资源
       - 如果更新失败，可能会导致无法获取新资源（如新角色、物品等）
    - 如果自动更新失败，可以在[AutoLiqi > Releases](https://github.com/Avenshy/AutoLiqi/releases/latest)下载，并手动替换`./proto`文件夹下的同名文件
2. 还有其它问题？
   在上方加入我们的[Telegram群](https://github.com/Avenshy/MajsoulMax?tab=readme-ov-file#%EF%B8%8Ftelegram%E9%A2%91%E9%81%93%E4%BA%A4%E6%B5%81%E7%BE%A4)
1. 为什么启动浏览器之后没有效果？
   - 关闭所有浏览器窗口后再启动带参数的浏览器。
2. 进不去游戏？
   - 先使用浏览器进入游戏一次，关闭后再启动带参数的浏览器。
   - 如果你正在使用代理，很可能是因为代理被覆盖而导致无法进入游戏，请看下一条。
3. 代理被覆盖了，不能使用梯子了怎么办？
   - 使用[Clash](https://github.com/Fndroid/clash_for_windows_pkg)的TUN模式
   - 或者在`mitmproxy`的启动参数中设置前置代理。例如，Clash默认端口为7890，则启动参数为：<br />`mitmdump -p 23410 -s addons.py --mode upstream:http://127.0.0.1:7890`
4. 看不懂怎么办？出现错误怎么解决？出现其它问题？
   - [提issue](https://github.com/Avenshy/mahjong-helper-majsoul-mitmproxy/issues)或者[加群](https://github.com/Avenshy/mahjong-helper-majsoul-mitmproxy#telegram%E9%A2%91%E9%81%93%E4%BA%A4%E6%B5%81%E7%BE%A4)！
5. 为什么不使用selenium之类的浏览器自动化，省去配置浏览器的麻烦？
   - 浏览器自动化的特征太多，极易被识别。为了雀魂的账号安全，不建议使用此方式。
6. 只支持浏览器吗？
   - 当然不是，也支持客户端和Steam！使用[Proxifier](https://www.proxifier.com/)或类似软件指向`127.0.0.1:23410`即可！
