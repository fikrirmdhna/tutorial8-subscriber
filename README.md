# Tutorial-8 
## Fikri Dhiya Ramadhana
## 2206819533
## AdvProg-C

### QnA
1. What is amqp?  
    - AMQP adalah singkatan dari Advanced Message Queuing Protocol yang dimana merupakan standar terbuka untuk middleware messaging yang memungkinkan aplikasi atau komponen yang berbeda berkomunikasi secara asinkron dengan melewati pesan melalui broker pesan.

2. what it means? guest:guest@localhost:5672, what is the first quest, and what is the second guest, and what is localhost:5672 is for?  
    - guest:guest@localhost:5672 adalah string koneksi dalam format URI yang digunakan untuk terhubung ke broker AMQP (RabbitMQ) koneksi dibuat menggunakan default credentials (nama pengguna "guest", yaitu first guest dan password, yaitu second guest) untuk terhubung ke broker AMQP yang berjalan pada mesin lokal di port 5672.

* Simulation slow subscriber  
![alt text](images/image-1.png)  
Karena ada nya downtime thread selama 1000ms maka akan terjadi queue yang panjang hingga 25 antrian saat menjalankan cargo run secara cepat dari console publisher. 

* Running at least three subscribers
![alt text](images/image-2.png)
![alt text](images/image.png)  
Saat menggunakan tiga subscriber sekaligus dapat dilihat bahwa spike queuenya lebih cepat menurun dibanding dengan hanya satu subscriber karena consumptionnya terbagi secara paralel. 

* What can we improve?  
1. Error Handling: Kedua kode publisher dan subscriber menggunakan unwrap() secara ekstensif, yang dapat menyebabkan panic dan menghentikan program jika terjadi kesalahan lebih baik menggunakan match atau if let.

2. Gunakan konstanta untuk string yang diulang, seperti "amqp://guest:guest@localhost:5672" agar code menjadi lebih readable.