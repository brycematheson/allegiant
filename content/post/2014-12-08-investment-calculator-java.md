+++
title = "Build a GUI Investment Calculator in Java"
date = "2014-12-08T18:50:20-07:00"
+++
I’m not a programmer. Some people just have that natural itch to want to go out and code all day long, but that isn’t me. I enjoy scripting and web development, but deep, low-level programming just simply isn’t my thing. So the fact that even *I* was able to create a simple GUI application should tell you how easy it is. The code below might look daunting at first, but we’ll walk through it piece by piece to hopefully clear things up. I’ll try to make it as easy as possible to understand, but you should have at least a *basic* understanding of programming to go through this.

Java makes creating applications really simple. I’ve dabbled with C++, but never stuck with it long enough to get into the Object Oriented pieces of it. Whenever learning a new programming language, it seems the first program you write is “Hello World.” The next program after that is a basic investment calculator, and so we’re going to continue that pattern.

When we’re finished, we’ll have a program that looks something like this:

<img src="/img/post_images/guicalculator.png" alt="GUI Investment Calculator" />

At the end of this post, I’ll show the complete code. If you have the Java JDK (a free download, <a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html" target="_blank">here</a>), you can easily import this code into a text editor, save it with a .java extension, and then compile it using the command line. Something this would work:

~~~java
javac SimpleGUIProgram.java
java SimpleGUIProgram
~~~

Personally, I use Eclipse. It’s a <a href="https://eclipse.org/downloads/packages/eclipse-ide-java-developers/keplersr1" target="_blank">free IDE that you can download</a>, if you’re not interested in using a text editor.

Let’s get started.

First, let’s import some libraries. Libraries are basically a repository of reusable code. Rather than having to rewrite code over and over, why don’t we write it once, store it in the Java API, and then import it into our program whenever we need it? Luckily, someone has already done that for us! The specifics of each of these libraries isn’t super important, but just know that these include the graphical components that we’ll need to build our program.

~~~java
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
~~~

Next, we’ll create the text fields and buttons that will be used in our program. Notice in the image above that we have four input fields (Investment Amount, Years, Annual Interest Rate, and Future Value) and two buttons (Compute and Reset). They’re pretty easy to define in Java.

You might wonder what <span class="smallcode">private</span> means. Whenever you create an object and set it to private, that means that it can only be accessed within that same class. We could change it to <span class="smallcode">public</span> or even <span class="smallcode">protected</span>, but for this example, we’ll leave it how it is. There are some benefits to leaving things private, such as avoiding data corruption and a few other things, but that’s outside the scope of this tutorial.

Then we need to tell Java what kind of object we’ll be creating. We’ll be using <span class="smallcode">JTextField</span>, which is just an input box, and <span class="smallcode">JButton</span>, which, obviously, is a button. And after that, we just need to name our object. For the sake of being descriptive, I usually like to prefix my object names with <span class="smallcode">jtf</span> or <span class="smallcode">jb</span> or similar, so I know what it is quickly by looking at it.

~~~java
private JTextField jtfInvestmentAmount;
private JTextField jtfAnnualInterestRate;
private JTextField jtfNumberOfYears;
private JTextField jtfFutureValue;
private JButton jbtCompute;
private JButton jbtReset;
~~~

Next, we’re going to define the properties for the frame (the program window). The <span class="smallcode">setTitle</span> property allows us to name the frame. You can see in the image above that the title of the window is “Loan Calculator” as we’ve defined here. You can name it whatever you’d like.

Next, we define the default close operation. This tells the computer what to do whenever the program is closed. We have the option to let the program to continue running, even when the box is closed. In this example, when the user hits the “x” in the corner of the window, we want our program to terminate, so we’ll use <span class="smallcode">setDefaultCloseOperation(Frame.EXIT_ON_CLOSE)</span>.

<span class="smallcode">setSize</span> defines the window width and height in pixels. Pretty self-explanatory.

<span class="smallcode">setLocationRelativeTo(null)</span> allows us to center the window right in the middle of the screen. In my opinion, that’s the easiest and most user friendly. You have the option to set that location in pixels, using x and y coordinates, but generally, I’ve found that the user expects the window to open in the center of the screen.

Last, we want to set the layout. Java uses things called “Layout Managers”, which basically defines how elements are laid out inside of the program window. There are three layout managers that are most commonly used: Border, Flow, and Grid. You can read up on those other two, as I’m not going to explain them, but in this program, we’re going to be using the grid layout manager. It allows us to define how many rows, and how many columns we want for our program. <span class="smallcode">GridLayout(5,2,5,5)</span> tells our program that we want to use the Grid Layout Manager, with five rows, two columns and then 5 pixels for spacing.

~~~java
setTitle("Loan Calculator");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
setSize(500,300);
setLocationRelativeTo(null);
setLayout(new GridLayout(5,2,5,5));
~~~

Now that we’ve defined our window, we need to create some text labels next to our input fields. Because it’s just text, we don’t use <span class="smallcode">private</span> or <span class="smallcode">public</span> on these objects. We use the following code to create a new label (JLabel) object. Again, when we name the object, it’s good practice to use a prefix so you can easily tell what type of object it is. I use <span class="smallcode">jl</span> as my prefix. Then, we create the string of text for what the JLabel will output.

If you notice, I’ve placed a preceding space in front of the text. I find that Java likes to push things right up against the frame, and it’s not very aesthetically pleasing. By adding a space, it allows us to push the text away from the left edge ever-so-slightly. You can add more spacing if you prefer.

~~~java
JLabel jlInvestmentAmount = new JLabel(" Investment Amount");
JLabel jlNumberOfYears = new JLabel(" Number of Years");
JLabel jlAnnualInterestRate = new JLabel(" Annual Interest Rate");
JLabel jlFutureValue = new JLabel(" Future Value");
~~~

Earlier, we defined our textfields and buttons, but we didn’t actually create them. We basically told the program, “Hey, I’m going to be making these soon. Just wanted to give you a heads up.” But now we create them.

In the last line of code, we write <span class="smallcode">jtfFutureValue.setEditable(false)</span>. I wanted the first three fields to be able to accept input from the user. But the last field (the Future Value field) is going to simply output our final answer. Rather than making the user confused by thinking they need to input something, I set the editing to <span class="smallcode">false</span>.

~~~java
jtfInvestmentAmount = new JTextField();
jtfNumberOfYears = new JTextField();
jtfAnnualInterestRate = new JTextField();
jtfFutureValue = new JTextField();
jbtCompute = new JButton("Compute");
jbtReset = new JButton("Reset");
jtfFutureValue.setEditable(false);
~~~

Now that we’ve defined and created everything, we should be good right? Not quite. If were to run the program right now, our program wouldn’t do anything. What happened to all the things we created, you might ask? We’ve created all the objects, but we haven’t told the program to add them to our frame (window). We can do this simply by typing <span class="smallcode">add</span> and then the name of the object.

~~~java
add (jlInvestmentAmount);
add (jtfInvestmentAmount);
add (jlNumberOfYears);
add (jtfNumberOfYears);
add (jlAnnualInterestRate);
add (jtfAnnualInterestRate);
add (jlFutureValue);
add (jtfFutureValue);
add (jbtCompute);
add (jbtReset);
~~~

Next, we need to tell the computer that we want it to do something once we click on a button. This code doesn’t do much else, besides call other methods (functions) that we’ll define in a bit.

~~~java
ListenerClass listener = new ListenerClass();
jbtCompute.addActionListener(listener);
jbtReset.addActionListener(listener);
~~~

Another very important piece: We need to set the window visibility to <span class="smallcode">true</span>. Otherwise, nothing will appearÂ when we run the program.

~~~java
setVisible(true);
~~~

Every program in Java requires a <span class="smallcode">main</span> method. All this code does is calls the class that we’ve already created. It doesn’t look like much, but our program won’t run at all if we don’t have this.

~~~java
public static void main(String[] args) {
new SimpleGUIProgram();
~~~

The following code does two important things: catches exceptions, and does all the math calculations for our program.

First, we need to assume that people are stupid. You would think that most people would be smart enough to input numbers into the fields of our program, but what happens if they entered a word instead of a number? Without a “try…catch”, the program would just crash, without any warning to our user. Instead, we can make things a little bit more user friendly and say, “Please enter numeric values” if they enter anything except numbers.

And second, the rest of this code takes the data entered by the user in the fields, does all of the calculations, and then formats it to look pretty. We pull the data from the fields, parse it into a number (either an Integer or a Double), and then convert the annual interest rate into a monthly interest rate. We could do that by dividing by 12, but I also combined the percentage into that calculation as well (1200 instead of 12) so that I don’t have to write another line of code to divide the percent by 100 as well.

~~~java
private void computeValue() {
try {
double annualInterestRate = Double.parseDouble(jtfAnnualInterestRate.getText());
double monthlyInterestRate = annualInterestRate / 1200.0;
int NumberOfYears = Integer.parseInt(jtfNumberOfYears.getText());
double investmentAmount = Double.parseDouble(jtfInvestmentAmount.getText());
double futureValue = investmentAmount * Math.pow(1.0 + monthlyInterestRate, NumberOfYears * 12);
jtfFutureValue.setText(String.format("%.2f", futureValue));
} catch (Exception e) {
JOptionPane.showMessageDialog(null, " Please enter numeric values.");
}
}
~~~

This code is very simple. Whenever a user clicks on the “Reset” button, it will call this method, and change whatever is input into the boxes into a blank string.

~~~java
private void resetForm() {
jtfInvestmentAmount.setText("");
jtfAnnualInterestRate.setText("");
jtfNumberOfYears.setText("");
jtfFutureValue.setText("");
}
~~~

And finally, this code is what links the buttons to the methods we created. We create a ListenerClass, which essentially says, “When I do this, do this.” So, “when I click on a button, call this method.”

~~~java
private class ListenerClass implements ActionListener {
public void actionPerformed(ActionEvent e) {
if (e.getSource() == jbtCompute) {
computeValue();
}
if (e.getSource() == jbtReset) {
resetForm();
}
~~~

And really, that’s it! Not to shabby for ~100 lines of code, eh? Here’s the entire code:

~~~java
/*************************
* Created by: Bryce Matheson
* Website: blog.mathesondigital.com
* Date: 12/7/2014
*
* Purpose: A simple GUI Investment Calculator
*
* Rights: Free to use for Personal Use
*************************/

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class SimpleGUIProgram extends JFrame {
    
    private JTextField jtfInvestmentAmount;
    private JTextField jtfAnnualInterestRate;
    private JTextField jtfNumberOfYears;
    private JTextField jtfFutureValue;
    private JButton jbtCompute;
    private JButton jbtReset;
    
    public SimpleGUIProgram() {
        
        setTitle("Loan Calculator");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(500,300);
        setLocationRelativeTo(null);
        setLayout(new GridLayout(5,2,5,5));
        
        JLabel jlInvestmentAmount = new JLabel(" Investment Amount");
        JLabel jlNumberOfYears = new JLabel(" Number of Years");
        JLabel jlAnnualInterestRate = new JLabel(" Annual Interest Rate");
        JLabel jlFutureValue = new JLabel(" Future Value");
        
        jtfInvestmentAmount = new JTextField();
        jtfNumberOfYears = new JTextField();
        jtfAnnualInterestRate = new JTextField();
        jtfFutureValue = new JTextField();
        jtfFutureValue.setEditable(false);
        
        jbtCompute = new JButton("Compute");
        jbtReset = new JButton("Reset");
        
        add (jlInvestmentAmount);
        add (jtfInvestmentAmount);
        add (jlNumberOfYears);
        add (jtfNumberOfYears);
        add (jlAnnualInterestRate);
        add (jtfAnnualInterestRate);
        add (jlFutureValue);
        add (jtfFutureValue);
        add (jbtCompute);
        add (jbtReset);
        
        ListenerClass listener = new ListenerClass();
        jbtCompute.addActionListener(listener);
        jbtReset.addActionListener(listener);
        
        setVisible(true);
    }
    
    public static void main(String[] args) {
        new SimpleGUIProgram();
    }

    private void computeValue() {
        try {
            double annualInterestRate = Double.parseDouble(jtfAnnualInterestRate.getText());
            double monthlyInterestRate = annualInterestRate / 1200.0;
            int NumberOfYears = Integer.parseInt(jtfNumberOfYears.getText());
            double investmentAmount = Double.parseDouble(jtfInvestmentAmount.getText());
            double futureValue = investmentAmount * Math.pow(1.0 + monthlyInterestRate, NumberOfYears * 12);
            jtfFutureValue.setText(String.format("%.2f", futureValue));
        } catch (Exception e) {
            JOptionPane.showMessageDialog(null, " Please enter numeric values.");
        }
    }
    
    private void resetForm() {
        jtfInvestmentAmount.setText("");
        jtfAnnualInterestRate.setText("");
        jtfNumberOfYears.setText("");
        jtfFutureValue.setText("");
    }
    
    private class ListenerClass implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            if (e.getSource() == jbtCompute) {
                computeValue();
            }
            if (e.getSource() == jbtReset) {
                resetForm();
            }
        }
    }
}
~~~