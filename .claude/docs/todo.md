# TODO List

## Feature: 로그인/회원가입 기능

### DB 작업
- [ ] User 모델 생성
  - [ ] 필드 정의 (id, username, email, password_hash, created_at, updated_at)
  - [ ] 유니크 제약조건 설정 (username, email)
- [ ] User CRUD 함수 작성
  - [ ] create_user (회원 생성)
  - [ ] get_user_by_email (이메일로 조회)
  - [ ] get_user_by_username (사용자명으로 조회)
  - [ ] get_user_by_id (ID로 조회)

### BE 작업
- [ ] 인증 관련 의존성 설치
  - [ ] python-jose[cryptography] (JWT 토큰)
  - [ ] passlib[bcrypt] (비밀번호 해싱)
  - [ ] python-multipart (폼 데이터)
- [ ] 비밀번호 해싱 유틸리티 작성
  - [ ] hash_password 함수
  - [ ] verify_password 함수
- [ ] JWT 토큰 유틸리티 작성
  - [ ] create_access_token 함수
  - [ ] verify_token 함수
  - [ ] get_current_user 의존성
- [ ] 회원가입 API 엔드포인트
  - [ ] POST /api/auth/register
  - [ ] Pydantic 스키마 정의 (UserCreate, UserResponse)
  - [ ] 이메일/사용자명 중복 체크
  - [ ] 비밀번호 해싱 후 저장
- [ ] 로그인 API 엔드포인트
  - [ ] POST /api/auth/login
  - [ ] Pydantic 스키마 정의 (LoginRequest, TokenResponse)
  - [ ] 사용자 인증 (이메일/비밀번호 확인)
  - [ ] JWT 토큰 발급
- [ ] 인증 확인 API 엔드포인트
  - [ ] GET /api/auth/me
  - [ ] JWT 토큰 검증
  - [ ] 현재 사용자 정보 반환

### FE 작업
- [ ] 인증 관련 타입 정의
  - [ ] User 인터페이스
  - [ ] LoginRequest 인터페이스
  - [ ] RegisterRequest 인터페이스
  - [ ] AuthResponse 인터페이스
- [ ] API 호출 함수 작성
  - [ ] /api/auth.ts 파일 생성
  - [ ] login(email, password) 함수
  - [ ] register(username, email, password) 함수
  - [ ] getMe() 함수 (현재 사용자 정보)
  - [ ] logout() 함수
- [ ] 인증 상태 관리
  - [ ] AuthContext 생성
  - [ ] useAuth 훅 작성
  - [ ] 토큰 저장/삭제 로직 (localStorage)
  - [ ] 자동 로그인 체크 (페이지 로드 시)
- [ ] 로그인 페이지
  - [ ] /login 라우트 생성
  - [ ] 로그인 폼 UI (이메일, 비밀번호)
  - [ ] 폼 유효성 검증
  - [ ] 로그인 API 호출
  - [ ] 에러 처리 및 메시지 표시
  - [ ] 로그인 성공 시 리다이렉트
- [ ] 회원가입 페이지
  - [ ] /register 라우트 생성
  - [ ] 회원가입 폼 UI (사용자명, 이메일, 비밀번호, 비밀번호 확인)
  - [ ] 폼 유효성 검증 (비밀번호 강도, 이메일 형식 등)
  - [ ] 회원가입 API 호출
  - [ ] 에러 처리 및 메시지 표시
  - [ ] 가입 성공 시 로그인 페이지로 이동
- [ ] 네비게이션/헤더 컴포넌트
  - [ ] 로그인 상태에 따른 UI 변경
  - [ ] 로그인 전: 로그인/회원가입 버튼
  - [ ] 로그인 후: 사용자 정보 표시, 로그아웃 버튼
- [ ] 보호된 라우트 구현
  - [ ] ProtectedRoute 컴포넌트 또는 미들웨어
  - [ ] 미인증 사용자 로그인 페이지로 리다이렉트

---

## 작업 순서 (권장)
1. DB 작업 (db-agent) - User 모델 및 CRUD
2. BE 작업 (be-agent) - 인증 API 엔드포인트
3. FE 작업 (fe-agent) - 로그인/회원가입 UI 및 연동
