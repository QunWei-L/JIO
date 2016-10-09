
#IO:http://ifeve.com/java-io/
wiki: http://wiki.jikexueyuan.com/project/java-special-topic/io.html

领域:标准输入输出，文件的操作，网络上的数据流，字符串流，对象流，zip 文件流...

当程序需要读取数据的时候，就会开启一个通向数据源的流，这个数据源可以是文件，内存，或是网络连接。
JDK 所提供的所有流类位于 java.io 包中，都分别继承自以下四种抽象流类：

字节流：读取二进制数据，如图象和声音。
InputStream：继承自 InputStream 的流都是用于向程序中输入数据的，且数据单位都是字节（8位）。
OutputSteam：继承自 OutputStream 的流都是程序用于向外输出数据的，且数据单位都是字节（8位）。

字符流：国际化的字符集，Unicode。
Reader：继承自 Reader 的流都是用于向程序中输入数据的，且数据单位都是字符（16位）。
Writer：继承自 Writer 的流都是程序用于向外输出数据的，且数据单位都是字符（16位）。

"适配器(adapter)"类：
InputStreamReader 负责将 InputStream 转化成 Reader，
OutputStreamWriter 则将 OutputStream 转化成 Writer。



#NIO:
http://ifeve.com/java-nio-all/
http://blog.csdn.net/shimiso/article/details/24990499
http://www.ibm.com/developerworks/cn/education/java/j-nio/



#Netty:http://wiki.jikexueyuan.com/project/java-special-topic/netty.html

#压力测试：
https://www.ibm.com/developerworks/cn/opensource/os-pressiontest/
http://sunjia-704471770-qq-com.iteye.com/blog/2282141
http://blog.jassassin.com/2014/04/17/tools/jmeter/


Temp:

MySQL全文检索中Like索引的实现:http://database.51cto.com/art/200908/144024.htm (兼容移动端)
站内搜索:http://www.dreamdu.com/webbuild/baidu_search/
Java_sql:http://database.51cto.com/art/201503/468891.htm
DB:http://database.51cto.com/col/587/
