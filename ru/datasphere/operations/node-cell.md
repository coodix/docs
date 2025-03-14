# Создание ноды из ячейки с кодом на Python

Для развертывания ячейки в виде микросервиса необходима [контрольная точка](projects/checkpoints.md). 

{% note info %}

Если в проекте вы используете пакеты и библиотеки, не входящие в [список предустановленного ПО](../concepts/preinstalled-packages.md), [настройте окружение](node-customization.md) ноды с помощью Docker-образа. 

{% endnote %}

1. Откройте вкладку ![Checkpoints](../../_assets/datasphere/jupyterlab/checkpoints-panel.svg) **Checkpoints** и сохраните контрольную точку, подготовленную для развертывания. 

1. Откройте ноутбук и выберите ячейку для развертывания.

1. Вызовите контекстное меню правой кнопкой мыши и выберите пункт **Deploy selected cell**.

1. В диалоговом окне задайте:
   * В поле **Name** — имя ноды.
   * В выпадающем списке **Select checkpoint to use for deployment** выберите нужную контрольную точку.
   * В блоках **Output variables** и **Input variables** определите имена и типы выходных и входных переменных, на основе которых будет автоматически сгенерирован API. Вы можете добавить переменные, нажимая на кнопку **Add new**.
   * В поле **Instance count** введите количество ВМ в ноде.

1. Нажмите кнопку **Create**, чтобы создать ноду.

После создания ноды вы увидите ее идентификатор внизу окна. Посмотреть все созданные ноды можно на вкладке ![Node](../../_assets/datasphere/node.svg) **Nodes**.