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
