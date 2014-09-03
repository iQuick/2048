2048
====

2048有你好看

## 引言

		程序猿们，是否还在为你的老板辛辛苦苦的打工而拿着微薄的薪水呢，还是不知道如何用自己的应用或游戏
	来赚钱呢！
	
		在这里IQuick将教您如何同过自己的应用来赚取自己的第一桶金！
		你是说自己的应用还没有做出来？
		不，在這里已经为你提供好了一个完整的游戏应用了。你只要稍做修改就可以变成一个完全属于自己的应用
	了，比如将4*4换成5*5，甚至是其它的。如果你实在是慵懒至极的话，你只要将本应用的包名及广告换成自己的，
	就可以上传到市场上轻轻松松赚取自己的第一桶金了。
	
		如果你觉得本文很赞的话，就顶一下作者吧，从下面的安装地址中下载应用，或者在导入本工程运行的时候，
	从广告中安装一个应用。动一动你的手指，就能让作者更进一步，也能让作者以后更加有动力来分享吧。
	
## 安装

[安智](http://apk.hiapk.com/appinfo/tk.woppo.mgame)

## 预览

![2048](https://github.com/iQuick/2048/blob/master/art/1.png) ![2048](https://github.com/iQuick/2048/blob/master/art/2.png)
![2048](https://github.com/iQuick/2048/blob/master/art/3.png) ![2048](https://github.com/iQuick/2048/blob/master/art/4.png)

## 项目结构

![2048](https://github.com/iQuick/2048/blob/master/art/6.png)

## 如何加载广告

	将项目结构上提到的对应平台的广告Lib加入到项目中
	
	在AndroidManifest.xml中加入权限及必要组件
	============
		<!--需要添加的权限  -->
		<uses-permission android:name="android.permission.INTERNET" />
		<uses-permission android:name="android.permission.READ_PHONE_STATE" /><!-- ismi -->
		<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
		<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
		<uses-permission android:name="android.permission.GET_TASKS" /><!-- TimeTask -->
		<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" /><!-- WindowManager -->
		<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
		<supports-screens android:anyDensity="true" />
	
	==============
	    <!-- 酷果广告组件 -->
        <activity android:name="com.phkg.b.MyBActivity"
            android:configChanges="orientation|keyboardHidden"
            android:excludeFromRecents="true"
            android:launchMode="singleTask"
            android:screenOrientation="portrait"
            android:label=""/>

        <receiver android:name="com.phkg.b.MyBReceive">
            <intent-filter>
                <action android:name="android.intent.action.PACKAGE_ADDED" />
                <data android:scheme="package" />
            </intent-filter>
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
            </intent-filter>
        </receiver>

        <!-- 有米广告组件 -->
        <activity android:name="net.youmi.android.AdBrowser" 
			android:configChanges="keyboard|keyboardHidden|orientation|screenSize"
            android:theme="@android:style/Theme.Light.NoTitleBar" >
        </activity>
        <service 
			android:name="net.youmi.android.AdService"  
			android:exported="false" >
        </service>
        <receiver android:name="net.youmi.android.AdReceiver" >
            <intent-filter>
                <action android:name="android.intent.action.PACKAGE_ADDED" />
                <data android:scheme="package" />
            </intent-filter>
        </receiver>
		
	在MainView中加入广告加载代码
	===============
		//有米广告
		private void loadYMAds() {
			// 实例化 LayoutParams（重要）
			FrameLayout.LayoutParams layoutParams = new FrameLayout.LayoutParams( 
				FrameLayout.LayoutParams.FILL_PARENT, FrameLayout.LayoutParams.WRAP_CONTENT);

			// 设置广告条的悬浮位置
			layoutParams.gravity = Gravity.BOTTOM | Gravity.RIGHT; // 这里示例为右下角
			// 实例化广告条
			AdView adView = new AdView(this, AdSize.FIT_SCREEN);
			adView.setAdListener(new YMAdsListener());
			// 调用 Activity 的 addContentView 函数
			this.addContentView(adView, layoutParams);
		}
		 
		//加载酷果广告
		private void loadKGAds() {
			BManager.showTopBanner(MainActivity.this, BManager.CENTER_BOTTOM, 
				BManager.MODE_APPIN, Const.COOID, Const.QQ_CHID);
			BManager.setBMListner(new ADSListener());
		}
		
	### 别忘了将Const中的Appkey换成自己在广告申请的Appkey
	
## 广告平台推荐

	有米(如果想加入有米广告，力荐从此链接注册，有惊喜等着你哦)
[https://www.youmi.net/account/register?r=NDg0ODA=](https://www.youmi.net/account/register?r=NDg0ODA=)
	
	酷果
[http://www.kuguopush.com/](http://www.kuguopush.com/)
	
## 导入

	如果是Android Studio的话可以直接导入。
	
	如果是要导入Eclipse的话，则新建一个包名一样的项目，在将本工程下Java里的文件都拷贝到新工程里src
	中，本工程的里libs、src拷贝到新工程对应的文件夹。
	并将本工程里的AndroidManifest.xml文件覆盖新项目AndroidManifest.xml文件。
	至此你就可以迁移完毕，你可以运行游戏了。
	
## 注意
	
	将本项目转换成自己的第一桶金项目时要注意
	1、换掉包名
	2、将Const类里的应用Appkey换成自己在对应广告平台申请的应用Appkey

License
============

    Copyright 2014 IQuick

	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.
