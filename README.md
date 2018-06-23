# admin-panel-server
Это Docker инфраструктура, нужно установить Docker, чтобы работать с этими файлами.

Рабочий проект копировать в папку "web/www/", предварительно ее создав.

Добавить "127.0.0.1 admin_panel.loc" в /etc/hosts;  
Выполнить: "docker-compose up -d --build";  
Зайти на машину с проектом: "docker exec -ti admin_panel_web bash";  
