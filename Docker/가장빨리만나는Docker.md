# 가장 빨리 만나는 DocKer
Link : http://pyrasis.com/docker.html

# 목차
- [x] 1장. Docker
- [ ] 2장. Docker 설치하기
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
