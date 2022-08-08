---
layout: post
title: "22-08-02-git 사용법 "
categories:
  - etc
---

# Repository 연결 설정

`git remote add origin https://~~.git` >> remote : 원격저장소(깃허브) 이름을 `origin`으로 설정

`git branch -M main` >> 브랜치 설정

`git push -u origin main` >> 로컬저장소와 원격저장소 연결

# Branch

: `main` 자체에서 건들면 위험, 브랜치를 나눠서 기능 구현하고 문제없으면 `main`에 추가

`git branch “name”` > 브랜치 만들기

`git switch “name”` > 브랜치 이동

`git switch -c “name”` > 브랜치 만들고 이동

# Merge

: 기반이 되는 브랜치에 병합할 브랜치에서 수정된 코드들이 추가된다.

main으로 이동 후 병합할 브랜치를 적음

`git merge “병합시킬 브랜치 이름”`

# Push && Pull Request

: push 하고 main 브랜치에 합칠 때 확인 절차, 검증과 피드백을 위해

`git push —set--upstream origin “name”`

> > `origin` 이라는 원천 저장소에 `“name”`이라는 브랜치를 세팅해야함

# Amend

: commit 수정을 위한 명령어

`git commit —amend` >> 직전 커밋의 메세지 수정 및 코드 내용 수정

# Reset

: commit 기록 초기화, 근데 기록이 아예 안남는다.

`git reset “커밋ID”` >> 커밋번호는 git log —oneline 으로 확인

git reset -v 로 관련 명령어 확인

# Revert

: reset 보다는 보통 이걸 쓴다. 되돌려도 기록이 남기때문에

`git revert “커밋ID”`

# Stash

: 변경사항이 있을 때 브랜치를 바꿔서 작업하고 싶은데 커밋은 안하고 잠시 치워두고 작업하고 싶을 때

굳이 브랜치를 안바꿔도 그냥 브랜치 내에서 여러 시도를 해보고 싶을때 사용

`git stash push -m “commit message”` >> 변경사항을 잠시 stash 서랍안에 넣어논 것

`git stash list` >> stash 안에 있는 것들을 볼 수 있음

`git stash show “stashID” -p` >> 변경사항의 자세한 내용이 확인 가능하다 .

후에 적용하고 싶은 stash가 있으면 불러오기

`git stash apply “stashID”` >> 옵션 적용안하면 가장 최근 stash 를 적용함

# cherry-pick

: 다른 브랜치의 코드를 가져오고 싶을 때

`git cherry-pick “해당 커밋 아이디”` >> 다른 브랜치의 커밋 아이디를 가져와서

충돌 발생하면 수정 후 `git add .` > `git cherry-pick —continue` 해서 커밋 메세지 수정 후 저장

- Feat - 새로운 기능 추가
- Fix - 버그 수정
- Build - 빌드 관련 파일 수정
- Ci - CI관련 설정 수정
- Docs - 문서 (문서 추가, 수정, 삭제)
- Style - 스타일 (코드 형식, 세미콜론 추가: 비즈니스 로직에 변경 없는 경우)
- Refactor - 코드 리팩토링
- Test - 테스트 (테스트 코드 추가, 수정, 삭제: 비즈니스 로직에 변경 없는 경우)
- Chore - 기타 변경사항 (빌드 스크립트 수정 등)

# Rebase

: 루트 브랜치를 바꾸는 것 (다른 브랜치에서 작업을 하다가 베이스 브랜치를 바꾸고 싶을 때 사용한다.)
