# CHAP 01-02 Discussion 정리 
24.09.13 update 

## 1. Bootstrap의 동작 과정 
![image](https://github.com/user-attachments/assets/f16fa5f4-9607-4b48-8e7c-5cf3c5d358b0)
1. Power ON
2. ROM(비휘발성 메모리)에 저장되어있는(이미 로드되어있는) BIOS(Basic Input/Output System)을 CPU가 실행
3. BIOS가 POST(power on self test) 진행: 하드웨어가 적절한 상태인지 점검하는 과정 
  ![image](https://github.com/user-attachments/assets/9c252b9c-a208-4a2b-b007-9fe613700a17)
4. POST 검사 성공 시 -> BIOS가 디스크(저장 장치)에 저장되어 있는 boot sector(=first-stage boot loader) RAM에 로드
    ![image](https://github.com/user-attachments/assets/9231d164-b1d2-4c63-b042-f380501a1028)
5. first-stage boot loader가 second-stage boot loader를 로드함
6. second-stage boot loader가 OS kernel을 로드함 


## 2. 키보드 버튼을 눌렀을때의 Interrupt의 동작 과정 
1. 키 입력 감지: 키보드 컨트롤러가 A 키가 눌렸음을 감지합니다.
2. 스캔 코드 생성: 키보드 컨트롤러가 A 키에 해당하는 스캔 코드를 생성합니다.
3. 인터럽트 요청: 키보드 컨트롤러가 시스템에 인터럽트 요청(IRQ)을 보냅니다.
4. CPU 인터럽트: CPU가 현재 작업을 일시 중단하고 인터럽트를 처리합니다.
5. 인터럽트 핸들러 실행: CPU가 키보드 인터럽트 핸들러를 실행합니다.
6. 스캔 코드 읽기: 인터럽트 핸들러가 키보드 컨트롤러로부터 스캔 코드를 읽습니다.
7. ASCII 변환: 스캔 코드를 해당하는 ASCII 코드('A')로 변환합니다.
8. 버퍼에 저장: 변환된 ASCII 코드를 키보드 버퍼(일반적으로 RAM의 특정 영역)에 저장합니다.
9. 프로세스에 전달: 현재 포커스를 가진 프로세스(예: 텍스트 편집기)가 키보드 입력을 요청하면, 운영체제가 버퍼에서 데이터를 읽어 해당 프로세스에 전달합니다.
10. 프로세스 처리: 프로세스가 입력된 'A'를 처리합니다 (예: 화면에 표시).


## 3. DMA가 정확히 어떻게 작동하는지, 구체적인 예시 
![image](https://github.com/user-attachments/assets/1bdb1c21-a195-4486-ab3d-bee0a81a8b64)
![image](https://github.com/user-attachments/assets/ebbae726-3694-4da2-b872-a107891374e3)

* DMA의 사용 예시
  * 디스크 드라이브 컨트롤러, 그래픽 카드, 네트워크 카드, 사운드 카드를 포함한 하드웨어 시스템이 사용함
  * 주변 디바이스에서 전송할 데이터가 많은 경우 이 문제를 해결하기 위해 DMA를 사용함
  * 멀티 코어 프로세스의 칩 내부 데이터 전송에도 쓰임 


### References
* https://yonghwankim-dev.tistory.com/188
* https://ko.wikipedia.org/wiki/%EC%A7%81%EC%A0%91_%EB%A9%94%EB%AA%A8%EB%A6%AC_%EC%A0%91%EA%B7%BC
