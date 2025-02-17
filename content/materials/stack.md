---
date: 2025-02-16
draft: true
status: Not started
title: "Cấu trúc dữ liệu ngăn xếp"
description: ""
author: PhDoanh
authorlink: https://github.com/PhDoanh
tags: 
  - dsa
  - coding
  - cpp
  - competitive
  - data-structure
aliases:
  - stack
cssclasses:
  - img
  - btn
---
%%  LƯU Ý
- Đinh dạng tên file : "dsa-name" (binary-search, linear-search, ...)
%%

%% banner
<figure style="text-align: center; margin: 20px auto;">
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
    <em>{chú thích}</em>
  </figcaption>
</figure>
%%

# 👀 Giới thiệu về Stack
**Ngăn xếp (Stack)** là một cấu trúc dữ liệu tuyến tính hoạt động theo nguyên tắc **LIFO (Last In, First Out)**, nghĩa là phần tử được thêm vào sau cùng sẽ được lấy ra đầu tiên. Các thao tác chính trên ngăn xếp bao gồm:

- **Push**: Thêm một phần tử vào đỉnh ngăn xếp.
- **Pop**: Loại bỏ phần tử ở đỉnh ngăn xếp.
- **Peek/Top**: Truy cập phần tử ở đỉnh ngăn xếp mà không loại bỏ nó.

**Ứng dụng của ngăn xếp:**

- **Quản lý bộ nhớ trong các ngôn ngữ lập trình**: Ngăn xếp được sử dụng để lưu trữ các lời gọi hàm và biến cục bộ, giúp theo dõi thứ tự gọi và trả về của các hàm.
- **Đảo ngược chuỗi hoặc cấu trúc dữ liệu**: Sử dụng ngăn xếp để đảo ngược chuỗi ký tự hoặc danh sách bằng cách đẩy từng phần tử vào ngăn xếp và sau đó pop ra theo thứ tự ngược lại.
- **Kiểm tra dấu ngoặc trong biểu thức toán học**: Ngăn xếp giúp xác định xem các dấu ngoặc mở và đóng có khớp nhau hay không trong biểu thức.
- **Chuyển đổi và tính toán biểu thức**: Chuyển đổi giữa các dạng biểu thức (infix, postfix, prefix) và tính giá trị của chúng.
- **Duyệt cây và đồ thị**: Sử dụng trong các thuật toán duyệt cây như duyệt theo chiều sâu (DFS).

> [!check] Ưu điểm
> - **Đơn giản và dễ triển khai**: Cấu trúc và thao tác trên ngăn xếp rất đơn giản, dễ hiểu và dễ cài đặt.
> - **Quản lý bộ nhớ hiệu quả**: Việc sử dụng ngăn xếp giúp quản lý bộ nhớ tự động, đặc biệt trong việc gọi hàm đệ quy.
> - **Tốc độ truy cập nhanh**: Thao tác thêm và loại bỏ phần tử chỉ diễn ra ở đỉnh ngăn xếp, do đó có độ phức tạp thời gian là $O(1)$.

> [!missing] Nhược điểm
> - **Truy cập hạn chế**: Chỉ có thể truy cập phần tử ở đỉnh ngăn xếp, không thể truy cập trực tiếp các phần tử khác.
> - **Kích thước cố định (trong trường hợp ngăn xếp tĩnh)**: Nếu ngăn xếp được triển khai bằng mảng có kích thước cố định, có thể dẫn đến lãng phí bộ nhớ hoặc tràn ngăn xếp.
> - **Dễ gây lỗi tràn ngăn xếp (Stack Overflow)**: Khi thêm quá nhiều phần tử mà không kiểm tra dung lượng, ngăn xếp có thể bị tràn và gây lỗi.

---

# 🛠️ Khai triển Stack trong C++

## Khai triển bằng mảng

> [!caution]- Nội dung đang hoàn thiện
> Quá trình xây dựng nội dung này có thể mất nhiều thời gian ⌛, nhưng bạn có thể thúc đẩy nó bằng cách tham gia [[article-collaboration-guide|cộng tác bài viết]] 🤝
> 
> **Rất mong sự thông cảm của các bạn 🙏**

## Khai triển bằng danh sách liên kết

## {tên thao tác}
%% mô tả %%

```cpp {}

```

> [!explain]- Giải thích code
> Dòng ?: 

---

# ✨ Stack trong thư viện chuẩn C++
%% mô tả %%

| Phương thức | Kiểu trả về | Tham số | Mô tả | Độ phức tạp |
|:-----------:|:-----------:|:------- |:----- |:-----------:|
|             |             |         |       |             |

```cpp {}

```

```txt title="Đầu ra"

```

> [!explain]- Giải thích code
> Dòng ?:

---

# 🔥 Tổng kết
%% tóm tắt, nhận xét %%
