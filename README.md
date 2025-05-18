
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



# کار با ابزار `fdisk` در لینوکس

### ✅ مشاهده پارتیشن‌های دیسک  
```bash
sudo fdisk -l
```

**مثال:**

```
Disk /dev/sda: 100 GB
Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1  *     2048 104857599 104855552  50G 83 Linux
/dev/sda2       104857600 209715199 104857600 50G 83 Linux
```

---

### ✅ انتخاب دیسک برای پارتیشن‌بندی

```bash
sudo fdisk /dev/sda
```

---

### ✅ ایجاد پارتیشن جدید

1. وارد ابزار `fdisk` شوید:

   ```bash
   sudo fdisk /dev/sda
   ```
2. ایجاد پارتیشن جدید:

   * وارد کردن `n` و زدن Enter
   * انتخاب `primary` یا `extended`
   * تعیین شماره پارتیشن (مثلاً `3`)
   * تعیین شروع و پایان پارتیشن (مثلاً `+10G`)

---

### ✅ مشاهده جدول پارتیشن‌ها

```bash
p
```

---

### ✅ ذخیره تغییرات

```bash
w
```

---

### ✅ حذف پارتیشن

1. وارد `fdisk` شوید:

   ```bash
   sudo fdisk /dev/sda
   ```
2. وارد کردن `d` و سپس شماره پارتیشن (مثلاً `3`)

---

### ✅ تغییر نوع پارتیشن

1. وارد `fdisk` شوید:

   ```bash
   sudo fdisk /dev/sda
   ```
2. وارد کردن `t`
3. انتخاب شماره پارتیشن (مثلاً `1`)
4. وارد کردن نوع پارتیشن (مثلاً `83` برای Linux)

---

### ✅ خروج بدون ذخیره تغییرات

```bash
q
```


