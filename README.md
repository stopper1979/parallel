## дописать в архиве job-builder.ini
ignore_cache=true
## 1

# //установка докера
sudo apt update

sudo apt install apt-transport-https ca-certificates curl software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

sudo apt update

sudo apt install docker-ce

sudo usermod -aG docker sto

# //запуск докера
sudo docker run -d --name selenoid -p 4444:4444 -v /var/run/docker.sock:/var/run/docker.sock -v /root/.aerokube/selenoid:/etc/selenoid aerokube/selenoid -limit 10

sudo docker run -d --name selenoid-ui -p 80:8080 aerokube/selenoid-ui  -selenoid-uri http://172.17.0.1:4444

sudo nano /root/.aerokube/selenoid/browsers.json //правлю браузеры

sudo docker pull selenoid/chrome:103.0

sudo docker pull selenoid/vnc_chrome:103.0

# //установка job-builder и запуск docker-compose
sudo apt install jenkins-job-builder

sudo docker-compose up -d

# //настройка jenkins
sudo docker-compose logs jenkins //ввод ключа для установки

//первоначальная настройка plugins, глобальная настройка, настройка пользователей и прав,

# //запуск формирования джобы
sudo jenkins-jobs --conf ./jobs/configs/job-builder.ini update ./jobs
