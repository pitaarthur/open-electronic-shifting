# Phased Roadmap / แผนงานเป็นระยะ

## Priority order / ลำดับความสำคัญ

1. Physical manual paddle / แป้นเปลี่ยนเกียร์ด้วยมือ
2. Independent bike-computer control / การควบคุมอิสระจากไมล์จักรยาน
3. Optional voice control / การสั่งเสียงแบบเลือกทำ
4. Automatic shifting / การเปลี่ยนเกียร์อัตโนมัติ

## Phase 0 — Feasibility and inventory / ความเป็นไปได้และรายการอุปกรณ์

**Goal / เป้าหมาย:** identify a viable GeX command path before committing to custom electronics. / ระบุช่องทางสั่ง GeX ที่ใช้ได้ก่อนลงทุนกับอิเล็กทรอนิกส์ทำเอง

Tasks / งาน:

- Record exact Shimano and GeX hardware/firmware. / บันทึกฮาร์ดแวร์/เฟิร์มแวร์ Shimano และ GeX ที่แน่นอน
- Ask WHEELTOP the interface questions in the research plan. / ถาม WHEELTOP ตามแผนวิจัย
- Map original pairing and button behavior. / ทำแผนที่การจับคู่และพฤติกรรมปุ่มเดิม
- Test donor switch contacts if available. / ทดสอบหน้าสัมผัสชิฟเตอร์ต้นทางหากมี
- Observe BLE/ANT only as needed; separate telemetry from control. / สังเกต BLE/ANT เท่าที่จำเป็น แยกเทเลเมทรีจากคำสั่ง

**Exit / ผ่าน:** Gate A or a no-go decision. / ผ่าน Gate A หรือบันทึก no-go

## Phase 1 — Mechanical paddle proof / พิสูจน์แป้นเชิงกล

**Goal / เป้าหมาย:** a reversible, ergonomic paddle that cannot obstruct braking. / แป้นถอดกลับได้ ใช้งานสบาย และไม่ขวางเบรก

Tasks / งาน:

- Capture lever geometry and hand positions. / เก็บรูปทรงมือเบรกและท่าจับ
- Make no-electronics ergonomic mockups. / ทำแบบจำลองการยศาสตร์โดยไม่มีไฟฟ้า
- Build one adjustable switch paddle; test clearance/failure poses. / สร้างแป้นสวิตช์ปรับได้หนึ่งตัวและทดสอบระยะ/ท่าความขัดข้อง
- Duplicate/mirror only after the feel and mapping are approved. / ทำซ้ำอีกข้างหลังอนุมัติสัมผัสและการแมป

**Exit / ผ่าน:** Gate B and mechanical portions of Gate C. / ผ่าน Gate B และส่วนเชิงกลของ Gate C

## Phase 2 — Integrated manual V1 / รวมระบบมือ V1

**Goal / เป้าหมาย:** reliable two-direction rear shifting with brake independence. / เปลี่ยนเกียร์หลังสองทิศอย่างน่าเชื่อถือโดยเบรกเป็นอิสระ

Tasks / งาน:

- Package bridge away from brake moving parts. / บรรจุกล่องแปลงให้ห่างชิ้นส่วนเบรกที่เคลื่อนที่
- Add connectors, strain relief, and environmental protection. / เพิ่มคอนเน็กเตอร์ ลดแรงดึง และป้องกันสภาพอากาศ
- Validate stuck switch, bounce, sleep/wake, low battery, and power cycle. / ตรวจสวิตช์ค้าง เด้ง พัก/ปลุก แบตต่ำ และปิดเปิด
- Run bench endurance, then controlled ride. / ทดสอบความทนทานบนแท่นแล้วขี่แบบควบคุม

**Exit / ผ่าน:** Gates C and D; V1 done. / ผ่าน Gate C และ D ถือว่า V1 เสร็จ

## Phase 3 — Independent bike computer / ไมล์จักรยานอิสระ

**Goal / เป้าหมาย:** allow a separate computer/button/touch interface to issue shifts without being required by the manual paddles. / ให้ไมล์หรืออินเทอร์เฟซปุ่ม/จอสั่งเกียร์แยกได้ โดยแป้นมือไม่ต้องพึ่ง

Entry condition / เงื่อนไขเริ่ม:

- Manual V1 is stable. / V1 แบบมือเสถียร
- A second command source is proven compatible with GeX pairing. / พิสูจน์ว่าแหล่งคำสั่งที่สองเข้ากับการจับคู่ GeX

No shared gear-state synchronization is required; display may show telemetry if available, but command safety must not depend on displayed state. / ไม่ต้องซิงก์สถานะเกียร์ การแสดงผลใช้เทเลเมทรีได้แต่ความปลอดภัยของคำสั่งต้องไม่พึ่งสถานะที่แสดง

**Exit / ผ่าน:** each controller works while the other is absent/off, or the limitation is documented and architecture revised. / ตัวควบคุมแต่ละตัวทำงานเมื่ออีกตัวถอด/ปิด หรือบันทึกข้อจำกัดและปรับสถาปัตยกรรม

## Phase 4 — Voice experiment / ทดลองเสียง

Optional and never the sole manual control. Define confirmation, false-trigger prevention, offline behavior, wind/noise tests, and cancellation. / เป็นตัวเลือกและห้ามเป็นตัวควบคุมด้วยมือเพียงอย่างเดียว ต้องกำหนดการยืนยัน ป้องกันคำสั่งหลอก ออฟไลน์ ลม/เสียง และการยกเลิก

## Phase 5 — Automatic shifting research / วิจัยเปลี่ยนเกียร์อัตโนมัติ

Last priority. Requires cadence/speed/load inputs, clear manual override, predictable limits, fault handling, and a separate safety case. It must not degrade the proven manual path. / ลำดับสุดท้าย ต้องมี cadence/ความเร็ว/โหลด การสั่งแทรกด้วยมือ ลิมิตคาดเดาได้ การจัดการข้อผิดพลาด และกรณีความปลอดภัยแยก ห้ามทำให้ทางเดินคำสั่งมือที่พิสูจน์แล้วแย่ลง

## Immediate next actions / งานถัดไปทันที

1. Photograph and record the exact model code on both Shimano levers and the GeX components owned/ordered. / ถ่ายภาพและบันทึกรหัสรุ่นมือเบรก Shimano ทั้งสองข้างและชิ้นส่วน GeX ที่มี/สั่ง
2. Confirm whether an original GeX shifter/controller is physically available for donor inspection. / ยืนยันว่ามีชิฟเตอร์/คอนโทรลเลอร์ GeX เดิมสำหรับตรวจเป็นชิ้นส่วนต้นทางหรือไม่
3. Send the manufacturer questions from R1 and log the answer. / ส่งคำถามผู้ผลิตจาก R1 และบันทึกคำตอบ
4. Create a cardboard/foam paddle mockup; do not attach electronics yet. / ทำแบบจำลองแป้นกระดาษ/โฟม ยังไม่ติดอิเล็กทรอนิกส์
5. Begin Experiment 001 using the template. / เริ่มการทดลอง 001 ด้วยแบบบันทึก

