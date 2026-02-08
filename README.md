Nama    : Ronald Saut Manurung
NIM     : 2481022
Prodi   : Teknik Informatika

Eksperimen 1 <br>
- Cookies: masih ada
- LocalStorage: masih ada
- SessionStorage: hilang

Eksperimen 2 <br>
Nilai counter di tab baru: 0 <br>
Setelah increment 3 kali di tab baru, nilai counter nya menjadi 3 <br>
Nilai counter di tab lama: 5 <br>
Kesimpulan: SessionStorage adalah tab-isolated <br>

Eksperimen 3 <br>
- Cookies: 4 KB
- LocalStorage: 5 - 10 MB
- SessionStorage: 5 - 10 MB <br>
Sejujurnya tidak bisa melihat quota masing-masing storage di DevTools-nya <br>
![alt text](https://github.com/ronalsm1/Storage-Lab-Handson-3-TI-WEB2/blob/main/screenshots/eksperimen3(b)%5Bcomparison-storagesize%5D.png?raw=true)
<br>
Eksperimen 4 <br>
Skenario 1 jawabannya LocalStorage. Alasannya, karena LocalStorage bersifat permanen, tidak memiliki waktu kadaluarsa, sehingga pilihan user tidak akan hilang meskipun browser ditutup total dan dibuka kembali di lain waktu. User tidak perlu mengatur ulang tema setiap kali berkunjung. <br>

Skenario 2 jawabannya SessionStorage. Alasannya, karena SessionStorage memiliki fitur isolasi tab, sehingga data pengisian formulir di satu tab tidak akan menimpa data di tab lain, dan sampah data otomatis terhapus saat tab ditutup demi privasi. <br>

Skenario 3 jawabannya Cookies (HttpOnly). Alasannya, karena Cookies (HttpOnly) dirancang khusus agar tidak dapat dibaca atau diakses oleh JavaScript, sehingga token login user jauh lebih aman dari risiko pencurian data melalui serangan XSS. <br>

Skenario 4 jawabannya LocalStorage. Alasannya, karena LocalStorage mampu menyimpan data di browser dalam jangka waktu lama, sehingga daftar belanjaan user tetap aman tersimpan meskipun user tidak sengaja menutup browser atau meninggalkan website berhari-hari sebelum checkout. <br>

**Pertanyaan Refleksi** <br>
1. **Mengapa session token TIDAK boleh disimpan di LocalStorage?**
Jawaban: Karena LocalStorage itu mudah diakses oleh JavaScript. Risikonya, kalau website terkena celah XSS, hacker bisa dengan mudah menyisipkan script buat curi token tersebut atau mengirimnya ke server mereka. Makanya lebih aman pakai Cookie dengan flag HttpOnly, karena fitur ini memblokir akses JavaScript sepenuhnya, jadi token nggak bakal bisa dicuri walaupun ada serangan XSS.
2. **Apa keuntungan SessionStorage untuk multi-step form dibanding LocalStorage?**
Jawaban: Keunggulan utamanya ada di isolasi data per tab. Bayangkan kalau user buka dua tab sekaligus buat ngisi form pendaftaran yang sama (misalnya satu buat dia, satu buat adiknya). Kalau pakai SessionStorage, data tiap tab dipisah total, jadi user bisa ngisi dua form barengan tanpa takut datanya bentrok atau saling timpa.
3. **Jika kamu membuat aplikasi todo list offline-first, storage mana yang akan kamu gunakan dan mengapa?**
Jawaban: Aku akan menggunakan LocalStorage, karena data todo harus tetap awet tersimpan walaupun user menutup aplikasinya dan baru membukanya lagi besok. Data todo nggak perlu dikirim bolak-balik ke server tiap kali refresh aplikasi. LocalStorage punya ruang yang jauh lebih lega buat nampung data todo.

Bonus: Kapan menggunakan masing-masing storage type <br>
Memilih penyimpanan di sisi client itu bergantung pada tiga faktor: seberapa lama data disimpan, lingkupnya, dan keamanannya. Pertama, gunakan LocalStorage kalau datanya ingin disimpan permanen tapi bukan data sensitif, seperti pilihan tema atau isi keranjang belanja. Kedua, pilih SessionStorage untuk data yang sifatnya sementara, terbilang sensitif, dan khusus untuk satu tab saja, misalnya saat mengisi formulir bertahap agar datanya tidak bentrok antar tab. Terakhir, khusus untuk token login, harus menggunakan Cookies (HttpOnly). Alasannya, karena Cookies paling aman dari akses skrip jahat atau JavaScript dan otomatis dikirim ke server setiap kali kita melakukan request.
