# GeX Command-Path Research Spike / การวิจัยช่องทางคำสั่ง GeX

## Research question / คำถามวิจัย

What is the least expensive, repeatable, and safe way for a simple external contact to cause one intentional shift in either direction on an owned WHEELTOP EDS GeX rear derailleur?

วิธีใดมีต้นทุนต่ำที่สุด ทำซ้ำได้ และปลอดภัย เพื่อให้หน้าสัมผัสภายนอกอย่างง่ายสั่งตีนผี WHEELTOP EDS GeX ที่เป็นเจ้าของให้เปลี่ยนเกียร์หนึ่งขั้นได้ทั้งสองทิศทาง

## Known versus unknown / สิ่งที่รู้และยังไม่รู้

### Confirmed from official public material, checked 2026-08-18 / ยืนยันจากข้อมูลสาธารณะของผู้ผลิต ตรวจเมื่อ 2026-08-18

- GeX is advertised as fully wireless, 1x, and compatible with 3–14 speeds. / โฆษณาว่า GeX เป็นระบบไร้สาย สำหรับ 1x และรองรับ 3–14 สปีด
- WHEELTOP advertises ANT+ bike-computer connectivity and app fine-tuning. / WHEELTOP ระบุการเชื่อมต่อไมล์ผ่าน ANT+ และปรับผ่านแอป
- The product FAQ says the GeX RD currently cannot pair with MTB shifters or TX components. / FAQ ระบุว่าปัจจุบันตีนผี GeX ยังจับคู่กับชิฟเตอร์ MTB หรือชิ้นส่วน TX ไม่ได้
- WHEELTOP's general FAQ describes automatic pairing between original shifter/controller and RD. / FAQ ทั่วไปอธิบายการจับคู่อัตโนมัติระหว่างชิฟเตอร์/คอนโทรลเลอร์เดิมกับตีนผี

Primary reference / แหล่งหลัก: [Official GeX product page](https://wheeltop.com/products/wheel-top-eds-gex) and [official WHEELTOP FAQ](https://wheeltop.com/pages/avada-faqs).

### Not confirmed / ยังไม่ยืนยัน

- A documented wired shift-command input on the RD. / อินพุตคำสั่งแบบมีสายบนตีนผีที่มีเอกสารรองรับ
- A public BLE characteristic or ANT+ profile that accepts shift actuation. / BLE characteristic หรือ ANT+ profile สาธารณะที่รับคำสั่งเปลี่ยนเกียร์
- Whether app traffic controls actuation or only setup, calibration, telemetry, and firmware. / ทราฟฟิกแอปสั่งเปลี่ยนเกียร์หรือใช้เพียงตั้งค่า คาลิเบรต เทเลเมทรี และเฟิร์มแวร์
- RF band, modulation, authentication, encryption, rolling counters, pairing ownership, and multi-controller support. / ย่าน RF มอดูเลชัน การยืนยันตัวตน การเข้ารหัส ตัวนับเปลี่ยนค่า การเป็นเจ้าของการจับคู่ และการรองรับหลายตัวควบคุม
- Whether donor shifter button contacts can be accessed without damaging the transmitter. / สามารถเข้าถึงหน้าสัมผัสปุ่มชิฟเตอร์ต้นทางโดยไม่ทำให้วงจรส่งเสียหายหรือไม่

## Evidence rules / กฎของหลักฐาน

Each finding must include date, exact model, hardware revision if visible, firmware/app version, test equipment, raw capture filename, procedure, and result. Classify it as `official`, `observed`, `inferred`, or `hypothesis`.

ข้อค้นพบทุกข้อระบุวันที่ รุ่นที่แน่นอน revision ฮาร์ดแวร์ถ้าเห็น เวอร์ชันเฟิร์มแวร์/แอป อุปกรณ์ทดสอบ ชื่อไฟล์ข้อมูลดิบ ขั้นตอน และผล พร้อมจัดประเภทเป็น `official`, `observed`, `inferred` หรือ `hypothesis`

“Device appears in a scan,” “pairs to a computer,” and “reports gear/battery data” are telemetry evidence only. Actuation is proven only when a deliberately generated command causes a repeatable directional shift.

“พบอุปกรณ์ในการสแกน” “จับคู่กับไมล์ได้” และ “รายงานเกียร์/แบตเตอรี่” เป็นหลักฐานด้านเทเลเมทรีเท่านั้น การสั่งงานพิสูจน์ได้เมื่อคำสั่งที่สร้างโดยตั้งใจทำให้ตีนผีเปลี่ยนทิศทางซ้ำได้จริง

## Spike sequence / ลำดับการทดลอง

### R0 — Inventory and exact identity / สำรวจและระบุตัวตน

Record the exact Shimano lever model, GeX RD model/cage, cassette, original GeX shifter model, serial/hardware labels, firmware, app version, bike computer model, and what components are physically available.

บันทึกรุ่นมือเบรก Shimano รุ่น/ความยาวขาตีนผี GeX เฟือง ชิฟเตอร์ GeX เดิม ป้าย serial/hardware เฟิร์มแวร์ เวอร์ชันแอป รุ่นไมล์ และรายการชิ้นส่วนที่มีจริง

**Exit:** inventory complete; no purchase yet. / **ผ่าน:** รายการครบ ยังไม่ซื้อของ

### R1 — Ask the manufacturer / สอบถามผู้ผลิต

Ask WHEELTOP whether GeX offers: a remote-button accessory, documented external switch input, developer protocol/SDK, BLE actuation characteristic, ANT+ control profile, replacement shifter PCB, or supported pairing of two command sources. Ask specifically whether bike-computer connectivity is read-only telemetry or supports shifting.

สอบถาม WHEELTOP ว่า GeX มีปุ่มรีโมต อินพุตสวิตช์ภายนอก โปรโตคอล/SDK สำหรับนักพัฒนา BLE characteristic สำหรับสั่งงาน ANT+ control profile แผงวงจรชิฟเตอร์อะไหล่ หรือการจับคู่แหล่งคำสั่งสองตัวหรือไม่ ถามตรงๆ ว่าการเชื่อมต่อไมล์เป็นเทเลเมทรีอ่านอย่างเดียวหรือสั่งเปลี่ยนเกียร์ได้

**Exit:** save written response verbatim with date; do not disclose secrets or request unsafe bypasses. / **ผ่าน:** เก็บคำตอบเป็นลายลักษณ์อักษรพร้อมวันที่ ไม่เปิดเผยความลับหรือขอวิธีเลี่ยงความปลอดภัย

### R2 — Non-invasive behavior map / แผนที่พฤติกรรมแบบไม่แกะ

Using only owned devices, document pairing/wake/reset behavior, which original control commands which direction, button hold behavior, multi-shift behavior, response at gear limits, and whether multiple official controllers remain paired.

ใช้อุปกรณ์ที่เป็นเจ้าของเท่านั้น บันทึกการจับคู่/ปลุก/รีเซ็ต ตัวควบคุมเดิมสั่งทิศใด พฤติกรรมกดค้าง หลายเกียร์ ลิมิตเกียร์ และการจับคู่ตัวควบคุมเดิมหลายตัว

**Exit:** repeatable state diagram and no change to brake system. / **ผ่าน:** ได้แผนภาพสถานะที่ทำซ้ำได้และไม่เปลี่ยนระบบเบรก

### R3 — BLE and ANT observation / สังเกต BLE และ ANT

Inventory advertised services/profiles and observe traffic during app calibration, original paddle shifts, and bike-computer pairing. Determine whether traffic is telemetry/configuration or contains an actuation route. Respect applicable radio, software, and device-ownership rules; do not transmit beyond a controlled bench setup until safe and lawful.

สำรวจ service/profile และสังเกตทราฟฟิกระหว่างคาลิเบรตผ่านแอป กดชิฟเตอร์เดิม และจับคู่ไมล์ แยกว่าเป็นเทเลเมทรี/ตั้งค่าหรือมีช่องทางสั่งงาน ปฏิบัติตามกฎวิทยุ ซอฟต์แวร์ และสิทธิ์เจ้าของอุปกรณ์ ห้ามส่งสัญญาณนอกแท่นควบคุมจนกว่าจะปลอดภัยและถูกต้อง

**Exit:** service/profile table with read/write/notify behavior and raw evidence. Discovery alone does not pass Gate A. / **ผ่าน:** ตาราง service/profile พร้อมพฤติกรรม read/write/notify และข้อมูลดิบ การค้นพบเพียงอย่างเดียวยังไม่ผ่าน Gate A

### R4 — Donor shifter interface / อินเทอร์เฟซจากชิฟเตอร์ต้นทาง

If a donor is available and owner accepts warranty risk, photograph and inspect it before modification. Identify switch contacts with power removed; measure behavior; then use a current-limited, isolated temporary contact to emulate a press. Do not inject voltage into an unknown input. Preserve original battery protection, antenna clearance, and pairing.

หากมีชิฟเตอร์ต้นทางและเจ้าของยอมรับความเสี่ยงต่อประกัน ให้ถ่ายภาพและตรวจสอบก่อนแกะ ระบุหน้าสัมผัสเมื่อปิดไฟ วัดพฤติกรรม แล้วใช้หน้าสัมผัสชั่วคราวที่แยกวงจรและจำกัดกระแสเพื่อจำลองการกด ห้ามป้อนไฟเข้าอินพุตที่ไม่ทราบ รักษาวงจรป้องกันแบต ระยะเสาอากาศ และการจับคู่เดิม

**Exit:** external dry contact commands both directions repeatedly on the bench. If successful, select Path 1 and stop RF reverse engineering for V1. / **ผ่าน:** หน้าสัมผัสแห้งภายนอกสั่งได้ทั้งสองทิศซ้ำบนแท่น หากสำเร็จให้เลือกช่องทาง 1 และหยุดการวิเคราะห์ RF สำหรับ V1

### R5 — Custom compatible radio, only if needed / วิทยุที่เข้ากันได้เมื่อจำเป็นเท่านั้น

Proceed only if R1–R4 do not produce a viable path and the cost/time gate is explicitly approved. Characterize pairing, authentication, replay resistance, timing, coexistence, interference, and firmware sensitivity before any moving-bike test.

ทำต่อเมื่อ R1–R4 ไม่ได้ช่องทางที่ใช้ได้และอนุมัติต้นทุน/เวลาอย่างชัดเจน ต้องตรวจการจับคู่ การยืนยันตัวตน การป้องกัน replay เวลา การอยู่ร่วมกับสัญญาณอื่น สัญญาณรบกวน และความไวต่อเฟิร์มแวร์ก่อนทดสอบบนจักรยานที่เคลื่อนที่

**Exit:** Gate A evidence or a documented no-go. / **ผ่าน:** หลักฐาน Gate A หรือบันทึกว่าไม่ควรทำต่อ

## Stop conditions / เงื่อนไขหยุด

Stop the spike and reassess if success requires opening the Shimano hydraulic system, bypassing RD motor limits, uncontrolled RF transmission, defeating access controls, relying on cloud availability for manual shifting, or spending more than the agreed prototype cap.

หยุดและประเมินใหม่หากต้องเปิดระบบไฮดรอลิก Shimano ข้ามลิมิตมอเตอร์ตีนผี ส่ง RF แบบควบคุมไม่ได้ เลี่ยงการควบคุมการเข้าถึง พึ่งคลาวด์เพื่อเปลี่ยนเกียร์ด้วยมือ หรือใช้เงินเกินเพดานต้นแบบที่ตกลง

## Research deliverables / ผลลัพธ์งานวิจัย

- Interface decision record with evidence grade. / บันทึกการเลือกอินเทอร์เฟซพร้อมระดับหลักฐาน
- Pairing/state diagram. / แผนภาพการจับคู่และสถานะ
- Raw capture index without credentials or personal identifiers. / ดัชนีข้อมูลดิบที่ไม่มีรหัสหรือข้อมูลส่วนบุคคล
- Minimal bench schematic. / วงจรบนแท่นขั้นต่ำ
- Go/no-go recommendation for donor bridge, official control path, or custom RF. / ข้อเสนอ go/no-go สำหรับวงจรต้นทาง ช่องทางผู้ผลิต หรือ RF ที่ทำเอง

