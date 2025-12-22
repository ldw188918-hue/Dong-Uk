# 개발 태스크 (Development Tasks): AI 기반 로컬 비즈니스 인사이트 대시보드

이 문서는 PRD를 기반으로 작성된 기능 구현을 위한 상세 태스크 리스트입니다.

## 1. 프로젝트 설정 (Project Setup)
- [ ] **환경 설정**
    - [ ] Python 3.9+ 가상환경(venv/conda) 생성
    - [ ] `requirements.txt` 작성 (`streamlit`, `pandas`, `plotly`, `openpyxl`, `requests` 등)
- [ ] **Git 초기화**
    - [ ] `.gitignore` 설정 (가상환경, 데이터 파일 제외)
    - [ ] 레포지토리 초기화

## 2. 데이터 수집 모듈 (Data Ingestion)
- [ ] **파일 업로드 UI 구현**
    - [ ] Streamlit `file_uploader` 위젯 추가 (CSV, XLSX 지원)
- [ ] **데이터 로더 구현**
    - [ ] Pandas로 파일 읽기 함수 작성
    - [ ] **유효성 검사**: 필수 컬럼(날짜, 금액 등) 확인 로직
    - [ ] **전처리**: 날짜 포맷 통일, 결측치 처리(0으로 대치 또는 알림)

## 3. 데이터 분석 및 시각화 (Analysis & Visualization)
- [ ] **KPI 계산 로직**
    - [ ] 총 매출(Total Revenue) 계산
    - [ ] 총 주문 건수(Total Orders), 객단가(AOV) 계산
    - [ ] 일평균 매출 계산
- [ ] **차트 시각화**
    - [ ] **[Line]** 일별/월별 매출 트렌드 그래프
    - [ ] **[Bar]** 인기 상품 TOP 10 랭킹
    - [ ] **[Heatmap]** 요일별/시간대별 혼잡도 분석 (히트맵)
- [ ] **필터링 기능**
    - [ ] 사이드바에 날짜 범위(Date Range) 선택 기능 추가

## 4. AI 인사이트 연동 (AI Insight Generation)
- [ ] **Ollama 연동 설정**
    - [ ] 로컬 Ollama 실행 확인 체크 로직
    - [ ] Python API 또는 `requests`로 Ollama와 통신하는 래퍼(Wrapper) 함수 작성
- [ ] **프롬프트 엔지니어링**
    - [ ] 데이터 요약 프롬프트 템플릿 작성 (DataFrame 통계치를 텍스트로 변환하여 주입)
    - [ ] "비즈니스 인사이트" 도출을 위한 시스템 프롬프트 최적화
- [ ] **인사이트 UI**
    - [ ] 분석 완료 후 "AI 보고서 생성" 버튼 및 결과 출력 영역 구현

## 5. UI/UX 통합 및 배포 준비
- [ ] **레이아웃 구성**
    - [ ] 3단 레이아웃 (KPI 상단, 차트 중앙, AI 인사이트 하단)
    - [ ] 스타일링 (Streamlit 기본 테마 활용 및 커스텀 CSS 필요시 적용)
- [ ] **사용자 테스트 (MVP)**
    - [ ] 샘플 데이터(.csv)로 전체 플로우(업로드 -> 분석 -> AI 결과) 테스트
