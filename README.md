### Repository ini progress crawling API dari shopee

### Goal
- mendapatkan response json berupa nama produk, price, image, dll

### Progress
Di API request Shopee terdapat request header yang wajib ada, dan value dari requet ini sepertinya terencrypt/hash. Dan ketika merubah body payload yang berupa JSON, maka response pun menjadi tidak valid.
Berarti nilai enkripsi/hash ini berkaitan juga dengan body payload. Guna untuk anti tamper.
Parameter yang harus ada dan terenkripsi adalah `Af-Ac-Enc-Dat`, `X-Sap-Ri`. Nilai dari `Af-Ac-Enc-Sz-Token` didapat dari response sebuah request ke `infra shopee`
```json
"X-Sap-Ri": "7cfeb066f4546c3b2badd03d040180d0d7c8823bd18b749aebc0",
"Accept": "application/json",
"Content-Type": "application/json",
"X-Shopee-Language": "id",
"X-Requested-With": "XMLHttpRequest",
"Af-Ac-Enc-Dat": "cd4f0dea7afb98c4",
"X-Csrftoken": "zKaHjThdScywXELhythaXoG1VZQ8kEYu",
"Af-Ac-Enc-Sz-Token": "GJAaAZD0K0JD5qajgs80MQ==|6XMG4HfntE68s1ADG77S15lBMulOYzKAYfMGX5cKvSCgRBRwW+YGor9PciD2BI6mHvv4zqvP3sU=|YdluBpe0dYrGY2XP|08|3",
```
Body Payload
```json
payload = {
    "bundle": "shop_page_category_tab_main",
    "shop_id": "36630xxxx",
    "limit": 30,
    "offset": 60,
    "upstream": "",
    "sort_type": 1
}
```
Proses client untuk melakukan hash/enkrip ada di file `sap-hook-latest.js` atau di bagian `module.js`

### Conclusion
Mungkin sekian dulu progress untuk Shopee crawling ini, diharapkan jika ada orang bisa sharing ilmu mengenai reversing di bagian JS nya, saya sangat berterima kasih
