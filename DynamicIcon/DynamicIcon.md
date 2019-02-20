��̬����ͼ����Ҫ�õ�**activity-alias**��**PackageManager��setComponentEnabledSetting����**�����岽�����£�

###1����AndroidManifest.xml��������������:

    <activity-alias
            android:name=".alias"
            android:enabled="false"
            android:icon="@mipmap/icon"
            android:label="Alias"
            android:targetActivity=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
    </activity-alias>

�����ļ�����:

    <?xml version="1.0" encoding="utf-8"?>
	<manifest xmlns:android="http://schemas.android.com/apk/res/android"
	    package="com.wangyz.dynamicicon">
	
	    <application
	        android:allowBackup="true"
	        android:icon="@mipmap/ic_launcher"
	        android:label="@string/app_name"
	        android:roundIcon="@mipmap/ic_launcher_round"
	        android:supportsRtl="true"
	        android:theme="@style/AppTheme">
	        <activity android:name=".MainActivity">
	            <intent-filter>
	                <action android:name="android.intent.action.MAIN" />
	
	                <category android:name="android.intent.category.LAUNCHER" />
	            </intent-filter>
	        </activity>
	        <activity-alias
	            android:name=".alias"
	            android:enabled="false"
	            android:icon="@mipmap/icon"
	            android:label="Alias"
	            android:targetActivity=".MainActivity">
	            <intent-filter>
	                <action android:name="android.intent.action.MAIN" />
	
	                <category android:name="android.intent.category.LAUNCHER" />
	            </intent-filter>
	        </activity-alias>
	    </application>
	
	</manifest>

###2���л�ͼ��

    getPackageManager().setComponentEnabledSetting(getComponentName(),
                PackageManager.COMPONENT_ENABLED_STATE_DISABLED,
                PackageManager.DONT_KILL_APP);
    getPackageManager().setComponentEnabledSetting(new ComponentName(this,
                        getPackageName() + ".alias"),
                PackageManager.COMPONENT_ENABLED_STATE_ENABLED,
                0);

setComponentEnabledSetting���������һ��������PackageManager.DONT_KILL_APP��ʾ���ر�App��0��ʾ�ر�Appˢ��ͼ�ꡣ

�����ļ�����:

    package com.wangyz.dynamicicon;

	import android.content.ComponentName;
	import android.content.pm.PackageManager;
	import android.os.Bundle;
	import android.support.v7.app.AppCompatActivity;
	import android.view.View;
	
	public class MainActivity extends AppCompatActivity {
	
	    @Override
	    protected void onCreate(Bundle savedInstanceState) {
	        super.onCreate(savedInstanceState);
	        setContentView(R.layout.activity_main);
	    }
	
	    public void changeIcon(View view) {
	        getPackageManager().setComponentEnabledSetting(getComponentName(),
	                PackageManager.COMPONENT_ENABLED_STATE_DISABLED,
	                PackageManager.DONT_KILL_APP);
	        getPackageManager().setComponentEnabledSetting(new ComponentName(this,
	                        getPackageName() + ".MainActivity"),
	                PackageManager.COMPONENT_ENABLED_STATE_ENABLED,
	                0);
	    }
	
	    public void changeIconAlias(View view) {
	        getPackageManager().setComponentEnabledSetting(getComponentName(),
	                PackageManager.COMPONENT_ENABLED_STATE_DISABLED,
	                PackageManager.DONT_KILL_APP);
	        getPackageManager().setComponentEnabledSetting(new ComponentName(this,
	                        getPackageName() + ".alias"),
	                PackageManager.COMPONENT_ENABLED_STATE_ENABLED,
	                0);
	    }
	}
