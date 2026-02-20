# Типи та характеристики SSD-накопичувачів

## 1. SATA SSD

![SATA SSD](https://upload.wikimedia.org/wikipedia/commons/1/1e/Samsung_SSD_850_EVO_250GB.jpg)

**Інтерфейс:** SATA III (6 Гбіт/с)  
**Форм-фактор:** 2.5"  
**Швидкість читання:** до 550 МБ/с  
**Швидкість запису:** до 520 МБ/с  

Переваги:
- Доступна ціна
- Сумісність із більшістю ПК

Недоліки:
- Обмежена швидкість через SATA інтерфейс

---

## 2. NVMe SSD (PCIe)

![NVMe SSD](https://upload.wikimedia.org/wikipedia/commons/0/0b/Samsung_960_PRO_M.2_SSD.jpg)

**Інтерфейс:** PCIe  
**Форм-фактор:** M.2  
**Швидкість читання:** до 7000 МБ/с  
**Швидкість запису:** до 5000 МБ/с  

Переваги:
- Висока швидкість
- Низька затримка

Недоліки:
- Вища ціна
- Потрібна підтримка материнською платою

---

## 3. M.2 SSD

![M.2 SSD](https://upload.wikimedia.org/wikipedia/commons/4/4b/M2_SSD.jpg)

**Типи інтерфейсу:** SATA або NVMe  
**Компактний розмір**

---

# Основні характеристики SSD

- Об’єм пам’яті (GB/TB)
- Швидкість читання/запису
- Тип пам’яті (SLC, MLC, TLC, QLC)
- TBW (ресурс перезапису)
- MTBF (надійність)

---

# Python-скрипт для відображення інформації про встановлений накопичувач

```python
import subprocess

def get_disk_info():
    print("Інформація про накопичувачі:\n")
    subprocess.run(["lsblk", "-o", "NAME,SIZE,TYPE,MODEL"])

if __name__ == "__main__":
    get_disk_info()
