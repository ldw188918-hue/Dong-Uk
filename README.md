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
