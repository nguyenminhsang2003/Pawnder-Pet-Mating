# 📱 Pawnder Mobile App

**SEP490_G151** - React Native mobile application

## 📋 Mô Tả

Ứng dụng di động cho iOS và Android - tìm kiếm, match, chat với thú cưng khác.

## ✨ Tính Năng

### 🎯 Matching & Discovery
- Swipe cards để tìm thú cưng phù hợp
- Filter theo preferences (breed, age, characteristics, distance)
- Matching algorithm thông minh
- Real-time match notifications

### ❤️ Favorite & Likes
- Xem danh sách likes đã nhận
- Xem danh sách matches
- Respond to likes (accept/reject)
- Match details modal với thông tin chi tiết

### 💬 Chat
- **User Chat**: Chat với người dùng đã match
- **AI Chat**: Tư vấn với Google Gemini AI
- **Expert Chat**: Tư vấn với chuyên gia
- Typing indicators, read receipts
- Badge notifications

### 📅 Appointments
- Tạo appointment với thú cưng đã match
- Counter-offer system
- Location picker với maps
- Check-in tại địa điểm
- Quản lý appointments

### 🎉 Events
- Xem danh sách events
- Submit entry (ảnh/video)
- Voting cho submissions
- Leaderboard real-time
- Winners announcement

### 👤 Profile
- Quản lý user profile
- Quản lý pet profiles (nhiều pets)
- Upload/edit pet photos
- Pet characteristics
- AI image analysis

### 💳 Premium
- Xem premium plans
- Thanh toán qua VietQR
- Payment history
- Premium features unlock
- Daily limits tracking

### 🔔 Notifications
- Real-time notifications
- Match notifications
- Message notifications
- Event notifications

### 👨‍⚕️ Expert
- Expert registration
- Expert confirmation
- Expert chat interface

### 📝 Policy
- Xem danh sách policies
- Policy acceptance
- Policy history

### 📢 Report & Block
- Report users/pets
- Block users
- Xem danh sách blocked users
- Xem lịch sử reports

### ⚙️ Settings
- Change password
- Help & support
- Resources

## 🛠️ Tech Stack

- React Native 0.74.3
- React 18.2.0
- TypeScript
- Redux Toolkit 2.9.0
- React Navigation 7.x
- SignalR Client (@microsoft/signalr 9.0.6)
- React Native Maps 1.14.0
- i18next (Internationalization)

## 📦 Prerequisites

- Node.js >= 18
- **Android**: Java JDK 17+, Android Studio
- **iOS**: Xcode 14+ (macOS only)

## 🔧 Installation

```bash
cd FE/FE-User
npm install
# iOS: cd ios && pod install && cd ..
```

## ⚙️ Configuration

Cấu hình `src/config/api.config.ts`:

### Environment Types
- `android`: Dùng cho Android emulator (10.0.2.2 hoặc production URL)
- `ios`: Dùng cho iOS simulator (localhost)
- `local_network`: Dùng cho real device (IP address)
- `production`: Production backend URL

### Current Environment
Thay đổi `CURRENT_ENVIRONMENT` trong file để switch giữa các environments.

**Lưu ý**: 
- Android emulator: Dùng `http://10.0.2.2:5297` cho local backend
- iOS simulator: Dùng `http://localhost:5297`
- Real device: Dùng IP address của máy chạy backend (ví dụ: `http://192.168.1.100:5297`)

## 🚀 Running

### Android
```bash
npm run android
```

### iOS
```bash
npm run ios
```

### Metro Bundler
```bash
npm start
```

## 🏗️ Project Structure

```
src/
├── features/        # Feature modules
│   ├── appointment/ # Appointments
│   ├── auth/        # Authentication
│   ├── badge/       # Badge management
│   ├── chat/        # Chat features
│   ├── event/       # Events
│   ├── expert/      # Expert features
│   ├── favorite/    # Favorite & Likes
│   ├── home/        # Home & Matching
│   ├── match/       # Matching
│   ├── notification/# Notifications
│   ├── payment/     # Premium & Payment
│   ├── pet/         # Pet management
│   ├── policy/      # Policy
│   ├── profile/     # Profile management
│   ├── report/      # Report & Block
│   └── settings/    # Settings
├── navigation/      # Navigation config
├── services/        # API & SignalR services
├── components/      # Reusable components
├── app/            # Redux store
└── config/         # Configuration files
```

## 🛠️ Maintenance Guide

### Thêm Feature Mới

1. Tạo feature folder trong `src/features/newFeature/`
2. Tạo API service trong `api/newFeatureApi.ts`
3. Tạo screens trong `screens/`
4. Tạo components nếu cần
5. Thêm Redux slice nếu cần state management
6. Thêm route trong `AppNavigator.tsx`

### Redux State Management

Thêm slice mới:
1. Tạo `newFeatureSlice.ts` với `createSlice`
2. Register trong `src/app/store.ts` trong reducer object

### SignalR Integration

Sử dụng `signalr.service.ts`:
- Connect: `await signalRService.connect(userId)`
- Listen: `signalRService.on('EventName', handler)`
- Send: `signalRService.send('MethodName', data)`

### Navigation

Thêm screen mới:
1. Thêm type vào `RootStackParamList`
2. Thêm `<Stack.Screen>` trong `AppNavigator.tsx`
3. Navigate: `navigate('ScreenName', { params })`

### API Configuration

Cấu hình trong `src/config/api.config.ts`:
- Thay đổi `CURRENT_ENVIRONMENT` để switch giữa dev/prod
- Android emulator: dùng `android` environment
- iOS simulator: dùng `ios` environment
- Real device: dùng `local_network` với IP address

## 🧪 Testing

```bash
npm test
```

## 🐛 Troubleshooting

### Android Build Issues
```bash
cd android && ./gradlew clean && cd ..
npm start -- --reset-cache
rm -rf node_modules && npm install
```

### iOS Build Issues
```bash
cd ios
pod deintegrate
pod install
cd ..
```

### Vector Icons Not Showing
```bash
npx react-native-asset
```

### API Connection Failed
- Kiểm tra Backend đang chạy (port 5297)
- Android emulator: dùng `10.0.2.2:5297` thay `localhost`
- iOS simulator: dùng `localhost:5297`
- Real device: dùng IP address của máy chạy backend

### Metro Bundler Issues
```bash
lsof -ti:8081 | xargs kill -9
npm start -- --reset-cache
```

## 🚢 Building for Production

### Android
```bash
cd android
./gradlew assembleRelease
# APK: android/app/build/outputs/apk/release/app-release.apk
```

### iOS
1. Mở Xcode: `open ios/Pawnder.xcworkspace`
2. Product → Archive
3. Distribute App

---

**Version**: 1.0  
**Last Updated**: 2026-02-02
