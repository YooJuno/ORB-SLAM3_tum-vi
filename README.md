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

./Examples/Monocular/mono_tum_vi.cc 에서 Webcam불러오는 32번 째 라인의 -1을 0 혹은 2로 바꾸면 될 수도


### [Relocalization 팁]

**맵 생성** - 최대한 많은 피쳐를 이용하여 맵을 만들어야 나중에 리로컬 할 때 편해진다. 고로 여기서 만져야 할 부분은 yaml파일이다.

1. ORBextractor.nFeatures(2000 이하가 적당한데 real time조건이 아니면 5000정도에서 하는게 제일 좋긴 함. 빼곡한 맵을 만들 수 있음)
2. ORBextractor.iniThFAST(60~120 사이의 값을 잘 정하면 됨.)
3. ORBextractor.minThFAST(10~30정도가 적당함)


**맵 불러오기** - 불러올 땐 특징점이 많은 곳에서 시작하는 것이 빠르다. 체크보드나 키보드를 가까이서 보게되면 수많은 피쳐들을 추출하게 된다. 그 순간 리로컬이 진행되는데, 복도나 별 특징이 없는 곳에선
