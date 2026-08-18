# Requirements and V1 Acceptance / ข้อกำหนดและเกณฑ์ยอมรับ V1

Status values / ค่าสถานะ: `Proposed / เสนอ`, `Verified / ยืนยัน`, `Blocked / ติดขัด`, `Deferred / เลื่อน`

## Requirements / ข้อกำหนด

| ID | Requirement / ข้อกำหนด | Priority / ลำดับ | Verification / วิธีตรวจสอบ | Status / สถานะ |
|---|---|---:|---|---|
| SAF-01 | Electronics shall not carry braking force or enter the hydraulic circuit. / อิเล็กทรอนิกส์ต้องไม่รับแรงเบรกหรือเข้าไปในวงจรไฮดรอลิก | Must / ต้องมี | Inspection + failure test / ตรวจสภาพและทดสอบความขัดข้อง | Proposed / เสนอ |
| SAF-02 | Full brake-lever travel and finger access shall remain unobstructed in every intended hand position. / ระยะก้านเบรกเต็มและการเข้าถึงด้วยนิ้วต้องไม่ถูกกีดขวางในทุกท่าจับที่ตั้งใจใช้ | Must / ต้องมี | Clearance check + stationary pull tests / ตรวจระยะและดึงเบรกขณะจอด | Proposed / เสนอ |
| SAF-03 | Loss of shifter power, broken/shorted wire, stuck switch, or bridge failure shall not remove braking. / ไฟดับ สายขาด/ลัดวงจร สวิตช์ค้าง หรือกล่องแปลงเสีย ต้องไม่ทำให้เบรกหาย | Must / ต้องมี | Fault injection while stationary / จำลองความขัดข้องขณะจอด | Proposed / เสนอ |
| FUN-01 | Manual controls shall issue both rear-shift directions for a 1x drivetrain. / ตัวควบคุมด้วยมือต้องสั่งตีนผีได้ทั้งสองทิศทางสำหรับระบบ 1x | Must / ต้องมี | Bench shift test / ทดสอบบนแท่น | Proposed / เสนอ |
| FUN-02 | The paddle shall be a simple momentary input with no required gear-state knowledge. / แป้นต้องเป็นอินพุตชั่วขณะอย่างง่ายและไม่ต้องรู้ตำแหน่งเกียร์ | Must / ต้องมี | Schematic and behavior inspection / ตรวจวงจรและพฤติกรรม | Proposed / เสนอ |
| FUN-03 | Manual shifting shall not depend on a bike computer, phone, cloud service, or voice service. / การเปลี่ยนเกียร์ด้วยมือต้องไม่พึ่งไมล์ โทรศัพท์ คลาวด์ หรือเสียง | Must / ต้องมี | Offline/power-off test / ทดสอบเมื่อออฟไลน์และปิดอุปกรณ์ | Proposed / เสนอ |
| INT-01 | The GeX command interface must be demonstrated, not inferred from ANT+/BLE pairing. / ต้องสาธิตอินเทอร์เฟซคำสั่ง GeX ไม่ใช่อนุมานจากการจับคู่ ANT+/BLE | Must / ต้องมี | Captured repeatable actuation evidence / หลักฐานสั่งงานซ้ำได้ | Proposed / เสนอ |
| MEC-01 | Mounting shall initially be reversible and shall not drill/cut the brake lever. / จุดยึดเริ่มต้นต้องถอดกลับได้และไม่เจาะ/ตัดมือเบรก | Must / ต้องมี | Inspection / ตรวจสภาพ | Proposed / เสนอ |
| MEC-02 | Paddle position shall be reachable from the normal hood grip with gloves. / ต้องกดแป้นได้จากท่าจับฮูดปกติขณะใส่ถุงมือ | Should / ควรมี | Ergonomic trial / ทดลองการยศาสตร์ | Proposed / เสนอ |
| MEC-03 | The mount shall not visibly drift or loosen during V1 endurance testing. / จุดยึดต้องไม่เลื่อนหรือคลายอย่างเห็นได้ชัดระหว่างทดสอบความทนทาน V1 | Must / ต้องมี | Mark-and-measure test / ทำเครื่องหมายและวัด | Proposed / เสนอ |
| ENV-01 | V1 shall tolerate sweat and light splash after bench validation; no immersion claim. / V1 ต้องทนเหงื่อและละอองน้ำหลังทดสอบบนแท่น แต่ไม่อ้างว่าจุ่มน้ำได้ | Should / ควรมี | Controlled splash test / ทดสอบละอองน้ำแบบควบคุม | Proposed / เสนอ |
| CST-01 | Target incremental paddle/interface BOM excludes the GeX RD and tools; purchases require a passed command-path gate. / เป้าหมาย BOM เพิ่มเติมไม่รวมตีนผี GeX และเครื่องมือ การซื้อต้องผ่านจุดตัดสินใจช่องทางคำสั่งก่อน | Must / ต้องมี | BOM review / ตรวจ BOM | Proposed / เสนอ |
| FUT-01 | A future bike-computer controller may independently command the RD without becoming a dependency of the manual shifter. / ไมล์จักรยานในอนาคตอาจสั่งตีนผีโดยอิสระโดยไม่เป็นสิ่งที่ชิฟเตอร์มือต้องพึ่ง | Deferred / เลื่อน | Phase 3 integration test / ทดสอบระยะ 3 | Deferred / เลื่อน |

## Acceptance gates / จุดผ่านการยอมรับ

### Gate A — GeX actuation feasibility / ความเป็นไปได้ในการสั่ง GeX

Pass only when all are true / ผ่านเมื่อครบทุกข้อ:

- A documented physical or radio path causes one intended RD movement repeatedly. / ช่องทางกายภาพหรือวิทยุที่บันทึกไว้ทำให้ตีนผีเคลื่อนตามตั้งใจซ้ำได้
- Both directions are demonstrated. / สาธิตได้ทั้งสองทิศทาง
- Ordinary bike-computer pairing is not presented as proof unless an actual shift command is captured and replayed successfully. / ไม่ใช้การจับคู่ไมล์ทั่วไปเป็นหลักฐาน เว้นแต่จับและทำซ้ำคำสั่งเปลี่ยนเกียร์สำเร็จจริง
- The method does not require modifying the Shimano brake hydraulics. / วิธีดังกล่าวไม่ต้องดัดแปลงระบบเบรกไฮดรอลิก Shimano
- Firmware version, device identifiers, equipment, steps, and results are logged. / บันทึกเวอร์ชันเฟิร์มแวร์ รหัสอุปกรณ์ เครื่องมือ ขั้นตอน และผลแล้ว

### Gate B — Brake independence / ความเป็นอิสระของเบรก

Perform stationary first; professional inspection is recommended before riding. / ทดสอบขณะจอดก่อน และแนะนำให้ช่างผู้เชี่ยวชาญตรวจสอบก่อนขี่

- No mount, wire, paddle, or enclosure contacts the lever through its full brake stroke. / จุดยึด สาย แป้น และกล่องไม่สัมผัสหรือขวางก้านตลอดระยะเบรก
- With all electronics removed or failed, braking action remains mechanically unchanged. / เมื่อถอดหรือทำให้อิเล็กทรอนิกส์เสีย การทำงานเชิงกลของเบรกยังเหมือนเดิม
- Fifty firm stationary brake pulls produce no mount movement, cable snag, cracking, or lever obstruction. / ดึงเบรกแรงขณะจอด 50 ครั้งแล้วจุดยึดไม่เลื่อน สายไม่เกี่ยว ไม่มีรอยแตก และไม่ขวางก้าน
- Hood cover, hose, bleed port, pivot, manufacturer fasteners, and lever body are not damaged or altered. / ยางฮูด สายไฮดรอลิก ช่องไล่น้ำมัน จุดหมุน สกรูผู้ผลิต และตัวมือเบรกไม่เสียหายหรือถูกดัดแปลง

### Gate C — Bench shifting / การเปลี่ยนเกียร์บนแท่น

With the bike securely supported and wheel/drivetrain clear / ยึดจักรยานมั่นคงและเว้นระยะล้อ/ชุดขับ:

- 200 commanded single shifts total, alternating directions where practical. / สั่งเปลี่ยนเกียร์เดี่ยวรวม 200 ครั้ง สลับทิศทางเมื่อทำได้
- At least 99% of commands produce the intended response; zero unintended shifts without a paddle press. / คำสั่งอย่างน้อย 99% ให้ผลตามตั้งใจ และไม่มีการเปลี่ยนเกียร์เองเมื่อไม่ได้กด
- Power-cycle and wake-from-sleep behavior are documented and repeatable. / พฤติกรรมหลังปิดเปิดและปลุกจากพักถูกบันทึกและทำซ้ำได้
- Stuck input, bounce, rapid presses, low battery, and disconnected-wire behavior are characterized. / ระบุพฤติกรรมเมื่ออินพุตค้าง หน้าสัมผัสเด้ง กดเร็ว แบตต่ำ และสายหลุด
- 1,000 dry paddle actuations cause no breakage or visible mount drift. / กดแป้นแบบแห้ง 1,000 ครั้งแล้วไม่แตกและจุดยึดไม่เลื่อนอย่างเห็นได้ชัด

### Gate D — Controlled ride / การขี่แบบควบคุม

Only after Gates A–C pass / ทำหลังผ่าน A–C เท่านั้น:

- Begin in a traffic-free, low-speed area with a conventional stopping plan. / เริ่มในพื้นที่ไม่มีรถ ความเร็วต่ำ และมีแผนหยุดรถตามปกติ
- Complete 50 deliberate shifts with no accidental actuation and at least 98% intended response. / สั่งเปลี่ยนเกียร์โดยตั้งใจ 50 ครั้ง ไม่มีการกดโดยไม่ตั้งใจ และตอบสนองตามตั้งใจอย่างน้อย 98%
- Confirm braking from hoods and drops remains unobstructed with bare hands and intended gloves. / ยืนยันว่าเบรกจากท่าจับฮูดและดรอปไม่ถูกขวาง ทั้งมือเปล่าและถุงมือที่จะใช้
- Stop immediately for mount movement, cracking, snagging, brake feel change, repeated unintended shifts, or intermittent control. / หยุดทันทีหากจุดยึดเลื่อน แตก สายเกี่ยว ความรู้สึกเบรกเปลี่ยน เกียร์เปลี่ยนเองซ้ำ หรือควบคุมติดๆ ดับๆ

## Definition of V1 done / นิยามว่า V1 เสร็จ

Gates A–D pass, evidence is logged, current CAD/schematic/BOM are saved, and braking still works normally with the entire electronic shifter disabled. This is prototype acceptance, not regulatory certification.

ผ่านจุด A–D มีหลักฐานครบ บันทึก CAD/วงจร/BOM รุ่นปัจจุบัน และเบรกยังทำงานปกติเมื่อปิดชิฟเตอร์ไฟฟ้าทั้งหมด นี่คือการยอมรับต้นแบบ ไม่ใช่การรับรองตามกฎหมาย

