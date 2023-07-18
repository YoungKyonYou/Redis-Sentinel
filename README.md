# Redis-Sentinel 로컬 환경에서 테스트 하는 방법 

1. Docker Desktop 실행
2. docker-compose-sentinel.yaml 이 있는 경로로 powershell로 이동 후 아래 명령어 실행
   - docker-compose -f docker-compose-sentinel.yaml up -d
   - 아래 사진과 같이 제대로 동작하는지 확인
![image](https://github.com/YoungKyonYou/Redis-Sentinel/assets/55623317/23d3f306-5498-4999-9344-beaa31aaf70d)
3. 각 컨테이너마다 내부 ip가 다 다르고 다시 시작할 때마다 바뀜 그래서 확인해서 sentinel.conf 내용을 수정해줘야 함
4. 아래와 같이 마스터와 슬레이브2개의 ip를 확인한 다음 sentinel.conf에 ip를 바꿔준다.
   - sentinel.conf에서 monitor의 마지막 파라미터로 1를 보내줬는데 이건 현재 센티널 서버를 한개만 켰기 때문이다. 3개 켰을 경우엔 2로 바꿔주기 

![image](https://github.com/YoungKyonYou/Redis-Sentinel/assets/55623317/46b36a7c-5028-453c-acb1-cebddaca18c2)
![image](https://github.com/YoungKyonYou/Redis-Sentinel/assets/55623317/1ce1e258-bd87-4e87-9b64-f8bd5548f43e)

5. 입력 후 docker desktop에서 redis-sentinel 컨테이너를 재시작하거나 powershell에서 재시작
6. 재시작이 완료 되면 redis 컨테이너를 중지 시킨 다음 replica나 replica2가 maser로 promotion 됐는지 확인

![image](https://github.com/YoungKyonYou/Redis-Sentinel/assets/55623317/f9e639a3-ced1-4bce-9c1a-3122230bb2f9)

7. 주의할 점은 ip를 제대로 확인하고 127.0.0.1로 하는 실수 하지 말것 
