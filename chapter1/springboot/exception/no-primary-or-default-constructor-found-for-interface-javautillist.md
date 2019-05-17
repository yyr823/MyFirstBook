### No primary or default constructor found for interface java.util.List

* **调用请求进行参数映射时出错.**

* **解决方法\(加上注解即可\)**

```java
public Object showCollectPros(@RequestParam(value = "content") List<String> content) {
            do smoething...
}
```



