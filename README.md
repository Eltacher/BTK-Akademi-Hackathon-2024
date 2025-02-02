# HACKATHON PROJE

## Genel Bakış
Bu proje, **BTK Akademi**'nin düzenlemiş olduğu **HACKATHON 2024** kapsamında geliştirilmiştir. Proje, **backend** ve **frontend** bileşenlerinden oluşmakta olup, **web scraping** işlevselliği ve **MySQL** ile **local** de çalışan bir veritabanından oluşmaktadır.

---

## Proje Yapısı

```
HACKATHON_PROJE/
│
├── backend/ # Arka uç (Node.js) dosyaları
│   ├── analyzer.js               # Verileri analiz eden modül
│   ├── countProjects.js          # Proje sayısını hesaplayan modül
│   ├── projectCountsDatabase.js  # Proje sayıları veritabanı işlemleri
│   ├── projectTitlesDatabase.js  # Proje başlıkları veritabanı işlemleri
│   ├── server.js                 # Sunucu başlangıç dosyası
│   ├── package.json              # Arka uç bağımlılıkları
│   └── package-lock.json         # Arka uç bağımlılık kilidi
│
├── frontend/ # Ön yüz (React/Vite) dosyaları
│   ├── public/                   # Statik dosyalar
│   ├── src/                      # Uygulama kaynak dosyaları
│   ├── index.html                # Ana HTML dosyası
│   ├── vite.config.js            # Vite yapılandırma dosyası
│   ├── package.json              # Ön yüz bağımlılıkları
│   └── package-lock.json         # Ön yüz bağımlılık kilidi
│
├── WebScrapping_Database/ # Web scraping için veritabanı dosyaları
│   ├── database.js        # Veritabanı bağlantısı ve işlemleri
│   ├── githubAPI.js       # GitHub API ile etkileşim
│   ├── githubDatabase.js  # GitHub veritabanı işlemleri
│   ├── index.js           # Web scraping başlangıç dosyası
│   ├── package.json       # Web scraping bağımlılıkları
│   └── package-lock.json  # Web scraping bağımlılık kilidi
│
└── README.md # Proje dökümanı
```

---

## Kurulum

### 1. Node.js ve npm'yi Yükleyin
Projeyi çalıştırmadan önce, sisteminizde **Node.js** ve **npm** yüklü olmalıdır. Yüklemek için [Node.js resmi web sitesini](https://nodejs.org/) ziyaret edin.

### 2. Bağımlılıkları Yükleme
Hem arka uç hem de ön yüz bağımlılıklarını yüklemek için, aşağıdaki komutları her klasör içinde çalıştırın:

```bash
cd backend
npm install

cd ../frontend
npm install

cd ../WebScrapping_Database
npm install
```

---

## Veritabanını Hazırlama
Projede **MySQL** kullanılmaktadır. **Local** ortamda **iki tane veritabanı** oluşturulmalıdır:

1. Web scraping ile çekilen proje başlıkları verilerini depolamak için bir veritabanı.
2. GitHub API kullanılarak çekilen proje sayıları verilerini depolamak için bir veritabanı.

**Veritabanına proje başlıklarını eklemek için:**
```bash
cd WebScrapping_Database
node database.js
```

**Veritabanına proje sayılarını eklemek için:**
```bash
cd WebScrapping_Database
node githubDatabase.js
```

### Notlar:
- **GitHub API** (githubAPI.js) kullanılarak yapılan proje sayıları araması "[query] projects" şeklinde yapılmıştır.
- **arxiv.com** kullanılarak yapılan proje başlıkları araması için doğrudan "[query]" kullanılmıştır.
- **Backend** klasörünün içinde bulunan **.env** dosyasına **Gemini AI API** anahtarı eklenmelidir.

---

## Projeyi Çalıştırma
Ana dizinde aşağıdaki komutu çalıştırın:
```bash
npm start
```

---

## Kullanım
Bu proje, kullanıcının seçmiş olduğu **proje alanı** için **web scraping** ile toplanan **proje başlıkları veritabanını** kullanarak **Gemini AI** ile yeni proje konuları önermeyi amaçlamaktadır.

Ayrıca, kullanıcı arayüzünde **seçilen proje alanı** ile ilgili **yıllara göre proje sayılarını grafiksel olarak göstermek** hedeflenmiştir. Bu sayede daha **canlı ve etkileşimli** bir deneyim sunulacaktır.

---

## Lisans
Bu proje **MIT Lisansı** altında lisanslanmıştır.

