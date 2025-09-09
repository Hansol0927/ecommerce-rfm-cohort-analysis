# 📌 이커머스 고객 RFM·Cohort 분석
개인 프로젝트 (2025)  
RFM 기반 고객 세분화, K-means 군집화, Cohort 리텐션 분석 수행

---

## 📄 프로젝트 개요
- **목표**: 고객 구매 데이터를 기반으로 RFM 분석·군집화·Cohort 분석을 통해 고객 행동 패턴을 파악하고 맞춤형 CRM 전략을 제안  
- **데이터**: 부트캠프 제공 이커머스 거래 데이터 (541,909건 → 전처리 후 397,884건, 고객 수 4,338명, 37개국)
- **기간**: 2025.08 (2주)  
- **형태**: 개인 프로젝트  

---

## 📂 파일 구성
```
project_rfm_cohort/
├─ README.md # 프로젝트 소개 문서
├─ ecommerce-rfm-cohort.ipynb # 전체 분석 코드 (EDA → RFM → 군집화 → Cohort)
└─ data/
└─ S_PJT06_DATA_rfm.csv # 원본 데이터 (부트캠프 제공)
```
---

## 📄 데이터 출처
본 프로젝트는 **부트캠프에서 제공된 이커머스 거래 데이터**를 기반으로 진행되었습니다.  
레포에는 **재현 목적의 샘플 데이터(sample_ecommerce_rfm.csv, 100행)**만 포함되어 있습니다.  
전체 데이터는 공개되지 않은 학습용 자료로, 별도 제공되지 않습니다.

---

## 📄 분석 및 모델링 과정
### 1. 데이터 전처리
- Null 값 제거 (CustomerID 기준)
- Quantity, UnitPrice 음수값 제거
- 고객별 Recency·Frequency·Monetary 지표 생성

### 2. RFM 분석
- R/F/M 지표 min-max 스케일링 후 Score 산출 (0~100점)  
- Rule-based 등급화 (Very Strong ~ Very Weak, 5등급)  
- 등급별 고객 수 vs 매출 기여율 비교 → **소수 VIP에 과도한 매출 의존 확인**

### 3. K-means 군집화
- Feature: Recency, Frequency, Monetary  
- Elbow & Silhouette → 최적 K=4 선정  
- Cluster 특성:  
  - Cluster 0: 충성 고객군  
  - Cluster 1: 저관여 고객군  
  - Cluster 2: 신규·잠재 고객군  
  - Cluster 3: 휴면·이탈 고객군  

### 4. Cohort 분석
- CohortMonth & CohortIndex 산출  
- 고객 잔존율(리텐션) Heatmap 시각화  
- **공통 패턴**: 첫 달 이후 급격한 이탈, 일부 Cohort에서 재활성화 반등 확인  

---

## 📄 주요 결과
- **RFM 분석**: 고객 기반은 소수 VIP 중심의 파레토(20:80) 구조  
- **K-means**: Rule-based Normal 그룹을 더 세밀하게 나눠 실행 가능한 전략 도출  
- **Cohort**: 온보딩 실패 → 첫 달 급격한 이탈, 재구매 유도 필요  

---

## 📄 인사이트 & 기대 효과
- **충성 고객군(Cluster 0)**: VIP 관리 강화 → 매출 안정성 확보  
- **저관여 고객군(Cluster 1)**: 리마인드·프로모션 → 활동성 회복  
- **신규 고객군(Cluster 2)**: 온보딩·첫 구매 프로모션 → 재구매 유도  
- **휴면 고객군(Cluster 3)**: 재활성화 캠페인 → 비용 효율적 관리  

▶ **기대 효과**  
- 충성 고객 리텐션 강화 → 핵심 매출 유지  
- 신규/저관여 고객 활성화 → 고객 모수 확대  
- 휴면 고객 관리 효율화 → 비용 최적화  

---

## 📄 기술 스택
- **Python**: Pandas, NumPy, Scikit-learn  
- **Visualization**: Matplotlib, Seaborn  
- **분석 환경**: Jupyter Notebook (Google Colab)  
- **협업/관리**: Git, GitHub  

---

## 📄 참고
- 본 프로젝트는 **학습·포트폴리오 목적으로 진행**되었으며, 실제 기업 데이터가 아님을 명시합니다.
