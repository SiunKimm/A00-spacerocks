# space-rock-dl-classifier

달에서 수집한 월석 이미지(Basalt vs Highland)를 분류하기 위한 딥러닝 이미지 분류 모델입니다.  
PyTorch 기반의 사전학습된 ResNet50 모델을 활용하여 전이학습(transfer learning)으로 구현되었으며, 데이터 전처리부터 학습, 평가, 예측까지의 전체 파이프라인을 포함합니다.

---

## 🧠 주요 기능 (Features)
- 224x224 크기로 이미지 전처리 (리사이징)
- 학습/검증 데이터셋 분할 및 `SubsetRandomSampler` 기반의 데이터 로더 구성
- ResNet50 기반 전이학습: Fully Connected Layer 수정 및 기존 가중치 Freeze
- 학습 손실, 검증 손실, 정확도 추적 및 시각화
- 학습된 모델 저장 및 불러오기
- 단일 이미지 예측 기능 구현
- 시드 고정을 통한 실험 재현성 확보

> ⚠️ 참고: 현재 이미지 정규화(`transforms.Normalize`)는 적용되지 않았으며, 추후 정확도 향상을 위해 도입 가능함

## 🔁 재현성 (Reproducibility)
이 프로젝트는 결과의 일관성과 비교 가능성을 보장하기 위해 **시드 고정(seed fixing)**을 통해 실험의 재현성을 확보합니다.  
Python의 `random`, `NumPy`, 그리고 PyTorch의 CPU/GPU 연산에서 모두 동일한 난수 시드를 설정하여, 학습 결과가 실행 환경이나 시점에 따라 달라지지 않도록 설계되었습니다.

## 🏗️ 모델 구조
- **백본(Backbone)**: ResNet50 (ImageNet 사전학습 가중치 활용)
- **출력 계층 수정**: 기존 Fully Connected Layer를 Basalt/Highland 이진 분류에 적합하게 재설계
- **과적합 방지**: Dropout(0.2) 사용, 파라미터 수 감소

## 🧪 학습 개요
- Optimizer: Adam (lr=0.003)
- 손실 함수: Negative Log Likelihood Loss (NLLLoss)
- 총 Epochs: 10
- 테스트 정확도: 최대 100% (소규모 샘플 데이터 기준)

## 🔧 필요 패키지
- torch
- torchvision
- numpy
- matplotlib
- Pillow (PIL)

## 📌 참고 사항
- 데이터는 `./data/Basalt`, `./data/Highland` 식으로 클래스별 하위 폴더에 구성되어야 합니다.
- 현재 데이터 증강(Data Augmentation)은 적용되어 있지 않습니다. 추후 개선 사항으로 고려 가능합니다.
- 실험에 사용된 월석 이미지는 공개 데이터셋 기반이며, Basalt와 Highland 지형에 대한 분류에 중점을 두고 설계되었습니다.
