# CHAP 03 Discussion 정리 
2024.10.25 update (작성중) 

## 1. waiting (queue)가 필요한 이유? waiting queue와 i/o queue(device queue)의 차이 
waiting queue는 i/o와 같은 이벤트가 발생했을 때 필요한 것 
* i/o queue를 waiting queue의 일종으로 볼 수 있다


## 2. PC의 역할? 
다음 실행될 명령어의 주소를 가리키는 역할 

## 3. IR? DR?
* IR: Instruction Register
  * 가장 최근에 인출된 명령어(현재 실행 중인 명령어)가 저장되어 있는 레지스터
* DR: Data Register
  * 데이터 레지스터(DR)은 메모리에서 읽은 데이터나 메모리에 쓸 데이터를 저장하는 데 사용


## 4. 멀티프로그래밍 vs. 멀티프로세싱 vs. 멀티타스킹 vs. 멀티스레딩 




## 5. 부모 프로세스-자식 프로세스 실행 코드 이해 
```C 
#include <stdio.h>
#include <stdlib.h>

int main() 
{
    pid_t pid;
    pid = fork();  // 새로운 프로세스를 생성
    
    if(pid < 0) {
	    fprintf(stderr, "Fork Failed");
	    return 1;
    } 
    else if(pid == 0) {
     // 자식 프로세스
	    execlp("/bin/ls", "Ls", NULL); // 프로그램을 실행
    } 
    else {
    // 부모 프로세스
	    wait(NULL); // 자식 프로세스가 종료될 때까지 대기
	    pintf("Child Complete");  // 자식 프로세스가 완료된 후 메시지 출력
    }
    return 0;
}
```

## 6. 부모 프로세스- 자식 프로세스 PID 출력 이해 - fork()
![image](https://github.com/user-attachments/assets/0b8355cf-d9e5-43c0-a3ac-590145647603)

![image](https://github.com/user-attachments/assets/110a2da9-4f97-4321-88c4-b1cb414fcbae)

* fork() 명령어는 부모 프로세스가 자식 프로세스를 만드는 명령어
* 부모 프로세스에게 생성한 자식프로세스의 고유 pid를 리턴, 자식 프로세스에게는 0을 리턴한다


### References
* https://technote.kr/310
* https://oobwrite.com/entry/%EC%BB%B4%ED%93%A8%ED%84%B0-%EA%B5%AC%EC%A1%B0-%EB%A0%88%EC%A7%80%EC%8A%A4%ED%84%B0Registers-%EC%B4%9D%EC%A0%95%EB%A6%AC
