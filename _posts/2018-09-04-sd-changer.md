---
layout: entry
title: SD Changer 제작기
description: 스케치에서 Apple SD Gothic Neo 폰트가 적용된 텍스트 레이어를 찾아 SF Pro Display 로 바꿔주는 스케치 플러그인을 만들었다.
publish: true
---

[SD Changer 다운로드는 여기서](https://github.com/yeun/sd-changer)

오랫동안 웹과 태블릿이 주력 제품인 회사에서 근무하다, 최근에 모바일 서비스가 중심인 회사로 이직하면서 모바일 기반의 새로운 작업 환경을 꾸리게 되었다. 직전 회사에서는 스케치를 거치지 않고 바로 코드로 구현하는 일이 잦았고 회사의 브랜드 서체가 있었기에 폰트 고민이 없었지만, 지금 회사의 제품은 많은 모바일 서비스가 그렇듯이, OS 기본 서체를 쓰고 있었다. 모바일이 생소한 내 눈엔 이 지점이 제일 먼저 들어왔다.

## 스케치의 폰트 문제

스케치에서는 하나의 텍스트 레이어에 하나의 폰트가 매칭된다. 하지만 아이폰에서 한글은 Apple SD Gothic Neo 폰트(이하 SD)로, 그 외 영문과 숫자, 특수 문자는 SF Pro Display 폰트(이하 SF)로 나온다. 그러므로 스케치에서 국문 베이스의 iOS 화면을 디자인하려면 하나의 텍스트 레이어에 두 개의 폰트가 적용되어야 한다. 그러므로 디자이너들은 SD가 적용된 텍스트 레이어에 다시 SF를 덮어씌워 우회적으로 폰트를 적용한다. 그러면 SF에는 국문 글리프가 없기 때문에 한글을 제외한 텍스트에 SF가 적용되어 iOS와 동일하게 보이기 때문이다.

문제는 텍스트 레이어를 선택해서 폰트를 바꿔주는 작업을 모든 레이어마다 해야 하며, 수많은 아트보드 사이에서 SF가 적용되지 않은 부분을 맨눈으로 찾아내기도 힘들다는 것이다. SD Changer는 단축키 한 번으로 이런 귀찮은 노동에서 벗어나고자 만들게 되었다.

## 스케치 플러그인 만들기

무식이 용감이라고, 전에 해본 적 없었지만, 막연히 'CSS 할 수 있으면 스케치 플러그인으로도 만들 수 있겠지' 하는 생각에 무작정 스케치 플러그인 만들기에 돌입했다. 생각보다 문서가 잘 되어있진 않았지만, 다른 사람들이 만든 플러그인 코드를 하나씩 뜯어보니 이것들을 응용해서 만들면 불가능할 것도 없어 보였다. 게다가 SD 폰트의 숫자와 영문이 자꾸 눈에 밟혀 내 스케치 파일에서 모두 없애고 싶은 마음이 컸기에 제작 동기가 아주 강력했다. 그렇다 보니 예상보다 빠른 일주일 만에 원하는 기능의 MVP 버전을 만들 수 있었다. 한 달 이상이 걸리거나 혹은 불가능할 수도 있다고 생각했기에 보람이 컸다.

첫 버전이 쉽게 만들어졌기에 정식으로 배포할 플러그인은 더 고도화된 모습으로 계획했다. 디자이너가 원하는 대로 폰트의 우선순위를 6개까지 정할 수 있고, 폰트 이름이 나오는 콤보박스 옵션에 해당 폰트가 적용되어있는 등 UX를 최적화하고 싶었다. 그러나 더 깊게 들어가니 Swift 라는 장벽을 만나게 되어 국문 사용자뿐만 아니라 전 세계적으로 사용될 수 있는 수준의 플러그인은 미래를 기약해야 했다. 

대신 MVP 버전을 사용하면서 느꼈던 몇 가지 불편한 점들을 개선했다. 몇 개의 레이어가 변환됐는지 메시지로 보여주기, 아트보드나 그룹을 선택하면 그 안에서 자동으로 텍스트 레이어를 찾아서 폰트를 바꿔주는 등의 기능이다. 모든 개선 사항을 반영해서 1.0.1 버전을 배포했고, 스케치 플러그인 리스트에 등재 신청을 했다.

<img src="https://raw.githubusercontent.com/yeun/sd-changer/master/sd-preview.gif">


## 앞으로

웹 디자인과 프론트엔드 코딩이 주 업무였던 때는 사이드 프로젝트로도 웹용 오픈 소스 프로젝트를 많이 했던 것처럼, 플랫폼 디자이너로 재직하는 지금은 디자이너들의 생산성을 높이는 플러그인이나 디자인 방법론을 연구하는 개인 작업을 많이 하게 될 것 같다. 지금은 iOS로 시안을 만들면 Android 화면으로 바꿔주는 식의 OS 변환 플러그인을 만들고 있는데, UI로만 접할 땐 알지 못했던 스케치의 심볼 시스템에 대해 깊이 이해할 수 있어 좋았다. 또한 내 새로운 고객인 동료 디자이너들이 주는 피드백은 엔드 유저 피드백보다 더 공감이 잘 되어 프로덕트 디자인을 할 때와는 다른 재미를 느끼며 일할 수 있을 것 같다.