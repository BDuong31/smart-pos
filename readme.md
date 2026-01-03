# Smart POS System (Monorepo)

Hệ thống Quản lý Bán hàng đa nền tảng. Quản lý bằng **Monorepo**, **pnpm Workspaces** và **Git Submodules**.

---

## Cấu trúc dự án

Dự án này liên kết 3 kho lưu trữ độc lập trên GitHub:

* **[smart-pos-nest](https://github.com/BDuong31/smart-pos-nest)**: Backend (NestJS + Prisma 7)
* **[smart-pos-next](https://github.com/BDuong31/smart-pos-next)**: Web Dashboard (Next.js 15)
* **[smart-pos-mobile](https://github.com/BDuong31/smart-pos-mobile)**: Mobile App (React Native/Expo)

---

## Hướng dẫn cài đặt

### 1. Clone dự án (Bao gồm Submodules)
```bash
git clone --recursive https://github.com/BDuong31/smart-pos.git
cd smart-pos
```

### 2. Cài đặt thư viện
```bash
pnpm install
```

### 3. Thiết lập Database (Docker)
```bash
docker-compose up -d
cd smart-pos-nest
npx prisma migrate dev
```

---

## Quy trình đồng bộ hóa (Git Submodules)

Để cập nhật code cho cả Repo Riêng và Repo Tổng, thực hiện theo 2 bước:

**Bước 1: Push tại thư mục con (Ví dụ Backend)**
```bash
cd smart-pos-nest
git add .
git commit -m "mô tả thay đổi"
git push origin main
```

**Bước 2: Cập nhật tại thư mục gốc (smart-pos)**
```bash
cd ..
git add smart-pos-nest
git commit -m "sync: cập nhật backend submodule"
git push origin main
```

---

## Lệnh chạy dự án (Development)

Chạy từ thư mục gốc bằng lệnh pnpm filter:

* **Backend**: `pnpm --filter smart-pos-nest dev`
* **Dashboard**: `pnpm --filter smart-pos-next dev`
* **Mobile**: `pnpm --filter smart-pos-mobile start`

---

## Tác giả
* **BDuong31** - [GitHub Profile](https://github.com/BDuong31)
