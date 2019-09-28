###  项目结构
    lib_audio:音乐播放相关组件  
    lib_common_ui：公用UI组件  
    lib_image_loader：图片处理相关组件  
    lib_network：网络请求封装组件  
    lib_pullalive：应用保活组件  
    lib_qrcode：扫描组件  
    lib_share：分享相关组件  
    lib_update：应用升级组件  
    lib_vidio：视频播放组件  
    lib_webview：封装webview组件  
    
### 统一管理各组件依赖的版本及配置
###### ①项目根目录下创建gradle配置文件music.gradle

```
ext{
    android = [
            compileSdkVersion:28,
            applicationId:'com.example.pursue.musicapp',
            minSdkVersion:19,
            targetSdkVersion:28,
            versionCode:1,
            versionName:'1.0'
    ]

    depsVersion = [
            appcompat:'28.0.0',
            constraint_layout:'1.1.3',
            junit:'4.12',
            runner: '1.0.2',
            espresso_core:'3.0.2'

    ]

    depsLibs = [
            appcompat:"com.android.support:appcompat-v7:${depsVersion.appcompat}",
            constraint_layout:"com.android.support.constraint:constraint-layout:${depsVersion.constraint_layout}",
            junit:"junit:junit:${depsVersion.junit}",
            runner:"com.android.support.test:runner:${depsVersion.runner}",
            espresso_core:"com.android.support.test.espresso:espresso-core:${depsVersion.espresso_core}"
    ]

}
```
##### ②在根目录的build.gradle中引用创建的music.gradle

```
apply from : this.rootProject.file('music.gradle')
```
##### ③修改各组件的build.grale,如：

```
 compileSdkVersion rootProject.android.compileSdkVersion
    defaultConfig {
        applicationId rootProject.android.applicationId
        minSdkVersion rootProject.android.minSdkVersion
        targetSdkVersion rootProject.android.targetSdkVersion
        versionCode rootProject.android.versionCode
        versionName rootProject.android.versionName
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }
```

```
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation rootProject.depsLibs.appcompat
    implementation rootProject.depsLibs.constraint_layout
    testImplementation rootProject.depsLibs.junit
    androidTestImplementation rootProject.depsLibs.runner
    androidTestImplementation rootProject.depsLibs.espresso_core
}
```






  
