# Java Journey, 17: Event Handlers.

Repository 17 is focused on Event Handlers in Java programming language. Event handling is a mechanism that allows the program to respond to user actions such as mouse clicks, keyboard input, etc. Java provides a rich set of classes and interfaces for event handling. This repository covers the basic concepts and techniques used in Java event handling, including event sources, event listeners, and event objects. By the end of this repository, you will have a solid understanding of how to create and use event handlers in Java.

## Understand the basics of event-driven programming and the concept of event handlers.

Event-driven programming is a programming paradigm where the flow of a program's execution is determined by events. An event is an occurrence that may trigger an action or response in the program. In Java, event handling involves creating an event listener that waits for an event to occur, and then responds to the event by executing code.

The following example demonstrates a simple event handler that listens for a button click event and displays a message dialog when the button is clicked:

```bash
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class EventHandlerExample extends JFrame implements ActionListener {

    private JButton button;

    public EventHandlerExample() {
        setTitle("Event Handler Example");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JPanel panel = new JPanel();
        button = new JButton("Click Me");
        button.addActionListener(this);
        panel.add(button);

        getContentPane().add(panel);
        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        JOptionPane.showMessageDialog(this, "Button Clicked!");
    }

    public static void main(String[] args) {
        EventHandlerExample example = new EventHandlerExample();
    }
}
```

In this example, we create a JFrame window with a JPanel containing a JButton. We add an ActionListener to the button using the addActionListener() method, passing in a reference to the current object (which implements the ActionListener interface).

When the button is clicked, the actionPerformed() method is called, which displays a message dialog using the JOptionPane class.

By understanding the basics of event-driven programming and event handlers, we can create dynamic and interactive user interfaces in Java Swing applications.

## Learn about the various types of events that can occur in Java Swing components.

Java Swing components generate various types of events in response to user actions or system events. These events can be categorized into three main types:

1- Action events: These events are generated when the user interacts with components such as buttons, menu items, or text fields. The ActionListener interface is used to handle action events.
Example:

Suppose we have a button named "submit" in our UI. We can add an ActionListener to this button as follows:

```bash
JButton submitButton = new JButton("Submit");
submitButton.addActionListener(new ActionListener() {
  public void actionPerformed(ActionEvent e) {
    // Code to handle the submit button action
  }
});
```

2- Component events: These events are generated when the state of a component changes, such as when it is resized, moved, or made visible or invisible. The ComponentListener interface is used to handle component events.
Example:

Suppose we have a panel named "myPanel" in our UI. We can add a ComponentListener to this panel as follows:

```bash
JPanel myPanel = new JPanel();
myPanel.addComponentListener(new ComponentListener() {
  public void componentResized(ComponentEvent e) {
    // Code to handle the panel being resized
  }
  public void componentMoved(ComponentEvent e) {
    // Code to handle the panel being moved
  }
  public void componentShown(ComponentEvent e) {
    // Code to handle the panel being shown
  }
  public void componentHidden(ComponentEvent e) {
    // Code to handle the panel being hidden
  }
});
```

3- Mouse events: These events are generated when the user interacts with components using the mouse, such as clicking or dragging. The MouseListener and MouseMotionListener interfaces are used to handle mouse events.
Example:

Suppose we have a label named "myLabel" in our UI. We can add a MouseListener and MouseMotionListener to this label as follows:

```bash
JLabel myLabel = new JLabel("My Label");
myLabel.addMouseListener(new MouseListener() {
  public void mouseClicked(MouseEvent e) {
    // Code to handle the label being clicked
  }
  public void mousePressed(MouseEvent e) {
    // Code to handle the mouse button being pressed
  }
  public void mouseReleased(MouseEvent e) {
    // Code to handle the mouse button being released
  }
  public void mouseEntered(MouseEvent e) {
    // Code to handle the mouse entering the label
  }
  public void mouseExited(MouseEvent e) {
    // Code to handle the mouse leaving the label
  }
});
myLabel.addMouseMotionListener(new MouseMotionListener() {
  public void mouseDragged(MouseEvent e) {
    // Code to handle the mouse being dragged over the label
  }
  public void mouseMoved(MouseEvent e) {
    // Code to handle the mouse being moved over the label
  }
});
```

In summary, understanding the various types of events that can occur in Java Swing components is essential for implementing effective event handlers. By using appropriate interfaces, we can handle events such as user interactions, component state changes, and mouse events to create responsive and interactive UIs.

## Familiarize yourself with the ActionListener interface and its implementation in handling button events.

In Java Swing, the ActionListener interface is used to handle button events. The ActionListener interface contains only one method, actionPerformed(), which is invoked when the button is clicked.

To implement the ActionListener interface, the following steps need to be followed:

1- Create an instance of the button and add it to a container.

2- Create an instance of the class that will handle the button events.

3- Register the class instance as a listener on the button by calling the addActionListener() method on the button object.

Here's an example of how to use ActionListener to handle button events:

```bash
import javax.swing.*;
import java.awt.event.*;

public class ButtonExample implements ActionListener {
    private JButton button;

    public ButtonExample() {
        JFrame frame = new JFrame("Button Example");
        button = new JButton("Click me!");
        button.addActionListener(this);
        frame.add(button);
        frame.setSize(300, 200);
        frame.setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == button) {
            JOptionPane.showMessageDialog(null, "Button clicked!");
        }
    }

    public static void main(String[] args) {
        new ButtonExample();
    }
}
```

In this example, we first create a JFrame object and a JButton object. We then register the ButtonExample class as an action listener on the button object by calling the addActionListener() method. When the button is clicked, the actionPerformed() method is called and displays a message dialog that says "Button clicked!".

By implementing the ActionListener interface, we can easily handle button events in Java Swing applications.

## Learn about mouse events, including MouseEvent and MouseListener interfaces.

Mouse events are a crucial part of any GUI application. Java Swing provides a rich set of classes and interfaces to handle mouse events. MouseEvent is an event that occurs when a mouse is clicked or moved. MouseListener is an interface that is used to handle mouse events.

To learn more about mouse events, let's consider an example where we have a JFrame containing a JButton. We will add a MouseListener to the JButton to handle mouse events.

```bash
import javax.swing.*;
import java.awt.event.*;

public class MouseEventHandler extends JFrame {
    private JButton button;

    public MouseEventHandler() {
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        button = new JButton("Click Me");
        button.addMouseListener(new MouseAdapter() {
            public void mouseClicked(MouseEvent e) {
                System.out.println("Button clicked.");
            }
        });

        add(button);
        setVisible(true);
    }

    public static void main(String[] args) {
        new MouseEventHandler();
    }
}
```

In the above example, we have created a class named MouseEventHandler that extends JFrame. We have created a JButton named button and added it to the JFrame. We have added a MouseListener to the button using the addMouseListener() method.

The MouseAdapter class is an abstract adapter class that implements the MouseListener interface. We have overridden the mouseClicked() method to handle the mouse clicked event. When the button is clicked, the mouseClicked() method is called, and the message "Button clicked." is printed to the console.

By implementing the MouseListener interface, we can handle various other mouse events like mouse pressed, mouse released, mouse entered, and mouse exited.

## Understand keyboard events and the KeyEvent interface for handling them.

In Java Swing, keyboard events refer to the events generated by keyboard input. These events are handled using the KeyEvent interface. The KeyEvent class contains information about the key that was pressed or released, as well as information about the state of the modifier keys (such as Shift or Control) at the time of the event.

To handle keyboard events in Java Swing, you need to implement the KeyEvent interface and override its methods. The most commonly used methods are keyPressed() and keyReleased(), which are called when a key is pressed or released, respectively.

Here's an example of how to handle keyboard events in Java Swing:

```bash
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import javax.swing.JFrame;
import javax.swing.JPanel;

public class KeyboardEventsExample extends JFrame implements KeyListener {

    private JPanel panel;

    public KeyboardEventsExample() {
        panel = new JPanel();
        add(panel);
        addKeyListener(this);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(300, 200);
        setVisible(true);
    }

    public void keyPressed(KeyEvent e) {
        int keyCode = e.getKeyCode();
        if (keyCode == KeyEvent.VK_ENTER) {
            System.out.println("Enter key pressed");
        }
    }

    public void keyReleased(KeyEvent e) {
        int keyCode = e.getKeyCode();
        if (keyCode == KeyEvent.VK_ENTER) {
            System.out.println("Enter key released");
        }
    }

    public void keyTyped(KeyEvent e) {
        // Not used in this example
    }

    public static void main(String[] args) {
        new KeyboardEventsExample();
    }
}
```

In this example, we create a JFrame and add a JPanel to it. We also add a KeyListener to the JFrame, which allows us to handle keyboard events. The keyPressed() and keyReleased() methods are called when the user presses or releases a key, respectively. In this example, we check if the Enter key was pressed or released and print a message to the console accordingly. The keyTyped() method is not used in this example, but it is another method that can be implemented to handle keyboard events.

## Learn about window events and the WindowListener interface for handling them.

In Java Swing, a window event occurs when a window is opened, closed, or minimized. The WindowListener interface is used to handle window events. This interface contains several methods that can be implemented to handle various window events. The methods are:

1- windowOpened(): This method is called when a window is opened.

2- windowClosing(): This method is called when a user attempts to close a window.

3- windowClosed(): This method is called after a window has been closed.

4- windowIconified(): This method is called when a window is minimized.

5- windowDeiconified(): This method is called when a window is restored from a minimized state.

6- windowActivated(): This method is called when a window is activated, meaning it is brought to the front of the screen.

7- windowDeactivated(): This method is called when a window is deactivated, meaning it is no longer the active window.

Here's an example of implementing the WindowListener interface:

```bash
import javax.swing.*;
import java.awt.event.*;

public class MyFrame extends JFrame implements WindowListener {

    public MyFrame() {
        // Set the frame properties
        this.setTitle("My Window");
        this.setSize(400, 300);
        
        // Add the window listener
        this.addWindowListener(this);
    }

    // Implement the methods of the WindowListener interface
    public void windowOpened(WindowEvent e) {
        System.out.println("Window opened.");
    }

    public void windowClosing(WindowEvent e) {
        System.out.println("Window closing.");
        System.exit(0);
    }

    public void windowClosed(WindowEvent e) {
        System.out.println("Window closed.");
    }

    public void windowIconified(WindowEvent e) {
        System.out.println("Window minimized.");
    }

    public void windowDeiconified(WindowEvent e) {
        System.out.println("Window restored.");
    }

    public void windowActivated(WindowEvent e) {
        System.out.println("Window activated.");
    }

    public void windowDeactivated(WindowEvent e) {
        System.out.println("Window deactivated.");
    }

    public static void main(String[] args) {
        MyFrame frame = new MyFrame();
        frame.setVisible(true);
    }
}
```

In this example, the MyFrame class extends JFrame and implements the WindowListener interface. The window listener is added to the frame using the addWindowListener() method. The various methods of the WindowListener interface are then implemented to handle the corresponding window events. When the window is opened, closed, minimized, restored, activated, or deactivated, the appropriate method is called and a message is printed to the console.
