# YM토탈이벤트

음향 · 조명 · LED전광판 · 특수효과 · 무대까지 한 팀이 맡는 토탈 이벤트 에이전시.
전남 고흥 · 목포 기반, 전국 출장.

**www.와이엠토탈이벤트.com** (`www.xn--el3bx2ohi64bba144lgmbdzd.com`)

---

## 페이지

| 주소 | 내용 |
|---|---|
| `/` | 메인 — 회사소개 · 서비스 · 규격 · 행사이력 · 갤러리 · 4단계 · 자주 묻는 질문 · 파트너 · 연락처 |
| `/quote.html` | 견적 · 문의 — 항목을 고르면 견적서가 자동으로 만들어집니다 |
| `/upload.html` | 행사 사진 올리기 (검색 제외 · 비밀번호 필요) |
| `/contact.html` | 옛 문의 페이지 — 견적 페이지로 넘겨줍니다 |

## 사진이 갤러리에 쌓이는 구조

서버 없이 돌아갑니다.

```
휴대폰 (upload.html)
   │  ① 사진을 웹용으로 줄이고 오른쪽 위에 워터마크
   ▼
구글 Apps Script (apps-script/Code.gs)
   │  ② 웹용 축소본 → 이 저장소의 photos 브랜치
   │  ③ 원본 → 구글 드라이브 (기본 꺼짐. 켰을 때만)
   ▼
메인 페이지 갤러리
      photos.json 을 읽어 행사별로 묶어 보여줍니다
```

- 사진은 **`photos` 브랜치**에 쌓입니다. `main` 에 넣으면 사진 한 장마다 페이지가 다시 배포돼서 분리해 뒀습니다.
- 목록은 `raw.githubusercontent.com`, 이미지는 `cdn.jsdelivr.net` 으로 읽습니다.
  jsDelivr 는 브랜치 파일을 **최대 12시간** 캐시하므로, 사진을 바꿔도 바로 안 보일 수 있습니다.

Apps Script 설치 방법은 [`apps-script/README.md`](apps-script/README.md) 를 보세요.

## 견적 문의가 오는 곳

`quote.html` 의 `견적_수신_이메일` 한 줄이 수신 주소입니다.
FormSubmit 을 쓰기 때문에 **주소를 바꾸면 첫 발송 때 인증 메일이 한 번 옵니다.**

## 고칠 때

빌드 과정이 없습니다. HTML 파일을 고쳐 `main` 에 올리면 그대로 배포됩니다.

- 견적 품목: `quote.html` 의 `CATALOG`
- 갤러리 고정 사진: `index.html` 의 `GALLERY` 주석 아래
- 대표 도장: `stamp.png` (없으면 견적서에서 알아서 빠집니다)
