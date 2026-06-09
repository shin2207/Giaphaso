# Gia Phả Số — Hướng dẫn đưa lên Vercel

Đây là web tĩnh, chỉ gồm 1 file `index.html`. Chọn 1 trong 3 cách dưới.

## Cách 1 — Kéo thả (nhanh nhất, không cần lệnh)
1. Vào https://vercel.com → đăng nhập (đăng ký miễn phí bằng GitHub/Google/email).
2. Bấm **Add New… → Project → Deploy** (hoặc trang https://vercel.com/new).
3. Kéo **cả thư mục `gia-pha-so-vercel`** (chứa `index.html` và `vercel.json`) thả vào ô upload.
4. Bấm **Deploy**. Khoảng 20–30 giây sau sẽ có link dạng `https://ten-cua-ban.vercel.app`.

## Cách 2 — Dùng Vercel CLI
```bash
npm i -g vercel          # cài 1 lần
cd gia-pha-so-vercel
vercel                   # làm theo hỏi đáp, đăng nhập lần đầu
vercel --prod            # đẩy bản chính thức
```

## Cách 3 — Qua GitHub (tự động deploy mỗi lần sửa)
1. Tạo repo mới trên GitHub, đẩy 2 file `index.html` + `vercel.json` lên.
2. Vào https://vercel.com/new → **Import** repo đó → **Deploy**.
3. Sau này mỗi lần `git push`, Vercel tự build lại.

---

## ⚠️ Về phần "dữ liệu dùng chung cho ai cũng truy cập"
Bản này lưu dữ liệu bằng **localStorage** — tức là dữ liệu nằm **riêng trên trình duyệt của từng người**:
- Mở trên máy A thì chỉ máy A thấy; máy B mở sẽ là gia phả trống.
- Xóa cache/đổi máy là mất dữ liệu trên máy đó.

Muốn **mọi người vào cùng một gia phả chung** (đúng nghĩa "cloud database") thì cần một cơ sở dữ liệu thật phía sau, ví dụ:
- **Vercel KV / Upstash Redis** (miễn phí mức cơ bản) — hợp nhất với Vercel.
- **Supabase** hoặc **Firebase** — có sẵn cả đăng nhập (auth) thật, bảo mật mật khẩu.

Việc này cần tài khoản dịch vụ + API key của bạn và thêm một ít code (serverless function). Nếu bạn muốn, gửi mình biết bạn chọn nền nào, mình sẽ viết phiên bản kết nối DB chung + đăng nhập an toàn để thay cho localStorage.
