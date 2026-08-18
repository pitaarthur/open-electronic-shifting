# Technical Risks and Unknowns / ความเสี่ยงและสิ่งที่ยังไม่ทราบ

Scale / ระดับ: Likelihood `L/M/H`; Impact `L/M/H`. / โอกาสและผลกระทบ `ต่ำ/กลาง/สูง`

| ID | Risk or unknown / ความเสี่ยงหรือสิ่งที่ยังไม่ทราบ | L / โอกาส | I / ผลกระทบ | Mitigation and evidence / การลดความเสี่ยงและหลักฐาน | Owner / ผู้รับผิดชอบ | Status / สถานะ |
|---|---|:---:|:---:|---|---|---|
| R-01 | No usable third-party GeX actuation path. / ไม่มีช่องทางบุคคลที่สามสั่ง GeX ได้ | H | H | Run R1–R4; prefer donor transmitter; no large purchase before Gate A. / ทำ R1–R4 ใช้วงจรเดิมก่อน ไม่ซื้อของมากก่อน Gate A | Builder / ผู้สร้าง | Open / เปิด |
| R-02 | ANT+/BLE exposes telemetry/config only, not shift control. / ANT+/BLE มีเพียงเทเลเมทรี/ตั้งค่า ไม่รับคำสั่งเกียร์ | H | H | Require actual directional actuation; never infer from pairing. / ต้องสาธิตสั่งงานจริง ห้ามอนุมานจากการจับคู่ | Builder / ผู้สร้าง | Open / เปิด |
| R-03 | Donor GeX shifter is integrated, inaccessible, potted, or warranty-sensitive. / วงจรชิฟเตอร์เดิมเข้าถึงยาก เคลือบ หรือกระทบประกัน | M | H | Non-invasive inspection first; photograph; define stop point; ask for spare PCB. / ตรวจแบบไม่แกะก่อน ถ่ายภาพ กำหนดจุดหยุด สอบถามแผงวงจรอะไหล่ | Builder / ผู้สร้าง | Open / เปิด |
| R-04 | Paddle/mount obstructs braking after rotation or breakage. / แป้น/จุดยึดขวางเบรกเมื่อหมุนหรือแตก | M | H | Independent mount, generous swept clearance, witness marks, Gate B fault poses. / จุดยึดอิสระ เผื่อระยะ เครื่องหมาย และท่าความขัดข้อง Gate B | Builder / ผู้สร้าง | Open / เปิด |
| R-05 | Accidental shifts on rough terrain or during braking. / เปลี่ยนเกียร์โดยไม่ตั้งใจบนทางขรุขระหรือขณะเบรก | M | M | Guard/recess, tactile force trial, one command per press, controlled ride test. / ขอบป้องกัน ทดลองแรงกด หนึ่งคำสั่งต่อการกด และทดสอบควบคุม | Builder / ผู้สร้าง | Open / เปิด |
| R-06 | Stuck contact or bounce triggers repeated/multiple shifts. / หน้าสัมผัสค้างหรือเด้งทำให้สั่งซ้ำ/หลายเกียร์ | M | M | Characterize donor behavior; mechanical stop; debounce/edge logic if a bridge MCU is used. / ตรวจวงจรเดิม มีตัวหยุด และ debounce หากใช้ MCU | Builder / ผู้สร้าง | Open / เปิด |
| R-07 | Radio pairing accepts only one controller or loses pairing after updates. / วิทยุรับตัวควบคุมเดียวหรือหลุดหลังอัปเดต | M | M | Test power cycle, reset, two sources, and firmware; record versions. / ทดสอบปิดเปิด รีเซ็ต สองแหล่ง และเฟิร์มแวร์ พร้อมบันทึกเวอร์ชัน | Builder / ผู้สร้าง | Open / เปิด |
| R-08 | Water/sweat damages custom switch, wiring, or donor PCB. / น้ำ/เหงื่อทำลายสวิตช์ สาย หรือวงจรเดิม | M | M | Sealed switch, drip loop, enclosure, conformal protection only after RF/repair review, splash test. / สวิตช์กันน้ำ ห่วงหยด กล่อง การเคลือบหลังประเมิน RF/ซ่อม และทดสอบละออง | Builder / ผู้สร้าง | Open / เปิด |
| R-09 | Thin wire snags and pulls on the lever or hose. / สายเล็กเกี่ยวแล้วดึงมือเบรกหรือสายไฮดรอลิก | M | H | Independent routing, breakaway connector, strain relief, full-steering inspection. / เดินสายอิสระ คอนเน็กเตอร์หลุดได้ ลดแรงดึง และตรวจเมื่อเลี้ยวเต็ม | Builder / ผู้สร้าง | Open / เปิด |
| R-10 | Wrong exact Shimano lever geometry. / รูปทรงมือเบรก Shimano รุ่นจริงไม่ตรง | M | M | Record model and measure physical lever before CAD; avoid “universal” V1. / บันทึกรุ่นและวัดของจริงก่อน CAD ไม่ทำสากลใน V1 | Builder / ผู้สร้าง | Open / เปิด |
| R-11 | Firmware/app changes invalidate observed protocol. / เฟิร์มแวร์/แอปเปลี่ยนจนโปรโตคอลเดิมใช้ไม่ได้ | M | M | Pin and record versions; keep donor bridge fallback; retest before update. / ตรึงและบันทึกเวอร์ชัน เก็บวงจรเดิมเป็นทางสำรอง ทดสอบก่อนอัปเดต | Builder / ผู้สร้าง | Open / เปิด |
| R-12 | Bike-computer independence impossible due to GeX pairing model. / ไมล์อิสระทำไม่ได้เพราะรูปแบบจับคู่ GeX | M | L for V1 / ต่ำต่อ V1 | Defer; it must not block manual V1. / เลื่อนและห้ามขวาง V1 แบบมือ | Builder / ผู้สร้าง | Deferred / เลื่อน |
| R-13 | Project cost grows into full replacement-shifter cost. / ต้นทุนบานจนเท่าชิฟเตอร์ทดแทนทั้งชุด | M | M | Purchase gates and separate RF budget; compare at each phase gate. / จุดอนุมัติซื้อและงบ RF แยก เปรียบเทียบทุกระยะ | Builder / ผู้สร้าง | Open / เปิด |

## Top unknowns to close first / สิ่งที่ต้องหาคำตอบก่อน

1. Is an original GeX shifter/controller available as a donor, and can its switch contacts be accessed safely? / มีชิฟเตอร์/คอนโทรลเลอร์ GeX เดิมเป็นต้นทางหรือไม่ และเข้าถึงหน้าสัมผัสได้ปลอดภัยหรือไม่
2. Does WHEELTOP offer any supported remote input or command documentation? / WHEELTOP มีอินพุตรีโมตหรือเอกสารคำสั่งที่รองรับหรือไม่
3. What exactly is the installed Shimano 105 lever model and usable mounting envelope? / มือเบรก Shimano 105 ที่ติดตั้งคือรุ่นใดและพื้นที่ยึดใช้งานได้เท่าใด
4. Can both original shift directions be produced from isolated dry contacts? / หน้าสัมผัสแห้งแยกวงจรสั่งได้ทั้งสองทิศหรือไม่
5. Does GeX permit two independent command sources for the later bike-computer phase? / GeX ยอมรับแหล่งคำสั่งอิสระสองแหล่งสำหรับระยะไมล์หรือไม่

