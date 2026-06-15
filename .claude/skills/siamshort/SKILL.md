---
name: siamshort
description: "Siamshort Studio — Seedance 2.0 film production via MCP. Use when user says '/siamshort', 'สร้างหนัง seedance', 'seedance project', 'siamshort', or wants to create projects/characters/scenes/shots and gen image+video through the seedance-workflow MCP server."
user_invocable: true
---

# Siamshort — Seedance 2.0 Film Production (MCP)

ควบคุม Siamshort Studio ผ่าน MCP server `seedance-workflow` (74 tools) เพื่อสร้างหนัง Seedance 2.0
ทั้ง pipeline: project → chapter → character/scene/item → shot → gen image/video
เอกสารฉบับเต็ม: `ψ/learn/siamshort/SIAMSHORT-MCP-SETUP.md` (Oracle home: /Users/admin/abdul-oracle)

## Prerequisite
ต้องต่อ MCP `seedance-workflow` แล้ว (ดู SIAMSHORT-MCP-SETUP.md). ถ้า tools ยังไม่โผล่ → restart / reconnect (`/mcp`).
MCP tools มาแบบ deferred — ใช้ ToolSearch หา/โหลด schema ก่อนเรียก (เช่น ToolSearch "list_projects siamshort").

## 🔴 กฎเหล็ก (Virtual Asset)
1. ทุก image/video ที่จะใช้ gen วิดีโอ ต้องเป็น Virtual Asset (VA) ก่อนเสมอ
2. ก่อน create_virtual_asset ต้องเรียก list_virtual_assets ก่อนทุกครั้ง — imageUrl ซ้ำให้ reuse
3. audio ยกเว้น · ห้ามใช้ raw image URL ตรงใน video gen (BytePlus ใช้ asset:// คุณภาพสูงกว่า)

## Mention Syntax
@CharacterName = ตัวละคร · #SceneName = ฉาก · $ItemName = ไอเทม · &AssetName = Virtual Asset

## Workflow
1. list_genre_presets  2. create_project  3. create_character/scene/item
4. regen_*_image หรือ generate_image (รูป reference)
5. list_virtual_assets → create_virtual_asset (ทำ VA)
6. create_chapter → create_shot  7. generate_prompt → update_shot_seedance_prompt
8. regen_shot_image (+ gen_manhwa_storyboard)  9. generate_video / generate_video_byteplus → poll_video*
ก่อนทำต่อใน project เดิม: get_full_project_context ก่อนเสมอ

## ทางลัด Story Workflow (สร้างทั้งเรื่องคำสั่งเดียว)
story_workflow_start → (user review) → story_workflow_advance → story_gen_images_batch
→ story_gen_prompts_all → story_gen_storyboards_batch → story_gen_video_next (+ story_poll_generation)

## Music Video
mv_upload_audio → mv_auto_producer → mv_get_producer_result → mv_apply_producer_option
→ mv_batch_write_prompts → (gen video ราย segment) → mv_export

## Behavior
- async tools คืน jobId/taskId → poll ทุก 5-10 วิ จน done/success
- ทุก gen เสียเครดิต → ตรวจ prompt ก่อนสั่ง
- gen วิดีโอคุณภาพสูง: generate_video_byteplus + VA byteplusSyncStatus='ready'
- เขียน Seedance prompt: ใช้ความรู้จาก [[2026-06-15_fortal-ai-film-director]] (กล้อง/เลนส์/แสง + timeline + 中文)
