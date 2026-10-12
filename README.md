# Bài 3 – Tối ưu tốc độ CI bằng Gradle Dependency Caching

## 1. Mục tiêu

Cấu hình Gradle Dependency Caching trong GitHub Actions để giảm thời gian tải lại các thư viện Gradle khi workflow chạy nhiều lần.

## 2. Cấu hình thực hiện

Trong file `.github/workflows/ci.yml`, bổ sung tham số `cache: 'gradle'` vào bước `actions/setup-java@v5`.

```yaml
- name: Set up Java JDK 17
  uses: actions/setup-java@v5
  with:
    java-version: '17'
    distribution: 'temurin'
    cache: 'gradle'
```

## 3. Kết quả kiểm tra

| Nội dung | Lần chạy thứ nhất | Lần chạy thứ hai |
|---|---|---|
| Thời gian toàn bộ Job | Chưa ghi nhận | Chưa ghi nhận |
| Thời gian bước Setup Java | Chưa ghi nhận | Chưa ghi nhận |
| Thời gian bước Run unit tests | Chưa ghi nhận | Chưa ghi nhận |
| Trạng thái cache | Chưa ghi nhận | Chưa ghi nhận |
