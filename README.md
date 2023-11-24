# helloboot
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