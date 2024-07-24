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
- git merge 브랜치 이름: 현재 브랜치에 브랜치이름에 커밋되어 있는 내용을 합병 시킴!!

# git 협업하기

- git fetch: git pull과 다르게 merge하지 않고 가져오기만 함
- git blame 파일이름: 특정 파일의 커밋을 보여줌
  - git show 커밋 아이디: 누가 언제 고쳤는지 보여줌
- git revert: 특정 커밋을 취소하는 기능 1 2 3 중에 revert 2를 하면 2만 사라짐
  - reset이랑 다름
    - reset은 그전의 커밋을 가르키는 거고
    - revert는 최신 커밋 이후로 새로운 커밋을 만듬

# git 활용하기

- git reset을 했을 때 사라지는 것이 아니라 그대로 남아있음
  - git reflog를 쓰면 그 전 커밋들이 모두 보임
- git log --pretty=onelline --all --graph: 그래프로 커밋들의 관계가 보임
- git rebase --continue :conflict나서 merge못한 커밋을 merge
- git stash :임시저장 (workgin directory내용이 깃에 보관)
  - git stash list: 임시 저장된 커밋이 있음
  - git stash apply: 스택에 있는 내용 적용 (최신으로 나옴 아이디를 적으면 그게 나옴)
    - 잘못된 브랜치에서 썻을 때도 활용가능
    - git stash pop: apply와 같지만 한번 쓰면 list에서 사라짐
  - git stash drop 아이디
- git cherry-pick 커밋 아이디: 원하는 커밋만 불러올 수 있음 (branch 옮기기)

## git 협업하기

# pull request

- PR (pull request)
  - 어떤 코드를 클론하고 변경 사항 커밋하고 푸쉬
    - open, merged, closed가 됨
  - pr을 처리할 때 merge 방법
    - merge commit
    - squash and merge
      - branch에 있는 여러개의 커밋을 하나의 커밋으로 합치고 merge하는 브랜치에 옮김 (브랜치가 없어짐)
    - rebase merge
      - branch에 있는 여러개의 커밋을 merge하는 브랜치에 그대로 옮김 (branch는 사라짐)
  - fork : repository를 복사해서 내 저장소에서 코드 작성

# 코드 리뷰하기

- 코드 리뷰: #을 쓰면 pull request 검색 가능
  - suggestion
    - comment: 개선 사항 제시
    - approve: 문제 없음
    - request change: 개선 및 수정 요구
- linting: 스타일 맞춰주는 도구
  - eslint와 prettier이 있음

# 브랜치 전략 (git flow)

- feature 전략: 수정 개발 업데이트를 할 때 새로운 브랜치를 생성해서 사용
  - feature은 develop(main)에서 나와서 develope에 병합됨
- 브랜치 이름은 직관적 지정: _ex)fix/login feat/login_
- 수정을 확인해야할 때 release 수정을 할 때 hotfix 브랜치
- CI(continuous ontegration)
  - 변경 사항을 공유된 통합과정에 공유
- CD 자동화를 통해 소프트웨어를 릴리즈
- github 버저닝
  - semver:1(주요변경사항-리뉴얼).0(기능 추가및 미세한 변경 사항).0(버그 수정)
    - 위에 번호가 올라가면 뒤에 초기화
  - choose tag를 해서 버전을 선택하면 커밋 내역을 가져옴

# 협업 자동화

- code owner 특정 파일 및 디랙토리 책임자 지정
  - .github/CODEOWNNERS
    - READ.ME @username 이런식으로 책임자 지정
    - 리뷰어가 되도록 자동화됨
- pull request 템플릿 기능
  - .github/PULL_REQUEST_TEMPLATE.md
  - 보통 -> pr 요약, 변경 사유, 체크리스트, 추가 사항을
- github workflow??
