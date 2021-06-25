# ELB
---
## ELB란?
---
- Elastic Load Balancing은 둘 이상의 AZ에서 EC2 인스턴스, 컨테이너, IP 주소 등 여러 대상에 걸쳐 수신되는 트래픽을 분산해줌
- 등록된 대상의 상태를 모니터링하면서, 상태가 양호한 대상으로만 트래픽을 라우팅
- Elastic Load Balancing은 아래의 로드 밸런서를 지원
    - Application Load Balancer
    - Network Load Balancer
    - Gateway Load Balancer
    - Classic Load Balancer


<br>

## CLB
---
- Classic Load Balancer
- 요새는 쓰지 않는 추세
- L4 / L7 둘다 지원
- HTTP/HTTPS/SSL/TCP 지원

<br>

## ALB
---
- Application Load Balancer
- L7 부하 분산 지원
- HTTP/HTTPS 지원

<br>

## NLB
---
- L4 분산 지원
- TCP / UDP 트래픽을 로드밸런싱
- 내부로 들어온 트래픽을 처리하고, 내부 인스턴스로 트래픽을 전송할 때

<br>

## ALB / NLB / GLB / CLB 비교한 표
---
[이미지 - https://aws.amazon.com/ko/elasticloadbalancing/features/]


<br>

## ELB 용어 정리
---
- L2(OSI Layer2)
    - 패킷의 MAC 주소를 기반으로 스위칭

    
<br>

- L3(OSI Layer3)
    - IP 주소를 기반으로 라우팅


<br>

- L4(OSI Layer4)
    - IP주소 + 포트번호를 보고 트래픽을 분배


<br>

- L7(OSI Layer7)
    - IP주소 + 포트번호 + HTTP/HTTPS 프로토콜의 헤더 내용을 기준으로 트래픽을 분배
    - L4 방식과 다른 점은 패킷의 내용을 본다는 것
        - 213.12.32.123:80/img/aaa.jpg와 213.12.32.123:80/img/bbb.jpg


<br>

- Health Check
    - EC2 인스턴스가 정상적으로 가동 중인지 확인하는 기능
    - 중단되었다고 판단되면 EC2 인스턴스는 트래픽 분배에서 제외


<br>

- Connection Draining
    - 사용자의 요청을 처리 중인 인스턴스를 Auto Scaling으로 인해 바로 삭제되지 못하도록 방지하는 기능
    - 예시) 지정한 임계점 이하로 트래픽이 줄어 Auto Scaling에 의해 인스턴스가 삭제되는데, 이때 사용자가 해당 인스턴스에서 파일을 다운로드 중이였다
    - 인스턴스가 삭제되면 파일 다운로드가 중단된다
    - 삭제하기 전, 요청을 처리할 수 있도록 지정한 시간만큼 삭제하지 않는다


<br>

- Sticky Sessions
    - 사용자의 세션을 확인하여 인스턴스를 분배
    - HTTP 쿠키를 이용한 세션
    - L7 로드밸런싱의 기능
    - 예시) 1번 서버에 이미 분배를 한 사용자의 요청이라면, 1번 서버로 보내지 않고 다른 서버로 요청을 분배해준다


<br>
    
- Surge Queue Length
    - ELB 로드 밸런서에서 인스턴스로 전달되지 못하고 큐에 남아있는 요청의 수


<br>

- Spilover Count
    - Surge Queue가 가득 차서 ELB 로드 밸런서가 거부한 요청의 개수

<br>

- Target Grouop
    - ELB는 Target Group으로 트래픽을 라우팅
리스너 규칙 생성 시 Target Group 및 조건을 지정
규칙 조건이 충족되면 해당하는 Target Group으로 트래픽이 전달