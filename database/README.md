# 🗄️ Pawnder Database Setup

**SEP490_G151** - Hướng dẫn setup và maintain database

## 📋 Tổng Quan

PostgreSQL database với 2 file SQL:
- `pawnder_database.sql` - Schema và dữ liệu mẫu (dùng cho development)
- `pawnder_data_backup.sql` - Backup (dùng để restore)

## 🛠️ Prerequisites

- PostgreSQL 12+
- pgAdmin (khuyến nghị) hoặc psql

## 📝 Setup

### Phương Pháp 1: pgAdmin (Khuyến nghị)

1. Mở pgAdmin → Chuột phải **Databases** → **Create → Database**
2. Tên: `pawnder_database` → **Save**
3. Chọn database → **Alt + Shift + Q** (Query Tool)
4. **Ctrl + O** → Chọn `pawnder_database.sql`
5. **F5** (Execute)

### Phương Pháp 2: psql

```bash
# Tạo database
psql -U postgres
CREATE DATABASE pawnder_database;
\q

# Import schema
psql -U postgres -d pawnder_database -f pawnder_database.sql
```

## ⚙️ Connection String

Cấu hình trong `BackEnd/BE/appsettings.json`:

```json
{
  "ConnectionStrings": {
    "DbContext": "Host=localhost;Port=5432;Database=pawnder_database;Username=postgres;Password=YOUR_PASSWORD;SSL Mode=Prefer;Trust Server Certificate=true"
  }
}
```

## 🔍 Verify

```sql
SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';
```

Sẽ thấy các bảng: `User`, `Pet`, `ChatUser`, `PetAppointment`, etc.

## 🔄 Restore Backup

```bash
psql -U postgres -d pawnder_database < pawnder_data_backup.sql
```

## 🛠️ Maintenance Guide

### Database Migrations

#### Sử dụng EF Core Migrations (Khuyến nghị)

```bash
cd BackEnd/BE

# Tạo migration
dotnet ef migrations add MigrationName

# Apply migration
dotnet ef database update

# Rollback
dotnet ef database update PreviousMigrationName

# Xem migration history
dotnet ef migrations list
```

#### Sử dụng SQL Scripts

1. Tạo file SQL với changes
2. Test trên development database
3. Apply lên production
4. Backup trước khi apply

### Thêm Bảng Mới

**Cách 1: Qua EF Core**
1. Tạo Model trong `BackEnd/BE/Models/`
2. Thêm vào DbContext
3. Tạo migration: `dotnet ef migrations add AddNewTable`
4. Apply: `dotnet ef database update`

**Cách 2: Qua SQL**
```sql
CREATE TABLE "NewTable" (
    "Id" SERIAL PRIMARY KEY,
    "Name" VARCHAR(100) NOT NULL,
    "CreatedAt" TIMESTAMP DEFAULT NOW()
);
```

### Thêm Column

```sql
ALTER TABLE "User" ADD COLUMN "NewColumn" VARCHAR(50);
```

Hoặc qua EF Core migration.

### Thêm Index

```sql
CREATE INDEX "IX_User_Email" ON "User"("Email");
```

### Backup Database

```bash
# Full backup
pg_dump -U postgres -d pawnder_database > backup_$(date +%Y%m%d).sql

# Backup chỉ schema
pg_dump -U postgres -d pawnder_database --schema-only > schema_backup.sql

# Backup chỉ data
pg_dump -U postgres -d pawnder_database --data-only > data_backup.sql
```

### Restore Database

```bash
psql -U postgres -d pawnder_database < backup_file.sql
```

### Common Queries

```sql
-- Xem tất cả bảng
\dt

-- Xem cấu trúc bảng
\d "User"

-- Đếm records
SELECT COUNT(*) FROM "User";

-- Xem indexes
\di

-- Xem foreign keys
SELECT * FROM information_schema.table_constraints 
WHERE constraint_type = 'FOREIGN KEY';
```

### Performance Optimization

1. **Thêm Indexes** cho columns thường query
2. **Analyze tables**: `ANALYZE "User";`
3. **Vacuum**: `VACUUM ANALYZE;`
4. **Monitor slow queries**: Enable `log_min_duration_statement`

## 🐛 Troubleshooting

- **"database does not exist"**: Tạo database trước khi import
- **"permission denied"**: Grant privileges cho user
- **"connection refused"**: Kiểm tra PostgreSQL service đang chạy
- **"password authentication failed"**: Kiểm tra username/password
- **"relation already exists"**: Drop và tạo lại hoặc skip existing tables

## 🔐 Security Best Practices

1. Không commit credentials vào git
2. Sử dụng environment variables cho production
3. Tạo user riêng cho ứng dụng (không dùng postgres)
4. Enable SSL trong production
5. Regular backups
6. Limit database user permissions

---

**Version**: 1.0  
**Last Updated**: 2026-02-02
