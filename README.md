<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>تقديم بيانات الطلاب</title>
<style>
  * { margin:0; padding:0; box-sizing:border-box; font-family:'Segoe UI', Tahoma, sans-serif; }
  body {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
    padding: 20px;
    color: #333;
  }
  .container { max-width: 900px; margin: 0 auto; }
  .header {
    background: #fff;
    padding: 25px;
    border-radius: 15px;
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
    margin-bottom: 25px;
  }
  .header h1 { color: #4a3f8f; font-size: 28px; margin-bottom: 8px; }
  .header p { color: #666; font-size: 15px; }

  .card {
    background: #fff;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.15);
    margin-bottom: 25px;
  }
  .card h2 {
    color: #4a3f8f;
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 2px solid #eee;
    font-size: 22px;
  }

  .form-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 18px;
  }
  .form-group label {
    display: block;
    margin-bottom: 6px;
    font-weight: 600;
    color: #4a3f8f;
    font-size: 14px;
  }
  .form-group input, .form-group select {
    width: 100%;
    padding: 12px 14px;
    border: 2px solid #e0e0e0;
    border-radius: 10px;
    font-size: 15px;
    transition: all 0.3s;
    background: #fafafa;
  }
  .form-group input:focus, .form-group select:focus {
    outline: none;
    border-color: #667eea;
    background: #fff;
    box-shadow: 0 0 0 3px rgba(102,126,234,0.15);
  }
  .optional-tag {
    font-size: 11px;
    color: #999;
    font-weight: normal;
    margin-right: 5px;
  }

  .buttons {
    display: flex;
    gap: 12px;
    margin-top: 25px;
    flex-wrap: wrap;
  }
  .btn {
    padding: 12px 28px;
    border: none;
    border-radius: 10px;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }
  .btn-primary { background: linear-gradient(135deg, #667eea, #764ba2); color: #fff; }
  .btn-danger  { background: linear-gradient(135deg, #eb3349, #f45c43); color: #fff; }
  .btn:hover { transform: translateY(-2px); box-shadow: 0 8px 20px rgba(0,0,0,0.2); }

  .toast {
    position: fixed;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    padding: 14px 28px;
    background: #11998e;
    color: #fff;
    border-radius: 10px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    z-index: 9999;
    opacity: 0;
    transition: opacity 0.3s;
    font-weight: 600;
  }
  .toast.show { opacity: 1; }

  .success-msg {
    background: #d4edda;
    color: #155724;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    margin-top: 20px;
    display: none;
  }
  .success-msg h3 { margin-bottom: 8px; }

  @media (max-width: 600px) {
    .header h1 { font-size: 22px; }
    .card { padding: 20px; }
    .btn { padding: 10px 18px; font-size: 14px; width: 100%; justify-content: center; }
  }
</style>
</head>
<body>
<div class="container">

  <div class="header">
    <h1>🎓 تقديم بيانات الطلاب</h1>
    <p>يرجى تعبئة النموذج التالي لتقديم بياناتك الدراسية</p>
  </div>

  <div class="card">
    <h2>📝 نموذج التقديم</h2>
    <form id="studentForm">
      <div class="form-grid">
        <div class="form-group">
          <label>الاسم الشخصي *</label>
          <input type="text" id="firstName" required placeholder="مثال: أحمد">
        </div>
        <div class="form-group">
          <label>الاسم الثلاثي *</label>
          <input type="text" id="fullName" required placeholder="الاسم الثلاثي الكامل">
        </div>
        <div class="form-group">
          <label>اسم الأب *</label>
          <input type="text" id="fatherName" required placeholder="اسم الأب">
        </div>
        <div class="form-group">
          <label>اسم الأم *</label>
          <input type="text" id="motherName" required placeholder="اسم الأم">
        </div>
        <div class="form-group">
          <label>سنة الدراسة *</label>
          <select id="studyYear" required>
            <option value="">-- اختر السنة الدراسية --</option>
            <optgroup label="المرحلة الابتدائية">
              <option>الصف الأول الابتدائي</option>
              <option>الصف الثاني الابتدائي</option>
              <option>الصف الثالث الابتدائي</option>
              <option>الصف الرابع الابتدائي</option>
              <option>الصف الخامس الابتدائي</option>
              <option>الصف السادس الابتدائي</option>
            </optgroup>
            <optgroup label="المرحلة الإعدادية">
              <option>الصف الأول الإعدادي</option>
              <option>الصف الثاني الإعدادي</option>
              <option>الصف الثالث الإعدادي</option>
            </optgroup>
            <optgroup label="المرحلة الثانوية">
              <option>الصف الأول الثانوي</option>
              <option>الصف الثاني الثانوي</option>
              <option>الصف الثالث الثانوي (البكالوريا)</option>
            </optgroup>
          </select>
        </div>
        <div class="form-group">
          <label>رقم الهاتف <span class="optional-tag">(اختياري)</span></label>
          <input type="tel" id="phone" placeholder="اختياري">
        </div>
        <div class="form-group">
          <label>المدينة <span class="optional-tag">(اختياري)</span></label>
          <select id="city">
            <option value="">-- اختر المدينة --</option>
            <option value="عفرين">عفرين</option>
            <option value="حلب">حلب</option>
            <option value="الحسكة">الحسكة</option>
            <option value="قامشلو">قامشلو</option>
          </select>
        </div>
        <div class="form-group">
          <label>الناحية / الضيعة <span class="optional-tag">(اختياري)</span></label>
          <input type="text" id="district" placeholder="اكتب اسم الناحية أو الضيعة">
        </div>
      </div>
      <div class="buttons">
        <button type="submit" class="btn btn-primary">📤 إرسال البيانات</button>
        <button type="reset" class="btn btn-danger">🗑️ مسح الحقول</button>
      </div>
    </form>

    <div id="successMsg" class="success-msg">
      <h3>✅ تم إرسال بياناتك بنجاح!</h3>
      <p>شكراً لك، سيتم مراجعة بياناتك من قبل الإدارة</p>
    </div>
  </div>

</div>

<div id="toast" class="toast"></div>

<script>
  const STORAGE_KEY = 'students_data_v1';

  function toast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.className = 'toast show';
    setTimeout(() => t.className = 'toast', 2500);
  }

  document.getElementById('studentForm').addEventListener('submit', (e) => {
    e.preventDefault();
    const students = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
    const newStudent = {
      id: Date.now().toString(),
      firstName: document.getElementById('firstName').value.trim(),
      fullName: document.getElementById('fullName').value.trim(),
      fatherName: document.getElementById('fatherName').value.trim(),
      motherName: document.getElementById('motherName').value.trim(),
      studyYear: document.getElementById('studyYear').value,
      phone: document.getElementById('phone').value.trim(),
      city: document.getElementById('city').value,
      district: document.getElementById('district').value.trim(),
      date: new Date().toLocaleDateString('ar-EG')
    };
    students.push(newStudent);
    localStorage.setItem(STORAGE_KEY, JSON.stringify(students));

    document.getElementById('studentForm').reset();
    document.getElementById('successMsg').style.display = 'block';
    toast('✅ تم إرسال بياناتك بنجاح');
    window.scrollTo({ top: 0, behavior: 'smooth' });

    setTimeout(() => {
      document.getElementById('successMsg').style.display = 'none';
    }, 5000);
  });
</script>
</body>
</html>
