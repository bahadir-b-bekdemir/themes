# GitHub’da B - Cube Temalarını Paylaşma Rehberi

Bu rehber, **Google Chrome** ve **Mozilla Firefox** için olan iki ayrı B - Cube tema projesini Git kullanarak GitHub’da nasıl yayınlayacağınızı adım adım anlatır.

İki yaygın yol var:

1. **Tek repo (monorepo)** — Her iki tema aynı `themes` deposunda kalır; tek bir GitHub reposu.
2. **İki ayrı repo** — Chrome teması ve Firefox teması için ayrı GitHub repoları.

---

## Seçenek 1: Tek Repo (Monorepo) — Mevcut Yapıyı Kullanmak

Şu anki yapınız zaten buna uygun: tüm temalar `themes` klasörü altında. Sadece bu repoyu GitHub’a itmeniz yeterli.

### 1.1 GitHub’da yeni repo oluşturma

1. [GitHub](https://github.com) → **New repository**
2. **Repository name:** `themes` (veya `b-cube-themes`)
3. **Public** seçin
4. **Add a README**, **.gitignore**, **License** eklemeyin (yerelde zaten var)
5. **Create repository** tıklayın

### 1.2 Yerel projeyi GitHub’a bağlama ve ilk push

PowerShell’i `themes` klasöründe açın:

```powershell
cd C:\Users\Balamir\Desktop\themes
```

Mevcut durumu kontrol edin:

```powershell
git status
```

Tüm değişiklikleri stage’e alıp commit edin:

```powershell
git add .
git status
git commit -m "Chrome ve Firefox B-Cube temaları eklendi"
```

GitHub’daki repoyu uzak (remote) olarak ekleyin. `KULLANICI_ADI` ve `REPO_ADI` yerine kendi bilgilerinizi yazın:

```powershell
git remote add origin https://github.com/KULLANICI_ADI/REPO_ADI.git
```

Örnek:

```powershell
git remote add origin https://github.com/bahadir-b-bekdemir/themes.git
```

Eğer `origin` zaten tanımlıysa adresi güncellemek için:

```powershell
git remote set-url origin https://github.com/KULLANICI_ADI/REPO_ADI.git
```

Ana dalı (genelde `main`) gönderin:

```powershell
git branch -M main
git push -u origin main
```

Bundan sonra projeler şu yollardan erişilebilir:

- Chrome: `https://github.com/KULLANICI_ADI/REPO_ADI/tree/main/google-chrome-themes/b-cube`
- Firefox: `https://github.com/KULLANICI_ADI/REPO_ADI/tree/main/mozilla-firefox-themes/b-cube`

README dosyalarınızdaki “Kaynak / Source” linklerini bu adreslere göre güncelleyebilirsiniz.

---

## Seçenek 2: İki Ayrı Repo (Chrome ve Firefox Ayrı)

Her tarayıcı teması için ayrı bir GitHub reposu istiyorsanız aşağıdaki yöntemi kullanın.

### 2.1 GitHub’da iki repo oluşturma

1. **Chrome teması için:** New repository → örn. `b-cube-chrome` → Public → Create (README/.gitignore/license eklemeyin).
2. **Firefox teması için:** New repository → örn. `b-cube-firefox` → Public → Create (README/.gitignore/license eklemeyin).

### 2.2 Chrome teması için ayrı repo

#### A) Yeni klasör ve temiz Git geçmişi (önerilen)

PowerShell’de:

```powershell
# Çalışma klasörü (masaüstü veya istediğiniz yer)
cd C:\Users\Balamir\Desktop

# Chrome teması için yeni klasör
mkdir b-cube-chrome
cd b-cube-chrome

# Git başlat
git init
```

Chrome tema dosyalarını kopyalayın (klasör içeriği, `b-cube` içindeki her şey):

```powershell
# themes\google-chrome-themes\b-cube içeriğini b-cube-chrome'a kopyala
Copy-Item -Path "C:\Users\Balamir\Desktop\themes\google-chrome-themes\b-cube\*" -Destination "C:\Users\Balamir\Desktop\b-cube-chrome" -Recurse -Force
```

`.gitignore` dahil tüm dosyaların geldiğini kontrol edin:

```powershell
dir
git status
```

İlk commit ve GitHub’a gönderme:

```powershell
git add .
git commit -m "İlk sürüm: B - Cube Chrome teması"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADI/b-cube-chrome.git
git push -u origin main
```

`KULLANICI_ADI` yerine kendi GitHub kullanıcı adınızı yazın.

#### B) Mevcut themes repo’sundan sadece Chrome klasörünü kopyalayıp repo yapmak

Eğer `themes` içinde çalışıyorsanız ve sadece Chrome tarafını “ayrı repo” yapmak istiyorsanız:

```powershell
cd C:\Users\Balamir\Desktop
mkdir b-cube-chrome
cd b-cube-chrome
git init
Copy-Item -Path "..\themes\google-chrome-themes\b-cube\*" -Destination "." -Recurse -Force
git add .
git commit -m "İlk sürüm: B - Cube Chrome teması"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADI/b-cube-chrome.git
git push -u origin main
```

### 2.3 Firefox teması için ayrı repo

Aynı mantık; sadece kaynak klasör ve repo adı farklı:

```powershell
cd C:\Users\Balamir\Desktop
mkdir b-cube-firefox
cd b-cube-firefox
git init
Copy-Item -Path "C:\Users\Balamir\Desktop\themes\mozilla-firefox-themes\b-cube\*" -Destination "C:\Users\Balamir\Desktop\b-cube-firefox" -Recurse -Force
git add .
git commit -m "İlk sürüm: B - Cube Firefox teması"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADI/b-cube-firefox.git
git push -u origin main
```

### 2.4 README linklerini güncelleme

İki ayrı repo kullandıysanız, her tema kendi repo URL’sine sahip olur. README’deki “Kaynak / Source” satırını buna göre değiştirin:

- **Chrome** (`b-cube-chrome/README.md`):  
  `https://github.com/KULLANICI_ADI/b-cube-chrome`
- **Firefox** (`b-cube-firefox/README.md`):  
  `https://github.com/KULLANICI_ADI/b-cube-firefox`

---

## Özet Tablo

| Yöntem            | Avantaj                          | Repo sayısı |
|-------------------|-----------------------------------|-------------|
| Tek repo (Seçenek 1) | Tek link, tek clone, basit yönetim | 1           |
| İki ayrı repo (Seçenek 2) | Her tema bağımsız, ayrı star/issue | 2           |

---

## Sık Kullanılan Git Komutları (Sonradan Güncellemeler İçin)

Değişiklik yaptıktan sonra GitHub’a göndermek için:

```powershell
git add .
git status
git commit -m "Kısa açıklama (örn: renk güncellemesi)"
git push
```

Başka bir bilgisayarda projeyi almak için:

```powershell
git clone https://github.com/KULLANICI_ADI/REPO_ADI.git
cd REPO_ADI
```

---

## Kimlik Doğrulama (HTTPS)

`git push` sırasında kullanıcı adı/şifre sorarsa:

- **Şifre:** Artık GitHub hesap şifresi değil, **Personal Access Token (PAT)** kullanılır.
- GitHub → **Settings** → **Developer settings** → **Personal access tokens** → **Tokens (classic)** → **Generate new token**. `repo` yetkisi verin; token’ı güvenli yerde saklayın.
- İlk push’ta kullanıcı adı = GitHub kullanıcı adı, şifre = token.

Alternatif: **GitHub Desktop** veya **SSH key** kullanarak da push yapabilirsiniz.

---

Bu rehber, hem tek repoda hem iki ayrı repoda yayınlamak için gerekli Git adımlarını kapsar. Hangisini kullanacağınız tamamen tercihinize bağlıdır.
