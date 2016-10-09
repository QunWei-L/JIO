InputStream 类 inputstream 类和 outputstream 类都为抽象类，不能创建对象，可以通过子类来实例化。
InputStream 是输入字节数据用的类，所以 InputStream 类提供了3种重载的 read 方法.
Inputstream 类中的常用方法：

（1）public abstract int read( )：读取一个 byte 的数据，返回值是高位补0的 int 类型值。
（2）public int read(byte b[ ])：读取 b.length 个字节的数据放到b数组中。返回值是读取的字节数。该方法实际上是调用下一个方法实现的
（3）public int read(byte b[ ], int off, int len)：从输入流中最多读取 len 个字节的数据，存放到偏移量为 off 的 b 数组中。
（4）public int available( )：返回输入流中可以读取的字节数。注意：若输入阻塞，当前线程将被挂起，
        如果 InputStream 对象调用这个方法的话，它只会返回0，这个方法必须由继承 InputStream 类的子类对象调用才有用
（5）public long skip(long n)：忽略输入流中的 n 个字节，返回值是实际忽略的字节数, 跳过一些字节来读取
（6）public int close( ) ：我们在使用完后，必须对我们打开的流进行关闭.


三．OutputStream 类 OutputStream 提供了3个 write 方法来做数据的输出，这个是和 InputStream 是相对应的。

public void write(byte b[ ])：将参数 b 中的字节写到输出流。
public void write(byte b[ ], int off, int len) ：将参数 b 的从偏移量 off 开始的 len 个字节写到输出流。
public abstract void write(int b) ：先将 int 转换为 byte 类型，把低字节写入到输出流中。
public void flush( ) : 将数据缓冲区中数据全部输出，并清空缓冲区。
public void close( ) : 关闭输出流并释放与流相关的系统资源。
注意：上述各方法都有可能引起异常。
InputStream 和 OutputStream 都是抽象类，不能创建这种类型的对象。

四．FileInputStream 类 :
FileInputStream 类是 InputStream 类的子类，用来处理以文件作为数据输入源的数据流。使用方法：

方式1：创建文件位置引用
File fin=new File("d:/abc.txt");
FileInputStream in=new FileInputStream(fin);

方式2：
FileInputStream in=new
FileInputStream("d: /abc.txt");

方式3： 构造函数将 FileDescriptor()对象作为其参数。<front color="#4590a3">//与C语言的文件描述符类似</front>
FileDescriptor fd=new FileDescriptor();
FileInputStream f2=new FileInputStream(fd);



五．FileOutputStream 类：
FileOutputStream 类用来处理以文件作为数据输出目的数据流；一个表示文件名的字符串，也可以是 File 或 FileDescriptor 对象。
创建一个文件流对象有两种方法：

方式1：
File f=new File("d:/abc.txt");
FileOutputStream out=new FileOutputStream (f);

方式2：

FileOutputStream out=new FileOutputStream("d:/abc.txt");

方式3：构造函数将 FileDescriptor()对象作为其参数。

FileDescriptor() fd=new FileDescriptor();
FileOutputStream f2=new FileOutputStream(fd);

方式4：构造函数将文件名作为其第一参数，将布尔值作为第二参数。

FileOutputStream f=new FileOutputStream("d:/abc.txt",true);

注意： （1）文件中写数据时，若文件已经存在，则覆盖存在的文件；
（2）读/写操作结束时，应调用 close 方法关闭流。
举例：2-1

 六．File 类 File 类与 InputStream / OutputStream 类同属于一个包，它不允许访问文件内容。
 File 类主要用于命名文件、查询文件属性和处理文件目录。举例：2-2

 七．从一个流构造另一个流 java 的流类提供了结构化方法，如，底层流和高层过滤流。
 而高层流不是从输入设备读取，而是从其他流读取。
 同样高层输出流也不是写入输出设备，而是写入其他流。
 使用"分层对象(layered objects)"，为单个对象动态地，透明地添加功能的做法，被称为 Decorator Pattern。
 Decorator 模式要求所有包覆在原始对象之外的对象，都必须具有与之完全相同的接口。
 这使得 decorator 的用法变得非常的透明--无论对象是否被 decorate 过，传给它的消息总是相同的。

 这也是 Java I/O 类库要有"filter(过滤器)"类的原因：
 抽象的"filter"类是所有 decorator 的基类。
 Decorator 模式常用于如下的情形：如果用继承来解决各种需求的话，类的数量会多到不切实际的地步。
 Java 的 I/O 类库需要提供很多功能的组合，于是 decorator 模式就有了用武之地。
 为 InputStream 和 OutputStream 定义 decorator 类接口的类，分别是 FilterInputStream 和 FilterOutputStream。


 DataOutputStream 类对象可以写各种类型的数据； 创建这两类对象时，必须使新建立的对象指向构造函数中的参数对象。例如：

 FileInputStream in=new FileInputStream("d:/abc.txt");
 DataInputStream din=new DataInputStream(in);


 BufferInputStream 和 bufferOutputStream 允许程序在不降低系统性能的情况下一次一个字节的从流中读取数据。
 BufferInputstream 定义了两种构造函数
 （1）BufferInputStream b= new BufferInputstream(in);
 （2）BufferInputStream b=new BufferInputStream(in,size) 第二个参数表示指定缓冲器的大小。

 同样 BufferOutputStream 也有两种构造函数。一次一个字节的向流中写数据。

 7.3printstream 用于写入文本或基本类型 两种构造函数方法：
 PrintStream ps=new PrintStream(out);
 PrintStream ps=new PrintStream(out, autoflush) 第二个参数为布尔值，控制每次输出换行符时 java 是否刷新输出流。


 八．字符流的读取和写入 java.io.Reader 和 java.io.InputStream 组成了 Java 输入类。
 Reader 用于读入16位字符，也就是 Unicode 编码的字符；而 InputStream 用于读入 ASCII 字符和二进制数据。


 Reader 体系结构 （1）FileReader FileReader 主要用来读取字符文件，使用缺省的字符编码，有三种构造函数：

 --将文件名作为字符串
 FileReader f=new FileReader(“c:/temp.txt”);

 --构造函数将 File 对象作为其参数。
 File f=new file(“c:/temp.txt”);
 FileReader f1=new FileReader(f);


 --构造函数将 FileDescriptor 对象作为参数
 FileDescriptor() fd=new FileDescriptor()
 FileReader f2=new FileReader(fd);


 (2)
 charArrayReader 将字符数组作为输入流,构造函数为：
 public CharArrayReader(char[] ch);

 (3)StringReader 读取字符串，构造函数如下：
 public StringReader(String s);

 (4)InputStreamReader 从输入流读取字节，在将它们转换成字符。
 Public inputstreamReader(inputstream is);

 (5)FilterReader 允许过滤字符流
 protected filterReader(Reader r);

 (6)BufferReader 接受 Reader 对象作为参数，并对其添加字符缓冲器，使用readline()方法可以读取一行。
 Public BufferReader(Reader r);




 DataInputStream 类对象可以读取各种类型的数据。 DataOutputStream 类对象可以写各种类型的数据；
 创建这两类对象时，必须使新建立的对象指向构造函数中的参数对象。例如：

 FileInputStream in=new FileInputStream("d:/abc.txt");
 DataInputStream din=new DataInputStream(in);

 7.2BufferInputStream 和 bufferOutputStream 允许程序在不降低系统性能的情况下一次一个字节的从流中读取数据。
 BufferInputstream 定义了两种构造函数
 （1）BufferInputStream b= new BufferInputstream(in);
 （2）BufferInputStream b=new BufferInputStream(in,size) 第二个参数表示指定缓冲器的大小。
 同样 BufferOutputStream 也有两种构造函数。一次一个字节的向流中写数据。

 7.3printstream 用于写入文本或基本类型
 两种构造函数方法：
 PrintStream ps=new PrintStream(out);
 PrintStream ps=new PrintStream(out, autoflush) 第二个参数为布尔值，控制每次输出换行符时 java 是否刷新输出流