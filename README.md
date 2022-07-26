# TIL 
> 오늘 내가 배운 내용 정리. 

> 매일매일의 커밋을 남기려고 노력하되, 어뷰징은 하지 않습니다 

# 2022년 7월 25일

## 기본 명령어 

 1. `git init`
    - git 으로 관리 시작
        - 디렉토리당 한번만 주의! 홈폴더나 바탕화면 x

2. `git status` (중요)
    - 파일 상태 확인

3. `git add` 파일명
    - 무대위로 올리기

4. `git commit -m` "커밋 사유"
    - 변경사항을 기록 즉, 사진 찍기 (vim 빠져 나오는 것 `esc + :q` )


5. `config` 설정 
-> 한번만
->git에게 내가 누군지 알려주기 
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git config --global --list

6. git log
커밋의 내역 확인
--oneline

7. 커밋들을 비교하기
git diff 해쉬값 해쉬값

8. github와 연결
    `git remote add origin URL`
    `git remote -v`


* remote 삭제
    `git remote rm origin`

9. github에 local commits 올리기

    `git push origin master`
