# Создание ключа доступа для сервисного аккаунта

Ранее был создан сервисный аккаунт `sls-deploy` с правами `editor`, мы используем его, 
чтобы создавать различные сущьности в облаке.

Этот этап нужен для получения идентификатора ключа доступа и секретного ключа.
Для создания ключа доступа необходимо вызвать следующую команду:

    yc iam access-key create --service-account-id $SERVICE_ACCOUNT_GAME_ID

В результате вы получите примерно следующее

    access_key:
        id: ajeibet32197n869t0lu
        service_account_id: ajehr6tv2eoo3isdbv0e
        created_at: "2023-03-13T10:20:58.471421425Z"
        key_id: YCASD3CT9mPCVFh3KRmB4JDx9
    secret: YCNhBcdvfDdssIuBa-FDl6zZz0MSky6ujSjACX

Сохраните идентификатор `key_id` в переменную `AWS_ACCESS_KEY_ID`
и секретный ключ `secret` в переменную `AWS_SECRET_ACCESS_KEY`.
Получить значение ключа снова будет невозможно. Подставьте свои значения и сохраните переменные:

    echo "export AWS_ACCESS_KEY_ID=<key_id>" >> ~/.bashrc && . ~/.bashrc
    echo $AWS_ACCESS_KEY_ID

    echo "export AWS_SECRET_ACCESS_KEY=<secret>" >> ~/.bashrc && . ~/.bashrc
    echo $AWS_SECRET_ACCESS_KEY

Для начала, задайте конфигурацию с помощью команды `aws configure`. При этом от вас потребуется ввести:
* `AWS Access Key ID` — это идентификатор ключа доступа `key_id` сервисного аккаунта, полученный ранее.
* `AWS Secret Access Key` — это секретный ключ `secret` сервисного аккаунта, полученный ранее.
* `Default region name` — используйте значение `ru-central1`.
* `Default output format` — оставьте пустым.

По завершению конфигурации вы сможете использовать AWS CLI для создания ресурсов в облаке:

    echo $AWS_ACCESS_KEY_ID
    echo $AWS_SECRET_ACCESS_KEY
    aws configure
    aws configure list

## Видео

https://youtu.be/3cPXWa9kdhc

# [cледующий этап >>>](../3-create-ydb/README.md)

