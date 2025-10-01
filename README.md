# 박성준 - Software Developer

> **디지털 전환**을 위해, **도메인과 프로세스에 몰입**하여 분석하고 구현하는 개발자입니다.<br/>
> <sub style="color: #777777;">포트폴리오는 핀테크, 세무, 로보틱스 등 여러 도메인의 디지털 전환 경험을 중심으로 작성되었습니다.</sub>

## About Me

- **이름**: 박성준 (PARK SEONGJUN)
- **생년월일**: 1998.10.23
- **연락처**: 010-5180-1657
- **최종학력**: 한양대학교 정보시스템학과 (2019.03 ~ 2023.08)

## Core Skills

### Backend Development
- **Languages**: Java | JavaScript | TypeScript | Python | C++
- **Frameworks**: Spring Boot | Node.js (Express, Fastify) | ROS C++
- **Database**: MySQL | MongoDB | Redis
- **Tools**: Kafka | WebSocket | Docker

### Frontend Development
- **Web**: React.js | Vue.js | HTML/CSS
- **Mobile**: Flutter (Dart) | Kotlin
- **UI/UX**: Figma

### AI & Modern Development
- **AI Collaboration**: Claude | GitHub Copilot | ChatGPT
- **Architecture Design**: RESTful API | Microservices
- **DevOps**: Ubuntu | Git | CI/CD

## Achievements

### 수상 이력 및 공모사업 선정 이력
- **2021년 2학기 한양학업 우수상**(성적 장학금 수혜)
- **2021년 중소벤처기업부 예비창업패키지 선정**
- **경희대학교 캠퍼 2기 예비창업팀 선정**

### 언어 능력
- TOEIC Speaking: Intermediate High (2025.03.26)
- 기본적인 영어 의사소통 가능

<br/>

## Work Experience

### 코가로보틱스(주) - 인턴
**2022.09 ~ 2023.02 (6개월)**

**Tech Stack**: ROS C++, Vue.js, Node.js, OpenCV, PCL, Ubuntu 20.04, Rviz, ArUco, ICP

**로봇 센서 캘리브레이션 시스템 개발 (Calibration Room)**

코가로보틱스 자율주행 솔루션 사업본부에서 서빙 로봇 및 자율주행 휠체어의 센서 캘리브레이션 자동화 시스템을 개발했습니다.

**프로젝트 배경**
- 생산팀과 연구팀이 로봇 센서(RGB-D Camera, 2D LiDAR) 조립 후 수작업으로 캘리브레이션 수행
- 센서별 위치/자세 측정에서 병목 발생 확인, 사람마다 측정값 편차 발생
- 로봇 URDF 파일 수동 수정으로 인한 휴먼 에러 발생

**디지털 전환 성과**
- **RGB Camera**: ArUco 마커 기반 6-DOF 포즈 자동 추정
- **RGB-D Camera**: 체스보드 패턴 + 깊이 정보 융합으로 밀리미터 단위 정밀 측정
- **2D LiDAR**: ICP 알고리즘 기반 스캔 매칭으로 위치 자동 계산
- **웹 GUI**: Vue.js 기반 실시간 모니터링 및 제어 인터페이스 구현
- **자동화**: 캘리브레이션 결과를 URDF 파일로 자동 생성 및 전송
- **효율성 향상**: 작업 시간 30분 → 5분 이내로 단축, 측정 정확도 향상

**기술 구현 상세**
- ROS C++로 센서 데이터 처리 및 좌표 변환 알고리즘 구현
- OpenCV와 PCL 라이브러리 활용한 컴퓨터 비전 처리
- Node.js 백엔드로 ROS와 웹 브라우저 간 실시간 통신
- Vue.js로 센서 이미지 스트리밍 및 6-DOF 데이터 시각화
- ROS GUI Viewer 개발 (Electron + Vue.js 기반 로봇 맵 시각화)

---

### 똑똑(주) - 인턴
**2022.07 ~ 2022.08 (2개월)**

**Tech Stack**: Vue.js, Fastify.js, MySQL, MongoDB, Redis, TypeScript, Quasar Framework, Bootstrap 5

**벤처캐피탈 투자 관리 ERP 시스템 구축**

DSC 인베스트먼트 자회사에서 VC/LP/GP/Startup 간 투자 프로세스 관리 및 사내 자원 관리를 위한 통합 ERP 시스템 개발에 참여했습니다.

**프로젝트 배경**
- VC 기업들이 노후화된 ERP 시스템 사용 중
- 투자 정보가 Email, Excel, PDF, Paper 등으로 분산 관리
- 법인 등기 열람 등 반복 업무에 많은 시간 소요

**디지털 전환 성과**
- **투자 정보 관리 API**: Fastify.js 기반 REST API 설계 및 MongoDB/Redis/MySQL 멀티 DB 연동
- **법인 등기 자동화**: 인터넷 등기소 크롤링, 엑셀 목록 일괄 처리, Setup 프로그램 배포
- **사용자 관리 페이지**: Vue.js 3 + TypeScript 기반 프론트엔드 단독 개발
- **실시간 알림**: Redis Pub/Sub + SMTP 이메일 자동 발송 시스템
- **프로세스 개선**: 법인 등기 조회 수작업 → 자동화, 분산 데이터 → 단일 시스템 통합

**기술 구현 상세**
- Monorepo 구조 (@microsoft/rush) 기반 프로젝트 관리
- Bootstrap 5 커스텀 컴포넌트 시스템 구축
- TypeScript로 타입 안전성 확보
- 데이터베이스 우선순위 전략: MongoDB → Redis → MySQL
- Quasar Framework에서 Bootstrap으로 컴포넌트 마이그레이션

<br/>

## Key Projects

### 1. Market Follower - 업비트 암호화폐 실시간 시세 및 가상 거래 서비스
**개인 프로젝트 | 진행 중**

**Tech Stack**
- **Backend**: Java Spring Boot, MySQL, Redis, Apache Kafka
- **Infrastructure**: Docker, AWS EC2, GitHub Actions
- **Real-time**: WebSocket (STOMP)

Spring Boot와 Kafka를 활용한 실시간 암호화폐 거래 시뮬레이션 플랫폼입니다. 업비트 API와 연동하여 600여 개 코인의 실시간 시세를 WebSocket으로 스트리밍하고, Redis 캐싱을 통해 밀리초 단위 응답속도를 구현했습니다.

**프로젝트 배경**
- 암호화폐 투자자들이 실전 투자 전 연습할 수 있는 플랫폼 필요
- 실시간 대용량 데이터 처리 및 트랜잭션 관리 기술 학습 목적

**주요 내용 및 성과**
- 실시간 데이터 처리: Kafka를 통한 600개 코인 시세 스트리밍, 10초마다 WebSocket 브로드캐스팅
- 고속 응답: Redis 캐싱으로 밀리초 단위 API 응답 구현
- 가상 거래 시스템: 실제 거래소와 동일한 매수/매도/체결 로직 구현
- 마이크로서비스 아키텍처: 확장 가능한 시스템 설계, Docker 컨테이너화
- 자동 배포: GitHub Actions CI/CD 파이프라인 구축

**GitHub**: [market-follower](https://github.com/seongjun-working-directories/market-follower)

---

### 2. Tax Canvas - AI 기반 세무 유사 판례 검색 서비스
**세무법인정성 외주 | 2023.08 ~ 2023.10**

**Tech Stack**
- **Frontend**: React.js, TypeScript
- **Backend**: Express.js, MongoDB (Vector DB)
- **AI**: OpenAI API

OpenAI API를 활용한 벡터 데이터베이스 기반의 세무 판례 검색 엔진입니다. 복잡한 세무 쟁점을 AI가 자동 분석하여 관련 법령, 판례, 예규를 빠르게 검색할 수 있도록 구현했습니다.

**프로젝트 배경**
- 세무사가 유사 판례 검색에 수 시간 소요
- 방대한 법령/판례/예규 자료를 수작업으로 검색
- 쟁점 분석 및 관련 자료 찾기의 어려움

**주요 내용 및 성과**
- AI 쟁점 분석: OpenAI API로 복잡한 세무 쟁점 자동 분석
- 벡터 검색: MongoDB Vector DB 기반 유사도 검색 엔진 구현
- 통합 검색: 법령, 판례, 예규를 한 번에 검색
- 팀 협업 기능: 프로젝트 공유 및 협업 시스템 구축
- 효율성 개선: 판례 검색 시간 수 시간 → 1시간 이내로 단축

**GitHub**: 비공개 (필요하신 경우, 이메일 주시면 감사하겠습니다.)

---

### 3. 사공사(sagongsa) - 쇼핑 최저가 검색 애플리케이션
**포스트랩(주) 외주 | 2023.06 ~ 2023.08**

**Tech Stack**
- **Mobile**: Flutter (Dart)

쇼핑 최저가 검색 모바일 애플리케이션 개발 프로젝트입니다.

**프로젝트 배경**
- 여러 쇼핑몰의 가격 비교를 위한 모바일 앱 수요
- 일관된 디자인 시스템과 재사용 가능한 UI 컴포넌트 필요

**주요 내용 및 성과**
- 전체 디자인 시스템 구현: Flutter 기반 일관된 UI/UX 설계
- 재사용 컴포넌트 개발: 확장 가능한 위젯 라이브러리 구축
- 구글플레이 1만+ 다운로드 달성

**GitHub**: 비공개 (필요하신 경우, 이메일 주시면 감사하겠습니다.)

## Development Philosophy

### 1. 기술 도입의 명확한 목적 설정
새로운 기술을 도입할 때 그 의도와 목적을 명확히 파악하고, 프로젝트에 최적화된 방식으로 적용합니다.

### 2. AI와의 효율적 협업
생성형 AI(Claude, Copilot, GPT)에게는 반복적인 구현 작업을 위임하고, 저는 코드 설계와 아키텍처에 집중하여 개발 효율성을 극대화합니다.

### 3. 지속적인 학습과 공유
새로운 기술 스택을 학습할 때 동료들과의 스터디와 커뮤니티 활동을 통해 지식을 공유하고 함께 성장합니다.

## Contact

| 채널 | 연락처 |
|------|--------|
| Email | seongjuncode@gmail.com |
| GitHub | https://github.com/seongjun-working-directories |
| Phone | 010-5180-1657 |

