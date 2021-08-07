# Java 集合之 HashSet

&emsp;

    Set 是元素无序并且不可以重复的集合，被称为集
    HashSet 是 Set 的一个重要实现类，称为哈希集
    HashSet 中只允许一个 null 元素
    HashSet 具有良好的存取和查找性能


&emsp;

### Iterator (迭代器)

&emsp;

    Iterator接口可以以统一的方式对各种集合元素进行遍历

        迭代器的两个重要方法：
            hashNext() 方法检测集合中是否还有下一个元素
                如果迭代具有更多元素，则返回 true 。
            next() 返回迭代中的下一个元素。


&emsp;

### Iterator (迭代器) 遍历流程

&emsp;

    假设我们在 Iterator（迭代器）当中有三条数据（如下表所示）
    由于 HashSet 中的数据是无序，我们做出了一下的假设：

    |Python|人生苦短，我用Python|
    |C|面向过程的通用编程语言|
    |Java|面向对象的高级编程语言|

    当我们第一次调用 HashNext() 方法时，这时指针（一个不存在的箭头）指向了第一条数据（即：|Python|人生苦短，我用Python|）,这时 HashSet() 方法会判断当前所指向的数据的下一条数据是否存在， 如果有，调用 Next() 方法，得到第一条数据（即：|Python|人生苦短，我用Python|），下一次循环再去判断 HashNext() 方法，判断下一条数据是否存在，如果有，继续执行 Next() 方法，直到最后没有数据，结束循环。


&emsp;

### 在集合中插入字符串

&emsp;

```java
package com.demo.set;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class WordDemo {
    public static void main(String[] args) {
        //  需求：用HashSet存储多个表示颜色的英文单词，并输出。

        //  将英文单词添加到 HashSet 中
        Set set = new HashSet();

        //  向集合中添加元素 “" . "“red" . “black "、" yellow”和“white”

        set.add("blue");
        set.add("red");
        set.add("black");
        set.add("yellow");
        set.add("white");

        //  显示集合的内容

        System.out.println("集合中的元素为：");
        Iterator it = set.iterator();

        //  遍历迭代器循环并输出元素

        while(it.hasNext()){    //  HashNext() 返回值：有数据 true，无数据 false
            System.out.print(it.next() + ", ");
        }

        //  在集合当中插入新的数据
        //  set.add("green");

        //  TODO: 插入失败但是不会报错
        set.add("white");
        it = set.iterator();
        System.out.println("\n*************************************");
        System.out.println("插入重复元素后的输出结果为：");
        while(it.hasNext()){    //  HashNext() 返回值：有数据 true，无数据 false
            System.out.print(it.next() + ", ");
        }

    }
}

```

&emsp;

### 案例：宠物猫信息管理

&emsp;

#### 需求

    添加和显示宠物猫信息
    查找某只宠物猫的信息并输出-修改宠物猫的信息
    删除宠物猫信息

#### 属性

    名字name
    年龄month
    品种species

#### 方法

    构造方法
    获取和设置属性值的方法
    其他方法


&emsp;

```java
package com.demo.set;

import java.util.Objects;

public class Cat {
    private String name;    //  名字
    private int month;  //  年龄
    private String species; //  品种

    //  构造方法

    public Cat(String name, int month, String species) {
        this.name = name;
        this.month = month;
        this.species = species;
    }

    // Getter 方法和 Setter 方法

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getMonth() {
        return month;
    }

    public void setMonth(int month) {
        this.month = month;
    }

    public String getSpecies() {
        return species;
    }

    public void setSpecies(String species) {
        this.species = species;
    }

    @Override
    public String toString() {
        return "{" +
                "姓名：" + name +
                ", 年龄：" + month +
                ", 品种：" + species +
                '}';
    }

    @Override
    public boolean equals(Object obj) {
        //  判断你对象是否相等，相等则返回true，不用继续比较属性
        if (this == obj) return true;
        //  判读 obj 是否是 Cat 类的对象
        if (obj.getClass()==Cat.class) {
            Cat cat = (Cat) obj;
            return cat.getName().equals(name) && (cat.getMonth()==month) && (cat.getSpecies().equals(species));
        }
        return false;
    }

    @Override
    public int hashCode() {
        final int prime = 31;int result = 1;
        result = prime * result + month;
        result = prime * result + ((name == null) ? 0 : name.hashCode());
        result = prime * result + ((species == null) ? 0 : species.hashCode());
        return result;

    }
}

```

&emsp;

```java
package com.demo.set;

import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class CatTest {
    public static void main(String[] args) {

        //  定义宠物猫对象
        Cat cat1 = new Cat("阿七",2, "大橘猫");
        Cat cat2 = new Cat("Tom", 3,"英国短尾猫");

        //  将宠物猫对象放入 HashSet 中
        Set<Cat> set = new HashSet<>();
        set.add(cat1);
        set.add(cat2);

        //  显示宠物猫信息
        Iterator<Cat> it = set.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }

        //  添加重复的数据
        Cat cat3 = new Cat("阿七",2, "大橘猫");
        set.add(cat3);
        System.out.println("*************************************");
        System.out.println("添加重复数据后的宠物猫信息：");
        it = set.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }

        //  查找宠物猫信息
        Cat cat4 = new Cat("阿三",12, "白色大橘猫");
        set.add(cat4);
        System.out.println("*************************************");
        System.out.println("添加阿三后的宠物猫信息：");
        it = set.iterator();
        while(it.hasNext()){
            System.out.println(it.next());
        }

        System.out.println("*************************************");
        //   在集合中查找阿三的信息并输出
        if(set.contains(cat4)){
            System.out.println("阿三找到了");
            System.out.println(cat4);
        }
        else{
            System.out.println("阿三没找到了");
        }
        System.out.println("*************************************");
        System.out.println("通过名字查找阿三信息");
        boolean flag = false;
        Cat c = null;
        it = set.iterator();
        //  在集合中使用名字查找阿三的信息
        while(it.hasNext()){
            c = it.next();
            if(c.getName().equals("阿三")){
                flag = true; // 找到了
                break;
            }
        }
        if(flag){
            System.out.println("花花找到了");
            System.out.println(c);
        }else{
            System.out.println("花花没有找到");
        }

        //  删除阿三的信息并重新输出
        set.removeIf(cat -> "阿三".equals(cat.getName()));    // TODO: 这种写法我并清楚
        System.out.println("*************************************");
        System.out.println("删除阿三后的数据");
        for (Cat cat:set) {
            System.out.println(cat);
        }

        //  删除集合中所有的宠物猫信息
        System.out.println("*************************************");
        boolean flag1 = set.removeAll(set);
        if (set.isEmpty()) {
            System.out.println("猫没了");
        }
        else{
            System.out.println("猫在");
        }

    }
}
```

&emsp;

