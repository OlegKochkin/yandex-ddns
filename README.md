# yandex-ddns
Set value A record in Yandex DNS 

Периодически запускать скрипт из cron.\
Сохраняет в локальном файле (/usr/local/etc/PrevIP.txt) предыдущий IP.\
Получает текущий IP из двух разных источников (http://ifconfig.io и http://myexternalip.com/raw). \
Если полученные IP одинаковы и валидны, проверяется соответствие ранее сохранённому предыдущему IP.\
Если текущий IP не равен предыдущему, получает с DNS Яндекса IP указанной записи.\
Если IP на DNS отличается от текущего, то он записывается в DNS.

Вызов функции для обновления записи:\
ChangeRecord <domain> <token> <subdomain> <record_id>

Токен получать здесь - https://pddimp.yandex.ru/api2/admin/get_token\
ID записей можно получить так - curl -sH 'PddToken: TOKEN' 'https://pddimp.yandex.ru/api2/admin/dns/list?domain=domain.com' | jq
