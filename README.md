<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/17cc88d8-9c16-4a34-b62a-eabeecddd731" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/081ab5cd-6853-4f56-9615-e091d8eab0d8" />
PS C:\Users\dinak\Downloads\block_blast_audited\block_blast\android> flutter create --platforms=android temp_project
Creating project temp_project...
Resolving dependencies in `temp_project`... (1.1s)
Downloading packages... 
Got dependencies in `temp_project`.
Wrote 35 files.

All done!
You can find general documentation for Flutter at: https://docs.flutter.dev/
Detailed API documentation is available at: https://api.flutter.dev/
If you prefer video documentation, consider: https://www.youtube.com/c/flutterdev

In order to run your application, type:

  $ cd temp_project
  $ flutter run

Your application code is in temp_project\lib\main.dart.

PS C:\Users\dinak\Downloads\block_blast_audited\block_blast\android> xcopy /E /Y temp_project\android block_blast\android\
temp_project\android\.gitignore
temp_project\android\build.gradle.kts
temp_project\android\gradle.properties
temp_project\android\gradlew
temp_project\android\gradlew.bat
temp_project\android\local.properties
temp_project\android\settings.gradle.kts
temp_project\android\temp_project_android.iml
temp_project\android\app\build.gradle.kts
temp_project\android\app\src\debug\AndroidManifest.xml
temp_project\android\app\src\main\AndroidManifest.xml
temp_project\android\app\src\main\java\io\flutter\plugins\GeneratedPluginRegistrant.java
temp_project\android\app\src\main\kotlin\com\example\temp_project\MainActivity.kt
temp_project\android\app\src\main\res\drawable\launch_background.xml
temp_project\android\app\src\main\res\drawable-v21\launch_background.xml
temp_project\android\app\src\main\res\mipmap-hdpi\ic_launcher.png
temp_project\android\app\src\main\res\mipmap-mdpi\ic_launcher.png
temp_project\android\app\src\main\res\mipmap-xhdpi\ic_launcher.png
temp_project\android\app\src\main\res\mipmap-xxhdpi\ic_launcher.png
temp_project\android\app\src\main\res\mipmap-xxxhdpi\ic_launcher.png
temp_project\android\app\src\main\res\values\styles.xml
temp_project\android\app\src\main\res\values-night\styles.xml
temp_project\android\app\src\profile\AndroidManifest.xml
temp_project\android\gradle\wrapper\gradle-wrapper.jar
temp_project\android\gradle\wrapper\gradle-wrapper.properties
25 File(s) copied
PS C:\Users\dinak\Downloads\block_blast_audited\block_blast\android> cd block_blast
PS C:\Users\dinak\Downloads\block_blast_audited\block_blast\android\block_blast> flutter run                                          
Changing current working directory to: C:\Users\dinak\Downloads\block_blast_audited\block_blast
Resolving dependencies... (1.1s)
Downloading packages... 
  _fe_analyzer_shared 85.0.0 (100.0.0 available)
  _flutterfire_internals 1.3.59 (1.3.71 available)
  analyzer 7.6.0 (13.0.0 available)
  analyzer_plugin 0.13.4 (0.14.9 available)
  build 2.5.4 (4.0.6 available)
  build_config 1.1.2 (1.3.0 available)
  build_resolvers 2.5.4 (3.0.4 available)
  build_runner 2.5.4 (2.15.0 available)
  build_runner_core 9.1.2 (9.3.2 available)
  cli_util 0.4.2 (0.5.1 available)
  cloud_firestore 5.6.12 (6.4.1 available)
  cloud_firestore_platform_interface 6.6.12 (8.0.1 available)
  cloud_firestore_web 4.4.12 (5.4.1 available)
  connectivity_plus 6.1.5 (7.1.1 available)
  custom_lint_core 0.7.5 (0.8.2 available)
  custom_lint_visitor 1.0.0+7.7.0 (1.0.0+9.0.0 available)
  dart_style 3.1.1 (3.1.9 available)
  firebase_analytics 11.6.0 (12.4.1 available)
  firebase_analytics_platform_interface 4.4.3 (6.0.1 available)
  firebase_analytics_web 0.5.10+16 (0.6.1+7 available)
  firebase_auth 5.7.0 (6.5.1 available)
  firebase_auth_platform_interface 7.7.3 (9.0.1 available)
  firebase_auth_web 5.15.3 (6.2.1 available)
  firebase_core 3.15.2 (4.9.0 available)
  firebase_core_platform_interface 6.0.3 (7.0.1 available)
  firebase_core_web 2.24.1 (3.7.0 available)
  firebase_crashlytics 4.3.10 (5.2.2 available)
  firebase_crashlytics_platform_interface 3.8.10 (3.8.22 available)
  firebase_storage 12.4.10 (13.4.1 available)
  firebase_storage_platform_interface 5.2.10 (6.0.1 available)
  firebase_storage_web 3.10.17 (3.11.7 available)
  flame_riverpod 5.4.21 (5.5.4 available)
  flutter_launcher_icons 0.13.1 (0.14.4 available)
  flutter_lints 4.0.0 (6.0.0 available)
  flutter_riverpod 2.6.1 (3.3.1 available)
  geocoding 3.0.0 (4.0.0 available)
  geocoding_android 3.3.1 (5.0.1 available)
  geocoding_platform_interface 3.2.0 (5.0.0 available)
  geolocator 12.0.0 (14.0.2 available)
  geolocator_android 4.6.2 (5.0.2 available)
  go_router 14.8.1 (17.2.3 available)
  google_fonts 6.3.3 (8.1.0 available)
  google_mobile_ads 5.3.1 (8.0.0 available)
  google_sign_in 6.3.0 (7.2.0 available)
  google_sign_in_android 6.2.1 (7.2.10 available)
  google_sign_in_ios 5.9.0 (6.3.0 available)
  google_sign_in_platform_interface 2.5.0 (3.1.0 available)
  google_sign_in_web 0.12.4+4 (1.1.3 available)
  intl 0.19.0 (0.20.2 available)
  lints 4.0.0 (6.1.0 available)
  matcher 0.12.19 (0.12.20 available)
  meta 1.17.0 (1.18.2 available)
  native_toolchain_c 0.17.6 (0.18.0 available)
  riverpod 2.6.1 (3.2.1 available)
  riverpod_annotation 2.6.1 (4.0.2 available)
  riverpod_generator 2.6.5 (4.0.3 available)
  source_gen 2.0.0 (4.2.3 available)
  test_api 0.7.10 (0.7.12 available)
  vector_math 2.2.0 (2.3.0 available)
  xml 6.6.1 (7.0.1 available)
Got dependencies!
60 packages have newer versions incompatible with dependency constraints.
Try `flutter pub outdated` for more information.
Launching lib\main.dart on sdk gphone64 x86 64 in debug mode...

FAILURE: Build failed with an exception.

* Where:
Build file 'C:\Users\dinak\Downloads\block_blast_audited\block_blast\android\app\build.gradle' line: 2

* What went wrong:
Plugin [id: 'com.android.application'] was not found in any of the following sources:

- Gradle Core Plugins (plugin is not in 'org.gradle' namespace)
- Included Builds (No included builds contain this plugin)
- Plugin Repositories (plugin dependency must include a version number for this source)

* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.
> Get more help at https://help.gradle.org.

BUILD FAILED in 3s
Running Gradle task 'assembleDebug'...                              4.2s
Error: Gradle task assembleDebug failed with exit code 1
PS C:\Users\dinak\Downloads\block_blast_audited\block_blast\android\block_blast> 
