### Instanceof###

~~~java
class Person{}
class Student extends Person{}
class Researcher extends Person{}
class Professor extends Researcher{}

public class InstanceofEx {
	static void print(Person p) {
		if(p instanceof Person)
			System.out.print("Person ");
		if(p instanceof Student)
			System.out.print("Student ");
		if(p instanceof Researcher)
			System.out.print("Researcher ");
		if(p instanceof Professor)
			System.out.print("Professor ");
		System.out.println("");
	}
	public static void main(String [] args) {
		System.out.print("new Student() ->\t");
		print(new Student());
		System.out.print("new Researcher() ->\t");
		print(new Researcher());
		System.out.print("new Professor() ->\t");
		print(new Professor());
	}
}
~~~



>Output
>
>new Student() ->	Person Student 
>new Researcher() ->	Person Researcher 
>new Professor() ->	Person Researcher Professor 



> Instanceof 를 통해 자신의 클래스와 모든 슈퍼클래스를 검사할 수 있다
>
> Professor 객체의 경우 Researcher, Person 클래스를 상속받았기 때문에 
>
> Person, Researcher, Professor 모두 해당된다.