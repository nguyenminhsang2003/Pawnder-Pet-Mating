# 🤝 Quy ước đóng góp cho dự án Pawnder

Tài liệu này giúp mọi người làm việc thống nhất, PR rõ ràng và dễ review.  
Nếu bạn là Team Lead, đây cũng là “hợp đồng làm việc” nhẹ giữa bạn và team.

---

## 1. Luồng làm việc cơ bản

1. **Pull code mới nhất** từ branch target (thường là `develop`):
   - `git checkout develop`
   - `git pull`
2. **Tạo branch mới** từ `develop`:
   - `git checkout -b feature/ten-nhiem-vu`
3. Code + commit từng phần nhỏ, có ý nghĩa.
4. Push lên remote:
   - `git push -u origin feature/ten-nhiem-vu`
5. Mở **Pull Request** vào branch target (thường là `develop`), dùng template có sẵn.
6. Chờ review, fix comment (nếu có), rồi Lead / Code Owner merge.

---

## 2. Quy ước đặt tên branch

Tên branch nên:
- Ngắn gọn, mô tả được mục đích.
- Dùng tiếng Anh, lowercase, nối bằng dấu `-`.

Gợi ý:

```text
feature/pet-matching-api
feature/mobile-chat-ui
bugfix/appointment-timezone
bugfix/admin-report-filter
hotfix/payment-callback
refactor/chat-service-cleanup
```

---

## 3. Quy ước commit message

Không cần quá phức tạp, nhưng nên:
- Dùng **thì hiện tại**, mô tả **làm gì**, không mô tả “fix bug”.
- Nếu có thể, group theo loại: `feat`, `fix`, `refactor`, `docs`, `chore`, ...

Ví dụ:

```text
feat: add pet matching endpoint
feat: implement mobile favorite screen
fix: correct appointment time validation
fix: handle null avatar in user profile
refactor: extract chat notification service
docs: update backend setup in README
chore: bump react-native version
```

Nếu PR lớn, nên có nhiều commit nhỏ theo từng phần logic, thay vì 1 commit “update code”.

---

## 4. Pull Request

- Mỗi PR nên:
  - Tập trung vào **một nhóm thay đổi** (một feature / một bug / một refactor).
  - Sử dụng **template** trong `.github/pull_request_template.md`.
  - Link tới issue (nếu có).
- Trước khi tạo PR:
  - Tự review lại code một lượt.
  - Tự test các flow liên quan.
  - Đảm bảo không còn debug log / comment thừa.

**Target branch gợi ý**

- Tính năng mới, thay đổi bình thường → `develop`.
- Hotfix gấp cho production → `main` (theo thỏa thuận với lead).

---

## 5. Backend (BackEnd/BE) – Lưu ý khi sửa

- Khi thêm entity mới:
  - Tạo `Model` trong `Models/`.
  - Thêm vào `PawnderDatabaseContext`.
  - Tạo `Repository` + `Service` + `Controller` theo pattern có sẵn.
- Khi thay đổi database:
  - Ưu tiên dùng **EF Core migrations** (`dotnet ef migrations add ...`).
  - Hoặc cập nhật SQL trong `database/` nếu team thống nhất.
- Luôn chạy:

```bash
cd BackEnd/BE.Tests
dotnet test
```

trước khi mở PR liên quan backend (nếu khả thi).

---

## 6. Mobile (FE/FE-User) – Lưu ý khi sửa

- Mỗi feature mới nên có folder riêng trong `src/features/`.
- Navigation:
  - Đăng ký screen mới trong `navigation` tương ứng.
- State:
  - Dùng Redux Toolkit, thêm slice mới vào `src/app/store.ts` nếu cần global state.
- API:
  - Dùng service / client có sẵn trong `src/services/` hoặc `api/`.
- Test nhanh:

```bash
cd FE/FE-User
npm test
```

---

## 7. Admin (FE/fe-admin) – Lưu ý khi sửa

- Tạo module mới dưới `src/features/`.
- API call nên đặt trong `shared/api/`.
- Dùng context / hooks có sẵn trong `shared/context/` nếu cần state global.
- Kiểm tra trên browser:
  - Các page liên quan.
  - Phân quyền / điều hướng / filter / sort.

---

## 8. Coding style & chất lượng

- Tôn trọng style hiện tại của project:
  - C# theo convention mặc định (.NET).
  - TS/JS theo ESLint/Prettier (nếu có).
- Tránh:
  - Hàm quá dài, class làm quá nhiều việc.
  - “Thử cho chạy được đã, sau tính sau” trong PR gửi review.
- Nên:
  - Tách nhỏ hàm / component.
  - Đặt tên rõ nghĩa (tiếng Anh).
  - Thêm comment ở chỗ logic khó hiểu / quan trọng.

---

## 9. Về quyền merge & review

- `main` và `develop` được bảo vệ bằng **Branch Protection**:
  - Không được push trực tiếp (trừ Lead / bot CI).
  - Mọi thay đổi phải qua **Pull Request**.
- `CODEOWNERS` được thiết lập trong `.github/CODEOWNERS`:
  - PR sẽ tự động request review từ người phụ trách.
  - Tùy rule, có thể **bắt buộc** code owner approve mới được merge.

Nếu bạn không chắc, hãy:
- Gắn người review phù hợp (backend / mobile / admin).
- Hỏi Lead trước khi merge những thay đổi lớn.

---

## 10. Hỏi thêm ở đâu?

- Đọc kỹ:
  - `README.md` (root và từng module).
  - `template.txt` để hiểu triết lý setup repo.
- Nếu vẫn chưa rõ:
  - Hỏi trực tiếp Team Lead / người phụ trách module.

> Mục tiêu: **ai cũng có thể đóng góp mà không làm “vỡ” project**,  
> và Lead có thể kiểm soát chất lượng mà không phải micro-manage.


