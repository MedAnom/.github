
# BLEP – SCH AI 플랫폼 활용 경진대회  
## 혈액건강데이터 기반 AI 분석 & 예방 대시보드 – MedAnom

## 📌 프로젝트 개요
MedAnom은 혈액검사 데이터를 기반으로 개인의 빈혈(ANE)·허혈성심장질환(IHD)·뇌졸중(STK) 위험도를 AI로 예측하고 예방 행동을 추천하는 대시보드입니다.

## 🎯 목표
- 혈액 건강 기반 질환 예측 모델 개발  
- 이상치 감지 및 건강 리스크 알림  
- 사용자 맞춤형 운동/식단/생활습관 가이드 제공  
- 지도 기반 병원 안내  

## 🧬 데이터
- 70만 건 혈액 데이터  
- SEX, AGE_G, HGB, TCHOL, TG(log1p), HDL  
- 타깃: ANE, IHD, STK  

## ⚙️ AI/ML Pipeline
### 전처리
- 성별·연령대 그룹 평균으로 결측치 대체  
- TG 로그 변환, 이상치 1% 클리핑  
- StandardScaler 적용  

### 모델
- Logistic Regression Pipeline  
- ROC-AUC 기반 성능 측정  
- IsolationForest + UMAP으로 이상치 감지  

## 🖥️ 시스템 아키텍처
- **Frontend**: React + Vite + Tailwind + Recharts  
- **Backend**: FastAPI + SQLModel + JWT 인증  
- **DB**: SQLite  
- **AI Engine**: scikit-learn 기반  
- **지도 API**: Kakao Maps  

## 🚀 주요 기능
- 건강위험 Radar Chart  
- 최근 검사 변동 Area Chart  
- 위험도 Chip Color 표시  
- 이상치 감지 알림  
- 맞춤형 건강 조언 섹션  
- 병원 지도 검색  


## 📍 개발자
- 정재민

## 문의
- wjdwoals000619@naver.com 
- made by jaemin0619 
