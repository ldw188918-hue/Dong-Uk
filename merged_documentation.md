

---
# README.md
---

# 🚀 Hanwha Smart SCM Sentinel: AI 리스크 모니터링 시스템

> **글로벌 공급망 위기 대응을 위한 데이터 기반 AI 에이전트 구축 프로젝트**
> 
> 본 프로젝트는 한화그룹의 제조 및 방산 부문에서 발생하는 글로벌 공급망 리스크를 실시간으로 탐지하고, 비즈니스 영향도를 분석하여 최적의 대응 시나리오를 제안하는 시스템입니다.

---

## 📊 1. 프로젝트 현재 상태 (Project Status)

| 단계 | 태스크 | 상태 | 진행률 |
| :--- | :--- | :---: | :--- |
| **Phase 1** | 비즈니스 로직 및 PRD 설계 | ✅ 완료 | 100% |
| **Phase 2** | 외부 데이터(News/Index) 파이프라인 구축 | 🏃 진행중 | 75% |
| **Phase 3** | LLM 기반 리스크 스코어링 엔진 개발 | 🏃 진행중 | 40% |
| **Phase 4** | Slack/Email 알림 인터페이스 통합 | 📅 대기 | 0% |

---

## ⚙️ 2. 시스템 아키텍처 (System Architecture)

프로젝트의 전체 데이터 흐름과 로직 구조입니다.

```mermaid
graph TD
    subgraph "External Data Sources"
        A[Google News API] --- B[Commodity Price Index]
        B --- C[Geopolitical Feeds]
    end

    subgraph "AI Core Engine (Python/LLM)"
        D{Data Aggregator} --> E[NLP Risk Analyzer]
        E --> F[Decision Support Logic]
    end

    subgraph "Output & Monitoring"
        F --> G[Daily Dashboard]
        F --> H[Emergency Slack Alert]
    end

    A & B & C --> D

---
# github_issue.md
---

---
title: "[Project] AI 기반 로컬 비즈니스 인사이트 대시보드 구축"
labels: ["enhancement", "project"]
---

## 1. 작업 배경 (Work Background)
소상공인 및 비즈니스 소유자는 매출 데이터를 보유하고 있지만, 이를 분석하여 실질적인 비즈니스 인사이트를 도출하는 데 어려움을 겪고 있습니다. 
단순한 시각화를 넘어, 데이터 프라이버시를 보장하면서도 로컬 AI(Ollama)를 활용해 구체적인 행동 제안(예: 프로모션 시간 추천)을 제공하는 도구가 필요합니다.
본 프로젝트는 Python과 Streamlit을 활용하여 빠르게 MVP를 구축하고, 로컬 환경에서 동작하는 데이터 분석 및 AI 요약 대시보드를 제공하는 것을 목표로 합니다.

## 2. 작업 내용 (Work Content)
이 프로젝트는 아래의 핵심 모듈을 개발하는 것을 포함합니다. 상세 내용은 `tasks.md`를 따릅니다.

### A. 프로젝트 설정 및 데이터 수집
- [ ] Streamlit 기반 웹 애플리케이션 기본 구조 셋업
- [ ] CSV 및 Excel 파일 업로드 기능 구현 (Drag & Drop)
- [ ] 데이터 전처리 및 유효성 검사 모듈 개발

### B. 데이터 분석 및 시각화
- [ ] 핵심 KPI(매출, 주문수, 객단가) 계산 및 카드 UI 구현
- [ ] Plotly를 활용한 대화형 차트 구현 (매출 추이, 히트맵 등)
- [ ] 날짜 및 카테고리 필터링 기능

### C. AI 인사이트 연동
- [ ] 로컬 Ollama 모델 연동 및 데이터 요약 프롬프트 개발
- [ ] 분석 결과에 대한 자연어 요약 및 비즈니스 제안 생성 기능

## 3. 인수 조건 (Acceptance Criteria)
1.  **파일 업로드**: 사용자가 `.csv` 또는 `.xlsx` 파일을 업로드했을 때 에러 없이 데이터가 로드되어야 한다.
2.  **대시보드 출력**: 업로드 직후 총 매출 등 KPI와 주요 그래프(최소 2개 이상)가 화면에 표시되어야 한다.
3.  **AI 분석**: "AI 보고서 생성" 버튼 클릭 시, 30초 이내에 해당 데이터에 대한 텍스트 요약 및 제안이 출력되어야 한다.
4.  **프라이버시**: 모든 데이터 처리는 로컬에서 수행되어야 하며, 외부 서버로 데이터가 전송되지 않음을 보장해야 한다.

---
# prd
---

# 제품 요구사항 문서 (PRD): AI 기반 로컬 비즈니스 인사이트 대시보드

## 1. 개요 (Introduction)
*   **제품명**: BizInsight Local (가칭)
*   **목적**: 소상공인 및 비즈니스 소유자가 복잡한 데이터 분석 기술 없이도 매출 데이터를 시각화하고, AI를 통해 구체적인 액션 아이템을 도출할 수 있도록 돕는 도구입니다.
*   **핵심 가치**:
    *   **보안성**: 로컬 LLM을 활용하여 민감한 매출 데이터가 외부 서버로 전송되지 않음.
    *   **접근성**: 엑셀/CSV 파일 업로드만으로 즉시 사용 가능.
    *   **실용성**: 단순 통계를 넘어 "목요일 오후 2시 프로모션 추천"과 같은 구체적 제안 제공.

## 2. 타겟 사용자 (Target Audience)
*   데이터 분석 전담 인력이 없는 소상공인 (식당, 카페, 소매점 등).
*   매출 데이터(POS 엑셀 다운로드 등)는 보유하고 있으나 활용 방법을 모르는 사용자.

## 3. 사용자 스토리 (User Stories)
*   "카페 사장인 나는, 재고 관리를 위해 어떤 메뉴가 가장 빨리 소진되는지 알고 싶다."
*   "편의점 점주인 나는, 매출이 저조한 시간대를 파악하여 타임 세일 이벤트를 기획하고 싶다."
*   "사용자는 복잡한 설정 없이 엑셀 파일을 드래그 앤 드롭만으로 보고서를 보고 싶다."

## 4. 기능 요구사항 (Functional Requirements)

### 4.1 데이터 수집 (Data Ingestion)
*   **파일 업로드**: CSV, Excel (.xlsx, .xls) 파일 지원.
*   **전처리**:
    *   날짜/시간 컬럼 자동 인식 및 변환.
    *   결측치 간단 처리 (알림 및 제외).
    *   필수 컬럼 매핑 (예: 날짜, 상품명, 수량, 금액).

### 4.2 데이터 분석 및 시각화 (Analysis & Visualization)
*   **기본 대시보드**:
    *   총 매출, 총 주문 건수, 객단가(AOV) 등 핵심 KPI 카드 표시.
    *   일별/주별/월별 매출 트렌드 그래프 (Line Chart).
    *   요일별/시간대별 히트맵 (Heatmap) - 피크 타임 식별용.
    *   상품별 판매 순위 (Bar Chart).
*   **필터링**: 날짜 범위 설정 기능.

### 4.3 AI 기반 인사이트 (AI Insight Generation)
*   **로컬 LLM 연동**: Ollama API를 통해 로컬에서 실행 중인 모델(Llama 2, Mistral 등) 호출.
*   **자동 보고서 생성**:
    *   통계적 요약(예: "금요일 매출이 평일 평균 대비 150% 높음")을 자연어로 변환.
    *   비즈니스 제안(예: "금요일 저녁 재고를 1.5배 확보하세요").
*   **질의응다(Q&A)**: (Optional) 사용자가 "가장 많이 팔린 메뉴는?"이라고 물으면 데이터 기반 답변.

## 5. 기술 스택 (Technical Stack)
*   **Language**: Python 3.9+
*   **Frontend**: Streamlit (빠른 프로토타이핑 및 대시보드 구축)
*   **Data Analysis**: Pandas (데이터 핸들링), Numpy
*   **Visualization**: Plotly Express (인터랙티브 차트)
*   **AI/LLM**: Ollama (Local LLM 실행), LangChain (Optional, 추후 확장 시 고려)

## 6. 비기능 요구사항 (Non-Functional Requirements)
*   **데이터 프라이버시**: 모든 데이터 처리는 사용자의 로컬 환경에서 이루어져야 함.
*   **성능**: 10MB 이하의 파일에 대해 30초 이내에 초기 분석 완료.
*   **사용성**: 개발 지식이 없는 사용자도 설치 및 실행이 간편해야 함 (향후 패키징 고려).

## 7. 향후 확장 계획 (Roadmap)
*   **v1.0 (MVP)**: CSV 업로드 -> 대시보드 -> 텍스트 요약.
*   **v1.1**: 여러 파일 병합 기능 (월별 데이터 합치기).
*   **v2.0**: 예측 모델(Forecasting) 도입 (다음 달 매출 예측).

---
# tasks.md
---

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

---
# tutorial.md
---

# [Tutorial] AI 기반 로컬 비즈니스 인사이트 대시보드 만들기

이 튜토리얼은 Python, Streamlit, 그리고 Ollama를 활용하여 **로컬 환경에서 동작하는 데이터 분석 및 AI 인사이트 대시보드**를 처음부터 끝까지 만드는 과정을 설명합니다.

## 1. 사전 준비 (Prerequisites)
이 프로젝트를 시작하기 전에 다음 도구들이 설치되어 있어야 합니다.
*   **Python 3.9 이상**: [python.org](https://www.python.org/)에서 다운로드.
*   **VS Code** (또는 선호하는 IDE).
*   **Ollama**: 로컬 LLM 실행을 위해 [ollama.com](https://ollama.com/)에서 다운로드 및 설치.
    *   설치 후 터미널에서 `ollama pull llama2` (또는 `mistral`) 명령어로 모델을 다운로드하세요.

## 2. 프로젝트 환경 설정
먼저 작업 폴더를 만들고 가상환경을 설정합니다.

```bash
mkdir biz_dashboard
cd biz_dashboard
python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate
```

필요한 라이브러리를 설치합니다.
```bash
pip install streamlit pandas plotly openpyxl requests
```

## 3. 단계별 구현 가이드

### Step 1: 기본 UI 및 파일 업로드 구현
`app.py` 파일을 생성하고 기본 골격을 잡습니다.
```python
import streamlit as st
import pandas as pd

st.title("📊 AI 로컬 비즈니스 인사이트")

uploaded_file = st.file_uploader("엑셀 또는 CSV 파일을 업로드하세요", type=["csv", "xlsx"])

if uploaded_file:
    df = pd.read_csv(uploaded_file) if uploaded_file.name.endswith('csv') else pd.read_excel(uploaded_file)
    st.write("데이터 미리보기:", df.head())
```
터미널에서 실행: `streamlit run app.py`

### Step 2: 데이터 시각화 (KPI & Charts)
데이터가 로드되면 핵심 지표를 보여줍니다.
```python
import plotly.express as px

# (app.py 계속)
if uploaded_file:
    # ... 데이터 로드 코드 ...
    
    # KPI 계산
    total_revenue = df['Amount'].sum()
    st.metric("총 매출", f"{total_revenue:,}원")
    
    # 차트 그리기
    fig = px.line(df, x='Date', y='Amount', title='일별 매출 추이')
    st.plotly_chart(fig)
```

### Step 3: Ollama로 AI 인사이트 생성하기
로컬 LLM에게 데이터 요약을 요청하는 함수를 만듭니다.
```python
import requests
import json

def get_ai_insight(data_summary):
    url = "http://localhost:11434/api/generate"
    prompt = f"다음 매출 데이터를 분석하고 사장님을 위한 3줄 조언을 해줘: {data_summary}"
    
    payload = {
        "model": "llama2",
        "prompt": prompt,
        "stream": False
    }
    response = requests.post(url, json=payload)
    return response.json()['response']

# 버튼 클릭 시 실행
if st.button("AI 인사이트 생성"):
    summary_text = df.describe().to_string() # 간단한 통계 요약
    insight = get_ai_insight(summary_text)
    st.success(insight)
```

## 4. 실행 및 테스트
1. 올라마(Ollama)가 실행 중인지 확인합니다.
2. `streamlit run app.py`를 실행합니다.
3. 준비된 샘플 엑셀 파일을 업로드하고 차트와 AI 조언이 나오는지 확인합니다.

## 5. 마무리
축하합니다! 이제 데이터 프라이버시 걱정 없는 나만의 비즈니스 분석 비서가 완성되었습니다.
이 튜토리얼을 바탕으로 기능을 확장해 보세요 (예: 파일 병합, 예측 모델 추가 등).
