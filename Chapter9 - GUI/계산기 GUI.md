### 계산기 GUI###



~~~java
import javax.swing.*;
import java.awt.*;

public class Calculator extends JFrame {	//JFrame 상속받아 사용
	public Calculator() {
		setTitle("Calculator");		//제목
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);	//x누르면 프로그램 종료
		
		Container c=getContentPane();	//컨테이너 생성
		c.setLayout(new BorderLayout());
		JTextField jt =new JTextField();
		c.add(jt,BorderLayout.NORTH);	//border의 위쪽
		
		JPanel jp = new JPanel();		//패널 jp생성
		jp.setLayout(new GridLayout(4,4,5,5));	//그리드4*4
		jp.add(new JButton("0"));
		jp.add(new JButton("1"));
		jp.add(new JButton("2"));
		jp.add(new JButton("+"));
		jp.add(new JButton("3"));
		jp.add(new JButton("4"));
		jp.add(new JButton("5"));
		jp.add(new JButton("-"));
		jp.add(new JButton("6"));
		jp.add(new JButton("7"));
		jp.add(new JButton("8"));
		jp.add(new JButton("*"));
		jp.add(new JButton("9"));
		jp.add(new JButton("c"));
		jp.add(new JButton("="));
		jp.add(new JButton("/"));
		
		c.add(jp,BorderLayout.CENTER);
		setSize(300,300);	//프레임 사이즈
		setVisible(true);	
	}
	
	public static void main(String[] args) {
		new Calculator();
	}
}
~~~



## 프로그램 설명

- AWT(Abstract Windowing Toolkit)고 Swing 패키지 사용
- 최상위 컨테이너로 JFrame을 상속받아서 사용
- 컴포넌트를 넣는 contentPane 레퍼런스 c
- c의 레이아웃을 border로 하고, North에 TextField를 add
- 패널 jp를 그리드로 생성하고 버튼을 생성하여 add함
- c에 jp를 cunter에 add함



![image](https://user-images.githubusercontent.com/45009100/69334921-0a474e00-0c9f-11ea-9732-acd03b954e20.png)

아직 event는 적용하지 않아서 버튼의 기능을 하지는 못함.