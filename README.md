# Ansible Deployment Repository

Dieses Repository ist eine Sammlung von Konfigurationsdateien und '# Workflows, die verwendet werden, um eine automatisierte Umgebung einzurichten.
Es umfasst die Bereitstellung von Jenkins, Docker-basierten Webanwendungen und einen Nginx-Reverse-Proxy mithilfe von Ansible und GitHub Actions.

## Inhalt

- **Workflow-Datei**: Enthält den GitHub Actions Workflow zur Automatisierung der Bereitstellung.
- **hosts.ini**: Inventardatei mit den Serverinformationen.
- **playbook.yml (main.yml)**: Ansible-Playbook zur Konfiguration der Server.
- **NginxConfig.conf**: Konfigurationsdatei für den Nginx-Webserver.
- **sshkey** und **sshkey.pub**: SSH-Schlüssel für die Authentifizierung.

## Repository-Struktur
    .
    ├── .github/workflows
    │   └── main.yml          # GitHub Workflow zur Ausführung des Ansible-Playbooks
    ├── hosts.ini             # Inventar-Datei für Ansible
    ├── playbook.yml          # Haupt-Playbook zur Serverkonfiguration
    ├── nginx_frontend.conf   # Nginx-Konfigurationsdatei
    ├── sshkey                # Privater SSH-Schlüssel (nicht öffentlich teilen!)
    ├── sshkey.pub            # Öffentlicher SSH-Schlüssel
    └── data.csv              # Beispieldaten für den Backend-Dienst

## Voraussetzungen

- Git
- Ansible
- Ein GitHub-Account mit Zugriff auf dieses Repository
- SSH-Zugriff auf die Zielserver
- Azure_Container_Rigestry(für speicher deine Contanetr basierte Anwendung)

## Installation & Konfiguration anpassen
  1. Klone das Repository auf deinen lokalen Rechner:
        ```bash
        git clone https://github.com//mohammadi-amir/Ansible.git
        cd Ansible
        ```

2. Stelle sicher, dass Ansible auf deinem System installiert ist:
    ```bash
    ansible --version
    ```

3. Bearbeite die Datei hosts.ini und ersetze <deine-zeil-Server-IP> mit der IP deines Zielservers.

    Füge die notwendigen Zugangsdaten (z.B. Azure Registry Passwort) in den Secrets deines GitHub-Repositories hinzu.

4. GitHub Actions aktivieren

    Der Workflow (main.yml) wird automatisch ausgeführt, wenn Code gepusht wird.

    Stelle sicher, dass der private SSH-Schlüssel in den Repository-Secrets (ähnlich SSH_PRIVATE_KEY) hinterlegt ist.

5. Ansible-Playbook ausführen

    Der Workflow führt das Playbook playbook.yml aus und richtet die Umgebung ein.


  
## Verwendung

### GitHub Actions Workflow

Der GitHub Actions Workflow (`.github/workflows/ansible.yml`) automatisiert die Bereitstellung des Ansible-Playbooks auf den Zielservern.

- **Checkout code**: Lädt den Code aus dem Repository herunter.
- **Run playbook**: Führt das Ansible-Playbook (`main.yml`) aus.

### Ansible Playbook

Das Ansible-Playbook (`main.yml`) konfiguriert die Server gemäß den in der `hosts.ini` Datei angegebenen Informationen.

### Nginx-Konfiguration

Die `NginxConfig.conf` Datei enthält die Konfiguration für den Nginx-Webserver. Diese Datei wird während der Ausführung des Playbooks auf die Zielserver kopiert.

## Inventardatei

Die `hosts.ini` Datei enthält die Informationen über die Zielserver. Beispiel:

```ini
[service]
<deine-ziel-Server-IP> ansible_ssh_private_key_file=/tmp/sshkey ansible_user=user
