# 만리 맛집 지도

먹방 유튜버 만리가 촬영한 맛집을 지도와 리스트로 보여주는 정적 사이트입니다. (현재 예시 데이터)

## 1. 깃허브에 올리기
1. GitHub에서 새 저장소 생성 (예: `manri-map`)
2. 이 폴더의 `index.html`, `README.md` 업로드
3. 저장소 **Settings → Pages → Branch: main / (root) → Save**
4. 1~2분 뒤 `https://<깃허브아이디>.github.io/manri-map/` 접속

## 2. 네이버 지도 연결
1. [네이버 클라우드 플랫폼](https://www.ncloud.com) 가입 → 콘솔 → **Maps** 이용 신청
2. Application 등록 → **Dynamic Map** 체크
3. **Web 서비스 URL**에 `https://<깃허브아이디>.github.io` 등록
4. 발급된 **Client ID**를 `index.html`의 `CONFIG.NAVER_KEY_ID`에 입력

```js
const CONFIG = { NAVER_KEY_ID: "발급받은_Client_ID" };
```

키가 비어 있으면 좌표만 찍는 미리보기 지도가 표시됩니다.
각 가게의 "네이버 지도" 버튼은 키 없이도 동작합니다.

## 3. 데이터 추가·수정
`index.html`의 `RESTAURANTS` 배열에 한 줄씩 추가합니다.

| 필드 | 설명 |
|---|---|
| name, category, region, address | 상호, 종류, 시/도, 주소 |
| precise | 도로명 주소까지 확인했으면 true, 동네까지만이면 false (지도에 속 빈 핀) |
| lat, lng | 위도, 경도 |
| naver | 네이버 지도 검색어 (상호 + 동네) |
| menu, note, challenge | 먹은 메뉴, 한줄 메모, 도전먹방 여부 |
| video.id / title / date | 유튜브 영상 ID(watch?v= 뒤), 제목, 업로드일 |

썸네일은 영상 ID로 자동 표시됩니다.
