- 준비큐에 있는 프로세스에 대해 CPU 할당하는 방법
	- 선점 vs 비선점
	- 비선점
		- FCFS(First Come First Start)
		- SJP(Shortest Job First)
			- 버스트 타임 : CPU가 사용하는 시간
			- 버스트 타임이 짧은 거 부터 할당
	- 선점
		- SRT(Shortest Remaining Time)
			- 남은 시간이 짧은 것을 선정
			- 먼저 실행된 애가 남은 시간이 내 실행시간보다 길다 -> 뺏기
		- 라운드로빈
			- 타임 슬라이스( == 타임 퀀텀)이 심하게 크면 FCFS와 다를 게 없다.
			- 그런데 너무 짧으면 또 context switching을 하는 것에 시간이 오래 걸림
		- 우선순위