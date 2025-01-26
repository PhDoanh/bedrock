---
date: 2025-01-25
draft: true
status: Doing
title: "Xử lý vào/ra trong C++"
description: ""
author: PhDoanh
authorlink: https://github.com/PhDoanh
tags: 
  - "coding"
  - cpp
  - cph
  - competitive
  - basic
aliases:
  - "input output"
  - "Xử lý vào/ra trong C++"
cssclasses:
  - img
  - btn
---
%% ĐỊNH DẠNG TÊN FILE: "tên-bài-viết" | VD: jp-typing-guide %%

<figure style="text-align: center; margin: 20px auto;">
  <img 
    src="images/input-output.png"
    alt="Xử lý vào/ra trong C++" 
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
    <em>caption</em>
  </figcaption>
</figure>

Trong C++, việc xử lý vào/ra (input/output) có thể được thực hiện thông qua các thư viện và phương pháp khác nhau. Dưới đây là chi tiết về các cách xử lý vào/ra tiêu chuẩn và vào/ra tệp, kèm theo ví dụ và lưu ý.

# Bài toán
Tính tổng hai số nguyên nhập từ bàn phím và in kết quả ra màn hình.

Đầu vào mẫu:
```
1 2
```

Đầu ra mẫu:
```
3
```

# Vào/ra tiêu chuẩn

## Thư viện `<iostream>{:cpp}`
Gọi toán tử trích xuất `>>{:cpp}` sau `cin{:cpp}` 

```cpp {6,8}
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cin >> a >> b;
    int sum = a + b;
    cout << "Tổng hai số là: " << sum << '\n'; // thay thế 
    return 0;
}
```

> [!info] Lưu ý
> - `cin{:cpp}` và `cout{:cpp}` là các đối tượng tiêu chuẩn, dễ sử dụng và phù hợp cho các bài toán đơn giản.
> - `cin{:cpp}` tự động bỏ qua khoảng trắng và ký tự xuống dòng khi nhập dữ liệu.
> - `endl` và `\n` không giống nhau, xem "Tăng tốc độ vào/ra" để biết chi tiết

## Thư viện `<cstdio>{:cpp}`



# Vào/ra tệp

## Hàm `freopen(){:cpp}`



## Thư viện `fstream{:cpp}`

