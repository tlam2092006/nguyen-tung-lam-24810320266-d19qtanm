# nguyen-tung-lam-24810320266-d19qtanm
I. PHẦN LÝ THUYẾT & CÂU HỎI NGẮN 

Câu 1: Trình bày sự khác nhau giữa Value Types (Kiểu giá trị) và Reference Types (Kiểu tham chiếu) trong C# về cơ chế lưu trữ vùng nhớ (Stack vs Heap). 

Value Types (Kiểu giá trị): 

Cơ chế lưu trữ: Thường được lưu trữ trực tiếp trên Stack (hoặc nằm trong một đối tượng trên Heap nếu nó là biến thành viên của một kiểu tham chiếu). 

Đặc điểm: Khi gán một biến kiểu giá trị cho một biến khác, toàn bộ dữ liệu được sao chép sang ô nhớ mới. Thay đổi giá trị ở biến này không ảnh hưởng đến biến kia. 

Ví dụ: Các kiểu số nguyên (int, float, double), bool, struct, enum. 

Reference Types (Kiểu tham chiếu): 

Cơ chế lưu trữ: Biến lưu trữ trên Stack thực chất chỉ là một con trỏ (địa chỉ) trỏ đến vùng dữ liệu thực sự được cấp phát trên Heap. 

Đặc điểm: Khi gán một biến kiểu tham chiếu cho biến khác, chỉ có địa chỉ (tham chiếu) được sao chép; cả hai biến cùng trỏ đến một vùng dữ liệu duy nhất trên Heap. Thay đổi dữ liệu qua một biến sẽ ảnh hưởng đến biến còn lại. 

Ví dụ: class, interface, delegate, string, object. 

Câu 2: Tính năng Init-only Properties (init) trong C# 9/10 khác gì so với thuộc tính có set thông thường? Nêu trường hợp sử dụng thực tế. 

Sự khác biệt: 

Thuộc tính với set thông thường: Cho phép thay đổi giá trị của thuộc tính bất cứ lúc nào trong vòng đời của đối tượng (mutable) sau khi khởi tạo. 

Thuộc tính init: Chỉ cho phép gán giá trị một lần duy nhất trong quá trình khởi tạo đối tượng (ví dụ: thông qua bộ khởi tạo đối tượng - object initializer). Sau khi đối tượng đã được khởi tạo xong, thuộc tính này trở thành read-only (bất biến), không thể thay đổi giá trị nữa. 

Trường hợp sử dụng thực tế: 

Dùng trong các đối tượng bất biến (Immutable Objects), các DTO (Data Transfer Objects) hoặc các record cấu hình. Giúp đảm bảo tính toàn vẹn dữ liệu, tránh việc vô tình làm thay đổi trạng thái của đối tượng sau khi nó đã được khởi tạo thành công. 

Câu 3: Phân tích sự khác nhau giữa phương thức virtual ở lớp cha và phương thức override ở lớp con khi triển khai tính Đa hình (Polymorphism). 

Phương thức virtual (ở lớp cha): 

Dùng để khai báo một phương thức mà lớp cha cung cấp sẵn một implementation mặc định, nhưng cho phép các lớp con ghi đè (override) lại hành vi đó nếu muốn. 

Phương thức override (ở lớp con):
Dùng ở lớp con để viết lại hoặc thay thế hoàn toàn implementation của phương thức virtual (hoặc abstract) đã được định nghĩa ở lớp cha. 

Cơ chế đa hình: Khi gọi phương thức thông qua tham chiếu kiểu lớp cha nhưng trỏ đến đối tượng của lớp con, phiên bản phương thức được thực thi sẽ là phương thức đã bị override ở lớp con (Dynamic Binding). 

Câu 4: Tại sao một thành phần được khai báo là static trong Lớp (Class) lại không thể truy xuất thông qua một thể hiện (Object Instance) được tạo bằng toán tử new? 

Nguyên nhân: 

Các thành phần static (thuộc tính hoặc phương thức tĩnh) thuộc về chính lớp đó (Class-level), được cấp phát bộ nhớ một lần duy nhất khi lớp được nạp vào bộ nhớ (AppDomain), chứ không thuộc về bất kỳ đối tượng cụ thể nào được tạo ra từ toán tử new (Instance-level). 

Do đó, các thể hiện (objects) không mang bản sao của các thành phần static. Trình biên dịch C# không cho phép truy cập thành phần static thông qua tên biến thể hiện nhằm tránh nhầm lẫn về mặt ngữ nghĩa và ép buộc lập trình viên phải truy cập trực tiếp thông qua tên của Lớp (ví dụ: TenLop.TenThanhPhanStatic).
