# plan

![[Pasted image 20221016182541.png]]


**Где лежит ssh конфиг файл и как ходить на сервер по укороченному имени**
 - _.vimrc_ - конфиг файл для настроек _vim_'а
 - _.bashrc_ - конфиг файл для _bash_'а (запускается каждый раз, когда открывается bash сессия (терминал)). можно биндить альясы, переменные окружения
```
cd ~/.ssh
```
у всех файлов .ssh должен быть уровень доступа 600 (только у правообладателя и только на чтение)
файл с конфигурациями хостов/серваков
```
config
```
```
host ...
hostname ...
user ...
identityfile ...
```
![[Pasted image 20221016183929.png]]
на сервере должна быть публичная часть ключа

как сгенерить ssh ключ
1. прописываем где он появится и как будет называться (также можно поставить на него сверху пароль, но можно и не ставить)
```
ssh-keygen
```
2. переносим через _scp_ публичную часть ключа и кладём куда нужно
(на курсе это так)
```
scp ...
cat key_name.pub >> ~/.ssh/authorized_keys
```



# schedulers

- Автоматизирует работу нескольких людей на 1-м суперкомпьютере 
> 1. вкл, выкл, закрытие доступа для других во время сессии
> 2. аллоцирует ресурсы и память
> 3. разрешает конфликты процессов

- Управляющий узел, рабочие узлы
![[Pasted image 20221016191028.png]]


## примеры scheduler'ов

### 1.  Torque TBS
![[Pasted image 20221016191752.png]]
![[Pasted image 20221016191909.png]]



### 2. SLURM

![[Pasted image 20221016192145.png]]

![[Pasted image 20221016193703.png]]



# page rank

![[Pasted image 20221016195209.png]]


- у перестановочно подобных матриц одинаковые собственные значения

![[Pasted image 20221016195944.png]]

![[Pasted image 20221016200317.png]]

![[Pasted image 20221016200601.png]]

![[Pasted image 20221016200801.png]]



# sparse matrix

![[Pasted image 20221016201509.png]]

![[Pasted image 20221016202052.png]]
























































































































 