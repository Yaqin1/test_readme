#### Nama : Ahmad Nur Yaqin
#### Kelas : XII RPL-1
#### Absen :10

# Modul 1

### soal 1
#### 1. Lakukan proses instalasi framework laravel kedalam folder dengan nama masing-masing.
```

composer create-project laravel/laravel penjualan

```

# Modul 2
### Soal 1
#### Buatlah migration tabel kategori dengan menggunakan teknik yang telah di pelajari dalam modul ini.

#### langkah pertama.
pertama kita akan membuat folder model kategori, gunakan perintah artisan pada command prompt sebagai berikut.
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

#### langkah ketiga.
selanjutnya kita akan membuat createKategoriTable, dan gunakan perintah comand prompt dibawah ini.

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

#### langkah kelima.
langkah berikutnya membuat kategoriTableSeeder, dengan menggunakan comand prompt dibawah ini.

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
