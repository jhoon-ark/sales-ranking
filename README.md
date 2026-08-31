# sales-ranking

일본 App Store 게임 매출 랭킹을 하루 4회 수집하고, 순위가 움직인 요인을
공식 고지 · 인앱 이벤트 · 배포 노트에서 특정해 주 단위로 정리한 기록.

- 한국어 <https://GITHUB_USER.github.io/sales-ranking/>
- 日本語 <https://GITHUB_USER.github.io/sales-ranking/index_ja.html>

## 발행

    python3 sellran_weekly.py --week 35     # briefs/ 에 한국어·일본어 리포트 생성
    python3 sellran_publish.py --commit     # site/ 갱신 후 커밋
    git -C site push

## 최초 1회 설정

1. GitHub 에서 `sales-ranking` 저장소를 만든다 (비어 있는 상태로).
2. 아래를 실행한다.

        cd ~/sellran/site
        git init -b main
        git remote add origin git@github.com:GITHUB_USER/sales-ranking.git
        git add -A && git commit -m "first publish"
        git push -u origin main

3. 저장소 Settings → Pages → Source 를 `main` / `/ (root)` 로 지정한다.
4. `python3 sellran_publish.py` 를 한 번 더 돌린다.
   remote 가 생겼으므로 OG 태그의 이미지·주소가 절대경로로 채워진다.
   그 뒤 커밋·푸시하면 페이스북 링크 프리뷰가 뜬다.

## 구성

    site/index.html      주차 목록 (한국어)
    site/index_ja.html   주차 목록 (일본어)
    site/w/YYYY-Www.html 주간 리포트
    site/og/YYYY-Www.png 링크 프리뷰 이미지 1200×630
    site/og/*_sq.png     페이스북 직접 업로드용 1080×1080
    site/og/YYYY-Www.json  OG 제목·설명 수동 지정 (없으면 본문에서 자동 추출)
