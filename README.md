# php-graph-sdk-codeigneter
> Login atau register menggunakan API Facebook dengan Codeigneter dan menginputkan data pengguna facebook ke database.

## Persyaratan
- PHP 5.6
- [CodeIgniter-3.1.10](http://www.codeigniter.com/)
- [Facebook SDK for PHP (v5)](https://github.com/facebook/php-graph-sdk)
- [Composer](https://getcomposer.org/)

## Pengumuman

Jika anda menggunakan xampp atau domain belum tersertifikat (https), diharuskan menggunakan browser [Opera Mini](https://www.opera.com/).

## Langkah - Langkah Penggunaan
**ikutilah langkah-langkah ini agar tidak terjadi error**

1. Buka file composer `composer.json` pada file codeigneter anda. dan lihat:
```php
  "require-dev": {
		"mikey179/vfsStream": "1.1.*",
		"phpunit/phpunit": "4.* || 5.*"
	}
 ```
diganti dengan
```php
  "require-dev": {
		"mikey179/vfsstream": "1.1.*",
		"phpunit/phpunit": "4.* || 5.*"
	}
 ```
2. Download [Facebook SDK for PHP (v5)](https://github.com/facebook/php-graph-sdk) menggunakan [Composer](https://getcomposer.org/) `composer require facebook/graph-sdk`. untuk penginstalan [Facebook SDK for PHP (v5)](https://github.com/facebook/php-graph-sdk) diletakkan diluar folder application (atau di dalam folder project anda).
3. di file Codeignter anda `/application/config/config.php`, pada code `$config['composer_autoload'] = False` ganti dengan `$config['composer_autoload'] = "vendor/autoload.php";` . [selengkapnya](https://www.codeigniter.com/user_guide/general/autoloader.html).
4. di file Codeignter anda `/application/config/autoload.php`, pada code `$autoload['libraries']`  dan `$autoload['helper']` tambahkan:

```php
$autoload['libraries'] = array('session','database');
$autoload['helper'] = array('url');
```
5. download file php-graph-sdk-codeigneter
6. Buatlah sebuah database dan table
```php
CREATE TABLE `users` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `oauth_provider` enum('','facebook','google','twitter') COLLATE utf8_unicode_ci NOT NULL,
 `oauth_uid` varchar(50) COLLATE utf8_unicode_ci NOT NULL,
 `first_name` varchar(25) COLLATE utf8_unicode_ci NOT NULL,
 `last_name` varchar(25) COLLATE utf8_unicode_ci NOT NULL,
 `email` varchar(25) COLLATE utf8_unicode_ci NOT NULL,
 `picture` varchar(200) COLLATE utf8_unicode_ci NOT NULL,
 `link` varchar(100) COLLATE utf8_unicode_ci NOT NULL,
 `created` datetime NOT NULL,
 `modified` datetime NOT NULL,
 PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```
7. Jangan lupa di file `/application/config/database.php` di atur sesuai database anda.
8. Sesuaikan file yang telah di sediakan sebagai berikut: 
```php
├── application/
│   ├── config/
│   │   └── facebook.php
│   ├── controllers/
│   │   └── User_authentication.php
│   ├── libraries/
│   │   ├── Facebook.php
│   ├── models/
│   │   └── User.php
│   └── views/
│       └── user_authentication/
│           └── index.php
└── vendor

```
**kecuali folder vendor, (Folder ini didapatkan ketika instalasi [Facebook SDK for PHP (v5)](https://github.com/facebook/php-graph-sdk) menggunakan [Composer](https://getcomposer.org/))**

9. pada file `/application/config/facebook.php`, sesuaikan
```php
$config['facebook_app_id'] = 'your_facebook_app_id';
$config['facebook_app_secret'] == 'your_facebook_app_secret';
```
10. Finally. Buka Browser opermini anda dan ketikkan link `https://www.domain-anda.com/user_authentication/`.
11. selamat Menikmati


### Referensi
- https://www.codexworld.com/facebook-login-codeigniter/
