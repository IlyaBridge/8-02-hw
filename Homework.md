# Домашнее задание к занятию "`Что такое DevOps. СI/СD`" - `Казначеев Илья`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1
Что нужно сделать:
1. Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.
2. Установите на машину с jenkins golang.
3. Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.
4. Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

`Приведите ответ в свободной форме........`

1. `1. Устанавливаем Java
$ sudo apt-get install default-jre
`
2. `Устанавливаем Jenkins из пакта для debian/ubuntu`
3. `Устанавливаем Golang:
$ sudo apt update
$ sudo apt install golang-go
`
4. `Откроем Jenkins (http://10.0.2.16:8080)`
5. `Создадим и настроим новый item `

```
В Build Steps добавьте:
# Для запуска тестов
go test .
# Для сборки Docker образа
docker build .
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота 1](ссылка на скриншот 1)`

![001 - 1 Конфиг_задача_1](https://github.com/user-attachments/assets/5ce05f64-b609-4f83-bf16-0df310b03e7f)

![001 - 2 Конфиг_задача_1](https://github.com/user-attachments/assets/f3cccaff-79e6-4e41-801c-1c456fd2748b)

![001 - 3 Ответ_задача_1](https://github.com/user-attachments/assets/81c47d85-d4ba-412e-ba46-87c55b571bdd)

![002 - 4 Ответ_задача_1](https://github.com/user-attachments/assets/6f60d7b0-ab47-4ac7-9097-17044876383e)

![003 - 5 Ответ_задача_1](https://github.com/user-attachments/assets/b8f23d8b-d8f8-42c7-aa45-95e75c8a3550)

---

### Задание 2
Что нужно сделать:
Создайте новый проект pipeline.
Перепишите сборку из задания 1 на declarative в виде кода.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

`Приведите ответ в свободной форме........`

```
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'go test'
                sh 'docker build -t my-image .'
            }
        }
    }
}
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота 2](ссылка на скриншот 2)`

![002-1 Создаем новый проект](https://github.com/user-attachments/assets/40d3055c-a497-450c-99dc-928f1d5dbb9e)

![002-2 Создаем новый проект](https://github.com/user-attachments/assets/45468f36-e08b-4b7e-9f20-0bea0b5877ea)

![002-3 Создаем новый проект](https://github.com/user-attachments/assets/c4f40c0d-8c57-47ad-8725-7e17e36cd02c)

![002-4 Создаем новый проект](https://github.com/user-attachments/assets/696178b6-2a8f-42a9-b39b-7152133bbaf4)

![002-4-1 Создаем новый проект](https://github.com/user-attachments/assets/e1ffd20e-3a03-40d0-80c7-323a30990fea)

![002-5 Создаем новый проект](https://github.com/user-attachments/assets/fa2a7f75-fdb2-4fdd-819b-0baef8b08e08)

![002-6 Результат - 1](https://github.com/user-attachments/assets/a72bf12d-b2c4-472b-9d78-2ef1c63af853)

![002-6 Результат - 2](https://github.com/user-attachments/assets/9757d994-153b-49e2-9c0e-d0572a6a6374)

![002-6 Результат - 3](https://github.com/user-attachments/assets/0c31f513-ec38-437f-ac23-1532d6db0b4b)

![002-6 Результат - 4](https://github.com/user-attachments/assets/105e8aee-b869-454e-8f7c-e9e90c08d948)

---

### Задание 3
Что нужно сделать:
Установите на машину Nexus.
Создайте raw-hosted репозиторий.
Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
Загрузите файл в репозиторий с помощью jenkins.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

`Приведите ответ в свободной форме........`

```
pipeline {
    agent any
 
    environment {
        NEXUS_URL = 'http://10.0.2.16:8081/repository/go-binaries'
        NEXUS_USER = 'admin'
        NEXUS_PASSWORD = '88520'
    }
 
    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/IlyaBridge/8-02-hw.git', branch: 'main'
            }
        }
        stage('Build Binary') {
            steps {
                sh 'go build -o go-app .'
            }
        }
        stage('Upload to Nexus') {
            steps {
                script {
                    def fileName = "go-app"
                    sh """
                       curl -v -u ${NEXUS_USER}:${NEXUS_PASSWORD} --upload-file ${fileName} ${NEXUS_URL}/${fileName}
                    """
                }
            }
        }
    }
}

```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

![image](https://github.com/user-attachments/assets/b91e0749-e76a-4448-a71c-73a59df44a78)
![image](https://github.com/user-attachments/assets/ff2a023f-89a8-45ff-8445-62f8925ada50)
![image](https://github.com/user-attachments/assets/056ddbae-2306-407e-b0cf-f9fe1c044102)
![image](https://github.com/user-attachments/assets/477fd237-ac9c-4807-90f3-05f5fafc1250)

![003 Jenkins Настройка](https://github.com/user-attachments/assets/d5d857c9-e3e2-4255-8068-125f8e0aaa9a)

![003 Итог выполнения](https://github.com/user-attachments/assets/3bba7b00-0cb8-4ed6-adae-824fae846af6)

![003 Ход выполнения](https://github.com/user-attachments/assets/5da49d5d-2781-4cc9-baab-b28566f3a3ab)







