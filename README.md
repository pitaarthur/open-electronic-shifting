# Low-Cost Add-On Electronic Bicycle Shifter

# ชุดเปลี่ยนเกียร์จักรยานไฟฟ้าแบบติดตั้งเพิ่มราคาประหยัด

Persistent engineering workspace for a personal gravel-bike prototype. The project preserves the existing Shimano 105 hydraulic brake levers and adds a simple electronic shift paddle for a WHEELTOP EDS GeX rear derailleur.

พื้นที่ทำงานวิศวกรรมแบบต่อเนื่องสำหรับต้นแบบจักรยานกราเวลส่วนบุคคล โครงการนี้คงมือเบรกไฮดรอลิก Shimano 105 เดิมไว้ และเพิ่มแป้นสั่งเปลี่ยนเกียร์ไฟฟ้าอย่างง่ายสำหรับตีนผี WHEELTOP EDS GeX

## Current status / สถานะปัจจุบัน

- Phase / ระยะ: **0 — GeX command-path feasibility / ตรวจสอบช่องทางสั่งงาน GeX**
- Overall / ภาพรวม: **Feasibility not yet proven / ยังไม่ยืนยันความเป็นไปได้**
- Safety boundary / ขอบเขตความปลอดภัย: **The electronics must never be part of the hydraulic braking load path. / ระบบอิเล็กทรอนิกส์ต้องไม่อยู่ในเส้นทางรับแรงของระบบเบรกไฮดรอลิก**
- Next gate / จุดตัดสินใจถัดไป: demonstrate a repeatable, authorized shift command on a bench without relying on ordinary ANT+ bike-computer pairing. / สาธิตคำสั่งเปลี่ยนเกียร์ที่ทำซ้ำได้บนแท่นทดสอบ โดยไม่ถือว่าการจับคู่ ANT+ กับไมล์จักรยานทั่วไปสามารถสั่งเปลี่ยนเกียร์ได้

## Working assumption / สมมติฐานที่ใช้ทำงาน

“SRAM-like single paddle” is provisionally interpreted as **one simple paddle per brake lever**, with one rear-shift direction assigned to each side. The first prototype may build only one identical paddle module, then duplicate it. A single total button using tap/hold/double-click is not the V1 default because it is less predictable while riding.

คำว่า “แป้นเดี่ยวแบบ SRAM” ถูกตีความชั่วคราวว่าเป็น **แป้นอย่างง่ายหนึ่งตัวต่อมือเบรกหนึ่งข้าง** โดยแต่ละข้างสั่งตีนผีคนละทิศทาง ต้นแบบแรกอาจสร้างโมดูลเพียงข้างเดียวแล้วจึงทำซ้ำอีกข้าง การใช้ปุ่มเดียวทั้งระบบแล้วแยกคำสั่งด้วยกดสั้น/กดค้าง/กดสองครั้งไม่ใช่ค่าเริ่มต้นของ V1 เพราะคาดเดาได้ยากกว่าขณะขี่

This is an explicit, reversible assumption; see the decision log. / นี่เป็นสมมติฐานที่ระบุชัดและเปลี่ยนกลับได้ โปรดดูบันทึกการตัดสินใจ

## Workspace map / แผนผังพื้นที่ทำงาน

| File | Purpose / วัตถุประสงค์ |
|---|---|
| [Project brief](docs/01-project-brief.md) | Scope, principles, success definition / ขอบเขต หลักการ และนิยามความสำเร็จ |
| [Requirements and acceptance](docs/02-requirements-and-acceptance.md) | Traceable V1 requirements and tests / ข้อกำหนดและการทดสอบ V1 ที่ตรวจสอบย้อนกลับได้ |
| [Architecture](docs/03-architecture.md) | System boundaries and candidate command paths / ขอบเขตระบบและช่องทางคำสั่งที่เป็นไปได้ |
| [GeX research spike](docs/04-gex-command-path-research.md) | Evidence-driven protocol/interface investigation / การตรวจสอบอินเทอร์เฟซด้วยหลักฐาน |
| [Mechanical paddle](docs/05-mechanical-paddle.md) | Mounting, ergonomics, and brake-clearance design / การยึดติด การยศาสตร์ และระยะห่างจากเบรก |
| [BOM and budget](docs/06-bom-and-budget.md) | Cost targets and purchasing gates / เป้าหมายต้นทุนและจุดอนุมัติการซื้อ |
| [Risks and unknowns](docs/07-risks-and-unknowns.md) | Ranked technical and safety risks / ความเสี่ยงทางเทคนิคและความปลอดภัยเรียงตามลำดับ |
| [Roadmap](docs/08-roadmap.md) | Phases, gates, and stop conditions / ระยะงาน จุดตัดสินใจ และเงื่อนไขหยุด |
| [Decision log](logs/decision-log.md) | Durable design decisions / บันทึกการตัดสินใจด้านการออกแบบ |
| [Experiment log](logs/experiment-log.md) | Append-only bench and ride evidence / หลักฐานจากแท่นและการขี่แบบเพิ่มต่อท้าย |
| [Experiment template](templates/experiment-template.md) | Repeatable test record / แบบบันทึกการทดสอบ |

## How to continue / วิธีทำงานต่อ

1. Update **Current status** and the decision log when a gate is passed. / อัปเดต **สถานะปัจจุบัน** และบันทึกการตัดสินใจเมื่อผ่านจุดตัดสินใจ
2. Copy the experiment template into the experiment log before each test. / คัดลอกแบบบันทึกการทดสอบลงในบันทึกการทดลองก่อนทดสอบแต่ละครั้ง
3. Record facts with source/date/device/firmware; label all inference and hypotheses. / บันทึกข้อเท็จจริงพร้อมแหล่งอ้างอิง วันที่ อุปกรณ์ และเฟิร์มแวร์ พร้อมติดป้ายข้ออนุมานและสมมติฐานทุกข้อ
4. Do not road-test until the brake-independence gate and bench-shift gate pass. / ห้ามทดสอบบนถนนจนกว่าจะผ่านเกณฑ์ความเป็นอิสระของเบรกและเกณฑ์เปลี่ยนเกียร์บนแท่น

## Confirmed public baseline / ข้อมูลสาธารณะที่ยืนยันแล้ว

Checked 2026-08-18 against the official [WHEELTOP GeX product page](https://wheeltop.com/products/wheel-top-eds-gex): GeX is described as wireless, 1x, 3–14-speed compatible, app-adjustable, and able to connect to bike computers over ANT+. The same page says a GeX rear derailleur currently cannot pair with MTB shifters or TX components. These statements do **not** document third-party shift actuation over ANT+ or BLE.

ตรวจสอบเมื่อ 2026-08-18 จาก [หน้าผลิตภัณฑ์ GeX ของ WHEELTOP](https://wheeltop.com/products/wheel-top-eds-gex): GeX ถูกอธิบายว่าเป็นระบบไร้สาย สำหรับ 1x รองรับ 3–14 สปีด ปรับตั้งผ่านแอป และเชื่อมต่อไมล์จักรยานผ่าน ANT+ หน้าเดียวกันระบุว่าปัจจุบันตีนผี GeX ยังจับคู่กับชิฟเตอร์ MTB หรือชิ้นส่วน TX ไม่ได้ ข้อความเหล่านี้ **ไม่ได้** ยืนยันว่าบุคคลที่สามสามารถสั่งเปลี่ยนเกียร์ผ่าน ANT+ หรือ BLE ได้

