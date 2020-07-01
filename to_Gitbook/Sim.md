## Gazebo
Из за отсутвия возможности тестирования кода на своем реальном дроне мы решили воспользоваться симулятором Gazebo.

Для запуска пакета ПО Клевера в симуляторе можно использовать [наш набор скриптов](https://github.com/vas0x59/clever_sim) или [оригинальную инструкцию от PX4](https://dev.px4.io/v1.9.0/en/simulation/ros_interface.html).

Для Innopolis Open мы сделали несколько тестовых сцен. [ior2020_uav_L22_AERO_sim](https://github.com/vas0x59/ior2020_uav_L22_AERO_sim) 

<img src="https://github.com/vas0x59/ior2020_uav_L22_AERO/raw/master/to_Gitbook/content/real_map.jpg" height="250">
<img src="https://github.com/vas0x59/ior2020_uav_L22_AERO/raw/master/to_Gitbook/content/big_map.jpg" height="250">

Также использование симулятора ускорило отладку полного выполнения кода, так как мы смогли добиться real time factor=2.5


