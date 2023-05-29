# 멀티 프로세싱
다수의 [프로세서](Processor.md)가 다수의 일을 함께 처리

여러 프로세서(CPU)에 프로그램을 병렬로 실행하여 실행속도를 극대화한다.

하나의 프로세서가 고장나더라도 해당 프로세서가 진행중인 작업은 다른 프로세서에서 수행하고 있기 때문에 작업이 정지되지 않는다.

또한 여러개의 프로세스가 수행되어야 할 때, 동일한 데이터를 사용한다면 각 데이터를 각 프로세서에게 할당할 필요 없이 하나의 공간에 데이터를 저장한 후 이를 공유하여 사용하도록 한다면 비용을 절약할 수 있다.