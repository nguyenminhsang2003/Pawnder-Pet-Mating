# 🚀 Pawnder Backend API

**SEP490_G151** - Backend API cho Pawnder Pet Dating App

## 📋 Mô Tả

ASP.NET Core 8.0 API với PostgreSQL, SignalR cho real-time communication, OData support.

## ✨ API Features

### Authentication & Authorization
- JWT Bearer authentication
- Refresh token mechanism
- Role-based authorization (User, Expert, Admin)
- Password reset với OTP
- Policy acceptance tracking (Global Policy Accept Filter)

### User Management
- User registration & login
- Profile management
- User preferences
- Ban/unban system
- User status tracking
- Email verification (Kickbox)

### Pet Management
- CRUD operations cho pets
- Pet characteristics (attributes)
- Pet photos với Cloudinary storage
- AI image analysis (Gemini)
- Pet approval system

### Matching System
- Smart matching algorithm dựa trên preferences
- Like/dislike system
- Match notifications
- Badge counts
- Statistics
- Distance calculation (LocationIQ)

### Chat System
- User-to-User chat (SignalR)
- AI Chat với Gemini
- Expert Chat
- Message history
- Typing indicators
- Read receipts

### Appointments
- Create appointments
- Counter-offer system (max 3 times)
- Location management
- Check-in system
- Appointment status tracking
- Auto-expiration handling (Background Service)

### Events
- Create & manage events
- Submission system
- Voting system
- Leaderboard
- Winner announcement
- Background service tự động chuyển trạng thái events

### Payments
- Premium plans
- VietQR integration
- Sepay integration
- Payment history
- Daily limits (likes, views, messages)
- Background service xử lý hết hạn payment

### Daily Limits
- Giới hạn hàng ngày cho free users
- Track remaining counts (likes, views, messages)
- Reset daily limits
- Premium users không bị giới hạn

### Reports & Safety
- Report system
- Block users
- Bad word filtering
- Admin review

### Notifications
- Real-time notifications (SignalR)
- Broadcast notifications
- Notification history
- Badge system

### Policies
- Policy versioning
- Policy acceptance tracking
- Policy history

## 🛠️ Tech Stack

- ASP.NET Core 8.0
- PostgreSQL + Entity Framework Core 9.0.9
- JWT Authentication
- SignalR 1.2.0
- OData 9.4.0
- Swagger/OpenAPI
- Cloudinary (Image Storage)
- Google Gemini AI
- Gmail OAuth2 API
- Kickbox (Email Verification)
- LocationIQ API

## 📦 Prerequisites

- .NET 8.0 SDK
- PostgreSQL 12+
- Visual Studio 2022 hoặc VS Code

## 🔧 Installation

```bash
cd BackEnd/BE
dotnet restore
```

## ⚙️ Configuration

Cấu hình `appsettings.json` với các key sau:

### Required
- **ConnectionStrings.DbContext**: PostgreSQL connection string
- **Jwt.Secret**: Secret key (tối thiểu 32 ký tự)
- **Jwt.Issuer**: JWT issuer
- **Jwt.Audience**: JWT audience
- **Cloudinary**: Cloud name, API key, API secret

### Optional
- **GeminiAI.ApiKey**: API key cho AI features
- **GmailOAuth2Settings**: Client ID, Secret, Access Token, Refresh Token (cho email)
- **KickboxSettings.ApiKey**: API key cho email verification
- **VietQr/Sepay**: Payment API credentials
- **LocationIQ.ApiKey**: API key cho location services

## 🚀 Running

```bash
dotnet run
```

API chạy tại: `http://localhost:5297`  
Swagger UI: `http://localhost:5297/swagger`

## 🏗️ Architecture & Code Structure

### Architecture Pattern

Dự án sử dụng **3-Layer Architecture**:
- **Controllers**: API Layer - chỉ nhận request/response
- **Services**: Business Logic Layer - xử lý business rules
- **Repositories**: Data Access Layer - database operations

### Project Structure

```
BE/
├── Controllers/     # API endpoints (29 controllers)
├── Services/        # Business logic (với Interfaces)
├── Repositories/    # Data access (với Interfaces)
├── Models/          # Database entities
├── DTO/             # Data transfer objects
├── Filters/         # Action filters (GlobalPolicyAcceptFilter)
└── Program.cs       # DI registration, middleware
```

### Dependency Injection

Tất cả services và repositories được register trong `Program.cs`:
- Repositories: `AddScoped<I{Entity}Repository, {Entity}Repository>()`
- Services: `AddScoped<I{Entity}Service, {Entity}Service>()`
- Background Services: `AddHostedService<{Service}>()`

### Background Services

3 background services chạy tự động:
- **PaymentExpirationBackgroundService**: Kiểm tra mỗi 1 giờ, update payment hết hạn
- **EventCompletionBackgroundService**: Kiểm tra mỗi 15 giây, chuyển trạng thái events
- **AppointmentExpirationBackgroundService**: Kiểm tra mỗi 5 phút, xử lý appointments quá hạn

### SignalR

Hub endpoint: `/chatHub`  
Cấu hình tối ưu: WebSocket compression, keep-alive 10s, timeout 20s.

### OData Support

Controllers hỗ trợ OData queries: `$select`, `$expand`, `$filter`, `$orderby`, `$count`, `$top`.

## 🔧 Maintenance Guide

### Thêm Entity/Feature Mới

1. Tạo Model trong `Models/{Entity}.cs`
2. Thêm vào DbContext (`PawnderDatabaseContext.cs`)
3. Tạo Repository Interface trong `Repositories/Interfaces/`
4. Tạo Repository Implementation kế thừa `BaseRepository<T>`
5. Tạo Service Interface trong `Services/Interfaces/`
6. Tạo Service Implementation
7. Tạo Controller
8. Register trong `Program.cs` (Repository và Service)

### Database Migrations

```bash
# Tạo migration
dotnet ef migrations add MigrationName

# Apply migration
dotnet ef database update

# Rollback
dotnet ef database update PreviousMigrationName
```

### Thêm API Endpoint

1. Thêm method vào Controller
2. Sử dụng Service để xử lý business logic
3. Trả về appropriate HTTP status codes
4. Swagger tự động document từ attributes

### Background Services

Thêm background service: Tạo class kế thừa `BackgroundService`, implement `ExecuteAsync`, register trong `Program.cs` với `AddHostedService<>()`.

### SignalR Hub

Hub endpoint: `/chatHub`  
Thêm method mới vào `ChatHub.cs`, call từ Service bằng static methods.

### Error Handling

- Controllers: Try-catch và trả về appropriate status codes
- Services: Throw exceptions, controllers handle
- Global exception handler trong `Program.cs` (logs errors)

### Logging

Sử dụng `ILogger<T>` để log information và errors.

## 🧪 Testing

```bash
cd ../BE.Tests
dotnet test
```

- **Unit Tests**: Test services và repositories riêng lẻ
- **Integration Tests**: Test API endpoints với database

## 🔐 Authentication

- JWT Bearer tokens
- Login: `POST /api/login`
- Refresh: `POST /api/refresh`
- Swagger: Click "Authorize" → Nhập `Bearer <token>`

Thêm protected endpoint: Thêm `[Authorize(Roles = "User,Admin")]` attribute.

## 🔄 SignalR

Hub endpoint: `/chatHub`  
Real-time cho chat, notifications, match events.

## 🌐 CORS Configuration

Allowed origins:
- `http://localhost:3000` (Admin Panel)
- `http://localhost:5297` (Backend)
- `http://127.0.0.1:3000`

## 🐛 Troubleshooting

- **Database Error**: Kiểm tra PostgreSQL đang chạy và connection string
- **CORS Error**: Kiểm tra `Program.cs` - thêm frontend URL vào allowed origins
- **JWT Invalid**: Kiểm tra secret key và token expiration
- **Migration Error**: Kiểm tra model changes và connection string
- **SignalR Connection Failed**: Kiểm tra CORS và authentication token

## 📚 API Endpoints

Xem đầy đủ trong Swagger UI sau khi chạy ứng dụng.

## 🚢 Deployment

```bash
dotnet publish -c Release -o ./publish
cd publish
dotnet BE.dll
```

---

**Version**: 1.0  
**Last Updated**: 2026-02-02
