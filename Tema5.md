# Типи та характеристики SSD-накопичувачів

## 1. SATA SSD

![SATA SSD](https://content.rozetka.com.ua/goods/images/big/37854461.jpg)

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

![NVMe SSD](https://content1.rozetka.com.ua/goods/images/big/598491855.jpg)

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
#!/usr/bin/env python3

import subprocess

def run_command(command):
    """Виконує системну команду та повертає результат."""
    try:
        result = subprocess.run(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
        return result.stdout
    except Exception as e:
        return f"Помилка виконання команди: {e}"

def show_basic_disk_info():
    print("\n=== БАЗОВА ІНФОРМАЦІЯ ПРО НАКОПИЧУВАЧІ ===\n")
    print(run_command(["lsblk", "-o", "NAME,SIZE,TYPE,MOUNTPOINT"]))

def show_model_info():
    print("\n=== МОДЕЛЬ ТА ВИРОБНИК ДИСКА ===\n")
    print(run_command(["lsblk", "-d", "-o", "NAME,SIZE,MODEL"]))

def show_detailed_info():
    print("\n=== ДЕТАЛЬНА ІНФОРМАЦІЯ (потрібні права sudo) ===\n")
    print(run_command(["sudo", "lshw", "-class", "disk"]))

def main():
    print("Програма відображення технічної інформації про накопичувач\n")
    show_basic_disk_info()
    show_model_info()

    choice = input("Показати детальну інформацію? (y/n): ")
    if choice.lower() == "y":
        show_detailed_info()
    else:
        print("Завершення роботи.")

if __name__ == "__main__":
    main()
