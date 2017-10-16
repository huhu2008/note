# note
记录工作问题

SDK下载地址：http://mirrors.neusoft.edu.cn/android/repository/

今天上传文件的时候用了MultipartEntityBuilder，添加了httpcore等2个依赖库，编译运行的时候，studio出现一个奇怪的错误提示：

Duplicate files copied in APK META-INF/DEPENDENCIES
File 1: /home/bluelife/.gradle/caches/modules-2/files-2.1/org.apache.httpcomponents/httpmime/4.3.1/f7899276dddd01d8a42ecfe27e7031fcf9824422/httpmime-4.3.5.jar
File 2: /home/bluelife/.gradle/caches/modules-2/files-2.1/org.apache.httpcomponents/httpmime/4.3.1/f7899276dddd01d8a42ecfe27e7031fcf9824422/httpmime-4.3.5.ja


不知道哪里出错，最后Google找到了解决方法。

需要在build.gradle文件里添加如下配置：

android {

    packagingOptions {
    
        exclude 'META-INF/DEPENDENCIES'
        exclude 'META-INF/NOTICE'
        exclude 'META-INF/LICENSE'
        exclude 'META-INF/LICENSE.txt'
        exclude 'META-INF/NOTICE.txt'
        
    }
    // ...
    
}

2015/4/3

Picasso缓存路径


PICASSO_CAcHCE="picasso-cache";

public static File createDefaultCacheDir(Context context){


   File cache = new File (context.getApplicationContext().getCatcheDir(),PICASSO_CACHE);
   
   if(cathce.exists()){
   
     cachce.mkdirs();
   
   }

      return cache;
      
 }


面试题集合 http://www.apkbus.com/android-115989-1-1.html
http://www.doc88.com/p-2035575757579.html

查找字符串中的url

 Pattern pattern=Pattern.compile("(http://|ftp://|https://|www){0,1}[^\u4e00-\u9fa5\\s]*?\\.(com|net|cn|me|tw|fr)[^\u4e00-\u9fa5\\s]*");

        Matcher matcher=pattern.matcher(mbody);

        while  (matcher.find()){

            HttpLog.Log("扫描结果为网址！" + matcher.group());

            mbody= mbody.replace(matcher.group(),"<a href=" + matcher.group() + ">链接>></a>");

        }
        

给Textview添加超链接的几种方法

http://blog.sina.com.cn/s/blog_7cd0c0a801014o5b.html

AsyncHttpClient  用https方式：



       client = new AsyncHttpClient();
        // using a socket factory that allows self-signed SSL certificates.
        client.setSSLSocketFactory(MySSLSocketFactory.getFixedSocketFactory());
        client.get("https://apollo.localnet:9292/", new AsyncHttpResponseHandler() {
           ....
        }
        
        http://download.csdn.net/download/fuyanai/9088575
        
        
        
 
android 7.0系统解决拍照的问题:


除了解决方案之外FileProvider，还有另一种解决方法。简单的说

StrictMode.VmPolicy.Builder builder = new StrictMode.VmPolicy.Builder();
StrictMode.setVmPolicy(builder.build());
在Application.onCreate()。以这种方式，VM会忽略文件URI曝光。

方法

builder.detectFileUriExposure()
启用文件曝光检查，如果我们没有设置VmPolicy，这也是默认行为。
