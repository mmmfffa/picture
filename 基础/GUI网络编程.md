[我的工作台 - Gitee.com](https://gitee.com/ma-fu/dashboard/projects)

# GUI简介

> 组件

窗口、弹窗、面板、文本框、列表框、按钮、图片、监听事件、鼠标、键盘事件、破解工具。。。

> GUI核心技术

Swing,AWT

1. 界面不美观
2. 需要jre环境

工作可能需要维护swing界面，概率极小；

了解MVC架构思想；

可以写一些想要的小工具。

AWT是底层，但是Swing是封装了的。



# AWT

## Awt介绍

1. 包含很多的类和接口。GUI：图形用户界面。
2. 元素：窗口，按钮，文本框。
3. java.awt

<img src="https://i.loli.net/2021/05/20/gLV4EivRrCBhwUZ.png" alt="mf1" style="zoom:50%;float:left" />

## 组件和容器

> window的Frame组件

```java
//GUI第一个界面程序
public class TestFrame {
    public static void main(String[] args) {
        //Frame学习：JDK,看源码！
        Frame frame = new Frame("第一个Java的GUI窗口");
        //需要设置可见性,窗口大小w，h，背景颜色
        frame.setVisible(true);
        frame.setSize(400,400);
        //new Color(r,g,b);
        frame.setBackground(Color.pink);
        //弹出的初始位置
        frame.setLocation(200,200);
        //设置大小固定
        frame.setResizable(false);
    }

}
```

封装：

```java
class MyFrame extends Frame {
    static int id=0;//存在多个窗口，需要计数
    public MyFrame(int x,int y,int w,int h,Color color) {
        super("myFrame+"+(++id));//继承并构造
        setBounds(x,y,w,h);
        setBackground(color);
        setVisible(true);
        setResizable(false);

    }
}
public class TestFrame02 {
    public static void main(String[] args) {
        //展示多个窗口 new  继承
        MyFrame myFrame1 = new MyFrame(100, 100, 200, 200, Color.GREEN);
        MyFrame myFrame2= new MyFrame(300, 100, 200, 200, Color.white);
        MyFrame myFrame3 = new MyFrame(100, 300, 200, 200, Color.yellow);
        MyFrame myFrame4 = new MyFrame(300, 300, 200, 200, Color.pink);

    }
}
```

<img src="https://i.loli.net/2021/05/20/eF9mqXwz7ObD5ZE.png" alt="QQ截图20210511091621" style="zoom:50%;float:left" />

问题：窗口无法关闭！



> 面板panel组件

```java
//panel可以看成一个空间，但是不能单独存在
public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame();
        Panel panel = new Panel();//布局的概念

        frame.setLayout(null);//设置布局
        frame.setBounds(300,300,500,500);
        frame.setBackground(Color.green);

        //panel设置坐标相对frame
        panel.setBounds(50,50,200,200);
        panel.setBackground(Color.white);

        frame.add(panel);
        frame.setVisible(true);
    }
}
```

<img src="https://i.loli.net/2021/05/20/OTzViGIBXFeRsAU.png" alt="QQ截图20210511093123" style="zoom:57%;float:left" />

关闭

```java
        //监听事件，监听窗口关闭事件  System.exit(0)
        //适配器模式
        frame.addWindowListener(new WindowAdapter() {
            //窗口点击关闭的时候需要做的事情
            @Override
            public void windowClosing(WindowEvent e) {
                //结束程序
                System.exit(0);
            }
        });
```



## 布局管理

- 流式布局

```java
public class TestFlowLayout {
    public static void main(String[] args) {
        Frame frame = new Frame();
        //组件-按钮
        Button button1 = new Button("button1");
        Button button2 = new Button("button2");
        Button button3 = new Button("button3");
        //设置流式布局
//        frame.setLayout(new FlowLayout());//居中
        frame.setLayout(new FlowLayout(FlowLayout.LEFT));
        frame.setSize(200,200);
        frame.add(button1);
        frame.add(button2);
        frame.add(button3);

        frame.setVisible(true);
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });

    }
}

```



- 东西南北中

<img src="https://i.loli.net/2021/05/20/ldowETpDu6nRhv2.png" alt="QQ截图20210511194712" style="zoom:50%;float:left" />

```java
        Frame frame = new Frame("TestBorderLayout");

        Button east = new Button("east");
        Button west = new Button("west");
        Button south = new Button("south");
        Button north = new Button("north");
        Button center = new Button("center");

        frame.add(east,BorderLayout.EAST);
        frame.add(west,BorderLayout.WEST);
        frame.add(south,BorderLayout.SOUTH);
        frame.add(north,BorderLayout.NORTH);
        frame.add(center,BorderLayout.CENTER);

        frame.setBounds(400,400,400,400);
        frame.setBackground(Color.red);
        frame.setVisible(true);
```



- 表格布局  Grid

```java
        Frame frame = new Frame("TestGridLayout");

        Button btn1 = new Button("btn1");
        Button btn2 = new Button("btn2");
        Button btn3 = new Button("btn3");
        Button btn4 = new Button("btn4");
        Button btn5 = new Button("btn5");
        Button btn6 = new Button("btn6");

        frame.setLayout(new GridLayout(3,2));
        frame.add(btn1);
        frame.add(btn2);
        frame.add(btn3);
        frame.add(btn4);
        frame.add(btn5);
        frame.add(btn6);

        frame.pack();//Java函数，自动选择最优布局
        frame.setVisible(true);
```



练习：

<img src="https://i.loli.net/2021/05/20/uT2dnQ3MD8eNrlt.png" alt="QQ截图20210511202810" style="zoom:67%;float:left" />

```java
        //总Frame窗
        Frame frame = new Frame();
        frame.setLayout(new GridLayout(2,1));
        frame.setBounds(400,400,700,700);
        frame.setBackground(Color.green);
        frame.setVisible(true);

        //4个面板
        Panel panel1 = new Panel(new BorderLayout());
        Panel panel2 = new Panel(new GridLayout(2, 1));
        Panel panel3 = new Panel(new BorderLayout());
        Panel panel4 = new Panel(new GridLayout(2, 2));

        panel1.add(new Button("west-1"),BorderLayout.WEST);
        panel1.add(new Button("east-1"),BorderLayout.EAST);
        panel2.add(new Button("grid-1"));
        panel2.add(new Button("grid-2"));
        panel1.add(panel2,BorderLayout.CENTER);

        panel3.add(new Button("west-2"),BorderLayout.WEST);
        panel3.add(new Button("east-2"),BorderLayout.EAST);
        for (int i = 0; i < 4; i++) {
            panel4.add(new Button("gridFor-"+i));
        }
        panel3.add(panel4,BorderLayout.CENTER);

        frame.add(panel1);
        frame.add(panel3);
```



## 事件监听

事件监听：当某个事情发生的时候，干什么？

```java
public class TestActionEvent {
    //关闭窗口事件
    public  static  void windowClose(Frame frame){
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
    public static void main(String[] args) {
        //按下按钮，触发一些事件
        Frame frame = new Frame();
        Button button = new Button();
        button.addActionListener(new MyActionListener());//因为需要ActionListener
        frame.setLayout(new FlowLayout());
        frame.add(button);
        frame.setBounds(400,400,500,500);
        frame.setBackground(Color.pink);

        windowClose(frame);
        frame.setVisible(true);

    }
}
class MyActionListener implements ActionListener{
    @Override
    public void actionPerformed(ActionEvent e) {
          System.out.println("aaa");
    }
}
```



```java
public class TestActionEvent02 {
    public static void main(String[] args) {
        //两个按钮实现同一个监听
        //开始，停止
        Frame frame = new Frame();
        Button start = new Button("start");
        Button stop = new Button("stop");
        stop.setActionCommand("stop-btn");//可以显示定义触发返回命令
        //可以只写一个button事件监听按钮
        MyMonitor myMonitor = new MyMonitor();
        start.addActionListener(myMonitor);
        stop.addActionListener(myMonitor);
        frame.add(start,BorderLayout.WEST);
        frame.add(stop,BorderLayout.EAST);
        frame.pack();
        frame.setVisible(true);


    }
}
class  MyMonitor implements ActionListener{

    @Override
    public void actionPerformed(ActionEvent e) {
        //e.getActionCommand()获得按钮的信息
          System.out.println("按钮被点击了=>"+e.getActionCommand());
    }
}
```



## 输入框TextField监听

```java
public class TextFieldListen {
    public static void main(String[] args) {
        //启动！
        new MyFrame();
    }
}
class MyFrame extends Frame{
    public MyFrame(){
        TextField textField = new TextField();
        add(textField);
        //监听这个文本框输入的文字
        //按下回车就会触发这个输入框的事件
        textField.addActionListener(new ActionListener2());
        pack();
        //设置替换编码
        textField.setEchoChar('*');
        setVisible(true);
    }
}
class ActionListener2 implements ActionListener{

    @Override
    public void actionPerformed(ActionEvent e) {
        TextField textField=(TextField)e.getSource();//获得一些资源
        System.out.println(textField.getText());//获得输入框中文本
        textField.setText("");//再次回车清空内容
    }
}

```



## 简易计算器

```java
public class Calculator {
    public static void main(String[] args) {
        new Calc();
    }
}
class Calc extends Frame{
    public Calc(){
        //3个文本框
        TextField num1 = new TextField(10);
        TextField num2 = new TextField(10);
        TextField num3 = new TextField(20);

        //1个按钮
        Button button = new Button("=");
        button.addActionListener(new MyCalcListener(num1,num2,num3));
        //1个标签
        Label label = new Label("+");

        setLayout(new FlowLayout());
        add(num1);
        add(label);
        add(num2);
        add(button);
        add(num3);
        pack();
        setVisible(true);
    }
}
class MyCalcListener implements ActionListener{
    //获取3个变量
    private TextField num1;
    private TextField num2;
    private TextField num3;

    public MyCalcListener(TextField num1, TextField num2, TextField num3) {
         this.num1=num1;
         this.num2=num2;
         this.num3=num3;
    }

    @Override
    public void actionPerformed(ActionEvent e) {
     //做加法
        //或的加数和被加数
        int n1=Integer.parseInt(num1.getText());
        int n2=Integer.parseInt(num2.getText());

        //将这个值+法运算，放到第三个框
        num3.setText(""+(n1+n2));
        //清除前两个框
        num1.setText("");
        num2.setText("");
    }
}
```

优化：运用组合

```java
public class Calculator {
    public static void main(String[] args) {
        new Calc().loadFrame();
    }
}
class Calc extends Frame{
    //属性
    TextField num1;
    TextField num2;
    TextField num3;
    //方法
    public void loadFrame(){
        //3个文本框
        num1 = new TextField(10);
        num2 = new TextField(10);
        num3 = new TextField(20);

        //1个按钮
        Button button = new Button("=");
        button.addActionListener(new MyCalcListener(this));
        //1个标签
        Label label = new Label("+");

        //布局
        setLayout(new FlowLayout());
        add(num1);
        add(label);
        add(num2);
        add(button);
        add(num3);
        pack();
        setVisible(true);
    }
}
class MyCalcListener implements ActionListener{
    //获取计算器这个对象
    Calc calc;
    public MyCalcListener(Calc calc) {
        this.calc=calc;
    }

    @Override
    public void actionPerformed(ActionEvent e) {
     //做加法
        //或的加数和被加数
        int n1=Integer.parseInt(calc.num1.getText());
        int n2=Integer.parseInt(calc.num2.getText());

        //将这个值+法运算，放到第三个框
        calc.num3.setText(""+(n1+n2));
        //清除前两个框
        calc.num1.setText("");
        calc.num2.setText("");
    }
}
```

完全改造为面向对象写法：内部类更好包装

```java
//简易计算器
public class Calculator {
    public static void main(String[] args) {
        new Calc().loadFrame();
    }
}
class Calc extends Frame{
    //属性
    TextField num1;
    TextField num2;
    TextField num3;
    //方法
    public void loadFrame(){
        //3个文本框
        num1 = new TextField(10);
        num2 = new TextField(10);
        num3 = new TextField(20);

        //1个按钮
        Button button = new Button("=");
        button.addActionListener(new MyCalcListener());
        //1个标签
        Label label = new Label("+");

        //布局
        setLayout(new FlowLayout());
        add(num1);
        add(label);
        add(num2);
        add(button);
        add(num3);
        pack();
        setVisible(true);
    }

    //监听器类
     private class MyCalcListener implements ActionListener{
        @Override
        public void actionPerformed(ActionEvent e) {
            //做加法
            //或的加数和被加数
            int n1=Integer.parseInt(num1.getText());
            int n2=Integer.parseInt(num2.getText());

            //将这个值+法运算，放到第三个框
            num3.setText(""+(n1+n2));
            //清除前两个框
            num1.setText("");
            num2.setText("");
        }
    }
}
```

内部类的最大好处就是畅通无阻使用外部类，进一步优化！

## 画笔paint

```java
public class TestPaint {
    public static void main(String[] args) {
       new MyPaint().loadFrame();
    }
}
class MyPaint extends Frame{

    public void loadFrame(){
        setBounds(400,400,800,800);
        setVisible(true);
        new windowsClose().close(this);
    }

    @Override
    public void paint(Graphics g) {
         //画笔需要有颜色
        g.setColor(Color.RED);
//        g.drawOval(100,100,200,200);
        g.fillOval(100,100,200,200);//实心

        g.setColor(Color.green);
        g.fillRect(200,300,400,200);
    }
}
```



## 鼠标监听

画板和画笔是绑定的。。

目的：想要实现鼠标画画(仅仅实现点)

<img src="https://i.loli.net/2021/05/20/jZR5uOpbyHsJUer.png" alt="QQ截图20210512100300" style="zoom:70%;float:left" />



```java
public class TestMouseListener {
    public static void main(String[] args) {
        new MyFrame("画图");
    }

}
class MyFrame extends Frame{
    //画画需要画笔，需要监听鼠标当前的位置，需要集合来存储点
    ArrayList points;
    public MyFrame(String title) {
        super(title);
        setBounds(300,300,700,700);
        //存在鼠标点击的点
        points=new ArrayList<>();
        addMouseListener(new MyMouseListener());

        setVisible(true);
        new windowsClose().close(this);
    }
    //画画需要画笔

    @Override
    public void paint(Graphics g) {
        //画画，监听鼠标监听器
        Iterator iterator = points.iterator();
        while (iterator.hasNext()){
            Point point = (Point) iterator.next();
            g.setColor(Color.green);
            g.fillOval(point.x,point.y,10,10);
        }
    }
    //添加一个点到界面上
    public void  addPaint(Point point){
         points.add(point);
    }

    //不使用MouseLister需要重写接口所有方法，采用适配器模式实现
    static class MyMouseListener extends MouseAdapter{
        //鼠标，按下，弹起，按住不放

        @Override
        public void mousePressed(MouseEvent e) {
           MyFrame myFrame =(MyFrame) e.getSource();//拿到这个窗口
            //这里点击的时候，就会在界面上产生一个点!画笔
            myFrame.addPaint(new Point(e.getX(),e.getY()));

            //每次点击鼠标都需要重新画一遍
            myFrame.repaint();//只要点击鼠标都会刷新一遍
        }
    }
}
```



## 窗口监听

```java
public class TestWindow {
    public static void main(String[] args) {
         new WindFrame();
    }
}
class WindFrame extends Frame{
    public WindFrame(){
        setBounds(200,200,400,400);
        setBackground(Color.blue);
        setVisible(true);
        addWindowListener(new MyWindowListener());

    }
    class MyWindowListener extends WindowAdapter {
        @Override
        public void windowClosing(WindowEvent e) {
            setVisible(false);//设置监听器，通过按钮，隐藏
           // System.exit(0);//正常退出
        }
    }
}
```

优化:使用匿名内部类

```java
public class TestWindow {
    public static void main(String[] args) {
         new WindFrame();
    }
}
class WindFrame extends Frame{
    public WindFrame(){
        setBounds(200,200,400,400);
        setBackground(Color.blue);
        setVisible(true);
        addWindowListener(
                //匿名内部类
                new WindowAdapter() {
                    @Override
                    public void windowClosing(WindowEvent e) {
                        System.exit(0);
                    }
                }
        );

    }
}
```



常用窗口监听事件；

```java
    //关闭窗口
    @Override
    public void windowClosing(WindowEvent e) {
        System.out.println("windowClosing");
        System.exit(0);
    }
    //激活窗口
    @Override
    public void windowActivated(WindowEvent e) {
        WindFrame windFrame =(WindFrame) e.getSource();
        windFrame.setTitle("窗口被激活了");
        System.out.println("windowActivated");
    }
```





## 键盘监听

```java
//键盘监听
public class TestKeyListener {
    public static void main(String[] args) {
         new KeyFrame();
    }
}
class KeyFrame extends Frame{
    public KeyFrame() {
        setBounds(200,200,400,400);
        setBackground(Color.pink);
        setVisible(true);

        //监听键盘事件
        addKeyListener(new KeyAdapter() {
            //键盘按下
            @Override
            public void keyPressed(KeyEvent e) {
                //键盘按下的键是哪一个,键盘的码
                int keyCode = e.getKeyCode();
                System.out.println(keyCode);
                if(keyCode==KeyEvent.VK_UP){
                    System.out.println("按下了up键");
                }
               //根据按下不同的键，不同操作产生不同结果
            }
        });

        addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```



# Swing

## 窗口JFrame

和AWT窗口一样，不过是换了个名字而已JFrame

```java
public class TestJFrame {
    //init();初始化一个方法
    public void init(){
        //顶级窗口
        JFrame jFrame = new JFrame("JFrame窗口");
        jFrame.setVisible(true);
        jFrame.setBounds(200,200,700,500);
        //jFrame.setBackground(Color.GREEN);
        //设置文字jLabel
        JLabel jLabel = new JLabel("欢迎学习JLabel!");
        jFrame.add(jLabel);
        //文字居中
        jLabel.setHorizontalAlignment(SwingConstants.CENTER);

        //容器实例化
        Container contentPane = jFrame.getContentPane();
        contentPane.setBackground(Color.GREEN);

        //JFrame默认实现了关闭窗口事件
        jFrame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

    }
    public static void main(String[] args) {
        //建立一个窗口
        new  TestJFrame().init();
    }
}
```

## 弹窗Dialog

```java
public class TestDialog extends JFrame {
    public TestDialog() {
        setVisible(true);
        setBounds(200,200,600,400);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        //JFrame容器，放东西
        Container contentPane = this.getContentPane();
        contentPane.setBackground(new Color(43, 234, 234));
        //绝对布局
        contentPane.setLayout(null);
        JButton button = new JButton("点击弹出一个对话框");
        button.setBounds(50,50,200,50);

        //点击这个按钮的时候弹出一个弹窗
        button.addActionListener(new ActionListener() {//监听器
            @Override
            public void actionPerformed(ActionEvent e) {
                //弹窗
                new MyDialog();
            }
        });

        contentPane.add(button);

    }

    public static void main(String[] args) {
       new TestDialog();
    }
}
//弹窗的窗口
class MyDialog extends JDialog{
    public MyDialog() {
        setVisible(true);
        setBounds(500,500,400,300);
      // 弹窗默认是可以关闭的 setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        Container contentPane = this.getContentPane();
        contentPane.setLayout(null);
        contentPane.add(new JLabel("欢迎学习Dialog!"));

    }
}
```



## 图标Icon

> ICON，ImageICON标签



```java
new JLabel("xxxx");
```

图标ICON

```java
//图标是一个接口，需要实现类，Frame继承
public class TestIcon extends JFrame implements Icon {
    private int width;
    private int height;

    public TestIcon() {
    }

    public TestIcon(int width, int height){
        this.width = width;
        this.height = height;
    }

    public void init(){


        this.setBounds(200,200,400,300);

        TestIcon testIcon = new TestIcon(80, 80);
        //图标可以放在标签上也可以放在按钮上
        JLabel jLabel = new JLabel("testIcon", testIcon, SwingConstants.CENTER);

        Container contentPane = this.getContentPane();
        contentPane.add(jLabel);
        contentPane.setBackground(Color.blue);

        this.setVisible(true);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

    }

    public static void main(String[] args) {
        new TestIcon().init();
    }

    @Override
    public void paintIcon(Component c, Graphics g, int x, int y) {
          g.setColor(Color.red);
          g.fillOval(x,y,width,height);
    }

    @Override
    public int getIconWidth() {
        return this.width;
    }

    @Override
    public int getIconHeight() {
        return this.height;
    }
}
```



> image标签



> 问题图片资源被过滤问题

重新rebuild一次即可解决

```java
        URL url= TestImageIcon.class.getResource("3.jpeg");
        ImageIcon imageIcon = new ImageIcon(url);
```



```java
public class TestImageIcon extends JFrame {
    public TestImageIcon(){
        //获取图片的地址：最快的方式是通过类的所在路径获取
        JLabel jLabel = new JLabel("ImageIcon");
        URL url= TestImageIcon.class.getResource("3.jpeg");
        ImageIcon imageIcon = new ImageIcon(url);
        jLabel.setIcon(imageIcon);
        jLabel.setHorizontalAlignment(SwingConstants.CENTER);

        Container contentPane = getContentPane();
        contentPane.add(jLabel);

        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

    }

    public static void main(String[] args) {
       new TestImageIcon();
    }
}
```



## 面板JPanel

```java
public class TestJPlane extends JFrame {

    public TestJPlane() {
        Container contentPane = getContentPane();
        contentPane.setLayout(new GridLayout(2,1,10,10));//最后两个参数表示上下间距

        JPanel jPanel1 = new JPanel(new GridLayout(1,3));
        JPanel jPanel2 = new JPanel(new GridLayout(1,2));
        JPanel jPanel3 = new JPanel(new GridLayout(2,1));
        JPanel jPanel4 = new JPanel(new GridLayout(3,2));

        jPanel1.add(new JButton("1-1"));
        jPanel1.add(new JButton("1-2"));
        jPanel1.add(new JButton("1-3"));

        jPanel2.add(new JButton("2-1"));
        jPanel2.add(new JButton("2-2"));

        jPanel3.add(new JButton("3-1"));
        jPanel3.add(new JButton("3-2"));

        jPanel4.add(new JButton("4-1"));
        jPanel4.add(new JButton("4-2"));
        jPanel4.add(new JButton("4-3"));
        jPanel4.add(new JButton("4-4"));
        jPanel4.add(new JButton("4-5"));
        jPanel4.add(new JButton("4-6"));



        contentPane.add(jPanel1);
        contentPane.add(jPanel2);
        contentPane.add(jPanel3);
        contentPane.add(jPanel4);

        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

    }

    public static void main(String[] args) {
        new TestJPlane();
    }
}

```



## 滚动条JScrollPanel

```java
public class TestScrollPanel extends JFrame {
    public TestScrollPanel(){
        Container contentPane = getContentPane();

        //文本域
        JTextArea jTextArea = new JTextArea(20,50);
        jTextArea.setText("欢迎学习文本域");
        //应该放到ScrollPanel面板中
        ScrollPane scrollPane = new ScrollPane();
        scrollPane.add(jTextArea);
        contentPane.add(scrollPane);

        setBounds(200,200,700,500);
        setVisible(true);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
       new TestScrollPanel();
    }
}
```



## 按钮

- 图按钮

```java
public class TestButton extends JFrame {
    public TestButton(){
        Container contentPane = getContentPane();
        contentPane.setLayout(new BorderLayout());
        URL resource = TestButton.class.getResource("3.jpeg");
        ImageIcon imageIcon = new ImageIcon(resource);

        //将图标放在按钮上
        JButton button = new JButton();
        button.setIcon(imageIcon);
        button.setToolTipText("皮卡丘");//提示文本

        JPanel jPanel = new JPanel();
        jPanel.add(button);
        contentPane.add(jPanel,BorderLayout.CENTER);
        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

    }

    public static void main(String[] args) {
        new TestButton();
    }
}
```



- 单选框

```java
public class TestRadio extends JFrame {
    public TestRadio() {
        Container contentPane = getContentPane();

        //单选框只能选一个，分组,一个组中只能选择一个
        JRadioButton jRadioButton1 = new JRadioButton("JRadio01");
        JRadioButton jRadioButton2 = new JRadioButton("JRadio02");
        JRadioButton jRadioButton3 = new JRadioButton("JRadio03");
        ButtonGroup buttonGroup = new ButtonGroup();
        buttonGroup.add(jRadioButton1);
        buttonGroup.add(jRadioButton2);
        buttonGroup.add(jRadioButton3);

        contentPane.add(jRadioButton1,BorderLayout.NORTH);
        contentPane.add(jRadioButton2,BorderLayout.CENTER);
        contentPane.add(jRadioButton3,BorderLayout.SOUTH);

        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new TestRadio();
    }
}
```



- 多选框

```java
public class TestCheckBox extends JFrame {
    public TestCheckBox(){
        Container contentPane = getContentPane();

        JCheckBox jCheckBox01 = new JCheckBox("JCheckBox01");
        JCheckBox jCheckBox02 = new JCheckBox("JCheckBox02");
        contentPane.add(jCheckBox01,BorderLayout.NORTH);
        contentPane.add(jCheckBox02,BorderLayout.SOUTH);

        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new TestCheckBox();
    }
}
```



## 列表

- 下拉框

```java
public class TestComboBox extends JFrame {
    public TestComboBox(){
        Container contentPane = getContentPane();

        JComboBox<Object> jComboBox = new JComboBox<>();
        jComboBox.addItem(null);
        jComboBox.addItem("热映电影");
        jComboBox.addItem("你的婚礼");
        jComboBox.addItem("秘密访客");

        contentPane.add(jComboBox);
        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new TestComboBox();
    }
}

```



- 列表框

```java
public class TestJList extends JFrame {
    public TestJList() {
        Container contentPane = getContentPane();

        String[] contents={"热映电影","你的婚礼","秘密访客"};
        //可以用其他集合动态放入删减
        JList<Object> jList= new JList<>(contents);
        contentPane.add(jList);


        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new TestJList();
    }
}
```



## 文本框

- 文本框

```java
public class TestText extends JFrame {
    public TestText() {
        Container contentPane = getContentPane();
        JTextField jTextField1 = new JTextField("Hello");
        JTextField jTextField2 = new JTextField("文本框",20);

        contentPane.add(jTextField1,BorderLayout.NORTH);
        contentPane.add(jTextField2,BorderLayout.SOUTH);
        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
       new TestText();
    }
}
```

- 密码框

```java
public class TestText extends JFrame {
    public TestText() {
        Container contentPane = getContentPane();
        
        JPasswordField jPasswordField1 = new JPasswordField("Hello");
        JPasswordField jPasswordField2 = new JPasswordField("文本框", 20);
        //可以设置隐藏样式
        jPasswordField1.setEchoChar('*');
        contentPane.add(jPasswordField1,BorderLayout.NORTH);
        contentPane.add(jPasswordField2,BorderLayout.SOUTH);
        setVisible(true);
        setBounds(200,200,400,300);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

    }

    public static void main(String[] args) {
       new TestText();
    }
}
```

- 文本域

配合滚动面板使用

```java
public class TestScrollPanel extends JFrame {
    public TestScrollPanel(){
        Container contentPane = getContentPane();

        //文本域
        JTextArea jTextArea = new JTextArea(20,50);
        jTextArea.setText("欢迎学习文本域");
        //应该放到ScrollPanel面板中
        ScrollPane scrollPane = new ScrollPane();
        scrollPane.add(jTextArea);
        contentPane.add(scrollPane);

        setBounds(200,200,700,500);
        setVisible(true);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
       new TestScrollPanel();
    }
}
```

# 贪吃蛇之界面绘制

帧：如果时间片足够小就是动画，一秒30帧，60帧拆开就是静态图片。

键盘监听；

定时器Timer。

---

1. 定义数据

2. 画上去

3. 监听事件

     键盘

     事件



StartGame.java

```java
package com.mf.Snake;

import javax.swing.*;
import java.awt.*;

/**
 * @author mf
 * @create 2021-05-12-20:19
 */
//游戏的主启动类
public class StartGame extends JFrame {

    public StartGame() {
        Container contentPane = getContentPane();

        setBounds(400,200,900,720);
        setResizable(false);
        setVisible(true);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        //正常的游戏界面都应该在面板上
        this.add(new GamePanel());

    }

    public static void main(String[] args) {
        new StartGame();
    }
}

```



GamePanel.java

```java
package com.mf.Snake;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.util.Random;

/**
 * @author mf
 * @create 2021-05-12-20:25
 */
public class GamePanel extends JPanel implements KeyListener, ActionListener {
    //定义蛇的数据结构
    int length;
    int[] snakeX=new int[600];
    int[] snakeY=new int[600];
    String direct="right";
    //游戏当前的状态：开始，停止
    boolean isStart=false;
    //定时器
    Timer timer=new Timer(100,this);//100ms执行一次,监听this对象
    //食物坐标
    int foodX;
    int foodY;
    Random random=new Random();

    //失败
    boolean isFail=false;
    //积分
    int score;

    public GamePanel() {
        init();
        //获得焦点赫尔键盘事件
        this.setFocusable(true);
        //获取键盘事件
        this.addKeyListener(this);
        timer.start();//游戏一开始定时器就启动

        //食物随机分布
        foodX=25+25*random.nextInt(34);
        foodY=75+25*random.nextInt(24);
    }

    public void  init(){
        length=3;
        snakeX[0]=100;snakeY[0]=100;
        snakeX[1]=75;snakeY[1]=100;
        snakeX[2]=50;snakeY[2]=100;
        score=0;
    }


    //绘制面板
    @Override
    protected void paintComponent(Graphics g) {
       //清屏
       super.paintComponent(g);
       //绘制静态面板
        Data.header.paintIcon(this,g,25,11); //头部栏
        g.setColor(new Color(246, 248, 222, 255));
        g.fillRect(25,75,850,600);//默认游戏界面
        g.setColor(Color.black);

        g.setColor(new Color(238, 162, 31, 255));
        //设置字体
        g.setFont(new Font("微软雅黑",Font.BOLD,25));
        g.drawString("长度"+length,750,25);
        g.drawString("分数"+score,750,50);

        //画食物
        Data.food.paintIcon(this,g,foodX,foodY);

        //把小蛇画上去
        if(direct.equals("right")) Data.right.paintIcon(this,g,snakeX[0],snakeY[0]);
        else if(direct.equals("left")) Data.left.paintIcon(this,g,snakeX[0],snakeY[0]);
        else if(direct.equals("up")) Data.up.paintIcon(this,g,snakeX[0],snakeY[0]);
        else if(direct.equals("down")) Data.down.paintIcon(this,g,snakeX[0],snakeY[0]);


        for (int i = 1; i < length; i++) {
            Data.body.paintIcon(this,g,snakeX[i],snakeY[i]);
        }



        //游戏状态
        if(!isStart){
            g.setColor(Color.pink);
            //设置字体
            g.setFont(new Font("微软雅黑",Font.BOLD,40));
            g.drawString("按下空格开始游戏",300,300);
        }

        if(isFail){
            g.setColor(Color.pink);
            //设置字体
            g.setFont(new Font("微软雅黑",Font.BOLD,40));
            g.drawString("游戏失败,按下空格重新开始",300,300);
        }
    }



    @Override
    public void keyPressed(KeyEvent e) {
        int keyCode = e.getKeyCode();
        if(keyCode==KeyEvent.VK_SPACE){
            //空格有两个作用，暂停和重新开始
            if(isFail){
                isFail=false;
                init();
            }else {
                isStart=!isStart;
            }
            repaint();
        }
        //小蛇移动
        if(direct.equals("down")&&keyCode==KeyEvent.VK_UP) direct="down";
        else if(direct.equals("up")&&keyCode==KeyEvent.VK_DOWN) direct="up";
        else if(direct.equals("left")&&keyCode==KeyEvent.VK_RIGHT) direct="right";
        else if(direct.equals("right")&&keyCode==KeyEvent.VK_LEFT) direct="left";
        else if(keyCode==KeyEvent.VK_UP){
            direct="up";
        }else if(keyCode==KeyEvent.VK_DOWN){
            direct="down";
        }else if(keyCode==KeyEvent.VK_LEFT){
            direct="left";
        }else if(keyCode==KeyEvent.VK_RIGHT){
            direct="right";
        }
    }

    @Override
    public void keyReleased(KeyEvent e) {}
    @Override
    public void keyTyped(KeyEvent e) {}

    //事件监听，来一个定时器，需要通过固定事件来刷新，1=10次
    @Override
    public void actionPerformed(ActionEvent e) {
        //如果游戏是开始状态,就让小蛇动起来
        if(isStart&&!isFail){
            //判断吃食物
            if(snakeX[0]==foodX&&snakeY[0]==foodY){
                length++;
                score+=10;
                if(score<150)
                  timer.setDelay(150-score);

                foodX=25+25*random.nextInt(34);
                foodY=75+25*random.nextInt(24);
            }

           //右移
            //移动
            for (int i = length-1; i >0; i--) {//向前移动一节
                snakeX[i]=snakeX[i-1];
                snakeY[i]=snakeY[i-1];

            }
            //走向
            if(direct.equals("right")){
                snakeX[0]+=25;
                //边界判断
                if(snakeX[0]>850) snakeX[0]=25;
            }else if(direct.equals("left")){
                snakeX[0]-=25;
                //边界判断
                if(snakeX[0]<25) snakeX[0]=850;
            }else if(direct.equals("down")){
                snakeY[0]+=25;
                //边界判断
                if(snakeY[0]>650) snakeY[0]=75;
            }else if(direct.equals("up")){
                snakeY[0]-=25;
                //边界判断
                if(snakeY[0]<75) snakeY[0]=650;
            }

            //失败判断，撞到自己就算失败
            for(int i=1;i<length;i++){
                if(snakeX[0]==snakeX[i]&&snakeY[0]==snakeY[i])
                      isFail=true;
            }

            repaint();//遍历完需要重画一下
        }
        timer.start();
    }
}

```



Data.java

```java
package com.mf.Snake;

import javax.swing.*;
import java.net.URL;

/**
 * @author mf
 * @create 2021-05-12-20:53
 */
//数据中心
public class Data {
    public static URL bodyURl=Data.class.getResource("/statics/body.png");
    public static ImageIcon body=new ImageIcon(bodyURl);
    public static URL downURl=Data.class.getResource("/statics/down.png");
    public static ImageIcon down=new ImageIcon(downURl);
    public static URL foodURl=Data.class.getResource("/statics/food.png");
    public static ImageIcon food=new ImageIcon(foodURl);
    public static URL headerURl=Data.class.getResource("/statics/header.png");
    public static ImageIcon header=new ImageIcon(headerURl);
    public static URL leftURl=Data.class.getResource("/statics/left.png");
    public static ImageIcon left=new ImageIcon(leftURl);
    public static URL rightURl=Data.class.getResource("/statics/right.png");
    public static ImageIcon right=new ImageIcon(rightURl);
    public static URL upURl=Data.class.getResource("/statics/up.png");
    public static ImageIcon up=new ImageIcon(upURl);
}

```





<img src="https://i.loli.net/2021/05/20/mOFbzysoe5GWKjg.png" alt="思维导图2" style="zoom:67%;float:left" />