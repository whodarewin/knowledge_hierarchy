# 事物拆解
事物的一组操作，分为两类，一类是执行操作，一类是rollback操作。rollback操作一般是业务上的，比如扣款，账户余额不足，执行rollback。
# 事物实现面临的问题
## 进程崩溃
进程崩溃是指事物执行到一半，进程崩溃，这样，即使重新启动进程，事物的A，C特性已经实现不了了。
## 一般性解决方案
### 单机
使用日志记录要做的事情，一个事物第一步是要在日志系统中留下日志，记录下做的事情，当崩溃重启后，走崩溃恢复流程。
即，只要在日志系统中留下日志，则要么事物全部执行完毕，要么事物因为业务上的原因rollback，一定能够满足ACID特性。
### 幂等性
当崩溃执行恢复程序时，会面临着一个问题，每个执行的子任务的任何一个阶段并不能每个细微的操作都进行日志记录，如何解决这个问题，需要每个子任务实现幂等性，即我虽然不知道这个操作是否执行，但是，我执行多少次都没关系，我再执行一次就是。