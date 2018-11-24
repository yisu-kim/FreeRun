---
description: 본 프로젝트의 오픈소스 코드를 활용하여 자신만의 프로젝트를 만들어 보세요.
---

# 오픈소스 프로젝트 활용하기

## Git 설치하기

Git이란 버전 관리 시스템 \(VCS - Version Control System\)으로 파일 변화를 시간에 따라 기록했다가 나중에 특정 시점의 버전을 다시 꺼내올 수 있는 시스템입니다. git 저장소\(repository\)를 로컬에 만들거나 GitHub 또는 GitLab을 이용하여 웹 상에 만들어 이용할 수 있습니다.

Git repository\(저장소\)에 있는 프로젝트의 소스 코드를 활용하고 본인의 프로젝트를 관리하기 위해서 Git을 설치합시다.

{% tabs %}
{% tab title="Linux" %}
콘솔에서 다음 명령어를 실행하세요.

```text
$ sudo apt-get install git
```
{% endtab %}

{% tab title="Windows" %}
윈도우용 Git은 [https://git-scm.com/download/win](https://git-scm.com/download/win) 웹사이트에서 자동으로 다운로드 받을 수 있습니다.

모두 기본 설정을 유지하며 다음으로 넘어가되, 다음 화면에서 "Use Git and optional Unix tools from the Windows command Prompt" 옵션 선택하세요.

![](../.gitbook/assets/git.png)
{% endtab %}
{% endtabs %}

## FreeRun 프로젝트 가져오기

{% hint style="info" %}
본 프로젝트의 전체 소스 코드는 아래 링크에서 확인할 수 있습니다.
{% endhint %}

{% embed url="https://gitlab.com/minh364/FreeRun" %}



이제 git을 사용해서 프로젝트를 로컬 즉, 본인의 컴퓨터로 가져옵시다. 콘솔에서 다음 명령어를 입력하세요.

```text
git clone git@gitlab.com:minh364/FreeRun.git
```

원격 저장소에 있는 FreeRun 프로젝트를 가져왔나요? 이제 자신만의 프로젝트를 만들어 보세요!

## 설치 완료

모든 설치 과정을 완료했습니다. 다음 장에서는 무선조종자동차를 조립하고 조종하는 방법을 소개합니다.

이미 무선조종자동차를 가지고 있는 경우 아래 링크를 통해 인공지능 모델에 필요한 첫 번째 단계, 트레이닝 세트 수집 방법을 배워보세요.

{% page-ref page="../untitled/" %}





