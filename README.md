# 박성준 (Park Seongjun)

> 사용자를 최우선으로, 기술적 문제를 해결합니다.

## 👨‍💻 About Me

- **이름**: 박성준 | Park Seongjun
- **생년월일**: 1998.10.23
- **최종학력**: 한양대학교 정보시스템학과 졸업
- **연락처**: 010-5180-1657
- **이메일**: seongjuncode@gmail.com

---

## ⚙️ Core Competencies

### Technical Understanding

**Backend**
- Spring Boot, Node.js

**Data**
- MySQL, MongoDB, Redis, Kafka

**Frontend**
- Web: React.js, Vue.js
- Desktop: Electron.js
- Mobile: Flutter

**Tools**
- Git, Docker

### Communication

- **부서 간 협업**: 기획/디자인팀과의 원활한 커뮤니케이션 및 기술 요구사항 정의
- **AI 도구 활용**: Claude, GPT를 활용한 생산성 향상 및 빠른 문제 해결
- **언어**: TOEIC Speaking Intermediate High (25.03.26)

---

## 🏆 Achievements

- 2021년 2학기 한양학업 우수상 (성적 장학금 수혜)
- 2021년 생애최초 예비창업패키지 선정 (중소벤처기업부 주관)
- 경희대학교 캠퍼 2기 예비창업팀 선정
- HY-성동 지역사회문제 해결을 위한 아이디어 - 우수 아이디어상 수상

---

## 💼 Work Experience

### 프리랜서형 미용 중개 플랫폼 - 대표 및 풀스택 개발
**예비창업팀 (7인 규모) | 2021.01 ~ 2021.12 (12개월)**

공간 임대업자-미용사-사용자 연결 중개 서비스 MVP 개발

#### 배경 및 문제 정의
- **공간 임대업자**: 유휴좌석 발생으로 고정비용 낭비 및 마케팅 부담
- **미용사**: 낮은 수익 분배(매출의 30% 이하)와 제한된 고객 접근성
- **고객**: 미용실 중심 예약 방식으로 원하는 디자이너 선택 어려움

#### 시스템 설계 및 개발

**1. 앱 아키텍처 설계**
- 3가지 사용자 타입(고객/디자이너/업주)별 플로우 설계
- 실시간 예약 및 스케줄 동기화 구조 설계

**2. 모바일 앱 개발 (Kotlin)**
- 고객용 기능: 디자이너 포트폴리오 검색, 위치 기반 검색, 실시간 예약
- 디자이너용 기능: 스케줄 관리, 수익 계산, Google Maps API 연동 이동 경로 최적화
- 업주용 기능: 유휴좌석 등록, 실시간 예약 현황 대시보드
- MVVM 패턴 기반 앱 구조 설계

**3. 백엔드 개발 (Firebase)**
- Firebase Authentication: 소셜 로그인 및 사용자 인증
- Cloud Firestore: 실시간 데이터 동기화 및 NoSQL 데이터 모델링
- Firebase Cloud Messaging: 예약 알림 푸시 시스템 구현
- Firebase Storage: 디자이너 포트폴리오 이미지 업로드 및 최적화

**4. 핵심 기능 구현**
- 실시간 예약 시스템: Firestore 실시간 리스너로 예약 충돌 방지
- 위치 기반 검색: Geohash 기반 근처 디자이너 검색 최적화
- 자동 스케줄 관리: 예약 시간 기반 자동 스케줄 생성 및 알림
- 수익 계산 대시보드: 디자이너별 일/주/월 수익 통계 시각화

#### 성과
- ✅ 2021년 생애최초 예비창업패키지 선정 (중소벤처기업부 주관)
- ✅ 경희대학교 캠퍼 2기 예비창업팀 선정 (경희대학교 캠퍼스타운 주관)
- ✅ MVP 앱 개발 완료 및 내부 테스트 진행
- ✅ 3가지 사용자 타입별 핵심 기능 구현 완료

**사용 기술**: Kotlin, Firebase (Authentication, Firestore, Cloud Messaging), Google Maps API

---

### 똑똑(주)
**벤처캐피탈 투자 관리 ERP 시스템 풀스택 개발 (인턴) | 2022.07 ~ 2022.08 (2개월)**

#### 배경 및 문제 정의
- VC 기업들이 노후화된 ERP 시스템 사용 중
- 투자 관련 정보가 Email, Excel, PDF, Paper 등으로 분산 관리
- 디지털 전환 필요성 도출: 업무 효율성 개선 및 데이터 통합 필요

#### 시스템 설계 및 개발

**1. 프론트엔드 개발**
- Vue.js 3 Composition API 기반 SPA 구축
- TypeScript 도입으로 타입 안정성 확보
- Bootstrap 5 기반 반응형 UI 컴포넌트 개발
- 사용자 관리, 투자 현황, 법인 등기 관리 페이지 구현

**2. 백엔드 개발**
- Fastify.js 기반 RESTful API 설계 및 구현
- 멀티 DB 전략 설계
  - MySQL: 투자 정보, 법인 데이터 등 관계형 데이터 관리
  - MongoDB: 문서 파일, 비정형 데이터 저장
  - Redis: 세션 관리 및 자주 조회되는 데이터 캐싱
- TypeORM을 활용한 데이터베이스 쿼리 최적화

**3. 실시간 알림 시스템 구현**
- Redis Pub/Sub 패턴으로 이벤트 기반 알림 시스템 설계
- SMTP 연동으로 이메일 알림 자동 발송

**4. 자동화 워크플로우 개발**
- 법인 등기 정보 수집 자동화: 반복 업무 자동화로 수작업 시간 단축

**5. 프로젝트 관리 및 배포**
- Monorepo 구조로 프론트엔드/백엔드 통합 관리
- 공통 유틸리티 및 타입 정의 재사용으로 코드 중복 최소화
- 개발/프로덕션 환경 분리

#### 성과
- ✅ 분산 데이터 → 단일 ERP 시스템 통합으로 데이터 접근성 향상
- ✅ 법인 등기 서류 자동화로 반복 업무 시간 단축
- ✅ TypeScript 도입으로 유지보수성 개선

**사용 기술**: Vue.js, TypeScript, Fastify.js, MySQL, MongoDB, Redis, Bootstrap 5

---

### 코가로보틱스(주)
**로봇 센서 캘리브레이션 자동화 시스템 개발 (인턴) | 2022.09 ~ 2023.02 (6개월)**

#### 배경 및 문제 정의
- 코가로보틱스 자율주행 솔루션 사업본부에서 서빙 로봇 및 자율주행 휠체어의 센서 캘리브레이션 자동화 시스템 개발
- 생산팀/연구팀이 로봇 센서(RGB-D Camera, 2D LiDAR) 조립 후 수작업으로 30분 이상 캘리브레이션 수행
- 센서별 위치/자세 측정에서 병목 발생, 작업자마다 측정값 편차로 품질 일관성 문제
- 로봇 URDF 파일 수동 수정으로 인한 휴먼 에러 빈번

#### 기술 구현 및 디지털 전환

**1. 센서별 자동 측정 알고리즘 개발**
- RGB Camera: ArUco 마커 기반 6-DOF 포즈 자동 추정
- RGB-D Camera: 체스보드 패턴 + 깊이 정보 융합으로 밀리미터 단위 정밀 측정
- 2D LiDAR: ICP 알고리즘 기반 스캔 매칭으로 위치 자동 계산
- ROS C++로 센서 데이터 처리 및 좌표 변환 알고리즘 구현
- OpenCV와 PCL 라이브러리 활용한 컴퓨터 비전 처리

**2. 실시간 모니터링 시스템 구축**
- Vue.js 기반 웹 GUI로 센서 이미지 스트리밍 및 6-DOF 데이터 시각화
- Node.js 백엔드로 ROS와 웹 브라우저 간 실시간 통신 구현
- Electron + Vue.js 기반 ROS GUI Viewer 개발 (로봇 맵 시각화)

**3. 자동화 워크플로우**
- 캘리브레이션 결과를 URDF 파일로 자동 생성 및 전송
- Rviz 연동으로 실시간 결과 검증

#### 성과
- ✅ 작업 시간 30분 → 5분 이내로 83% 단축
- ✅ 측정 정확도 향상 및 품질 일관성 확보
- ✅ 생산팀/연구팀 업무 효율 개선 및 휴먼 에러 제거

**사용 기술**: ROS C++, Vue.js, Node.js, OpenCV, PCL, Ubuntu 20.04, Rviz, Electron

**문서**: [calibration-room 설명 문서](https://github.com/seongjun-working-directories/seongjun-working-directories/blob/main/docs/calibration-room.md)

---

## 📁 Key Projects

### 1. Tax Canvas - AI 기반 세무 판례 검색 서비스
**세무법인정성 | 2023.08 ~ 2023.10**

#### 서비스 배경
세무사가 유사 판례 검색에 수 시간 소요, 방대한 법령/판례/예규 자료를 수작업으로 검색

#### 핵심 기능 개발

**1. AI 쟁점 분석 시스템**
- OpenAI API를 활용한 자연어 기반 세무 쟁점 자동 분석
- 사실관계 입력 → 쟁점 도출 → AI 분석 → 결과 제공 파이프라인 구현
- 토큰 사용량 추적 및 과금 시스템 개발 (Personal: 40k, Team: 100k)

**2. 벡터 검색 엔진 구축**
- MongoDB Vector DB 기반 의미적 유사도 검색 시스템 구현
- 법령, 판례, 예규 통합 검색 기능
- 실시간 검색 결과 필터링 및 정렬 알고리즘

**3. 인증 및 보안 시스템**
- Passport.js + JWT 기반 소셜 로그인 (Google, Naver OAuth 2.0)
- CoolSMS API 연동 SMS 인증 시스템 (일일 10회 제한, 5분 만료)
- IP 기반 접근 제어 (사용자당 최대 2개 IP 등록)
- Class Validator를 활용한 입력 데이터 검증

**4. 팀 협업 시스템**
- 팀 생성, 초대, 권한 관리 기능 구현
- Nodemailer(Gmail SMTP) 활용 HTML 템플릿 기반 초대 이메일 발송
- 월별 토큰 사용량 추적 및 팀원별 사용 내역 관리

**5. 고객 지원 시스템**
- 문의 유형별 분류 및 파일 첨부 지원 (최대 20MB, 다양한 포맷)
- 자동 이메일 알림 및 답변 완료 시 첨부 파일 자동 삭제

**6. 프론트엔드 구현**
- React + TypeScript로 타입 안전성을 갖춘 컴포넌트 기반 UI 개발
- Styled Components 기반 재사용 가능한 디자인 시스템 구축

**7. 개발 환경 구축**
- Winston Logger로 구조화된 로깅 시스템 구축
- Swagger를 활용한 REST API 문서 자동화
- 통합 에러 핸들러로 일관된 에러 응답 처리

#### 성과
- ✅ 판례 검색 시간 수 시간 → 1시간 이내로 단축
- ✅ 세무사 업무 효율성 대폭 개선
- ✅ AI 기반 자동 쟁점 분석으로 정확도 향상

**사용 기술**: TypeScript, Express.js, React.js, MongoDB, OpenAI API

**문서**: [tax-canvas 설명 문서](https://github.com/seongjun-working-directories/seongjun-working-directories/blob/main/docs/tax-canvas.md)

---

### 2. Market Follower - 암호화폐 모의 투자 플랫폼
**2025.07 ~ 2025.09 (3개월)**

#### 서비스 배경
암호화폐 투자자들이 실전 투자 전 연습할 수 있는 안전한 환경 필요

#### 핵심 기능 개발

**1. 실시간 데이터 파이프라인 구축**
- Kafka Producer/Consumer 아키텍처로 코인 데이터 실시간 수집
- 10초마다 시세/호가 데이터를 Kafka 토픽으로 발행 및 소비
- Redis 캐싱(TTL: 3분)으로 API 응답 속도 밀리초 단위 달성
- WebSocket(STOMP) 기반 실시간 브로드캐스팅 시스템 구현

**2. 차트 데이터 관리 시스템**
- 5개 기간대별(7일/30일/3개월/1년/5년) 캔들 데이터 수집 및 저장
- 당일 5분봉 데이터를 Redis에 실시간 업데이트 (5분마다)
- Spring Scheduler로 일일 캔들 데이터 동기화 및 정리 자동화
- 총 600코인 * 5개 기간 유형 = 약 50만 레코드 효율적 관리

**3. 가상 거래 엔진 개발**
- 실제 거래소와 동일한 매수/매도/체결 로직 구현
- 호가창 기반 주문 매칭 알고리즘 (5초마다 체결 조건 확인)
- 비관적 락으로 동시성 제어 및 데이터 정합성 보장
- 개인별 WebSocket 채널로 주문 체결 실시간 알림
- 평균 매수가 자동 계산 및 포트폴리오 업데이트

**4. 인증 및 보안 시스템**
- Spring Security + JWT 기반 Stateless 인증 구현
- Google OAuth 2.0 소셜 로그인 연동
- Role-Based Access Control(RBAC)로 권한 관리
- AES-256 암호화로 민감 정보 보호

**5. 인프라 및 CI/CD**
- Docker Compose로 Spring Boot, MySQL, Redis, Kafka 멀티 컨테이너 환경 구성
- GitHub Actions CI/CD 파이프라인 구축 (빌드 → 도커 이미지화 → AWS EC2 배포)
- GitHub Container Registry로 도커 이미지 관리
- AWS EC2 t3.medium 인스턴스 기반 무중단 배포

#### 성과
- ✅ 600개 코인 실시간 데이터를 10초마다 안정적으로 처리
- ✅ Redis 캐싱으로 평균 50ms 이하 API 응답 속도 달성
- ✅ Kafka 기반 초당 10,000 메시지 처리 가능한 확장 가능한 아키텍처 구축
- ✅ WebSocket 최대 5,000 동시 연결 지원
- ✅ 비관적 락 기반 동시성 제어로 거래 데이터 정합성 보장

**사용 기술**: Spring Boot, MySQL, Redis, Kafka, WebSocket, Docker

**GitHub**: [market-follower 설명 문서](https://github.com/seongjun-working-directories/seongjun-working-directories/blob/main/docs/tax-canvas.md)

---

### 3. 사공사(sagongsa) - 쇼핑 최저가 검색 앱
**포스트랩(주) | 2023.06 ~ 2023.08**

#### 서비스 배경
여러 쇼핑몰의 가격 비교를 위한 모바일 앱 수요, 일관된 디자인 시스템 필요

#### 구현 내용
- 간편한 검색 → 최저가 비교 → 구매 전환까지의 플로우 최적화
- Flutter 기반 전체 디자인 시스템 설계 및 구현
- Figma를 사용한 디자인 시스템 및 컴포넌트 단위 품질 보증
- 앱 성능 최적화 및 로딩 시간 단축
- 플랫폼별 네이티브 기능 통합(Android/iOS) 및 권한 처리
- 테스트 코드 작성 및 Flutter Test/Widget Test를 통한 안정성 검증

#### 성과
- ✅ 구글플레이 1만+ 다운로드 달성 기여
- ✅ UI/UX 품질 보증으로 사용자 만족도 향상 기여

**사용 기술**: Figma, Flutter (Dart)

---

## 📖 Service Philosophy

### 1. 기술 도입의 명확한 목적 설정
새로운 기술을 도입할 때 그 의도와 목적을 명확히 파악하고, 프로젝트에 최적화된 방식으로 적용합니다.

### 2. AI와의 효율적 협업
생성형 AI(Claude, Copilot, GPT)에게는 반복적인 구현 작업을 위임하고, 저는 코드 설계와 아키텍처에 집중하여 개발 효율성을 극대화합니다.

### 3. 지속적인 학습과 공유
새로운 기술 스택을 학습할 때 동료들과의 스터디와 커뮤니티 활동을 통해 지식을 공유하고 함께 성장합니다.

---

## 📞 Contact

- **Email**: seongjuncode@gmail.com
- **GitHub**: [github.com/seongjun-working-directories](https://github.com/seongjun-working-directories)
- **Phone**: 010-5180-1657
