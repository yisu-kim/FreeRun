---
description: Anaconda 가상 환경을 통해 독립된 개발 환경을 구성해 봅시다.
---

# Anaconda 설치하기

텐서플로우 설치 전, 개발 환경을 깔끔하게 관리해주는 도구를 설치해 봅시다. 가상 환경\(Virtual environment\)은 독립된 개발 환경을 구성할 수 있도록 도와줍니다.

{% tabs %}
{% tab title="Windows" %}
윈도우용 아나콘다는 [https://www.anaconda.com/download/\#windows](https://www.anaconda.com/download/#windows) 웹사이트에서 다운로드 할 수 있습니다. 32-Bit인지 또는 64-Bit인지 확인하고 Python 2.7 version을 다운로드 하세요. 다운받은 설치 프로그램을 실행하여 설치를 완료하세요.

설치가 완료되었는지 확인하려면 Anaconda Prompt를 실행하고 다음 명령어를 입력하세요.

```text
> conda --version
conda x.x.x
```
{% endtab %}

{% tab title="Linux" %}
리눅스용 아나콘다는 https://www.anaconda.com/download/\#linux 웹사이트에서 다운로드 할 수 있습니다. 32-Bit인지 또는 64-Bit인지 확인하고 Python 2.7 version을 다운로드 하세요.

아나콘다를 다운 받은 위치에서 다음 명령을 입력하세요. \(다운 받은 버전에 따라 파일명이 다를 수 있습니다.\)

```text
$ bash Anaconda2-x.x.x-Linux-x86_64.sh
```



{% hint style="info" %}
설치 시 다음 메시지가 나오면 지시사항에 따르세요.
{% endhint %}

```text
# yes 입력
Do you accept the license terms? [yes|no]
>>> yes

# Enter
Anaconda2 will now be installed into this location: /home/pirl/anaconda2
 >>>
 
# yes 입력
Do you with the installer to prepend the Anaconda2 install location to PATH in your /home/pirl/.bashrc ? [yes|no]
>>> yes
```



설치가 완료되었습니다. 설정된 PATH 환경변수를 로딩하기 위해 다음 명령어를 입력하세요.

```text
$ source ~/.bashrc
```



설치된 아나콘다 버전을 확인하려면 다음 명령어를 입력하세요.

```text
$ conda --version
conda x.x.x
```
{% endtab %}
{% endtabs %}

## Jupyter Notebook 사용하기

주피터 노트북은 라이브 코드, 방정식, 시각화 및 네러티브 텍스트가 포함된 문서를 만들고 공유할 수 있는 오픈 소스 웹 응용 프로그램입니다. 데이터 정리 및 변환, 수치 시뮬레이션, 통계 모델링, 데이터 시각화, 기계 학습 등 다양한 분야에서 사용할 수 있는 도구랍니다.



아나콘다를 설치했다면 주피터 노트북이 함께 설치되어 있을 거예요.

주피터 노트북을 실행하려면 콘솔에서 다음 명령어를 입력하세요. \(윈도우의 경우 Anaconda Prompt에서 입력\)

```text
jupyter notebook
```

