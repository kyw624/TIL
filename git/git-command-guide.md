# 자주 쓰이는 CLI 명령어

```
$ ls
 현재 디렉토리 리스트 출력

	○ 옵션
		-al : 상세정보 함께 출력
```

```
$ cd <경로>
// 해당 경로로 이동
```

```
$ mkdir <디렉토리명>
// 디렉토리 생성
```

```
$ rm <파일명>
// 해당 파일 삭제
```

```
$ rmdir <디렉토리명>
// 빈 디렉토리 삭제

    ○ 옵션
    	-rf : 비어있지 않은 디렉토리 삭제
```

```
$ cp <파일명1> <파일명2>
// 파일명1 복사 후 파일명2 생성
```

```
$ vim <파일명>
// vim 에디터로 파일 편집 (파일 생성도 가능)

	○ 사용법
		i : 입력모드
		esc : 명령어 모드
		:q! : 저장하지 않고 종료
		:wq : 저장 후 종료
```

```
$ cat <파일명> [파일명2] [파일명3]...
// 해당 파일의 내용 출력 (여러개의 파일 연속 출력 가능)

	○ 옵션
  	-n : 행 번호 표시
```

<br />

# Git Bash 명령어

## 1. 설정과 초기화

`$ git config`

> ### 전역 사용자 설정

```
$ git config --global user.name "USERNAME"
$ git config --global user.email "E-MAIL"
```

> ### 저장소별 사용자 설정

```
해당 디렉토리로 이동 후

$ git config user.name "USERNAME"
$ git config user.email "E-MAIL"
```

> ### 설정 정보 조회

```
$ git config [--global] --list
```

저장소별 [전역] 설정 정보 조회

<br />

> ### 저장소 초기화

```
$ git init
```

해당 디렉토리에 버전관리를 위한 `.git`이라는 하위 디렉토리 생성됨.

> ### 저장소 복제

```
$ git clone <저장소 url>
```

해당 저장소의 프로젝트 히스토리를 전부 받아온다.

> ### 저장소 연결

```
$ git remote add <원격 저장소> <저장소 url>
```

<br />

## 2. 기본 명령어

> ### 저장소 상태 표시

```
$ git status
```

현재 저장소 내부 파일들의 버전관리 상태를 표시한다.

> ### 추적 할 파일 추가

```
$ git add <파일명>
```

스테이지 영역(커밋 전 임시 영역)에 파일 추가.  
명령 수행 후 `git status` 실행 시 파일이 `Tracked`, `Staged` 상태로 변경된다.

### **_add의 원리_**

1. add하면 index가 생성됨.
2. index에 파일명과 objects 값 생성됨.
3. objects에는 파일의 내용이 저장됨.
4. 파일명이 달라도 파일 내용이 같다면 objects 값이 같다.

> ### 변경사항 커밋

```
$ git commit -m "<커밋 메시지>"
```

스테이지 영역에 있는 파일들의 변경사항을 메시지와 함께 저장소에 반영한다.  
`-a` 옵션 사용 시 `git add`를 생략하고 바로 커밋 가능.

> ### 변경된 내역 원격 저장소에 보내기

```
$ git push -u <원격 저장소> <브랜치>
```

마지막으로 커밋한 사항을 원격 저장소에 올린다.  
`-u` 옵션은 원격 저장소로 업데이트 받은 후 push 한다는 의미.

> ### 원격 저장소에서 변경사항 가져오기

```
$ git pull <원격 저장소>
```

해당 원격 저장소의 변경사항들을 로컬 저장소로 가져온다.

> ### 파일 삭제

```
$ git rm <파일명>
```

해당 명령으로 Staging Area에서 삭제 후 커밋하면 파일이 삭제된다.  
`--cached` 옵션을 사용하면 로컬 저장소에서는 삭제하지 않는다.

<br />

## 3. 되돌리기

> ### 커밋 수정

```
`$ git commit --amend
```

마지막으로 한 커밋을 수정할 수 있다. (덮어씀)

> ### 파일 Unstage로 변경

```
$ git reset HEAD <파일명>
```

Staging Area에 있는 파일을 꺼낼 수 있다.

> ### Modified 파일 되돌리기

```
$ git checkout -- <파일명>
```

해당 파일을 수정 이전의 파일로 덮어쓴다.  
**하지만 수정했던 내용이 전부 사라지기때문에 주의!**

<br />

## 4. 브랜치

> ### 브랜치 목록

```
$ git branch
```

브랜치 목록과 현재 브랜치를 표시.
`-r` 옵션 사용 시 서버의 브랜치 표시.

> ### 브랜치 생성 및 이동

```
$ git checkout -b <브랜치명>
```

<브랜치명>으로 브랜치 생성 후 이동한다.

> ### 브랜치 삭제

```
$ git branch -d <브랜치명>
```

> ### 브랜치 합치기

```
$ git merge <브랜치명>
```

다른 브랜치를 현재 브랜치로 합친다.  
`--no-commit` 옵션 사용 시 커밋하지 않고 합침.

<br />

## 5. Git 이력

`$ git log`

> ### 모든 이력 표시

```
$ git log
```

> ### 특정 파일, 디렉토리 이력만 표시

```
$ git log <파일명>
```

> ### 변경사항을 함께 표시

```
$ git log -p
```

> ### n개의 항목만 표시

```
$ git log -n
```

> ### 로그의 첫 번째 요약 줄만 표시

```
$ git log --pretty=short
```

> ### 시각적으로 표시

```
$ git log --graph
```
