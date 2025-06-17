from zipfile import ZipFile
import os

# Create basic structure of the digital product store (HTML/CSS)
store_name = "noqta_digital"
base_dir = f"/mnt/data/{store_name}"
os.makedirs(base_dir, exist_ok=True)

# HTML content (simple homepage)
html_content = """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>نقطة رقمية</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>نقطة رقمية</h1>
    </header>
    <main>
        <section class="products">
            <h2>الكتب</h2>
            <div class="product">📘 اسم الكتاب - 5 ريال</div>

            <h2>الروايات</h2>
            <div class="product">📖 اسم الرواية - 3 ريال</div>

            <h2>الخدمات</h2>
            <div class="product">🔧 خدمة رفع نقاط سناب - 15 ريال</div>
        </section>
    </main>
    <footer>
        <p>مكتبة رقمية متكاملة لكل مايخص التجارة الالكترونية، كتب، خدمات، اشتراكات، والمزيد..</p>
        <div class="links">
            <h3>روابط مهمة</h3>
            <p>📞 تواصل معنا: <a href="https://wa.me/9669117918" target="_blank">واتساب</a></p>
        </div>
    </footer>
</body>
</html>
"""

# CSS content
css_content = """
body {
    font-family: 'Arial', sans-serif;
    background: #f4f4f4;
    color: #333;
    margin: 0;
    padding: 0;
    direction: rtl;
    text-align: right;
}

header {
    background: #222;
    color: white;
    padding: 20px;
    text-align: center;
}

.products {
    padding: 20px;
}

.product {
    background: white;
    padding: 15px;
    margin-bottom: 10px;
    border-radius: 5px;
}

footer {
    background: #222;
    color: white;
    padding: 20px;
    text-align: center;
}

a {
    color: #00ffcc;
    text-decoration: none;
}
"""

# Save files
with open(f"{base_dir}/index.html", "w", encoding="utf-8") as f:
    f.write(html_content)

with open(f"{base_dir}/style.css", "w", encoding="utf-8") as f:
    f.write(css_content)

# Create ZIP file
zip_path = f"{base_dir}.zip"
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(f"{base_dir}/index.html", arcname="index.html")
    zipf.write(f"{base_dir}/style.css", arcname="style.css")

zip_path
