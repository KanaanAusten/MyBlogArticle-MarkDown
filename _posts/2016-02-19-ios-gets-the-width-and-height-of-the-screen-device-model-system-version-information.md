---
id: 191
title: iOS获取屏幕宽高、设备型号、系统版本信息
date: 2016-02-19T22:50:12+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=191
permalink: /2016/02/19/ios-gets-the-width-and-height-of-the-screen-device-model-system-version-information/
dsq_thread_id:
  - 4632687062
views:
  - 20
categories:
  - OC
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

获取设备相关信息，如屏幕宽高、设备型号、系统版本

## [](https://github.com/KanaanAusten/GetDeviceInfoDemo#介绍)介绍

本工程获取三种常用的设备信息：

  * 获取屏幕的宽高。用于在设置控件位置的时候计算相对屏幕的距离
  * 获取设备的型号。5s和6+的屏幕大小相差很远，相应的控件位置、大小都需要做出调整，不然就会出现在6+上显得很空旷或者在5s上显示不全的问题。
  * 获取系统版本。不同的系统版本有着不同的特性，举个栗子，iOS 9以下的版本就没有Live Photo；再举个栗子，iOS 7以上的系统版本往往需要调整一下边界

## [](https://github.com/KanaanAusten/GetDeviceInfoDemo#方法)方法

以下方法均使用pch宏文件来设置，便于全局调用

  * 获取屏幕的宽高

<pre class="prettyprint" ><code>// 设备宽度 [UIScreen mainScreen].bounds.size.width
// 设备高度 [UIScreen mainScreen].bounds.size.height
</code></pre>

  * 获取设备的型号

<pre class="prettyprint" ><code>// 根据屏幕分辨率判断设备，是则返回YES，不是返回NO
#defineisiPhone5or5sor5c ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(640, 1136), [[UIScreen mainScreen] currentMode].size) : NO)
#defineisiPhone6or6s ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(750, 1334), [[UIScreen mainScreen] currentMode].size) : NO)
#defineisiPhone6plusor6splus ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(1242, 2208), [[UIScreen mainScreen] currentMode].size) : NO)
</code></pre>

  * 获取系统版本

<pre class="prettyprint" ><code>// 设备的系统版本 #defineSystemVersion ([[UIDevice currentDevice] systemVersion]) // 使用：if ([SystemVersion floatValue] &gt;= 7.0)
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->