# Установка ROS2 Jazzy

## Шаг 0. Проверка системы.
```bash
lsb_release -a
```
Должно быть Ubuntu 24.04

## Шаг 1. Настройка кодировки.
Нужно убедиться, что система использует правильные стандарт кодирования и языковую среду, чтобы обеспечить корректное отображение языка и поддержку локализации при установке и запуске программного обеспечения.
```bash
sudo apt update && sudo apt install locales
```
```bash
sudo locale-gen en_US en_US.UTF-8
```
```bash
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
```
```bash
export LANG=en_US.UTF-8
```

## Шаг 2. Добавление репозитория ROS 2.
```bash
sudo apt update && sudo apt install curl gnupg2 lsb-release -y
```
```bash
sudo apt install software-properties-common
```
```bash
sudo add-apt-repository universe
```
```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
Добавить репозиторий в список источников:
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

## Шаг 3. Установка ROS 2.
```bash
sudo apt update
```
```bash
sudo apt upgrade
```
```bash
sudo apt install ros-jazzy-desktop
```

## Шаг 4. Настройка переменных окружения.
```bash
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
```
```bash
source ~/.bashrc
```

## Шаг 5. Тестовый пример.
В одном терминале
```bash
ros2 run demo_nodes_cpp talker
```
В другом терминале
```bash
ros2 run demo_nodes_py listener
```
Если строка «Hello World» передается между двумя терминалами без проблем, то система коммуникации ROS 2 работает корректно.
