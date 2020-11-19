import java.awt.Color;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.*;


import javax.swing.*;

class CalcDeployment extends JFrame implements ActionListener{
//create a frame
	static JFrame frame1;

	//create a textfield
	static JTextField field1;
	// operands
	String s0, s1, s2;
	//default constructor
	CalcDeployment(){
		s0=s1=s2="";
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		frame1 = new JFrame();
		frame1.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		try {
			UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
		}
		catch (Exception e) {
			System.err.println(e.getMessage());
		}
		// create a frame
		//create a object of class
		
		CalcDeployment calc = new CalcDeployment();
		// create a textfield
		field1 = new JTextField();
		field1.setSize(180,20);
		//added borderlayout north
		frame1.add(field1,BorderLayout.NORTH);
		//frame1.add(field1);
		// non editable textfield
		field1.setEditable(false);
		//calc.setVisible(true);
		
		//calc.setSize(600,400);

		// exit the application
		
		
		
		//create buttons 
		JButton button0, button1, button2, button3, button4,
		button5, button6, button7, button8, button9, beq1, bplus,
		bsub, bdivide, bmult, beq, bce;
		
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
		bce = new JButton("AC");
		//create a pannel.
		JPanel panel1 = new JPanel();
		//add action listeners

		button0.addActionListener(calc);
		button1.addActionListener(calc);
		button2.addActionListener(calc);
		button3.addActionListener(calc);
		button4.addActionListener(calc);
		button5.addActionListener(calc);
		button6.addActionListener(calc);
		button7.addActionListener(calc);
		button8.addActionListener(calc);
		button9.addActionListener(calc);
		
		beq1.addActionListener(calc);
		bplus.addActionListener(calc);
		bsub.addActionListener(calc);
		bdivide.addActionListener(calc);
		bmult.addActionListener(calc);
		beq.addActionListener(calc);
		bce.addActionListener(calc);
		//add to panel
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
		panel1.add(bce);
		
		//setbackground color
		panel1.setBackground(Color.cyan);
		//add panel to frame
		//////added borderlayout.center
		frame1.add(panel1,BorderLayout.CENTER);
		frame1.setSize(200, 220);
		//pack frame to component preferred size
		//frame1.pack();
		//replaces show()
		//field1.setVisible(true);
		frame1.setVisible(true);

		
	}
	public void actionPerformed(ActionEvent e) {
		
		String s = e.getActionCommand();
		
		//if the variable is a number
		if (((s.charAt(0) >= '0' && s.charAt(0) <= '9') || (s.charAt(0) == '.'))){
			// if operand is present then add to second num

				if( !s1.equals("")) {
					//if s2 is longer than 8 ignore the other digits
					if(s2.length() > 8) {
					
					}
					else {
						s2 = s2 + s;
					}
				}
				else {
					// if s0 is longer than 8 ignore the other digits
					if(s0.length() > 8) {
						
					}
					else{
						s0 = s0 +s;
					}
				}
				// set the value of text
				field1.setText(s0 + s1 + s2);
			
		}
		else if(s.charAt(0) == 'C') {
			//clear one letter
			// if operand is present then add to second num

			if( !s2.equals("")) {
				s2 = "";
			}
			else {
				s0= s1= ""; 
			}
			//set the value of text
			field1.setText(s0 + s1 + s2);
		}
		else if(s.charAt(0) == 'A') {
			//clear all letters
			s0 = s1 = s2 = "";
			//set the value of txt
			field1.setText(s0 + s1 + s2);
		}
		else if (s.charAt(0) == '=') {
			
			double var;
			String var2; 
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
			var2 = Double.toString(var);
			if(var2.length() < 8 ) {
				// set the value of text
				field1.setText(s0 + s1 + s2 + "=" + var);
				// convert it to string
				s0 = Double.toString(var);
				s1= s2 = "";
			}
			else {
				field1.setText("ERR");
			}
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
			field1.setText(s0 + s1 + s2);
		}
	}

}
