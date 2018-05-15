---
description: '무선조종자동차에 필요한 구성품목을 확인하고, 조립해봅시다!'
---

# 무선조종자동차 조립하기

## 무선조종자동차 구성품목 \(준비물\)

1. 
#### Arduino 스마트 자동차 4WD kit ver.2 

{% hint style="info" %}
본 프로젝트에서는 아두이노는 사용하지 않으니, 아래의 부품이 포함된 다른 키트를 구매하거나 개별 구매하여도 좋습니다.
{% endhint %}

* 자동차 상/하판
* 자동차 바퀴  4개
* L298N 모터 드라이버 보드
* DC Motor x 4
* Mini bread board
* 1.5v 배터리 케이스 \(6개입\)
* 9v 배터리 케이스 \( 휴대용 보조배터리 팩으로 대체가능\)

#### Raspberry PI kit

* Raspberry PI 3
* MicroSD 32G
* 2.5A 어댑터
*  MicroSD 카드 리더기
* 방열판
* HDMI 케이블
* Pi Camera Module V2

#### 별도 구매

* ipTIME N100mini-AP dongle
* 1.5v 배터리 다수

## 무선조종자동차 조립하기



#### 1. DC모터를 조립합니다. 그리고 알루미늄 고정 틀, 긴 나사, 너트를 이용해 DC모터를 차체 하판에 고정시킵니다.

![](../.gitbook/assets/image.png)

모터에 고정한 알루미늄 고정 틀의 아랫부분 나사 홀과 하단 홀을 일치시켜 볼트로 고정시킵니다. DC 모터에 선이 없는 경우에는 납땜하여 고정시켜야 합니다.  


![](../.gitbook/assets/image%20%283%29.png)

볼트로 조여주며 DC모터 축 방향이 일직선이 되도록 잘 조절 해 주었다면, 이제 타이어를 끼워줍니다.

  


#### 2. DC모터와 L298N 모터 드라이버를 연결해 줍니다

![](../.gitbook/assets/image%20%285%29.png)

  
  
DC 모터는 L298N 모터 드라이버의 Motor A, Motor B 포트에 각각 2개씩 연결됩니다.  DC 모터는 2개의 단자가 있으며, 각 단자에 +,- 극을 연결하여 전원을 입력할 경우 모터가 작동합니다. 

{% hint style="info" %}
DC 모터는 L298N 모터 드라이버의 Motor A, Motor B 포트에 각각 2개씩 연결됩니다.  DC 모터는 2개의 단자가 있으며, 각 단자에 +,- 극을 연결하여 전원을 입력할 경우 모터가 작동합니다. 연결선이 빠지지않도록 잘 연결해주세요!  

{% endhint %}



#### 3. 라즈베리파이와 L298N 모터드라이버를 연결해줍니다. 그리고 AA배터리 홀더는 L298N 모터드라이버에 파이카메라는 라즈베리파이에 연결해줍니다.

{% hint style="info" %}
라즈베리파이와 L298N 모터드라이버를 연결은 아래를 참고하세요.

**라즈베리 파이   \(-연결선 -\)  L298N  
**[\#1,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=1%2C) 27Pin BCM0           -        ENB  
[\#2,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=2%2C) 29Pin BCM5           -        IN4  
[\#3,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=3%2C) 31Pin BCM6           -        IN3  
[\#4,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=4%2C) 33Pin BCM13         -        IN2  
[\#5,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=5%2C) 35Pin BCM19         -        IN1  
[\#6,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=6%2C) 37Pin BCM26         -        ENA  
[\#7,](https://blog.naver.com/PostListByTagName.nhn?blogId=chandong83&encodedTagName=7%2C) 39Pin GND             -        GND
{% endhint %}

![https://blog.naver.com/chandong83/221156273595](../.gitbook/assets/image%20%281%29.png)

{% hint style="info" %}
L298N 모터드라이버는 라즈베리 파이를 보조해주는 역할을 합니다. 모터는 MCU가 허용하는 전류보다 더 큰 전류가 필요한 경우가 많아 추가적인 회로가 필요합니다. 이때 필요한 것이 모터 드라이버입니다!
{% endhint %}

![](../.gitbook/assets/image%20%282%29.png)

