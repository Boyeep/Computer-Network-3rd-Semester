# Latihan Kuis 1 Jaringan Komputer

Dokumen ini disusun dari 30 foto soal di folder `Practice-Images`. Kerjakan pertanyaan pada gambar terlebih dahulu, lalu buka bagian **Jawaban dan penjelasan** untuk memeriksa hasilnya.

> Catatan: soal 17–18, 20–24, dan 25–27 memuat tiga pasang soal yang sama dengan urutan pilihan berbeda. Semuanya tetap dicantumkan agar setiap foto memiliki referensi.

## 1. Header pada transport layer

![Soal tentang header transport layer](Practice-Images/01-transport-layer-header.jpeg)

Mengapa transport layer menambahkan header sebelum meneruskan data ke network layer?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: e.** Header transport membawa informasi yang dibutuhkan penerima, terutama nomor port untuk mengarahkan data ke proses/aplikasi yang tepat. Pada TCP, header juga dapat mendukung penomoran urut, acknowledgment, kontrol aliran, dan deteksi kesalahan melalui checksum.

</details>

## 2. Instantaneous throughput dan average throughput

![Soal instantaneous dan average throughput](Practice-Images/02-instantaneous-vs-average-throughput.jpeg)

Apa yang membedakan *instantaneous throughput* dari *average throughput*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** *Instantaneous throughput* adalah laju transfer pada suatu saat atau interval yang sangat pendek, sedangkan *average throughput* adalah rata-rata laju transfer selama interval yang lebih panjang.

</details>

## 3. Kebutuhan layanan Internet telephony

![Soal kebutuhan layanan Internet telephony](Practice-Images/03-internet-telephony-service-requirements.jpeg)

Layanan apa yang paling sesuai untuk aplikasi telepon Internet yang membutuhkan delay rendah tetapi masih dapat mentoleransi sebagian *loss*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: c.** Komunikasi suara interaktif lebih mengutamakan ketepatan waktu dan delay rendah. Sebagian kecil paket yang hilang sering lebih dapat ditoleransi daripada retransmisi yang datang terlambat dan mengganggu percakapan.

</details>

## 4. Urutan PDU saat enkapsulasi

![Soal urutan PDU ketika data turun melalui protocol stack](Practice-Images/04-urutan-pdu-enkapsulasi.jpeg)

Apa urutan nama unit data ketika informasi bergerak turun dari application layer ke link layer?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: e.** Urutannya adalah *message* → *segment* → *datagram* → *frame*. Application layer menghasilkan *message*. Transport layer membungkusnya sebagai *segment*, network layer sebagai *datagram*, dan link layer sebagai *frame*.

</details>

## 5. Layer pada host, router, dan switch

![Soal implementasi layer pada host router dan switch](Practice-Images/05-layer-host-router-switch.jpeg)

Mengapa host mengimplementasikan kelima layer, sedangkan router dan link-layer switch mengimplementasikan lebih sedikit layer?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Host menghasilkan dan memakai data aplikasi sehingga membutuhkan seluruh stack. Perangkat perantara umumnya hanya memproses layer yang diperlukan untuk meneruskan data: router sampai network layer, sedangkan switch terutama link dan physical layer.

</details>

## 6. Distribusi file berbasis chunk

![Soal P2P pada distribusi chunk file](Practice-Images/06-p2p-distribusi-chunk.jpeg)

Host A mengunduh chunk dari server dan host lain, lalu mengunggah chunk yang telah dimiliki kepada host lain. Arsitektur apa yang paling tepat?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: f, yaitu P2P.** Pada arsitektur *peer-to-peer*, host peserta dapat bertindak sebagai penerima sekaligus penyedia konten. Keberadaan server awal tidak membuat sistem tersebut menjadi *strict client-server*.

</details>

## 7. P2P file sharing

![Soal arsitektur P2P file sharing](Practice-Images/07-arsitektur-p2p-file-sharing.jpeg)

Aplikasi mengunduh chunk dari suatu peer dan mengunggah chunk kepada peer lain. Arsitektur apa yang digambarkan?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: a, yaitu P2P architecture.** Setiap peer dapat meminta sekaligus menyediakan data; tidak seluruh pertukaran harus melalui satu server pusat.

</details>

## 8. Apa yang ditentukan oleh protokol?

![Soal protokol dan urutan pertukaran message](Practice-Images/08-definisi-protokol-urutan-message.jpeg)

Browser mengirim *connection request*, menunggu respons, lalu mengirim permintaan Web. Sifat protokol apa yang ditunjukkan?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Protokol menentukan format dan urutan pesan yang dipertukarkan, serta tindakan yang dilakukan ketika suatu pesan dikirim atau diterima.

</details>

## 9. Kompatibilitas protokol

![Soal alasan protokol harus kompatibel](Practice-Images/09-kompatibilitas-protokol.jpeg)

Mengapa dua entitas yang berkomunikasi harus menerapkan protokol yang kompatibel?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: a.** Tanpa aturan yang sama, kedua pihak dapat menafsirkan format pesan, urutan pesan, dan tindakan yang diharapkan secara berbeda sehingga komunikasi gagal.

</details>

## 10. Perbedaan nama PDU antarlayer

![Soal penamaan PDU pada tiap layer](Practice-Images/10-penamaan-pdu-tiap-layer.jpeg)

Mengapa data yang sama disebut *message*, *segment*, *datagram*, dan *frame* pada titik yang berbeda di protocol stack?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: b.** Setiap layer melihat data beserta informasi kontrol yang relevan bagi layer tersebut. Penambahan header pada proses enkapsulasi menghasilkan PDU yang berbeda pada setiap layer.

</details>

## 11. Queueing delay

![Soal queueing delay pada output link](Practice-Images/11-queueing-delay-output-link.jpeg)

Mengapa sebuah paket dapat mengalami *queueing delay* pada suatu output link?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: c.** Jika output link sedang mentransmisikan paket lain, paket yang baru tiba harus menunggu di buffer. Delay ini berubah-ubah mengikuti pola kedatangan trafik dan tingkat kesibukan link.

</details>

## 12. Keuntungan circuit switching

![Soal keuntungan circuit switching](Practice-Images/12-keuntungan-circuit-switching.jpeg)

Apa keuntungan utama *circuit switching* dibandingkan *packet switching*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: a.** Sumber daya dicadangkan untuk satu sesi sehingga kapasitas dan performanya lebih dapat diprediksi. Konsekuensinya, sumber daya yang sedang tidak dipakai oleh sesi tersebut tidak mudah dimanfaatkan pengguna lain.

</details>

## 13. Peran Web pada 1990-an

![Soal peran Web bagi pertumbuhan Internet](Practice-Images/13-peran-web-1990-an.jpeg)

Mengapa Web penting bagi pertumbuhan Internet pada 1990-an?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: a.** Web menyediakan antarmuka dan platform yang mudah diakses untuk informasi, aplikasi, dan layanan komersial sehingga Internet menarik bagi masyarakat luas, bukan hanya komunitas riset.

</details>

## 14. Transmission delay dan propagation delay

![Soal perbedaan transmission dan propagation delay](Practice-Images/14-transmission-vs-propagation-delay.jpeg)

Apa perbedaan utama *transmission delay* dan *propagation delay*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: b.** *Transmission delay* adalah waktu untuk memasukkan seluruh bit paket ke link, yaitu `L/R`. *Propagation delay* adalah waktu perjalanan sinyal melintasi link, yaitu `d/s`.

</details>

## 15. Propagasi radio

![Soal faktor yang memengaruhi propagasi radio](Practice-Images/15-faktor-propagasi-radio.jpeg)

Sifat apa yang paling langsung memengaruhi propagasi radio?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Refleksi, penghalang, dan interferensi memengaruhi kekuatan dan kualitas sinyal radio. Dampaknya dapat berupa pelemahan, multipath, dan error transmisi.

</details>

## 16. Cable Internet sebagai shared access network

![Soal cable Internet sebagai shared access network](Practice-Images/16-cable-network-shared-access.jpeg)

Mengapa Internet kabel disebut sebagai *shared access network*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: e.** Beberapa rumah menggunakan bagian infrastruktur HFC (*hybrid fiber-coaxial*) yang sama. Karena kapasitas segmen dibagi, trafik pelanggan lain dapat memengaruhi throughput yang dirasakan.

</details>

## 17. FTP control bersifat out-of-band (varian A)

![Soal FTP out-of-band varian A](Practice-Images/17-ftp-control-out-of-band-varian-a.jpeg)

Mengapa kontrol FTP disebut *out-of-band*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: b.** Perintah dan respons kontrol menggunakan koneksi yang terpisah dari koneksi data untuk pemindahan file atau directory listing. Pemisahan dua koneksi inilah yang disebut *out-of-band control*.

</details>

## 18. FTP control bersifat out-of-band (varian B)

![Soal FTP out-of-band varian B](Practice-Images/18-ftp-control-out-of-band-varian-b.jpeg)

Soal ini sama dengan nomor 17, tetapi urutan pilihannya berbeda.

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: c.** Informasi kontrol FTP menggunakan koneksi yang terpisah dari koneksi data. Jawabannya berbeda huruf dari nomor 17 hanya karena urutan pilihan diacak.

</details>

## 19. Definisi throughput

![Soal definisi throughput](Practice-Images/19-definisi-throughput.jpeg)

Apa yang dimaksud dengan *throughput*?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: c.** Throughput adalah laju aktual perpindahan bit antara pengirim dan penerima, biasanya dinyatakan dalam bit per detik. Nilainya dapat lebih kecil daripada kapasitas nominal link akibat bottleneck, trafik bersama, dan overhead.

</details>

## 20. FTP LIST dan data connection (varian A)

![Soal FTP LIST varian A](Practice-Images/20-ftp-list-data-connection-varian-a.jpeg)

Setelah menerima perintah FTP `LIST` pada control connection, melalui koneksi mana server mengirim directory listing?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Directory listing dikirim melalui koneksi data yang terpisah, bukan sebagai isi langsung pada control connection.

</details>

## 21. Enkapsulasi segment menjadi datagram

![Soal enkapsulasi segment pada network layer](Practice-Images/21-enkapsulasi-segment-ke-datagram.jpeg)

Apa yang umumnya terjadi ketika transport-layer segment diberikan kepada network layer?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: b.** Network layer menambahkan header miliknya, termasuk informasi pengalamatan dan kontrol IP, sehingga terbentuk network-layer datagram.

</details>

## 22. Beberapa nilai delay pada traceroute

![Soal arti beberapa nilai delay pada traceroute](Practice-Images/22-traceroute-beberapa-delay-satu-hop.jpeg)

Apa arti beberapa nilai delay yang ditampilkan untuk satu hop pada `traceroute`?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: a.** Nilai tersebut merupakan hasil pengukuran *round-trip time* dari beberapa paket probe ke hop yang sama. Perbedaan nilainya menunjukkan variasi delay jaringan.

</details>

## 23. Virus dan worm

![Soal perbedaan virus dan worm](Practice-Images/23-perbedaan-virus-dan-worm.jpeg)

Apa perbedaan utama antara virus dan worm?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Virus umumnya melekat pada file/program dan sering memerlukan tindakan pengguna untuk aktif atau menyebar. Worm dapat mereplikasi dan menyebar melalui jaringan tanpa interaksi pengguna secara eksplisit.

</details>

## 24. FTP LIST dan data connection (varian B)

![Soal FTP LIST varian B](Practice-Images/24-ftp-list-data-connection-varian-b.jpeg)

Soal ini sama dengan nomor 20, tetapi urutan pilihannya berbeda.

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: e.** Server mengirim directory listing melalui koneksi data terpisah. Huruf jawabannya berbeda dari nomor 20 karena pilihan telah diacak.

</details>

## 25. Elastic application (varian A)

![Soal elastic application varian A](Practice-Images/25-elastic-application-throughput-varian-a.jpeg)

Mengapa *elastic application* dapat mentoleransi throughput yang berubah-ubah?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Aplikasi elastis dapat memanfaatkan throughput yang tersedia dan biasanya tidak membutuhkan laju minimum yang tetap. Throughput yang lebih rendah terutama membuat penyelesaian transfer lebih lama.

</details>

## 26. Switch dan application-layer message

![Soal switch memproses link layer](Practice-Images/26-switch-memproses-link-layer.jpeg)

Mengapa link-layer switch dapat meneruskan frame tanpa memahami application-layer message di dalamnya?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Switch memproses informasi link layer yang diperlukan untuk forwarding, misalnya alamat MAC. Payload dari layer lebih tinggi dibawa di dalam frame tanpa harus ditafsirkan oleh switch.

</details>

## 27. Elastic application (varian B)

![Soal elastic application varian B](Practice-Images/27-elastic-application-throughput-varian-b.jpeg)

Soal ini sama dengan nomor 25, tetapi urutan pilihannya berbeda.

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: f.** Aplikasi dapat memakai throughput yang tersedia tanpa membutuhkan *fixed minimum rate*. Huruf jawabannya berbeda dari nomor 25 karena urutan pilihan diacak.

</details>

## 28. Interkoneksi antar-ISP

![Soal alasan ISP saling terhubung](Practice-Images/28-interkoneksi-antar-isp.jpeg)

Mengapa ISP yang dikelola secara independen harus saling terhubung?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: e.** Interkoneksi membuat host yang tersambung melalui ISP berbeda dapat saling berkomunikasi. Internet pada dasarnya adalah *network of networks*.

</details>

## 29. Data center untuk client-server skala besar

![Soal data center pada layanan client-server](Practice-Images/29-data-center-client-server.jpeg)

Mengapa layanan client-server berskala besar lazim menggunakan data center besar?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: d.** Satu server mungkin tidak mampu menangani volume permintaan yang besar. Sekumpulan server di data center memungkinkan pembagian beban, skalabilitas, redundansi, dan ketersediaan yang lebih baik.

</details>

## 30. Layer yang diproses router

![Soal layer yang diproses router ketika forwarding](Practice-Images/30-layer-yang-diproses-router.jpeg)

Router menerima frame dari satu link dan meneruskan informasinya ke link lain. Interpretasi mana yang sesuai dengan model berlapis?

<details>
<summary><strong>Jawaban dan penjelasan</strong></summary>

**Jawaban: c.** Router memproses link layer untuk menerima dan membentuk frame pada tiap link, serta network layer untuk menentukan forwarding datagram. Router biasa tidak perlu menjalankan application layer milik paket yang diteruskan.

</details>

## Rekap kunci jawaban

| No. | Kunci | Topik singkat |
|---:|:---:|---|
| 1 | e | Header transport |
| 2 | d | Instantaneous vs average throughput |
| 3 | c | Kebutuhan telepon Internet |
| 4 | e | Urutan PDU |
| 5 | d | Layer pada perangkat |
| 6 | f | P2P berbasis chunk |
| 7 | a | Arsitektur P2P |
| 8 | d | Definisi protokol |
| 9 | a | Kompatibilitas protokol |
| 10 | b | PDU antarlayer |
| 11 | c | Queueing delay |
| 12 | a | Circuit switching |
| 13 | a | Pertumbuhan Web |
| 14 | b | Transmission vs propagation |
| 15 | d | Propagasi radio |
| 16 | e | Shared cable access |
| 17 | b | FTP out-of-band A |
| 18 | c | FTP out-of-band B |
| 19 | c | Throughput |
| 20 | d | FTP LIST A |
| 21 | b | Segment ke datagram |
| 22 | a | Traceroute |
| 23 | d | Virus vs worm |
| 24 | e | FTP LIST B |
| 25 | d | Elastic application A |
| 26 | d | Link-layer switch |
| 27 | f | Elastic application B |
| 28 | e | Interkoneksi ISP |
| 29 | d | Data center |
| 30 | c | Forwarding oleh router |
