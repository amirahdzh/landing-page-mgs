# Frontend Developer Take-Home Test

## 📌 Deskripsi Proyek
Proyek ini merupakan implementasi landing page berdasarkan desain Figma dan API service yang diberikan dalam take-home test untuk posisi **Frontend Developer (Vue.js)**.

## 🛠️ Teknologi yang Digunakan
- Vue 3 + Vite
- TypeScript
- Tailwind CSS
- Library VueUse (useFetch dan onClickOutside)

## 📂 Struktur Direktori
```
Directory structure:
└── landing-page-mgs/
    ├── README.md
    ├── index.html
    ├── package.json
    ├── tsconfig.app.json
    ├── tsconfig.json
    ├── tsconfig.node.json
    ├── vite.config.ts
    ├── public/
    └── src/
        ├── App.vue
        ├── main.ts
        ├── style.css
        ├── vite-env.d.ts
        ├── assets/
        │   └── home/
        ├── components/
        │   ├── AppFooter.vue
        │   ├── AppHeader.vue
        │   └── Home/
        │       ├── Cards/
        │       │   ├── ServiceCard.vue
        │       │   └── WhyUsCard.vue
        │       └── Sections/
        │           ├── AboutSection.vue
        │           ├── CareersSection.vue
        │           ├── ContactSection.vue
        │           ├── HeroSection.vue
        │           ├── PurposeSection.vue
        │           ├── ServicesSection.vue
        │           └── WhyUsSection.vue
        ├── router/
        │   └── index.ts
        └── views/
            └── HomeView.vue

```

## 🚀 Cara Menjalankan Proyek
Pastikan Anda sudah menginstal **Node.js** (disarankan versi terbaru LTS) dan **npm** atau **yarn**.

1. **Clone repositori ini**
   ```sh
   git clone <repository-url>
   cd <nama-folder>
   ```

2. **Install dependensi**
   ```sh
   npm install
   # atau jika menggunakan yarn
   yarn install
   ```

3. **Jalankan proyek**
   ```sh
   npm run dev
   # atau jika menggunakan yarn
   yarn dev
   ```

4. **Akses di browser**
   Buka `http://localhost:5173/` untuk melihat hasilnya.

## 📌 Fitur Utama
✅ Sesuai desain Figma yang diberikan  
✅ Implementasi Tailwind CSS tanpa `<style>` dalam komponen  
✅ Struktur proyek yang modular dan maintainable  
✅ Konsumsi API untuk Services (GET), Whies (GET), Contacts (POST)

## 📝 Catatan Tambahan
- Saya telah memastikan bahwa tampilan dan fungsionalitas sesuai dengan desain yang diberikan.
- Tampilan responsif merupakan pandangan subjektif saya karena desain yang disediakan tidak memberikan tampilan referensi selain layar besar.
- Akan ada banyak peringatan `[Vue Router warn]: No match found for location with path` pada console karena saya mengimplementasikan <RouterLink /> dengan path yang belum didefinisikan di src/router/index.ts.

---
Terima kasih! 🚀
