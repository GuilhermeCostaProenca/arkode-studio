C:\Users\labsfiap\Desktop\gscrossplataform>flutter run
Connected devices:
Windows (desktop) • windows • windows-x64    • Microsoft Windows [Version 10.0.26100.4351]
Chrome (web)      • chrome  • web-javascript • Google Chrome 136.0.7103.93
Edge (web)        • edge    • web-javascript • Microsoft Edge 142.0.3595.80
[1]: Windows (windows)
[2]: Chrome (chrome)
[3]: Edge (edge)
Please choose one (or "q" to quit): 2
Launching lib\main.dart on Chrome in debug mode...
Waiting for connection from debug service on Chrome...              6.0s
This app is linked to the debug service: ws://127.0.0.1:58883/tnYTb7zhF3s=/ws
Debug service listening on ws://127.0.0.1:58883/tnYTb7zhF3s=/ws

Flutter run key commands.
R Hot restart.
h List all available interactive commands.
d Detach (terminate "flutter run" but leave application running).
c Clear the screen
q Quit (terminate the application on the device).

A Dart VM Service on Chrome is available at: http://127.0.0.1:58883/tnYTb7zhF3s=
Error: TypeError: Failed to fetch dynamically imported module:
https://www.gstatic.com/flutter-canvaskit/dd93de6fb1776398bf586cbd477deade1391c7e4/chromium/canvaski
t.js

Dart stack trace:
Non-error `null` thrown by JS does not have stack trace.
Caught in Dart at:


dart-sdk/lib/_internal/js_shared/lib/js_util_patch.dart 306:16                    callConstructor   
dart-sdk/lib/_internal/js_shared/lib/js_interop_unsafe_patch.dart 94:17
JSFunctionUnsafeUtilExtension._callAsConstructor
dart-sdk/lib/js_interop_unsafe/js_interop_unsafe.dart 115:9
JSFunctionUnsafeUtilExtension.callAsConstructor
lib/_engine/engine/js_interop/js_promise.dart 29:46                               <fn>
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 741:5
[_completeErrorObject]
dart-sdk/lib/async/future_impl.dart 745:5                                         [_completeError]  
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 510:7                completeError     
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 581:12               _asyncRethrow     
lib/_engine/engine/app_bootstrap.dart 49:33                                       <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 622:19               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 647:23               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 597:5                <fn>
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 741:5
[_completeErrorObject]
dart-sdk/lib/async/future_impl.dart 745:5                                         [_completeError]  
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 510:7                completeError     
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 581:12               _asyncRethrow     
lib/ui_web/ui_web/initialization.dart 30:49                                       <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 622:19               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 647:23               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 597:5                <fn>
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 741:5
[_completeErrorObject]
dart-sdk/lib/async/future_impl.dart 745:5                                         [_completeError]  
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 510:7                completeError     
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 581:12               _asyncRethrow     
lib/_engine/engine/initialization.dart 112:14                                     <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 622:19               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 647:23               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 597:5                <fn>
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 741:5
[_completeErrorObject]
dart-sdk/lib/async/future_impl.dart 745:5                                         [_completeError]  
dart-sdk/lib/async/future.dart 515:18                                             handleError       
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 741:5
[_completeErrorObject]
dart-sdk/lib/async/future_impl.dart 745:5                                         [_completeError]  
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 510:7                completeError     
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 581:12               _asyncRethrow     
lib/_engine/engine/initialization.dart 207:14                                     <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 622:19               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 647:23               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 597:5                <fn>
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 741:5
[_completeErrorObject]
dart-sdk/lib/async/future_impl.dart 745:5                                         [_completeError]  
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 510:7                completeError     
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 581:12               _asyncRethrow     
lib/_engine/engine/canvaskit/fonts.dart 96:28                                     <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 622:19               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 647:23               <fn>
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 597:5                <fn>
dart-sdk/lib/async/zone.dart 1854:54                                              runBinary
dart-sdk/lib/async/future_impl.dart 239:22                                        handleError       
dart-sdk/lib/async/future_impl.dart 963:46                                        handleError       
dart-sdk/lib/async/future_impl.dart 984:13
_propagateToListeners
dart-sdk/lib/async/future_impl.dart 687:7                                         _chainCoreFuture  
dart-sdk/lib/async/future_impl.dart 693:7                                         callback
dart-sdk/lib/async/schedule_microtask.dart 40:11                                  _microtaskLoop    
dart-sdk/lib/async/schedule_microtask.dart 49:5
_startMicrotaskLoop
dart-sdk/lib/_internal/js_dev_runtime/private/ddc_runtime/operations.dart 117:77  tear
dart-sdk/lib/_internal/js_dev_runtime/patch/async_patch.dart 186:7                <fn>

