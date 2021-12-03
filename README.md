# jmeterReports2
Что делать чтобы попробовать? 
1. Качаем JMeter - нужна версия 5.4.1 (проверенно на ней). https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.4.1.zip
2. На машинке где будете разворачивать окружение должен стоять докер. Я использую https://www.docker.com/products/docker-desktop
3. Вытягиваем репозиторий к себе
4. Содержимое папки jmeter копируем в скаченный и разархивированнный вами дистрибутив в п.1 (заменяем файлы)
5. В корне лежат проекты (напр. Project1) и папка template - они должны лежать на одном уровне вложенности (рядом с друг другом)
6. Делаем "docker-compose up -d" из корня директории. (Потребует 7Гб RAM, 2 vCPU можно поменять в .yml)
7. Открываем Jmeter, открываем /Project1/project1_example_test.jmx - это уже настроенный тест план. Можем сразу его запустить
8. В онлайне можно посмотреть результаты в Grafana http://localhost:3000 - логин и пароль: admin/1234qwer (как и в инфлюкс)
   </br>*В случае если на панельках в графане повисает надпись "panic: runtime error" - не паникуем, а идем и рестартуем контейнер с influxdb:*
      - docker ps
      - docker restart <influxdb_container_id>
      - *После этого перезапустить тест*
10. Дайте тесту пару минут, чтобы над данными можно было сделать все аггрегации и нажмите на Stop. Тест начнет рендерить графики и отправлять их в confluence
11. Тестовый конфлюенс живет тут https://qaload.atlassian.net/wiki/spaces/TEST - для инвайта кидайте мне почту @login40k telegram
12. Еще резльтаты упадут в тестовый slack - https://join.slack.com/t/kirillyurkovqaload/shared_invite/zt-vmugmi7b-~vDk0zLTaEimqFKChVzqDw инвайт-линк туда.

Общие моменты:
- В тренды тесты попадают только тогда когда они соответствуют выставленным требованиям по времени, выставляется дашборде Test Trends

Eng:
# jmeterReports2
What should I do to try it?
1. Download JMeter - needed version is 5.4.1 (test on it). https://dlcdn.apache.org//jmeter/binaries/apache-jmeter-5.4.1.zip
2. You need the Docker in machine. I am using this for win https://www.docker.com/products/docker-desktop
3. Clone current repo
4. Copy the jmeter folder from repo to unzipped jmeter distr from #1 (replace files)
5. Root folder contains projects (ex. Project1) and folder template - the should be in one directory layer level (close to each other)
6. Execute "docker-compose up -d" from root. (Req. 7Gb RAM, 2 vCPU but you can change it in .yml)
7. Open Jmeter, and there open /Project1/project1_example_test.jmx - it is already done test plan. You can start it.
8. You can see online results in Grafana http://localhost:3000 - log and pass: admin/1234qwer (same for influx)
   </br>*If you see this message in Grafana panels "panic: runtime error" - don't panic, just go and restart container with influxdb:*
      - docker ps
      - docker restart <influxdb_container_id>
      - *Rerun your test*
10. Wait few minutes after start. Click on Stop button and then it will start to render graphs and push it to confluence
11. Test Confluence is here https://qaload.atlassian.net/wiki/spaces/TEST - for invatation write to me @login40k telegram
12. Also there is test slack - https://join.slack.com/t/kirillyurkovqaload/shared_invite/zt-vmugmi7b-~vDk0zLTaEimqFKChVzqDw invitation link. If doesn't work writ eto me)

PS:
- Tests pushing to trends only when themselfs durations is more then requrements in dashbord Test Trends
