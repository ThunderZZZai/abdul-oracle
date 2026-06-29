---
type: learning
date: 2026-06-16
concepts: ["siamshort", "seedance", "image-gen", "timeout", "workflow", "gotcha"]
human: เพชร (Petch)
related: ["[[2026-06-15_siamshort-mcp-connected]]", "[[siamshort]]"]
---

# Siamshort: generate_image sync timeout → ใช้ route ที่ poll ได้แทน

## ปัญหาที่เจอ
- `generate_image` แบบ **standalone (ไม่มี shotUid)** = sync → **timeout ที่ tool layer ทุกครั้ง** (ลองทั้ง laozhang, nanobanana, nanobanana-pro) และ **ไม่มี jobId ให้ poll** → ผลหาย กู้ไม่ได้
- `generate_image` แบบมี `shotUid` = **ถูก BLOCK** ("use story_* or regen_* instead") สำหรับ content ที่อยู่ในโปรเจกต์
- `poll_image_task` ใช้ได้เฉพาะ jobId จาก generate_image ที่มี shotUid → catch-22

## ทางออกที่ใช้ได้จริง (เสถียร)
สร้าง asset ในโปรเจกต์ก่อน แล้ว gen ผ่าน `regen_*` — **call จะ timeout client-side แต่ผลถูกเซฟเข้า asset ฝั่งเซิร์ฟเวอร์** → poll `get_scene` / `get_shot` จน `imageUrl`/`storyboardUrl` โผล่ (ใช้เวลา ~2-4 นาที)

| อยากได้ | ใช้ | ได้อะไร |
|---|---|---|
| **ภาพเดี่ยวคลีน (establishing)** | `create_scene` → `regen_scene_image` → poll `get_scene.imageUrl` | ภาพเดียวคลีน ✅ |
| สตอรีบอร์ดหลายช่อง | `create_shot` (+seedancePrompt) → `regen_shot_image` → poll `get_shot.storyboardUrl` | แผ่นสตอรีบอร์ด 8 ช่อง มี text/กริด |

⚠️ `regen_shot_image` ต้องเซ็ต `seedancePrompt` ก่อน (`update_shot status=prompt_ready`) ไม่งั้น error "Generate prompt first"

## Pattern การ poll
```
regen_*  (timeout — ปล่อยผ่าน)
loop: sleep 45-55s (background) → get_scene/get_shot → ถ้า imageUrl ยัง null วนซ้ำ
```

## รูป reference ไฟล์ในเครื่อง
- `referenceUrls` ต้องเป็น URL → ต้อง `upload_image` ด้วย base64 ก่อน
- base64 ไฟล์ใหญ่ (>~20KB) **ส่งผ่าน tool ไม่ไหว/ไม่ชัวร์** → ทางเลี่ยง: อับดุลดูรูปเอง แล้ว**ถอดโครง/เลย์เอาต์/มุมกล้องใส่ลง prompt** เป็นคำ ได้ผลใกล้เคียงและเสถียรกว่า

> สรุปสั้น: **อย่าใช้ generate_image standalone (ตาย sync) — ไปทาง scene/shot asset + poll เสมอ**
