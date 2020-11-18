# Calculator
// second implementation and work in process
// creatation of more buttons and actions 
// not a pleasant UI and non function text box
//import action event for active listener
import java.awt.event.ActionEvent;
// import event for active listener
import java.awt.event.ActionListener;

import javax.swing.*;
// JFrame is a top-level window
public class ButtonCalculator extends JFrame implements ActionListener{
	// create a frame
	static JFrame f;
	// create a textfield
	static JTextField textField1;
	private JButton button0, button1, button2, button3, button4,
	button5, button6, button7, button8, button9, beq1, bplus,
	bsub, bdivide, bmult, beq, be;
	
	// create operand and operator containers
	private String s0, s1, s2;
	
	
	public ButtonCalculator() {
		JPanel panel1 = new JPanel();
		
		s0 =s1 = s2 = "";
		//create buttons
		button0 = new JButton("0");
		button1 = new JButton("1");
		button2 = new JButton("2");
		button3 = new JButton("3");
		button4 = new JButton("4");
		button5 = new JButton("5");
		button6 = new JButton("6");
		button7 = new JButton("7");
		button8 = new JButton("8");
		button9 = new JButton("9");
		// create equal button
		beq1 = new JButton ("=");
		// create operators
		bplus = new JButton("+");
		bsub = new JButton("-");
		bdivide = new JButton("/");
		bmult = new JButton("*");
		beq = new JButton("C");
		// create . button
		be = new JButton(".");
		//create textfield
		textField1 = new JTextField(20);
		
		//add action listener to buttons
		ListenForButton listenForButton = new ListenForButton();
		button0.addActionListener(listenForButton);
		button1.addActionListener(listenForButton);
		button2.addActionListener(listenForButton);
		button3.addActionListener(listenForButton);
		button4.addActionListener(listenForButton);
		button5.addActionListener(listenForButton);
		button6.addActionListener(listenForButton);
		button7.addActionListener(listenForButton);
		button8.addActionListener(listenForButton);
		button9.addActionListener(listenForButton);
		
		beq1.addActionListener(listenForButton);
		bplus.addActionListener(listenForButton);
		bsub.addActionListener(listenForButton);
		bdivide.addActionListener(listenForButton);
		bmult.addActionListener(listenForButton);
		beq.addActionListener(listenForButton);
		be.addActionListener(listenForButton);
		
	
		// add to JFrame
		panel1.add(button0);
		panel1.add(button1);
		panel1.add(button2);
		panel1.add(button3);
		panel1.add(button4);
		panel1.add(button5);
		panel1.add(button6);
		panel1.add(button7);
		panel1.add(button8);
		panel1.add(button9);
		panel1.add(beq1);
		panel1.add(bplus);
		panel1.add(bsub);
		panel1.add(bdivide);
		panel1.add(bmult);
		panel1.add(beq);
		panel1.add(be);
		panel1.add(textField1);
		
		this.add(panel1);
	}
	//ActiveListener is an interface that implements on a class
	// and makes a handler class that listens to the click event
	// in a particular button
	private class ListenForButton implements ActionListener{
		
		@Override
		public void actionPerformed(ActionEvent e) {
			
		}
		
	}
	public void actionPerformed(ActionEvent e) {
		
		String s = e.getActionCommand();
		
		//if the variable is a number
		if (((s.charAt(0) >= '0' && s.charAt(0) <= '9') || (s.charAt(0) == '.'))){
			// if operand is present then add to second num
			if( !s1.equals("")) {
				s2 = s2 + s;
			}
			else {
				s0 = s0 +s;
			}
			// set the value of text
			textField1.setText(s0 + s1 + s2);
		}
		else if(s.charAt(0) == 'C') {
			//clear one letter
			s0 = s1 = s2 = "";
			//set the value of text
			textField1.setText(s0 + s1 + s2);
		}
		else if (s.charAt(0) == '=') {
			
			double var;
			// store the value in 1rst
			if (s1.equals("+")) {
				var = (Double.parseDouble(s0) + Double.parseDouble(s2));
			}
			
			else if(s1.equals("-")) {
				var = (Double.parseDouble(s0)- Double.parseDouble(s2));
			}
			else if(s1.equals("/")) {
				var = (Double.parseDouble(s0) / Double.parseDouble(s2));
			}
			else {
				var = (Double.parseDouble(s0) * Double.parseDouble(s2));
			}
			
			// set the value of text
			textField1.setText(s0 + s1 + s2 + "=" + var);
			
			// convert it to string
			
			s0 = Double.toString(var);
			
			s1 = s2 = "";
		}
		else {
			// if there isn't an operand
			if (s1.equals("") || s2.equals("")) {
				s1 = s;
			}
			// else evaluate
			else {
				double var;
				// store the value in 1st
				if(s1.equals("+")) {
					var = (Double.parseDouble(s0)+ Double.parseDouble(s2));
				}
				else if (s1.equals("-")) {
					var = (Double.parseDouble(s0) - Double.parseDouble(s2));
				}
				else if(s1.equals("/")) {
					var = (Double.parseDouble(s0)/ Double.parseDouble(s2));
				}
				else {
					var = (Double.parseDouble(s0) * Double.parseDouble(s2));
				}
				
				// convert it to string
				s0 = Double.toString(var);
				// place the operator
				s1 = s;
				// make the operand blank
				s2 = "";
			}
			// set the value of text
			textField1.setText(s0 + s1 + s2);
		}
	}
}
import javax.swing.*;
public class Main {

	public static void main(String[] args) {
		
		// create a frame
		//create a object of class
		
		ButtonCalculator calc = new ButtonCalculator();
		// create a textfield
		
		
		calc.setSize(600,400);
		//set frame to visble
		calc.setVisible(true);
		// exit the application
		calc.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
	}

}
