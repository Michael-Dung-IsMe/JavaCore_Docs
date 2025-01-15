# BUỔI 6. INTERFACE VÀ TRỪU TƯỢNG

<aside>
ℹ️

Sách: JavaCore

https://gemini.google.com/

https://rikkei.edu.vn/abstract-class-trong-java/

https://gpcoder.com/2295-abstract-class-va-interface-trong-java/

https://www.javatpoint.com/interface-in-java

https://www.geeksforgeeks.org/difference-between-abstract-class-and-interface-in-java/

</aside>

### 1. Định nghĩa Interface và Abstract class

- **1.1. Abstract class là gì?**
    
    
    - **Abstract class** (Lớp trừu tượng) được sử dụng để định nghĩa các phương thức trừu tượng mà các lớp con cần triển khai.
    - Chứa **ít nhất 1** phương thức trừu tượng (khai báo với keyword **`abstract`**)
    - Một lớp kế thừa từ lớp trừu tượng không cần phải implement non-abstract methods, nhưng các abstract methods thì bắt buộc phải **`override`**. Trừ khi subclass cũng là abstract.
    - *Mục đích sử dụng*
        - Cung cấp một mẫu (**template**) để triển khai quá trình trừu tượng hóa = giấu đi chi tiết cài đặt.
        - Giảm sự phụ thuộc (**Loose Coupling**) giữa các thành phần của chương trình    → Tăng tính linh hoạt + dễ bảo trì
        - Tái sử dụng mã (**Code Reusability**) → Tiết kiệm thời gian
        - Sự hỗ trợ của phương thức động (**Dynamic Resolution**) → Giải quyết nhiều vấn đề chỉ với 1 phương thức trừu tượng.
    
    ![*Đặc điểm của Abstract Class trong Java*](image.png)
    
    *Đặc điểm của Abstract Class trong Java*
    
    - *Lưu ý*
        - Nó không thể được khởi tạo.
        - Nó có thể có các phương thức trừu tượng và phương thức không trừu tượng.
        - Nó có thể có các phương thức khởi tạo (constructor) và phương thức tĩnh (static method).
        - Nó có thể có các phương thức cuối cùng (final) được dùng để buộc lớp con không được thay đổi nội dung của phương thức.
- **1.2. Các thao tác cơ bản với Abstract class?**
    
    
    ```java
    <Access_Modifier> abstract class <Class_Name> {
    	//Data_Members; 
    	//Statements;
    	//Methods (Abstract/non-abstract);
    }
    
    //ex
    public abstract class Shape {
        private String color = "red";
        public Shape() { }
        public abstract void draw();
        public String getColor() {
            return color;
        }
    }
    ```
    
    ```java
    <modifier> abstract <return_type> <method_name>(<parameter_list>);
    //ex
    public abstract void draw();
    ```
    
    ```java
    @Override
    <modifier> <return_type> <method_name>(<parameter_list>) {
        // code implementation
    }
    //ex
    public class Rectangle extends Shape {
    	  @Override
    	  public void draw() {
    	      System.out.println("Draw " + super.getColor() + " rectangle");
    	  }
    }
    
    public class Circle extends Shape {
        @Override
        public void draw() {
            System.out.println("Draw " + super.getColor() + " circle");
        }
    }
    ```
    
- **1.3. Interface là gì?**
    - **Interface** (Giao diện) là một bản thiết kế hoặc một "hợp đồng" mà các lớp (class) phải tuân theo. Nó định nghĩa một tập các phương thức (method) mà một lớp phải hiện thực (implement) nếu nó muốn "tuân thủ" interface đó.
    - **Interface** chỉ chứa khai báo phương thức (method signature), không chứa phần thân (body) của phương thức.
    
    - *Đặc điểm*
        - **Tính trừu tượng (Abstraction):** Interface thể hiện tính trừu tượng cao, chỉ định nghĩa "cái gì" mà không định nghĩa "như thế nào". Nó ẩn đi cách thức thực hiện cụ thể của các phương thức
        - **Đa kế thừa (Multiple Inheritance):** Trong Java, một lớp chỉ có thể kế thừa trực tiếp từ một lớp cha (single inheritance), nhưng có thể hiện thực nhiều interface, giúp đạt được hiệu quả tương tự như đa kế thừa.
        - **Tính ràng buộc (Contract):** Bất kỳ lớp nào hiện thực một interface đều phải cung cấp hiện thực cho tất cả các phương thức được định nghĩa trong interface đó.
        - **Interface** luôn luôn có modifier là: **`public interface`**, cho dù bạn có khai báo rõ hay không.
        - Nếu có các trường (field) thì chúng đều là: **`public static final`**, cho dù bạn có khai báo rõ hay không.
        - Các method của nó đều là method trừu tượng, và đều có modifier là: **`public abstract`**, cho dù bạn có khai báo hay không.
    
    - *So sánh giữa interface và class*
        
        
        |  |
        | --- |
        |  |
        |  |
    
- **1.4. Các thao tác với Inteface?**
    - *Khai báo một interface*
        
        ```java
        public interface myInterface {
            // Khai báo các phương thức trừu tượng
            void phuongThuc1();
            int phuongThuc2(String thamSo);
        
            // Khai báo hằng số
            int HANG_SO = 10; // Tương đương public static final int HANG_SO = 10;
        }
        ```
        
    - *Hiện thực một interface*
        - Một lớp hiện thực một interface bằng cách sử dụng từ khóa `implements`. Lớp đó phải cung cấp hiện thực (body) cho tất cả các phương thức được khai báo trong interface.
        - Nếu có nhiều hơn một giao diện được thực thi, các tên sẽ được ngăn cách với nhau bởi một dấu phẩy.
        
        ```java
        class TenLop implements TenInterface {
            @Override
            public void phuongThuc1() {
                // Hiện thực của phuongThuc1
                System.out.println("Đã hiện thực phuongThuc1");
            }
        
            @Override
            public int phuongThuc2(String thamSo) {
                // Hiện thực của phuongThuc2
                System.out.println("Đã hiện thực phuongThuc2 với tham số: " + thamSo);
                return 0;
            }
        }
        ```
        
    - 
    - **Lưu ý**
        1. Tất cả phương thức trong các giao diện này đều phải là kiểu **`public`** 
        2. Các phương thức được định nghĩa trong một lớp mà lớp này hiện thực giao diện.

### 2. So sánh Abstract Class và Interface

|  | Lớp trừu tượng (Abstract Class) | Interface |
| --- | --- | --- |
| Tính trừu tượng | < 100% | 100% |
| Phương thức | abstract và non-abstract | Mặc định là abstract; Từ Java 8 có thêm default, static, private methods |
| Đa kế thừa | Không hỗ trợ | Có hỗ trợ |
| Kế thừa | Có thể kế thừa (extend) từ một class và hiện được nhiều giao diện (Sử dụng từ khóa **`extends`**) | Chỉ có thể kế thừa với một giao diện khác (Sử dụng từ khóa **`implements`**) |
| Biến số | Có thể có các biến thành viên (**`final`**, **`non-final`**, **`static`**, **`non-static`)** | Biến ngầm định là **`public`**, **`static`** và **`final`** (hằng số) |
|  | Có thể có các phương thức static, main, constructor | Không thể có phương thức static, main, hoặc constructor |
| Trình triển khai | Có thể cung cấp trình triển khai của Interface | Không cung cấp trình triển khai cụ thể của lớp abstract |

### 3. Khi nào dùng Abstract Class, Interface

- Sử dụng lớp trừu tượng (**Abstract Class)** khi:
    - Khi ta cần định nghĩa một khuôn mẫu chung cho một nhóm các lớp có chung một số đặc điểm.
    - Khi bạn muốn một số phương thức phải được hiện thực bởi các lớp con.
    - Khi bạn muốn chia sẻ code giữa các lớp con thông qua các phương thức bình thường trong lớp cha.

- Sử dụng giao diện (**Interface**) khi:
    - khi bạn muốn tạo dựng một bộ khung chuẩn gồm các chức năng (method/ function) mà tất cả module/ project cần phải có.
    - Khi bạn muốn đạt được tính đa kế thừa trong Java.
    - Khi bạn muốn tách biệt phần giao diện (**interface**) và phần hiện thực (**implementation**)

### 4. Tính trừu tượng (Abstraction)

- Tính trừu tượng (**Abstraction**) trong Java là khả năng mô tả và tập trung vào các đặc tính quan trọng của một đối tượng, bỏ qua các chi tiết không quan trọng, và tạo ra các lớp, phương thức và thuộc tính trừu tượng để thể hiện các tính năng của đối tượng đó.
- Nó giúp đơn giản hóa việc tương tác với đối tượng và giảm độ phức tạp của hệ thống.
- Tính trừu tượng giúp bạn tập trung vào những cốt lõi cần thiết của đối tượng thay vì quan tâm đến cách nó thực hiện.
- Tính trừu tượng trong Java được thực hiện thông qua các cơ chế:
    1. Lớp trừu tượng (**Abstract class**)
    2. Giao diện (**Interface**)

### 5. Enum

- **5.1. Khái niệm enum**
    - **enum** (Viết tắt của **enumeration**) là một kiểu dữ liệu đặc biệt được sử dụng để định nghĩa một tập hợp các hằng số được đặt tên.
    - **enum** có thể được định nghĩa bên trong hoặc bên ngoài một lớp, vì nó tương tự như lớp trong java.
    - Một **enum** có thể chứa các trường, phương thức và constructor.
    - Vì các giá trị của Enum là các hằng số, nên tên của các trường kiểu enum thường là các chữ cái hoa (VD: Các ngày trong tuần - MONDAY, TUESDAY…; Các mùa trong năm - SPRING, SUMMER…)
- **5.2. Các thao tác với enum**
    - **Khai báo enum (Sử dụng từ khóa `enum`)**
        
        
        *Enum được định nghĩa trong một lớp*
        
        ```java
        public class EnumExample {
            enum WeekDay {
                MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
            }
         
            public static void main(String[] args) {
                WeekDay d = WeekDay.MONDAY;
                    System.out.println(d);
            }
        }
        
        //Output
        MONDAY
        ```
        
        *Enum được định nghĩa bên ngoài một lớp*
        
        - **enum** định nghĩa bên ngoài một lớp không thể dùng access modifier public, protected, private.
        
        ```java
        enum WeekDay { // Không được khai báo access modifier (sử dụng default)
            MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
        }
         
        public class EnumExample {
            public static void main(String[] args) {
                WeekDay d = WeekDay.MONDAY;
                    System.out.println(d);
            }
        }
        //Output
        MONDAY
        ```
        
    - **Duyệt các phần tử trong enum**
        
        Có thể duyệt thông qua phương thức **`values()`**. Khi được biên dịch, trình biên dịch trong Java sẽ tự động thêm phương thức **`values()`** vào **enum** và trả về một mảng chứa tất cả các giá trị của **enum**
        
        ```java
        public class EnumExample {
            enum WeekDay {
                MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
            }
         
            public static void main(String[] args) {
                for (WeekDay d : WeekDay.values()) {
                    System.out.println(d);
                }
            }
        }
        ```
        
        > **Output:**
        > 
        > 
        > ```java
        > MONDAY
        > TUESDAY
        > WEDNESDAY
        > THURSDAY
        > FRIDAY
        > SATURDAY
        > SUNDAY
        > ```
        > 
    - **Khởi tạo giá trị đặc biệt cho hằng số enum**
        - Các hằng số enum có giá trị ban đầu bắt đầu từ 0, 1, 2, 3, … Nhưng ta có thể khởi tạo giá trị cụ thể cho các hằng số enum bằng cách định nghĩa các trường và constructor.
        - Constructor của enum luôn là **`private`** , nếu không khai báo **`private`**, Java sẽ tự hiểu là **`private`**
        - Các phần tử trong enum luôn là **`static final`**, và có thể viết một **`static`** method trong enum
        
        ```java
        public class EnumExample3 {
            enum WeekDay {
                // Khởi tạo các phần tử từ construnctor
                MONDAY(2), TUESDAY(3), WEDNESDAY(4), THURSDAY(5), FRIDAY(7), SATURDAY(7), SUNDAY(1);
                private int value;
                // constructor này chỉ dùng trong nội bộ Enum
                WeekDay(int value) {
                    this.value = value;
                }
                // Có thể viết một static method lấy ra WeekDay theo value.
                public static WeekDay getWeekDayByValue(int value) {
                    for (WeekDay d : WeekDay.values()) {
                        if(d.value == value) {  return d;  }
                    }
                    return null;
                }
            }
         
            public static void main(String[] args) {
                for(WeekDay d : WeekDay.values()) {
                    System.out.println(d + " = " + d.value);
                }
                // Sử dụng static method của enum
                WeekDay d = WeekDay.getWeekDayByValue(3);
                System.out.println("value 3 is " + d);
            }
        }
        ```
        
        > **Output:**
        > 
        > 
        > ```java
        > MONDAY = 2
        > TUESDAY = 3
        > WEDNESDAY = 4
        > THURSDAY = 5
        > FRIDAY = 7
        > SATURDAY = 7
        > SUNDAY = 1
        > value 3 is TUESDAY
        > ```
        > 
    - **So sánh các phần tử java enum**
        
        Sử dụng toán tử == hoặc **`equals()`** 
        
        ```java
        public class EnumExample {
            enum WeekDay {
                MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
            }
         
            public static void main(String[] args) {
                WeekDay today = WeekDay.SUNDAY;
         
                // use equal() method
                if (today.equals(WeekDay.SUNDAY)) {
                    System.out.println("Today is holiday");
                } else {
                    System.out.println("Today is working day");
                }
         
                // use == operator
                if (today == WeekDay.SUNDAY) {
                    System.out.println("Today is holiday");
                } else {
                    System.out.println("Today is working day");
                }
            }
        }
        ```
        
    - **Sử dụng như tham số trong câu lệnh `switch`**
        
        ```java
        public class EnumExample {
            enum WeekDay {
                MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
            }
         
            public static void main(String[] args) {
                WeekDay today = WeekDay.SUNDAY;
         
                switch (today) {
                case MONDAY:
                    System.out.println("Today is working day");
                    break;
                case SATURDAY:
                case SUNDAY:
                    System.out.println("Today is holiday");
                    break;
                default:
                    System.out.println(today);
                }
            }
        }
        ```
        
    - **Ghi đè phương thức (Overriding Method)**
        
        Do **enum** cũng là một kiểu dữ liệu được kết thừa từ lớp **Object,** nên chúng ta có thể ghi đè method **`toString()`** của lớp **Object**.
        
        ```java
        public class EnumExample3 {
            enum WeekDay {
                MONDAY(2), TUESDAY(3), WEDNESDAY(4), THURSDAY(5), FRIDAY(7), SATURDAY(7), SUNDAY(1);
                private int value;
                WeekDay(int value) {  this.value = value;  }
         
                @Override
                public String toString() {
                    if (value == 1) { // other way: if (this == SUNDAY) {
                        return "Today is holiday";
                    } else {
                        return "Today is working day";
                    }
                }
            }
         
            public static void main(String[] args) {
                WeekDay today = WeekDay.SUNDAY;
                System.out.println(today);
                System.out.println(today.toString());
            }
        }
        ```
