# Bin 3D

Trợ thủ tối ưu in 3D cho **Bambu Lab A1 + Bambu PETG Basic** trên Bambu Studio.

| Thư mục | Nội dung |
|---|---|
| `CLAUDE.md` | Vai trò Bin 3D cho Claude Code |
| `.claude/skills/bin-3d/` | Skill chẩn đoán và sửa lỗi in |
| `presets/` | Preset người dùng để nhập vào Bambu Studio |
| `reference/official-defaults.md` | Thông số gốc lấy từ profile chính hãng |
| `docs/index.html` | Trang "Sổ tay Bin 3D" |

## Dùng preset
Bambu Studio → **File → Import → Import Configs…** → chọn 2 file trong `presets/`.
Hai preset kế thừa profile chính hãng và chỉ ghi đè vài thông số:

- **Bin3D PETG Basic Min @A1** (filament): max volumetric 13 → 10 mm³/s, retraction 0.4 → 0.6 mm.
- **Bin3D 0.20mm Min @A1** (process): outer wall 200 → 120 mm/s, accel 5000 → 3000, top surface 200 → 150 mm/s, scarf seam Contour (smart), 3 wall loops, avoid crossing walls.

Nếu bản Bambu Studio của bạn không nhận file `.json`, đặt các giá trị trên bằng tay rồi lưu thành preset.
