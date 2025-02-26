#Buổi 10. THƯ VIỆN ĐỒ HỌA SWING VÀ JAVAFX

### Java Swing

- **Thư viện đồ họa Swing cơ bản**
    
    
    - **Swing** trong Java là một bộ công cụ **Giao diện Người dùng Đồ họa (GUI)** bao gồm các thành phần GUI. Swing cung cấp một bộ widget và gói phong phú để tạo ra các thành phần GUI tinh vi cho các ứng dụng Java.
    - **Swing** là thư viện Lớp nền tảng Java (JFC - Java Foundation Classes) và là phần mở rộng của Bộ công cụ cửa sổ trừu tượng (AWT), một bộ công cụ GUI phụ thuộc vào nền tảng cũ hơn. Khác với AWT, Swing hoạt động nhẹ hơn và độc lập với nền tảng thiết bị, và bổ sung thêm nhiều lớp hiển thị mạnh mẽ hơn.
    - Gói **`javax.swing`** cung cấp các lớp cho java swing API như JButton, JTextField, JTextArea, JRadioButton, JCheckbox, JMenu, JColorChooser, etc..
    
    | Java AWT | Java Swing |
    | --- | --- |
    | Java AWT là một API để phát triển các ứng dụng GUI trong Java. | Swing là một lớp nền tảng của Java và được sử dụng để tạo các ứng dụng khác nhau. |
    | Các thành phần của AWT có trọng số nặng và phụ thuộc vào nền tảng. | Các thành phần của Java Swing rất nhẹ và độc lập với nền tảng thiết bị. |
    | Thời gian thực hiện nhiều hơn Swing | Thời gian thực hiện nhỏ hơn AWT |
    | Các thành phần yêu cầu gói **`java.awt`** | Các thành phần yêu cầu gói **`javax.swing`** |
    
    - **Đặc điểm**
        - Độc lập với thiết bị.
        - Có thể tùy chỉnh, mở rộng.
        - Khá nhẹ.
        - Có thể cấu hình.
    - **Sử dụng**: Cung cấp các bộ điều khiển nâng cao như thanh trượt, colorpicker, Tree, TabbedPane và bảng điều khiển,..
    
    - **Event**:
        - Là sự thay đổi trạng thái của một đối tượng
        - Sự tương tác của người dùng với hệ thống: Click vào button, cuộn màn hình…
        - **Event Handler**: được gọi khi event xảy ra (VD: Một event handler được gọi để bắt các sự kiện xảy ra khi click vào button)
        - **Callback**: Các hàm được gọi trong event handler để xử lý các logic toán bài toán.
    
    ![Các lớp phân tầng Java Swing (Source: [https://t3h.com.vn](https://t3h.com.vn/))](image.png)
    
    Các lớp phân tầng Java Swing (Source: [https://t3h.com.vn](https://t3h.com.vn/))
    
    **Các phương thức thường gặp ở lớp Component**
    
    | **Phương thức** | **Mô tả** |
    | --- | --- |
    | `public void add(Component c)` | Thêm một thành phần vào thành phần khác. |
    | `public void setSize(int width, int height)` | Thiết lập kích thước của thành phần. |
    | `public void setLayout(LayoutManager m)` | Thiết lập trình quản lý bố cục (layout) cho thành phần. |
    | `public void setVisible(boolean b)` | Thiết lập khả năng hiển thị của thành phần. Nó theo mặc định là false (ẩn) |
- **Container trong Java**
    - Container là thành phần chủ chốt trong các thành phần cơ bản của Swing GUI. Một Container cung cấp một không gian cho các Component hoạt động bên trong.
    - Các lớp con của Container được gọi là Container. Một số lớp con của Container là **`JPanel`**, **`JLabel`**, **`JWindow`**
    - Một layout mặc định có mặt trong mỗi container. Layout này có thể bị ghi đè bởi sử dụng phương thức **`setLayout()`**
    - **`JPanel`**: Lớp này gồm các Constructor sau
        - **`JPanel()`**: Tạo một JPanel mới với một doubleBuffer và một Flow Layout.
        - **`JPanel(boolean isDoubleBuffered)`:** Tạo một JPanel mới với Flow Layout và trình đệm đã xác định.
        - **`JPanel(LayoutManager layout)`:** Tạo một JPanel mới với Layout Manager đã cho
        - **`JPanel(LayoutManager layout, boolean is DoubleBuffered)`:** Tạo một JPanel mới với Layout Manager đã cho và trình đệm đã xác định.
            
            ```java
            import java.awt.*;
            import java.awt.event.*;
            import javax.swing.*;
            
            public class SwingContainerDemo {
               private JFrame mainFrame;
               private JLabel headerLabel;
               private JLabel statusLabel;
               private JPanel controlPanel;
               private JLabel msglabel;
            
               public SwingContainerDemo(){
                  prepareGUI();
               }
            
               public static void main(String[] args){
                  SwingContainerDemo  swingContainerDemo = new SwingContainerDemo();  
                  swingContainerDemo.showJPanelDemo();
               }
            
               private void prepareGUI(){
                  mainFrame = new JFrame("Vi du Java Swing");
                  mainFrame.setSize(400,400);
                  mainFrame.setLayout(new GridLayout(3, 1));
                  mainFrame.addWindowListener(new WindowAdapter() {
                     public void windowClosing(WindowEvent windowEvent){
                        System.exit(0);
                     }        
                  });    
                  headerLabel = new JLabel("", JLabel.CENTER);        
                  statusLabel = new JLabel("",JLabel.CENTER);    
            
                  statusLabel.setSize(350,100);
            
                  msglabel = new JLabel("Chao mung ban den voi bai huong dan Java Swing.", JLabel.CENTER);
            
                  controlPanel = new JPanel();
                  controlPanel.setLayout(new FlowLayout());
            
                  mainFrame.add(headerLabel);
                  mainFrame.add(controlPanel);
                  mainFrame.add(statusLabel);
                  mainFrame.setVisible(true);  
               }
            
               private void showJPanelDemo(){
                  headerLabel.setText("Container in action: JPanel");      
            
                  JPanel panel = new JPanel();
                  panel.setBackground(Color.magenta);
                  panel.setLayout(new FlowLayout());        
                  panel.add(msglabel);
            
                  controlPanel.add(panel);        
                  mainFrame.setVisible(true);      
               }   
            }
            ```
            
    - **`JFrame`**: Giống như một cửa sổ window có tiêu đề và viền
        
        
        - Các Constructor
            - **`JFrame()`**: Xây dựng một Frame mới, ban đầu là không nhìn thấy (invisible).
            - **`JFrame(GraphicsConfiguration gc)`**: Tạo một Frame trong GraphicsConfiguration đã cho của một thiết bị màn hình và một title trống.
            - **`JFrame(String title)`**: Tạo một Frame mới, ban đầu là không nhìn thấy (invisible) với title đã cho.
            - **`JFrame(String title, GraphicsConfiguration gc)`**: Tạo một Frame với title đã cho và GraphicsConfiguration đã cho của một thiết bị màn hình.
        
        - Các phương thức
            - `setTitle("Title")` : cài đặt tên tiêu đề.
            - `setLocationRelativeTo(null)` : đặt cho cửa sổ xuất hiện ở giữa màn hình.
            - `setResizable(false)` : cài đặt ko cho phép kéo thả thay đổi kích thước cửa sổ.
            - `setDefaultCloseOperation(DO_NOTHING_ON_CLOSE)` : lựa chọn ko làm gì khi bạn nhấn nút đóng cửa sổ (nút chéo đỏ).
            - `setLayout(layout)` : cài đặt cách bố trí các component trong container.
            - `add(component)`: Thêm component vào Container → Hiển thị component
        
        ```java
        import java.awt.*;
        import java.awt.event.*;
        import javax.swing.*;
        
        public class SwingContainerDemo {
           private JFrame mainFrame;
           private JLabel headerLabel;
           private JLabel statusLabel;
           private JPanel controlPanel;
           private JLabel msglabel;
        
           public SwingContainerDemo(){
              prepareGUI();
           }
        
           public static void main(String[] args){
              SwingContainerDemo  swingContainerDemo = new SwingContainerDemo();  
              swingContainerDemo.showJFrameDemo();
           }
        
           private void prepareGUI(){
              mainFrame = new JFrame("Vi du Java Swing");
              mainFrame.setSize(400,400);
              mainFrame.setLayout(new GridLayout(3, 1));
              mainFrame.addWindowListener(new WindowAdapter() {
                 public void windowClosing(WindowEvent windowEvent){
                    System.exit(0);
                 }        
              });    
              headerLabel = new JLabel("", JLabel.CENTER);        
              statusLabel = new JLabel("",JLabel.CENTER);    
        
              statusLabel.setSize(350,100);
        
              msglabel = new JLabel("Chao mung ban den voi bai huong dan Java Swing.", JLabel.CENTER);
        
              controlPanel = new JPanel();
              controlPanel.setLayout(new FlowLayout());
        
              mainFrame.add(headerLabel);
              mainFrame.add(controlPanel);
              mainFrame.add(statusLabel);
              mainFrame.setVisible(true);  
           }
        
           private void showJFrameDemo(){
              headerLabel.setText("Container in action: JFrame");   
        
              final JFrame frame = new JFrame();
              frame.setSize(300, 300);
              frame.setLayout(new FlowLayout());       
              frame.add(msglabel);
              frame.addWindowListener(new WindowAdapter() {
                 public void windowClosing(WindowEvent windowEvent){
                    frame.dispose();
                 }        
              });    
              JButton okButton = new JButton("Open a Frame");
              okButton.addActionListener(new ActionListener() {
                 public void actionPerformed(ActionEvent e) {
                    statusLabel.setText("Mot Frame duoc hien thi toi nguoi dung.");
                    frame.setVisible(true);
                 }
              });
              controlPanel.add(okButton);
              mainFrame.setVisible(true);  
           }
        }
        ```
        
    - **`JWindow`**: Lớp này gồm các Constructor sau
        - **`JWindow()`**: Tạo một window mà không xác định khung sở hữu nó (owner frame).
        - **`JWindow(Frame owner)`**: Tạo một window với owner frame đã cho.
        - **`JWindow(GraphicsConfiguration gc)`**: Tạo một window với GraphicsConfiguration đã cho của một thiết bị màn hình.
        - **`JWindow(Window owner)`**: Tạo một window với cửa sổ sở hữu nó đã cho (owner window).
        - **`JWindow(Window owner, GraphicsConfiguration gc)`**: Tạo một window với cửa sổ sở hữu nó đã cho (owner window) và GraphicsConfiguration đã cho của một thiết bị màn hình.
            
            ```java
            import java.awt.*;
            import java.awt.event.*;
            import javax.swing.*;
            
            public class SwingContainerDemo {
               private JFrame mainFrame;
               private JLabel headerLabel;
               private JLabel statusLabel;
               private JPanel controlPanel;
               private JLabel msglabel;
            
               public SwingContainerDemo(){
                  prepareGUI();
               }
            
               public static void main(String[] args){
                  SwingContainerDemo  swingContainerDemo = new SwingContainerDemo();  
                  swingContainerDemo.showJWindowDemo();
               }
            
               private void prepareGUI(){
                  mainFrame = new JFrame("Vi du Java Swing");
                  mainFrame.setSize(400,400);
                  mainFrame.setLayout(new GridLayout(3, 1));
                  mainFrame.addWindowListener(new WindowAdapter() {
                     public void windowClosing(WindowEvent windowEvent){
                        System.exit(0);
                     }        
                  });    
                  headerLabel = new JLabel("", JLabel.CENTER);        
                  statusLabel = new JLabel("",JLabel.CENTER);    
            
                  statusLabel.setSize(350,100);
            
                  msglabel = new JLabel("Chao mung ban den voi bai huong dan Java Swing."
                     , JLabel.CENTER);
            
                  controlPanel = new JPanel();
                  controlPanel.setLayout(new FlowLayout());
            
                  mainFrame.add(headerLabel);
                  mainFrame.add(controlPanel);
                  mainFrame.add(statusLabel);
                  mainFrame.setVisible(true);  
               }
            
               private void showJWindowDemo(){
                  headerLabel.setText("Container in action: JWindow");   
                  final MessageWindow window = new MessageWindow(mainFrame, "Chao mung ban den voi bai huong dan Java Swing.");
            
                  JButton okButton = new JButton("Open a Window");
                  okButton.addActionListener(new ActionListener() {
                     public void actionPerformed(ActionEvent e) {
                        window.setVisible(true);
                        statusLabel.setText("Mot Window duoc hien thi toi nguoi dung."); 
                     }
                  });
                  controlPanel.add(okButton);
                  mainFrame.setVisible(true);  
               }
            
               class MessageWindow extends JWindow{
                  private String message; 
            
                  public MessageWindow(JFrame parent, String 
                     message) { 
                     super(parent);               
                     this.message = message; 
                     setSize(300, 300);       
                     setLocationRelativeTo(parent);         
                  }
            
                  public void paint(Graphics g) 
                  { 
                     super.paint(g);
                     g.drawRect(0,0,getSize().width - 1,getSize().height - 1); 
                     g.drawString(message,50,150); 
                  } 
               }
            }
            ```
            
- **Một số Component cơ bản**
    - **`JButton`**
        
        
        - Là một bộ thư viện trong Java Swing, được sử dụng để tạo một nút button mà có trình triển khai là độc lập nền tảng. Thành phần này có một label và tạo một sự kiện (event) khi được nhấn. Nó cũng có thể có Image.
        - Các Constructor của **`JButton`**
            - **`JButton()`**: Tạo một button mà không thiết lập text hoặc icon.
            - **`JButton(Action a)`**: Tạo một button tại đây các thuộc tính được nhận từ Action đã cung cấp.
            - **`JButton(Icon icon)`**: Tạo một button với một icon.
            - **`JButton(String text)`**: Tạo một button với text.
            - **`JButton(String text, Icon icon)`**: Tạo một button với text ban đầu và một icon.
        - Các phương thức của **`JButton`**
            - `setText("Bấm vào đây")` : đặt nội dung text cần hiển thị.
            - `setFont(font)` : cài đặt font.
        
        ```java
        import javax.swing.*;
        
        public class Main {
            public static void main(String[] args) {
                JFrame a = new JFrame("Example");
                JButton b = new JButton("click me");
                b.setBounds(100, 100, 100, 100);
                a.add(b);
                a.setSize(400, 400);
                a.setLayout(null);
                a.setVisible(true);
            }
        }
        ```
        
    - **`JLabel`**
        
        
        - Có thể hiển thị hoặc text, hoặc hình ảnh hoặc cả hai. Các nội dung của Label được gán bởi thiết lập căn chỉnh ngang và dọc trong khu vực hiển thị của nó.
        - Theo mặc định:
            - Các label được căn chỉnh theo chiều dọc trong khu vực hiển thị.
            - text-only label là căn chỉnh theo cạnh, image-only label là căn chỉnh theo chiều ngang.
        - Các Constructor của **`JLabel`**
            - **`JLabel()`**: Tạo một instance của JLabel, không có hình ảnh, và với một chuỗi trống cho title.
            - **`JLabel(Icon image)`**: Tạo một instance của JLabel với hình ảnh đã cho.
            - **`JLabel(Icon image, int horizontalAlignment)`**: Tạo một instance của JLabel với hình ảnh và căn chỉnh ngang đã cho.
            - **`JLabel(String text)`**: Tạo một instance của JLabel với text đã cho.
            - **`JLabel(String text, Icon icon, int horizontalAlignment)`**: Tạo một instance của JLabel với text, hình ảnh, và căn chỉnh ngang đã cho.
            - **`JLabel(String text, int horizontalAlignment)`**: Tạo một instance của JLabel với text và căn chỉnh ngang đã cho.
        - Các phương thức của **`JLabel`**
            - `setText("Số lần bấm: " + count)` : đặt nội dung text cần hiển thị.
            - `setFont(new Font("VNI", Font.PLAIN, 24))` : cài đặt font.
            - `setOpaque(true)` : mặc định màu nền của Label là trong suốt → Cài đặt tính đục bằng `true` → Phương thức `setBackground()` mới có hiệu lực.
            - `setHorizontalAlignment(JLabel.CENTER)` : căn text vào giữa Label theo hàng ngang.
            - `setVerticalAlignment(JLabel.CENTER)` : căn text vào giữa Label theo hàng dọc.
        
        ```java
        import javax.swing.*;
        
        public class Main {
            Main(){
                JFrame frame = new JFrame("Demo Console");
                JLabel b1;
                b1 = new JLabel("Hello World");
                b1.setBounds(80, 80, 100, 100);
                frame.add(b1);
                frame.setSize(400, 400);
                frame.setLayout(null);
                frame.setVisible(true);
            }
            public static void main(String[] args) {
                new Main();
            }
        }
        ```
        
    - **`JTextField`**
        
        
        - Nó kế thừa lớp **`JText`** Component và dùng để cho phép chỉnh sửa dòng đơn.
        - Kết hợp **`JTextField`** + **`JLabel`** → Form nhập thông tin cho User.
        - Các Constructor của **`JTextField`**
            - **`JTextField**()`: Xây dựng một TextField mới.
            - **`JTextField**(Document doc, String text, int columns)`: Xây dựng một JTextField mới mà sử dụng mô hình lưu trữ text đã cho và số cột đã cho.
            - **`JTextField**(int columns)`: Xây dựng một TextField mới và trống với số cột đã cho.
            - `JTextField(String text)`: Xây dựng một TextField mới được khởi tạo với text đã cho.
            - **`JTextField**(String text, int columns)`: Xây dựng một TextField mới được khởi tạo với text và các cột đã cho.
        - Các phương thức cơ bản của **`JTextField`**
            - `setText()` : tương tự.
            - `setFont()` : tương tự.
            - `setEnabled(false)` : ngăn ko cho chỉnh sửa nội dung text từ bên ngoài.
        
        ```java
        import javax.swing.*;
        
        public class Main {
            public static void main(String[] args) {
                JFrame frame = new JFrame("JTextField Example");
                JTextField text = new JTextField("Type sth: ");
                text.setEditable(false);
                text.setBounds(50, 60, 100, 120);
                frame.add(text);
                frame.setSize(400, 300);
                frame.setLayout(null);
                frame.setVisible(true);
            }
        }
        ```
        
    - **`JTextArea`**
        
        
        - Cho phép nhập dữ liệu trong nhiều dòng, nhiều hàng khác nhau.
        - Các Constructor của **`JTextArea`**
            - **`JTextArea()`**: Tạo một TextArea mới.
            - **`JTextArea**(String s)`: Tạo một TextArea mới với text đã cho.
            - **`JTextArea**(int row, int column)`: Tạo một TextArea trống, mới với số hàng và cột đã cho.
            - **`JTextArea**(String s, int row, int column)`: Tạo một TextArea mới với text, số hàng và cột đã cho.
        - Một số phương thức của **`JTextArea`**
            - `setText()` : tương tự.
            - `setFont()` : tương tự.
            - `setEnabled()` : tương tự.
            - `setLineWrap(true)` : cài đặt xuống dòng khi tràn chiều dài khung text, tuy nhiên nó ko cắt nguyên vẹn từ xuống dòng mới đâu.
            - `setWrapStyleWord(true)` : cho phép cắt nguyên vẹn từ xuống dòng mới.
        
        ```java
        import java.awt.Color;
        import javax.swing.*;
        
        public class Main {
            JTextArea area;
            JFrame f;
            Main(){
                f = new JFrame();
                area = new JTextArea(300,300);
                area.setBounds(10,30,300,300);
                area.setBackground(Color.black);
                area.setForeground(Color.white);
                
                f.add(area);
                f.setSize(400,400);
                f.setLayout(null);
                f.setVisible(true);
            }
            public static void main(String[] args) {
                new Main();
            }
        }
        ```
        
    - **`JList`**
        
        
        - `JList` là một component hiển thị danh sách các đối tượng, cho phép người dùng chọn được item.
        - Bản thân `JList` chỉ là thành phần hiển thị. Để nạp dữ liệu cho `JList` hiển thị, cần có đối tượng model để chứa dữ liệu đó là **`DefaultListModel`**.
        - Để truyền dữ liệu vào model cần có mảng dữ liệu, mảng đó là kết quả của các quá trình tìm kiếm, sắp xếp
        → Con đường dữ liệu được hiển thị: ArrayList –> DefaultListModel –> JList
        - `JList` thường phải đặt trong một loại component khung chứa là `JScrollPane` (Hỗ trợ thanh cuộn)
        - Các Constructor của `JList`
            - **`JList()`**: Xây dựng một `JList` với một model là empty, read-only.
            - **`JList(ListModel dataModel)`**: Xây dựng một `JList` mà hiển thị các phần tử từ model đã cho và non-null.
            - **`JList(Object[] listData)`**: Xây dựng một `JList` mà hiển thị các phần tử trong mảng đã cho.
            - **`JList(Vector<?> listData)`**: Xây dựng một `JList` mà hiển thị các phần tử trong Vector đã cho.
        - Các trường quan trọng của `JList`
            - **`static int HORIZONTAL_WRAP`**: Trình bày một layout theo phong cách như một tờ báo ("newspaper style") với các ô tràn theo chiều ngang và sau đó là chiều dọc.
            - **`static int VERTICAL`**: Chỉ một cách bố trí các ô theo chiều dọc, trong một cột đơn.
            - **`static int VERTICAL_WRAP`**: Chỉ một layout theo phong cách như một tờ báo "newspaper style" với các ô tràn theo chiều dọc và sau đó là chiều ngang.
        
        ```java
        import javax.swing.*;
        
        public class Main {
            Main(){
                JFrame frame = new JFrame("JList Example");
                DefaultListModel<String> listModel = new DefaultListModel<>();
                listModel.addElement("First item");
                listModel.addElement("Second item");
                JList<String> jl = new JList<>(listModel);
                jl.setBounds(100, 100, 75, 75);
                frame.add(jl);
                frame.setSize(400, 400);
                frame.setVisible(true);
                frame.setLayout(null);
            }
            public static void main(String[] args){
                new Main();
            }
        }
        ```
        
    - **`JTable`**
        
        
        - Lớp `JTable` được sử dụng để hiển thị dữ liệu trên các ô của bảng hai chiều.
        - Con đường hiển thị dữ liệu ra màn hình của `JTable` như sau: ArrayList –> DefaultTableModel –> JTable
        - `JTable` chỉ có khả năng hiển thị dữ liệu dạng String → Chuyển các dữ liệu khác về kiểu chuỗi.
        - Các Constructor của `JTable`
            - **`JTable()`**: Tạo một bảng với các ô trống.
            - **`JTable(Object[][] rows, Object[] columns)`**: Tạo một bảng với dữ liệu đã cho.
        
        ```java
        import javax.swing.*;
        public class Main {
            JFrame f;
            Main(){
                f=new JFrame();
        
                String data[][]={ {"101","Amit","670000"},
                        {"102","Jai","780000"},
                        {"101","Sachin","700000"}};
                String column[]={"ID","NAME","SALARY"};
        
                JTable jt=new JTable(data,column);
                jt.setBounds(30, 40, 200, 300);
                JScrollPane sp=new JScrollPane(jt);
                f.add(sp);
        
                f.setSize(300,400);
            //  f.setLayout(null);
                f.setVisible(true);
            }
            public static void main(String[] args) {
                new Main();
            }
        }
        ```
        
- **BorderLayout, FlowLayout, GridLayout**
    - **Layout**: có tác dụng tự động bố trí các component trên container (Giống như một căn nhà lớn có nhiều phòng, mỗi phòng có thể tự thay đổi kích thước và các vật dụng trong đó tự thay đổi theo tỷ lệ của phòng)
    - **BorderLayout**
        
        
        - BorderLayout sắp xếp các component theo vùng, ở đây có 5 vùng là Đông (**EAST**), Tây (**WEST**), Nam (**SOUTH**), Bắc (**NORTH**), và Chính giữa (**CENTER**)
        - Do mỗi vùng chỉ chứa một component → Đưa nhiều component vào một vùng: Đưa một Layout khác vào → Đưa các component vào Layout mới.
        - Kích thước mỗi vùng do dev tự thiết lập, trừ vùng **CENTER** sẽ thay đổi kích thước tùy thuộc vào 4 vùng còn lại.
        - Mặc định JFrame dùng sẵn BorderLayout nên chúng ta không cần phải thiết lập lại.
        
        ```java
        import javax.swing.JButton;
        import javax.swing.JFrame;
        import javax.swing.JPanel;
        
        import java.awt.*;
        
        public class Main {
            public static void main(String[] args) {
                // Create and set up a frame window
                JFrame.setDefaultLookAndFeelDecorated(true);
                JFrame frame = new JFrame("Layout");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
                // Define the panel to hold the buttons
                JPanel panel = new JPanel();
                JButton jb1 = new JButton("NORTH");
                JButton jb2 = new JButton("SOUTH");
                JButton jb3 = new JButton("WEST");
                JButton jb4 = new JButton("EAST");
                JButton jb5 = new JButton("CENTER");
        
                // Define the panel to hold the buttons
                panel.setLayout(new BorderLayout());
                panel.add(jb1, BorderLayout.NORTH);
                panel.add(jb2, BorderLayout.SOUTH);
                panel.add(jb3, BorderLayout.WEST);
                panel.add(jb4, BorderLayout.EAST);
                panel.add(jb5, BorderLayout.CENTER);
        
                // Set the window to be visible as the default to be false
                frame.add(panel);
                frame.pack();
                frame.setVisible(true);
            }
        }
        ```
        
    - **FlowLayout**
        
        
        - Đây là loại layout đơn giản nhất, layout này thường được dùng kết hợp với các layout khác.
        - Layout này quy định kích thước của các component con là vừa đủ với nội dung hiển thị của component.
        - Mặc định: các component sẽ được sắp xếp trên một hàng từ trái sang phải, nếu không vừa đủ một hàng thì chúng sẽ xuống hàng. Các component sẽ cách nhau 5 pixel và cách viền cửa sổ 5 pixel.
            
            ```java
            FlowLayout()
            FlowLayout(int align)
            FlowLayout(int align, int hgap, int vgap)
            
            // Chú thích:
            // align: Sắp xếp từ trái sang phải hoặc ngược lại
            // hgap: Khoảng cách giữa các component theo chiều ngang
            // vgap: Khoảng cách giữa các component theo chiều dọc
            ```
            
        
        ```java
        import javax.swing.JButton;
        import javax.swing.JFrame;
        import javax.swing.JPanel;
        
        import java.awt.FlowLayout;
        
        public class Main {
        
            public static void main(String[] args) {
                // Create and set up a frame window
                JFrame.setDefaultLookAndFeelDecorated(true);
                JFrame frame = new JFrame("Layout");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
                // Define new buttons
                JButton jb1 = new JButton("Button 1");
                JButton jb2 = new JButton("Button 2");
                JButton jb3 = new JButton("Button 3");
        
                // Define the panel to hold the buttons
                JPanel panel = new JPanel();
                FlowLayout flowLayout = new FlowLayout();
                flowLayout.setAlignment(FlowLayout.LEFT);
                flowLayout.setHgap(10);
                panel.setLayout(flowLayout);
                panel.add(jb1);
                panel.add(jb2);
                panel.add(jb3);
        
                // Set the window to be visible as the default to be false
                frame.add(panel);
                frame.pack();
                frame.setVisible(true);
            }
        }
        ```
        
    - **GridLayout**
        
        
        - Layout này sắp xếp các component theo dạng lưới hình chữ nhật. Các component là các hình chữ nhật có kích thước bằng nhau.
        - Chúng ta có thể khởi tạo GridLayout thông qua các constructor sau:
            
            ```java
            GridLayout()
            GridLayout(int row, int col)
            GridLayout(int row, int col, int hgap, int vgap)
            
            // Chú thích
            // row: Số hàng được tạo
            // col: Số cột được tạo
            // hgap: Khoảng cách giữa các phần tử trên một dòng
            // vgap: Khoảng cách giữa các phần tử trên một cột
            ```
            
        
        ```java
        import javax.swing.*;
        import java.awt.*;
        
        public class Main extends JFrame {
            public static void main(String[] args) {
                // Create and set up a frame window
                JFrame.setDefaultLookAndFeelDecorated(true);
                JFrame frame = new JFrame("GridLayout Example");
                frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                
                JButton jb1 = new JButton("Button 1");
                JButton jb2 = new JButton("Button 2");
                JButton jb3 = new JButton("Button 3");
                JButton jb4 = new JButton("Button 4");
                JButton jb5 = new JButton("Button 5");
        
                JPanel panel = new JPanel();
                panel.setLayout(new GridLayout(3, 2));
                panel.add(jb1);
                panel.add(jb2);
                panel.add(jb3);
                panel.add(jb4);
                panel.add(jb5);
        
                frame.add(panel);
                frame.pack();
                frame.setVisible(true);
            }
        }
        ```
        
- **Graphics2D, Image**
    - **Graphics2D**
        
        
        - Graphics2D là một lớp mở rộng của Graphics, cung cấp khả năng vẽ đồ họa 2D nâng cao trong Java. Nó được sử dụng để vẽ các hình dạng (đường thẳng, hình tròn, chữ nhật), tô màu, vẽ văn bản, và xử lý hình ảnh trên các thành phần giao diện như JPanel hoặc JFrame.
        - Thường được lấy từ phương thức **`paintComponent(Graphics g)`** khi bạn ghi đè (override) nó trong một thành phần Swing (như JPanel).
        - Đặc điểm:
            - Hỗ trợ vẽ vector (hình học).
            - Hỗ trợ các hiệu ứng như xoay, thu phóng, đổ bóng.
            - Là công cụ chính để tùy chỉnh giao diện Swing.
        - Thuộc tính/Phương thức chính:
            - `setColor(Color c)`: Đặt màu vẽ.
            - `draw(Shape s)`: Vẽ viền của hình dạng (ví dụ: đường thẳng, hình tròn).
            - `fill(Shape s)`: Tô màu bên trong hình dạng.
            - `drawString(String str, int x, int y)`: Vẽ văn bản tại vị trí (x, y).
            - `setFont(Font f)`: Đặt kiểu chữ cho văn bản.
            - `drawImage(Image img, int x, int y, ImageObserver observer)`: Vẽ hình ảnh tại vị trí (x, y).
            - `setRenderingHint()`: Tùy chỉnh chất lượng vẽ (ví dụ: chống răng cưa).
        
        ```java
        import javax.swing.*;
        import java.awt.*;
        
        public class Graphics2DDemo extends JPanel {
            @Override
            protected void paintComponent(Graphics g) {
                super.paintComponent(g);
                Graphics2D g2d = (Graphics2D) g; // Ép kiểu sang Graphics2D
        
                // Vẽ hình tròn đỏ
                g2d.setColor(Color.RED);
                g2d.fillOval(50, 50, 100, 100); // Hình tròn tại (50, 50), kích thước 100x100
        
                // Vẽ văn bản
                g2d.setColor(Color.BLACK);
                g2d.setFont(new Font("Times New Roman", Font.BOLD, 20));
                g2d.drawString("Hello Graphics2D", 50, 180);
            }
        
            public static void main(String[] args) {
                SwingUtilities.invokeLater(() -> {
                    JFrame frame = new JFrame("Graphics2D Demo");
                    frame.setSize(300, 250);
                    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                    frame.add(new Graphics2DDemo());
                    frame.setVisible(true);
                });
            }
        }
        ```
        
    - **Image**
        
        
        - Image là một lớp trừu tượng trong gói **`java.awt`**, đại diện cho hình ảnh (ảnh bitmap như PNG, JPG). Trong Swing, nó thường được sử dụng cùng Graphics2D để vẽ hình ảnh lên giao diện. Để làm việc với hình ảnh cụ thể, bạn thường dùng lớp con BufferedImage từ gói `java.awt.image`.
        - Đặc điểm:
            - Hỗ trợ tải hình ảnh từ file, URL, hoặc tạo thủ công.
            - Có thể thay đổi kích thước, xoay, hoặc chỉnh sửa pixel.
        - Thuộc tính/Phương thức chính:
            - `ImageIO.read(File file)`: Tải hình ảnh từ file (trả về BufferedImage).
            - `Graphics.drawImage(Image img, int x, int y, ImageObserver observer)`: Vẽ hình ảnh lên giao diện.
            - `getScaledInstance(int width, int height, int hints)`: Thay đổi kích thước hình ảnh.
            - `BufferedImage.getGraphics()`: Lấy đối tượng Graphics2D để vẽ lên hình ảnh.
        
        ```java
        import javax.swing.*;
        import java.awt.*;
        import java.awt.image.BufferedImage;
        import javax.imageio.ImageIO;
        import java.io.File;
        import java.io.IOException;
        
        public class ImageDemo extends JPanel {
            private BufferedImage image;
        
            public ImageDemo() {
                try {
                    // Tải hình ảnh từ file (đảm bảo file tồn tại)
                    image = ImageIO.read(new File("example.jpg")); // Thay "example.jpg" bằng đường dẫn file của bạn
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        
            @Override
            protected void paintComponent(Graphics g) {
                super.paintComponent(g);
                Graphics2D g2d = (Graphics2D) g;
        
                if (image != null) {
                    // Vẽ hình ảnh tại (50, 50)
                    g2d.drawImage(image, 50, 50, null);
        
                    // Vẽ viền đỏ quanh hình ảnh
                    g2d.setColor(Color.RED);
                    g2d.drawRect(50, 50, image.getWidth(), image.getHeight());
                }
            }
        
            public static void main(String[] args) {
                SwingUtilities.invokeLater(() -> {
                    JFrame frame = new JFrame("Image Demo");
                    frame.setSize(400, 400);
                    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
                    frame.add(new ImageDemo());
                    frame.setVisible(true);
                });
            }
        }
        ```
        

### JavaFX

- Java FX là một nền tảng phát triển ứng dụng giao diện người dùng đa nền tảng (UI) được xây dựng trên ngôn ngữ lập trình Java.
- Nó cung cấp các công cụ và thư viện mạnh mẽ để phát triển giao diện người dùng đáng tin cậy, đẹp mắt và tương tác trên các thiết bị khác nhau như máy tính cá nhân, máy tính bảng, thiết bị di động và các thiết bị nhúng.
- Java FX kế thừa và hoàn thiện công nghệ Swing truyền thống trong Java.

| Ưu điểm | Nhược điểm |
| --- | --- |
| Giao diện người dùng đẹp mắt và tương tác cao. | Học cú pháp và khái niệm mới so với Swing. |
| Hỗ trợ các hiệu ứng đồ họa và hoạt ảnh phức tạp. | Việc tạo ra một số hiệu ứng phức tạp có thể yêu cầu kiến thức sâu về Java FX. |
| Đa nền tảng và tương thích ngược với Swing. | Số lượng tài liệu và tài nguyên hạn chế so với Swing. |
| Công cụ và thư viện mạnh mẽ để xây dựng ứng dụng phong phú. |  |
| Tích hợp tốt với ngôn ngữ Java và các thư viện Java. |  |
| Hỗ trợ kéo thả và chỉnh sửa Layout tốt hơn, hỗ trợ phát triển trên nền tảng di động. |  |

- **Cấu trúc giao diện JavaFX**
    
    
    - **Stage**
        - Là container cấp cao nhất, đại diện cho cửa sổ ứng dụng.
        - Một ứng dụng JavaFX có thể có nhiều Stage (ví dụ: cửa sổ chính, cửa sổ bật lên), nhưng thường chỉ có một Stage chính.
        - Đối tượng Stage đã tạo sẽ được truyền như một đối số cho phương thức **`start()`** của lớp **Application**
        - Thuộc tính: tiêu đề (title), kích thước, khả năng hiển thị (**`show()`**)
    - **Scene**
        - Là container trực tiếp chứa Scene Graph, mỗi Scene Graph là một cây - giống như CTDL thể hiện nội dung của một Scene.
        - Được gắn vào Stage thông qua **`setScene()`**
        - Yêu cầu:
            - Một node gốc (root node)
            - Kích thước (width, height)
        - Ví dụ: `Scene scene = new Scene(root, 600, 400);`
    - **Node**
        - Là một đối tượng trực quan/đồ họa của Scene Graph, bao gồm:
            - Controls (Điều khiển): Button, Label, TextField, CheckBox, v.v.
            - Shapes (Hình dạng): Rectangle, Circle, Line, v.v.
            - Media: ImageView, MediaView để hiển thị hình ảnh, video.
            - Layouts (Bố cục): Các container tổ chức các node khác.
    
    ![Cấu trúc ứng dụng JavaFX (Source: [https://v1study.com](https://v1study.com/))](image%201.png)
    
    Cấu trúc ứng dụng JavaFX (Source: [https://v1study.com](https://v1study.com/))
    
- **Một số Component cơ bản**
    
    
    1. **Button**
        - Mô tả: Nút bấm để người dùng tương tác, thường gắn với một hành động khi được nhấp.
        - Cách dùng: Tạo một đối tượng Button và gắn sự kiện (event) bằng **`setOnAction`**.
    2. **Label**
        - Mô tả: Hiển thị văn bản không chỉnh sửa được, thường dùng để chú thích.
        - Cách dùng: Tạo đối tượng Label và đặt nội dung bằng **`setText()`**.
    3. **TextField**
        - Mô tả: Ô nhập liệu cho phép người dùng gõ văn bản một dòng.
        - Cách dùng: Tạo TextField và lấy dữ liệu nhập bằng **`getText()`**.
    
    1. **CheckBox**
        - Mô tả: Hộp kiểm cho phép người dùng chọn/bỏ chọn một tùy chọn.
        - Cách dùng: Tạo CheckBox và kiểm tra trạng thái bằng **`isSelected()`**.
        
    2. **RadioButton**
        - Mô tả: Nút chọn tròn, thường dùng trong nhóm để người dùng chỉ chọn một tùy chọn duy nhất.
        - Cách dùng: Sử dụng cùng ToggleGroup để đảm bảo chỉ một nút được chọn.
        
    3. **ComboBox**
        - Mô tả: Hộp thả xuống cho phép người dùng chọn một mục từ danh sách.
        - Cách dùng: Thêm các mục bằng **`getItems().add()`**.
    
    1. **ListView**
        - Mô tả: Danh sách các mục mà người dùng có thể chọn (hỗ trợ chọn một hoặc nhiều).
        - Cách dùng: Thêm dữ liệu vào **`getItems()`**.
    
    1. **Slider**
        - Mô tả: Thanh trượt để người dùng chọn giá trị trong một khoảng.
        - Cách dùng: Đặt giá trị min, max và giá trị ban đầu.
        
    2. **TextArea**
        - Mô tả: Ô nhập liệu nhiều dòng để người dùng nhập văn bản dài.
        - Cách dùng: Tương tự TextField nhưng hỗ trợ nhiều dòng.
        
    3. **Progressbar**
        - Mô tả: Thanh hiển thị tiến độ (thường dùng khi tải hoặc xử lý dữ liệu).
        - Cách dùng: Đặt giá trị từ 0.0 đến 1.0 (0% đến 100%).
    
    ```java
    Button button = new Button("Nhấn tôi");
    button.setOnAction(e -> System.out.println("Nút đã được nhấn!"));
    ```
    
    ```java
    Label label = new Label("Đây là nhãn");
    ```
    
    ```java
    TextField textField = new TextField();
    textField.setPromptText("Nhập tên của bạn"); // Gợi ý trong ô
    ```
    
    ```java
    CheckBox checkBox = new CheckBox("Đồng ý?");
    checkBox.setOnAction(e -> {
        if (checkBox.isSelected()) {
            System.out.println("Đã chọn!");
        } else {
            System.out.println("Bỏ chọn!");
        }
    });
    ```
    
    ```java
    RadioButton radio1 = new RadioButton("Tùy chọn 1");
    RadioButton radio2 = new RadioButton("Tùy chọn 2");
    ToggleGroup group = new ToggleGroup();
    radio1.setToggleGroup(group);
    radio2.setToggleGroup(group);
    radio1.setSelected(true); // Mặc định chọn tùy chọn 1
    ```
    
    ```java
    ComboBox<String> comboBox = new ComboBox<>();
    comboBox.getItems().addAll("Mục 1", "Mục 2", "Mục 3");
    comboBox.setValue("Mục 1"); // Giá trị mặc định
    ```
    
    ```java
    ListView<String> listView = new ListView<>();
    listView.getItems().addAll("Item A", "Item B", "Item C");
    listView.getSelectionModel().select(0); // Chọn mục đầu tiên
    ```
    
    ```java
    Slider slider = new Slider(0, 100, 50); // Min: 0, Max: 100, Giá trị mặc định: 50
    slider.setShowTickLabels(true); // Hiển thị nhãn số
    ```
    
    ```java
    TextArea textArea = new TextArea();
    textArea.setPromptText("Nhập ghi chú...");
    textArea.setPrefRowCount(5); // Số dòng mặc định
    ```
    
    ```java
    ProgressBar progressBar = new ProgressBar(0.5); // Tiến độ 50%
    ```
    
- **Một số Container**
    
    
    1. **HBox (Horizontal Box)**
        - **Mục đích**: Sắp xếp các thành phần theo chiều ngang.
        
        ```java
        import javafx.application.Application;
        import javafx.scene.Scene;
        import javafx.scene.control.Button;
        import javafx.scene.layout.HBox;
        import javafx.stage.Stage;
        
        public class HBoxExample extends Application {
        
            @Override
            public void start(Stage primaryStage) {
                Button button1 = new Button("Button 1");
                Button button2 = new Button("Button 2");
                Button button3 = new Button("Button 3");
        
                HBox hbox = new HBox(10); // Khoảng cách giữa các thành phần là 10
                hbox.getChildren().addAll(button1, button2, button3);
        
                Scene scene = new Scene(hbox, 300, 50);
                primaryStage.setScene(scene);
                primaryStage.show();
            }
        
            public static void main(String[] args) {
                launch(args);
            }
        }
        ```
        
    
    1. **GridPane**
        - **Mục đích**: Sắp xếp các thành phần theo lưới.
        
        ```java
        import javafx.application.Application;
        import javafx.geometry.Insets;
        import javafx.scene.Scene;
        import javafx.scene.control.Button;
        import javafx.scene.control.Label;
        import javafx.scene.control.TextField;
        import javafx.scene.layout.GridPane;
        import javafx.stage.Stage;
        
        public class GridPaneExample extends Application {
        
            @Override
            public void start(Stage primaryStage) {
                GridPane gridPane = new GridPane();
                gridPane.setPadding(new Insets(10, 10, 10, 10)); // Khoảng cách viền
                gridPane.setVgap(5); // Khoảng cách giữa các hàng
                gridPane.setHgap(5); // Khoảng cách giữa các cột
        
                Label nameLabel = new Label("Name:");
                TextField nameField = new TextField();
                Label emailLabel = new Label("Email:");
                TextField emailField = new TextField();
                Button submitButton = new Button("Submit");
        
                gridPane.add(nameLabel, 0, 0);
                gridPane.add(nameField, 1, 0);
                gridPane.add(emailLabel, 0, 1);
                gridPane.add(emailField, 1, 1);
                gridPane.add(submitButton, 1, 2);
        
                Scene scene = new Scene(gridPane, 300, 150);
                primaryStage.setScene(scene);
                primaryStage.show();
            }
        
            public static void main(String[] args) {
                launch(args);
            }
        }
        ```
        
    
    1. **AnchorPane**
        - **Mục đích**: Sắp xếp các thành phần dựa trên neo.
        
        ```java
        import javafx.application.Application;
        import javafx.scene.Scene;
        import javafx.scene.control.Button;
        import javafx.scene.layout.AnchorPane;
        import javafx.stage.Stage;
        
        public class AnchorPaneExample extends Application {
        
            @Override
            public void start(Stage primaryStage) {
                AnchorPane anchorPane = new AnchorPane();
        
                Button button1 = new Button("Top Left");
                AnchorPane.setTopAnchor(button1, 10.0);
                AnchorPane.setLeftAnchor(button1, 10.0);
        
                Button button2 = new Button("Bottom Right");
                AnchorPane.setBottomAnchor(button2, 10.0);
                AnchorPane.setRightAnchor(button2, 10.0);
        
                anchorPane.getChildren().addAll(button1, button2);
        
                Scene scene = new Scene(anchorPane, 300, 200);
                primaryStage.setScene(scene);
                primaryStage.show();
            }
        
            public static void main(String[] args) {
                launch(args);
            }
        }
        ```
        
    
    1. **VBox (Vertical Box)**
        - **Mục đích**: Sắp xếp các thành phần theo chiều dọc.
        
        ```java
        import javafx.application.Application;
        import javafx.scene.Scene;
        import javafx.scene.control.Button;
        import javafx.scene.layout.VBox;
        import javafx.stage.Stage;
        
        public class VBoxExample extends Application {
        
            @Override
            public void start(Stage primaryStage) {
                Button button1 = new Button("Button 1");
                Button button2 = new Button("Button 2");
                Button button3 = new Button("Button 3");
        
                VBox vbox = new VBox(10); // Khoảng cách giữa các thành phần là 10
                vbox.getChildren().addAll(button1, button2, button3);
        
                Scene scene = new Scene(vbox, 200, 150);
                primaryStage.setScene(scene);
                primaryStage.show();
            }
        
            public static void main(String[] args) {
                launch(args);
            }
        }
        ```
        
        1. **FlowPane**
            - **Mục đích**: Sắp xếp các thành phần theo luồng.
            
            ```java
            import javafx.application.Application;
            import javafx.geometry.Orientation;
            import javafx.scene.Scene;
            import javafx.scene.control.Button;
            import javafx.scene.layout.FlowPane;
            import javafx.stage.Stage;
            
            public class FlowPaneExample extends Application {
            
                @Override
                public void start(Stage primaryStage) {
                    FlowPane flowPane = new FlowPane();
                    flowPane.setOrientation(Orientation.HORIZONTAL); // Sắp xếp theo chiều ngang
                    flowPane.setHgap(10); // Khoảng cách giữa các thành phần
            
                    for (int i = 1; i <= 10; i++) {
                        flowPane.getChildren().add(new Button("Button " + i));
                    }
            
                    Scene scene = new Scene(flowPane, 400, 100);
                    primaryStage.setScene(scene);
                    primaryStage.show();
                }
            
                public static void main(String[] args) {
                    launch(args);
                }
            }
            ```
            
        
        1. **BorderPane**
            - **Mục đích**: Sắp xếp các thành phần vào các vùng biên và trung tâm.
            
            ```java
            import javafx.application.Application;
            import javafx.scene.Scene;
            import javafx.scene.control.Button;
            import javafx.scene.layout.BorderPane;
            import javafx.stage.Stage;
            
            public class BorderPaneExample extends Application {
            
                @Override
                public void start(Stage primaryStage) {
                    BorderPane borderPane = new BorderPane();
            
                    Button topButton = new Button("Top");
                    Button bottomButton = new Button("Bottom");
                    Button leftButton = new Button("Left");
                    Button rightButton = new Button("Right");
                    Button centerButton = new Button("Center");
            
                    borderPane.setTop(topButton);
                    borderPane.setBottom(bottomButton);
                    borderPane.setLeft(leftButton);
                    borderPane.setRight(rightButton);
                    borderPane.setCenter(centerButton);
            
                    Scene scene = new Scene(borderPane, 400, 300);
                    primaryStage.setScene(scene);
                    primaryStage.show();
                }
            
                public static void main(String[] args) {
                    launch(args);
                }
            }
            ```
            
- **SceneBuilder và FXML**
    
    
    **SceneBuilder**
    
    - Scene Builder: Là một công cụ đồ họa (GUI) giúp bạn thiết kế giao diện JavaFX bằng cách kéo-thả các thành phần (như button, label, text field) mà không cần viết mã hoàn toàn từ đầu.
    - Ưu điểm: Dễ hình dung bố cục, tiết kiệm thời gian, và tạo ra file FXML để kết nối với mã Java.
    
    **FXML**
    
    - FXML: Là một định dạng dựa trên XML, dùng để mô tả cấu trúc giao diện trong JavaFX. Thay vì viết mã Java để tạo từng thành phần và bố cục, bạn dùng FXML để khai báo chúng, rồi liên kết với logic trong Java.
    - Lợi ích: Tách biệt giao diện (UI) và logic, giúp mã dễ bảo trì hơn.
