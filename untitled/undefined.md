---
description: '무선조종자동차 정비를 마쳤다면, 이제 무선조종차와 함께 데이터세트를 구축 할 차례입니다!'
---

# 데이터세트 구축



신경망 학습을 위한 데이터는 pi camera를 통해 전달받은 이미지에 전,후,좌,후의 방향키를 라벨링하여 모읍니다.

PC에서는 collect\_training\_data.py을 실행하고,

raspberry pi에서는 control\_client.py와 stream\_client.py을 순차적으로 실행합니다.

