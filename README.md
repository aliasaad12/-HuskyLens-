# -HuskyLens-
 التعرف على الوجه باستخدام HuskyLens مع الأردوينو

هذا المشروع يوضح كيفية استخدام كاميرا HuskyLens AI للتعرف على الوجوه وربطها مع لوحة Arduino عبر واجهة UART، بحيث يمكن قراءة بيانات التعرف من الأردوينو لتنفيذ أوامر معينة.

⸻

📌 مميزات المشروع
	•	التعرف على الوجه باستخدام الذكاء الاصطناعي المدمج في HuskyLens.
	•	التواصل بين HuskyLens والأردوينو عبر SoftwareSerial.
	•	إمكانية برمجة الأردوينو لتنفيذ أوامر مختلفة عند التعرف على وجه معيّن.

⸻

🛠 المكونات المطلوبة
	•	لوحة Arduino Uno أو ما يعادلها.
	•	حساس HuskyLens AI Camera.
	•	كابل USB-C لتوصيل HuskyLens بالطاقة أو تحديث الإعدادات.
	•	4 أسلاك توصيل (Jumper Wires) للتوصيل عبر UART.
	•	مكتبة HUSKYLENS للأردوينو
 ⚙ التوصيل
طرف HuskyLens
طرف Arduino Uno
VCC
5V
GND
GND
TX
Pin 11 (RX)
RX
Pin 10 (TX)
 📥 تثبيت مكتبة HuskyLens
	1.	افتح برنامج Arduino IDE.
	2.	من القائمة اختر: سكيتش → تضمين مكتبة → إدارة المكتبات…
	3.	في خانة البحث اكتب: HUSKYLENS.
	4.	عند ظهور المكتبة، اضغط تثبيت
 � كود أردوينو
#include "HUSKYLENS.h"
#include "SoftwareSerial.h"

HUSKYLENS huskylens;
SoftwareSerial mySerial(10, 11); // TX, RX

void setup() {
  Serial.begin(9600);
  mySerial.begin(9600);
  huskylens.begin(mySerial);
}

void loop() {
  if (huskylens.request()) {
    HUSKYLENSResult result = huskylens.read();
    if (result.ID != 0) {
      Serial.print("تم اكتشاف وجه برقم ID: ");
      Serial.println(result.ID);
    }
  }
  delay(500);
}
<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/64c724fd-7581-4053-a9cf-e805fe35c6a8" />

HUSKYLENS husky
  delay(500);
}
