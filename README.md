# การสร้างกราฟ SLA by Month

โปรเจกต์นี้ใช้ Python และไลบรารี Pandas, Matplotlib ในการสร้างกราฟแท่ง (bar chart) และกราฟเส้น (line chart) เพื่อติดตามสถานะของ SLA ในแต่ละเดือน โดยแสดงจำนวนของ IN_SLA และ OUT_SLA พร้อมทั้งแสดงเปอร์เซ็นต์ของ IN_SLA

## ไลบรารีที่ใช้

- **pandas**: สำหรับการจัดการและประมวลผลข้อมูลในรูปแบบตาราง
- **matplotlib**: สำหรับสร้างกราฟและการแสดงผลข้อมูล
- **numpy**: สำหรับการจัดการอาร์เรย์และการคำนวณเชิงตัวเลข

## ขั้นตอนการทำงานของโค้ด

1. **โหลดข้อมูลจากไฟล์ Excel**:
   - โค้ดจะโหลดข้อมูลจากไฟล์ Excel ชื่อ `Ticket_summary.xlsx` และเลือกเฉพาะคอลัมน์ `MONTH` และ `SLA` จากชีต `sheet1` เท่านั้น

2. **จัดเรียงข้อมูลเดือน**:
   - กำหนดลำดับของเดือนในรูปแบบที่ต้องการ เพื่อให้การแสดงผลเรียงตามลำดับเดือน ตั้งแต่ `January` ถึง `December`

3. **คำนวณจำนวน IN_SLA และ OUT_SLA**:
   - ใช้การ Group ข้อมูลตามเดือนและสถานะ SLA (IN_SLA และ OUT_SLA) เพื่อคำนวณจำนวนของแต่ละสถานะในแต่ละเดือน
   - คำนวณเปอร์เซ็นต์ของ IN_SLA สำหรับแต่ละเดือนโดยคำนวณจากสูตร:
     \[
     \text{\% IN_SLA} = \left( \frac{\text{IN_SLA}}{\text{IN_SLA} + \text{OUT_SLA}} \right) \times 100
     \]

4. **สร้างกราฟ**:
   - สร้างกราฟแท่ง (bar chart) เพื่อแสดงจำนวน IN_SLA และ OUT_SLA สำหรับแต่ละเดือน
   - สร้างกราฟเส้น (line chart) เพื่อแสดงเปอร์เซ็นต์ของ IN_SLA (`% IN_SLA`) ในแต่ละเดือน โดยใช้เส้นประและเครื่องหมาย `o` เพื่อแสดงจุด

5. **เพิ่มรายละเอียดให้กราฟ**:
   - แสดงจำนวนบนแท่งกราฟของ IN_SLA และ OUT_SLA (เฉพาะค่าที่ไม่ใช่ 0)
   - ตั้งค่าชื่อแกน x เป็น `Month` และแกน y ของกราฟแท่งเป็น `Count` 
   - เพิ่มแกน y ที่สองสำหรับกราฟเส้น เพื่อแสดงเปอร์เซ็นต์ IN_SLA โดยกำหนดรูปแบบการแสดงผลเป็นเปอร์เซ็นต์ (ใช้ `FuncFormatter`)
   - ตั้งค่าเลเจนด์ (legend) ไว้ด้านข้างของกราฟเพื่อแยกแยะค่า IN_SLA, OUT_SLA และ `% IN_SLA`

6. **แสดงกราฟ**:
   - ใช้ `plt.show()` เพื่อแสดงกราฟ

## คำสั่งการใช้งาน

1. ตรวจสอบให้แน่ใจว่าไฟล์ `Ticket_summary.xlsx` อยู่ในไดเรกทอรีที่กำหนด
2. รันโค้ดเพื่อสร้างกราฟโดยใช้ Python

## ผลลัพธ์ที่ได้

กราฟจะแสดงสถานะ SLA ของแต่ละเดือน โดย:
- กราฟแท่งจะแสดงจำนวนของ IN_SLA และ OUT_SLA
- กราฟเส้นจะแสดงเปอร์เซ็นต์ของ IN_SLA ต่อเดือน (ตั้งแต่ 0 ถึง 100%)
- เพิ่มเลเจนด์ด้านข้างของกราฟเพื่อแยกแยะ IN, OUT, และ % IN สะดวกต่อการอ่านข้อมูล

## หมายเหตุ

- คุณสามารถปรับแต่งสีของกราฟแท่งหรือเส้นเพิ่มเติมได้ตามต้องการ
- กราฟจะแสดงเฉพาะเดือนที่มีข้อมูล IN_SLA หรือ OUT_SLA เท่านั้น
