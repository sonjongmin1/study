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

## `gcp에 서버연동`

`사전작업 : 내컴퓨터에서 작업폴더로 가서 모든 파일을 압축한다.
(터미널에서 압축하는거 mac은 명령어 찾아서해보기)`

- 만든 저장소 설정안내 가서 허가 받기

1. Artifact Registry에서 저장소를 만든다.
2. 저장소를 선택하고 설정안내 클릭 인증 명령어 복사
3. 클라우드 쉘을 열어서, 복사한 내용을 붙여넣기 해서 인증받음
4. 쉘에서 내컴퓨터 프로젝트에 있는 압축파일을 업로드 한다.
5. 업로드 확인한다. ls -l
6. 압축을 푼다. unzip 압축파일 이름.zip
7. 하위폴더(server파일)로 이동 명령어 cd
8. docker build -t 리전이름-docker.pkg.dev/프로젝트id/저장소이름(guestbook)/이미지이름(guestbook) . <- 마지막에 . 중요

```sql
docker build -t us-central1-docker.pkg.dev/apt-gear-449911-e5/guestbook/guestbook .
```

9. docker images // 빌드 성공 확인
10. docker push 리전이름-docker.pkg.dev/프로젝트id/저장소이름(guestbook)/이미지이름(guestbook)

```sql
docker push us-central1-docker.pkg.dev/apt-gear-449911-e5/guestbook/guestbook
```

11. docker ps (push 확인 명령어), 지금 상태가 up이라고 되어있으면 된거다.
12. api 발급을 위한 Cloud Run 메뉴 선택한다. (클라우드 쉘은 닫아도 됨)
13. 서비스만들기, 컨테이너배포
14. docker 이미지에서 선택 클릭
15. 변수 및 보안설정, 변수 추가 이름 환경 변수 변수 추가에 하나씩 올리기, DB_HOST 값 공개 ip, DB_USER, 값 root, 패스워드, 네임
16. sql 연결, 테이블을 만든 id, sql을 만들었을때 고유 아이디 (인스턴스 연결 이름), 기본적으로 설정 되어있음
17. 배포 클릭, 클라우드런에서 api 주소가 만들어짐, root에 안만들었기 때문에 클릭해도 안나옴, url에/message <- /message를 입력해줘야 된다.
18. Cloud Storage로 이동, 프론트를 만들어주는 친구, 버킷에가면 업로드시킬수 있음
    - 누구나 오픈 할 수 있기때문에 권한에서 엑세스 권한 부여, allUser
    - (IAM은 본격적인 권한주는 곳 여기는 나중에 공부하기)

## 버킷만들기

- 시작히기 이름
- 데이터 저장 위치 Region - 아이오아
- 데이터의 스토리지 클래스, 스탠다드
- 공개 액세스 방지 체크표시 해제
- 세분화
- 세분화된 엑세스 제어 체크
- 객체 데이터를 보호하는 방법 선택
  - 소프트 삭제 정책, 기본 보관 기간 사용

### 권한

- 새 주 구성원 allUsers
- 역할 지정, 클라우드 스토리지,저장소 관리자
