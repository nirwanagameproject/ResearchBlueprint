# ResearchBlueprint

ReserachBlueprint adalah projek riset flow blueprint pada game engine Unreal Engine

Spesifikasi Testing
- Sistem Operasi : Windows 10 Pro 64 Bit
- Prosesor : Intel(R) Core(TM) i9-9900K CPU @ 3.60GHz 3.60 GHz
- GPU : Nvidia GTX 1080 Ti
- RAM : 24 GB
- Game Engine : Unreal Engine 5.0.2

## Langkah Unreal Engine

### Pembuatan Proyek Baru

Langkah Pembuatan Proyek pada Unreal Engine
- Buka Unreal Engine
- Pilih "Games" pada kolom kiri
- Pilih "First Person" pada kolom tengah
- Pilih "BLUEPRINT"
- Isi "Target Platform" : "Desktop"
- Isi "Quality Preset" : "Maximum"
- Isi "Starter Content" : "Yes" (Checklist)
- Isi "Raytracing" : "None" (Checklist)
- Tentukan Lokasi Proyek pada kolom bawah
  - Misal Isi "Project Location" : "C:\Users\Fajar\Documents\Unreal Project"
- Tentukan Nama Protek
  - Misal Isi "Project Name" : "ResearchBlueprint"
- Jika sudah seperti tampilan yang dibawah ini maka pilih "Create"

![alt text](https://raw.githubusercontent.com/nirwanagameproject/ResearchBlueprint/main/Screenshot/Capture%20ResearchBlueprint%20step%201.PNG "Tampilan Unreal Engine Create New Project")

### Edit Blueprint pada Objek

Langkah untuk membuka Blueprint pada suatu Objek (contoh : BP_Rifle Actor)
- Pada kolom kanan terdapat "Outliner"
- Cari Objek "Item Label" bernama "BP_Rifle"
- Pilih "Edit BP_Rifle" pada kolom "type" seperti berikut

![alt text](https://raw.githubusercontent.com/nirwanagameproject/ResearchBlueprint/main/Screenshot/Capture%20ResearchBlueprint%20step%202.png "Tampilan Unreal Engine Edit Blueprint BP_Rifle")

- Maka akan terbuka pada tab Event Graph seperti berikut

![alt text](https://raw.githubusercontent.com/nirwanagameproject/ResearchBlueprint/main/Screenshot/Capture%20ResearchBlueprint%20step%203.png "Tampilan Unreal Engine Blueprint BP_Rifle")

## Blueprint Unreal Engine

### Penjelasan Flow Blueprint

Untuk penjelasan flow blueprint mengambil sample dari Objek BP_Rifle berikut

![alt text](https://raw.githubusercontent.com/nirwanagameproject/ResearchBlueprint/main/Screenshot/Capture%20ResearchBlueprint%20step%204.png "Tampilan Penjelasan Flow Unreal Engine Blueprint BP_Rifle")

- Terdapat 4 kolom Action pada tampilan diatas yaitu action "On Component Begin Overlap (SphereCollision)" ,"Cast to BP_FirstPersonCharacter" , "SET" dan "Print String"
  - Action "On Component Begin Overlap" terdapat
    - fungsi "Exec" yang disambungkan ke action "Cast to BP_FirstPersonCharacter" maka ketika komponen BP_Rifle ini yang memiliki SphereCollision bertabrakan dengan BP_FirstPersonCharacter
    - variabel Overlapped Component, tidak digunakan
    - variabel Other Actor yang disambungkan ke action "Cast to BP_FirstPersonCharacter" dan menegembalikan value dari Objek itu
    - variabel Other Comp, tidak digunakan
    - variabel Other Body Index, tidak digunakan
    - variabel From Sweep,tidak digunakan
    - variabel Sweep Result,tidak digunakan
  - Action "Cast to BP_FirstPersonCharacter" terdapat
    - fungsi menerima "Exec" dari Action "On Component Begin Overlap"
    - fungsi return value Object ke Other Actor dari Action "On Component Begin Overlap"
    - fungsi "Exec" yang disambungkan ke Action "SET" maka ketika action "Cast to BP_FirstPersonCharacter" sukses dijalankan maka akan mengekseksusi action "SET"
    - fungsi "Exec" "Cast Failed" yang disambungkkan ke Action "Print String" maka ketika action "Cast to BP_FirstPersonCharacter" gagal dijalankan maka akan mengeksekusi action "Print String"
    - variabel As BP First Person Character yang disambungkan ke First Person Character Reference dari action "SET" utnuk mencapatkan objek first person character
  - Action "SET" terdapat
    - fungsi menerima "Exec" dari Action "Cast to BP_FirstPersonCharacter"
    - fungsi return value First Person Character Reference ke As BP First Person Character dari Action "Cast to BP_FirstPersonCharacter"
    - variabel First Person Character Reference, tidak diguanakan
    - fungsi "Exec"
  - Action "Print String"
    - fungsi menerima "Exec" dari Action "Cast to BP_FirstPersonCharacter"
    - variabel In String, diinput manual string "Cast to BP_FirstPersonCharacter FAILED"
    - fungsi Exec
- Dalam setiap action bisa terdapat beberapa fungsi 
  - fungsi "Exec" untuk disambungkan ke Action lain maka akan mengeksekusi action lain
  - fungsi menginput Variabel/Parameter dari action lain seperti Actor,Integer atau Tipe Data lain.
  - menginput data Variabel/Parameter manual setelah di "Exec" seperti String,Integer,dan tipe data lain.

### Macam-macam Blueprint

Terdapat Macam-macam tipe blueprint sebagai berikut
- Blueprint Class, blueprint biasa dengan class dan fungsi
- Blueprint Interface,blueprint hanya berisi interface tanpa implementasi tidak bisa menambahkan variabel,edit grafik dan menambahkan komponen
- Blueprint Data-Only,blueprint hanya berisi kode (dalam bentuk grafik simpul), variabel, dan komponen yang diwarisi dari induknya.
- Blueprint Macro Library,blueprint berisi macro dan grafik node-node.