---
layout:     post
subtitle:   Intent跳转功能
date:       2018-09-21
author:     HarlanSong
header-img: img/upload/aa97c67c8c1d79a0ce94c0fee2a30bfd8838df307da2f-RPC97X.jpg
catalog: 	 true
tags:
    - Android
    - Intent
---

## 浏览器打开连接

```java
Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("http://www.google.com"));  
startActivity(intent);
```
 

## 启动拨号程序
```java
Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("tel:186xxxxxxxx"));
startActivity(intent);
```

## 发送短信

```java
Uri smsUri = Uri.parse(url);
Intent intent = new Intent(Intent.ACTION_VIEW, smsUri);
intent.setType("vnd.android-dir/mms-sms");
startActivity(intent);
```

## 启动通讯录

```java
Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("content://contacts/people/1"));
startActivity(intent);
```

## 启动地图程序（Google Maps等）
```java
Uri mapUri = Uri.parse(url);
Intent intent = new Intent(Intent.ACTION_VIEW, mapUri);
startActivity(intent);
```

## 启动邮件程序

```java
Uri uri =Uri.parse("mailto:harlansong@qq.com");
Intent intent = newIntent(Intent.ACTION_SENDTO, uri);
intent.putExtra(Intent.EXTRA_SUBJECT, "Hello world");
intent.putExtra(Intent.EXTRA_TEXT, "Ganbarimasu");
startActivity(intent);
```
说明：启动邮件程序并将收件人设为harlansong@qq.com，邮件主题设为Hello world，内容设为Ganbarimasu。

## 启动邮件程序并添加多个收件人

```java
Intent intent=new Intent(Intent.ACTION_SEND);     
String[] tos={"me@example.com"};     
String[]ccs={"you@example.com"};     
intent.putExtra(Intent.EXTRA_EMAIL, tos);     
intent.putExtra(Intent.EXTRA_CC, ccs);     
intent.putExtra(Intent.EXTRA_TEXT, "The email body text");     
intent.putExtra(Intent.EXTRA_SUBJECT, "The email subject text");     
intent.setType("message/rfc822");     
startActivity(Intent.createChooser(intent,"Choose Email Client"));
```

## 启动邮件程序并添加附件

```java
Intent intent = newIntent(Intent.ACTION_SEND);   
intent.putExtra(Intent.EXTRA_SUBJECT, "The email subject text");    
intent.putExtra(Intent.EXTRA_STREAM,"file:///sdcard/mysong.mp3);   
sendIntent.setType("audio/mp3");   
startActivity(Intent.createChooser(intent,"Choose Email Client"));
```

## 播放音乐文件

```java
Intent intent = new Intent(Intent.ACTION_VIEW);
Uri uri =Uri.parse("file:///sdcard/song.mp3");
intent.setDataAndType(uri,"audio/mp3");
startActivity(intent);
```
 

## 卸载程序

```java
Uri uri =Uri.fromParts("package", strPackageName, null);   
Intent intent = newIntent(Intent.ACTION_DELETE, uri);   
startActivity(intent);
```
说明：卸载包名为strPackageName的程序。

 
## 安装程序

```java
Uri installUri = Uri.fromParts("package",strPackageName, null);
returnIt = newIntent(Intent.ACTION_PACKAGE_ADDED, installUri);
```
 说明：安装包名为strPackageName的程序。

## 启动应用市场

```java
Uri uri=Uri.parse("market://search?q=pname:org.breezesoft.techolite");
Intent intent=new Intent(Intent.ACTION_VIEW,uri);
startActivity(intent);
```