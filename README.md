# MAJOR UPDATE (3-8-2026) v3 워드 (.docx)파일 내보내기가 별도의 파이프라인으로 분리되었습니다!

## obsidian-hwp-writer 주요기능 안내

### 1. 워드 전용 미리보기 / 한글 전용 미리보기 분할

![1](https://github.com/user-attachments/assets/cd213f56-d840-45c6-8cdc-72309021ef6f)

- 기존의 "분할" (라이브뷰) 버튼이 "hwp 분할" 버튼으로 분리되었습니다.
  - 기존의 "템플릿" 또한 "hwp 템플릿"으로 변경되었습니다. 작동은 동일합니다.
  - hwpx 파이프라인은 pypandoc-hwpx 기반으로 라이브 뷰 및 내보내기가 작동합니다.

### 2. 워드 전용 템플릿 - 옵시디언 in-app 설정

![2](https://github.com/user-attachments/assets/656639c4-4a37-4f02-85b5-d1bf1dda05bf) 

- "워드 템플릿" 버튼을 눌러서 "모든" 종류의 템플릿 설정을 세부 지정할 수 있습니다.
  - 줄간격, 자간, 볼드, 이탤릭, 들여쓰기 등 거의 모든 부분들을 미세 조작할 수 있습니다.
  - 현재는 "Font Faimily"에 폰트를 타이핑 할 때 라이브 뷰 때문에 타이핑이 제대로 되지 않는 버그가 있습니다. (메모장에서 "Pretendard Variable" 같은 형식으로 타이핑을 해서 Ctrl + C / Ctrl + V로 붙여넣으시면 됩니다 - 추후 수정예정) / 대신에 로컬 폰트도 라이브 뷰 및 내보내기가 완벽 적용됩니다

### 3. 주의: 워드 전용 템플릿 사용시 "Save"를 꼭 누르세요

![3](https://github.com/user-attachments/assets/af21974d-1c7e-47a1-85d4-8a92598b5c34)

세이브 버튼은 "워드 템플릿"에서 스크롤을 내리면 하단에 있습니다.
각각 미세조정 하시고 반드시 Save를 누르시기 바랍니다.

### 4. 한글 및 워드 별도의 라이브 뷰 독립 관리

![4](https://github.com/user-attachments/assets/d17d6f03-28f1-4a3b-95b4-bd71e952b825)

- 한글 라이브 뷰는 pypandoc-hwpx 기반으로, 워드 라이브 뷰는 pandoc 기반으로 따로 작동됩니다.
- 따라서 서로 충돌하지 않고 별도로 편하게 독립적으로 관리할 수 있습니다.


추후 업데이트 예정 (내 맘대로 적는 로드맵 : 언제 업데이트 또 될지 모릅니다)
- 워드 템플릿1, 템플릿2, 템플릿3... 등 Preset 최소 5개 이상 지정 기능 및 Preset 이름 변경 기능 추가.
- 워드 템플릿 설정창에서 Font Family 에 폰트 이름을 붙여넣기 불편한 부분 수정 (수치 수정 등)

[obsidian-hwp-writer-1.6.0.zip](https://github.com/user-attachments/files/25824404/obsidian-hwp-writer-1.6.0.zip)


옵시디언 폴더의 .obsidian/plugins의 obsidian-hwp-writer에 기존의 파일들 덮어 쓰기 + 1.6.0 버전에서 새로 추가 된 word-assets를 폴더째로 새로 만들어서 복사하기 (그러니까 1.6.0 버전 파일들을 기존 파일들에 새로 덮어 씌우세요.)



# MAJOR UPDATE (2-28-2026) v2 - 대형 표 크래시 해결 + 워드 내보내기 통합본
- **대형 한글 표 (두 세 페이지 이상 넘어가는 마크다운 테이블을 포함한 문서)**를 한글 hwpx로 내보내기 하면 hwpx 실행시 튕기는 문제를 해결
- 중요 업데이트이므로 1.5.0 압축파일 내용을 기존의 옵시디언 plugin 볼트에 obsidian-hwp-writer 폴더 안에 전부 덮어쓰세요.
- 추가 기능 (1.5.0) : 이제 워드 파일 내보내기가 됩니다! 완벽하게 매핑되지는 않지만, 어쨌든 됩니다!

[## 최신 버전 링크 바로가기](https://github.com/laguna821/obsidian-hwp-writer/releases/tag/obsidian-hwpx-writer_1.5.0)


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

