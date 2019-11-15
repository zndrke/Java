전화번호부 프로그램



~~~java

import java.util.*;

public class PhoneBook {
	public static void main(String[] args) {
		HashMap<String,Phone> map = new HashMap<String,Phone>();	//해시맵 레퍼런스 map
		int n;
		Scanner sc = new Scanner(System.in);
		
		System.out.println("몇 명을 저장하시겠습니까?");
		n=sc.nextInt();
		
		for(int i=0;i<n;i++) {
			System.out.println((i+1) + "이름");
			String name=sc.next();
			System.out.println((i+1) + "전화번호");
			String number=sc.next();
			System.out.println((i+1) + "주소");
			String address=sc.next();
			
			map.put(name,new Phone(name,number,address));	//저장
		}
		
		while(true) {
			System.out.println("삽입:0	삭제:1	찾기:2	전체보기:3		종료:4	");
			int m;
			m=sc.nextInt();
			if(m==0) {
				//삽입
				System.out.println("이름");
				String name=sc.next();
				System.out.println("전화번호");
				String number=sc.next();
				System.out.println("주소");
				String address=sc.next();
				
				map.put(name,new Phone(name,number,address));
			}
			else if(m==1) {
				//삭제
				System.out.println("삭제 하려는 이름");
				String name=sc.next();
				map.remove(name);
				
			}
			else if(m==2) {
				//찾기
				System.out.println("조회 하려는 이름");
				String name=sc.next();
				
				Phone phone= map.get(name);	//해시맵의 value를 phone에 저장
				if(map.containsKey(name)) {	//키가 존재하면
					System.out.println("이름"+phone.getName());
					System.out.println("번호"+phone.getNumber());
					System.out.println("주소"+phone.getAddress());
				}
				else
					System.out.println(name+"등록되지 않은 사람입니다.");
			}
			else if(m==3) {
				//전체보기
				
				Iterator<String> it = sortByValue(map).iterator();	
				//list를 정렬한 후 itorator를 통해 접근
				while(it.hasNext()) {
				String name = (String) it.next();	//캐스팅
				Phone phone= map.get(name);
				
				System.out.println("이름"+phone.getName());
				System.out.println("번호"+phone.getNumber());
				System.out.println("주소"+phone.getAddress());}
			}
			else if(m==4) {
				return;
			}
		}
	}
	
	public static List sortByValue(final Map map) {

		List<String> list = new ArrayList();	//컬렉션 저장
		list.addAll(map.keySet());
		
		Collections.sort(list); 
		//Collections.reverse(list); // 주석시 오름차순
		return list;
		}
}

~~~



~~~java

public class Phone {
	String name;
	String number;
	String address;

	public Phone(String name,String number,String address) {
		this.name=name;
		this.number=number;
		this.address=address;
	}
	
	public String getName() {return name;}
	public String getNumber() {return number;}
	public String getAddress() {return address;}	
}
~~~



# 해시맵 value 정렬하는 법

- hashmap은 정렬되지 않기 때문에 Arraylist를 통해 정렬함

1. Iterator<String> it = sortByValue(map).iterator();	

   - **Itorator 인터페이스를 통해 값 출력**
   - 출력하기전에 sortByValue 함수를  통해 해시맵을 정렬함

   ​

   //sortByValue 함수 내부

2. List<String> list = new ArrayList();	

   - **ArrayList 생성**

3. list.addAll(map.keySet());

   - **해시맵의 모든 value를 ArrayList에 저장**

4. Collections.sort(list); 

   - **list의 컬렉션 정렬**