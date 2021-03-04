## Thread中Wait与Sleep的区别

我们还是以Jamvm为例，定位JVM中的源码

在Sleep中

```c
// thread.c
void threadSleep(Thread *self, long long ms, int ns) {
    monitorLock(&sleep_mon, self);
    monitorWait(&sleep_mon, self, ms, ns, FALSE, TRUE);
    monitorUnlock(&sleep_mon, self);
}
```

在Object.wait的实现中

```c
// lock.c
void objectWait(Object *obj, long long ms, int ns, int interruptible) {
    //....
    if(monitorWait(mon, self, ms, ns, TRUE, interruptible))
        return;
}
```

因此粗略上看，我们只要弄清楚两个问题即可

* monitorWait如何实现，是否耗费CPU？
* monitorLock/monitorUnlock具体有什么用？

