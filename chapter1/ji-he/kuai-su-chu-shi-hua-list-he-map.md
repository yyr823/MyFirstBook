# 快速初始化list和map

* #### [原文详解链接](https://blog.csdn.net/weixin_38750084/article/details/86640647)

> List

```java
public static void main(String[] args) {

        List<String> list = new ArrayList<String>(){
            {
               add("周一");
               add("周五");
             }
            };
        System.out.println("list=="+list);

    }
```

> Map

```java
public static void main(String[] args) {
        System.out.println(
            new HashMap<String, Object>(){
            {
               put("上班", "不开心");
               put("下班", "开心");
            }

        } );

    }
```



