## Посадка 

Посадка выполняется в 3 этапа:
1. Перелет к предпологаемой зоне посадки и завесание на высоте 1.5м
2. Спуск до высоты в 0.85м с 3 корректировками по координат маркера относительно aruco_map
3. Спуск в течении нескольких секунд с постоянной корректировкой по координатам маркера посадки в системе координат body (так как aruco маркеры могут быть уже не видны), вместо navigate используется set_position


<video autoplay loop src="https://github.com/vas0x59/ior2020_uav_L22_AERO_info/raw/master/to_Gitbook/content/l2.mp4" height="400" ></video>