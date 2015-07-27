# note
记录工作问题

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
