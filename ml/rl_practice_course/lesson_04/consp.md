
# ON-policy RL

Текущая проблема:
 - вне зависимости от того, насколько маленький lr, наша политика может расходиться из-за домножения на сумм. диск. награду
решение:
 - будем не давать политике сильно менять распределение на действия
как:
![[Pasted image 20221112135929.png]]
 - КЛ дивергенция асимитрична
 - можем использовать приближение мат. ожидания по старой политике за счёт старых данных (Монте-Карло)




Считаем advantage function для новой политики с новым распределением


![[Pasted image 20221112140758.png]]
![[Pasted image 20221112140847.png]]
![[Pasted image 20221112141735.png]]




PPO with penalty

идея:
 - заменим условие на порог КЛ дивергенции на регуляризацию в лоссе членом с КЛ дивергенцией
![[Pasted image 20221112142241.png]]
(знаки деления и умножения перепутаны местами)

благодаря такому ходу алгоритм становится устойчив к любым значениям advantage function (scale)



PPO with clipping
![[Pasted image 20221112142525.png]]



proximal policy optimization
![[Pasted image 20221112143034.png]]
![[Pasted image 20221112143429.png]]



# model-based rl

**идея**:
 - сначала выучим модель среды (динамику среды)
 - затем на нашей модели будем обучать агента без взаимодействий со средой


**алгоритмы**
- world model (игра wizDoom - нужно уклоняться от снарядов, обучение на вирт. окружении)
- PlaNet
- Dreamer


- когда окружение очень медленное, нам быстрее будет выучить модель динамики среды и обучать агента уже на ней











































































