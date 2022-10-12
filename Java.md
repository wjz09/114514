# 1.图形界面编程

## 文件输入输出

### 源码部分解析

> 引入什么包：
>
> awt ：图形界面GUI，下有组件，容器，布局管理
>
> awt.event : 提供处理由 AWT 组件所激发的各类事件的接口和类，包含有源对象，监视器对象，事件对象
>
> swing：包括了图形用户界面（GUI）器件如：文本框，按钮，分隔窗格和表
>
> swing.filechooser : 文件选择
>
> io： 以数据流形式读写文件



>主类继承问题：
>
>继承了Frame类的子类JFrame，同时又继承了事件监听接口ActionListener



>实例对象初始化问题：
>
>1. JFileChooser：选择文件
>
>方法：JFileChooser.APPROVE_OPTION 是否确认该选项
>
>   2.菜单的构成：
>
>JMenu：菜单							
>
>JMenuItem：菜单选项
>
>JMenuBar：菜单条		实现此方法还需setJMenuBar(JMenuBar J);
>
>>步骤:
>>
>>先将菜单实JMenu实例化，并赋值	“这个大的菜单选项是干嘛的”
>>
>>然后将JMenuItem菜单选项实例化赋值，“上面的大菜单下设的几个或多个小菜单的名称”，之后调用JMenuItem的事件监听方法，.addActionListener(this)，以触发对应的小项点击后的事件
>>
>>最后需要逐步将菜单选项添加至菜单中，之后将菜单添加至可以显示的菜单条中
>
>3.文本域:
>
>JTextarea:构造方法中传入（行数，列数）
>
>.setFont(new Font("楷体_gb2312",Font.PLAIN,28))//	字体、PLAIN：常规类，BOLD :粗体样式常量 ,ITALIC: 斜体样式常量、字体大小
>
>另一种写法：
>
>```java
>Font t= new Font("楷体_gb2312",Font.PLAIN,28);
>        text.setFont(t);
>```
>
>.getText：获取已提交文本和撰写文本的组合
>
>.setText：设定此文本为目标文本
>
>.append：将给定文本追加到文本区的当前文本
>
>4.流
>
>BufferReader: 字符输入流中读取文本，==缓冲==各个字符，从而实现字符、数组和行的高效读取
>
>> 通俗的来讲就是数据传输时需要将写入或者读出的文本先传输到指定的流中
>>
>> 实例化之后使用ReadLine方法可以单行读取文件。.write方法可以实现写入操作
>
>FileReader：用来读取字符文件
>
>



>主类调用的方法：
>
>setSize(宽，高) //设定
>
>setVisible：如果为 true，则显示此组件
>
>### **setDefaultCloseOperation**：设置用户在此内部窗体上发起 "close" 时默认执行的操作
>
>默认为
>
>​	```setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);```
>
>