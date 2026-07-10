# Hướng Dẫn Cấu Hình Server Palworld (Fast Playthrough)

> [!IMPORTANT]
> Hướng dẫn và cấu hình này được thiết kế **dành riêng cho Palworld Dedicated Server**. Nếu bạn chơi chế độ Singleplayer hoặc Co-op (tạo thế giới trực tiếp trong game), vị trí file cài đặt và cách áp dụng sẽ hoàn toàn khác.

## 1. Cách Áp Dụng Cấu Hình

**LƯU Ý:** KHÔNG sửa trực tiếp vào file `DefaultPalWorldSettings.ini` vì nó sẽ không có tác dụng.

Dưới đây là quy trình chuẩn để vận hành Server bằng Git mà không sợ mất file Save hay bị conflict (xung đột dữ liệu):

**A. Cài đặt lần đầu (Chỉ làm 1 lần trên mỗi máy):**
1. Đảm bảo Server đang tắt. Nếu có sẵn thư mục `Pal/Saved`, hãy xóa nó đi (hoặc đổi tên để backup).
2. Mở Terminal (CMD/PowerShell) tại thư mục `Pal`.
3. Gõ lệnh: `git clone https://github.com/ductongnguyen/new-palword Saved` để kéo dữ liệu về.

**B. Trước khi mở Server để chơi:**
1. Mở Terminal tại thư mục `Pal/Saved`.
2. **Bắt buộc:** Gõ lệnh `git pull` để tải về bản Save mới nhất (phòng trường hợp có thành viên khác vừa host server xong và đã push lên).
3. Khởi động Server và vào game!

**C. Sau khi kết thúc buổi chơi:**
Nhớ đồng bộ dữ liệu Save lên Github để cất giữ an toàn bằng các lệnh sau (chạy tại thư mục `Pal/Saved`):
```bash
git add .
git commit -m "Backup save data - $(date)"
git push
```
---

## 2. Các Cải Tiến Đáng Chú Ý

Dưới đây là danh sách các thông số đã được tối ưu lại so với mặc định để trải nghiệm game "đã" hơn:

| Tên Cài Đặt (Setting) | Giá Trị Mới | Lợi Ích Cốt Lõi |
| :--- | :---: | :--- |
| `ExpRate` | **5.0** | Kinh nghiệm x5, lên cấp vù vù không cần đánh quái nhỏ. |
| `PalCaptureRate` | **3.0** | Tỉ lệ ném cầu bắt dính Pal x3, siêu tiết kiệm Sphere. |
| `PalSpawnNumRate` | **1.5** | Mật độ quái ngoài map x1.5 lần, thế giới nhộn nhịp hơn. |
| `EnemyDropItemRate` | **4.0** | Lượng vật phẩm rơi ra khi giết quái x4 (Tha hồ lấy Dầu, Dịch...). |
| `CollectionDropRate` | **4.0** | Tài nguyên rớt ra khi đập đá/chặt cây x4. |
| `CollectionObjectHpRate` | **0.5** | Máu của cây/đá giảm một nửa, đập vỡ nhanh gấp đôi. |
| `CollectionObjectRespawnSpeedRate`| **3.0** | Cây cối, khoáng sản mọc lại nhanh gấp 3 lần. |
| `ItemWeightRate` | **0.1** | Trọng lượng vật phẩm giảm còn 1/10 (ôm hàng ngàn cục quặng không lo nặng).|
| `ItemCorruptionMultiplier` | **0.1** | Đồ ăn lâu thiu gấp 10 lần. |
| `EquipmentDurabilityDamageRate` | **0.5** | Vũ khí, giáp lâu hỏng hơn gấp đôi. |
| `PlayerStomachDecreaceRate` | **0.5** | Bạn lâu đói hơn gấp đôi. |
| `PlayerStaminaDecreaceRate` | **0.5** | Bạn trâu bò hơn, chạy/bay/leo núi lâu hơn gấp đôi. |
| `PalStomachDecreaceRate` | **0.2** | Lũ Pal lâu đói gấp 5 lần (Ít bỏ việc đi ăn). |
| `PalStaminaDecreaceRate` | **0.2** | Lũ Pal lâu mệt gấp 5 lần (Ít bỏ việc đi ngủ). |
| `bEnableNonLoginPenalty` | **False** | Tắt hình phạt vắng mặt. Cứu lũ Pal khỏi cảnh chết đói/bệnh tật khi chủ Server tắt máy đi ngủ. |
| `WorkSpeedRate` | **5.0** | Tốc độ chế tạo đồ đạc bằng tay x5. |
| `MonsterFarmActionSpeedRate` | **5.0** | Tốc độ rớt đồ trong Nông trại (Ranch) x5. |
| `PalEggDefaultHatchingTime` | **0.1** | Rút ngắn tối đa thời gian đếm ngược ấp trứng. |
| `BaseCampMaxNumInGuild` | **10** | Xây tối đa 10 Căn cứ (Base) cho một Guild. |
| `BuildObjectDeteriorationDamageRate`| **0.0** | Công trình xây ngoài ranh giới Base sẽ không bao giờ tự hỏng. |
| `DeathPenalty` | **None** | KHÔNG rơi đồ, không rớt trang bị khi chết. |

---

## 3. Hướng Dẫn Kết Nối Bằng Radmin VPN

Nếu bạn không thể mở Port (Port Forwarding) cho router mạng ở nhà, cách nhanh gọn và miễn phí nhất để chơi cùng bạn bè là dùng **Radmin VPN** tạo mạng LAN ảo.

**Quy trình thực hiện:**
1. **Tải phần mềm:** Chủ server và tất cả người chơi truy cập [https://www.radmin-vpn.com/](https://www.radmin-vpn.com/) tải và cài đặt Radmin VPN.
2. **Tạo phòng (Dành cho Host):**
   - Mở Radmin VPN, bật nút nguồn lên màu xanh.
   - Chọn menu **Network** -> **Create new network**.
   - Nhập Tên phòng và Mật khẩu, sau đó gửi thông tin này cho bạn bè.
3. **Vào phòng (Dành cho Người chơi):**
   - Mở Radmin VPN, chọn menu **Network** -> **Join network**.
   - Chuyển sang tab **Private Network**, nhập Tên phòng và Mật khẩu do host gửi.
4. **Cách vào Game:**
   - **Host:** Chuột phải vào tên máy của chính mình trên giao diện Radmin VPN, chọn *Copy IP address* (thường có dạng `26.x.x.x`) gửi cho bạn bè.
   - **Người chơi:** Mở game Palworld, chọn **Join Multiplayer Game**, kéo xuống thanh địa chỉ IP ở dưới cùng màn hình và nhập IP của host kèm theo cổng `:8211` (Ví dụ: `26.11.22.33:8211`), sau đó nhấn **Connect**.

> 💡 **Tip:** Nếu bấm Connect mà bị báo `Time out`, hãy chắc chắn cả Host và người chơi đã cấp quyền đi qua Tường lửa (Firewall) cho Palworld và Radmin VPN, hoặc tạm tắt Firewall của Windows.

---

