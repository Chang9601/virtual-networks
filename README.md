# 가상 네트워크

## 소개

- Docker, Mininet, Stratum, ONOS를 사용해서 호스트와 스위치로 구성된 가상 네트워크를 설치한다.

## 목적

- Mininet, Stratrum, ONOS가 무엇인지 그리고 역할을 배운다.
- 설치된 가상 네트워크가 정상적으로 동작하는지 확인한다.

## 툴

### Docker

- Docker는 오픈 소스 플랫폼으로 특정 운영체제에 종속되지 않는 구성 요소인 컨테이너의 모음으로 애플리케이션을 개발하고 배포할 수 있게 해준다. 즉, 컨테이너는 애플리케이션 소스 코드를 어느 환경(e.g., 윈도우, 리눅스, 맥)에서나 실행할 수 있도록 운영체제 라이브러리와 의존성을 결합하는 구성 요소이다.
- Docker는 자신만의 커널을 실행하고 하나의 하드웨어의 서버를 공유하는 Virtual Machine (VM)과 달리 하나의 호스트 커널의 자원을 공유한다.

### Mininet

- Mininet은 호스트, 링크, 스위치로 구성된 네트워크를 모방하는 툴이다. stratum_bmv2를 기본 스위치로 사용하는 Open Networking Lab의 Docker 버전을 사용한다.

### Stratum

- Stratum은 SDN을 위한 오픈 소스 실리콘 독립적인 스위치 운영체제이다.

### ONOS

- ONOS은 오픈 소스 SDN 컨트롤러이며 SDN을 관리하고 제어하는데 사용한다. ONOS REST API를 사용해서 파이썬으로 작성된 애플레케이션이 컨트롤러와 상호작용하고 스위치에 규칙을 설치한다.

## 실행

- 총 4개의 터미널 사용

1. make controller: ONOS를 실행
2. make mininet: Mininet을 실행
3. mininet> net: 실행된 가상 네트워크의 호스트와 스위치 그리고 연결성을 출력
4. make cli: 스위치가 들어오는 패킹을 어디로 라우팅하는지 모르기 때문에 스위치를 ONOS 컨트롤러에 연결하고 ONOS의 fwd 네트워크 애플리케이션을 실행. fwd는 스위치에게 패킷을 어디로 라우팅해야 하는지 지시
5. onos@root > app activate fwd: fwd 실행
6. make netcfg: ONOS 컨트롤러가 스위치의 존재를 인지. JSON 파일이 ONOS 컨트롤러에게 어느 IP:PORT로 스위치에 연결하는지 지시
7. mininet> h1 ping h2: 호스트 h1에서 호스트 h2로 패킷을 전달되는 것을 확인

## 출처

- Purdue University (CS 422: Computer Networks)
