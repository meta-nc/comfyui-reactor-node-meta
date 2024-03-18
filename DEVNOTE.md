# DEVNOTE

## get_face_single

`scripts/reactor_swapper.py` 의 `get_face_single()` 함수가 수정되었습니다.

* 변경 목적 : 얼굴 선택 알고리즘 수정
* 기존 : Bounding box 기준으로 가장 왼쪽 얼굴을 선택
* 변경 후 : 아래 절차를 따릅니다.
    1. Bounding box의 넓이를 모두 구하고, 가장 큰 Bounding box를 선택합니다.
    2. 가장 큰 Bounding box와 비슷한 크기 `(가장 큰Bounding box 크기) * AREA_FILTER_THRESHOLD`의 Bounding box만 남깁니다.
    3. 이 Bounding box 를 랜덤 순서로 정렬한 후, `target_index` 또는 `source_index` 파라미터에 의해 선택됩니다.
