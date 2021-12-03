# Opencore 시작하기에 앞서..

OpenCore 기반 시스템을 만들기 전에, 우리는 몇가지를 알아야합니다.

## 준비사항

1. <span style="color:red">_**[CRUCIAL]**_</span> 시간과 인내심.
   * 해킨토시는 메인컴(업무용) 과 같은 기기에 적합한 os가 아닙니다. 따라서, 중요한 작업을 하시거나, 마감기일이 있는 일이 있으시면 왠만해서는 하지 말아주세요. 
2. <span style="color:red">_**[CRUCIAL]**_</span> 사양을 정확히 아시는게 중요합니다.
   * CPU 세대와 이름
   * GPU(그래픽카드)
   * 저장장치(SSD,Nvme,HDD) (Nvme는 비삼성류를 추천합니다.)
   * 노트북이나 완본체일경우 제품명
   * 이더넷 칩셋 모델
   * 와이파이/블루투스 칩셋 모델
3. <span style="color:red">_**[CRUCIAL]**_</span> **명령어를 쓸줄 아는 기본적인 지식.**
   * 이 사항은 이 후술될 가이드의 **기본사항**이기도 합니다. 명령어 사용법을 모르신다면, 해킨토시는 권장하지 않습니다.
4. <span style="color:red">_**[CRUCIAL]**_</span> 호환성 섹션호환되는(해킨토시에서 쓸수 있는) 하드웨어를 알려드립니다.  [호환성](macos-limits.md)
5. <span style="color:red">_**[CRUCIAL]**_</span> 최소한의 USB용량:
   * macOS 에서 제작하시면 16기가 이상 필요합니다.
   * 윈도우,리눅스에서 제작하시면 4이상 필요합니다.
6. <span style="color:red">_**[CRUCIAL]**_</span> **이더넷 연결** (macOS가 지원하는 이더넷 동글또는 직결 포트) 그리고 LAN카드의 모델명을 알아야합니다.
   * 물리적인 이더넷 포트가 있거나, macOS 에 [호환되는 동글](https://dortania.github.io/Wireless-Buyers-Guide/) 이 필요합니다. 호환되지 않는 와이파이 카드를 사용할때도 동글을 사용하셔도 됩니다.
     * 대부분의 주요한 wifi 카드는 지원되지 않습니다.
   * [HoRNDIS](https://joshuawise.com/horndis#available_versions)를 사용하여 안드로이드폰으로 와이파이를 테더링하여 사용하실 수도 있습니다.
7. <span style="color:red">_**[CRUCIAL]**_</span> **적절한 OS 설치:**
   * 예시:
     * macOS (확실하게도 최신버전이 좋습니다.)
     * Windows (Windows 10, 1703 이상)
     * Linux (Python 2.7 이상이 돌아가는 적당한 Linux)
   * 리눅스와 윈도우 유저는 **15GB** 정도의 여유공간이 필요합니다. 윈도우에서는,C드라이브에 적어도 **15GB** 이상 필요합니다.
   * macOS 유저에게는 **30GB**이상의 유공간이 필요합니다.
   * 이 설명글에 있는 대부분의 도구는  [Python](https://www.python.org/downloads/)이 필요합니다
