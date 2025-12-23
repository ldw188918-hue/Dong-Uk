# GitHub Pages 배포 가이드

## 🎯 목표
Marp 프레젠테이션을 HTML로 변환하여 GitHub Pages에 배포하기

## ✅ 완료된 작업
1. ✅ Marp 마크다운 파일 확인 (`Presentation_MARP.md`)
2. ✅ Python 스크립트로 HTML 변환 (`presentation.html` 생성)

## 📋 GitHub 업로드 및 배포 단계

### 방법 1: 현재 저장소에 배포

#### Step 1: GitHub 저장소 확인
먼저 현재 디렉토리가 Git 저장소인지 확인하세요.
```bash
git status
```

#### Step 2: 파일 추가 및 커밋
```bash
# HTML 파일 추가
git add grouped_docs/presentation.html

# 커밋
git commit -m "Add: HTML presentation for BizInsight Local"

# GitHub에 푸시
git push origin main
```
> **Note**: 브랜치 이름이 `main`이 아닌 `master`일 수 있습니다. `git branch` 명령으로 확인하세요.

#### Step 3: GitHub Pages 활성화
1. GitHub 저장소 페이지로 이동
2. **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 클릭
4. **Source** 섹션에서:
   - Branch: `main` (또는 `master`) 선택
   - Folder: `/ (root)` 선택
5. **Save** 버튼 클릭

#### Step 4: 프레젠테이션 접속
몇 분 후 다음 URL로 접속할 수 있습니다:
```
https://YOUR_USERNAME.github.io/REPO_NAME/grouped_docs/presentation.html
```

---

### 방법 2: 별도의 프레젠테이션 전용 저장소 생성 (추천)

더 깔끔한 URL을 원하신다면 별도 저장소를 만드는 것을 추천합니다.

#### Step 1: 새 GitHub 저장소 생성
1. GitHub에서 **New Repository** 클릭
2. Repository name: `bizinsight-presentation`
3. Public으로 설정
4. **Create repository** 클릭

#### Step 2: 로컬에서 새 디렉토리 생성 및 초기화
```bash
# 새 디렉토리 생성
mkdir bizinsight-presentation
cd bizinsight-presentation

# Git 초기화
git init

# HTML 파일 복사
copy ..\doc\grouped_docs\presentation.html index.html

# README 파일 생성 (선택사항)
echo "# BizInsight Local Presentation" > README.md

# 파일 추가
git add .

# 커밋
git commit -m "Initial commit: Add presentation"

# GitHub 저장소와 연결 (YOUR_USERNAME을 본인 계정으로 변경)
git remote add origin https://github.com/YOUR_USERNAME/bizinsight-presentation.git

# 푸시
git branch -M main
git push -u origin main
```

#### Step 3: GitHub Pages 활성화
- 위의 **방법 1의 Step 3**과 동일

#### Step 4: 프레젠테이션 접속
```
https://YOUR_USERNAME.github.io/bizinsight-presentation/
```
> 파일 이름을 `index.html`로 했기 때문에 URL이 더 간단합니다!

---

## 🎨 프레젠테이션 사용법

생성된 HTML 프레젠테이션은 다음 기능을 제공합니다:

### 조작 방법
- **→ (오른쪽 화살표)** 또는 **Space**: 다음 슬라이드
- **← (왼쪽 화살표)**: 이전 슬라이드
- 화면 하단의 **이전/다음 버튼** 클릭

### 특징
- 📱 반응형 디자인 (모바일/태블릿/데스크톱 지원)
- 🎨 그라디언트 배경과 모던한 UI
- 📊 슬라이드 카운터 표시
- ⌨️ 키보드 단축키 안내

---

## 🔧 추가 커스터마이징

HTML 파일을 직접 편집하여 다음을 변경할 수 있습니다:
- 색상 테마 (CSS의 `linear-gradient` 값 수정)
- 폰트 크기
- 애니메이션 효과
- 배경 이미지 추가

---

## 📝 체크리스트
- [ ] Git 저장소 확인
- [ ] HTML 파일 커밋 및 푸시
- [ ] GitHub Pages 활성화
- [ ] URL 접속 확인
- [ ] 발표 자료 최종 점검
