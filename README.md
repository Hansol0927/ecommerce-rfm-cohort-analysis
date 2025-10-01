# 📌 이커머스 고객 RFM·Cohort 분석
개인 프로젝트 (2025)  
RFM 기반 고객 세분화, K-means 군집화, Cohort 리텐션 분석 수행

---

## 📄 프로젝트 개요
- **목표**: 고객 구매 데이터를 기반으로 RFM 분석·군집화·Cohort 분석을 통해 고객 행동 패턴을 파악하고 맞춤형 CRM 전략을 제안  
- **데이터**: 부트캠프 제공 이커머스 거래 데이터 (541,909건 → 전처리 후 397,884건, 고객 수 4,338명, 37개국)
- **기간**: 2025.06 (2주)  
- **형태**: 개인 프로젝트  

---

## 📂 파일 구성
```
project_rfm_cohort/
├─ README.md # 프로젝트 소개 문서
├─ ecommerce-rfm-cohort.ipynb # 전체 분석 코드 (EDA → RFM → 군집화 → Cohort)
└─ data/
└─ sample_ecommerce_rfm.csv (재현용 샘플 데이터 (100행)
```
---

## 📄 데이터 출처
본 프로젝트는 부트캠프에서 제공된 이커머스 거래 데이터를 기반으로 진행되었습니다.  
레포에는 재현 목적의 샘플 데이터(sample_ecommerce_rfm.csv, 100행)만 포함되어 있습니다.  
전체 데이터는 공개되지 않은 학습용 자료로, 별도 제공되지 않습니다.

---

## 📄 분석 및 모델링 과정
### 1. 데이터 전처리
- CustomerID Null 값 제거
- Quantity, UnitPrice 음수값 제거
- 이상치(대량 주문·고가 상품)는 VIP/B2B 거래로 판단, 제거하지 않고 분석에 포함
- 고객별 Recency·Frequency·Monetary 지표 생성

### 2. RFM 분석
- R/F/M 지표 min-max 스케일링 후 Score 산출 (0~100점)  
- Rule-based 5등급 분류 (Very Strong ~ Very Weak)
- 결과:  
  - 상위 20% 고객이 매출의 약 **66.5%** 기여  
  - 고객 수가 가장 많은 Normal 그룹은 매출 기여가 낮음  
  - 전형적인 **파레토(20:80) 구조** 확인  

### 3. K-means 군집화
- Feature: Recency, Frequency, Monetary  
- Elbow & Silhouette → 최적 K=4 선정  
- Cluster 특성:  
  - Cluster 0: Core Value (핵심 활동 고객군, 매출 80% 차지)
  - Cluster 1: At-Risk (이탈 위험 고객군, 매출 5%) 
  - Cluster 2: Growth (신규 성장 고객군, 매출 12%)  
  - Cluster 3: Dormant (휴면 고객군, 매출 3%)
*  Rule-based Normal 그룹을 Core Value / At-Risk / Growth로 재구성 → 차별화된 전략 도출

### 4. Cohort 분석
- CohortMonth, CohortIndex 산출 후 리텐션율(잔존율) 계산  
- 전체 고객 공통 패턴:  
  - 첫 달 이탈률 급격히 높음 → 온보딩·재구매 유도 필요  
  - 일부 Cohort에서 2~4개월차 재활성화 반등 발생  
- Cluster별 차이:  
  - Core Value: 1개월차 평균 잔존율 30% 이상 (안정적)  
  - Growth: 낮은 초기 유지율, 후반 반등 여지 있음  
  - At-Risk: 초기 급격한 이탈 (평균 15%)  
  - Dormant: 장기 유지 불가, ROI 낮음  
---

## 📄 주요 결과
- **RFM 분석**: 고객 기반은 소수 VIP 중심의 파레토(20:80) 구조  
- **K-means**: Rule-based 단순 구간화 대비 정교한 세분화 → 실행 가능한 전략 도출  
- **Cohort**: 첫 달 이탈이 공통 문제, 일부 고객군은 재활성화 가능성 존재  


---

## 📄 인사이트 & 기대 효과  

### 클러스터별 전략 제안  
- **Core Value (Cluster 0)**: VIP 멤버십·장기 리워드 / **행동 패턴을 다른 고객군에 확산** → 매출 안정성 확보  
- **At-Risk (Cluster 1)**: 장바구니 리마인드·자동화 케어 플로우 / 불만족 요인 개선 → 이탈 방어  
- **Growth (Cluster 2)**: 온보딩 프로세스 강화 / **Cohort 기반 2~4개월차 집중 프로모션** / Cross-sell·Up-sell  → 전환 촉진  
- **Dormant (Cluster 3)**: 저비용 자동화 관리 / 과거 Core Value 경험 고객 선택적 집중 / ROI 고려한 선택적 대응  

### 기대 효과  
- Core Value 고객 리텐션 강화 → 핵심 매출 안정성 확보  
- Growth·At-Risk 활성화 → 매출 성장 및 구조 다변화  
- Dormant 효율적 관리 → 비용 최적화  

---

## 📄 기술 스택  
- **Python**: Pandas, NumPy, Scikit-learn  
- **Visualization**: Matplotlib, Seaborn  
- **분석 환경**: Jupyter Notebook (Google Colab)  
- **협업/관리**: Git, GitHub  

---

## 📄 참고  
본 프로젝트는 **학습·포트폴리오 목적으로 진행**되었으며, 실제 기업 데이터가 아님을 명시합니다.  
