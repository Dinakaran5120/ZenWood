PS C:\Users\dinak\Downloads\block_blast_complete\block_blast> flutter run 
Connected devices:
Windows (desktop) • windows • windows-x64    • Microsoft Windows [Version 10.0.26200.8457]
Chrome (web)      • chrome  • web-javascript • Google Chrome 148.0.7778.168
Edge (web)        • edge    • web-javascript • Microsoft Edge 148.0.3967.70
[1]: Windows (windows)
[2]: Chrome (chrome)
[3]: Edge (edge)
Please choose one (or "q" to quit): 1
Launching lib\main.dart on Windows in debug mode...
Error: Unable to find suitable Visual Studio toolchain. Please run `flutter doctor` for more details.
PS C:\Users\dinak\Downloads\block_blast_complete\block_blast> flutter run 
Launching lib\main.dart on sdk gphone64 x86 64 in debug mode...
lib/core/analytics/analytics_service.dart:5:8: Error: Error when reading 'lib/core/admob/admob_service.dart': The system cannot find the path specified
import '../admob/admob_service.dart';
       ^
lib/core/analytics/analytics_service.dart:88:32: Error: Type 'AdType' not found.
  Future<void> logAdImpression(AdType type) async {
                               ^^^^^^
lib/core/analytics/analytics_service.dart:95:28: Error: Type 'AdType' not found.
  Future<void> logAdReward(AdType type, int coins) async {
                           ^^^^^^
lib/core/analytics/analytics_service.dart:88:32: Error: 'AdType' isn't a type.
  Future<void> logAdImpression(AdType type) async {
                               ^^^^^^
lib/core/analytics/analytics_service.dart:95:28: Error: 'AdType' isn't a type.
  Future<void> logAdReward(AdType type, int coins) async {
                           ^^^^^^
lib/features/admob/admob_service.dart:319:1: Error: Directives must appear before any declarations.
Try moving the directive before any declarations.
import 'package:flutter/material.dart';
^^^^^^
lib/features/admob/admob_service.dart:42:9: Error: Type 'AnalyticsService' not found.
  final AnalyticsService _analytics;
        ^^^^^^^^^^^^^^^^
lib/features/admob/admob_service.dart:343:30: Error: Undefined name 'analyticsServiceProvider'.
  final analytics = ref.read(analyticsServiceProvider);
                             ^^^^^^^^^^^^^^^^^^^^^^^^
lib/features/admob/admob_service.dart:42:9: Error: 'AnalyticsService' isn't a type.
  final AnalyticsService _analytics;
        ^^^^^^^^^^^^^^^^
Target kernel_snapshot_program failed: Exception
FAILURE: Build failed with an exception.
* What went wrong:
Execution failed for task ':app:compileFlutterBuildDebug'.
> Process 'command 'C:\Users\dinak\flutter_windows_3.41.7-stable\flutter\bin\flutter.bat'' finished with non-zero exit value 1
* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.
> Get more help at https://help.gradle.org.
BUILD FAILED in 40s
Running Gradle task 'assembleDebug'...                             41.1s
Error: Gradle task assembleDebug failed with exit code 1
PS C:\Users\dinak\Downloads\block_blast_complete\block_blast>
