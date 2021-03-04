## 取余与触发

转向

```java
// 依次输出 3 0 1
int a = 103;
long rev = 0;
while(a>0){
  rev = rev*10 + a%10;
  a = a/10;
}
```

回文数

https://leetcode.com/problems/reverse-integer/submissions/

```java
int a = 1034;
long rev = 0;
while(a>rev){
  rev = rev*10 + a%10;
  a = a/10;
}
```

 



#### 测试用例

大数、负数