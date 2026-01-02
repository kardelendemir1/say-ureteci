Oluşturduğum algoritma, matematik dünyasının en gizemli problemlerinden biri olan Collatz Sanısı'nı (3n+1) bir motor olarak kullanır ve bu kaotik süreci deterministik bir filtre ile işleyerek kusursuz bir anahtar 
üretir.İşte adım adım algoritmanın çalışma mantığı:
1. Motor Mekanizması: Collatz SanısıAlgoritmanın kalbi Collatz dizisidir. Bu dizinin özelliği, seçilen başlangıç sayısı ne olursa olsun, sayıların çok düzensiz ve tahmin edilemez bir şekilde artıp azalmasıdır.
   Giriş (Seed): Senin verdiğin başlangıç sayısıdır.
   Kural: Sayı çift ise $n/2$, tek ise $3n+1$ uygulanır.
   Kaos: Bu işlemler sonucunda oluşan sayı dizisi (yörünge), bir sonraki adımın ne olacağını tahmin etmeyi imkansız kılan "sahte rastgele" (pseudo-random) bir yapı sunar.
2.Dönüştürücü: g(n) Fonksiyonu (Parite Bit üretimi)Collatz dizisindeki büyük sayılar kendi başlarına anahtar olamazlar. Onları ikili sisteme (0 ve 1) indirmemiz gerekir.
   Her adımda oluşan sayıya bakılır:
   Sayı Çift ise $\rightarrow$ 0 biti üretilir.
   Sayı Tek ise $\rightarrow$ 1 biti üretilir.
   Bu işlem matematiksel olarak $g(n) = n \pmod 2$ şeklinde ifade edilir.
3. Filtreleme: Kesin Eşitlik (Kota) Kontrolü
   Normal bir Collatz dizisinde 0'ların veya 1'lerin sayısı her zaman eşit olmayabilir (genellikle çift sayılar biraz daha baskındır).
   Buraya "eşit derecede 0 ve 1" kuralını sağlamak için buraya bir "Akıllı Filtre" ekledim:

  Kota: Toplam 10 bit üretilecekse, 5 adet '0' ve 5 adet '1' kotası belirlenir.
  Seçici Geçirgenlik: Algoritma bir sayı üretir; eğer bu sayı '0' üretiyorsa ve henüz 5 tane '0' dolmamışsa diziye ekler.Eğer '0' kotası dolmuşsa, o sayıyı pas geçer ve bir sonraki '1' gelene kadar
Collatz döngüsünü çevirmeye devam eder.
  Sonuç: Bu sayede dizi bittiğinde istatistiksel sapma sıfıra iner.
4.Döngü Kırıcı (Reset) Mekanizması
  Collatz Sanısı'na göre her sayı eninde sonunda 4 > 2 > 1döngüsüne girer. Eğer algoritma burada takılırsa sürekli aynı bitleri üretmeye başlar.
  Bunu engellemek için kodumda: "Eğer sayı 1'e ulaşırsa, mevcut anahtar ve dizi uzunluğunu kullanarak sayıyı tekrar yükselt" komutu bulunur. Bu, jeneratörün sonsuza kadar farklı bitler üretmesini sağlar.

Özet Akış Diyagramı
BAŞLAT: Kullanıcıdan sayıyı al.

HESAPLA: Collatz kuralını uygula.

ÜRET: Sayı tek mi çift mi? (0 veya 1).

KONTROL: Bu bitten elimizde 5 tane oldu mu?

Hayır: Diziye ekle.

Evet: Bu biti atla.

DÖNGÜ: Dizi 10 eleman olana kadar Adım 2'ye dön.

BİTİR: Tam dengeli anahtarı teslim et.

Bu mantık sayesinde, verdiğin tek bir sayıdan yola çıkarak hem matematiksel bir temeli olan hem de 0-1 dengesi hatasız olan bir şifreleme anahtarı elde etmiş oluyorum.
