# Setup_OS

## 서두
* 오픈소스 툴체인을 완성하기 위해서는 리눅스를 필수적으로 사용해야 한다고 보는게 편합니다.
* 그러나, 회사의 업무환경 및 3D CAD 소프트웨어가 윈도우즈 환경에서만 가능한 경우가 많기 때문에, 업무용 PC를 완전히 리눅스로 바꾸는 것은 현실적으로 어렵습니다.
* 대신 기존에 사용하는 윈도우PC에 VirtualBox를 사용하여 가상 리눅스 환경을 만들어 사용하는 것이 현실적이라고 사료됩니다.  물론 별도의 전용 리눅스PC를 마련해서 해석 전용으로 운용할 수 있다면 더 좋을 것입니다.
* 본 설명서에서는 일단 VirtualBox 가상머신을 사용하는 경우를 상정하겠습니다.

## PC의 사양
* 일단 RAM 용량은 무조건 많이 확보하는 것이 좋겠습니다.  (최소 8GB 이상)
* 그래픽카드는 물론 3D 작업을 위해 NVIDIA Quadro 류의 좋은 제품을 사용하는 것이 좋겠습니다.  그러나 VirtualBox 가상머신에서 돌아가는 리눅스 환경은 그래픽카드와 전연 관련이 없습니다.  VirtualBox는 그래픽카드까지도 가상화된 것이기 때문에 실제 달려 있는 그래픽카드의 자원을 활용하지는 못하기 때문입니다.
* 그러나 가상머신이 아니고, 전용으로 리눅스를 통째로 설치해서 사용할 경우에는 가급적 그래픽카드 드라이버가 큰 문제없이 돌아가는 Intel 내장 그래픽이나, 또는 NVIDIA 계열 제품을 사용하면 최대한의 성능을 끌어낼 수 있습니다.
* CPU는 당연히 코어 숫자가 많고 퍼포먼스가 좋을수록 더 좋습니다.  FEM 해석을 실시할 때 코어를 더 할당할 수 있으면 계산시간을 크게 줄일 수 있습니다.  따라서 8개의 하이퍼스레딩 코어가 제공되는 Intel i7 CPU가 가장 좋겠습니다.  물론 돈이 많다면 2개 이상의 CPU를 넣는 전용 워크스테이션 기계가 있다면 좋겠지만 꼭 그런식으로 과잉 투자할 필요는 없다고 생각됩니다.  PC라는게 몇년만 지나면 새걸로 바꿔줘야 하는 일종의 소모품이기 때문에, 차라리 가장 많이들 사용하는 무난한 체급이 투자 대비 효과성을 가장 높이 볼 수 있다고 생각됩니다.

## 윈도우 환경
* 아직은 회사에서 보통 윈도우7 내지는 윈도우8.1 정도를 사용할 것입니다. 물론 윈도우10이라도 별 상관 없다고 생각됩니다.
* 리눅스 가상머신을 위해 하드디스크 공간을 20GB 정도 확보하고 있는지만 확인합시다.
* 인터넷에는 당연히 연결된 상태여야겠죠.

## 리눅스 배포판 선택
* 보통 리눅스를 처음 사용한다고 하면, Ubuntu, Mint 같은 배포판들이 추천됩니다.  그러나 이것들의 UI 환경은 너무 무거운 감이 있기 때문에 쓸데없이 PC의 자원을 낭비하는 것 같습니다.  리눅스OS 자체적으로 사용하는 자원은 최소한으로 쥐어짜고 메모리 용량을 최대한 활용하는 것이 좋겠습니다.
* 따라서 본 가이드에서는 Ubuntu Server 배포판(그래픽 환경이 없는 것)을 기반으로, 그 위에 X윈도우 환경을 직접 쌓아올려주는 방식을 사용하도록 하겠습니다.  윈도우 매니저는 가장 가벼운 것 중의 하나인 OpenBox를 사용합니다.
* 이렇게 구성을 하면, 삽질을 좀 하는 대신에 리눅스 시스템을 좀 더 잘 이해할 수 있고, 또 리눅스 부팅후 점유하는 메모리가 겨우 200~300MB 정도 수준에 불과하기 때문에 굉장히 가볍고 빠릿빠릿하며 안정적인 시스템을 얻을 수 있습니다.
* 설치하는 리눅스는 반드시 64bit 버전으로 합니다.  32bit 버전의 배포판을 사용하면 FEM 해석용 소프트웨어가 제대로 동작하지 않게 됩니다.  (오픈소스 해석 소프트웨어가 주로 사용하는 포트란 라이브러리 중에서 32bit로 컴파일된 것이 제공되지 않는 경우가 많습니다.)

## VirtualBox 다운로드 및 설치
* https://www.virtualbox.org/ 으로 가서 다운로드 받은 후, 윈도우PC에 설치합니다.

## Ubuntu Server 다운로드
* http://www.ubuntu.com/download/server 에서 Ubuntu Server를 다운로드 받습니다.
* 2015.11.25일 현재, 14.04.3 LTS 버전과 15.10 버전이 제공되고 있는데, .10 버전은 지원기간이 짧기 때문에 14.04 버전을 선택해서 다운로드 받는 것이 좋겠습니다.  나중(2016년 중반)에 16.04 버전이 나오면 그때 업그레이드를 하거나 하면 될 것입니다.
* X윈도우 부분이 빠진 서버 운용체제이기 때문에, 다운로드 용량은 600MB 미만으로 작은 편입니다.  파일은 .iso로 CD이미지 파일로 제공됩니다.
* 이제 .iso 파일을 받았으면 이것을 VirtualBox 가상머신을 만들어주고 거기에 설치하면 됩니다.

## VirtualBox 가상머신 준비
* VirtualBox를 일단 실행시키고, '파일-환경설정-팝업창뜨면-일반'메뉴로 들어갑니다.  여기서 가상머신 파일의 경로를 확인하고 원하는대로 정해 줍니다.  나머지는 건드릴 필요 없습니다.
* 그리고 이제 '새로만들기' 아이콘을 눌러서 새로운 가상머신을 생성해 줍니다.  '이름'은 'UbuntuBang'정도로 적당히 정해주면 되고, '종류'는 'Linux'로, '버전'은 'Ubuntu(64bit)'로 해 줍니다.
* 이제 '다음' 버튼을 눌러서 넘어가면 메모리 용량을 정해주는 팝업창이 뜹니다.  메모리는 일단 2048MB로 잡아줍니다.  나중에 사용하다가 메모리가 부족하다면 설정을 바꿔주기만 하면 됩니다.
* 이제 '다음' 버튼을 눌러서 넘어가면 하드디스크를 정해주는 팝업창이 뜹니다.  '지금 새 가상 하드디스크 만들기'를 체크해줍니다.
* '다음'으로 넘어가서 하드디스 파일 종류를 'VDI'로 정해줍니다.
* '다음'으로 넘어가서 '고정 크기'로 정해줍니다.  '동적 할당'을 선택해도 무방하겠지만 아무래도 퍼포먼스가 좀 떨어진다고 합니다.
* '다음'으로 넘어가서 파일 위치가 원하는대로 잘 잡혀있는지 확인하고, 파일 크기를 정해줍니다.  본 가이드를 통해서 구성되는 시스템이 잡아먹는 용량은 별로 안 큽니다.  그러나 너무 작게 잡아놓으면 나중에 후회할 수 있으므로, 20GB 정도 잡아주는 것이 좋겠습니다.  충분히 여유있게 잡아줘도 좋긴 한데, 실제 작업한 데이타는 윈도우시스템 쪽과 공유해서 다룰 수 있도록 해 주기 위해 공유할 것이므로, 리눅스 쪽에는 데이타 저장 공간을 별로 고려할 필요는 없다고 생각됩니다.
* '만들기' 버튼을 누르면 시간이 좀 소요된 후 파일이 생성됩니다.
* 그럼 VirtualBox에 새로 만든 가상머신을 선택할 수 있습니다.  마우스를 한 번 눌러줘서 선택한 상태로 한 후, '설정' 아이콘을 눌러서 이 가상머신의 사양을 좀 만져주도록 합시다.
* '일반-고급'으로 들어가서, '클립보드 공유', '드래그 엔 드롭'을 모두 '양방향'으로 설정해 줍니다.  이렇게 하면 윈도우와 리눅스 양쪽으로 클립보드 복사 같은걸 할 수 있게 됩니다.  물론 완벽하지는 않습니다(VirtualBox 버그).  그래도 아쉬운대로 일단 되는게 어딥니까.
* 그리고 '시스템-마더보드'로 들어가서, 부팅순서 카테고리에서 '플로피디스크'는 불필요하므로 Uncheck 합니다.
* '시스템-프로세서'로 들어가서, '프로세서 개수'는 일단 2개만 잡아줍니다.  'PAE/NX 사용하기'라는 것도 체크해 주면 나쁠 것 없겠습니다.
* '디스플레이-화면'으로 들어가서, '비디오 메모리'는 128MB의 최대로 잡아줍니다.  '3차원 가속 사용하기'는 체크해도 되긴 한데, 일단은 체크하지 말도록 합니다.  3차원 가속 기능이 아직 완전하지는 않아서, 일부 어플리케이션이 제대로 동작하지 않는 경우가 있습니다(LightTable등).  '2차원 비디오 가속' 기능은 아예 Uncheck 합니다.  역시 버그 때문에 제대로 동작하지 않습니다.  없는 기능으로 생각하는게 마음 편합니다.
* '저장소' 메뉴로 들어갑니다.  광학드라이브를 누르면 우측에 속성을 정해줄 수 있습니다.  'IDE 세컨더리 마스터'라는 문구 옆에 CD모양 아이콘을 눌러줍니다.  여기서 '가상 광학 디스크 파일 선택'을 눌러주고, 아까 다운로드 받은 Ubuntu Server의 .iso 파일을 선택해 줍니다.  즉 가상머신의 가상CD롬 드라이브에 Ubuntu Server 설치 CD를 미리 넣어두는 것과 같은 이야기죠.  앞서 부팅순서에서 CD롬이 맨 먼저 부팅되도록 되어 있으므로, 이렇게 해 두고 시작을 하면 가상CD롬 드라이브의 Ubuntu Server 설치 CD로 부팅이 되면서 설치가 이루어질 수 있도록 된다는 것입니다.
* '네트워크-어댑터1'으로 들어가서, '브리지 어댑터'를 선택합니다.  브리지 어댑터를 선택할 경우, 가상머신상의 리눅스에서 어떤 웹서버 같은 것을 동작시켜주면 외부에서 접근이 가능해지기 때문입니다.  'NAT'를 선택하면 이것이 안됩니다.
* '공유폴더'는 여기서 설정해 주고 들어가도 되긴 하는데, 이렇게 할 경우 리눅스 쪽에서 접근할 때 root 권한이 있어야만 사용가능해 집니다.  차라리 이것을 사용하지 않고 다른 방법으로 SMB 서비스 접근하는 쪽이 나을 수도 있습니다.  일단은 체크하지 말고 그냥 둡니다.
* '확인'하고 설정을 완료합니다.


## Ubuntu Server 설치
* 이제 VirtualBox에서 '시작' 아이콘을 누르면 가상머신이 작동됩니다.  부팅되면서 앞서 설정한대로 Ubuntu Server 가상 설치 CD가 로딩되면서 부팅됩니다.  이후부터는 Ubuntu Server 설치 프로세스로 들어가게 됩니다.
* 'Language'는 'English'로 선택합니다.  만일 여기서 '한국어'를 선택할 경우에는, 터미널에서 나오는 메시지들 중에서 한국어로 나오는 것들이 한글 폰트 문제로 깨져서 나올 수 있어서 보기가 좋지 않습니다.  한글 환경 설정은 설치 후에 따로 하는 것이 낫습니다.
* 'Install Ubuntu Server'를 선택해서 설치를 시작합시다.
* 다시 'Language' 선택 화면이 나오는데, 역시 'English'로 합시다.
* 'Select your location'은 'other - Asia - Korea, Republic of'로 선택해 줍니다.
* 'Configure locales'는 일단 'United States'로 해줍니다.  나중에 한글환경으로 다시 셋팅을 바꿔줄 때 한국 로케일로 바꿀 겁니다.
* 'Configure the keyboard'에서 일단 'Yes'하고 시키는대로 따라해 줍니다.
* 이제 설치준비가 시작됩니다.  기다립니다.
* 'Configure the network'에서 Hostname을 정해줍니다.  가능한 짧은 이름이 좋겠습니다.  편의상 ubuntubang으로 정해줘 봅니다.
* 'Set up users and passwords'에서 관리자 이름을 정해줍니다.  편의상 Full name을 dong으로, Username 역시 dong으로 해줍니다.  password는 알아서 적당히 정해줍니다.  8글자 미만이면 안좋다고 메시지가 나오는데 무시해도 됩니다.  그리고 넘어가면 홈 디렉토리를 암호화 할지 묻는데, 편의상 역시 암호화는 안 하도록 합니다.
* 'Configure the clock'에서는 현재 위치를 알아서 잘 잡았을테니(Asia/Seoul) Yes하고 넘어가 줍니다.
* 'Partition disks' 설정의 경우는, 가상머신상에 올리는 경우이므로 굳이 파티션을 인위적으로 나눌 필요가 없습니다.  따라서 'Guided - use entire disk and set up LVM'을 선택합니다.  LVM이라는 것은 디스크 관리를 좀 더 잘 해 주는 RAID 같은 것에 비교될 수 있는 관리자 같은 것 같습니다.  아무튼 죽죽 넘어갑시다.  파티션 역시 그냥 나오는대로 따라가면 됩니다.
* 이제 시스템 설치가 시작됩니다.  다 될때까지 기다립니다.
* 중간에 'Configure the package manager'가 나오는데, 여기서 HTTP proxy를 정하라고 나오는데, 프록시는 안 쓸 것이므로 그냥 넘어갑니다.
* 또 중간에 'Configuring tasksel'이라는게 나오는데, 'Install security updates automatically'를 해 줍니다.
* 'Software selection'에서는 아무것도 선택하지 말고 continue 합니다.  필요한게 있으면 나중에 별도로 깔면 됩니다.
* 'Install GRUB bootloader'가 나오면 yes 해 줍니다.
* 'Finish the installation'에서 넘어가면 설치가 완료되고 재시작됩니다.


## Ubuntu Server 최초 실행
* 이제 재시작되고 로그인 화면이 나옵니다.  아까 정해준 username 및 password를 쳐서 로그인 합니다.
* 로그인이 이상없이 되었으면 최초로 다음 명령어를 쳐 봅시다.  현재 위치한 홈 디렉토리에서 파일 리스트를 보여주는 ls 명령어 입니다.  -a 라는 옵션은 숨겨진 파일까지 다 보여주라는 의미입니다.
```bash
ls -a
```
* 나오는 목록을 보면, '.bashrc'같은 이름들이 보입니다.  두문자로 '.'이 붙어 있는데, 이것은 리눅스에서는 숨긴 파일로 취급됩니다.
* 그럼 '.bashrc'라는 파일의 내용을 보려면 간단히 다음 명령을 쳐 봅니다.
```bash
more .bashrc
```
* 그러면 '.bashrc'라는 설정파일의 내용들이 보입니다.  스페이스바를 누르면 다음 페이지로 죽죽 넘어가집니다.  뭔 내용인지는 모르겠지만, bash 쉘 즉 현재의 명령환경을 규정하는 각종 설정들이 정해져 있음을 볼 수 있습니다.
* 이제 시스템을 업데이트 해 봅니다.
* 일단 기본적으로 다음 명령을 기계적으로 쳐 봅니다.
```bash
sudo apt-get update
```
* 그러면 패스워드를 넣으라고 나옵니다.  패스워드 쳐 줍니다.  그럼 뭔가 목록이 주루룩 나오면서 갱신되는 것을 볼 수 있습니다.
* 'sudo'는 슈퍼유저 즉 root 권한으로 다음에 나오는 명령을 실행하라는 뜻입니다.  때문에 패스워드가 요구된 것입니다.
* 'apt-get'은 데비안 또는 우분투 계열 배포판 리눅스의 패키지 관리자 유틸리티 명령어입니다.  온라인상으로 원격 제공되는 각종 패키지들의 목록을 갱신하거나 그것을 다운로드 받고 시스템에 설치하는 등등의 일을 해 줍니다.
* 'update' 옵션은 원격 패키지 저장소의 목록을 갱신하라는 것입니다.  그래서 목록이 주루룩 나오면서 최신 정보로 갱신되었습니다.
* 이제 실제로 갱신된 정보를 반영해서 시스템을 업그레이드 하면 됩니다.  다음 명령을 쳐 줍니다.
```bash
sudo apt-get upgrade
```
* 이번에는 'sudo'가 들어갔는데도 패스워드를 요구하지 않습니다.  왜냐면 조금 전에 이미 한 번 쳐 넣어 줬기 때문에 기억하는 것입니다.  시간이 좀 지나면 이게 풀려서 패스워드를 다시 요구하게 됩니다.  편의성과 보안성을 절충한 셋팅입니다.
* 아무튼 나오는 메시지를 대충 보면, 어떤 패키지들을 업그레이드 할 것인지에 관한 목록이 나오고, 또 총 몇 메가바이트의 용량을 다운로드 받을 것인지 등에 관한 정보를 보여줍니다.  계속할지 묻는데 당연히 y를 쳐 줍니다.
* 이제 다운로드가 시작되고, 이후에 자동으로 시스템에 설치가 됩니다.  끝날 때 까지 잠시 기다립니다.
* 이제 최신 시스템으로 업그레이드가 완료되었습니다.  이상 해 본 것 처럼, `sudo apt-get update` 및 `sudo apt-get upgrade` 명령은 심심하면 쳐 넣어 주는 습관을 들여 주면 됩니다. 각종 패키지들의 업데이트는 상시적으로 이루어지기 때문에 자주 해 주는 것이 좋습니다.  물론 이걸 자동화해둬도 좋겠지만 터미널 명령에 익숙해지기 위해서 직접 수동으로 쳐넣어주는 것이 학습효과가 좋습니다.

## 시스템 둘러보기
* 현재의 환경은 Bash쉘 환경이므로, 일일이 명령어를 쳐넣어가면서 뭔가를 하기에는 상당히 불편합니다.  그래서 좀 편해지게 해 줄 수 있는 간단한 유틸리티를 하나 설치해 봅시다.
```bash
sudo apt-get install mc
```
* 위 명령에서 'install'은 새로운 패키지를 설치하라는 옵션입니다.  'mc'라는 패키지를 설치하겠다는 것입니다.
* 'mc'는 Midnight Commander를 말합니다.  설치 한 후, `mc`라고 명령을 쳐 봅니다.
* 옛날 DOS 시절에 많은 사람들이 애용하던 MDIR이나 Norton Commander와 비슷한 것입니다.  이걸로 시스템 전체의 여러 디렉토리를 돌아다니면서 활용하면 좀 편합니다.
* 루트 디렉토리 '/'까지 올라가서, 그 밑의 하위 디렉토리들을 보면 대충 다음과 같이 분류됩니다.
* '/bin'은 시스템의 기본 명령어들이 들어가 있습니다.  아까 써 봤던 ls 라던가 more 같은 것들도 당연히 여기에 들어 있습니다.  Path가 다 잡혀 있기때문에 어느 위치에서든지 다 명령어가 통합니다.
* '/boot'에는 리눅스 커널 및 부팅매니저인 GRUB 관련한 것이 들어가 있습니다.  리눅스 커널을 직접 바꿔가면서 노는데 관심이 없다면 그냥 그런게 있구나 하고 관심을 끕시다.
* '/dev'에는 시스템의 하드웨어들이 파일로 표현되어 있습니다.  유닉스 계열 운영체제는 모든 것을 파일로 취급하는 사상이 있다 보니, CPU라던가 Disk 같은 하드웨어들도 전부 파일로 표현해서 마치 파일처럼 다루도록 구성되어 있어서 그렇습니다.  역시 아하 이런 식이구나 하고 이해만 하고 넘어갑시다.
* '/etc'에는 시스템의 기본 명령은 아니지만 핵심적인 서비스를 구성하는 명령들이 들어가 있습니다.  예를 들어, 아까 시스템 업그레이드를 해 주는 패키지 관리자인 'apt-get' 같은 것도 'apt' 디렉토리 안에 들어가 있습니다.  그 외에도 X11(x윈도우), apm 등이 보입니다.
* '/home'은 사용자 홈 디렉토리 입니다.  현재는 dong 이라는 사용자 1명 밖에 계정이 없으므로, 안에 'dong'이라는 디렉토리만 있습니다.  시스템 부팅후 dong으로 로그인하면 '/home/dong' 위치에서 시작하게 됩니다.  이 안에 있는 파일들만 해당 사용자가 지웠다 썼다 가능하며, 그 위의 나머지 모든 디렉토리나 폴더들은 보기만 되고 쓰기는 허용되지 않습니다.  그때는 'sudo' 등으로 권한을 획득해야 합니다.
* '/lib', '/lib64'는 공용으로 갖다쓰는 라이브러리들이 들어있습니다.
* 'lost+found'는 나도 잘 모르겠네요. ㅋㅋ
* '/media'는 외부의 저장장치를 로딩하면 이곳에 디렉토리가 생기면서 들어가 볼 수 있게 링크가 됩니다.  CD롬이라던가, 네트워크 드라이브 같은 것들.
* '/mnt'는 외부 드라이브 마운트 할 때 잡히는 것입니다.
* '/opt'는 우분투 시스템과는 별도의 외부 어플리케이션을 설치하도록 만들어둔 장소입니다.  나중에 Google Chrome 같은 것을 설치하면 이곳에 설치가 됩니다.
* '/proc'은 현재 시스템에서 돌아가고 있는 프로세스들을 파일처럼 생성해서 자동을 관리하는 장소입니다.  역시 사용자가 건드릴 일은 없겠습니다.
* '/root'는, 별도의 사용자 계정이 아니고 root 계정을 위한 홈 디렉토리입니다.  다만 Ubuntu 시스템은 root 계정 로그인이 디폴트로 막아놨기 때문에 이 장소는 거의 건드릴 일은 없겠습니다.
* '/usr'는 일반적인 응용 소프트웨어들을 위한 장소입니다.  일반적인 소프트웨어들은 거의 다 이곳으로 설치가 됩니다.
* '/var'은 시스템 운용에 필요한 변수들(Variable) 관련한 장소인 것 같은데 역시 거의 건드릴 일은 없습니다.
* 기타 디렉토리들의 역할은 생략합니다.
* 아무튼 Ubuntu는 이렇게 시스템 디렉토리가 정해져서 셋팅되어 있습니다.  우분투가 데비안에서 파생되었기 때문에 데비안 배포판 역시 큰 차이는 아직 없습니다.  다만 데비안과 다른 계열인 레드헷 계열(CentOS) 라던가 수세리눅스 같은 것들은 이와 좀 다른 디렉토리 구조를 가지고 있습니다.  그러나 구성이 여러모로 다르더라도 근본적인 차이는 없습니다.
* 아무튼 시스템 대충 파악해 봤으니, mc는 종료합니다.  f10 키를 눌러서 Quit을 하면 됩니다.







## X윈도우 구성

* 일단 예의상 시스템 업그레이드를 해 줍니다.
```
sudo apt-get update
sudo apt-get upgrade
```

* Xorg 그래픽 서버 패키지를 설치합니다.  이것의 역할은 리눅스에 GUI 환경을 조성해 주는 것입니다.  Xorg 말고도 여러가지 있긴 한데(Xfree86,Wayland,Mir등), 이게 가장 전통적으로 안정화되어 있고 무난합니다.
```
sudo apt-get install xorg
```

* Openbox 그래픽 매니저를 설치합니다.  그래픽 서버 위에서 실제 화면에 뿌려지는 GUI를 통제하는 것입니다.  역시 다른것들(GNOME,Awesome등)이 많이 있지만, Openbox는 가장 단순하면서도 이해하기가 쉽습니다.
```
sudo apt-get install openbox
```

* 오픈박스 메뉴(obmenu) 유틸리티를 설치합니다.  이걸 설치해 주면, 바탕화면에서 마우스 오른쪽 버튼을 누르면 나타는 메뉴(윈도우의 '시작버튼'과 같은 것)를 쉽게 편집해 줄 수 있습니다.
```
sudo apt-get install obmenu
```

* Appearance 설정 유틸리티를 설치합니다.  여기서는 LXDE 환경용으로 사용되는 것을 가져다 씁니다.  이것의 역할은, GUI 화면에 보이는 작업창들의 테마를 변경할 수 있게 해 주는 것입니다.  다른걸 써도 되는데 이게 간단해서 다루기가 좀 나은 것 같습니다.  GTK+ 기반입니다.
```
sudo apt-get install lxappearance
```

* X Composer Manager 유틸리티를 설치합니다.  이것의 역할은, GUI 작업창의 테두리에 그림자 효과를 주거나 또는 터미널 배경화면을 반투명하게 하거나 하는 효과를 줄 수 있도록 해 줍니다.  이것 말고 Compiz 같은 것들도 있는데, 그것 보다 이게 훨씬 가볍고 3D 가속이 지원되지 않아도 작동이 되기 때문에 이걸 사용합니다.
```
sudo apt-get install xcompmgr
```

* 배경화면 변경 유틸(Nitrogen)을 설치합니다.  이것의 역할은, 배경화면에 원하는 그림을 넣거나 색깔을 바꿀 수 있게 해 주는 것입니다.
```
sudo apt-get install nitrogen
```

* Tint2 태스크바를 설치합니다.  이것 말고 Plank Dock 같은 것도 있고 좋은 것들이 많이 있는데, 그중에 이 Tint2가 가장 심플합니다.  디자인은 촌스럽지만... 일단 이걸 사용해보다가 나중에 좋은 걸로 바꾸면 됩니다.
```
sudo apt-get install tint2
```

* NumLockX 설치 (키보드 숫자판을 기본적으로 활성해 해 주는 유틸리티)
```
sudo apt-get install numlockx
```
설정을 완전하게 해 주려면, 편집기로 autostart 파일에 `numlockx on &` 구문을 추가해 주면 됩니다.


* LightDM : 그래픽에서 로그인을 바로 하도록 해 주는 것입니다.  이것의 설치는 생략합니다.  시스템을 시작하고 Bash 상태로 로그인 한 다음, `startx`로 직접 X윈도우를 시작하는게 오히려 더 편한 것 같습니다.

* xscreensaver 스크린세이버 : 스크린세이버를 사용하는 것을 좋아하지 않으므로 설치는 생략합니다.  필요한 분은 `apt-get`으로 설치하시면 되고, autostart 파일에 `xscreensaver -no-splash &` 구문을 추가해 주면 됩니다.




## X윈도우의 기본적인 환경 셋팅

* 일단 아래의 명령을 쳐서 X윈도우를 최초로 시작해 봅니다.
```
startx
```

* 그러면 어두운 회색 그래픽 화면에 마우스 아이콘이 덩그러니 놓여있는 것을 볼 수 있습니다.  이상없이 실행된 것입니다.  여기서 마우스 오른쪽 버튼을 눌러보면 obmenu가 뜹니다.  나오는 obmenu 중에서 ObConf를 선택합니다.

* 그러면 기본적인 테마를 고르거나 뭐 여러가지 건드려 볼 수 있습니다.

* 그런데, 현재 화면 해상도가 낮아서 ObConf의 창이 너무 커서 다 보이지가 않습니다.  따라서, 창 아래쪽 어딘가에 있을 'Ok' 버튼을 찾을수가 없을텐데, Tab 키를 적당히 쳐서 반드시 Ok로 빠져나옵니다.  이렇게 해야 Openbox 설정파일이 `~/.config/openbox/rc.xml`으로 만들어 집니다.

* 아무튼 X윈도우가 이상없이 잘 실행되는 것이 확인되었으므로, X윈도우를 종료해 봅시다.  마우스 오른쪽 버튼 눌러서 나오는 메뉴 중에서 'Exit'를 선택해서 종료합니다.


* 이제 다시 돌아온 텍스트 명령 모드에서, 홈 디렉토리의 파일 목록을 확인해 봅시다.
```
ls -a
```

* 나오는 목록 중에서 파란색 글씨로 된 것은 디렉토리 입니다.  이 중에서 '.config' 디렉토리가 생겼는지 확인해 봅시다.  최초로 `startx` 명령을 줘서 X윈도우를 실행했을 때 이 폴더가 자동적으로 생성되었을 것입니다.


* 이제 앞서 설치한 기본적인 유틸리티들이 X윈도우 시작해서 OpenBox가 작동할 때 자동으로 로딩되도록 설정파일을 편집해 줍니다.  아래의 명령을 쳐서 nano 편집기로 들어갑니다.
```
nano ~/.config/openbox/autostart
```

* 그리고 아래의 내용을 써 넣어줍니다.
```
xcompmgr &
nitrogen --restore &
tint2 &
conky &
```

* 이 autostart라는 파일은, OpenBox가 시작할 때 자동으로 실행할 명령들을 적어주는 배치파일 같은 것입니다.  배경화면을 잡아주는 nitrogen과, 태스크바인 tint2를 자동으로 실행되도록 한 것이죠.  '--restore' 옵션은 설정해 둔 배경화면이 계속 유지되도록 고정해 주라는 의미입니다.  그리고 각 명령어 마지막에 붙인 '&' 문자는, 해당 명령을 백그라운드 실행하라는 의미입니다.

* 내용을 다 써 줬으면, 저장후 nano 편집기를 빠져나옵니다.  화면 아래에 원하는 명령을 주는 도움말이 있으므로 그대로 하면 됩니다.  '^O' 즉 'Ctrl+o' 키를 누르면, 저장할 파일 이름을 확인하라고 나오는데 엔터를 쳐 주면 저장됩니다.  그리고 '^X' 즉 'Ctrl+x' 키를 눌러서 nano 편집기를 빠져나옵니다.

* 이제 다시 `startx` 해서 X윈도우를 실행해 봅니다.  화면 아래쪽에 tint2 테스크바가 실행되어 보이는 것을 확인할 수 있을 것입니다.



## X윈도우의 필수 유틸리티 추가 설치

* X윈도우가 실행된 상태에서 이제 작업 들어갑니다.

* 마우스 오른쪽 버튼으로 누르면 나오는 obmenu 메뉴에서, 'Terminal emulator'를 선택해서 실행시킵니다.  그러면 터미널 창이 나옵니다.  그런데 기본으로 제공되는 이 터미널은 xterm으로 생각되는데, 좀 안 예쁘고 불편해 보입니다.  더 좋은 걸로 바꿔 봅시다.

* 여러가지 터미널 에뮬레이터 중에서, Terminator를 골라봤습니다.  이걸 깔아봅니다.
```
sudo apt-get install terminator
```
* 다 깔았으면 이제 터미널 창을 닫았다가, 다시 마우스 오른쪽 버튼으로 누르면 나오는 obmenu 메뉴에서, 'Terminal emulator'를 선택해서 실행시킵니다.  그러면 금방 새로 설치한 Terminator로 바뀌어서 뜹니다.  이게 기능이 더욱 빵빵하므로 천천히 알아가면서 주력으로 사용해 보도록 합시다.

* 또 X윈도우용 텍스트 편집기를 설치합니다.  leafpad, gedit, geany 등등 여러가지 많이 있습니다.  일단 가장 가벼운 leafpad를 설치하도록 하겠습니다.  gedit는 GTK 라이브러리를 적극적으로 가져다 쓰기 때문에 좀 설치용량이 많은 편이고, geany는 프로그래밍용 IDE 성격이 강해서 쓸데없는 메뉴가 많습니다.  윈도우 메모장 정도로 간단한 것은 leafpad인 듯 합니다.  역시 터미널 에뮬레이터에서 작업해 줍니다.
```
sudo apt-get install leafpad
```

* leafpad를 설치했으면, 직접 명령어를 쳐 넣어서 한 번 실행해 봅시다.
```
leafpad
```

* 이제 파일탐색기를 설치해 봅시다.  물론 탐색기도 여러가지 많이 있습니다.  일단 가장 가벼운 축에 속하는 PCmanFM을 선택해서 깔아봅니다.  유사품으로 SpaceManFM, Nautilus 등등 매우 여러 종류가 있습니다만, 일단은 제일 가벼운 놈으로 설치해 봅니다.
```
sudo apt-get install pcmanfm
```

* 이제 작업관리자를 설치해 봅시다.  현재 메모리 사용량, CPU 점유율, 어떤 프로그램이 돌아가고 있는지 등을 보여주는 것입니다.  윈도우에서 Ctrl+Shft+Del 키를 누르면 나오는 작업관리자랑 같다고 보시면 됩니다.  물론 이것도 매우 여러 종류가 있는데, 그중에 제일 가벼운 것으로 lxtask를 갖다 씁니다.
```
sudo apt-get install lxtask
```

* 필요하다 싶으면 명령 실행기(gmrun)을 설치합니다.  터미널창을 별도로 안 띄우고, 간단히 명령어만 직접 입력해 넣을 때 쓰는건데 사실 저는 잘 안 씁니다.
```
sudo apt-get install gmrun
```

* 화면 캡쳐 유틸리티도 필요하다면 설치합니다.  뭐 굳이 지금 설치하지 않고 나중에 필요하면 좋은 걸 골라서 설치해도 됩니다.
```
sudo apt-get install gnome-screenshot
```

* Conky 시스템 모니터링 유틸리티도 필요하다면 설치하면 됩니다.  이건 순수하게 개인 취향에 따라 설치하면 됩니다.  conky가 뭔지는 구글 검색해 보면 수두룩하게 나옵니다.
```
sudo apt-get install conky
```

* 이제 반드시 필요한 웹브라우저 설치합니다.  제일 기본적으로 Firefox를 설치해 봅시다. Flash 지원 중단 이슈 때문에 골치가 아픈데, 일단은 구버전의 플래쉬 플레이어 플러그인도 함께 깔아줍시다.  Google Chrome은 나중에 필요할 때 별도로 설치하면 됩니다.
```
sudo apt-get install firefox firefox-locale-ko flashplugin-nonfree
```



## 'VirtualBox 게스트 확장' 설치

* 'VirtualBox 게스트 확장'이라는 것은, VirtualBox가 제공하는 가상머신의 기능을 보강해 주기 위해 게스트OS 즉 여기서는 현재 작동중인 리눅스 환경에다가 깔아주는 소프트웨어를 말합니다.

* 구체적으로 어떤 기능이 보강되냐면, (1) 화면 해상도를 마음대로 바꿀 있게 됩니다.  전체화면 모드도 가능해지고요.  (2) 또 호스트OS(윈도우)와 게스트OS(리눅스) 간에 클립보드 복사 등을 불완전하나마 할 수 있게 됩니다.

* 우선 빌드 환경을 먼저 만들어줍니다.  기계적으로 따라 써 주면 됩니다.  이때, ` 기호는 키보드 맨 왼쪽 위의 ~ 문자 아래의 문자입니다.  이 문자를 영어로는 BackTick 이라고 지칭하더군요.  작은 따옴표 문자와는 다릅니다.  빌드 환경이란, 어떤 경우에는 프로그램 소스코드를 직접 컴파일해서 설치하는 경우도 있는데 그때 컴파일 및 설치본을 만들어주는 환경을 말합니다.  여러가지 기본적인 라이브러리등과 컴파일러들이 주루룩 깔립니다.
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

* 이제 VirtualBox 메뉴중에서, '장치'에서 '게스트확장 CD이미지 삽입'을 선택해 줍니다.  그리고 나서 아래의 명령을 쳐 줍니다.
```
sudo mount /dev/cdrom /mnt
```

* 그러면, VirtualBox가 제공해준 가상CD롬을 리눅스에 마운트해 줘서 읽어들이는 것이 가능한 상태가 됩니다.

* 이제 다음 명령을 쳐서 게스트확장 소프트웨어를 설치합니다.  리눅스는 대소문자를 구분하기 때문에 정확히 써 넣어 줍시다.
```
sudo /mnt/VBoxLinuxAdditions.run
```

* 그러면 이제 VBoxLinuxAdditions.run라는 스크립트가 실행되면서, 소프트웨어를 빌드해서 설치를 합니다.  조금 기다리면 완료됩니다.

* 이제 새롭게 게스트확장 기능이 작동될 수 있도록, X윈도우를 완전히 끝내고 리눅스도 껐다가 다시 재부팅합시다.  재부팅 방법은, VirtualBox 메뉴에서 '파일-닫기'를 누르고 '컴퓨터 끄기 신호 보내기'를 선택하면 됩니다.  컴퓨터의 전원 버튼을 누르는 것과 같은 의미입니다.

* 다시 UbuntuBang을 시작한 다음, 로그인하고 `startx`를 실행시켜 줍니다.

* 이 상태에서, 오른쪽 Ctrl키와 f 키를 함께 눌러줘 봅시다. (이 단축키와 동일한 것은 VirtualBox 메뉴에서 '보기-전체화면모드' 입니다)  그리고 전체화면 전환을 해 봅시다.

* 전체화면으로 잘 전환되면 게스트확장 기능이 잘 작동하고 있는 것입니다.  이제 화면이 작아서 창이 다 안보인다던가 하는 일은 없을 것입니다.




## 한글 환경 구성

* 현재까지는 영어 환경이었는데, 이제 한글 환경을 꾸며 봅시다.

* 제일 먼저 한글 환경용 언어팩을 설치해 줍니다.  여러가지 자질구레한 것들을 모아서 편하게 설치할 수 있도록 Ubuntu에서 제공해 주는 패키지입니다.
```
sudo apt-get install language-pack-ko
```

* 이것을 시도할 때, 의존성이 맞지 않다는 등의 메시지가 나오고 중단된면, 다음 명령을 쳐주고 다시 시도하면 강제로 완결할 수 있습니다.
```
sudo apt-get -f install
```

* 그리고 한글 폰트도 설치해 줍니다.  일단 Ubuntu 저장소에서 기본으로 제공하는 한글 폰트 중에서 제일 중요한 것 2종류를 먼저 설치해 줍시다.  Google Noto CJK라는 폰트와, Naver Nanum 폰트 패키지입니다.
```
sudo apt-get install fonts-noto-cjk fonts-nanum*
```

* 그리고, 이제 한국어 로케일을 설정해 줍니다.  로케일(Locale)이라는 말의 의미는, 단순히 언어만 변경하는 것이 아니고, 날짜표기 방법이라던가 돈의 표기법, 주소, 전화번호, 숫자 자릿수 끊어주는 기호, 시간 표기법, 도량형 등 각 나라마다 제각각의 표기법들을 전부 다 한 방에 설정해 준다는 개념을 의미합니다.  일단 다음 명령을 쳐서 편집기로 들어가 줍시다.
```
sudo leafpad /etc/default/locale
```

* 그럼 현재는 영어로 설정해 뒀기 때문에 다음의 내용이 들어있을 것입니다.
```
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

* 위 내용을 지우고, 아래의 내용으로 대체한 후 저장하고 나옵니다.
```
LANG="ko_KR.UTF-8"
LANGUAGE="ko_KR:ko"
LC_NUMERIC="ko_KR.UTF-8"
LC_TIME="ko_KR.UTF-8"
LC_MONETARY="ko_KR.UTF-8"
LC_PAPER="ko_KR.UTF-8"
LC_IDENTIFICATION="ko_KR.UTF-8"
LC_NAME="ko_KR.UTF-8"
LC_ADDRESS="ko_KR.UTF-8"
LC_TELEPHONE="ko_KR.UTF-8"
LC_MEASUREMENT="ko_KR.UTF-8"
```

* 이제 마지막으로, 한글 입력기를 설치합시다.  한글 입력기란, 한글을 키보드로 써 줄 수 있도록 한/영 전환해 주는 유틸리티를 말하죠.  iBus,Fcitx,Nabi,UIM 등등 여러가지가 있는데, 대체로 보면 어떤 경우에도 완벽한 입력기는 아직 없는 듯 합니다.  소프트웨어 생태계가 원체 방대하다보니, 너무 다양한 경우의 수가 나오기 때문인데요.  따라서 2가지 정도를 깔아놓고 필요에 따라 바꿔가면서 쓰는 것이 제일 낫습니다.

* 일단 먼저 UIM을 설치하도록 합니다.  UIM은 일본에서 만든 다국어 입력기이므로, 여기에 한글 입력을 위한 벼루(UIM-Byeoru)라는 확장을 하나 더 추가로 설치해 줍니다.
```
sudo apt-get install uim uim-byeoru
```

* 그리고, 이것과 별도로 새로 나온 다솜입력기를 설치해 봅니다.  UIM벼루와 비교해서 일장일단이 있는 듯 합니다.

* 다솜입력기는 2015.12.05일부터 PPA 저장소에서 자동 설치본 제공이 시작되었습니다.  따라서 다음 저장소를 반영합니다.
```
sudo add-apt-repository ppa:dasom
```
* 그리고 설치하면 됩니다.
```
sudo apt-get update
sudo apt-get install dasom dasom-gtk dasom-qt dasom-jeongeum
```


* UIM벼루 및 다솜입력기 2가지를 설치했습니다.  이제 어느것을 사용할지 결정해 줘야 할 것 같습니다.  한글입력기 결정을 설정해 주는 유틸리티로 im-config가 있으며, 이것을 또 설치해 줍시다.
```
sudo apt-get install im-config
```

* 일단 시험삼아 다솜입력기를 기본입력기로 설정해 봅시다.
```
im-config
```

* 위 명령을 쳐서 창이 뜨면, Next,OK 해 줘서 창을 넘긴 다음에 입력기를 고르는 창이 나오면 'dasom'을 선택해 주면 됩니다.

* 또 다솜입력기의 세부 설정을 건드려주기 위한 유틸리티로는 dconf-editor를 사용하도록 되어 있습니다.  따라서 이걸 깔아주고 실행해 봅니다.
```
sudo apt-get install dconf-editor
dconf-editor
```

* dconf-editor가 실행되면, 좌측 트리에서 'org-freedesktop-dasom-engines-jeongeum'으로 찾아들어갑니다.  여기서 각 항목을 다음과 같이 맞춰줍시다.

** double-consonant-rule ** ::: 체크해제 (이렇게 하면 'ㄷㄷ'을 칠 때 'ㄸ'이 아니라 'ㄷㄷ'이 된다.)
** hangul-keys ** ::: ['hangul', 'shift-mask space'] (한글키(=우측Alt키) 및 Shift+Space키로 모두 한영전환이 되도록 설정)
** hanja-keys ** ::: ['hangul-hanja'] (한자키(=우측Ctrl키)로 한글을 한자로 변환)
** korean-101-104-key-compatible ** ::: 체크. (내부적으로 xmodmap이 돌아가도록 하는 설정이라고 함)
** layout ** ::: '2' (2벌식 자판)

* 설정을 다 맞췄으면 이제 그냥 종료하면 됩니다.  별도의 OK 버튼이라던가 저장 같은 것을 해 줄 필요는 없는 듯 합니다.

* 이제 X윈도우를 빠져나갔다가, 다시 `startx`해서 들어오면 다솜입력기 아이콘이 Tint2 태스크바에 작고 흰 네모칸으로 보일 것입니다.

* 그리고 입력기를 나중에 UIM벼루로 바꾸고 싶다면, `im-config` 명령을 쳐서 바꿔주면 됩니다.

* 다솜입력기의 장점은, 일단 입력이 그럭저럭 무난하게 잘 됩니다.  그리고 한영전환을 Sift-Space 및 한/영키 모두 어렵지 않게 사용가능하다는 점입니다.  또 F9키를 이용해서 한자 변환하는 것도 용이합니다.  다만 간혹 어떤 어플리케이션에서 다솜입력기가 제대로 안 먹을 경우에는, 입력기를 바꿔보던가 할 수 있습니다.

* 참고로 다솜입력기는 개발자인 Cogniti님이 계속 업데이트를 해주고 계시기 때문에, 빠른 속도로 완성도가 더 높아져 갈 것으로 기대됩니다.  최근에 홈페이지( https://dasom-im.github.io )도 개설되었고, 곧 PPA 저장소( https://launchpad.net/~dasom )도 활성화 될 것이라고 하므로 나중에는 설치가 좀 더 용이해 질 것입니다.


## 사운드 환경 구성

* 사운드 부분은 아무래도 하드웨어 관련되어 있다보니 실패 확률이 있습니다.  일단 다음 레시피를 따라서 해 보고, 만일 실패한다면 다른 방법을 천천히 찾아보면 될 것입니다.

* 오픈소스 ALSA 사운드 드라이버를 설치합니다.

```
sudo apt-get install alsa alsa-tools
sudo adduser  username audio
sudo init 6
```

* 볼륨조절 명령은 `alsamixer` 입니다.  이 명령은 GUI용이 아니고 터미널용이기 때문에 예쁘지는 않습니다.  아쉬운대로 일단 그냥 씁니다.

* 트레이에 볼륨조절 아이콘을 올리기 위해 다음 명령을 쳐서 추가로 깔아줍니다.

```
sudo apt-get install volumeicon-alsa
```

* 볼륨조절 아이콘 자동으로 올리도록 autostart 파일을 편집해 줍니다.

```
leafpad ~/.config/openbox/autostart
```

* 편집기에서 다음 내용 추가해 주고 저장

```
volumeicon &
```



## 결론

* 흥미가 있다면 여기서 이제 더 예쁘게 설정들을 건드려 본다던가, 유틸리티를 더 좋은 걸로 설치해 본다던가 하면서 놀아보면 됩니다.
* UI 관련 주요 설정파일의 위치는 다음과 같습니다.
```
~/.config/tint2/tint2rc
~/.config/openbox/autostart
~/.config/openbox/menu.xml
~/.config/openbox/rc.xml
```
* 위 파일 중에서, tint2rc 및 autostart 같은 것들은 직접 편집기로 설정을 수정하면 좋을 것이고, menu.xml은 `obmenu` 명령으로 나오는 GUI를 통해 편집 가능합니다.
* rc.xml 파일은 편집기로 열어서 잘 살펴보면 폰트나 단축키 같은 것들을 원하는대로 편집해 줄 수 있습니다.
* 이상의 셋팅을 완료한 후, X윈도우를 종료하고 재부팅 명령어 `sudo reboot now`를 쳐서 재부팅 해 줍니다.  그리고 다시 `startx` 한 후에 `lxtask`를 통해서 메모리 사용량을 확인해 보니 108MB를 점유하고 있음을 확인할 수 있습니다.
* 일단 기본적인 환경 구성을 대충 해 보았습니다.
