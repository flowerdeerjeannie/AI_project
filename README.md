# 선박용품 카테고리 분류 및 리드타임 예측 서비스

## 💡 프로젝트 소개
선용품의 카테고리 분류와 리드타임 예측을 통해 최적의 발주 시기를 추천하는 웹 서비스입니다. 이 서비스는 선용품의 리드타임을 정확히 예측하여 선박 운영의 안정성을 향상시키고, 불필요한 보관비용을 줄이는 것을 목표로 합니다.

## 📈 개발 기간
2024.08.26 - 2024.0

## 🔧 개발 환경
- Java: 17.0.10
- JDK: 17.0.10
- React: 18.2.0
- IDE: STS4
- Framework: Spring Boot 2.x
- Database: MySQL 8.0.37
- Deep Learning: Python (Pytorch), BERT, MLP, XGBoost

## 📌 주요 기능
#### 1. 카테고리 분류
모델: BERT Classification / XGBoost
기능: 사용자가 입력한 선용품 정보를 바탕으로 정확한 카테고리 분류.
기술: BERT 임베딩을 활용하여 선용품의 텍스트 데이터를 분석하고, XGBoost로 최종 분류.
성과 목표: F1 스코어 90% 이상 달성.
#### 2. 리드타임 예측
모델: MLP, LightGBM/XGBoost, BERT+파인튜닝
기능: 선용품의 리드타임을 예측하여 최적의 발주 시기를 제안.
기술: BERT 임베딩, 발주처 원핫 인코딩, 발주수량과 발주금액 정규화를 통해 다양한 회귀 모델을 사용.
성과 목표: RMSE 및 MAE 7 이하.
#### 3. 발주 시기 및 대체 품목 추천
기능: 예상 리드타임을 바탕으로 발주 시기와 대체 가능한 유사 품목을 추천.
기술: 예측된 리드타임 정보를 기반으로 사용자가 최적의 발주 계획을 세울 수 있도록 지원.
#### 4. 웹 서비스
화면 설계: 발주 현황 조회, 선용품 선택 및 리드타임 예측, 장바구니 및 재고 관리 기능 제공.
기술: React.js로 프론트엔드 구현, Spring Boot로 백엔드 API 개발.

## 📊 데이터 분석 및 AI 모델
### 모델 선택 및 학습
#### 카테고리 분류
- BERT 임베딩: 'Machinery, Assembly, 청구품목, Part No.1, Part No.2' 결합하여 임베딩 생성.
- XGBoost: 텍스트 데이터와 수치형 데이터를 결합하여 최적의 카테고리 분류 모델 생성.
#### 리드타임 예측
- 모델: MLP, LightGBM/XGBoost, BERT+파인튜닝 중 최적의 모델 선택.
- 결측치 처리: BERT 임베딩과 코사인 유사도를 활용하여 창고입고일 결측치를 대체.
#### 성능 평가 및 튜닝
- 성능 평가: K-폴드 교차 검증으로 모델의 일반화 능력 평가 및 RMSE, MAE 회귀 지표로 평가.
- 튜닝: 학습률, 뉴런 수, 레이어 수, 배치 크기 등 하이퍼파라미터 조정, Dropout, L2 정규화로 과적합 방지.
  
## 📋 웹 서비스 기능
1. 발주 현황 조회 및 입력
발주 현황 조회와 발주 입력을 통해 선용품의 현재 상태를 확인하고, 추가 발주를 관리.
2. 선용품 선택 및 리드타임 예측
사용자가 카테고리를 선택하여 선용품 리스트를 조회하고, 예상 리드타임을 확인.
3. 장바구니 및 재고 관리
예상 리드타임을 기준으로 통합 리드타임을 제공하며, 과거 리드타임 추이와 대체 품목을 추천.

## 📈 AI 데이터 분석 계획
1. 데이터 수집 및 전처리
데이터 수집: 마린소프트가 제공한 데이터베이스에서 발주 및 창고 데이터를 수집.
텍스트 데이터 처리: BERT 임베딩으로 변환.
날짜 처리: 발주일자와 창고입고일자를 기반으로 리드타임(일수) 계산.
2. 모델 학습 및 평가
모델 학습: BERT 임베딩, 수치형 피처 정규화, 범주형 피처 인코딩 후 모델 학습.
성능 평가: RMSE, MAE 등 회귀 지표로 평가.
튜닝: 하이퍼파라미터 조정 및 정규화로 모델 성능 최적화.
3. 웹 서비스 활용
발주 시기 추천: 예측된 리드타임을 바탕으로 발주 시기 추천.
대체 품목 추천: 유사 품목 추천 기능 제공
