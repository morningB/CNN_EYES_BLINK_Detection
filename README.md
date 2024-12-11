# CNN_EYES_BLINK_Detection
눈 깜박임을 구별할 수 있는 인공지능 모델


## Abstract
- 요즘 시대 사람들은 디지털 화면에 많은 노출이 있다. 이에 따라 눈의 피로도 또한 증가할 수 밖에 없는 상황이다. 그렇기에 눈을 뜨고 감고 있는 모습을 구별하는 인공지능 모델을 만들어보고자 한다. 데이터 셋은 본인 자신을 모델로 사용하며 알고리즘은 CNN 모델을 사용하여 구현한다. 하이퍼파라미터를 바꾸며 정확도 변화를 봤고 epcoh을 늘렸을 때 가장 높은 Acurracy가 나왔는데 이때 최대 Accuracy는 0.694까지 높아졌다. 최종적으로 눈 깜박임을 분류하는 모델의 정확도를 높이는 것이 매우 어렵다는 것을 깨달았다.

## 서론

  - 요즘 같이 디지털 시대에서 디지털 기기를 오랫동안 보고 있으면 눈을 깜박이지 않기에 눈에 피로가 많이 쌓이며 시력이 나빠지는 결과가 초래된다. 그래서 인공지능을 이용하여 이미지로 눈을 감고 뜬 모습을 구별하는 모델을 구현해 볼려고 한다.
 
## 본론

1. 데이터 셋
-  먼저 눈을 뜨고 감는 것을 분리하기 위해 사람 사진을 사용하려 했고 처음 인공지능 프로젝트인 만큼 나만의 데이터 셋을 쓰고 싶어서 본인 사진을 사용했으며 본인 얼굴을 직접 여러 방향으로 찍으며 구축했다.
2. 수행 환경
  - 구글 드라이브에서 코랩에서 파이토치로 실험했다.
  - 그리고 사진은 Teachable Machine을 사용하여 찍었다.
3. 알고리즘
- CNN 모델을 이용하여 학습시켰다. Cnn 클래스에서 layer에 대한 하이퍼파라미터는 아래에 표같이 설정하였다

  > layer에 대한 정보
  
  ![image](https://github.com/morningB/CNN_EYES_BLINK_Detection/assets/114423035/79f16a3f-7c95-4d31-bc4f-b35f1b609e7e)

 > layer4까지의 완전 연결층

  ![image](https://github.com/morningB/CNN_EYES_BLINK_Detection/assets/114423035/ec952761-63c7-4b22-be85-f533bed029be)


- 인공지능이 더욱 복잡한 데이터 셋을 이해하게 만들기 위해 epoch을 늘려서 Accuracy를 증가시켰다.
-  device는 기본으로는 GPU이며 없는 경우는 CPU를 이용하고 learning rate를 0.001로 맞추며 Loss는 CrossEntropy를 사용, optimizer는 Adam을 사용했다. 하이퍼파라미터를 바꾸며 정확도의 변화를 측정해봤다.

  ## 결과
 - 그래프는 본론에서 언급했던 layer는 2번까지, epoch은 20 ,learning rate는 0.001을 기준으로 각 epoch, learning rate, layer를 변화시키며 차이를 확인했고, epoch을 바꿀 경우 나머지는 기준과 동일하게 하였고 다른 경우도 같은 설정을 한 결과이다.
   > 기준인 상태로 학습시킨 경우
   
![image](https://github.com/morningB/CNN_EYES_BLINK_Detection/assets/114423035/2847a162-2e66-47d7-ab2e-4ce4db034670)

> learning rate 를 변화시킨 경우

![image](https://github.com/morningB/CNN_EYES_BLINK_Detection/assets/114423035/71cb13f1-7140-4d87-bdd6-dc139f4a7f3e)

> layer를 추가한 경우

![image](https://github.com/morningB/CNN_EYES_BLINK_Detection/assets/114423035/13b75dd2-70cb-4322-90a2-2651b6535558)

> epoch을 증가시킨 경우

![image](https://github.com/morningB/CNN_EYES_BLINK_Detection/assets/114423035/921ede18-710b-4e4e-911e-bbaf24c59d57)


## 고찰 
- 데이터 셋을 더 선명한 이미지나 더 많은 양으로 진행했으면 더 좋은 결과가 나왔을 것이라고 생각한다.
- 그리고 좀 더 얼굴의 다른 부위를 노출시키는거 보다는 눈 부위를 집중적으로 촬영했으면 더 나은 결과가 나왔을까 생각했고 실제로 kaggle에 눈 부위만 찍은 데이터 셋으로 실행해본 결과 정확도가 1.00이 나와 무언가 잘 못 되었다고 판단하여 원래의 데이터 셋으로 진행하였다.
-  본론에서의 방법 말고도 learning rate를 0.00001까지 낮춰보았으나 학습이 조기에 종료되는 형태가 나왔고 layer를 변화시킨 정확도는 미미한 것을 알 수 있지만 epoch을 83까지 늘린 것이 다른 것에 비해 acurracy 상승이 더 높아졌음을 알 수 있었다.
-  더 높은 epoch을 해볼까도 생각했지만 과적합이 발생할 수 있다는 생각에 83회까지만 측정하였다.
-  더 최적의 하이퍼파라미터를 찾았으면 더 높아질 가능성이 있지만 찾지 못한 것이 아쉽다.
- 이번 프로젝트에서는 CNN모델을 사용했을 때에는 다소 아쉬운 정확도가 나왔지만 레즈넷과 같은 전이 학습의 모델로 학습을 진행 했다면 더 높은 정확도가 나왔을 것이라고 생각이 들었다.


## 결론
  - 서론에서 언급했던 이유도 있지만 눈을 감고 뜨는 이미지가 눈을 제외하고는 크게 다르지 않기에 인공지능에 학습시키는 경우 분류를 잘 할지에 대한 궁금증이 컸었고 실험을 시작했다.
  - 데이터 셋을 적절하게 설정하고 수집한다는 것이 매우 힘든 작업이라고 생각했다.
  - 학습률을 변화시키고 EyesCNN 클래스에서 layer 안에 하이퍼파라미터를 계속해서 바꿔보았지만 아쉬운 결과가 나온거 같다.
  - 고찰에서도 언급했던 전이 학습 모델로 학습한다면 더 좋은 결과를 기대해 볼 수 있을거 같다.
  - 결론적으로 사람 사진으로 학습을 시킬 때 정확도를 높이기 매우 힘들구나라고 생각했다
