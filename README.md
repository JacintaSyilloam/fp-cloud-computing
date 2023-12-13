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

## Rancangan Arsitektur dan Tabel Harga Spesifikasi VM
- Berikut adalah rancangan arsitektur yang telah kami buat untuk final project kami
![arsitektur](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/37e9159f-92a0-439e-be1e-93a078b3abff)
- Kami memilih untuk menggunakan Digital Ocean sebagai lingkungan cloud yang akan kami gunakan. Berikut adalah tabel harga spesifikasi VM yang kami buat <br>
![tabel harga](https://github.com/JacintaSyilloam/fp-cloud-computing/assets/115382618/a01e2923-4a51-400e-b937-6a994f369e1b)

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

8. Jika tidak ada error, maka worker sudah berjalan

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
1. Endpoint Get Order
- RPS Maksimum (load testing 60 detik)
- Peak Concurrency Maksimum (spawn rate 25, load testing 60 detik)
- Peak Concurrency Maksimum (spawn rate 50, load testing 60 detik)
- Peak Concurrency Maksimum (spawn rate 100, load testing 60 detik)
2. Endpoint Create New Order
- RPS Maksimum (load testing 60 detik)
- Peak Concurrency Maksimum (spawn rate 25, load testing 60 detik)
- Peak Concurrency Maksimum (spawn rate 50, load testing 60 detik)
- Peak Concurrency Maksimum (spawn rate 100, load testing 60 detik)
