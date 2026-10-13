# moon-practice — Takım Ay projesi (pratik)

NASA Space Apps 2026 hazırlığımızın **takım pratik projesi**. 2023'teki "Make a Moonquake Map 2.0!" görevini temel
alıp, gerçek NASA verisiyle bir **Ay haritası web uygulaması** yapıyoruz ve üzerine **yürüyüş rotası araçları ve rota
arama (A\*)** ekliyoruz. Amaç: takım olarak birlikte çalışmayı, entegrasyonu ve araçları öğrenmek.
**Bu repo yarışma projesi değildir.**

> **İlk kez mi geliyorsun?** Önce kurulum rehberi:
> [`mars-drills/KURULUM.md`](https://github.com/mertikiz/mars-drills/blob/main/KURULUM.md).
>
> Ajanlar ve takım: kurallar [`AGENTS.md`](AGENTS.md) içinde. Plan ve kararlar özel planlama reposunda
> (`nasa-space-apps-2026`): `README.md` → `docs/notes/plan-current.md` → `docs/notes/prep-plan.md`.

## Sprintler (haftada ~2 saatlik ortak oturum)
| Sprint | Hafta | Ne yapıyoruz |
|---|---|---|
| 1 | 20–26 Ekim | React + Vite + Leaflet ile **Ay haritası**, yayında (Moon Trek karoları) |
| 2 | 27 Ekim–2 Kasım | Apollo **deprem istasyonları ve depremler** katman olarak (pin, açılır bilgi, tarih) |
| 3 | 3–6 Kasım | **Rota araçları:** yol çiz, uzunluk (Ay yarıçapıyla), yükseklik profili, yürüme süresi |
| 4 | 3–6 Kasım | **Rota arama:** (a) A\*'ı bir kez elle düz bir ızgarada yaz; (b) Python ile gerçek Ay yükseklik verisinden küçük bir **eğim maliyet ızgarası** (~100×100) üret → JSON; (c) açık kaynak bir A\* kütüphanesi (ör. EasyStar.js, MIT) en ucuz yolu bulsun, haritada çiz |

Her oturumda **farklı biri** oturumu yönetir ve `main`'e birleştirir (merge). Roller provadan sonra belirlenecek.

## Veri kaynakları
| Ne | Kaynak | Durum |
|---|---|---|
| Ay temel haritası | Moon Trek karoları, ör. `https://trek.nasa.gov/tiles/Moon/EQ/LRO_WAC_Mosaic_Global_303ppd_v02/1.0.0/WMTSCapabilities.xml` (karo ızgarası için bu dosyayı oku) · Leaflet'te `crs: L.CRS.EPSG4326` | ✅ çalışıyor, tarayıcıdan erişilebilir (CORS) |
| Apollo deprem verisi | NASA PDS arşivi (Apollo pasif sismik deney) | ⚠️ doğrulanacak (sprint 2'de) |
| Ay yükseklik/eğim (LOLA) | NASA LRO LOLA ürünleri | ⚠️ doğrulanacak (sprint 4'te) |

Her veri seti için `sablonlar/veri-karti.md` şablonuyla bir **veri kartı** doldurun.

## Çalışma şekli
- **`main` korumalı** (doğrudan push yok). Her iş için **kendi dalında** (branch) çalış, küçük commit'ler, sonra pull
  request; oturum yöneticisi birleştirir.
- **"Açıklayamadığın kodu birleştirme."** Yapay zekânın yazdığı her değişikliği oku ve çalıştırıp dene.
- Yapay zekâ kullanımını kısa bir kayda yaz (tarih, araç, ne için, nasıl doğrulandı); asıl projede beyan edeceğiz.

## Asıl projeyle ilişkisi (önemli)
NASA kuralı: projeye **14 Kasım 09:00'dan önce başlanmaz.** Bu yüzden buradaki **rota arama/A\* kodu, eğim/tehlike
kuralları, veri işleme betikleri ve arayüz tasarımı** yarışma reposuna **kopyalanmaz**, ezberden de yeniden yazılmaz.
Sadece **genel kurulum kodu** (Vite/React iskeleti, temel harita bileşeni, yardımcı fonksiyonlar) kaynak gösterilerek
kullanılabilir. Açık kaynak A\* kütüphanesi asıl projede de kullanılabilir.

Lisans: [MIT](LICENSE).
