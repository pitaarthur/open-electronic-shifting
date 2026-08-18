# System Architecture / สถาปัตยกรรมระบบ

## V1 boundary / ขอบเขต V1

```text
Left paddle ── momentary contact ──┐
                                   ├── Command bridge ── verified GeX RF ── GeX RD
Right paddle ─ momentary contact ──┘

Shimano brake lever ── hydraulic/mechanical path ── brake caliper
                      (no electronic dependency)
```

```text
แป้นซ้าย ── หน้าสัมผัสชั่วขณะ ──┐
                                 ├── กล่องแปลงคำสั่ง ── RF GeX ที่ยืนยันแล้ว ── ตีนผี GeX
แป้นขวา ─ หน้าสัมผัสชั่วขณะ ──┘

มือเบรก Shimano ── ทางกล/ไฮดรอลิก ── คาลิเปอร์เบรก
                  (ไม่พึ่งอิเล็กทรอนิกส์)
```

The preferred cheap V1 keeps the paddles electrically dumb and allows the bridge to live under the bar, stem, or elsewhere away from the brake mechanism. / V1 ราคาประหยัดที่ต้องการทำให้แป้นเป็นเพียงหน้าสัมผัส และวางกล่องแปลงไว้ใต้แฮนด์ ใต้สเต็ม หรือจุดอื่นที่ห่างจากกลไกเบรก

## Candidate command paths / ช่องทางคำสั่งที่เป็นไปได้

| Rank | Path / ช่องทาง | Why / เหตุผล | Gate / จุดตัดสินใจ |
|---:|---|---|---|
| 1 | **Reuse an original GeX shifter transmitter as the bridge**; connect external momentary contacts across its button inputs. / ใช้วงจรส่งสัญญาณของชิฟเตอร์ GeX เดิมเป็นกล่องแปลง แล้วต่อหน้าสัมผัสภายนอกขนานกับปุ่ม | Highest chance of protocol/pairing compatibility; little or no custom RF. May require donor teardown and void warranty. / มีโอกาสเข้ากันได้สูงสุด ใช้ RF เดิม แต่อาจต้องแกะอุปกรณ์และเสียประกัน | Inspect and bench-test donor without touching brakes. / ตรวจและทดสอบชิ้นส่วนเดิมบนแท่นโดยไม่แตะระบบเบรก |
| 2 | **Official supported accessory/API/protocol**, if WHEELTOP confirms one. / อุปกรณ์เสริม API หรือโปรโตคอลที่ผู้ผลิตรองรับ | Safest long-term interface and best documentation. None is currently confirmed. / ปลอดภัยระยะยาวและมีเอกสารดีที่สุด แต่ยังไม่ยืนยันว่ามี | Written documentation plus actual actuation test. / เอกสารเป็นลายลักษณ์อักษรและทดสอบสั่งงานจริง |
| 3 | **Compatible radio implementation** based on lawful observation of owned devices. / ทำวิทยุที่เข้ากันได้จากการสังเกตอุปกรณ์ที่เป็นเจ้าของอย่างถูกต้อง | Could remove donor dependency and enable bike-computer control. Encryption, rolling codes, RF compliance, firmware changes, and pairing may block it. / อาจลดการพึ่งชิ้นส่วนเดิมและรองรับไมล์ แต่การเข้ารหัส รหัสเปลี่ยน กฎ RF เฟิร์มแวร์ และการจับคู่อาจเป็นอุปสรรค | Authenticated, repeatable bench actuation with interference tests. / สั่งงานบนแท่นซ้ำได้และผ่านการทดสอบสัญญาณรบกวน |
| 4 | **BLE/ANT actuation**, only if a writable control service/profile is proven. / สั่งผ่าน BLE/ANT เมื่อพิสูจน์ว่ามี service/profile สำหรับควบคุม | Useful for future computer; public claims currently show connectivity, not actuation. / เหมาะกับไมล์ในอนาคต แต่ข้อมูลสาธารณะยืนยันเพียงการเชื่อมต่อ ไม่ใช่คำสั่ง | Write/capture causes intentional shift in both directions. / การเขียนหรือส่งแพ็กเก็ตทำให้เปลี่ยนเกียร์ทั้งสองทิศจริง |
| 5 | **Internal RD electrical injection.** / ป้อนสัญญาณไฟฟ้าภายในตีนผี | High risk to waterproofing, warranty, motor control, and derailleur limits. / เสี่ยงต่อการกันน้ำ ประกัน การควบคุมมอเตอร์ และลิมิต | Bench research only; not a preferred ride architecture. / วิจัยบนแท่นเท่านั้น ไม่ใช่สถาปัตยกรรมที่ต้องการใช้ขี่ |

## Baseline V1 architecture decision / การตัดสินใจสถาปัตยกรรม V1 เบื้องต้น

Proceed with Path 1 first if a donor GeX shifter is available. The custom part is then only a reversible paddle, sealed switch, wire, strain relief, and enclosure for retained original transmitter electronics. Do not buy RF development hardware until the donor feasibility check is complete.

เริ่มจากช่องทาง 1 หากมีชิฟเตอร์ GeX สำหรับเป็นชิ้นส่วนต้นทาง ชิ้นส่วนที่ทำเองจะเหลือเพียงแป้นถอดกลับได้ สวิตช์กันน้ำ สาย ตัวลดแรงดึง และกล่องสำหรับวงจรส่งเดิม ยังไม่ซื้ออุปกรณ์พัฒนา RF จนกว่าจะตรวจความเป็นไปได้ของชิ้นส่วนต้นทางเสร็จ

## Command semantics / ความหมายของคำสั่ง

Provisional V1 mapping / การแมปชั่วคราวสำหรับ V1:

- Left paddle: one step to an easier rear gear. / แป้นซ้าย: ไปเกียร์หลังที่เบาขึ้นหนึ่งขั้น
- Right paddle: one step to a harder rear gear. / แป้นขวา: ไปเกียร์หลังที่หนักขึ้นหนึ่งขั้น
- One press produces one command by default. Hold-to-multishift is disabled or deferred unless the retained original electronics impose it and testing shows it is predictable. / กดหนึ่งครั้งส่งหนึ่งคำสั่งเป็นค่าเริ่มต้น การกดค้างหลายเกียร์ปิดไว้หรือเลื่อนออกไป เว้นแต่วงจรเดิมบังคับและทดสอบแล้วคาดเดาได้

This mapping is reversible after ergonomic testing. / สามารถเปลี่ยนการแมปนี้ได้หลังทดสอบการยศาสตร์

## Future independent bike computer / ไมล์จักรยานอิสระในอนาคต

```text
Manual paddles ── Bridge A ───────┐
                                  ├── GeX RD
Bike computer ── Controller B ────┘
```

Controller B must not be in the manual path. “Independent” means either controller can be absent or powered off while the other continues within GeX pairing limitations. No shared gear-state synchronization is required. Whether GeX permits two command sources is an open research question, not an architecture assumption.

Controller B ต้องไม่อยู่ในทางเดินคำสั่งจากแป้น “อิสระ” หมายถึงถอดหรือปิดตัวใดตัวหนึ่งแล้วอีกตัวยังทำงานได้ภายใต้ข้อจำกัดการจับคู่ของ GeX ไม่ต้องซิงก์สถานะเกียร์ร่วมกัน การที่ GeX ยอมรับแหล่งคำสั่งสองแหล่งหรือไม่ยังเป็นคำถามวิจัย ไม่ใช่สมมติฐาน

