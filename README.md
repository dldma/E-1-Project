# E-1 개발 워크스테이션 구축

## 1. 프로젝트 개요

이 프로젝트는 Linux CLI, Docker, Git/GitHub를 활용하여 재현 가능한 개발 워크스테이션을 구축하고 검증하는 과제이다.

터미널을 이용한 파일 및 디렉토리 관리, 권한 변경, Docker 이미지와 컨테이너 운영, Dockerfile 기반 웹 서버 제작, 포트 매핑, 바인드 마운트, Docker 볼륨 영속성 검증을 수행한다.

각 실습은 명령어와 출력 결과를 기록하여 동일한 환경에서 다시 실행할 수 있도록 문서화하는 것을 목표로 한다.

---

## 2. 실행 환경

| 항목 | 환경 |
|---|---|
| 호스트 운영체제 | Windows 11, 빌드 26200.8655 |
| Linux 환경 | WSL2 |
| Linux 배포판 | Ubuntu 26.04 LTS |
| Shell | Bash (`/bin/bash`) |
| 터미널 | VS Code WSL Terminal |
| Git | 2.53.0 |
| Docker | 29.6.2 |
| Docker 실행 환경 | Docker Desktop + WSL2 |
| VS Code | 1.131.0 |

### 환경 확인 명령어

```bash
uname -a
cat /etc/os-release
echo $SHELL
git --version
docker --version
docker info
```

자세한 출력 결과는 아래 문서에 기록한다.

- [터미널 조작 로그](docs/log/2_terminal.md)
- [Docker 운영 및 검증 로그](E-1-Project/docs/log
/2_docker.md)

---

## 3. 수행 항목 체크리스트

### 터미널 및 권한

- [x] 현재 위치 확인
- [x] 일반 파일 목록 확인
- [x] 숨김 파일 포함 목록 확인
- [x] 디렉토리 이동
- [x] 파일 및 디렉토리 생성
- [x] 파일 복사
- [x] 파일 이동 및 이름 변경
- [x] 파일 및 디렉토리 삭제
- [x] 파일 내용 확인
- [x] 빈 파일 생성
- [x] 파일 권한 변경 실습
- [x] 디렉토리 권한 변경 실습
- [x] `r`, `w`, `x` 권한 의미 정리
- [x] `644`, `755` 숫자 권한 의미 정리

### Docker

- [x] Docker Desktop 설치
- [x] WSL2와 Docker Desktop 연동
- [x] Docker 버전 확인
- [x] Docker 엔진 상태 확인
- [ ] Docker 이미지 다운로드
- [ ] Docker 이미지 목록 확인
- [ ] 컨테이너 실행
- [ ] 컨테이너 중지 및 재실행
- [ ] 실행 중인 컨테이너 목록 확인
- [ ] 전체 컨테이너 목록 확인
- [ ] 컨테이너 로그 확인
- [ ] 컨테이너 리소스 사용량 확인
- [ ] `hello-world` 컨테이너 실행
- [ ] Ubuntu 컨테이너 실행 및 내부 진입
- [ ] `attach`와 `exec` 차이 확인

### Dockerfile 및 웹 서버

- [ ] Dockerfile 작성
- [ ] 웹 서버 소스코드 작성
- [ ] 커스텀 이미지 빌드
- [ ] 커스텀 컨테이너 실행
- [ ] 포트 매핑 적용
- [ ] 브라우저 접속 확인
- [ ] `curl` 응답 확인
- [ ] 바인드 마운트 변경 반영 확인
- [ ] Docker 볼륨 생성
- [ ] Docker 볼륨 영속성 검증

### Git 및 GitHub

- [x] Git 사용자 정보 설정
- [ ] Git 기본 브랜치 설정 확인
- [x] GitHub 저장소 생성
- [x] 로컬 저장소 Clone
- [x] VS Code와 WSL 저장소 연결
- [x] 원격 저장소 연결
- [x] Commit 및 Push 수행
- [ ] `git config --list` 결과 기록
- [ ] GitHub 연동 증거 스크린샷 첨부
- [ ] 민감정보 최종 점검

---

## 4. 수행 결과 및 검증 방법

## 4.1 터미널 조작 실습

현재 위치 확인, 목록 확인, 파일 생성, 복사, 이동, 이름 변경 및 삭제 작업을 수행한다.

### 검증 명령어

```bash
pwd
ls
ls -la
cd
mkdir
touch
cp
mv
cat
rm
rmdir
```

### 수행 결과

```
### 수행 결과

Linux CLI를 사용하여 다음 작업을 수행하였다.

- `pwd`로 현재 작업 디렉토리의 절대 경로를 확인하였다.
- `ls`로 일반 파일과 디렉토리 목록을 확인하였다.
- `ls -la`로 `.git`을 포함한 숨김 파일, 권한, 소유자와 파일 크기를 확인하였다.
- `cd`를 사용하여 하위 디렉토리와 상위 디렉토리로 이동하였다.
- `mkdir`과 `mkdir -p`를 사용하여 일반 디렉토리와 여러 단계의 디렉토리를 생성하였다.
- `touch`로 빈 파일을 생성하였다.
- `echo`와 `>`를 사용하여 파일에 내용을 작성하였다.
- `cp`로 파일을 복사하고 다른 디렉토리에도 복사하였다.
- `mv`로 파일 이름을 변경하고 파일을 다른 디렉토리로 이동하였다.
- `cat`으로 파일 내용을 확인하였다.
- `rm`으로 일반 파일을 삭제하였다.
- `rmdir`은 빈 디렉토리만 삭제할 수 있다는 것을 확인하였다.

실습 과정에서 `cd~`처럼 명령어와 경로 사이의 공백을 생략하거나, `rssult`처럼 경로 이름을 잘못 입력하면 명령어가 실행되지 않는 것도 확인하였다. 또한 파일이 들어 있는 디렉토리에 `rmdir`을 사용하면 `Directory not empty` 오류가 발생하며, 내부 파일을 먼저 삭제해야 한다는 것을 확인하였다.
```

### 상세 기록

[터미널 조작 로그 보기](docs/log/4_1.md)

---

## 4.2 파일 및 디렉토리 권한 실습

파일 1개와 디렉토리 1개를 대상으로 권한을 확인하고 변경한다.

### 검증 명령어

```bash
ls -l
chmod
```

### 파일 권한 변경 결과

작성 예정

### 디렉토리 권한 변경 결과

작성 예정

### 권한 설명

작성 예정

- `r`: 작성 예정
- `w`: 작성 예정
- `x`: 작성 예정
- `644`: 작성 예정
- `755`: 작성 예정

### 상세 기록

[터미널 조작 로그 보기](docs/terminal-log.md)

---


## 4.3 Docker 이미지 관리

Docker 이미지를 다운로드하고 이미지 목록을 확인한다.

### 실행 명령어

```bash
docker pull 이미지명
docker images
```

### 사용한 이미지

작성 예정

### 실행 결과

작성 예정

### 상세 기록

[Docker 운영 및 검증 로그 보기](docs/docker-log.md)

---

## 4.4 Docker 컨테이너 기본 운영

컨테이너를 실행하고 중지한 뒤 상태와 로그를 확인한다.

### 실행 명령어

```bash
docker run 이미지명
docker ps
docker ps -a
docker stop 컨테이너명
docker start 컨테이너명
docker logs 컨테이너명
docker stats --no-stream
```

### 실행 결과

작성 예정

### 상세 기록

[Docker 운영 및 검증 로그 보기](docs/docker-log.md)

---

## 4.5 hello-world 컨테이너 실행

Docker가 이미지를 다운로드하고 컨테이너를 정상적으로 실행할 수 있는지 확인한다.

### 실행 명령어

```bash
docker run hello-world
```

### 실행 결과

작성 예정

### 검증 결과

작성 예정

---

## 4.6 Ubuntu 컨테이너 실행

Ubuntu 컨테이너를 대화형 모드로 실행하고 컨테이너 내부에서 Linux 명령어를 실행한다.

### 실행 명령어

```bash
docker run -it --name ubuntu-practice ubuntu bash
```

컨테이너 내부에서 실행할 명령어:

```bash
pwd
ls
echo "Hello Docker"
cat /etc/os-release
```

### 실행 결과

작성 예정

### `run`, `start`, `attach`, `exec` 차이

작성 예정

---

## 4.7 Dockerfile 기반 커스텀 이미지

### 선택한 방식

작성 예정

예상 방식:

```text
NGINX Alpine 베이스 이미지와 정적 HTML 파일을 사용한 웹 서버
```

### 선택한 베이스 이미지

작성 예정

예상 베이스 이미지:

```text
nginx:alpine
```

### Dockerfile

작성 예정

예상 구조:

```dockerfile
FROM nginx:alpine

COPY app/ /usr/share/nginx/html/

EXPOSE 80
```

### 커스텀 포인트

작성 예정

### 이미지 빌드 명령어

```bash
작성 예정
```

### 컨테이너 실행 명령어

```bash
작성 예정
```

### 실행 결과

작성 예정

### 상세 기록

[Docker 운영 및 검증 로그 보기](docs/docker-log.md)

---

## 4.8 포트 매핑 및 웹 접속

컨테이너 내부 웹 서버 포트를 호스트 포트와 연결하여 브라우저에서 접속한다.

### 실행 명령어

```bash
작성 예정
```

예상 명령어:

```bash
docker run -d \
  -p 8080:80 \
  --name e1-web-container \
  e1-web:1.0
```

### 접속 주소

```text
작성 예정
```

예상 접속 주소:

```text
http://localhost:8080
```

### `curl` 확인 결과

```bash
작성 예정
```

### 브라우저 접속 결과

작성 예정

### 증거 이미지

작성 예정

[스크린샷 폴더 보기](docs/screenshots)

---

## 4.9 바인드 마운트

호스트의 파일을 컨테이너 내부 경로와 연결하고, 호스트 파일 변경이 컨테이너에 즉시 반영되는지 확인한다.

### 실행 명령어

```bash
작성 예정
```

### 변경 전 결과

작성 예정

### 호스트 파일 수정 내용

작성 예정

### 변경 후 결과

작성 예정

### 검증 결과

작성 예정

---

## 4.10 Docker 볼륨 영속성

Docker 볼륨을 생성하고 컨테이너에 연결한다.

컨테이너를 삭제한 후 새로운 컨테이너에서 동일한 데이터를 확인하여 데이터가 유지되는지 검증한다.

### 볼륨 생성 명령어

```bash
작성 예정
```

### 볼륨 연결 명령어

```bash
작성 예정
```

### 데이터 생성 결과

작성 예정

### 기존 컨테이너 삭제 결과

작성 예정

### 새로운 컨테이너에서 데이터 확인

작성 예정

### 검증 결과

작성 예정

---

## 4.1 Git 설정 및 GitHub 연동

Git 사용자 정보를 설정하고 GitHub 원격 저장소와 연결하였다.

### Git 설정 확인

```bash
git config --list
```

실행 결과:

```text
작성 예정
```

### 원격 저장소 확인

```bash
git remote -v
```

실행 결과:

```text
작성 예정
```

### 현재 브랜치 확인

```bash
git branch --show-current
```

실행 결과:

```text
main
```

### GitHub 연동 결과

작성 예정

### 연동 증거

작성 예정

---

## 5. 트러블슈팅

실습 중 발생한 문제의 원인과 해결 과정을 기록한다.

### 트러블슈팅 1

작성 예정

### 트러블슈팅 2

작성 예정

자세한 내용은 아래 문서에서 확인한다.

[트러블슈팅 기록 보기](docs/troubleshooting.md)

---

## 6. 저장소 구조

```text
E-1-Project/
├── README.md
├── Dockerfile                 # 작성 예정
├── app/
│   └── index.html             # 작성 예정
├── data/
├── practice/
└── docs/
    ├── terminal-log.md
    ├── docker-log.md
    ├── troubleshooting.md
    └── screenshots/
```

### 폴더별 용도

| 경로 | 용도 |
|---|---|
| `README.md` | 프로젝트 전체 기술 문서 |
| `Dockerfile` | Docker 커스텀 이미지 제작 설정 |
| `app/` | 웹 서버 소스코드 |
| `data/` | 데이터 및 볼륨 관련 실습 자료 |
| `practice/` | 터미널 및 권한 실습 |
| `docs/terminal-log.md` | 터미널 명령어와 출력 결과 |
| `docs/docker-log.md` | Docker 명령어와 출력 결과 |
| `docs/troubleshooting.md` | 문제 발생 및 해결 기록 |
| `docs/screenshots/` | 터미널 및 브라우저 증거 이미지 |

---

## 7. 문서 및 결과 링크

- [터미널 조작 로그](docs/terminal-log.md)
- [Docker 운영 및 검증 로그](docs/docker-log.md)
- [트러블슈팅 기록](docs/troubleshooting.md)
- [스크린샷 폴더](docs/screenshots)

---

## 8. 보안 및 개인정보 보호

- GitHub Personal Access Token은 저장소에 기록하지 않는다.
- GitHub 및 Ubuntu 비밀번호는 문서에 기록하지 않는다.
- 개인키와 인증 코드는 Git에 추가하지 않는다.
- 민감정보가 포함된 화면은 캡처하지 않거나 마스킹한다.
- GitHub에 Push하기 전에 문서와 스크린샷의 민감정보를 확인한다.

### 보안 점검 체크리스트

- [ ] README에 토큰이 포함되지 않았는지 확인
- [ ] 터미널 로그에 비밀번호가 포함되지 않았는지 확인
- [ ] 스크린샷에 인증 정보가 노출되지 않았는지 확인
- [ ] 개인키가 Git에 추가되지 않았는지 확인
- [ ] Push 전 전체 파일