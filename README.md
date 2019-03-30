# RajaOngkir
[![Latest Stable Version](https://poser.pugx.org/steevenz/rajaongkir/v/stable)](https://packagist.org/packages/steevenz/rajaongkir) [![Total Downloads](https://poser.pugx.org/steevenz/rajaongkir/downloads)](https://packagist.org/packages/steevenz/rajaongkir) [![Latest Unstable Version](https://poser.pugx.org/steevenz/rajaongkir/v/unstable)](https://packagist.org/packages/steevenz/rajaongkir) [![License](https://poser.pugx.org/steevenz/rajaongkir/license)](https://packagist.org/packages/steevenz/rajaongkir)

[RajaOngkir][11] API PHP Class Library berfungsi untuk melakukan request API [RajaOngkir][11].

Fitur
-----
- Support seluruh tipe akun RajaOngkir (Starter, Basic, Pro).
- Support mendapatkan biaya ongkos kirim berdasarkan berat (gram) dan volume metrics (p x l x t - otomatis akan dikonversi ke satuan gram). 

Instalasi
---------
Cara terbaik untuk melakukan instalasi library ini adalah dengan menggunakan [Composer][7]
```
composer require ruanglabs/rajaongkir
```
PHP Framework yang mendukung instalasi diatas:
1. O2System Framework
2. Laravel Framework
3. Yii Framework
4. Symfony Framework
5. CodeIgniter Framework

Instalasi pada framework lain atau PHP Native
```php
require_once('path/to/ruanglabs/rajaongkir/src/autoload.php');
```
Implementasi / Penggunaan Untuk Framework yii Dan Menampilkan Ke Gridview / DataTables
---------------------
Library GridView Menggunakan Library [Kartik][3] 
- Membuat Controller 
 example : ApiRajaongkir.php
 
 ```php
<?php
  /**
   * Created by PhpStorm.
   * User: archeta
   * Date: 25/03/2019
   * Time: 15.10
   */
  
  namespace backend\controllers;
  
  require 'D:\xampp\htdocs\ngoprektoko\vendor\autoload.php';
  
  use Ruanglabs\Rajaongkir;
  use yii\data\ArrayDataProvider;
  use yii\web\Controller;
  
  
  class ApiRajaongkir extends Controller
  {
  	public $enableCsrfValidation = true;
  
  	public function actionIndex()
  	{
  		$rajaongkir = new Rajaongkir('c66cf95cc5b981ca2967077a3e684cb8', Rajaongkir::ACCOUNT_STARTER);
  
  		$config['api_key'] = 'c66cf95cc5b981ca2967077a3e684cb8';
  		$config['account_type'] = 'starter';
  
  		$rajaongkir = new Rajaongkir($config);
  
  		/*
  		 * --------------------------------------------------------------
  		 * Mendapatkan list seluruh propinsi
  		 * --------------------------------------------------------------
  		 */
  		$provinces = $rajaongkir->getProvinces();
  		
  
  //		$lazada->GetBrands($limit = 100, $offset = 0);
  //		echo $provinces;
  		$dataProvider = new ArrayDataProvider([
  			'allModels' => $provinces,
  			'pagination' => [
  				'pageSize' => 10,
  			],
  //			'sort' => [
  //				'attributes' => ['id'],
  //			],
  
  		]);
  //		print_r($data);
  //		print_r($data);
  		return $this->render('index', [
  			'dataProvider' => $dataProvider,
  		]);
  	}
  }
 ```
 
 - Membuat View Index 
 
 example : rajaongkir-view.php
 
 ```php
<?php
/**
 * Created by PhpStorm.
 * User: archeta
 * Date: 25/03/2019
 * Time: 15.12
 */

/**
 * @var $dataProvider \yii\data\ArrayDataProvider
 * @var $searchModel  \
 */

?>
<div class="rajaongkir-view-index">

	<?php // echo $this->render('_search', ['model' => $searchModel]); ?>

	<?= yii\grid\GridView::widget([
		'dataProvider' => $dataProvider,
		'filterModel' => $kota,
		'columns' => [
			'province_id',
			'province',
		],
	]); ?>

</div>
 ```

Bugs and Issues
---------------
Jika anda menemukan bugs atau issue, anda dapat mempostingnya di [Github Issues][6].

Requirements
------------
- PHP 5.6+
- [Composer][9]
- [O2System Curl][10]

Referensi
---------
Untuk mengetahui lebih lanjut mengenai RajaOngkir API, lihat di [Dokumentasi RajaOngkir][12].

[3]: http://demos.krajee.com/grid
[6]: http://github.com/ruanglabs/rajaongkir/issues
[7]: https://packagist.org/packages/
[9]: https://getcomposer.org
[10]: http://github.com/o2system/curl
[11]: http://rajaongkir.com
[12]: http://rajaongkir.com/dokumentasi
"# rajaongkir" 
