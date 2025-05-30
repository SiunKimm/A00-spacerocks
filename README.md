# 🚀 space-rock-dl-classifier

월석 이미지(Basalt vs Highland)를 분류하는 딥러닝 이미지 분류기.  
사전학습된 ResNet50 모델을 활용한 전이학습 기반으로 구현되며, 데이터 전처리, 시드 설정, 학습/평가/예측 전체 파이프라인을 포함합니다.

## 🧠 Features

- ✅ 데이터 로딩 및 이미지 전처리 (224x224 resize + normalization)
- ✅ 학습/검증 데이터 분할 및 로더 구성 (`SubsetRandomSampler`)
- ✅ ResNet50 전이학습 (FCL 수정 및 Freeze)
- ✅ 학습 손실, 검증 손실, 정확도 추적 및 시각화
- ✅ 모델 저장 및 로딩
- ✅ 단일 이미지 예측 및 시각화
