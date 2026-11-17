---
name: bin-3d
description: Chẩn đoán và sửa lỗi in 3D cho Bambu Lab A1 + PETG Basic trong Bambu Studio — dư nhựa/sợi tơ (stringing, blob), bề mặt không láng, đường nối (seam) lộ rõ, bề mặt không đều nhựa (under/over-extrusion, gợn sóng). Dùng khi người dùng mô tả hoặc gửi ảnh bản in lỗi, hỏi thông số PETG, hoặc muốn tối ưu file từ MakerWorld.
---

# Bin 3D — Sổ tay sửa lỗi PETG Basic trên Bambu A1

## 0. Profile gốc (bắt đầu từ đây)
Chọn đúng: Printer `Bambu Lab A1 0.4 nozzle` + Filament `Bambu PETG Basic` + Process `0.20mm Standard @BBL A1`.
Giá trị tham khảo (kiểm tra lại profile trong bản Bambu Studio đang dùng):

| Thông số | Mặc định chính hãng (đã kiểm chứng) | Khi cần chỉnh |
|---|---|---|
| Nhiệt đầu phun | 245 °C (lớp đầu 245) | 235–255 °C; giới hạn 230–270 |
| Nhiệt bàn (Textured PEI) | 70 °C | 65–75 °C |
| Quạt làm mát chi tiết | min 30% / max 50%, overhang 50% | 0–60% |
| Flow ratio | 0.94 | chạy Flow Rate calibration |
| Max volumetric speed | 13 mm³/s | 8–10 khi cần mặt đẹp |
| Retraction (A1 direct drive) | 0.4 mm, wipe 1 mm, Spiral Lift | 0.4–1.0 mm — KHÔNG dùng 4–7 mm |
| Outer wall / top surface speed | 200 / 200 mm/s | 100–150 cho mặt đẹp |
| Outer wall acceleration | 5000 mm/s² | 2000–3000 khi gợn sóng |
| Seam | aligned, scarf tắt | scarf Contour (smart) |
| Sấy nhựa | 65 °C / 8 h (máy sấy) | hoặc trên bàn A1 75 °C / 12 h |

Chi tiết và nguồn: `reference/official-defaults.md`. Preset nhập sẵn: `presets/`.

⚠️ PETG trên **Smooth PEI** phải bôi keo dán (glue stick) làm lớp tách, nếu không có thể dính chết và bóc rách mặt bàn. Ưu tiên **Textured PEI**.

## 1. Checklist trước mọi chẩn đoán (theo thứ tự)
1. **Sấy nhựa** — PETG hút ẩm là nguyên nhân số 1 gây tơ, bọt, mặt sần, tiếng lách tách.
2. Lau đầu phun (nhựa PETG bám đầu phun → kéo vết lên bề mặt).
3. Lau bàn bằng nước rửa chén/IPA, không chạm tay.
4. Chạy **Calibration → Flow Dynamics** (Pressure Advance) và **Flow Rate** cho cuộn nhựa này.
5. Kiểm tra Slice preview: đúng filament profile, không bị override bởi project MakerWorld.

## 2. Bảng lỗi → cách sửa

### A. Dư nhựa: sợi tơ, cục nhựa (stringing / blobs / zits)
1. Sấy nhựa (bắt buộc trước).
2. Giảm nhiệt đầu phun từng bước 5 °C (in tháp nhiệt: Calibration → Temperature).
3. Filament settings → Retraction (bật override): length 0.4 → 0.6–1.0 mm (tăng 0.2 mm mỗi lần), speed 30–40 mm/s. In test retraction (Calibration → Retraction test) trước.
4. Process → Others/Quality: bật **Wipe while retracting**, wipe distance 1 → 1.5–2 mm; Travel: **Avoid crossing walls** = bật (giảm vệt kéo qua bề mặt).
5. Z-hop: PETG hay kéo tơ khi Z-hop cao → dùng Z-hop 0.2–0.4 mm, kiểu Spiral/Slope. (Lưu ý cộng đồng báo A1 có thể bỏ qua spiral Z-hop khi tắt timelapse.)
6. Over-extrusion toàn bộ → giảm Flow ratio 0.98–0.95 sau khi chạy Flow Rate calibration.
7. Tơ siêu mảnh còn sót: hơ nhanh bằng súng khò nhiệt sau khi in.

### B. Bề mặt không láng mịn (sần, gợn, xỉn)
1. Ẩm nhựa → sấy.
2. Giảm tốc độ tường ngoài: Process → Speed → Outer wall 200 → 60–120 mm/s; giảm Max volumetric speed còn 8–10 mm³/s.
3. Bật **Quality → Ironing** cho mặt trên phẳng (Top surfaces, spacing 0.15, flow 10–15%).
4. Gợn sóng lặp (ringing/ghosting): giảm Outer wall acceleration 5000 → 2000–3000, đặt máy chắc chắn trên mặt phẳng nặng; A1 là bed-slinger nên vật cao/nặng dễ rung → giảm tốc.
5. Mặt trên lỗ chỗ: Top shell layers 5–6, Top surface pattern = Monotonic line.
6. Lớp đầu xấu: chạy Bed leveling + giảm First layer speed 50 → 30 mm/s.
7. Quạt: PETG cần ít quạt cho bám lớp; mặt cong/overhang xấu thì tăng quạt overhang, không tăng quạt toàn bộ quá 50–60%.

### C. Vết nối (seam) lộ rõ
1. Process → Quality → **Seam position**: Aligned (gọn 1 đường) hoặc Back; Random chỉ khi chấp nhận mặt hơi sần.
2. Bật **Scarf joint seam** (Bambu Studio ≥1.9): Scarf seam application = Contour (hoặc Contour and hole), scarf length ~10–20 mm, scarf steps ~10. Không áp scarf ở vùng overhang.
3. **Seam painting** (tô seam) đặt mối nối vào góc cạnh hoặc mặt sau chi tiết.
4. Bật **Seam gap** ~10–15% và **Wipe on loops** — nếu thấy tệ hơn với PETG thì tắt lại (có báo cáo cộng đồng).
5. Chạy Flow Dynamics (Pressure Advance) — PA sai là nguyên nhân chính của seam lồi/lõm.
6. Giảm tốc Outer wall để seam đều hơn; chi tiết trang trí có thể dùng Fuzzy skin để giấu seam.

### D. Bề mặt không đều nhựa (chỗ thiếu, chỗ dư, sọc lớp)
1. Thiếu nhựa / khe hở → kiểm tra Max volumetric speed (quá cao → thiếu nhựa ở đoạn nhanh), hạ xuống 10–12; tăng nhiệt +5 °C.
2. Chạy lại Flow Rate calibration (coarse + fine).
3. Sọc ngang lớp (banding): kiểm tra trục Z sạch/không kẹt, cuộn nhựa không vướng (A1 có buffer phía sau — đảm bảo filament đi trơn), AMS lite kéo không bị kẹt.
4. Vùng tường mỏng/đổi tốc độ: Process → Speed → bật **Slow down for overhangs**; giảm khác biệt tốc độ giữa inner/outer wall.
5. Infill lộ qua tường: Wall loops 3–4, Infill/wall overlap 15%.

## 3. Mẫu trả lời chuẩn của Bin 3D
```
🔎 Lỗi: <tên lỗi>
🎯 Nguyên nhân khả dĩ nhất: <...>
🛠️ Sửa (Bambu Studio):
  1. <Tab → mục → thông số>: <cũ> → <mới>
  2. ...
🧪 Test: <mẫu thử nhỏ cần in>
📌 Nếu chưa hết: <bước tiếp theo>
```

## 4. Nguồn
- Bambu Lab Wiki (Seam/Scarf): https://wiki.bambulab.com/en/software/bambu-studio/Seam
- Bambu Forum: https://forum.bambulab.com
- PETG Basic TDS (thông số nhiệt/quạt/sấy) — tra trên trang sản phẩm Bambu Lab.
- Nguồn cộng đồng (tham khảo, cần kiểm chứng): Polymaker PETG stringing guide, các blog/TikTok/YouTube về A1.
