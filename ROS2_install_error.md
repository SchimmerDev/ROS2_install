# 내가 마주했던 error들
**결론 : ROS2 humble 20220523 버전으로 재설치**

## 1. failed to create process.
242382번 마주했던 에러.
시도1, 시도2 해도 어차피 다른 에러 떴기에 효과있는지는 모르겠음

*시도1*
1. ros2-script.py 찾기 (Script아래에 있음)
2. notepad으로 수정하기 
3. 제일 첫 줄 "#!<C:\Program Files\Python38\python.exe" 으로 바꾸기 (<python 있는 경로>)
4. 저장
5. 새로운 cmd
6. 다시 실행해보기
7. (이걸로 해결되진 않고 다른 에러 뜸)

*시도2*
1. chocolatey로 다운로드한 python이 path에서 우선순위 오도록 예전에 다운로드 받은 python들을 path에서 삭제
2. 이때 3.8.x 버전으로 작동되도록 함


## 2. ImportError: DLL load failed while importing _rclpy_pybind11: The specified module could not be found.
C:\dev\ros2-windows\bin 을 path에 추가
→ 바뀐 것 x

## 3. 'ros2' is not recognized as an internal or external command, operable program or batch file.

## 4. PackageNotFoundError: ros2cli

## 5. ModuleNotFoundError: No module named 'ros2cli'

---
path 신경써서 정리 몇 번 함
ros2 제일 최신 버전 말고 20220523 버전으로 다시 깔았더니 해결됨
