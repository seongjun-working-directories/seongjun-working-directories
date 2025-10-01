# 🤖 Calibration Room (자동 포즈 추정 시스템)

자동 포즈 추정 시스템은 카메라, 깊이 센서, 라이다를 활용하여 로봇의 위치와 자세를 실시간으로 추정하는 ROS 패키지입니다. 웹 기반 GUI를 통해 직관적인 캘리브레이션과 모니터링을 제공합니다.

---

## 📋 목차

1. [🎯 시스템 개요](#-시스템-개요)
2. [🏗️ 시스템 아키텍처](#️-시스템-아키텍처)
3. [⚡ 빠른 시작](#-빠른-시작)
4. [🛠️ 상세 설치 가이드](#️-상세-설치-가이드)
5. [🚀 사용법](#-사용법)
6. [🖥️ GUI 사용 가이드](#️-gui-사용-가이드)
7. [📡 API 및 토픽 레퍼런스](#-api-및-토픽-레퍼런스)
8. [⚙️ 설정 및 파라미터](#️-설정-및-파라미터)
9. [🔧 잠재적 오류 대응](#-잠재적-오류-대응)
10. [🧮 알고리즘 상세](#-알고리즘-상세)
11. [🔄 캘리브레이션 워크플로우](#-캘리브레이션-워크플로우)
12. [📚 참고 자료](#-참고-자료)

---

## 🎯 시스템 개요

이 시스템은 다음과 같은 센서들을 이용하여 다중 센서 융합 기반의 포즈 추정을 수행합니다:

- 📷 **Camera Pose Estimator**: ArUco 마커를 이용한 비전 기반 포즈 추정
- 🔍 **Depth Pose Estimator**: 체스보드와 ArUco 마커를 이용한 깊이 카메라 기반 포즈 추정
- 📡 **LiDAR Pose Estimator**: ICP 알고리즘을 이용한 라이다 스캔 매칭 기반 포즈 추정
- 🖥️ **Web-based GUI**: Vue.js 기반 실시간 모니터링 및 제어 인터페이스

### ✨ 주요 특징

- 🎯 실시간 6-DOF 포즈 추정 (위치 + 자세)
- 🖥️ 실시간 센서 데이터 스트리밍 (이미지 + 포인트클라우드)
- 🎮 웹 기반 로봇 제어 (수동 조작 + 자율 주행)
- 📁 자동 URDF 생성 및 파일 전송
- ⚙️ 센서별 활성화/비활성화 설정
- 📊 실시간 시각화 및 모니터링

---

## 🏗️ 시스템 아키텍처

### 📁 전체 프로젝트 구조

```
calibration-room/
├── auto_pose_estimation/              # ROS 포즈 추정 시스템
│   └── src/
│       ├── camera_pose_estimator/     # ArUco 마커 기반 카메라 포즈 추정
│       ├── depth_pose_estimator/      # 깊이 센서 기반 포즈 추정
│       └── lidar_pose_estimator/      # LiDAR 기반 포즈 추정
└── pose_estimation_gui/               # 웹 기반 GUI 시스템
    ├── client/                        # Vue.js 프론트엔드
    └── server/                        # Express.js 백엔드
```

### 🌐 네트워크 구성

```
🖥️ Main PC (192.168.2.2)             🖥️ Sub PC (192.168.2.3)
├── ROS Master                         ├── Additional Sensors
├── Navigation Stack                   └── Data Processing
└── Goal Management

📱 Client PC (192.168.2.8)
├── Web GUI Interface
├── Real-time Monitoring
└── Calibration Control
```

### 🔄 데이터 플로우

```
📱 Frontend (Vue.js 3 + TypeScript)
        ↕️ HTTP/WebSocket
🖥️ Backend (Express.js + TypeScript)
        ↕️ ROS Bridge
🤖 ROS System (C++/Python)
```

---

## ⚡ 빠른 시작

### 🚀 3단계로 시작하기

#### 1. 환경 설정

```bash
# 환경 변수 설정 (IP는 실제 환경에 맞게 수정)
export ROS_HOSTNAME=192.168.2.8
export ROS_MASTER_URI=http://192.168.2.2:11311
```

#### 2. 시스템 실행

```bash
# 터미널 1: 백엔드
npm run dev --prefix ~/calibration-room/pose_estimation_gui/server

# 터미널 2: 프론트엔드
npm run dev --prefix ~/calibration-room/pose_estimation_gui/client
```

#### 3. GUI 접속

브라우저에서 `http://localhost:5173` 접속  
→ **LAUNCH ON** 버튼 클릭  
→ **SHOW RESULT**로 결과 확인

---

## 🛠️ 상세 설치 가이드

### 🔧 시스템 요구사항

- **OS**: Ubuntu 20.04 LTS (ROS Noetic 지원)
- **ROS**: Noetic Ninjemys
- **Node.js**: 16.18.0+
- **메모리**: 8GB+ 권장
- **저장공간**: 10GB+ 사용 가능 공간

### 📦 의존성 설치

#### 1. ROS 패키지

```bash
# 핵심 ROS 패키지
sudo apt-get update
sudo apt-get install ros-$ROS_DISTRO-rosbridge-server
sudo apt-get install ros-$ROS_DISTRO-image-transport
sudo apt-get install ros-$ROS_DISTRO-tf ros-$ROS_DISTRO-tf2-ros
sudo apt-get install ros-$ROS_DISTRO-tf2-web-republisher
sudo apt-get install ros-$ROS_DISTRO-pcl-conversions
sudo apt-get install ros-$ROS_DISTRO-image-geometry
sudo apt-get install ros-$ROS_DISTRO-camera-info-manager
```

#### 2. 컴퓨터 비전 및 수학 라이브러리

```bash
# OpenCV with ArUco support
sudo apt-get install libopencv-dev libopencv-contrib-dev

# PCL 및 수학 라이브러리
sudo apt-get install libpcl-dev libeigen3-dev
sudo apt-get install libgflags-dev libgoogle-glog-dev
sudo apt-get install libusb-1.0-0-dev libuvc-dev
```

#### 3. Node.js 환경 설정

```bash
# Node.js 설치 및 설정
sudo apt install nodejs npm
sudo npm install -g n
sudo n 16.18.0
hash -r

# 개발 도구 설치
sudo npm install -g typescript
sudo npm install -g @microsoft/rush
```

### 🛠️ 프로젝트 빌드

#### 1. ROS 패키지 빌드

```bash
cd ~/calibration-room/auto_pose_estimation
catkin_make -j4
source devel/setup.bash
```

#### 2. GUI 시스템 설정

```bash
cd ~/calibration-room/pose_estimation_gui
rush purge    # 이전 설치 정리
rush update   # 패키지 일괄 설치
```

#### 3. 설정 파일 복사

```bash
# LiDAR 참조 데이터
sudo cp lidar_01_reference.txt ~/.ros/
sudo cp lidar_02_reference.txt ~/.ros/
```

### ⚙️ 환경 변수 설정

`~/.bashrc` 파일에 추가:

```bash
# ROS 환경 설정
export ROS_HOSTNAME=192.168.2.8              # 현재 시스템 IP로 변경
export ROS_MASTER_URI=http://192.168.2.2:11311

source /opt/ros/noetic/setup.bash
source ~/calibration-room/auto_pose_estimation/devel/setup.bash

# 편의를 위한 alias 설정
alias be='npm run dev --prefix ~/calibration-room/pose_estimation_gui/server'
alias fe='npm run dev --prefix ~/calibration-room/pose_estimation_gui/client'
alias main='ssh cona@192.168.2.2 -XC'
alias sub='ssh cona@192.168.2.3 -XC'
```

적용:

```bash
source ~/.bashrc
```

---

## 🚀 사용법

### 🖥️ GUI 시스템 실행

단계별 실행:

```bash
# 1. 백엔드 서버 시작
cd ~/calibration-room/pose_estimation_gui/server
npm run dev
# 또는: be

# 2. 프론트엔드 시작 (새 터미널)
cd ~/calibration-room/pose_estimation_gui/client
npm run dev
# 또는: fe

# 3. 웹 브라우저에서 접속
http://localhost:5173
```

### 🛠️ ROS 시스템 실행 모드

#### 통합 실행 (권장)

```bash
# 기본 모드 - 모든 센서 활성화
roslaunch depth_pose_estimator classic_pose_estimator_launch.launch

# 단일 깊이 센서 모드
roslaunch depth_pose_estimator integrated_pose_estimator_launch.launch

# 이중 깊이 센서 모드
roslaunch depth_pose_estimator new_pose_estimator_launch.launch
```

#### 개별 센서 실행

```bash
# 각 센서를 별도로 실행하고 싶은 경우
roslaunch camera_pose_estimator camera_pose_estimator_launch.launch
roslaunch depth_pose_estimator depth_pose_estimator_launch.launch
roslaunch lidar_pose_estimator lidar_pose_estimator_launch.launch
```

### 📡 LiDAR 캘리브레이션 절차

#### 1. 참조 데이터 수집 (초기 한번만)

```bash
# GUI에서 또는 터미널에서 실행 가능
rostopic pub /lidar_01_reference std_msgs/Bool "data: true"
rostopic pub /lidar_02_reference std_msgs/Bool "data: true"
```

#### 2. 현재 데이터와 매칭

```bash
# 로봇 위치 변경 후 매칭 수행
rostopic pub /lidar_01_current std_msgs/Bool "data: true"
rostopic pub /lidar_02_current std_msgs/Bool "data: true"
```

---

## 🖥️ GUI 사용 가이드

### 🏠 홈 페이지

- 🟢 **LAUNCH ON**: 전체 ROS 시스템 시작
- 🔴 **LAUNCH OFF**: ROS 시스템 안전 종료
- 📊 **SHOW RESULT**: 캘리브레이션 메인 페이지
- 🖥️ **WEBVIZ**: 3D 시각화 도구 (별도 창)

### 📊 캘리브레이션 페이지

**모드 전환:**
- 📈 **6-DOF DATA**: 실시간 센서 위치/자세 수치 데이터
- 🖥️ **SENSOR IMAGE**: 센서별 이미지 스트리밍 (카루셀)

**LiDAR 제어:**
- 📡 **LIDAR 1 CURRENT**: 전방 라이다 매칭 실행
- 📡 **LIDAR 2 CURRENT**: 후방 라이다 매칭 실행

**데이터 관리:**
- 💾 **캘리브레이션 결과 추출**: 현재 6-DOF 값으로 URDF 파일 생성
- 📤 **추출된 파일 전송**: 생성된 URDF를 메인 시스템으로 자동 전송

### ⚙️ 설정 페이지

- 📷 **RGB Camera**: 카메라 활성화/비활성화
- 🔍 **RGB-D Camera**: 깊이 카메라 개별 선택 (`/depth1`, `/depth2`)
- 📡 **2D LiDAR**: 라이다 센서 개별 선택 (`/scan1`, `/scan2`)
- 💾 **설정 저장/복원**: 사용자 정의 설정 관리

### 🎮 조작 페이지

**수동 제어:**
- ⬆️⬇️⬅️➡️ **방향 버튼**: 직관적인 로봇 제어
- ⏹️ **정지 버튼**: 즉시 모든 움직임 정지

**자율 주행:**
- 🏠 **홈**: 시작 위치로 복귀
- 1️⃣ 2️⃣ 3️⃣: 각 테이블 번호로 자동 이동

---

## 📡 API 및 토픽 레퍼런스

### 📥 입력 토픽

| 토픽명 | 타입 | 설명 |
|--------|------|------|
| `/camera/image_raw/compressed` | `sensor_msgs/CompressedImage` | 카메라 이미지 |
| `/camera/depth/image_raw` | `sensor_msgs/Image` | 깊이 이미지 |
| `/camera/depth_registered/points` | `sensor_msgs/PointCloud2` | 깊이 포인트클라우드 |
| `/scan1`, `/scan2` | `sensor_msgs/LaserScan` | 라이다 스캔 데이터 |
| `/cmd_vel` | `geometry_msgs/Twist` | 로봇 제어 명령 |

### 📤 출력 토픽

| 토픽명 | 타입 | 설명 |
|--------|------|------|
| `/camera_01_image_01`, `/camera_01_image_02` | `sensor_msgs/CompressedImage` | 처리된 카메라 이미지 |
| `/depth_01_image_01`, `/depth_01_image_02` | `sensor_msgs/CompressedImage` | 처리된 깊이 이미지 |
| `/lidar_01_image_01`, `/lidar_01_image_02` | `sensor_msgs/CompressedImage` | 라이다 시각화 이미지 |
| `/depth_world_pointcloud` | `sensor_msgs/PointCloud2` | 월드 좌표계 포인트클라우드 |
| `/depth_camera_pointcloud` | `sensor_msgs/PointCloud2` | 카메라 좌표계 포인트클라우드 |

### 🔄 TF 프레임

- `base_link` → `camera_01_tf`: 카메라 포즈
- `base_link` → `depth_01_tf`: 깊이 센서 포즈
- `base_link` → `lidar_01_tf`: 전방 라이다 포즈
- `base_link` → `lidar_02_tf`: 후방 라이다 포즈

### 🌐 Web API 엔드포인트

| 엔드포인트 | 메소드 | 설명 |
|-----------|--------|------|
| `/on` | GET | 🟢 ROS 시스템 시작 |
| `/off` | GET | 🔴 ROS 시스템 종료 |
| `/store` | POST | 💾 캘리브레이션 데이터 저장 (URDF 생성) |
| `/send` | GET | 📤 URDF 파일 메인 시스템으로 전송 |
| `/get-ip` | GET | 🌐 현재 시스템 IP 주소 조회 |
| `/get-cr-settings` | GET | ⚙️ 현재 센서 설정 조회 |
| `/cr-settings` | POST | ⚙️ 센서 설정 저장 |
| `/lidar_1_current` | GET | 📡 LiDAR 1 매칭 실행 |
| `/lidar_2_current` | GET | 📡 LiDAR 2 매칭 실행 |

---

## ⚙️ 설정 및 파라미터

### 📁 설정 파일 위치

- 📷 `camera_pose_estimator/params/camera_pose_estimator_params.yaml`
- 🔍 `depth_pose_estimator/params/depth_pose_estimator_params.yaml`
- 🔍 `depth_pose_estimator/params/double_depth_pose_estimator_params.yaml`
- 🖥️ `pose_estimation_gui/server/assets/cr-settings.json`

### 🎯 주요 파라미터

**카메라 관련:**
- `ARUCO_EDGE_SIZE`: ArUco 마커 크기 (mm)
- `ARUCO_GAP_SIZE`: 마커 간 간격 (mm)
- `ARUCO_BOARD_X/Y`: 그리드 보드 구성 (개수)

**깊이 센서 관련:**
- `CHESSBOARD_WIDTH/HEIGHT`: 체스보드 패턴 크기
- `CHESSBOARD_EDGE_SIZE`: 체스보드 셀 크기 (mm)
- `FRAMES_PER_SECONDS`: 처리 프레임 레이트

**좌표계 변환:**
- 시스템은 오른손 법칙을 준수하여 좌표 변환 수행
- 센서별 오프셋 보정값 적용
- 쿼터니언 ↔ 오일러 각도 자동 변환

---

## 🔧 잠재적 오류 대응

### 📋 체크리스트 방식 예상 오류 대응 현황

#### 1. 📷 마커/패턴이 검출되지 않는 경우 대응

- ✅ 조명 조건 확인 (적절한 밝기, 그림자 없음)
- ✅ 마커 크기 및 인쇄 품질 확인 (선명한 경계)
- ✅ 카메라 초점 및 해상도 설정
- ✅ 마커와 카메라 간의 적절한 거리 유지 (0.5m~3m)

#### 2. 🎯 포즈 추정 정확도 저하되는 경우 대응

- ✅ 카메라 캘리브레이션 재수행 (`camera_calibration` 패키지)
- ✅ 참조 패턴과 현재 관측 간의 대응점 확인
- ✅ 센서 노이즈 필터링 파라미터 조정
- ✅ 환경 변화 (조명, 온도, 진동) 고려

#### 3. 🔄 TF 변환 오류가 있는 경우 대응

- ✅ 프레임 ID 일치 여부 확인 (`rosrun tf view_frames`)
- ✅ 시간 동기화 문제 점검 (`rosrun tf tf_monitor`)
- ✅ TF tree 구조 검증 (`rosrun rqt_tf_tree rqt_tf_tree`)

#### 4. 🖥️ GUI 연결 문제 상황 대응

- ✅ ROSBridge 서버 상태 확인
  ```bash
  roslaunch rosbridge_server rosbridge_websocket.launch port:=9090
  ```
- ✅ 네트워크 설정 및 방화벽 확인
- ✅ 브라우저 개발자 도구에서 WebSocket 연결 상태 확인
- ✅ 포트 충돌 확인 (`netstat -tulpn | grep 9090`)

#### 5. 📡 LiDAR 매칭 실패

- ✅ 참조 데이터 품질 확인 (`~/.ros/` 폴더의 텍스트 파일)
- ✅ 환경 변화가 큰 경우 참조 데이터 재수집
- ✅ ICP 알고리즘 파라미터 조정 (iteration 수, epsilon 값)
- ✅ 스캔 범위 내 장애물 존재 여부 확인

### 🔍 디버깅 명령어

```bash
# TF 관련 디버깅
rosrun tf view_frames && evince frames.pdf
rostopic echo /tf

# 토픽 상태 확인
rostopic list | grep -E "(image|scan|tf)"
rostopic hz /camera/image_raw/compressed

# 노드 상태 확인
rosnode list
rosrun rqt_graph rqt_graph
```

---

## 🧮 알고리즘 상세

### 📷 Camera Pose Estimator

**처리 단계:**

1. **ArUco 마커 검출**: `cv::aruco::detectMarkers()` 함수 사용
2. **PnP 문제 해결**: `cv::aruco::estimatePoseBoard()`를 통한 6-DOF 포즈 추정
3. **Rodrigues 변환**: 회전 벡터 → 회전 행렬 변환
4. **좌표계 보정**: 카메라 좌표계 → 월드 좌표계 변환

**핵심 수식:**

```
P_world = R * P_camera + T
```

여기서 `R`: 3x3 회전행렬, `T`: 3x1 변환벡터

### 🔍 Depth Pose Estimator

**처리 단계:**

1. **패턴 검출**: 체스보드 또는 ArUco 패턴 인식
2. **3D 포인트 추출**: 깊이 정보 + 2D 좌표 → 3D 좌표 변환
3. **Rigid Transformation**: SVD 기반 최적 변환 행렬 계산
4. **이상값 필터링**: RANSAC 또는 통계적 방법으로 노이즈 제거

**SVD 기반 변환:**

```
H = Σ(Pi_camera - mean_camera) * (Pi_world - mean_world)^T
[U, S, V] = SVD(H)
R = V * U^T
T = mean_world - R * mean_camera
```

### 📡 LiDAR Pose Estimator

**ICP 알고리즘 단계:**

1. **전처리**: 라이다 스캔 데이터 정규화 및 필터링
2. **히스토그램 매칭**: 각도별 거리 히스토그램 생성 및 비교
3. **대응점 탐색**: kd-tree를 이용한 최근점 탐색
4. **반복 최적화**: SVD 기반 변환 행렬 반복 계산
5. **수렴 판정**: 오차 임계값 또는 최대 반복 수 도달

**수렴 조건:**

```
|error_k - error_{k-1}| < epsilon  (일반적으로 0.1)
max_iterations = 100
```

---

## 🔄 캘리브레이션 워크플로우

```
🚀 시스템 시작
    ↓
📡 센서 데이터 수집
    ↓
센서 타입 확인
    ↓
┌────────────────────────────────┐
│  📷 Camera  │  🔍 Depth  │  📡 LiDAR  │
│      ↓      │      ↓     │      ↓     │
│ 🎯 ArUco   │ 📋 체스보드 │ 🖥️ 스캔   │
│  마커 검출  │  /ArUco 검출│ 데이터 매칭│
└────────────────────────────────┘
    ↓
📊 6-DOF 계산
    ↓
🖥️ 실시간 모니터링
    ↓
정확도 만족?
    ↓ Yes          ↓ No
💾 결과 저장    ⚙️ 파라미터 조정
    ↓               ↓
📁 URDF 생성    (반복)
    ↓
📤 파일 전송
    ↓
✅ 캘리브레이션 완료
```

### 단계별 상세 설명

1. **🚀 시스템 초기화**: ROS 노드 시작, GUI 연결 확인
2. **📡 데이터 수집**: 각 센서로부터 실시간 데이터 스트리밍
3. **🎯 패턴 인식**: 센서별 특화된 패턴/마커 검출
4. **📊 포즈 계산**: 알고리즘별 6-DOF 값 산출
5. **🖥️ 모니터링**: GUI를 통한 실시간 결과 확인
6. **⚙️ 최적화**: 필요시 파라미터 조정 및 재수행
7. **💾 데이터 저장**: 최종 캘리브레이션 결과 저장
8. **📁 파일 생성**: 로봇 시스템용 URDF 파일 자동 생성

---

## 📚 참고 자료

### 🔬 핵심 알고리즘 논문

- **ArUco**: Garrido-Jurado et al., "Automatic generation and detection of highly reliable fiducial markers under occlusion"
- **ICP**: Besl & McKay, "A method for registration of 3-D shapes"
- **Pose Estimation**: Lepetit et al., "EPnP: Efficient Perspective-n-Point Camera Pose Estimation"

### 📖 기술 문서

- [OpenCV ArUco Documentation](https://docs.opencv.org/master/d5/dae/tutorial_aruco_detection.html)
- [PCL Point Cloud Library](https://pointclouds.org/)
- [ROS tf2 Tutorials](http://wiki.ros.org/tf2/Tutorials)
- [Vue.js 3 Official Guide](https://vuejs.org/)
- [ROS Bridge Suite](http://wiki.ros.org/rosbridge_suite)

### 🖥️ 개발 환경

- **ROS Noetic**: 로봇 운영체제 LTS 버전
- **OpenCV 4.x**: 컴퓨터 비전 라이브러리
- **PCL 1.10+**: 포인트 클라우드 처리 라이브러리
- **Vue.js 3**: 반응형 웹 프레임워크
- **TypeScript**: 타입 안전 JavaScript
- **Bootstrap 5**: 반응형 UI 컴포넌트

---

**문서 버전**: 1.0  
**최종 업데이트**: 2025년  
**작성자**: Calibration Room Development Team
