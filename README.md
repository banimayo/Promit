# Promit

Promit는 주사위 기반 프롬프트 빌더입니다. 키워드를 캡슐/칩 단위로 구성하여 다양한 조합을 빠르게 만들고 재사용할 수 있습니다.

## 주요 흐름

1. **캡슐에서 칩 추가**
   - 상단 캡슐을 클릭하거나 드래그해 캔버스에 칩을 배치합니다.
   - 칩을 클릭하면 옵션 팝오버가 열려 값 추가/삭제/선택을 할 수 있습니다.
   - 팝오버 항목을 길게 누르면 인라인 편집이 활성화되어 해당 옵션을 즉시 수정/삭제할 수 있습니다.

2. **칩 편집 & 배치**
   - 칩 왼쪽의 아이콘을 눌러 🎲(랜덤)/🔒(고정) 상태를 전환합니다.
   - 칩 사이 공간을 클릭하면 링크가 토글되어 출력 시 공백/콤마를 조절합니다.
   - 칩 자체는 드래그&드롭으로 순서 변경 및 중간 삽입이 가능합니다.
   - 휴지통 영역으로 드래그하면 칩을 삭제할 수 있습니다.

3. **랜덤 롤 & 히스토리**
   - 중앙의 🎲 Generate 버튼을 누르면 🎲 상태 칩만 랜덤으로 굴려 새 프롬프트를 생성합니다.
   - 생성 결과는 문자열 히스토리로 저장되며, 히스토리 패널에서 클릭하면 해당 구성을 즉시 복원합니다.
   - 단축키: `Ctrl+Z`는 이전 히스토리, `Ctrl+Shift+Z` 또는 `Ctrl+Y`는 다음 히스토리로 이동합니다.

4. **즐겨찾기 프리셋**
   - 현재 구성을 그대로 즐겨찾기에 추가하면 프리셋 칩 보드가 생성됩니다.
   - 즐겨찾기 칩을 드래그해 일부만 캔버스에 삽입하거나, 클릭하여 전체 구성을 불러올 수 있습니다.
   - 즐겨찾기 이름은 칩 길게 누르기 또는 상단 `activeFavoriteLabel` 인라인 편집으로 즉시 변경 가능합니다.

## 단축키 & 인터랙션 요약

| 기능 | 조작 |
| --- | --- |
| 랜덤/고정 전환 | 칩의 🎲/🔒 아이콘 클릭 |
| 링크 토글 | 칩 사이의 점선을 클릭 |
| 팝오버 인라인 편집 | 팝오버 항목 길게 누르기 |
| 캡슐 이름 변경/삭제 | 캡슐을 약 2초 길게 누르기 |
| 즐겨찾기 이름 변경 | 즐겨찾기 칩 길게 누르기 또는 상단 라벨 클릭 |
| 히스토리 복원 | 히스토리 항목 클릭 |
| 히스토리 전체 삭제 | 히스토리 탭 오른쪽 휴지통 버튼 |
| 단축키 | `Ctrl + Z` / `Ctrl + Shift + Z` (또는 `Ctrl + Y`) |

## 백업 & 임포트

- JSON 백업에는 `schemaVersion: 1`, `version: "PromIt 1.0"`이 포함됩니다.
- `prompts.json` 파일을 내보내면 히스토리를 제외한 모든 데이터가 포함됩니다.
- 임포트는 동일 스키마 버전만 허용하며 구조 검증 후 반영됩니다.
  - full-state JSON: 앱 전체 데이터를 초기화하고 새 상태로 교체.
  - favorites-only JSON: 즐겨찾기/커스텀 타입/캡슐 라벨만 덮어쓰기.
- AI와 함께 활용하기: ChatGPT/Bard 등에게 “이 JSON 구조에 맞춰 새로운 키워드 목록을 만들어줘”라고 요청하고, 결과를 직접 편집해 기존 `prompts.json`과 병합하면 손쉽게 대규모 키워드 라이브러리를 구축할 수 있습니다.

## 로컬 실행

```bash
# 정적 파일이라 직접 열어도 되지만, 웹서버가 필요하면
python -m http.server 8080
# 그런 다음 http://localhost:8080/prompt_maker.html 로 접속
```

## 배포

정적 HTML만 있으면 되므로 GitHub Pages, Netlify, Cloudflare Pages 등 아무 호스팅에나 올릴 수 있습니다.

1. `prompt_maker.html`을 `index.html`로 리네임하거나 호스팅 환경에서 루트 경로에 둡니다.
2. `<head>`에 포함된 data URI 파비콘을 유지하면 주사위 아이콘이 자동 노출됩니다.
3. GitHub Pages 사용 시 Settings → Pages → `Deploy from branch`로 활성화하면 https://{username}.github.io/{repo}/ 경로에서 접근 가능합니다.

## MIT License

```
MIT License

Copyright (c) 2024 Promit

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
