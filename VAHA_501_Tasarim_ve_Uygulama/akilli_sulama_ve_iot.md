# 📱 Akıllı Sulama ve IoT Entegrasyonu

Vaha Mekaniği'nde her damla suyun hesabı tutulur. IoT (Nesnelerin İnterneti) sistemleri, ekosistemin "sinir sistemi" olarak görev yaparak suyun en verimli şekilde dağıtılmasını sağlar.

## 📡 Sistem Bileşenleri
Akıllı bir vaha yönetim ünitesi şu katmanlardan oluşur:

1.  **Sensör Katmanı:**
    *   **Kapasitif Toprak Nem Sensörü:** Toprağın su içeriğini ölçer. (Korozyona dayanıklı modeller tercih edilmelidir).
    *   **Sıcaklık ve Nem (DHT22):** Mikro-iklim verilerini toplar.
    *   **Işık Şiddeti (BH1750):** Buharlaşma potansiyelini tahmin etmek için kullanılır.
2.  **Kontrol Katmanı:**
    *   **ESP32 / Arduino:** Sensörlerden gelen verileri işleyen ve Wi-Fi/LoRa üzerinden buluta gönderen ana beyin.
3.  **Aktüatör Katmanı:**
    *   **Solenoid Valfler:** Sulama hattını otomatik olarak açıp kapatan elektromanyetik vanalar.

## 🧠 Akıllı Algoritmalar
Sistem basit bir zamanlayıcıdan ziyade, şu verileri analiz ederek karar verir:
- **Vapotranspirasyon (ET) Hesabı:** Hava sıcaklığı, nem ve rüzgar verilerine göre bitkinin kaybettiği suyun tahmin edilmesi.
- **Hava Durumu Entegrasyonu:** Eğer 24 saat içinde yağmur bekleniyorsa sulamanın ertelenmesi.
- **Hidrobölge Yönetimi:** Sukulentler ve ağaçlar için farklı sulama rejimlerinin otomatik uygulanması.

## 📊 Veri İzleme (Dashboard)
Toplanan veriler Grafana veya benzeri platformlarda görselleştirilerek sistemin sağlığı takip edilir:
- Toprak nem seviyesi trendleri.
- Toplam su tüketimi raporları.
- Pil/Güneş paneli voltaj takibi.

## 🛠️ Açık Kaynak Yaklaşımı
Vaha Mekaniği, bu sistemlerin yerel imkanlarla ve düşük maliyetle kurulabilmesi için açık kaynak kodlu yazılımlar ve standart donanımlar kullanmayı teşvik eder.

---
*"Teknoloji, doğayı izlemek ve onun sessiz ihtiyaçlarını duymak için bir kulaklıktır."*
