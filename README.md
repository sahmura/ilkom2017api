# Ilkom2017API
Ilkom2017api merupakan sebuah API sederhana untuk mendapatkan informasi umum perkuliahan, informasi beasiswa, dan jadwal perkuliahan.
API ini bisa digunakan hanya orang tertentu saja karena membutuhkan api key untuk mengaksesnya.

# Penggunaan
Adapun cara penggunaannya adalah sebagai berikut.

Alamat utama dari API ini adalah

```
old :

MAINURL = https://ilkomunnes.000webhostapp.com/api

new :

MAINURL = https://ilkom2017api.herokuapp.com/api
```


Fungsi yang tersedia hanya GET. Berikut parameternya.


1. Mendapatkan semua list informasi

```
MAINURL/info/all/{APIKEY}
```

2. Mendapatkan informasi berdasarkan ID

```
MAINURL/info/{id}/{APIKEY}
```

3. Mendapatkan semua list informasi beasiswa

```
MAINURL/beasiswa/all/{APIKEY}
```

4. Mendapatkan informasi beasiswa berdasarkan ID


```
MAINURL/beasiswa/{id}/{APIKEY}
```

5. Mendapatkan list semua jadwal

```
MAINURL/jadwal/all/{APIKEY}
```

6. Mendapatkan list semua jadwal berdasarkan hari

```
MAINURL/jadwal/hari/{hari}/{APIKEY}
```

7. Mendapatkan list semua jadwal berdasarkan rombel

```
MAINURL/jadwal/rombel/{rombel}/{APIKEY}
```

8. Mendapatkan list semua jadwal berdasarkan rombel dan hari

```
MAINURL/jadwal/hari/{hari}/rombel/{rombel}/{APIKEY}
```

10. Mendapatkan list jadwal pada hari itu

```
MAINURL/jadwal/{APIKEY}
```


# Hasil respon
Hasil respon yang memungkinkan.


#### Jika tidak ditemukan

```json
{
"koneksi":true,
"status":"NotFound",
"data":null
}
```

#### Jika ditemukan, untuk info / beasiswa

```json
{
"koneksi":true,
"status":"NotFound",
"data":[
	{
		"id": "string",
		"dari": "string",
		"judul": "string",
		"pesan": "string",
		"date": "string"
	}

	{
		"..."
	}
]
}
```


#### Jika ditemukan untuk jadwal

```json
 {
 "koneksi":true,
 "status":"Success",
 "data":[
        {
            "id": "string",
            "makul": "string",
            "hari": "string",
            "jam": "string",
            "tempat": "string",
            "rombel": "string",
            "kode_hari": "string"
        }
 
        {
            "..."
        }
 ]
 }
 ```


#### Jika ditemukan untuk beberapa kondisi jadwal yang menghasilkan hasil dua rombel sekaligus

 ```json
 {
 	"koneksi": true,
 	"status": "Success",
 	"data":
 		{
 			"rombel 1":
 				{
 					"id": "string",
 					"makul": "string",
 					"hari": "string",
 					"jam": "string",
 					"tempat": "string",
 					"kode_hari": "string"
 				}
 				{
 					"..."
 				}
 		}
 		{
 			"rombel 2":
 				{
 					"id": "string",
 					"makul": "string",
 					"hari": "string",
 					"jam": "string",
 					"tempat": "string",
 					"kode_hari": "string"
 				}
 				{
 					"..."
 				}
 		}
 }
 ```


Dalam json decode PHP, untuk mengakses data di atas jika sudah dijadikan array assosiatif adalah 

 ```php
$get = file_get_contents('URI API');
$decode = json_decode($get, true);

$rombel1 = $decode['data'][0]['rombel 1'];
$rombel2 = $decode['data'][1]['rombel 2'];
```
