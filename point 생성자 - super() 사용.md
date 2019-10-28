point 생성자 - super() 사용



~~~java

public class Point {
	private int x,y;
	public Point(int x,int y) {		//슈퍼 클래스 생성자
		this.x=x;
		this.y=y;
	}
	
	
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
	
	public ColorPoint(int x,int y,String color) {	//생성자
		super(x,y);			//슈퍼클래스 생성자 호출
		this.color=color;
	}
	
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
		//Point p= new Point();	
		//p.set(1, 2);
		//p.showPoint();
		
		ColorPoint cp = new ColorPoint(3,5,"yellow");	//객체 생성
		//cp.set(3, 5);			//상속받은 set메소드 사용
		//cp.setColor("red");		
		cp.showColorPoint();	
	}
}
~~~

