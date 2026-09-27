# Ringkasan Materi Penting Kuis 1 Jaringan Komputer

Ringkasan ini memprioritaskan konsep yang muncul pada kumpulan soal latihan. Fokus utama bukan menghafal huruf jawaban, tetapi memahami alasan teknis di baliknya.

## Prioritas belajar

1. **Model lima layer, enkapsulasi, dan fungsi perangkat:** paling sering muncul dan menjadi dasar soal lain.
2. **Delay, throughput, dan packet switching:** pahami definisi, penyebab, serta rumusnya.
3. **Arsitektur aplikasi dan kebutuhan layanan:** bedakan client-server, P2P, aplikasi elastis, dan real-time.
4. **FTP dan definisi protokol:** kuasai koneksi kontrol/data serta unsur sebuah protokol.
5. **Access network, ISP, wireless, traceroute, dan keamanan dasar:** konsep pendukung yang tetap berpotensi keluar.

## 1. Model lima layer Internet

| Layer | Fungsi utama | Contoh protokol/teknologi | Nama PDU |
|---|---|---|---|
| Application | Layanan jaringan untuk aplikasi | HTTP, FTP, DNS, SMTP | Message |
| Transport | Komunikasi antaraplikasi/proses | TCP, UDP | Segment (umum untuk TCP) |
| Network | Pengalamatan dan forwarding antarnetwork | IP, routing | Datagram |
| Link | Pengiriman pada satu link, framing, MAC | Ethernet, Wi-Fi | Frame |
| Physical | Mengirim bit sebagai sinyal | Kabel, fiber, radio | Bit |

### Enkapsulasi

Saat data bergerak dari pengirim menuju media:

```text
message → segment → datagram → frame → bit
```

Setiap layer menambahkan informasi kontrol berupa header; link layer tertentu juga dapat menambahkan trailer. Pada penerima terjadi proses kebalikannya, yaitu dekapsulasi.

Contoh penting:

- Transport layer menambahkan nomor port agar data dapat diarahkan ke aplikasi yang benar.
- Network layer membungkus segment dengan header IP sehingga menjadi datagram.
- Link layer membungkus datagram menjadi frame untuk dikirim pada satu link.

### Layer yang diproses perangkat

| Perangkat | Layer yang umumnya diproses | Alasan |
|---|---|---|
| Host | Kelima layer | Menjalankan aplikasi serta mengirim/menerima data end-to-end |
| Router | Physical, link, network | Menerima frame, memeriksa datagram, lalu meneruskannya ke link berikutnya |
| Link-layer switch | Physical dan link | Meneruskan frame berdasarkan informasi link layer seperti alamat MAC |

Inti yang perlu diingat: payload dari layer atas tidak harus dipahami oleh perangkat layer bawah. Switch dapat meneruskan frame tanpa memahami pesan aplikasi di dalamnya.

## 2. Protokol

Protokol menentukan tiga hal:

1. **Format** pesan.
2. **Urutan** pesan yang dipertukarkan.
3. **Tindakan** yang dilakukan ketika pesan dikirim atau diterima.

Dua pihak harus memakai protokol yang kompatibel. Jika format atau urutan ditafsirkan berbeda, komunikasi tidak akan berjalan benar meskipun koneksi fisiknya tersedia.

## 3. Delay dalam jaringan

Total nodal delay dapat ditulis sebagai:

```text
d_nodal = d_processing + d_queueing + d_transmission + d_propagation
```

### Processing delay

Waktu untuk memeriksa header, mendeteksi error, dan menentukan output link. Biasanya relatif kecil, tetapi bergantung pada perangkat.

### Queueing delay

Waktu tunggu paket di buffer sebelum dapat ditransmisikan. Terjadi karena output link mungkin sedang mengirim paket lain. Nilainya paling berubah-ubah karena bergantung pada kepadatan trafik.

Jika buffer penuh, paket baru dapat dibuang sehingga terjadi *packet loss*.

### Transmission delay

Waktu untuk memasukkan seluruh bit paket ke link:

```text
d_transmission = L / R
```

- `L` = panjang paket dalam bit.
- `R` = transmission rate link dalam bit/detik.

Transmission delay bergantung pada ukuran paket dan laju link, bukan pada panjang fisik link.

### Propagation delay

Waktu yang dibutuhkan sinyal untuk bergerak dari satu ujung link ke ujung lain:

```text
d_propagation = d / s
```

- `d` = panjang link.
- `s` = kecepatan propagasi sinyal pada media.

Propagation delay bergantung pada jarak dan media, bukan pada ukuran paket.

### Jebakan yang sering muncul

- **Transmission** = memasukkan bit ke link.
- **Propagation** = bit berjalan melintasi link.
- Analogi: transmission seperti waktu memasukkan seluruh rombongan mobil ke jalan; propagation seperti waktu perjalanan satu mobil menuju tujuan.

## 4. Throughput dan bottleneck

**Throughput** adalah laju aktual perpindahan bit dari pengirim ke penerima. Satuannya bit per detik.

- *Instantaneous throughput*: laju pada saat atau interval sangat pendek.
- *Average throughput*: rata-rata selama interval yang lebih panjang.
- Pada jalur tanpa trafik pesaing, throughput end-to-end dibatasi oleh link paling lambat atau *bottleneck*.

Untuk jalur dengan laju link `R1`, `R2`, ..., `Rn`, pendekatan sederhananya:

```text
throughput ≈ min(R1, R2, ..., Rn)
```

Throughput aktual juga dapat turun akibat trafik pengguna lain, antrean, retransmisi, dan overhead protokol.

## 5. Packet switching dan circuit switching

### Packet switching

- Data dipecah menjadi paket.
- Sumber daya link dipakai bersama secara dinamis.
- Efisien untuk trafik yang muncul tidak terus-menerus.
- Dapat mengalami queueing delay dan packet loss saat padat.

### Circuit switching

- Sumber daya dicadangkan selama sesi.
- Performa lebih stabil dan dapat diprediksi.
- Kapasitas yang telah dicadangkan dapat menganggur ketika sesi tidak mengirim data.

Kunci perbandingan: **packet switching unggul dalam efisiensi berbagi sumber daya; circuit switching unggul dalam jaminan sumber daya yang lebih dapat diprediksi.**

## 6. Kebutuhan layanan aplikasi

Aplikasi dapat dinilai berdasarkan:

- **Reliability/data integrity**: apakah kehilangan data dapat diterima?
- **Throughput**: apakah ada laju minimum yang dibutuhkan?
- **Timing**: seberapa sensitif terhadap delay dan jitter?
- **Security**: apakah membutuhkan kerahasiaan, integritas, dan autentikasi?

### Real-time vs elastic

| Jenis aplikasi | Karakteristik |
|---|---|
| Real-time interaktif, misalnya telepon Internet | Sangat sensitif terhadap delay; kadang dapat mentoleransi sedikit loss |
| Elastic, misalnya transfer file atau unduhan | Dapat memakai throughput yang tersedia; throughput rendah membuat transfer lebih lama |

Untuk suara interaktif, paket yang terlambat sering tidak lagi berguna. Karena itu, menghindari delay besar dapat lebih penting daripada menjamin setiap paket tiba.

## 7. Arsitektur aplikasi

### Client-server

- Server menyediakan layanan dan biasanya selalu aktif.
- Client mengirim permintaan kepada server.
- Layanan skala besar memakai data center karena satu host server dapat tidak cukup kuat.
- Data center mendukung pembagian beban, redundansi, dan skalabilitas.

### Peer-to-peer (P2P)

- Peer dapat meminta sekaligus menyediakan data.
- File dapat dibagi menjadi chunk dan diambil dari banyak peer.
- Kapasitas sistem dapat bertambah ketika peer baru ikut menyediakan sumber daya.
- Kehadiran server awal atau tracker tidak otomatis membuat arsitektur menjadi *strict client-server*.

## 8. FTP: control connection dan data connection

FTP menggunakan koneksi terpisah:

- **Control connection** membawa perintah dan respons, misalnya login atau `LIST`.
- **Data connection** membawa isi file atau directory listing.

Karena kontrol dan data melewati koneksi berbeda, FTP disebut memakai **out-of-band control**.

Jebakan soal: perintah `LIST` diterima melalui control connection, tetapi isi directory listing dikirim melalui data connection yang terpisah.

## 9. Access network dan media

### Cable Internet/HFC

Jaringan kabel disebut *shared access* karena beberapa rumah berbagi bagian infrastruktur HFC yang sama. Throughput yang dirasakan satu pelanggan dapat dipengaruhi aktivitas pelanggan lain pada segmen tersebut.

### Wireless

Propagasi radio dipengaruhi oleh:

- refleksi;
- penghalang dan pelemahan;
- interferensi;
- multipath.

Faktor-faktor tersebut dapat menyebabkan sinyal melemah, berubah, atau tiba melalui beberapa lintasan.

## 10. Internet sebagai network of networks

Internet tersusun dari banyak ISP yang dikelola secara independen. ISP perlu saling terhubung melalui peering, transit, dan titik pertukaran agar host pada jaringan berbeda dapat berkomunikasi.

Intinya: tanpa interkoneksi antar-ISP, pelanggan hanya dapat mencapai host dalam jaringan ISP-nya sendiri.

## 11. Traceroute

`traceroute` memperlihatkan hop yang dilewati paket menuju tujuan. Beberapa angka waktu pada satu hop berasal dari beberapa paket probe dan menunjukkan *round-trip time* masing-masing probe.

Nilai yang berbeda pada hop yang sama wajar karena queueing delay dan kondisi jaringan berubah dari waktu ke waktu.

## 12. Keamanan dasar: virus dan worm

- **Virus** biasanya melekat pada file atau program lain dan sering memerlukan tindakan pengguna agar aktif atau menyebar.
- **Worm** adalah program mandiri yang dapat mereplikasi serta menyebar melalui jaringan tanpa tindakan pengguna secara eksplisit.

Keduanya dapat berbahaya; perbedaannya terutama terletak pada cara bergantung pada host dan cara penyebarannya.

## 13. Peran Web dalam pertumbuhan Internet

Pada 1990-an, Web membuat informasi dan layanan Internet jauh lebih mudah diakses melalui browser dan hyperlink. Hal ini mendorong munculnya berbagai aplikasi, konten, dan layanan komersial serta memperluas penggunaan Internet.

## Checklist sebelum kuis

Pastikan Anda dapat menjawab tanpa melihat catatan:

- [ ] Menuliskan lima layer dan fungsi utamanya.
- [ ] Menuliskan urutan `message → segment → datagram → frame → bit`.
- [ ] Menjelaskan mengapa host, router, dan switch memproses layer yang berbeda.
- [ ] Membedakan `L/R` dari `d/s`.
- [ ] Menjelaskan penyebab queueing delay dan packet loss.
- [ ] Mendefinisikan throughput, average throughput, dan bottleneck.
- [ ] Membandingkan packet switching dengan circuit switching.
- [ ] Membedakan client-server dengan P2P.
- [ ] Menjelaskan kebutuhan aplikasi real-time dan elastic.
- [ ] Menjelaskan mengapa FTP control disebut out-of-band.
- [ ] Menjelaskan shared access pada jaringan kabel.
- [ ] Menafsirkan beberapa nilai delay pada satu hop traceroute.
- [ ] Membedakan virus dengan worm.

## Strategi menjawab pilihan ganda

1. Cari kata absolut seperti **selalu**, **hanya**, **nol**, atau **tidak pernah**. Pada konsep jaringan, klaim absolut sering menjadi pengecoh.
2. Cocokkan istilah dengan layer yang tepat. Port berada di transport layer, IP di network layer, dan MAC/frame di link layer.
3. Untuk soal delay, tanyakan: apakah yang berubah adalah ukuran paket/laju link atau jarak/kecepatan sinyal?
4. Untuk soal arsitektur, lihat perilaku host. Jika host menerima sekaligus menyediakan konten, itu ciri P2P.
5. Jangan menghafal huruf jawaban karena urutan opsi dapat diacak; hafalkan alasannya.
