---
{"dg-publish":true,"permalink":"/01.DevLog/240825_Malformed URL로 인한 문제 해결/"}
---

# 개요
- `UnityWebRequest`를 통해 **S3에 저장된 이미지 파일을 불러오는 기능을 개발**했다
- 그런데 **특정 이미지들이 iOS에서만 불러와지지 않는 문제가 발생**했다

# 문제 상황
- 상황을 정리해보니 다음과 같았다
- **에디터 & 안드로이드**
    - **정상적**으로 모든 이미지 로드 됨
- **iOS**
    - **일부 이미지** 로드 **실패**
# 원인 발견

* **Development 빌드로 XCode 디버깅**을 수행해 보니 UnityWebRequest에서 아래와 같은 에러 메시지가 발견되었다
* `Cysharp.Threading.Tasks.UnityWebRequestException: Malformed URL`
* **Malformed URL**..? 🤔

- 로그와 데이터를 비교 분석한 결과, 문제의 원인은 **URL에 포함된 특수문자**였다!
- **파일명에 URL형식에 허용되지 않는 일부 특수문자**가 포함된 경우 문제가 발생하는 것이었다.
    - **안드로이드에서는 위와 같은 URL도 정상적으로 처리**했지만, **iOS에서는 특수문자가 포함된 URL을 예외없이 예외를 발생**시켰던것

# 해결
- `System.Uri.EscapeUriString`를 사용하여 URL 문자열을 이스케이프 처리해주니 문제가 해결되었다
* URL에 사용할 수 없는 문자들을 `%` 인코딩된 헥사 표현으로 변환시켜 줌

```csharp
string baseUrl = "https://videoPlayer/";
string fileName = "[image]Image.jpg";

// [image]Image.jpg -> %5Bimage%5DImage.jpg
string escapedFileName = System.Uri.EscapeUriString(fileName); 

string finalUrl = baseUrl + escapedFileName;

// UnityWebRequest에 finalUrl 사용
```

