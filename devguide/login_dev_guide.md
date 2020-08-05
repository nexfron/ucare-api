# 로그인 개발 가이드

UCARE 의 로그인 프로그램을 Customize 하기 위한 내용을 설명합니다.

### Login 관련 소스

| 구분 | 경로 |
|:---:|:---:|
| `java` | com\nexfron\core\web\login|
| `jsp` | WEB-INF\jsp\login\login.jsp|


### Login 관련 설정 및 변경
`global.properties` 에서 다음과 같은 설정이 필요

| 속성 | 설명 |
|:---:|:---:|
| CONFIG.PRJ.LOGIN.PATH | 로그인 URL PATH |
| CONFIG.PRJ.MAIN.PAGE | Main 화면 구성을 위한 layout name |

```
# 로그인 Path
CONFIG.PRJ.LOGIN.PATH=/login.do
# 메인화면 layout
CONFIG.PRJ.MAIN.PAGE=layout-main
```

 - Login Path 변경  
   1. `global.properties` 의 `CONFIG.PRJ.LOGIN.PATH` 를 변경  
      ```
      # 로그인 Path
      CONFIG.PRJ.LOGIN.PATH=/ucare/login.do
      ```   
   2. `LoginController.java` 의 RequestMapping 변경
      ```java
      @Controller
      @RequestMapping(value="ucare/login")
      public class LoginController {
        ...
      }
      ```

 - Main 화면layout 변경
   1. `global.properties` 의 `CONFIG.PRJ.MAIN.PAGE` 를 변경  
      ```
      # 메인화면 layout
      CONFIG.PRJ.MAIN.PAGE=layout-main-ucare
      ```   
   2. `tiles.xml` 의 definition 변경  
      ```xml
      <definition name="layout-main-ucare" template="/WEB-INF/tiles/ucare/layout-main-ucare.jsp">
        <put-attribute name="mainTop" value="/WEB-INF/tiles/ucare/mainTop.jsp" />
        <put-attribute name="mainLeft"   value="/WEB-INF/tiles/ucare/mainLeft.jsp" />
        <put-attribute name="mainBody"   value="/WEB-INF/tiles/mainBody.jsp" />
      </definition>
      ```

### Login VO property 추가
  - Login Query 는 `Login.xml` 의 `selectLogin` 에 정의되어 있습니다. Login Query 를 프로젝트 상황에 맞게 변경하여 사용할 수 있습니다.
  - `LoginDVO` 는 `UcareBaseLoginDVO` 를 상속하여 구현되어 있습니다. Login Query 변경으로 VO 파일 변경이 필요하면, `LoginDVO` 에 property 를 추가하여 사용할 수 있습니다.
    ```java
      // Property(부서) 추가 예제

      @Alias("loginDVO")
      public class LoginDVO extends UcareBaseLoginDVO implements Serializable {
        ...
        private String dept; // 부서

        public String getDept() {
          return dept;
        }

        public void setDept(String dept) {
          this.dept = dept;
        }
        
        ...
      }    
    ```
  - `UcareBaseLoginDVO` 의 default 이외 property 는 `LoginDVO` 에 추가하여 사용합니다.

### Session 정보 property 추가
  - `SessionVO` 는 `SessionCoreVO` 를 상속하고, `UserSessionInfo` 는 `UserSessionInfoCore` 를 상속하여 구현되어 있습니다. 
  - Session 에 property 의 추가가 필요한 경우, `SessionVO`, `UserSessionInfo` 를 수정하여 사용할 수 있습니다.

  ```java
    // SessionVO property 추가 - 부서
    public class SessionVO extends SessionCoreVO {
      ...
      private String dept;

      public String getDept() {
        return dept;
      }

      public void setDept(String dept) {
        this.dept = dept;
      }
      ...
    }
  ```

  ```java
    // UserSessionInfoCore property 추가 - 부서  
    public class UserSessionInfo extends UserSessionInfoCore {
      ...
      public String getDept() {
        SessionCoreVO sessionVO = getSessionCore(UserSessionInfoCore.USER_KEY);

        return (null == sessionVO)? "":sessionVO.getDept();        
      }
      ...
    }
  ```

### 사용자 비밀번호 암호화 변경
  - 사용자 비밀번호 암호화는 `SHA512` 를 기본으로 하고 있습니다. 
  - 사용자 비밀번호 암호화 방법을 변경하는 경우, Login 처리 시   `LoginController.java` 의 `getEncryptPassword` 메소드에서 프로젝트에 맞게 암호화 방법을 변경해야 합니다.
  - 비밀번호 암호화 방법은 사용자 Table 의 비밀번호 암호화와 동일하게 구현되어야 합니다. 
  ```java
    @Override
    public String getEncryptPassword(UcareBaseLoginPVO loginPVO, UcareBaseLoginDVO loginDVO) {
      String encryptPassword = "";

      ...
      encryptPassword = CryptoUtil.encrypt("SHA256", decryptPassword, passwordSalt);
      ...
      return encryptPassword;
    }
  ```