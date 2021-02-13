# 插件说明
插件提供了对mp3,png,jpg资源的压缩功能,在保证文件质量的前提下,对文件进行瘦身,减小文件体积的大小

## 其他说明
- 项目中压缩mp3使用了lame
    - npm地址: https://www.npmjs.com/package/node-lame
    - sourceforge地址: http://lame.sourceforge.net/
- 项目中压缩图片使用了[imageMin](https://github.com/imagemin/imagemin#readme)

## 插件使用
- 打开快捷键: Cmd/Ctrl + m
- 音频文件: 目前插件只会对mp3进行压缩,所以建议项目使用mp3类型音频文件

## 使用动态图
![使用小视频]( ../../assets/res-compress/插件使用.gif)  

## 压缩效果
### mp3
- [压缩前文件 9.79k](../../assets/res-compress/testcase.mp3)
- [压缩后文件 4.94k](../../assets/res-compress/testcase-compress.mp3)

### jpg
- [压缩前jpg 1.08M](../../assets/res-compress/test.jpg)
- [压缩后jpg 360k](../../assets/res-compress/test-compress.jpg)

### png
- [压缩前png 57.3k](../../assets/res-compress/test.png)
- [压缩后png 12.6k](../../assets/res-compress/test-compress.png)

## 帮助
在mac平台下,执行lame需要运行权限,插件会自动授予权限,如果插件提示了权限问题,需要再次检查下lame的权限

![权限问题]( ../../assets/res-compress/mac.png) 


