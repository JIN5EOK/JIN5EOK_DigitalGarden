---
{"dg-publish":true,"permalink":"/01.DevLog/Sources/241124_Aseprite Importer 사용 후기/","noteIcon":"","created":"2025-05-23T02:19:34.925+09:00","updated":"2025-07-20T02:49:56.111+09:00"}
---

> Aseprite Importer : Aseprite파일을 임포트, 에셋처럼 사용하도록 해주는 플러그인


- **처음 기대효과**
    - **스프라이트 시트**의 **관리 용이성**
        - 어차피 Aseprite파일로 픽셀작업 하는데 이걸로 관리하면 유지보수가 훨씬 쉬워지지 않을까?
- **장단점이 있어 고민해봐야 할듯**
    - **장점**
        - Aseprite로 애니메이션 작업을 하고 별다른 수정 없이 그대로 임포트 가능
        - 디자이너와의 협업 효율성 증가
    - **단점**
        - 에셋스토어 에셋들은 Aseprite파일이 제공되지 않는 경우가 많음, 이 때 **통일성 저하**
        - aseprite파일 내 개별 스프라이트 **이름 변경 불가** (내가 못 찾은 것일수도?)
            - 임포트된 Aseprite파일의 개별 스프라이트 이름이 Frame_0, Frame_1.. 같은 방식으로 나옴
                - 모든 스프라이트들의 이름들이 같아버리면 식별이 너무 어려움
![](https://i.imgur.com/cuV2Pn3.png)

* 최종적으로는 사용하기로 하였음