# 🚀 BizInsight Local

> **소상공인을 위한 프라이버시 보호형 AI 비즈니스 인사이트 대시보드**
> *"당신의 데이터는 로컬에, 통찰은 비즈니스에."*

<div align="center">

[![Python Version](https://img.shields.io/badge/python-3.9+-blue.svg?style=flat-square&logo=python)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Framework-Streamlit-FF4B4B.svg?style=flat-square&logo=streamlit)](https://streamlit.io/)
[![AI Engine](https://img.shields.io/badge/AI-Ollama_(Local_LLM)-black.svg?style=flat-square&logo=ollama)](https://ollama.com/)
[![PR Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

</div>

---

## 📖 프로젝트 개요 (Introduction)

많은 소상공인 및 비즈니스 오너들이 POS 시스템을 통해 귀중한 매출 데이터를 보유하고 있지만, 복잡한 데이터 분석 기술의 장벽으로 인해 이를 의사결정에 충분히 활용하지 못하고 있습니다.

**BizInsight Local**은 이러한 문제를 해결하기 위한 **프라이버시 중심의 로컬 BI(Business Intelligence) 도구**입니다. 사용자는 엑셀/CSV 파일을 업로드하는 것만으로 직관적인 시각화 대시보드와 로컬 LLM이 제공하는 구체적인 경영 전략을 얻을 수 있습니다.

### 💡 핵심 가치 (Core Value Proposition)

| 가치 | 설명 |
| :--- | :--- |
| **🔒 보안성 (Privacy First)** | 민감한 매출 데이터를 외부 서버(OpenAI 등)로 전송하지 않고, **100% 로컬 환경**에서 안전하게 분석합니다. |
| **⚡ 접근성 (Easy Access)** | 데이터 분석 지식이 전혀 없어도 파일 드래그 앤 드롭만으로 즉시 사용 가능합니다. |
| **🎯 실용성 (Actionable Insight)** | 단순 통계를 넘어 "목요일 오후 2시 타임세일 추천"과 같은 구체적인 실행 방안을 제안합니다. |

---

## ⚙️ 작동 원리 (How It Works)

데이터가 투입되어 인사이트로 변환되기까지의 데이터 흐름도입니다.

```mermaid
graph LR
    A[📂 엑셀/CSV 업로드] --> B(⚙️ 데이터 전처리<br>Pandas/Numpy);
    B --> C{📊 BI 대시보드<br>Streamlit/Plotly};
    C --> D[🤖 로컬 LLM 분석<br>Ollama API];
    D --> E[💡 전략 리포트 생성<br>자연어 제안];
