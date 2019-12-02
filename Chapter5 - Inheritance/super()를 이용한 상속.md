### super()를 이용한 상속###



~~~java
//1
class Point {
	private int x, y; // 한 점을 구성하는 x, y 좌표
	public Point() {
		this.x = this.y = 0;
	}
	public Point(int x, int y) {
		this.x = x; this.y = y;
	}
	public void showPoint() { // 점의 좌표 출력
		System.out.println("(" + x + "," + y + ")");
	}
}
//2
class ColorPoint extends Point { 
	private String color; // 점의 색
	public ColorPoint(int x, int y, String color) {
		super(x, y); // Point의 생성자 Point(x, y) 호출
		this.color = color;
	}
	public void showColorPoint() { // 컬러 점의 좌표 출력
		System.out.print(color);
		showPoint(); // Point 클래스의 showPoint() 호출
	}
}

public class SuperEx {
	public static void main(String[] args) {
		ColorPoint cp = new ColorPoint(5, 6, "blue");
		cp.showColorPoint();
	}
}
~~~



> //1
>
> 점을 찍는 클래스Point
>
> - 멤버 : x, y
> - 생성자: 0,0으로 초기화 || x,y로 초기화
> - ShowPoint 메소드: 좌표를 출력



> //2
>
> 색을 찍는 클래스 ColorPoint를 Point 상속받아 사용
>
> - 멤버 color
> - **생성자: ColorPoint(int x,int y, String Color)에서 x,y 값을 super(x,y)로 슈퍼클래스의 생성자 사용**
> - ShowColorPoint 메소드: 자신의 멤버color를 찍고 슈퍼클래스의 메소드 showPoint()를 통해 좌표출력