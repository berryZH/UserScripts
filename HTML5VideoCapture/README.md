HTML5视频截图器
=========================

[脚本发布页](https://greasyfork.org/zh-CN/scripts/370819)

[个人脚本仓库](https://github.com/indefined/UserScripts)

[问题反馈到这里](https://github.com/indefined/UserScripts/issues)

**提交问题前请仔细读完说明和使用须知**

-------------------------
## 功能

- 检测网页中的HTML5视频
- 自动将所选中视频滚动到视野中
- HTML5视频控制(暂停/播放/步进)
- 视频截图(png格式原始视频画面)
- jpg截图压缩并自动下载(适用于部分视频和浏览器)

![功能界面](https://greasyfork.org/system/screenshots/screenshots/000/011/874/original/HTML5VideoCapture.capture.jpg)

## 使用说明
- 脚本启动
  方法1. 使用脚本管理器安装脚本，在脚本管理器按钮上点击‘启用HTML5视频截图器’打开工具栏
    - ![脚本启动](https://greasyfork.org/system/screenshots/screenshots/000/011/875/original/HTML5VideoCapture.TM.jpg) ![脚本启动](https://greasyfork.org/system/screenshots/screenshots/000/011/876/original/HTML5VideoCapture.VM.jpg)

  方法2. 复制下面代码保存为书签（可直接选中代码直接拖到书签栏），在需要使用的网页点击该书签打开工具栏
    - 仅适用于视频没有在嵌入框架中的一般网页，在一些不允许跨域调用的网页中会被拦截

  ```
  javascript:s=document.createElement('script');s.src='https://greasyfork.org/scripts/370819-html5视频截图器/code/HTML5视频截图器.user.js';document.head.append(s);
  ```

- 视频识别
  - 工具栏启动会自动检测网页中存在的HTML5视频并选中第一个视频作为操作对象，如果没有视频将提示检测不到视频
  - 点击工具栏上的检测按钮强制重新检测网页中的视频
  - 如果网页中存在多个视频，从下拉框中选择需要操作的对象，被选中的视频会自动滚动到视野内

- 视频控制：工具栏提供三个按钮供对截图对象视频进行通用操作，但不同网页表现差异较大，具体问题请看[使用须知](#使用须知)

- 截图
  - 如果视频源和浏览器支持，点击截图右侧的↓箭头可以直接下载一张95%质量的jpg格式截图，大小只有原始图片的20%左右
  - 如果视频或者浏览器不支持，点击↓箭头和点截图一样会打开一个新窗口显示当前视频画面，在画面上右键另存可得到png格式原始截图
  - 或许你也可以拿它来截一些直播，不过适用性应该会比截普通视频差，控制按钮也不一定生效

-------------------------
## 兼容性

- chrome 67 in Tampermonkey4.6 、书签测试通过
- 火狐 in Tampermonkey4.7 、Violentmonkey 、书签测试通过
- 不兼容Greasemonkey4，因为GM4取消了菜单注册，使用GM4安装脚本会在所有网页自动弹出截图工具栏
- 使用书签打开工具栏只对没有在嵌入框体中的视频有效
- 其它浏览器和脚本管理器未知

-------------------------
## 使用须知

- 功能依赖HTML5，脚本检测的是网页中的HTML5视频，准确来说是`<video>`标签的视频，其它类型视频不支持
- 当前已加入嵌套框架支持，但无法保证所有网页适用，如果有明确不支持的HTML5网页请反馈提交
- 工具栏的外观取决于所处的网页和浏览器有可能会很丑
- 使用时请确保视频播放器完成加载，如果视频没有加载出来，哪怕检测到播放器了脚本也无法对视频进行操作
- 如果播放器在播放过程中发生变更（换源或重载）脚本可能会操作失败，此时一般重新检测可以解决
- 播放暂停控制按钮不一定对所有视频生效，或者有时生效但是在网页上会表现很怪异（比如转圈/遮罩层/弹幕没停止）
- 逐帧控制并不一定适用于所有视频，有些播放器改变时间轴后会自动播放所以控制会失效
- 逐帧控制使用30fps的帧率进行控制，这个数据并不一适用于所有视频，所以实际控制并不一定是逐帧的
- 逐帧控制时画面并不一定会实时响应，特别是你快速点了很多下的情况下一般要等播放器缓过来
- 截取到的图片尺寸为视频的原始大小，和当前播放器窗口大小无关
- 截取到的图片不会包含播放暂停按钮、弹幕等非视频内的内容
- 截取到的图片也无法去除水印等原本视频里就有的内容
- 直接下载截图并不一定对所有视频和浏览器有效，有时可能和点截图按钮效果一样，甚至可能点了完全没有反应
- chrome里按住ctrl键点截图可在后台打开截图窗口从而不影响当前视频播放（或许你可以继续截图）
- 拖动工具栏悠着点，如果你追不上工具栏了最好换个方向拦它，或者关了重开，有些网页中拖动可能会表现十分怪异
- 脚本检测到的视频并不一定都是你能看到的，可能会有一些隐藏视频或空视频标签，自行在下拉框中寻找合适的进行操作
