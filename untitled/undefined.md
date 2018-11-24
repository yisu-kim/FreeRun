# 데이터세트 구축



신경망 학습을 위한 데이터는 pi camera를 통해 전달받은 이미지에 전,후,좌,후의 방향키를 라벨링하여 구축합니다.

![&amp;lt;&#xB77C;&#xBCA8;&#xB9C1;&#xB41C; &#xB370;&#xC774;&#xD130;&amp;gt;](../.gitbook/assets/image%20%284%29.png)

PC에서는 `collect_training_data.py`을 실행하고,  Raspberry pi에서는 `control_client.py`와 `stream_client.py`을 순차적으로 실행하고, 주행로 위에서 자동차의 방향을 조종하면 `collect_training_data.py`에 의해 자동적으로 라벨링됩니다.

