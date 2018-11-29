@ITKOO<br>

TIL - jsoup crawler

Jsoup을 이용한 크롤러
===================

- **Topic** :  Spring를 이용한 크롤러 제작을 위한 세팅과정
- **시작일** :  2018.11.28~

#### 설명

**1. Spring Framework 설치**

	    ●  https://spring.io/tools3/sts/all/ 에 접속해 Spring Tool Suite를 설치
      
	    ●  압축해제 후 환경세팅(테마, 폰트 ,,,) - 반드시 Java가 기본세팅되어있어야함
	    
	    ●  STS에서 Spring Starter Project를 생성한 후 src/main/java 밑 com.example.XXX 밑에 코드작성
	    
![image](https://user-images.githubusercontent.com/31758135/49138651-19691980-f333-11e8-910a-fe92f7c2c359.png)

      
Q. Spring이란?
	    
●  Java플랫폼을 위한 오픈소스 어플리케이션 프레임워크(Famework)
	    
●  Java 엔터프라이즈 개발을 편하게 해주는 오픈소스 경량급 어플리케이션 

	    


#  
**2. Jsoup 다운로드**

	●  https://jsoup.org/download 에 접속해 jsoup dependency를 복사
	
	●  만들어 둔 Starter Project pom.xml에 복사한 dependency 붙여넣기
	
      
![image](https://user-images.githubusercontent.com/31758135/49138622-07877680-f333-11e8-99cc-baacab4c2449.png)


Q. jsoup이란?
	    
●   jsoup은 java html parser로써 데이터를 추출하고 조작하기 위해 사용하는 라이브러리,

DOM, CSS 구조를 이용, jquery와 비슷한 메서드를 가지고 있음.(HTML5 지원)
      
	    
