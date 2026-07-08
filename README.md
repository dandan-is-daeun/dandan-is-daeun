# ☁️ Cloud Data Engineer | 안다은 (Daeun Ahn)

"문제 흐름을 구조적으로 분석하고, 팀과 함께 완성도 있는 소프트웨어를 만들어가는 개발자입니다."

<div align="left">
  <a href="mailto:cyma54@naver.com"><img src="https://img.shields.io/badge/Email-cyma54@naver.com-blue?style=flat-square&logo=Gmail&logoColor=white"/></a>
  <a href="https://www.notion.so/dandan-is-dandan/29f40052297f8181872ff6d6a8ae2fbd?source=copy_link" target="_blank"><img src="https://img.shields.io/badge/Notion-Portfolio-black?style=flat-square&logo=Notion&logoColor=white"/></a>
</div>

---

## 🛠️ Tech Stacks

* **Cloud & Platform:** `Azure Ecosystem`, `GCP (Google Cloud Platform)`
* **Data Pipeline:** `Azure Event Hubs`, `Stream Analytics`, `Azure Data Factory`
* **Serverless & AI:** `Azure Functions`, `Azure Databricks`, `Azure OpenAI`
* **Languages & DB:** `Python`, `Pandas`, `SQL`, `Embedded Robot Control`

---

## 🚀 Key Projects

### 1. Azure 기반 가상 멀티 에이전트 주식 시장 시뮬레이션 (`2026.06 ~ 2026.07`)
* **Description:** 가상 참여자(에이전트)의 주문과 외부 변수가 시장 가격 및 체결 구조에 미치는 영향을 관찰할 수 있는 실시간 트랜잭션 수집 및 시뮬레이션 데이터 아키텍처 구축 프로젝트입니다.
* **Tech Stack:** `Azure Event Hubs`, `Azure Stream Analytics`, `Azure Databricks`, `Azure SQL Database`, `Azure OpenAI`, `Python`
* **Role:** **팀장 및 데이터 엔지니어 / 클라우드 아키텍처 설계 총괄**
* **Detailed Core Tasks:** * **인프라 계층 분리 설계:** 동시다발적인 대규모 거래 트랜잭션이 발생하는 체결 엔진의 특성을 고려하여, 실시간 데이터 처리 레이어(`Event Hubs` + `Stream Analytics`)와 장기적인 거래 패턴 분석을 위한 배치 레이어(`Databricks`)의 저장 구조를 완전히 분리 설계했습니다.
  * **스트리밍 파이프라인 구축:** 체결 이벤트 데이터를 `Event Hubs`로 유실 없이 수집하고, `Stream Analytics`를 연동하여 실시간 호가창(Order Book) 및 체결 가격 변화를 윈도우 기반으로 가공하는 스트리밍 흐름을 구현했습니다.
  * **AI 변수 연동 및 적재:** `Azure OpenAI`를 통해 금리, 뉴스 등 외부 변수에 반응하는 에이전트의 투자 심리 상태 데이터를 생성하고, `Databricks`로 전처리 및 군집화(Clustering)하여 어드민 대시보드 백엔드용 `Azure SQL DB` 스키마와 유기적으로 연동했습니다.
* **Technical Troubleshooting:**
  * *Problem:* 대규모 가상 매매가 동시 체결될 때 정형 DB(Azure SQL DB) 저장소에 원시 데이터가 다이렉트로 유입되면서 인덱스 락 및 적재 지연(Latency) 현상이 식별되었습니다.
  * *Solution:* 원시 로그는 즉시 가벼운 스토리지 레이어로 바이패스하고, 대시보드 서빙에 필수적인 집계 데이터만 `Stream Analytics`에서 1차 마이크로 배칭 처리 후 정형 DB에 적재되도록 파이프라인을 최적화하여 병목을 해결했습니다.

<img src="./images/stock-pipeline.png" width="80%" alt="Stock Pipeline Architecture"/>

<br>

### 2. Azure 기반 실시간 EV 배터리 이상 탐지 시스템 (`2026.06 ~ 2026.06`)
* **Description:** 대용량 차량 시뮬레이터 센서 데이터를 클라우드 환경에서 실시간으로 인제스션하고, 이상 탐지 결과를 최종 서비스 화면까지 끊김 없이 전달하는 End-to-End 파이프라인 프로젝트입니다.
* **Tech Stack:** `Azure IoT Hub`, `Azure Stream Analytics`, `Azure SQL Database`, `Azure Functions`, `Python`
* **Role:** **팀장 및 데이터 엔지니어** (전체 파이프라인 인프라 설계, 데이터 흐름 구현)
* **Detailed Core Tasks:**
  * **스트리밍 수집 파이프라인 구축:** Python 기반 차량 시뮬레이터에서 송출되는 전압, 전류, 온도 등 시계열 배터리 멀티 센서 데이터를 `Azure IoT Hub`로 안정적으로 수집·유지하는 엔드포인트를 설계했습니다.
  * **실시간 필터링 및 판단 로직:** `Stream Analytics` 쿼리를 활용해 수집되는 스트리밍 데이터에서 이상 징후 임계값을 실시간으로 탐지하고 정제하는 필터링 로직을 아키텍처 단에 내재화했습니다.
  * **서빙 레이어 구현:** 탐지된 이상 징후 결과 데이터를 `Azure SQL DB`에 실시간 적재함과 동시에, 서버리스 인프라인 `Azure Functions` 트리거 및 REST API를 통해 모니터링 웹 대시보드 화면에 지연 없이 실시간 표출되는 전 과정을 검증했습니다.

<img src="./images/ev-pipeline.png" width="80%" alt="EV Battery Pipeline Architecture"/>

<br>

### 3. ETRI 제지공정 전력 최적화 및 스팀량 예측 분석 (`2024.02 ~ 2024.09`)
* **Description:** 한국전자통신연구원(ETRI) 과제로서 산업 실증 데이터를 기반으로 초지 공정의 전건조 및 후건조 단계 에너지 효율을 분석하고 최적화 모니터링 방안을 도출한 연구 프로젝트입니다.
* **Tech Stack:** `Python`, `Pandas`, `LSTM`, `Data Visualization`, `Heatmap`
* **Role:** **연구 보조원** (산업 공정 데이터 전처리 알고리즘 및 시계열 분석 모델링 개발)
* **Detailed Core Tasks:**
  * **산업용 데이터 정제:** 실제 제지공정 설비 센서에서 발생한 대규모 누락값(결측치)과 비정상값(이상치)을 도메인 특성에 맞게 전처리하고, 복잡한 지종 및 평량별 공정 조건에 맞게 데이터를 정형화했습니다.
  * **특성 변수 선택 및 상관관계 분석:** 공정 내 수많은 센서 태그(Tag) 변수들과 전·후건조 스팀 사용량 간의 인과관계를 상관관계 히트맵(Heatmap) 시각화로 검토하여 물리적 모델 성능에 영향을 미치는 핵심 변수를 추출했습니다.
  * **예측 모델 및 도메인 검증:** 추출된 변수를 기반으로 LSTM 시계열 예측 모델을 설계하여 변수 선택이 예측 정확도에 미치는 영향을 평가하고, 건조 과정 후 응축 열인 회수열 데이터와 연동 분석하여 최적의 에너지 모니터링 평가지표를 검토했습니다.

<img src="./images/etri-analysis.png" width="80%" alt="ETRI Research Analysis"/>

<br>

### 4. 딥러닝 기반 딸기 숙성도 분류 및 로봇 팔 수확 자동화 (`2025.01 ~ 2025.10`)
* **Description:** AI 비전 인식 기술을 통해 딸기의 성숙도와 정확한 위치 좌표를 식별하고, 이를 물리적 임베디드 로봇 제어 시스템과 실시간 연동하여 수확을 자동화하는 하드웨어-소프트웨어 융합 시스템입니다.
* **Tech Stack:** `Python`, `Nvidia Jetson Nano`, `Embedded Robot Control`, `Deep Learning Object Detection`
* **Core Tasks:**
  * **좌표계 매핑 데이터 연동:** 2D 비전 카메라 센서로 탐지된 딸기의 픽셀 좌표 정보를 로봇팔이 물리적 공간에서 타겟팅하여 이동할 수 있도록 실제 3차원 공간 좌표계로 실시간 변환하는 수치 연동 로직을 Python 코드로 구현했습니다.
  * **에지 통신 및 제어 자동화:** `Jetson Nano` 에지 디바이스 환경에서 비전 객체 인식 분류 결과(숙성/미숙성)에 따라 구동 명령 분기 처리를 정립하고, 로봇 하드웨어 컨트롤러 간의 소켓 및 시리얼 통신 안정성을 반복 검증했습니다.

<br>

### 5. OCR 기반 FRS 이미지 자동 판독 및 프로파일 산출 (`2025.07 ~ 2025.09`)
* **Description:** (주)두우엔지니어링 일경험 프로젝트로 원자력 발전소 내진검증 문서의 핵심인 비정형 FRS 이미지 데이터를 정형 데이터로 자동 변환하여 현업의 판독 비효율을 획기적으로 개선한 프로젝트입니다.
* **Tech Stack:** `Python`, `Pandas`, `OCR`
* **Core Tasks:**
  * **비정형 가공 파이프라인 자동화:** FRS 수작업 판독 시 발생하는 인적 오류를 최소화하기 위해 OCR 기술로 추출된 파일 단위 비정형 데이터를 파싱하여 대량의 Pandas `DataFrame` 구조로 통합 및 자동 병합하는 스크립트를 개발했습니다.
  * **데이터 품질 제고:** 파편화된 주파수 측정 단위를 통일하고 정렬 기준을 정립하여, 입력값의 품질 변화에 구애받지 않고 일관성 있게 원본 프로파일과 보수 프로파일을 산출·대조할 수 있는 데이터 정제 파이프라인을 설계했습니다.

---

## 👩‍💻 Career

| 기간 | 기관 / 부서 | 역할 | 수행 실무 |
| :--- | :--- | :--- | :--- |
| **2025.07 ~ 2025.09** | **(주)두우엔지니어링** | 인턴 / 데이터 전처리 개발 | OCR 기반 FRS 이미지 파싱 및 프로파일 산출 프로그램 구축 |
| **2023.10 ~ 2024.12** | **Eco AI Lab (빅데이터 연구실)** | 랩장 (Lab Leader) | ETRI 공정 데이터 모델링 분석 총괄 및 멀티 센서 전처리 기준 수립 |
| **2025.01 ~ 2025.10** | **DfX Lab (임베디드 연구실)** | 연구 학부생 | 로봇팔 자동화 수확 시스템 하드웨어 제어 및 좌표계 통신 실습 |

---

## 📝 Publications

* **“딥러닝 전처리 모델 및 클러스터링 분석을 활용한 주거용 건물 실시간 공기질 모니터링 플랫폼”** | 한국통신학회 (KICS), 2024
* **“최적 스팀량 예측 인공지능 모델을 통한 공정의 에너지 효율 개선 모니터링 시스템”** | 대한전자공학회 (IEEK), 2024
* **“멀티 센서 기반의 스마트홈 공기질 향상을 위한 모니터링 시스템”** | 한국통신학회 (KICS), 2024

---

## 🏆 Awards

| 일자 | 상장 명칭 / 훈격 | 시상 기관 |
| :--- | :--- | :--- |
| **2025.12** | 우수성과상 | 국립한밭대학교 교수학습센터 |
| **2025.12** | 장려상 | 국립한밭대학교 정보기술대학 |
| **2025.10** | 장려상 | 국립한밭대학교 HRD 센터장 |
| **2025.10** | 장려상 | 국립한밭대학교 공학교육혁신센터 |
| **2025.09.05** | 장려상 | 대전과학산업진흥원 |
| **2025.08.23** | 동상 (SP!ED 2025 Bronze Award) | iRE-Asia(아시아 혁신 연구·교육 컨소시엄) |
| **2024.11** | 우수상 | 국립한밭대학교 LINK 3.0 사업단 |
| **2024.11.22** | 우수상 | KT / 대전·세종·충남(DSC) 지역혁신플랫폼 |
| **2024.08** | 최우수상 (제 1회 2024 대한민국 학생 창업 주간) | 한국연구재단 |

---

## 🎓 Education & Certifications

### Education
* **국립한밭대학교** | 컴퓨터공학과 학사 졸업 (`2020.03 ~ 2026.02`)
  * *도시공학과에서 컴퓨터공학과로 전과 완료, 소프트웨어 학문 간 융합 역량 구축*

### Certifications
* **2026.06** | SQL 개발자 (SQLD) — *한국데이터산업진흥원 최종합격*
* **2026.03** | 데이터분석준전문가 (ADsP) — *한국데이터산업진흥원 최종합격*
* **2026.03** | 빅데이터분석기사 (필기) — *한국데이터산업진흥원 필기합격*
* **2026.02** | 정보처리기사 (필기) — *한국산업인력공단 필기합격*
* **2022.12** | 한국사능력검정시험 (2급) — *국사편찬위원회 최종합격*
* **2021.02** | 드론사진영상운용(기능)사 자격증 — *대한드론진흥협회 최종합격*
* **2020.08** | 2종보통운전면허 — *경찰청 최종합격*

---

## 🕹️ Activities

* **Microsoft Data School 4기** | 클라우드 아키텍처 및 데이터 엔지니어링 과정 이수 (`2026.03 ~ 2026.09`)
* **국립한밭대학교 자작자동차동아리** | EV 차량 주행 센서 기반 배터리 전력 데이터 최적화 분석 (`2023.03 ~ 2024.10`)
* **글로벌 캡스톤 디자인** | 국립한밭대학교 & 태국 마히돌대학교 공동 교육과정 (`2024.09 ~ 2024.11`)
* **기타 활동:** 나눔지기 멘토링 프로그램 봉사 (`2024.09 ~ 2024.12`), 영어학원 강사 (`2022.08 ~ 2025.08`), 캐나다 단기 연수 (`2022.07 ~ 2022.08`)

---

## 📊 GitHub Stats
<p align="left">
  <img src="https://github-readme-stats.vercel.app/api?username=daeun-ahn&show_icons=true&theme=radial" alt="Daeun's GitHub Stats" />
</p>
