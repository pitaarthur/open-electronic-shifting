# Decision Log / บันทึกการตัดสินใจ

Do not rewrite history; append superseding decisions and link the earlier ID. / ห้ามแก้ประวัติย้อนหลัง ให้เพิ่มการตัดสินใจใหม่ที่แทนของเดิมและอ้าง ID ก่อนหน้า

| ID | Date / วันที่ | Decision / การตัดสินใจ | Rationale / เหตุผล | Status / สถานะ |
|---|---|---|---|---|
| D-001 | 2026-08-18 | V1 is a personal add-on paddle for the existing Shimano 105 hydraulic brake lever; rear-only 1x GeX. / V1 เป็นแป้นติดเพิ่มส่วนบุคคลสำหรับมือเบรกไฮดรอลิก Shimano 105 เดิม ใช้ตีนผี GeX ระบบ 1x | Controls scope and preserves existing brakes. / คุมขอบเขตและรักษาเบรกเดิม | Accepted / ยอมรับ |
| D-002 | 2026-08-18 | Braking is mechanically/hydraulically independent from all shifter electronics. / เบรกเป็นอิสระทางกลและไฮดรอลิกจากอิเล็กทรอนิกส์ชิฟเตอร์ทั้งหมด | Electronics failure must remove shifting only. / ไฟฟ้าเสียต้องเสียเฉพาะเกียร์ | Accepted / ยอมรับ |
| D-003 | 2026-08-18 | Manual paddles are dumb momentary inputs; protocol and pairing live in a separate bridge. / แป้นมือเป็นหน้าสัมผัสชั่วขณะ โปรโตคอลและการจับคู่อยู่ในกล่องแปลง | Lowest complexity at the brake lever and reusable future architecture. / ลดความซับซ้อนใกล้เบรกและใช้ต่อในอนาคตได้ | Accepted / ยอมรับ |
| D-004 | 2026-08-18 | First command-path spike tests official support and retained original GeX shifter electronics before custom RF. / งานวิจัยแรกตรวจช่องทางผู้ผลิตและวงจรชิฟเตอร์ GeX เดิมก่อน RF ทำเอง | Highest compatibility and lowest V1 protocol risk. / เข้ากันได้สูงและลดความเสี่ยงโปรโตคอล V1 | Accepted / ยอมรับ |
| D-005 | 2026-08-18 | ANT+ bike-computer pairing is not evidence of shift actuation. / การจับคู่ไมล์ ANT+ ไม่ใช่หลักฐานว่าสั่งเปลี่ยนเกียร์ได้ | Connectivity may expose telemetry only. / การเชื่อมต่ออาจมีเพียงเทเลเมทรี | Accepted / ยอมรับ |
| D-006 | 2026-08-18 | Provisional control layout is one simple paddle per lever: left easier, right harder; build one module first then mirror it. / การจัดวางชั่วคราวคือหนึ่งแป้นต่อมือเบรก ซ้ายเบาลง ขวาหนักขึ้น สร้างหนึ่งตัวก่อนแล้วทำอีกข้าง | Interprets “SRAM-like single paddle” predictably without tap/hold ambiguity. / ตีความแบบ SRAM โดยไม่ใช้กดสั้น/ค้างที่กำกวม | Proposed; validate ergonomically / เสนอ รอทดสอบ |
| D-007 | 2026-08-18 | Future bike-computer control is an independent source and cannot become a manual-shifter dependency. / ไมล์ในอนาคตเป็นแหล่งคำสั่งอิสระและห้ามเป็นสิ่งที่ชิฟเตอร์มือต้องพึ่ง | Matches the desired modular system and preserves manual operation. / ตรงกับระบบแยกส่วนและรักษาการสั่งมือ | Accepted / ยอมรับ |
| D-008 | 2026-08-18 | Voice is optional after computer control; automatic shifting is last. / เสียงเป็นตัวเลือกหลังไมล์ และอัตโนมัติเป็นลำดับสุดท้าย | Protects V1 scope. / ป้องกันขอบเขต V1 บาน | Accepted / ยอมรับ |

## New decision template / แบบการตัดสินใจใหม่

| ID | Date / วันที่ | Decision / การตัดสินใจ | Rationale / เหตุผล | Status / สถานะ |
|---|---|---|---|---|
| D-___ | YYYY-MM-DD |  |  | Proposed / Accepted / Superseded |

