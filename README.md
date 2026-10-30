# Shopping List App (쇼핑 리스트 앱)

간단하고 직관적인 쇼핑 리스트 웹 애플리케이션입니다. 목록은 Supabase 데이터베이스에 저장되어 어느 기기에서 열어도 같은 목록을 볼 수 있습니다.

## 기능

- 아이템 추가/삭제
- 완료 체크 표시
- 완료된 항목 일괄 삭제
- Supabase 데이터베이스에 저장 (기기가 바뀌어도 목록 유지)
- 예전 버전에서 브라우저(localStorage)에 저장한 항목은 처음 열 때 자동으로 데이터베이스로 이동
- 반응형 디자인, 다크 모드 지원

## 사용 방법

1. 입력창에 살 물건을 입력하고 **추가** 버튼을 누르거나 Enter 키를 누릅니다.
2. 산 물건은 체크박스를 눌러 완료 표시합니다.
3. ✕ 버튼으로 항목 하나를 삭제하고, **완료된 항목 지우기**로 완료된 항목을 한 번에 지웁니다.

## 기술 스택

- HTML, CSS, JavaScript (빌드 도구 없이 `index.html` 하나로 동작)
- [Supabase](https://supabase.com) (PostgreSQL 데이터베이스, `@supabase/supabase-js`)
- [Vercel](https://vercel.com) 배포

## 데이터베이스 구조

`shopping_items` 테이블

| 컬럼 | 타입 | 설명 |
|---|---|---|
| `id` | bigint | 기본 키 (자동 증가) |
| `text` | text | 물건 이름 (1~200자) |
| `done` | boolean | 완료 여부 (기본값 `false`) |
| `created_at` | timestamptz | 추가한 시각 |

Row Level Security(RLS)가 켜져 있으며, 로그인 없이 누구나 읽기·추가·수정·삭제할 수 있도록 정책이 설정되어 있습니다.

## 로컬에서 실행

`index.html` 파일을 브라우저로 열면 바로 실행됩니다.
