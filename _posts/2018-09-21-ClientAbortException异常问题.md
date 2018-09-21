---
layout:     post
title:      ClientAbortException异常问题
subtitle:   org.apache.catalina.connector.ClientAbortException: java.io.IOException: APR error: -730054
date:       2018-09-21
author:     HarlanSong
header-img: img/upload/aa97c67c8c1d79a0ce94c0fee2a30bfd8838df307da2f-RPC97X.jpg
catalog: 	 true
tags:
    - java
    - spring
	- ClientAbortException
---

已发现问题，还没有找到解决方案，如有解决方案麻烦留言，感谢。

错误内容
```
org.apache.catalina.connector.ClientAbortException: java.io.IOException: APR error: -730054
	at org.apache.catalina.connector.OutputBuffer.doFlush(OutputBuffer.java:356) ~[catalina.jar:8.0.36]
	at org.apache.catalina.connector.OutputBuffer.flush(OutputBuffer.java:320) ~[catalina.jar:8.0.36]
	at org.apache.catalina.connector.CoyoteOutputStream.flush(CoyoteOutputStream.java:110) ~[catalina.jar:8.0.36]
	at com.fasterxml.jackson.core.json.UTF8JsonGenerator.flush(UTF8JsonGenerator.java:1022) ~[jackson-core-2.6.7.jar:2.6.7]
	at com.fasterxml.jackson.databind.ObjectWriter.writeValue(ObjectWriter.java:891) ~[jackson-databind-2.6.7.jar:2.6.7]
	at org.springframework.http.converter.json.AbstractJackson2HttpMessageConverter.writeInternal(AbstractJackson2HttpMessageConverter.java:269) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.http.converter.AbstractGenericHttpMessageConverter.write(AbstractGenericHttpMessageConverter.java:100) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.annotation.AbstractMessageConverterMethodProcessor.writeWithMessageConverters(AbstractMessageConverterMethodProcessor.java:223) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.annotation.AbstractMessageConverterMethodProcessor.writeWithMessageConverters(AbstractMessageConverterMethodProcessor.java:154) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.annotation.RequestResponseBodyMethodProcessor.handleReturnValue(RequestResponseBodyMethodProcessor.java:165) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.method.support.HandlerMethodReturnValueHandlerComposite.handleReturnValue(HandlerMethodReturnValueHandlerComposite.java:81) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:126) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:832) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:743) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:85) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:961) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:895) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:967) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:869) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:648) ~[servlet-api.jar:na]
	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:843) ~[spring-webmvc-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:729) ~[servlet-api.jar:na]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:292) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52) ~[tomcat-websocket.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:240) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:99) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:240) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.springframework.web.filter.HttpPutFormContentFilter.doFilterInternal(HttpPutFormContentFilter.java:87) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:240) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.springframework.web.filter.HiddenHttpMethodFilter.doFilterInternal(HiddenHttpMethodFilter.java:77) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:240) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:121) ~[spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:240) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.springframework.boot.context.web.ErrorPageFilter.doFilter(ErrorPageFilter.java:120) [spring-boot-1.3.6.RELEASE.jar:1.3.6.RELEASE]
	at org.springframework.boot.context.web.ErrorPageFilter.access$000(ErrorPageFilter.java:61) [spring-boot-1.3.6.RELEASE.jar:1.3.6.RELEASE]
	at org.springframework.boot.context.web.ErrorPageFilter$1.doFilterInternal(ErrorPageFilter.java:95) [spring-boot-1.3.6.RELEASE.jar:1.3.6.RELEASE]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.2.7.RELEASE.jar:4.2.7.RELEASE]
	at org.springframework.boot.context.web.ErrorPageFilter.doFilter(ErrorPageFilter.java:113) [spring-boot-1.3.6.RELEASE.jar:1.3.6.RELEASE]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:240) [catalina.jar:8.0.36]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:207) [catalina.jar:8.0.36]
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:212) [catalina.jar:8.0.36]
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:106) [catalina.jar:8.0.36]
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:502) [catalina.jar:8.0.36]
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:141) [catalina.jar:8.0.36]
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:79) [catalina.jar:8.0.36]
	at org.apache.catalina.valves.AbstractAccessLogValve.invoke(AbstractAccessLogValve.java:616) [catalina.jar:8.0.36]
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:88) [catalina.jar:8.0.36]
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:528) [catalina.jar:8.0.36]
	at org.apache.coyote.http11.AbstractHttp11Processor.process(AbstractHttp11Processor.java:1099) [tomcat-coyote.jar:8.0.36]
	at org.apache.coyote.AbstractProtocol$AbstractConnectionHandler.process(AbstractProtocol.java:670) [tomcat-coyote.jar:8.0.36]
	at org.apache.tomcat.util.net.AprEndpoint$SocketProcessor.doRun(AprEndpoint.java:2508) [tomcat-coyote.jar:8.0.36]
	at org.apache.tomcat.util.net.AprEndpoint$SocketProcessor.run(AprEndpoint.java:2497) [tomcat-coyote.jar:8.0.36]
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142) [na:1.8.0_65]
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617) [na:1.8.0_65]
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61) [tomcat-util.jar:8.0.36]
	at java.lang.Thread.run(Thread.java:745) [na:1.8.0_65]
Caused by: java.io.IOException: APR error: -730054
	at org.apache.coyote.http11.InternalAprOutputBuffer.writeToSocket(InternalAprOutputBuffer.java:291) ~[tomcat-coyote.jar:8.0.36]
	at org.apache.coyote.http11.InternalAprOutputBuffer.writeToSocket(InternalAprOutputBuffer.java:244) ~[tomcat-coyote.jar:8.0.36]
	at org.apache.coyote.http11.InternalAprOutputBuffer.flushBuffer(InternalAprOutputBuffer.java:213) ~[tomcat-coyote.jar:8.0.36]
	at org.apache.coyote.http11.AbstractOutputBuffer.flush(AbstractOutputBuffer.java:305) ~[tomcat-coyote.jar:8.0.36]
	at org.apache.coyote.http11.AbstractHttp11Processor.action(AbstractHttp11Processor.java:764) [tomcat-coyote.jar:8.0.36]
	at org.apache.coyote.Response.action(Response.java:177) ~[tomcat-coyote.jar:8.0.36]
	at org.apache.catalina.connector.OutputBuffer.doFlush(OutputBuffer.java:352) ~[catalina.jar:8.0.36]
	... 65 common frames omitted
``` 