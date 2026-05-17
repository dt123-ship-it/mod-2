# 🐇 Bhop Mod — Minecraft 1.21.4 Fabric

Mod **Bunny Hop** cho Minecraft: nhảy liên tục trong khi chạy để tăng tốc độ di chuyển!

---

## ⚙️ Cơ chế hoạt động

| Sự kiện | Kết quả |
|---|---|
| Rời đất khi đang sprint + di chuyển | +0.015 tốc độ tích lũy |
| Đang trên không + sprint | Áp dụng tốc độ bhop vào velocity |
| Không sprint / không di chuyển | Tốc độ × 0.98 (giảm dần) |
| Tốc độ vượt ngưỡng | Giới hạn ở 3.0 blocks/tick |

**Công thức:**
```
bhopSpeed = min(bhopSpeed + 0.015, 3.0)   // mỗi jump thành công
velocity.xz = direction × (0.13 + bhopSpeed)
```

---

## 🚀 Cách build

### Yêu cầu
- Java 21+
- Git

### Các bước

```bash
# 1. Clone / download project
cd bhop-mod

# 2. Build mod
./gradlew build          # Linux/macOS
gradlew.bat build        # Windows

# 3. File .jar xuất hiện tại:
#    build/libs/bhop-mod-1.0.0.jar
```

---

## 📦 Cài đặt

1. Cài **Fabric Loader 0.16.9+** cho Minecraft 1.21.4
2. Tải **Fabric API** (bắt buộc)
3. Copy `bhop-mod-1.0.0.jar` vào thư mục `.minecraft/mods/`
4. Khởi động Minecraft với profile Fabric

---

## 🎮 Cách chơi

1. **Giữ Shift + W** (sprint + forward) — hoặc double-tap W để sprint
2. **Nhảy** (Space) — và **nhảy lại ngay khi chạm đất**
3. Tốc độ tăng dần mỗi lần nhảy thành công!
4. Dừng nhảy hoặc dừng sprint → tốc độ giảm dần về 0

> **Mẹo:** Timing quan trọng! Nhảy ngay khi chân chạm đất để duy trì momentum.

---

## ⚙️ Tùy chỉnh thông số

Chỉnh trong `BhopMod.java`:

```java
public static final double MAX_SPEED    = 3.0;   // Tốc độ tối đa
public static final double ACCELERATION = 0.015; // Gia tốc mỗi nhảy
public static final double BASE_SPEED   = 0.13;  // Tốc độ cơ bản
public static final double SPEED_DECAY  = 0.98;  // Hệ số giảm (thấp hơn = giảm nhanh hơn)
```

---

## 📁 Cấu trúc project

```
bhop-mod/
├── src/main/java/com/bhopmod/
│   ├── BhopMod.java                    # Entry point
│   ├── BhopState.java                  # Interface lưu trạng thái
│   └── mixin/
│       └── ClientPlayerEntityMixin.java # Logic bhop chính
├── src/main/resources/
│   ├── fabric.mod.json                 # Metadata mod
│   └── bhopmod.mixins.json             # Khai báo mixin
├── build.gradle
├── gradle.properties
└── settings.gradle
```

---

## 📋 Phiên bản tương thích

| Component | Phiên bản |
|---|---|
| Minecraft | 1.21.4 |
| Fabric Loader | ≥ 0.16.9 |
| Fabric API | 0.119.2+1.21.4 |
| Java | 21 |
