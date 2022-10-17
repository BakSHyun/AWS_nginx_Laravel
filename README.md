# AWS_nginx_Laravel
Amazon Linux 2 AMI -Kernel 5.10. 
using to nginx and Laravel

서버이 이미 각종 기능들이 포함 되어 있어, 설치가 간편하다.
키패어를 등록해두어 접속 보안에 신경쓰자, 물론 키페어 관리는 필수이다.

자동 할당된 IP 주소를 참고하여 서버에 접속한다.
ec2-user
위 아이디를 통해 접속가능하며, sudo 명령어를 통해 각종 설치 및 권한이 필요한 작업을 진행 할 수 있다.


$ amazon-linux-extras list
// 위 명령어를 통해 설치가 가능한 리스트를 확인 할 수 있다.
// 설치할 목록은 nginx, php7.2 버전이다.

// nginx 설치
$ sudo yum install nginx
//위 명령어를 기입함으로 필요한 amazon-linux-extras를 확인 할 수 있다.

$ sudo amazon-linux-extras install nginx
// nginx를 우선 설치한다.
$ sudo service nginx start
// nginx를 실행한다.
// nginx 설정 파일은 /etc/nginx/nginx.conf 참조한다.


// mysql 설치
$ sudo yum install mariadb-server
// 위 명령어를 통해 필요한 amazon-linux-extras를 확인 후 설치한다.
$ sudo service mariadb start

$ sudo vi /etc/my.cnf
// mysql 설정파일을 생성한다.

[mysqld]

port = 3306 //포트번호 기입 3306 포트 이용 시 기입하지 않아도 좋음
character-set-server = utf8mb4 //이모지 등을 다루기 위하 해당 캐릭터셋 사용
collation-server = utf8mb4_unicode_ci
character_set_server = utf8mb4
collation_server = utf8mb4_unicode_ci

//위 내용을 적고 저장

$ sudo service mariadb restart
// DB 리스타트
$ mysqladmin -u root -p password '비밀번호기입';
$ mysql -u root -p
비밀번호 기입

create database 데이터베이스이름;
//데이터베이스 생성
use mysql;
// mysql 데이버베이스로 이동

create user '아이디'@% identified by '비밀번호'; 

GRANT ALL PRIVILEGES ON DB이름.* TO '아이디'@'%'
//외부에서도 접속 할 수있게 % 설정

FLUSH PRIVILEGES;
//새로고침








