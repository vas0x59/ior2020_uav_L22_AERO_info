## Основной код
При реализации кода в первоначальной концепции использовались свои типы сообщений, множество нод и других возможностей ROS, для обеспечение этого функционала необходимо создавать пакет и компелировать его, но из-за специфики соревнованиии(использование одной sd карты для все команд) весь код был объединен в один файл (900 строк :). Данный подход усложнил отладку, но упростил запуск на площадке.

1. Взлет 
1. Распознование QR-Кода
1. Поиск цветных маркеров
1. Посадка
1. Генерация отчета и видео 

<!-- Итоговые координаты маркеров основываються на полученных из системы распознования за весь полет, которые автоматически группируються и усредняються. -->
Итоговыми координатами маркеров являются автоматически сгруппированные и усредненные данные из системы распознования полученных за весь полет.
Для покрытие всей территории была выбрана траектория "Зиг-заг".
Для отладки применен симулятор Gazebo.


<!-- **1. Взлет.** Одна из самых простых частей программы, совершается взлет на высоту 1.5 метров, а затем снижаемся до 1 метра для распознавания QR-кода.   -->
<!-- **2. QR-код.** Для этого используется библиотека PyZbar. Чтобы дрон точно распознал QR-код, мы производим полет на небольшой высоте по точкам вокруг места расположения QR-кода.  
**3. Полет.** Перед взлетом генерируется список точек в виде зиг-зага, по которым и производится полет. Мы летаем по такому маршруту для увеличения точности определения координат цветных меток.  
**4. Распознавание цветных маркеров.** С помощью библиотеки OpenCV, мы распознаем цвета маркеров, тем самым определяя их тип. А с помощью функции ```cv2.solvePNP()``` происходит определение их координат в системе координат поля.  
**5. Посадка** Она реализована из нескольких фаз, состоящих из разных корректировок относительно места посадки (сначала происходит "грубая" коррекция положения коптера, далее идут более точные), что позволило нам совершить несколько удачных посадок.  
**6. Запись логов** Запись видео и текстовых отчетов позволила нам проанализировать совершенный полет, затем мы могли внести изменения в код, чтобы он стал еще лучше.  
**7. Симулятор** Также в нашем распоряжении был симулятор, позволявший нам протестировать код до его запуска на реальном дроне, что избавило нас от ситуаций, когда наш код вылетал с ошибкой во время полета. [Симулятор](https://github.com/vas0x59/clever_sim) -->