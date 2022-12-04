# 한밭대학교 컴퓨터공학과 ICIS-COM 팀
## 주제: 제한된 컴퓨팅 환경에서 분산학습 응용 시스템 개발

**팀 구성**
- 20161640 백승진 
- 20171603 황순규
- 20171613 박재현

## <u>ICIS-COM</u> Project Background
- ### 필요성
  - 연합학습은 일반적으로 모든 데이터를 서버로 모아, AI를 학습하는 방식과 달리, 사용자가 직접 사용하는 스마트폰에서 데이터를 처리하고 모델을 강화하고 이 모델을 한 곳에 모아 더 정교한 모델을 만들어 다시 배포하는 방식이다.

  - 이는 상대적으로 적은 데이터로 최적화한 AI 모델을 개발할 수 있다. 방대한 데이터를 저장하는 스토리지나 이런 데이터를 처리하기 위한 고성능 프로세서를 사용자 개인 디바이스로 분산했으며, 필요 사항만을 공유해 최적화한 모델을 다시 배포하는 만큼 트래픽에 대한 부담도 적다. 또 개인정보 침해 가능성 역시 상대적으로 적어 제도적 장벽 역시 쉽게 넘을 수 있다.

- ### 기존 해결책의 문제점
  ![image](https://user-images.githubusercontent.com/81350489/205481365-e72b7b58-2e32-4a16-b5ef-5a1b92d3e024.png)

## System Design
<img src="https://img.shields.io/badge/Python-1572B6?style=for-the-badge&logo=Python&logoColor=white"> <img src="https://img.shields.io/badge/Pytorch-FF8000?style=for-the-badge&logo=Pytorch&logoColor=white"> <img src="https://img.shields.io/badge/Docker-2ECCFA?style=for-the-badge&logo=Docker&logoColor=white"> <img src="https://img.shields.io/badge/Opencv-D7DF01?style=for-the-badge&logo=Opencv&logoColor=white">
<img src="https://img.shields.io/badge/Grafana-FF0000?style=for-the-badge&logo=Grafana&logoColor=white"> <img src="https://img.shields.io/badge/Influxdb-339933?style=for-the-badge&logo=Influxdb&logoColor=white"> <img src="https://img.shields.io/badge/Ubuntu-000000?style=for-the-badge&logo=Ubuntu&logoColor=white">
  - ### System Requirements
    - Docker Container를 활용하여 논리적인 FL 환경 구축
    - Rasberripy와 Jetson nano를 활용하여 물리적인 FL 환경 구축
    - 서버와 클라이언트들의 CPU, 메모리, 디스크 용량, GPU 사용량 등의 데이터를 수집 도구인 telegraf를 이용해 시계열DB인 influxDB에 저장 후 Grafana를 이용해 모니터링 시스템 구축
  - ### System Architecture
  <img src="https://user-images.githubusercontent.com/81350489/205480991-4bfc31bd-1eeb-43cf-98e0-907d45c132f3.png" width=900>
  <img src="https://user-images.githubusercontent.com/81350489/205481849-260dfe7f-ebfe-4b4e-8059-0332e095fa43.png" width=600>

  
## Conclusion
  <img src="https://user-images.githubusercontent.com/81350489/205482839-954171a7-7411-4761-a26a-51acaf8ad5b4.png" width=900>
  
  - 정형화된 MNIST 데이터를 활용하여 기존 인공지능 방식과 물리적으로 나눈 엣지 단말들에서 연합학습을 이용한 방식은 아래 그래프처럼 거의 근접한 성능을 보이는 것을 확인할 수 있다.
  <img src="https://user-images.githubusercontent.com/81350489/205482573-5451d137-8641-4d5e-a7c8-88e668263e71.png" width=900>
 
 - 비정형화된 위상 영상 데이터를 활용하여 Segmentation을 진행했을 때, 학습하는 데이터를 n개로 나누어 각 노드에서 연합학습을 진행하면 기존 인공지능 방식보다 성능이 못 미치는 것을 확인할 수 있다. 이를 해결하기 위해서는 데이터를 노드의 수로 나누지 않고 같은 양의 데이터에 시드값을 다르게 주어 연합학습을 진행한다면 앙상블하는 효과를 얻어 기존 인공지능 방식에 거의 근접하거나 좀 더 좋은 성능을 보일 수 있을 것이다.
