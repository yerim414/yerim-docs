# GIT

git 저장소 자동 생성 스크립트

```bash
#!/bin/bash

# 저장소 이름을 사용자로부터 입력받음
read -p "저장소 이름을 입력하세요: " REPO_NAME

# 저장소 디렉토리 생성
mkdir -p "/home/git/$REPO_NAME.git"

# 저장소 초기화
cd "/home/git/$REPO_NAME.git"
git init --bare

# 권한 설정
chown -R git:git "/home/git/$REPO_NAME.git"

#chmod -R 755 "/home/git/$REPO_NAME.git"
chmod -R g+w ./*
find -type d -exec chmod g+s {} +

# 저장소 URL 출력
echo "저장소가 생성되었습니다: ssh://<사용자명>@<호스트주소>:/home/git/$REPO_NAME.git"
```

git clone repository

- 브랜치 관련 명령어
    
    [https://git-scm.com/book/ko/v2/Git-브랜치-브랜치란-무엇인가](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)
    
    - 새로운 브랜치 생성
    
    ```bash
    git branch yerim_dev
    ```
    
    - 브랜치 이동하기
    
    ```bash
    git checkout yerim_dev
    ```
    
    - 브랜치 목록 확인
    
    ```bash
    git branch
    git branch -v // 브랜치의 상세 정보 확인가
    ```
    
    - 마스터 브랜치에 내 작업 병합하기
    
    ```bash
    git checkout master // 마스터 브랜치로 이동
    git merge origin yerim_dev
    ```
    
    - 브랜치 삭제
    
    ```bash
    git branch -d 브랜치 이름 //로컬 삭제
    git push 원격 저장소 이름 -d 브랜치 이름 //원격 삭제
    ```
    
- 롤백
    
    ```bash
    git reset // 커밋 history를 이전으로 되돌린다.
    
    git revert // 커밋 history를 유지한 체 로컬 파일만 이전 상태로 되돌린다.
    
    ```
    
    **reset은 레포지토리를 혼자 사용할때만 사용하자**
    
    ```bash
    git revert HEAD // 바로 이전 커밋으로 되돌린다.
    
    git revert 커밋아이디 // 특정 커밋아이디로 되돌린다.
    
    git revert -m 1 HEAD // 마지막 커밋이 merge라면, 마지막 커밋으로 되돌린다.
    
    git revert --no-commit 커밋아이디 // 특정 커밋아이디를 stage에는 올라가지만 commit하지는 않은 상태로 되돌린다.
    ```
    
- 추적 파일 제거
    
    git ignore 에 파이썬 .pyc 파일 추적을 해줬는데 이전에 .pyc파일들을 push 해버려서 계속 추적되고 있음
    
    ```bash
    git rm --cached -r .
    git add .
    git commit -m "Remove pyc files from tracking"
    ```
    
    `git rm --cached -r .` : 현재 디렉터리의 모든 추적 파일을 제거하지만, 실제 파일은 삭제하지 않는다. (이 과정에서 `.gitignore` 규칙을 적용)
    
    다른 소스코드의 변경사항이 없을때 하기!!
    

git 오류

- **Pulling is not possible because you have unmerged files 에러**
    
    **Pulling is not possible because you have unmerged files**
    
    ```bash
    error: Pulling is not possible because you have unmerged files.
    hint: Fix them up in the work tree, and then use 'git add/rm <file>'
    hint: as appropriate to mark resolution and make a commit.
    fatal: Exiting because of an unresolved conflict
    ```
    
    로컬에서 변경한 파일과 원격 저장소의 파일이 충돌(conflict)하여 병합되지 않은 상태
    
    병합을 해주거나 강제로 pull 을 받을 수 있다.
    
    ```bash
    git reset --hard HEAD
    git clean -fd
    git pull origin <branch-name>
    ```
    
    - `git reset --hard HEAD`
        - 현재 브랜치에서 변경된 파일을 전부 삭제하고, 마지막 커밋 상태로 되돌린다.
        - `-hard` 옵션을 사용하면 **스테이징된 파일과 작업 중인 파일을 모두 삭제**
    - `git clean -fd`
        - `f`(force): 강제 삭제
        - `d`(directories): 추적되지 않는 디렉토리까지 삭제
        - **Git이 추적하지 않는 파일(예: `.gitignore`에 포함된 파일 등)도 삭제함**
    - `git pull origin <branch-name>`
        - 원격 저장소에서 최신 코드 가져오기
