# Docker

## 도커란?

[Docker 개념 및 기초](https://sarc.io/index.php/cloud/1552-docker-1-docker)
[docker docs](https://docs.docker.com/)
[도커한글스터디](https://github.com/remotty/documents.docker.co.kr)
[도커 초보 안내서](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html)

[Dockerfile을 사용한 tomcat에 War file 배포하기](http://jmlim.github.io/docker/2019/02/19/dockerfile-tomcat-deploy/)

- 컨테이너 방식 가상화를 위한 플랫폼
- Docker를 통해 애플리케이션의 개발 환경 구축, 애플리케이션의 실행 및 배포가 가능

컨테이너 : 격리된 공간에서 프로세스가 동작하는 기술. 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 관리를 단순화 시킬 수 있다.

기존 가상화는 OS를 가상화 한 것으로 호스트 OS 위에 게스트 OS 전체를 가상화(VMWare, VirtualBox)하여 사용하거나, 반가상화(오픈스택, AWS) 방식
추가적인 OS를 설치하여 가상화하는 방법은 성능 문제가 있고 이를 개선하기 위해 프로세스를 격리하는 방식(ex:도커)이 등장한다.

image : 컨테이너 실행에 필요한 파일과 설정값 등을 모두 포함하고 있는 것. 상태값을 가지지 않고 변하지 않는다(Immutable)
같은 이미지에서 여러 개의 컨테이너를 생성할 수 있고 컨테이너의 상태가 바뀌거나 삭제되어도 이미지는 변하지 않고 그대로 남아있다.
컨테이너를 실행하기 위한 모든 정보(실행파일, 명령어, 포트 정보, database, 소스 등등등)를 가지고 있기 때문에 의존성 파일을 따로 설치할 필요가 없음

Docker Engine: Docker Image로부터 컨테이너를 작성하거나, 컨테이너를 관리하는 기능
