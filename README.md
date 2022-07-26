#### Nama : Ahmad Nur Yaqin
#### Kelas : XII RPL-1
#### Absen :10

# Modul 1

### soal 1
#### 1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing.

#### pertama kita akan merubah title nama.

![image](https://user-images.githubusercontent.com/109929695/180903949-1a715f38-b3a8-4fe9-ac73-b87298dd8edb.png)

#### langkah kedua.
kita akan memasukkan comand prompt cmd.
```
composer create-project laravel/laravel penjualan

```
![image](https://user-images.githubusercontent.com/109929695/180904289-ef85729b-a442-48f8-877a-bca8d07bda43.png)


# Modul 2
### Soal 1
#### Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam modul ini.

#### langkah pertama.
pertama kita akan membuat folder model kategori, gunakan perintah artisan pada terminal VS CODE sebagai berikut.
```
php artisan make:model kategori
```

#### langkah kedua.
lalu kita edit isi kategori sebagai berikut.

```
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class kategori extends Model
{
    use HasFactory;

    protected $table = 'kategori';
}

```

![image](https://user-images.githubusercontent.com/109929695/180904779-e3196608-8819-49c6-a8cd-246b17d0b3eb.png)


#### langkah ketiga.
selanjutnya kita akan membuat createKategoriTable, dan gunakan perintah artisan di terminal VS CODE dibawah ini.

```
php artisan make:migration create_kategori_table
```

#### langkah keempat.
selanjutnya kita isi createKategoriTable seperti dibawah ini.

```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('kategori', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('kategori');
    }
};
```
![image](https://user-images.githubusercontent.com/109929695/180904825-9d2ab354-a4be-491c-9495-e81d8c40c6ea.png)


#### langkah kelima.
langkah berikutnya membuat kategoriTableSeeder, dengan menggunakan perintah artisan di terminal VS CODE dibawah ini.

```
php artisan make:seeder kategoriTableSeeder
```

#### langkah keenam.
kemudian kita tambahkan use DB; agar bisa dijalankan, dan isi kategoriTableSeeder sebagai berikut.

```
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use DB;

class kategoriTableSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        DB::table('kategori')->insert(array(
            [
                'name'=>'perlengkapan sekolah',
            ],
            [
                'name'=>'komputer',
            ],
            [
                'name'=>'sabun',
            ],
            [
                'name'=>'accesoris',
            ],
            [
                'name'=>'atk',
            ]
            ));
    }
}

```
![image](https://user-images.githubusercontent.com/109929695/180904881-3bfcac4d-31cb-49d2-89f2-c2d9f6cabf34.png)


#### langkah ke tujuh.
lalu kita akan menambahkan codingan di modul DatabaseSeeder seperti berikut.

```
<?php

namespace Database\Seeders;

// use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(produkTableSeeder::class);
        $this->call(kategoriTableSeeder::class);

    }
}

```
![image](https://user-images.githubusercontent.com/109929695/180904916-cc47df4c-e88e-4e6c-9866-2a756aae5d28.png)


### soal 2
#### 2. Berikan data dengan menggunakan seeder yang telah anda pelajari pada modul ini.

Seeder digunakan untuk membuat contoh data pada database. Fitur ini sangat bermanfaat saat 
melakukan pengembangan suatu sistem yang dimana kita memerlukan suatu contoh data. Apalagi 
ketika membutuhkan contoh data yang banyak, fitur ini dapat membantu dari pada memasukan data 
satu persatu scara manual melalui PhpMyAdmin.
