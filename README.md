# Tutorial Modul 5
---
> 1. What is the difference between the approach of performance testing with JMeter and profiling with IntelliJ Profiler in the context of optimizing application performance?

Kalau saya pakai JMeter, itu lebih ke simulasi beban dari luar. Misalnya, saya kirim banyak request ke aplikasi untuk melihat seberapa cepat atau stabil responnya saat ditekan beban. Sedangkan IntelliJ Profiler itu bekerja dari dalam aplikasi. Alat ini membantu saya melihat secara detail bagaimana kode berjalan, berapa lama eksekusinya, penggunaan CPU, dan memori. Jadi, intinya JMeter lebih untuk menguji performa secara keseluruhan, sedangkan Profiler membantu saya menemukan bagian kode yang perlu dioptimasi.

> 2. How does the profiling process help you in identifying and understanding the weak points in your application?

Dengan melakukan profiling, saya bisa mendapatkan data runtime seperti berapa banyak waktu yang dihabiskan oleh setiap metode, alokasi memori, dan sebagainya. Tampilan seperti flame graph atau call tree membuat saya bisa “melihat” bagian mana yang paling berat. Jadi, saya bisa tahu bagian mana dari kode yang bikin performa menurun dan harus dioptimalkan.

> 3. Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?

Menurut saya, IntelliJ Profiler cukup efektif. Karena terintegrasi langsung di IDE, saya bisa langsung melihat hasil profiling di samping kode yang kamu tulis. Fitur seperti in-editor performance hints dan visualisasi seperti flame graph sangat membantu untuk langsung menemukan bagian yang bermasalah tanpa harus beralih ke alat lain. Jadi, cukup praktis dan langsung terasa manfaatnya.

> 4. What are the main challenges you face when conducting performance testing and profiling, and how do you overcome these challenges?

Ada beberapa tantangan, misalnya:

- Pengaturan Lingkungan: Sulit memastikan lingkungan pengujian sama dengan kondisi produksi, sehingga hasilnya bisa berbeda.
- Overhead dari Profiling: Saat melakukan profiling, ada tambahan beban yang kadang bisa mempengaruhi performa aplikasi.
- Banyaknya Data: Data yang dihasilkan bisa sangat banyak dan kompleks.
Untuk mengatasinya, kita bisa melakukan sampling agar overhead tidak terlalu besar, pastikan lingkungan pengujian sudah disetting mirip dengan produksi, dan manfaatkan fitur filter serta visualisasi di profiler supaya data yang ditampilkan lebih mudah dipahami.

> 5. What are the main benefits you gain from using IntelliJ Profiler for profiling your application code?

Ada beberapa keuntungan yang saya rasakan ketika menggunakan IntelliJ Profiler, antara lain:

- Integrasi Langsung dengan IDE: Jadi, kamu bisa profiling tanpa keluar dari IntelliJ, yang memudahkan workflow kamu.
- Visualisasi yang Mudah Dimengerti: Tampilan seperti flame graph, call tree, dan timeline membantu kamu cepat menangkap masalah.
- Feedback Langsung di Kode: Fitur in-editor performance hints menandai langsung di samping baris kode yang bermasalah, sehingga kamu bisa langsung melihat dan memperbaikinya.
- Analisis CPU dan Memori Bersamaan: Kamu bisa melihat kedua aspek sekaligus untuk mendapatkan gambaran yang lebih komprehensif tentang performa aplikasi.
> 6. How do you handle situations where the results from profiling with IntelliJ Profiler are not entirely consistent with findings from performance testing using JMeter?

Kadang-kadang, hasil dari IntelliJ Profiler dan JMeter bisa berbeda karena cara mereka mengukur performa itu pun berbeda. Kalau JMeter mengukur respon dari luar, profiler mengukur aktivitas internal. Jadi, jika hasilnya tidak konsisten, saya bisa:

- Pastikan skenario pengujian saya sama di kedua alat.
- Lihat data secara mendetail, cari tahu konteks perbedaannya. Mungkin ada faktor eksternal atau internal yang membuat perbedaan itu muncul.
- Lakukan pengujian berulang dan review kode untuk memastikan bahwa kedua alat saling melengkapi.

> 7. What strategies do you implement in optimizing application code after analyzing results from performance testing and profiling? How do you ensure the changes you make do not affect the application's functionality?
Setelah mendapatkan insight dari testing dan profiling, langkah selanjutnya adalah mengoptimasi kode. Biasanya, strategi yang saya lakukan meliputi:

- Refactoring Kode: Memperbaiki logika atau algoritma yang ternyata menjadi penyebab lambatnya eksekusi.
- Benchmarking dan Perbandingan: Membandingkan hasil sebelum dan sesudah optimasi untuk melihat peningkatan performa.
- Pengujian Otomatis: Menjalankan unit test dan regression test untuk memastikan perubahan yang dilakukan tidak merusak fungsionalitas aplikasi.
- Iterasi Berkala: Melakukan testing dan profiling berulang agar setiap perubahan terbukti meningkatkan performa dan tidak menimbulkan masalah baru.

## JMeter Test via CMD:
### all-student test
- Sebelm optimisasi:
```
timeStamp,elapsed,label,responseCode,responseMessage,threadName,dataType,success,failureMessage,bytes,sentBytes,grpThreads,allThreads,URL,Latency,IdleTime,Connect
1741934445158,5,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-2,text,false,,2631,0,2,2,http://localhost:8080/all-student,0,0,5
1741934445145,16,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-1,text,false,,2631,0,2,2,http://localhost:8080/all-student,0,0,16
1741934445259,1,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-3,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,1
1741934445359,2,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-4,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,2
1741934445456,2,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-5,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,2
1741934445554,1,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-6,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,1
1741934445655,2,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-7,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,2
1741934445755,2,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-8,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,2
1741934445855,1,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-9,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,1
1741934445954,2,HTTP Request,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-10,text,false,,2631,0,1,1,http://localhost:8080/all-student,0,0,2
```

### all-student-name test:
- Sebelum Optimisasi:
```
timeStamp,elapsed,label,responseCode,responseMessage,threadName,dataType,success,failureMessage,bytes,sentBytes,grpThreads,allThreads,URL,Latency,IdleTime,Connect
1741934136883,22,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-1,text,false,,2631,0,2,2,http://localhost:8080/all-student-name,0,0,21
1741934136884,22,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-2,text,false,,2631,0,2,2,http://localhost:8080/all-student-name,0,0,21
1741934136982,1,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-3,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,1
1741934137080,2,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-4,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,2
1741934137180,1,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-5,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,1
1741934137278,2,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-6,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,2
1741934137376,2,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-7,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,2
1741934137477,1,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-8,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,1
1741934137575,2,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-9,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,2
1741934137675,2,all-student-name,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-10,text,false,,2631,0,1,1,http://localhost:8080/all-student-name,0,0,2
```
### highest-gpa test:
- Sebelum Optimisasi:
```
timeStamp,elapsed,label,responseCode,responseMessage,threadName,dataType,success,failureMessage,bytes,sentBytes,grpThreads,allThreads,URL,Latency,IdleTime,Connect
1741934185576,15,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-1,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,15
1741934185603,1,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-2,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,1
1741934185704,3,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-3,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,3
1741934185802,1,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-4,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,1
1741934185890,1,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-5,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,1
1741934185990,2,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-6,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,1
1741934186090,2,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-7,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,2
1741934186191,1,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-8,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,1
1741934186289,2,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-9,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,2
1741934186389,1,highest-gpa,Non HTTP response code: org.apache.http.conn.HttpHostConnectException,"Non HTTP response message: Connect to localhost:8080 [localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect",Thread Group 1 1-10,text,false,,2631,0,1,1,http://localhost:8080/highest-gpa,0,0,1
```

## JMeter Test Via App
### all-student Test:
- Sebelum Optimisasi:
![image](https://github.com/user-attachments/assets/eb44b7fd-21b8-4cc7-a79d-4abb174c8acb)
- Setelah Optimisasi:
![image](https://github.com/user-attachments/assets/0685754f-7635-499e-b97b-53b4a7de6d19)

### all-student-name Test:
- Sebelum Optimisasi:
![image](https://github.com/user-attachments/assets/0fee05bf-b379-4f28-9213-9bf12bb4083b)

- Setelah Optimisasi:
![image](https://github.com/user-attachments/assets/3ef7c392-f478-4520-8ea8-66715d169c31)

### highest-gpa Test:
- Sebelum Optimisasi:
![image](https://github.com/user-attachments/assets/1db41a32-d4f4-4a94-a512-732a284f2969)


- Setelah Optimisasi:
![image](https://github.com/user-attachments/assets/ff914446-0791-408c-848a-0a3e5104cd64)



