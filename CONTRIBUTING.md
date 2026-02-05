# 🤝 Quy ước đóng góp

Ngắn gọn để mọi người làm giống nhau, PR dễ review.

---

## 1. Luồng làm việc

1. `git checkout develop` + `git pull`
2. Tạo branch mới từ `develop`:
   - `git checkout -b feature/ten-nhiem-vu`
3. Code → commit → `git push`
4. Tạo Pull Request vào `develop`, dùng template có sẵn.

---

## 2. Tên branch

```text
feature/pet-matching-api
bugfix/appointment-timezone
hotfix/payment-callback
refactor/chat-service
```

---

## 3. Commit message

```text
feat: add pet matching endpoint
fix: correct appointment time validation
refactor: cleanup chat service
docs: update backend README
```

Nên chia nhiều commit nhỏ, có ý nghĩa.

---

## 4. Pull Request

- Dùng template: `.github/pull_request_template.md`.
- Mỗi PR nên tập trung 1 nhóm thay đổi.
- Trước khi mở PR:
  - Đã tự review code.
  - Đã tự test flow liên quan.
  - Không còn log / comment thừa.

Target branch:

- Thường: `develop`.
- Hotfix gấp (theo thoả thuận): `main`.

---

## 5. Backend / Mobile / Admin (lưu ý nhanh)

- **Backend**:
  - Thêm entity: Model → DbContext → Repository → Service → Controller.
  - Thay đổi DB: dùng EF migrations nếu có thể.
- **Mobile (FE-User)**:
  - Mỗi feature 1 folder trong `src/features/`.
  - Screen mới: khai báo trong navigation.
- **Admin (fe-admin)**:
  - Module mới trong `src/features/`.
  - API call để trong `shared/api/`.

---

## 6. Quyền merge & review

- `main` và `develop`:
  - Không push trực tiếp (dùng Branch Protection).
  - Bắt buộc qua Pull Request.
- `CODEOWNERS`:
  - PR tự request review đúng người phụ trách.

Nếu không chắc, hãy hỏi Lead / người phụ trách module.


