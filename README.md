# jmeterReports2
Что делать чтобы попробовать? 
1. Качаем JMeter - нужна версия 5.4.1 (проверенно на ней). https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.4.1.zip
2. На машинке где будете разворачивать окружение должен стоять докер. Я использую https://www.docker.com/products/docker-desktop
3. Вытягиваем репозиторий к себе
4. Содержимое папки jmeter копируем в скаченный и разархивированнный вами дистрибутив в п.1 (заменяем файлы)
5. В корне лежат проекты (напр. Project1) и папка template - они должны лежать на одном уровне вложенности (рядом с друг другом)
6. Делаем "docker-compose up из" корня директории. (Потребует 3Гб RAM, 1 vCPU можно поменять в .yml)
7. Открываем Jmeter, открываем /Project1/project1_example_test.jmx - это уже настроенный тест план. Можем сразу его запустить
8. В онлайне можно посмотреть результаты в Grafana http://localhost:3000 - логин и пароль: admin/1234qwer (как и в инфлюкс)
  8.1 В случае если на панельках в графане повисает надпись "panic: runtime error" - не паникуем, а идем и рестартуем контейнер с influxdb:
      - docker ps
      - docker restart <influxdb_container_id>
  8.2 После этого перезапустить тест
10. Дайте тесту пару минут, чтобы над данными можно было сделать все аггрегации и нажмите на Stop. Тест начнет рендерить графики и отправлять их в confluence
11. Тестовый конфлюенс живет тут https://qaload.atlassian.net/wiki/spaces/TEST - для инвайта кидайте мне почту @login40k telegram
12. Еще резльтаты упадут в тестовый slack - https://join.slack.com/t/kirillyurkovqaload/shared_invite/zt-vmugmi7b-~vDk0zLTaEimqFKChVzqDw инвайт-линк туда.

