# 🩸 MedAnom – 혈액건강데이터 기반 AI 분석 & 예방 대시보드

![Award](https://img.shields.io/badge/Award-BLEP_장려상_수상-FFD700?style=for-the-badge&logo=trophy)
![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![FastAPI](https://img.shields.io/badge/FastAPI-0.95+-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Google_Login](https://img.shields.io/badge/Auth-Google_OAuth-4285F4?style=for-the-badge&logo=google&logoColor=white)

## 🏆 Awards
> **BLEP – SCH AI 플랫폼 활용 경진대회 [장려상] 수상** 🎖️  
>
> *본 프로젝트는 혈액 건강 데이터 분석 모델과 헬스케어 대시보드 구현의 실용성을 인정받아 수상하였습니다.*

---

## 📌 프로젝트 개요 (Project Overview)
**MedAnom**은 70만 건 이상의 대규모 혈액검사 데이터를 기반으로, 개인의 **빈혈(ANE)·허혈성심장질환(IHD)·뇌졸중(STK)** 위험도를 예측하고, 결과를 사용자 친화적으로 시각화하여 예방 행동 가이드를 제공하는 헬스케어 플랫폼입니다.

## 🎯 목표 (Goals)
- 🧠 **질환 예측**: 혈액 건강 지표 기반 3대 질환 위험도(확률) 예측 모델 개발
- 🚨 **이상 신호 제공**:
  - 임상 기준 기반 혈액 지표 경고(HGB/TCHOL/TG/HDL)
  - (선택) 패턴 기반 이상 탐지(IsolationForest)로 비정형 패턴 탐지
- 🏃 **맞춤형 가이드**: 사용자 상태에 최적화된 운동/식단/생활습관 솔루션 제공
- 🏥 **의료 접근성**: 지도 API를 활용한 주변 의료기관 탐색(환경에 따라 선택적 제공)

---

## ⚙️ 시스템 아키텍처 & 기술 스택 (Tech Stack)

### Frontend
- **Framework**: React, Vite
- **Styling**: Tailwind CSS
- **Visualization**: Recharts (Radar Chart, Area Chart 등)
- **Map Service**: Kakao Maps API

### Backend & Security
- **Server**: FastAPI
- **Database**: SQLite (SQLModel ORM)
- **Authentication (Auth)**:
  - **Social Login**: Google Identity Services 기반 로그인(환경에 따라 적용)
  - **Local Auth**: JWT 기반 회원가입/로그인

### AI & Data Science
- **Framework**: scikit-learn
- **Modeling**: Logistic Regression (질환별 독립 모델)
- **Anomaly / Visualization (선택)**:
  - IsolationForest (패턴 기반 이상 탐지)
  - UMAP (2D 임베딩 시각화)

---

## 🧬 활용 데이터 (Data)
- **Dataset**: 70만 건 이상의 혈액검사 데이터
- **Key Features**:
  - `SEX` (성별), `AGE_G` (연령대)
  - `HGB` (혈색소), `TCHOL` (총콜레스테롤)
  - `TG` (중성지방), `HDL` (HDL 콜레스테롤)
- **Target Diseases**: 빈혈(ANE), 허혈성심장질환(IHD), 뇌졸중(STK)

> ⚠️ 참고: 현재 백엔드 코드 기준으로 모델 입력 피처는 수치 기반 알고리즘(스케일러/분류기)을 사용하므로  
> **결측치가 없는 정제 데이터**를 전제로 동작합니다.

---

## 🚀 주요 기능 (Key Features)

### 1. 보안 인증 시스템 (Authentication)
- **간편 로그인**: Google 계정 기반 로그인(환경에 따라 적용)
- **자체 회원 관리**: JWT Access Token을 통한 회원가입 및 로그인 세션 유지

### 2. AI 건강 분석 대시보드
- **건강위험 Radar Chart**: 3대 질환 위험도를 한눈에 시각화
- **건강 추이 Area Chart**: 검사 결과 변동 흐름 추적(기록 저장 시)
- **위험도 신호등(Chip Color)**: `정상` / `주의` / `위험`을 직관적으로 표시

### 3. 지능형 알림 및 가이드
- **임상 기준 기반 경고(Rule-based Alert)**:
  - HGB, TCHOL, TG, HDL 등 임상 기준 범위를 벗어날 때 경고 표시
- **맞춤형 솔루션**: 위험도/경고/생활습관 입력을 종합하여 식단·운동·생활습관 가이드 제공

### 4. 위치 기반 서비스 (선택)
- **병원 찾기**: Kakao Maps API 기반 주변 의료기관 검색 (키/권한 설정 필요)

---

## ⚙️ AI/ML Pipeline 상세 (코드 기준)

### 1) 입력 검증 및 기본 전처리
- API 입력값 범위 검증(Pydantic)으로 비현실적 입력 차단
- `AGE → AGE_G`(10년 단위 연령대) 변환으로 일반화 성능 보조

### 2) 질환 위험도 예측 (Logistic Regression)
- 질환별 독립 모델(ANE/IHD/STK)에서 **발병 확률(p)** 출력
- 훈련 데이터에서 F1-score가 최대가 되는 임계값(threshold)을 저장하여,
  확률(p)과 비교해 `label(0/1)` 및 위험 등급을 산출

### 3) 이상 신호 제공
- **임상 기준 기반 경고(rule-based)**: HGB/TCHOL/TG/HDL 기준치를 바탕으로 warn 플래그 생성
- **패턴 기반 이상 탐지**:
  - RobustScaler로 극단값 영향 완화
  - IsolationForest로 다변량 패턴 이상 샘플 탐지
  - UMAP으로 2D 임베딩 시각화(정상/이상 분포 확인)
  - permutation 기반 영향도 추정(top features) 제공

---

## 📍 개발자 (Developer)
- **Name**: 정재민 (Jaemin Jeong)
- **Role**: Full-stack Developer & AI Researcher
- **Contact**: wjdwoals000619@naver.com
- **GitHub**: [made by jaemin0619](https://github.com/jaemin0619)

---
Copyright © 2025 MedAnom. All rights reserved.
