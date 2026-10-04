# Kullanıcı Giriş Akışı — Algoritma Diyagramı

## Projenin Amacı
Bu algoritma, bir web uygulamasındaki kullanıcı giriş sürecini (Login) iş kurallarına uygun şekilde modellemektedir. Sistemin güvenliğini sağlamak amacıyla başarısız giriş denemelerini takip eden ve hesabı kilitleyen bir mantık üzerine kurulmuştur.

## İş Kuralları
- Algoritma başladığında öncelikle hesabın kilitli olup olmadığı kontrol edilir.
- Kullanıcı veri girişinde (e-posta veya şifre) boş alan bırakırsa uyarı gösterilir ve sayaç artırılmadan veri alma adımına geri dönülür.
- Bilgiler doğruysa başarılı giriş mesajı verilerek akış sonlandırılır.
- Bilgiler yanlışsa başarısız giriş sayacı 1 artırılır.
- Üç başarısız denemeye ulaşıldığında hesap geçici olarak kilitlenir ve giriş akışı kesilir.

## Akış Diyagramı
![Kullanıcı giriş akış diyagramı](flowchart.png)

## Test Senaryoları

| Senaryo | Beklenen Sonuç | Diyagram Doğrulaması |
|---|---|---|
| T1: Hesap kilitli | Giriş engellenir, akış biter | Başarılı (İlk kilit kontrolünden çıkış) |
| T2 & T3: E-posta veya şifre boş | Uyarı gösterilir, sayaç artmaz | Başarılı (Sayaç tetiklenmeden geri döner) |
| T4: Bilgiler doğru | Başarılı giriş gerçekleşir | Başarılı (Giriş başarılı adımıyla biter) |
| T7 & T8: Üçüncü yanlış deneme | Hesap kilitlenir, yeni giriş engellenir | Başarılı (Sayaç=3 kontrolü hesabı kilitler) |

## Tasarım Kararları
- **Sayaç Mantığı:** Başarısız giriş sayacı başlangıçta 0 (sıfır) olarak dikdörtgen bir işlem kutusunda tanımlanmıştır. 
- **Döngü Yönetimi:** Kullanıcı hatalı bilgi girdiğinde veya alanları boş bıraktığında, akış okları güvenli bir şekilde `E-posta ve şifre al` paralelkenar adımına geri bağlanarak döngü tamamlanmıştır.

## Öğrenci Bilgisi
- **Ad Soyad:** Emine Burnak
- **Ödev:** Algoritma Tasarımı ve Akış Diyagramı Ödevi

