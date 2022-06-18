---
title: "Liner"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
draft: true
---


## Nội suy tuyến tính

Vấn đề: Cho 1 xe khách đi từ vị trí a->b và biết xe khách này đi tới vị trí b mất 5 giây. Vậy khi ở giây thứ 2 xe khách đó sẽ ở vị trí nào trong đoạn a->b? Vị trí a là mét thứ 5, vị trí b mét thứ 12

Dùng phép nội suy tuyến tính để nội suy xem vị trí xe khách ở đâu trong giây thứ 2.

Phép nội suy tuyến tính cho 2 điểm đã biết {{< katex>}}(x_0,y_0) {{< /katex>}} và {{< katex>}} (x_1,y_1){{< /katex >}}. Và giá trị 
{{< katex>}} x {{< /katex>}} là giá trị trong khoảng 
{{< katex>}}(x_0, x_1){{< /katex>}}

Vậy ta có biểu thức


{{< katex>}}
\dfrac{y - y_0}{x - x_0}=\dfrac{y_1 - y_0}{x_1 - x_0}

{{< /katex>}}

Tìm 
{{< katex>}}y{{< /katex>}} là giá trị không biết tại giá trị {{< katex>}}x{{< /katex>}}

{{< katex>}}
y = y_0 + (x - x_0)\dfrac{y_1 - y_0}{x_1 - x_0}
{{< /katex >}}


Quay trở lại bài toán: ta gọi x thời gian, y biểu diễn cho vị trí. Vậy thế vào phương trình trên ta đc

{{< katex >}}
y_0 \rightarrow y_1: 5 \rightarrow 12{{< /katex >}}

{{< katex >}}
x_0 \rightarrow x_1: 0 \rightarrow 2 
{{< /katex >}}. Hỏi giây x thứ 2 xe khách ở vị trí y nào?

- Giải:

    {{< katex>}}
        y = 5 + (2 - 0)\dfrac{12 - 5}{5 - 0}
    {{< /katex >}}

## Cài đặt

Dựa vào biểu thức trên ta có thể cài đặt code như bên dưới



```c++
// Imprecise method, which does not guarantee v = v1 when t = 1, due to floating-point arithmetic error.
// This method is monotonic. This form may be used when the hardware has a native fused multiply-add instruction.
float lerp(float v0, float v1, float t) {
  return v0 + t * (v1 - v0);
}

// Precise method, which guarantees v = v1 when t = 1. This method is monotonic only when v0 * v1 < 0.
// Lerping between same values might not produce the same value
float lerp(float v0, float v1, float t) {
  return (1 - t) * v0 + t * v1;
}
```

## Tham khảo
    Tham khảo từ wikipedia https://en.wikipedia.org/wiki/Linear_interpolation