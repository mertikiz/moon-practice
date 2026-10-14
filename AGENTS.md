# AGENTS.md — moon-practice (takım Ay pratik projesi)

Bu repoda çalışan **tüm yapay zekâ ajanları** (Google Antigravity, Claude Code, Copilot, Cline, …) için kurallar.
Önce `README.md`'yi oku.

## Dil
- Kullanıcı hangi dilde yazıyorsa (genelde **Türkçe**) o dilde cevap ver.
- Kod, değişken/fonksiyon adları ve commit mesajları **İngilizce**; kod yorumları Türkçe olabilir.

## Bu repo ne?
- NASA Space Apps 2026 hazırlığı için **takım pratik projesi**: gerçek NASA verisiyle bir **Ay haritası web
  uygulaması** + yürüyüş rotası araçları + A\* ile rota arama. Yarışma projesi **değil**.
- Teknoloji: **React + Vite + TypeScript**, harita **OpenLayers + proj4**, arayüz **Tailwind + shadcn/ui**, grafik
  **Recharts**, durum (state) önce React'in kendisiyle (gerekirse Zustand), kontrol **ESLint + Prettier + Vitest**,
  yayın **Cloudflare Pages**. Veri hazırlama için `scripts/` altında küçük **Python** betikleri. Rota arama için açık
  kaynak bir A\* kütüphanesi (ör. EasyStar.js, MIT).
- Moon Trek karoları eşit dikdörtgen (equirectangular) ızgarada: OpenLayers'ta katmanı Trek'in `WMTSCapabilities.xml`
  dosyasından kur (`optionsFromCapabilities`), Ay koordinat sistemini proj4 ile tanımla. Koordinatlar: GeoJSON
  **[boylam, enlem]**. Haritayı React içinde **bir kez** oluştur (ref + effect); her render'da yeniden kurma.
- Paket sürümlerini `package.json`'dan kontrol et; farklı OpenLayers sürümlerinin örneklerini karıştırma.

## Kurallar
1. **Önce plan göster**, onay al, sonra değiştir. Küçük, anlaşılır adımlarla ilerle.
2. Mevcut yapıyı ve kütüphaneleri koru; ekip onayı olmadan mimariyi/kütüphaneyi değiştirme, gereksiz bağımlılık ekleme.
3. **Veri uydurma.** URL, uç nokta, veri seti adı veya sonuç uydurma; emin değilsen "doğrulanmadı" de. Gerçek veri
   yoksa açıkça "örnek/sentetik veri" diye işaretle.
4. Her veri seti için bir **veri kartı** doldurulmasına yardım et (`sablonlar/veri-karti.md`).
5. Değişiklikten sonra ilgili kontrolleri çalıştır (`npm run build`, testler, Python betiği için küçük bir örnek girdi)
   ve **gerçek sonucu** bildir; çalıştırmadığın şeye "geçti" deme.
6. **Git:** her iş kendi dalında; commit/push/merge sadece kullanıcı isteyince. Force-push, `reset --hard`, `clean -fd`,
   dal silme yok. **Asla** gizli bilgi (API anahtarı, token, şifre) veya kişisel e-posta commit etme. Büyük veri
   dosyaları `data/` içine (git'e girmez).
7. Buradaki **rota arama/A\* kodu, eğim/tehlike kuralları, veri işleme betikleri ve arayüz tasarımı** yarışma reposuna
   kopyalanmaz (NASA'nın "14 Kasım 09:00'dan önce projeye başlama" kuralı). Genel kurulum kodu kaynak gösterilerek
   kullanılabilir.
8. İşin sonunda kısaca özetle: hangi dosyalar değişti, hangi komutlar çalıştı, sonuç ne, eksik ne.

## GitHub kuralları
- **`main` korumalı:** doğrudan push edilemez. Her iş için **yeni bir dal** aç (ör. `sprint2-deprem-katmani`), küçük
  commit'ler at, sonra **pull request** aç. O oturumun yöneticisi (session lead) inceleyip birleştirir (merge).
- Pull request açıklamasına yaz: ne değişti, nasıl test edildi, yapay zekâ kullanıldıysa ne için.
- Dalda çalışmaya başlamadan önce `main`'i çek (`git pull`), sonra dalını güncel tut.
- **Asla** force-push yapma, push edilmiş geçmişi yeniden yazma, başkasının dalını silme.
- **Repo ayarları, görünürlük (özel/açık), işbirlikçiler, dal koruması ve repo silme sahibine (Mert) aittir.**
  Ajanlar bunlara dokunmaz.
- Sadece çalıştırıp kontrol ettiğin işi push et (`npm run build` geçmeli).
