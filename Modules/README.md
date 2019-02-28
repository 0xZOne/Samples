# �������������Ҫ���裺

### һ���½�Modules

1���½�Project,��ΪӦ�õ���Module��

2���½�Module:"Common"������ѡ��"Android Library",��Ϊ��������Module�Ļ��������⡣

3���½�Module:"Home"������ѡ��"Android Library",����"Common"��

4���½�Module:"Project"������ѡ��"Android Library",����"Common"��

5���½�Module:"User"������ѡ��"Android Library",����"Common"��

**�����½�������Module�����Ը���ʵ��ҵ��������������ѡ���½�"Home"��"Project"��"User"��ģ��ҵ��**

### ��������Flag�Ա���release��debugģʽ���л�

**1����gradle.properties�ļ�������һ������**

    isDebug = false

![flag.png](https://upload-images.jianshu.io/upload_images/3381990-ba4cca25a5fa0501.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**��isDebugΪtrueʱ��ΪDebugģʽ��������Module������Ϊ������App���С���isDebugΪfalseʱ��ΪReleaseģʽ��������ModuleΪLibraryģʽ�����ܵ�������,��ʱֻ����App�������С�**

**2���޸�app��build.gradle�ļ�**

    implementation project(':common')
    if (!isDebug.toBoolean()) {
        implementation project(':home')
        implementation project(':project')
        implementation project(':user')
    }

![app_flag.png](https://upload-images.jianshu.io/upload_images/3381990-527cfa0ff9e9e29b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**3���޸�home��build.gradle�ļ�**

    if (isDebug.toBoolean()) {
	    apply plugin: 'com.android.application'
	} else {
	    apply plugin: 'com.android.library'
	}

![home_flag.png](https://upload-images.jianshu.io/upload_images/3381990-772b26caf4703d31.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**4���޸�project��build.gradle�ļ�**

    if (isDebug.toBoolean()) {
	    apply plugin: 'com.android.application'
	} else {
	    apply plugin: 'com.android.library'
	}

![project_flag.png](https://upload-images.jianshu.io/upload_images/3381990-7c724ab1c7beb40c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**5���޸�user��build.gradle�ļ�**

    if (isDebug.toBoolean()) {
	    apply plugin: 'com.android.application'
	} else {
	    apply plugin: 'com.android.library'
	}

![user_flag.png](https://upload-images.jianshu.io/upload_images/3381990-b259028ccc40ef1c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### Ϊ���ڸ�Module�������Կ����������ڸ�Module�¸���isDebug�ı�������ģʽ��

�л����̵�Projectģʽ�£���ԭ����AndroidManifest.xml�ļ��Ƴ�����Module��srcĿ¼���½�debug��releaseĿ¼�����½�������Ŀ¼�£��ֱ��½�AndroidManifest.xml�ļ�����Homeģ��Ϊ����

![home_manifest.png](https://upload-images.jianshu.io/upload_images/3381990-859a2e9d3286e5cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**Debugģʽ�µ�AndroidManifest.xml**

![home_debug_manifest.png](https://upload-images.jianshu.io/upload_images/3381990-e908c187b36f0479.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**Releaseģʽ�µ�AndroidManifest.mxl**

![home_release_manifest.png](https://upload-images.jianshu.io/upload_images/3381990-d77a62d53186f828.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


��Home�µ�build.gradle�ļ�������AndroidManifest.xml

    sourceSets {
        main {
            if (isDebug.toBoolean()) {
                manifest.srcFile 'src/debug/AndroidManifest.xml'
            } else {
                manifest.srcFile 'src/release/AndroidManifest.xml'
                java { exclude 'debug/**' }
            }
        }
    }


![home_gradle_source.png](https://upload-images.jianshu.io/upload_images/3381990-a4ab6113a8372490.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


����ModuleҲ�����ƵĴ���


### ����ͳһ����Module�汾��

1��Ϊ����ͳһ����汾�ţ�����Ŀ�ĸ�Ŀ¼�µ�build.gradle�ļ�������ͳһ�İ汾��:

    ext {
	    compileSdkVersion = 28
	
	    minSdkVersion = 21
	    targetSdkVersion = 28
	    versionCode = 1
	    versionName = "1.0"
	}

![version.png](https://upload-images.jianshu.io/upload_images/3381990-d9f695ecf08c0158.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


2��������Module����Ӧ�޸�

**Appģ��:**

![app_version.png](https://upload-images.jianshu.io/upload_images/3381990-1189de646a14b7cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**Commonģ��:**

![common_version.png](https://upload-images.jianshu.io/upload_images/3381990-3cf02be42e527ff3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**Homeģ��:**

![home_version.png](https://upload-images.jianshu.io/upload_images/3381990-002f4c055092b0c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**Projectģ��:**

![project_version.png](https://upload-images.jianshu.io/upload_images/3381990-4b83cc48cbef2858.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**Userģ��:**

![user_version.png](https://upload-images.jianshu.io/upload_images/3381990-d109a2ccaebf2d05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### �ġ���Module��ͨ��

Ϊ�����Module��ͨ�ŵ����⣬����ARouter��ܡ�GitHub��ַ��[ARouter](https://github.com/alibaba/ARouter "ARouter")

Ϊ�����Module�ظ����ã���Common������һ�Σ�����Module���ü��ɡ�

![common_arouter.png](https://upload-images.jianshu.io/upload_images/3381990-63ca33cec654c55c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**ע�⣺������������Common��ModuleҲ��Ҫʹ��Arouter�����������ʱ����Ҫ��implementation��Ϊapi�����ʹ��implementation,����Module���޷�ʹ��Arouter��**

����Module��ʹ��:

����Ҫ�ٴ�implementation,���ǻ�����Ҫ��dependencies����

    annotationProcessor 'com.alibaba:arouter-compiler:1.2.2'

�Լ���android-defaultConfig�����ӣ�

	javaCompileOptions {
            annotationProcessorOptions {
                arguments = [AROUTER_MODULE_NAME: project.getName()]
            }
        }    

ע�⣺"AROUTER_MODULE_NAME"������ƣ������Ը�Ϊ�����ַ������������뱨��

![home_arouter.png](https://upload-images.jianshu.io/upload_images/3381990-c274f6834a4c0c00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


��Commonģ��������BaseApplication,��ARouter���г�ʼ����

    public class BaseApplication extends Application {

	    private boolean isDebugARouter = true;
	
	    @Override
	    public void onCreate() {
	        super.onCreate();
	
	        if (isDebugARouter) {
	            ARouter.openLog();
	            ARouter.openDebug();
	        }
	        ARouter.init(this);
	    }
	}

����Module:App������App,�̳���BaseApplication,Ȼ����AndroidManifefst.xml�����á�

>    `public class App extends BaseApplication {}`

    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
	    xmlns:tools="http://schemas.android.com/tools"
	    package="com.wangyz.modules">
	
	    <application
	        android:name=".App"
	        android:allowBackup="true"
	        android:appComponentFactory="whateverString"
	        android:icon="@mipmap/ic_launcher"
	        android:label="@string/app_name"
	        android:roundIcon="@mipmap/ic_launcher_round"
	        android:supportsRtl="true"
	        android:theme="@style/AppTheme"
	        tools:replace="android:appComponentFactory">
	
	        <activity android:name=".MainActivity">
	            <intent-filter>
	                <action android:name="android.intent.action.MAIN" />
	                <category android:name="android.intent.category.LAUNCHER" />
	            </intent-filter>
	        </activity>
	
	    </application>
	</manifest>

������Ҫ�����õ�Activity����Fragment����ע�⣺

![home_route.png](https://upload-images.jianshu.io/upload_images/3381990-9fe806ab55f395f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**�����½�һ�������࣬����������Щ·�ɵ�ַ��������ڼ򻯣�û���ٶ�����������ࡣ**

#### ���÷�ʹ��ARouter��

    Fragment fragment = (Fragment) ARouter.getInstance().build("/home/fragment").navigation();
    mFragmentManager.beginTransaction().replace(R.id.container, fragment).commit();

![app_arouter.png](https://upload-images.jianshu.io/upload_images/3381990-1486accfe0e539c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### �塢ButterKnife������

ButterKnife�ڵ�Module��ʹ��ʱ���Ƚϼ򵥣����ڶ�Module��ʹ��ʱ��������Щ��Ҫע�������������ò�������:

**1������Ŀ��Ŀ¼��build.gradle����������:**

	dependencies {
	        classpath 'com.android.tools.build:gradle:3.1.4'
	        classpath 'com.jakewharton:butterknife-gradle-plugin:9.0.0'
	
	        // NOTE: Do not place your application dependencies here; they belong
	        // in the individual module build.gradle files
	    }

![root_gradle.png](https://upload-images.jianshu.io/upload_images/3381990-3a9be6f741385005.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


��common����������:

    api 'com.jakewharton:butterknife:9.0.0'
    annotationProcessor 'com.jakewharton:butterknife-compiler:9.0.0'

![common_butterknife.png](https://upload-images.jianshu.io/upload_images/3381990-8baa5b8a03e8d093.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


�ھ���ʹ��ButterKnife��Module����������:

    apply plugin: 'com.jakewharton.butterknife'
	
	annotationProcessor 'com.jakewharton:butterknife-compiler:9.0.0'


![home_butterknife_1.png](https://upload-images.jianshu.io/upload_images/3381990-cf6f9c1df6263c7e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![home_butterknife_2.png](https://upload-images.jianshu.io/upload_images/3381990-ba45575d98034b3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


��ARouterһ����ʹ��ButterKnife��Module��Ȼ�����ظ�����butterknife��������⣬����ע����صĿ⻹����Ҫ���á�

����ʹ�ã�

    @BindView(R2.id.click)
    TextView mText;

**BindView��ʱ����Ҫʹ��R2.id.xx**

	@OnClick(R2.id.click)
    public void click() {
        Toast.makeText(getActivity().getApplicationContext(), "click", Toast.LENGTH_SHORT).show();
    }

**��Ӧ�ĵ���¼��ȣ�����ǵ���ʹ�ã�Ҳ��ʹ��R2.id.xx������Ƕ��idһ��ʹ�ã��ڲ�ͨ��id���жϣ�����Ҫʹ��if...else if...������ʹ��switch...case������if�жϵ�id��Ҫʹ��R.id.xx**

**Ĭ���ǻᱨ���Ҳ���R2��ص�class����Ҫ�ֶ�buildһ�βŻ����ɡ�**

**ע�⣺ButterKnife.9.0�Ժ���Ҫjdk�汾1.8���ϣ��������ᱨ��**



