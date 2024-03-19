# DEVNOTE

## get_face_single

`scripts/reactor_swapper.py` 의 `get_face_single()` 함수가 수정되었습니다.

* 변경 목적 : 얼굴 선택 알고리즘 수정
* 기존 : Bounding box 기준으로 가장 왼쪽 얼굴을 선택
* 변경 후 : 아래 절차를 따릅니다.
    1. Bounding box의 넓이를 모두 구하고, 가장 큰 Bounding box를 선택합니다.
    2. `(가장 큰 Bounding box 넓이) * AREA_FILTER_THRESHOLD` 보다 큰 넓이를 가진 Bounding box만 남깁니다.
    3. `해당 Bounding box의 넓이 / 가장 큰 Bounding box 넓이` 를 확률로 하여 1개의 Bounding box만 선택합니다.
        * 0번 index를 선택하도록 하드코딩 되어 있기 때문에 face_index 파라미터는 사용되지 않습니다.
