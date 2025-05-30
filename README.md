# 🚀 space-rock-dl-classifier

화성 암석 이미지(Basalt vs Highland)를 분류하는 딥러닝 기반 이미지 분류기입니다.  
사전학습된 ResNet50 모델을 기반으로 전이학습을 적용하였으며, 데이터 로딩, 시드 설정, 학습/검증 분할, 시각화 및 예측 파이프라인이 통합되어 있습니다.

## 🧠 Features

✅ 이미지 전처리 및 224x224 크기로 리사이징  
✅ 학습/검증 데이터 분할 및 로더 구성 (`SubsetRandomSampler`)  
✅ ResNet50 기반 전이학습, Fully Connected Layer 수정 및 가중치 고정  
✅ 학습 손실, 검증 손실, 정확도 추적 및 그래프 시각화  
✅ 학습 완료 모델 저장 (`torch.save`) 및 로딩 (`torch.load`)  
✅ 단일 이미지 예측 함수 및 이미지 예측 시각화  
