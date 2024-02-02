# Capstone_3_Hotel_Booking_Demands
Hotel_Booking_Demands

**Context:**
  
Sebuah hotel ingin menyiapkan kamar untuk calon pelanggannya. Hotel ingin mengetahui pelanggan mana yang akan benar - benar menginap dan mana yang tidak.


Target :

0 : Tidak membatalkan booking

1 : Membatalkan Booking

**Problem Statement :**

Proses penyiapan fasilitas seperti kamar pada hotel memakan waktu dan sumber daya. Seandainya hotel menyiapkan semua fasilitas tetapi tidak digunakan maka akan sia - sia dan hotel mengalami kerugian dan beberapa fasilitas hotel kualitasnya akan menurun seiring berjalannya waktu, sehingga fasilitas harus disiapkan disaat diminta.

Perusahaan mengasumsikan biaya sebagai berikut
- Biaya yang dikeluarkan oleh Hotel untuk menyiapkan fasilitas kepada calon Customer (Kondisi False Negative): $50 / orang
- Biaya yang dikeluarkan Hotel untuk biaya marketing: $30 / orang
- Oleh karena biaya yang dikeluarkan akan lebih tinggi ketika pada saat kondisi False Negative maka hotel akan berusaha untuk menurunkan biaya yang telah dikeluarkan tersebut. Kemudian metrik yang dapat kita gunakan untuk melakukan pemilihan terhadap model Machine Learning yaitu Recall.

**Goals :**

Maka berdasarkan permasalahan tersebut, hotel ingin memiliki kemampuan untuk memprediksi faktor - faktor apa saja yang membuat pelanggan membatalkan booking, sehingga dapat memfokuskan penyiapan fasilitas pada pelanggan yang akan menginap dihotel tersebut.




**Analytic Approach :**

Jadi yang akan kita lakukan adalah menganalisis data untuk menemukan pola yang membedakan pengunjung yang jadi menginap di hotel dan yang tidak jadi(batal).

Kemudian kita akan membangun model klasifikasi yang akan membantu hotel untuk dapat memprediksi karakteristik pengunjung yang akan menginap atau tidak.

### Attribute Information

| Attribute | Data Type, Length | Description |
| --- | --- | --- |
| country | str | Negara Asal Pelanggan |
| market_segment | str | Segmen Pasar |
| previous_cancellations | int64 | Berapa kali melakukan pembatalan pemesanan |
| booking_changes | int64 | Berapa kali melakukan prubahan pemesanan |
| daposit_type | str | Tipe deposit |
| days_in_waiting_list | int64 | hari menunggu dalam waiting list |
| customer_type | str | Tipe pemesanan |
| reserved_room_type | str | Tipe kamar yang disewa |
| required_car_parking_space | int64 | Jumlah perminataan lahan parkir |
| total_of_special_request | int64 | Permintaan Tambahan |
| is_canceled(target) | int64 | Pembatalan pemesanan,0 – Tidak batal, 1 – Batal |


### **Kesimpulan**
Biaya Pengeluaran Hotel Sebelum Menggunakan Pemodelan Machine Learning (ML)

- Permasalahan utama yang dihadapi hotel adalah bagaimana cara mengelola sumber daya dan meminimalisir pengeluaran ketika terjadi kondisi di mana tamu yang sebelumnya diprediksi akan menginap ternyata membatalkan pemesanannya. Situasi ini mengakibatkan hotel telah mengeluarkan biaya untuk menyiapkan kamar dan fasilitas lainnya untuk tamu yang pada akhirnya tidak jadi menginap.
- Jika dilihat dari nilai FN (False Negative) pada Confusion Matrix sebelum menggunakan modeling maka terdapat sejumlah 324 calon Customer yang diprediksi tidak akan membatalkan booking namun aktualnya menggagalkan booking/ salah prediksi. Maka biaya yang telah dikeluarkan oleh Hotel pada saat sedang memprediksi tersebut adalah sebesar 324 x $50 = $ 16.200

Biaya Pengeluaran Hotel setelah Menggunakan Pemodelan Machine Learning (ML)

- Setelah implementasi model ML yang optimal dengan menggunakan stacking method, biaya yang dikeluarkan hotel untuk kasus-kasus salah prediksi dapat diminimalisir. Model ML membantu hotel untuk lebih akurat memprediksi pemesanan mana yang akan benar-benar terjadi dan mana yang kemungkinan besar akan dibatalkan.
- Jika dilihat dari nilai FN pada Confusion Matrix setelah menggunakan modeling + Threshold terbaik maka jumlah calon Customer yang diprediksi tidak akan membatalkan booking namun aktualnya menggagalkan booking menjadi turun drastis yaitu hanya 26 calon customer saja jika dibandingkan jumlah calon Customer sebelumnya dilakukan modeling yaitu sejumlah 321 calon Customer. Maka biaya yang dikeluarkan Hotel pada saat salah prediksi setelah dilakukan modeling adalah hanya sebesar 26 x $50 = $1.300 saja.

- ## **Insight**
 - Feature Importances merupakan item yang bertujuan untuk mengetahui fitur-fitur yang memiliki pengaruh signifikan terhadap target. Variabel yang menjadi target dalam penelitian ini adalah 'is canceled', sedangkan fitur selain 'is canceled' merupakan fitur yang berkontribusi terhadap target.
 - Jika dilihat pada plot maka fitur 'market segment' merupakan fitur yang paling berpengaruh terhadap target, yaitu 'is canceled'. Sehingga dapat disimpulkan bahwa dari market segment manakah seorang calon customer merupakan fitur yang paling berpengaruh untuk menentukkan apakah calon customer tersebut melakukan cancel booking atau tidak
