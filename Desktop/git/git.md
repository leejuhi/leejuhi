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
  -git commit --amend: 최신 커밋 수정
