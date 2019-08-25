# 가장 빨리 만나는 DocKer
Link : http://pyrasis.com/docker.html

# 목차
- [x] 1장. Docker
- [x] 2장. Docker 설치하기
- [x] 3장. Docker 사용해보기
- [x] 4장. Docker 이미지 생성하기
- [x] 5장. Docker 살펴보기
- [ ] 6장. Docker 좀더 활용하기
- [ ] 7장. Docker file 자세히 알아보기
- [ ] 8장. Docker로 애플리케이션 배포하기
- [ ] 9장. Docker 모니터링 하기
- [ ] 10장. Amazon Web Services에서 Docker 사용하기
- [ ] 11장. Google Cloud Platform에서 Docker 사용하기
- [ ] 12장. Microsoft Azure에서 Docker 사용하기
- [ ] 13장. Docker Hub 사용하기
- [ ] 14장. Docker Remote API 사용하기
- [ ] 15장. CoreOS 사용하기
- [ ] 16장. Docker로 워드프레스 블로그 구축하기
- [ ] 17장. Docker로 Ruby on Rails 애플리케이션 구축하기
- [ ] 18장. Docker로 Django 애플리케이션 구축하기
- [ ] 19장. Docker 활용 시나리오

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



