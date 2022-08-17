dev env:

    git clone ...
    cp config/sensitive.properties.example config/sensitive.properties
    mkdir -p htaccess dump extra logs media upgrade

AUtostart:

no arquivo /etc/systemd/system/nunaliit-travel.service inserir:

    [Unit]
    Description=nunaliit-travel
    Requires=couchdb.service
    After=couchdb.service

    [Service]
    Type=simple
    User=nunaliit
    ExecStart=/home/nunaliit/travel_atlas/nunaliit/bin/nunaliit --atlas-dir "/home/nunaliit/travel_atlas/travel/." run
    Restart=on-failure

    [Install]
    WantedBy=multi-user.target

Start:

    sudo systemctl enable nunaliit-travel
    sudo systemctl start nunaliit-travel
