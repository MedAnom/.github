# 🩸 MedAnom – 혈액건강데이터 기반 AI 분석 & 예방 대시보드

![Award](https://img.shields.io/badge/Award-BLEP_장려상_수상-FFD700?style=for-the-badge&logo=trophy)
![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![FastAPI](https://img.shields.io/badge/FastAPI-0.95+-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Google_Login](https://img.shields.io/badge/Auth-Google_OAuth-4285F4?style=for-the-badge&logo=google&logoColor=white)

## 🏆 Awards
> **BLEP – SCH AI 플랫폼 활용 경진대회 [장려상] 수상** 🎖️
>
> *본 프로젝트는 혈액 건강 데이터 분석 모델의 우수성과 헬스케어 대시보드의 실용성을 인정받아 수상하였습니다.*

---

## 📌 프로젝트 개요 (Project Overview)
**MedAnom**은 70만 건 이상의 대규모 혈액검사 데이터를 AI로 분석하여, 개인의 **빈혈(ANE)·허혈성심장질환(IHD)·뇌졸중(STK)** 위험도를 예측하고 맞춤형 예방 행동을 추천하는 헬스케어 플랫폼입니다.

## 🎯 목표 (Goals)
- 🧠 **질환 예측**: 혈액 건강 지표를 기반으로 한 3대 질환 발병 확률 예측 모델 개발
- 🚨 **이상치 탐지**: IsolationForest 기반의 Anomaly Detection으로 건강 리스크 조기 알림
- 🏃 **맞춤형 가이드**: 사용자 상태에 최적화된 운동/식단/생활습관 솔루션 제공
- 🏥 **의료 접근성**: 지도 API를 활용한 내 주변 전문 병원 안내

---

## ⚙️ 시스템 아키텍처 & 기술 스택 (Tech Stack)

### **Frontend**
- **Framework**: React, Vite
- **Styling**: Tailwind CSS
- **Visualization**: Recharts (Radar Chart, Area Chart 등)
- **Map Service**: Kakao Maps API

### **Backend & Security**
- **Server**: FastAPI (High-performance async framework)
- **Database**: SQLite (managed via SQLModel ORM)
- **Authentication (Auth)**:
  - **Social Login**: Google OAuth 2.0 API 연동
  - **Local Auth**: JWT (JSON Web Token) 기반 회원가입/로그인 보안 시스템 구현

### **AI & Data Science**
- **Framework**: scikit-learn
- **Pipeline**:
  - Preprocessing (Imputation, Log Transform, Scaling)
  - Modeling (Logistic Regression, IsolationForest)
  - Visualization (UMAP)

---

## 🧬 활용 데이터 (Data)
- **Dataset**: 70만 건의 혈액 검진 데이터
- **Key Features**:
  - `SEX` (성별), `AGE_G` (연령대)
  - `HGB` (혈색소), `TCHOL` (총콜레스테롤)
  - `TG` (중성지방 - log1p 변환 적용), `HDL` (콜레스테롤)
- **Target Diseases**: 빈혈(ANE), 허혈성심장질환(IHD), 뇌졸중(STK)

---

## 🚀 주요 기능 (Key Features)

### 1. 보안 인증 시스템 (Authentication)
- **간편 로그인**: Google 계정을 연동한 One-Click OAuth 2.0 로그인 지원
- **자체 회원 관리**: JWT Access Token 방식을 통한 안전한 회원가입 및 로그인 세션 유지

### 2. AI 건강 분석 대시보드
- **건강위험 Radar Chart**: 3대 질환의 위험도를 시각적으로 한눈에 파악
- **건강 추이 Area Chart**: 최근 검사 결과의 변동 흐름 추적
- **위험도 신호등 (Chip Color)**: `정상(Green)` / `주의(Yellow)` / `위험(Red)` 직관적 표시

### 3. 지능형 알림 및 가이드
- **이상치 감지 (Anomaly Alert)**: 일반적인 임상 범위를 벗어난 수치 탐지 시 즉시 알림
- **맞춤형 솔루션**: 분석된 위험도에 따라 구체적인 식단 및 운동 가이드 제공

### 4. 위치 기반 서비스
- **병원 찾기**: Kakao Maps API를 활용하여 현재 위치 기반 진료 가능한 병원 실시간 검색

---

## ⚙️ AI/ML Pipeline 상세
1.  **전처리 (Preprocessing)**:
    - 성별/연령대 그룹 평균으로 결측치(Missing Value) 대치
    - 편향된 TG(중성지방) 데이터 로그 변환 및 상위 1% 이상치 Clipping
    - StandardScaler를 이용한 데이터 정규화
2.  **모델링 (Modeling)**:
    - Logistic Regression Pipeline 구축
    - ROC-AUC Metric 기반 성능 최적화 검증
3.  **이상치 탐지 (Anomaly Detection)**:
    - IsolationForest 알고리즘 적용
    - UMAP 차원 축소를 통한 데이터 군집 시각화

---

## 📍 개발자 (Developer)
- **Name**: 정재민 (Jaemin Jeong)
- **Role**: Full-stack Developer & AI Researcher
- **Contact**: wjdwoals000619@naver.com
- **GitHub**: [made by jaemin0619](https://github.com/jaemin0619)

---
Copyright © 2025 MedAnom. All rights reserved.
