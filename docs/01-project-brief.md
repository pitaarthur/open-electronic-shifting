# Project Brief / บทสรุปโครงการ

## Problem / ปัญหา

Integrated electronic brake/shift levers are expensive. The user already owns functional Shimano 105 mechanical-shift levers with hydraulic brakes and wants to keep the braking system while replacing only the shift input with a low-cost electronic add-on.

มือเบรก/ชิฟเตอร์ไฟฟ้าแบบรวมมีราคาแพง ผู้ใช้มีมือเกียร์กล Shimano 105 ที่รวมเบรกไฮดรอลิกและยังใช้งานได้ดี จึงต้องการคงระบบเบรกไว้และเปลี่ยนเฉพาะอินพุตเปลี่ยนเกียร์เป็นอุปกรณ์ไฟฟ้าราคาประหยัดที่ติดตั้งเพิ่ม

## V1 product statement / คำอธิบายผลิตภัณฑ์ V1

An add-on, SRAM-like paddle fitted to the existing Shimano brake lever. It is a dumb momentary input for rear shifting on a 1x gravel bike. A separate command bridge converts the contact closure into a command accepted by the WHEELTOP EDS GeX rear derailleur. Loss of power, radio, firmware, or wiring removes shifting only; normal hydraulic braking remains available.

แป้นกดแบบ SRAM ที่ติดเพิ่มกับมือเบรก Shimano เดิม ทำหน้าที่เป็นอินพุตชั่วขณะอย่างง่ายสำหรับสั่งตีนผีของจักรยานกราเวล 1x กล่องแปลงคำสั่งแยกต่างหากจะแปลงการปิดหน้าสัมผัสเป็นคำสั่งที่ตีนผี WHEELTOP EDS GeX ยอมรับ หากไฟฟ้า วิทยุ เฟิร์มแวร์ หรือสายสัญญาณขัดข้อง จะเสียเฉพาะการเปลี่ยนเกียร์ ส่วนเบรกไฮดรอลิกยังทำงานตามปกติ

## User and use / ผู้ใช้และการใช้งาน

- One owner-builder; personal prototype only. / ผู้สร้างและผู้ใช้คนเดียว เป็นต้นแบบส่วนบุคคลเท่านั้น
- Gravel bicycle, 1x drivetrain, rear derailleur only. / จักรยานกราเวล ระบบ 1x ใช้เฉพาะตีนผี
- Lowest practical incremental cost is preferred over polish or universality. / ให้ความสำคัญกับต้นทุนเพิ่มที่ต่ำที่สุด มากกว่าความสวยงามหรือการรองรับแบบสากล
- Initial mechanical target: the exact Shimano 105 lever already on the bike. Record its model number before CAD. / เป้าหมายเชิงกลแรกคือมือเบรก Shimano 105 ตัวจริงบนจักรยาน ต้องบันทึกเลขรุ่นก่อนเริ่ม CAD

## Product principles / หลักการผลิตภัณฑ์

1. **Brake independence / เบรกเป็นอิสระ:** no electronic part carries brake load, opens the hydraulic circuit, limits lever travel, or changes the manufacturer clamp. / ชิ้นส่วนไฟฟ้าไม่รับแรงเบรก ไม่เปิดวงจรไฮดรอลิก ไม่จำกัดระยะก้านเบรก และไม่ดัดแปลงแคลมป์ของผู้ผลิต
2. **Dumb input / อินพุตอย่างง่าย:** the paddle behaves as a momentary contact; protocol, pairing, and state belong in a separate bridge. / แป้นทำหน้าที่เป็นหน้าสัมผัสชั่วขณะ โปรโตคอล การจับคู่ และสถานะอยู่ในกล่องแปลงแยก
3. **Evidence before architecture lock / ใช้หลักฐานก่อนล็อกสถาปัตยกรรม:** ANT+ or BLE discovery is not proof of actuation. / การค้นพบ ANT+ หรือ BLE ไม่ใช่หลักฐานว่าสั่งงานได้
4. **Reversible first / เริ่มจากสิ่งที่ย้อนกลับได้:** clamp or strap before drilling, donor interface before custom RF, bench before road. / ใช้แคลมป์หรือสายรัดก่อนเจาะ ใช้อินเทอร์เฟซเดิมก่อนทำ RF เอง และทดสอบบนแท่นก่อนถนน
5. **Independent future controllers / ตัวควบคุมอนาคตเป็นอิสระ:** a future bike computer may command the derailleur directly, but V1 manual shifting must not depend on it. / ในอนาคตไมล์จักรยานอาจสั่งตีนผีโดยตรง แต่การเปลี่ยนเกียร์ด้วยมือใน V1 ต้องไม่พึ่งไมล์

## In scope / อยู่ในขอบเขต

- Paddle geometry, mount, switch, wiring, enclosure, and strain relief. / รูปทรงแป้น จุดยึด สวิตช์ สาย กล่อง และตัวลดแรงดึง
- Discovering a safe GeX command path. / ค้นหาช่องทางสั่งงาน GeX ที่ปลอดภัย
- A minimal command bridge, preferably reusing official GeX shifter electronics if feasible. / กล่องแปลงคำสั่งขั้นต่ำ โดยให้ความสำคัญกับการใช้อิเล็กทรอนิกส์ชิฟเตอร์ GeX เดิมหากทำได้
- Bench and controlled-ride validation. / การทดสอบบนแท่นและการขี่ในพื้นที่ควบคุม

## Out of scope for V1 / นอกขอบเขต V1

- Front derailleur or 2x control. / สับจานหน้าหรือระบบ 2x
- Replacing, opening, or modifying the Shimano hydraulic brake circuit. / การเปลี่ยน เปิด หรือดัดแปลงวงจรเบรกไฮดรอลิก Shimano
- Universal fit across lever brands/models. / การติดตั้งแบบสากลกับมือเบรกหลายยี่ห้อหรือหลายรุ่น
- Voice and automatic shifting. / การสั่งด้วยเสียงและเปลี่ยนเกียร์อัตโนมัติ
- Production certification, public sale, or claims of roadworthiness. / การรับรองเพื่อผลิต การขายสู่สาธารณะ หรือการอ้างว่าพร้อมใช้บนถนน

## V1 success / ความสำเร็จของ V1

The custom add-on paddles reliably command both rear-shift directions on the GeX while the original Shimano braking action, travel, hose, and lever structure remain unaffected. Passing details are defined in the acceptance document.

แป้นที่ติดตั้งเพิ่มสามารถสั่งตีนผี GeX ได้อย่างน่าเชื่อถือทั้งสองทิศทาง โดยการทำงาน ระยะก้าน สายไฮดรอลิก และโครงสร้างมือเบรก Shimano เดิมไม่ได้รับผลกระทบ รายละเอียดเกณฑ์ผ่านอยู่ในเอกสารการยอมรับ

