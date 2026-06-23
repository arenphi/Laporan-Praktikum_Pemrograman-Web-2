# 🌐 Portal Artikel — Vue.js SPA × CodeIgniter 4

**Laporan Praktikum 1-14 Pemrograman Web 2**

| 👤 Nama | 🎓 NIM | 📚 Mata Kuliah |
| --- | --- | --- |
| **Reynaldi Nugraha Putra** | **312410278** | **Pemrograman Web** |

---

## 📋 Daftar Isi

[🌐 Gambaran Umum](https://www.google.com/search?q=%23-gambaran-umum) •
[🖥️ Lab 8 Vue.js](https://www.google.com/search?q=%23%EF%B8%8F-lab-8--spa-frontend-vuejs) •
[🔥 Lab 11 CI4](https://www.google.com/search?q=%23-lab-11--backend-codeigniter-4) •
[📡 REST API](https://www.google.com/search?q=%23rest-api--dokumentasi-lengkap) •
[🔧 Troubleshooting](https://www.google.com/search?q=%23troubleshooting)

---

## 🌐 Gambaran Umum

> Proyek ini adalah aplikasi **Portal Artikel** yang dibangun menggunakan pendekatan **decoupled architecture** — frontend dan backend berjalan terpisah dan berkomunikasi lewat REST API[cite: 19].

```
╔══════════════════════════════════════════════════════════════════════╗
║                         ARSITEKTUR SISTEM                           ║
╠══════════════════════════════════════════════════════════════════════╣
║                                                                      ║
║   ┌─────────────────────────┐         ┌──────────────────────────┐  ║
║   │   🖥️  BROWSER (Client)   │         │    🖥️  SERVER (localhost)  │  ║
║   │                         │         │                          │  ║
║   │  ┌───────────────────┐  │  REST   │  ┌────────────────────┐ │  ║
║   │  │  LAB 8 — Vue.js   │  │  API    │  │ LAB 11 — CI4       │ │  ║
║   │  │                   │──┼─────────┼─▶│                    │ │  ║
║   │  │  /#/    → Home    │  │  JSON   │  │ Routes → Controller │ │  ║
║   │  │  /#/art → Artikel │◀─┼─────────┼──│ Controller → Model  │ │  ║
║   │  │                   │  │         │  │ Model → MySQL       │ │  ║
║   │  │  Vue Router 4     │  │         │  └────────────────────┘ │  ║
║   │  │  Axios            │  │         │                          │  ║
║   │  └───────────────────┘  │         │  ┌────────────────────┐ │  ║
║   │                         │         │  │  MySQL — lab_ci4   │ │  ║
║   └─────────────────────────┘         │  │  · artikel         │ │  ║
║                                       │  │  · kategori        │ │  ║
║                                       │  │  · user            │ │  ║
║                                       │  └────────────────────┘ │  ║
║                                       └──────────────────────────┘  ║
╚══════════════════════════════════════════════════════════════════════╝

```

|  | Lab 8 — Vue.js | Lab 11 — CodeIgniter 4 |
| --- | --- | --- |
| **Peran** | Frontend (Tampilan) | Backend (Logika & Data) |
| **Teknologi** | Vue 3 + Vue Router + Axios | PHP + CI4 + MySQL |
| **Akses** | `localhost/lab8_vuejs/` | `localhost/lab11_ci/ci4/public/` |
| **Output** | Antarmuka CRUD Artikel | REST API + Admin Panel |

---

# 🖥️ Lab 8 — SPA Frontend Vue.js

> 💡 Aplikasi **Single Page Application (SPA)** berbasis Vue.js 3 yang terhubung ke REST API CodeIgniter 4. Dibangun tanpa build tool — murni CDN, langsung jalan di browser[cite: 19].

### 💡 Apa itu SPA?

**SPA (Single Page Application)** adalah aplikasi web yang hanya memuat satu file HTML di awal, lalu semua perubahan konten dilakukan secara dinamis oleh JavaScript — tanpa perlu me-refresh atau berpindah halaman[cite: 19].

|  | 🌐 Web Tradisional | ⚡ SPA (Lab 8) |
| --- | --- | --- |
| Navigasi halaman | Browser reload penuh ke server | Komponen diganti, tidak reload |
| Data dari server | HTML siap saji | JSON mentah, dirender Vue |
| Kecepatan navigasi | Lambat (request baru tiap halaman) | Cepat (hanya ambil data JSON) |
| Contoh | Website biasa, PHP murni | Gmail, Facebook, Lab 8 ini |

### ✨ Fitur Lab 8

* 🏠 **Halaman Beranda** — Sambutan selamat datang di portal admin[cite: 19]
* 📰 **Manajemen Artikel** — Operasi CRUD lengkap: Tambah, Lihat, Edit, dan Hapus[cite: 19]
* 🔀 **Client-Side Routing** — Navigasi mulus tanpa reload menggunakan Vue Router 4[cite: 19]
* 📡 **Komunikasi REST API** — Kirim & terima data dari backend CI4 via Axios[cite: 19]
* 🪟 **Modal Form** — Form tambah dan edit artikel muncul sebagai popup[cite: 19]
* 🏷️ **Status Artikel** — Tandai artikel sebagai *Draft* atau *Publish*[cite: 19]
* ⚡ **Zero Build Tool** — Tidak perlu Node.js, npm, atau proses build apapun[cite: 19]

### 🛠️ Tech Stack Lab 8

| Teknologi | Versi | Fungsi |
| --- | --- | --- |
|  | 3.x via CDN | Framework utama untuk membuat komponen UI reaktif |
|  | 4.x via CDN | Mengatur navigasi antar halaman tanpa reload |
|  | Latest via CDN | Mengirim HTTP request ke REST API backend |
|  | — | Struktur halaman dan wadah mounting Vue |
|  | — | Styling tabel, modal, tombol, dan navigasi |

### 📁 Struktur Proyek Lab 8

```
📦 lab8_vuejs/
│
├── 📄 index.html               ← Satu-satunya halaman HTML (entry point SPA)
│
└── 📂 assets/
    ├── 📂 css/
    │   └── 🎨 style.css        ← Semua styling: layout, tabel, modal, tombol
    │
    └── 📂 js/
        ├── ⚙️  app.js           ← Inisialisasi Vue App + konfigurasi router
        │
        └── 📂 components/
            ├── 🏠 Home.js       ← Komponen halaman beranda
            └── 📰 Artikel.js    ← Komponen CRUD artikel (tabel + modal form)

```

### 🔍 Penjelasan File Lab 8

File ini adalah satu-satunya halaman HTML. Ia memuat semua library via CDN dan mendefinisikan elemen `<div id="app">` tempat Vue mengambil alih[cite: 19].

```html
<!-- Library dimuat via CDN — tidak perlu npm install -->
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script src="https://unpkg.com/vue-router@4/dist/vue-router.global.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>

<div id="app">
  <!-- router-link bukan <a href> biasa — mencegah reload ke server -->
  <nav>
    <router-link to="/">Beranda</router-link>
    <router-link to="/artikel">Kelola Artikel</router-link>
  </nav>

  <!-- Tempat komponen aktif dirender sesuai route -->
  <router-view></router-view>
</div>

```

```javascript
// URL base backend CI4 — sesuaikan jika lokasi berbeda
const apiUrl = 'http://localhost/lab11_ci/ci4/public';

// Definisi rute: URL → komponen yang ditampilkan
const routes = [
    { path: '/',        component: Home    },  // /#/
    { path: '/artikel', component: Artikel }   // /#/artikel
];

// Hash Mode: URL jadi /#/artikel
// Keuntungan: tidak perlu konfigurasi server khusus
const router = createRouter({
    history: createWebHashHistory(),
    routes
});

const app = createApp({});
app.use(router);
app.mount('#app');  // Vue mengambil alih elemen #app

```

> **Mengapa Hash Mode?** Agar bisa berjalan di web server biasa (Apache/XAMPP) tanpa konfigurasi `.htaccess` tambahan. Tanda `#` memastikan semua navigasi dikelola Vue di sisi browser[cite: 19].

Komponen terbesar. Berisi logika CRUD lengkap menggunakan Vue 3 Options API[cite: 19].

**State (data):**

```javascript
data() {
    return {
        artikel: [],        // Array berisi semua data artikel dari API
        showForm: false,    // Kontrol tampil/sembunyi modal form
        formTitle: '',      // "Tambah Data" atau "Ubah Data"
        formData: {         // Terikat ke input form via v-model
            id: null,
            judul: '',
            isi: '',
            status: 0
        },
        statusOptions: [
            { text: 'Draft',   value: 0 },
            { text: 'Publish', value: 1 }
        ]
    };
}

```

**Methods:**

| Method | Dipanggil Saat | Yang Dilakukan |
| --- | --- | --- |
| `loadData()` | Mount + setelah simpan/hapus | `GET /post` → isi array `artikel` |
| `tambah()` | Klik tombol "Tambah Data" | Reset form, buka modal |
| `edit(data)` | Klik "Edit" di tabel | Isi form dengan data baris, buka modal |
| `saveData()` | Submit form | Ada `id` → PUT, tidak ada → POST |
| `hapus(index, id)` | Klik "Hapus" di tabel | Konfirmasi → DELETE → hapus dari array |
| `statusText(status)` | Render tabel | Konversi `0/1` ke teks `Draft/Publish` |

### 🚀 Cara Menjalankan Lab 8

> **Prasyarat:** Web server lokal aktif (XAMPP/Laragon) dan backend Lab 11 sudah berjalan[cite: 19].

**Langkah 1** — Tempatkan folder di web server

```bash
# XAMPP
C:/xampp/htdocs/lab8_vuejs/

# Laragon
C:/laragon/www/lab8_vuejs/

```

**Langkah 2** — Pastikan URL API sesuai di `assets/js/app.js`

```javascript
const apiUrl = 'http://localhost/lab11_ci/ci4/public';
//              ↑ Ubah jika lokasi backend CI4 kamu berbeda

```

**Langkah 3** — Buka di browser

```
http://localhost/lab8_vuejs/

```

> ✅ **Tidak ada `npm install`, tidak ada build process.** Buka browser, langsung jalan!

### 🗺️ Routing & Endpoint Lab 8

**Routing SPA (Hash Mode):**

| Route | Komponen | Deskripsi |
| --- | --- | --- |
| `http://localhost/lab8_vuejs/#/` | `Home.js` | Halaman beranda |
| `http://localhost/lab8_vuejs/#/artikel` | `Artikel.js` | Manajemen artikel |

**Endpoint API yang Dikonsumsi:**

| Method | Endpoint | Aksi |
| --- | --- | --- |
| `GET` | `/post` | Ambil semua artikel → isi tabel |
| `POST` | `/post` | Tambah artikel baru |
| `PUT` | `/post/{id}` | Update artikel yang dipilih |
| `DELETE` | `/post/{id}` | Hapus artikel dari database |

### 🔄 Alur Kerja Lab 8

```
 Klik "Tambah Data"
        │
        ▼
 ┌─────────────────┐
 │  Modal Muncul   │  showForm = true, formData direset
 └────────┬────────┘
          │  User isi form → klik "Simpan"
          ▼
 ┌─────────────────┐
 │  saveData()     │
 └────────┬────────┘
          │
    ┌─────┴──────┐
    │            │
   Ada ID?     Tidak?
    │            │
    ▼            ▼
  PUT /post    POST /post
  (update)     (tambah baru)
    │            │
    └─────┬──────┘
          │  Response 200/201
          ▼
 ┌─────────────────┐
 │   loadData()    │  GET /post → refresh tabel otomatis
 └────────┬────────┘
          │
          ▼
   Modal tertutup ✅
   Tabel terupdate ✅

```

---

# 🔥 Lab 11 — Backend CodeIgniter 4

> 💡 Aplikasi web portal artikel berbasis **CodeIgniter 4** yang dilengkapi panel admin, autentikasi user, fitur AJAX, dan **REST API** siap dikonsumsi frontend Vue.js[cite: 19].

### 💡 Apa itu CodeIgniter 4?

CodeIgniter 4 adalah framework PHP yang menggunakan pola **MVC (Model-View-Controller)**[cite: 19]:

```
   HTTP Request
        │
        ▼
   ┌─────────┐
   │ Router  │  ← Cocokkan URL → controller
   └────┬────┘
        ▼
   ┌────────────┐
   │ Controller │  ← Terima request, panggil model, pilih view
   └──────┬─────┘
          │
     ┌────┴────┐
     ▼         ▼
 ┌───────┐  ┌──────┐
 │ Model │  │ View │
 └───┬───┘  └──────┘
     │  ← Komunikasi dengan MySQL
     ▼
  MySQL

```

### ✨ Fitur Lab 11

* 📰 **Portal Artikel Publik** — Siapa saja bisa membaca artikel tanpa login[cite: 19]
* 🔐 **Admin Panel Terproteksi** — Semua `/admin/*` dijaga filter autentikasi[cite: 19]
* 👤 **Sistem Login/Logout** — Autentikasi berbasis session + `password_hash()`[cite: 19]
* 🔍 **AJAX Search Real-time** — Cari artikel di admin tanpa reload halaman[cite: 19]
* 🏷️ **Filter Kategori** — Admin bisa filter artikel per kategori[cite: 19]
* 📄 **Pagination** — Daftar admin dibatasi 10 artikel per halaman[cite: 19]
* 🔌 **REST API Lengkap** — Endpoint `/post` untuk semua operasi CRUD[cite: 19]
* 🌱 **Database Seeder** — Data admin & user awal dibuat dengan satu perintah[cite: 19]

### 🛠️ Tech Stack Lab 11

| Teknologi | Versi | Fungsi |
| --- | --- | --- |
|  | 4.x | Framework MVC utama |
|  | ≥ 8.1 | Bahasa pemrograman server-side |
|  | 5.7 / 8.x | Database artikel, kategori, user |
|  | Latest | Dependency manager PHP |
|  | — | Web server + URL rewriting |

### 📁 Struktur Proyek Lab 11

```
📦 lab11_ci/ci4/
│
├── 📂 app/                         ← Kode aplikasi utama
│   │
│   ├── 📂 Config/
│   │   ├── ⚙️  Routes.php           ← Semua URL route didaftarkan di sini
│   │   ├── ⚙️  Filters.php          ← Daftarkan filter auth, CSRF, dll
│   │   └── ⚙️  Database.php         ← Konfigurasi koneksi MySQL
│   │
│   ├── 📂 Controllers/
│   │   ├── 🏠 Home.php              ← Halaman utama (/)
│   │   ├── 📄 Page.php              ← Halaman statis (about, contact, dll)
│   │   ├── 📰 Artikel.php           ← CRUD artikel + admin panel
│   │   ├── 👤 User.php              ← Login & logout
│   │   ├── 🔌 Post.php              ← REST API Controller (untuk Vue.js)
│   │   └── ⚡ AjaxController.php    ← Endpoint khusus AJAX
│   │
│   ├── 📂 Models/
│   │   ├── 📰 ArtikelModel.php      ← Query ke tabel `artikel`
│   │   ├── 🏷️  KategoriModel.php    ← Query ke tabel `kategori`
│   │   └── 👤 UserModel.php         ← Query ke tabel `user`
│   │
│   ├── 📂 Filters/
│   │   └── 🔐 Auth.php              ← Cek session sebelum masuk admin
│   │
│   ├── 📂 Views/
│   │   ├── 📂 artikel/
│   │   │   ├── index.php            ← Daftar artikel publik
│   │   │   ├── detail.php           ← Detail artikel publik
│   │   │   ├── admin_index.php      ← Admin: daftar + search + pagination
│   │   │   ├── form_add.php         ← Form tambah artikel
│   │   │   └── form_edit.php        ← Form edit artikel
│   │   ├── 📂 user/
│   │   │   └── login.php            ← Halaman form login
│   │   ├── 📂 layout/
│   │   │   └── main.php             ← Layout utama
│   │   └── 📂 template/
│   │       ├── header.php           ← Navigasi publik
│   │       ├── footer.php           ← Footer publik
│   │       ├── admin_header.php     ← Navigasi admin
│   │       └── admin_footer.php     ← Footer admin
│   │
│   └── 📂 Database/
│       └── 📂 Seeds/
│           └── 🌱 UserSeeder.php    ← Data admin & user awal
│
├── 📂 public/                      ← Web root (arahkan Apache ke sini)
│   ├── index.php                   ← Entry point semua HTTP request
│   └── .htaccess                   ← URL rewriting Apache
│
├── 📂 system/                      ← Core CI4 (jangan diubah)
├── 🔧 .env                         ← Konfigurasi environment
└── 📦 composer.json                ← Dependensi PHP

```

### 🧩 Penjelasan Komponen Utama

```php
class ArtikelModel extends Model
{
    protected $table      = 'artikel';   // nama tabel di MySQL
    protected $primaryKey = 'id';        // kolom primary key

    // Hanya kolom ini yang boleh diisi (proteksi mass assignment)
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
}

```

Dengan konfigurasi ini, controller bisa langsung menggunakan:

| Method | SQL yang Dijalankan |
| --- | --- |
| `$model->findAll()` | `SELECT * FROM artikel` |
| `$model->find($id)` | `SELECT * FROM artikel WHERE id = ?` |
| `$model->insert($data)` | `INSERT INTO artikel ...` |
| `$model->update($id, $data)` | `UPDATE artikel SET ... WHERE id = ?` |
| `$model->delete($id)` | `DELETE FROM artikel WHERE id = ?` |

`admin_index()` menangani search, filter, dan pagination AJAX[cite: 19]:

```php
public function admin_index()
{
    $q          = $this->request->getVar('q') ?? '';
    $kategori_id = $this->request->getVar('kategori_id') ?? '';

    $builder = $model->table('artikel')
        ->select('artikel.*, kategori.nama_kategori')
        ->join('kategori', 'kategori.id_kategori = artikel.id_kategori', 'left');

    if ($q != '')          $builder->like('artikel.judul', $q);
    if ($kategori_id != '') $builder->where('artikel.id_kategori', $kategori_id);

    $artikel = $builder->paginate(10);

    // Jika request AJAX → kirim JSON saja
    // Jika request biasa → render view HTML
    if ($this->request->isAJAX()) {
        return $this->response->setJSON($data);
    } else {
        return view('artikel/admin_index', $data);
    }
}

```

Di-extend dari `ResourceController` bawaan CI4. Satu class = 5 endpoint CRUD otomatis[cite: 19].

```php
class Post extends ResourceController
{
    use ResponseTrait;

    public function index()   { /* GET /post    → ambil semua */ }
    public function create()  { /* POST /post   → tambah baru */ }
    public function show($id) { /* GET /post/id → ambil satu  */ }
    public function update($id){ /* PUT /post/id → update     */ }
    public function delete($id){ /* DELETE /post/id → hapus   */ }
}

```

Didaftarkan cukup dengan satu baris di `Routes.php`:

```php
$routes->resource('post');  // CI4 otomatis buat 5 route

```

Dijalankan **sebelum** controller apapun di grup `/admin/*`[cite: 19]:

```php
public function before(RequestInterface $request, $arguments = null)
{
    // Jika belum login → tolak, paksa ke halaman login
    if (!session()->get('logged_in')) {
        return redirect()->to('/user/login');
    }
    // Jika sudah login → lanjut ke controller tujuan
}

```

Cara pendaftaran di `Routes.php`:

```php
// Semua route di dalam group ini wajib lewat filter 'auth' dulu
$routes->group('admin', ['filter' => 'auth'], function($routes) {
    $routes->get('artikel', 'Artikel::admin_index');
    $routes->get('artikel/add', 'Artikel::add');
    // dst...
});

```

### ⚙️ Instalasi & Konfigurasi

> **Prasyarat:** PHP ≥ 8.1, MySQL, Composer, Apache (XAMPP/Laragon)

**Step 1** — Install dependensi PHP

```bash
cd lab11_ci/ci4
composer install

```

**Step 2** — Buat database dan tabel di MySQL

```sql
CREATE DATABASE lab_ci4
    CHARACTER SET utf8mb4
    COLLATE utf8mb4_general_ci;

USE lab_ci4;

-- Tabel artikel: menyimpan konten artikel
CREATE TABLE artikel (
    id          INT(11)      AUTO_INCREMENT PRIMARY KEY,
    judul       VARCHAR(200) NOT NULL,
    isi         TEXT,
    gambar      VARCHAR(200),
    status      TINYINT(1)   DEFAULT 0,    -- 0 = Draft, 1 = Publish
    slug        VARCHAR(200),               -- versi URL dari judul
    id_kategori INT(11)
);

-- Tabel kategori: master kategori artikel
CREATE TABLE kategori (
    id_kategori   INT(11)      AUTO_INCREMENT PRIMARY KEY,
    nama_kategori VARCHAR(100) NOT NULL
);

-- Tabel user: akun admin & user
CREATE TABLE user (
    id           INT(11)      AUTO_INCREMENT PRIMARY KEY,
    username     VARCHAR(100) NOT NULL,
    useremail    VARCHAR(100) NOT NULL UNIQUE,
    userpassword VARCHAR(255) NOT NULL   -- disimpan dalam bentuk hash
);

```

**Step 3** — Konfigurasi file `.env`

```env
# Mode: development menampilkan error detail di browser
CI_ENVIRONMENT = development

# Koneksi MySQL
database.default.hostname = localhost
database.default.database = lab_ci4
database.default.username = root
database.default.password =           # kosong jika XAMPP default
database.default.DBDriver = MySQLi
database.default.port     = 3306

```

**Step 4** — Jalankan Seeder untuk data awal

```bash
php spark db:seed UserSeeder

```

**Step 5** — Akses aplikasi

```
http://localhost/lab11_ci/ci4/public/

```

### 🗺️ Routing Aplikasi

#### 🌐 Halaman Publik *(Tanpa Login)*

| Route | Method | Controller | Penjelasan |
| --- | --- | --- | --- |
| `/` | GET | `Home::index` | Halaman utama portal |
| `/artikel` | GET | `Artikel::index` | Daftar artikel publik |
| `/artikel/:slug` | GET | `Artikel::view` | Detail artikel |
| `/about` | GET | `Page::about` | Halaman tentang |
| `/contact` | GET | `Page::contact` | Halaman kontak |

#### 🔐 Admin Panel *(Wajib Login)*

| Route | Method | Controller | Penjelasan |
| --- | --- | --- | --- |
| `/admin/artikel` | GET | `Artikel::admin_index` | Daftar artikel + search + filter |
| `/admin/artikel/add` | GET | `Artikel::add` | Form tambah artikel |
| `/admin/artikel/add` | POST | `Artikel::add` | Simpan artikel baru |
| `/admin/artikel/edit/:id` | GET | `Artikel::edit` | Form edit artikel |
| `/admin/artikel/edit/:id` | POST | `Artikel::edit` | Update artikel |
| `/admin/artikel/delete/:id` | GET | `Artikel::delete` | Hapus artikel |

#### 👤 Autentikasi

| Route | Method | Controller | Penjelasan |
| --- | --- | --- | --- |
| `/user/login` | GET | `User::login` | Tampilkan form login |
| `/user/login` | POST | `User::login` | Proses validasi login |
| `/user/logout` | GET | `User::logout` | Logout & hapus session |

#### 🔌 REST API *(Dikonsumsi Lab 8)*

| Method | Endpoint | Controller | Penjelasan |
| --- | --- | --- | --- |
| `GET` | `/post` | `Post::index` | Ambil semua artikel → JSON |
| `POST` | `/post` | `Post::create` | Tambah artikel baru |
| `GET` | `/post/:id` | `Post::show` | Ambil satu artikel |
| `PUT` | `/post/:id` | `Post::update` | Update artikel |
| `DELETE` | `/post/:id` | `Post::delete` | Hapus artikel |

#### ⚡ AJAX Endpoints

| Route | Method | Controller | Penjelasan |
| --- | --- | --- | --- |
| `/ajax` | GET | `AjaxController::index` | Halaman demo AJAX |
| `/ajax/getData` | GET | `AjaxController::getData` | JSON semua artikel |
| `/artikel/delete/:id` | DELETE | `AjaxController::delete` | Hapus via AJAX |

### 👤 Akun Default

> Tersedia setelah `php spark db:seed UserSeeder`[cite: 19]

| 🧑 Username | 📧 Email | 🔑 Password | 🎭 Role |
| --- | --- | --- | --- |
| `admin` | `admin@email.com` | `admin123` | Administrator |
| `user` | `user@email.com` | `user123` | User biasa |

> ⚠️ **Catatan:** Password di database disimpan dalam bentuk **bcrypt hash** menggunakan `password_hash()` — bukan teks biasa[cite: 19]. Verifikasi saat login menggunakan `password_verify()`[cite: 19].

### 🔐 Sistem Autentikasi

```
  Buka /user/login
        │
        ▼
  ┌─────────────────────────┐
  │  Isi Email + Password   │
  │  → Klik Login           │
  └────────────┬────────────┘
               │  POST /user/login
               ▼
  ┌─────────────────────────┐
  │  Cari email di DB       │
  │  UserModel::where()     │
  └────────────┬────────────┘
               │
         ┌─────┴──────┐
       Ditemukan?   Tidak?
         │               └─→ Flash "Email tidak terdaftar"
         ▼                   Redirect ke /user/login ❌
  ┌─────────────────────────┐
  │  password_verify()      │
  │  (input vs hash di DB)  │
  └────────────┬────────────┘
               │
         ┌─────┴──────┐
        Cocok?      Tidak?
         │               └─→ Flash "Password salah"
         ▼                   Redirect ke /user/login ❌
  ┌─────────────────────────┐
  │  session()->set([       │
  │    'user_id'   => ...,  │
  │    'user_name' => ...,  │
  │    'logged_in' => true  │
  │  ])                     │
  └────────────┬────────────┘
               │
               ▼
        Redirect → /admin/artikel ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Saat akses /admin/*:

  Request → Filter Auth::before()
               │
         ┌─────┴──────┐
     logged_in?     Tidak?
         │               └─→ Redirect /user/login ❌
         ▼
  Lanjut ke Controller ✅
━━━━━━━━━━━━━━━━━━━━━━━━━━━

```

### 📡 REST API — Dokumentasi Lengkap

**Request:**

```http
GET http://localhost/lab11_ci/ci4/public/post

```

**Response `200 OK`:**

```json
{
  "artikel": [
    {
      "id": 3,
      "judul": "Judul Artikel Ketiga",
      "isi": "Isi artikel...",
      "status": "1",
      "slug": "judul-artikel-ketiga",
      "gambar": null
    },
    {
      "id": 2,
      "judul": "Judul Artikel Kedua",
      "isi": "Isi artikel kedua...",
      "status": "0",
      "slug": "judul-artikel-kedua",
      "gambar": null
    }
  ]
}

```

> Diurutkan dari ID terbesar ke terkecil (`ORDER BY id DESC`)[cite: 19]

**Request:**

```http
POST http://localhost/lab11_ci/ci4/public/post
Content-Type: application/x-www-form-urlencoded

judul=Judul Artikel Baru&isi=Isi artikel baru&status=1

```

**Response `201 Created`:**

```json
{
  "status": 201,
  "error": null,
  "messages": {
    "success": "Data artikel berhasil ditambahkan."
  }
}

```

**Request:**

```http
GET http://localhost/lab11_ci/ci4/public/post/1

```

**Response `200 OK`:**

```json
{
  "id": 1,
  "judul": "Judul Artikel Pertama",
  "isi": "Isi lengkap artikel...",
  "status": "1",
  "slug": "judul-artikel-pertama",
  "gambar": null
}

```

**Response `404 Not Found`:**

```json
{
  "status": 404,
  "error": 404,
  "messages": { "error": "Data tidak ditemukan." }
}

```

**Request:**

```http
PUT http://localhost/lab11_ci/ci4/public/post/1
Content-Type: application/x-www-form-urlencoded

id=1&judul=Judul Diperbarui&isi=Isi yang sudah diedit

```

**Response `200 OK`:**

```json
{
  "status": 200,
  "error": null,
  "messages": { "success": "Data artikel berhasil diubah." }
}

```

**Request:**

```http
DELETE http://localhost/lab11_ci/ci4/public/post/1

```

**Response `200 OK`:**

```json
{
  "status": 200,
  "error": null,
  "messages": { "success": "Data artikel berhasil dihapus." }
}

```

### ⚡ Fitur AJAX Admin Panel

Di halaman `/admin/artikel`, pencarian dan filter kategori bekerja **tanpa reload halaman**[cite: 19]:

```
 Ketik keyword di search box
        │
        ▼
 JavaScript tangkap event keyup
        │
        ▼
 fetch('/admin/artikel?q=keyword')
 + header 'X-Requested-With: XMLHttpRequest'
        │
        ▼
 Artikel::admin_index() menerima
        │
        ├── isAJAX() == true
        │       └── setJSON($data) → kirim JSON saja
        │
        └── Request biasa
                └── view('admin_index') → HTML penuh
        │
        ▼
 JavaScript update tabel dari JSON ✅
 (tanpa reload halaman)

```

### 🔧 Troubleshooting

Pastikan:

* XAMPP MySQL sudah aktif di XAMPP Control Panel
* Nama database di `.env` sudah benar: `lab_ci4`
* Username dan password MySQL sesuai (default XAMPP: user `root`, password kosong)

Pastikan:

* Backend CI4 sudah berjalan
* `apiUrl` di `app.js` sesuai dengan URL backend
* Tidak ada CORS error di browser console (klik kanan → Inspect → Console)

Pastikan seeder sudah dijalankan:

```bash
php spark db:seed UserSeeder

```

Password yang benar adalah `admin123`, bukan hash-nya.

Session mungkin tidak tersimpan. Periksa:

* Direktori `writable/session/` ada dan bisa ditulis (permission 755/777)
* File `.env` sudah dikonfigurasi dengan benar

---
