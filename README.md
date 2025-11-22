# Human_Action_Recognition
딥러닝 기반 사람 행동 인식 시스템.
동영상 파일 또는 실시간 웹캠 입력을 분석해 사람이 어떤 행동을 하고 있는지 자동으로 예측한다.
ResNet18 + LSTM 구조로 시간 흐름 정보까지 반영해 행동을 분류한다. 실시간 모드에서는 YOLO로 사람 박스를 감지하고 추적한다.

----------------------------------------------------------------------------------------------------------------------------------------------------------------

1) Video File Action Recognition
동영상 입력을 프레임 단위로 잘라 분석

ResNet18으로 프레임 특징 추출

LSTM으로 시간 흐름 기반 행동 판단

Top-K 확률 출력

예: CricketShot / PlayingCello / Punch / ShavingBeard / TennisSwing
(5-class subset, UCF101 기반 데이터)

Real-Time Action Recognition
웹캠 실시간 입력 처리

YOLO로 사람 위치 탐지

스무딩 알고리즘으로 감지 박스 흔들림 최소화

ResNet18+LSTM으로 행동 분류 후 화면에 확률 표시

System Architecture

[Input Video/Webcam]
        │
    (YOLO)  ← 실시간만
        │ person crop
[Frame Extractor]  → 20 frames
        │
[ResNet18]  → 512-d Feature
        │
[LSTM]  → Action Classification
        │
[Top-K Probabilities Output]
