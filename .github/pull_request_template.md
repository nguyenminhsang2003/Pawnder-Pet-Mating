## 📝 Mô tả tổng quan

<!-- Bắt buộc: Tóm tắt ngắn gọn PR này làm gì, bối cảnh nào, link issue (nếu có). -->

- Loại thay đổi: (Backend / Mobile / Admin / Docs / Other)
- Liên quan đến: (Issue #..., task, màn hình, endpoint, use case...)

## 🔍 Thay đổi chính

<!-- Liệt kê theo nhóm, giúp reviewer đọc nhanh. -->

- **Backend**:
  - [ ] API mới:
  - [ ] Sửa logic:
  - [ ] Thay đổi model / DTO / migration:
- **Mobile (FE-User)**:
  - [ ] Màn hình / component:
  - [ ] Logic Redux / state:
  - [ ] Navigation / flow:
- **Admin (fe-admin)**:
  - [ ] Page / component:
  - [ ] API call / service:
- **Khác**:
  - [ ] Config / env:
  - [ ] Docs / README:

## ✅ Đã test chưa?

<!-- Nên ghi rõ đã test những case nào, trên môi trường nào. -->

- [ ] Backend:
  - [ ] Đã chạy `dotnet test`
  - [ ] Đã test thủ công trên Swagger
- [ ] Mobile:
  - [ ] Android emulator
  - [ ] iOS simulator
- [ ] Admin:
  - [ ] Đã test các flow chính trên browser
- [ ] Không có thay đổi cần test đặc biệt

**Mô tả chi tiết cách test (nếu có):**

- Bước 1:
- Bước 2:
- Kỳ vọng:

## 🔄 Ảnh hưởng side-effect

- [ ] Có thay đổi database (migration / SQL)
- [ ] Có ảnh hưởng tới auth / permission
- [ ] Có ảnh hưởng tới performance
- [ ] Không có side-effect đáng kể

Nếu có, mô tả rõ:

## 📸 Hình ảnh / Screenshot (nếu có UI)

<!-- Đính kèm ảnh trước/sau, hoặc GIF demo flow. -->

## 📋 Checklist

- [ ] Code đã tự review lại một lượt
- [ ] Không còn comment/debug log thừa
- [ ] Đã cập nhật README / docs nếu cần
- [ ] Đã đảm bảo backward-compatible (nếu là API/public contract)
- [ ] Đã sync/merge từ `develop` (hoặc branch target) mới nhất


