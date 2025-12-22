# 🚀 BizInsight Local (가칭)
> **소상공인을 위한 프라이버시 보호형 AI 비즈니스 대시보드**

본 프로젝트는 매출 데이터를 외부 서버로 전송하지 않고 로컬 환경에서 분석하여, 소상공인에게 실질적인 비즈니스 액션 아이템을 제안하는 도구입니다.

## ✨ 핵심 기능
- **Data Security:** Ollama를 활용한 로컬 LLM 연동으로 매출 데이터 유출 원천 차단.
- **Auto Dashboard:** 엑셀/CSV 업로드만으로 매출 트렌드, 피크 타임 히트맵, 상품 순위 자동 시각화.
- **AI Strategy:** 데이터 기반의 맞춤형 경영 제안 (예: "목요일 오후 재고 확보 권장").

## 🛠 Tech Stack
- **Language:** Python 3.9+
- **Frontend/App:** Streamlit
- **Data:** Pandas, Plotly
- **AI:** Ollama (Llama 3 / Mistral)

## ⚙️ 실행 방법
1. **Ollama 설치 및 모델 실행:**
   ```bash
   ollama run llama3
