---
date: 2025-02-16
draft: true
status: Doing
title: "Cấu trúc dữ liệu ngăn xếp"
description: 
author: PhDoanh
authorlink: https://github.com/PhDoanh
tags: 
  - dsa
  - coding
  - cpp
  - competitive
  - "data-structure"
  - stack
aliases:
  - "stack"
cssclasses:
  - img
  - btn
---
%% ĐỊNH DẠNG TÊN FILE: "tên-cấu-trúc-dữ-liệu-hoặc-thuật-toán" | VD: binary-search %%

%% <figure style="text-align: center; margin: 20px auto;">
  <img 
    src="images/stack.png"
    alt="Cấu trúc dữ liệu ngăn xếp" 
    style="
      width: 90%;
      height: auto;
      display: block;
      margin: 0 auto;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    "
  >
  <figcaption style="
    font-style: italic;
    color: #666;
    margin-top: 10px;
    font-size: 1em;
    padding: 0 10px;
  ">
    <em>dsa_name</em>
  </figcaption>
</figure> %%

# 👀 Giới thiệu về Stack
Ngăn xếp (Stack) là một cấu trúc dữ liệu có cách hoạt động theo nguyên tắc **LIFO (Last In, First Out)**, tức là phần tử được thêm vào sau cùng sẽ được lấy ra trước. Nó có hai thao tác chính:

- **Push**: Thêm một phần tử vào đỉnh ngăn xếp.
- **Pop**: Loại bỏ phần tử ở đỉnh ngăn xếp.  

Ngoài ra, có thể có các thao tác bổ sung như **Peek (Top)** để xem phần tử ở đỉnh mà không loại bỏ nó, và **isEmpty** để kiểm tra xem ngăn xếp có rỗng không. Ngăn xếp có thể được triển khai bằng **mảng (Array)** hoặc **danh sách liên kết (Linked List)**.

> [!info] Ứng dụng
> - **Trong xử lý biểu thức toán học và ngôn ngữ lập trình**: Chuyển đổi giữa các biểu thức **Infix, Postfix, Prefix**. Thực thi biểu thức hậu tố (Reverse Polish Notation – RPN).
> - **Quản lý lời gọi hàm trong chương trình**: Khi một hàm được gọi, thông tin trạng thái (như biến cục bộ, địa chỉ trả về) được lưu trên ngăn xếp gọi hàm. Khi hàm kết thúc, thông tin được lấy ra khỏi ngăn xếp.
> - **Cơ chế "Undo" và "Redo" trong phần mềm**: Khi thực hiện một thao tác chỉnh sửa, trạng thái trước đó được lưu vào ngăn xếp. Khi nhấn "Undo", trạng thái được lấy ra từ ngăn xếp và áp dụng.
> - **Duyệt cây (Tree Traversal) và đồ thị (Graph Traversal)**: Trong thuật toán **Duyệt theo chiều sâu (DFS - Depth First Search)**, ngăn xếp được sử dụng để lưu các đỉnh đang chờ duyệt.
> - **Quản lý bộ nhớ trong hệ điều hành**: Ngăn xếp được sử dụng để quản lý bộ nhớ stack frame của từng tiến trình.
> - **Xử lý dấu ngoặc trong biểu thức**: Dùng ngăn xếp để kiểm tra tính hợp lệ của dấu ngoặc trong một chuỗi, ví dụ: `({[ ]})`

> [!check] Ưu điểm
> - **Tốc độ truy xuất nhanh**: Các thao tác `Push` và `Pop` có thời gian thực thi **O(1)** trong cả hai cách triển khai bằng mảng hoặc danh sách liên kết.  
> - **Dễ triển khai**: Cấu trúc đơn giản, chỉ cần quan tâm đến phần tử ở đỉnh.  
> - **Quản lý bộ nhớ hiệu quả**: Trong một số trường hợp như gọi hàm đệ quy, ngăn xếp giúp tránh lãng phí bộ nhớ.

> [!missing] Nhược điểm
> - **Không truy cập ngẫu nhiên được**: Chỉ có thể thao tác với phần tử ở đỉnh, không thể truy cập trực tiếp phần tử ở giữa như trong mảng hoặc danh sách liên kết.  
> - **Giới hạn kích thước (khi dùng mảng)**: Nếu dùng mảng để cài đặt ngăn xếp, phải xác định trước kích thước, có thể gây lãng phí bộ nhớ hoặc tràn ngăn xếp.  
> - **Dễ bị lỗi tràn ngăn xếp (Stack Overflow)**: Khi gọi đệ quy quá sâu mà không có điều kiện dừng tốt, chương trình có thể bị lỗi tràn stack.

---

# 🛠️ Khai triển Stack trong C++

> [!info] Lưu ý
> Việc triển khai ngăn xếp các phần tử có kiểu dữ liệu khác bên dưới hoàn toàn tương tự!

## Khai triển bằng mảng

> [!check] Ưu điểm
> - **Truy cập nhanh hơn danh sách liên kết**: Mảng có địa chỉ liên tiếp trong bộ nhớ, giúp truy cập nhanh hơn so với danh sách liên kết (do danh sách liên kết cần truy xuất con trỏ).
> - **Bộ nhớ liên tục, tiết kiệm không gian cho con trỏ**: Do không sử dụng con trỏ như danh sách liên kết, mảng tiết kiệm được bộ nhớ. Mỗi phần tử chỉ cần lưu giá trị, không cần lưu thêm con trỏ `next`
> - **Dễ cài đặt và quản lý**: Việc thêm (`Push`) và xóa (`Pop`) phần tử chỉ cần thao tác với chỉ số (`top`), không cần cấp phát bộ nhớ động như danh sách liên kết
> - **Ít rủi ro lỗi bộ nhớ**: Không cần cấp phát hoặc giải phóng bộ nhớ động, tránh lỗi như rò rỉ bộ nhớ (memory leak) hoặc lỗi sử dụng con trỏ `nullptr`.

> [!missing] Nhược điểm
> - **Kích thước cố định, không co giãn linh hoạt**: Nếu cần một ngăn xếp có kích thước thay đổi liên tục, việc sử dụng danh sách liên kết sẽ hiệu quả hơn.
> - **Lãng phí bộ nhớ nếu không sử dụng hết phần tử**
> - **Chi phí cao khi mở rộng**: Nếu cần mở rộng ngăn xếp, phải tạo một mảng mới có kích thước lớn hơn, sao chép dữ liệu từ mảng cũ sang, rồi giải phóng mảng cũ. Điều này tốn tài nguyên

### Định nghĩa ngăn xếp

```cpp {1,4,9-13}
const int MAX = 1000;

class Stack { 
	int top; 

public: 
    int arr[MAX];

    Stack() { top = -1; } 
    bool Push(int e); 
    int Pop(); 
    int Top(); 
    bool Empty(); 
}; 
```

> [!explain]- Giải thích code
> Dòng 1: Số phần tử tối đa mà ngăn xếp có thể chứa (kích thước ngăn xếp)
> Dòng 4: Vị trí của phần tử ở đỉnh ngăn xếp
> Dòng 9: Hàm tạo khởi tạo ngăn xếp với `top = -1` để ngầm hiểu nó rỗng
> Dòng 10: Hàm thêm phần tử `e` vào đỉnh ngăn xếp
> Dòng 11: Hàm xóa phần tử khỏi đỉnh ngăn xếp
> Dòng 12: Hàm trả về phần tử ở đỉnh ngăn xếp
> Dòng 13: Hàm kiểm tra ngăn xếp rỗng hay không

### Thao tác thêm phần tử

> [!caution]- Nội dung đang hoàn thiện
> Quá trình xây dựng nội dung này có thể mất nhiều thời gian ⌛, nhưng bạn có thể thúc đẩy nó bằng cách tham gia [[article-collaboration-guide|cộng tác bài viết]] 🤝
> 
> **Rất mong sự thông cảm của các bạn 🙏**

%%

Thao tác này sẽ kiểm tra ngăn xếp còn có thể thêm được nữa hay không rồi mới thêm 1 phần tử mới vào đỉnh đầu ngăn xếp

```cpp {}

```

> [!explain]- Giải thích code
> Dòng 3-4: Thao tác sẽ không được thực hiện nếu ngăn xếp đầy
> Dòng 6-7: Tăng vị trí `top` lên 1 đơn vị và gán phần tử tại vị trí đó thành `e`

%%

### Thao tác xóa phần tử

> [!caution]- Nội dung đang hoàn thiện
> Quá trình xây dựng nội dung này có thể mất nhiều thời gian ⌛, nhưng bạn có thể thúc đẩy nó bằng cách tham gia [[article-collaboration-guide|cộng tác bài viết]] 🤝
> 
> **Rất mong sự thông cảm của các bạn 🙏**

%%

Thao tác này sẽ xóa đi phần tử ở đỉnh ngăn xếp và trả về phần tử đã xóa

```cpp {}

```

> [!explain]- Giải thích code
> Dòng 2-3: Thao tác sẽ không được thực hiện nếu ngăn xếp rỗng
> Dòng 5-6: Lấy phần tử được xóa ra khỏi ngăn xếp, đồng thời giảm `top` đi 1 đơn vị 

%%

### Thao tác lấy phần tử ở đỉnh

> [!caution]- Nội dung đang hoàn thiện
> Quá trình xây dựng nội dung này có thể mất nhiều thời gian ⌛, nhưng bạn có thể thúc đẩy nó bằng cách tham gia [[article-collaboration-guide|cộng tác bài viết]] 🤝
> 
> **Rất mong sự thông cảm của các bạn 🙏**

%%

```cpp {}

```

> [!explain]- Giải thích code
> Dòng 1: 

%%

### Thao tác kiểm tra rỗng hay không

> [!caution]- Nội dung đang hoàn thiện
> Quá trình xây dựng nội dung này có thể mất nhiều thời gian ⌛, nhưng bạn có thể thúc đẩy nó bằng cách tham gia [[article-collaboration-guide|cộng tác bài viết]] 🤝
> 
> **Rất mong sự thông cảm của các bạn 🙏**

%%

```cpp {}

```

> [!explain]- Giải thích code
> Dòng 1: 

%%

## Khai triển bằng danh sách liên kết

> [!caution]- Nội dung đang hoàn thiện
> Quá trình xây dựng nội dung này có thể mất nhiều thời gian ⌛, nhưng bạn có thể thúc đẩy nó bằng cách tham gia [[article-collaboration-guide|cộng tác bài viết]] 🤝
> 
> **Rất mong sự thông cảm của các bạn 🙏**

---

# ✨ Stack trong thư viện chuẩn C++
**Stack trong STL (Standard Template Library) của C++** là một cấu trúc dữ liệu hoạt động theo nguyên tắc **LIFO (Last In, First Out)**, được cung cấp trong thư viện `<stack>`. Nó hỗ trợ các thao tác cơ bản như `push()`, `pop()`, `top()`, `empty()` và `size()`, giúp quản lý dữ liệu một cách tiện lợi mà không cần tự cài đặt. Stack STL có thể được triển khai dựa trên `deque` (mặc định), `vector` hoặc `list`, tùy vào yêu cầu về hiệu suất và bộ nhớ. Dưới đây là chương trình mẫu sử dụng các hàm cơ bản trên:

```cpp {}
#include <iostream>
#include <stack>

int main() {
    std::stack<int> s; // Tạo một ngăn xếp lưu số nguyên

    // 1. push(): Thêm phần tử vào đỉnh stack
    s.push(10);
    s.push(20);
    s.push(30);
    std::cout << "Đã đẩy 3 phần tử vào stack.\n";

    // 2. top(): Lấy giá trị phần tử ở đỉnh stack (không xóa)
    std::cout << "Phần tử đỉnh stack: " << s.top() << "\n"; // Kết quả: 30

    // 3. pop(): Xóa phần tử ở đỉnh stack
    s.pop();
    std::cout << "Đã xóa phần tử đỉnh, phần tử mới ở đỉnh: " << s.top() << "\n"; // Kết quả: 20

    // 4. size(): Lấy số lượng phần tử trong stack
    std::cout << "Kích thước hiện tại của stack: " << s.size() << "\n"; // Kết quả: 2

    // 5. empty(): Kiểm tra stack có rỗng không
    if (s.empty()) {
        std::cout << "Stack rỗng.\n";
    } else {
        std::cout << "Stack không rỗng.\n";
    }

    return 0;
}
```

```txt title="Output"
Đã đẩy 3 phần tử vào stack.
Phần tử đỉnh stack: 30
Đã xóa phần tử đỉnh, phần tử mới ở đỉnh: 20
Kích thước hiện tại của stack: 2
Stack không rỗng.
```

> [!explain]- Giải thích code
> Dòng ?: 

---

# 🔥 Tổng kết
Ngăn xếp là một cấu trúc dữ liệu quan trọng với nguyên tắc LIFO, được sử dụng rộng rãi trong nhiều lĩnh vực như quản lý lời gọi hàm, xử lý biểu thức toán học, duyệt đồ thị, và cơ chế "Undo/Redo". Nó có ưu điểm là tốc độ truy xuất nhanh và dễ triển khai nhưng cũng có hạn chế như không truy cập ngẫu nhiên được và dễ bị tràn ngăn xếp khi sử dụng đệ quy.
