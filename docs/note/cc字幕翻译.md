---
lang: zh-CN
title: cc字幕实时翻译
description: 一个简单的油猴脚本
---

# cc字幕翻译工具

## 什么是 CC 字幕
> 早期，CC 字幕是指闭路电视字幕 (Closed Captioning)。这是一种以文字形式呈现音频内容的字幕格式，是为听力受损或语言不同的人士提供的一种辅助工具，可以帮助他们更好地理解视频的内容。 CC 字幕通常会出现在视频底部或侧边，并以白色字体和黑色背景呈现。

> 现在，人们也常用 CC 字幕来指视频文件中的文本字幕。这种文本字幕可以是人工添加的，也可以是自动生产的。与传统的字幕不同，CC 字幕可以关闭或打开，即使在无声电视或视频中也可以使用。它们也可以被用来表示原始音频的翻译，从而使视频更具可访问性，适用于一些听力或字幕障碍的观众。总的来说，“CC 字幕” 在现代的用法中代表了更广泛的含义。

## 这个工具的受众是谁
- 使用现代浏览器如chrome/edge/firefox浏览视频网站
- 这些视频只提供了外文cc字幕
- 如果你使用youtube，建议用该网站本身的字幕翻译功能
- 你想实时翻译这些字幕以更好的理解视频内容
- 你有申请到百度翻译的通用翻译api

## 如何使用？
1. 安装油猴浏览器插件
2. 安装[cc-caption-translator](https://greasyfork.org/zh-CN/scripts/465174-cc-caption-automatic-translator)脚本
3. 编辑该脚本，修改脚本 17 行到 22 行的 api id、api key、需要翻译的语言和目标语言。语言的标记代码参考： https://api.fanyi.baidu.com/api/trans/product/apidoc
4. 打开目标页面，点击显示 cc 字幕，启动视频播放
5. 点击页面右下角按钮（“开始翻译”）。无论页面是否有视频，点击后按钮都会消失。