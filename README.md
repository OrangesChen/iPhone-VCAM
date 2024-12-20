# iPhone-VCAM

基于 *Cydia Substrate* 的虚拟摄像头

# 作用

替换 iOS 系统摄像头画面

## 生效软件
- 支持绝大多数App
- 系统相机 (System Camera)
- 相机 (Message)
- 网页 (Webkit)
- QQ
- TIM
- Wechat
- TokTik
- Telegram (已知问题: 先使用拍照功能，在点右边的录像时，录像会卡顿)
- Google Translate
- Youtube
- Facebook
- Discord
- 大多数App都支持......

## 支持系统版本

- 开发测试版本为 iOS13.3、因为手上没有其他版本所以无法真机测试
- 理论支持 iOS11.0 以上
- iOS15可能出点问题，且目前iOS15越狱方案没有

# 开始使用

## 安装
1. 需要安装 theos 环境，并配置环境变量 THEOS、THEOS_MAKE_PATH
```shell
 $ git clone https://github.com/theos/theos.git
 $ export THEOS=/Users/xxx/theos
 $ export THEOS_MAKE_PATH=/Users/xxx/theos/makefiles
```
2. 安装 ldid
```shell
 $ brew install ldid
```
3. 编译，执行 make
```shell
 $ make
```
4. 拷贝 dylib 文件到 /Library/MobileSubstrate/DynamicLibraries/ 目录下
```shell
 $ scp build/TTest.dylib root@IP:/Library/MobileSubstrate/DynamicLibraries/ 
```
5. 重启设备
```shell
 $ killall SpringBoard
```

## 使用
- 以下 **-** 符号表示 **音量减键**, **+** 表示 **音量加键**, 在一秒内切换点击以触发

### 完整模式
弹窗较多，有些软件会在弹窗后暂停运行
- 快捷键 + -
- 功能见按钮说明
- 下载视频
    - *每次下载完成后都会有系统的静音提示框弹出*
    1. 视频文件
        1. 在线视频地址，需要确保这个链接指向了一个可访问的视频
        2. 如果文件损坏或不可播放或不受支持不会发生任何变化
    2. 流式媒体(暂未支持)

### 便捷模式
尽量减少弹窗以防止打断当前程序的运行状态  
- 快捷键 - + 触发**选择视频**
- 如果设置了**下载视频**功能，则此快捷键改为触发**下载视频**
- 将**下载视频**的连接设置为空时，继续使用**选择视频**
    - 下载完成后会有静音模式弹窗会弹出
    - 如果远程文件不可用则禁用替换

# 常见问题
- 以下 **-** 符号表示 **音量减键**, **+** 表示 **音量加键**, 在一秒内切换点击以触发

## Q: 该怎样选择视频分辨率？
A: 使用摄像头后 + -，将会出现详细信息。 当宽度大于高度时，表示视频的方向时旋转的，大部分情况下后置摄像头需要逆时针90度，前置摄像头顺时针90度，有时需要旋转并水平翻转。视频的具体方向因不同软件处理方式不同需要自行观察。**替换预览始终保持正确的方向**，*如果视频的宽高和提示的不一致时，可能出现画面与识别结果偏移、预览拉伸甚至闪退的情况*
- 简单来说，替换视频的宽高必须和 + - 快捷键提示的 W, H一致，根据预览到的画面调整替换视频角度

## Q: 拍照后画面旋转？
A: 预览始终保持了正确的方向，部分软件会直接处理横向的图片，但是给用户预览的时候把预览旋转过来了
- 简单来说，根据被旋转的方向，把替换视频提前往相反的方向旋转一次就好了



# TODO
- 音频支持
- 修复有些软件录像循环后失效问题
