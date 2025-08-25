# HIT-WEB-PUBLIC-2025 - WEEK 6


## Nội dung

## [I. CSS Position](#i-css-position-1)

## [II. CSS Animation](#ii-css-animation-1)

## [III. CSS Transition](#iii-css-transition-1)

---

# I. **CSS Position**

`CSS Position` là thuộc tính dùng để định vị và kiểm soát cách các phần tử xuất hiện trên trang web. Nó cho phép các phần tử di chuyển linh hoạt hoặc cố định trong giao diện tùy theo nhu cầu thiết kế .

Dưới đây là các giá trị phổ biến của thuộc tính `position`:

### **1. `static` (Mặc định)**

- Đây là giá trị mặc định của tất cả các phần tử HTML.
- Phần tử được sắp xếp theo thứ tự xuất hiện trong tài liệu và không bị ảnh hưởng bởi các thuộc tính định vị như `top`, `left`, `right`, `bottom`.

**Ví dụ:**

```html
<div class="static-box">Box</div>
```

```css
.static-box {
  position: static;
  background-color: lightblue;
}
```

- **Kết quả**: Phần tử được sắp xếp theo vị trí tự nhiên mà không có sự thay đổi.

### **2. `relative`**

- Phần tử được định vị **so với vị trí ban đầu của chính nó**.
- Khi sử dụng các thuộc tính `top`, `left`, `right`, `bottom`, phần tử sẽ di chuyển khỏi vị trí ban đầu mà không làm ảnh hưởng đến các phần tử khác trong bố cục.

**Ví dụ:**

```html
<div class="relative-box">Box</div>
```

```css
.relative-box {
  position: relative;
  top: 20px; /* Di chuyển xuống 20px */
  left: 30px; /* Di chuyển sang phải 30px */
  background-color: lightgreen;
}
```

- **Kết quả**: Phần tử di chuyển xuống dưới và sang phải nhưng không chiếm vị trí mới trong luồng tài liệu.

### **3. `absolute`**

- Phần tử được định vị **so với phần tử cha gần nhất có `position` khác `static`**.
- Nếu không có phần tử cha nào có `position`, nó sẽ căn cứ vào toàn bộ trang (`html`).
- Phần tử không giữ vị trí trong luồng tài liệu và sẽ không ảnh hưởng đến các phần tử khác.

**Ví dụ:**

```html
<div class="relative-container">
  <div class="absolute-box">Box</div>
</div>
```

```css
.relative-container {
  position: relative;
  width: 300px;
  height: 200px;
  background-color: lightgray;
}

.absolute-box {
  position: absolute;
  top: 10px;
  left: 20px;
  background-color: lightpink;
  padding: 10px;
}
```

- **Kết quả**: Phần tử `.absolute-box` được định vị dựa trên container `.relative-container`. Nó không chiếm chỗ trong luồng tài liệu.

### **4. `fixed`**

- Phần tử được định vị **so với cửa sổ trình duyệt (viewport)**.
- Vị trí của phần tử sẽ không thay đổi ngay cả khi trang được cuộn.

**Ví dụ:**

```html
<div class="fixed-box">Fixed Box</div>
```

```css
.fixed-box {
  position: fixed;
  top: 10px;
  right: 10px;
  background-color: yellow;
  padding: 10px;
}
```

- **Kết quả**: Phần tử cố định ở góc trên bên phải trình duyệt và không di chuyển khi cuộn trang.

### **5. `sticky`**

- Phần tử hoạt động như `relative` cho đến khi cuộn đến một điểm nhất định, sau đó trở thành `fixed`.
- Phạm vi dính của phần tử chỉ nằm trong container của nó.

**Ví dụ:**

```html
<div class="sticky-container">
  <div class="sticky-box">Sticky Box</div>
</div>
```

```css
.sticky-container {
  height: 200vh; /* Tăng chiều cao để cuộn */
}

.sticky-box {
  position: sticky;
  top: 20px; /* Cố định cách mép trên 20px */
  background-color: orange;
  padding: 10px;
}
```

- **Kết quả**: Phần tử dính ở vị trí cách mép trên 20px khi cuộn trang nhưng sẽ dừng lại khi container kết thúc.

### 5. **Ví dụ: Kết hợp `relative` và `absolute`**

**Trường hợp thực tế:** Một phần tử con có `position: absolute` nằm trong một phần tử cha có `position: relative`. Điều này cho phép phần tử con được định vị tự do nhưng vẫn trong phạm vi của phần tử cha.

```html
<div class="relative-container">
  <div class="absolute-child">Absolute Child</div>
</div>
```

```css
.relative-container {
  position: relative;
  width: 400px;
  height: 300px;
  background-color: lightblue;
}

.absolute-child {
  position: absolute;
  top: 50px;
  left: 100px;
  background-color: lightcoral;
  padding: 10px;
}
```

- **Kết quả**: Phần tử `.absolute-child` chỉ được di chuyển trong phạm vi của `.relative-container`.

### 6. **Tổng kết**

| **Giá trị** | **Ý nghĩa**                                                             | **Giữ vị trí trong luồng tài liệu** | **Định vị dựa trên**                |
| ----------- | ----------------------------------------------------------------------- | ----------------------------------- | ----------------------------------- |
| `static`    | Vị trí mặc định, không thể điều chỉnh.                                  | Có                                  | Luồng tự nhiên.                     |
| `relative`  | Di chuyển so với vị trí ban đầu của chính nó.                           | Có                                  | Chính nó.                           |
| `absolute`  | Di chuyển tự do trong phạm vi phần tử cha gần nhất có `position`.       | Không                               | Phần tử cha gần nhất có `position`. |
| `fixed`     | Cố định trong cửa sổ trình duyệt, không thay đổi khi cuộn trang.        | Không                               | Cửa sổ trình duyệt.                 |
| `sticky`    | Dính tại một vị trí khi cuộn trang, chỉ trong phạm vi container của nó. | Có                                  | Container hoặc viewport (khi cuộn). |

---

## **II. CSS Animation**

CSS Animation giúp bạn tạo ra các hiệu ứng chuyển động mượt mà giữa các trạng thái của phần tử trong trang web. Hoạt ảnh trong CSS được áp dụng qua hai phần chính: khai báo `@keyframes` và sử dụng thuộc tính `animation`.

### **1. Khai báo `@keyframes`**

Để tạo ra một hoạt ảnh, bạn cần khai báo `@keyframes`, đây là nơi định nghĩa các trạng thái khác nhau của phần tử tại các thời điểm cụ thể trong quá trình chuyển động.

- **`from` và `to`**: Được sử dụng để định nghĩa trạng thái ban đầu và trạng thái kết thúc của hoạt ảnh.
- **Phần trăm (%)**: Bạn cũng có thể sử dụng giá trị phần trăm (0%, 50%, 100%) để xác định các điểm thời gian trong quá trình hoạt ảnh.

**Ví dụ về `@keyframes`:**

```css
@keyframes moveRight {
  from {
    transform: translateX(0); /* Bắt đầu tại vị trí gốc */
  }
  to {
    transform: translateX(200px); /* Di chuyển sang phải 200px */
  }
}
```

**Ví dụ về sử dụng phần trăm để chia nhỏ quá trình:**

```css
@keyframes bounce {
  0%,
  100% {
    transform: translateY(0); /* Ở vị trí gốc */
  }
  50% {
    transform: translateY(-50px); /* Nâng lên 50px tại giữa quá trình */
  }
}
```

### **2. Các thuộc tính trong `animation`**

Sau khi khai báo `@keyframes`, bạn cần sử dụng thuộc tính `animation` để áp dụng hoạt ảnh lên phần tử.

#### **a. `animation-name`**

- **Chức năng**: Đặt tên cho hoạt ảnh đã khai báo với `@keyframes`.
- **Giá trị**: Tên của `@keyframes`.

**Ví dụ:**

```css
animation-name: bounce; /* Áp dụng hoạt ảnh 'bounce' đã khai báo */
```

#### **b. `animation-duration`**

- **Chức năng**: Xác định thời gian mà hoạt ảnh sẽ diễn ra.
- **Giá trị**: Một khoảng thời gian (ví dụ: `2s`, `500ms`).

**Ví dụ:**

```css
animation-duration: 2s; /* Hoạt ảnh diễn ra trong 2 giây */
```

#### **c. `animation-timing-function`**

- **Chức năng**: Xác định cách thức thay đổi tốc độ trong suốt quá trình hoạt ảnh. Điều này giúp tạo ra các hiệu ứng chuyển động mượt mà hoặc có sự thay đổi tốc độ.
- **Giá trị**: Các giá trị như `linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`.

**Ví dụ:**

```css
animation-timing-function: ease-in-out; /* Tốc độ thay đổi mượt mà */
```

#### **d. `animation-delay`**

- **Chức năng**: Xác định thời gian trì hoãn trước khi hoạt ảnh bắt đầu.
- **Giá trị**: Một khoảng thời gian (ví dụ: `1s`, `500ms`).

**Ví dụ:**

```css
animation-delay: 1s; /* Hoạt ảnh bắt đầu sau 1 giây */
```

#### **e. `animation-iteration-count`**

- **Chức năng**: Xác định số lần hoạt ảnh sẽ lặp lại.
- **Giá trị**: Một số lượng cụ thể (ví dụ: `3`) hoặc `infinite`.

**Ví dụ:**

```css
animation-iteration-count: infinite; /* Hoạt ảnh sẽ lặp lại vô hạn */
```

##### **f. `animation-direction`**

- **Chức năng**: Xác định hướng của hoạt ảnh.
- **Giá trị**: `normal` (hoạt ảnh chạy theo chiều mặc định), `reverse` (hoạt ảnh chạy ngược lại), `alternate` (hoạt ảnh chạy theo chiều thuận và ngược lại), `alternate-reverse`.

**Ví dụ:**

```css
animation-direction: alternate; /* Hoạt ảnh chạy theo chiều thuận rồi ngược lại */
```

### **3. Cú pháp shorthand của `animation`**

Sau khi hiểu các thuộc tính cơ bản, bạn có thể sử dụng cú pháp shorthand để áp dụng tất cả các thuộc tính này trong một dòng mã duy nhất.

**Cú pháp shorthand:**

```css
animation: [animation-name] [animation-duration] [animation-timing-function]
  [animation-delay] [animation-iteration-count] [animation-direction];
```

**Ví dụ:**

```css
/* Ứng dụng toàn bộ thuộc tính animation vào phần tử */
.animation-box {
  animation: bounce 2s ease-in-out 1s infinite alternate;
}
```

### **4. Ví dụ cụ thể**

HTML:

```html
<div class="box"></div>
```

CSS:

```css
@keyframes moveRight {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(200px);
  }
}

.box {
  width: 100px;
  height: 100px;
  background-color: lightblue;
  animation: moveRight 2s ease-in-out infinite;
}
```

**Giải thích**:

- `@keyframes moveRight`: Khai báo hoạt ảnh di chuyển sang phải.
- `animation: moveRight 2s ease-in-out infinite`: Áp dụng hoạt ảnh với thời gian 2 giây, chuyển động mượt mà, lặp vô hạn.

---

## **III. CSS Transition**

CSS Transition giúp tạo ra các hiệu ứng chuyển đổi mượt mà giữa hai trạng thái của phần tử. Các thuộc tính của Transition giúp bạn tạo hiệu ứng mượt mà khi người dùng thay đổi trạng thái của phần tử (ví dụ: hover, focus, active).

### **1. Các thuộc tính trong `transition`**

#### **a. `transition-property`**

- **Chức năng**: Xác định thuộc tính CSS mà bạn muốn tạo hiệu ứng chuyển đổi.
- **Giá trị**: Tên thuộc tính (ví dụ: `background-color`, `width`, `transform`).

**Ví dụ:**

```css
transition-property: background-color; /* Tạo hiệu ứng chuyển đổi cho background-color */
```

#### **b. `transition-duration`**

- **Chức năng**: Xác định thời gian mà hiệu ứng chuyển đổi sẽ hoàn thành.
- **Giá trị**: Một khoảng thời gian (ví dụ: `0.5s`, `300ms`).

**Ví dụ:**

```css
transition-duration: 0.3s; /* Chuyển đổi trong 0.3 giây */
```

#### **c. `transition-timing-function`**

- **Chức năng**: Xác định cách thức thay đổi tốc độ trong suốt quá trình chuyển đổi.
- **Giá trị**: Các giá trị như `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out`.

**Ví dụ:**

```css
transition-timing-function: ease-in-out; /* Chuyển đổi mượt mà */
```

#### **d. `transition-delay`**

- **Chức năng**: Xác định thời gian trì hoãn trước khi hiệu ứng chuyển đổi bắt đầu.
- **Giá trị**: Thời gian trì hoãn (ví dụ: `0.5s`, `1s`).

**Ví dụ:**

```css
transition-delay: 0.2s; /* Chuyển đổi bắt đầu sau 0.2 giây */
```

### **2. Cú pháp shorthand của `transition`**

Sau khi hiểu các thuộc tính cơ bản của `transition`, bạn có thể sử dụng cú pháp shorthand để áp dụng tất cả các thuộc tính này trong một dòng mã duy nhất.

**Cú pháp shorthand:**

```css
transition: [transition-property] [transition-duration]
  [transition-timing-function] [transition-delay];
```

**Ví dụ:**

```css
/* Ứng dụng toàn bộ thuộc tính transition vào phần tử */
.transition-box {
  transition: background-color 0.3s ease-in-out 0.2s;
}
```

---

### 3. **Ví dụ cụ thể**

HTML:

```html
<div class="transition-box">Hover Me</div>
```

CSS:

```css
.transition-box {
  width: 200px;
  height: 200px;
  background-color: lightblue;
  transition: background-color 0.5s ease;
}

.transition-box:hover {
  background-color: lightgreen;
}
```

**Giải thích**:

- `transition: background-color 0.5s ease`: Tạo hiệu ứng chuyển đổi màu nền trong 0.5 giây.
- Khi di chuột qua phần tử `.transition-box`, màu nền sẽ thay đổi từ `lightblue` sang `lightgreen` một cách mượt mà.

---

### **Tổng kết so sánh giữa CSS Transition và CSS Animation**

| **Đặc điểm**             | **CSS Transition**                                                      | **CSS Animation**                                                                                  |
| ------------------------ | ----------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Kích hoạt**            | Khi trạng thái của phần tử thay đổi (chẳng hạn như khi hover).          | Tự động chạy hoặc có thể kích hoạt bằng cách thay đổi lớp hoặc sự kiện.                            |
| **Độ phức tạp**          | Hiệu ứng đơn giản, chuyển đổi giữa hai trạng thái.                      | Có thể tạo ra các hiệu ứng phức tạp, với nhiều bước chuyển động.                                   |
| **Lặp lại**              | Không lặp lại trừ khi trạng thái thay đổi liên tục.                     | Có thể lặp lại vô hạn, hoặc lặp lại một số lần nhất định.                                          |
| **Thời gian bắt đầu**    | Chỉ có thể bắt đầu khi có thay đổi trạng thái.                          | Có thể bắt đầu ngay lập tức hoặc sau một khoảng thời gian trì hoãn (delay).                        |
| **Sử dụng**              | Thích hợp cho các hiệu ứng chuyển đổi đơn giản như hover, focus.        | Thích hợp cho các hoạt ảnh phức tạp, nhiều bước thay đổi như di chuyển, thay đổi màu sắc liên tục. |
| **Điều khiển tốc độ**    | Dễ dàng điều khiển với các thuộc tính như `transition-timing-function`. | Cung cấp nhiều tùy chọn kiểm soát chuyển động như `keyframes`, `animation-timing-function`.        |
| **Sự kiện**              | Không thể tự kích hoạt hay có nhiều trạng thái.                         | Có thể tạo nhiều trạng thái và chuyển động, chẳng hạn như di chuyển, thay đổi màu sắc, xoay vòng.  |
| **Khả năng tái sử dụng** | Ít linh hoạt hơn khi muốn thay đổi nhiều trạng thái.                    | Rất linh hoạt trong việc thay đổi nhiều trạng thái và tạo hiệu ứng phức tạp.                       |
