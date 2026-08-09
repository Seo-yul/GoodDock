<p align="center">
  <img src="assets/logo.png" width="360" alt="GoodDock 로고. 강아지가 Dock 위에 얌전히 앉아 있다.">
</p>

<h1 align="center">GoodDock</h1>

<p align="center"><em>"앉아. 기다려. 착하지."</em><br>
macOS Dock을 원하는 모니터에 얌전히 앉혀두는 메뉴 막대 앱</p>

<p align="center">
  <a href="https://github.com/Seo-yul/GoodDock/releases/latest"><b>⬇︎ 내려받기</b></a> ·
  <a href="https://devops.ai.kr/GoodDock/">소개 페이지</a> ·
  <a href="README.md">English</a>
</p>

---

## 왜 만들었나

macOS에서 모니터를 여러 대 쓰면 Dock이 한자리에 가만히 있지 않습니다. 아무 모니터에서나 포인터를 화면 하단으로 꾹 밀면 Dock이 그 모니터로 따라와버립니다. 잠깐 마우스를 내렸을 뿐인데 Dock이 옆 모니터로 이사를 가 있고, 다시 데려오려면 또 하단을 꾹 눌러야 합니다.

Apple이 준 선택지는 둘뿐이고 어느 쪽도 답이 아닙니다. "디스플레이별 공간 사용"을 끄면 Dock은 고정되지만 Space 전환 시 모든 모니터가 한꺼번에 넘어가는 더 큰 불편이 생깁니다. 켜두면 Space는 독립적이지만 Dock이 떠돌아다닙니다.

GoodDock은 두 마리 토끼를 모두 잡습니다. 화면 하나를 지정하면 Dock은 그곳에 머물고, Space는 원래대로 모니터별로 독립적으로 동작합니다.

## 어떻게 동작하나

macOS는 Dock을 특정 디스플레이에 고정하는 API를 제공하지 않습니다. 그래서 GoodDock은 Dock을 직접 옮기는 대신, Dock이 다른 모니터로 넘어가는 조건 자체를 없앱니다.

Dock을 부르는 동작은 화면 맨 아래에 닿아 있는 포인터를 한 번 더 아래로 미는 것입니다. GoodDock은 마우스 이벤트를 감시하다가 고정하지 않은 모니터에서 이 동작이 감지되는 순간 포인터를 몇 픽셀 위로 되돌립니다. 포인터가 바닥에 붙어 있을 수 없으니 Dock이 불려 나올 일도 없습니다.

아래쪽에 다른 모니터가 이어져 있는 가장자리는 자동으로 제외하므로, 모니터 사이의 포인터 이동은 방해받지 않습니다.

## 기능

- 메뉴 막대에 작은 강아지 아이콘으로 상주하며 Dock 자리를 차지하지 않습니다
- 실제 모니터 배치를 축소한 지도에서 클릭으로 고정할 화면을 선택합니다
- 모니터를 연결하거나 분리하거나 배치를 바꿔도 자동으로 인식합니다
- 메뉴를 열면 지금 작동 중인지 바로 확인할 수 있습니다
- 로그인 시 자동 실행을 켜고 끌 수 있습니다
- 언제든 "고정 안 함"을 고르면 원래 동작으로 돌아갑니다

## 설치

macOS 13 이상이 필요합니다.

[Releases](https://github.com/Seo-yul/GoodDock/releases/latest)에서 DMG를 받아 열면 설치 안내 화면이 뜹니다. 화살표를 따라 GoodDock을 응용 프로그램 폴더로 끌어놓으세요.

### 처음 열 때: "악성 코드가 없음을 확인할 수 없습니다" 경고

이 앱은 Apple 개발자 인증서로 서명되어 있지 않아서 처음 열 때 Gatekeeper가 막습니다. 아래 순서로 한 번만 허용하면 이후로는 그냥 실행됩니다.

1. GoodDock을 처음 열면 경고 창이 뜹니다. **"완료"**를 누르세요. "휴지통으로 이동"을 누르면 앱이 지워지니 주의하세요.

2. 왼쪽 위 Apple 메뉴 > 시스템 설정 > 개인정보 보호 및 보안으로 들어가 아래로 내리면 "Mac을 보호하기 위해 'GoodDock'을(를) 차단했습니다"라는 안내가 보입니다. 옆의 **"그래도 열기"**를 누르세요.

   <img src="docs/assets/guide-blocked.png" width="560" alt="개인정보 보호 및 보안 설정의 차단 안내와 그래도 열기 버튼">

3. 확인 창이 뜨면 한 번 더 **"그래도 열기"**를 누르세요.

   <img src="docs/assets/guide-open-anyway.png" width="280" alt="확인 창의 그래도 열기 버튼">

macOS 14 이하에서는 앱을 우클릭한 뒤 "열기"를 선택하는 것으로 충분합니다. 그래도 열리지 않으면 격리 속성을 지우세요.

```bash
xattr -dr com.apple.quarantine /Applications/GoodDock.app
```

### 첫 실행

첫 실행 시 손쉬운 사용(Accessibility) 권한을 요청합니다. "시스템 설정 열기"를 누른 뒤 목록에서 GoodDock을 켜주세요. (시스템 설정 > 개인정보 보호 및 보안 > 손쉬운 사용) 허용하면 앱이 자동으로 감지해서 바로 동작합니다.

<img src="docs/assets/guide-accessibility.png" width="480" alt="손쉬운 사용 접근 권한 요청 창">

그다음 메뉴 막대의 강아지를 눌러 Dock을 앉혀둘 모니터를 클릭하면 끝입니다. 메뉴 맨 위가 "작동 중"으로 보이면 정상입니다.

> **주의:** "디스플레이별 공간 사용"(시스템 설정 > 데스크탑 및 Dock > Mission Control)은 **켜진** 상태여야 합니다. 이 설정을 끄면 모든 모니터가 같은 Space로 묶이는데, 바로 그 불편을 피하려고 만든 앱입니다.

## 제거

GoodDock을 종료하고 `/Applications/GoodDock.app`을 휴지통에 넣으면 됩니다. 설정까지 지우시려면 아래를 실행하세요.

```bash
defaults delete kr.ai.devops.gooddock
tccutil reset Accessibility kr.ai.devops.gooddock
```

## 알아둘 점

- 고정하지 않은 모니터에서는 화면 맨 아래 2픽셀에 포인터를 밀어붙이는 동작이 살짝 제한됩니다. Dock을 막는 원리상 필요한 비용이고 일반적인 클릭에는 영향이 없습니다.
- 앱을 종료하면 모든 동작이 즉시 원래대로 돌아갑니다. 시스템 설정을 건드리지 않습니다.
- 저장하는 값은 고정한 화면의 UUID 하나뿐이고 `~/Library/Preferences/kr.ai.devops.gooddock.plist`에 들어갑니다.
- 네트워크 통신은 전혀 하지 않습니다.

## 이름에 대하여

Dock이 말을 안 듣고 돌아다니길래 훈련을 시켰습니다. 이제 지정한 자리에 얌전히 앉아 기다립니다. 착한 Dock, GoodDock입니다.

## 문의

버그 제보나 기능 제안은 [Issues](https://github.com/Seo-yul/GoodDock/issues)에 남겨주세요.

[LinkedIn](https://www.linkedin.com/in/yoon-seoyul)으로 연락 주셔도 됩니다.

## 라이선스

개인이든 업무든 무료로 쓰실 수 있습니다.

저작권자가 모든 권리를 보유하며 **수정과 재배포, 상업적 이용은 허용되지 않습니다.** 전체 조건은 [LICENSE](LICENSE)를 참고하세요.
