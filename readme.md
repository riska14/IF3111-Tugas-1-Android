# Tugas 1 Android

Aplikasi ini adalah aplikasi android yang membantu Tom untuk mencari dan menangkap Jerry. 
Aplikasi ini dibuat untuk berkomunikasi dengan Spike untuk mengetahui lokasi dan lama persembunyian Jerry di lokasi tersebut, juga dapat melaporkan penangkapan Jerry kepada Spike.

## Latar Belakang
Di kawasan ITB, terdapat banyak kucing yang berkeliaran. Salah satu kucing yang paling populer di ITB adalah Tom. Tom adalah kucing pemburu tikus yang paling handal di ITB. 
Suatu hari, ia bertemu dengan Jerry, seekor tikus yang sangat lihai dalam mencari makanan dan bersembunyi. Karena kelihaian Jerry, Tom tidak mampu mengejar dan menangkap Jerry ketika berkeliaran. 
Satu-satunya kesempatan untuk menangkap Jerry adalah ketika Jerry masih ada di dalam persembunyian. Bersegeralah karena Jerry akan berpindah posisi secara berkala!
Tom mempunyai teman seekor anjing pelacak yang bernama Spike. Dengan bantuan Spike, Tom dapat melakukan tracking terhadap tempat persembunyian Jerry. 
Selain itu, Tom juga perlu melapor ke Spike untuk menghindari kaburnya Jerry. Jerry seringkali berpindah tempat persembunyian dalam jangka waktu tertentu. 
Spike dapat memberitahu posisi persembunyian Jerry saat itu dan berapa lama Jerry bersembunyi di tempat itu.

## Spesifikasi Aplikasi
Functional Requirement
	1. GPS Tracking
		Posisi yang diberikan Spike berbentuk latitude dan longitude. Lama persembunyian Jerry juga diberikan dalam waktu UTC+7. Setelah waktu persembunyian habis, posisi Jerry akan berubah. 
		Aplikasi dapat menampilkan posisi Jerry. Jenis tampilan yang digunakan adalah map, dengan location untuk menunjukkan posisi Jerry.
	2. Geomagnetic Sensor
		Kompas yang dibuat dengan memanfaatkan Geomagnetic Sensor digunakan untuk menunjukkan arah utara dan selatan dengan benar.
	3. QR-Code Scanner
		Untuk menangkap Jerry, harus dilakukan scanning token dari QR-code yang disediakan dan dikirimkan ke server.
				
Non Functional Requirement
	- Menggunakan Android API 10 (GingerBread)
	- user friendly, user tidak perlu selalu menekan tombol refresh untuk mendapatkan informasi terbaru dari Spike
	- Source code cukup terstruktur
	- Membutuhkan daya yang tidak terlalu besar
		

## Spesifikasi Endpoint
Alamat Server: 167.205.32.46/pbd
	
TRACK : [GET] /api/track?nim=13512062
	pemanggilan:
	/api/track?nim=13512062 (167.205.32.46/pbd/api/track?nim=13512062)
	
	kembalian:
	{
	“lat”: “-6.890323” // Koordinat latitude tujuan
	“long”: “107.610381” // Koordinat longitude tujuan 
	“valid_until”:1425833999 // Date dalam format UTC+7 kapan token hangus
	}
		
CATCH : [POST] /api/catch
	Header request:
	Content-type: application/json
	
	Parameter request:
	token := “CONTOHTOKEN”
	nim := “13512062”
		
	body request:
	{"nim": "13512062", "token": "secret_token"}
		
	Response status:
		- status: 200 OK (Apabila pengumpulan sukses dengan token sesuai)
		- status: 400 MISSING PARAMETER (Apabila parameter yang dikirim tidak lengkap)
		- status: 403 FORBIDDEN (Apabila terdapat parameter yang salah)

## License
