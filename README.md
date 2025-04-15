# ROS 2 Humble 설치 가이드 (Windows)


---

## 📦 1. Chocolatey 설치

> 관리자 권한 PowerShell에서 아래 명령어 실행

```

Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = `
[System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

```

---

## 🔧 2. 필수 툴 설치
powershell에서

```
choco install -y git cmake python visualstudio2022buildtools
```

설치 후 시스템 재시작

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
정상적으로 버전 정보가 출력되면 설치 완료입니다 🎉

---

## 🔗 참고 링크
공식 문서: docs.ros.org (Windows Install)

