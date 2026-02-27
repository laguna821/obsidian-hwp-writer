# MAJOR UPDATE (2-28-2026)
- **대형 한글 표 (두 세 페이지 이상 넘어가는 마크다운 테이블을 포함한 문서)**를 한글 hwpx로 내보내기 하면 hwpx 실행시 튕기는 문제를 해결
- 중요 업데이트이므로 1.4.0 압축파일 내용을 기존의 옵시디언 plugin 볼트에 obsidian-hwp-writer 폴더 안에 전부 덮어쓰세요.

## 최신 버전 링크:
https://github.com/laguna821/obsidian-hwp-writer/releases/tag/obsidian-hwpx-writer

# Obsidian HWP Writer

마크다운으로 작성하고, 한글(HWPX) 형식으로 바로 내보내기 위한 Obsidian 플러그인입니다.  
`pypandoc-hwpx` 변환 엔진 + `editing-toolbar` 편집 UX를 한 플러그인으로 통합했습니다.

## 왜 만들었나

많은 사용자가 이런 흐름에서 막힙니다.

- 지식 관리와 기록은 마크다운으로 하고 싶다.
- 그런데 학교/공공기관 제출은 한글 형식(HWPX) 편집을 요구한다.
- 결국 한글에서 다시 편집하게 되고, 마크다운 기록은 누락된다.

Obsidian HWP Writer는 이 악순환을 줄이기 위해 만들었습니다.  
Obsidian 안에서 작성하고, 템플릿 기반 HWPX로 내보내며, 라이브 뷰로 형식을 최대한 맞춰서 작업 피로를 줄입니다.

## 핵심 특징

- 마크다운 작성 + HWPX/DOCX/HTML 내보내기
- `pypandoc-hwpx` 기반 HWPX 변환
- 한글 2020 스타일에 맞춘 툴바 UI/UX
- 템플릿(`.hwpx`) 기반 스타일 추출 및 즉시 적용
- 커스텀 템플릿 교체 시 라이브 미리보기 동기화
- 초보자용 설치 가이드(플러그인 내부 3단계 점검)

## 설치 방법

### 1) BRAT로 설치 (권장)

1. 이 저장소를 GitHub에 업로드합니다.
2. Obsidian에서 BRAT 플러그인을 엽니다.
3. `Add Beta Plugin`에서 저장소 URL을 입력해 설치합니다.

BRAT 설치용 필수 파일:

- `manifest.json`
- `main.js`
- `styles.css`
- `blank.hwpx`

권장 포함 파일:

- `package.json` (버전/메타 관리용)
- `README.md`

### 2) 수동 설치

1. Obsidian 볼트의 `.obsidian/plugins/` 폴더로 이동합니다.
2. `obsidian-hwp-writer` 폴더를 생성합니다.
3. 위 필수 파일들을 해당 폴더에 복사합니다.
4. Obsidian 설정에서 플러그인을 활성화합니다.

## 최초 1회 환경 준비 (필수)

플러그인 첫 실행 시 설치 가이드가 자동으로 열립니다.

1. Python 설치 확인
2. Pandoc 설치 확인
3. 변환 패키지 설치 확인

패키지 설치 명령:

```bash
python -m pip install pypandoc pypandoc-hwpx pillow
```

참고:

- 플러그인 설정에서 `Python 경로`, `Pandoc 경로`를 직접 지정할 수 있습니다.
- PATH가 잡히지 않은 환경에서도 절대경로 지정으로 동작합니다.

## 사용 흐름

1. Obsidian에서 마크다운 문서를 작성합니다.
2. 툴바에서 제목/강조/목록/정렬 등 서식을 적용합니다.
3. `HWPX` 버튼으로 내보냅니다.
4. 현재 문서 폴더에 `.hwpx` 파일이 생성(또는 덮어쓰기)됩니다.

## 템플릿 커스터마이징 (중요)

기본 템플릿은 `blank.hwpx`입니다.  
커스텀 템플릿을 쓰려면 아래 순서를 권장합니다.

1. `blank.hwpx`를 복사해 한글에서 엽니다.
2. `F6`에서 바탕글/Heading 1~9의 글꼴, 크기, 줄간격, 들여쓰기 등을 조정합니다.
3. 새 `.hwpx` 파일로 저장합니다.
4. 플러그인 템플릿 메뉴에서 파일을 등록/선택합니다.
5. 즉시 미리보기와 내보내기에 반영됩니다.

## 라이브 뷰와 실제 내보내기

- 라이브 뷰는 작업 편의를 위한 실시간 미리보기입니다.
- 최종 HWPX 결과는 `pypandoc-hwpx + 선택한 템플릿` 기준으로 생성됩니다.
- 즉, 최종 제출 품질은 템플릿(`.hwpx`)이 결정합니다.

## 초보자 관점에서의 장점

기존에는 CLI에서 `pypandoc-hwpx` 명령을 직접 다뤄야 해서 진입 장벽이 있었습니다.  
이 플러그인은 버튼 클릭으로 내부에서 Python 변환을 자동 실행하므로, CLI 사용 부담을 크게 줄입니다.

## 트러블슈팅

### `Python/Pandoc` 인식 실패

- 플러그인 설정에서 실행 파일 경로를 직접 지정하세요.
- 예: `C:\Python312\python.exe`, `C:\Program Files\Pandoc\pandoc.exe`

### `pypandoc-hwpx` 모듈 오류

아래 명령을 다시 실행하세요.

```bash
python -m pip install --upgrade pypandoc pypandoc-hwpx pillow
```

### 템플릿 적용이 이상함

- 올바른 `.hwpx` 파일을 선택했는지 확인하세요.
- 템플릿 재선택 후 폰트 재로드를 실행하세요.

## 개발/검증

```bash
npm install
npm run build
npm run verify:portable
```

`verify:portable`는 로컬 절대경로/환경 의존 참조가 번들에 남아있는지 검사합니다.

## 라이선스

MIT

