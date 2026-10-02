# marketing-calendar-internal-app

내부 분기 플래닝 캘린더의 **앱 셸**입니다. GitHub Pages로 서비스됩니다.

👉 **https://janeeyye.github.io/marketing-calendar-internal-app/**

## 이 저장소에 무엇이 있고, 무엇이 없는지

이 저장소는 public 입니다. 따라서 **일정 데이터는 여기에 두지 않습니다.**

| | 위치 | 공개 여부 |
|---|---|---|
| 앱 코드 (`index.html`) | 이 저장소 | public |
| 일정 데이터 (`calendar-data.json`) | `janeeyye/marketing-calendar-internal` | **private** |
| 접근 토큰 (PAT) | 각자 브라우저 `localStorage` | 공유 안 됨 |

`index.html` 에는 일정이 들어 있지 않습니다. 앱은 실행 시점에 private 저장소에서
데이터를 내려받습니다. 토큰이 없는 사람이 위 주소를 열면 **빈 캘린더와 연결 안내만** 보입니다.

> ⚠️ 이 저장소에 일정 데이터나 토큰을 절대 커밋하지 마세요.
> `index.html` 안의 `<script id="seed">` 블록은 비어 있어야 합니다.

## 처음 쓰는 사람 (1회 설정)

1. 위 주소를 엽니다.
2. 오른쪽 위 **⋯ › GitHub 연결** 을 누릅니다.
3. 토큰을 발급해 붙여넣습니다. [토큰 발급 페이지](https://github.com/settings/personal-access-tokens/new)
   - **Repository access** → `Only select repositories` → `marketing-calendar-internal` **하나만**
   - **Permissions** → `Contents` → `Read and write`
   - **Expiration** → 90일 등 만료일을 반드시 지정
4. 상태 표시가 **`동기화됨`** 으로 바뀌면 끝입니다.

토큰은 브라우저에만 저장되므로 PC나 브라우저를 바꾸면 다시 등록해야 합니다.

## 같이 쓰기

- 변경하면 2초 뒤 자동 저장됩니다. 따로 저장 버튼이 없습니다.
- 30초마다 동기화되어 **다른 사람의 변경이 자동으로 반영**됩니다.
- 수정창을 열어두거나 드래그 중이면 작업이 끊기지 않도록 보류했다가, 닫는 순간 반영합니다.
- 두 사람이 동시에 저장하면 덮어쓰지 않고 **선택 창**이 뜹니다. GitHub가 오래된 저장을
  거부(409)하기 때문에 한쪽 변경이 조용히 사라지는 일은 구조적으로 일어나지 않습니다.

## 앱을 고쳤을 때

`main` 에 push 하면 GitHub Pages가 1~2분 안에 재배포합니다.
팀원은 **새로고침만** 하면 됩니다. 파일을 다시 받을 필요가 없습니다.

## 로컬에서 확인하려면

```powershell
cd marketing-calendar-internal-app
python -m http.server 8778
# http://127.0.0.1:8778/index.html
```

`index.html` 을 더블클릭(`file://`)해도 동작하지만, 배포본과 어긋날 수 있으니
평소에는 위 주소를 쓰세요.

## 문제가 생기면

| 증상 | 원인 | 해결 |
|---|---|---|
| `연결 실패` | 토큰 만료 또는 오타 | ⋯ › GitHub 연결 에서 재등록 |
| `파일 없음 — 첫 저장 대기` | private 저장소에 `calendar-data.json` 이 없음 | 아무 일정이나 수정하면 새로 생성됨 |
| 일정이 안 보임 | 토큰 미등록 | 위 *처음 쓰는 사람* 참고 |
| 바꿨는데 남들이 못 봄 | 토큰에 쓰기 권한 없음 | `Contents: Read and write` 로 재발급 |
