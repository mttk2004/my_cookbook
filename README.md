# Sổ Tay Công Thức Nấu Ăn

Dự án LaTeX cho sổ tay nấu ăn với cấu trúc modular, dễ dàng cấu hình và bảo trì.

## 📁 Cấu trúc thư mục

```
my_cookbook/
├── config/                 # Thư mục chứa các file cấu hình
│   ├── packages.tex        # Các gói tiện ích (graphicx, xcolor, tikz, ...)
│   ├── page_setup.tex      # Cấu hình khổ giấy và căn lề
│   ├── fonts.tex           # Cấu hình font chữ và tiếng Việt
│   ├── headers.tex         # Thiết lập header/footer
│   └── styles.tex          # Macro tùy chỉnh (\monan, chapter style, ...)
├── frontmatter/            # Thư mục chứa phần đầu sách
│   └── titlepage.tex       # Trang bìa tự thiết kế
├── chapters/               # Thư mục chứa các chương
│   ├── 01_uop_thit.tex
│   ├── 02_mon_mi_bun.tex
│   ├── 03_mon_xao.tex
│   ├── 04_mon_nuong.tex
│   ├── 05_mon_luoc_ham.tex
│   ├── 06_mon_trung.tex
│   └── 07_mon_phu.tex
└── main.tex                # File chính (gọn gàng, chỉ include các module)
```

## 🚀 Biên dịch

```bash
# Sử dụng script có sẵn
./compile.sh

# Hoặc biên dịch thủ công bằng XeLaTeX
xelatex main.tex
xelatex main.tex  # Chạy lần 2 để cập nhật mục lục
```

## 📝 Hướng dẫn chỉnh sửa

### 1. Thay đổi kích thước trang và lề

Mở file `config/page_setup.tex` và chỉnh sửa các thông số:

```latex
\usepackage[
    a5paper,        % Thay đổi khổ giấy (a4paper, a5paper, letterpaper, ...)
    inner=2cm,      % Lề trong (gần gáy sách)
    outer=0.5cm,    # Lề ngoài
    top=1.5cm,      # Lề trên
    bottom=1.5cm    # Lề dưới
]{geometry}
```

### 2. Thay đổi font chữ

Mở file `config/fonts.tex`:

```latex
% Thay đổi font chính
\setmainfont{FreeSerif}        % Đổi thành font khác như: Times New Roman, Arial, ...
\setsansfont{FreeSans}
\setmonofont{FreeMono}

% Điều chỉnh kích thước font
\renewcommand{\normalsize}{\fontsize{9}{10.8}\selectfont}  % Thay đổi con số
```

### 3. Tùy chỉnh header/footer

Mở file `config/headers.tex`:

```latex
\fancyhead[LE,RO]{\textbf{\thepage}}           # Số trang
\fancyhead[RE]{\itshape\nouppercase{\leftmark}}  # Tên chapter
\fancyhead[LO]{\itshape\nouppercase{\rightmark}} # Tên section
```

### 4. Thêm/bớt gói LaTeX

Mở file `config/packages.tex` và thêm/xóa các dòng `\usepackage{...}`

### 5. Chỉnh sửa trang bìa

Mở file `frontmatter/titlepage.tex` để thay đổi:
- Tiêu đề sách
- Tên tác giả
- Màu sắc và trang trí
- Vị trí các phần tử

### 6. Thêm món ăn mới

Mở file chương tương ứng trong `chapters/` và sử dụng macro `\monan`:

```latex
\monan{Tên món ăn}{
    % Nguyên liệu
    \item 500g thịt ba chỉ
    \item 2 quả trứng
    \item 2 củ hành
}{
    % Sơ chế (để trống {} nếu không có)
    \item Luộc thịt sơ qua
    \item Bóc vỏ trứng
}{
    % Chế biến
    \item Kho thịt với nước dừa
    \item Thêm trứng vào
    \item Nêm gia vị
}
```

### 7. Tạo chương mới

1. Tạo file mới trong `chapters/`, ví dụ: `08_mon_canh.tex`
2. Viết nội dung:
```latex
\chapter{Món Canh}

\monan{Canh Chua}{
    \item 200g cá
    \item Rau muống
}{}{
    \item Nấu nước dùng
    \item Thêm cá và rau
}
```
3. Thêm vào `main.tex`:
```latex
\include{chapters/08_mon_canh}
```

## 🎨 Tùy chỉnh macro \monan

Nếu muốn thay đổi cách hiển thị công thức món ăn, mở file `config/styles.tex` và chỉnh sửa định nghĩa `\newcommand{\monan}[4]{...}`

Ví dụ:
- Đổi màu sắc: `\color{brown!80!black}` → `\color{blue}`
- Đổi ký hiệu bullet: `$\bullet$` → `$\star$`
- Thay đổi khoảng cách: `\vspace{0.2cm}` → `\vspace{0.5cm}`

## 🔧 Yêu cầu hệ thống

- **LaTeX Distribution**: TeX Live hoặc MiKTeX
- **Engine**: XeLaTeX (hỗ trợ Unicode và font hiện đại)
- **Fonts**: FreeSerif, FreeSans, FreeMono (thường có sẵn)

## 💡 Lợi ích của cấu trúc modular

1. **Dễ bảo trì**: Mỗi phần cấu hình nằm ở file riêng
2. **Tái sử dụng**: Copy file config sang dự án khác
3. **Dễ debug**: Biết chính xác file nào chứa phần cần sửa
4. **Làm việc nhóm**: Nhiều người có thể edit các file khác nhau
5. **Rõ ràng**: File `main.tex` ngắn gọn, dễ hiểu

## 📚 Tài liệu tham khảo

- [LaTeX Documentation](https://www.latex-project.org/help/documentation/)
- [Overleaf Tutorials](https://www.overleaf.com/learn)
- [TikZ Manual](https://tikz.dev/)

## 👤 Tác giả

**Mai Tran Tuan Kiet**

---

*Được tạo với ❤️ sử dụng LaTeX*