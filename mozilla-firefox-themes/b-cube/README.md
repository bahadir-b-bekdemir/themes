<div align="center">

# B - Cube

</div>

<div align="center">

[![Lisans: MIT](https://img.shields.io/badge/Lisans-MIT-blue.svg)](LICENSE)
[![Firefox](https://img.shields.io/badge/Firefox-Tema-FF7139?logo=firefox)](https://www.mozilla.org/firefox/)

**B - Cube**, Firefox için yalnızca koyu modda kullanılabilen, sade ve modern bir statik temadır.

**Mozilla Add-ons:** [addons.mozilla.org/firefox/addon/b-cube](https://addons.mozilla.org/firefox/addon/b-cube)

**Kaynak:** [github.com/bahadir-b-bekdemir/themes → mozilla-firefox-themes/b-cube](https://github.com/bahadir-b-bekdemir/themes/tree/main/mozilla-firefox-themes/b-cube)

</div>

---

<div align="center">

## Kendi bilgisayarında yükleme

</div>

1. Bu depoyu indirin veya klonlayın.
2. Firefox’ta adres çubuğuna `about:debugging` yazıp girin.
3. **Bu Firefox** sekmesinde **Geçici eklenti yükle** düğmesine tıklayın.
4. `manifest.json` dosyasının bulunduğu `b-cube` klasörünü seçin.

Tema yüklenecektir; geçici eklenti her Firefox yeniden başlatıldığında kaldırılır, tekrar yüklemeniz gerekir.

---

<div align="center">

## Görünüm

Temanın tarayıcıda nasıl göründüğü:

![B - Cube tema önizlemesi](images/preview.svg)

*Koyu arka plan, turuncu ve yeşil-sarı vurgular; sekme çubuğu ve araç çubuğu.*

</div>

---

<div align="center">

## Özellikler

</div>

- **Koyu tema** — Göz yormayan koyu renk paleti  
- **Statik tema** — Yalnızca `manifest.json`; ek script veya izin gerekmez  
- **Manifest v3** — Güncel WebExtension standardı  

---

<div align="center">

## Geliştirme

### Gereksinimler

</div>

- [Node.js](https://nodejs.org/) (LTS önerilir)
- [Firefox](https://www.mozilla.org/firefox/)

<div align="center">

### Bağımlılıkları yükleme

</div>

```bash
npm install
```

<div align="center">

### Geliştirme modunda çalıştırma

</div>

```bash
npm run run
```

Firefox’ta geçici bir profil ile eklenti açılır.

<div align="center">

### Derleme (paket oluşturma)

</div>

```bash
npm run build
```

Çıktı `web-ext-artifacts/` klasöründe `.xpi` dosyası olarak oluşur.

<div align="center">

### Lint

</div>

```bash
npm run lint
```

---

<div align="center">

## Proje yapısı

</div>

```
b-cube/
├── manifest.json   # Tema tanımı (renkler vb.)
├── package.json
├── images/
│   └── preview.svg
├── README.md
├── LICENSE
└── .gitignore
```

---

<div align="center">

## Lisans

Bu tema [MIT Lisansı](LICENSE) ile lisanslanmıştır.

© 2026 [Bahadır B. Bekdemir](mailto:bahadir.b.bekdemir@hotmail.com)

</div>
