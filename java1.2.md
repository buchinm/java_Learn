# JAVA(二）

### 一、java 修饰符

修饰符用来定义类、方法或者变量，通常放在语句的最前端。

- 访问修饰符
- 非访问修饰符

### 访问控制修饰符

- default（默认）：同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法
- private：在同一类内可见。使用对象：变量、方法（不能修饰外部类）
- public：对所有类可见。使用对象：类、接口、变量、方法
- protected：对同一包内的类和所有子类可见。使用对象：变量、方法（不能修饰外部类）

| 修饰符    | 当前类 | 同一包内 | 子孙类（同一包） | 子孙类(不同包) | 不同包 |
| --------- | ------ | -------- | ---------------- | -------------- | ------ |
| default   | Y      | Y        | Y                | N              | N      |
| public    | Y      | Y        | Y                | Y              | Y      |
| private   | Y      | N        | N                | N              | N      |
| protected | Y      | Y        | Y                | Y/N            | N      |

1. default：接口里的变量都是隐式声明为==public static final==,而接口里的方法默认情况下访问权限为public
2. private：类和接口不能声明为 private。声明为私有访问类型的变量只能通过类中公共的 ==getter== 法被外部类访问。主要用来隐藏类的实现细节和保护类的数据
3. public：如果几个相互访问的 public 类分布在不同的包中，则需要导入相应 public 类所在的包，==main()方法==必须设置成 public
4. protected：protected可以修饰数据成员，构造方法，方法成员，**不能修饰类（内部类除外）**。接口及接口的成员变量和成员方法不能声明为 protected

##### 访问控制和继承

- 父类中声明为 public 的方法在子类中也必须为  public
- 父类中声明为 protected 的方法在子类中要么声明为 protected，要么声明为 public，不能声明为 private
- 父类中声明为 private 的方法，不能够被继承

### 非访问修饰符

- static
- final
- abstract
- synchronized
- transient
- volatile

##### static修饰符

- **静态变量：**static 关键字用来声明独立于对象的静态变量，无论一个类实例化多少对象，它的静态变量只有一份拷贝。静态变量也被称为类变量。==局部变量==不能被声明为 static 变量。静态变量并不是说其就不能改变值，不能改变值的量叫常量。 其拥有的值是可变的 ，而且它会保持最新的值。说其静态，是因为它不会随着函数的调用和退出而发生变化。即上次调用函数的时候，如果我们给静态变量赋予某个值的话，下次函数调用时，这个值保持不变。
- **静态方法：**static 关键字用来声明独立于对象的静态方法。==静态方法只能使用类的静态变量==。静态方法从参数列表得到数据，然后计算这些数据。

##### final修饰符

- 变量：一旦赋值后，==不能被重新赋值==。被 final 修饰的实例变量必须==显式指定初始值==。final 修饰符通常和 static 修饰符一起使用来创建类常量
- 方法：父类中的final方法可以被子类继承，但是不能被子类重写
- 类：final 类不能被继承，没有类能够继承 final 类的任何特性

##### abstract修饰符

抽象类==不能用来实例化对象==，声明抽象类的唯一目的是为了将来对该类进行扩充。一个类不能同时被 abstract 和 final 修饰。如果一个类包含抽象方法，那么该类一定要声明为抽象类，否则将出现编译错误

抽象方法

- 抽象方法是一种没有任何实现的方法，该方法的的具体实现由子类提供。
- 抽象方法不能被声明成 final 和 static。
- 任何继承抽象类的子类必须==实现父类的所有抽象方法==，除非该子类也是抽象类。
- 如果一个类包含若干个抽象方法，那么该类必须声明为抽象类。抽象类可以不包含抽象方法。
- ==抽象方法的声明以分号结尾==，

##### synchronized 修饰符

synchronized 关键字声明的方法同一时间只能被一个线程访问。synchronized 修饰符可以应用于四个访问修饰符

##### transient修饰符

序列化的对象包含被 transient 修饰的实例变量时， java 虚拟机(JVM)跳过该特定的变量。该修饰符包含在定义变量的语句中，用来预处理类和变量的数据类型

##### volatile 修饰符

volatile 修饰的成员变量在每次被线程访问时，都强制从共享内存中重新读取该成员变量的值。而且，当成员变量发生变化时，会强制线程将变化值回写到共享内存。这样在任何时刻，两个不同的线程总是看到某个成员变量的同一个值。一个 volatile 对象引用可能是 null

### 二、java 运算符

- 算术运算符

- 关系运算符

- 位运算符

- 逻辑运算符

- 赋值运算符

- 条件运算符

- instanceof 运算符

  如果运算符左侧变量所指的对象，是操作符右侧类或接口(class/interface)的一个对象，那么结果为真

##### 注：

1. **前缀自增自减法(++a,--a):** 先进行自增或者自减运算，再进行表达式运算。
2. **后缀自增自减法(a++,a--):** 先进行表达式运算，再进行自增或者自减运算
3. 在判断一个实例引用的类型时，使用的是实际类型，而不是声明的类型
4. 子类的实例可以声明为父类型，但父类的实例不能声明为子类型

### 三、java 循环结构

- while
- do...while
- for

##### jva增强for循环

```
  for(声明语句 : 表达式)
  {
     //代码句子
  }
```

- 声明语句：声明新的局部变量，该变量的类型必须和数组元素的类型匹配。其作用域限定在循环语句块，其值与此时数组元素的值相等

- 表达式：表达式是要访问的数组名，或者是返回值为数组的方法

##### break关键字

- break：主要用在循环语句或者 switch 语句中，用来跳出整个语句块
- break：跳出最里层的循环，并且继续执行该循环下面的语句

##### continue关键字

- continue：适用于任何循环控制结构中。作用是让程序立刻跳转到下一次循环的迭代。
- 在for循环中 continue 语句使程序立即跳转到更新语句。
- 在 while 或者 do…while 循环中，程序立即跳转到布尔表达式的判断语句

### 四、java 条件语句

if...else

```
  if(布尔表达式){
     //如果布尔表达式的值为 true
  }else{
     //如果布尔表达式的值为 false
  }
```

### java switch case 语句

```
   switch(expression){
   case value :
          //语句
          break; //可选
       case value :
          //语句
          break; //可选
       //你可以有任意数量的 case 语句
       default : //可选
          //语句
   }
```

1. switch 语句中的变量类型可以是： byte、short、int 或者 char。从 Java SE 7 开始，switch 支持字符串 String 类型了，同时 ==case 标签必须为字符串常量或字面量==
2. switch 语句可以拥有多个 case 语句。每个 case 后面跟一个要比较的值和冒号
3. case 语句中的值的数据类型必须与变量的数据类型相同，而且只能是常量或者字面常量。
4. 当变量的值与 case 语句的值相等时，那么 case 语句之后的语句开始执行，直到 break 语句出现才会跳出 switch 语句
5. 当遇到 break 语句时，switch 语句终止。程序跳转到 switch 语句后面的语句执行。case 语句不必须要包含 break 语句。如果没有 break 语句出现，程序会继续执行下一条 case 语句，直到出现 break 语句
6. switch 语句可以包含一个 default 分支，该分支一般是 switch 语句的最后一个分支（可以在任何位置，但建议在最后一个）。default 在没有 case 语句的值和变量值相等的时候执行。default 分支不需要 break 语句

### 五、java Number & Math 类

##### Number & Math类方法

| 方法        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| xxxValue()  | 将 Number 对象装换为xxx数据类型的值并返回                    |
| compareTo() | 将Number对象与参数比较                                       |
| equals()    | 判断Number 对象是否与参数相等                                |
| valueOf()   | 返回一个 Number 对象指定的内置数据类型                       |
| toString()  | 以字符串形式返回值                                           |
| parseInt()  | 将字符串解析为 int 型                                        |
| abs()       | 返回参数的绝对值                                             |
| ceil()      | 返回大于等于(>=)给定参数的最小整数，类型为双精度浮点型       |
| floor()     | 返回小于等于(<=)给定参数的最大整数                           |
| rint()      | 返回与参数最接近的整数，返回类型为 double                    |
| round()     | 四舍五入，算法为 **Math.floor(x+0.5)**，即将原来的数字加上 0.5 后再向下取整，所以，Math.round(11.5) 的结果为12，Math.round(-11.5) 的结果为-11。 |
| min()       | 返回两个参数中的最小值                                       |
| max()       | 返回两个参数中的最大值                                       |
| exp()       | 返回自然数e的参数次方                                        |
| log()       | 返回参数的自然数底数的对数值                                 |
| pow()       | 返回第一个参数的第二个参数次方                               |
| sqrt()      | 求参数的算数平方根                                           |
| sin()       | 求指定的 double 类型参数的正弦值                             |
| cos()       | 求指定 double 类型参数的余弦值                               |
| toDegrees() | 将参数转化为角度                                             |
| toRadians() | 将角度转化为弧度                                             |
| random()    | 返回一个随机数                                               |

### 六、javaCharacter 类

Character 类用于对单个字符进行操作，在对象包装一个基本类型 char 的值

##### 转义序列

前面有反斜杠(\)的字符代表转移字符

- **\r**： return 到当前行的最左边
- **\n**： newline 向下移动一行，并不移动左
- Linux中**\n**表示：回车+换行
- Windows中**\r\n**表示：回车+换行
- Mac中**\r**表示：回车+换行

##### Character 方法

| 方法           | 描述                                    |
| -------------- | --------------------------------------- |
| isLetter()     | 是否是一个字母                          |
| isDigit()      | 是否是一个数字字符                      |
| isWhitespace() | 是否是一个空白字符                      |
| isUpperCase()  | 是否是一个大写字母                      |
| isLowerCase()  | 是否是一个小写字母                      |
| toUpperCase()  | 指定字母的大写形式                      |
| toLowerCase()  | 指定字母的小写形式                      |
| toString()     | 返回字符的字符串形式，字符串的长度仅为1 |

### 七、java String 类

String 类是不可改变的，如果要对字符串做很多修改，应该使用 StringBuffer & StringBuilder 类

##### 字符串长度

length() 方法获取字符串长度，返回字符串对象包含的字符数

##### 连接字符串

`string1.concat(string2);`

##### 创建格式化字符串

String 类的静态方法 format() 能用来创建可复用的格式化字符串，而不仅仅是用于一次打印输出

`  String fs;fs = String.format("...",...);`

##### String方法

| 方法                                 | 描述                                     |
| ------------------------------------ | ---------------------------------------- |
| char charAt(int index)               | 返回指定索引处的char值                   |
| int compareTo(Object o)              | 把这个字符串和另一个对象比较             |
| int compareTo(String anotherString)  | 按字典顺序比较两个字符串                 |
| String concat(String str)            | 将指定字符串连接到此字符串的结尾         |
| boolean equals(Object anotherObject) | 将次字符串与指定的对象比较               |
| int hashCode()                       | 返回此字符的哈希码                       |
| int indexOf(int ch)                  | 返回指定字符在此字符串中第一次出现的索引 |
| int length()                         | 返回此字符串的长度                       |
| contains(CharSequence chars)         | 判断是否包含指定的字符系列               |
| isEmpty()                            | 判断字符串是否为空                       |

##### length() 方法，length 属性和 size() 方法的区别:

1. **length()** 方法是针对字符串来说的，要求一个字符串的长度就要用到它的length()方法；
2. **length 属性**是针对 Java 中的数组来说的，要求数组的长度可以用其 length 属性；
3. Java 中的 **size()** 方法是针对泛型集合说的, 如果想看这个泛型有多少个元素, 就调用此方法来查看!

### 八、java StringBuffer 和 StringBuilder 类

当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象

### 九、java 数组

##### 声明数组变量

`dataType[] arrayRefVar;`

##### 创建数组

`dataType[] arrayRefVar = new dataType[arraySize];`

##### For-Each循环

不使用下标的情况下遍历数组

```
  for(type element: array){
      System.out.prinln(element);
  }
```

##### 多维数组

二维数组创建

`type[][] typeName = new type[typeLength1][typeLength2];`

##### Arrays 类

java.util.Arrays 类能方便地操作数组，它提供的所有方法都是静态的。具有以下功能：

1. 给数组赋值：通过 fill 方法
2. 对数组排序：通过 sort 方法,按升序
3. 比较数组：通过 equals 方法比较数组中数值是否相等
4. 查找数组元素：通过 binarySearch 方法能对排序好的数组进行二分查找法操作

### 十、java 日期时间

java.util 包提供了 Date 类来封装当前的日期和时间。Date 类提供两个构造函数来实例化 Date 对象

- 第一个构造函数使用当前日期和时间来初始化对象。

  `Date( )`

- 第二个构造函数接收一个参数，该参数是从1970年1月1日起的毫秒数。

  `Date(long millisec)`