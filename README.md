# Final Project 
### Teknologi Komputasi Awan

**Kelas A**

**Kelompok 3**
|Nama|NRP  |
|--|--|
|Fazrul Ahmad Fadhilah|5027221025|
|Iki Adfi Nur Mohamad|5027221033|
|Jacinta Syilloam|5027221036|
|Muhammad Harvian Dito Syahputra|5027221039|
|Ilhan Ahmad Syafa|5027221040|

## Permasalahan
Anda adalah seorang lulusan Teknologi Informasi, sebagai ahli IT, salah satu kemampuan yang harus dimiliki adalah Kemampuan merancang, membangun, mengelola aplikasi berbasis komputer menggunakan layanan awan untuk memenuhi kebutuhan organisasi.(menurut kurikulum IT ITS 2023 😙)

Pada suatu saat teman anda ingin mengajak anda memulai bisnis di bidang digital marketing, anda diberikan sebuah aplikasi berbasis API File: app.py dengan spesifikasi sebagai berikut.

Kemudian anda diminta untuk mendesain arsitektur cloud yang sesuai dengan kebutuhan aplikasi tersebut. Apabila dana maksimal yang diberikan adalah 1 juta rupiah per bulan (65 US$) konfigurasi cloud terbaik seperti apa yang bisa dibuat?

## Rancangan Arsitektur dan Tabel Harga Spesifikasi VM
Setelah melakukan berbagai pertimbangan dari segi harga hingga spesifikasi. Akhirnya kami memutuskan untuk menggunakan Digital Ocean sebagai lingkungan cloud yang akan kami gunakan. Pertimbangan ini diambil karena Digital Ocean memiliki harga yang lebih terjangkau dengan spesifikasi yang lebih tinggi dan tentunya tidak terlalu membebani device kami dibandingkan kedua opsi lainnya yaitu VM yang berat untuk device kami dan Azure yang lebih tinggi harganya.

- Berikut adalah rancangan arsitektur yang telah kami buat untuk final project kami
![arsitektur](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/936d5e63-1aa0-4a73-af8c-5176cd495a34)

- Berikut adalah tabel harga spesifikasi VM yang kami buat <br>
![tabel harga](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/0ceda6d0-0fd0-4f0b-99f7-19aadae14b12)

## Langkah Implementasi dan Konfigurasi Teknologi
1. Buat database dan copy connection string
![e9bf51bc-fff5-416d-9208-c6f6ab0734e7](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/ce08c7bf-385d-449d-beb6-89bddde4566a)

2. Create new connection dengan string database yang sudah di-copy sebelumnya
![0b04f257-0ef6-48e9-988b-1737c8475b16](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/2fd86bc3-2ba8-4b79-bd81-10819d69533b)

3. Buat database sesuai dengan variabel yang sudah dibuat di dalam app.py
![Screenshot 2023-12-13 133954](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/91484af1-616b-4e9b-a9f5-4c975d87620d)

4. Create database baru dengan collection order, add data (import json file)lalu pilih file orders.json yang berisi data-data yang akan dimasukan ke database<br>
![268eff90-912c-475b-b165-7919dc1d8d74](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/606b56f9-1c17-4553-870c-dd613223427d)

5. Run app.py hingga muncul url-nya
![73269c30-c764-4838-867b-f74991970945](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/2a9dda00-5c63-4cee-8631-c075db58b8bd)

6. Untuk mengecek database-nya bisa menggunakan postman, request ke url/orders. Jika statusnya sudah 200 ok, maka database sudah bisa berjalan dengan normal
![73269c30-c764-4838-867b-f74991970945](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/2a9dda00-5c63-4cee-8631-c075db58b8bd)

7. Deploy VM untuk worker dengan installasi requirement yang diperlukan di worker
![8d40b7fd-b13c-4b93-828f-97572effd529](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/5f72b077-ca0e-4ed1-9985-bf020010b5ae)

8. Buat Load Balancer dan pilih droplet worker yang sudah dibuat sebelumnya
![load bal](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/521b3301-7be7-4bc0-8fa2-630f7921413b) 

9. Jika tidak ada error, maka selanjutnya bisa dilakukan load tetsting locust

## Hasil Pengujian Setiap Endpoint
1. Get All Orders
![get all orders](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/127307991/cf0d700b-751e-4112-b7e3-129605201325)

2. Get a Specific Orders by ID
![get order by id](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/127307991/baf487db-6cf9-40e4-a8a6-1d87e0737e6f)

3. Create a New Order
![create](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/127307991/04ad7a67-fe00-4fee-b4d6-febd2375fcb9)

4. Update an Order by ID
![update order](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/127307991/12aec701-9dff-41f6-9061-c8d4b5d4b991)

5. Delete an Order by ID
![delete](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/127307991/a49b1ad8-2a4d-4d1e-92b4-928b081c4f3b)

## Hasil Pengujian dan Analisis Loadtesting Locust
- RPS Maksimum (load testing 60 detik)
![max rps](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/041b8bbc-4ffa-42b5-b87e-a5c915baa97a)
Pada load testing locust untuk mencari RPS maksimum yang bisa didapatkan, kami menggunakan konfigurasi 305 user dan 25 spawn rate. Didapatkan hasil average RPS akhir sebesar 81,2 dengan RPS tertinggi yang sempat disentuh yaitu 143,9. Pada testing ini tidak ditemukan failure sama sekali.

- Peak Concurrency Maksimum (spawn rate 25, load testing 60 detik)
![1500 user 25 spawn rate](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/67294dcf-43a6-4279-8bb1-5000a2be40db)
Pada load testing locust untuk spawn rate 25, peak concurrency yang kami dapat berjumlah 1500. Hasil ini didapatkan dengan failure sebesar 0% dengan RPS sebesar 42,6.

- Peak Concurrency Maksimum (spawn rate 50, load testing 60 detik)
![1400 user 50 spawn rate](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/903fa121-a0e2-46a1-b61f-18062f8dc2bc)
Pada load testing locust untuk spawn rate 50, peak concurrency yang kami dapat berjumlah 1400. Hasil ini didapatkan dengan failure sebesar 0% dengan RPS sebesar 26,9.

- Peak Concurrency Maksimum (spawn rate 100, load testing 60 detik)
![1200 user 100 spawn rate](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/f5b83a58-f525-4a0a-9c89-5fa3dec61783)
Pada load testing locust untuk spawn rate 100, peak concurrency yang kami dapat berjumlah 1200. Hasil ini didapatkan dengan failure sebesar 0% dengan RPS sebesar 30,7.

## Kesimpulan dan Saran
- Setelah percobaan yang kami lakukan berulang kali, jumlah node load balancer sebaiknya scale up dengan jumlah worker karena ketika kami mencoba menggunakan 1 node load balancer dan 3 worker terjadi down pada ketiga worker tersebut
![a78daaeb-889e-458f-aa5b-e7457f011a95](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/c11984c3-57b1-4c47-94e4-a31e02741f25)
- Harga yang ditawarkan Digital Ocean lebih murah daripada Azure dan sekelasnya, tetapi kami menyadari memang ada harga ada kualitas di sini. Pada beberapa kesempatan, VM worker dan load balancer kami yang telah dideploy mengalami down sehingga harus direstart bahkan worst case adalah mensetup ulang. Saran dari kami, jika hendak mendeploy projek yang besar dan budget mencukupi, silakan menggunakan layanan dari Azure, AWS, GCP dan sekelasnya yang memang ditujukan kalangan enterprise dan lebih terpercaya.
- Terdapat banyak variabel yang berpengaruh dalam skenario pengujian locust, seperti:
    - Koneksi internet
    - Kuantitas dan Kualitas (spesifikasi) VM yang digunakan
    - Peak concurrency yang diinput
    - Spawn rate yang diinput
    - Durasi pengetesan\
  Saran dari kami, ketika hendak melakukan pengetesan sesuaikan dengan kebutuhan yang ingin kalian analisis dan gunakan koneksi internet yang stabil untuk memaksimalkan proses pengujian.
- Ternyata ketika dilakukan pengujian, database akan semakin bertambah banyak seiring frekuensi pengujian dan hal tersebut memengaruhi jumlah RPS yang dapat ditangani oleh server kami. Jadi, kuantitas database juga dapat memengaruhi performa server/applikasi yang kami buat karena beban worker VM untuk melakukan GET /orders dan POST /orders juga semakin berat.
    - Berikut adalah hasil pengujian dengan skenario peak concurrency = 500, spawn rate = 50 dan run time = 60 detik
<a href="https://ibb.co/xF2wpR1"><img src="https://i.ibb.co/wcd89xS/1.png" alt="1" border="0"></a>
<a href="https://ibb.co/428kvcH"><img src="https://i.ibb.co/FX5pZ9F/2.png" alt="2" border="0"></a>
<a href="https://ibb.co/mCs8PXv"><img src="https://i.ibb.co/99XtdVw/3.png" alt="3" border="0"></a>
<a href="https://ibb.co/mB5tP6j"><img src="https://i.ibb.co/RSTPJzF/4.png" alt="4" border="0"></a>
<a href="https://ibb.co/FXMKsdm"><img src="https://i.ibb.co/W0w6DRG/5.png" alt="5" border="0"></a> 

    - Berikut adalah perkembangan kuantitas database pada mongodb
<a href="https://ibb.co/8KhrFj6"><img src="https://i.ibb.co/X2w7mzS/bukti1.png" alt="bukti1" border="0"></a>
<a href="https://ibb.co/Wx5t98m"><img src="https://i.ibb.co/mDT8sZf/bukti2.png" alt="bukti2" border="0"></a>
<a href="https://ibb.co/mv1F3wJ"><img src="https://i.ibb.co/HN1pjs7/bukti3.png" alt="bukti3" border="0"></a>
<a href="https://ibb.co/jT8rhRv"><img src="https://i.ibb.co/2yFkqN7/bukti4.png" alt="bukti4" border="0"></a>
<a href="https://ibb.co/N1fH1Yp"><img src="https://i.ibb.co/6vGfvsb/bukti5.png" alt="bukti5" border="0"></a> 

Jika ingin mendapatkan hasil pengujian yang akurat, maka setiap menjalankan locust atau setiap ronde pengujian sebaiknya untuk mereset database terlebih dahulu.
