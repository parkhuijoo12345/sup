# NETLAB — 네트워크관리사 2급 학습실

원본 NA2-study의 문제은행 데이터를 활용하지만, 화면과 학습 흐름은 새로 설계한 독립 학습 사이트입니다.

## 문제 데이터 저장 방식

- 사이트는 `./data/bank.json`을 읽습니다.
- `data/bank.json`은 동기화 작업이 완료되면 **이 `sup` 저장소 안에 실제 파일로 저장**됩니다.
- 방문자의 브라우저는 다른 저장소의 원본 URL을 직접 요청하지 않습니다.
- 데이터 동기화는 GitHub Actions의 **Sync question bank into this repository** 워크플로에서 수행합니다.
- 워크플로는 수동 실행할 수 있으며, `index.html`, `README.md` 또는 해당 워크플로 파일이 `main`에 변경될 때도 실행됩니다.
- 원본 데이터 출처: https://github.com/sumilee-phd/NA2-study/blob/main/public/data/bank.json

## 구현된 기능

- 원본 문제은행의 전체 문항 수와 회차 반영
- 회차별 연습 및 실전형 학습 세션
- 문제 검색, 연도·회차·과목·풀이 상태 필터
- 원문 문제 이미지와 선택지 표시
- 정답 확인, 이전·다음 이동, 문항 번호 이동
- 오답 복습, 북마크, 미풀이 우선 10문항
- 풀이 시도·정답률·학습일·세션 기록
- JSON 학습 기록 백업 및 복원
- PC·모바일 반응형 화면

## 배포 및 최초 설정

1. GitHub 저장소의 **Actions** 탭에서 `Sync question bank into this repository` 워크플로가 성공했는지 확인합니다.
2. 저장소의 `data/bank.json` 파일이 생성되었는지 확인합니다.
3. **Settings → Pages**에서 `Deploy from a branch`, `main`, `/(root)`를 선택합니다.
4. GitHub Pages가 배포를 완료하면 `https://parkhuijoo12345.github.io/sup/`에서 접속합니다.

워크플로가 파일을 커밋하려면 저장소 설정에서 Actions의 `GITHUB_TOKEN` 쓰기 권한이 허용되어야 합니다. 워크플로가 실패하면 Actions 로그에서 원인을 확인해야 합니다.

## 학습 기록

학습 기록은 현재 브라우저의 `localStorage`에 저장됩니다. 다른 브라우저나 기기와 자동 동기화되지는 않으므로, 다른 기기로 옮길 때는 JSON 백업을 사용하세요.

## 참고

문제 원문 이미지에 별도 해설 텍스트가 없는 문항은 정답 번호를 표시합니다. 이 버전은 필기 문제은행을 중심으로 구현되어 있으며, 이론·실기 자료는 별도 통합 작업이 필요합니다.
