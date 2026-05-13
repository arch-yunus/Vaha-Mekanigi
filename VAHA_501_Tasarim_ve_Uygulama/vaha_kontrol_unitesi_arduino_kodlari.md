# 🤖 Vaha Kontrol Ünitesi: Arduino ve ESP32 Kodları

Bu bölüm, VAHA 501 kapsamında akıllı sulama ve ekosistem izleme sisteminin kalbi olan **Vaha Kontrol Ünitesi** için gerekli temel kodları ve devre şemasını içerir.

## 📡 Donanım Gereksinimleri
- **Mikrodenetleyici:** ESP32 (Wi-Fi/Bluetooth desteği için) veya Arduino Uno.
- **Sensör:** Kapasitif Toprak Nem Sensörü v1.2 (Korozyona dayanıklı).
- **Aktüatör:** 5V/12V Röle Modülü (Su pompası veya solenoid vana için).
- **Güç:** 5V Güneş Paneli ve Li-ion pil şarj devresi (TP4056).

## 💻 Temel Otomasyon Kodu (Arduino C++)

```cpp
/*
  Vaha Mühendisliği - Akıllı Sulama Sistemi v1.0
  Toprak nemi belirli bir eşiğin altına düştüğünde pompayı çalıştırır.
*/

const int sensorPin = 34;    // ESP32 Analog Pin
const int relayPin = 26;     // Röle Kontrol Pini
const int threshold = 2500;  // Nem eşik değeri (Sensöre göre kalibre edilmeli)

void setup() {
  Serial.begin(115200);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH); // Röleyi kapalı başlat (Modüle göre değişebilir)
}

void loop() {
  int sensorValue = analogRead(sensorPin);
  Serial.print("Toprak Nem Değeri: ");
  Serial.println(sensorValue);

  if (sensorValue > threshold) { // Toprak kuru ise (Değer yükseldikçe kuruluk artar)
    Serial.println("Vaha sulanıyor...");
    digitalWrite(relayPin, LOW); // Pompayı aç
    delay(10000);                // 10 saniye sula
    digitalWrite(relayPin, HIGH); // Pompayı kapat
    delay(3600000);              // 1 saat bekle (Aşırı sulamayı önlemek için)
  } else {
    Serial.println("Toprak nemi ideal.");
    digitalWrite(relayPin, HIGH);
  }
  
  delay(10000); // 10 saniyede bir ölçüm yap
}
```

## 🌐 Nesnelerin İnterneti (IoT) Katmanı
ESP32 kullanarak verileri **Blynk** veya **Thingspeak** gibi platformlara göndererek, vahanın durumunu dünyanın her yerinden cep telefonunuzla izleyebilirsiniz.

## 📐 Montaj Notları
- Sensör kablolarını korozyona karşı korumak için epoksi veya silikon ile izole edin.
- Kontrol ünitesini dış etkenlerden korumak için IP65 sınıfı su geçirmez bir kutu içine yerleştirin.

---
*"Kod, toprağın susuzluğunu dijital bir çığlığa dönüştürür."*
