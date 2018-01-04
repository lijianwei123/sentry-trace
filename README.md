# sentry-trace
> 调用链 是跟踪调用会话的利器

> 说明，这里只是把一些设计思想贴出，代码暂时还不能放出

## 架构图
![架构图](http://chuantu.biz/t6/196/1515055205x-1566673187.png)

## 目前功能支持
- controller层 service层 
- dubbo
- db层

## 基本使用
- 引用jar
- -javaagent:sentry-agent-1.0-SNAPSHOT.jar
- spring boot项目默认加载
- 其他非spring boot项目，通过配置Bootstrap类即可

## 查看调用链日志
调用链日志默认打印在/logs/项目/platform_sentry_trace.log下
```
[2018-01-04 16:25:04] [INFO] [http-nio-9999-exec-3] [c.g.p.s.t.b.aop.aspect.TraceAspect.?] Line:[?] - traceId: 0f15e879-1e62-43be-b374-675fde80b4ff, [tag: platform_sentry_trace, method: com.ggj.platform.sentry.proxy.controller.HealthCheckController.zkClusterStatus(), phase: method_exec_start], args: []
[2018-01-04 16:25:04] [INFO] [http-nio-9999-exec-3] [c.g.p.s.t.b.aop.aspect.TraceAspect.?] Line:[?] - traceId: 0f15e879-1e62-43be-b374-675fde80b4ff, [tag: platform_sentry_trace, method: com.ggj.platform.sentry.proxy.service.impl.CheckServiceImpl.zkClusterStatus(), phase: method_exec_start], args: []
[2018-01-04 16:25:04] [INFO] [http-nio-9999-exec-3] [c.g.p.s.t.b.aop.aspect.TraceAspect.?] Line:[?] - traceId: 0f15e879-1e62-43be-b374-675fde80b4ff, [tag: platform_sentry_trace, method: com.ggj.platform.sentry.proxy.service.impl.CheckServiceImpl.telnet(String, Integer), phase: method_exec_start], args: [127.0.0.1, 2181]
[2018-01-04 16:25:04] [INFO] [http-nio-9999-exec-3] [c.g.p.s.t.b.aop.aspect.TraceAspect.?] Line:[?] - traceId: 0f15e879-1e62-43be-b374-675fde80b4ff, [tag: platform_sentry_trace, method: com.ggj.platform.sentry.proxy.service.impl.CheckServiceImpl.telnet(String, Integer), phase: method_exec_end], elapsed: 6.641ms
[2018-01-04 16:25:04] [INFO] [http-nio-9999-exec-3] [c.g.p.s.t.b.aop.aspect.TraceAspect.?] Line:[?] - traceId: 0f15e879-1e62-43be-b374-675fde80b4ff, [tag: platform_sentry_trace, method: com.ggj.platform.sentry.proxy.service.impl.CheckServiceImpl.zkClusterStatus(), phase: method_exec_end], elapsed: 7.935ms
[2018-01-04 16:25:04] [INFO] [http-nio-9999-exec-3] [c.g.p.s.t.b.aop.aspect.TraceAspect.?] Line:[?] - traceId: 0f15e879-1e62-43be-b374-675fde80b4ff, [tag: platform_sentry_trace, method: com.ggj.platform.sentry.proxy.controller.HealthCheckController.zkClusterStatus(), phase: method_exec_end], elapsed: 8.2ms
```
