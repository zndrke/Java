### 텍스트 Field&Area###

~~~java
import javax.swing.*;
import java.awt.event.*;
import java.awt.*;

public class TextAreaEx extends JFrame {
	private JTextField tf = new JTextField(20);		//접근하기 위해 멤버로 생성
	private JTextArea ta = new JTextArea(7, 20);

	public TextAreaEx() {
		setTitle("텍스트영역 만들기 예제");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container c = getContentPane();
		c.setLayout(new FlowLayout());
		
		c.add(new JLabel("입력 후 <Enter> 키를 입력하세요"));
		c.add(tf);
		c.add(new JScrollPane(ta));

		tf.addActionListener(new ActionListener() {		//임의 클래스로 ActionListener 생성
			public void actionPerformed(ActionEvent e) {
				JTextField t = (JTextField)e.getSource();
				ta.append(t.getText() + "\n");	//TextField의 문자를 TextArea로 이동
				t.setText("");	//TextField Clear
			}
		});
		setSize(300,300);
		setVisible(true);
	}
	public static void main(String [] args) {
		new TextAreaEx();
	}
}
~~~



> 텍스트 필드에 입력한 정보를 텍스트 에어리어로 옮김
>
> 1. TextField와 TextArea를 멤버로 선언하여 접근하기 쉽게 함
> 2. 컨텐트팬에 Field와 Area를 add함
> 3. TextField에서 ActionListener를 add 하고 임의 클래스로 ActionListener 정의