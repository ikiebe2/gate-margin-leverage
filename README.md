# gate io kaldıraçlı işlem: Marj mı vadeli mi, kaç x kaldıraç var, komisyonlar ne kadar — sıfırdan ilk pozisyona kadar

Bu kelimeyi aratan kişinin kafasındaki soru genelde tek: "Kaldıraçlı işlemi nereden açacağım, kaç x'e kadar çıkabilirim ve bu bana kaça mal olur?" Gate tarafında cevap, çoğu rehberin atladığı bir detay yüzünden karışıyor: platformda birbirinden tamamen farklı iki kaldıraç mekanizması var ve ikisinin limitleri, maliyetleri ve riskleri aynı değil. Üstüne bir de yeni açılan vadeli hesabın ilk günlerinde devreye giren bir kaldıraç sınırı var; bunu bilmeyen kullanıcılar "125x yazıyordu, neden 20x görüyorum" diye dolaşıyor.

Aşağıda ikisini de ayırıp, hesap açma adımlarından komisyon tablosuna, VIP kademelerinden likidasyon eşiğine kadar ne varsa toparladım.

## Gate'te iki farklı kaldıraç yolu var

Spot marj ile vadeli işlem, isim olarak benziyor ama işleyiş olarak ayrı dünyalar. Spot marjda borç alıp mevcut bakiyenizin üstünde pozisyon açıyorsunuz ve faiz ödüyorsunuz. Vadeli işlemde ise sözleşme alıp satıyorsunuz; borç faizi yok ama fonlama ücreti ve likidasyon mekanizması devrede.

|  | Spot marj (kaldıraçlı spot) | USDT-M süresiz vadeli |
| --- | --- | --- |
| Kaldıraç aralığı | 10x'e kadar | İzole marjda 1x–125x |
| Maliyet yapısı | İşlem komisyonu + borç faizi | Emir komisyonu + fonlama ücreti |
| Vade / sona erme | Yok, borç açık kaldığı sürece faiz işler | Sözleşme süresiz, fonlama 8 saatte bir |
| Uygun kullanım | Mevcut coini teminat göstererek pozisyon büyütmek | Yön tahmini, kısa pozisyon, hedge |
| Temel risk | Teminat oranı düşerse zorunlu azaltma | Likidasyon, izole/çapraz seçimine göre |

Yeni başlayanlar için pratik ayrım şu: "kaldıraç" kelimesini duyunca akıllarına gelen şey genelde vadeli işlem. Spot marj daha çok elindeki varlığı satmadan pozisyon büyütmek isteyenlerin tercihi.

## Kaldıraç neyi değiştirir, neyi değiştirmez

En yaygın yanılgı komisyonla ilgili. Vadeli tarafta işlem ücreti pozisyon büyüklüğü üzerinden hesaplanıyor, kaldıraçla hiçbir bağlantısı yok. 100 USDT'lik bir pozisyonu 100x'te de açsanız, 3x'te de açsanız ödediğiniz komisyon aynı. Kaldıracın değiştirdiği tek şey, o pozisyonu tutmak için gereken başlangıç teminatı.

Sayılarla bakalım. 1.000 USDT teminatla 10x kaldıraç kullanırsanız 10.000 USDT'lik pozisyon açarsınız. Fiyat aleyhinize %1 hareket ettiğinde pozisyon tarafında 100 USDT kayıp oluşur; bu sizin teminatınızın %10'u. Aynı hareket 20x'te %20'ye, 50x'te %50'ye çıkar. Kaldıraç, zarar durdur emri koymadığınız senaryoda likidasyon mesafesini de aynı oranda daraltır.

> Gate'in kendi yardım dokümanı, kaldıraç arttıkça gereken teminatın azaldığını ama riskin belirgin şekilde yükseldiğini, kaldıraç değişiminin gerçekleşmiş veya gerçekleşmemiş kâr-zararı doğrudan etkilemediğini belirtiyor.

## Adım adım: kayıttan ilk kaldıraçlı pozisyona

Süreç Gate tarafında şöyle işliyor:

1. **Kayıt ve kimlik doğrulama.** Hesabı açıp KYC'yi tamamlıyorsunuz. Vadeli ve marj hesapları için bu adım fiilen zorunlu; ayrıca iki adımlı doğrulamayı açmak para çekme işlemlerinde işinizi kolaylaştırır.
   👉 [👉 Gate hesabı aç ve KYC'yi tamamla](https://bit.ly/GateVIP)
2. **Vadeli hesabı aktive etmek.** Vadeli işlem sekmesine girdiğinizde platform hesabı açmanızı ister. Bu noktada yeni hesap sayıldığınız için kaldıraç üst sınırınız kısıtlı başlar.
3. **Varlık transferi.** Klasik hesap modunda sağ alttaki "Transfer" ile spot bakiyenizi vadeli hesaba aktarıyorsunuz. Vadeli hesapta USDT dışındaki coinleri de teminat olarak kullanabilirsiniz, ancak hesaplama kura göre yapılır.
4. **Marj modu ve kaldıraç seçimi.** Pozisyon açmadan önce izole mi çapraz mı kullanacağınızı, kaç x kaldıraç istediğinizi belirliyorsunuz. İkisi de pozisyon açıkken de değiştirilebiliyor, ancak hedge (iki yönlü) modda açık pozisyon varken marj modu değiştirilemiyor — önce pozisyonu kapatmanız gerekiyor.
5. **Pozisyon modu.** Tek yönlü veya hedge modları arasında seçim yapıyorsunuz. Konuyu aşağıda ayrı açıyorum çünkü kaldıraç seçiminden daha çok fark yaratıyor.
6. **Emir ve risk emirleri.** Limit, piyasa, koşullu ve gelişmiş limit emirleri mevcut. Emri gönderdikten sonra "Pozisyonlar" sekmesinden likidasyon fiyatını takip edip zarar durdur / kâr al seviyelerini kurabilirsiniz.

## Yeni vadeli hesapta 20x sınırı

Bu, Türkçe kaynaklarda pek geçmeyen ama en çok kafa karıştıran nokta. Gate, vadeli hesabını 3 günden kısa süre önce açmış kullanıcılara kaldıraç kısıtı uyguluyor: başlangıç üst sınırı 20x. Üç gün geçtikten sonra limit kademeli olarak açılıyor ve zamanla piyasanın izin verdiği seviyeye (izole marjda 125x'e kadar) yaklaşıyor.

> Kısıt, hesabınızın "yeni" sayılmasıyla ilgili; teminat miktarınız ya da VIP seviyenizle değil. Panik yapıp hesabı yeniden açmak bir şey kazandırmaz, sayaç sıfırlanır.

## Komisyon oranları: tablodaki rakamlar

Gate'in canlı ücret sayfasındaki güncel yapı şöyle:

| İşlem türü | VIP 0 oranı | Not |
| --- | --- | --- |
| Spot (maker/taker) | %0,10 / %0,10 | GT ile ödemede %0,09 / %0,09 |
| USDT-M vadeli (maker/taker) | %0,020 / %0,050 | Taker oranı VIP 3'ten sonra düşmeye başlıyor |
| Alpha | %0,8 | Hiçbir kademede değişmiyor |
| USDC/USDT paritesi | %0 / %0 | Hacmi VIP hesaplamasına dahil edilmiyor |

Komisyonun pratik hesabı: 60.000 USDT büyüklüğünde bir BTC pozisyonunu piyasa emriyle açarsanız 60.000 × %0,050 = 30 USDT ödersiniz. Aynı pozisyonu limit emriyle defterde bekletirseniz 60.000 × %0,020 = 12 USDT. Aynı işlem, iki farklı sonuç. Kaldıraçlı işlemde işlem sayısı arttığı için maker emir kullanmak ciddi fark yaratıyor.

Gate 9 Nisan 2026'da spot ve vadeli ücret yapısını güncelledi. Değişikliğin özeti: VIP 0–VIP 2 spot oranları aynı kaldı, üst kademelerde GT ile ödeme avantajı büyüdü, vadeli taker oranı VIP 3'ten itibaren kademeli olarak aşağı çekildi. ABD dolarına endeksli sözleşmelerde (USD1) hacim tartımı %20 üzerinden hesaplanıyor, yani bu kontratları işlemek VIP yükseltmede vadeli kadar etkili değil.

## VIP kademeleri: 17 seviyenin tamamı

Aşağıdaki tablo, Gate'in ücret sayfasında yayınlanan 30 günlük işlem hacmi eşiklerini ve o kademedeki oranları gösteriyor. VIP satın alınan bir paket değil; hacim veya GT varlığıyla kazanılıyor.

| Kademe | 30 günlük hacim eşiği | Spot maker/taker | GT ile ödeme | Vadeli taker | 24s çekim limiti | Hesap |
| --- | --- | --- | --- | --- | --- | --- |
| VIP 0 | 0 USDT | %0,100 / %0,100 | %0,090 | %0,0500 | 3.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 1 | 60.000 USDT | %0,099 / %0,099 | %0,089 | %0,0500 | 3.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 2 | 120.000 USDT | %0,098 / %0,098 | %0,088 | %0,0500 | 3.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 3 | 240.000 USDT | %0,097 / %0,097 | %0,087 | %0,0480 | 3.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 4 | 500.000 USDT | %0,095 / %0,096 | %0,086 | %0,0480 | 3.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 5 | 1.000.000 USDT | %0,090 / %0,095 | %0,081 / %0,085 | %0,0450 | 5.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 6 | 3.000.000 USDT | %0,085 / %0,090 | %0,076 / %0,081 | %0,0420 | 5.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 7 | 8.000.000 USDT | %0,080 / %0,085 | %0,070 / %0,076 | %0,0375 | 5.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 8 | 20.000.000 USDT | %0,075 / %0,080 | %0,060 / %0,072 | %0,0350 | 5.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 9 | 50.000.000 USDT | %0,070 / %0,075 | %0,050 / %0,068 | %0,0320 | 8.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 10 | 100.000.000 USDT | %0,040 / %0,058 | %0,040 / %0,058 | %0,0300 | 8.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 11 | 120.000.000 USDT | %0,030 / %0,045 | %0,030 / %0,045 | %0,0280 | 8.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 12 | 240.000.000 USDT | %0,020 / %0,037 | %0,020 / %0,037 | %0,0260 | 10.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 13 | 440.000.000 USDT | %0,010 / %0,030 | %0,010 / %0,030 | %0,0240 | 20.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 14 | 800.000.000 USDT | %0,008 / %0,023 | %0,008 / %0,023 | %0,0220 | 30.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 15 | 1.600.000.000 USDT | %0 / %0,020 | %0 / %0,020 | %0,0180–%0,0220 | 40.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |
| VIP 16 | 3.000.000.000 USDT | %0 / %0,0175 | %0 / %0,0175 | %0,0160–%0,0200 | 50.000.000 USDT | [ kayıt](https://bit.ly/GateVIP) |

Tabloda iki şey dikkat çekiyor. Birincisi, VIP 0'dan VIP 3'e kadar maker ve taker oranı birebir aynı — yani o kademelerde defterde bekleyen emir vermenin komisyon avantajı yok. Ayrılık VIP 4'te başlıyor. İkincisi, GT ile ödeme avantajı VIP 10'dan sonra kayboluyor; iki kolon aynı rakama dönüşüyor.

VIP 15–16'daki vadeli taker oranı aralık olarak veriliyor çünkü kontrat gruplarına göre değişiyor: BTC, ETH, SOL ve XRP'enstrümanlarından oluşan A grubu en düşük oranı alırken, diğer sözleşmeler C grubunda daha yüksek oran ödüyor.

Ayrıca küçük bir tutarsızlığa dikkat: Gate'in kendi öğrenme merkezindeki bazı makaleler hâlâ "VIP 0–14" diye 15 kademe anlatıyor, ücret sayfası ise 17 kademe listeliyor. Hesap açıp ne kadar ödeyeceğinizi merak ediyorsanız ücret sayfasındaki tabloyu baz alın.

## Kademe sadece hacimle yükselmiyor

VIP ataması üç ayrı yoldan yapılıyor ve bunlardan herhangi biri yeterli: hesaptaki varlık, son 14 günün ortalama GT bakiyesi veya son 30 günün işlem hacmi. Örnek eşikler:

| Kademe | Varlık | 14 gün ortalama GT | 30 günlük hacim |
| --- | --- | --- | --- |
| VIP 1 | 2.000 USDT | 50 GT | 60.000 USDT |
| VIP 5 | 40.000 USDT | 2.000 GT | 1.000.000 USDT |
| VIP 10 | 2.000.000 USDT | 100.000 GT | 100.000.000 USDT |
| VIP 14 | 30.000.000 USDT | 1.500.000 GT | 800.000.000 USDT |

Hacim hesabında her ürün aynı ağırlıkta sayılmıyor: spot ve hisse işlemleri %100, USDT ve BTC vadeli sözleşmeleri %40, opsiyonlar %20, CFD kontratları %10 üzerinden hesaba katılıyor. Yani aynı büyüklükte işlem yapan bir spot kullanıcısı ile bir vadeli kullanıcısı aynı kademeye düşmüyor; vadeli tarafta aynı hacmi üretmek için yaklaşık iki buçuk kat daha fazla pozisyon açmanız gerekiyor.

## Pozisyon modu, kaldıraçtan daha çok fark yaratıyor

Kaldıraçlı işleme yeni başlayanların çoğu kaldıraca odaklanıp pozisyon modunu es geçiyor. Oysa hangi modda olduğunuz, tek bir hatanın ne kadarını kaybedeceğinizi belirliyor.

**İzole marj** modunda her pozisyonun teminatı bağımsız. O pozisyon likide olursa kaybınız yalnızca ona ayırdığınız teminatla sınırlı kalıyor, hesabın geri kalanı etkilenmiyor. **Çapraz marj** modunda hesaptaki tüm bakiye ortak teminat havuzu olarak kullanılıyor; kısa vadeli dalgalanmalara karşı pozisyon daha dayanıklı hale geliyor ama hesabın net varlığı yetersiz kalırsa tüm bakiyeyi kaybedebiliyorsunuz.

Şubat 2026'da eklenen "Hedge Split" modu ise aynı piyasada dört pozisyonun bir arada tutulmasına izin veriyor: çapraz long, çapraz short, izole long ve izole short. İzole taraftaki long ve short pozisyonlar birbirinden bağımsız kaldıraç seviyeleri kullanabiliyor. Bu özellik için uygulamanın 8.7.0 veya üstü sürümü gerekiyor, ayrıca o an lead trader olarak işlem yapan hesaplar bu moda geçemiyor.

## Teminat oranı, likidasyon ve "hesabım neden eridi"

Spot marj tarafında Gate'in kendi dokümanında belirtilen iki eşik var:

> Teminat oranı %300'e indiğinde sistem azaltma uyarısı verir; %100 ve altına düştüğünde zorunlu azaltma tetiklenir ve pozisyonun bir kısmı veya tamamı otomatik kapatılır.

Vadeli tarafta izole modda eşik pozisyon teminatına bağlıyken, çapraz modda hesabın tamamı hesaplamaya giriyor. Bir başka deyişle çapraz modda "küçük bir pozisyon açtım, sadece onu kaybederim" varsayımı geçerli olmayabilir.

## Kaldıraç kullanmadan kaldıraç: 3x ve 5x tokenlar

Gate'te ayrıca kaldıraçlı token (ETF) ürünleri var. Bu tokenlar spot piyasada işlem görüyor ve 3x ile 5x seviyelerinde long/short stratejileri temsil ediyor. Teminat yönetimi ve marj takibi gerektirmiyor, otomatik yeniden dengeleme mekanizması kâr edildiğinde pozisyonu büyütüyor, zarar edildiğinde küçültüyor.

Buradaki mantık net: likidasyon riski neredeyse yok, ama karşılığında kaldıraç yapısını siz yönetmiyorsunuz ve ürün yatay piyasada değer kaybedebiliyor. Kısa vadeli işlemler ve hedge stratejileri için uygun görülüyor, uzun vadeli "al ve tut" mantığına uymuyor.

## Nakit maliyeti düşürmenin somut yolları

- **GT ile komisyon ödemek.** VIP 0'da spot oranı %0,10'dan %0,09'a indiriyor. Dikkat edilecek nokta: bakiye yetersiz kaldığında sistem otomatik olarak standart VIP oranına dönüyor ve bunu ayrıca uyarmıyor.
- **Limitte kalmak.** Vadeli tarafta maker/taker farkı iki buçuk kat. Emri defterde bekletmek her işlemde net kazanç.
- **USDC/USDT paritesini kullanmak.** %0 komisyon, ancak bu hacim VIP hesaplamasına dahil edilmiyor.
- **Komisyon iadesi kuponları.** Vadeli taker emirleri için puan kartı kullanılabiliyor; sabit %0,075 oranı üzerinden hesaplanıp belirli koşullarda %0,0225'e kadar inebiliyor.
- **Kademeyi takip etmek.** Vadeli hacim %40 ağırlıkla sayıldığı için sadece vadelle kademe atlamak zor; spot tarafındaki hareketlilik daha hızlı sonuç veriyor.

## Türkiye'den işlem yapacaklar için birkaç not

Gate'in davet ve ödül kampanyalarının kural metinlerinde Türkiye, Belçika, Birleşik Krallık, Fransa, Almanya, Hollanda, Avusturya ve Güney Kore ile birlikte kısıtlı bölgeler listesinde geçiyor. Bu, "arkadaşını davet et, ödül al" tarzı kampanyaların Türkiye mukimleri için geçerli olmadığı anlamına geliyor — hesap açıp işlem yapmanın önünde bir engel olarak yazılmamış, kampanya katılımı bazında bir istisna.

Uygulamada işinize yarayacak iki şey: KYC'yi işlem yapmadan önce tamamlamak ve kampanya katılırken kural metnindeki bölge maddesini okumak. Yeni kullanıcı ödül tutarları da kampanyaya göre değişiyor; Gate'in vadeli duyurularının alt kısmında "10.000 dolara kadar" ifadesi yer alırken, ödül merkezi sayfasında 5.000 dolar yazıyor. Hangi kampanyaya katıldığınıza göre değişen bir rakam, sabit bir taahhüt değil.

Hesap açma ve kampanya koşullarını görmek için:
👉 [👉 Gate vadeli işlem hesabını aç](https://bit.ly/GateVIP)

## Sık yapılan hatalar

**Teminatı sonuna kadar kullanmak.** Likidasyon fiyatı pozisyonun dibine yakınsar, ufak bir fitil sizi dışarı atar.

**Çapraz marjda tek pozisyon gibi davranmak.** Hesabın tamamı teminattır; bu modda risk hesap seviyesinde yönetilir.

**Zarar durdur emrini sonradan koymak.** Vadeli işlemde likidasyon otomatik, ama zarar durdur otomatik değil.

**Fonlama ücretini hesaba katmamak.** Uzun süre tutulan pozisyonlarda 8 saatte bir kesilen fonlama, komisyondan daha büyük bir maliyet kalemi haline gelebilir.

**Ağ seçimini kontrol etmemek.** Para yatırırken yanlış ağ seçmek, geri dönüşü olmayan bir işlem demek. USDT'yi ERC20 üzerinden çekerken minimum tutar 1 USDT; BTC'de minimum çekim 0,0005 BTC. Tablodaki ağ durumu sütununa bakmak beş dakikalık işlemi destek talebine çevirmekten iyidir.

## Sık sorulan sorular

**Gate'te maksimum kaldıraç kaç x?** İzole marjda vadeli pozisyonlarda 125x'e kadar ayar yapılabiliyor. Ancak vadeli hesabı 3 günden yeni olan kullanıcılarda üst sınır başlangıçta 20x ve zamanla açılıyor. Spot marjda üst sınır 10x.

**Komisyon kaldıraçla artar mı?** Hayır. Vadeli işlem komisyonu pozisyon büyüklüğü üzerinden hesaplanır, kaldıraç bu hesaba girmiyor.

**İzole mi çapraz mı seçmeliyim?** Tek bir işlemin riskini hesabın geri kalanından ayırmak istiyorsanız izole. Sermaye verimliliği ve dalgalanmaya dayanıklılık öncelikliyse çapraz, ama tüm bakiye riske girer.

**Kaldıraçlı işlem için minimum tutar var mı?** Pozisyon büyüklüğü sözleşme bazında değişiyor; belirleyici olan emrin minimum büyüklüğü ve teminatınızın likidasyon mesafesini kaldırabilmesi.

**VIP seviyemi nasıl yükseltirim?** Varlık, 14 günlük ortalama GT bakiyesi veya 30 günlük işlem hacmi yollarından herhangi biri yeterli. Hacim ağırlıkları ürüne göre değişiyor: spot %100, vadeli %40.

**Kaldıraçlı token ile vadeli aynı şey mi?** Değil. Tokenlar spot piyasada işlem görür, teminat yönetimi istemez ve likidasyon riski neredeyse yoktur; vadeli sözleşmede ise likidasyon fiyatı ve teminat oranı doğrudan sizin sorumluluğunuzda.

Kaldıraçlı işlem, hızlı kazanç vaadi değil, hata payını daraltan bir araç. Aynı %1'lik ters hareketin 5x'te canınızı yakmayacağı yerde 50x'te hesabınızı kapatması, stratejiden değil tamamen seçtiğiniz orandan kaynaklanıyor. Kademe ve oran tablosunu bir kenara not edip, ilk pozisyonu küçük tutmak bu işin en az konuşulan ama en çok işe yarayan kısmı.

İlk kaldıraçlı pozisyonunuzu açmak için:
👉 [👉 Gate'e kayıt ol ve vadeli hesabını aktive et](https://bit.ly/GateVIP)
