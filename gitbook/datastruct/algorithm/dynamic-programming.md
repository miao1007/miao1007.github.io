# 动态规划

动态规划通过一个全局的数据结构（HashMap，InvetedIndex，Array等）缓存计算结果，类似于Groovy的memorization，它是编译器CPS优化的例子

## Fibonacci

以Fibonacci为例

```java
public class Main {

  public static void main(String[] args) {
    // or cache = new HashMap<Integer, Integer>();
    int[] cache = new int[1000]; //key = input , value = result
    System.out.println(new Main().fibWrapper(10, cache));
  }

  public int fibWrapper(int n, int[] cache) {
    if (cache[n] != 0) {
      return cache[n];
    }
    if (n <= 2) {
      return 1;
    }
    return fibWrapper(n-1) + fibWrapper(n - 2);
  }

  public int fib(int n) {
    if (n <= 2) {
      return 1;
    }
    return fib(n-1) + fib(n - 2);
  }
}
```

