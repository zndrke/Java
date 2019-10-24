콘서트 예약 프로그램 - equals 메소드와 ==연산자의 차이



~~~java
//좌석 클래스
public class Seat {
	boolean chair;
	String name;
	
	public void Seat() {	//생성자 초기화
		chair=false;
	}
	
	public void setSeat(String name) {	
		chair=true;
		this.name=name;
	}
	public void showSeat() {
		if (chair==false) {
			System.out.print("--- ");
		}
		else {
			System.out.print(name);
		}
	}
	
	public void clearSeat(String name) {
		
		if(name.equals(this.name)){	//equals 메소드와 ==의 차이
			chair=false;
			name=null;
		}	
	}
}
~~~



~~~java
import java.util.Scanner;
public class Customer {
	
	public static void main(String[] args) {
		
		System.out.println("콘서트 예약 시스템 입니다");
		Scanner sc= new Scanner(System.in);
		
		Seat[][] seat = new Seat[3][10];		//레퍼런스 생성
		for(int i=0;i<seat.length;i++) {	//객체 생성 및 초기화
			for (int j=0;j<10;j++){
				seat[i][j]= new Seat();
			}
		}
		while(true) {
			System.out.println("예약 1, 조회 2, 취소 3, 끝내기 4");
			int a= sc.nextInt();
			
			if (a==1) {		//예약
				
				System.out.print("좌석 구분 S(1) A(2) B(3) >> ");
				int cls=sc.nextInt();
				cls--;
				for(int i=0;i<10;i++) {		//좌석 조회
					seat[cls][i].showSeat();
				}
				
				System.out.println("");
				System.out.print("이름>>");
				String name= sc.next();
				System.out.print("번호>>");
				int num=sc.nextInt();
				num--;
				seat[cls][num].setSeat(name);
				
			}
			else if(a==2) {		//조회
				for(int i=0;i<seat.length;i++) {
					for (int j=0;j<10;j++) {
						seat[i][j].showSeat();
					}
					System.out.println("");
				}
				System.out.println("<<<조회를 완료하였습니다>>>");
			}
			else if(a==3) {	//취소
				System.out.print("좌석 구분 S(1) A(2) B(2) >> ");
				int cls=sc.nextInt();
				cls--;
				for(int i=0;i<10;i++) {
					seat[cls][i].showSeat();
				}
				
				System.out.print("이름>>");
				String name =sc.next();
				
				for(int j=0;j<10;j++) {
					seat[cls][j].clearSeat(name);
				}
			}
			else if(a==4) {
				break;
			}
		}
	}
}
~~~



a.equals(b)는 a와 b의 문자열을 비교하고 같으면 true 다르면 false

a==b 는 문자열의 주소값을 비교함. 따라서 파라미터와 객체 필드를 비교할때 적절하지 않음



```java
public void clearSeat(String name) {	
	if(name.equals(this.name)){	//equals 메소드와 ==의 차이
		chair=false;
		name=null;
	}	
}
```
파라미터인 name과 객체의 필드인 this.name은 서로 다른 주소값을 가진다

따라서 둘을 비교할 때 equals 메소드를 사용해야 한다.