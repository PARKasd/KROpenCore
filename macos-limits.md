# 하드웨어 한계점

macOS에서는 설치이전에 당신이 고려해야할 무수히 많은 하드웨어 제한이 있습니다. 이 카테고리는 애플이 지원하거나, 해킨토시 커뮤니티에서 패치한 지원이 되는 소수의 하드웨어에 대해 설명해드립니다.

확인해야할 주요 하드웨어:

[[toc]]

더 자세한 내용을 원하신다면 아래 링크들을 확인해주세요:

* [GPU 구매 가이드](https://dortania.github.io/GPU-Buyers-Guide/)
  * 어떤 macOS에서 현재 GPU가 지원되는지 확인할 수 있습니다.
* [wifi 구매 가이드](https://dortania.github.io/Wireless-Buyers-Guide/)
  * wifi 카드 지원여부를 확인하실 수 있습니다.
* [사지 말아야할 부품가이드](https://dortania.github.io/Anti-Hackintosh-Buyers-Guide/)
  * 어떤 하드웨어가 실패의 요인인지 확인할수 있습니다.

## CPU 지원

CPU 지원에 대한 안내:

* 32bit, 64bit CPU 둘다 지원합니다.

  - 그러나, CPU 지원은 macOS 버전에 따라 상이할수 있으니, 아래표를 보고 참고해주세요
* 인텔의 데스크탑 CPU는 대부분 지원됩니다.

  - Yonah 부터 Comet 레이크까지 지원합니다.
* 인텔의 하이엔드 데스크톱과 서버의 CPU가 지원됩니다.
  
  *  Nehalem 부터 Cascade 레이크 X까지 지원됩니다.
* 인텔의 i시리즈와 제온시리즈의 노트북 CPU 가 지원됩니다. 
  
  - Arrandale 부터 Ice 레이크까지 지원됩니다. 
  
  - 아톰,셀러론,펜티엄은 지원되지 않는점 유의해주세요
* AMD의 불도저~ 라이젠 데스크탑 CPU
  - **노트북용 CPU**는 지원되지 않습니다.
  - AMD CPU는 macOS 의 **모든 기능이 지원되지 않습니다.**

**For more in-depth information, see here: [Anti-Hardware Buyers Guide](https://dortania.github.io/Anti-Hackintosh-Buyers-Guide/)**

::: details CPU Requirements(자세한 CPU 요구사항)

CPU 요구사항

* 32bit CPU는 macOS 10.4.1 ~ 10.6.8 에서 지원됩니다.
  * 10.7.x 버전 부터는 64bit를 요구하기에, 32bit CPU 는 10.6 버전까지 지원됩니다.
* 64bit CPU는 10.4.1 부터 현재까지 지원됩니다.

SEE 요구사항:

* SSE3 는 모든 인텔기준 macOS에서 요구됩니다.
* SSSE3 는 모든 64bit macOS에서 요구됩니다.
  * SSSE3가 없는 CPU (현재 64bit 펜티엄), 32bit 사용자공간을 만드는것을 권장합니다. (`i386-user32`)
* SSE4는 macOS 10.12 이상에서 요구됩니다.
* SSE4.2는 macOS 10.14 이상에서 요구됩니다.
  * SSE4.1 CPU들은 [telemetrap.kext](https://forums.macrumors.com/threads/mp3-1-others-sse-4-2-emulation-to-enable-amd-metal-driver.2206682/post-28447707)로 지원됩니다.
  * AMD 드라이버는 Metal 지원을 위해 SSE4.2가 필요합니다. 이를 해결하기 위해  [MouSSE: SSE4.2 emulation](https://forums.macrumors.com/threads/mp3-1-others-sse-4-2-emulation-to-enable-amd-metal-driver.2206682/)를 읽어보세요

Firmware 요구사항:

* OS X 10.4.1 부터 10.4.7는 EFI32 (i.e. IA32 (32-bit) OpenCore 버전)를 요구합니다.
  * OS X 10.4.8 ~ 10.7.5 는  EFI32와 EFI64 둘다 지원합니다.
* OS X 10.8 이후의 버전은 EFI64 (i.e. x64 (64-bit) OpenCore)를 요구합니다.
* OS X 10.7 ~ 10.9는 리커버리 파티션으로 부팅하기 위해 OpenPartitionDxe.efi를 요구합니다. 

Kernel 요구사항:

* OS X 10.4, 10.5는 32bit Kernel 만 지원하기에 32bit kexts를 요구합니다. 
  * OS X 10.6, 10.7 은 32bit, 64bit Kernel 둘다 지원합니다.
* OS X 10.8 이후는 64bit Kernel 만 지원하기에 64bit kexts를 요구합니다.
  * `lipo -archs` 명령어를 통해 kext가 지원하는 아키텍쳐를 확인해보세요.(kext 묶음에서 돌리는것이 아닌 binary 자체에서 돌려주세요)

코어/스레드 제한:

* OS X 10.10 이하는 24스레드 보다 많다면 부팅하지 않을 수 있습니다. (`mp_cpus_call_wait() timeout` 패닉의 원인일수 있습니다.)
* OS X 10.11 이후는 64스레드 제한이 있습니다.
* `cpus=` 부팅옵션은 workaround 로 쓰이거나, 하이퍼쓰레딩을 비활성화 하는데 이용될 수 있습니다.

주의 사항:

* Lilu 와 플러그인은 10.8 이상에서 구동됩니다.
  * 10.8 이하는 FakeSMC 사용을 권장합니다.
* OS X 10.6 이하는 RebuildAppleMemoryMap 이 활성화되어야 합니다.
  * 초기커널의 문제를 해결해줄 수 있습니다.

:::

::: details Intel CPU Support Chart(상세한 intel CPU 지원 리스트)

순정 커널에 기반한 지원명단 (i.e. no modifications):

| CPU 세대 | 최초 <br />지원 | 최종<br />지원<br />버전<br />                    | 주의 사항 | CPUID |
| :--- | :--- | :--- | :--- | :--- |
| [Pentium 4](https://en.wikipedia.org/wiki/Pentium_4) | 10.4.1 | 10.5.8 | dev kit 에서만 <br />사용됨               | 0x0F41 |
| [Yonah](https://en.wikipedia.org/wiki/Yonah_(microprocessor)) | 10.4.4 | 10.6.8 | 32-Bit | 0x0006E6 |
| [Conroe](https://en.wikipedia.org/wiki/Conroe_(microprocessor)), [Merom](https://en.wikipedia.org/wiki/Merom_(microprocessor)) | 10.4.7 | 10.11.6 | No SSE4 | 0x0006F2 |
| [Penryn](https://en.wikipedia.org/wiki/Penryn_(microarchitecture)) | 10.4.10 | 10.13.6 | No SSE4.2 | 0x010676 |
| [Nehalem](https://en.wikipedia.org/wiki/Nehalem_(microarchitecture)) | 10.5.6 | <span style="color:green">현재 <br />지원 </span> | N/A | 0x0106A2 |
| [Lynnfield](https://en.wikipedia.org/wiki/Lynnfield_(microprocessor)), [Clarksfield](https://en.wikipedia.org/wiki/Clarksfield_(microprocessor)) | 10.6.3 | ^^ | 10.14 이후에서 <br />내장그래픽 미지원 | 0x0106E0 |
| [Westmere, Clarkdale, Arrandale](https://en.wikipedia.org/wiki/Westmere_(microarchitecture)) | 10.6.4 | ^^ | ^^ | 0x0206C0 |
| [Sandy Bridge](https://en.wikipedia.org/wiki/Sandy_Bridge) | 10.6.7 | ^^ | ^^ | 0x0206A0(M/H) |
| [Ivy Bridge](https://en.wikipedia.org/wiki/Ivy_Bridge_(microarchitecture)) | 10.7.3 | ^^ | 12 이후에서 <br />내장그래픽 미지원       | 0x0306A0(M/H/G) |
| [Ivy Bridge-E5](https://en.wikipedia.org/wiki/Ivy_Bridge_(microarchitecture)) | 10.9.2 | ^^ | N/A | 0x0306E0 |
| [Haswell](https://en.wikipedia.org/wiki/Haswell_(microarchitecture)) | 10.8.5 | ^^ | ^^ | 0x0306C0(S) |
| [Broadwell](https://en.wikipedia.org/wiki/Broadwell_(microarchitecture)) | 10.10.0 | ^^ | ^^ | 0x0306D4(U/Y) |
| [Skylake](https://en.wikipedia.org/wiki/Skylake_(microarchitecture)) | 10.11.0 | ^^ | ^^ | 0x0506e3(H/S) 0x0406E3(U/Y) |
| [Kaby Lake](https://en.wikipedia.org/wiki/Kaby_Lake) | 10.12.4 | ^^ | ^^ | 0x0906E9(H/S/G) 0x0806E9(U/Y) |
| [Coffee Lake](https://en.wikipedia.org/wiki/Coffee_Lake) | 10.12.6 | ^^ | ^^ | 0x0906EA(S/H/E) 0x0806EA(U)|
| [Amber](https://en.wikipedia.org/wiki/Kaby_Lake#List_of_8th_generation_Amber_Lake_Y_processors), [Whiskey](https://en.wikipedia.org/wiki/Whiskey_Lake_(microarchitecture)), [Comet Lake](https://en.wikipedia.org/wiki/Comet_Lake_(microprocessor)) | 10.14.1 | ^^ | ^^ | 0x0806E0(U/Y) |
| [Comet Lake](https://en.wikipedia.org/wiki/Comet_Lake_(microprocessor)) | 10.15.4 | ^^ | ^^ | 0x0906E0(S/H)|
| [Ice Lake](https://en.wikipedia.org/wiki/Ice_Lake_(microprocessor)) | ^^ | ^^ | ^^ | 0x0706E5(U) |
| [Rocket Lake](https://en.wikipedia.org/wiki/Rocket_Lake) | ^^ | ^^ | Comet Lake CPUID 필요 | 0x0A0671 |
| [Tiger Lake](https://en.wikipedia.org/wiki/Tiger_Lake_(microprocessor)) | <span style="color:red"> N/A </span> | <span style="color:red"> N/A </span> | <span style="color:red"> Untested </span> | 0x0806C0(U) |

:::

::: details AMD CPU Limitations in macOS(macOS 내에서 AMD CPU 제한사항)

많은 macOS 의 기능들이 불행하게도 지원되지 않고, 많은 것들이 부분적으로 망가져있습니다. 후술내용들을 포함합니다. 

* AppleHV를 이용한 가상화 미지원
  
  - Vmware, Parallels, Docker, Android Studio 와 같은 것들이 안됩니다.
  
  - VirtualBox는 독자적인 방식을 사용하기에 유일하게 가능합니다.
  -  Vmware 10 과 Parallels 13.1.0 또한 지원은 하지만, 너무 오래되었기에 사용을 권장하지 않습니다.
  
* Adobe 미지원
  * 대부분의 Adobe의는 인텔의 방식에 맞춰져있기에, AMD CPU에서 돌리면 충돌이 일어납니다.
  * Raw Support와 같은 충돌을 일으키는 근본적인 기능들을 비활성화 할수 있습니다: [Adobe Fixes](https://gist.github.com/naveenkrdy/26760ac5135deed6d0bb8902f6ceb6bd)
  
* 32bit 미지원
  
  * 후술할 패치 커널이 지원하지 않습니다. [커스텀 커널](https://files.amd-osx.com/?dir=Kernels)을 이용해서 사용해볼순 있지만, imessage 지원이 안되며, 지원이 제공되지 않습니다.
  
* 안정성
  * Logic Pro 와 같은 오디오 관련 앱들이 제대로 동작하지 않습니다.
  * DaVinci Resolve 는 종종 일어나는 문제들이 있습니다.

:::

## GPU지원

GPU 지원은 시장에 매우 많은 GPU들이 존재하기에 훨씬 더 복잡하지만, 일반적으로는:

* AMD's GCN 기반 GPU들은 macOS 최신버전에서 지원됩니다.
  * AMD APU들은 지원되지 않습니다.
  * 폴라리스 시리즈의 AMD's [Lexa based cores](https://www.techpowerup.com/gpu-specs/amd-lexa.g806)도 지원되지 않습니다.
  * MSI 나비 유저 사용자들 문제: [Installer not working with 5700XT #901](https://github.com/acidanthera/bugtracker/issues/901)
    * macOS 11 (빅서)에서 해결되었습니다.
* Nvidia's GPU 지원은 복잡합니다:
  * [Maxwell(9XX)](https://en.wikipedia.org/wiki/GeForce_900_series) 과 [Pascal(10XX)](https://en.wikipedia.org/wiki/GeForce_10_series) GPU들은 macOS 10.13:하이시에라까지 사용가능합니다.
  * [Nvidia's Turing(20XX,](https://en.wikipedia.org/wiki/GeForce_20_series)[16XX)](https://en.wikipedia.org/wiki/GeForce_16_series) GPU들은 **어떠한 버전에서도 지원되지 않습니다.**
  * [Nvidia's Ampere(30XX)](https://en.wikipedia.org/wiki/GeForce_30_series) GPU들은 **어떠한 버전에서도 지원되지 않습니다.**
  * [Nvidia's Kepler(6XX,](https://en.wikipedia.org/wiki/GeForce_600_series)[7XX)](https://en.wikipedia.org/wiki/GeForce_700_series) GPU들은 macOS 11: 빅서 까지 지원됩니다.
* Intel's [GT2+ tier](https://en.wikipedia.org/wiki/Intel_Graphics_Technology) 시리즈 내장그래픽들은
  * 아이비브릿지부터 아이스레이크 내장그래픽지원은 이 안내를 통해 지원됩니다.
    * GMA  iGPUs 대한 정보를 알수있습니다: [GMA Patching](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/)
  * Note GT2 refers to the tier of iGPU, low-end GT1 iGPUs found on Pentiums, Celerons and Atoms are not supported in macOS

And an important note for **Laptops with discrete GPUs**:

* 90% of discrete GPUs will not work because they are wired in a configuration that macOS doesn't support (switchable graphics). With NVIDIA discrete GPUs, this is usually called Optimus. It is not possible to utilize these discrete GPUs for the internal display, so it is generally advised to disable them and power them off (will be covered later in this guide).
* However, in some cases, the discrete GPU powers any external outputs (HDMI, mini DisplayPort, etc.), which may or may not work; in the case that it will work, you will have to keep the card on and running.
* However, there are some laptops that rarely do not have switchable graphics, so the discrete card can be used (if supported by macOS), but the wiring and setup usually cause issues.

**For a full list of supported GPUs, see the [GPU Buyers Guide](https://dortania.github.io/GPU-Buyers-Guide/)**

::: details Intel GPU Support Chart

| GPU Generation | Initial support | Last supported version | Notes |
| :--- | :--- | :--- | :--- |
| [3rd Gen GMA](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Third_generation) | 10.4.1 | 10.7.5 | [Requires 32-bit kernel and patches](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/legacy-intel/) |
| [4th Gen GMA](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen4) | 10.5.0 | ^^ | ^^ |
| [Arrandale(HD Graphics)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen5) | 10.6.4 | 10.13.6 | Only LVDS is supported, eDP and external outputs are not |
| [Sandy Bridge(HD 3000)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen6) | 10.6.7 | ^^ | N/A |
| [Ivy Bridge(HD 4000)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen7) | 10.7.3 | 11.6.1 | ^^ |
| [Haswell(HD 4XXX, 5XXX)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen7) | 10.8.5 | <span style="color:green"> Current </span> | ^^ |
| [Broadwell(5XXX, 6XXX)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen8) | 10.10.0 | ^^ | ^^ |
| [Skylake(HD 5XX)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen9) | 10.11.0 | ^^ | ^^ |
| [Kaby Lake(HD 6XX)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen9) | 10.12.4 | ^^ | ^^ |
| [Coffee Lake(UHD 6XX)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen9) | 10.13.6 | ^^ | ^^ |
| [Comet Lake(UHD 6XX)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen9) | 10.15.4 | ^^ | ^^ |
| [Ice Lake(Gx)](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Gen11) | 10.15.4 | ^^ | Requires `-igfxcdc` and `-igfxdvmt` in boot-args |
| [Tiger Lake(Xe)](https://en.wikipedia.org/wiki/Intel_Xe) | <span style="color:red"> N/A </span> | <span style="color:red"> N/A </span> | <span style="color:red"> No drivers available </span> |
| [Rocket Lake](https://en.wikipedia.org/wiki/Rocket_Lake) | <span style="color:red"> N/A </span> | <span style="color:red"> N/A </span> | <span style="color:red"> No drivers available </span> |

:::

::: details AMD GPU Support Chart

| GPU Generation | Initial support | Last supported version | Notes |
| :--- | :--- | :--- | :--- |
| [X800](https://en.wikipedia.org/wiki/Radeon_X800_series) | 10.3.x | 10.7.5 | Requires 32 bit kernel |
| [X1000](https://en.wikipedia.org/wiki/Radeon_X1000_series) | 10.4.x | ^^ | N/A |
| [TeraScale](https://en.wikipedia.org/wiki/TeraScale_(microarchitecture)) | 10.4.x | 10.13.6 | ^^ |
| [TeraScale 2/3](https://en.wikipedia.org/wiki/TeraScale_(microarchitecture)) | 10.6.x | ^^ | ^^ |
| [GCN 1](https://en.wikipedia.org/wiki/Graphics_Core_Next) | 10.8.3 | <span style="color:green"> Current </span> | ^^ |
| [GCN 2/3](https://en.wikipedia.org/wiki/Graphics_Core_Next) | 10.10.x | ^^ | ^^ |
| [Polaris 10](https://en.wikipedia.org/wiki/Radeon_RX_400_series), [20](https://en.wikipedia.org/wiki/Radeon_RX_500_series) | 10.12.1 | ^^ | ^^ |
| [Vega 10](https://en.wikipedia.org/wiki/Radeon_RX_Vega_series) | 10.12.6 | ^^ | ^^ |
| [Vega 20](https://en.wikipedia.org/wiki/Radeon_RX_Vega_series) | 10.14.5 | ^^ | ^^ |
| [Navi 10](https://en.wikipedia.org/wiki/Radeon_RX_5000_series) | 10.15.1 | ^^ | Requires `agdpmod=pikera` in boot-args |
| [Navi 20](https://en.wikipedia.org/wiki/Radeon_RX_6000_series) | 11.4 | ^^ | <span style="color:yellow"> Currently only some Navi 21 models are working </span> |

:::

::: details Nvidia GPU Support Chart

| GPU Generation | Initial support | Last supported version | Notes |
| :--- | :--- | :--- | :--- |
| [GeForce 6](https://en.wikipedia.org/wiki/GeForce_6_series) | 10.2.x | 10.7.5 | Requires 32 bit kernel and [NVCAP patching](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/nvidia-patching/) |
| [GeForce 7](https://en.wikipedia.org/wiki/GeForce_7_series) | 10.4.x | ^^ | [Requires NVCAP patching](https://dortania.github.io/OpenCore-Post-Install/gpu-patching/nvidia-patching/) |
| [Tesla](https://en.wikipedia.org/wiki/Tesla_(microarchitecture)) | 10.4.x | 10.13.6 | ^^ |
| [Tesla v2](https://en.wikipedia.org/wiki/Tesla_(microarchitecture)#Tesla_2.0) | 10.5.x | ^^ | ^^ |
| [Fermi](https://en.wikipedia.org/wiki/Fermi_(microarchitecture)) | 10.7.x | ^^ | ^^ |
| [Kepler](https://en.wikipedia.org/wiki/Kepler_(microarchitecture)) | 10.7.x | 11.6.1 | N/A |
| [Kepler v2](https://en.wikipedia.org/wiki/Kepler_(microarchitecture)) | 10.8.x | ^^ | ^^ |
| [Maxwell](https://en.wikipedia.org/wiki/Maxwell_(microarchitecture)) | 10.10.x | 10.13.6 | [Requires NVIDIA Web Drivers](https://www.nvidia.com/download/driverResults.aspx/149652/) |
| [Pascal](https://en.wikipedia.org/wiki/Pascal_(microarchitecture)) | 10.12.4 | ^^ | ^^ |
| [Turing](https://en.wikipedia.org/wiki/Turing_(microarchitecture)) | <span style="color:red"> N/A </span> | <span style="color:red"> N/A </span> | <span style="color:red"> No drivers available </span> |
| [Ampere](https://en.wikipedia.org/wiki/Ampere_(microarchitecture)) | ^^ | ^^ | ^^ |

:::

## Motherboard Support

For the most part, all motherboards are supported as long as the CPU is. Previously, B550 boards had issues:

* [~~AMD's B550 boards~~](https://en.wikipedia.org/wiki/List_of_AMD_chipsets)

However thanks to recent developments, B550 boards are now bootable with the addition of [SSDT-CPUR](https://github.com/naveenkrdy/Misc/blob/master/SSDTs/SSDT-CPUR.dsl). More info will be provided in both [Gathering Files](./ktext.md) and [Zen's config.plist section](./AMD/zen.md)

## Storage Support

For the most part, all SATA based drives are supported and the majority of NVMe drives as well. There are only a few exceptions:

* **Samsung PM981, PM991 and Micron 2200S NVMe SSDs**
  * These SSDs are not compatible out of the box (causing kernel panics) and therefore require [NVMeFix.kext](https://github.com/acidanthera/NVMeFix/releases) to fix these kernel panics. Note that these drives may still cause boot issues even with NVMeFix.kext.
  * On a related note, Samsung 970 EVO Plus NVMe SSDs also had the same problem but it was fixed in a firmware update; get the update (Windows via Samsung Magician or bootable ISO) [here](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/).
  * Also to note, laptops that use [Intel Optane Memory](https://www.intel.com/content/www/us/en/architecture-and-technology/optane-memory.html) or [Micron 3D XPoint](https://www.micron.com/products/advanced-solutions/3d-xpoint-technology) for HDD acceleration are unsupported in macOS. Some users have reported success in Catalina with even read and write support but we highly recommend removing the drive to prevent any potential boot issues.
  
* **Intel 600p**
  * While not unbootable, please be aware this model can cause numerous problems. [Any fix for Intel 600p NVMe Drive? #1286](https://github.com/acidanthera/bugtracker/issues/1286)

## Wired Networking

Virtually all wired network adapters have some form of support in macOS, either by the built-in drivers or community made kexts. The main exceptions:

* Intel I225 2.5Gb NIC
  * Found on high-end Desktop Comet Lake boards
  * Workarounds are possible: [Source](https://www.hackintosh-forum.de/forum/thread/48568-i9-10900k-gigabyte-z490-vision-d-er-läuft/?postID=606059#post606059) and [Example](config.plist/comet-lake.md#deviceproperties)
* Intel I350 1Gb server NIC
  * Normally found on Intel and Supermicro server boards of various generations
  * [Workaround](config-HEDT/ivy-bridge-e.md#deviceproperties)
* Intel 10Gb server NICs
  * Workarounds are possible for [X520 and X540 chipsets](https://www.tonymacx86.com/threads/how-to-build-your-own-imac-pro-successful-build-extended-guide.229353/)
* Mellanox and Qlogic server NICs

## Wireless Networking

Most WiFi cards that come with laptops are not supported as they are usually Intel/Qualcomm. If you are lucky, you may have a supported Atheros card, but support only runs up to High Sierra.

The best option is getting a supported Broadcom card; see the [WiFi Buyer's Guide](https://dortania.github.io/Wireless-Buyers-Guide/) for recommendations.

Note: Intel WiFi is unofficially (3rd party driver) supported on macOS, check [WiFi Buyer's Guide](https://dortania.github.io/Wireless-Buyers-Guide/) for more information about the drivers and supported cards.

## Miscellaneous

* **Fingerprint sensors**
  * There is currently no way to emulate the Touch ID sensor, so fingerprint sensors will not work.
* **Windows Hello Face Recognition**
  * Some laptops come with WHFR that is I2C connected (and used through your iGPU), those will not work.
  * Some laptops come with WHFR that is USB connected, if you're lucky, you may get camera functionality, but nothing else.
* **Intel Smart Sound Technology**
  * Laptops with Intel SST will not have anything connected through them (usually internal mic) work, as it is not supported. You can check with Device Manager on Windows.
* **Headphone Jack Combo**
  * Some laptops with a combo headphone jack may not get audio input through them and will have to either use the built-in microphone or an external audio input device through USB.
* **Thunderbolt USB-C ports**
  * (Hackintosh) Thunderbolt support is currently still iffy in macOS, even more so with Alpine Ridge controllers, which most current laptops have. There have been attempts to keep the controller powered on, which allows Thunderbolt and USB-C hotplug to work, but it comes at the cost of kernel panics and/or USB-C breaking after sleep. If you want to use the USB-C side of the port and be able to sleep, you must plug it in at boot and keep it plugged in.
  * Note: This does not apply to USB-C only ports - only Thunderbolt 3 and USB-C combined ports.
  * Disabling Thunderbolt in the BIOS will also resolve this.
