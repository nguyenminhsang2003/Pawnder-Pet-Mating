# 🖥️ Pawnder Admin Panel

**SEP490_G151** - Web dashboard quản trị

## 📋 Mô Tả

React web app cho quản trị viên - quản lý users, pets, reports, events, experts, policies, payments.

## ✨ Tính Năng

### 👥 User Management
- Xem danh sách tất cả users
- Chi tiết user (profile, pets, activities)
- Ban/Unban users (với duration và reason)
- Quản lý user roles (User, Expert, Admin)
- Xem lịch sử ban
- User statistics

### 🐾 Pet Management
- Xem danh sách tất cả pets
- Chi tiết pet (photos, characteristics, owner)
- Approve/Reject pets
- Quản lý pet photos
- Xem activities của pets

### 📢 Report Management
- Xem danh sách reports
- Chi tiết report (content, reporter, reported user)
- Resolve/Reject reports
- Xử lý reports theo priority

### 🎉 Event Management
- Tạo và quản lý events
- Xem danh sách events
- Chi tiết event (submissions, votes, leaderboard)
- Quản lý submissions
- Announce winners

### 👨‍⚕️ Expert Management
- Tạo và quản lý experts
- Chi tiết expert (profile, chats, confirmations)
- Expert chat interface
- Expert AI chat
- Quản lý expert notifications

### 💬 Chat Management
- AI Chat management
- Expert Chat monitoring
- Chat content moderation

### 📝 Policy Management
- Tạo và quản lý policies
- Version control cho policies
- Draft versions
- Policy acceptance tracking
- Policy statistics

### 💳 Payment Management
- Xem payment history
- Quản lý premium subscriptions
- Payment statistics
- Revenue tracking

### 🚫 Bad Word Management
- Thêm/sửa/xóa bad words
- Quản lý bad word categories
- Bad word levels
- Bad word detail và edit

### 📊 Dashboard
- Thống kê tổng quan
- Charts và graphs (Recharts)
- Quick actions
- Real-time updates
- User growth chart

### 🔔 Notification System
- Broadcast notifications
- Send notifications to users
- Notification history
- Draft notifications

### 🏷️ Attribute Management
- Quản lý attributes (đặc điểm thú cưng)
- Quản lý attribute options
- CRUD operations cho attributes

## 🛠️ Tech Stack

- React 19.2.0
- React Router DOM 6.30.1
- Axios 1.13.0
- SignalR Client (@microsoft/signalr 10.0.0)
- Recharts 3.3.0

## 📦 Prerequisites

- Node.js >= 18
- Backend API đang chạy (port 5297)

## 🔧 Installation

```bash
cd FE/fe-admin
npm install
```

## ⚙️ Configuration

Tạo file `.env` trong root folder:
- `REACT_APP_API_URL`: Backend API URL (mặc định: `http://localhost:5297`)
- `REACT_APP_APP_NAME`: App name (mặc định: `Pawnder Admin`)
- `REACT_APP_SIGNALR_URL`: SignalR hub URL (mặc định: `http://localhost:5297/chatHub`)

## 🚀 Running

```bash
npm start
```

Ứng dụng chạy tại: `http://localhost:3000`

## 🏗️ Project Structure

```
src/
├── features/        # Feature modules
│   ├── attributes/ # Attribute management
│   ├── auth/       # Authentication
│   ├── badwords/   # Bad word management
│   ├── dashboard/  # Dashboard
│   ├── events/     # Event management
│   ├── experts/    # Expert management
│   ├── notifications/# Notification system
│   ├── payments/   # Payment management
│   ├── pets/       # Pet management
│   ├── policies/   # Policy management
│   ├── reports/    # Report management
│   └── users/      # User management
├── shared/          # Shared resources
│   ├── api/       # API services
│   ├── context/   # React Context (Auth, SignalR, etc.)
│   └── utils/     # Utilities
└── components/     # Reusable components
```

## 🛠️ Maintenance Guide

### Thêm Feature Mới

1. Tạo feature folder trong `src/features/newFeature/`
2. Tạo API service trong `shared/api/newFeatureService.js`
3. Tạo components (List, Detail, etc.)
4. Thêm route trong `config/App.js`
5. Thêm link trong `Sidebar.js` (nếu cần)

### State Management

Sử dụng React Context cho global state:
- `AuthContext` - Authentication state
- `SignalRContext` - SignalR connection
- `NotificationContext` - Notifications
- `ThemeContext` - Theme

Thêm context mới: Tạo file trong `shared/context/`, export Provider và custom hook.

### API Client

Sử dụng `shared/api/apiClient.js`:
- Tự động thêm JWT token vào headers
- Handle 401 errors (auto logout)
- Error handling tập trung

### SignalR Integration

Sử dụng `SignalRContext`:
- Get connection từ context
- Listen: `connection.on('EventName', handler)`
- Send: `connection.send('MethodName', data)`

### Protected Routes

Sử dụng `ProtectedRoute` component để bảo vệ routes cần authentication.

### Adding New Page

1. Tạo component trong `features/`
2. Thêm route trong `config/App.js`
3. Thêm link trong `Sidebar.js` (nếu cần)

### Styling

- Component-specific: CSS files trong `styles/` folder
- Global: `index.css`
- Sử dụng CSS modules hoặc inline styles

## 🔐 Authentication

- Login tại `/login`
- JWT token lưu trong localStorage
- Protected routes tự động redirect nếu chưa login
- Token refresh xử lý trong `apiClient.js`

## 🧪 Testing

```bash
npm test
```

## 🚢 Build for Production

```bash
npm run build
```

Deploy thư mục `build/` lên web server.

## 🐛 Troubleshooting

### CORS Error
- Kiểm tra Backend CORS config (allowed origins: localhost:3000)
- Đảm bảo frontend URL trong allowed origins

### Authentication Issues
- Kiểm tra token trong localStorage
- Login lại nếu token expired

### API Connection Failed
- Kiểm tra Backend đang chạy (port 5297)
- Kiểm tra `REACT_APP_API_URL` trong `.env`

### Build Errors
```bash
rm -rf node_modules package-lock.json
npm install
rm -rf build
npm run build
```

### SignalR Connection Issues
- Kiểm tra hub URL (http://localhost:5297/chatHub)
- Kiểm tra authentication token
- Xem browser console logs

---

**Version**: 1.0  
**Last Updated**: 2026-02-02
