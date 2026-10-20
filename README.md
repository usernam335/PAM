# PAM

## Описание домашнего задания:
 Ограничить доступ к системе для всех пользователей, кроме группы администраторов в выходные дни (суббота и воскресенье), за исключением праздничных дней.

## 1. Создаем каталок для ВМ: 

    mkdir -p otus/vagrant-pam


## 2. Перекидываем [Vagrantfile](https://github.com/usernam335/PAM/blob/main/Vagrantfile) в каталог vagrant-pam:

    mv /path/to/Vagrantfile otus/vagrant-pam 
   ________________________________________________ 
    cd otus/vagrant-pam


## 3. Создаем ВМ:

    vagrant up


## 4. Подключаемся к созданной ВМ:

    vagrant ssh

## 5. Получаем права root:

    sudo -i

## 6. Создаем пользователей otusadm и otus:

    sudo useradd otusadm && sudo useradd otus

## 7. Создаем пользователям пароли:

    echo -e 'otusadm:Otus2026!\notus:Otus2026!' | sudo chpasswd
    
## 8. Создаем группу admin

    sudo groupadd -f admin

## 9. Добавляем пользователей vagrant,root и otusadm в группу admin:

     sudo usermod -aG admin otusadm && sudo usermod -aG admin vagrant && sudo usermod -aG admin root

<img width="375" height="62" alt="Снимок экрана от 2026-10-18 20-59-15" src="https://github.com/user-attachments/assets/3d6eb763-4253-4953-afe0-05f2549c88d2" />











    
