# HIT15-WEB-PUBLIC-2025 - WEEK 7


---

## Nội dung

## [I. Tổng quan CSS Grid](#i-tổng-quan-về-css-grid)

## [II. Cách sử dụng CSS Grid](#ii-cách-sử-dụng-css-grid)

## [III. CSS Responsive](#iii-css-responsive-tạo-giao-diện-linh-hoạt-và-thích-nghi)

---

![alt text](grid.png)

### **CSS Grid: Hệ thống bố cục mạnh mẽ và chi tiết**

CSS Grid là một hệ thống layout được thiết kế để giúp bạn xây dựng bố cục web một cách chính xác, dễ dàng và nhanh chóng. Grid cho phép bạn định nghĩa không gian theo cả **hàng (row)** và **cột (column)**, giúp kiểm soát toàn diện layout của trang web.

---

### **I. Tổng quan về CSS Grid**

![alt text](grid-2.png)

CSS Grid bao gồm các khái niệm cơ bản sau:

1. **Grid Container**:

   - Là phần tử cha được thiết lập thuộc tính `display: grid`
   - Chịu trách nhiệm định nghĩa bố cục, số hàng, số cột, và vị trí của các phần tử con.

2. **Grid Item**:

   - Là các phần tử con trực tiếp bên trong Grid Container.
   - Chúng có thể được đặt vào bất kỳ vị trí nào trong grid và tùy chỉnh kích thước, khoảng cách một cách linh hoạt.

3. **Grid Row và Grid Column**:

   - **Grid Row**: Hàng ngang trong grid, được tạo ra bởi `grid-template-rows`.
   - **Grid Column**: Cột dọc trong grid, được tạo ra bởi `grid-template-columns`.

4. **Grid Line**:

   - Là các đường dọc hoặc ngang, chia Grid Container thành các phần nhỏ.
   - Các Grid Line được đánh số bắt đầu từ 1 và kéo dài qua toàn bộ Grid Container.

5. **Grid Track**:

   - Là khoảng không gian giữa hai Grid Line, bao gồm các hàng hoặc cột.

6. **Grid Cell**:

   - Là một ô duy nhất, nơi một Grid Item có thể được đặt.

7. **Grid Area**:

   - Là vùng bao gồm một hoặc nhiều Grid Cell, có thể đặt tên hoặc xác định bằng các dòng.

8. **Grid Gap**:
   - Là khoảng cách giữa các hàng và cột, được thiết lập thông qua `grid-gap`.

---

### **II. Cách sử dụng CSS Grid**

##### **1. Khai báo một Grid Container**

Để biến một phần tử thành Grid Container, sử dụng thuộc tính `display: grid`:

```css
.container {
  display: grid;
}
```

##### **2. Định nghĩa số hàng và cột**

- **`grid-template-columns`**: Định nghĩa số lượng và kích thước của các cột.
- **`grid-template-rows`**: Định nghĩa số lượng và kích thước của các hàng.

Ví dụ:

```css
.container {
  display: grid;
  grid-template-columns: 100px 200px 100px; /* Ba cột với kích thước khác nhau */
  grid-template-rows: 150px 150px; /* Hai hàng, mỗi hàng cao 150px */
}
```

- **Sử dụng đơn vị `fr`**:  
  Đơn vị `fr` chia sẻ không gian còn lại trong grid container.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr; /* Tỷ lệ các cột: 1-2-1 */
}
```

- **Sử dụng hàm `repeat()`**:  
  Rút gọn cú pháp khi có các cột hoặc hàng lặp lại.

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Ba cột, mỗi cột có kích thước 1fr */
}
```

##### **3. Khoảng cách giữa các hàng và cột**

- **`grid-gap`**: Khoảng cách giữa các hàng và cột.

```css
.container {
  display: grid;
  grid-gap: 20px; /* Khoảng cách 20px giữa các hàng và cột */
}
```

- **`grid-row-gap`** và **`grid-column-gap`**: Định nghĩa khoảng cách riêng biệt cho hàng và cột.

```css
.container {
  display: grid;
  grid-row-gap: 10px; /* Khoảng cách giữa các hàng */
  grid-column-gap: 15px; /* Khoảng cách giữa các cột */
}
```

##### **4. Định vị trí Grid Item**

- **`grid-column`**: Xác định vị trí bắt đầu và kết thúc của Grid Item theo cột.

```css
.item {
  grid-column: 1 / 3; /* Bắt đầu từ cột 1 và kết thúc trước cột 3 */
}
```

- **`grid-row`**: Xác định vị trí bắt đầu và kết thúc của Grid Item theo hàng.

```css
.item {
  grid-row: 2 / 4; /* Bắt đầu từ hàng 2 và kết thúc trước hàng 4 */
}
```

- **`grid-area`**: Định nghĩa vùng bao phủ của Grid Item.

```css
.item {
  grid-area: 1 / 1 / 3 / 4; /* Từ hàng 1, cột 1 đến trước hàng 3, cột 4 */
}
```

- **`span`**: Kéo dài Grid Item qua nhiều hàng hoặc cột.

```css
.item {
  grid-column: span 2; /* Kéo dài qua 2 cột */
  grid-row: span 3; /* Kéo dài qua 3 hàng */
}
```

##### **5. Đặt tên và định nghĩa Grid Area**

Sử dụng `grid-template-areas` để đặt tên cho các vùng trong Grid:

```css
.container {
  display: grid;
  grid-template-areas:
    "header header header"
    "main main sidebar"
    "footer footer footer";
}

.header {
  grid-area: header;
}
.main {
  grid-area: main;
}
.sidebar {
  grid-area: sidebar;
}
.footer {
  grid-area: footer;
}
```

!!! ::: Ngoài ra, còn có sử dụng `align-items`, `justify-items`, `align-content`, `justify-content`, `align-self`, `justify-self` để căn chỉnh vị trí của các ô trong grid.

---

### III. **CSS Responsive: Tạo giao diện linh hoạt và thích nghi**

![responsive](./responsive.png)

Responsive Web Design (RWD) đảm bảo giao diện hoạt động tốt trên mọi thiết bị bằng cách sử dụng layout và styling linh hoạt.

#### **1. Cách thức hoạt động**

- Sử dụng các đơn vị đo lường linh hoạt như `%`, `em`, `rem`, ...

- Sử dụng Media Queries để thay đổi layout, font-size, màu sắc, ...

- Sử dụng Flexbox hoặc CSS Grid để xây dựng layout linh hoạt.

#### **2. Media Queries**

Sử dụng Media Queries để thay đổi layout dựa trên kích thước màn hình.

- **Cú pháp**:

```css
@media screen and (max-width: value) {
  /* CSS properties */
}
```

- **Ví dụ:**

```css
@media screen and (max-width: 768px) {
  .container {
    grid-template-columns: 1fr; /* Một cột duy nhất trên màn hình nhỏ */
  }
}
```

- **Breakpoints:**

  - Extra small devices: 0px - 575px.
  - Small devices: 576px - 767px.
  - Medium devices: 768px - 991px.
  - Large devices: 992px - 1199px.
  - Extra large devices: 1200px trở lên.

- **Ví dụ với Breakpoints thường dùng**:

```css
/* Màn hình nhỏ */
@media (max-width: 576px) {
  .container {
    grid-template-columns: 1fr;
  }
}

/* Màn hình trung bình */
@media (min-width: 577px) and (max-width: 768px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Màn hình lớn */
@media (min-width: 769px) {
  .container {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

#### **3. Sử dụng CSS Grid linh hoạt cho Responsive**

CSS Grid kết hợp với Media Queries là công cụ mạnh mẽ để xây dựng giao diện linh hoạt.

Ví dụ:

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>
```

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

/* Responsive: màn hình nhỏ */
@media (max-width: 768px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Responsive: màn hình rất nhỏ */
@media (max-width: 480px) {
  .container {
    grid-template-columns: 1fr;
  }
}
```

**Kết quả**:

- Màn hình lớn: Hiển thị 3 cột.
- Màn hình trung bình: Hiển thị 2 cột.
- Màn hình nhỏ: Hiển thị 1 cột.
