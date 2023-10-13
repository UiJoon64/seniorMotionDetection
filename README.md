👵 SENIOR_MOTION_DETECTION 👴
========================
노령층 이상행동 감지 및 보호자 알림 서비스


🌳 프로젝트 개요
=======================
65세 이상의 고령 인구가 증가함에 따라, 홀로 계시는 어르신 또한 많아지고 있다.

이 프로젝트는 혼자 계시는 어르신의 행동 특성과 발생 소리를 모니터링하여 

위험사항을 예측 및 감지하고 보호자에게 즉시 알리기 위해 제작되었다.


👨‍👨‍👧‍👧 멤버 구성
======================
팀장_전의준 : (이모티콘)제작 총괄

팀원_김민영 : (이모티콘)음성 데이터 분석 및 학습

팀원_김지아 : (이모티콘)이미지 및 영상 데이터 분석 및 학습

팀원_손수지 : (이모티콘)웹 페이지 제작

팀원_윤지수 : (이모티콘)이미지 및 영상 데이터 분석 및 학습


⚙ 개발 환경
======================
PYTHON 3.9.16

CUDA 11.3

이미지데이터 : YOLOv7-tiny

영상데이터 : YOLOv7, media pipe

음성데이터 : webkitSpeechRecognition, BERT

웹 : 


⭐ 이미지데이터
=====================
AI-Hub에서 총 80가지의 일상생활 라벨링 데이터를 담은

**< 일상생활 이미지 데이터 >** 를 가져와, 가정에서 흔히 발생할 수 있는 **17가지의 상황만을 선별**하였다.

![image](https://github.com/UiJoon64/seniorMotionDetection/assets/144432006/b4db6294-5ef4-4de8-ab6a-a93d9ebf09a1)


이미지들은 YOLOv7-tiny의 학습을 위해 이미지 크기를 1920x1080 사이즈에서 640x360의 사이즈로 조절하였다.

이미지마다 각 행동의 바운딩박스 좌표가 들어있었고, 바운딩박스의 좌표 또한 이미지 크기 비율에 맞춰 정규화시켜주었다.


* YOLOv7-tiny를 선정한 이유는 YOLOv7-tiny가 객체 탐지의 가장 기본적이고 속도가 매우 빠른 알고리즘으로,

  프로젝트에 필요한 실시간 영상 처리에 적합하다고 생각했기에 선정하였다.


이미지 사이즈와 바운딩박스 좌표 정규화가 끝난 5325개의 데이터들은 Batch Size=4, Epoch=100으로 YOLOv7-tiny를 통해 학습시켜

17가지의 행동 분류 결과를 텍스트로 추출한다.

![image](https://github.com/UiJoon64/seniorMotionDetection/assets/144432006/029870ad-8f2c-4897-99e3-c0d5e8e26a85)


예를 들어, 말할까 ???????????????????



🌟 영상데이터
====================
AI-Hub에서 고령자 개인의 외형과 행위 특성(습관), 건강 상태, 생활 패턴 등을 담고 있는

< 이상행동 영상 데이터 > 를 가져와, 일상 생활에서 일어날 수 있다고 판단한 낙상/일상/배회 총 3가지 section의 데이터를 선별하였다.

이 프로젝트에서는 보통 재택 공간(실내)에서 일어나는 이상 상황을 감지하지만, 모델의 학습을 위해 실내와 실외 데이터 모두 사용하였다.


영상 데이터 중 낙상/일상/배회가 일어나는 순간인 2초 정도를 하이라이트로 가져왔고, 영상의 전처리


✨ 음성데이터
=====================


💫 웹 서비스 구현
====================


🤩 프로젝트 결과 및 실행
========================
