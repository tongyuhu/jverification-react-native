# Tongyuhu-JVerification-React-Native
JVerification-React-Native 官方很久没更新了，内部SDK版本太老，我便fork 官方代码进行了升级。
* 注意：安卓有一些配置UI的属性出现了变化。
```
这里数组中三个字段分别代表协议名称、协议地址、协议前面的分割符
privacyNameAndUrlBeanList: [
    { name: '用户协议', url: 'https://xxx.html', separator: '、', },
    { name: '隐私政策', url: 'https://xxx.html', separator: '、', }
],
/**
* 这个代表两个长度，分别代表首尾
*/
privacyText: ['登录即代表您已阅读并同意', '并授权xxx获得本机号码'],
```

## 1. 安装

```
npm install tongyuhu-jverification-react-native --save
```

* 注意：如果项目里没有tongyuhu-jcore-react-native，需要安装

  ```
  npm install tongyuhu-jcore-react-native --save
  ```

## 2. 配置

### 2.1 Android

* build.gradle

  ```
  android {
        defaultConfig {
            applicationId "yourApplicationId"           //在此替换你的应用包名
            ...
            manifestPlaceholders = [
                    JPUSH_APPKEY: "yourAppKey",         //在此替换你的APPKey
                    JPUSH_CHANNEL: "yourChannel"        //在此替换你的channel
            ]
        }
    }
  ```

  ```
  dependencies {
        ...
        implementation project(':tongyuhu-jverification-react-native') // 添加 jverification 依赖
        implementation project(':tongyuhu-jcore-react-native')         // 添加 jcore 依赖
    }
  ```

* setting.gradle

  ```
  include ':tongyuhu-jverification-react-native'
  project(':tongyuhu-jverification-react-native').projectDir = new File(rootProject.projectDir, '../node_modules/tongyuhu-jverification-react-native/android')
  include ':tongyuhu-jcore-react-native'
  project(':tongyuhu-jcore-react-native').projectDir = new File(rootProject.projectDir, '../node_modules/tongyuhu-jcore-react-native/android')
  ```

### 2.2 iOS

### 2.2.1 pod

```
pod install
```

* 注意：如果项目里使用pod安装过，请先执行命令

  ```
  pod deintegrate
  ```
  
### 2.2.2 配置AppKey

* App.js
```
const initParams = {
    'time': 5000,
    'appKey': 'yourAppKey',               //仅iOS
    'channel': 'channel',                 //仅iOS
    'advertisingId': 'advertisingId',     //仅iOS
    'isProduction': false,                //仅iOS
};
```

## 3. 引用

参考：[App.js](https://github.com/jpush/jverification-react-native/tree/master/example/App.js)

## 4. API
+ API详细说明：[API详细说明.md](https://github.com/jpush/jverification-react-native/blob/master/API%E8%AF%A6%E7%BB%86%E8%AF%B4%E6%98%8E.md) 

+ 授权页面元素配置说明：[认证SDK授权页面元素配置API说明.md](https://github.com/jpush/jverification-react-native/blob/master/%E8%AE%A4%E8%AF%81SDK%E6%8E%88%E6%9D%83%E9%A1%B5%E9%9D%A2%E5%85%83%E7%B4%A0%E9%85%8D%E7%BD%AEAPI%E8%AF%B4%E6%98%8E.md)

+ 示例详见：[index.js](https://github.com/jpush/jverification-react-native/tree/master/index.js)

## 5.  其他

* 集成前务必将example工程跑通
* JVerification2.2.0属于重构版本，如有紧急需求请前往[极光社区](https://community.jiguang.cn/c/question)
* 上报问题还麻烦先调用JVerification.setLoggerEnable( true)，拿到debug日志

 
