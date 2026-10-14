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
9. **Commit'ten önce değişiklik özeti:** `git status` ve `git diff --stat` sonucunu göster. Görevle ilgisiz bir dosya
   değiştiyse ya da mevcut bir kod silindiyse bunu açıkça söyle ve geri almayı öner.
10. **İki deneme kuralı:** aynı hatayı iki denemede çözemezsen dur. Ne denediğini, hatanın tam metnini ve bir sonraki
    küçük adımı yaz, kullanıcıdan yön iste; körlemesine denemeye devam etme.
11. **Anlat:** iş bitince yazdığın kodun ne yaptığını kısa ve Türkçe anlat (hangi dosya ne yapıyor, veri nereden gelip
    nereye gidiyor). Kullanıcı sorarsa satır satır açıkla. Amaç: kullanıcı kodu jüriye kendisi anlatabilsin.
12. **Pull request açıklamasını sen doldur:** `.github/pull_request_template.md` şablonunu kullan; "Yapay zekâ
    kullanımı" bölümüne aracı, modeli ve ne yaptığını yaz. "Kodu okudum, ne yaptığını anlatabilirim" kutusunu
    **işaretleme**; onu kullanıcı işaretler.

## GitHub kuralları
- **`main` korumalı:** doğrudan push edilemez. Her iş için **yeni bir dal** aç (ör. `sprint2-deprem-katmani`), küçük
  commit'ler at, sonra **pull request** aç. O oturumun yöneticisi (session lead) inceleyip birleştirir (merge).
- Pull request açıklaması `.github/pull_request_template.md` şablonuyla açılır; ajan doldurur (kural 12), kişi kontrol eder.
- Dalda çalışmaya başlamadan önce `main`'i çek (`git pull`), sonra dalını güncel tut.
- **Asla** force-push yapma, push edilmiş geçmişi yeniden yazma, başkasının dalını silme.
- **Repo ayarları, görünürlük (özel/açık), işbirlikçiler, dal koruması ve repo silme sahibine (Mert) aittir.**
  Ajanlar bunlara dokunmaz.
- Sadece çalıştırıp kontrol ettiğin işi push et (`npm run build` geçmeli).
