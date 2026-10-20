# PAM

## Описание домашнего задания:
 Ограничить доступ к системе для всех пользователей, кроме группы администраторов в выходные дни (суббота и воскресенье), за исключением праздничных дней.

## Создаем каталог для ВМ и перенесем Vagrantfile: 

    mkdir -p otus/vagrant-pam


 1. Перекидываем [Vagrantfile](https://github.com/usernam335/PAM/blob/main/Vagrantfile) в каталог vagrant-pam:


        mv /path/to/Vagrantfile otus/vagrant-pam 
   ________________________________________________ 
        cd otus/vagrant-pam


## Создаем и настраиваем ВМ:

      vagrant up


1. Подключаемся к созданной ВМ:

       vagrant ssh

2. Получаем права root:

       sudo -i

 3. Создаем пользователей otusadm и otus:

        sudo useradd otusadm && sudo useradd otus

4. Создаем пользователям пароли:

       echo -e 'otusadm:Otus2026!\notus:Otus2026!' | sudo chpasswd
    
5. Создаем группу admin

        sudo groupadd -f admin

6. Добавляем пользователей vagrant,root и otusadm в группу admin:

  <img width="375" height="62" alt="Снимок экрана от 2026-10-18 20-59-15" src="https://github.com/user-attachments/assets/3d6eb763-4253-4953-afe0-05f2549c88d2" />
     
     sudo usermod -aG admin otusadm && sudo usermod -aG admin vagrant && sudo usermod -aG admin root


7. Проверим подключение пользователей по SSH:

<img width="700" height="827" alt="Снимок экрана от 2026-10-20 17-02-14" src="https://github.com/user-attachments/assets/60d8b04e-63c4-4749-86aa-156ee8402f5e" />

      ssh otus@192.168.57.10

<img width="700" height="827" alt="Снимок экрана от 2026-10-20 17-00-20" src="https://github.com/user-attachments/assets/006ebcb3-c90b-4da0-a810-43a5394ef99f" />

    ssh otusadm@192.168.57.10

8. Проверим, что пользователи root, vagrant и otusadm есть в группе admin:

<img width="375" height="62" alt="Снимок экрана от 2026-10-18 20-59-15" src="https://github.com/user-attachments/assets/b74b10e1-05f0-436f-839c-231bd826cac4" />

    grep admin /etc/group

## Создадим [файл-скрипт]() для контроля доступа в выходные и праздничные дни:

    sudo nano /usr/local/bin/login.sh


    




    
