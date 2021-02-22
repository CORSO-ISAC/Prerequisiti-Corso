# Prerequisiti linux
## Visual Studio Code

### Su Ubuntu
#### Con snap
Da ubuntu 18 snap è installato di default.
Se non c'è si installa con 
```
apt install snap

```
poi possiamo installare vscode lanciando

```
snap install code --classic
```

#### Con APT

Visual Studio Code non c'è nei repository di Ubuntu, bisogna aggiungere il repository di microsoft.

Prima di tutto aggiungiamo la chiave e installiamo un po di cose che servono
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
```

Poi aggiungiamo il repository:
```
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
```

Aggiorniamo l'indice pacchetti e installiamo Visual Studio Code

```
sudo apt update
audo apt install code
```

### Su Archlinux

```
pacman -S code
```


## Docker

### Installare il pacchetto

Questo si fa in base alla distribuzione, copriamo circa tre casi

#### Ubuntu o Debian

Prima di iniziare si installano un paio di pacchetti necessari e si importa la chiave del progetto docker.
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Poi si aggiunge il repository, questo va fatto in base alla nostra distribuzione:

##### Ubuntu 18.04 Bionic Beaver

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
```

##### Ubuntu 20.04 Focal Fossa
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable
```

##### Debian Buster
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian buster stable
```

Poi aggiorniamo l'indice dei pacchetti con
```
sudo apt update
```

Accertiamoci di star prendendo il pacchetto esattamente da dove vogliamo prenderlo:
```
apt-cache policy docker-ce
```
Nell'output del comando vedremo nella lista *Version table* l'origine del pacchetto, dhe dovrebbe essere https:///download.docker.com

Lo installiamo con
```
apt install docker-ce
```

#### CentOS / RHEL

```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io
```

#### Archlinux

```
pacman -S docker docker-compose
```

### Il demone docker

Per funzionare docker ha bisogno del suo demone attivo, in background.
Con questo comando avviamo il demone docker e lo facciamo partire in automatico al riavvio.
```
systemctl enable --now docker
```

Controlliamo che tutto sia andato a buon fine con:
```
systemctl status docker
```
Che dovrebbe dirci, in verde, **active**


### I permessi giusti
Infine, per poter comunicare con docker abbiamo bisogno di dare al nostro utente i giusti privilegi.
Questa cosa si fa aggiungendo il nostro utente al gruppo docker con il comando:
```
sudo usermod -aG docker ${USER}
```

Per rendere effettiva questa modifica abbiamo bisogno di fare logout e di nuovo login.

Controlliamo di esserci per davvero col comando:
```
id -nG
```
Che ci da la lista dei gruppi di cui facciamo parte, dentro la lista dovremmo vedere docker.


## Docker Compose

Quello che c'è nei repository della distribuzione di solito va bene.
Se è troppo vecchio o non c'è, si può installare con:
```
curl -L https://github.com/docker/compose/releases/download/1.28.4/docker-compose-Linux-x86_64 -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

Attenzione: installandolo in questo modo non verrà aggiornato automaticamente dal package manager.



## Git

Installare git è semplice, si trova tranquillamente nei repository di tutte le distribuzioni linux, in alcuni casi è già installato.
Se non lo avete ecco le indicazioni per installarlo insieme ad un paio di utili tool.

### Debian, Ubuntu e derivate

```
apt install git gitk meld 
```

### Centos 7

```
yum install git gitk meld
```

### Archlinux

```
pacman -S git gitk meld
```
