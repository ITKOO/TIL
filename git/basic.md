@ITKOO<br>

TIL - Git

Git 기본
===================

#### 설명

**1. git이란**

	    ●  여러명의 개발자(분산)가 특정 프로젝트를 자신의 컴퓨터로 협업하여 개발하면서 버전을 관리할 수 있는 시스템
      
        ●  프로그램 등의 소스 코드 관리를 위한 분산 버전 관리 시스템
      
  
#  
**2. 사용법**

```sh
*//처음에 git을 추가할 때* 

git init

git status  *// 빨간색 ---> 아직 올라가지 않은 상태*



git add .  *// 모든파일을 git에 추가하는 것*

git status  *// 초록색 ---> 잘올라간 상태*

git commit -m "Pratice"  *// 내가 어떠한 것을 했는지 알려주는, ex) README.md파일을 수정했다면 commit message는 "Update README.md"* 

git config --global user.email "itkoo2000@gmail.com"  *// git과 github 계정을 연동*

git config --global user.name "ITKOO"

git remote add origin https://github.com/ITKOO/php-codeigniter-study.git    *// git과 github에 있는 레파지토리를 연동시켜주는 것*

git push -u origin master  *// git에 add했던 파일들을 github 레파지토리에 푸쉬해주는 작업*


//수정한 프로젝트를 git에 올릴 때

git status  *// 빨간색 , 그 코드 들은 내가 고친 내용 담겨있음.*

git add . 

git commit -m "Add pra.html file"

git push origin master

```

**3. 참고 하면 좋을 사이트**

>https://rogerdudler.github.io/git-guide/index.ko.html

