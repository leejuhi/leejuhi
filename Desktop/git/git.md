## git 정리 하기

# 터미널 명령어

- mkdir 파일이름 (파일 생성)
- cd 파일이름 (파일 안으로 이동)
- touch 파일이름 -빈 파일 생성
- cat 파일이름 - 읽어옴

# 사용자 설정

- 이름: git config user.name “”
- Email: git config user.email “”

# Commit file 반영

- git add 파일이름 or 전체 업뎃시 .->git commit -m “메시지“
- git status git 상태보기
- git reset 파일 이름 - staging area에서 삭제
- git push: local 에서 바뀐 내용을 remote 해줌 (local->remote)
  - 주소 바꾸기 git remote remove origin -> 다시 git remote add origin "url"
  - 주소 확인하기 git remote -v
- git pull: remote에서 local로 가져오기 (현재 로컬 저장소에서 무슨 변화가 있었다면 git stash로 임시 저장)
- git clone "url": 다른 사람의 프로젝트 가져오기

# Commit 다루기

- git log (--pretty=oneline): commit 기록 일지 보기
- git show (commit id 앞 네자리만 쳐도 됨)
- **최신 커밋 수정**
  - git commit: commit 메시지 창이 뜨면서 i를 누르면 수정 esc를 누르고 :wq를 적으면 수정 종료
  - git commit --amend: 최신 커밋 수정
  - 어렵다
- 단축기 붙이기
  - git config alias.단축어 '명령어 내용'
- 커밋끼리 비교하기
  - git diff log아이디1 log아이디2
- head :가장 최근에 한 커밋이 원래인데 바꾸는 법
  - git reset --hard 가고 싶은 커밋아이디 4자리
    - head가 과거의 커밋을 가르키게 함
    - 워킹 디렉토리를 과거 커밋으로 설정함
    - 최근 커밋 복구 x
  - git reset --mixed xxxx
    - staging area만 reset
  - git reset --soft xxxx
    - repository만 reset
  - 아이디 말고 head~번호를 써도 됨
  - git tag 별명 아이디 를 쓰면 별명으로 쓸 수 있음
    - 별명 확인 시 git tag를 사용하면 어떤 별명 사용하는지 보임
    - git tad -d 별명 ->별명 해제

# branch 정리(나무)

- git branch 이름: 이름의 브랜치를 만듬
- git checkout 브랜치 이름: 다른 브랜치로 작업 영역을 옮겨감
- git branch -d 브랜치 이름: 브랜치 이름 삭제
- git checkout -b 브랜치 이름: git branch+checkout 브랜치이름 과 같은 기능
- git merge 브랜치 이름: 현재 브랜치에 브랜치이름에 커밋되어 있는 내용을 합병 시킴
