# ☀️ SunnyWords — Học Tiếng Anh Hè Vui Nhộn

Chương trình học tiếng Anh 60 ngày hè dành cho trẻ em tiểu học (~7 tuổi).
Rèn luyện **Nghe – Nói – Phát âm – Từ vựng** với giao diện vui nhộn nhiều màu sắc.

---

## 📁 Cấu Trúc Dự Án

```
sunnywords/
├── index.html                    ← Trang chủ Landing Page
├── app.html                      ← App chính + onboarding
├── roadmap.html                  ← Lộ trình 60 ngày hè
├── vocab.html                    ← Học từ vựng theo chủ đề
├── listening.html                ← Luyện kỹ năng nghe
├── speaking.html                 ← Luyện nói & phát âm
├── games.html                    ← Mini-games học tiếng Anh
├── chat.html                     ← Chat với AI bằng tiếng Anh
├── netlify.toml                  ← Cấu hình Netlify
├── netlify/
│   └── functions/
│       └── chat-proxy.js         ← Proxy bảo mật Anthropic API Key
└── README.md                     ← File này
```

---

## 🚀 Hướng Dẫn Deploy Lên Netlify Qua GitHub

### BƯỚC 1 — Tạo Repository trên GitHub

1. Đăng nhập vào [https://github.com](https://github.com)  
   (Chưa có tài khoản? → Click **Sign up**, đăng ký miễn phí)

2. Click nút **"+"** góc trên phải → **"New repository"**

3. Điền thông tin:
   - **Repository name:** `sunnywords`
   - **Visibility:** `Public` ✅ *(Netlify free tier yêu cầu public)*
   - Bỏ trống các ô còn lại

4. Click **"Create repository"**

---

### BƯỚC 2 — Upload Toàn Bộ File Lên GitHub

1. Trong trang repository vừa tạo, click **"uploading an existing file"**

2. **Kéo thả** toàn bộ nội dung trong thư mục `sunnywords/` vào vùng upload:
   ```
   index.html
   app.html
   roadmap.html
   vocab.html
   listening.html
   speaking.html
   games.html
   chat.html
   netlify.toml
   netlify/functions/chat-proxy.js   ← Quan trọng! Phải upload đúng đường dẫn
   ```
   
   > ⚠️ **Lưu ý thư mục con:** GitHub không tự tạo thư mục. Với file `chat-proxy.js`, bạn cần:
   > - Dùng Git CLI (xem Cách 2 bên dưới), HOẶC
   > - Tạo thư mục trực tiếp trên GitHub UI (xem bên dưới)

3. **Cách tạo thư mục `netlify/functions/` trên GitHub UI:**
   - Click **"Add file"** → **"Create new file"**
   - Trong ô tên file, gõ: `netlify/functions/chat-proxy.js`
   - GitHub tự động tạo thư mục khi bạn gõ `/`
   - Copy nội dung file `chat-proxy.js` vào ô editor
   - Click **"Commit changes"**

4. Sau khi upload hết, click **"Commit changes"** (màu xanh)

#### Cách 2 — Dùng Git CLI (Nhanh hơn nếu đã cài Git)
```bash
cd sunnywords
git init
git add .
git commit -m "Initial commit - SunnyWords app"
git remote add origin https://github.com/TÊN_BẠN/sunnywords.git
git push -u origin main
```

---

### BƯỚC 3 — Tạo Tài Khoản & Kết Nối Netlify

1. Truy cập [https://app.netlify.com](https://app.netlify.com)

2. Click **"Sign up"** → Chọn **"Continue with GitHub"**

3. Cấp quyền cho Netlify truy cập GitHub (click **"Authorize Netlify"**)

---

### BƯỚC 4 — Import Dự Án Vào Netlify

1. Trên Netlify Dashboard → Click **"Add new site"** → **"Import an existing project"**

2. Chọn **"Deploy with GitHub"**

3. Tìm và click repository `sunnywords`

4. Cấu hình build *(giữ nguyên mặc định)*:
   - **Branch to deploy:** `main`
   - **Base directory:** *(để trống)*
   - **Build command:** *(để trống)*
   - **Publish directory:** `.`

5. Click **"Deploy sunnywords"**

6. Chờ ~1 phút → Netlify hiển thị URL kiểu:  
   `https://sunny-words-abc123.netlify.app` 🎉

---

### BƯỚC 5 — Cấu Hình Anthropic API Key (Bắt Buộc Cho Chat AI)

1. Vào **Site configuration** → **Environment variables**

2. Click **"Add a variable"** → **"Add a single variable"**

3. Nhập:
   - **Key:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-xxxxxxxxxxxxxxxxxx` *(key thật của bạn)*

4. Click **"Save"**

5. **Trigger redeploy để env var có hiệu lực:**
   - Vào **Deploys** tab
   - Click **"Trigger deploy"** → **"Deploy site"**

6. Sau khi deploy xong → Vào trang `/chat.html` để test AI chat ✅

---

### BƯỚC 6 — (Tuỳ Chọn) Đặt Tên Miền Đẹp Hơn

**Đổi subdomain miễn phí** (ví dụ: `sunnywords.netlify.app`):
1. **Site configuration** → **Domain management** → **Custom domains**
2. Click vào tên hiện tại (ví dụ `sunny-words-abc123`) → **"Edit site name"**
3. Nhập tên mới → **"Save"**

**Dùng domain riêng** (ví dụ: `sunnywords.vn`):
1. **Add domain** → Nhập domain của bạn
2. Làm theo hướng dẫn cập nhật DNS record

---

## 🔄 Cập Nhật File Sau Khi Thay Đổi

Netlify **tự động deploy lại** mỗi khi bạn push code mới lên GitHub:

```bash
# Sửa file xong, chạy lệnh này
git add .
git commit -m "Cập nhật nội dung"
git push
# Netlify sẽ tự detect và deploy trong ~1 phút
```

Hoặc upload thủ công qua GitHub UI → Commit → Netlify tự redeploy.

---

## 🌐 Kiểm Tra Sau Deploy

| Trang | URL |
|-------|-----|
| 🏠 Landing Page | `https://your-site.netlify.app/` |
| 📱 App chính | `https://your-site.netlify.app/app.html` |
| 🗺️ Lộ trình 60 ngày | `https://your-site.netlify.app/roadmap.html` |
| 📚 Từ vựng | `https://your-site.netlify.app/vocab.html` |
| 👂 Luyện nghe | `https://your-site.netlify.app/listening.html` |
| 🎤 Luyện nói | `https://your-site.netlify.app/speaking.html` |
| 🎮 Mini-games | `https://your-site.netlify.app/games.html` |
| 🤖 Chat AI | `https://your-site.netlify.app/chat.html` |

---

## ❓ Xử Lý Lỗi Thường Gặp

| Lỗi | Nguyên nhân | Giải pháp |
|-----|-------------|-----------|
| Trang trắng khi vào `/` | Thiếu `index.html` | Đảm bảo file landing đã đổi tên thành `index.html` |
| Chat AI báo lỗi | API Key chưa set | Kiểm tra Environment Variables trên Netlify |
| Chat AI trả về 500 | Key sai hoặc hết credit | Kiểm tra lại key tại console.anthropic.com |
| `404` khi vào trang con | Thiếu file | Kiểm tra tất cả 8 file đã upload lên GitHub |
| Netlify Functions không chạy | `netlify/functions/` thiếu | Đảm bảo `chat-proxy.js` nằm đúng thư mục |
| Font không hiển thị | Mạng chặn Google Fonts | Thường gặp khi test local, deploy xong sẽ OK |

---

## 🔒 Bảo Mật

- API Key **không bao giờ** xuất hiện trong code client-side
- File `chat-proxy.js` chạy ở server (Netlify Function), ẩn hoàn toàn với người dùng
- Key được lưu trong **Environment Variables** mã hoá của Netlify

---

*SunnyWords ☀️ — Chúc bé học tiếng Anh vui và hiệu quả! 🌟*
