# Mechanical Paddle Design / การออกแบบแป้นเชิงกล

## Design intent / เป้าหมายการออกแบบ

Create a small, tactile paddle reachable from the normal hood grip without changing the Shimano brake mechanism. The mount must be reversible, stable, glove-friendly, and shaped so an electronics failure cannot block braking.

สร้างแป้นขนาดเล็กที่สัมผัสชัดและกดได้จากท่าจับฮูดปกติ โดยไม่เปลี่ยนกลไกเบรก Shimano จุดยึดต้องถอดกลับได้ มั่นคง ใช้กับถุงมือได้ และมีรูปทรงที่ความขัดข้องทางไฟฟ้าไม่สามารถขวางเบรก

## Capture before CAD / ข้อมูลที่ต้องเก็บก่อนทำ CAD

- Exact lever model number and left/right photos with a scale. / เลขรุ่นมือเบรกและภาพซ้าย/ขวาพร้อมสเกล
- Hood and drop hand positions, bare hand and normal gloves. / ท่าจับฮูดและดรอป ทั้งมือเปล่าและถุงมือปกติ
- Lever path from rest to full brake pull, including lateral flex. / เส้นทางก้านจากพักถึงดึงเต็ม รวมการยืดตัวด้านข้าง
- Free surfaces that are not the hose, bleed port, pivot, hood sealing lip, or manufacturer fasteners. / พื้นที่ว่างที่ไม่ใช่สายไฮดรอลิก ช่องไล่น้ำมัน จุดหมุน ขอบซีลฮูด หรือสกรูผู้ผลิต
- Clearance to bar tape, cables, bag, and hands while steering. / ระยะจากผ้าพันแฮนด์ สาย กระเป๋า และมือขณะเลี้ยว

## Preferred concept / แนวคิดที่ต้องการ

```text
finger → broad paddle → compliant stop → sealed momentary switch
                         │
reversible clamp/strap ──┴── lever body exterior
                         └── strain-relieved thin wire to bridge
```

The paddle should push against its own mount, never against a moving brake surface. Provide a mechanical stop so switch over-travel does not load the switch body. / แป้นต้องรับแรงกับจุดยึดของตัวเอง ไม่ใช่ผิวเบรกที่เคลื่อนที่ และมีตัวหยุดเชิงกลเพื่อไม่ให้ระยะกดเกินถ่ายแรงเข้าสู่ตัวสวิตช์

## Concept ladder / ลำดับต้นแบบ

1. Cardboard/foam ergonomic mockup, no electronics. / แบบจำลองกระดาษ/โฟม ไม่มีไฟฟ้า
2. Temporary strap-on printed mount with oversized clearance. / จุดยึดพิมพ์สามมิติแบบรัดชั่วคราวและเผื่อระยะมาก
3. Adjustable prototype with switch and external wire. / ต้นแบบปรับตำแหน่งได้พร้อมสวิตช์และสายภายนอก
4. Mirrored left/right mounts after command semantics are confirmed. / จุดยึดซ้าย/ขวาแบบกระจกหลังยืนยันความหมายคำสั่ง
5. Sealed, strain-relieved V1 enclosure. / กล่อง V1 กันละอองและลดแรงดึงสาย

## Geometry and feel targets / เป้าหมายรูปทรงและสัมผัส

These are starting ranges, not locked requirements. / เป็นช่วงเริ่มต้น ไม่ใช่ข้อกำหนดตายตัว

- Paddle face: large enough for winter/full-finger gloves, with rounded edges. / หน้าแป้นใหญ่พอสำหรับถุงมือเต็มนิ้ว ขอบมน
- Deliberate tactile click and short travel; no sharp edge against finger. / คลิกชัด ระยะสั้น ไม่มีขอบคมสัมผัสนิ้ว
- Guard or recess against accidental activation during hard braking or rough terrain. / มีขอบป้องกันหรือทำร่องเพื่อลดการกดโดยไม่ตั้งใจขณะเบรกแรงหรือทางขรุขระ
- Tool-accessible adjustment for reach and angle. / ปรับระยะและมุมด้วยเครื่องมือได้
- Visible witness marks to detect mount drift. / มีเครื่องหมายตรวจการเลื่อนของจุดยึด
- Left/right parts should share the switch, fasteners, wire, and as much geometry as practical. / ซ้าย/ขวาใช้สวิตช์ สกรู สาย และรูปทรงร่วมกันให้มากที่สุด

## Material and attachment notes / วัสดุและการยึด

- First mounts: tough printed polymer or simple formed bracket with a soft, non-slip liner. / จุดยึดแรกใช้โพลิเมอร์พิมพ์ที่เหนียวหรือขายึดดัดง่ายพร้อมแผ่นรองนุ่มกันลื่น
- Avoid brittle resin for load-bearing clips. / หลีกเลี่ยงเรซินเปราะในคลิปรับแรง
- Avoid adhesives as the only retention method near sweat, heat, or rain. / ไม่ใช้กาวเป็นวิธียึดเพียงอย่างเดียวใกล้เหงื่อ ความร้อน หรือฝน
- Do not exceed manufacturer torque or clamp onto flexible hood rubber alone. / ไม่เกินแรงขันผู้ผลิตและไม่ยึดกับยางฮูดที่ยืดหยุ่นเพียงอย่างเดียว
- Route wire with a service loop and strain relief; it must tear away or unplug without pulling the brake hose or lever. / เดินสายเผื่อระยะและลดแรงดึง สายต้องหลุด/ขาดได้โดยไม่ดึงสายเบรกหรือมือเบรก

## Mechanical failure checks / การตรวจความขัดข้องเชิงกล

- Paddle broken inward/outward. / แป้นหักเข้าด้านใน/ออกด้านนอก
- Clamp rotated toward lever. / แคลมป์หมุนเข้าหาก้าน
- Loose screw or detached enclosure. / สกรูคลายหรือกล่องหลุด
- Wire snagged by glove, bag, branch, or handlebar rotation. / สายเกี่ยวถุงมือ กระเป๋า กิ่งไม้ หรือจากการหมุนแฮนด์
- Switch stuck pressed. / สวิตช์ค้าง
- Hood rolled back for service and returned. / เปิดยางฮูดเพื่อซ่อมแล้วใส่กลับ

Every case must leave full brake access. / ทุกกรณีต้องยังเข้าถึงเบรกเต็มที่

