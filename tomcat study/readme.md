# 톰캣 포트 오류

톰캣 구동 시

Several ports (8005, 8080) required by Tomcat v9.0 Server at localhost are already in use. The server may already be running in another process, or a system process may be using the port. To start this server you will need to stop the other process or change the port number(s).

이런 오류가 발생한다면
포트오류이다. 
나는 이클립스가 멈춰서 강제종료 시키고 난 뒤 이런 오류가 떴다.

<b><원인></b><br>
Tomcat이 사용하고 있는 기본 포트(8080, ~)이 이미 사용중이라 생기는 오류

<b><해결></b>
1. cmd 창
2. netstat -p tcp -ano
3. 로컬 주소가 0.0.0.0:8080 인 것을 찾고 해당 PID값을 인지
4.taskkill /f /pid ~
~ 는 해당 PID값을 넣으면 된다.

이렇게 해결함.
