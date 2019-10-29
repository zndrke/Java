book 입력 - 객체 배열

~~~java

public class Book {
	String title;
	String author;
	
	void show() {
		System.out.println(title+" "+author);
	}
	
	public Book(String title,String author) {
		this.title=title;
		this.author=author;
	}
}

~~~



~~~java
import java.util.Scanner;
public class BookArray {
	public static void main(String[] args) {
		Book [] book= new Book[2];	//레퍼런스를 갖는 배열 레퍼런스 생성
		
		Scanner sc = new Scanner(System.in);
		for(int i=0;i<book.length;i++) {
			System.out.println("제목>>>");
			String title=sc.nextLine();
			
			System.out.println("저자>>>");
			String author=sc.nextLine();
			
			book[i] = new Book(title,author);	//객체 생성
			
		}
		
		for(int i=0;i<book.length;i++) {
			book[i].show();
		}
		sc.close();
	}
}
~~~

