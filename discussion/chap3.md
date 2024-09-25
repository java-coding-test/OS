# CHAP 03 Discussion 정리 
2024.09.25 update (작성중) 

## 1. waiting (queue)가 필요한 이유? 


## 2. PC의 역할? 

## 3. IR? DR?
* IR: Instruction Register
* DR: Data Register

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



