# Tutorial 2 GameDev

- Nama: Kirene Naomi Kristin Pangaribuan
- NPM: 1906353473

## **Pertanyaan 1**: *Apa saja pesan log yang dicetak pada panel Output?*

### **Jawaban:**
Godot Engine v4.3.stable.mono.official.77dcf97d8 - https://godotengine.org
Vulkan 1.3.280 - Forward+ - Using Device #0: NVIDIA - NVIDIA GeForce MX450

Platform initialized
Reached objective!
Reached objective!
--- Debugging process stopped ---

## **Pertanyaan 2**: *Coba gerakkan landasan ke batas area bawah, lalu gerakkan kembali ke atas hingga hampir menyentuh batas atas. Apa saja pesan log yang dicetak pada panel Output?*

### **Jawaban:**
Godot Engine v4.3.stable.mono.official.77dcf97d8 - https://godotengine.org
Vulkan 1.3.280 - Forward+ - Using Device #0: NVIDIA - NVIDIA GeForce MX450

Platform initialized
Reached objective!
Reached objective!
Reached objective!
Reached objective!
--- Debugging process stopped ---

## **Pertanyaan 3**: *Buka scene MainLevel dengan tampilan workspace 2D. Apakah lokasi scene ObjectiveArea memiliki kaitan dengan pesan log yang dicetak pada panel Output pada percobaan sebelumnya?*

### **Jawaban:**
Ya, ObjectiveArea mendeteksi jika ada collision pada collisionArea, signal event tersebut ke dalam game log.

## **Pertanyaan 4**: *Scene BlueShip dan StonePlatform sama-sama memiliki sebuah child node bertipe Sprite. Apa fungsi dari node bertipe Sprite?*

### **Jawaban:**
Sprite berfungsi untuk menampilkan atau merender aset visual seperti karakter, musuh, background, UI, baik itu dalam 2D maupun 3D. Sebagai node, Sprite bisa dikombinasikan dengan node lain untuk menentukan interaksi atau properti dari sprite dalam sebuah parental node.

## **Pertanyaan 5**: *Root node dari scene BlueShip dan StonePlatform menggunakan tipe yang berbeda. BlueShip menggunakan tipe RigidBody2D, sedangkan StonePlatform menggunakan tipe StaticBody2D. Apa perbedaan dari masing-masing tipe node?*

### **Jawaban:**
RigidBody2D berfungsi mensimulasikan interaksi berdasarkan fisika. Pengaruhnya terlihat pada Playtest dimana ketika bergerak kebawah, pesawat akan jatuh lalu kemudian membentur platform seperti gravitasi.

Sementara itu, StaticBody2D berfungsi untuk objek yang tidak bergerak, namun dapat memberikan reaksi kepada objek yang bertipe RigidBody2D. Pada playtest hal ini terlihat pada Playtest saat bergerak kebawah kemudian berhenti, pesawat berhenti diatas platform ketika membenturnya, daripada menembusnya dengan berhenti pada lokasi yang sama dengan platform.

## **Pertanyaan 6**: *Ubah nilai atribut Mass pada tipe RigidBody2D secara bebas di scene BlueShip, lalu coba jalankan scene MainLevel. Apa yang terjadi?*

### **Jawaban:**
Sejauh perubahan yang terlihat tidak ada perbedaan, bahkan membandingkan 1000kg RigidBody2D dengan 0,007kg. Hal ini karena external force seperti gravity dan collision belum di setup. Namun, misalnya jika gravity diubah menjadi 10, pengaruh perbedaan Mass kini mulai terlihat dengan bouncing yang terjadi pada pesawat ketika membentur platform.

## **Pertanyaan 7**: *Ubah nilai atribut Disabled pada tipe CollisionShape2D di scene StonePlatform, lalu coba jalankan scene MainLevel. Apa yang terjadi?*

### **Jawaban:**
Pesawat kini tidak lagi membentur platform sehingga jatuh menembus platform sampai tak terhingga. Mengaktifkan atribut Disabled mengakibatkan Stoneplatform tidak dapat mendeteksi adanya benturan dari pesawat.

## **Pertanyaan 8**: *Pada scene MainLevel, coba manipulasi atribut Position, Rotation, dan Scale milik node BlueShip secara bebas. Apa yang terjadi pada visualisasi BlueShip di Viewport?*

### **Jawaban:**
Mengubah koordinat position akan berpengaruh pada lokasi center dari node BlueShip. Secara visual, hal ini terlihat pada perubahan letak sprite Blueship. Mengubah koordinat x akan mengubah lokasi Blueship secara horizontal, dan koordinat y mengubah lokasi secara vertikal. Mengubah Rotation akan memiringkan node beberapa derajat dari sumbu semula. 

Sementara itu, mengubah nilai scale akan memperbesar atau memperkecil ukuran node pada Viewport. Mengubah scale memberikan warning karena perubahan dilakukan pada objek bertipe RigidBody2D. Artinya, saat Playtest, perubahan scaling pada node tidak akan berpengaruh karena untuk objek ini akan disimulasikan fisika. Berdasarkan fisika, semakin besar suatu objek yang sama, semakin besar massanya. Namun, mengubah scale dari scene MainLevel tidak mengubah massa tersebut.

## **Pertanyaan 9**: *Pada scene MainLevel, perhatikan nilai atribut Position node PlatformBlue, StonePlatform, dan StonePlatform2. Mengapa nilai Position node StonePlatform dan StonePlatform2 tidak sesuai dengan posisinya di dalam scene (menurut Inspector) namun visualisasinya berada di posisi yang tepat?*

### **Jawaban:**
Posisi platform yang tidak bersesuaian adalah posisi pada sumbu Y. Hal ini karena node StonePlatform dan StonePlatform2 berada di dalam parent node yaitu PlatformBlue. Pada Inspector atribut Position, PlatformBlue memiliki koordinat lokasi yang sesuai dengan tampilan lokasi platform pada ViewPort. Setup pada PlatformBlue menjadi global attribute bagi StonePlatform dan StonePlatform2. Jika dengan setup tersebut, kita mengubah atribut position milik StonePlatform atau StonePlatform2, maka perubahan lokasi yang terjadi akan relatif terhadap global attribute Position yang dimiliki PlatformBlue.