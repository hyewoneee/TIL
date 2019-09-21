# 가장 빨리 만나는 DocKer
Link : http://pyrasis.com/docker.html

# 목차
- [x] 1장. Docker
- [x] 2장. Docker 설치하기
- [x] 3장. Docker 사용해보기
- [x] 4장. Docker 이미지 생성하기
- [x] 5장. Docker 살펴보기
- [x] 6장. Docker 좀더 활용하기
- [x] 7장. Docker file 자세히 알아보기
- [x] 8장. Docker로 애플리케이션 배포하기
- [x] 9장. Docker 모니터링 하기
- [ ] 10장. Amazon Web Services에서 Docker 사용하기
- [ ] 11장. Google Cloud Platform에서 Docker 사용하기
- [ ] 12장. Microsoft Azure에서 Docker 사용하기
- [x] 13장. Docker Hub 사용하기
- [x] 14장. Docker Remote API 사용하기
- [ ] 15장. CoreOS 사용하기
- [ ] 16장. Docker로 워드프레스 블로그 구축하기
- [ ] 17장. Docker로 Ruby on Rails 애플리케이션 구축하기
- [ ] 18장. Docker로 Django 애플리케이션 구축하기
- [x] 19장. Docker 활용 시나리오

--- 
# 1장. 가상머신과 Docker

##  가상 머신 단점
편하긴 하지만 성능이 좋지 못한 것

지금까지 CPU에 가상화를 위한 기능들이 많이 추가되었지만 아직도 가상 머신은 리얼머신에 비해 속도가 느림

가상 머신 자체는 완전한 컴퓨터라 항상 게스트 OS를 설치해야 함

그래서 이미지 안에 OS가 포함되기 때문에 이미지 용량이 커진다.

## DocKer
OS를 설치하지 않는다.

Dokcer 이미지에 서버 운영을 위한 프로그램과 라이브러리만 격리해서 설치 가능하고, OS 자원(시스템 콜)은 호스트와 공유하며 이미지 용량이 크게 줄었다.

Docker는 하드웨어를 가상화하는 계층이 없기 때문에 메모리 접근, 파일시스템, 네트워크 속도가 가상 머신에 비해 월등히 빠르다.

Docker는 가상 머신과 달리 이미지 생성과 배포에 특화된 기능을 제공

- 이미지 버전 관리 기능 제공(Git에서 소스를 관리하는 것처럼)
- 중앙 관리를 위해 저장소에 이미지를 올리고, 받을 수 있다(Push/Pull)
- DocKer 이미지를 공유할 수 있는 DocKerHub도 제공(GitHub 처럼)

Docker는 특정 실행 파일 또는 스크립트를 위한 실행환경
시스템 구조가 단순해지고 명확해지는 장점이 있지만 의존성 관계를 해결하기가 어려워지는 단점이 있다

## 리눅스 컨테이너
유닉스/리눅스 환경은 **chroot** 제공

**chroot**는 디렉터리 경로를 격리하기 때문에 서버 정보 유출과 피해를 최소하는데 주로 사용

리눅스는 LXC(LinuX containder)라는 시스템 레벨 가상화를 제공

LXC는 컴퓨터를 통째로 가상화하여 OS를 실행하는 것이 아닌 리눅스 커널 레벨에서 제공하는 일종의 격리(Isolate)된 가상 공간

가상 공간에는 OS가 설치되지 않기 때문에 가상 머신이라 하지 않고, 컨테이너라 부름

리눅스 커널의 Control Groups(cgroups)는 CPU, 메모리, 디스크, 네트워크 자원을 할당하여 완전한 형태의 가상 공간을 제공

### Namespace isolation(namespaces)
프러세스 트리, 사용자 계정, 파일시스템,  IPC 등을 격리시켜 호스트와 별개의 공간

LXC는 리눅스 커널의 cgroups와 namespace 기능을 활용하여 가상공간을 제공 

LXC는 격리된 공간만 제공할 뿐 개발 및 서버 운영에 필요한 부가 기능이 부족

Docker는 리눅스 커널의  cgroups와 namespaces를 기반으로 하여 이미지, 컨테이너 생성 및 관리 기능과 다양한 부가 기능을 제공

---
# 2장. Docker 설치하기
## 리눅스
### 자동 설치 스크립드
	$ sudo wget -qO- https://get.docker.com/ | sh
	
	get.docker.com 스크립트로 Docker를 설치하면 hello-world 이미지도 자동으로 설치됩니다. hello-world 이미지는 사용하지 않을 것이므로 모두 삭제합니다.
	
	$ sudo docker rm `sudo docker ps -aq`
	$ sudo docker rmi hello-world 
### 우분투
	$ sudo apt-get update
	$ sudo apt-get install docker.io
	$ sudo ln -sf /usr/bin/docker.io /usr/local/bin/docker
	
	/usr/bin/docker.io 실행 파일을 /usr/local/bin/docker로 링크해서 사용

### Mac OS X

다음 URL에서 docker-install.exe를 받음
https://docs.docker.com/toolbox/toolbox_install_windows/

	VirtualBox와 Git을 따로 설치하려면 다음 주소에서 파일을 받은 뒤 설치하면 됨
	VirtualBox: https://www.virtualbox.org
	Git: ht	tp://git-scm.com
---

# 3장. Docker 사용해보기
Docker 명령어 `docker <명령>` 형식

항상 root 권한으로 실행

**sudo 입력하지 않기**

- docker 명령은 root 권한으로 실행해야 하기 때문에 일반 계정에서는 항상  sudo 사용
- sudo를 입력하지 않는 방법

	처음부터 root계정으로 로그인하거나 
	sudo su 명령을 사용하여 root 계정으로 전환
	$ sudo su
	
	현재 계정을 docker 그룹에 포함(docker 그룹은 root 권한과 동일하므로 꼭 필요한 계정에만 포함)
	$ sudo usermd -aG docker ${USER}
	$ sudo service docker restart
	
	현재 계정에서 로그아웃한 뒤 다시 로그인
### pull 명령으로 이미지 받기 
Docker Hub에서 우분투 리눅스 이미지 받기
	lastest를 설정하면 최신 버전을 받을 수 있다
	ubuntu:14.04처럼 태그를 지정해 줄 수 있다
	$ sudo docker pull ubuntu:latest
`docker pull <이미지 이름(ID)>:<태그>` 형식

### images 명령으로 이미지 목록 출력하기
	$ sudo docker images
	REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
	docker-registry.29cm.co.kr/apis/checkplus   v43.dev             ca1de88c7bfa        4 days ago          1.38GB
	docker-registry.29cm.co.kr/apis/checkplus   v44.dev             ca1de88c7bfa        4 days ago          1.38GB
	ubuntu                                      latest              3556258649b2        12 days ago         64.2MB
`docker images` 명령은 모든 이미지 목록을 출력 
`docekr images ubuntu` 처럼 이미지 이름을 설정하면 이름은 같지만 태그가 다른 이미지가 출력
### run 명령으로 컨테이너 생성
	ubuntu 이미지를 컨테이너로 생성한 뒤 ubuntu 이미지 안의 /bin/bash를 실행
	이미지 이름 대신 이미지 ID를 사용해도 됨
	$ sudo docker run -i -t --name hello ubuntu /bin/bash
	root@a7f75c7b59de:/#
`docker run <옵션> <이미지 이름> <실행할 파일` 형식
- `-i`(interactive), `-t` (Pseudo-tty) 옵션을 사용하면 실행된 Bash 셸에 입력 및 출력을 할 수 있음
- `--name` 옵션으로 컨테이너의 이름을 지정할 수 있다.
    - 이름을 지정하지 않으면 Docker가 자동으로 이름을 생성하여 지정
### ps 명령으로 컨테이너 목록 확인
	모든 컨테이너 목록을 출력
	$ sudo docker ps -a
    
    ONTAINER ID        IMAGE                                               COMMAND                  CREATED             STATUS                      PORTS                    NAMES
    a7f75c7b59de        ubuntu                                              "/bin/bash"              5 minutes ago       Exited (0) 48 seconds ago                            hello
    
    # 컨테이너 생성 시 hello로 지정했으므로 컨테이너 목록에서도 hello로 표시
`docker ps` 형식
- `-a` 옵션을 사용하면 정지된 컨테이너까지 모두 출력
- 옵션을 사용하지 않으면 실행되고 있는 컨테이너만 출력
### start 명령으로 컨테이너 시작
	$ sudo docker start hello
	hello
`docekr start <컨테이너 이름(ID)>` 
### restart 명령으로 컨테이너 재시작
	$ sudo docker restart hello
	hello
`docker restart <컨테이너 이름(ID)>` 형식
### attach 명령으로 컨테이너에 접속하기 
다음 명령을 실행한 뒤 엔터 한번 입력하면 Bash 셸이 표시
	$ docker attach hello
	root@a7f75c7b59de:/#
`docker attach <컨테이너 이름(ID)>` 형식
`/bin/bash`를 실행했기 때문에 명령을 자유롭게 입력할 수 있지만. DB나 서버 애플리케이션을 실행하면 입력은 할 수 없고 출력만 보게 된다
### exec 명령으로 외부에서 컨테이너 안의 명령 실행하기
 `/bin/bash`를 통하지 않고 외부에서 컨테이너 안의 명령 실행
	$ docker exec hello echo "Hello World"
	Hello World
`docker exec <컨테이너 이름(ID)><명령><매개 변수>` 형식
`docker exe` 명령은 이미 실행된 컨테이너에 `apt-get`, `yum` 명령으로 패키지를 설치하거나, 각종 데몬을 실행할 때 활용할 수 있음

### stop 명령으로 컨테이너 정지하기
	$ docker stop hello
`docker stop <컨테이너 이름(ID)>`
### rm 명령으로 컨테이너 삭제하기
	docker rm hello
`docker rm <컨테이너 이름(ID)> `
`docker rmi ubuntu` 처럼 이미지 이름만 지정하면 태그는 다르지만 `ubuntu` 이름을 가진 모든 이미지가 삭제됨

### 컨테이너를 삭제하기 전에 이미지를 삭제할 경우
	$ docker rmi -f [IMAGE ID]
---
# 4장. Docker 이미지 생성하기
### Dockerfile 작성하기
Dockerfile은 Docker 이미지 설정 파일

	$ mkdir example
	$ cd example

Dockerfile 생성

	FROM ubuntu:14.04
	MAINTAINER Foo Bar <foo@bar.com>
	RUN apt-get update
	RUN apt-get install -y nginx
	RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf
	RUN chown -R www-data:www-data /var/lib/nginx
	
	VOLUME ["/data", "/etc/nginx/site-enabled", "/var/log/nginx"]
	
	WORKDIR /etc/nginx
	    
	CMD ["nginx"]
	    
	EXPOSE 80
	EXPOSE 443
우분투 14.04를 기반으로 nginx 서버를 설치한 Docker 이미지를 생성하는 예제

- FROM: 어떤 이미지를 기반으로 할지 설정
- Docker 이미지는 기존에 만들어진 이미지를 기반으로 생성
- `<이미지 이름>:<태그>` 형식
- MAINTAINER: 메인테이너 정보
- RUN: 셸 스크립트 혹은 명령을 실행
    - 이미지 생성 중에는 사용자 입력을 받을 수 없으므로 apt-get install 명령에서 `-y` 옵션을 사용(yum install도 동일).
    - 나머지는 nginx 설정
    - VOLUME: 호스트와 공유할 디렉터리 목록입
    - `docker run` 명령에서 `-v` 옵션으로 설정가능
        - ex) `-v /root/data:/data`는 호스트의 **/root/data** 디렉터리를 Docker 컨테이너의 **/data** 디렉터리에 연결
- CMD: 컨테이너가 시작되었을 때 실행할 실행 파일 또는 셸 스크립트
- WORKDIR: CMD에서 설정한 실행 파일이 실행될 디렉터리
- EXPOSE: 호스트와 연결할 포트 번호
### build 명령으로 이미지 생성하기
	~/example$ docker build --tag test:0.1 .
	~/example$ docker imamges
	REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
	test                                        0.1                 38923ae29368        6 seconds ago       223MB

`docker bulid <옵션> <Dockerfile 경로> 형식`
`--tag` 옵션으로 이미지 이름과 태그를 설정
이미지 이름만 설정하면 태그는 `latest` 로 설정
### 실행
	$ docker run --name test-nginx -d -p 80:80 -v /root/data:/data test:0.1
- `-d` 옵션은 컨테이너를 백그라운드로 실행
- `-p 80:80` 옵션으로 **호스트의 80번 포트**와 **컨테이너의 80번 포트**를 연결하고 외부에 노출
- 이렇게 설정한 뒤 **http://<호스트 IP>:80**에 접속하면 컨테이너의 **80**번 포트로 접속
- `-v /root/data:/data` 옵션으로 호스트의 **/root/data** 디렉터리를 컨테이너의 **/data** 디렉터리에 연결합니다. **/root/data** 디렉터리에 파일을 넣으면 컨테이너에서 해당 파일을 읽음
---
# 5장. Docker 살펴보기
### history 명령으로 이미지 히스토리 살펴보기
	IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
	38923ae29368        3 minutes ago       /bin/sh -c #(nop)  EXPOSE 443                   0B
	6257469ebb45        3 minutes ago       /bin/sh -c #(nop)  EXPOSE 80                    0B
	a0987a8878ee        3 minutes ago       /bin/sh -c #(nop)  CMD ["nginx"]                0B
	11716480557a        3 minutes ago       /bin/sh -c #(nop) WORKDIR /etc/nginx            0B
	d143d6c9ce87        3 minutes ago       /bin/sh -c #(nop)  VOLUME [/data /etc/nginx/…   0B
	89eb1f80ee2c        3 minutes ago       /bin/sh -c chown -R www-data:www-data /var/l…   0B
	4339d4cfc039        3 minutes ago       /bin/sh -c echo "\ndaemon off;" >> /etc/ngin…   1.61kB
	b83e316b72e8        3 minutes ago       /bin/sh -c apt-get install -y nginx             20.9MB
	6dc0de774514        3 minutes ago       /bin/sh -c apt-get update                       13.4MB
	19d892025f3f        3 minutes ago       /bin/sh -c #(nop)  MAINTAINER Foo Bar <foo@b…   0B
	2c5e00d77a67        2 months ago        /bin/sh -c #(nop)  CMD ["/bin/bash"]            0B
`docker history <이미지 이름(ID)>:<태그>` 형식
### cp 명령으로 파일 꺼내기
	$ docker cp test-nginx:/etc/nginx/nginx.conf ./
`docker cp <컨테이너 이름>:<경로> <호스트 경로>` 형식
현재 디렉터리에  `nginx.conf` 파일 복사
### commit 명령으로 컨테이너 변경사항을 이미지로 생성하기
`docker commit`  명령은 컨테이너의 변경 사항을 이미지 파일로 생성

	hello-nginx 컨테이너 안의 파일 내용이 바뀌었다 치고, 컨테이너를 이미지 파일로 생성
	$ docker commit -a "Foo Bar <foo@bar.com>" -m "add hello.txt" test-nginx test:0.2

`docker commit <옵션> <컨테이너 이름(ID)> <이미지 이름>:<태그>` 형식
`-a "Foo Bar <foo@bar.com>"과 -m "add test.txt"` 옵션으로 커밋한 사용자와 로그 메시지를 설정
**test-nginx** 컨테이너를 **test:0.2** 이미지로 생성

	// test:0.2 이미지 생성
	docker images
	REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
	test                                        0.2                 d4489f7e07df        12 seconds ago      223MB
	test                                        0.1                 38923ae29368        3 days ago          223MB

### diff 명령으로 컨테이너에서 변경된 파일 확인하기
`docker diff` 명령은 컨테이너 실행되면서 변경된 파일 목록을 출력
비교 기준은 컨테이너를 생성한 이미지 내용

	docker diff test-nginx
	C /etc
	C /etc/nginx
	A /etc/nginx/site-enabled
	A /data
	C /run
	A /run/nginx.pid
	C /var
	C /var/lib
	C /var/lib/nginx
	A /var/lib/nginx/body
	A /var/lib/nginx/fastcgi
	A /var/lib/nginx/proxy
	A /var/lib/nginx/scgi

`docker diff <컨테이너 이름(ID)>` 
`A`는 추가된 파일, `C` 는 변경된 파일, `D` 는 삭제된 파일

### inspect 명령으로 세부 정보 확인하기
`docker inspect` 명령은 이미지와 컨테이너의 세부 정보를 출력
`docker inspect <이미지(이미지 ID) 또는 컨테이너(컨테이너 ID) 이름>`
A /var/lib/nginx/uwsgi

---
# 6. Docker 좀더 활용하기
## Docker  개인 저장소 구축하기
Docker 저장소 서버는 Docker 레지스트리(registry) 서버라고 부름.
`docker push` 명령으로 레지스트리 서버에 이미지를 올리고,
`docker pull` 명령으로 이미지를 받을 수 있다.
Docker 레지스트리가 동작하는 서버에 저장하는 방법과  Amazon S3에 저장하는 방법을 설명
	먼저 기존에 실행되고 있는 Docker 데몬을 정지한 뒤 --insecure-segistry 옵션을 사용하여 Docker 데몬을 실행
	sudo sservice docker stop
	docker -d --insecure-registry localhost:5000

보통 Docker 데몬을 직접 실행하지 않고 서비스 형태로 실행
이때는 /etc/init.d/docker 파일의 DOCKER_OPTS 부분을 다음과 같이 설정(이 파일은 root 권한으로 수정해야한다)
	/etc/init.d/docker
	DOCKER_OPTS=--insecure-registry localhost:5000

Docker 1.8.0 이후부터는 `docker -d` 옵션이 `docker daemon` 명령으로 바뀜
### 로컬에 이미지 데이터 저장
Docker 레지스트리 서버도 Docker Hub를 통해 Docker 이미지로 제공된다.
먼저 Docker 레지스트리 이미지를 받는다.

	docker pull registry:latest
	
	docker run -d -p 5000:5000 --name hello-registry \
	    -v /tmp/registry:/tmp/registry \
	    registry
	
	15d09d97e73cd24c8c00c2f752daa162f6f619a71e42c6fe7eda34c7331ba273

이렇게 실행하면 이미지 파일은 호스트의 **/tmp/registrt** 디렉터리에 저장된다.
### push 명령으로 이미지 올리기
test:0.1 이미지를 개인 저장소에 올리기

	docker tag test:0.1 localhost:5000/test:0.1
	docker push localhost:5000/test:0.1

태그를 생성하는 명령어

`docker tag <이미지 이름>:<태그> <Docker 레지스트리 URL>/<이미지 이름>:<태그>` 형식

이미지 올리는 명령어

`docker push <Docker 레지스트리 URL>/<이미지 이름>:<태그>`


개인 저장소에 이미지를 올릴 때는 태그를 먼저 생성

`docker tag` 명령으로 `test:0.1` 이미지를 [localhost:5000/test:0.1](http://localhost:5000/test:0.1) 태그로 생성

그리고 `docker push` 명령으로 [localhost:5000/test:0.1](http://localhost:5000/test:0.1) 이미지를 개인 저장소에 올림(태그를 생성했으므로 실제로는 test:0.1 이미지가 올라감)


이제 다른 서버에서 개인 저장소(Docker 레지스트리 서버)에 접속하여 이미지를 받아 올 수 있다.
	docker pull ip/test:0.1

### Docker 컨테이너 연결하기
Docker 컨테이너끼리 연결할 때는 `docker run` 명령에서  `--link` 옵션을 사용

	mongo DB를 사용하여 DB 이미지를 컨테이너로 실행
	(docker run 명령은 로컬에 이미지가 없으면 자동으로 이비지를 받아온다)
	
	docker run --name db -d mongo

DB 컨테이너 이름은 db로 설정 

web 컨테이너를 생성하면서 db 컨테이너와 연결 

웹 서버로 사용할 컨테이너는 nginx 이미지로 생성

	docker run --name web -d -p 80:80 --link db:db nginx

docker run 명령에서 연결 옵션은 `--link <컨테이너 이름>:<별칭>`

	docker ps -a
	CONTAINER ID        IMAGE                                               COMMAND                   CREATED             STATUS                     PORTS                         NAMES
	7a1b5ef0d5fe        nginx                                               "nginx -g 'daemon of…"    3 minutes ago       Created                                                  web
	fb7d2e4a097d        mongo                                               "docker-entrypoint.s…"    6 minutes ago       Up 6 minutes               27017/tcp                     db

**db** 컨테이너와 **web** 컨테이너가 연결됨

**web/db**라고 표시되는데 **web** 컨테이너에서 **db** 컨테이너에 접속할 수 있다는 것임

이제 **web** 컨테이너 안에서 `db:27017` 주소로 **db** 컨테이너의 MongoDB에 접속할 수 있다.

	mongodb://db:27017/exampledb

컨테이너 안에서 다른 컨테이너에 접속할 때는 `<별칭>:<포트번호>` 형식으로 사용

네트워크를 생성하고 컨테이너를 연결시키면 해당 네트워크 안에 속한 컨테이너끼리 서로 접속할 수 있다.

`docker network create` 명령으로 hello-network 생성

	docker network create hello-network
	438d1e96379f08b121740b3699d3122c1a23c369035ddb27d6af4b228421ff20

DB 컨테이너를 생성하면서 hello-network에 연결

	docker run --name db -d --network hello-network mongo
	121bcb1cc89db9075e3c8468700cd932991230724b096e96fbe16567d736b88c

web 컨테이너를 생성하면서 hello-network에 연결

	sudo docker run --name web -d -p 80:80 --network hello-network nginx
	e9a5c375749d228834dccf1606acf6db907420369ff667a5964dc17e1e28b911

web 컨테이너에서 Bash 셸을 실행한 뒤에 ping을 실행

	docker exec -it web bash
	root@e9a5c375749d:/# ping db
	
	₩bash: ping: command not found₩ 흠...
	이렇게 같은 네트워크에 속한 컨테이너끼리는 컨테이너 이름으로 접속할 수 있다.

### 다른 서버의 Docker 컨테이너에 연결

`--link` 옵션은 같은 서버의 컨테이너끼리 연결하는 옵션

이번에는 앰배시더 컨테이너(Ambassador Container) 라는 것을 이용하여 다른 서버에 있는 컨테이너에 연결

앰배시더 컨테이너는 특별한 컨테이너가 아닌 그냥 일반적인 Docker 컨테이너

앰배시더 컨테이너는 socat 이라는 프로그램을 이용하여 TCP 연결을 다른 곳으로 전달하도록 구성

`docker run` 명령을 실행할 때 전달한 환경 변수를 이용하여 socat을 실행하는 셸 스크립트

	CMD env | grep _TCP= | \
	    sed 's/.*_PORT_\([0-9]*\)_TCP=tcp:\/\/\(.*\):\(.*\)/socat \
	TCP4-LISTEN:\1,fork,reuseaddr TCP4:\2:\3 \&/'  \
	    | sh && top

`docker run` 명령에서 `--link` 옵션을 사용하거나 `-e EXAMPLE_PORT_1234_TCP=tcp://192.168.0.10:1234` 라고 설정 해주면 다음과 같이 환경 변수에 포트 정보가 설전된다.

`env` 명령으로 환경 변수를 출력하고 

`grep` 명령으로 *_TCP*=를 포함하는 문자열을 찾음.

`sen` 명령으로 정규표현식을 사용하여 문자열에서 포트 번호와 IP 주소를 추출

추출한 포트 번호와 IP  주소룰을 이용하여 soct 명령을 실행

	EXAMPLE_PORT=tcp://192.168.0.10:1234
	EXAMPLE_PORT_1234_TCP_ADDR=192.168.0.10
	EXAMPLE_NAME=/example_ambassador/example
	HOSTNAME=0cf479687cb0
	EXAMPLE_PORT_1234_TCP_PORT=1234
	HOME=/
	EXAMPLE_PORT_1234_TCP_PROTO=tcp
	EXAMPLE_PORT_1234_TCP=tcp://192.168.0.10:1234
	TERM=xterm
	PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
	PWD=/

**앰배서터 패턴(Ambassador Pattern)란**

- 위 예제의 환경에서 `socat` 명령으로 로컬의 TCP 프로토콜 1234번 포트를 192.168.0.10 의 1234번 포트로 데이터를 전달하도록 설정하는 것
- 컨테이너에서 포트를 노출시키러면 해당  서버의 IP 주소나 도메인을 알아야한다.
- 이렇게 되면 작성한 애플리케이션의 소스 레벨에서 IP주소나 도메인을 설정해주어야 한다.
- 앰배서더 컨데이너를 이용하면 별칭으로 접근하므로 서버의 IP주소, 도메인이 바뀌어도 소스 수정하지 않아도 된다.
- 즉 외부에 있는 서버라도 같은 서버의 Docker 내부망에 있는 것과 같은 효과가 난다.

**socat**

**SOcket** **CAT**을 뜻하며 소켓 통신을 다른 채널로 전달하는 프로그램

- 채널
    - 파일, 파이프, 장치(시리얼, pseudo 터미널 등), 소켓(유닉스 소켓, TCP, UDP 등)이 있다.

앰배시터 컨테이너를 이용해서 다른 서버의 컨테이너에 연결해 보겠다. 

원활한 테스트를 위해 Redis를 사용하겠다.

	docker pull redis:latest
	docker run -d --name redis redis:latest
	dd8388a1619882bd0fd79606020b860d857fc726fdfb8ded6c61c41eeca408cf

`--name redis` 옵션으로 컨테이너 이름을 **redis**로 지정

	Redis 컨테이너를 위해 앰배서더 컨테이너 생성
	docker run -d --link redis:redis --name redis_ambassador \
	    -p 6379:6379 svendowideit/ambassador

`-d` 옵션으로 컨테이너를 백그라운드로 실행

`--link redis:redis` 옵션으로 **redis** 컨테이너를 **redis** 별칭으로 연결

`--name redis_ambassador` 옵션으로 컨테이너 이름을 `redis_ambassador`로 지정

`p 6379:6379` 옵션으로 컨테이너의 **6379**번 포트와 호스트의 **6379** 연결하고 외부에 노출한다.

Docker Hub에 있는 svendowideit/ambassador 이미지를 받은 뒤 컨테이너로 생성(docker run 명령은 로컬에 이미지가 없으면 자동으로 이미지를 받아온다.)

	Redis 클라이언트를 사용할 컴퓨터에서 앰배서더 컨테이너 생성
	Redis 서버의 IP 주소는 192.168.0.10
	
	docker run -d --name redis_ambassador --expose 6379 \
	    -e REDIS_PORT_6379_TCP=tcp://192.168.0.10:6379 svendowideit/ambassador
	3a8872a37856a5116e9209d945d3875d76656ed840a1007cfb90ae6aa410ea01


`--name redis_ambassador` 옵션으로 컨테이너 이름을 **redis_ambassador**로 지정

`--expose 6379` 옵션으로 다른 컨테이너에서 6379번 포트에 연결할 수 있도록 설정

즉 Redis 클라리언트가 이 redis_ambassador 컨테이너의 6379 포트에 접속하게 된다.

`--expose` 옵션은 `-p` 옵션과는 달리 호스트의 포트를 외부에 노출하지 않는다.

`-e REDIS_POST_6379_TCP=tcp://192.168.0.10:6379` 옵션으로 IP 주소와 포트를 설정하여 다른 서버에 있는 redis_ambassador  컨테이너에 연결

Docker Hub에 있는 svendowideit/ambassador 이미지 받은 뒤 컨테이너로 실행

Docker Hub에 Redis 클라이언트만 들어있는 컨테이너도 있다.

이 컨테이너를 이용하여 redis_amassador 컨테이너에 접속

	docker run -i -t --rm --link redis_ambassador:redis relateiq/redis-cli

`-i` `-t` 옵션으로 콘솔에서 입출력을 할 수 있도록 설정

`--rm` 옵션으로 컨테이너를 실행만 하고 컨테이너 자체는 삭제(Redis 클라이언트처럼 1회성으로 사용할 때 편리)

`--link redis_ambassador:redis` 옵션으로 redis_ambassador 컨테이너를 redis 별칭으로 연결

Docker Hub에 있는 relateiq/redis-cli 이미지를 받은 뒤 컨테이너로 실행

Redis 클라이언트가 실행되면 `ping`  명령을 입력

	결과로 PONG이 출력되면 다른 서버의 Redis 컨테이너에 정상적으로 연결된 것 
		
	redis 172.17.0.4:6379> ping ...왜 ping이 안쳐지는가..
	PONG
	redis 172.17.0.4:6379>

### Dcoker 데이터 볼륨 사용하기

Docker 데이터 볼륨은 데이터를 컨테이너가 아닌 호스트에 저장하는 방식

데이터 볼륨은 컨테이너끼리 데이터를 공유할 때 활용할 수 있다.

Docker 컨테이너 안의 파일 변경 사항은 Unifon File System에 의해 관리된다.

하지만 데이터 볼륨은 Union file System을 통하지 않고 바로 호스트에 저장

`docker commit` 명령을 통해 이미지로 생성해도 데이터 볼륨의 변경 사항은 이미지에 포함되지 않는다.

다음 명령을 입력하면 컨테이너 안의 `/data` 디렉터리가 데이터 볼륨으로 설정된다.

컨테이너의 Bash 셸이 실행되면 `/data` 디렉터리로 이동한 뒤 hello 라는 빈 파일을 생성

	sudo docker run -i -t --name test-volume -v /data ubuntu /bin/bash
	
	root@e86ea97c03cc:/# cd /data/
	root@e86ea97c03cc:/data# touch hello
	root@e86ea97c03cc:/data# ls
	hello
	root@e86ea97c03cc:/data# exit
	exit

데이터 볼륨 옵션은  `-v <컨테이너 디렉터리>` 형식

`docker inspect` 명령으로 **test-volume** 컨테이너의 데이터 볼륨 경로를 확인

	sudo docker inspect -f "{{ .Volumes }}" test-volume

다음 명령을 실행하여 컨테이너를 생성하고 데이터 볼륨을 설정

컨테이너의 Bash 셸이 실행되면 `/data` 디렉터리로 이동한 뒤 world 라는 빈 파일을 생성

	sudo docker run -i -t --name hello-volume1 -v /Users/:/data ubuntu /bin/bash
	root@d3684bfe5c9a:/data# touch world
	touch: cannot touch 'world': Permission denied

데이터 볼륨 옵션은 `-v <호스트 디렉터리>:<컨테이너 디렉터리>` 형식

여기서의 호스트의 `/root/data` 디렉터리를 Docker  컨테이너의 `/data` 디렉터리에 연결

	두 번째 컨테이너 생성
	sudo docker run -i -t --name hello-volume2 -v /Users:/data ubuntu /bin/bash
	root@af5a7bdb3e5a:/# ls /data
	world

앞에서 생성한 world  파일이 hello-volume2 파일에서도 보인다.

`/data` 디렉터리에 파일을 생성하면 호스트 및 hello-volume1  컨테이너에서도 사용할 수 있다.

이렇게 데이터 볼륨 설정을 통해 컨테이너끼리 데이터를 공유할 수 있다.

	sudo docker run -i -t --name test-volume -v /root/hello.txt:/root/hello.txt \
    ubuntu /bin/bash

### Docker 데이터 볼륨 컨테이너 사용하기

데이터 볼륨 컨테이너는 데이터 볼륨을 설정한 컨테이너를 뜻함

일반 컨테이너에서 데이터 볼륨 컨테이너를 연결하면 데이터 볼륨 컨테이너 안의 데이터 볼륨 디렉터리에 접근할 수 있다.

	sudo docker run -i -t --name hello-volume -v /Users/root/data:/data ubuntu /bin/bash
	oot@36ea0db2408b:/data# touch hello2
	touch: cannot touch 'hello2': Permission denied

일반 컨테이너를 생성하면서 방금 생성한 hello-volume 데이터 볼륨 컨테이너를 연결

컨테이너의 Bash 셸이 실행되면 `/data` 디렉터리의 파일 목록을 출력

	sudo docker run -i -t --volumes-from hello-volume --name hello ubuntu /bin/bash
	root@f162e814ebb2:/# ls /data

데이터 볼륨 컨테이너를 연결하는 옵션은 `--volumes-from <데이터 볼륨 컨테이너>` 형식

이제 데이터 볼륨 컨테이너에서 생성한 hello2 파일이 보임(호스트의 `/Users/root/data` 에 연결했기 때문에 앞에서 생성한 다른 파일들이 보일 수 있다.

데이터 볼륨 컨테이너에 일반 컨테이너를 여러 개 연결해도 된다.

다음 명령처럼 `/data` 디렉터리를 호스트의 특정 디렉터리에 연결하지 않아도 데이터 볼륨 컨테이너로 사용할 수 있다.

	sudo docker run -i -t --volumes-from test-volume --name hello ubuntu /bin/bash
	root@6a553c31076c:/#


### Docker 베이스 이미지 생성하기

보통 Dockerfile로 이미지를 생성할 때 Docker Hub에서 제공하는 공식 이미지를 기반으로 생성

이번에는 나만의 베이스 이미지를 생성하는 방법을 알아볼 것

**빈 베이스 이미지 생성하기**

아무것도 들어있지 않은 베이스 이미지를 생성하는 방법

Docker에서는 빈 베이스 이미지를 **sratch** 이미지라 부른다.

`/dev/null` 장치를 이용하여 빈 tar 빈 파일을 만들어서 `docekr import` 명령에 전달

	tar cv --files-from /dev/null | sudo docker import - scratch

**scratch** 이미지는 안에 아무것도 없기 때문에 컨테이너로 생성되지 않는다.

여기서 Dockerfile을 작성하여 여러분이 만든 실행 파일을 넣으면 된다.

hello 디렉터리를 생성한 뒤 hello.c를 아래의 코드로 저장

	int main ()
	{
	    printf("Hello Docker\n");
	    return 0;
	} 

hello.c 파일을 컴파일하여 실행 파일로 만든다.

scratch 이미지에는 아무 라이브러리도 없으므로 반드시 정적(static) 바이너리 컴파일 해야한다.

	gcc hello.c -static -o hello

Dockerfile로 다음 내용을 저장

	FROM scratch
	ADD ./hello /hello
	CMD ["/hello"]

scratch 이미지를 기반으로 새로운 이미지를 생성

- FROM: 어떤 이미지를 기반으로 할지 설정. Docker 이미지는 기존에 만들어진 이미지 기반으로 생성 `<이미지 이름>:<태그>` 형식
- ADDL 이미지에 포함할 파일을 설정 `<로컬 경로><이미지 경로>` 형식
- CMD: 컨테이너가 시작되었을 때 실행할 실행 파일 또는 스크립트

`docker build` 명령으로 이미지 생성

	sudo docker build --tag hello:0.1 .

scratch 이미지를 이용해서 만든 hello:0.1 이미지를 컨테이너로 생성

	sudo docker run --rm hello:0.1

### Docker 안에서 Docker 실행하기

복잡하게 왜 Docker 컨테이너 안에서 Docker를 실행할까?

예를 들면 Jenkins나 CruiseControl과 같은 빌드 자동화 시스템을 이용해서 Docker 이미지를 생성할 때 활용할 수 있다.

Jenkins, CruiseControl 환경 자체도 Docker 이미지로 만들면 Docker 컨테어니 안에서 Docker를 실행할 수 있어야 한다.

	GitHub에서 Dockerfile과 Bash 스크립트를 받음
	git clone https://github.com/pyrasis/dind.git
	
	dind 디렉터리로 이동한뒤 dockr bulid 명령으로 이미지 생성
	cd dind
	sudo docker build --tag dind .

 dind 이미지로 컨테이너 생성

	sudo docker run -i -t --privileged dind
	root@7cdab901e53e:/#

여기서 `--privileged` 옵션이 중요하다.

- 이 옵션은 컨테이너 안에서 호스트의 리눅스 커널 기능을 모두 사용할 수 있도록 해준다.

Docker in Docker 는 실험적인 기능이기 때문에 로그를 출력하도록 설정되어있다.

로그를 출력하지 않으려면 다음과 같이 `-e LOG=file` 옵션을 사용하면 된다.

	sudo docker run -i -t --privileged -e LOG=file dind

Docker 컨테이너 안에서 Docker 컨테이너 실행

	root@a4d395335e0b:/# sudo docker run -i -t busybox:latest /bin/sh
	Unable to find image 'busybox:latest' locally
	latest: Pulling from library/busybox
	ecf7dd1833d3: Pull complete
	839136952431: Pull complete
	Digest: sha256:bb84a4a069de8e6b9f1a39fecb503ce2cb8b8b68c998b997948a5b96e8b0d119
	Status: Downloaded newer image for busybox:latest
	/ #

이렇게 호스트 → dind 컨테이너 → busybox 컨테이너 순서로 실행되었다.
---

# 7장. Docker file 자세히 알아보기

이 장에서는 Dockerfile을 좀 더 자세히 살펴본다.

Dockerfile은 다음과 같이 `<명령> <매게변수>` 형식

#는 주석이다. 명령은 대소문자를 구분하지 않지만 보통 대문자로 작성

	# 주석
	FROM scratch

Docker는 Dockerfile에 작성된 명령을 순서대로 처리

그리고 Dockerfile에서 명령은 **항상** `FROM`으로 **시작**해야한다.

`FROM` 이 없거나 `FORM` 앞에 다른 명령이 있으면 이미지가 생성되지 않는다. 

또한, 각 명령은 독립적으로 실행된다.

예를 들어 `RUN cd/home/hello` 로 디렉터리를 이동하더라도 뒤에오는 명령에는 영향을 주지 않는다.

이미지를 생성할 때는 Dockerfile이 있는 디렉터리에서 `docker bulid` 명령을 사용

	sudo docker build --tag example .
	sudo docker build --tag pyrasis/example .

`--tag` 또는 `-t` 옵션으로 이미지 이름을 설정할 수 있다.

Docker Hub에 이미지를 올리려면 **pyrasis/example**처럼 / 앞에 사용자명을 붙이면 된다.

이미지 이름을 설정하지 않아도 이미지는 생성된다. 

이때 이미지를 사용하려면 이미지 ID를 지정하면 된다.

### .dockerignore

Dockerfile과 같은 디렉터리에 들어있는 모든 파일을 컨텍스트(context)라고 한다.

특히 이미지를 생성할 때 컨텍스트를 모두 Docker 데몬에 전송하므로 필요 없는 파일이 포함되지 않도록 주의한다.

컨텍스트에서 파일이나 디렉터리를 제외하고 싶을 때는 **.dockerignore** 파일을 사용하면 된다.

Docker는 Go 언어로 작성되어 있기 때문에 파일매칭도 Go 언어의 규칙을 따른다.

	Dockerfile
	
	example/hello.txt
	example/*.cpp
	wo*
	*.cpp
	.git

특정 파일이나 디렉터리를 제외할 수 있고,  보통 `*` 를 주로 사용한다.

버전 관리 시스템을 이용하여 Dockerfile 과 필요한 파일을 관리할때 `.git`, `.svn` 과 같은 디렉터리는 제외해준다.


### FROM

FROM은 어떤 이미지를 기반으로 이미지를 생성할지 설정

Dockerfile로 이미지를 생성할 때는 항상 기존에 있는 이미지를 기반으로 생성하기 때문에 FROM은 반드시 설정해야한다.

	Dockerfile
	FROM ubuntu
	
	FROM ubuntu:14.04

`FROM <이미지> 또는 FROM <이미지>:<태그>` 

Dockerfile 파일 하나에 FROM을 여러 개 설정할 수 있다.

FROM을 두 개 설정했다면 이미지가 두 개 생성된다.

`--tag` 옵션으로 이미지 이름을 설정했다면 맨 마지막에 FROM에 적용된다.

### MAINTAINER

MAINTAINER는 이미지를 생성한 사람의 정보를 설정

`MAINTANER <작성자 정보>`

### RUN

RUN은 FROM에서 설정한 이미지 위에서 스크립트 혹은 명령을 실행

여기서 RUN으로 실행한 결과가 새 이미지로 생성되고, 실행 내역은 이미지의 히스토리에 기록된다.

`RUN <명령>` 형식이며 셀 스크립트 구문을 사용할 수 있다.

FROM으로 설정한 이미지에 포함된 `/bin/sh` 실행 파일을 사용하게 되며 `/bin/sh` 실행 파일이 없으면 사용할 수 없다.

`RUN ["<실행 파일>", "매개 변수1>", "<매개 변수2>"` 형식

실행 파일과 매개 변수를 배열 형태로 설정

FROM으로 설정한 이미지 `/bin/sh` 실행 파일을 사용하지 않는 방식이다.

셀 스크립트 문법이 인식되지 않으므로 셀 스크립트 문법과 관련된 무자를 그래도 실행 파일에 넘겨줄 수 있다.

RUN으로 실행한 결과는 캐시되며 다음 빌드 때 재사용된다.

캐시된 결과를 사용하지 않으려면 `docker build` 명령에서  `--no-cache` 옵션을 사용하면 된다.

### CMD

CMD는 컨테이너가 시작되었을 때 스크립트 혹은 명령을 실행

`docer run` 명령으로 컨테이너를 생성하거나, `docker start` 명령으로 정지된 컨테이너를 시작할 대 실행된다.

정지된 컨테이너를 시작할 때 실행된다.

CMD는 Dockerfile에서 한 번만 사용할 수있다.

**셸(/bin/sh)로 명령 실행하기**

	CMD touch /home/hello/hello/txt

`CMC <명령>`  형식

셀 스크립트 구문을 사용할 수 있다.

FROM으로 설정한 이미지에 포함된 `/bin/sh` 실행 파일을 사용하게 되며 `/bin/sh` 실행 파일이 없으면 사용할 수 없다.

**셸 없이 바로 실행하기**

	CMD ["redis-server"]

**셸 없이 바로 실행할 때 매개 변수 설정**

	CMD ["mysqld", "--datadir=/var/lib/mysql", "--user=mysql"]

`CMD ["실행 파일>", "<매개 변수1>", "<매개 변수2>"]` 형식

실행 파일과 매개 변수를 배열 형태로 설정

FROM으로 설정한 이미지 `/bin/sh` 실행 파일을 사용하지 않는 방식

셸 스크립트 문법이 인식되지 않으므로 셸 스크립트 문법과 관련된 문자를 그대로 실행 파일에 넘겨줄 수 있다.

**ENTRYPOINT를 사용하였을 때**

	ENTRYPOINT ["echo"]
	CMD ["hello"]

`CMD ["매개 변수1>", "<매개 변수2>"` 형식

ENTRYPOINT에 설정한 명령에 매개 변수를 전달하여 실행

Dockerfile에 ENTRYPOINT가 있으면 CMD는 ENTRYPOINT에 매개 변수만 전달하는 역할

그래서 CMD 독자적으로 파일을 실행할 수 없게 된다.

다음과 같이 Dockerfile을 빌드하여 컨테이너를 생성하면 **hello**가 출력된다.

	sudo docker build --tag example .
	sudo docker run example
	hello

### EXPOSE

EXPOSE는 호스트와 연결할 포트 번호를 설정

`docekr run` 명령의 `--expose` 옵션과 동일 

    EXPOSE 하나로 포트 번호를 두 개 이상 동시에 설정할 수 있다.
    EXPOSE 80 443

`EXPOSE <포트 번호>` 형식

EXPOSE는 호스트와 연결만 할 뿐 외부에 노출은 되지 않는다.

포트를 외부에 노출하려면 `docker run` 명령의 `-p`, `-P` 옵션을 사용해야 한다.

### ENV

ENV는 환경 변수를 설정

ENV로 설정한 환경 변수는 RUN, CMD, ENTRYPOINT에 적용된다.

`ENV <환경 변수><값>` 형식

환경 변수를 사용할 때는 `$` 를 사용하면 된다.

	ENV HELLO 1234
	CMD echo $HELLO
	
	sudo docker build --tag example .
	sudo docker run example
	1234

ENV에서 설정한 **HELLO**의 값을 **1234**가 출력

환경 변수는 `docker run` 명령에서도 설정할 수 있다.

	sudo docker run -e HELLO=4321 example
	4321

`-e <환경 변수>=<값>` 형식

`-e` 옵션은 여러번 사용할 수 있고, `--env` 옵션과 같다.

### ADD

ADD는 파일을 이미에 추가

	ADD hello-entrypoint.sh /entrypoint.sh
	ADD hello-dir /hello-dir
	ADD zlib-1.2.8.tar.gz /
	ADD hello.zip /
	ADD http://example.com/hello.txt /hello.txt
	ADD *.txt /root/

`ADD <복사할 파일 경로> <이미지에서 파일이 위치할 경로>` 형식

- `<복사할 파일 경로>`는 컨텍스트 아래를 기준으로 하며 컨텍스트 바깥의 파일, 디렉터리나 절대 경로는 사용할 수 없다.
    - 예) `ADD ../hello.txt /home/hello` (X)
    - 예) `ADD /home/hello/hello.txt /home/hello` (X)

- `<복사할 파일 경로>`는 파일뿐만 아니라 디렉터리도 설정할 수 있으며, 디렉터리를 지정하면 디렉터리의 모든 파일을 복사한다.
- 또한, 와일드카드를 사용하여 특정 파일만 복사할 수 있다.
    - 예) `ADD *.txt /root/`
- `<복사할 파일 경로>`에 인터넷에 있는 파일의 URL을 설정
    - `<이미지에서 파일이 위치할 경로>`의 마지막에 /가 있으면 디렉터리가 생성되고 파일은 그 아래에 복시된다.
    - `ADD http://example.com/hello.txt /home/hello/` 와 같이 설정하면 **/home/hello/hello.txt**에 파일이 복사된다.

- 로컬에 있는 압축 파일(tar.gz, tar.bz2, tar.xz)은 압축을 해제하고 tar를 풀어서 추가된다. 단, 인터넷에 있는 파일 URL은 압축만 해제한 뒤 tar 파일이 그대로 추가된다.
    - 예) `ADD hello.tar.gz /` (압축을 해제하고 tar를 풀어서 추가)
    - 예) `ADD http://zlib.net/zlib-1.2.8.tar.gz /` (gzip 압축만 해제한 뒤 tar 파일을 추가. 단 파일 내용은 tar이지만 파일 이름은 zlib-1.2.8.tar.gz처럼 .gz가 붙어있다.)
- `<이미지에서 파일이 위치할 경로>`는 항상 절대 경로로 설정해야 한다.
- 마지막이 `/`로 끝나면 디렉터리가 생성되고 파일은 그 아래에 복사된다..
- `ADD ./ /hello`와 같이 현재 디렉터리를 추가할 때 **.dockerignore** 파일에 설정한 파일과 디렉터리는 제외된다.


### COPY

`COPY` 는 파일을 이미지에 추가한다.

`ADD` 와 달리 `COPY`는 압축 파일을 추가할 때 압축을 해제하지 않고, 파일 URL도 사용할 수 없다.

	Dockerfile	
	
	COPY hello-entrypoint.sh /entrypoint.sh
	COPY hello-dir /hello-dir
	COPY zlib-1.2.8.tar.gz /zlib-1.2.8.tar.gz
	COPY *.txt /root/

`COPY <복사할 파일 경로> <이미지에서 파일이 위치할 경로` 형식

- `<복사할 파일 경로>` 는 컨텍스트 아래를 기준으로 하면 컨텍스트 바깥의 파일, 디렉터리나, 절대 경로는 사용할 수 없다.
    - ex) `COPY ../hello.text /home/hello` (X)
    - ex) `COPY /home/hello/hello.txt /home/hello` (X)
- `<복사할 파일 경로>` 에 파일 뿐만 아니라 디렉터리로 설정할 수 있으며, 디렉터리를 지정하면 디렉터리의 모든 파일을 복사
- 또한 와일드 카드를 사용하여 특정 파일만 복사할 수 있다.
    - ex) `COPY *.txt /root/`
- `<복사할 파일 경로>`에 인터넷에 있는 파일의 URL은 사용할 수 없다.
- 압축 파일은 압축을 해제하지 않고 그대로 복사
- `<이미지에서 파일이 위치할 경로>`는 항상 절대 경로로 설정
- 마지막이 `/`로 끝나면 디렉터리가 생성되고 파일은 그 아래에 복사된다.
- `COPY ./ /hello`와 같이 현재 디렉터리를 추가할 때 **.dockerignore** 파일에 설정한 파일과 디렉터리는 제외된다.

`COPY` 로 추가되는 파일은 소유자(UID) 0, 그룹(GID) 0으로 설정되고 권한은 기존 파일의 권한을 따른다.

### VOLUME

`VOLUME` 은 디렉터리의 내용을 컨테이너에 저장하지 않고 호스트에 저장하도록 설정.

	Dockerfile
	
	VOLUME /data
	VOLUME ["/data", "/var/log/hello"]

`VOLUME <컨테이너 디렉터리> 또는 VOLUME ["컨테이너 디렉터리 1", "컨테이너 디렉터리2"]` 형식

**/data**처럼 바로 경로를 설정할 수도 있고**, [“/data”, “/var/log/hello”]**처럼 배열 형태로 설정할 수 있다.

단, VOLUME으로는 호스트의 특정 디렉터리와 연결할 수는 없다.

데이터 볼륨을 호스트의 특정 디렉터리와 연결하면 `docekr run` 명령에서  `-v` 옵션을 사용

	sudo docker run -v /root/data:/data example

옵션은 `-v <호스트 디렉터리>:<컨테이너 디렉터리>` 형식

### USER

USER는 명령을 실행할 사용자 계정을 설정

RUN, CMD, ENTRYPOINT에 적용

	USER nobody

`USER <계정 사용자명>` 형식

USER 뒤에 오는 모든 RUN, CMD, ENTRYPOINT에 적용되며, 중간에 다른 사용자를 설정하여 사용자를 바꿀 수 있다.

	Dockerfile
	
	처음에는 nobody 계정으로 /tmp/hello.txt 파일을 생성
	그 다음부터는 root 계정으로 /hello.txt 파일을 생성하고
	(/에는 root계정만 파일을 생성할 수 있으므로),
	/hello-entrypoint.sh파일을 실행
	
	USER nobody
	RUN touch /tmp/hello.txt
		
	USER root
	RUN touch /hello.txt
	ENTRYPOINT /hello-entrypoint.sh

### WORKDIR

`WORKDIR`은 RUN, CMD, ENTPRYPOINT의 명령이 실행될 디렉터리를 설정

	Dockerfile
	WORKDIR /var/www

`WORKDIR <경로>` 형식

`WORKDIR` 뒤에 오는 모든 RUN, CMD, ENTRYPOINT 에 적용되며, 중간에 다른 디렉터리를 설정하여 실행 디렉터리를 바꿀 수 있다.

	Dokcerfile
	
	WORKDIR /root
	RUN touch hello.txt
	
	WORKDIR /tmp
	RUN touch hello.txt

`WORKDIR`은 절대 경로 대신 상대 경로도 사용할 수 있다.

상대 경로를 사용하면 먼저 설정한 WORKDIR의 경로를 기준으로 디렉터리를 변경

최초기준은 `/`

	Dockefile
	WORKDIR var
	WORKDIR www
	
	RUN touch hello.txt

상대 경로를 사용하여 `/`에서 **var**로 이동한 뒤 **www**로 이동했기 때문에 **/var/www/hello.txt**에 파일이 생성된다.

### ONBULID

`ONBUILD` 는 생성한 이미지를 기반으로 다른 이미지가 생성될 때 명명을 실행(tigger)

최초에 ONBULID를 사용한 상태에서 아무 명령도 실행하지 않는다.

다음 번에 이미지가 `FROM` 으로 사용될 때 실행할 명령을 예약하는 기능이라 할 수 있다.

	Dockerfile
	
	ONBUILD RUN touch /hello.txt
	ONBUILD ADD world.txt /world.txt

`ONBUILD <Dockerfile 명령> <Dockerfile 명령의 매개 변수>` 형식

FROM, MAINTAINER, ONBUILD를 제외한 모든 Dockerfile 명령을 사용할 수 있다.

ONBUILD는 이미지를 생성한 뒤 해당 이미지를 기반으로 커스터마이징을 할 때 활용할 수 있다.

다음과 같이 ONBUILD를 사용하여 `RUN touch /hello.txt`를 실행하도록 설정한다.

	Dockerfile
	
	FROM ubuntu:latest
	ONBUILD RUN touch /hello.txt

`docker build` 명령으로 **example** 이미지를 생성한 뒤 `docker run` 명령으로 컨테이너를 생성

컨테이너의 Bash 셸이 실행되면 ls 명령으로 `/`의 파일 목록을 출력

	docker build --tag example .
	docker run -i -t example /bin/bash
	root@891ccb6749e9:/# ls
	bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

ONBUILD로 설정했기 때문에 **example** 이미지에는 `/hello.txt` 파일이 생성되지 않았다.

이제 FROM을 사용하여 **example** 이미지를 기반으로 새 이미지를 생성

	Dockfile
	FROM example

`docker build` 명령으로 **example2** 이미지를 생성한 뒤 `docker run` 명령으로 컨테이너를 생성\

컨테이너의 Bash 셸이 실행되면 `ls` 명령으로 `/`의 파일 목록을 출력

	docker build --tag example2 .
	Sending build context to Docker daemon  12.22MB
	Step 1/1 : FROM example
	 ---> e7eebd313cd1
	Successfully built e7eebd313cd1
	Successfully tagged example2:latest
	 hyewon@sinhyewon-ui-MacBook-Pro-5  ~/study/TIL   master  docker run -i -t example2 /bin/bash
	docker: Error response from daemon: OCI runtime create failed: container_linux.go:345: starting container process caused "exec: \"/bin/bash\": stat /bin/bash: no such file or directory": unknown.
	
	
	
	root@874d3e1fdd6f:/# ls
	bin  boot  dev  etc  hello.txt  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var

`docker build` 명령을 실행할 때 **# Executing 1 build triggers**라고 출력되고 그 아래부터 ONBUILD로 설정한 명령이 실행된다. 

이제 ONBUILD를 통해 **example2** 이미지에 **/hello.txt** 파일이 생성됨

ONBUILD는 바로 아래 자식 이미지를 생성할 때만 적용되고, 손자 이미지에는 적용되지 않는다.

즉 ONBUILD 설정은 상속되지 않음

	docekr inspect 명령으로 이미지의 ONBUILD 설정을 확인할 수 있다.
	sudo docker inspect -f "{{ .ContainerConfig.OnBuild }}" example
	[RUN touch /hello.txt]

---
# 8장. Docker로 애플리케이션 배포하기

지금까지 Docker 기본 사용법과 각종 기능들을 알아보았다.

8장에서는 Docker로 애플리케이션을 배포하는 방법을 알아보자

분산형 버전 관리 시스템인 Git과 Docker를 이용하여 애플리케이션을 배포하는 방법을 소개하겠다.

### 서버 한 대에 애플리케이션 배포하기

1. 개발자의 PC에서 애플리케이션을 개발
2. `git push` 명령으로 소스를 서버에 올림
3. 서버에서는 저장소에 `git push` 명령이 발생하면 git hook을 실행
4. git hook에서 Docker 이미지를 생성하고, 이미지를 컨테이너로 실행

### 서버 여러 대에 애플리케이션 배포하기

서버 한 대에 Docker이미지를 생성할 때와는 달리 Docker 이미지를 여러 서버에 전달해야 하기 때문에 Docker 레지스트리 서버를 구축해야한다.

1. 개발자의 PC에 애플리케이션을 개발
2. `git push` 명령으로 소스를 배포 서버에 올림
3. 배포 서버에서는 저장소에 `git push` 명령이 발생하면 git hook을 실행
4. git hook에서 Docker 이미지를 생성한 뒤 Docker 레지스트리에 올림
5. 배포 서버는 SSH로 애플리케이션 서버에서 `docker pull` 명령을 실행시키고, `docker run` 명령으로 컨테이너 생성

---
# 9장. Docker 모니터링 하기

Docker로 서비스를 구축했을 때 서버의 CPU나 메모리 사용량이 얼마나 되는지 모니터링 할 필요가 있다.

9장에서는 다양한 도구 중에 `Graphite` 를 사용하여 서버 모니터링 시스템을 구축해보겠다.

`Graphite`는 서버의 자원을 모니터링하고 그래프를 출력해주는 오픈 소스 도구이며 다양한 도구를 조합하여 사용한다.

이번에는 `Graphite` 에 `Graphite Web`, `Grafana`, `Elasticsearch`, `Diamond`를 조합하여 Docker 컨테이너로 실행하는 방법을 소개하겠다.

**Graphite**

시간 기반의 측정치(Metric) 데이터를 저장하는 저장소. 

Python으로 작성되었다.

- Grapite Web
    - 저장된 측정치 데이터와 시간을 그래프로 표시해주는 웹 어플리케이션
- Carbon-Cache
    - 네트워크상에서 측정치 데이터를 수집하고 디스크에 저장하는 데몬

**Grafana**

Graphite 대시보드

웹 애플리케이션이며 Graphite Web 보다 UI나 화면 구성이 좀더 깔끔

Graphite Web에서 데이터를 가져오기 때문에 Graphite Web이 필요하다

- Elasticsearch
    - Apache Lucene을 기반으로 하는 검색엔진
    - Grafana 대시보드상의 그래프 설정값을 저장하는 용도로만 사용

---
# 13. Docker Hub 사용하기

Docker Hub는  Docker 공식 ㄷ이미지를 세공하고, 사용자들끼리 이미지를 공유하는 사이트

공개저장소(Pubpic Respository)

- 저장된 이미지를 다른 사람들도 사용할 수 있다.
- 또한, 개수 제한 없이 무료로 생성할 수 있다.

개인 저장소(Private Respository)

- 저장된 이미지를 혼자만 사용할 수 있다.
- 1개까지 무료로 생성할 수 있고 그 이상부터는 유료다

즐겨찾기(Starred)

- 다른 사람의 유용한 저장소를 다음에 사용할 수 있도록 즐겨 찾기에 추가할 수 있다.

Automated Build

- GitHub 또는 BitBucket 저장소와 연동하여 Dockerfile을 Push했을 때 이미지를 자동으로 빌드하는 기능

`docker bulid` 명령으로 이미지 생성

Docker Hub에 이미지를 올리려면 이미지 이름을 `<Docker Hub 사용자 계정>/<이미지 이름>:<태그>` 형식으로 생성해야 한다.

아무 사용자 이름이나 사용할 수 있지만 내 계정 이름과 일치해야 이미지를 올릴수 있다.

태그를 지정하지 않으면 **latest**가 된다.

`docker push` 명령으로 이미지를 올린다.

`docker push <Docker Hub  사용자 계정>/<이미지 이름>:<태그>` 형식

이제 다른 사람들이 `docker pull <Docker Hub 사용자 계정>/example-ningx` 명령으로 **example-nginx** 이미지를 사용할 수 있다.

---
# 14장. Docker Remote API 사용하기

Docker는 데몬과 클라이언트 간의 통신을 할 때 로컬에서는 유닉스 소켓을 사용하고, 원격에서는 TCP 소켓을 사용한다.

여기에 HTTP REST 형식으로 API가 구현되어 있다.

따라서 API가 특정 언어에 종속되어 있지 않고, 다양한 언어에서 사용할 수 있다.

먼저 기존의 Docker 데몬을 정지하고 TCP 소켓으로 다시 실행시켜 API 테스트해보자

	service docker stop
	docker -d -H tcp://0.0.0.0:4243

`docker -d -H tcp://0.0.0.0:4243` 형식

`-d` 옵션을 사용하여 데몬 모드로 실행하고 

`-H` 옵션을 사용하여 접속을 받을 IP 주소와 포트 번호를 설정

Docker 데몬의 기본 포트번호는 4243

명령을 실행하면 Docker 데몬이 foreground로 실행된다.

따라서 테스트를 위해 새 터미널을 실행

Docker Remote API는 HTTP REST 형식으로 `curl` 명령으로 손쉽게 사용할 수 있다.

	nginx 이미지를 받음
	curl -X POST http://127.0.0.1:4243/images/create?fromImage=nginx:latest

- `-X` :POST 메서드를 사용하도록 설정
- 이미지를 받는 Remote API는 `/images/create?fromimage=<이미지 이름>:<태그>` 형식

	nginx 이미지로 컨테이너를 생성
	
	curl -X POST -H "Content-Type: application/json" \
	    -d '{ "Image":"nginx:latest", "ExposedPorts":"80/tcp" }' \
	    http://127.0.0.1:4243/containers/create
	{"Id":"386147f1c71ca7ee6a7013dbd2fff5d3091e41268885f954046be964b9ade39e","Warnings":null}

- `-X` : POST 메서드를 사용하도록 설정
- `-H` : Context-Type을 **application/json**으로 사용하도록 설정
- `-d` : 컨테이너를 생성하기 위해 설정 데이터를 보냄. 여기서는 **Image**에 **nginx:lastest**를 설정하였고, 호스트에 포트를 연결하기 위해 **ExposedPosts**에 **80/tcp**를 설정
- 컨테이너를 생성하는 Remote API는 `/containers/create` 다.

컨테이너가 생성되면 컨테이너 ID가 출력된다.

이처럼 HTTP 메서드를 이용하여 Docker 데몬을 제어할 수 있다.

---
# 19장. Docker 활용 시나리오

### 로드 밸런서와 연계한 확장 전개

클라우드 서비스가 등장하면서 이제 클릭 몇 번 만으로 수십, 수백대의 서버를 사용할 수 있게 되었다.

그래서 예전처럼 서버를 1년 365일 켜두고 쓰는 것이 아니라 필요할 때만 서버 인스턴스를 생성하여 사용하는 형태로 바뀌고 있다.

특히 부하를 분산하는 로드 밸런서와 자동 확장(Auto Scaling) 기능을 활용하여 급격히 늘어나는 트래픽에도 유연하게 대처할 수 있게 되었다.

Docker를 활용하면 클라우드 서비스에서 제공하는 기능과 조합하여 좀더 편리한 자동 확장 환경을 구축할 수 있다.

AWS의 ELB 로드밸런서와 Auto Scaling에 Docker를 활용한 구성도다.

- ELB 로드 밸런서는 외부에서 들어오는 트래픽을 Auto Scaling 그룹에 속한 EC2 인스턴스에 분배한다.
- Auto Scaling은 트래픽에 따라 EC2 인스턴스를 생성하거나 삭제한다.
- 새로 생성되는 EC2 인스턴스는 Docker 레지스트리에서 이미지를 받아와서 컨테이너로 실행한다.
- EC2 인스턴스를 생성할 때 모든 서비스 환경이 설정된  AMI(Amazon Machine Images)를 이용하는 것보다 Docker 를 사용하는 쪽이 좀 더 간편하다.
- 특히 Docker를 사용하면 EC2 인스턴스와 내부 테스트 환경 그리고 개발자의 PC를 동일한 환경으로 구성할 수 있다.
    - AMI에는 Docker만 설치한 상태로 사용
    - Docker 이미지를 빨리 받아올 수 있도록 Docker 레지스트리는 AWS 내부에 구축한다.

이런 방식으로 AWS뿐만 아니라 다른 클라우드 서비스에서도 동일하게 구축할 수 있다.

### 개발, 테스트, 운영을 통합

DevOps(Dev + Ops) 는 Chef의 개발사인 Opscode에서 만든 용어다.

DevOps는 개발, 테스트, 운영에 이르는 전 구간을 자동화하여 배포 주기를 짧게하고, 표준화된 도구를 사용하여 커뮤니케이션 비용을 줄이는 환경을 뜻한다.

- 개발자가 소스 서버/실드 서버에 소스를 올리면 Docker 이미지를 자동으로 빌드한다.
    - 소스 서버는 Git, Subversion, Mericuial, Perforce 등과 같은 도구로 구성
    - 빌드 서버는 Jenkins, CruiseControl 등과 같은 도구로 생성
- 자동 빌드된 Docker 이미지는 미리 정의된 테스트 케이스로 자동 테스트하거나 사람이 직접 테스트한다.
    - 웹 사이트는 Phantofjs와 같은 Headless 웹 브라우저로 손쉽게 테스트 할 수 있다.
- 테스트가 완료되면 Docker 이미지를 서비스 용 서버에 배포하고, 컨테이너로 실행한다.

Docker를 사용하면 자신의 PC에서 이미지와 컨테이너를 생성하여 서비스 환경과 동일한 상태에서 개발할 수 있다.

그리고 테스트 담당자는 서비스 환경, 개발자의 PC와 동일한 상태에서 테스트를 할 수 있다.

즉 Docker라는 공통된 도구를 사용하므로 개발자의 PC의 환경, 테스트 환경, 서비스 환경이 달라서 발생하는 각종 문제를 방지할 수 있다.

### 손쉬운 서비스 이전

Docker만 설치되어 있으면 어디든지 Docker 컨테이너를 생성할 수 있기 때문에 사내망에서 클라우드 서비스로 또는, 클라우드 서비스에서 다른 클라우드 서비스로 손쉽게 이전할 수 있다.

### 테스트 용도

Docker를 활용하면 실험적인 환경을 빠르게 구성해볼 수 있다.

한 번 만들어놓은 개발 환경은 Dockerfile로 작성하여 공유하면 편리하다.

간단하게 테스트 해보려면 `docker run` 명령의 `--rm` 옵션을 사용하면 편리하다.

**ubuntu:14.04** 이미지로 테스트 해본 뒤 `exit` 명령으로 빠져나오면 컨테이너가 바로 삭제된다.

    docker run -i -t --rm ubuntu:14.04 /bin/bash
