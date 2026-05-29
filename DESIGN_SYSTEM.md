# Design System — Uzm. Psk. Çağla Dilara Sipahi
> Claude Code için hazırlanmış tam tasarım referansı. Bu dosyayı projenin kök dizinine koy ve Claude Code'a "DESIGN_SYSTEM.md dosyasını oku ve buna göre uygula" de.

---

## Genel His & Ton

- **Stil**: Sıcak & organik — Meadowell.com ilhamlı
- **Hedef kitle**: Çocuk, ergen ve genç yetişkinlerin ebeveynleri + ergenler kendileri
- **Ton**: Profesyonel ama sıcak, sade, iddialı cümlelerden kaçınılan
- **Referans siteler**: meadowell.com, mindify.framer.website

---

## Renkler

### Ana Palet

| İsim | Hex | Kullanım |
|------|-----|----------|
| Krem Arka Plan | `#F5F0E8` | Sayfa arka planı, hero dışı section'lar |
| Sıcak Gri | `#EDEAE2` | Hizmetler section arka planı |
| Açık Bej | `#EDE5D0` | Süreç section arka planı |
| Koyu Metin | `#2C2C2A` | Başlıklar, ana metin |
| Orta Gri | `#888780` | Alt metin, açıklamalar |
| Footer/Koyu | `#2C2C2A` | Footer arka planı |

### Yeşil Palet (Ana Renk)

| İsim | Hex | Kullanım |
|------|-----|----------|
| Açık Yeşil | `#EAF3DE` | Tag arka planı, ikon kutu arka planı |
| Orta Yeşil | `#C0DD97` | Hero aksanlar, açık yeşil yazı |
| Ana Yeşil | `#639922` | Başlık vurguları, italic metinler |
| Koyu Yeşil | `#3B6D11` | İkonlar, section eyebrow'lar |
| Derin Yeşil | `#27500A` | Hero arka planı (koyu ton) |

### Amber Palet (Vurgu Rengi)

| İsim | Hex | Kullanım |
|------|-----|----------|
| Açık Amber | `#FDF0D0` | Tag arka planı, ikon kutu |
| Ana Amber | `#E8A830` | Hero butonu, vurgu |
| Koyu Amber | `#C48A10` | Hizmet numaraları, süreç numaraları |
| Derin Amber | `#A0720A` | Section eyebrow yazıları |

### WhatsApp Butonu

| Durum | Arka Plan | Yazı Rengi |
|-------|-----------|------------|
| Normal | `#1DAF5B` | `#C0DD97` (açık yeşil) |
| Hover | `#1DAF5B` | `#C0DD97` (değişmez) |

---

## Tipografi

### Fontlar

```css
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;1,400&family=Inter:wght@300;400;500&display=swap');

--font-display: 'Playfair Display', serif;  /* Başlıklar */
--font-body: 'Inter', sans-serif;            /* Gövde metni */
```

### Hiyerarşi

| Eleman | Font | Boyut | Ağırlık | Renk |
|--------|------|-------|---------|------|
| Hero adı | Playfair Display | 40px | 400 | `#F5F0E8` |
| Hero unvan | Playfair Display italic | 18px | 400 | `rgba(245,240,232,0.75)` |
| H2 başlık | Playfair Display | 26–30px | 400 | `#2C2C2A` |
| Section eyebrow | Inter | 11px | 500 | `#A0720A` — uppercase, letter-spacing: 0.1em |
| Gövde metin | Inter | 13–14px | 400 | `#888780` — line-height: 1.8 |
| Hizmet başlığı | Inter | 15px | 500 | `#2C2C2A` |
| Hizmet numarası | Inter | 12px | 500 | `#C48A10` |
| Nav linkleri | Inter | 12px | 500 | `rgba(245,240,232,0.8)` — uppercase, letter-spacing: 0.06em |

### Italic Vurgu (Playfair)
Başlıklarda belirli kelimeleri vurgulamak için Playfair Display italic + yeşil renk kullan:
```html
<h2>Hangi konularda <em style="color:#639922; font-style:italic;">destek</em> verebilirim?</h2>
```

---

## Navigation

### Layout
- Logo/isim **ortada**, linkler iki yana yayılmış (CSS grid: `1fr auto 1fr`)
- Hero üzerinde `position: absolute`, transparan arka plan
- Padding: `22px 40px`

### Nav CTA Butonu
```css
background: rgba(232,168,48,0.2);
border: 1px solid rgba(232,168,48,0.5);
color: #F5C96A;
font-size: 11px;
font-weight: 500;
padding: 8px 16px;
border-radius: 5px;
text-transform: uppercase;
letter-spacing: 0.06em;
```

---

## Hero Section

### Yapı
- Tam ekran (`min-height: 480px`)
- Fotoğraf arka plan (psikolog fotoğrafı)
- Üzerine koyu overlay
- İçerik **ortada ve ortalanmış** (`align-items: center`, `text-align: center`)

### Overlay Katmanları
```css
/* 1. Arka plan (fotoğraf yokken) */
background: linear-gradient(170deg, #2A3A18 0%, #3D5020 30%, #4A6028 55%, #7A8A50 80%, #9AAA70 100%);

/* 2. Radyal ışık efekti */
background: radial-gradient(ellipse at 50% 80%, rgba(100,140,60,0.4) 0%, transparent 70%);

/* 3. Karartma overlay */
background: linear-gradient(to bottom, rgba(20,28,12,0.4) 0%, rgba(20,28,12,0.15) 50%, rgba(20,28,12,0.6) 100%);
```

### İçerik Sırası (yukarıdan aşağıya)
1. Eyebrow: `Adana · Çocuk, Ergen & Genç Yetişkin` — amber `#F5C96A`
2. Unvan: `Uzman Psikolog` — Playfair italic, `rgba(245,240,232,0.75)`
3. İsim: `Çağla Dilara Sipahi` — Playfair 40px, `#F5F0E8`
4. Alt metin: kısa açıklama — `rgba(245,240,232,0.58)`
5. Buton: WhatsApp — amber `#E8A830`

### Hero Giriş Animasyonu
```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}
/* Her eleman için artan delay: 0.15s, 0.3s, 0.38s, 0.5s, 0.65s */
```

---

## Section Arka Plan Renkleri (Sıra)

| Section | Arka Plan |
|---------|-----------|
| Nav + Hero | Fotoğraf / koyu yeşil |
| Hakkımda | Sol: koyu yeşil fotoğraf, Sağ: `#F5F0E8` |
| Hizmetlerim | `#EDEAE2` |
| Süreç | Sol: koyu yeşil fotoğraf, Sağ: `#EDE5D0` |
| İletişim/CTA | `#F5F0E8` |
| Footer | `#2C2C2A` |

---

## Hizmetler Section

### Layout
- Liste tarzı, `border-top` ile ayrılmış satırlar
- Grid: `40px 1fr 44px` (numara | içerik | ikon)
- `padding: 20px 0` her satır
- `border-bottom: 0.5px solid rgba(0,0,0,0.08)`

### İkon Kutusu
```css
width: 40px; height: 40px;
background: #FDF0D0;   /* amber açık */
border-radius: 10px;
```
İkon rengi: `#A0720A`

### 4 Hizmet
1. Oyun Odaklı Çocuk Danışmanlığı
2. Çocuk & Ergen Danışmanlığı
3. Sınav Süreci Danışmanlığı
4. Online Danışmanlık

---

## Süreç Section

### Layout
- 2 sütun grid: Sol fotoğraf | Sağ içerik
- Sağ arka plan: `#EDE5D0` (açık bej)
- Padding: `60px 44px`

### Adım Yapısı
```html
<div class="step">
  <span class="step-num">01.</span>  <!-- #C48A10 amber -->
  <div>
    <div class="step-title">...</div>  <!-- #2C2C2A, 14px, 500 -->
    <div class="step-desc">...</div>   <!-- #7A6A50, 12px, line-height 1.75 -->
  </div>
</div>
```

### 3 Adım
1. İlk İletişim & Randevu
2. İlk Seans & Değerlendirme
3. Kişiye Özel Plan

---

## CTA Section

### İçerik
```
Eyebrow: İLETİŞİM & RANDEVU
H2: Adana Gazipaşa'da yüz yüze,
    tüm Türkiye'ye online seans
Alt metin: Seans saatleri: Salı–Cuma 11:00–20:00, Cumartesi 11:00–17:00
Buton: WhatsApp ile Randevu Al
```

### WhatsApp Butonu
```css
background-color: #1DAF5B;
color: #C0DD97;           /* açık yeşil yazı */
font-size: 15px;
font-weight: 600;
padding: 15px 34px;
border-radius: 7px;
border: none;
/* ikon fill da #C0DD97 */
```

---

## Scroll Animasyonları

Tüm section'lara `.reveal` class'ı ekle, JS ile `IntersectionObserver` kullan:

```css
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry, i) => {
    if (entry.isIntersecting) {
      setTimeout(() => entry.target.classList.add('visible'), i * 80);
    }
  });
}, { threshold: 0.12 });

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```

---

## Spacing Sistemi

| Token | Değer | Kullanım |
|-------|-------|----------|
| xs | 4px | İç boşluklar |
| sm | 8px | Elementler arası |
| md | 12–16px | Component içi |
| lg | 24–28px | Section içi gap |
| xl | 48px | Section padding dikey |
| 2xl | 60–72px | Büyük section padding |

---

## Border Radius

| Eleman | Değer |
|--------|-------|
| Buton | 6–7px |
| Kart | 12px |
| İkon kutu | 10px |
| Tag/pill | 20px |
| Sayfa wrapper | 16px |

---

## İçerik Kuralları

- ❌ İstatistik sayaçları kullanma ("300+ kişi", "%95 memnuniyet")
- ❌ Testimonials/yorum bölümü ekleme
- ❌ İddialı cümleler ("Hayatını değiştir", "En iyi psikolog")
- ❌ Aile danışmanlığı hizmeti yok
- ✅ Sade, profesyonel, güven veren ton
- ✅ Hizmetler: Oyun Terapisi, Çocuk & Ergen, Sınav, Online
- ✅ İletişim: Sadece WhatsApp butonu (e-posta butonu yok)
- ✅ Lokasyon: Adana Gazipaşa (yüz yüze) + tüm Türkiye (online)

---

## Fotoğraf Alanları

| Yer | Açıklama |
|-----|----------|
| Hero arka plan | Psikolog fotoğrafı — tam ekran, overlay altında |
| Hakkımda sol | Psikolog portre fotoğrafı |
| Süreç sol | Ofis / ortam fotoğrafı |

---

## İletişim Bilgileri

```
WhatsApp: +90 505 421 71 28
E-posta: pskcagladsipahi@gmail.com (footer'da göster, buton olarak değil)
Adres: Cemalpaşa Mah., Seyhan / Adana
Seans saatleri: Salı–Cuma 11:00–20:00 | Cumartesi 11:00–17:00
```
