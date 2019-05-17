* #### [原文链接](https://blog.csdn.net/veryisjava/article/details/51675036)

* #### 场景

有时候需要对集合中的元素按照一定的规则进行排序，这就需要用到,Java中提供的对集合进行操作的工具类Collections，其中的sort方法

* 实践:

简单的例子:

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

list里装有对象:

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
			System.out.print(user.getScore() + "," + user.getAge()+);
		}
}
输出结果：
55,23
67,23
78,26
34,56
```



