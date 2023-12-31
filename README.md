# helloboot
## 23-11-29
- 구성정보를 동적으로 추가할 수 있도록 MyAutoConfigImportSelector 추가
- EnableMyAutoConfiguration 어노테이션 수정 안해도 되게 만듦
- importselector에서 읽을 구성정보 파일을 외부 파일로 분리
- @Configuration(proxyBeanMethods = false) default true
- @Bean 메소드 직접 호출로 빈 의존관계 주입을 하지 않는다면 복잡한 프록시 생성을 굳이 할 필요가 없음

## 23-11-28
- 합성 어노테이션을 사용해서 myspringbootannotation 어노테이션 적용
- config 파일로 팩토리 메소드 분리해서 스프링부트 초기 화면과 비슷하게 수정
- config를 componentscan 대상에서 제외 시키도록 리패토링
- import 어노테이션으로 config 구성정보 추가
- config 분리하고 import 수정
- enableautoconfiguration 어노테이션 생성하고 import 대체
- 사용자 구성정보와 자동구성정보로 분리

## 23-11-26
- 웹 요청 테스트 코드 작성 및 검증. 서버 켜두고 실행
- 단위 테스트 코드 작성. 서버 안 켜도 실행됨. 예외 발생 테스트 코드 작성
- Decorator 기존 코드에 동적으로 책임을 추가할 때 쓰는 패턴
- primary 어노테이션으로 우선순위 지정

## 23-11-25
- 팩토리 메소드 제거 컴포넌트스캔 어노테이션 사용
- 컴포넌트 어노테이션이 붙은 클래스를 찾아서 빈으로 등록해줌
- 컴포넌트 어노테이션을 메타 어노테이션으로 갖고 있는 어노테이션으로 변경
- 커스텀 어노테이션을 만들 수 있음
- 톰캣 서블릿 팩토리와 디스패처 서블릿도 빈으로 등록 -> 스프링 컨테이너가 관리 (팩토리 메소드로 등록함)
- 스프링 컨테이너가 디스패처 서블릿에 어플리케이션컨텍스트를 자동으로 주입해줌
- main에 있는 코드를 분리하고 메인 클래스를 파라미터로 받아서 사용

## 23-11-24
- HelloService 인터페이스 생성
- 컨트롤러에 생성자 파라미터로 주입. 변수로 저장
- helloservice 타입을 빈으로 등록. 클래스 타입을 넣어서 등록해야함
- dispatcherservlet으로 변경. 프론트 컨트롤러의 기능들을 하는 서블릿 클래스를 갖고 있음
- 컨트롤러에 getmapping 어노테이션으로 매핑
- RequestMapping(value = "", method = requestmethod.GET") 와 동일
- restcontroller 어노테이션은 dispacherservlet과 관련이 별로 없음
- 디스패처가 빈 중에서 웹 요청 매핑 되어 있는 클래스를 찾아서 요청 정보 추출하고 테이블을 만들어둠
- 클래스 레벨에 RequestMapping 어노테이션을 붙여서 디스패처가 잘 찾게함
- ResponseBody 어노테이션으로 뷰 대신 스트링 리턴 가능하게 함
- RestController를 사용하면 Responsebody가 모든 메소드에 있음
- 서블릿 만들고 초기화하는 과정을 스프링컨테이너가 초기화되는 과정에 수행하도록 변경 <- 스프링부트가 이렇게 함
- 팩토리메소드를 사용해서 빈 오브젝트를 생성
- bean이 있으면 configuration 어노테이션 필요

## 23-11-22
- 스프링 컨테이너 만들기 전 코드 수정
- 스프링 컨테이너 생성 및 빈 요청
- 서비스 빈 생성 
- Objects.requireNonNull(x) 파라미터가 null인지 확인하고 아닌 것만 리턴
- DI 정리

## 23-11-21
- 서블릿 컨테이너 띄우고 서블릿 등록
- 상태 코드, 헤더, 바디를 이용해서 웹요청 생성
- 하드코딩 대신 스프링에 미리 등록된 enum으로 변경
- 요청에 파라미터 받아서 응답 생성
- 프론트 컨트롤러로 전환
- 프론트 컨트롤러에 hello컨트롤러 매핑과 바인딩

## 23-11-15
- RestController, GET
- HTTP 요청과 응답 확인
- 컨테이너 설치와 배포 등의 작업을 하지 않고 서블릿 컨테이너를 동작시키는 방법 구현하기
- 스프링 부트가 사용하는 코드 HellobootApplication에서 제거
- 톰캣 서블릿 컨테이너 실행하는 코드 작성