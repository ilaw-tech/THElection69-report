# Scatter Formula Regions — GitHub Pages Embed Pack

12 ไฟล์ HTML กราฟ scatter `y = αx + b + ε` รายภูมิภาค พร้อม embed ลง WordPress ผ่าน iframe

## โครงสร้างไฟล์

| ไฟล์ | ภูมิภาค | ประเภทบัตร |
|---|---|---|
| `national-partylist.html` | ทั้งประเทศ | บัญชีรายชื่อ |
| `national-constituency.html` | ทั้งประเทศ | แบ่งเขต |
| `north-partylist.html` | ภาคเหนือ | บัญชีรายชื่อ |
| `north-constituency.html` | ภาคเหนือ | แบ่งเขต |
| `isan-partylist.html` | ภาคอีสาน | บัญชีรายชื่อ |
| `isan-constituency.html` | ภาคอีสาน | แบ่งเขต |
| `central-partylist.html` | ภาคกลาง | บัญชีรายชื่อ |
| `central-constituency.html` | ภาคกลาง | แบ่งเขต |
| `bkk-partylist.html` | กรุงเทพและปริมณฑล | บัญชีรายชื่อ |
| `bkk-constituency.html` | กรุงเทพและปริมณฑล | แบ่งเขต |
| `south-partylist.html` | ภาคใต้ | บัญชีรายชื่อ |
| `south-constituency.html` | ภาคใต้ | แบ่งเขต |
| `index.html` | preview รวม + ปุ่มคัดลอก embed |

---

## Deploy ขึ้น GitHub Pages — 5 ขั้นตอน

### ขั้นที่ 1: สร้าง GitHub Repository ใหม่

1. ไปที่ https://github.com/new
2. ตั้งชื่อ repo: `ilaw-election-embeds` (หรือชื่ออื่น — จำชื่อไว้)
3. เลือก **Public** (ต้อง public เพื่อให้ GitHub Pages ใช้ฟรีได้)
4. **อย่าเช็ค** "Add a README" — เราจะ push ของเราขึ้นเอง
5. กด "Create repository"

### ขั้นที่ 2: ลบ `.git` folder ที่ค้างอยู่ (ถ้ามี)

เปิด PowerShell ในโฟลเดอร์นี้ แล้วรัน:

```powershell
cd "C:\Users\lenovo\Desktop\ilaw\THElection2026\embeds\scatter-formula"
Remove-Item -Recurse -Force .git -ErrorAction SilentlyContinue
```

### ขั้นที่ 3: รัน deploy script

```powershell
.\deploy.ps1
```

สคริปต์จะถาม URL ของ repo ที่สร้างไว้ในขั้นที่ 1 — copy URL จาก GitHub (รูปแบบ `https://github.com/USERNAME/ilaw-election-embeds.git`) แล้วแปะ

### ขั้นที่ 4: เปิด GitHub Pages

1. ไปที่ repo บน GitHub → **Settings** → **Pages** (เมนูซ้าย)
2. ที่ "Build and deployment" → **Source: Deploy from a branch**
3. Branch: **main** / folder: **/(root)** → **Save**
4. รอประมาณ 1-2 นาที — refresh หน้านี้แล้วจะเห็น URL: `https://USERNAME.github.io/ilaw-election-embeds/`

### ขั้นที่ 5: เอา URL ไป embed บน WordPress

ใส่ใน Custom HTML block ของ WP:

```html
<iframe src="https://USERNAME.github.io/ilaw-election-embeds/national-partylist.html"
        width="100%" height="640" frameborder="0" style="border:none"
        loading="lazy"></iframe>
```

เปลี่ยน `USERNAME` กับชื่อไฟล์ตามที่ต้องการ embed

---

## อัปเดตไฟล์ทีหลัง

ถ้าแก้กราฟ → push ใหม่:

```powershell
cd "C:\Users\lenovo\Desktop\ilaw\THElection2026\embeds\scatter-formula"
git add .
git commit -m "Update charts"
git push
```

GitHub Pages จะ auto-update ภายใน 1-2 นาที

---

## หมายเหตุ

- ไฟล์ใหญ่สุดคือ `national-partylist.html` (1.8 MB) — ยังอยู่ในขีดจำกัดของ GitHub Pages (file size limit 100 MB ต่อไฟล์, repo total <1 GB)
- Plotly โหลดจาก CDN (`cdn.plot.ly`) — ไม่ต้อง host เอง
- ฟ้อนต์ Noto Sans Thai โหลดจาก Google Fonts
- ไฟล์ทั้งหมด responsive — ใช้บนมือถือได้
