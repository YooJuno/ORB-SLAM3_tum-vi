### [SLAM 실행 - Webcam]

실행 명령어는

$ ./Examples/Monocular/mono_tum_vi ./Vocabulary/ORBvoc.txt ./mono_cam.yaml

카메라 종류에 따른 yaml파일 필요시
https://github.com/UZ-SLAMLab/ORB_SLAM3/tree/master/Examples/Monocular
여기서 다운받으면 됨

### [맵 저장 방법]

카메라 정보를 담고있는 yaml파일에서(나는 mono_cam.yaml)

System.SaveAtlasToFile: "test1"

System.LoadAtlasFromFile: "test2"

이 두 명령어를 적절하게 주석처리하면 됨.


### [카메라를 못불러올 때]

./Examples/Monocular/mono_tum_vi.cc 에서 Webcam불러오는 32번 째 라인의 -1을 0
