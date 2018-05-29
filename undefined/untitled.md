---
description: >-
  실제 차량은 핸들로 조향하지만, 이 무선조종자동차는 앞바퀴와 뒷바퀴가 고정되어있어요. 이런 상태에서 방향을 조절하려면 좌, 우측 바퀴의
  속도에 차이를 주거나, 진행 방향을 반대로 설정하면 됩니다. 이러한 방향조종방식을 PWM(Pulse Width Modulation)이라고
  합니다.
---

# 무선방향조종 \(PWM 방식\)

![](../.gitbook/assets/image%20%288%29.png)

L298N 모터드라이브를 보면 ENA, IN1, IN2, IN3, IN4, ENB라 쓰여 있는 핀 포트를 발견할 수 있습니다. 핀 포트 중 ENA는 Enable A를 뜻하며, 모터에 입력되는 전력을 ON/OFF 하는 기능을 합니다. 

![](../.gitbook/assets/image%20%282%29.png)

ENA가 항상 ON이면 최대 출력으로 모터가 회전하고, OFF를 하면 모터가 회전하지 않아요. 속도를 조절하려면 ON/OFF의 비율을 조절해야 합니다. 이 비율은 hyper parameter\(사용자가 정해주는 값\)로써 0 ~ 255사이의 값을 주면 됩니다.

Free Run project 에서는 Forward, backward의 ch1, ch2값으로 \(100, 100\)을 주었고, Right, Left의 값으로 \(120, 40\), \(40, 120\)을 주어 방향을 제어했습니다.

control\_client.py

```text
import socket
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
HOST = 'Local host’
PORT = 5000
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((HOST, PORT))
s.listen(1)
conn, addr = s.accept()
print ('Connected by', addr)
while 1:
    data = conn.recv(1024)
    if not data: break
    if 'w' == data:
        print ('forward')
        setMotor(CH1, 150, BACKWORD)
        setMotor(CH2, 150, FORWARD)
    elif 's' == data:
        print ('stop')
        setMotor(CH1, 150, STOP)
        setMotor(CH2, 150, STOP)
    elif 'a' == data:
        # left side reverse
        print ('left')
        setMotor(CH1, 120, BACKWORD)
        setMotor(CH2, 40, FORWARD)
    elif 'd' == data:
        # right side reverse
        print ('right')
        setMotor(CH1, 40, BACKWORD)
        setMotor(CH2, 120, FORWARD)
    elif 'x' == data:
        print ('back')
        setMotor(CH1, 150, FORWARD)
        setMotor(CH2, 150, BACKWORD)
    else:
        continue conn.close()
```



