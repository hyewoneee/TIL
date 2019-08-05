# 가장 빨리 만나는 DocKer
Link : http://pyrasis.com/docker.html

# 목차
- [x] 1장. Docker
- [x] 2장. Docker 설치하기
- [ ] 3장. Docker 사용해보기
- [ ] 4장. Docker 이미지 생성하기
- [ ] 5장. Docker 살펴보기
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
`docker pull <이미지 이름>:<태그>` 형식

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
`docekr start <컨테이너 이름>` 
컨테이너 이름 대신 컨테이너 ID를 사용해도 됨
### restart 명령으로 컨테이너 재시작
	$ sudo docker restart hello
	hello
`docker restart <컨테이너 이름>` 형식
컨테이너 이름 대신 컨테이너 ID를 사용해도 됨
