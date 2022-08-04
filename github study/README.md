# 목차

1. [git conflict 해결방법](#1.-git-conflict-해결방법)

2. [github folder rename 방법](#2.-github-folder-rename-방법)

3. [github 사진 첨부 방법](#3.-github-사진-첨부-방법)

4. [git rebase](#4.-git-rebase)

---

## 1. git conflict 해결방법 

eclipse 로 프로젝트 진행 한 다음 git에 push후 pr을 날릴 경우 기존의 레파지토리에 저장되어있던 파일과 현재 내가 push 날리려는 파일간의 conflict가 날 수 있다.

이럴경우 보통은 <b>pr 날리는 곳에서 resolve conflicts 버튼을 눌러 파일 내용을 수정을 해서 다시 pr을 보내면 된다.</b> 하지만 <b>resolve conflicts 가 비활성화</b> 되는 경우가 있다.

<b>confilct 난 파일의 양이 많을 경우</b> 대부분 이런 현상이 발생한다.

처음에는 eclipse 에서 일일히 비교하면서 수정해서 다시 pr을 보냈었는데 너무나 비효율적이여서 해결방법을 찾다가 개발자 친구의 추천으로 <b>github desktop</b>을 이용해 수정하는 방법을 알아 냈다.

1. github desktop에 들어가 내가 pr 날릴 브랜치로 변경후 <b>local에서 해당 브랜치-> master로 merge를 시도</b>한다.

2. merge버튼을 누르면 충돌 발생 시 충돌 파일을 알려주고, open in visual studio code를 눌러서 충돌 부분을 해결할 수 있다.

그리고 vscode로 파일에 들어가면 충돌된 부분을 시각적으로 확인할 수 있다.

<b>master 부분은 초록색으로 감싸져 있을 거고 브랜치는 파란색</b>으로 감싸져있을 것이다.

두 부분을 보고 지울 내용을 지우고 저장후 다시 github desktop으로 돌아오면 confilct 났었던 파일이 사라진다. 그리고 다시 <b>commit merge 후 상단에 push origin을 이용해 push</b>하면 머지가 잘 된다.

-------------

## 2. github folder rename 방법

레파지토리에서 폴더를 이용해 파일들을 관리할 경우에 폴더의 이름을 수정해야하는 상황이 필요할때가 있다.

보통의 경우 웹사이트에서 물리적으로 수정할 수도 있지만 폴더가 많을경우에는 일일히 수정하기 버거울 때가 있어 git bash 커맨드를 이용해서 수정할 때가 있다.

그럴땐

~~~
git mv 기존폴더명 바꿀폴더명
~~~

을 기입해서 수정하면 된다. 그런데 아래와 같은 오류가 발생할 경우가 생긴다.

오류 사진<br>
![rename ex2.PNG](https://github.com/YoonSeung/TIL/blob/master/github%20study/png/rename%20ex2.PNG?raw=true)

사진에서 보면

<b>fatal : destination 'study' is not a directory</b> 라고 뜨면서 수정이 되지 않는다.

이럴 경우는 보통 띄어쓰기로 되어있는 이름명으로 수정하려고 할 경우에 생긴다.

그래서 수정을 할 경우 어쩔 수 없이 폴더이름을 붙여서 수정해야 할 경우가 있었는데 내 생각에는 분명히 이 부분도 해결 할 수 있을 것 같았다. 그래서 찾아보았고 해결방법을 알아냈다.

해결 방법<br>
![folder rename ex.PNG](https://github.com/YoonSeung/TIL/blob/master/github%20study/png/folder%20rename%20ex.PNG?raw=true)

그건 바꿀 폴더명을 " " 로 감싸는 방법 이다. 위의 사진의 방법대로 수정을 해서 지금의 TIL 폴더명으로 수정했다. 

---

## 3. github 사진 첨부 방법
사진을 첨부하는 방법이 구글링을 통해 찾아서 해보았는데 크게 2가지였다.

1.issue를 활용하는 방법 

2.파일을 폴더에 넣고 불어보는 방법


~~~
2번 예시
customer A
![jpg_1](./img/1.JPG)
~~~

그런데 나는 1번 issue를 활용하는 방법은 나중에 사진이 지워질경우나 수정이 필요할 경우 사라지면 골치가 아파질것 같아서 사용하지 않았고,

2번 경우에는 첨부가 잘 되지 않았다. (자꾸 엑스박스로 뜸)

그래서 오류를 찾다가 2번에서 () 안의 링크를 물리적으로 적용하는 방식으로 해결했다.

해결 방법<br>
![img add ex.png](https://github.com/YoonSeung/TIL/blob/master/github%20study/png/img%20add%20ex.png?raw=true)

위와 같이 사진의 주소를 복사한 후 

~~~
customer A
![jpg_1]( 이 곳에 복사한 주소를 붙여넣기 )
~~~

를 하면 된다.

---

## 4. git rebase

git rebase를 쓰는 이유는 github의 전략 중 하나인데 

기존의 경우 브랜치를 나눠 각자 기능을 구현 후 pr을 날리고 머지를 하면 merge commit 기록이 남는다. 그런데 이 merge commit 기록을 남기지 않고 머지를 시킬 수 있는 방법이 rebase 이다.

