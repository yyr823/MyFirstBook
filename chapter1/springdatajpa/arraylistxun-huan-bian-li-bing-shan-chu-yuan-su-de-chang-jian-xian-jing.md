# ArrayList循环遍历并删除元素的常见陷阱

* #### [原文链接](https://www.cnblogs.com/huangjinyong/p/9455163.html)
* #### 代码示例

```
import java.util.ArrayList;
public class ArrayListRemove
{
　　publicstaticvoidmain(String[]args)
　　{
　　　　ArrayList<String>list=newArrayList<String>();
　　　　list.add("a");
　　　　list.add("b");
　　　　list.add("b");
　　　　list.add("c");
　　　　list.add("c");
　　　　list.add("c");
　　　　remove(list);
　　　　for(Strings:list)
　　　　{
　　　　　　System.out.println("element : "+s);
　　　　}
　　}
　　public static void remove(ArrayList<String> list)
　　{
　　// TODO:
　　}
}
```

* #### 操作：想删除list的b字符

1. **错误例子1：**

```
public static void remove(ArrayList<String> list)
{
    for(inti=0;i<list.size();i++)
    {
        Strings=list.get(i);
        if(s.equals("b"))
        {
            list.remove(s);
        }
    }
}
```

* 效果：这种最普通的循环写法执行后会发现第二个“b”的字符串没有删掉

* 原因：

翻开JDK的ArrayList源码，先看下ArrayList中的remove方法（注意ArrayList中的remove有两个同名方法，只是入参不同，这里看的是入参为Object的remove方法）是怎么实现的：

```
public boolean remove(Objecto){
    if(o==null){
        for(intindex=0;index<size;index++)
            if(elementData[index]==null){
                fastRemove(index);
                return true;
            }
            }else{
                for(intindex=0;index<size;index++)
                if(o.equals(elementData[index])){
                fastRemove(index);
                return true;
            }
    }
    return false;
}
```

一般情况下程序的执行路径会走到else路径下最终调用faseRemove方法：

```
private void fastRemove(int index){
        modCount++;
        intnumMoved=size-index-1;
        if(numMoved>0)             
        　　System.arraycopy(elementData,index+1,elementData,index,numMoved);
        elementData[--size]=null;// Let gc do its work
}
```

**可以看到会执行System.arraycopy方法，导致删除元素时涉及到数组元素的移动**。在遍历第一个字符串b时因为符合删除条件，所以将该元素从数组中删除，并且将后一个元素移动（也就是第二个字符串b）至当前位置，导致下一次循环遍历时后一个字符串b并没有遍历到，所以无法删除。

* 针对这种情况可以_**倒序删除**_的方式来避免（因为数组倒序遍历时即使发生元素删除也不影响后序元素遍历）：

```
public static void remove(ArrayList<String> list)
{
    for(inti=list.size()-1;i>=0;i--)
    {
        Strings=list.get(i);
        if(s.equals("b"))
        {
            list.remove(s);
        }
    }
}
```

2.错误例子2：

```
public static void remove(ArrayList<String> list)
{
    for(Strings:list)
    {
        if(s.equals("b"))
        {
            list.remove(s);
        }
    }
}
```

* 效果：这种for-each写法会报出著名的并发修改异常：_**`java.util.ConcurrentModificationException`**_

* 原因：

foreach写法是对实际的Iterable、hasNext、next方法的简写，问题同样处在上文的fastRemove方法中，可以看到第一行把modCount变量的值加一，但在ArrayList返回的迭代器（该代码在其父类AbstractList中）

```
public Iterator<E> iterator() {
        return new Itr();
}
```

这里返回的是AbstractList类内部的迭代器实现private class Itr implements Iterator，看这个类的next方法：

```
public E next() {
        checkForComodification();
        try {
            E next = get(cursor);
            lastRet = cursor++;
            return next;
        } catch (IndexOutOfBoundsException e) {
            checkForComodification();
            throw new NoSuchElementException();
        }
}
```

checkForComodification方法：

```
final void checkForComodification() {
        if (modCount != expectedModCount)
            throw new ConcurrentModificationException();
}
```

**这里会做迭代器内部修改次数检查，因为上面的remove\(Object\)方法修改了modCount的值，所以才会报出并发修改异常。**

* 针对这种情况可以在使用迭代器迭代时（显示或for-each的隐式）不要使用ArrayList的remove,改为用_**`Iterator的remove`**_的方式来避免:

```
public static void remove(ArrayList<String> list) 
    {
        Iterator<String> it = list.iterator();
        while (it.hasNext()) 
        {
            String s = it.next();
            if (s.equals("b")) 
            {
                it.remove();
            }
        }
}
```











