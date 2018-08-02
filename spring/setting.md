
@ITKOO<br>

TIL - Spring

Spring MVC Project Setting
===================

- **Topic** :  Spring MVC Framework 프로젝트 설정하기
- **작업환경** :  Eclipse Oxygen
- **시작일** :  2018.07.27~

    #### 순서
    
	**1. Spring Legacy Project 생성**
	    -  프로젝트 이름 설정(첫글자 대문자 추천)
	    -  package 이름 설정

			ex) com.itkoo.web -> 여기서 web이 context 부분
			
	**2. 프로젝트 안에 있는 pom.xml 부분에 
		자바 버전 및 스프링 프레임 워크 version을 조정**
		
	**3. pom.xml 부분에 필요한 library dependency 추가**
	
	 -  mysql
	 -  spring-jdbc
	 -  mybatis
	 - mybatis-spring
	 
		 `  <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>5.1.46</version>
            </dependency> `
            
		 `   <!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
            <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>spring-jdbc</artifactId>
                <version>${org.springframework-version}</version>
            </dependency> `
	  
		 `    <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
            <dependency>
                <groupId>org.mybatis</groupId>
                <artifactId>mybatis</artifactId>
                <version>3.4.0</version>
            </dependency> `    
	            
		 `   <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis-spring -->
            <dependency>
                <groupId>org.mybatis</groupId>
                <artifactId>mybatis-spring</artifactId>
                <version>1.3.0</version>
            </dependency> `  

  	**4.  한글이 깨지는 현상을 막기 위해 web.xml에 filter, filter-mapping 추가**
		( jsp의 request.setCharacterEncoding("UTF-8"); 과 동일한 기능 )
		
	`<filter>
            <filter-name>encodingFilter</filter-name>
            <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
	    <init-param>
                  <param-name>encoding</param-name>
                  <param-value>UTF-8</param-value>
            </init-param>
      </filter>`
      
     `<filter-mapping>
            <filter-name>encodingFilter</filter-name>
            <url-pattern>/*</url-pattern>
      </filter-mapping>`
		
 	**5.  DB관련 세팅 -> root-context.xml 파일에** 
     -  dataSource( DBMS 관련 정보들, id, password 등 )
	 -  sqlSession( mybatis 와 관련 - 실제 프로젝트와 관련)
	 -  sqlSessionFactory( sqlSession 세팅에 도움을 줌 )
	 
	 ```sh
	 <bean id="dataSource"
		class="org.springframework.jdbc.datasource.DriverManagerDataSource">
		<property name="driverClassName"
			value="com.mysql.jdbc.Driver" />
		<property name="url" value="jdbc:mysql://localhost:3306/mydb?useUnicode=true&amp;characterEncoding=UTF-8" />
		<property name="username" value="root" />
		<property name="password" value="1234" />
	</bean>

	<bean id="sqlSessionFactory"
		class="org.mybatis.spring.SqlSessionFactoryBean">
		<property name="dataSource" ref="dataSource" />
		<property name="configLocation" value="classpath:/mybatis-config.xml" />
		<property name="mapperLocations" value="classpath:/mappers/**/*Mapper*.xml" />
	</bean>
	
	<bean id="sqlSession"
	class="org.mybatis.spring.SqlSessionTemplate"
	destroy-method="clearCache">
	<constructor-arg ref="sqlSessionFactory"/>
	</bean>	
	 ```
		

	**6.  root-context.xml에 sqlSessionFactory밑 mapperLocations property value 에 써놓은 폴더 이름명으로 
	src/main/resources 밑에 폴더 생성**<br>
	ex) src/main/resources/mappers 폴더 생성

	**7.  src/main/resources 밑에 mybatis-config.xml 파일 생성 및 코드 넣기**

		<configuration>
		 <typeAliases>
		            <package name="user.domain"/>
		      </typeAliases>
		  </configuration>
		



#### 만약 톰캣이 문제이거나, 디펜던시 건드렸을때 에러가 난다!

-> 이클립스를 나간 후 C:\Users\Mirim\.m2\repository 여기 안에 있는것들 모두 삭제 후 이클립스 다시 실행




### MySQL DB Tables
1. DB사용하기<br> 
`use mydb;`<br>
-> 여기서 mydb는 DB 이름

2. 테이블 생성<br>
`create table user(
id varchar(50) not null primary key,
pw varchar(50) not null,
name varchar(100) not null
);`
3. 데이터 삽입<br>
`insert into user values('aaa', 'aaa', '가가가');
insert into user values('bbb', 'bbb', '나나나');`<br>

	![vv](https://user-images.githubusercontent.com/31758135/43306411-f826236e-91b5-11e8-9ad6-d46ffd364a07.JPG)


