# Configuring environment (Windows)
---

## 1️. 매번 셸(cmd 또는 PowerShell)을 열 때 ROS 2 사용 가능하게 만들기

ROS 2 명령어(`ros2 run`, `ros2 topic list` 등)를 사용하려면, 셸을 열 때마다 아래 명령어를 입력하세요:

```cmd
call C:\dev\ros2\local_setup.bat
```

## 2. 환경 변수 확인하기
ROS 2 환경이 제대로 설정되었는지 확인하려면:
```cmd
set | findstr -i ROS
```
