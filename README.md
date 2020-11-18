# Calculator
// first implementation and work in process
//import action event for active listener
import java.awt.event.ActionEvent;
// import event for active listener
import java.awt.event.ActionListener;

import javax.swing.*;
// JFrame is a top-level window
public class ButtonCalculator extends JFrame{
	
	private JButton button1;
	private JButton button2;
	private JButton button3;
	private JButton button4;
	private JTextField textField1;
	
	private String op1 = "0";
	private String op2 = "0";
	private String operand = "0";
	
	public ButtonCalculator() {
		JPanel panel1 = new JPanel();
		
		//create buttons
		button1 = new JButton("+");
		button2 = new JButton("-");
		button3 = new JButton("*");
		button4 = new JButton("/");
		//create textfield
		textField1 = new JTextField(20);
		
		//add action listener to buttons
		ListenForButton listenForButton = new ListenForButton();
		button1.addActionListener(listenForButton);
		button2.addActionListener(listenForButton);
		button3.addActionListener(listenForButton);
		button4.addActionListener(listenForButton);
		
		// add to JFrame
		panel1.add(button1);
		panel1.add(button2);
		panel1.add(button3);
		panel1.add(button4);
		panel1.add(textField1);
		
		this.add(panel1);
	}
	//ActiveListener is an interface that implements on a class
	// and makes a handler class that listens to the click event
	// in a particular button
	private class ListenForButton implements ActionListener{
		
		@Override
		public void actionPerformed(ActionEvent e) {
			// if the source is button1 then do something
			if(e.getSource()==button1) {
				textField1.setText("This is from the button1");
			}
		}
		
	}
	public void actionPerformed(ActionEvent e) {
		
		double number1 = 0;
		double number2 = 0;
		try {
			number1 = Double.parseDouble(textField1.getText());
		}
		
	}
}
public class Main {

	public static void main(String[] args) {
		
		ButtonCalculator calc = new ButtonCalculator();
		calc.setTitle("Calculator");
		calc.setSize(600,400);
		//set frame to visble
		calc.setVisible(true);
		// exit the application
		calc.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
	}

}
