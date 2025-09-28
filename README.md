# 🛒 Ecommerce Catalog - VIX Front End Core Initiative

## 📌 Fitur Utama
- **Menampilkan Data dari API** → menggunakan [Fake Store API](https://fakestoreapi.com/docs).  
  Contoh: `https://fakestoreapi.com/products/1` → kategori "men’s clothing".  
- **Tampilan Produk Dinamis** → hanya menampilkan 1 produk, berganti saat klik **Next Product**.  
- **Loading Element** → menggunakan skeleton/loader agar lebih UX friendly.  
- **API Call**:  
  - Endpoint: `https://fakestoreapi.com/products/{index}` (index = 1–20).  
  - Jika kategori `men’s clothing` / `women’s clothing` → ditampilkan.  
  - Jika kategori lain → diarahkan ke halaman **Unavailable Product**.  
  - Index otomatis reset ke `1` setelah mencapai `20`.  

---

## 🎨 Komponen Desain
- **Men Section**  
- **Women Section**  
- **Unavailable Product**
  
---

## 🛠️ Tech Stack
- [Vue.js](https://vuejs.org/) → Frontend framework  
- **CSS** → Styling halaman
- [Fake Store API](https://fakestoreapi.com/docs) → Data produk Ecommerce  

---

## ⚡ Project Setup
```bash
# Install dependencies
npm install

# Compiles and hot-reloads for development
npm run dev

# Compiles and minifies for production
npm run build
