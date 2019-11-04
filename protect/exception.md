# 程序运行信息的获取与信息异常的快速发现
程序运行信息对程序的运维来说至关重要，如何及时，准确，省力的发现程序运行信息中的异常信息，如何及时，准确，省力的发现异常产生的具体原因，是程序运维的关键。
这里面重要的三点为
1. 及时
2. 省力
3. 准确


在这三个诉求上面，业界提出了共三个不同的程序运行信息表现形式，分别从数字表现信息，文本表现信息上做出了一些方案设计。
# 监控
## 收集数据
数字
## 表现形式
图表
## 好处
可以直接基于数字给出结论（报警信息，异常原因等）
## 作用
1. 利用机器及时发现线上业务出现的问题，能在第一时间发现故障。
2. 以图表的方式展示信息，方便定位故障原因。

## 监控方式
1. 数量监控
2. 时间监控
## 监控报警原则
1. 系统对外提供或者依赖的所有动作，必须报警。
2. 每次上线代码关键性链路必须打监控。
3. catch 异常处必须打监控，并且打印日志。
# 日志
## 收集数据形式
文字
## 表现形式
文字
## 好处
表达能力更强。
## 作用
使用监控发现故障后，需要通过日志发现故障的详细原因。
# trace：日志的另一种编排方式
## 收集数据
文字
## 表现形式
以请求流程串联起来的文字表现形式。
## 好处
可以看到一次请求流程的全貌，更加方便排查问题。
## 作用
以请求的整个链路串联起来的日志（编排方式变更），更加清晰的观察整个流程，方便定位问题（支付链路常用）