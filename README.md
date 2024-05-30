# Ponderada - Turtlebot teleoperado

Desenvolvido por Isabelle Beatriz Vasquez Oliveira

Este projeto é capaz de realizar a leitura das teclas pressionadas pelo usuário e, utilizando um publisher no tópico adequado, provocar a movimentação do robô.

Nesse projeto, o usuario deve usar as seguintes teclas para movimentar o robô:
- W:	aumenta velocidade linear do robô
- A:	aumenta velocidade angular do robô em sentido anti-horário
- D:	aumenta velocidade angular do robô em sentido horário
- S:	anula a velocidade de movimentação do robô
- Q:	interrompe a execução do código de movimentação do robô

A tecla `S` é o botão de emergência desta aplicação, garantindo que o robô interrompa sua movimentação quando o usuário julgar necessário.

Para garantir que o usuário receba feedback constante em relação à operação do robô, foi utilizado o método `print` para que o usuário visualize em formato de texto suas últimas decisões de movimentação, juntamente com a velocidade do robô, que é apresentada constantemente ao usuário.

O vídeo de demonstração do funcionamento do projeto pode ser encontrado no link a seguir: https://youtu.be/ZsJmXcjVQBI

## Como executar?

**Os requisitos de execução e o tutorial de execução têm como referência a documentação do projeto SugarZ3ro!**

Para executar o projeto corretamente, o usuário deve ter os seguintes pré-requisitos: 

- Python3 e Git instalados no computador usado para operar o robo;
- ROS2 e Pacote ROS do Turtlebot 3 instalados no sistema operacional (Linux Ubuntu) da Raspberry do Turtlebot 3 e do computador usado para operá-lo remotamente;
- Raspberry do Turtlebot 3 e computador usado para operá-lo remotamente conectados na mesma rede wi-fi.

Para executar o programa, o usuario deve seguir os seguintes passos:

  **Sistema operacional da Raspberry contida no Turtlebot 3**
  
No sistema operacional da Raspberry contida no Turtlebot 3 a ser controlado, abra uma janela de terminal e digite os seguintes comandos para limitar a comunicação via ROS a um domínio com ID 5 dentro da rede:

`echo 'export ROS_DOMAIN_ID=5' >> ~/.bashrc`

`source ~/.bashrc`

    Também é necessário realizar a comunicação via SSH. Para isso, é necessário seguir os seguintes passos: 
    No sistema operacional da Raspberry do Turtlebot 3, abra uma janela de terminal e clone e dê build no repositório do projeto no diretório de sua preferência através dos comandos:

    git clone https://github.com/IsabelleVOliveira/ponderada-S5-M6.git
        
    colcon build
    
    Na mesma janela de terminal, digite os seguintes comandos para instalar o pacote responsável por iniciar um servidor SSH e executá-lo.
    sudo apt install openssh-server
    
    sudo systemctl enable ssh
    
    sudo ufw allow ssh
    
    sudo systemctl start ssh
    
    Na mesma janela de terminal, digite o seguinte comando para iniciar a comunicação entre a Raspberry e o microcontrolador do robô, bem como torná-lo apto a receber comandos de movimentação remotamente:
    ros2 launch turtlebot3_bringup robot.launch.py
    
    No sistema operacional do computador que será utilizado para controlar o robô de maneira remota, abra uma janela de terminal e digite o seguinte comando:
    ssh user@server

    Digite a senha de usuário que será solicitada pelo terminal.

Na mesma janela de terminal, digite o seguinte comando para iniciar a comunicação entre a Raspberry e o microcontrolador do robô, bem como torná-lo apto a receber comandos de movimentação remotamente:
`ros2 launch turtlebot3_bringup robot.launch.py`

**Computador que vai controlar o robo**

No sistema operacional do computador que será utilizado para controlar o robô de maneira remota, abra uma janela de terminal no diretório de sua preferência e clone o repositório através do seguinte comando:
`git clone https://github.com/IsabelleVOliveira/ponderada-S5-M6.git`

Na mesma janela de terminal, digite o seguinte comando para iniciar o build do workspace:
`colcon build`

Na mesma janela de terminal, digite o seguinte comando para habilitar o uso do pacote criado:
`source install/local_setup.bash`

Na mesma janela de terminal, digite os seguintes comandos para limitar a comunicação via ROS a um domínio com ID 5 dentro da rede:
`echo 'export ROS_DOMAIN_ID=5' >> ~/.bashrc`

`source ~/.bashrc`

Por fim, na mesma janela de terminal, digite o seguinte comando para executar o script responsável por inicializar a CLI para controle de movimentação do robô:
`ros2 run run start_moving`.




