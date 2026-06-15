# Siamshort Studio MCP — คู่มือต่อ + ใช้งาน (สำหรับทีม)

> ส่งไฟล์นี้ให้ AI ของคุณ (Claude Code / Cursor / Claude Desktop / หรือ AI agent ใดก็ได้ที่รองรับ MCP) แล้วบอกว่า
> **"อ่านไฟล์นี้แล้วต่อ MCP ให้หน่อย"** — AI จะตั้งค่าและเริ่มสร้างหนัง Seedance ได้เลย

**Siamshort Studio** = เว็บ workflow สร้างหนัง **Seedance 2.0** (จัดการ project → chapter → character/scene/item → shot → gen image/video) — มี **MCP server พร้อมใช้** ไม่ต้องเขียนโค้ดเชื่อมเอง

- Server: `siamshort` (เรียกใน config ว่า `seedance-workflow`) — v1.2.0, **74 tools**
- Web: https://studio.siamshort.com

---

## 1. ขอ API Key (ทำเองครั้งเดียว)

> 🔑 **แต่ละคนต้องสร้าง key ของตัวเอง** — key เป็นความลับส่วนตัว ผูกกับ project ที่บัญชีคุณเข้าถึงได้ **อย่าแชร์ key ให้คนอื่น**

1. เปิด https://studio.siamshort.com/api-docs (ต้อง **login** ก่อน)
2. กดปุ่ม **"สร้าง Key"**
3. Copy key ที่ขึ้นต้นด้วย `sk-sdwf-...` เก็บไว้ (จะใช้ในขั้นต่อไป)

---

## 2. การเชื่อมต่อ (Connection)

| | |
|---|---|
| **Endpoint** | `https://studio.siamshort.com/api/mcp` |
| **Transport** | Streamable HTTP |
| **Auth** | `Authorization: Bearer sk-sdwf-...` |
| **ทางเลือก auth** | ต่อท้าย URL ได้: `https://studio.siamshort.com/api/mcp?token=sk-sdwf-...` |

### Claude Code (CLI) — วิธีเร็วสุด
```bash
claude mcp add --transport http seedance-workflow \
  https://studio.siamshort.com/api/mcp \
  --header "Authorization: Bearer sk-sdwf-YOUR_KEY_HERE"
```
> เพิ่ม `-s user` เพื่อให้ใช้ได้ทุก project (global), หรือ `-s project` เพื่อ commit ลง repo (ระวัง: อย่า commit key ลง git)

### Claude Code / Claude Desktop — แก้ไฟล์ config เอง
เพิ่มลง `mcpServers` ใน config (Claude Code global = `~/.claude.json`):
```json
{
  "mcpServers": {
    "seedance-workflow": {
      "type": "http",
      "url": "https://studio.siamshort.com/api/mcp",
      "headers": { "Authorization": "Bearer sk-sdwf-YOUR_KEY_HERE" }
    }
  }
}
```

### Cursor — `.cursor/mcp.json`
```json
{
  "mcpServers": {
    "seedance-workflow": {
      "url": "https://studio.siamshort.com/api/mcp",
      "headers": { "Authorization": "Bearer sk-sdwf-YOUR_KEY_HERE" }
    }
  }
}
```

> **หลังเพิ่ม config → restart / reconnect** (Claude Code: ปิด-เปิดใหม่ หรือ `/mcp`) ครั้งแรกอาจมี prompt ให้ approve server — กด allow

### ทดสอบว่าต่อติด (ไม่มี client ก็เทสได้ด้วย curl)
```bash
curl -s -X POST "https://studio.siamshort.com/api/mcp" \
  -H "Authorization: Bearer sk-sdwf-YOUR_KEY_HERE" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"list_projects","arguments":{}}}'
```
ถ้าเห็นรายการ project กลับมา = ต่อสำเร็จ ✅

---

## 3. 🔴 กฎสำคัญ ต้องทำตามทุกครั้ง (Virtual Asset Enforcement)

1. **ทุก image/video ที่จะใช้ gen วิดีโอ ต้องเป็น Virtual Asset (VA) ก่อนเสมอ** — upload รูป → `create_virtual_asset` → แล้วค่อยอ้างใน prompt
2. **ก่อนสร้าง VA ใหม่ ให้เรียก `list_virtual_assets` ก่อนทุกครั้ง** ถ้ามี VA ที่ใช้ `imageUrl` เดียวกันอยู่แล้ว → reuse อย่าสร้างซ้ำ
3. ไฟล์ **เสียง (audio) ยกเว้น** ไม่ต้องทำ VA
4. **อย่าใช้ raw image URL ตรงๆ** ใน video gen — ให้ผ่าน VA pipeline เสมอ (คุณภาพดีกว่า โดยเฉพาะ BytePlus ที่ใช้ `asset://` URI)

### Mention Syntax (ใช้อ้าง entity ใน prompt)
| สัญลักษณ์ | อ้างถึง | ตัวอย่าง |
|---|---|---|
| `@CharacterName` | ตัวละคร | `@Somchai วิ่งหนี` |
| `#SceneName` | ฉาก/สถานที่ | `ใน #OldTemple ตอนกลางคืน` |
| `$ItemName` | ไอเทม/พร็อพ | `ถือ $MagicSword` |
| `&AssetName` | Virtual Asset | `&HeroPortrait` |

ระบบจะ auto-resolve เป็น VA URI ให้เอง

---

## 4. Workflow มาตรฐาน (ลำดับที่แนะนำ)

```
1. list_genre_presets              → ดู genre/subGenre/camera/lighting ที่ใช้ได้
2. create_project                  → ตั้งโลก, art style, กล้อง, อัตราส่วน
3. create_character / create_scene / create_item   → สร้าง entity
4. generate_image (หรือ regen_*_image)             → ทำรูป reference ของ entity
5. create_virtual_asset            → (สำคัญ) ทำ VA จากรูป entity
6. create_chapter                  → สร้างบท
7. create_shot                     → สร้าง StoryBox (presetText = สรุปเรื่อง)
8. generate_prompt → update_shot_seedance_prompt   → เขียน Seedance prompt
9. regen_shot_image / gen_manhwa_storyboard        → ทำ storyboard
10. generate_video (หรือ generate_video_byteplus)  → gen วิดีโอ
11. poll_video / poll_video_byteplus               → รอผล แล้วเอา videoUrl
```

### ทางลัด: Story Workflow อัตโนมัติ (one-shot)
ถ้าอยากให้ AI สร้างทั้งเรื่องในคำสั่งเดียว ใช้กลุ่ม `story_*`:
```
story_workflow_start  (ใส่ synopsis + characters + scenes + items + shots)
  → หยุดที่ user_review ให้ตรวจ
  → story_workflow_advance (อนุมัติ)
  → story_gen_images_batch    (ทำรูป asset ทั้งหมด, เรียกซ้ำจน remaining=0)
  → story_gen_prompts_all     (เขียน prompt ทุก shot ต่อเนื่องกัน)
  → story_gen_storyboards_batch (ทำ storyboard ทั้งหมด)
  → story_gen_video_next      (gen วิดีโอทีละ shot ต่อเนื่อง) + story_poll_generation
```

---

## 5. Tool Reference (74 tools)

### Discovery & Project
| Tool | หน้าที่ |
|---|---|
| `list_genre_presets` | ดู genre/subGenre/camera/lighting IDs ที่ใช้ได้ (เรียกก่อนสร้าง project) |
| `list_projects` | list project ทั้งหมดที่ key เข้าถึงได้ |
| `create_project` | สร้าง project (name*, world, artStyle, genre, camera, aspectRatio) |
| `get_project` | ดูรายละเอียด project |
| `update_project` | แก้ค่า project |
| `get_full_project_context` | โหลด context ทั้งหมด (world+chars+scenes+items+chapters+shots) — ใช้ก่อนทำงานต่อเพื่อ continuity |

### Chapter
| Tool | หน้าที่ |
|---|---|
| `create_chapter` | สร้างบท (projectUid*, title*, mode, genre, graphicStyle, camera) |
| `list_chapters` | list บททั้งหมด |
| `delete_chapter` | ลบบท (ลบบทสุดท้ายไม่ได้) |

### Character / Scene / Item (Assets)
| Tool | หน้าที่ |
|---|---|
| `create_character` / `create_scene` / `create_item` | สร้าง entity |
| `get_character` / `get_scene` / `get_item` | ดูรายละเอียด entity |
| `update_character` / `update_scene` / `update_item` | แก้ entity |
| `list_assets` | list virtual assets (char/scene/item) ใน project |
| `batch_update_assets` | แก้หลาย asset ในครั้งเดียว |
| `update_asset` | แนบ imageUrl/desc ให้ asset |
| `delete_asset` | ลบ entity |
| `regen_character_image` / `regen_scene_image` / `regen_item_image` | gen รูป reference ใหม่ของ entity |

### Shot (StoryBox)
| Tool | หน้าที่ |
|---|---|
| `create_shot` | สร้าง StoryBox (presetText = สรุปเรื่อง, seedancePrompt = prompt วิดีโอ) |
| `list_shots` / `get_shot` | list / ดู StoryBox |
| `update_shot` | แก้ field / link entity (characterIds, sceneIds, itemIds) |
| `update_shot_seedance_prompt` | เขียนเฉพาะ Seedance prompt (set status=prompt_ready) |
| `update_shot_storyboard` | set storyboard URL ตรงๆ จาก CDN |
| `regen_shot_prompt` | gen prompt ใหม่ของ shot เดิม |
| `regen_shot_image` | gen storyboard ใหม่ |
| `gen_manhwa_storyboard` | gen storyboard สไตล์ manhwa (panel+bubble+SFX) — ทำคู่กับ regular |
| `regen_shot_video` | gen วิดีโอใหม่ link เป็น version |
| `list_shot_videos` | list ทุก video attempt ของ shot |
| `delete_shot` | ลบ shot |

### Generation
| Tool | หน้าที่ |
|---|---|
| `generate_image` | gen รูป (มี shotUid = async คืน jobId → poll_image_task / ไม่มี = sync) |
| `poll_image_task` | เช็คสถานะ async image |
| `generate_prompt` | gen Seedance prompt จาก คำบรรยายธรรมชาติ + genre/style |
| `generate_video` | gen วิดีโอผ่าน Ark Seedance 2.0 → คืน taskId |
| `poll_video` | เช็คสถานะ video (Ark) |
| `generate_video_byteplus` | gen วิดีโอผ่าน BytePlus Official (คุณภาพสูง, ต้องใช้ VA) → taskId |
| `poll_video_byteplus` | เช็คสถานะ video (BytePlus) + token/credits |
| `generate_cover` | gen ปก/โปสเตอร์ project |

### Virtual Assets & Upload
| Tool | หน้าที่ |
|---|---|
| `upload_image` | upload รูป (base64/URL) → คืน permanent URL (ต้องทำ VA ต่อ) |
| `create_virtual_asset` | ทำ VA จาก image/video URL (sync ไป xskill + BytePlus) — **เช็ค list ก่อน** |
| `list_virtual_assets` | list VA ทั้งหมด (เช็ค syncStatus / byteplusSyncStatus) |
| `delete_virtual_asset` | ลบ VA |
| `sync_virtual_asset_byteplus` | sync VA เดิมไป BytePlus |

### Audio (ยกเว้น VA)
| Tool | หน้าที่ |
|---|---|
| `upload_shot_audio` | upload เสียง reference ให้ shot (URL/base64) |
| `request_audio_upload` → `confirm_audio_upload` | upload เสียงไฟล์ใหญ่ผ่าน direct URL แล้ว confirm |
| `upload_shot_video` | upload วิดีโอ reference ให้ shot (อ้างด้วย `%ref`) |

### Music Video Pipeline (`mv_*`)
| Tool | หน้าที่ |
|---|---|
| `mv_upload_audio` | upload track เพลงเข้า MV chapter |
| `mv_auto_producer` → `mv_get_producer_result` → `mv_apply_producer_option` | AI Producer (GPT 5.5) ฟังเพลง เสนอ 4 วิธีตัด segment แล้ว apply |
| `mv_create_segments` / `mv_list_segments` | สร้าง/ดู segment (≤14 วิ/segment) |
| `mv_ai_director` | AI Director วิเคราะห์ทุก segment เสนอ direction |
| `mv_write_shot_prompt` / `mv_batch_write_prompts` | เขียน prompt ราย segment / หลาย segment |
| `mv_change_shot_type` | เปลี่ยนชนิด shot (singing/dancing/story/cinematic/mixed) |
| `mv_get_shot_details` | ดูรายละเอียด segment |
| `mv_export` | รวมทุก segment + เพลง เป็น MP4 เดียว |

### Story Workflow อัตโนมัติ (`story_*`)
| Tool | หน้าที่ |
|---|---|
| `story_workflow_start` | สร้างทั้ง project+world+chars+scenes+items+chapter+shots ในคำสั่งเดียว (หยุดที่ user_review) |
| `story_workflow_status` | เช็คสถานะ workflow |
| `story_workflow_advance` | ผ่าน checkpoint user_review |
| `story_gen_images_batch` | gen รูป asset ทั้งหมด (batch 5, เรียกซ้ำจน remaining=0) |
| `story_gen_prompts_all` | gen prompt ทุก shot ต่อเนื่อง (continuity) |
| `story_gen_storyboards_batch` | gen storyboard ทั้งหมด (batch 5) |
| `story_gen_video_next` | gen วิดีโอ shot ถัดไป (extend ต่อจาก shot ก่อนเพื่อ continuity) |
| `story_poll_generation` | poll สถานะการ gen |

---

## 6. (ทางเลือก) ให้ AI สร้าง Skill `/siamshort` ให้อัตโนมัติ

> ถ้า AI ของคุณรองรับ skill/slash-command (เช่น Claude Code) บอกว่า **"สร้าง skill ชื่อ siamshort ตามไฟล์นี้"**
> AI จะสร้างไฟล์ `.claude/skills/siamshort/SKILL.md` ในโปรเจกต์ ด้วยเนื้อหาด้านล่าง (ก๊อปได้เลย):

```markdown
---
name: siamshort
description: "Siamshort Studio — Seedance 2.0 film production via MCP. Use when user says '/siamshort', 'สร้างหนัง seedance', 'seedance project', 'siamshort', or wants to create projects/characters/scenes/shots and gen image+video through the seedance-workflow MCP server."
user_invocable: true
---

# Siamshort — Seedance 2.0 Film Production (MCP)

ควบคุม Siamshort Studio ผ่าน MCP server `seedance-workflow` (74 tools) เพื่อสร้างหนัง Seedance 2.0
ทั้ง pipeline: project → chapter → character/scene/item → shot → gen image/video
เอกสารฉบับเต็ม: `SIAMSHORT-MCP-SETUP.md`

## Prerequisite
ต้องต่อ MCP `seedance-workflow` แล้ว (ดู SIAMSHORT-MCP-SETUP.md). ถ้า tools ยังไม่โผล่ → restart / reconnect.

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
```

> **หมายเหตุ**: ปรับ description/persona ให้เข้ากับ AI ของทีมได้ตามสะดวก ส่วน workflow + กฎ VA ให้คงไว้

---

## 7. เคล็ดลับ
- **ก่อนทำงานต่อใน project เดิม** เรียก `get_full_project_context` ก่อนเสมอ เพื่อรักษา continuity
- **gen วิดีโอคุณภาพสูง** ใช้ `generate_video_byteplus` + VA ที่ `byteplusSyncStatus='ready'`
- **เลี่ยง VA ซ้ำ** `list_virtual_assets` ก่อน `create_virtual_asset` ทุกครั้ง
- async tools (`generate_image` แบบมี shotUid, `generate_video*`) คืน jobId/taskId → ต้อง poll ทุก 5-10 วิ จนกว่า status = done/success

---

*จัดทำโดย Friday (Oracle ของภูมิ) — 2026-06-15*
