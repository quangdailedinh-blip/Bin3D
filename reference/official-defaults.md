# Thông số gốc chính hãng (đã kiểm chứng)

Nguồn: repo chính thức `bambulab/BambuStudio`, nhánh `master`, thư mục `resources/profiles/BBL/`.
Đã đối chiếu ngày 2026-11-17 bằng cách gộp chuỗi kế thừa của profile.

## Filament `Bambu PETG Basic @BBL A1`
Kế thừa: `fdm_filament_common` → `fdm_filament_pet` → `Bambu PETG Basic @base` → `@BBL A1`

| Khóa | Giá trị |
|---|---|
| nozzle_temperature / initial_layer | 245 / 245 °C |
| Khoảng nhiệt đầu phun cho phép | 230–270 °C |
| textured_plate_temp / hot_plate_temp | 70 °C |
| fan_min_speed / fan_max_speed | 30% / 50% |
| overhang_fan_speed | 50% |
| close_fan_the_first_x_layers | 3 |
| filament_flow_ratio | 0.94 |
| filament_max_volumetric_speed | 13 mm³/s |
| filament_retraction_length | 0.4 mm |
| filament_wipe / wipe_distance | bật / 1 mm |
| filament_z_hop_types | Spiral Lift |
| slow_down_layer_time | 12 s |

## Process `0.20mm Standard @BBL A1`
| Khóa | Giá trị |
|---|---|
| outer_wall_speed | 200 mm/s |
| inner_wall_speed | 300 mm/s |
| top_surface_speed | 200 mm/s |
| outer_wall_acceleration | 5000 mm/s² |
| default_acceleration | 6000 mm/s² |
| initial_layer_speed | 50 mm/s |
| seam_position | aligned |
| seam_slope_type (scarf) | none |
| seam_gap (mặc định chương trình) | 15% |
| wall_loops | 2 |
| top_shell_layers / pattern | 5 / monotonicline |
| ironing_type | no ironing (flow 10%, spacing 0.15) |
| reduce_crossing_wall | 0 |

## Tên khóa scarf seam (từ `src/libslic3r/PrintConfig.cpp`)
`seam_slope_type` = none | external (Contour) | all (Contour and hole) ·
`seam_slope_conditional` (Smart scarf, mặc định bật) · `seam_slope_steps` (10) ·
`seam_slope_min_length` (Scarf length, 10) · `seam_slope_inner_walls` (bật).
