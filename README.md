# Cauly 리타겟팅 Android Hybrid 연동 가이드

### 개요
하이브리드 앱은 앱 안에서 Webview 를 이용하여 컨텐츠를 보여주는 형식의 앱입니다. 
Naver 앱, Daum 앱 등이 이 경우에 해당하며, 이 경우 Cauly Tracker Native SDK 의 일부 기능을 사용하여 앱 안의 Webview 에 Cauly 의 Tracking Web SDK 와 통신할 수 있는 기능을 추가해야 합니다. 
본 문서는 광고주의 앱이 하이브리드 앱일 경우 Cauly 와 리타겟팅 연동을 하는 방법에 대해서 설명하는 문서입니다.

### 문서 버전
| 문서 버전 | 작성 날짜 | 작성자 및 내용 | 
| ---------- | ----------- | ---------------- |
| 1.0.0 | 2016.4.28 | 권순국(nezy at fsn.co.kr) - 초안작성 |

### 목차
- [연동 절차](#연동-절차)
- [연동 상세](#연동-상세)

### 연동 절차
1. Cauly 담당자 혹은 cauly@fsn.co.kr로 연락하여 Cauly 리타겟팅 연동에 대해서 협의합니다.
1. 협의 완료 후, track_code 를 발급받습니다.
1. track_code 를 포함한 tracker 코드를 Android 앱의 필요한 곳에 삽입합니다.
1. 코드 삽입 이후 연동이 되었는지 Cauly 에서 테스트를 진행합니다.
1. 테스트가 완료되면 광고를 집행합니다.

### 연동 상세

- Setting
 - proguard: https://github.com/CaulyTracker/Android-Tracking-SDK#proguard
 - AndroidManifest.xml
   - track_code 추가: https://github.com/CaulyTracker/Android-Tracking-SDK#initialize
    - Install Referrer 추가: https://github.com/CaulyTracker/Android-Tracking-SDK#install-referrer-check
- 초기화: https://github.com/CaulyTracker/Android-Tracking-SDK#session
 
#### Webview 연동
```java
Webview web; // 앱에서 이미 만들어 사용하고 있는 Webview 가 있다고 가정하고 아래처럼 처리해준다.
web.addJavascriptInterface(new CaulyJsInterface(web),CaulyJsInterface.CAULY_JS_INTERFACE_NAME);
```
