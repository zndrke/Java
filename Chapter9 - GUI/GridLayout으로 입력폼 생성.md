### GridLayout으로 입력폼 생성###



~~~java
import javax.swing.*;
import java.awt.*;

public class GridLayoutEX extends JFrame{
	public GridLayoutEX() {
		setTitle("GridLayoutEX");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		GridLayout grid = new GridLayout(4,2);	//4*2 그리드
		grid.setVgap(5);	//간격
		
		Container c = getContentPane();
		c.setLayout(grid);
		c.add(new JLabel("이름"));
		c.add(new JTextField(""));
		c.add(new JLabel("학번"));
		c.add(new JTextField(""));
		c.add(new JLabel("학과"));
		c.add(new JTextField(""));
		c.add(new JLabel("과목"));
		c.add(new JTextField(""));
		
		setSize(300,300);
		setVisible(true);
	}
	
	public static void main(String[] args) {
		new GridLayoutEX();
	}
}
~~~



- contentPane 레퍼런스인 c에 GridLayout인 grid를 레이아웃으로 사용함
- 4*2 크기의 그리드에 순서대로 Label과 Textfield를 add함

![image](https://user-images.githubusercontent.com/45009100/69337556-809a7f00-0ca4-11ea-94a3-a89cad400ff4.png)