# `작업순서`

- 로컬테스트를 위한 프로그램 설치
  - docker, mysql, node (로컬테스트를 위해 docker 와 mysql은 필수 설치)

1. gcp mysql 계정 생성 -> 테이블 작성, 테스트를 위한 데이터 삽입
   - 모든 사람에게 개방 0.0.0.0/0
2. 내 컴퓨터에 프로젝트 폴더 생성
   - 서버파일들을 관리하기 위한 하위폴더로 생성 (예시 : server)
3. 필수 프로그램 설치
   - express : 웹서버(노드)의 프레임워크
   - mysql2 : mysql과 연동 할 수 있는 express에서 도와주는 것
   - cors : 각 객체들이 표준에 맞춰서 연결
   - dotenv : 환경 변수 관리 .env
4. 서버폴더로 이동하여 필수 파일 작성 ( 도커가 실행된 상태에서 하기와 같이 진행 )
   - 도커파일 : Dockerfile (docker 가상의 공간을 만들어주는 곳), 가장 대중적이다.
   - server.js : 서버와 통신을 관리 node.js작성
     - 노드가 관리하는 친구(노드 환경에서 꾸며진 자바스크립트), 일반적으로 실행되는게 아니라 노드를 불러서 실행 가능함.
   - .env : 환경변수 파일 (숨은 파일로 존재함, 다른사람들이 가져 갈 수 없다, 보안상 이점을 가짐)
   - 서버통신 파일 server.js 작성 로컬 테스트 (server.js가 잘못 되었는지 내 컴퓨터에서 테스트)
   - 터미널 명령어 : node server.js
   - http://localhost:8080/messages
   - 내 컴퓨터에서 docker build -t 이름(guestbook) . //도커 이미지 생성
   - 도커 이미지 확인 : docker images (빌드가 잘 되었는지 확인), 오류 나면 도커파일에서 잘못된 곳을 찾는다.
   - 클라우드는 push할 공간을 만들어서 push가 가능했는데, local test는 run을 시켜야한다. `명령어 docker run -d -p 8080:8080 도커이미지이름(guestbook)` // -d는 백그라운드에서 해라, -p는 포트번호를 누구에게 연결시키는가
   - curl http://localhost:8080/messages
