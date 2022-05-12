# C언어 랜덤 숫자 출력

## 랜덤 숫자 출력

* 위에  #include<stdlib> 쓰기
  - rand() 사용 가능
* 위에  #include<time.h> 쓰기
  * 시드값을 계속 다르게 만들때 사용됨

__특정한 범위의 값을 랜덤하게 출력할 경우 __

* 나머지 연산자(%)  사용
* ex) 0~9 -> rand()%10
* ex) 10~20 -> rand%11 + 10

문제점!!!

* 첫 실행시 랜덤하게 출력한 값을 다시 출력시키면 매번 같은 데이터 나옴

* 랜덤값을 생성할때 쓰이는 시드값이 같기 떄문

* 이 역할을 하는 함수 -> srand()

  ==> 사용법: main함수 안에 srand(time(NULL)); 써주기

  ====> #include<time.h> 작성  이유

-------------------------------------

예시 - 가위바위보 게임

```c
#include<stdio.h>

#include<stdlib.h>

#include<time.h>

int main(){

	int per = 0, com;
	int c1=0, c2=0, c3=0;// c1 : 이긴 횟수, c2 : 비긴 횟수, c3 : 진 횟수
	int c;
	srand(time(NULL)); //시드가 바뀌게 하기 위해 사용
	while (1) {
		com = rand()%3+1;//랜덤 컴퓨터 숫자 생성
        
		printf("가위(1), 바위(2), 보(3), 종료(4) 선택 : ");
		scanf("%d", &per);
        
        if (per == 4)//4입력시 종료
            break;
        //가위바위보 이기고 질 경우의 수
        if (per == 1) {
            if (com == 2)
                c=1;
            else if (com == 3)
                c = 3;
            else
                c = 2;
        }
         else if (per == 2) {
                if (com == 3)
                    c = 1;
                else if (com == 1)
                    c = 3;
                else
                    c = 2;
       }
		else if (per == 3) {
			if (com == 1)
				c = 1;
			else if (com == 2)
				c = 3;
			else
				c = 2;
		}
		else {//다른 수 입력시 '오류'출력/ 종료
			printf("오류");
			return 0;
		}
        
        //결과확인/ 횟수 세기
		if (c == 1) {
			c1++;
			printf("이겼다.\n");
		}
		else if (c == 2)
		{
			c2++;
			printf("비겼다.\n");
		}
		else {
			c3++;
			printf("졌다.ㅠㅠ\n");
		}
	}
    
    //결과물 출력
	printf("내가 총 이긴 횟수는 %d번, 진 횟수는 %d번, 비긴 횟수는 %d번입니다", c1,c3,c2);
    
    return 0;
}

```



