- npm init 명령어로 package.json 파일 생성
- 프로젝트의 루트 디렉토리에서 npm init을 실행하여 package.json 파일을 생성할 수 있습니다. -y 플래그를 사용하면 기본값으로 빠르게 생성할 수 있습니다.

```js
npm init -y
```

설치

```js
 npm install express mysql2 cors dotenv
```

### 20250218

- 도커 이미지 에러, 빌드 에러
- rm -rf \*, 다삭제
- ls -l , toal 확인 명령어
- gcp 저장소 Artifact Registry 검색
- 리눅스 압축푸는 명령어 unzip 파일명
- unzip unzip할파일명
- cd 파일명
- cd server
- ls -l docker파일 존재여부확인
- docker 파일 존재하면 빌드 준비
```sql
docker build -t 리전명-docker.pkg.dev/프로젝트id/guestbook/도커이미지명 . 으로 빌드
```
- guestbook이라는 이미지를 만들어서 빌드
- 저장소 만든것을 허가 받아야된다, 내가 만든 저장소에 설정 안내 > 인증 정보 도우미 코드 복붙, 인증허가 받기
- 인증 받고 아래와 같이 진행

\*\* 현재 막힌 부분 zip해제 했을때 server 안나옴

```sql
-- strong 나의 프로젝트 아이디를 쓰는 부분
docker build -t us-central1-docker.pkg.dev/apt-gear-449911-e5/guestbook/guestbook .
```

docker build -t us-central1-docker.pkg.dev/apt-gear-449911-e5/guestbook/guestbook .


- strong 나의 프로젝트 아이디를 쓰는 부분
- 프로젝트를 클릭했을때 나오는 id strong에 복붙
- us-central1 <- 이부분은 리전이름
- 빌드를 시켜라 내가 가진 리전에, 그안에 내가 가진 프로젝트에, 내가 가진 저장소에, 마지막이 게스트부분이라는 도커 이미지를 만들어줘
- 내가가진 파일 이름에 .찍기
- 빌드 이후 push 하기, push 하기전에 빌드가 잘 되었는지 확인하려면 , docker img를 검색하면 아래쪽에 나타남, 목록이 뜨면 잘 된거다.

```sql
docker push us-central1-docker.pkg.dev/principal-truck-450001-d4/guestbook/guestbook
```

docker push us-central1-docker.pkg.dev/apt-gear-449911-e5/guestbook/guestbook

- 메뉴, Cloud Run 이동
- 도커가 만들어진 이후 실제로 api 서비스를 만들러감
- 선택 > 컨테이너 이미지 선택 > 도커로 만든 주소 > ls test선택 > 선택단추 파란색 활성화 > 선택 클릭
- 서비스 이름과 리전은 자동으로 부여됨
- 인증되지 않은 호출 허용 클릭
- 엔드포인트 url, 나의 API 주소
- 변수 및 보안 비밀
- .env require("dotenv").config()g <- 주석처리, env파일은 환경변수 파일이다. 생겨난 이유는 vscode에서 반드시 필수적으로 들어가는게 서버인데 db부분을 누군가가 쉽게 볼수 있어서 환경변수 파일로 만들어서 보안상의 이유를 못보게끔 할 수 있다.
- 환경 변수 변수 추가에 하나씩 올리기, DB_HOST 값 공개 ip, DB_USER, 값 root, 패스워드, 네임
- 요청 > 100 > 인스턴스 동시 80
- 인스턴스 최소 0, 최대 100
- 시작 cpu부스트 체크 표시 해제
- Cloud SQL 연결, 연결 추가, 내가 만든 root라는 DB가 있다.
- 사용 설정
- 만들기
- 그럼 api키가 생성된다.
