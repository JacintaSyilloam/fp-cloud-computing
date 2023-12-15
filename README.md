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
Pada load testing locust untuk mencari RPS maksimum yang bisa didapatkan, kami menggunakan konfigurasi 305 user dan 25 spawn rate. Didapatkan hasil average rps akhir sebesar 81,2 dengan RPS tertinggi yang sempat disentuh yaitu 143,9. Pada testing ini tidak ditemukan failure sama sekali.

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
