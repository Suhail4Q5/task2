# task2
*COMPANY NAME*:CODTECH IT SOLUTIONS 

*NAME*:SHAIK SUHAIL

*INTERN ID*:CT06DF2960

*DOMAIN*:EMBEDDED SYSTEM

*DURATION*:6 WEEKS

*MENTOR*:NEELA SANTOSH

*DESCRIPTION*: 
**Core Components:**
Arduino UNO – serves as the brain (microcontroller).
HC‑05 Bluetooth Module – establishes wireless communication using Serial over Bluetooth (SPP). 
electronicsworkshops.com
+13
howtomechatronics.com
+13
quartzcomponents.com
+13
Relay Module (1–4 channels) – switches mains-powered devices on or off. 
electronicwings.com
Voltage Divider – protects the HC‑05’s RX pin by stepping down the Arduino’s 5 V TX to 3.3 V. 
quartzcomponents.com
+12
instructables.com
+12
electroinvention.co.in
+12
Smartphone App – sends simple ASCII commands ('1' to ON, '0' to OFF). You can use pre-made apps or custom-designed ones via MIT App Inventor. 
instructables.com
+1
techatronic.com
+1
**🛠 How It Works**:
Pairing: Pair your phone with the HC‑05 (default PIN: 1234/0000).
Command Transmission: The app sends either '1' or '0' via Bluetooth.
Arduino Logic:
On receiving '1', it pulls the relay pin LOW → energizes relay → device turns ON.
On receiving '0', it sets pin HIGH → de-energizes relay → device turns OFF. 
electroinvention.co.in
smartify.in
Optional Feedback: The Arduino can print "Bulb ON"/"Bulb OFF" to the Serial Monitor for debugging. 
instructables.com
+6
smartify.in
+6
electroinvention.co.in
+6**
**Circuit Setup**:
**Power & Ground: HC‑05 VCC → 5 V; GND to common ground (Arduino + relay).
Serial Lines:
HC‑05 TX → Arduino RX (pin 0)
HC‑05 RX ← Arduino TX (pin 1) through a 1 kΩ + 2.2 kΩ resistor divider 
electroinvention.co.in
+1
howtomechatronics.com
+1
Relay Connection:
Relay VCC → 5 V, GND → common GND
IN1 (or INx) → chosen Arduino digital output (e.g., pin 4)
Device Wiring: AC live wire → relay COM; relay NO output wire → appliance live input; neutral goes straight to appliance. 
smartify.in

****Sample Arduino Sketch:**
Copy
Edit
#define RELAY_PIN 4
char data;

void setup() {
  pinMode(RELAY_PIN, OUTPUT);
  digitalWrite(RELAY_PIN, HIGH); // Relay OFF by default
  Serial.begin(9600);
}

void loop() {
  if (Serial.available()) {
    data = Serial.read();
    if (data == '1') {
      digitalWrite(RELAY_PIN, LOW);  // ON
      Serial.println("Device ON");
    } else if (data == '0') {
      digitalWrite(RELAY_PIN, HIGH); // OFF
      Serial.println("Device OFF");
    }
  }
}
This matches the instructions from multiple tutorials and examples. 
projecthub.arduino.cc
+6
subr.edu
+6
smartify.in
+6
howtomechatronics.com
+1
smartify.in
+1
**✅ Advantages & Use-Cases**:
Affordable & simple: Typically under $30 for a single-device setup.
Customizable: Scale to multiple devices by adding more relays and buttons. 
electroinvention.co.in
+10
hackaday.io
+10
makersportal.com
+10
Expandable: Can integrate sensors like PIR, LDR, or voice control. 
projecthub.arduino.cc
+1
**THANK YOU!**
CIRCUIT:   ![Image](https://github.com/user-attachments/assets/9697b103-e645-438b-a405-98c9faf02225)

*OUTPUT*:
When the Arduino receives a character over Bluetooth (via the HC‑05):

If it gets '1', it sets RELAY_PIN (digital pin 4) LOW, which activates the relay, allowing power through and turning the connected appliance ON.

If it gets '0', it sets RELAY_PIN HIGH, which deactivates the relay, cutting power and turning the appliance OFF.

There’s no text output printed to your Serial Monitor—only the relay’s electrical state changes. If you want debug feedback over USB, you could add code like this:

cpp
Copy
Edit
if (data == '1') {
  digitalWrite(RELAY_PIN, LOW); // Relay on
  Serial.println("Relay ON");
} else if (data == '0') {
  digitalWrite(RELAY_PIN, HIGH); // Relay off
  Serial.println("Relay OFF");
}
This way, each button press from your phone would result in an “Relay ON” or “Relay OFF” message

