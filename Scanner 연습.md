Scanner 연습

~~~java
import java.util.Scanner;

public class Hello2030 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		String name = sc.next();
		System.out.print("이름은 "+ name +",");
		
		String city = sc.next();
		System.out.print("도시는 "+ city +",");
		
		int age = sc.nextInt();
		System.out.print("나이는 " + age + ",");
		
		double weight =sc.nextDouble();
		System.out.print("체중은 " + weight + ",");
		
		boolean marriage = sc.nextBoolean();
		System.out.println("결혼은 "+ marriage + " 입니다");
		
	}
}
~~~

