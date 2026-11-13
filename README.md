# photo LP

사진과 영상을 LP판 위에 올려 두고, 음악과 함께 넘겨 보는 웹 페이지입니다.

**바로 써보기:** https://chloe115758-arch.github.io/photoLP/

설치할 것 없이 `index.html` 파일 하나로 동작합니다.

## 할 수 있는 것

- **사진·영상 올리기:** 최대 20개까지 LP 위의 원에 올립니다. 아이폰 사진(HEIC)도 됩니다.
- **크게 보기:** 원을 누르면 아래에 크게 보입니다. 영상은 소리 없이 재생됩니다.
- **LP 돌리기:** 손가락이나 마우스로 끌면 LP가 돌아가고, 다음 사진이 차례로 나옵니다.
- **슬라이드쇼:** 사진은 4초마다, 영상은 끝까지 재생된 뒤 다음으로 넘어갑니다.
- **음악:** YouTube에서 곡을 검색하거나 링크를 붙여넣어 재생합니다. 재생 중에는 LP가 천천히 돕니다.
- **순서 바꾸기:** 원을 길게 눌러 다른 원 위로 끌어다 놓으면 두 사진의 자리가 바뀝니다.
- **영상으로 저장:** 컴퓨터의 Chrome·Edge에서 화면과 음악을 함께 녹화해 파일로 받습니다.

## 사용법

| 하고 싶은 것 | 방법 |
|---|---|
| 사진·영상 추가 | 처음에는 아래 `+` 버튼, 그다음부터는 LP의 빈 아이보리 원을 누릅니다 |
| 노래 틀기 | LP 위쪽 가운데의 아이보리 원을 눌러 검색창을 열고, 곡 이름이나 YouTube 링크를 입력합니다 |
| 노래 멈춤·재생 | LP 가운데의 곡 제목을 누릅니다 |
| 슬라이드쇼 | 아래 가운데 재생 버튼을 누릅니다 |
| 순서 바꾸기 | 사진 원을 0.5초쯤 길게 누른 뒤 다른 사진 원으로 끌어다 놓습니다 |
| 영상 저장 (컴퓨터) | 아래 왼쪽 저장 버튼을 누르고, 공유 창에서 "Chrome 탭"과 "탭 오디오도 공유"를 선택합니다 |
| 전부 지우기 | 아래 오른쪽 되돌리기 버튼을 누릅니다 |

## 알아둘 점

- 올린 사진과 영상은 서버로 전송되지 않고 내 브라우저 안에만 있습니다. 새로고침하면 사라집니다.
- 폰에서는 저장 버튼이 나타나지 않습니다. 폰의 화면 기록 기능을 쓰세요.
- 일부 곡은 YouTube 밖에서 재생이 막혀 있습니다. 그럴 때는 검색 결과에서 다른 영상을 고르세요.
- 곡 검색은 하루 약 100번까지 됩니다. 같은 검색어는 30일 동안 저장된 결과를 쓰고, YouTube 링크를 붙여넣는 것은 횟수에 포함되지 않습니다.

## 내 컴퓨터에서 실행하기

`index.html`을 더블클릭해서 열면 YouTube 재생이 막힙니다. 아래처럼 로컬 서버로 여세요.

```
git clone https://github.com/chloe115758-arch/photoLP.git
cd photoLP
python3 -m http.server 8000
```

브라우저에서 `http://localhost:8000`으로 접속합니다.

## 직접 배포하려면

곡 검색에는 YouTube Data API 키가 필요합니다. 저장소에 들어 있는 키는 이 저장소의 주소에서만 동작하므로, 복사해서 배포할 때는 본인 키로 바꿔야 합니다.

1. [Google Cloud 콘솔](https://console.cloud.google.com)에서 프로젝트를 만들고 **YouTube Data API v3**를 사용 설정합니다.
2. **사용자 인증 정보**에서 API 키를 만듭니다.
3. 키의 **애플리케이션 제한사항**을 "웹사이트"로 하고, 배포할 주소와 `http://localhost:*`만 허용합니다. **API 제한사항**은 YouTube Data API v3만 허용합니다.
4. `index.html`의 `const YT_KEY='...'`에 키를 넣습니다.

키를 비워 두면 검색은 안 되지만, YouTube 링크를 붙여넣어 재생하는 것은 됩니다.

## 사용한 것

- HTML, CSS, JavaScript (빌드 도구와 프레임워크 없음)
- [YouTube IFrame Player API](https://developers.google.com/youtube/iframe_api_reference), [YouTube Data API v3](https://developers.google.com/youtube/v3)
- [heic-to](https://github.com/hoppergee/heic-to) (HEIC 사진 변환)
- [Pretendard](https://github.com/orioncactus/pretendard) (글꼴)
