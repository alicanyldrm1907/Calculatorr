import javax.swing.*;
import javax.swing.border.Border;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Locale;
import java.util.Scanner;
import java.util.Stack;

public class Main implements ActionListener{
    double num1=0;
    double num2=0;
    double result=0;
    String operator;
    JFrame frame=new JFrame("Calculator");
    JPanel panel=new JPanel();
    JButton pointButton=new JButton(".");
    JButton button1 = new JButton("0");
    JButton button2 = new JButton("1");
    JButton button3 = new JButton("2");
    JButton button4 = new JButton("3");
    JButton button5 = new JButton("4");
    JButton button6 = new JButton("5");
    JButton button7 = new JButton("6");
    JButton button8 = new JButton("7");
    JButton button9 = new JButton("8");
    JButton button10 = new JButton("9");
    JButton [] numberButtons = new JButton []{button1,button2,button3,button4,button5,button6,button7,button8,button9,button10};
    JButton delButton=new JButton("Del");
    JButton ACButton=new JButton("AC");
    JButton plusButton=new JButton("+");
    JButton minusButton=new JButton("-");
    JButton timesButton=new JButton("x");
    JButton dividedButton = new JButton("/");
    JButton equalsButton = new JButton("=");
    JButton [] mathButtons = new JButton[]{plusButton,minusButton,timesButton,dividedButton};
    JTextField textField=new JTextField();

    Main () {

        textField.setBounds(150,55,250,40);
        textField.setFocusable(false);
        textField.setFont(new Font(null,Font.BOLD,30));

        panel.setBounds(150,100,250,250);
        panel.setLayout(new GridLayout(4,4,10,10));

        ACButton.setBounds(150,360,120,30);
        delButton.setBounds(280,360,120,30);
        button1.setFont(new Font(null,Font.BOLD,30));
        button2.setFont(new Font(null,Font.BOLD,30));
        button3.setFont(new Font(null,Font.BOLD,30));
        button4.setFont(new Font(null,Font.BOLD,30));
        button5.setFont(new Font(null,Font.BOLD,30));
        button6.setFont(new Font(null,Font.BOLD,30));
        button7.setFont(new Font(null,Font.BOLD,30));
        button8.setFont(new Font(null,Font.BOLD,30));
        button9.setFont(new Font(null,Font.BOLD,30));
        button10.setFont(new Font(null,Font.BOLD,30));
        plusButton.setFont(new Font(null,Font.BOLD,30));
        minusButton.setFont(new Font(null,Font.BOLD,30));
        timesButton.setFont(new Font(null,Font.BOLD,30));
        dividedButton.setFont(new Font(null,Font.BOLD,30));
        equalsButton.setFont(new Font(null,Font.BOLD,30));
        pointButton.setFont(new Font(null,Font.BOLD,30));

        for (int i=0;i<numberButtons.length;i++) {
            numberButtons[i].addActionListener(this);
        }

        ACButton.addActionListener(this);
        delButton.addActionListener(this);
        pointButton.addActionListener(this);

        for (int i = 0; i < mathButtons.length; i++) {
            mathButtons[i].addActionListener(this);
        }
        equalsButton.addActionListener(this);


        panel.add(button2);
        panel.add(button3);
        panel.add(button4);
        panel.add(plusButton);
        panel.add(button5);
        panel.add(button6);
        panel.add(button7);
        panel.add(minusButton);
        panel.add(button8);
        panel.add(button9);
        panel.add(button10);
        panel.add(timesButton);
        panel.add(pointButton);
        panel.add(button1);
        panel.add(equalsButton);
        panel.add(dividedButton);

        frame.add(panel);
        frame.add(textField);
        frame.add(ACButton);
        frame.add(delButton);

        frame.setSize(500,500);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        Main main=new Main();
    }
    @Override
    public void actionPerformed(ActionEvent e) {

        for (int i=0;i<10;i++) {
            if (e.getSource() == numberButtons[i]) {
                textField.setText(textField.getText().concat(String.valueOf(i)));
            }
        }
        if (e.getSource()==pointButton) {
            textField.setText(textField.getText().concat("."));
        }
        if (e.getSource()==ACButton) { // Yardım aldığım yer
            textField.setText("");
        }
        if (e.getSource()==plusButton) { // Yardım aldığım yer
            num1=Double.parseDouble(textField.getText());
            operator="+";
            textField.setText("");
        }
        if (e.getSource()==minusButton) {
            num1=Double.parseDouble(textField.getText());
            operator="-";
            textField.setText("");
        }
        if (e.getSource()==timesButton) {
            num1=Double.parseDouble(textField.getText());
            operator="x";
            textField.setText("");
        }
        if (e.getSource()==dividedButton) {
            num1=Double.parseDouble(textField.getText());
            operator="/";
            textField.setText("");
        }
        if (e.getSource()==delButton) { // Yardım aldığım yer
            String a=textField.getText();
            textField.setText("");
            for (int i=0;i<a.length()-1;i++) {
                textField.setText(textField.getText()+a.charAt(i));
            }
        }
        if (e.getSource()==equalsButton) {
            num2=Double.parseDouble(textField.getText());
            switch (operator) {
                case "+": result=num1+num2;
                break;
                case "-": result=num1-num2;
                break;
                case "x": result=num1*num2;
                break;
                case "/": result=num1/num2;
                break;
            }
            textField.setText(String.valueOf(result));
            num1=result;
        }
    }
}
