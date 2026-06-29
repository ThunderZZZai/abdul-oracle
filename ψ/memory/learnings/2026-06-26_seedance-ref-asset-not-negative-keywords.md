---
pattern: Seedance face/continuity drift is fixed with reference assets (capture frame → %ref), not by piling negative-prompt keywords
date: 2026-06-26
source: "rrr: abdul-oracle (วิมานทองคำ)"
concepts: [seedance, fable, video-gen, face-lock, continuity, anti-slop, root-cause]
---

# Seedance drift: ref-asset is the root fix, negative keywords are band-aids

## Context
ตลอด loop ทำหนัง "วิมานทองคำ" หน้าตัวละคร (ครีม) เพี้ยน/ถูกโมเดล "ปรับให้คม-มั่นใจขึ้น" และมือ (พราว) สีผิดเป็นประจำ. ผมแก้ด้วยการ **อัด negative-prompt keyword เพิ่มทีละรอบ** (`face changed, beautified, more mature, identity drift, dark discolored hands…`) หลายเทิร์น — ได้ผลบ้างไม่ได้บ้าง.

## Lesson
**เมื่อตัวละคร AI-video drift (หน้า/มือ/ตำแหน่ง) ซ้ำ ≥2 รอบ → หยุดเติม negative keyword แล้วล็อกด้วย reference asset.**
- `capture_video_frame(projectUid, chapterUid, videoUrl, timeSec, name)` จับเฟรมหน้า/มุมที่ดีจากคลิปเก่า → `add_ref_asset_to_shot` → อ้าง `%name` ใน prompt.
- กำกับ `%ref` ให้ใช้ **"หน้า/มุมกล้องเท่านั้น ❌ห้ามลอก graphic style/แสง"**.
- ลุคเปลี่ยน (variant): `regen_character_image(newUid, referenceUrls:[orig.imageUrl], "SAME face but…")` = face-lock.
- negative keyword = patch อาการ ; ref-asset = pin ตัวตน. Patch ซ้ำ = สัญญาณว่าควรหา systemic fix.

## Generalizes to
ทุกงาน generative ที่ "identity/continuity ต้องคงที่ข้ามช็อต" — ถ้าแก้อาการเดิมซ้ำหลายรอบด้วยคำสั่งห้าม ให้สงสัยว่ากำลังรักษาอาการ ไม่ใช่ต้นเหตุ. หา anchor/reference ที่ pin สิ่งที่ต้องคงที่ แทนการบรรยายห้ามไปเรื่อยๆ.

## Bonus (เครื่อง macOS ไม่มี ffmpeg/poppler)
- PDF→text: `swift` PDFKit (`PDFDocument(url:).string`).
- video→poster frame: `qlmanage -t -s <px> -o <dir> <file.mp4>`.
- Seedance/BytePlus (จีน) filter เด้ง: พระพุทธรูป/หิ้งพระ + ผู้เยาว์ในภาวะทุกข์ → ใช้คำสถานที่กลาง + ระบุผู้ใหญ่ + buddha/minor ใน negative.
