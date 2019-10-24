color point - 상속

~~~java
public class Point {
	private int x,y;
	//생성자 없음 Point();
	public void set(int x,int y) {	
		this.x=x;
		this.y=y;
	}
	public void showPoint() {		
		System.out.println("("+x+","+y+")");
	}
}
~~~



~~~java
public class ColorPoint extends Point{		//상속 선언
	private String color;
	
	public void setColor(String color) {	
		this.color=color;
	}
	public void showColorPoint() {
		System.out.print(color);
		showPoint();		//슈퍼클래스 메서드 호출
	}
}
~~~



~~~java
public class ColorPointEX {
	public static void main(String[] args) {
		Point p= new Point();	
		p.set(1, 2);
		p.showPoint();
		
		ColorPoint cp = new ColorPoint();	//서브클래스 객체 생성
		cp.set(3, 5);			//상속받은 set메소드 사용
		cp.setColor("red");		
		cp.showColorPoint();	
	}
}
~~~

