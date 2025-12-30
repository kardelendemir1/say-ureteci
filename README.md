ALGORİTMA EsitBitUreteci(seed, adet)
    bitler = [] (Boş liste)
    sifir_kotasi = adet / 2
    bir_kotasi = adet / 2
    n = seed

    DÖNGÜ: bitler listesinin uzunluğu < adet olduğu sürece
        EĞER n çiftse:
            n = n / 2
        DEĞİLSE:
            n = 3 * n + 1
        
        EĞER n <= 1 ise:
            n = n + seed + 7 (Döngü kırma)

        gelen_bit = n MOD 2

        EĞER (gelen_bit == 0 VE sifir_kotasi > 0) ise:
            bitler'e 0 ekle
            sifir_kotasi = sifir_kotasi - 1
        EĞER Kİ (gelen_bit == 1 VE bir_kotasi > 0) ise:
            bitler'e 1 ekle
            bir_kotasi = bir_kotasi - 1
        DEĞİLSE (Gelen bitin kotası dolmuşsa):
            Diğer bitin kotasından düş ve bitler'e ekle
    
    DÖNGÜ SONU
    DİZİYİ DÖNDÜR
BİTTİ
