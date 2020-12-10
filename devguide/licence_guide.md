# 라이센스 가이드

UCARE 의 라이센스 내용을 설명합니다.

### 서버 라이센스
  - 다음의 정보로 서버 라이센스 Key 를 생성하여, 라이센스 파일에 라이센스 Key 를 입력한다.
    - 서버 IP
    - Max 사용자 수
    - 라이센스 유효일자
  - 라이센스 파일명은 `ucareLicense.dat` 이며, `WEB-INF/classes/config/ucareLicense.dat` 에 파일을 위치한다.
  - 라이센스 Key 에는 유효일자, Max 사용자수, 서버 라이센스 Key 정보 포함
  - 서버 Key 는 서버 IP 를 `SHA512` 로 암호화
  - 서버 라이센스 Key 가 유효하지 않은 경우, 서버 Start 에서 Exception 발생하여, 서버가 실행되지 않는다.
  - 다음의 파일은 아래와 같은 역할을 한다.
    - MakeUcareLicence : 라이센스 Key 생성
    - UcareLicense : 서버 Start 에서 서버 라이센스 Check
    - LicenseCryptoUtil : 라이센스 암호화 처리
    
<br />

### 사용자 라이센스
  - 사용자 ID 로 사용자 라이센스 Key 를 생성
  - tb_sys_user_m.USER_LCNS_KEY 컬럼에 사용자 라이센스 KEY 입력
  - 사용자 생성 시, Max 사용자를 초과하면 사용자 추가 불가
  - 로그인 시, 사용자 라이센스 Key 검증
  - 사용자 Key 는  검증값 + 사용자 ID를 `SHA512` 암호화
  - 사용자 라이센스 Key 가 유효하지 않은 경우, 로그인 불가
  - 다음의 파일은 아래와 같은 역할을 한다.
    - UcareLicense.getUserLicenseKey : 사용자 라이센스 Key 생성
    - UcareLicense.getUserVerificationValue : 사용자 라이센스 검증
