
# کار با ابزار `parted` در لینوکس

### ایجاد پارتیشن جدید  
1. اجرای `parted`:  
   ```bash
   sudo parted /dev/sda
   ```


2. ایجاد جدول پارتیشن:

   ```bash
   (parted) mklabel gpt
   ```
3. ایجاد پارتیشن جدید:

   ```bash
   (parted) mkpart primary ext4 1MiB 10GiB
   ```
4. خروج از `parted`:

   ```bash
   (parted) quit
   ```

---

### نمایش پارتیشن‌ها

```bash
sudo parted /dev/sda print
```

**مثال:**

```
Number  Start   End    Size    Type     File system  Flags
 1      1MiB    10GiB  10GiB   primary  ext4
```

---

### تغییر اندازه پارتیشن

```bash
sudo parted /dev/sda resizepart 1 15GiB
```

---

### حذف پارتیشن

```bash
sudo parted /dev/sda rm 1
```

---

### تغییر نوع پارتیشن

```bash
sudo parted /dev/sda set 1 boot on
```

---

### بررسی دیسک برای خطاها

```bash
sudo parted /dev/sda check 1
```


