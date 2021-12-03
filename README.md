---
home: true
heroImage: /dortania-logo-clear.png
heroText: Dortania의 OpenCore 설치 가이드
actionText: Getting Started??
actionLink: prerequisites.md

meta:
- name: description
  content: 지원버전 0.7.5
---

# 오픈코어란 무엇인가요?
오픈코어는 우리가 "부트로더"라고 정의하는것과 같나요?? macOS를 쓰기 위해 우리가 준비하는 복잡한 소프트웨어 쪼가리에 불가한가요?? 특히 SMBIOS, ACPI 와 켁스트들을 macOS에 적용하면서요. 이 도구가 클로버와 같은 다른 도구와 다른점은 보안과 질을 염두에 두고 만들어진 프로그램이라는 겁니다. 이 덕분에 우리는 리얼 맥에서 볼수 있는 [System Integrity Protection](https://support.apple.com/en-ca/HT204899) 와 [FileVault](https://support.apple.com/en-ca/HT204837) 같은 다양한 보안 기능들을 사용할수 있습니다. 더 깊은 분석은 [Why OpenCore over Clover and others](why-oc.md) 여기서 보실수 있습니다.

이 가이드는 두가지 주요한 내용에 집중할 예정입니다:

* x86 기반 컴퓨터에 macOS 설치
* 당신의 크랙이 작동하게 하는 원리 설명

이로인해, 당신은 아마도 읽으며 배우고, 심지어는 구글링까지 할 수 있습니다. 이것은 쉬운 원클릭 설치방법이 아닙니다.

OpenCore 는 아직도 beta 단계라는것을 염두에 두셨으면 좋겠습니다. 하지만, 꽤 안정적이며, 클로버보다 더 안정적이라는것은 확신합니다. Opencore 는 자주 업데이트 되며, 이로인해 설정의 일부분이 자주 바뀔 수 있습니다.

마지막으로, Opencore를 작업하시다 문제가 있다면, [r/Hackintosh subreddit](https://www.reddit.com/r/hackintosh/) 와 [r/Hackintosh Discord](https://discord.gg/u8V7N5C) 또는 [x86](https://https://x86.co.kr/)에서 도움말을 얻어가세요.
