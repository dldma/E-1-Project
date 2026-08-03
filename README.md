# E-1 개발 워크스테이션 구축

## 1. 프로젝트 개요

이 프로젝트는 Linux CLI, Docker, Git/GitHub를 활용하여 재현 가능한 개발 워크스테이션을 구축하는 과제이다.

터미널을 이용한 파일 및 권한 관리, Docker 이미지와 컨테이너 운영, Dockerfile 기반 웹 서버 제작, 포트 매핑, 바인드 마운트와 볼륨 영속성 검증을 수행한다.

## 2. 실행 환경

| 항목 | 환경 |
|---|---|
| 운영체제 | 작성 예정 |
| Linux 환경 | WSL2 Ubuntu |
| Shell | bash |
| 터미널 | VS Code Ubuntu(WSL) Terminal |
| Git | 작성 예정 |
| Docker | 작성 예정 |

## 3. 수행 체크리스트

- [ ] 터미널 기본 조작
- [ ] 파일 및 디렉토리 권한 실습
- [ ] Docker 설치 및 점검
- [ ] Docker 이미지 다운로드 및 확인
- [ ] 컨테이너 실행·중지·삭제
- [ ] Dockerfile 작성 및 이미지 빌드
- [ ] 웹 서버 포트 매핑
- [ ] 바인드 마운트 변경 반영
- [ ] Docker 볼륨 영속성 검증
- [ ] Git 및 GitHub 연동
- [ ] 트러블슈팅 2건 이상 작성
- [ ] 민감정보 점검

## 4. 검증 결과

### 4.1 터미널 조작

[터미널 조작 로그](docs/terminal-log.md)

### 4.2 Docker 운영

[Docker 운영 및 검증 로그](docs/docker-log.md)

### 4.3 트러블슈팅

[트러블슈팅 기록](docs/troubleshooting.md)

### 4.4 결과 화면

[스크린샷 폴더](docs/screenshots)

## 5. 저장소 구조

```text
E-1-Project/
├── README.md
├── app/
├── data/
├── practice/
└── docs/
    ├── screenshots/
    ├── terminal-log.md
    ├── docker-log.md
    └── troubleshooting.md
```

## 6. Git 및 GitHub

- 원격 저장소: GitHub E-1-Project
- 기본 브랜치: main
- 민감정보인 비밀번호와 GitHub 토큰은 저장소에 기록하지 않는다.