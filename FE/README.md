# 🎨 Pawnder Frontend

**SEP490_G151** - Frontend applications

## 📋 Tổng Quan

2 ứng dụng frontend:
- **FE-User** - Mobile App (React Native) - Ứng dụng di động cho người dùng
- **fe-admin** - Admin Panel (React) - Web dashboard cho quản trị viên

## ✨ Tính Năng Tổng Quan

### Mobile App (FE-User)
- 🎯 Matching & Discovery - Swipe, filter, matching algorithm
- 💬 Chat System - User chat, AI chat, Expert chat
- 📅 Appointments - Đặt lịch hẹn gặp với counter-offer
- 🎉 Events - Cuộc thi ảnh/video với voting
- 👤 Profile Management - Quản lý user và pet profiles
- 💳 Premium - Nâng cấp tài khoản và thanh toán
- 🔔 Notifications - Real-time notifications

### Admin Panel (fe-admin)
- 👥 User Management - Quản lý users, ban/unban
- 🐾 Pet Management - Approve/reject pets
- 📢 Report Management - Xử lý reports
- 🎉 Event Management - Tạo và quản lý events
- 👨‍⚕️ Expert Management - Quản lý chuyên gia
- 💳 Payment Management - Quản lý thanh toán
- 📊 Dashboard - Thống kê và analytics

## 🚀 Quick Start

### Prerequisites
- Node.js >= 18
- (Mobile) Java JDK 17+, Android Studio / Xcode

### Mobile App

```bash
cd FE-User
npm install
# iOS: cd ios && pod install && cd ..
npm run android  # hoặc npm run ios
```

### Admin Panel

```bash
cd fe-admin
npm install
npm start  # Chạy tại http://localhost:3000
```

## ⚙️ Configuration

### Mobile App
Cấu hình `FE-User/src/config/api.config.ts`:
- Thay đổi `CURRENT_ENVIRONMENT` để switch giữa các environments
- Android emulator: dùng `android` environment (10.0.2.2:5297)
- iOS simulator: dùng `ios` environment (localhost:5297)
- Real device: dùng `local_network` với IP address
- Production: dùng `production` environment

### Admin Panel
Tạo `.env` trong `fe-admin/`:
- `REACT_APP_API_URL`: Backend API URL (mặc định: `http://localhost:5297`)
- `REACT_APP_APP_NAME`: App name
- `REACT_APP_SIGNALR_URL`: SignalR hub URL

## 🔗 Backend Connection

Cả 2 app kết nối đến:
- API: `http://localhost:5297/api` (hoặc production URL)
- SignalR: `http://localhost:5297/chatHub`

**Đảm bảo Backend chạy trước khi start frontend (port 5297).**

## 📚 Documentation

- [Mobile App](./FE-User/README.md) - Setup, Features, Development, Maintenance
- [Admin Panel](./fe-admin/README.md) - Setup, Features, Development, Maintenance

## 🛠️ Maintenance Guide

### Thêm Feature Mới

**Mobile App:**
1. Tạo feature folder trong `FE-User/src/features/`
2. Tạo API service, screens, components
3. Thêm routes trong `AppNavigator.tsx`
4. Thêm Redux slice nếu cần (trong `app/store.ts`)

**Admin Panel:**
1. Tạo feature folder trong `fe-admin/src/features/`
2. Tạo API service trong `shared/api/`
3. Tạo components và pages
4. Thêm routes trong `config/App.js`

### Shared Code

- **API Client**: Cả 2 app có API client riêng
- **SignalR**: Cả 2 app sử dụng SignalR client
- **Utils**: Mỗi app có utils riêng trong `shared/utils/` hoặc `utils/`

### State Management

- **Mobile App**: Redux Toolkit (trong `src/app/store.ts`)
- **Admin Panel**: React Context (trong `shared/context/`)

### Testing

```bash
# Mobile App
cd FE-User
npm test

# Admin Panel
cd fe-admin
npm test
```

## 🐛 Common Issues

- **CORS Error**: Kiểm tra Backend CORS config (allowed origins: localhost:3000, localhost:5297)
- **API Connection Failed**: Kiểm tra Backend đang chạy (port 5297) và API URL
- **SignalR Issues**: Kiểm tra hub URL (http://localhost:5297/chatHub) và authentication token

## 🚢 Deployment

### Mobile App
- **Android**: `cd FE-User/android && ./gradlew assembleRelease`
- **iOS**: Build qua Xcode

### Admin Panel
- `cd fe-admin && npm run build`
- Deploy thư mục `build/` lên web server

---

**Version**: 1.0  
**Last Updated**: 2026-02-02
