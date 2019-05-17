### 对List集合中的元素进行排序

* #### [原文链接](https://blog.csdn.net/veryisjava/article/details/51675036)
* #### 场景

有时候需要对集合中的元素按照一定的规则进行排序，这就需要用到,Java中提供的对集合进行操作的工具类Collections，其中的sort方法

* #### **实践:**
* [x] 简单的例子:

```java
public static void main(String[] args) {
    List<Integer> nums = new ArrayList<Integer>();
        nums.add(3);
        nums.add(5);
        nums.add(1);
        nums.add(0);
        System.out.println(nums);    //[3, 5, 1, 0]
        Collections.sort(nums);
        System.out.println(nums);    //[0, 1, 3, 5]
}
```

* [x] 复杂例子\(list里装有对象\):

1.Collections提供的第一种排序方法Comparable&lt;T&gt;  compareTo\(\)方法

```java
package core.java.collection.collections;

public class User implements Comparable<User>{

    private int score;

    private int age;

    public User(int score, int age){
        super();
        this.score = score;
        this.age = age;
    }

    public int getScore() {
        return score;
    }

    public void setScore(int score) {
        this.score = score;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public int compareTo(User o) {
        int i = this.getAge() - o.getAge();//先按照年龄排序
        if(i == 0){
            return this.score - o.getScore();//如果年龄相等了再用分数进行排序
        }
        return i;
    }

}

public static void main(String[] args) {
        List<User> users = new ArrayList<User>();
        users.add(new User(78, 26));
        users.add(new User(67, 23));
        users.add(new User(34, 56));
        users.add(new User(55, 23));
        Collections.sort(users);
        for(User user : users){
            System.out.print(user.getScore() + "," + user.getAge()+"\t\t");
            //输出结果：55,23  67,23  78,26  34,56
        }
}
```

我们会发现sort\(List&lt;T&gt;\)方法中List中的T`必须实现Comparable<T>接口`，然后实现`compareTo()`方法，该方法的返回值0代表相等，1表示大于，-1表示小于;为什么在简单例子中没有看到实现Comparable接口呢？是因为Integer类其实自己已经实现了Comparable接口,Java已经给我们做好了。

2.Collections提供的第二种排序方法**sort\(List&lt;T&gt; list, Comparator&lt;? super T&gt; c\)    
**

```java
package core.java.collection.collections;

public class Students {

    private int age;
    private int score;

    public Students(int age, int score){
        super();
        this.age = age;
        this.score = score;
    }

    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public int getScore() {
        return score;
    }
    public void setScore(int score) {
        this.score = score;
    }
}
public static void main(String[] args) {
        List<Students> students = new ArrayList<Students>();
        students.add(new Students(23, 100));
        students.add(new Students(27, 98));
        students.add(new Students(29, 99));
        students.add(new Students(29, 98));
        students.add(new Students(22, 89));
        Collections.sort(students, new Comparator<Students>() {

            @Override
            public int compare(Students o1, Students o2) {
                int i = o1.getScore() - o2.getScore();
                if(i == 0){
                    return o1.getAge() - o2.getAge();
                }
                return i;
            }
        });
        for(Students stu : students){
            System.out.print("score:" + stu.getScore() + ":age" + stu.getAge()+"\t\t");
    //输出结果： score:89:age22  score:98:age27  score:98:age29  score:99:age29  score:100:age23
        }
}
```

从上面的例子我们可以看出Students类没有实现Comparable&lt;T&gt;接口，只是在sort\(\)方法中多传入一个参数，只不过该参数是一个接口我们需要实现其**compare**方法。

