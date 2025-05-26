# EE495 Selected Topic in Electrical Engineering 

ที่มาและความสำคัญ 

อากาศยานไร้คนขับขนาดเล็ก (Drone) เป็นอากาศยานที่ควบคุมจากระยะไกล ใช้การควบคุมอัตโนมัติซึ่งมีอยู่ด้วยกัน 2 ลักษณะ คือ การควบคุมอัตโนมัติจากระยะไกล และการควบคุมแบบอัตโนมัติโดยใช้ระบบการบินด้วยตนเอง โดย Drone จะใช้ Microcontroller ในการควบคุมการบิน โดยในรายวิชานี้จะได้เจาะลึกลงไปถึงการวิเคราะห์โครงสร้างของ Drone, วิธีการเลือกบอร์ด Microcontroller ที่เหมาะสม, ศึกษาระบบการทำงานและระบบควบคุม, ออกแบบ PCB, การประกอบอุปกรณ์, การเขียนโปรแกรมควบคุมด้วย Arduino IDE, การสื่อสารระหว่างอุปกรณ์, และการทดสอบการบิน

## ชิ้นส่วนและอุปกรณ์
| ประเภทอุปกรณ์ | รุ่น | น้ำหนัก (กรัม) |
|---|---|---|
| Drone Frame | FPV F330 | 143 |
| Electronic Speed Controller | 40A | 30 |
| Blushless DC Motor | A2212 1400KV | 216 |
| Prop | 8045 CW, CCW | 20 |
| Battery | LiPo 3s 2800mAh | 207 |
| Receiver | FS-iA6B | 18 |
| Microcontroller | STM32F108C8T6 | 10 |
| Gyroscope | MPU-6050 | 5 |
| Ultrasonic Sensor | HC-SR04 | 10 |
| Bluetooth | HC-05 | 5 |
| น้ำหนักรวม |  | 664 |

## การเลือกบอร์ด Microcontroller
![Alt text](https://miro.medium.com/v2/resize:fit:720/format:webp/1*lH13bx-OzuJKV9nAXCYbXw.png)

เพื่อประสิทธิภาพการบินที่สูงขึ้น จึงเลือกใช้ STM32F103C8T6
![Alt text](https://os.mbed.com/media/uploads/hudakz/stm32f103c8t6_pinout_voltage01.png)

## การใช้งาน STM32F103C8T6 กับโปรแกรม Arduino IDE

1. เพิ่มบอร์ด STM32 ลงใน Arduino IDE
  
  ![Screenshot 2025-05-26 222618](https://github.com/user-attachments/assets/bbcbdefb-4a36-4d3a-a4e9-fc942d580d7a)
  
2. ติดตั้งไดร์เวอร์ ST-Link
  
  ![image](https://github.com/user-attachments/assets/b30d192a-a185-4bb8-b918-9a30d3efcdad)

โดยสามารถดูวิธีการลงโปรแกรมได้ตามวิดีโอนี้ https://www.youtube.com/watch?v=cnv8bpl67uw

3. เชื่อมต่อ ST-Link กับ STM32F103C8T6

  ![Alt text](https://lungmaker.com/wp-content/uploads/2021/01/1-2.png)

  * กดปุ่ม "Target" เพื่อเชื่อมข้อมูลระหว่าง ST-Link กับ STM32F103C8T6

    ![image](https://github.com/user-attachments/assets/d6b33783-db71-44cb-97b8-5782b2205e3b)

    ✅ ถ้า STM32F103C8T6 ตัวที่ใช้ มีตัวเลขขึ้นตามตัวอย่าง แสดงว่าสามารถใช้งานได้ปกติ แต่ถ้าไม่มีต้องทำการ Bootloader DFU ใหม่ 
    
    📌 Bootloader DFU (Device Firmware Upgrade) โดยเป็นมาตรฐาน USB สำหรับการอัปเดตเฟิร์มแวร์บนอุปกรณ์
    
    📌 STM32 บางรุ่น ไม่มี DFU Bootloader มาจากโรงงานจึงต้องแฟลชเข้าไปเองครั้งแรก
    
    📌 ตัวอย่างไฟล์ Bootloader ที่รองรับ DFU (.bin) 

![Screenshot 2025-05-26 230505](https://github.com/user-attachments/assets/28eec64b-24da-48ef-babd-ed3b7c222c1e)

 4. เปิดโปรแกรม Arduino IDE ทำการเลือกบอร์ด "Generic STM32F103C series"

![Screenshot 2025-05-26 234413](https://github.com/user-attachments/assets/b1239923-63b4-4e6c-bb9a-41314da2fa23)

 5. เลือกวิธีการอัพโหลดข้อมูลเป็น "STLink"

![image](https://github.com/user-attachments/assets/405b637d-67ca-443d-a205-4aa41a38ed65)

✅ สามารถใช้งาน STM32F103C8T6 ได้ปกติ

## Printed Circuit Board (PCB)

1. ออกแบบวงจรด้วยเว็บไซต์ https://easyeda.com/
   
![Schematic_Newdrone_2025-05-27](https://github.com/user-attachments/assets/d910a225-131a-4599-965c-16fbc15cc04c)

*โดยออกแบบตามอุปกรณ์ที่ได้เลือกและอ้างอิง Schematic บางส่วนจากโปรเจค YMFC-32 http://brokking.net/*

2. แปลงเป็นแผ่นลายวงจร

![image](https://github.com/user-attachments/assets/8d75e93a-a12c-4ba9-92cc-8a222a5a6a4b)

![image](https://github.com/user-attachments/assets/d066224d-d6dd-4f7a-878b-c1899750032e)

3. ผลิตแผ่น PCB
* ดาวน์โหลดไฟล์ PCB เป็นไฟล์ "PCB Fabrication File (Gerber)" และสั่งผลิตด้วย https://jlcpcb.com/

## ประกอบอุปกรณ์

* รูปอุปกรณ์ที่ประกอบแล้ว

* รูปอุปกรณ์ที่ประกอบแล้วทั้งลำ

## ศึกษาการทำงานของ STM32F103C8T6, Sensor และการสื่อสารระหว่างอุปกรณ์
* STM32F103C8T6 ใช้ ST-Link ในการอัพโหลดข้อมูล

* รูปต่อสาย stlink

* STM32F103C8T6 ใช้ Micro-USB, USB-C (แล้วแต่ชนิดของบอร์ด) ในการแสดงผลข้อมูล

* รูปต่อสาย usb

* โดยสามารถแสดงผลบน Serial Monitor ในโปรแกรม Arduino IDE

* รูปต่อ port maple

| อุปกรณ์  | การเชื่อมต่อ 1 | การเชื่อมต่อ 2 | หมายเหตุ |
|---|---|---|---|
| MPU-6050 | PB10 | PB11 | SCL, SDA |
| HC-05 | PA9 | PA10 | TX,RX |
| HC-SR04 | PB0 | PB1 | PWM |

📌 สามารถใช้ "#define TRIG_PIN" และ "#define ECHO_PIN" กับ pin ที่ยังว่างบน STM32F103C8T6 ได้ตามต้องการ

❗ยกเว้น pin ที่กำลังใช้งานกับอุปกรณ์อื่นอยู่ เช่น TX/RX, I2C

## การรับข้อมูล Bluetooth และแสดงผลบน PC ด้วยโปรแกรม PuTTY
* เปิด Device Manager เช็ค Ports ที่ PC มีอยู่แล้ว ก่อนทำการเชื่อมต่อกับ HC-05
  
![image](https://github.com/user-attachments/assets/6c70c2ab-6c12-4d6b-b55c-4d5067b8f774)

* เชื่อมต่อ HC-05 กับ PC
  
❗ไฟแสดงสถานะบน HC-05 จะกะพริบถี่ หมายถึงพร้อมสำหรับการเชื่อมต่อ ถ้ากะพริบช้าแสดงว่ามีการเชื่อมต่อเดิมอยู่
  
  ![image](https://github.com/user-attachments/assets/9d1ef2a3-77e1-45c0-aee0-9a61f988db2e)

* เปิด Device Manager เช็ค Ports ที่เพิ่มขึ้นมา ถ้าไม่ขึ้นแสดงว่าทำการเชื่อมต่อไม่สำเร็จ

  ![image](https://github.com/user-attachments/assets/879060b6-675e-4879-8b17-6cd8c23726c2)

  
* เปิดโปรแกรม PuTTY จากนั้นเลือก Connection type เป็น Serial เลือก Speed ตามที่ได้โปรแกรมไว้ และเลือก COM ที่เพิ่มขึ้นมา
  
  ![image](https://github.com/user-attachments/assets/a5623483-d112-45ba-b01a-2c8104c9c307)

* การแสดงผลบน PuTTY จะต้องเลือก Output ที่สอดคล้องกับ pin ที่ต่ออยู่

| STM32F108C8T6 | ประเภทการเชื่อมต่อ | Output ด้วย Micro-USB | Output ด้วย HC-05 |
|---|---|---|---|
| PA9 | Serial1 TX | "Serial.print" | "Serial1.print" |
| PA10 | Serial1 RX | "Serial.print" | "Serial1.print" |








  




