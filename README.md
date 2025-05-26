# EE495 Selected Topic in Electrical Engineering 

ที่มาและความสำคัญ 

อากาศยานไร้คนขับขนาดเล็ก (Drone) เป็นอากาศยานที่ควบคุมจากระยะไกล ใช้การควบคุมอัตโนมัติซึ่งมีอยู่ด้วยกัน 2 ลักษณะ คือ การควบคุมอัตโนมัติจากระยะไกล และการควบคุมแบบอัตโนมัติโดยใช้ระบบการบินด้วยตนเอง โดย Drone จะใช้ Microcontroller ในการควบคุมการบิน โดยในรายวิชานี้จะได้เจาะลึกลงไปถึงการวิเคราะห์โครงสร้างของ Drone, วิธีการเลือกบอร์ด Microcontroller ที่เหมาะสม, ศึกษาระบบการทำงานและระบบควบคุม, ออกแบบ PCB, การประกอบอุปกรณ์, การเขียนโปรแกรมควบคุมด้วย Arduino IDE, การสื่อสารระหว่างอุปกรณ์, และการทดสอบการบิน

## ชิ้นส่วนและอุปกรณ์
| ประเภทอุปกรณ์ | รุ่น | น้ำหนัก (กรัม) |
|---|---|---|
| Drone Frame | FPV F330 | 143 |
| Electronic Speed Controller | 40A | 30 |
| Blushless DC Motor | A2212 1400KV | 216 |
| Prop | 8045 CW, CCW | 5 |
| Battery | LiPo 3s 2800mAh | 207 |
| Receiver | FS-iA6B | 18 |
| Microcontroller | STM32F108C8T6 | 10 |
| Gyroscope | MPU-6050 | 5 |
| Ultrasonic Sensor | HC-SR04 | 10 |
| Bluetooth | HC-05 | 5 |

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

    ถ้า STM32F103C8T6 ตัวที่ใช้ มีตัวเลขขึ้นตามตัวอย่าง แสดงว่าสามารถใช้งานได้ปกติ แต่ถ้าไม่มีต้องทำการ Bootloader DFU ใหม่
    
     **Bootloader DFU (Device Firmware Upgrade) โดยเป็นมาตรฐาน USB สำหรับการอัปเดตเฟิร์มแวร์บนอุปกรณ์
    
     **STM32 บางรุ่น ไม่มี DFU Bootloader มาจากโรงงานจึงต้องแฟลชเข้าไปเองครั้งแรก
  * ตัวอย่างไฟล์ Bootloader ที่รองรับ DFU (.bin) 

![Screenshot 2025-05-26 230505](https://github.com/user-attachments/assets/28eec64b-24da-48ef-babd-ed3b7c222c1e)

 4. เปิดโปรแกรม Arduino IDE ทำการเลือกบอร์ด "Generic STM32F103C series"

![Screenshot 2025-05-26 234413](https://github.com/user-attachments/assets/b1239923-63b4-4e6c-bb9a-41314da2fa23)

 5. เลือกวิธีอัพโหลดข้อมูลเป็น "STLink"

![image](https://github.com/user-attachments/assets/405b637d-67ca-443d-a205-4aa41a38ed65)

สามารถใช้งาน STM32F103C8T6 ได้ปกติ

## ศึกษาการทำงานของ STM32F103C8T6, Sensor และการสื่อสารระหว่างอุปกรณ์





