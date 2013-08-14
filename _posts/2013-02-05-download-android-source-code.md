---
layout: post
title: 批量下载Android源代码
tags: android
---

1.先去https://android.googlesource.com/右下角点txt，保存一份txt文件。重命名为1.txt，放到c盘根目录下。 

2.运行程序
{% highlight java %}
public class git {  
  
    public static void main(String[] args) {  
        String fileName = "C:/1.txt";  
        readFileByLines(fileName);  
    }  
    private static void readFileByLines(String fileName) {  
        try {  
        File file = new File(fileName);  
        BufferedReader reader = null;  
            reader = new BufferedReader( new FileReader(file));  
            String tempString = null;  
            while ((tempString = reader.readLine()) != null) {  
  
                    String gitGet = "git clone https://android.googlesource.com/";  
                    System. out.println(gitGet + tempString);  
                }  
                        reader.close();  
                  } catch (IOException e) {  
                        e.printStackTrace();  
                  }  
            }  
    }  
{% endhighlight %}

将打印出来的内容保存成repourl.txt 

3.安装python，加入到环境变量，将gitbat文件夹移动到python安装目录 Lib\site-package目录下。
将Gitbat.py和repourl.txt一起放到存放android源码的目录下。

4.cmd进入存放android源码的目录下  
`python Gitbat.py -c "git clone" -e`  
生成gitbat.sh文件。

5.复制gitbat.sh中的内容，在存放android源码的目录下打开git bash，粘贴，运行代码.  
用到的资源在这里下载：http://download.csdn.net/detail/joyuan300/4660507