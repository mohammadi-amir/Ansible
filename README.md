# Ansible Deployment Repository

Dieses Repository enthält den Code und die Konfigurationsdateien für die Bereitstellung einer Webserver-Infrastruktur mit Ansible .

## Inhalt

- **Workflow-Datei**: Enthält den GitHub Actions Workflow zur Automatisierung der Bereitstellung.
- **hosts.ini**: Inventardatei mit den Serverinformationen.
- **playbook.yml (main.yml)**: Ansible-Playbook zur Konfiguration der Server.
- **NginxConfig.conf**: Konfigurationsdatei für den Nginx-Webserver.
- **sshkey** und **sshkey.pub**: SSH-Schlüssel für die Authentifizierung.

## Voraussetzungen

- Git
- Ansible
- Ein GitHub-Account mit Zugriff auf dieses Repository
- SSH-Zugriff auf die Zielserver

## Installation

1. Klone das Repository auf deinen lokalen Rechner:
    ```bash
    git clone https://github.com/dein-benutzername/dein-repository.git
    cd dein-repository
    ```

2. Stelle sicher, dass Ansible auf deinem System installiert ist:
    ```bash
    ansible --version
    ```

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
