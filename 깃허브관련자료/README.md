eclipse 로 프로젝트 진행 한 다음 git에 push후 pr을 날릴 경우 기존의 레파지토리에 저장되어있던 파일과 현재 내가 push 날리려는 파일간의 conflict가 날 수 있다.

이럴경우 보통은 pr 날리는 곳에서 resolve conflicts 버튼을 눌러 파일 내용을 수정을 해서 다시 pr을 보내면 된다. 하지만 resolve conflicts 가 비활성화 되는 경우가 있다.

confilct 난 파일의 양이 많을 경우 대부분 이런 현상이 발생한다.

처음에는 eclipse 에서 일일히 비교하면서 수정해서 다시 pr을 보냈었는데 너무나 비효율적이여서 해결방법을 찾다가 개발지인의 추천으로 github desktop을 이용해 수정하는 방법을 알아 냈다.
github desktop에 들어가 내가 pr 날릴 브랜치로 변경후 local에서 해당 브랜치-> master로 merge를 시도한다.
merge버튼을 누르면 충돌 발생 시 충돌 파일을 알려주고, open in visual studio code를 눌러서 충돌 부분을 해결할 수 있다.

vscode로 파일에 들어가면 충돌 부분을 확인할 수 있다.
master 부분은 초록색으로 감싸져 있을 거고 브랜치는 파란색으로 감싸져있을 것이다.
두 부분을 보고 지울 내용을 지우고 저장후 다시 github desktop으로 돌아오면 confilct 났었던 파일이 사라진다. 그리고 다시 commit merge 후 상단에 push origin을 이용해 push하면 머지가 잘 된다.
