# Data Analytics

### การวิเคราะห์ปัจจัยที่ส่งผลต่อยอดขายรวม (Total Sales) ของ AdidasStore เพื่อวางแผนกลยุทธ์การเพิ่มยอดขาย
โปรเจกต์นี้มุ่งเน้นการวิเคราะห์ปัจจัยสำคัญที่มีอิทธิพลต่อยอดขายรวม (Total Sales) ของ Adidas Store เช่น ราคา จำนวนขาย และช่องทางการจำหน่าย โดยใช้การวิเคราะห์ข้อมูลเชิงสถิติและโมเดลเชิงพยากรณ์ เพื่อทำความเข้าใจความสัมพันธ์ของปัจจัยต่าง ๆ กับยอดขาย ผลการวิเคราะห์จะช่วยระบุปัจจัยที่ส่งผลต่อยอดขายมากที่สุด และนำไปใช้ในการวางแผนกลยุทธ์การตั้งราคา การบริหารช่องทางการขาย และการเพิ่มยอดขายอย่างมีประสิทธิภาพในอนาคต

---

## 📌 Data Source

- **Dataset:** Adidas Sales Dataset
- **Platform:** Kaggle
- **Link:** https://www.kaggle.com/datasets/heemalichaudhari/adidas-sales-dataset
- **Total Rows:** 9,649 records
- **Total Columns:** 13 features

---

## 🧾 Data Dictionary

| Column Name | Column Thai Name | Type | Description  | Example |
|----------|----------|----------|----------|----------|
|Retailer |ชื่อผู้ค้าปลีก/ร้านค้า|Categorical|ชื่อร้านค้าหรือผู้จัดจำหน่ายสินค้า|Foot Locker,Walmart,West Gear|
|Retailer ID|รหัสผู้ค้าปลีก|Categorical|รหัสประจำตัวของผู้ค้าปลีกแต่ละราย|1185732|
|Invoice Date|วันที่ออกใบแจ้งหนี้|DateTime|วันที่และเวลาที่บันทึกรายการขาย|01-01-20 00:00|
|Region|ภูมิภาค|Categorical|ภูมิภาคที่เกิดการขาย|Northeast,South,West,Midwest|
|State|รัฐ/จังหวัด|Categorical|รัฐหรือจังหวัดที่เกิดการขาย|New York,Texas|
|City|เมือง|Categorical|เมืองที่เกิดการขาย|New York,Houston|
|Product|ประเภทสินค้า|Categorical|หมวดหมู่ของสินค้าที่ขาย|Men's Street Footwear|
|Price per Unit|ราคาต่อหน่วย|Decimal|ราคาขายต่อหนึ่งหน่วยสินค้า|[0, ∞)|
|Units Sold|จำนวนที่ขาย|Integer|จำนวนหน่วยสินค้าที่ขายได้|[0, ∞)|
|Total Sales|ยอดขายรวม|Decimal|รายได้รวมจากการขายสินค้า|[0, ∞)|
|Operating Profit|กำไร|Decimal|กำไรจากการขายหลังหักต้นทุน|[0, ∞)|
|Operating Margin|สัดส่วนกำไร|Decimal|สัดส่วนกำไรต่อยอดขาย|[0, 1]|
|Sales Method|ช่องทางการขาย|Categorical|ช่องทางที่ใช้ในการขายสินค้า|In-store,Outlet,Online|



---

## 🎯 Objectives (จุดประสงค์ของโครงการ)

1. เพื่อทำความเข้าใจปัจจัยที่ส่งผลต่อยอดขายรวม (Total Sales Drivers)
2. เพื่อระบุแนวโน้มเชิงธุรกิจและ Insight สำคัญ

---

## 🔎 EDA (Exploratory Data Analysis) – แนวทางการสำรวจข้อมูล

#### 🧪 Statistical Analysis (การวิเคราะห์เชิงสถิติ)
•	ตั้งกรอบสมมติฐาน H₀/H₁:

    o	H₀: การขาย In-store, Online, Outlet ให้ยอดขายรวมเท่ากันโดยไม่มีความแตกต่าง
    o	H₁: มีอย่างน้อยหนึ่งช่องทางขาย มีผลต่อ Total Sales 
    
•	ใช้ **One-way ANOVA** เพื่อทดสอบความแตกต่างของค่าเฉลี่ย Total Sales ระหว่างช่องทางการขาย  
•	กำหนดระดับนัยสำคัญ **α = 0.05**
•	เครื่องมือที่ใช้: **Microsoft Excel**
<br>
<img width="281" height="65" alt="one way anova" src="https://github.com/user-attachments/assets/ed191356-bade-4e27-925c-516e728fa80e" />
<br>
## ✅ Statistical Conclusion (ข้อสรุปเชิงสถิติ)

จากการทดสอบ One-way ANOVA ที่ระดับนัยสำคัญ 0.05  
พบว่า **p-value มีค่าใกล้เคียง 0** ซึ่ง **น้อยกว่า 0.05 อย่างมีนัยสำคัญ**  

ดังนั้นจึง **ปฏิเสธสมมติฐาน H₀**  
สรุปได้ว่า **มีอย่างน้อยหนึ่งช่องทางขาย มีผลต่อ Total Sales อย่างมีนัยสำคัญทางสถิติ**

---

## ⭐ Major Findings and Insights (ผลการค้นพบหลัก)


### 1) แนวโน้มยอดขายและกำไร (2020 → 2021)
- Sales และ Profit มีแนวโน้มเพิ่มขึ้นอย่างชัดเจนตั้งแต่ปี 2020 → 2021
- เส้นแนวโน้ม (Trend line) ของทั้งสองตัวชี้วัดเป็น “ขาขึ้น” สะท้อนการเติบโตของธุรกิจโดยรวม
--
<img width="553" height="347" alt="Profit and Sales by month of date" src="https://github.com/user-attachments/assets/5c496673-9c57-4a7d-9206-86c57f3eb156" />



### 2) Correlation Heatmap
- Units Sold เป็นปัจจัยหลักที่ขับเคลื่อน Total Sales และ Operating Profit
- แสดงให้เห็นว่า ปริมาณการขาย เป็นตัวแปรสำคัญที่สุดในการเพิ่มทั้งยอดขายรวมและกำไรจากการดำเนินงาน
--
<img width="398" height="317" alt="Corr Heatmap" src="https://github.com/user-attachments/assets/0b37e854-8196-431c-9d0a-ec52d26e98c8" />


### 3) ช่องทาง In-store ยังสร้างยอดขายสูงสุด
- ช่องทาง **In-store** ยังคงสร้างยอดขายรวมสูงสุด
- สะท้อนว่าร้านหน้าร้านยังเป็นช่องทางหลักในการสร้างรายได้ของ Adidas
- แม้พฤติกรรมผู้บริโภคจะเปลี่ยนไปสู่ดิจิทัลมากขึ้น แต่ยอดขาย Online ยังตามหลังช่องทางออฟไลน์
--
<img width="545" height="343" alt="Sale Medthod" src="https://github.com/user-attachments/assets/438889c0-9a4f-4722-92d3-b742be1505c0" />


### 4) ภาพรวมด้านสินค้า (Product Mix)
- **Men’s Street Footwear** ทำยอดขายสูงสุด → สะท้อนความนิยมรองเท้าแนว Lifestyle/Street ในกลุ่มลูกค้าชาย
- **Women’s Apparel** ยังมีศักยภาพ → กลุ่มลูกค้าผู้หญิงมี Demand สูงในสินค้า Apparel มากกว่ารองเท้ากีฬา
- **Women’s Athletic Footwear** มียอดขายต่ำสุด → อาจเกิดจาก Positioning/ความต้องการตลาดไม่ตรงกลุ่ม
<img width="553" height="343" alt="Product and Sales" src="https://github.com/user-attachments/assets/735b89bf-0a7e-4a4c-8e70-363805910513" />


### 5) Units Sold เป็นตัวขับเคลื่อนยอดขายหลัก (Sales Driver)
- เมื่อ **Units Sold เพิ่มขึ้น → Total Sales เพิ่มขึ้นตามอย่างชัดเจน**
- แสดงให้เห็นว่า Units Sold เป็นตัวขับเคลื่อนหลักของ Total Sales
<img width="377" height="344" alt="Correlation Sales and unit sold" src="https://github.com/user-attachments/assets/7b4cd31c-6ee7-4f5b-b377-7677f60b296e" />

### 6)	Foot Locker และ West Gear เป็น Retailer หลักที่สร้างยอดขายสูงสุด 
-	แสดงให้เห็นว่า แสดงว่า Retailer กลุ่มนี้ มีฐานลูกค้าใหญ่ และเชี่ยวชาญสินค้า Street / Athletic
-	Men’s Street Footwear เป็น “สินค้าทำเงินหลัก” ทุกช่องทาง เป็น Core Product ที่ขับเคลื่อน Total Sales
-	ช่องทาง Online อย่าง Amazon และ Walmart มียอดขายต่ำกว่า
-	แสดงให้เห็นว่า Retailer และ Product Category เป็นปัจจัยสำคัญที่ส่งผลต่อ Total Sales
<img width="556" height="345" alt="512Total Sales by Retailer and Product Category" src="https://github.com/user-attachments/assets/b64ecf75-2c1e-4bb3-a70a-de8725cf0430" />

### 7)  West เป็น Region ที่สร้างยอดขายสูงสุดอย่างชัดเจน 
-	แสดงว่า ตลาดมีขนาดใหญ่, Demand สูง
-	Northeast อยู่ในอันดับ 2 และเป็น Region ที่แข็งแรง ซึ่งมีศักยภาพในการ ขยายยอดขายเพิ่มเติม หากลงทุนเพิ่ม
-	Midwest เป็น Region ที่ยอดขายต่ำสุด เป็น Region ที่ควรเร่งปรับกลยุทธ์ 
<img width="521" height="346" alt="512Total Sales by Region" src="https://github.com/user-attachments/assets/833c7d9a-c7e9-460b-a817-a849f1021926" />

### 8) Region West ทำยอดขายสูงสุดเกือบทุก Product Category 
-	แสดงให้เห็นว่า มี Demand สูง,Product Mix แข็งแรงหลายหมวด
-	Men’s Street Footwear คือสินค้าทำเงินอันดับ 1 ทุก Region เป็นสินค้า Mass + Lifestyle,ตอบโจทย์ลูกค้าหลากหลายกลุ่ม
-	South มีขายในหมวดหมู่ Women’s Apparel สูงสุด ต่างจาก Region อื่นที่ Men’s Street Footwear นำ
<img width="554" height="343" alt="512Total Sales by Product Category and Region" src="https://github.com/user-attachments/assets/e90c79b4-245e-4cfc-b20f-bfadd7d03c49" />

### 9)	Region West มียอดขายสูงสุด แต่มีความผันผวนสูงเช่นกัน 
-	จุดสูงสุดอยู่ช่วง May–July มีเทรนลงชัดเจนใน August–October ก่อนฟื้นตัวปลายปี มีความเสี่ยงจาก Seasonality
-	Northeast ยอดขายสม่ำเสมอและเติบโตปลายปี แนวโน้มเพิ่มขึ้นชัดใน November–December ความผันผวนน้อยกว่า West เป็น Region ที่เสถียรและขยายได้ในระยะยาว
-	 ทุก Region มีรูปแบบ Seasonality  ยอดขายโดยรวมสูงช่วง กลาง–ปลายปี
<img width="556" height="353" alt="512Monthly Total Sales Trend by Region" src="https://github.com/user-attachments/assets/3735e9ad-c2a7-4381-bb36-276cead3c4a6" />

### 10) South มี Operating Margin สูงที่สุด
-	 แม้ยอดขายอาจไม่สูงสุด แต่ทำกำไรได้ดี การควบคุมต้นทุนมีประสิทธิภาพ เป็น Region ที่ มีคุณภาพของรายได้ (Profitability) สูง
-	West ยอดขายสูง แต่ Margin ไม่ได้สูงที่สุด มีบางจุดที่ Outliers ต่ำ แสดงให้เห็นว่า อาจมีการแข่งขันด้านราคา หรือมีต้นทุนการขายสูง ดังนั้น West เป็น Volume-driven Region มากกว่า Margin-driven
<img width="567" height="455" alt="Profit   Margin ตาม Region" src="https://github.com/user-attachments/assets/b3e2b2a6-fe7f-490f-9569-726d98f7990c" />

### 11)	ทุก Region มีแนวโน้มฟื้นตัวชัดเจนในปี 2021
-	ยอดขายของทุก Region ฟื้นตัวชัดเจน และมีลักษณะ Seasonality โดยยอดขายสูงช่วงกลางถึงปลายปี
<img width="846" height="430" alt="Trend ของ Total Sales ตามเวลา (แยก Region)" src="https://github.com/user-attachments/assets/780df98f-3bdc-412d-b735-b1f8a263cb12" />



---

## 🔍 Findings and Insights 

1. **ช่องทางการขายมีผลต่อ Total Sales อย่างมีนัยสำคัญ**  
   •	ผลวิเคราะห์ทางสถติ แสดงให้เห็นอย่างชัดเจนว่า ช่องทางการขาย (In-store, Online, Outlet) ส่งผลต่อค่าเฉลี่ย Total Sales แตกต่างกัน แสดงว่าการจัดสรรทรัพยากรและกลยุทธ์ในแต่ละช่องทางไม่ควรเหมือนกันทั้งหมด

2. **In-store เป็น Revenue Driver หลัก**  
   •	แม้พฤติกรรมผู้บริโภคจะเปลี่ยนไปสู่ Online มากขึ้น แต่ In-store ยังสร้างยอดขายรวมสูงสุด แสดงถึงความสำคัญของประสบการณ์หน้าร้าน (Physical Experience) เช่น การลองสินค้า การให้คำแนะนำจากพนักงาน

3. **Online Channel ยังเติบโตได้อีก**  
   •	Online Sales ยังตามหลัง In-store ช่องว่างนี้สะท้อน Opportunity ในการเพิ่มยอดขายผ่าน Digital Marketing, และ Promotion เฉพาะออนไลน์

4. **Product Mix มีผลต่อยอดขายรวม**  
   •	Men’s Street Footwear ทำยอดขายสูงสุด → ตลาด Lifestyle / Streetwear ยังแข็งแรง
   •	Women’s Apparel แสดงศักยภาพสูง → ลูกค้าผู้หญิงให้ความสำคัญกับแฟชั่นและการใช้งานในชีวิตประจำวัน
   •	Women’s Athletic Footwear มียอดขายต่ำ → อาจเกิดจากการวางตำแหน่งสินค้า (Positioning) หรือไม่ตรงกับความต้องการตลาด


5. **Units Sold เป็นตัวขับเคลื่อนยอดขายหลัก**  
   •	Units Sold เป็นตัวขับเคลื่อนหลักของ Total Sales ตัวแปรที่เกี่ยวข้องกับ Units Sold มีอิทธิพลสูงที่สุด แสดงว่าปริมาณการขายคือปัจจัยสำคัญที่สุดในการสร้างรายได้
   •	ราคา × ปริมาณขาย ต้องพิจารณาร่วมกัน Interaction ระหว่าง Price per Unit และ Units Sold มีผลชัด แสดงว่ากลยุทธ์ราคาและปริมาณต้องออกแบบควบคู่กัน

6.**Retailer Strategy สำคัญไม่แพ้ Channel Strategy**
   • Foot Locker และ West Gear เป็น Retailer หลักที่สร้างยอดขายสูงสุด
   • Retailer เหล่านี้มีความเชี่ยวชาญด้าน Street / Athletic และเข้าถึงลูกค้ากลุ่ม Mass ได้ดี

7.**Region West = High Volume แต่ไม่ใช่ High Margin**
   • West เป็น Region ที่มียอดขายสูงสุดเกือบทุก Product Category แต่ Operating Margin ไม่ได้สูงสุด และมี Outliers ต่ำ 
   • ตรงข้ามกับ South ที่ยอดขายไม่สูงสุด แต่ ทำกำไรได้ดีที่สุด

8.**Seasonality เป็นความเสี่ยงที่ต้องบริหาร**
   • ทุก Region มียอดขายสูงช่วง กลาง–ปลายปี
   • Insight นี้สำคัญต่อการวาง Inventory & Promotion Calendar

---

## 📌 Recommendations (ข้อเสนอแนะเชิงธุรกิจ)

1. **เพิ่มสต็อกและกิจกรรมการขายในช่องทาง In-store**  
   เพราะมีผลบวกต่อยอดขายรวมสูงที่สุด และควรใช้ In-store เป็น “Experience Hub” มากกว่าจุดขายเพียงอย่างเดียว

2. **เพิ่มแรงกระตุ้นการขายในช่องทาง Online**  
   ทำโปรโมชัน/แคมเปญ เช่น Flash Sale, Free Shipping  
   และเพิ่มบริการออนไลน์ เช่น “Size Recommendation” เพื่อช่วยตัดสินใจซื้อ

3. **เน้นกลยุทธ์เพิ่ม Units Sold**  
   ใช้ Bundle Promotion (รองเท้า + เสื้อผ้า), Quantity Discount (โดยเฉพาะออนไลน์), และ Loyalty Program เพื่อกระตุ้นการซื้อซ้ำ

4. **ส่งเสริมการขายสินค้า Women’s Athletic Footwear**  
   ปรับกลยุทธ์ด้านราคา ทำโปรโมชั่นเฉพาะกลุ่ม เพิ่มการมองเห็นบนช่องทางออนไลน์




