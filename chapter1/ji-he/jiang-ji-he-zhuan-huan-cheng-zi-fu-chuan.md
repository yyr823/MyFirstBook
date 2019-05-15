### 将集合转换成字符串

StringUtils工具类下的join\(\)方法：

```
import java.util.ArrayList;
import java.util.List;
import org.apache.commons.lang3.StringUtils;
public class Test {
	public static void main(String[] args) {
		List<String> list = new ArrayList<>();
		list.add("aa");
		list.add("bb");
		list.add("cc");
		System.out.println(list);
		// 将集合转换成字符串
		String str = StringUtils.join(list, ",");
		//打印出字符串
		System.out.println(str);
	}
}
```

使用join\(\)方法时，要传两个参数，一个是要转换的集合list，一个是要用符号分开的分隔符，这样利用工具类就会自动转换成“,”分隔的字符串形式。

### 字符串转换成集合

```
import java.util.Arrays;
import java.util.List;
public class Test1 {
	public static void main(String[] args) {
	  String str="aa,bb,cc"; 
	//用逗号将字符串分开，得到字符串数组 String[]
	  String[] strs=str.split(","); 
	 //将字符串数组转换成集合list 
	  List<String> list = Arrays.asList(strs);
	  //打印出集合
	  System.out.println(list);
	}
}
```

**注意：包的导入！**

