# Branching Strategy

Branching Strategies adalah strategi yang diterapkan oleh tim pengembangan perangkat lunak saat menulis, menggabungkan, dan menerapkan kode saat menggunakan sistem kontrol versi. Ini pada dasarnya adalah seperangkat aturan yang dapat diikuti pengembang untuk menentukan bagaimana mereka berinteraksi dengan basis kode bersama.

<img src= https://i.ytimg.com/vi/Bg8tiOLZw4A/maxresdefault.jpg>

Branching memungkinkan tim pengembang untuk berkolaborasi dengan mudah di dalam satu basis kode pusat. Ketika pengembang membuat branch, sistem kontrol versi membuat salinan basis kode pada titik waktu tersebut. Perubahan pada branch tidak mempengaruhi pengembang lain dalam tim

Strategi ini sangat penting dalam siklus hidup pengembangan perangkat lunak karena memungkinkan tim untuk bekerja secara paralel pada fitur yang berbeda tanpa mengganggu pekerjaan orang lain. Ini juga memfasilitasi proses seperti code review, integrasi terus menerus (CI), dan penyebaran terus menerus (CD) yang merupakan bagian penting dari praktik pengembangan perangkat lunak modern.

Dengan strategi branching yang efektif, tim dapat mengelola dan mengontrol perubahan kode dengan lebih baik, meminimalkan risiko bug dan konflik, dan pada akhirnya menghasilkan produk perangkat lunak yang lebih stabil dan berkualitas tinggi.

#### Referensi:
- [Branching Strategies](https://www.abtasty.com/blog/git-branching-strategies/)
- [Software Development Branching](https://www.atlassian.com/agile/software-development/branching)

## Trunk

<img src="https://statusneo.com/wp-content/uploads/2022/08/tbd_workflow.drawio-1-1.png"/>

Trunk Based Development (TBD) adalah strategi pengembangan perangkat lunak di mana pengembang menggabungkan setiap fitur baru, perbaikan bug, atau perubahan kode lainnya ke satu branch pusat dalam sistem kontrol versi. branch ini disebut "trunk", "mainline", atau dalam Git, "master branch".

TBD adalah strategi pengembangan perangkat lunak di mana para insinyur menggabungkan perubahan yang lebih kecil lebih sering ke basis kode utama dan bekerja dari salinan trunk daripada bekerja pada branch fitur jangka panjang. Model pengembangan ini sering digunakan sebagai bagian dari alur kerja pengembangan integrasi terus-menerus.

Dalam TBD, setiap pengembang membagi pekerjaan mereka menjadi batch kecil dan menggabungkan pekerjaan tersebut ke trunk setidaknya sekali (dan mungkin beberapa kali) sehari. Perbedaan kunci antara pendekatan ini adalah cakupan. branch fitur biasanya melibatkan beberapa pengembang dan membutuhkan hari atau bahkan minggu kerja. Sebaliknya, branch dalam pengembangan berbasis trunk biasanya tidak bertahan lebih dari beberapa jam, dengan banyak pengembang menggabungkan perubahan individu mereka ke trunk dengan sering.

Salah satu manfaat utama dari pendekatan berbasis trunk adalah bahwa itu mengurangi kompleksitas acara penggabungan dan menjaga kode tetap terkini dengan memiliki sedikit jalur pengembangan dan melakukan penggabungan kecil dan sering.

### Example

![example-tbd](https://wpblog.semaphoreci.com/wp-content/uploads/2023/02/unnamed-9-1056x672.png)

**Main**: Ini adalah branch utama dalam repositori kode sumber, yang sering disebut sebagai "trunk" atau "master". Semua perubahan kode yang dikembangkan harus akhirnya digabungkan ke branch ini. branch ini harus selalu dalam keadaan yang siap untuk di-deploy ke produksi.

**Short-lived branch**: Ini adalah branch-branch yang diciptakan dari branch utama (main) dan memiliki umur yang pendek. Pengembang menggunakan branch ini untuk bekerja pada fitur, perbaikan bug, atau tugas pengembangan lainnya secara terisolasi dari branch utama. branch ini tidak seharusnya ada untuk waktu yang lama dan harus digabungkan (merged) kembali ke branch utama sesegera mungkin untuk mengurangi konflik penggabungan dan memastikan integrasi yang lancar.

**Build, Test, Merge**: Ini adalah siklus CI (Continuous Integration) di mana kode dari branch-branch pendek di-build dan diuji. Jika build dan tes berjalan dengan sukses, perubahan kode tersebut siap untuk digabungkan kembali ke branch utama.

**Release**: Setelah perubahan kode telah digabungkan kembali ke branch utama dan semua tes telah lulus, kode tersebut siap untuk di-release. Ini bisa berarti penyebaran ke lingkungan praproduksi atau produksi tergantung pada siklus rilis.

Referensi:
- [Trunk-based Development | Atlassian.](https://www.atlassian.com/continuous-delivery/continuous-integration/)
- [DevOps tech: Trunk-based development - Google Cloud.](https://cloud.google.com/architecture/devops/)
- [Trunk-Based Development – Glossary – Split](https://www.split.io/glossary/trunk-based-development/)
- [What is trunk-based development? - Optimizely](https://www.optimizely.com/optimization-glossary/trunk-based-development/)

## Git Flow

<img src = "https://wac-cdn.atlassian.com/dam/jcr:8f00f1a4-ef2d-498a-a2c6-8020bb97902f/03%20Release%20branches.svg?cdnVersion=1280">

GitFlow adalah salah satu strategi branching yang sangat populer dan banyak digunakan. Strategi ini melibatkan dua branch utama dengan durasi hidup tak terbatas: `master` dan `develop`. branch `master` mencerminkan versi produksi saat ini, sementara branch `develop` adalah tempat pengembangan aktif berlangsung.

GitFlow adalah pola branching model yang digunakan pada suatu kolaborasi menggunakan version control GIT. Pada setiap branch, nantinya akan disatukan dan menghasilkan suatu produk yang utuh. Model ini dinilai merupakan suatu hal yang cocok untuk melakukan kolaborasi dan mengukur pekerjaan suatu developer team.

GitFlow membagi repo kedalam 2 branch utama, yaitu master dan develop. Branch master adalah branch yang siap atau yang sedang live di production, sedangkan branch develop adalah branch yang masih dalam tahap pengembangan.

GitFlow adalah sebuah fitur dari Git yang digunakan untuk keperluan desain alur kerja, yang dapat digunakan untuk mendefinisikan model perbranchan alur kerja secara jelas dan efisien. Gitflow adalah aturan-aturan yang disepakati oleh tim agar selama proses pengerjaan project terbentuk alur yang jelas.

### Example

![example-gitflow](https://miro.medium.com/v2/resize:fit:658/1*5i8mTaBs05J3eGhp_CJv5Q.png)

1. **Master**: Ini adalah branch utama tempat semua perubahan akhir akan digabungkan. Biasanya, branch ini akan mencerminkan kode yang ada di produksi¹.

2. **Hotfixes**: branch ini biasanya digunakan untuk perbaikan bug mendesak yang perlu diterapkan ke produksi secepat mungkin.

3. **Release Branches**: branch rilis merujuk pada ide bahwa rilis sepenuhnya terkandung dalam branch. Ini berarti bahwa pada akhir siklus pengembangan, manajer rilis akan membuat branch dari branch utama (misalnya, "branch pengembangan 1.1"). Semua perubahan untuk rilis 1.1 perlu diterapkan dua kali: sekali ke branch 1.1 dan kemudian ke baris kode utama.

4. **Develop**: branch ini biasanya digunakan sebagai branch utama tempat pengembang menggabungkan perubahan mereka. Setelah semua perubahan telah diuji dan diintegrasikan di branch pengembangan, perubahan tersebut kemudian dapat digabungkan ke branch master.

5. **Feature Branches**: branch fitur sering dikaitkan dengan flag fitur - "toggle" yang mengaktifkan atau menonaktifkan fitur dalam produk. Hal ini memudahkan penyebaran kode ke branch utama dan mengontrol kapan fitur diaktifkan, sehingga memudahkan penyebaran kode awal sebelum fitur tersebar ke end user.

## Branch Naming
Branch naming adalah konvensi penamaan yang digunakan dalam pengembangan perangkat lunak untuk memberi nama cabang dalam sistem kontrol versi seperti Git. Konvensi penamaan ini penting untuk memastikan komunikasi dalam proyek perangkat lunak. Berikut adalah beberapa praktik terbaik dalam penamaan cabang:

1. **Mulai nama cabang dengan kata kelompok**: Kata kelompok bisa apa saja yang cocok dengan alur kerja Anda. Misalnya, "bug" untuk bug yang perlu diperbaiki segera atau "wip" untuk pekerjaan yang sedang berlangsung.
   - Contoh benar: `bug-logo-alignment-issue`, `wip-ioc-container-added`.
   - Contoh salah: `LogoAlignmentIssue`, `IoCContainerAdded`.

    | Category Word | Meaning |
    | --- | --- |
    | hotfix | untuk memperbaiki masalah kritis dengan cepat, biasanya dengan solusi sementara |
    | bugfix | untuk memperbaiki bug |
    | feature | untuk menambah, menghapus, atau memodifikasi sebuah fitur |
    | test | untuk mencoba sesuatu yang bukan merupakan masalah |
    | wip | untuk pekerjaan yang sedang berjalan |

2. **Gunakan ID Unik dalam nama cabang**: Anda bisa menggunakan ID pelacak masalah dalam nama cabang Anda¹.
   - Contoh benar: `bug-123-logo-alignment-issue`, `wip-456-ioc-container-added`.
   - Contoh salah: `bug-logo-alignment-issue`, `wip-ioc-container-added`.

3. **Gunakan tanda hubung atau garis miring sebagai pemisah**: Hindari penggunaan spasi, garis bawah, atau karakter non-alfanumerik.
   - Contoh benar: `feature/new-login`, `bugfix/header-styling`.
   - Contoh salah: `feature_new login`, `bugfix_header styling`.

4. **Hindari penggunaan angka saja**: Jangan gunakan hanya angka dalam nama cabang.
   - Contoh benar: `bug-123-logo-alignment-issue`, `wip-456-ioc-container-added`.
   - Contoh salah: `123`, `456`.

5. **Hindari nama deskriptif yang panjang untuk cabang jangka panjang**: Untuk cabang yang akan ada dalam jangka waktu yang lama, hindari nama yang terlalu panjang¹.
   - Contoh benar: `master`, `develop`, `QA`.
   - Contoh salah: `master-branch-for-final-code`, `development-branch`, `quality-assurance-branch`.


## Conclusion

### GitFlow
GitFlow cocok digunakan untuk proyek yang memiliki siklus rilis yang terjadwal. Adanya Feature Branch Workflow memberikan peran yang sangat spesifik untuk cabang yang berbeda dan menentukan bagaimana dan kapan mereka harus berinteraksi. GitFlow bekerja dengan baik untuk produk dalam model rilis yang lebih tradisional, di mana rilis dilakukan setiap beberapa minggu sekali. Namun, proses ini rusak secara signifikan saat Anda merilisnya sekali sehari atau lebih.

### Trunk Based Development
Trunk Based Development adalah pendekatan pengembangan perangkat lunak di mana pengembang sering mengintegrasikan perubahan kode mereka ke cabang utama. Pendekatan ini cocok untuk tim yang menerapkan prinsip integrasi terus-menerus dan penyebaran terus-menerus. Dengan Trunk Based Development, pengembang dapat dengan mudah mengintegrasikan kode mereka dengan cabang utama. Ketika mereka menyelesaikan pekerjaan baru, mereka menggabungkan perubahan ke cabang utama. Namun, mereka tidak seharusnya menggabungkan ke cabang utama sampai mereka telah menyelesaikan build yang berhasil.