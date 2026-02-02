# 🐾 Pawnder - Pet Dating App

**SEP490_G151** - Ứng dụng hẹn hò cho thú cưng

## 📋 Mô Tả

Pawnder là nền tảng kết nối chủ nuôi thú cưng, sử dụng thuật toán matching thông minh để tìm bạn đồng hành phù hợp dựa trên đặc điểm, sở thích và khoảng cách địa lý.

## ✨ Tính Năng Chính

### 🎯 Matching System
- **Thuật toán matching thông minh**: Dựa trên preferences, đặc điểm thú cưng và khoảng cách
- **Swipe cards**: Tương tác trực quan để tìm thú cưng phù hợp
- **Filter nâng cao**: Lọc theo breed, age, characteristics, distance
- **Real-time match notifications**: Thông báo ngay khi có match
- **Like/Dislike system**: Like thú cưng và nhận like từ người khác
- **Favorite screen**: Xem danh sách likes và matches

### 💬 Chat System
- **User-to-User Chat**: Chat real-time giữa người dùng đã match
- **AI Chat**: Tư vấn với Google Gemini AI về chăm sóc thú cưng
- **Expert Chat**: Tư vấn với chuyên gia thú y
- **Typing indicators & Read receipts**: Trải nghiệm chat đầy đủ
- **Badge notifications**: Thông báo tin nhắn mới

### 📅 Appointments
- **Đặt lịch hẹn gặp**: Tạo appointment với thú cưng đã match
- **Counter-offer system**: Đề xuất thời gian/địa điểm khác (tối đa 3 lần)
- **Location picker**: Chọn địa điểm với Google Maps integration
- **Check-in system**: Xác nhận đến địa điểm hẹn
- **Appointment management**: Quản lý lịch hẹn của bạn
- **Auto-expiration**: Tự động xử lý appointments quá hạn

### 🎉 Events
- **Cuộc thi ảnh/video**: Tham gia events với thú cưng
- **Submission & Voting**: Submit entry và vote cho submissions khác
- **Leaderboard**: Bảng xếp hạng real-time
- **Prize system**: Nhận điểm thưởng khi thắng
- **Auto-transition**: Tự động chuyển trạng thái events (upcoming → active → submission_closed → voting_ended)

### 🤖 AI Integration
- **Google Gemini AI**: Chat AI thông minh về thú cưng
- **Image Analysis**: Phân tích ảnh thú cưng để gợi ý characteristics
- **Smart Recommendations**: Gợi ý thú cưng phù hợp

### 💳 Premium & Payment
- **Premium Plans**: Nâng cấp tài khoản với nhiều tính năng
- **Payment Integration**: VietQR và Sepay
- **Payment History**: Theo dõi lịch sử thanh toán
- **Daily Limits**: Giới hạn hàng ngày cho free users (likes, views, messages)
- **Auto-expiration**: Tự động xử lý payment hết hạn

### 👤 User & Pet Management
- **User Profiles**: Quản lý thông tin cá nhân
- **Pet Profiles**: Tạo và quản lý nhiều thú cưng
- **Pet Photos**: Upload và quản lý ảnh thú cưng (Cloudinary)
- **Pet Characteristics**: Mô tả đặc điểm chi tiết
- **AI Image Analysis**: Tự động phân tích ảnh để gợi ý characteristics
- **Pet Approval**: Admin approve/reject pets

### 🔔 Notifications
- **Real-time notifications**: Qua SignalR
- **Match notifications**: Thông báo khi có match mới
- **Message notifications**: Thông báo tin nhắn mới
- **Event notifications**: Thông báo về events
- **System notifications**: Thông báo hệ thống
- **Broadcast notifications**: Admin gửi thông báo hàng loạt

### 📢 Reports & Safety
- **Report System**: Báo cáo người dùng/thú cưng không phù hợp
- **Block Users**: Chặn người dùng
- **Bad Word Filtering**: Lọc từ ngữ không phù hợp
- **Admin Review**: Admin xem xét và xử lý reports

### 📝 Policy Management
- **Policy Versioning**: Quản lý các phiên bản policy
- **Policy Acceptance**: Yêu cầu user chấp nhận policy
- **Policy History**: Lịch sử chấp nhận policy
- **Draft Versions**: Quản lý draft policies

### 👨‍⚕️ Expert Features
- **Expert Registration**: Đăng ký trở thành chuyên gia
- **Expert Confirmation**: Xác nhận thông tin chuyên gia
- **Expert Chat**: Chat với người dùng
- **Expert AI Chat**: AI chat cho chuyên gia
- **Expert Notifications**: Quản lý thông báo chuyên gia

### 🖥️ Admin Panel
- **User Management**: Quản lý users, ban/unban
- **Pet Management**: Approve/reject pets
- **Report Management**: Xử lý reports
- **Event Management**: Tạo và quản lý events
- **Expert Management**: Quản lý chuyên gia
- **Dashboard & Analytics**: Thống kê và biểu đồ
- **Payment Management**: Quản lý thanh toán
- **Policy Management**: Quản lý policies
- **Bad Word Management**: Quản lý từ ngữ không phù hợp
- **Attribute Management**: Quản lý attributes và options
- **Notification Broadcasting**: Gửi thông báo hàng loạt

## 🏗️ Kiến Trúc

```
Mobile App (React Native) ──┐
                            ├──> Backend API (ASP.NET Core 8.0) ──> PostgreSQL
Admin Panel (React) ────────┘
```

## 🛠️ Tech Stack

- **Backend**: ASP.NET Core 8.0, PostgreSQL, SignalR 1.2.0, OData
- **Mobile**: React Native 0.74.3, React 18.2.0, TypeScript, Redux Toolkit
- **Admin**: React 19.2.0, React Router DOM
- **AI**: Google Gemini AI
- **Storage**: Cloudinary (Images)
- **Email**: Gmail OAuth2 API, Kickbox (Email Verification)
- **Maps**: LocationIQ API

## 🚀 Quick Start

### Prerequisites
- .NET 8.0 SDK
- PostgreSQL 12+
- Node.js >= 18
- (Mobile) Java JDK 17+, Android Studio / Xcode

### Setup

1. **Database**: Xem [database/README.md](./database/README.md)
2. **Backend**: Xem [BackEnd/README.md](./BackEnd/README.md)
3. **Mobile App**: Xem [FE/FE-User/README.md](./FE/FE-User/README.md)
4. **Admin Panel**: Xem [FE/fe-admin/README.md](./FE/fe-admin/README.md)

## ⚙️ Configuration

### Backend (`BackEnd/BE/appsettings.json`)
- **ConnectionStrings**: PostgreSQL connection
- **Jwt**: Secret key (32+ ký tự), Issuer, Audience
- **Cloudinary**: Cloud name, API key, API secret
- **GeminiAI**: API key
- **GmailOAuth2Settings**: Client ID, Secret, Access Token, Refresh Token
- **KickboxSettings**: API key (email verification)
- **VietQr/Sepay**: Payment API credentials
- **LocationIQ**: API key

### Frontend
- **Mobile**: `FE/FE-User/src/config/api.config.ts` - Cấu hình API URL theo environment
- **Admin**: Tạo `.env` với `REACT_APP_API_URL`

## 📚 Documentation

- [Backend](./BackEnd/README.md) - Setup, Architecture, Maintenance
- [Database](./database/README.md) - Setup, Migrations, Backup
- [Mobile App](./FE/FE-User/README.md) - Setup, Development, Maintenance
- [Admin Panel](./FE/fe-admin/README.md) - Setup, Development, Maintenance

## 🔗 API Documentation

Swagger UI: `http://localhost:5297/swagger` (sau khi chạy Backend)

## 🛠️ Maintenance Guide

### Thêm Feature Mới

1. **Backend**:
   - Tạo Model trong `BackEnd/BE/Models/`
   - Tạo Repository interface và implementation
   - Tạo Service interface và implementation
   - Tạo Controller
   - Register trong `Program.cs`

2. **Frontend**:
   - Tạo feature folder trong `src/features/`
   - Tạo API service
   - Tạo components và screens
   - Thêm routes

### Database Changes

1. Tạo migration: `dotnet ef migrations add MigrationName`
2. Update database: `dotnet ef database update`
3. Hoặc update SQL file và import lại

### Testing

- **Backend**: `cd BackEnd/BE.Tests && dotnet test`
- **Frontend**: `npm test` trong từng project

### Deployment

1. Build Backend: `dotnet publish -c Release`
2. Build Frontend: `npm run build`
3. Deploy theo hướng dẫn trong từng README

## 🐛 Troubleshooting

- **Database Error**: Kiểm tra PostgreSQL đang chạy và connection string
- **CORS Error**: Kiểm tra CORS config trong `BackEnd/BE/Program.cs` (allowed origins: localhost:3000, localhost:5297)
- **API Connection**: Đảm bảo Backend chạy trước Frontend (port 5297)

---

**Version**: 1.0  
**Last Updated**: 2026-02-02
