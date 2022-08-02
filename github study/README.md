# 1. git conflict 해결방법 
eclipse 로 프로젝트 진행 한 다음 git에 push후 pr을 날릴 경우 기존의 레파지토리에 저장되어있던 파일과 현재 내가 push 날리려는 파일간의 conflict가 날 수 있다.

이럴경우 보통은 <b>pr 날리는 곳에서 resolve conflicts 버튼을 눌러 파일 내용을 수정을 해서 다시 pr을 보내면 된다.</b> 하지만 <b>resolve conflicts 가 비활성화</b> 되는 경우가 있다.

<b>confilct 난 파일의 양이 많을 경우</b> 대부분 이런 현상이 발생한다.

처음에는 eclipse 에서 일일히 비교하면서 수정해서 다시 pr을 보냈었는데 너무나 비효율적이여서 해결방법을 찾다가 개발자 친구의 추천으로 <b>github desktop</b>을 이용해 수정하는 방법을 알아 냈다.

github desktop에 들어가 내가 pr 날릴 브랜치로 변경후 <b>local에서 해당 브랜치-> master로 merge를 시도</b>한다.
merge버튼을 누르면 충돌 발생 시 충돌 파일을 알려주고, open in visual studio code를 눌러서 충돌 부분을 해결할 수 있다.

vscode로 파일에 들어가면 충돌된 부분을 시각적으로 확인할 수 있다.
<b>master 부분은 초록색으로 감싸져 있을 거고 브랜치는 파란색</b>으로 감싸져있을 것이다.
두 부분을 보고 지울 내용을 지우고 저장후 다시 github desktop으로 돌아오면 confilct 났었던 파일이 사라진다. 그리고 다시 <b>commit merge 후 상단에 push origin을 이용해 push</b>하면 머지가 잘 된다.

-------------

# 2. github folder rename 방법

레파지토리에서 폴더를 이용해 파일들을 관리할 경우에 폴더의 이름을 수정해야하는 상황이 필요할때가 있다.
보통의 경우 웹사이트에서 물리적으로 수정할 수도 있지만 폴더가 많을경우에는 일일히 수정하기 버거울 때가 있어 git bash 커맨드를 이용해서 수정할 때가 있다.
그럴땐

~~~
git mv 기존폴더명 바꿀폴더명
~~~

을 기입해서 수정하면 된다.
