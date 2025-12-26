	Ecfinder - программа для поиска и автоматического сохранения в файл прошивок мультиконтроллеров (EC), клавиатурных контроллеров (KBC), биосов и их кусков, в любых бинарных файлах: дампы, обновления с оф сайта и тд

 
 И не только!

	Заодно ищет и сохраняет и основные прошивки биоса или его часть и ряд клавиатурных контроллеров (встречаются редко)

	Автоматическое преобразование SPD DDR3 в SPD DDR3L с правкой контрольной суммы: 
Алгоритм срабатывает при открытие файла размером строго 256 байт (размер eeprom SPD 24c02/34c02), 
дальше идет проверка, что это SPD DDR3 и если да - изменяется в DDR3L (с правкой CRC), файл сохраняется в папку исходного файла; если нет - выход
В консольном режиме файл открывать без параметров: ECFinder.exe filepath-путь-к-файлу

Режим csefix:
Исправляет ошибки при открытии прошивок Intel с ME регионом 15.x и 16.x версий в утилитах Intel Flash Image Tool (FIT) и Modular Flash Image Tool (MFIT), типа:
Error 179: [Fit Actions] Failed to parse CSE region. 
Error 10: [Ifwi Actions] Failed to decompose Region. Failed to decompose CSE data.
Error 18: [Ifwi Actions] Failed to generate decomposed files. CSE Region
Error 18: [Ifwi Actions] Failed to generate decomposed files.
используется только для открытия прошивки в утилите для последующей очистки ME региона, просто патченный файл не шить!
Запустить файл csefix.cmd или через консоль ecfinder.exe -csefix (или ecfinder.exe -csefix путь-имя-файла), указать файл - патченный сохранится рядом автоматически

Режим skipec:
Пропускает этап поиска прошивок мультиконтроллеров (EC), клавиатурных контроллеров (KBC)

Поддерживает / program features:

- Мультиконтроллеры(EC) ENE, ITE, Nuvoton, MEC
- Клавиатурных контроллеров (KBC) it8171 / it8176 / IT891x 56kb,  it829x 120kb
- PD Type-C ITE885x 64kb
- BIOS update:
AMI "hidden" CSE ME / PMC / PCHC / PHY regions update extracting (*.CSME_xx.x.x.xxxx_extracted_update.bin)
AMI PFAT (*uncut_region.bin is the sum of all parts from an update; *main.bin - presumable cutting)
Asus CAP (*.cap... extract from an update)
Lenovo CAP (*.cap... extract from an update)
Insyde h2o update (*.fd, isflash.bin... extract from an update)

detect (CS)ME region version
detect Boot Guard Status (ME version 12-18)
save OEM Public Key Hash to a ...info.txt file
save Windows license key starting address (HEX) to a ...info.txt file

- SPD DDR3 ----> SPD DDR3L
- Fixing CSE region / CSE data errors in Intel Flash Image Tool 15.x and Modular Flash Image Tool 16.x


Использование / How to use:

При простом запуске утилиты будет предложено указать файл путем его перетаскивания в окошко или, нажав Enter, откроется окно выбора файла
Из exe обновлений файл нужно будет сначала извлечь и найти (если есть)
You have to extract and find an update/bios file from *.exe
Open file by drag and drop or window manager (press enter)

Консольный режим работы / Console (CMD):
Usage: ECFinder.exe -x filepath-путь-к-файлу
x = 128, 160, 192, 256, 288, 384, 512, 768, 1024 or IT5679
Example/Пример: ECFinder.exe -128 d:\file.bin

**режим csefix / csefix mode**
ecfinder.exe -csefix
ecfinder.exe -csefix filepath-путь-к-файлу

**режим skipec / skipec mode**
ecfinder.exe -skipec
ecfinder.exe -skipec filepath-путь-к-файлу


Системные требования / Requirements:
Win7x64 и новее
Интернет / Internet !!!