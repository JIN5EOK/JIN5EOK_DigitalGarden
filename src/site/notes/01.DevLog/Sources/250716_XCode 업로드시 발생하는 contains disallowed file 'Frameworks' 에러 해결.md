---
{"dg-publish":true,"permalink":"/01.DevLog/Sources/250716_XCode 업로드시 발생하는 contains disallowed file 'Frameworks' 에러 해결/"}
---


## 개요
* 구글 플레이 스토어에서 요구하는 API 버전에 맞추기 위해 유니티 버전을 올리는 작업을 했다
* 그런데  유니티 버전을 올린 후 iOS에서 유니티 빌드 후 XCode 아카이브 후 AppStore 업로드를 수행하자..
 
 `.../Frameworks/UnityFramework.framework contains disallowed file 'Frameworks'.`

* 앱 스토어 업로드에 실패하며 위와 같은 오류가 발생했다! 😇

## 해결책 발견

* 인터넷에서 관련 정보를 서치한 결과 다행히 나와 같은 케이스들이 아주 많았다.
* XCode 프로젝트 -> UnityFramework -> Build Settings -> Always Embed Swift Standard Libraries
    * 이 항목의 설정값을 No로 바꿔주면 해결이 된다!

* 다만 우리는 **젠킨스를 통해 구현한 빌드머신**을 사용해 빌드하고 있었으며 그게 아니더라도 매번 수정하기는 힘드니, **포스트 프로세싱**을 통해 **빌드 이후 값을 자동으로 수정해주는 처리**를 추가해야 했다.
* 기존에 사용하던 **포스트 프로세스싱 스크립트**에 다음과 같은 사항을 추가하니 해결 완료!

```CSharp
...
    string projectPath = pathToBuiltProject + "/Unity-iPhone.xcodeproj/project.pbxproj";  
    var project = new PBXProject();  
    project.ReadFromFile(projectPath);  
      
    SetSwiftStandardLibraries(project, projectPath);
}

// iOS 빌드 아카이브시 발생하는 .../Frameworks/UnityFramework.framework contains disallowed file 'Frameworks'. 에러 방지  
static void SetSwiftStandardLibraries(PBXProject project, string projectPath)  
{  
    project.SetBuildProperty(project.GetUnityFrameworkTargetGuid(), "ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES", "NO");  
    project.WriteToFile(projectPath);  
}
```

