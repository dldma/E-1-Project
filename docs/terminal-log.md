# 터미널 조작 로그

Linux CLI를 사용하여 현재 위치 확인, 파일 및 디렉토리 목록 확인, 디렉토리 이동, 파일과 디렉토리 생성, 파일 복사, 이름 변경, 이동, 내용 확인 및 삭제를 수행하였다.

명령어를 잘못 입력하거나 삭제 조건을 만족하지 못했을 때 발생한 오류도 함께 기록하고 원인을 분석하였다.

---

## 1. 현재 위치 확인

현재 터미널에서 작업 중인 디렉토리의 절대 경로를 확인하기 위해 `pwd` 명령어를 실행하였다.

### 입력

```bash
pwd
```

### 출력

```text
/home/dldmswl/codyssey/E-1-Project
```

### 확인 결과

현재 작업 위치가 `E-1-Project` 저장소의 최상위 디렉토리임을 확인하였다.

---

## 2. 파일 및 디렉토리 목록 확인

현재 디렉토리에 있는 일반 파일과 디렉토리의 목록을 확인하기 위해 `ls` 명령어를 실행하였다.

### 입력

```bash
ls
```

### 출력

```text
README.md  app  data  docs  practice
```

### 확인 결과

프로젝트 최상위 디렉토리에 다음 항목이 존재하였다.

- `README.md`
- `app`
- `data`
- `docs`
- `practice`

---

## 3. 숨김 파일을 포함한 상세 목록 확인

숨김 파일, 권한, 소유자, 파일 크기 및 수정 시간을 확인하기 위해 `ls -la` 명령어를 실행하였다.

### 입력

```bash
ls -la
```

### 출력

```text
total 40
drwxr-xr-x 7 dldmswl dldmswl  4096 Aug  3 19:26 .
drwxr-xr-x 5 dldmswl dldmswl  4096 Aug  3 19:15 ..
drwxr-xr-x 7 dldmswl dldmswl  4096 Aug  3 21:37 .git
-rw-r--r-- 1 dldmswl dldmswl 10855 Aug  3 21:46 README.md
drwxr-xr-x 2 dldmswl dldmswl  4096 Aug  3 19:27 app
drwxr-xr-x 2 dldmswl dldmswl  4096 Aug  3 19:27 data
drwxr-xr-x 3 dldmswl dldmswl  4096 Aug  3 21:41 docs
drwxr-xr-x 2 dldmswl dldmswl  4096 Aug  3 19:27 practice
```

### 확인 결과

- `.git`은 이름이 `.`으로 시작하는 숨김 디렉토리이다.
- `README.md`는 일반 파일이며 권한은 `-rw-r--r--`이다.
- `app`, `data`, `docs`, `practice`는 디렉토리이며 권한은 `drwxr-xr-x`이다.
- `ls -la`를 사용하면 일반적인 `ls`에서 보이지 않는 숨김 파일과 디렉토리도 확인할 수 있다.

---

## 4. 하위 디렉토리로 이동

`practice` 디렉토리로 이동하기 위해 `cd` 명령어를 실행하였다.

### 입력

```bash
cd practice
```

### 출력

```text
출력 없음
```

### 변경된 위치

```text
/home/dldmswl/codyssey/E-1-Project/practice
```

### 확인 결과

`cd practice` 명령어를 사용하여 현재 디렉토리 아래의 `practice` 디렉토리로 이동하였다.

---

## 5. 상위 디렉토리로 이동

현재 위치에서 한 단계 위의 디렉토리로 이동하기 위해 `cd ..` 명령어를 실행하였다.

### 입력

```bash
cd ..
```

### 출력

```text
출력 없음
```

### 변경된 위치

```text
/home/dldmswl/codyssey/E-1-Project
```

### 확인 결과

`..`은 현재 디렉토리의 상위 디렉토리를 의미한다.

---

## 6. 잘못 입력한 디렉토리 이동 명령어

홈 디렉토리로 이동하려고 `cd~`를 입력했으나 명령어가 정상적으로 실행되지 않았다.

### 잘못된 입력

```bash
cd~
```

### 출력

```text
Command 'cd~' not found, did you mean:
  command 'cdi' from deb cdo (2.5.4-1)
  command 'cdp' from deb irpas (0.10-10build1)
  command 'cdo' from deb cdo (2.5.4-1)
  command 'cdb' from deb tinycdb (0.81-2build1)
  command 'cd5' from deb cd5 (0.1-4build1)
  command 'cdw' from deb cdw (0.8.1-3build4)
  command 'cde' from deb cde (0.1+git9-g551e54d-3)
  command 'cdv' from deb erlang-observer (1:27.3.4.6+dfsg-1)
Try: sudo apt install <deb name>
```

### 원인

`cd`