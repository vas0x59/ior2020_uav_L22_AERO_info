# Innopolis Open 2020


## Команда 
<ul style="list-style: none; font-size:15px; padding-left:10px">
 <li><b>Юрьев Василий</b></li>
 <li><b>Оконешников Дмитрий</b></li>
 <li><b>Антонов Георгий</b></li>
</ul>

## Описание задачи финала

Внедрение новых технологий происходит в различных отраслях экономики в том числе и в сельском хозяйстве. Дроны или БПЛА не стали исключением. Благодаря применению беспилотников оценка состояния сельскохозяйственных территорий и анализ компонентов ландшафта стали более доступными и эффективными. 


<div style="display: inline-block; vertical-align: top;">
<p align="center"><img src="https://lh3.googleusercontent.com/EC9SW_yuIq46aqxf6jpyVJhft5Fjxbned75RMcv_XLYABa6Qobz1fZRM1J0SzlMGRw_cpCa2Z6wyH-uG5r9TNzauScajpE0VxXtNL72UN1aSMs5hL1a3cpjw4L6mIkMia7zpKZIem5vRsc6YxLLcOl7hNknlfcMzPk8GZ7k11IfZzodiPCEjasy_sz4NGsXN0t7r207DQkJdkTCCkOonBNItijZQpPMIFfdDoS2wj8pGrl4r5cmWzWz2T0SEnfkgq_NypHYluFUMMCO1AVgJEbPu9bh5dhd-Vmqy56q12EV8ZAy7ASd-loL_THEos1kWhYMe4mq3UCzTj46E20uBd2MYUIBX1Vff-mug__CGVEJQlMsSolpHG6lw-Z8LufgMBOgIma-a8SmqQyZykyFDUFZ4crDeJwKBYJ0jAdKPSOGhE7LBznajePEFdu_vZKyZuwm0qSim9e5vvNuSUqZcaYL1dOxScabbu0mPgS05qVhnEkcSH_4eZ38hm95D3xj0Ry0qbemf7fmsFk40R8ud8_OZ88lnPFa8C64L7YXvtBt-MZ87DsaLrEEwZMblqSLqr5oXQtNAs-aH5KOtYCSLp8Dk0ZLLaJ9cbsS-WALlGnKg24sUgfWkf3Y_IflsyaYHahbOdZwd7whdEqEvjC2uYAdibDZdmUO0ed_0iTyN99x7VoRdtzspb4s-s6zTE4jx5EHzwQ=w1920-h625-ft" width="300"></p>  
<p><i>Один из вариантов поля</i></p>
</div>
<div style="display: inline-block; vertical-align: top;padding-left:50px; width:50%">
<p>
Финальная задача Innopolis Open 2020 была посвящена мониторингу сельскохозяйственных территорий и состояла из следующих элементов:
</p>
<ul style="list-style-type: decimal; font-size:15px; padding-left:10px">
 <li>Взлет (с QR-кода) и посадка (на цветной маркер небольшего размера).</li>
 <li>Распознавание зашифрованного сообщения в QR-коде.</li>
 <li>Распознавание цвета объектов (цветных маркеров – условное обозначение сельхоз угодий).</li>
 <li>Определение их координат (расположение на поле изменяется).</li>
 <li>Отчет по полученным данным.</li>
</ul>
</div>

# Код
## Github [https://github.com/vas0x59/ior2020_uav_L22_AERO](https://github.com/vas0x59/ior2020_uav_L22_AERO)




## QR-код

<div style="display: inline-block; vertical-align: top;">
<img src="https://lh3.googleusercontent.com/0FGhp05Cek_U63x4aRgD0DKrcoNSwvonOtrR16Zk3ol-8Owg3ir8DKw3bts7PU5V8x5kdCoL4466qY6BYLvZNuLpDYsnwZKu_NslfenqrjSVfqQZ68DXzKiYRbXKF3ALhHGjFWyb9SuwrYU3VDzdFJUsCAF_80I95Bo6e2eUxmxfWUZQt5Wxp7ilyg0Q2LzisLVsgj82tzR5TYaQ2kPRPqpoBb4hzleGs3p5yt4PoCS00QiMIjcMqcgejaML8musmMJ3Kh6zCThLzgkzv8r2LFFjotQadaZ_BkSDe6h-YaU_10bXD-Med-BFzwKW4NRYRMBBhthSVy0yarC0jZcbz55rlN8IhHio_729xUH7FXx--XNNtJ08DKDmE0lVnsnZmWq6o1JEYTthbG8Lo5I3O2pyzkUwBQwSkKUnhksrkQ32BiFInpgT2tEvGILCxjrOdsWRXK81s2KqoUMWWZ7o1DUPxQIBA-v2O-oPxh8Ao-9fPck_ohxWw_OgjopUNh4WtFfhoy26MXq0dCPs2ItcI2jS54W5CgV41tEQyHkf2TUIZRc_AE5b_zZGYLKnx3H0cfOqLj0qwyKpvEKxCteM7cyPNoQaNX2tg_50wJdZe9A3cN6EN5cIud8Ou851RotAFO5miHFyGzpZXNyIGe5_1onyctZ6vaLb1PRrwUbBoXHzjlv7PY7X9e93A4i5n-9-Hpsy9Q=w1920-h937-ft" width="400" >
<p><i>Момент распознавания QR-кода во время зачетной попытки</i></p>
</div>
<div style="display: inline-block; vertical-align: top;padding-left:20px; width:50%">
<p>
Для выполнения задачи распознавания QR - кода была использовала библиотека PyZbar. 
С целью повышения результативности и точности распознавания QR-кода полеты производились на небольшой высоте по точкам, расположенным вокруг данного объекта.
</p>

</div>



