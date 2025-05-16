# Planet Adventure! - Tutorial 8: Game Polishing & Balancing
Tutorial ini merupakan lanjutan dari **Tutorial 6**

---

## 🎮 Fitur yang Ditambahkan

###  Membuat Partikel Hujan & Salju

Saya menambahkan node `GPUParticles2D` pada **Level1** (hujan) dan **Level2** (salju), kemudian membuat *ParticlesMaterial* baru melalui tab **Process Material** di Inspector.

Beberapa penyesuaian yang dilakukan:

- **Display / Scale**: Mengatur *Scale Max* menjadi `10`.
- **Spawn / Position**: Mengubah *Emission Shape* menjadi `Box`, dengan nilai *Emission Box Extents (x)* menyesuaikan lebar area level.
- **Display / Color Curves**: Mengubah warna partikel menjadi **biru** (hujan) dan **putih** (salju).
- **Velocity / Spread**: Diatur menjadi `20` agar penyebaran partikel tidak terlalu melebar.
- **Acceleration / Gravity**: Menambahkan efek gravitasi ke arah kiri bawah dengan mengatur *Gravity X* dan *Gravity Y*.
- **Drawing / Visibility Rect**: Disesuaikan dengan area level agar partikel tetap terlihat saat pemain bergerak.
- **Trail**: *Enabled* diatur menjadi `true` agar partikel memiliki efek ekor.

###  Membuat Partikel Jejak Kaki

Partikel ini ditambahkan agar muncul saat pemain berjalan di lantai, memberikan kesan jejak yang dinamis.

Langkah-langkah:

- Menggunakan `GPUParticles2D` seperti sebelumnya, namun kali ini memakai *texture* dari folder `assets`.
- **Amount**: Diatur menjadi `4`.
- **Lifetime**: Diatur menjadi `0.5`.
- **Gravity (Y)**: Diubah menjadi `200` agar partikel bergerak ke atas.
- **Spawn / Velocity**:
    - *Spread*: Diatur ke `180°` untuk sebaran ke segala arah.
    - *Initial Velocity*: Diatur ke `50`.
- **Spawn / Position / Emission Shape**: Menggunakan `Box` dengan *extent X* `30`.
- **Transform**: Posisi partikel digeser ke bawah agar berada di kaki player (`Y = 30`).
- Ditambahkan logika dalam script agar partikel hanya muncul saat player berjalan di lantai.

###  Game Balancing

Untuk memastikan game tetap seru dan menantang, saya melakukan penyesuaian sebagai berikut:

- Mengatur *spawn rate* musuh (tikus) menjadi **setiap 2 detik**.
- Menambahkan **spawner tikus** pada **Level1** dan **Level2** untuk menjaga konsistensi tantangan di tiap level.
