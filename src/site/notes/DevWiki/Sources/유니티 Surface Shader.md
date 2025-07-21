---
{"dg-publish":true,"permalink":"/DevWiki/Sources/유니티 Surface Shader/","noteIcon":"","created":"2025-05-24T15:57:28.000+09:00","updated":"2025-07-19T22:58:36.000+09:00"}
---


## Properties
> 머테리얼의 유니티 인스펙터상에 **표시 및 값을 커스텀** 할 수 있는 **사용자 정의 입력값** 정의
> 변수, 프로퍼티라고 생각하면 편함

| 타입     | 형식                                      | 설명                      |
| ------ | --------------------------------------- | ----------------------- |
| Float  | MyFloat ("Float", Float) = 0.5          | 단일 실수                   |
| Range  | MyRange ("Range", Range(0,1)) = 0.5     | 슬라이더 형태의 실수             |
| Color  | MyColor ("Color", Color) = (1,1,1,1)    | RGBA 색상 값               |
| Vector | MyVector ("Vector", Vector) = (1,1,1,1) | 4D 벡터 값                 |
| 2D     | MyTex ("Texture", 2D) = "white" {}      | 2D 텍스처 (알베도 등)          |
| Cube   | MyCube ("Cubemap", Cube) = "" {}        | 큐브맵 (환경 반사 등)           |
| 3D     | My3D ("Volume", 3D) = "" {}             | 3D 텍스처 (주로 볼륨 쉐이딩용)     |
| Any    | MyTex ("Texture", Any) = "" {}          | 범용 텍스쳐 (어떤 종류의 텍스쳐든 가능) |
## SubShader
> 실제로 실행되는 **렌더링 코드**

* 여러개의 SubShader를 선언할 수 있으며 런타임시 **하드웨어상으로 사용 가능한 첫번째 쉐이더**를 자동으로 골라내 사용하게 된다
``` 
SubShader
{
    Pass     // 첫 번째 Pass (기본 렌더링)
    {
    
    }
    Pass     // 두 번째 Pass (예: 그림자 처리)
    {

    }
}
SubShader
{
    Pass     // 첫 번째 Pass (기본 렌더링)
    {
    
    }
    Pass     // 두 번째 Pass (예: 그림자 처리)
    {

    }
}

```
## **#pragma**
* 쉐이더에서 어떤 기능을 사용할지 알려주는 **지시어**
* `#pragma vertex vert
	* vertext 셰이더 함수를 vert라는 함수로 사용하겠다

## **Semantic**
* 쉐이더에서 각 변수(정점, 색상, 텍스처 좌표 등)가 **어떤 용도인지 지정해주는 키워드***

| **시맨틱**                 | **의미**   | **위치**      | **설명**                        |
| ----------------------- | -------- | ----------- | ----------------------------- |
| POSITION                | 정점 위치    | 정점 셰이더 입력   | 모델 좌표 공간의 위치 (예: v.vertex)    |
| SV_POSITION             | 화면 위치    | 정점 셰이더 출력   | 클립 공간 좌표 (GPU가 **픽셀 위치로 해석**) |
| TEXCOORD0, TEXCOORD1, … | 텍스처 좌표   | 입력/출력 모두 가능 | UV 좌표, 또는 임의 데이터 전달에 자주 씀     |
| NORMAL                  | 정점 노멀 벡터 | 입력          | 표면의 방향 정보                     |
| COLOR                   | 정점 색상    | 입력          | 메쉬에서 전달되는 정점 색상               |
| SV_Target               | 픽셀 색상 출력 | 픽셀 셰이더 출력   | 렌더 타겟으로 보낼 최종 색상              |
| SV_VertexID             | 정점 ID 번호 | 정점 셰이더 입력   | 정점 인덱스 (GPU 계산용)              |
