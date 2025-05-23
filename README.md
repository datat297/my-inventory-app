<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>ระบบจัดเก็บสินค้า</title>
  <style>
    body { font-family: sans-serif; margin: 20px; background-color: #f9f9f9; }
    input, select, button { display: block; margin-bottom: 15px; width: 100%; padding: 10px; font-size: 16px; }
    h2 { color: #333; }
  </style>
</head>
<body>
  <h2>📦 ระบบจัดเก็บสินค้า (Barcode + Location)</h2>
  <form id="inventory-form">
    <label>📌 BARCODE SKU:</label>
    <input type="text" name="barcode" placeholder="สแกนหรือกรอกบาร์โค้ดสินค้า" required>

    <label>🔢 จำนวนกล่อง:CTN</label>
    <input type="number" name="quantity" placeholder="จำนวนกล่อง" required>

    <label>🚛 หมายเลขตู้คอนเทนเนอร์:CONTAINER</label>
    <input type="text" name="container" placeholder="กรอกหมายเลขตู้คอนเทนเนอร์" required>

    <label>📍 Barcode Location:</label>
    <input type="text" name="location" placeholder="RACK SCAN" required>

    <button type="submit">✅ SAVE</button>
  </form>
  <p id="status"></p>

  <script>
    const scriptURL = 'https://script.google.com/macros/s/AKfycbyE1VmOGb02Gcx_CljDLU0ml-s0cJBHgscRRD41b00R_kTk0hccqq0tpfaYQUrU4pRw/exec';
    const form = document.getElementById('inventory-form');
    const status = document.getElementById('status');

    form.addEventListener('submit', e => {
      e.preventDefault();
      const data = new FormData(form);
      fetch(scriptURL, { method: 'POST', body: data })
        .then(response => status.innerText = "✅ OK")
        .catch(error => status.innerText = "❌ ERROR");
      form.reset();
    });
  </script>
</body>
</html>
