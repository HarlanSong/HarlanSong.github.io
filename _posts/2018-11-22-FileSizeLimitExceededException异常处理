---
layout:     post
title:      Spring Boot 上传文件FileSizeLimitExceededException问题解决方案
date:       2018-11-22
author:     HarlanSong
header-img: img/upload/bg_spring.jpg
catalog: true
tags:
    - Java
    - 问题解决方案
    - Spring
    - Spring Boot
---

Spring Boot 上传文件时报了以下错误：

```
org.apache.tomcat.util.http.fileupload.FileUploadBase$FileSizeLimitExceededException: The field file exceeds its maximum permitted size of 1048576 bytes.
	at org.apache.tomcat.util.http.fileupload.FileUploadBase$FileItemIteratorImpl$FileItemStreamImpl$1.raiseError(FileUploadBase.java:628) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.tomcat.util.http.fileupload.util.LimitedInputStream.checkLimit(LimitedInputStream.java:76) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.tomcat.util.http.fileupload.util.LimitedInputStream.read(LimitedInputStream.java:135) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at java.io.FilterInputStream.read(FilterInputStream.java:107) ~[na:1.8.0_141]
	at org.apache.tomcat.util.http.fileupload.util.Streams.copy(Streams.java:98) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.tomcat.util.http.fileupload.util.Streams.copy(Streams.java:68) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.tomcat.util.http.fileupload.FileUploadBase.parseRequest(FileUploadBase.java:293) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.connector.Request.parseParts(Request.java:2884) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.connector.Request.parseParameters(Request.java:3232) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.connector.Request.getParameter(Request.java:1137) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.connector.RequestFacade.getParameter(RequestFacade.java:381) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.springframework.web.filter.HiddenHttpMethodFilter.doFilterInternal(HiddenHttpMethodFilter.java:75) ~[spring-web-5.0.6.RELEASE.jar:5.0.6.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) ~[spring-web-5.0.6.RELEASE.jar:5.0.6.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:200) ~[spring-web-5.0.6.RELEASE.jar:5.0.6.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) ~[spring-web-5.0.6.RELEASE.jar:5.0.6.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:198) ~[tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:96) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:496) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:140) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:81) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:87) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:342) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:803) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:66) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:790) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1468) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149) [na:1.8.0_141]
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624) [na:1.8.0_141]
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61) [tomcat-embed-core-8.5.31.jar:8.5.31]
	at java.lang.Thread.run(Thread.java:748) [na:1.8.0_141]
```

**解决方案：**
在application.properties中添加配置，大小视实际情况定。
```
spring.servlet.multipart.max-file-size=100Mb
spring.servlet.multipart.max-request-size=1000Mb
```
