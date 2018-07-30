@ITKOO<br>

TIL - Spring

Spring MVC Project Basic
===================

- **Topic** :  Spring MVC Framework의 기본 흐름 알아보기
- **작업환경** :  Eclipse Oxygen
- **시작일** :  2018.07.30~

#### Q. Spring MVC에서 유저가 학생목록을 한번 조회할려면 밑 과정을 거쳐야합니다. 이과정들은 무엇일까요?
![sdd](https://user-images.githubusercontent.com/31758135/43382880-32d9c2e4-9414-11e8-9a1c-84ec2a7bd8f5.png)


**1. DispatcherServlet**

```sh
웹 애플리케이션의 맨 앞에서 사용자의 요청을 받아들여여 URL을 기준으로 요청을 처리할 Controller를 
정해진 XML에서 찾고 그 Controller에 처리를 위임하고 결과를 받아서 사용자에게 처리 결과가 담긴 화면 제공
.
.
.
**쉽게 말해서 누가 어떤일을 할 지 알고있는것! (딱 알고만 있는다.)**
그래서 어떠한 일이 발생하면 그 일을 잘 처리할 수 있는 곳에 전달한다.

ex) 홈플러스 푸드코트에서 돈까스와 짜장면 주문이 들어오면
    돈까스는 일식집에
    짜장면은 중식집에 
    연결하는것.
``` 
```sh
이 DispatcherServlet 설정은 web.xml 파일에서 설정함!
```


**2. context-mvc.xml**

```sh
DispatcherServlet에게 
사용자의 요청을 처리할 수 있는 Controller 목록과, 
사용자에게 보여줄 화면 URL을 만드는 ViewResolver
정보를 제공
``` 
![default](https://user-images.githubusercontent.com/31758135/43383795-12b7bc70-9417-11e8-9a3d-89d3be8834e9.JPG)

```sh
이 context-mvc.xml 설정은 servlet-context.xml 파일에서 설정함!
```

**2. Controller**

```sh
DispatcherServlet에 의해 호출되어 사용자의 Request(요청)를 전달받고, 
해당 요청의 비즈니스 처리를 담당하는 서비스 객체를 Spring으로부터 주입(Dependency Injection)받아서,
그 서비스 객체에 처리를 위임하고, 처리 결과와 결과 화면에 대한 정보를 DispatcherServlet에게 반환한다.

ex) 음식 접수대에서
    돈까스를 받으면 
    -> 일식부분에서 주문을 확인(일식이 맞는지 아닌지)
    -> 일식이 나오면 일식이라는 태그 부착
    
    짜장면을 받으면
    -> 중식부분에서 주문을 확인(중식이 맞는지 아닌지)
    -> 중식이 나오면 중식이라는 태그 부착
    
``` 
![dt](https://user-images.githubusercontent.com/31758135/43384316-9e87f476-9418-11e8-937f-b06261b6a7b1.JPG)

```sh
@Controller, @RequestMapping, @Autowired
서비스 처리 결과를 Model에 담으면, 컨트롤러 클래스의 RequestMapping값(/student)과 
핸들러 메서드의 RequestMapping값(/list)을 기준으로,
DispatcherServlet이 ViewResolver를 통해 화면 URL 생성
```	   
