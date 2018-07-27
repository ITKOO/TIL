TIL - Spring
===================



----------


@ITKOO<br>
Spring MVC Project Setting
-------------
- **Topic** :  Spring MVC Framework ������Ʈ �����ϱ�
- **�۾�ȯ��** :  Eclipse Oxygen
- **������** :  2018.07.27~

    #### <i class="icon-folder-open"></i> ����
    
	1. Spring Legacy Project ����
	    -  ������Ʈ �̸� ����(ù���� �빮�� ��õ)
	    -  package �̸� ����

			ex) com.itkoo.web -> ���⼭ web�� context �κ�
			
	2. ������Ʈ �ȿ� �ִ� pom.xml �κп� 
		�ڹ� ���� �� ������ ������ ��ũ version�� ����
		
	3. pom.xml �κп� �ʿ��� library dependency �߰�
	
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

  4.  �ѱ��� ������ ������ ���� ���� filter, filter-mapping �߰�
		( jsp�� request.setCharacterEncoding("UTF-8"); �� ������ ��� )
		
		` <filter>
            <filter-name>encodingFilter</filter-name>
            <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
            <init-param>
                  <param-name>encoding</param-name>
                  <param-value>UTF-8</param-value>
            </init-param>
      </filter>   `
      
		` <filter-mapping>
            <filter-name>encodingFilter</filter-name>
            <url-pattern>/*</url-pattern>
      </filter-mapping> `
		
 5.  DB���� ���� -> root-context.xml ���Ͽ� 
     -  dataSource( DBMS ���� ������, id, password �� )
	 -  sqlSession( mybatis �� ���� - ���� ������Ʈ�� ����)
	 -  sqlSessionFactory( sqlSession ���ÿ� ������ �� )
	 
		 	`<bean id="dataSource"
            class="org.springframework.jdbc.datasource.DriverManagerDataSource">
            <property name="driverClassName" value="com.mysql.jdbc.Driver" />
            <property name="url" value="jdbc:mysql://localhost:3306/mydb? 
            useUnicode=true&;characterEncoding=UTF-8" />
            <property name="username" value="root" />
            <property name="password" value="1234" />
      </bean> 
			`
` <bean id="sqlSessionFactory"
            class="org.mybatis.spring.SqlSessionFactoryBean">
            <property name="dataSource" ref="dataSource" />
            <property name="configLocation" value="classpath:/mybatis-config.xml" />
            <property name="mapperLocations" value="classpath:/mappers/**/*Mapper*.xml" />
			`
`  <bean id="sqlSession" 
class="org.mybatis.spring.SqlSessionTemplate" 
destroy-method="clearCache">
      <constructor-arg ref="sqlSessionFactory"/>
      </bean> 
			`

6.  root-context�� property value �� ����� ���� �̸������� 
	src/main/resources �ؿ� ���� ����
	ex) src/main/resources/mappers ���� ����

7.  src/main/resources �ؿ� mybatis-config.xml ���� ���� �� �ڵ� �ֱ�

		`<configuration>
		 <typeAliases>
		            <package name="user.domain"/>
		      </typeAliases>
		  </configuration>
		`



#### <i class="icon-refresh"></i> ���� ��Ĺ�� �����̰ų�, ������� �ǵ������ ������ ����!

-> ��Ŭ������ ���� �� C:\Users\Mirim\.m2\repository ���� �ȿ� �ִ°͵� ��� ���� �� ��Ŭ���� �ٽ� ����




### MySQL DB Tables
1. DB����ϱ� 
`use mydb;`
-> ���⼭ mydb�� DB �̸�

2. ���̺� ����
`create table user(
id varchar(50) not null primary key,
pw varchar(50) not null,
name varchar(100) not null
);`
3. ������ ����
`insert into user values('aaa', 'aaa', '������');
insert into user values('bbb', 'bbb', '������');`

	id    | pw | name
	-------- | ---
	aaa | aaa | ������
	bbb    | bbb | ������


