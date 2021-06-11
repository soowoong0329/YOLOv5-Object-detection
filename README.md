# 잡초 및 병충해 분류 인식 융복합 프로젝트

## System Architecture

* IoT + **AI** + Big Data +  Cloud

![arch1](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/arch1.PNG?raw=true)

> Object Detection for Tomato Disease

* Google Colab

* Python3
* Pytorch
* YOLOv5
* Labelme
* Roboflow

---

### DATA

![캡처](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/캡처.PNG?raw=true)

---

### Preprocessing

|       이름       | Label Number | 병충해/잡초 |
| :--------------: | :----------: | :---------: |
|       건강       |      0       | 건강한 작물 |
|      궤양병      |      1       |   병충해    |
|      녹응애      |      2       |   병충해    |
| 아메리카잎굴파리 |      3       |   병충해    |
|    잎곰팡이병    |      4       |   병충해    |
|     점무늬병     |      5       |   병충해    |
|      청벌레      |      6       |   병충해    |
|    차먼지응애    |      7       |   병충해    |
|     흰가루병     |      8       |   병충해    |
|       잡초       |      9       |    잡초     |

* 이미지 증강
  * 많은 이미지 데이터가 확보되지 않은 병충해는 이미지 증강을 사용
  * Imgaug Library , Roboflow 사용
    * Cloud, Snowflake, Rotate, Blur, Brightness, Distortion 6가지로 이미지 증강
* Labeling
  * Labelme을 활용
  * image 파일마다 labeling에 대한 좌표, Labeling number에 대한 json 파일 생성

---

### Modeling

![modeling1](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/modeling1.PNG?raw=true)

![modeling2](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/modeling2.PNG?raw=true)

* 속도 대신 정확하게 병충해를 분류하는 것이 가장 중요
* YOLOv5 Pre-Trained Model 중 정확도가 가장 높은 YOLOv5x 모델 사용

---

### Classification Result

![modeling3](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/modeling3.png?raw=true)

![modeling4](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/modeling4.PNG?raw=true)

* 모델 Train에 사용하지 않은 잡초 및 병충해 이미지 데이터, 유튜브 동영상 캡쳐 이미지 등 Test로 활용
  * 모두 높은 정확도와 mAP 수치를 보임

#### 발생한 문제점

* 실제 모종에 병충해를 표현하기 위해 인위적으로 마킹하여 테스트하였지만, 오분류 및 분류 하지 못함
* 잎에 병충해 사진을 표현하려 했지만, 시간 및 비용부족
* Raspberry Pi Camera 해상도 문제 발생
* IoT와의 연결 및 시스템 프로토 타입 구현을 위해 사진으로 제작하여 표현

---

### 시연결과

* 병충해 작물 인식

![result1](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/result1.PNG?raw=true)

* 정상 작물 인식

![result2](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/result2.PNG?raw=true)

* 잡초 인식

![result3](https://github.com/soowoong0329/YOLOv5-Object-detection/blob/master/img/result3.PNG?raw=true)

---

