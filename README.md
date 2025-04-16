# ROS 2 Humble 설치 (Windows)

~~아직 하는 중~~

---

## 📦 1. Chocolatey 설치

[https://chocolatey.org/](https://docs.chocolatey.org/en-us/choco/setup/)

관리자 권한 cmd 아래 명령어 실행

```

@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

```
또는 

관리자 권한 powershell 아래 명령어 실행
```
Get-ExecutionPolicy
```
실행했을 때 결과가 *Restricted*라면, 

A.를 눌러서 AllSigned이 되도록 설정한 후 

아래 명령어 실행
```

Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

```
choco 또는 choco -? 명령어를 입력해서 확인
---


## 🔧 2. 필수 툴 설치


1. Python
관리자용 cmd에서 아래 명령어 입력하여 툴 설치
```
choco install -y python --version 3.8.3
```
2. Visual C++ Redistributables
```
choco install -y vcredist2013 vcredist140
```
3. OpenSSL
```
choco install -y python --version 3.8.3
```
환경변수 유지하도록 설정 :
```
setx /m OPENSSL_CONF "C:\Program Files\OpenSSL-Win64\bin\openssl.cfg"
```
4. Visual Studio
https://aka.ms/vs/16/release/vs_community.exe

5. OpenCV

5-1. [OpenCV 3.4.6 (Windows용 Precompiled 버전)](https://github.com/opencv/opencv/releases/tag/3.4.6)을 다운로드합니다.
5-2. `C:\opencv`에 압축을 해제합니다.
5-3. 관리자 권한 명령 프롬프트를 열고 아래 명령을 실행합니다:
```
setx /m OpenCV_DIR C:\opencv
```
시스템 환경 변수 PATH에 다음 경로를 추가합니다:
```
C:\opencv\x64\vc16\bin
```
6. dependencies
6-1. CMake 설치 및 환경 변수 설정
```
choco install -y cmake
```
설치 후, 다음 경로를 시스템 PATH에 추가합니다:
```
C:\Program Files\CMake\bin
```
6-2. 수동 설치용 패키지 다운로드
아래 .nupkg 파일을 해당 GitHub 저장소에서 다운로드합니다:

asio.1.12.1.nupkg
bullet.3.17.nupkg
cunit.2.1.3.nupkg
eigen.3.3.4.nupkg
tinyxml-usestl.2.6.2.nupkg
tinyxml2.6.0.0.nupkg

6-3. 패키지 설치
다운로드한 파일이 위치한 디렉토리 경로를 <PATH\TO\DOWNLOADS>로 지정한 후, 관리자 권한 PowerShell 또는 CMD에서 다음을 실행합니다:

```
choco install -y -s <PATH\TO\DOWNLOADS> asio cunit eigen tinyxml-usestl tinyxml2 bullet
```
7. Python 패키지
Python 관련 종속성은 pip을 통해 설치할 수 있습니다.

7-1. pip 및 setuptools 업그레이드
```
python -m pip install -U pip setuptools==59.6.0
```
7-2. ROS 2용 Python 패키지 설치
```
python -m pip install -U catkin_pkg cryptography empy==3.3.4 importlib-metadata \
lark==1.1.1 lxml matplotlib netifaces numpy opencv-python PyQt5 pillow \
psutil pycairo pydot pyparsing==2.4.7 pyyaml rosdistro
```

8. Qt5
8-1. Qt5 설치
https://www.qt.io/offline-installers   
Qt 공식 사이트에서 5.12.x 버전의 오프라인 설치 파일을 다운로드합니다. (5.15.x 설치함)

8-2. 환경변수 설정 
Qt가 설치된 경로가 C:\Qt라고 가정할 때, 관리자 CMD에서 다음 명령을 실행
```
setx /m Qt5_DIR C:\Qt\Qt5.12.12\5.12.12\msvc2017_64
setx /m QT_QPA_PLATFORM_PLUGIN_PATH C:\Qt\Qt5.12.12\5.12.12\msvc2017_64\plugins\platforms
```


> 9. RQr dependencies



---

## 📥 3. ROS 2 Humble 설치
공식 GitHub 릴리즈 페이지에서 .msi 설치파일 다운로드

예: ros2-humble-*-windows-release-amd64.msi 설치

---

## 🛠️ 4. 환경 변수 설정
Windows 환경 변수 Path에 다음 경로 추가:

vbnet에서
```
C:\dev\ros2_humble\bin
C:\dev\ros2_humble\lib
```
---

⚙️ 5. ROS 2 실행
Visual Studio Developer Command Prompt (x64) 실행


cmd에서
```
call C:\dev\ros2_humble\local_setup.bat
ros2 --version
```

---

## 🔗 참고 링크
공식 문서: [docs.ros.org](https://docs.ros.org/en/crystal/Installation/Windows-Install-Binary.html) (Windows Install)

