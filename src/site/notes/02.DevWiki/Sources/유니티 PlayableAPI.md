---
{"dg-publish":true,"permalink":"/02.DevWiki/Sources/유니티 PlayableAPI/","noteIcon":"","updated":"2025-07-19T22:58:36.000+09:00"}
---


## PlayableAPI

> 애니메이션, 오디오, Timeline 같은 재생 가능한 콘텐츠를 노드처럼 연결해서 실행 및 제어하는 API

- Unity Timeline도 PlayableAPI를 기반으로 동작된다

``` Csharp
PlayableGraph graph = PlayableGraph.Create();
AnimationClipPlayable clipPlayable = AnimationClipPlayable.Create(graph, myClip);
AnimationPlayableOutput output = AnimationPlayableOutput.Create(graph, "Anim", animator);
output.SetSourcePlayable(clipPlayable);
graph.Play();
```

- PlayableGraph
    - 전체 재생 흐름 관리하는 그래프
- Playable
    - AnimationClip, Mixer 등 재생 노드
- Output
    - 결과를 어디로 보낼지 (Animator 등)
- AnimatorController와 비교해서
    - AnimatorController
        - 상태기반
        - 비 개발자 친화적
        - 런타임 중 내용 조작 제한
    - PlayableAPI
        - 데이터 흐름 기반
        - 개발자 친화적
        - 런타임 중 내용 조작 가능
- 어떨때 사용할까?
    - 복잡하거나 상태머신으로 구현하기 힘든 연출과 애니메이션 등을 코드를 통해 자유롭고 정밀하게 다루고 싶을 때
- Animator와 Playable 혼합도 가능, 예를들면
    - 기본적인 애니메이션인 Idle/Move는 AnimatorController로
    - 종류가 많고 복잡한 조건에 따라 체이닝 되어야 하는 스킬, 컷씬을 PlayableGraph로 구현

## ScriptPlayable

> Unity의 **Playable API**와 **Timeline**에서 사용 가능한 시용자 정의 Playable
### 사용자 정의 Playable을 구현하기 위해 필요한 것들
* PlayableBehaviour : 클립에서 실제로 실행할 사용자 정의 로직
* PlayableAsset : 트랙의 클립 정의 (트랙의 '클립')
* TrackAsset : 타임라인에 삽입할 트랙 (타임라인의 '트랙')

```C#
public class MyCustomBehaviour : PlayableBehaviour
{
    public string message;

    public override void OnBehaviourPlay(Playable playable, FrameData info)
    {
        Debug.Log($"[Play] {message}");
    }

    public override void OnBehaviourPause(Playable playable, FrameData info)
    {
        Debug.Log($"[Pause] {message}");
    }
}
```
```C#
[System.Serializable]
public class MyCustomPlayableAsset : PlayableAsset
{
    public string message;

    public override Playable CreatePlayable(PlayableGraph graph, GameObject owner)
    {
        var playable = ScriptPlayable<MyCustomBehaviour>.Create(graph);
        var behaviour = playable.GetBehaviour();
        behaviour.message = message;
        return playable;
    }
}
```
```C#
[TrackColor(0.8f, 0.4f, 0.1f)]
[TrackClipType(typeof(MyCustomPlayableAsset))]
public class MyCustomTrack : TrackAsset
{
    public override Playable CreateTrackMixer(PlayableGraph graph, GameObject go, int inputCount)
    {
        return ScriptPlayable<PlayableBehaviour>.Create(graph, inputCount);
    }
}
```

