---
date: 2025-02-16
draft: true
status: Doing
title: "Danh sách liên kết đơn"
description: "Danh sách liên kết đơn là một cấu trúc dữ liệu quan trọng giúp quản lý bộ nhớ động hiệu quả. Tìm hiểu cách triển khai Singly Linked List trong C++ với mã nguồn chi tiết và cách sử dụng thư viện chuẩn."
author: PhDoanh
authorlink: https://github.com/PhDoanh
tags: 
  - dsa
  - coding
  - cpp
  - competitive
  - "data-structure"
  - linked-list
aliases:
  - "singly linked list"
cssclasses:
  - img
  - btn
---
%% ĐỊNH DẠNG TÊN FILE: "tên-cấu-trúc-dữ-liệu-hoặc-thuật-toán" | VD: binary-search %%

%% <figure style="text-align: center; margin: 20px auto;">
  <img 
    src="images/singly-linked-list.png"
    alt="Cấu trúc danh sách liên kết đơn" 
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

# 👀 Giới thiệu về Singly Linked List
Danh sách liên kết (**Linked List**) là một cấu trúc dữ liệu động bao gồm các **nút (node)**, mỗi nút chứa **dữ liệu** và một **con trỏ** trỏ đến nút tiếp theo. Không giống như mảng, danh sách liên kết không yêu cầu bộ nhớ liên tục, giúp tối ưu việc cấp phát bộ nhớ động. 

Danh sách được gọi là **liên kết đơn** nếu mỗi nút chứa dữ liệu và một **con trỏ** trỏ đến nút kế tiếp. Nó giúp quản lý bộ nhớ động nhưng chỉ duyệt theo một chiều.

---

# 🛠️ Khai triển Singly Linked List trong C++

## Định nghĩa nút
```cpp {2,4,6-10}
struct Node {
    int data;

    Node* next;

    Node(int data)
    {
        this->data = data;
        this->next = nullptr;
    }
};
```

> [!explain]- Giải thích code
> Dòng 2: Phần **dữ liệu** của nút
> Dòng 4: **Con trỏ** trỏ tới nút tiếp theo trong danh sách
> Dòng 6-10: Hàm tạo để **khởi tạo** dữ liệu nút

## Thao tác duyệt phần tử 
Thao tác này sẽ in ra dữ liệu của từng nút trong danh sách

```cpp {3,5-10}
void print(Node* head)
{
    Node* current = head;

    while (current != nullptr) {
      
        cout << current->data << " ";

        current = current->next;
    }

    cout << '\n';
}
```

> [!explain]- Giải thích code
> Dòng 3: Bắt đầu từ đầu danh sách (con trỏ `head`)
> Dòng 5: Duyệt danh sách đến khi phần tử cuối cùng là `nullptr` thì dừng lại
> Dòng 7: In dữ liệu của nút hiện tại
> Dòng 9: Di chuyển tới nút tiếp theo

## Thao tác tìm kiếm
Thao tác này sẽ cho biết phần tử cần tìm có nằm trong danh sách hay không

```cpp {3,5-7,9,12}
bool find(Node* head, int target)
{
    while (head != nullptr) {

        if (head->data == target) {
            return true;
        }

        head = head->next;
    }

    return false;
}
```

> [!explain]- Giải thích code
> Dòng 3: Duyệt toàn bộ danh sách liên kết
> Dòng 5-7: Phần tử được tìm thấy nếu dữ liệu nút hiện tại bằng với nó
> Dòng 9: Di chuyển tới nút tiếp theo
> Dòng 12: Không tìm thấy phần tử do đã duyệt và kiểm tra hết danh sách mà không thỏa mãn dòng 5-7

## Thao tác lấy chiều dài danh sách
Thao tác này sẽ trả về số phần tử có trong danh sách

```cpp {3,5,8,12}
int len(Node* head)
{
    int length = 0;

    Node* current = head;

    while (current != nullptr) {
        length++;
        current = current->next;
    }

    return length;
}
```

> [!explain] Giải thích code
> Dòng 3: Khởi tạo biến đếm số phần tử 
> Dòng 5: Bắt đầu từ đầu danh sách (con trỏ `head`)
> Dòng 8: Tăng biến đếm lên 1 đơn vị trong quá trình duyệt toàn bộ danh sách
> Dòng 12: Trả về số phần tử đã đếm được

## Thao tác chèn phần tử
Thao tác này dùng để chèn 1 nút mới vào danh sách tại 1 vị trí cụ thể

```cpp {8-12,14-19,21-24,26-28}
Node* insertNode(Node* head, int pos, int data)
{
    if (pos < 1) {
        cout << "Invalid position!" << endl;
        return head;
    }

    if (pos == 1) {        
        Node* temp = new Node(data);
        temp->next = head;
        return temp;
    }

    Node* prev = head;
    int count = 1;
    while (count < pos - 1 && prev != nullptr) {
        prev = prev->next;
        count++;
    }

    if (prev == nullptr) {
        cout << "Invalid position!" << endl;
        return head;
    }

    Node* temp = new Node(data);
    temp->next = prev->next;
    prev->next = temp;

    return head;
}

```

> [!explain] Giải thích code
> Dòng 8-12: Xử lý trường hợp đặc biệt khi chèn tại ví trí đầu tiên
> Dòng 14-19: Duyệt danh sách để tìm ra nút đứng trước vị trí cần chèn
> Dòng 21-24: Xử lý trường hợp vị trí cần chèn lớn hơn số nút
> Dòng 26-28: Chèn nút mới vào vị trí hiện tại tìm được theo `pos`

## Thao tác xóa phần tử
Thao tác dùng để xóa 1 nút khỏi danh sách tại 1 vị trí cụ thể

```cpp {4-5,7-12,14-17,19-21,23-25}
Node* eraseNode(Node* head, int position)
{
    if (head == nullptr || position < 1) {
        return head;
    }

    if (position == 1) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return head;
    }

    Node* current = head;
    for (int i = 1; i < position - 1 && current != nullptr; i++) {
        current = current->next;
    }

    if (current == nullptr || current->next == nullptr) {
        return;
    }

    Node* temp = current->next;
    current->next = current->next->next;
    delete temp;
  
    return head;
}
```

> [!explain] Giải thích code
> Dòng 4-5: Xử lý trường hợp đặc biệt khi danh sách rỗng hoặc vị trí xóa không hợp lệ
> Dòng 7-12: Xử lý tường hợp đặc biệt khi muốn xóa nút đầu tiên
> Dòng 14-17: Duyệt danh sách để tìm ra nút đứng trước vị trí cần xóa
> Dòng 19-21: Xử lý trường hợp vị trí cần xóa lớn hơn số nút
 > Dòng 23-25: Lưu trữ nút cần xóa (nút kế tiếp), nối nút hiện tại (nút đứng trước vị trí cần xóa) với nút kế tiếp của nút cần xóa (kế tiếp của kế tiếp) và xóa nút đã lưu

---

# ✨ Singly Linked List trong thư viện chuẩn C++
description

## Hàm %% `find()` %%
description

```cpp

```

> [!info] Lưu ý
> Contents

---

# 🔥 Tổng kết
Danh sách liên kết đơn là một cấu trúc dữ liệu **đơn giản, tiết kiệm bộ nhớ** do mỗi nút chỉ cần một con trỏ trỏ đến phần tử kế tiếp. Nó phù hợp với các bài toán **chỉ cần duyệt một chiều** và **thao tác chèn/xóa nhanh ở đầu danh sách**. Tuy nhiên, nhược điểm lớn là **khó duyệt ngược**, việc **chèn/xóa ở cuối kém hiệu quả** vì phải duyệt toàn bộ danh sách.
