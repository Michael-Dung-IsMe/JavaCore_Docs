## Preparation

### Giới thiệu về Java

1. Ngôn ngữ Java là gì?
    - Java là một trong những ngôn ngữ lập trình hướng đối tượng, thuộc top phổ biến nhất trên thế giới.
    - Ngôn ngữ Java được sử dụng phổ biến trong phát triển phần mềm, trang web, game hay ứng dụng trên các thiết bị di động.
2. Lịch sử ra đời
    - Java được khởi đầu bởi James Gosling và bạn đồng nghiệp ở Sun MicroSystem năm 1991.
    - Mục đích ra đời: **viết phần mềm cho các sản phẩm gia dụng (tên là Oak)**
3. Cách hoạt động
    - Được thiết kế dựa trên tiêu chí: ***“Write Once, Run Anywhere”***  (mã nguồn Java có thể chạy trên mọi nền tảng có hỗ trợ Java Virtual Machine (**JVM**) ⇒ NNLT đa nền tảng
    - Khi ta viết một chương trình Java, quy trình hoạt động có thể chia làm 3 bước chính:
        1. **Viết mã nguồn**: Lập trình viên viết mã nguồn vào file `.java`
        2. **Biên dịch mã nguồn**: Được biên dịch bởi Java Compiler thành ***bytecode*** (tệp `.class`)
            - ***bytecode:*** là mã trung gian mà trình biên dịch Java tạo ra sau khi biên dịch mã nguồn, có thể chạy trên bất kỳ hệ điều hành nào có **JVM**
        3. **Chạy chương trình**: JVM dịch bytecode này thành mã máy (machine code) để hệ điều hành và phần cứng cụ thể có thể hiểu và thực thi chương trình.
4. Cấu trúc một chương trình Java
    
    
    - Thường chia làm 6 phần:
        - **package (Gói)**: mô tả không gian tên có chứa các lớp của Java, sử dụng ký tự thường và dấu chấm để định nghĩa tên.
        - **import**: được sử dụng nhằm xác định các class / package được sử dụng trong lớp này.
        - **class**:  Được dùng để định nghĩa lớp của Java. Nó đứng trước khai báo tên lớp của Java
        - **Variables (biến/trường)**: Cũng có 1 số tài liệu gọi là thuộc tính trực thuộc lớp. Nó chứa thông tin cụ thể liên quan tới các đối tượng là thể hiện của lớp.
        - **Methods (Phương thức/hàm chứa các hđ thực thi)**: nội dung của phương thức chính là các đoạn mã thực thi của chính phương thức này.
        - **Constructors:** Là hàm khởi tạo của đối tượng.
    
    ```java
    package <package_name>;
    
    import <other_package>;
    
    public class ClassName {
      <Variables (also known as fields)>;
    
      <constructor method(s)>;
    
      <other methods>;
    }
    ```
    
5. Syntax cơ bản trong code
    - Khai báo biến nguyên thủy: `DataType varName [ = value] [, varName2] [ = value2]...;`
        - **DataType**: kiểu dữ liệu của biến
        - **varName**: Tên biến
