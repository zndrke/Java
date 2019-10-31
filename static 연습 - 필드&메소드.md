static 연습 - 필드&메소드

~~~java

public class StaticSample {
	public int n;
	public void g() {
		m=20;
	}
	public void h() {
		m=30;
	}
	public static int m;
	public static void f() {
		m=5;
	}
	
	public static void main(String[] args) {
		StaticSample s1,s2;
		s1= new StaticSample();
		s1.n=5;		//s1만의 변수, 공유 x
		s1.g();		//m=20
		s1.m=50;	//m=50
		s2=new StaticSample();
		s2.n=8;		//s2만의 변수, 공유 x
		s2.h();		//m=30
		s2.f();		//m=5
		System.out.println(m);
		
		StaticSample.m=50;	//클래스에서 static변수 m은 하나이기 때문에 클래스명.m으로 접근가능
		System.out.println(m);
	}
}

~~~



~~~java

public class StaticMethod {
	int n;
	void f1(int x) {	//non-static 메소드에 non-static 필드 (o)
		n=x;
	}
	void f2(int x) {	//non-static 메소드에 static 필드 (o)
		m=x;
	}
	
	static int m;
	/*
	static void s1(int x) {	//static 메소드에 non-static 필드 (x)
		n=x;
	}
	
	static void s2(int x) {//static 메소드에 non-static 메소드 (x)
		f1(3);
	}
	*/
	static void s3(int x) {	//static 메소드 static 필드 (o)
		m=x;
	}
	static void s4(int x) {	//static 메소드 static 메소드 (o)
		s3(x);
	}
}
~~~

