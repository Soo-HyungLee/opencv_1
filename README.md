# opencv_1



영상처리와 딥러닝은 서로 밀접한 관계입니다.
딥러닝과 이미지 프로세싱은 다른 문제를 해결하는 효과적인 도구입니다. 이를 뒷받침하듯 좋은 예시를 소개해 드리겠습니다.

먼저 스도쿠 퍼즐의 게임 방법은 가로 세로 9칸씩 모두 81칸으로 이루어진 정사각형의 가로줄과 세로줄에 각각 1에서9까지 숫자를 한 번씩만 써서 채웁니다. 또, 큰 정사각형은 가로세로 각 3칸으로 모두 9칸인 작은 사각형 9개로 이루어져 있는데 그 9칸짜리 작은 사각형 안에서도 1~9까지의 숫자가 겹치지 않아야 합니다.
 
 ![1](https://user-images.githubusercontent.com/42931922/80525854-d6e6b900-89cc-11ea-814b-d05395179b35.png)



 
저희 조의 주제는 스도쿠 퍼즐을 인식하여 해답을 찾아내는 것 입니다. 


스도쿠 문제를 해결하기 위한 각 과정을 설명해드리겠습니다.

 
![11](https://user-images.githubusercontent.com/42931922/80525876-dfd78a80-89cc-11ea-8f8d-b7ef74509ea3.png)

 

첫 번째로, 스도쿠 퍼즐을 찾는 것 입니다. 

이미지에서 스도쿠를 인식해 찾아내는 과정이 첫 과정입니다. 
이미지에서 스도쿠의 위치와 크기는 모두 다를 수 있습니다. 
또한, 조명과 카메라의 촬영 조건에 의해서도 달라질 것입니다. 이러한 문제를 해결하기 위해서 Semantic Segmentation Deep network를 사용하도록 하겠습니다. 네트워크에서는 스도쿠 퍼즐에 해당되는 영역을 픽셀 단위로 분리해 낼 것입니다. 이를 위해서 학습 데이터에도 픽셀 단위로 라벨을 지정해야 합니다. 그러면 스도쿠 퍼즐에 해당되는 영역을 지정하게 됩니다. 


두 번째 과정은 상자를 찾는 과정입니다.
전 단계에서 스도쿠 퍼즐의 대략적인 위치를 찾아냈다면 노이즈를 지워주기 위한 작업을 진행하는 것이 목표입니다. 색을 바꿔야 하는 조건이 있을 시 grayscale을 이용해 바꿔 줄 예정입니다. 
그 후에 가로,세로 9칸씩 9x9 사각형의 각 상자를 따로 식별해 내는 과정이 필요합니다.

세 번째 단계는 숫자를 읽는 과정입니다.
숫자를 인식하는 방법은 여러가지가 있습니다.
가장 일반적인 방법인 OCR과 HOG특징을 이용한 머신러닝 기법도 있습니다. 그렇지만 저희 조는 딥러닝을 이용하여 숫자를 인식하는 모델을 만들겠습니다.

MATLAB에서는 필기체 숫자의 다양한 변형을 확보하기 위해서 합성 데이터를 생성하고 이를 학습에 사용하겠습니다. 학습에 사용할 데이터가 준비됐으면 네트워크를 구성하고 학습을 진행하겠습니다. 이렇게 학습이 완료된 네트워크를 토대로 스도쿠 솔루션을 구할 수 있을 것이라 생각됩니다. 

네 번째 단계는 스도쿠의 빈 공간을 규칙에 맞게 채우는 과정입니다.# opencv_1



영상처리와 딥러닝은 서로 밀접한 관계입니다.
딥러닝과 이미지 프로세싱은 다른 문제를 해결하는 효과적인 도구입니다. 이를 뒷받침하듯 좋은 예시를 소개해 드리겠습니다.

먼저 스도쿠 퍼즐의 게임 방법은 가로 세로 9칸씩 모두 81칸으로 이루어진 정사각형의 가로줄과 세로줄에 각각 1에서9까지 숫자를 한 번씩만 써서 채웁니다. 또, 큰 정사각형은 가로세로 각 3칸으로 모두 9칸인 작은 사각형 9개로 이루어져 있는데 그 9칸짜리 작은 사각형 안에서도 1~9까지의 숫자가 겹치지 않아야 합니다.
 
 ![1](https://user-images.githubusercontent.com/42931922/80525854-d6e6b900-89cc-11ea-814b-d05395179b35.png)



 
저희 조의 주제는 스도쿠 퍼즐을 인식하여 해답을 찾아내는 것 입니다. 


스도쿠 문제를 해결하기 위한 각 과정을 설명해드리겠습니다.

 
![11](https://user-images.githubusercontent.com/42931922/80525876-dfd78a80-89cc-11ea-8f8d-b7ef74509ea3.png)

 

첫 번째로, 스도쿠 퍼즐을 찾는 것 입니다. 

이미지에서 스도쿠를 인식해 찾아내는 과정이 첫 과정입니다. 
이미지에서 스도쿠의 위치와 크기는 모두 다를 수 있습니다. 
또한, 조명과 카메라의 촬영 조건에 의해서도 달라질 것입니다. 이러한 문제를 해결하기 위해서 Semantic Segmentation Deep network를 사용하도록 하겠습니다. 네트워크에서는 스도쿠 퍼즐에 해당되는 영역을 픽셀 단위로 분리해 낼 것입니다. 이를 위해서 학습 데이터에도 픽셀 단위로 라벨을 지정해야 합니다. 그러면 스도쿠 퍼즐에 해당되는 영역을 지정하게 됩니다. 


두 번째 과정은 상자를 찾는 과정입니다.
전 단계에서 스도쿠 퍼즐의 대략적인 위치를 찾아냈다면 노이즈를 지워주기 위한 작업을 진행하는 것이 목표입니다. 색을 바꿔야 하는 조건이 있을 시 grayscale을 이용해 바꿔 줄 예정입니다. 
그 후에 가로,세로 9칸씩 9x9 사각형의 각 상자를 따로 식별해 내는 과정이 필요합니다.

세 번째 단계는 숫자를 읽는 과정입니다.
숫자를 인식하는 방법은 여러가지가 있습니다.
가장 일반적인 방법인 OCR과 HOG특징을 이용한 머신러닝 기법도 있습니다. 그렇지만 저희 조는 딥러닝을 이용하여 숫자를 인식하는 모델을 만들겠습니다.

MATLAB에서는 필기체 숫자의 다양한 변형을 확보하기 위해서 합성 데이터를 생성하고 이를 학습에 사용하겠습니다. 학습에 사용할 데이터가 준비됐으면 네트워크를 구성하고 학습을 진행하겠습니다. 이렇게 학습이 완료된 네트워크를 토대로 스도쿠 솔루션을 구할 수 있을 것이라 생각됩니다. 

네 번째 단계는 스도쿠의 빈 공간을 규칙에 맞게 채우는 과정입니다.
검색 알고리즘과 최소 잔여 값 접근법으로 9x9 스도쿠 테이블에서 존재하는 수 많은 경우의 수를 점차 좁혀나가며 답을 찾아낼 것 입니다.


