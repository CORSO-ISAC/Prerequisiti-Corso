# Prerequisiti-Windows-10

### Visual Studio Code
[Link installazione](https://code.visualstudio.com/download)

### Docker
#### Installazione Subsystem linux
Guida realizzata sulla base della [documentazione ufficiale](https://docs.microsoft.com/it-it/windows/wsl/install-win10)

1. Aggiorna alla versione di Windows 10 più recente: [Windows Update](ms-settings:windowsupdate) e riavvia su richiesta
2. Abilitare il sottosistema Windows per Linux: apri *PowerShell come amministratore* ed esegui il comando, successivamente riavvia
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all
```
3. Abilitare le funzionalità delle macchine virtuali: apri *PowerShell come amministratore* ed esegui il comando, successivamente riavvia
``` 
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all
```
4. Scarica e installa il [pacchetto di aggiornamento del kernel Linux](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
5. Impostare WSL 2 come versione predefinita: apri *PowerShell come amministratore* ed esegui il comando
```
wsl --set-default-version 2
```
6. Installare la distribuzione di Linux preferita, se avete già dimestichezza con una distribuzione, utilizzate quella altrimenti Ubuntu: [Linux WSL](https://aka.ms/wslstore)


#### Installazione Docker
Guida realizzata sulla base della [documentazione ufficiale](https://docs.docker.com/docker-for-windows/wsl/)

1. Scarica e installa [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows/)
2. Avvia Docker Desktop dsl menu di Windows
3. Vai su "Settings" > "General"
4. Seleziona "Use WSL 2 based engine"
5. Premi il pulsante "Apply & Restart"

### GIT
[Link installazione](https://git-scm.com/download/win)
