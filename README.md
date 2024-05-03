
## 🚀 미션: 코틀린 숫자야구 게임 왼벽 구현하자 (이왕이면 객체 지향까지 ..)

이번 프로젝트의 미션은 숫자야구 게임을 구현하는 것이었습니다. (과제의 주어진 필수 구현 기능과 선택 구현 기능은 아래를 참고해주세요)
스스로 LV1 - LV3까지 패키지로 나누어 보았으며,
필수 구현기능, 선택 구현기능, 객체 구현기능으로 레벨을 나누어 보았습니다.

<img src="https://techcourse-storage.s3.ap-northeast-2.amazonaws.com/2020-03-16T10:41:53.786image.png" width="400">

<br/>

## ✨ 룰 : 필수 구현 기능

요구사항 별 상세 기능을 구현하고, 실제 게임을 진행해보며 발생할 수 있는 예외사항들을 고려해봅니다.

-입력과 출력

- 입력
서로 다른 3자리 수
게임 시작, 기록 보기, 종료를 구분하는 수 입력
필수 구현에서는 실행 시, 바로 게임 시작
선택 구현에서 시작, 기록, 종료 구분
    
- 출력
입력한 수에 대한 결과값을 “볼, 스트라이크, Nothing”으로 표시
    
- 요구사항
    1에서 9까지의 서로 다른 임의의 수 3개를 정하고 맞추는 게임입니다.
    정답은 랜덤으로 만듭니다.(1에서 9까지의 서로 다른 임의의 수 3자리)
    상세
        정답을 맞추기 위해 3자리수를 입력하고 힌트를 받습니다
            힌트는 야구용어인 **볼**과 **스트라이크**입니다.
            같은 자리에 같은 숫자가 있는 경우 **스트라이크**, 다른 자리에 숫자가 있는 경우 **볼**입니다.
            만약 올바르지 않은 입력값에 대해서는 오류 문구를 보여주세요.
            3자리 숫자가 정답과 같은 경우 게임이 종료됩니다.

<br/>

## ✨ 룰 : 선택 구현 기능

1. 안내문구 출력
프로그램을 시작할 때 안내문구를 출력해주세요 (1번 게임 시작하기의 경우 **“필수 구현 기능”** 의 예시처럼 게임이 진행됩니다)
정답을 맞혀 게임이 종료된 경우 위 안내문구를 다시 보여주세요
(안내문구 내 게임시작, 기록 보기, 게임종료가 있습니다)

2. 정답이 되는 숫자를 0에서 9까지의 서로 다른 3자리의 숫자로 바꿔주세요.
  맨 앞자리에 0이 오는 것은 불가능합니다.

3. 기록 보기
  기록 보기 실행 시, 완료한 게임들에 대해 시도 횟수를 보여줍니다.
4. 종료하기
   종료하기 실행 시, 기록들을 모두 초기화합니다.

<br/>

## ✨ 전체적인 코드흐름

(LV2 패키지를 참고하여 봐주시면 감사하겠습니다.)
while(true) 조건을 주어 게임 실행 단 전체를 감싸고, 총 3개의 옵션 (1.Game Start 2.View Record 3. End The Game) 중 하나를 선택
처음부터 기록 조회 번호를 입력 시 예외 문구 출력하여 다시 메뉴를 선택할 수 있도록 조정, 숫자가 아닌 문자를 입력하거나 다른 수를 입력 시 예외가 발생하며 다시 처음 옵션선택으로 되돌아가도록 설정

0부터 9까지 리스트를 구성하여 숫자를 섞고 인덱스 0번부터 2번까지 리스트를 잘라 정답을 구성
정답이 사용자가 입력한 수와 일치할 때 정답이 되며 게임이 종료되도록 설정
해당 과정에서 처음부터 숫자 0을 입력하거나, 세자리 수를 입력하지 않거나, 동일한 숫자를 입력 시 예외문구 출력 후 다시 숫자를 입력할 수 있도록 설정

<br/>

## 여러가지 기능을 구현하며 어려웠던 부분

게임 전체를 while 문으로 감싸 코드의 흐름을 이해하고 작성하는 방식이 다소 어려웠고, 무엇보다 LV3 단계를 구현하는 과정에서 명확하게 객체의 역할과 책임을 분리하지 못해 실패했습니다.

<br/>

## 🚜🎨 객체 지향

처음 구상해 본 그림은 다음과 같습니다.
게임의 결과를 기록하는 **“기록원”**  / 스트라이크, 볼을 판단하고 사용자에게 문구를 출력하는 **“심판”** / 경기 중 발생할 수 있는 오류들을 처리하는 **“게임관리인”** 
객체들이 공통적으로 필요한 정보를 가진 **“NumberBaseballGame”**

- 앞전에 설명한 것 처럼 while 문으로 게임 진행부분 전체를 갑싸 안고 코드를 작성하여 객체 별 역할을 분리 시 컴파일이 되지 않는 문제가 발생했고 기존 짜여진 코드로 역할을 분리하는 것은 사실 불가능에 가까웠습니다.
- 객체 지향 관련 이전 강의를 돌려보며 직접 구현해볼 수 있겠다 생각했으나 실제로 해보는 것은 정말 다른 일이었습니다.
- 객체 지향은 과제 해설 이후 주말동안 다시 진행해 볼 예정입니다.

  <img src="https://i.ibb.co/RgDdR67/IMG-0007.jpg" width="400">

<br/>

## 🔨 빌드 환경

* Language: Kotlin
* IDE: Intellij
* SDK: Eclipse Temurin 22.0.1
