## Gazebo
По причине отсутвия возможности тестирования кода на своем реальном дроне было принято решение воспользоваться симулятором Gazebo.

Для запуска пакета ПО Клевера в симуляторе можно использовать [набор скриптов](https://github.com/vas0x59/clever_sim) или [оригинальную инструкцию от PX4](https://dev.px4.io/v1.9.0/en/simulation/ros_interface.html).

Для Innopolis Open было создано несколько тестовых сцен. [ior2020_uav_L22_AERO_sim](https://github.com/vas0x59/ior2020_uav_L22_AERO_sim)

Также использование симулятора ускорило отладку полного выполнения кода, так как запуск производился с real time factor=2.5

<img src="https://github.com/vas0x59/ior2020_uav_L22_AERO_info/raw/master/to_Gitbook/content/real_map.jpg" height="250">
<img src="https://github.com/vas0x59/ior2020_uav_L22_AERO_info/raw/master/to_Gitbook/content/big_map.jpg" height="250">

При тестировании выявлены некоторые проблемы(некорректное положение aruco_map) с использованием дисторсии в плагине камеры, по этому в симуляторе использовалась камера типа Pinhole (без искожений от объектива)

