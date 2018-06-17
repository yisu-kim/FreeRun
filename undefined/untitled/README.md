---
description: 무선조종기능을 구현해봅시다.
---

# 방향조종구현하기 \(PWM 방식\)

{% hint style="info" %}
실제 차량은 핸들로 조향하지만, 이 무선조종자동차는 앞바퀴와 뒷바퀴가 고정되어있어요. 

이런 상태에서 차체의 방향을 조절하려면 좌, 우측 바퀴의 속도에 차이를 주거나, 바퀴의 진행 방향을 반대로 설정하면 됩니다. 

이런 방향조종방식을 PWM\(Pulse Width Modulation\)이라고 합니다.
{% endhint %}

![](../../.gitbook/assets/image%20%289%29.png)

L298N 모터드라이브를 보면 ENA, IN1, IN2, IN3, IN4, ENB라 쓰여 있는 핀 포트를 발견할 수 있습니다. 핀 포트 중 ENA는 Enable A를 뜻하며, 모터에 입력되는 전력을 ON/OFF 하는 기능을 합니다. 

![](../../.gitbook/assets/image%20%282%29.png)

ENA가 항상 ON이면 최대 출력으로 모터가 회전하고, OFF를 하면 모터가 회전하지 않아요. 속도를 조절하려면 ON/OFF의 비율을 조절해야 합니다. 이 비율은 hyper parameter\(사용자가 정해주는 값\)로써 0 ~ 255사이의 값을 주면 됩니다.

Free Run project 에서는 Forward, backward의 ch1, ch2값으로 \(100, 100\)을 주었고, Right, Left의 값으로 \(120, 40\), \(40, 120\)을 주어 방향을 제어했습니다.

{% hint style="info" %}
그럼, 라즈베리파이의 GPIO를 제어할 수 있는 파이썬 패키지 wiringpi를 설치하고,  각 바퀴의 속도를 조절해볼까요?

아래는 앞으로 자동차를 전진하게하는 코드입니다.  
왼쪽, 오른쪽으로 회전과 정지를 할 수 있는 코드로 수정해보세요.
{% endhint %}

{% tabs %}
{% tab title="control\_client.py" %}
```python
import wiringpi

# motor
STOP = 0
FORWARD = 1
BACKWORD = 2

# moter channel
CH1 = 0
CH2 = 1

# PIN input & output
OUTPUT = 1
INPUT = 0

# PIN setting
HIGH = 1
LOW = 0

# Raspberry GPIO setting
# PWM
ENA = 25
ENB = 30

# GPIO PIN
IN1 = 24
IN2 = 23
IN3 = 22
IN4 = 21

# PIN setting function
def setPinConfig(EN, INA, INB):
    wiringpi.pinMode(EN, OUTPUT)
    wiringpi.pinMode(INA, OUTPUT)
    wiringpi.pinMode(INB, OUTPUT)
    wiringpi.softPwmCreate(EN, 0, 255)
    
# motor control function
def setMotorControl(PWM, INA, INB, speed, stat):
    # motor speed control PWM
    wiringpi.softPwmWrite(PWM, speed)
    # FORWARD
    if stat == FORWARD:
        wiringpi.digitalWrite(INA, HIGH)
        wiringpi.digitalWrite(INB, LOW)
    # BACKWORD
    elif stat == BACKWORD:
        wiringpi.digitalWrite(INA, LOW)
        wiringpi.digitalWrite(INB, HIGH)
    # STOP
    elif stat == STOP:
        wiringpi.digitalWrite(INA, LOW)
        wiringpi.digitalWrite(INB, LOW)

# motor control function_wrap
def setMotor(ch, speed, stat):
    if ch == CH1:
        setMotorControl(ENA, IN1, IN2, speed, stat)
    else:
        setMotorControl(ENB, IN3, IN4, speed, stat)


# GPIO library setting
wiringpi.wiringPiSetup()

# motor PIN setting
setPinConfig(ENA, IN1, IN2)
setPinConfig(ENB, IN3, IN4)

while 1:
    setMotor(CH1, 150, BACKWORD)
    setMotor(CH2, 150, FORWARD)

```
{% endtab %}

{% tab title="<- 임의로 코드바꿈,  잘 돌아가는지 확인해봐야함" %}

{% endtab %}
{% endtabs %}



