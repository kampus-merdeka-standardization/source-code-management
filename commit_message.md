# Commit Message

Pesan commit adalah cara berkomunikasi antara anggota tim. Pesan commit yang bermakna dapat menghemat waktu dalam menjawab pertanyaan "mengapa?" dan "bagaimana?" dan memberi kita lebih banyak waktu untuk bekerja produktif.

Pesan commit harus mendeskripsikan apa yang berubah dalam perilaku kode, bukan apa yang berubah dalam kode itu sendiri. Pesan commit harus menggunakan kalimat perintah, waktu sekarang, dan tidak ada titik di akhir.

## Rules

Ada tujuh aturan untuk menulis pesan commit Git yang informatif, konsisten, dan berguna. diantaranya :

1. Gunakan baris kosong untuk memisahkan judul dan isi
2. Ringkas perubahan dalam sekitar 50 karakter atau kurang
3. Gunakan huruf kapital di awal judul
4. Jangan gunakan tanda titik (`.`) di akhir judul
5. Gunakan mode perintah untuk judul
6. Bungkus isi pada 72 karakter
7. Gunakan Isi (Body) untuk menjelaskan what and why, not how

## Explanation

### Gunakan baris kosong untuk memisahkan judul dan isi
___
Meskipun tidak diwajibkan, ada baiknya untuk memulai pesan komit dengan satu baris pendek (kurang dari 50 karakter) yang meringkas perubahan, diikuti dengan baris kosong dan kemudian deskripsi yang lebih menyeluruh. Teks hingga baris kosong pertama dalam pesan komit dianggap sebagai judul komit.

#### Contoh
```bash
git commit -m 'Added login feature to the web application' -m "In this commit, I added the login feature to our web application. This feature allows users to log into their accounts by entering their email and password. I've also created a login page with the appropriate login form and implemented input validation to ensure security. This feature is expected to enhance the user experience and maintain data security."
```

kemudian untuk kita bisa menggunakan perintah `git log` untuk melihat daftar commit yang telah dilakukan beserta informasi seperti penulis commit, tanggal commit, pesan commit, dan hash commit. Seperti:
```
$ git log
commit 42e769bdf4894310333942ffc5a15151222a87be
Author: User Name <username@example.com>
Date:   Fri Jan 01 00:00:00 1982 -0200

Added login feature to the web application

In this commit, I added the login feature to our web application. This feature allows users to log into their accounts by entering their email and password. I've also created a login page with the appropriate login form and implemented input validation to ensure security. This feature is expected to enhance the user experience and maintain data security.
```


`git log --oneline` untuk melihat baris judul saja
```
$ git log --oneline
42e769 Added login feature to the web application
```

`git shortlog` untuk mengelompokkan commit berdasarkan user dan hanya menampilkan baris judul
```
$ git shortlog
Kevin Flynn (1):
      Derezz the master control program

Alan Bradley (1):
      Introduce security program "Tron"

Ed Dillinger (3):
      Rename chess program to "MCP"
      Modify chess program
      Upgrade chess program

Walter Gibbs (1):
      Introduce protoype chess program
```


### Ringkas perubahan dalam sekitar 50 karakter atau kurang
___
Ini adalah judul pesan commit yang harus menjelaskan apa yang dilakukan commit secara singkat, yaitu dengan batas 50 karakter.

> Jika kesulitan dalam merangkum dengan batasan 50 karakter, kemungkinan anda melakukan banyak perubahan dalam satu commit. Cobalah untuk memperkecil perubahan dalam satu commit, atau melakukan pemisahan komit menjadi bagian-bagian kecil.


### Gunakan huruf kapital di awal judul
___
Ini adalah konvensi penulisan yang umum dan membuat judul lebih mudah dibaca.

#### Contoh yang Benar ✔️
- Accelerate to 88 miles per hour
#### Contoh yang Salah ❌
- `a`ccelerate to 88 miles per hour

### Jangan gunakan tanda titik (`.`) di akhir judul
---
Tanda baca tidak diperlukan dan hanya membuang ruang yang berharga.

#### Contoh yang Benar ✔️
- Open the pod bay doors
#### Contoh yang Salah ❌
- Open the pod bay doors`.`

### Gunakan mode perintah untuk judul
___
Mode perintah berarti menulis seolah-olah memberikan perintah atau instruksi. Ini membuat judul lebih jelas dan tegas dan sesuai dengan konvensi Git sendiri, seperti:

1. `git merge` akan dihasilkan commit message:
    ```
    Merge branch 'myfeature'
    ```

2. `git revert` akan dihasilkan commit message:
    ```
    Revert "Add the thing with the stuff"

    This reverts commit cc87791524aedd593cff5a74532befe7ab69ce9d.
    ```

3. Tombol **Merge** pada github pull request akan menghasilkan commit message:
    ```
    Merge pull request #123 from someuser/somebranch
    ```

Jadi, gunakanlah kalimat perintah dalam membuat commit message.

#### Contoh yang Benar ✔️
- Refactor subsystem X for readability
- Update getting started documentation
- Remove deprecated methods
- Release version 1.0.0

#### Contoh yang Salah ❌
- ~~Fixed bug with Y~~
- ~~Changing behavior of X~~
- ~~More fixes for broken stuff~~
- ~~Sweet new API methods~~

#### Judul commit message yang baik harus bisa melengkapi kalimat:

"If applied, this commit will `judul commit message`"

#### Contoh yang Benar ✔️
- If applied, this commit will `Refactor subsystem X for readability`
- If applied, this commit will `Update getting started documentation`
- If applied, this commit will `Remove deprecated methods`
- If applied, this commit will `Release version 1.0.0`
- If applied, this commit will `Merge pull request #123 from user/branch`

#### Contoh yang Salah
- If applied, this commit will ~~`Fixed bug with Y`~~
- If applied, this commit will ~~`Changing behavior of X`~~
- If applied, this commit will ~~`More fixes for broken stuff`~~
- If applied, this commit will ~~`Sweet new API methods`~~


> Penggunaan kalimat perintah hanya berlaku pada baris judul, tidak pada baris isi (body)

### Bungkus isi pada 72 karakter
___
Git tidak pernah membungkus teks secara otomatis. Ketika Anda menulis isi pesan komit, Anda harus memperhatikan margin kanan, dan membungkus teks secara manual.

Rekomendasi kami adalah melakukan ini pada 72 karakter, sehingga Git memiliki banyak ruang untuk mengindentasi teks sambil tetap menjaga semuanya di bawah 80 karakter secara keseluruhan.

Ini untuk memastikan bahwa isi pesan commit mudah dibaca dan tidak terlalu panjang. Gunakan editor teks yang dapat membantu Anda melakukan pembungkusan teks secara manual.

### Gunakan Isi (Body) untuk menjelaskan _what and why, not how_
___
Dalam banyak kasus, kita bisa mengabaikan detail tentang bagaimana sebuah perubahan dibuat. Kode pada umumnya sudah cukup jelas dalam hal ini (dan jika kodenya sangat kompleks sehingga perlu dijelaskan dalam bentuk prosa, itulah gunanya membuat komentar pada sumber kode). Fokuslah untuk menjelaskan alasan mengapa Anda membuat perubahan di tempat pertama - cara kerja sebelum perubahan (dan apa yang salah dengan itu), cara kerjanya sekarang, dan mengapa Anda memutuskan untuk menyelesaikannya dengan cara yang Anda lakukan.

Contoh [commit dari Bitcoin Core](https://github.com/bitcoin/bitcoin/commit/eb0b56b19017ab5c16c745e6da39c53126924ed6)
```
commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille <pieter.wuille@gmail.com>
Date:   Fri Aug 1 22:57:55 2014 +0200

Simplify serialize.h's exception handling

Remove the 'state' and 'exceptmask' from serialize.h's stream
implementations, as well as related methods.

Remove the 'state' and 'exceptmask' from serialize.h's stream implementations, as well as related methods. 

As exceptmask always included 'failbit', and setstate was always called with bits = failbit, all it did was immediately raise an exception. Get rid of those variables, and replace the setstate with direct exception throwing (which also removes some dead code). 

As a result, good() is never reached after a failure (there are only 2 calls, one of which is in tests), and can just be replaced by !eof(). 

fail(), clear(n) and exceptions() are just never called. Delete them.
```

