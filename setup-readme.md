# Installation und Konfiguration des Wahlorant-Systems

## Systemvoraussetzungen

Zur lokalen Einrichtung des Kubernetes-Clusters benötigen Sie:

> **Wichtig: Verwenden Sie ein Terminal mit Administratorrechten**

Installieren Sie zunächst Chocolatey über folgenden Befehl

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Anschließend können sie die folgenden erforderlichen Komponenten installieren (Falls nicht bereits auf dem Rechner installiert!):

```powershell
# i. Docker Desktop installieren
choco install docker-desktop -y

# ii. Minikube installieren
choco install minikube -y

# iii. kubectl installieren
choco install kubernetes-cli -y

# iiii. Skaffold installieren
choco install skaffold -y
```

## Einrichtungsprozess

1. Klonen Sie das Repository mit allen Submodulen:
   ```bash
   git clone --recurse-submodules https://github.com/JavaHammes/Whalorant.git
   ```

2. Initialisieren Sie die Minikube-Umgebung mit ggf. angemessener Ressourcenzuweisung:
   ```bash
   minikube start 
   ```

3. Verifizieren Sie den aktuellen Status der Minikube-Installation:
   ```bash
   minikube status
   ```

4. Aktivieren Sie den Ingress-Controller für korrektes Routing und Tunneling:
   ```bash
   minikube addons enable ingress
   ```

5. Etablieren Sie eine Tunnel-Verbindung:
   ```bash
   minikube tunnel
   ```
   **Hinweis: Lassen Sie dieses Terminal geöffnet und fahren Sie in einem neuen Terminal fort.**

6. Konfigurieren Sie die Umgebungsvariablen durch Umbenennung der Datei `.env.example` zu `.env` im Backend-Verzeichnis.

7. Navigieren Sie zum Hauptverzeichnis des Repositories und starten Sie den Entwicklungsprozess:
   ```bash
   skaffold dev --profile=dev
   ```

8. Überprüfen Sie die Kubernetes-Dienste in einem separaten Terminal:
   ```bash
   kubectl get svc 
   kubectl get pods 
   kubectl get ingress
   ```

## Systemzugriff

9. Nach erfolgreicher Einrichtung können Sie auf folgende Systemkomponenten zugreifen:

   | Komponente | URL | Funktion                             |
   |------------|-----|--------------------------------------|
   | Frontend   | [http://app.wahlorant.localhost/](http://app.wahlorant.localhost/) | Benutzeroberfläche des Wahlsystems   |
   | Backend    | [http://api.wahlorant.localhost/api-docs/](http://api.wahlorant.localhost/api-docs/) | API-Dokumentation und Schnittstellen |
   | Adminer    | [http://adminer.wahlorant.localhost/](http://api.wahlorant.localhost/api-docs/) | (Dev Only) Datenbank Administration  |

