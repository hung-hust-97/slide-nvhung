# HƯỚNG DẪN TẠO SLIDE HTML — Trường Đại học CMC

> **Mục đích**: File này là hướng dẫn đầy đủ để AI (hoặc người) có thể tạo ra 1 bài slide HTML hoàn chỉnh từ đầu đến cuối mà không cần hỏi thêm. Đọc file này + file `template.css` là đủ thông tin.

---

## 1. CẤU TRÚC THƯ MỤC

```
CNTT/                              ← Lĩnh vực: Công nghệ thông tin
├── template.css                   ← CSS dùng chung cho TẤT CẢ các môn trong lĩnh vực CNTT
├── template.md                    ← File này — hướng dẫn tạo slide
├── shared/                        ← Hình nền + logo dùng chung cho tất cả môn CNTT
│   ├── bg-title.png               ← Background slide trang bìa (xanh đậm, có hoa văn)
│   ├── bg-content.jpg             ← Background slide nội dung (trắng, header xanh)
│   └── logo-white.png             ← Logo CMC University màu trắng
├── image/template/                ← Hình mẫu (thư mục dự phòng, hiện trống)
│
├── ThietKeXayDungPhanMem/         ← Môn: Thiết kế & Xây dựng phần mềm
│   ├── yeu_cau/                   ← THƯ MỤC NGUỒN: chứa file PPTX gốc, đề cương, tài liệu
│   │   ├── Lesson_01_Agile.pptx
│   │   ├── Lesson_02_SDD.pptx
│   │   ├── Lesson_03_ArchitectureDesign.pptx
│   │   ├── Lesson_04_UML.pptx
│   │   ├── Lesson_05_Springboot.pptx
│   │   ├── Lesson_06_JPA-Hibernate.pptx
│   │   ├── Lesson_07_Spring-advance.pptx
│   │   ├── Lesson_08_Angular.pptx
│   │   ├── Lesson_09_Angular-API.pptx
│   │   ├── SOFT4002_v1.2_Nguyen_Viet_Hung.docx  ← Đề cương môn học
│   │   ├── BM  Ma trận đề thi bài tập lớn...docx
│   │   └── Học_Online_SE2_22IT.pdf                ← Tài liệu tham khảo
│   ├── Lesson_01_Agile/
│   │   ├── index.html             ← Slide tiếng Việt (tạo trước)
│   │   ├── index_en.html          ← Slide tiếng Anh (tạo SAU khi hoàn tất tiếng Việt)
│   │   └── assets/                ← Hình minh họa riêng cho bài này
│   │       ├── image6.jpeg
│   │       └── scrum-board.png
│   ├── Lesson_02_SDD/
│   │   ├── index.html
│   │   ├── index_en.html
│   │   └── assets/
│   ├── Lesson_03_ArchitectureDesign/
│   ├── Lesson_04_UML/
│   ├── Lesson_05_Springboot/
│   ├── Lesson_06_JPA-Hibernate/
│   ├── Lesson_07_Spring-advance/
│   ├── Lesson_08_Angular/
│   └── Lesson_09_Angular-API/
│
├── CongNghePhanMem/               ← Môn: Công nghệ phần mềm (sẵn sàng, chưa có bài)
├── DaPhuongTien/                  ← Môn: Đa phương tiện
│   └── Lesson_03_MediaFundamentals/  (sẵn thư mục, chưa có nội dung)
└── LapTrinhDaNenTang/             ← Môn: Lập trình đa nền tảng với Flutter
    ├── yeu_cau/                   ← Nguồn: 5 file PPTX tiếng Anh
    │   ├── 01.1-Tong-Quan-Phat-Trien-Ung-Dung-Di-Dong-en.pptx
    │   ├── 01.2-Tong-Quan-Kien-Truc-Ung-Dung-Di-Dong-en.pptx
    │   ├── 02-Tong-Quan-Dart-en.pptx
    │   ├── 03-Lap-trinh-huong-doi-tuong-Dart.pptx
    │   ├── 04-Flutter-Framework-va-quan-ly-trang-thai.pptx
    │   └── 05-Navigation và Routing.pptx
    ├── Lesson_01_MobileOverview/   (10 slides) — Tổng quan phát triển ứng dụng di động
    ├── Lesson_02_CrossPlatform/    (17 slides) — Kiến trúc đa nền tảng
    ├── Lesson_03_DartBasics/       (18 slides) — Tổng quan ngôn ngữ Dart
    ├── Lesson_04_OOPDart/          (14 slides) — Lập trình hướng đối tượng với Dart
    ├── Lesson_05_FlutterState/     (20 slides) — Flutter Framework và Quản lý Trạng thái
    └── Lesson_06_Navigation/        (11 slides) — Navigation và Routing
```

### Đường dẫn tương đối quan trọng
Mỗi file HTML nằm ở `CNTT/<TenMon>/Lesson_XX/index.html`, tức cách thư mục `CNTT/` **2 cấp**. Do đó:
- CSS: `href="../../template.css"`
- Background: `url('../../shared/bg-title.png')` hoặc `url('../../shared/bg-content.jpg')`
- Logo: `src="../../shared/logo-white.png"`
- Hình riêng bài: `src="assets/ten-hinh.png"` (nằm cùng thư mục Lesson)

**Quy tắc bất di bất dịch**: Luôn dùng `../../` để trỏ lên `CNTT/`. KHÔNG BAO GIỜ dùng đường dẫn tuyệt đối.

---

## 2. KHUNG HTML CỦA MỘT BÀI SLIDE
Nếu số slide yêu cầu lớn, cần chia nhỏ theo từng batch để tránh lỗi 529, 502

Mỗi bài là **1 file HTML duy nhất** chứa tất cả slide. Cấu trúc tổng thể:

```html
<!DOCTYPE html>
<html lang="vi">
<!-- Đổi thành lang="en" nếu là bản tiếng Anh -->
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bài XX - Tên bài học</title>
<link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="../../template.css">
</head>
<body>

<!-- SLIDE 1: Trang bìa -->
<section class="slide slide-title-page" ...> ... </section>

<!-- SLIDE 2: Phân đoạn phần 1 -->
<section class="slide slide-section" ...> ... </section>

<!-- SLIDE 3-N: Các slide nội dung -->
<section class="slide slide-content" ...> ... </section>

<!-- SLIDE CUỐI: Thank You -->
<section class="slide slide-title-page" ...> Thank You! </section>

</body>
</html>
```

**Quan trọng**:
- Font bắt buộc: **Open Sans** (Google Fonts link ở trên). KHÔNG dùng Inter, Raleway, Roboto hay bất kỳ font nào khác.
- Mỗi `<section class="slide">` là 1 trang slide (kích thước A4 ngang: 297mm × 210mm).
- Slide được đánh số liên tục từ 1 → N bằng `<span class="slide-num">`.
- Mỗi slide đều phải có: background-image (inline), logo, slide-num, slide-author.

---

## 2.5. NGUỒN NỘI DUNG — THƯ MỤC `yeu_cau/`

Nội dung slide được lấy từ thư mục `yeu_cau/` trong mỗi môn học.

**Quy trình tạo slide:**
1. **Kiểm tra** thư mục `yeu_cau/` có file PPTX tương ứng không (VD: `Lesson_01_Agile.pptx`)
2. **Nếu CÓ file PPTX**: Lấy nội dung từ PPTX gốc, chuyển thành HTML theo template này. Bổ sung thêm ví dụ thực tế, dẫn chứng, hộp xu hướng hiện đại
3. **Nếu KHÔNG CÓ file PPTX**: Tự tạo nội dung mới dựa trên tên bài, đề cương môn học (nếu có), và kiến thức chuyên ngành. Đảm bảo nội dung đầy đủ, có ví dụ thực tế, dẫn chứng

**Tài liệu hỗ trợ trong `yeu_cau/`:**
- File PPTX gốc (`Lesson_XX_*.pptx`) — nguồn nội dung chính
- Đề cương môn học (`.docx`) — tham khảo phạm vi kiến thức
- Tài liệu PDF — tham khảo thêm
- Hình ảnh extract từ PPTX cũng lưu vào `assets/` của bài tương ứng

**Thứ tự ưu tiên:**
- **LUÔN tạo bản tiếng Việt (`index.html`) TRƯỚC**
- **CHỈ tạo bản tiếng Anh (`index_en.html`) SAU KHI** bản tiếng Việt đã được chốt (không còn thay đổi) và cần hỏi lại

---

## 3. 4 LOẠI SLIDE (có ví dụ đầy đủ)

### 3.1 SLIDE TRANG BÌA (Title Page) — Luôn là slide đầu tiên

Dùng cho: slide mở đầu bài giảng. Background xanh đậm, chữ trắng.

```html
<!-- ==================== SLIDE 1 ==================== -->
<section class="slide slide-title-page" style="background-image:url('../../shared/bg-title.png')">
  <img class="slide-logo" src="../../shared/logo-white.png" alt="CMC University">
  <div class="title-content">
    <h1>AGILE SCRUM TRONG<br>PHÁT TRIỂN PHẦN MỀM</h1>
    <p class="subtitle">Phương pháp phát triển linh hoạt trong thời đại AI</p>
  </div>
  <span class="slide-num" style="color:white;">1</span>
  <span class="slide-author">ThS. Nguyễn Việt Hưng - Trường Đại học CMC</span>
</section>
```

**Chi tiết**:
- `slide-title-page`: class bắt buộc → nền xanh, text trắng, logo góc phải trên
- `bg-title.png`: background slide bìa (xanh gradient có hoa văn)
- `<h1>`: Tiêu đề chính, **VIẾT HOA trực tiếp** trong HTML. Dùng `<br>` để xuống dòng nếu dài
- `<p class="subtitle">`: Phụ đề, viết thường, nhỏ hơn
- `slide-num` thêm `style="color:white;"` vì nền tối
- `slide-author`: Luôn ghi `ThS. Nguyễn Việt Hưng - Trường Đại học CMC` (bản tiếng Anh: `MSc. Nguyen Viet Hung - CMC University`)

### 3.2 SLIDE PHÂN ĐOẠN (Section Divider) — Đánh dấu đầu mỗi phần lớn

Dùng cho: chia bài thành các phần lớn (VD: Phần 1: Giới thiệu, Phần 2: Chi tiết...). Có thể kèm hình minh họa.

```html
<!-- ==================== SLIDE 5 ==================== -->
<section class="slide slide-section" style="background-image:url('../../shared/bg-content.jpg')">
  <img class="slide-logo" src="../../shared/logo-white.png" alt="CMC University">
  <div class="section-content">
    <img src="assets/scrum-board.png" alt="Scrum Board">
    <h1>SCRUM FRAMEWORK</h1>
    <p class="section-desc">Khung làm việc phổ biến nhất trong Agile, được sử dụng bởi hơn 87% tổ chức</p>
  </div>
  <span class="slide-num">5</span>
  <span class="slide-author">ThS. Nguyễn Việt Hưng - Trường Đại học CMC</span>
</section>
```

**Chi tiết**:
- `slide-section`: class bắt buộc → căn giữa tất cả nội dung
- `section-content`: chứa nội dung, căn giữa theo chiều dọc và ngang
- `<img>` trong section-content: hình minh họa (TÙY CHỌN, có thể bỏ nếu không cần)
- `<h1>`: Tiêu đề phần, **VIẾT HOA**, chữ xanh (#0070C0), to 58px
- `<p class="section-desc">`: Mô tả ngắn, chữ xám
- Background dùng `bg-content.jpg` (NỀN TRẮNG, không phải bg-title)

### 3.3 SLIDE NỘI DUNG (Content) — Phần chính của bài giảng

Dùng cho: trình bày kiến thức, ví dụ, bảng biểu, code... Chiếm phần lớn số slide.

```html
<!-- ==================== SLIDE 6 ==================== -->
<section class="slide slide-content" style="background-image:url('../../shared/bg-content.jpg')">
  <img class="slide-logo" src="../../shared/logo-white.png" alt="CMC University">
  <div class="slide-header"><h2>TUYÊN NGÔN AGILE (AGILE MANIFESTO - 2001)</h2></div>
  <div class="slide-body">

    <!-- === NỘI DUNG SLIDE ĐẶT Ở ĐÂY === -->

  </div>
  <span class="slide-num">6</span>
  <span class="slide-author">ThS. Nguyễn Việt Hưng - Trường Đại học CMC</span>
</section>
```

**Chi tiết**:
- `slide-content`: class bắt buộc → header xanh ở trên, body ở dưới
- `slide-header > h2`: Tiêu đề slide, **VIẾT HOA**, chữ trắng trên nền xanh. Tự co lại nếu dài (clamp 18px-28px). KHÔNG để tiêu đề tràn sang logo góc phải (`padding-right: 200px` đã xử lý)
- `slide-body`: Vùng nội dung chính. Đặt mọi thứ (text, bảng, hình, card...) ở đây
- Background **luôn** dùng `bg-content.jpg`

### 3.4 SLIDE THANK YOU — Luôn là slide cuối cùng

```html
<!-- ==================== SLIDE 39 ==================== -->
<section class="slide slide-title-page" style="background-image:url('../../shared/bg-title.png'); justify-content:center; text-align:center; flex-direction:column; align-items:center;">
  <img src="../../shared/logo-white.png" alt="CMC University" style="height:80px; margin-bottom:30px;">
  <h1 style="font-family:'Open Sans',sans-serif; font-size:72px; font-weight:700; color:white; text-shadow:2px 3px 10px rgba(0,0,0,0.4);">Thank You!</h1>
  <p style="font-size:22px; color:white; margin-top:40px; font-weight:400;">Bài tiếp theo: Software Design Document (SDD)</p>
  <span class="slide-num" style="color:rgba(255,255,255,0.7);">39</span>
  <span class="slide-author" style="color:rgba(255,255,255,0.7);">ThS. Nguyễn Việt Hưng - Trường Đại học CMC</span>
</section>
```

**Chi tiết**:
- Dùng class `slide-title-page` (cùng nền xanh như trang bìa), nhưng thêm inline style để căn giữa
- Logo ở giữa (KHÔNG dùng class `slide-logo` — logo lớn hơn, 80px)
- "Thank You!" là `<h1>` inline style, 72px
- Ghi tên bài tiếp theo (nếu có) hoặc bỏ dòng đó
- `slide-num` và `slide-author` thêm `color:rgba(255,255,255,0.7)` cho mờ nhẹ

---

## 4. CÁC COMPONENT NỘI DUNG (đặt bên trong `slide-body`)

Dưới đây là tất cả component có sẵn trong CSS. Chọn component phù hợp với nội dung.

### 4.1 Layout 2 cột (two-columns) — ƯU TIÊN SỬ DỤNG

```html
<div class="two-columns">
  <div class="col">
    <!-- Cột trái: text, danh sách, card... -->
    <h3>Tiêu đề phần</h3>
    <ul>
      <li>Điểm 1</li>
      <li>Điểm 2</li>
    </ul>
  </div>
  <div class="col">
    <!-- Cột phải: text, danh sách, card... -->
  </div>
</div>
```

Hoặc cột ảnh (1 cột text + 1 cột hình):
```html
<div class="two-columns">
  <div class="col" style="flex:1.4;">
    <h3>Nội dung chính</h3>
    <p>Giải thích chi tiết...</p>
  </div>
  <div class="col-img">
    <img src="assets/ten-hinh.png" alt="Mô tả">
    <p class="img-caption">Tên hình<br>
      <a href="https://source-url.com" target="_blank">Nguồn: Tên</a>
    </p>
  </div>
</div>
```

**Quy tắc**:
- `col`: cột text, chiều rộng tự chia đều (flex: 1)
- `col-img`: cột hình, chiếm 38% chiều rộng. Hình tự thu nhỏ vừa cột
- `style="flex:1.4;"`: làm cột text rộng hơn (tùy chọn)
- Gap giữa 2 cột: 3% (CSS đã xử lý)
- **Luôn ưu tiên 2 cột** trừ khi nội dung là bảng rộng hoặc danh sách rất dài

### 4.2 Thẻ Card — Hiển thị nhóm thông tin

```html
<div class="cards">
  <div class="card">
    <h4>Tiêu đề card 1</h4>
    <p>Nội dung card 1</p>
  </div>
  <div class="card accent-orange">
    <h4>Tiêu đề card 2</h4>
    <ul>
      <li>Điểm 1</li>
      <li>Điểm 2</li>
    </ul>
  </div>
  <div class="card accent-green">
    <h4>Tiêu đề card 3</h4>
    <p>Nội dung card 3</p>
  </div>
</div>
```

**Màu sắc card** (thêm class phụ):
| Class | Viền trái + Tiêu đề | Khi nào dùng |
|-------|---------------------|-------------|
| (mặc định) | Xanh dương #4472C4 | Thông tin chung |
| `accent-orange` | Cam #ED7D31 | Cảnh báo, quan trọng |
| `accent-green` | Xanh lá #70AD47 | Ưu điểm, thành công |
| `accent-gold` | Vàng #FFC000 | Lưu ý, gợi ý |
| `accent-purple` | Tím #7C4DFF | Nâng cao, đặc biệt |

Card tự chia đều chiều rộng (`flex: 1`). Thường dùng 2-4 card mỗi hàng.

### 4.3 Bảng (Table)

```html
<table>
  <thead>
    <tr>
      <th style="width:20%">Tiêu chí</th>
      <th style="width:40%">Agile</th>
      <th style="width:40%">Waterfall</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Tính linh hoạt</td>
      <td>Cao, dễ thay đổi</td>
      <td>Thấp, khó thay đổi</td>
    </tr>
    <tr>
      <td>Rủi ro</td>
      <td>Phát hiện sớm qua mỗi sprint</td>
      <td>Phát hiện muộn, ở giai đoạn cuối</td>
    </tr>
  </tbody>
</table>
```

**Chi tiết**:
- `<th>`: nền xanh (#4472C4), chữ trắng, header bảng
- `<td>` cột đầu tiên: tự động in đậm, chữ xanh, nền xanh nhạt (CSS đã xử lý)
- Hàng chẵn: nền xanh rất nhạt (zebra stripe)
- Dùng `style="width:XX%"` trên `<th>` để chia cột
- Thêm class `table-small` vào `<table>` nếu bảng nhiều cột cần chữ nhỏ hơn (14.5px)

### 4.4 Steps (Quy trình từng bước)

```html
<div class="steps">
  <div class="step">
    <div class="step-num">1</div>
    <div class="step-content">
      <h4>Product Backlog</h4>
      <p>PO tạo danh sách tất cả tính năng, sắp xếp theo độ ưu tiên</p>
    </div>
  </div>
  <div class="step">
    <div class="step-num">2</div>
    <div class="step-content">
      <h4>Sprint Planning</h4>
      <p>Đội chọn items từ Backlog cho sprint (2-4 tuần)</p>
    </div>
  </div>
  <div class="step">
    <div class="step-num">3</div>
    <div class="step-content">
      <h4>Sprint Review</h4>
      <p>Demo sản phẩm cho stakeholders, nhận feedback</p>
    </div>
  </div>
</div>
```

**Chi tiết**:
- `step-num`: số tròn xanh, chữ trắng (42px × 42px)
- `step-content > h4`: tiêu đề bước, xanh dương
- `step-content > p`: mô tả bước
- Phù hợp cho quy trình, lifecycle, các bước tuần tự

### 4.5 Quote Box (Trích dẫn)

```html
<div class="quote-box">
  <p>"Simplicity — the art of maximizing the amount of work not done — is essential."</p>
  <p style="font-size:14px; color:#666; margin-top:6px;">— Agile Manifesto, Principle #10</p>
</div>
```

Dùng cho: trích dẫn nổi bật, định nghĩa quan trọng. Viền xanh bên trái, nền xanh nhạt, chữ nghiêng.

### 4.6 Hộp Xu hướng hiện đại (Trend Box)

```html
<div class="ai-box">
  <div class="ai-label">&#x2728; XU HƯỚNG HIỆN ĐẠI</div>
  <p><strong>GitHub Copilot</strong> tăng tốc code 40-55%
    <a class="ref" href="https://github.blog/news-insights/research/..." target="_blank">[GitHub Research]</a>,
    <strong>AI Testing</strong> tự động phát hiện regression → release nhanh hơn.
  </p>
</div>
```

**Quy tắc**:
- Đặt ở **cuối** `slide-body`, sau nội dung chính
- Mỗi slide **tối đa 1** hộp (không bắt buộc phải có)
- KHÔNG chiếm quá 20% diện tích slide
- Phải có **dẫn chứng nguồn** (class `ref`) nếu nêu số liệu
- Tiêu đề cố định: `&#x2728; XU HƯỚNG HIỆN ĐẠI` (có emoji ✨)
- KHÔNG ghi "AI" trong tiêu đề hộp

### 4.7 Highlight text (Nhấn mạnh trong đoạn văn)

```html
<p>Scrum là <span class="highlight">framework phổ biến nhất</span> trong Agile,
được áp dụng bởi <span class="accent">87% tổ chức</span> toàn cầu.</p>
```

- `highlight`: in đậm, xanh dương (#0070C0)
- `accent`: in đậm, cam (#ED7D31)

### 4.8 Reference link (Dẫn nguồn)

```html
<a class="ref" href="https://digital.ai/resource-center/analyst-reports/state-of-agile-report/" target="_blank">[Digital.ai]</a>
```

Hiển thị nhỏ (11px), xám (#888), không gạch chân. Đặt ngay sau câu có số liệu/dẫn chứng.

---

## 5. QUY TẮC VIẾT NỘI DUNG

### 5.1 Tiêu đề — VIẾT HOA trực tiếp trong HTML

| Loại | Cách viết | Ví dụ |
|------|-----------|-------|
| h1 (bìa, phân đoạn) | VIẾT HOA trong HTML | `<h1>AGILE SCRUM TRONG PHÁT TRIỂN PHẦN MỀM</h1>` |
| h2 (header slide nội dung) | VIẾT HOA trong HTML | `<h2>TUYÊN NGÔN AGILE (AGILE MANIFESTO - 2001)</h2>` |
| h3, h4 (trong slide-body) | Viết thường, in đậm | `<h3>Vai trò Product Owner</h3>` |

**TUYỆT ĐỐI KHÔNG** dùng CSS `text-transform: uppercase` — tiếng Việt sẽ mất dấu (ĐẠI → DAI).

### 5.2 Font chữ — BẮT BUỘC Open Sans

- Font duy nhất: **Open Sans** từ Google Fonts
- Link: `https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500;600;700&display=swap`
- **KHÔNG** dùng Inter (lỗi dấu tiếng Việt khi viết hoa)
- **KHÔNG** dùng Raleway, Roboto hay bất kỳ font nào khác trong mọi inline style
- Nếu cần ghi font trong inline style: `font-family:'Open Sans',sans-serif;`

### 5.3 Ngôn ngữ

**Bản tiếng Việt** (`index.html`, `lang="vi"`) — TẠO TRƯỚC:
- Nội dung chính bằng **tiếng Việt**
- Thuật ngữ chuyên ngành giữ **tiếng Anh trong ngoặc**: "Kiến trúc 3 tầng (Three-tier Architecture)"
- Tiêu đề có thể song ngữ: `TUYÊN NGÔN AGILE (AGILE MANIFESTO - 2001)`
- Tác giả: `ThS. Nguyễn Việt Hưng - Trường Đại học CMC`

**Bản tiếng Anh** (`index_en.html`, `lang="en"`) — TẠO SAU khi tiếng Việt đã hoàn tất:
- Chỉ tạo bản tiếng Anh **sau khi bản tiếng Việt đã hoàn chỉnh và kiểm tra xong**
- Toàn bộ nội dung dịch sang tiếng Anh, giữ nguyên cấu trúc HTML và đường dẫn
- Tác giả: `MSc. Nguyen Viet Hung - CMC University`
- Hộp xu hướng: `MODERN TRENDS` thay vì `XU HƯỚNG HIỆN ĐẠI`
- Giữ nguyên: code block, URL, tên riêng (Scrum, Sprint, Agile...)

### 5.4 Layout — Ưu tiên 2 cột

- **Luôn ưu tiên** layout 2 cột (`two-columns`) để slide không trống
- Slide 1 cột chỉ khi: bảng rộng, danh sách rất dài, hoặc nội dung đặc biệt
- **KHÔNG** để slide trống nhiều — nội dung phải bao phủ ≥ 70% diện tích
- Khi dùng `col-img`: hình phải có caption + nguồn

### 5.5 Số slide

- Đánh số liên tục từ 1 → N (slide-num)
- Slide 1: Trang bìa
- Slide cuối: Thank You
- Dùng comment `<!-- ==================== SLIDE N ==================== -->` trước mỗi section để dễ đọc

---

## 6. QUY TẮC HÌNH ẢNH

### 6.1 Logo CMC (tự động có trên mọi slide)
```html
<img class="slide-logo" src="../../shared/logo-white.png" alt="CMC University">
```
- Nằm góc phải trên (CSS absolute position)
- **Mọi slide đều phải có** — KHÔNG được bỏ

### 6.2 Hình minh họa
- Đặt trong thư mục `assets/` của mỗi Lesson
- Ưu tiên hình từ **PPTX gốc** (nếu có, đã extract vào assets/)
- Nếu cần hình mới: **tải về `assets/` trước**, KHÔNG nhúng URL trực tiếp từ internet
- **KHÔNG** dùng cùng 1 hình cho 2 slide khác nhau
- Tên file rõ nghĩa: `three-tier.svg`, `scrum-board.png`, `erd-example.png`

### 6.3 Quy trình tải hình từ internet
1. Tìm hình phù hợp (Wikimedia Commons, tech blog...)
2. Tải về thư mục `assets/`: `curl -o assets/ten-hinh.png "URL"`
3. Kiểm tra file thực sự là ảnh: `file assets/ten-hinh.png` → phải là PNG/JPEG/SVG, không phải HTML
4. Dùng đường dẫn local: `src="assets/ten-hinh.png"`
5. Ghi credit trong caption

### 6.4 Caption hình ảnh (BẮT BUỘC cho mọi hình minh họa)
```html
<div class="col-img">
  <img src="assets/scrum-board.png" alt="Scrum Board">
  <p class="img-caption">Scrum Board ví dụ<br>
    <a href="https://en.wikipedia.org/wiki/Scrum_(software_development)" target="_blank">Nguồn: Wikipedia</a>
  </p>
</div>
```

- Hình từ PPTX gốc: chỉ cần tên hình, không cần link
- Hình từ internet: **bắt buộc** ghi URL gốc
- Caption nhỏ (11px), nguồn nhỏ hơn (10px, xám #aaa)

---

## 7. QUY TẮC DẪN CHỨNG

### 7.1 Mọi số liệu phải có nguồn
```html
<p>Hơn 80% tổ chức sử dụng Agile
  <a class="ref" href="https://digital.ai/resource-center/analyst-reports/state-of-agile-report/" target="_blank">[Digital.ai]</a>
</p>
```

### 7.2 Ví dụ thực tế phải có dẫn chứng
- Mỗi khái niệm quan trọng cần **ví dụ thực tế** từ công ty/dự án thực
- VD: "Netflix dùng microservices..." → phải kèm link blog Netflix
- **KHÔNG** dùng ví dụ chung chung không có nguồn
- Kiểm tra URL còn hoạt động trước khi dùng

### 7.3 Nguồn uy tín ưu tiên
✅ **Nên dùng**: IEEE Standards, Wikipedia, Martin Fowler, Atlassian, engineering blog (Netflix, Spotify, Grab, Google), NIST, NASA, OWASP
❌ **TRÁNH**: FPT Techday (link chết), Samsung Research VN (lỗi server), Standish Group (PDF bị xóa)

---

## 8. BACKGROUND IMAGE

Background **PHẢI** đặt inline trong HTML attribute `style`, KHÔNG đặt trong CSS.

```html
<!-- Slide bìa/Thank You → dùng bg-title.png (xanh đậm) -->
<section class="slide slide-title-page" style="background-image:url('../../shared/bg-title.png')">

<!-- Slide nội dung/phân đoạn → dùng bg-content.jpg (trắng) -->
<section class="slide slide-content" style="background-image:url('../../shared/bg-content.jpg')">
<section class="slide slide-section" style="background-image:url('../../shared/bg-content.jpg')">
```

**Lý do**: CSS dùng đường dẫn tương đối từ vị trí file CSS (CNTT/), nhưng HTML dùng đường dẫn từ vị trí file HTML (CNTT/MonHoc/Lesson_XX/). Nếu đặt trong CSS sẽ sai đường dẫn.

---

## 9. CHECKLIST KIỂM TRA CHẤT LƯỢNG

Trước khi hoàn thành mỗi bài, kiểm tra **tất cả** các mục sau:

**Cấu trúc:**
- [ ] Slide đầu tiên là trang bìa (`slide-title-page` + `bg-title.png`)
- [ ] Slide cuối cùng là Thank You (`slide-title-page` + `bg-title.png`)
- [ ] Số slide liên tục 1 → N, không trùng, không nhảy
- [ ] Mỗi slide có đủ: `background-image`, `slide-logo`, `slide-num`, `slide-author`

**Tiêu đề:**
- [ ] h1, h2 đã VIẾT HOA trực tiếp trong HTML (không dùng CSS text-transform)
- [ ] h2 trong slide-header không quá dài (tránh tràn logo)

**Font & Style:**
- [ ] Google Fonts link là Open Sans (không phải Inter, Raleway...)
- [ ] Mọi inline style font-family đều là `'Open Sans',sans-serif`

**Hình ảnh:**
- [ ] Mọi hình minh họa có caption + dẫn nguồn
- [ ] Không có 2 slide dùng cùng 1 hình
- [ ] Hình dùng đường dẫn local (`assets/...`), không phải URL internet

**Nội dung:**
- [ ] Số liệu thống kê có ref link
- [ ] Ví dụ thực tế có dẫn chứng
- [ ] Nội dung bao phủ slide đầy đủ (≥ 70%)
- [ ] Ưu tiên layout 2 cột

**Đường dẫn:**
- [ ] CSS: `href="../../template.css"`
- [ ] Background: `url('../../shared/...')`
- [ ] Logo: `src="../../shared/logo-white.png"`

---

## 10. THÔNG TIN CỐ ĐỊNH (KHÔNG THAY ĐỔI)

| Thông tin | Giá trị |
|-----------|---------|
| Tác giả (VN) | `ThS. Nguyễn Việt Hưng - Trường Đại học CMC` |
| Tác giả (EN) | `MSc. Nguyen Viet Hung - CMC University` |
| CSS file | `../../template.css` |
| Background bìa | `../../shared/bg-title.png` |
| Background nội dung | `../../shared/bg-content.jpg` |
| Logo trắng | `../../shared/logo-white.png` |
| Font | Open Sans (Google Fonts) |
| Kích thước slide | 297mm × 210mm (A4 ngang) |

**Lưu ý**: Tất cả asset dùng chung nằm trong `CNTT/shared/`. KHÔNG copy vào từng Lesson. Mỗi Lesson chỉ lưu hình minh họa riêng trong `assets/`.

---

## 11. QUY ƯỚC CHO MÔN FLUTTER / DART (đã thực hiện)

Khi tạo slide cho môn Lập trình đa nền tảng với Flutter:

| Tiêu chí | Quy ước |
|-----------|---------|
| Số bài học | 6 bài (Lesson_01 → Lesson_06) |
| Tên thư mục | `Lesson_01_MobileOverview/`, `Lesson_02_CrossPlatform/`, `Lesson_03_DartBasics/`, `Lesson_04_OOPDart/`, `Lesson_05_FlutterState/`, `Lesson_06_Navigation/` |
| Đường dẫn CSS | `../../template.css` |
| Thuật ngữ kỹ thuật | Giữ nguyên tiếng Anh: Flutter, Dart, Android, iOS, SDK, JIT, AOT, API, MVC, MVVM, Provider, Riverpod, GetX, Redux, Widget, State, StatelessWidget, StatefulWidget, async/await, Future, Navigator, Routing, GoRouter... |
| Tiêu đề slide | VIẾT HOA (tiếng Việt) |
| Code examples | Dùng `quote-box` với `font-family:monospace;font-size:13px;` — KHÔNG dùng `<pre><code>` |
| Hộp xu hướng | Flutter + AI, Firebase Genkit, GoRouter, Riverpod, Clean Architecture |

**Bản tiếng Anh (`index_en.html`):** CHỈ tạo SAU KHI bản tiếng Việt đã chốt. Nội dung dịch nguyên structure HTML, giữ nguyên code, giữ nguyên technical terms.

---

## 12. QUY TẮC QUẢN LÝ TOKEN ĐỂ TRÁNH PROMPT TOO LONG

> **Vấn đề**: Session compaction summary chứa toàn bộ lịch sử hàng chục phiên làm việc → prompt trở nên quá dài → lỗi "Prompt is too long".

### 12.1 Nguyên tắc vàng

1. **Viết mỗi batch TỐI ĐA 10 slides** (Edit 10 slides mỗi lần)
2. **Dùng `/clear` TRƯỚC khi chuyển sang bài/lesson mới** — xóa context bài cũ, giữ session nhẹ
3. **Prompt ngắn gọn** — chỉ cần: "Viết batch tiếp theo: slides 11-20" thay vì giải thích dài

### 12.2 Chiến lược batch cho mỗi bài (50 slides)

| Giai đoạn | Slides | Số lần Edit |
|-----------|--------|-------------|
| Batch 1 | 1-10 | 1 |
| Batch 2 | 11-20 | 1 |
| Batch 3 | 21-30 | 1 |
| Batch 4 | 31-40 | 1 |
| Batch 5 | 41-50 | 1 |
| **Tổng** | **50** | **5 lần Edit** |

### 12.3 Prompt mẫu cho từng batch

**Batch đầu tiên (slides 1-10):**
```
Viết 10 slides đầu tiên (1-10) cho Bài XX: [Tên bài].
File: /đường/dẫn/index.html
Nội dung từ PPTX/Chương_X.
Cấu trúc: slide 1 bìa, slide 2 phân đoạn, slides 3-10 nội dung.
```

**Các batch tiếp theo:**
```
Tiếp tục: viết slides 11-20 cho Bài XX.
```

### 12.4 Khi nào dùng /clear

| Tình huống | Hành động |
|-----------|-----------|
| Chuyển từ Lesson_A sang Lesson_B | `/clear` trước khi prompt mới |
| Chuyển từ môn A sang môn B | `/clear` bắt buộc |
| Sau mỗi ~25-30 slides viết xong | Kiểm tra token, `/clear` nếu cần |
| Gặp lỗi "Prompt is too long" | `/clear` ngay, viết lại batch đang dang dở |

### 12.5 Đọc nội dung PPTX — trước batch đầu tiên

Đọc PPTX bằng Python (python-pptx) để trích nội dung TRƯỚC khi viết batch đầu tiên, lưu vào biến hoặc ghi chú trong prompt. Không đọc lại PPTX trong mỗi batch — tốn token.

### 12.6 Checklist trước mỗi session

- [ ] Xác định bài đang viết: Lesson_XX, slides nào còn thiếu
- [ ] Chạy `/clear` nếu bắt đầu bài mới hoặc môn mới
- [ ] Prompt viết batch ≤ 10 slides
- [ ] Sau khi viết xong mỗi batch: xác nhận slide-num đúng, không trùng

**Tóm tắt**: Batch nhỏ + /clear giữa các bài + Prompt ngắn = không bao giờ "Prompt too long".
