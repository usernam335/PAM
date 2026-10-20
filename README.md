# PAM

## Описание домашнего задания:
 Ограничить доступ к системе для всех пользователей, кроме группы администраторов в выходные дни (суббота и воскресенье), за исключением праздничных дней.

## 1. Создать каталок для ВМ: 

    mkdir -p otus/vagrant-pam


## 2. Перекинуть [Vagrantfile](https://github.com/usernam335/PAM/blob/main/Vagrantfile) в каталог vagrant-pam:

    mv /path/to/Vagrantfile otus/vagrant-pam 

## 3. Поднять ВМ:

    cd otus/vagrant-pam
__________________________________________________
    vagrant up

    
