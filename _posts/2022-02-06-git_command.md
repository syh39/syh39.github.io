---
title: "Git add, commit, push 한번에 하기"
excerpt: "블로그 게시물을 쓸 때 보통 Typora로 게시물을 쓰고 깃허브 저장소로 올릴 때는 위 3가지 명령어로 올리는데 매번 쓰다보니 3가지 명령어를 차례대로 쓰는게 귀찮아서 한번에 올리는 방법이 없을까 생각하다가 방법을 찾았다. "

categories:
  - Git
tags:
  - Git
last_modified_at: 2022-02-06 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

---


### Cmd에서 git add, commit, push 한번에 하기

블로그 게시물을 쓸 때 보통 Typora로 게시물을 쓰고 깃허브 저장소로 올릴 때는  

1. `git add .` 
2. `git commit -m 'commit message'` 
3. `git push` 

위 3가지 명령어로 올리는데 매번 쓰다보니 3가지 명령어를 차례대로 쓰는게 귀찮아서 한번에 올리는 방법이 없을까 생각하다가 방법을 찾았다. 

`git config --global alias.cmp '!f() { git add -A && git commit -m "$@" && git push; }; f'`

명령어로 .gitconfig 파일에 alias를 추가해주면 된다.

이렇게 하면 `git cmp 'commit message'` 이 한줄로 위의 3줄과 동일한 명령어를 실행할 수 있게 된다. 



### 출처

- <https://stackoverflow.com/questions/19595067/git-add-commit-and-push-commands-in-one>
