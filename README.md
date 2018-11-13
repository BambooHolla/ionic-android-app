## ionic 打包android环境配置注意点

1. node.js(8.1~8.9版本，除非有需要更高的)
2. jdk(java网站，下载java SE，基本1.8版本，除非有个人需要别的版本)
3. sdk(下载26的，需要配置系统环境变量)
4. gradle(4.6版本，需要配置系统环境变量)
5. cordova 7.0.0版本
6. 新的ionic项目 使用cordova-plugin-crosswalk-webview@2.4.0 用于集成浏览器环境
7. 谷歌发布了com.android.support:support-v4的新版本28.0.0-alpha1,并添加2个新属性(android:fontVariationSettings和android:ttcIndex)。插件使用最新的android支持库，这会导致V4包与compileSdkVersion配置不一致报错。
    1. > 解决办法：cordova plugin add cordova-android-support-gradle-release --fetch
    2. > cordova platform rm android
    3. > cordova platform add android

* 注：由于android 8 系统，将私有空间不再提供使用情况下，使得如果使用热更新，需要把下载的安装包放置于手机目录中，并需要修改`AndroidManifest.xml`中 
```
<uses-sdk android:minSdkVersion="16" android:targetSdkVersion="26" />
改为
<uses-sdk android:minSdkVersion="16" android:targetSdkVersion="23" />
```
