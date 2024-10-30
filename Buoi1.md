## BUỔI 1: WELCOME TO JAVA

### I. Giới thiệu về Java

1. Ngôn ngữ Java là gì?
    - Java là một trong những ngôn ngữ lập trình hướng đối tượng được thiết kế để chạy trên nhiều nền tảng khác nhau mà không cần phải chỉnh sửa mã nguồn.
    - Ngôn ngữ Java được sử dụng phổ biến trong phát triển phần mềm, trang web, game hay ứng dụng trên các thiết bị di động.
    - Nó được phát triển bởi Sun Microsystems và hiện tại thuộc về Oracle.
2. Lý do ra đời
    - Java ra đời nhằm giải quyết vấn đề tương thích đa nền tảng và cung cấp một môi trường phát triển đơn giản, bảo mật, và mạnh mẽ cho các ứng dụng mạng.
3. Cách hoạt động
    - Được thiết kế dựa trên tiêu chí: ***“Write Once, Run Anywhere”***  (mã nguồn Java có thể chạy trên mọi nền tảng có hỗ trợ Java Virtual Machine (**JVM**) ⇒ NNLT đa nền tảng
    - Khi ta viết một chương trình Java, quy trình hoạt động có thể chia làm 3 bước chính:
        1. **Viết mã nguồn**: Lập trình viên viết mã nguồn vào file `.java`
        2. **Biên dịch mã nguồn**: Được biên dịch bởi Java Compiler thành ***bytecode*** (tệp `.class`)
            - ***bytecode:*** là mã trung gian mà trình biên dịch Java tạo ra sau khi biên dịch mã nguồn, có thể chạy trên bất kỳ hệ điều hành nào có **JVM**
        3. **Chạy chương trình**: JVM dịch bytecode này thành mã máy (machine code) để hệ điều hành và phần cứng cụ thể có thể hiểu và thực thi chương trình.

### II. Cấu trúc một chương trình Java
    ```java
    package <package_name>; 
    
    import <other_package>;
    
    public class ClassName {
      <Variables (also known as fields)>;
    
      <constructor method(s)>;
    
      <other methods>;
    }
    ```
    
6. Syntax cơ bản trong code
    - Khai báo biến nguyên thủy: `DataType varName [ = value] [, varName2] [ = value2]...;`
        - **DataType**: kiểu dữ liệu của biến
        - **varName**: Tên biến
