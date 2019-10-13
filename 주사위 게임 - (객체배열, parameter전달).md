주사위 게임 - (객체배열, parameter전달)

~~~java

public class Dice {
	private final int MAX=6;
	
	private int value;
	
	public Dice() {			//생성자
		value=1;
	}
	
	public int roll() {		
		return value=(int)(Math.random()*MAX)+1;
	}
	
	public int getValue() {
		return value;
	}
}
~~~



~~~java

public class Member {
	private String name;
	
	private int win=0;
	private int num=0;
	
	public Member() {}		//생성자	
	
	public void setName(String n) {
		name=n;
	}
	
	public String getName() {
		return name;
	}
	
	public void setWin(){
		
			win++;
	}
	
	public int getWin() {
		return win;
	}
	
	public void setNum(int n) {
		num=n;
	}
	
	public int getNum() {
		return num;
	}	
}
~~~



~~~java
import java.util.Scanner;

public class Game {
	
	public static int Game(Member[] m) {
		
		Dice dice1= new Dice();
		Dice dice2= new Dice();
		int d1=0;int d2=0;
		
		Scanner sc= new Scanner(System.in);
		int k=0;
		System.out.println("*** 지금부터 게임을 시작합니다 ***");
		
		while(true) {
			System.out.println("Game #"+ (k+1));	
			
			for (int j=0;j<m.length;j++) {
				System.out.print(m[j].getName()+"차례입니다. 1을 입력하세요. 0은 게임종료");
				if(sc.nextInt()==0) {
					System.out.println("게임을 종료합니다.");
					return k;
				}
					
				d1=dice1.roll();
				d2=dice2.roll();
				System.out.println(m[j].getName()+": 첫번쨰 주사위 "+d1+" 두번째 주사위 "+ d2+ " 두 주사위의 합 : "+ (d1+d2));
				m[j].setNum(d1+d2);
			}
			int max=0;
			System.out.print("이번 게임의 승자는 ");
			for(int l=0;l<m.length;l++) {
				if(m[l].getNum()>max) {
					max=m[l].getNum();
				}
			}
			for(int l=0;l<m.length;l++) {
				if(m[l].getNum()==max) {
					System.out.print(m[l].getName()+" ");
					m[l].setWin();
				}
			}
			System.out.println("입니다");
			k++;	
		}
	}

	public static void main(String[] args) {
		
		Scanner sc= new Scanner(System.in);
		
		int player;
		int num;
		
		while(true) {
			System.out.println("게임 참가자의 수를 입력하시오.");
			player=sc.nextInt();
			
			if (player>1&&player<7)
				break;
			else 
				System.out.println("2~6의 인원을 입력하시오");
		}
		
		Member [] m;
		m= new Member[player];
		
		for(int i=0;i<m.length;i++) {
			System.out.println(i+1 +"번째 참가자 이름 입력:");
			
			m[i]= new Member();
			m[i].setName(sc.next());
		}
		
		num=Game(m);
		
		System.out.println("전체 "+num+"게임 중");

		for(int i=0;i<m.length;i++) {
			System.out.print(m[i].getName() +" "+ m[i].getWin()+"승   ");
			System.out.println(" 하였습니다.");
		}
	}
}
~~~



주사위 2개를 이용하여 2~6명의 플레이어가 주사위 게임을 한다.

주사위 2개의 수를 합산하여 가장 큰 수를 얻은 참가자가 게임의 승자가 된다.

게임은 0을 입력할 때까지 반복한다. 

게임이 끝나면 각 게임의 횟수와 승수를 출력하도록 한다.