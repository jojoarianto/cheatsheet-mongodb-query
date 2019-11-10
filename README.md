# cheatsheet-mongodb-query
Collection of my queries on mongodb

## Index
- [Update key_answer by test_id and it's number](query_1.md)
- [Add user on spesific database on mongodb](add_user.md)

## Tools
tools yang saya gunakan disini adalah "NoSQLBooster for mongodb"

### Softdelete Voucher (Reset Voucher)
Sebelum menghapus data, pastikan kamu benar-benar paham data seperti apa yang ingin kamu hapus (softdelete). untuk lebih mudah dipahami saya berikan contoh sebagai berikut

Goal : Saya ingin menghapus data voucher where event_id=XXXX

oke, biasanya saya count dulu berapa data voucher dengan event_id XXX
```sql
db.vouchers.count({event_id: "XXXXXX"})
```

output 
```bash
2500
```

Oke berarti saya tahu bahwa saya akan mengubah 2500 data saja. menurut saya ini penting untuk menjadi acuan tujuan kita. Selanjutany, deleting proses

```sql
db.vouchers.update(
    {event_id: "XXXXXX"},
    {$set: {deleted_at: new ISODate("2019-01-11T03:34:54Z") }},
    {multi: true}
);
```

kita tidak benar benar melakukan delete data melainkan softdelete dimana artinya kita menambahkan field deteled_at dengan mengisi sebuah date data disana. Output dari query ini adalah

```bash
WriteResult({ "nMatched" : 2500, "nUpserted" : 0, "nModified" : 2500 })
```

nice, disini dapat kita simpulkan proses update data (softdelete) telah berhasis dan data yang berubah sesuai dengan jumlah yang kita inginkan.


### Softdelete User 
```bash
db.users.update(
    {event_id: "XXXXX"},
    {$set: {deleted_at: new ISODate("2019-01-11T03:34:54Z") }},
    {multi: true}
);
```

output
```bash
WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })
```
---
Thanks!
