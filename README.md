# Set Up Kafdrop for GUI (Graphical User Interface) Apache Kafka Ubuntu Server

Create kafdrop directory

    sudo mkdir /opt/kafdrop && cd /opt/kafdrop/ 

Download kafdrop.jar

    curl -LO https://github.com/obsidiandynamics/kafdrop/releases/download/3.30.0/kafdrop-3.30.0.jar

## Set kafdrop as a services (optional)

    sudo nano /etc/systemd/system/kafdrop.service

Append this:

    [Unit]
    Description=Kafdrop server
    Documentation=https://github.com/obsidiandynamics/kafdrop
    Requires=network.target remote-fs.target
    After=network.target remote-fs.target
    
    [Service]
    Type=simple
    ExecStart=/bin/java --add-opens=java.base/sun.nio.ch=ALL-UNNAMED \
        -jar /opt/kafdrop/kafdrop-3.30.0.jar \
        --kafka.brokerConnect=(your ip):9092
    Restart=on-abnormal
    
    [Install]
    WantedBy=multi-user.target

## After that start a services

    sudo systemctl daemon-reload
    sudo systemctl start kafdrop
    sudo systemctl enable kafdrop
    sudo systemctl status kafdrop

![image](https://github.com/arliputraa/kafdrop-configuration-for-gui-kafka/assets/110078907/a89cade3-fe62-4907-aadc-0458b45f9251)
![image](https://github.com/arliputraa/kafdrop-configuration-for-gui-kafka/assets/110078907/d41a836d-0513-4101-bb85-843702e898f5)

## Open kafdrop GUI
Open in your browser
    (your ip) :9000

![image](https://github.com/arliputraa/kafdrop-configuration-for-gui-kafka/assets/110078907/d245371d-07b9-48f6-9223-fb3d9944fd30)

## For more Instalation Apache Kafka in this link: https://github.com/arliputraa/apache-kafka-instalation

## For more Setup Kafka Cluster in this link: https://github.com/arliputraa/kafka-cluster-configuration
