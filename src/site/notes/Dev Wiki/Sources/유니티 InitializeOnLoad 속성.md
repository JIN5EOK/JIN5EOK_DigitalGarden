---
{"dg-publish":true,"permalink":"/Dev Wiki/Sources/유니티 InitializeOnLoad 속성/","noteIcon":"","created":"2024-09-18T17:56:38.000+09:00","updated":"2025-07-19T22:58:36.983+09:00"}
---

### 개요
[InitializeOnLoad] 속성을 사용한 정적 메서드는 에디터 초기화시 실행이 된다
```
using UnityEngine;
using UnityEditor;

[InitializeOnLoad]
public class Startup {
    static Startup()
    {
        Debug.Log("Up and running");
    }
}
```
### Update처리
EditorApplication.update 대리자에 원하는 정적 메서드 이벤트를 등록하여 Update를 처리할 수 있다

```
using UnityEditor;
using UnityEngine;

[InitializeOnLoad]
class MyClass
{
    static MyClass ()
    {
        EditorApplication.update += Update;
    }

    static void Update ()
    {
        Debug.Log("Updating");
    }
}

```
