# sayitahminoyunu 
#230601039 idal kapan programlama dersi ödevi soru1
enkucuk = None   #en küçük tahmin sayısını saklamak için bir değişken oluşturdum.

from random import randint #random rastgele sayılar üretmemizi sağlayan bir standart kütüphanedir.
                           #randint(a, b),a ve b arasında (a ve b dahil olmak üzere)rastgeletam sayı üretir.

def tahmin_oyunu():    # Tahmin oyunu işlevini tanımlayan fonksiyondur
    global enkucuk
    
    print("Bilgisayar 50 ile 250 arasında bir sayı tuttu.")
    bilgisayar = randint(50, 250)   #bilgisayar 50ve 250 dahil olarak bunlar arasında bir tamsayı tutar
    hak = 10         #10 deneme hakkımız var.
    senin_tahminin = 0
    tahminler = []      #yapılan tahninleri tutacak bir liste oluşturuldu.
    
    while senin_tahminin != bilgisayar and hak > 0: #tahmin işlemi yapılır.
        print(f"Kalan tahmin hakkınız: {hak}")      #kalan tahmin hakkı ekranda gösteriir.
        girilen_sayi = False               

        while not girilen_sayi:
            try:
                senin_tahminin = int(input("Tahmininiz nedir? "))    
                if senin_tahminin < 50 or senin_tahminin > 250:
                    print("Lütfen 50 ile 250 arasında bir sayı giriniz.")
                else:
                    tahminler.append(senin_tahminin)
                    girilen_sayi = True
            except ValueError:      #eğer tam sayı harici bir şey girilirse kullanıcı uyarılır.
                print("Geçersiz giriş. Lütfen bir tam sayı giriniz.")

        if senin_tahminin > bilgisayar:         #eğer tahminim bilgisayardan büyükse bu kısım çalışır.
            print("Daha küçük bir sayı tahmin etmelisin.")
        elif senin_tahminin < bilgisayar:         #eğer tahmin bilgisayardan küçükse bu kısım    çalışır.
            print("Daha büyük bir sayı tahmin etmelisin.")
        
        hak -= 1     #tahmin hakkı bir düşürülür.

    if hak > 0 and senin_tahminin == bilgisayar:   #tahmin hakkı 0'dan büyükse ve doğru tahmin yapıldıysa bu kısım çalışır.
        print(f"TEBRİKLER! {bilgisayar} sayısını {len(tahminler)} tahminde bildiniz.")
        print("Geçmiş Tahminler:", tahminler)   #geçmiş tahminler gösterilir ekranda.
        
        if enkucuk is None or len(tahminler) < enkucuk:
            enkucuk = len(tahminler)

        print(f"En Başarılı Tahmin Rekoru: {enkucuk} tahmin")


    elif hak == 0:     #eğer tahmin hakkı kalmadıysa bu kısım çalışır.
        print("MAALESEF! Tahmin hakkınız bitti. Doğru Cevap:", bilgisayar)

while True:
    tahmin_oyunu()      #tahmin oyunu fonksiyonu çağırılır.
    devam = input("Başka bir oyun oynamak ister misiniz? (E/H): ")
    if devam.lower() != 'e':     #e tuşuna basılmazssa oyun biter.
        print("Oyunu sonlandırdınız. İyi günler!")
        break

