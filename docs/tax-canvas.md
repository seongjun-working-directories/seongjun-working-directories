# Tax Canvas - AI 기반 세무 유사 판례 검색 시스템

**AI-powered Tax Case Searching Service**

![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)

**세무법인정성 외주 | 2023.08 ~ 2023.10**

세무 분야 유사 판례 검색을 위한 효율적이고 혁신적인 AI 솔루션

---

## 📋 프로젝트 개요

Tax Canvas는 AI 기술을 활용하여 세무 유사 판례 검색의 효율성을 증대시킵니다.

### 핵심 가치

- **속도**: 자료검색부터 보고서 작성까지 단 30분
- **정확성**: AI 기반 쟁점 분석으로 정확한 법률 검토
- **편의성**: 직관적인 UI/UX로 누구나 쉽게 사용
- **안전성**: 강화된 보안 시스템으로 안전한 데이터 관리

### 주요 특징

- **AI 기반 쟁점 분석**: 복잡한 세무 이슈를 AI가 자동으로 분석
- **통합 법령 검색**: 관련 법령, 판례, 예규를 한 번에 검색
- **팀 협업 기능**: 팀원과 프로젝트를 공유하고 협업
- **강화된 보안**: IP 제어, SMS 인증, 소셜 로그인
- **토큰 기반 과금**: 투명하고 합리적인 사용량 기반 요금제

---

## 🛠 기술 스택

### Backend Architecture

```
Express.js Framework
├── Core Technologies
│   ├── TypeScript 4.x          # 타입 안전성
│   ├── Express.js              # 웹 프레임워크
│   ├── MongoDB 4.x             # NoSQL 데이터베이스
│   └── Mongoose ODM            # 객체 문서 매핑
│
├── Authentication & Security
│   ├── Passport.js             # 인증 미들웨어
│   ├── JWT Strategy            # 토큰 기반 인증
│   ├── Class Validator         # 입력 데이터 검증
│   └── IP-based Access Control # IP 기반 접근 제어
│
├── External Services
│   ├── CoolSMS API             # SMS 인증
│   ├── Nodemailer (Gmail)      # 이메일 서비스
│   ├── Google OAuth 2.0        # 구글 소셜 로그인
│   └── Naver OAuth 2.0         # 네이버 소셜 로그인
│
└── Utilities
    ├── Winston Logger          # 구조화된 로깅
    ├── Swagger Documentation   # API 문서화
    └── Custom Error Handler    # 통합 에러 처리
```

### Frontend Architecture

```
React Ecosystem
├── Core Framework
│   ├── React 18.x              # 컴포넌트 기반 UI
│   ├── TypeScript 4.x          # 타입 안전성
│   ├── React Router 6.x        # 클라이언트 라우팅
│   └── React Hooks             # 상태 관리
│
├── Styling & UI
│   ├── Styled Components       # CSS-in-JS
│   ├── Custom Design System    # 일관된 디자인
│   ├── Responsive Design       # 모바일 최적화
│   └── Lucide React Icons      # 아이콘 라이브러리
│
├── State Management
│   ├── React State Hooks       # 로컬 상태 관리
│   ├── Context API             # 전역 상태 공유
│   └── LocalStorage            # 클라이언트 저장소
│
└── HTTP & Data
    ├── Axios                   # HTTP 클라이언트
    ├── React Query (예정)      # 서버 상태 관리
    └── Form Validation         # 폼 데이터 검증
```

---

## 프로젝트 구조

### Backend Structure

```
src/
├── app.module.ts                  # 루트 모듈 - 모든 모듈의 진입점
├── main.ts                        # 애플리케이션 부트스트랩
│
├── modules/
│   ├── user/                      # 사용자 관리 모듈
│   │   ├── dto/                   # 데이터 전송 객체
│   │   │   ├── user.dto.ts        # 사용자 생성 DTO
│   │   │   ├── user-read.dto.ts   # 사용자 조회 DTO
│   │   │   ├── user-update.dto.ts # 사용자 수정 DTO
│   │   │   ├── user-code.dto.ts   # 소셜 로그인 DTO
│   │   │   └── user-ip.dto.ts     # IP 관리 DTO
│   │   ├── schema/
│   │   │   └── user.schema.ts     # MongoDB 스키마
│   │   ├── user.controller.ts     # REST API 엔드포인트
│   │   ├── user.service.ts        # 비즈니스 로직
│   │   └── user.module.ts         # 모듈 정의
│   │
│   ├── team/                      # 팀 관리 모듈
│   │   ├── dto/
│   │   │   ├── team.dto.ts        # 팀 생성 DTO
│   │   │   └── team-update.dto.ts # 팀 수정 DTO
│   │   ├── schema/
│   │   │   ├── team.schema.ts     # 팀 스키마
│   │   │   └── team.invitation.schema.ts # 팀 초대 스키마
│   │   ├── team.controller.ts
│   │   ├── team.service.ts
│   │   └── team.module.ts
│   │
│   ├── mobile/                    # SMS 인증 모듈
│   │   ├── dto/
│   │   │   ├── mobile-send.dto.ts # SMS 발송 DTO
│   │   │   └── mobile-verify.dto.ts # SMS 인증 DTO
│   │   ├── schema/
│   │   │   └── mobile.schema.ts   # SMS 인증 기록 스키마
│   │   ├── mobile.controller.ts
│   │   ├── mobile.service.ts      # CoolSMS 연동
│   │   └── mobile.module.ts
│   │
│   ├── qna/                       # 고객센터 모듈
│   │   ├── dto/
│   │   │   └── qna.dto.ts         # 문의 접수 DTO
│   │   ├── schema/
│   │   │   └── qna.schema.ts      # 문의 스키마
│   │   ├── qna.controller.ts      # 파일 업로드 지원
│   │   ├── qna.service.ts
│   │   └── qna.module.ts
│   │
│   ├── mailer/                    # 이메일 서비스 모듈
│   │   ├── mailer.service.ts      # Gmail SMTP 연동
│   │   └── mailer.module.ts
│   │
│   ├── logger/                    # 로깅 모듈
│   │   ├── logger.service.ts      # Winston 커스텀 로거
│   │   └── logger.module.ts
│   │
│   └── common/                    # 공통 유틸리티
│       ├── util.ts                # 시간, 랜덤 생성 등
│       ├── error.ts               # 에러 핸들링
│       └── common.module.ts
│
├── config/
│   └── default.config.ts          # 환경 설정 (API 키, DB 연결 등)
│
└── swagger/
    └── swagger.ts                 # API 문서화 설정
```

### Frontend Structure

```
src/
├── pages/                         # 페이지 컴포넌트
│   ├── home/
│   │   ├── Home.tsx               # 랜딩 페이지
│   │   └── HomeStyle.tsx          # 스타일드 컴포넌트
│   │
│   ├── search/
│   │   └── SearchPage.tsx         # 세무 분석 메인 페이지
│   │
│   ├── feedback/
│   │   ├── Feedback.tsx           # 피드백 수집 페이지
│   │   └── UserFeedback.tsx       # 고객센터 문의 페이지
│   │
│   ├── settings/                  # 설정 관리
│   │   ├── PaymentPage.tsx        # 결제 관리
│   │   ├── PlanPage.tsx           # 요금제 관리
│   │   ├── TeamSettingPage.tsx    # 팀 설정
│   │   └── TokenHistoryPage.tsx   # 토큰 사용 내역
│   │
│   └── user/                      # 사용자 관련 페이지 (예정)
│
├── components/                    # 재사용 가능한 컴포넌트
│   ├── guides/                    # 기본 UI 컴포넌트
│   │   ├── button/                # 버튼 컴포넌트
│   │   ├── form/                  # 폼 컴포넌트
│   │   ├── modal/                 # 모달 컴포넌트
│   │   ├── dropdown/              # 드롭다운 컴포넌트
│   │   ├── textarea/              # 텍스트 영역
│   │   ├── checkbox/              # 체크박스
│   │   ├── chip/                  # 칩 컴포넌트
│   │   └── navbar/                # 내비게이션
│   │
│   ├── search/                    # 세무 분석 전용 컴포넌트
│   ├── settings/                  # 설정 관련 컴포넌트
│   └── modal/                     # 커스텀 모달
│
├── styles/                        # 글로벌 스타일
│   ├── color.ts                   # 컬러 팔레트
│   ├── typography.ts              # 타이포그래피
│   └── shadow.ts                  # 박스 섀도우
│
└── assets/                        # 정적 리소스
    ├── icons/                     # SVG 아이콘
    ├── images/                    # 이미지
    └── main/                      # 메인 페이지 이미지
```

---

## 상세 기능 가이드

### 1. 인증 및 보안 시스템

#### 소셜 로그인 플로우

```
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant Social
    
    User->>Frontend: 로그인 버튼 클릭
    Frontend->>Social: OAuth 인증 요청
    Social->>Frontend: Authorization Code 반환
    Frontend->>Backend: /user/signin/code
    Backend->>Social: Access Token 요청
    Social->>Backend: 사용자 정보 반환
    Backend->>Frontend: 사용자 데이터 + 가입 여부
    Frontend->>User: 로그인 완료 / 회원가입 유도
```

#### IP 기반 접근 제어

- **제한**: 사용자당 최대 2개의 IP 주소 등록 가능
- **자동 추가**: 새로운 IP에서 접근 시 자동으로 추가 (2개 미만인 경우)
- **IP 교체**: 3번째 IP 접근 시 기존 IP 중 하나를 선택하여 교체
- **보안 검증**: 모든 API 요청에서 등록된 IP 여부 확인

#### SMS 인증 시스템

- **발송 제한**: 동일 번호당 일일 10회 제한
- **만료 시간**: 인증번호 5분 후 자동 만료
- **재전송**: 만료 후 새로운 인증번호 발송 가능
- **검증**: 신규 사용자와 기존 사용자 구분 검증

---

### 2. 팀 관리 시스템

#### 팀 생성 및 관리

```typescript
// 팀 스키마 구조
{
  id: string;                    // 2자리 알파벳 + 8자리 숫자
  administrators: string[];      // 관리자 이메일 목록
  name: string;                  // 팀명
  plan: 'personal' | 'team';     // 요금제
  phoneNumber: string;           // 대표 연락처
  address: string;               // 주소
  registrationNumber: string;    // 사업자등록번호
  tokens: Array<{                // 월별 토큰 사용량
    date: string;                // "2024-01" 형식
    basic: number;               // 기본 제공 토큰
    additional: number;          // 추가 사용 토큰
  }>;
  history: Array<{               // 사용 내역
    date: string;                // 사용 날짜
    token: number;               // 사용 토큰량
    consumer: string;            // 사용자 이메일
  }>;
}
```

#### 팀 초대 시스템

- **초대 코드**: 랜덤 생성된 고유 코드
- **이메일 발송**: HTML 템플릿 기반 초대 이메일
- **만료 관리**: 초대 코드 만료 시간 관리
- **권한 부여**: 초대 수락 시 팀 멤버 권한 자동 부여

---

### 3. 세무 분석 시스템

#### AI 쟁점 분석 프로세스

1. **사실관계 입력**: 의뢰 건의 구체적인 사실 관계 입력
2. **쟁점 도출**: 주요 쟁점을 사용자가 직접 입력
3. **AI 분석**: 입력된 쟁점에 대한 AI 기반 분석 수행
4. **결과 제공**: 관련 법령, 판례, 예규와 분석 결과 제공
5. **저장 관리**: 분석 결과를 프로젝트별로 저장 및 관리

#### 토큰 시스템

- **기본 제공**: 월별 기본 토큰 할당 (Personal: 40k, Team: 100k)
- **사용량 추적**: 실시간 토큰 사용량 모니터링
- **과금 체계**: 초과 사용 시 추가 요금 부과
- **내역 관리**: 상세한 사용 내역 및 결제 예정 금액 제공

---

### 4. 고객 지원 시스템

#### 문의 처리 플로우

```typescript
// 문의 접수 데이터 구조
{
  type: '로그인 및 계정' | '서비스 이용' | '건의사항' | '기타';
  email: string;                 // 문의자 계정 이메일
  content: string;               // 문의 내용
  receiverEmail: string;         // 답변 받을 이메일
  agreeCollectingData: boolean;  // 개인정보 수집 동의
  files?: Array<File>;           // 첨부 파일 (선택)
}
```

#### 파일 업로드 지원

- **지원 형식**: jpg, gif, psd, png, tif, zip, pdf, ms office, hwp
- **용량 제한**: 최대 20MB
- **자동 삭제**: 답변 완료 시 첨부 파일 자동 삭제
- **보안**: 바이러스 검사 및 파일 타입 검증

---

## 설치 및 구성 가이드

### 개발 환경 설정

#### 시스템 요구사항

```bash
# Node.js 버전 확인
node --version  # v16.0.0 이상 필요

# MongoDB 설치 확인
mongod --version  # v4.4 이상 권장

# Git 설치 확인
git --version
```

#### 프로젝트 클론 및 초기 설정

```bash
# 저장소 클론
git clone https://github.com/your-org/taxcanvas.git
cd taxcanvas

# 브랜치 확인
git branch -a

# 의존성 설치
npm install

# 환경 설정 파일 생성
cp .env.example .env
```

---

### 데이터베이스 설정

#### MongoDB 설정

```typescript
// config/default.config.ts
export const configurations = {
  // 로컬 개발환경
  mongodb: {
    uri: 'mongodb://localhost:27017/taxcanvas',
    options: {
      useNewUrlParser: true,
      useUnifiedTopology: true,
    }
  },
  
  // 프로덕션 환경 (MongoDB Atlas)
  mongodb_production: {
    uri: 'mongodb+srv://username:password@cluster.mongodb.net/taxcanvas',
    options: {
      retryWrites: true,
      w: 'majority',
    }
  }
};
```

#### 필수 컬렉션 생성

```bash
# MongoDB 콘솔 접속
mongo

# 데이터베이스 선택
use taxcanvas

# 인덱스 생성
db.users.createIndex({ email: 1 }, { unique: true })
db.users.createIndex({ phoneNumber: 1 }, { unique: true })
db.teams.createIndex({ id: 1 }, { unique: true })
db.mobiles.createIndex({ phoneNumber: 1, requestTimestamp: 1 })
```

---

### API 키 설정

#### 소셜 로그인 설정

```typescript
// config/default.config.ts
export const configurations = {
  // Google OAuth 2.0
  google: {
    key: 'your-google-client-id',
    secret: 'your-google-client-secret',
    redirectUri: 'http://localhost:3000/auth/google/callback'
  },
  
  // Naver OAuth 2.0
  naver: {
    key: 'your-naver-client-id',
    secret: 'your-naver-client-secret',
    redirectUri: 'http://localhost:3000/auth/naver/callback'
  },
  
  // Kakao OAuth 2.0 (개발 중)
  kakao: {
    key: 'your-kakao-client-id',
    secret: 'your-kakao-client-secret',
    redirectUri: 'http://localhost:3000/auth/kakao/callback'
  }
};
```

#### CoolSMS 설정

```typescript
// SMS 인증 서비스 설정
coolSms: {
  key: 'your-coolsms-api-key',
  secret: 'your-coolsms-api-secret',
  sender: 'your-registered-phone-number'  // 발신번호 등록 필요
}
```

#### Gmail SMTP 설정

```typescript
// 이메일 서비스 설정
googleEmail: {
  key: 'your-gmail-address@gmail.com',
  app: 'your-gmail-app-password'  // 2단계 인증 필요
}
```

---

### 서버 실행

#### Backend 서버

```bash
# 개발 모드 실행
npm run start:dev

# 프로덕션 모드 빌드
npm run build
npm run start:prod

# 테스트 실행
npm run test
npm run test:e2e
```

#### Frontend 서버

```bash
# React 개발 서버 실행
cd frontend
npm start

# 프로덕션 빌드
npm run build

# 빌드된 앱 서빙
npm install -g serve
serve -s build
```

---

## 보안 및 성능

### 보안 기능

#### 입력 데이터 검증

```typescript
// DTO 검증 예시
export class UserDto {
  @IsNotEmpty()
  @IsEmail()
  email: string;

  @IsNotEmpty()
  @Length(2, 50)
  name: string;

  @IsNotEmpty()
  @Matches(/^010-\d{4}-\d{4}$/)
  phoneNumber: string;
}
```

#### IP 접근 제어

```typescript
// IP 검증 로직
async checkIpAccess(email: string, currentIp: string): Promise<boolean> {
  const user = await this.userModel.findOne({ email });
  if (!user) return false;
  
  const allowedIps = user.ips.map(ip => ip.ip);
  return allowedIps.includes(currentIp);
}
```

#### 에러 처리

```typescript
// 통합 에러 핸들러
export function errorHandler(
  error: any,
  response: Response,
  defaultStatus: number = 500
) {
  const status = error.status || defaultStatus;
  const message = error.message || 'Internal Server Error';
  
  response.status(status).json({
    statusCode: status,
    message: message,
    timestamp: new Date().toISOString(),
  });
}
```

---

### 성능 최적화

#### 데이터베이스 최적화

```javascript
// 인덱스 설정
db.users.createIndex({ email: 1 }, { unique: true })
db.users.createIndex({ phoneNumber: 1 }, { unique: true })
db.mobiles.createIndex({ phoneNumber: 1, requestTimestamp: 1 })
db.teams.createIndex({ id: 1 }, { unique: true })

// 복합 인덱스
db.qnas.createIndex({ email: 1, requestedAt: -1 })
```

#### 캐싱 전략

```typescript
// Redis 캐싱 예시
@Injectable()
export class CacheService {
  async get(key: string): Promise<any> {
    // Redis GET 구현
  }

  async set(key: string, value: any, ttl: number): Promise<void> {
    // Redis SET 구현
  }
}
```

---

## Contact

문의사항이나 추가 정보가 필요하신 경우 연락 주시기 바랍니다.

- **Email**: seongjuncode@gmail.com
- **GitHub**: [seongjun-working-directories](https://github.com/seongjun-working-directories)
- **Phone**: 010-5180-1657
