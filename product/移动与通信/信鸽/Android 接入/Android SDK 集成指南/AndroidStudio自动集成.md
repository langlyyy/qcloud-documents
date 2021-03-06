
## 一导入依赖

AndroidStudio上可以使用jcenter远程仓库自动接入，不需要在项目中导入jar包和so文件；
在AndroidManifest.xml中不需要配置信鸽相关的内容，jcenter 会自动导入。
导入依赖过后修改应用配置，书写注册代码就能够实现信鸽快速接入。 
对应的依赖版本号均是，官网上最新的版本。
用户自定义的recevier.依然需要在Androidmianfest.xml配置相关节点。

在app build.gradle文件下配置 以下内容
```
android {
    ......
    defaultConfig {

        //信鸽官网上注册的包名.注意application ID 和当前的应用包名以及 信鸽官网上注册应用的包名必须一致。
        applicationId "你的包名" 
        ......

        ndk {
            //根据需要 自行选择添加的对应cpu类型的.so库。 
            abiFilters 'armeabi', 'armeabi-v7a', 'arm64-v8a' 
            // 还可以添加 'x86', 'x86_64', 'mips', 'mips64'
        }

        manifestPlaceholders = [

            XG_ACCESS_ID:"注册应用的accessid",
            XG_ACCESS_KEY : "注册应用的accesskey",
        ]
        ......
    }
    ......
}

dependencies {
    ......

    //完整的信鸽依赖三个都必须有，如果发生依赖冲突请根据对应的依赖版本号选择高版本的依赖。（使用jcenter自动接入请确认libs 中没有信鸽的相关jar包）



    //采集安装列表
    compile 'com.tencent.xinge:xinge:3.1.2-release' 

    //wup包 
    compile 'com.tencent.wup:wup:1.0.0.E-release'

    //mid包
    compile 'com.tencent.mid:mid:3.9.0-release'
    ......
}
```

>***注意*** 

>如果在添加以上 abiFilter 配置之后android Studio出现以下提示：
>
    NDK integration is deprecated in the current plugin. Consider trying the new experimental plugin.
>则在 Project 根目录的gradle.properties文件中添加：
>
    android.useDeprecatedNdk=true
> 如需监听消息请参考XGBaseReceiver接口或者是demo的MessageReceiver类。自行继承XGBaseReceiver并且在配置文件中配置如下内容：
>
```
  <receiver android:name="完整的类名如:com.qq.xgdemo.receiver.MessageReceiver"
      android:exported="true" >
      <intent-filter>
          <!-- 接收消息透传 -->
          <action android:name="com.tencent.android.tpush.action.PUSH_MESSAGE" />
          <!-- 监听注册、反注册、设置/删除标签、通知被点击等处理结果 -->
          <action android:name="com.tencent.android.tpush.action.FEEDBACK" />
      </intent-filter>
  </receiver>
```

