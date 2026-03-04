Proje: ShopLite E-Ticaret Arayüzü
Teslim İçerikleri: index.html, style.css, README.txt

** Hangi Layout Yöntemlerini Nerede Kullandım? **
1. CSS Flexbox (Esnek Kutu Düzeni):
   - Üst Bar (Header): Logo ve menü linklerini yan yana dizmek, aralarındaki boşluğu (space-between) ayarlamak ve dikeyde ortalamak için kullanıldı.
   - Filtre Satırı (Filters): Arama kutusu ve kategori butonlarını (chipleri) hizalamak, sığmadığı durumda alt satıra şık bir biçimde kaymasını (flex-wrap: wrap) sağlamak için kullanıldı.
   - Kart İçi Düzen (Card Content): Ürün adı, açıklama, fiyat ve butonun dikey ve düzenli sıralanması için 'flex-direction: column' tercih edildi. Bu sayede footer (fiyat+buton) kısmı her zaman kartın en altına itilebildi (margin-top: auto).
   - Ana Footer: Telif hakkı metni ve alt linkleri yatay eksende uç noktalara yaslamak için kullanıldı.

2. CSS Grid (Izgara Düzeni):
   - Ürün Listesi (Product Grid): Tasarımın omurgası olan 8 adet ürün kartını ekran boyutuna göre kusursuz dizebilmek (Masaüstünde 4'lü, tablette 2'li, mobilde 1'li) için kullanıldı (grid-template-columns kullanılarak).

** Breakpoint'ler (Kırılma Noktaları) **
Responsive tasarımı sağlarken media queries kullandım:
1. Varsayılan (Masaüstü, >= 1024px): "Mobile-first" yerine projeyi genel desktop odaklı başlatarak ana CSS kurallarını geniş ekranlar için (4 sütunlu ızgara vb.) yazdım. 
2. @media (max-width: 1023px) - (600px ile 1023px arası Tabletler): Ürün gridi 4 sütundan 2 sütuna düşürülüp (grid-template-columns: repeat(2, 1fr)), hero başlık font boyutları ekranla orantılı küçültüldü.
3. @media (max-width: 599px) - (600px altı Mobil Ekranlar): Ürün listesi tek sütuna (1fr) düşer. Header içerisindeki logo ve menü dikey hizaya geçer. Filtre satırındaki arama input'u tüm genişliği (%100) kaplayarak dokunmatik ekranlara uyum sağlar.

** Öğrendiklerim / Zorlandıklarım **
1. CSS Değişkenleri (:root) kullanmak renk paletini (`--primary`, `--bg`, vb.) merkezi tek bir noktadan yönetmemi sağladı. Bu sayede her yere elle renk kodu yazmaktan kurtuldum ve tutarlı bir tema bütünlüğü (örneğin gölgelerde, kenarlıklarda `--muted` değişkenini kullanarak) elde ettim.
2. Erişilebilirlik (Accessibility) için standart ':focus' yerine ':focus-visible' kullandığımda, sadece klavye ile gezen kullanıcıların belirgin halkaları (outline) gördüğünü ve fare ile tıklayan kullanıcıların görsel olarak gereksiz outline'lardan rahatsız olmadığını deneyimledim. Bu, Modern UI prensipleri için önemli bir detaydı.
3. Grid ve Flex'i Aynı Projede Kullanmak: Makro layout için (kart dizilimi vb.) CSS Grid çok kesin ve matematiksel bir düzene imkan sağlarken, mikro layout için (menü linkleri, kart içi elemanlar) Flexbox'un esnekliği inanılmazdı. Bunların kombinasyonunu herhangi bir framework olmadan yapmak öğretici oldu.
4. "Sticky" Header: Header'ın sayfayla birlikte kaybolmaması, menünün her zaman üstte kalması için 'position: sticky; top: 0;' özelliğini kullandım. Arka planı düz beyaz yaparak içeriğin menüye karışmasını engelledim.
