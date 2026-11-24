# Meinkraft

## Packwiz Installation

```bash
sudo apt update
sudo apt install -y git golang-go

go install github.com/packwiz/packwiz@latest

export PATH="$PATH:$(go env GOPATH)/bin"

packwiz --version
```

## Updates durchführen

### Mods hinzufügen

```bash
packwiz modrinth add [MODNAME]
packwiz refresh
```

### Mods aktualisieren

```bash
packwiz update --all
packwiz refresh
```

### Änderungen veröffentlichen

```bash
git diff
git add --all
git commit -m "feat: update Minecraft mods"
git push
```

### Server aktualisieren

```bash
sudo systemctl stop minecraft

# Backup
sudo tar -czf \
  "/var/backups/minecraft-world-$(date +%F-%H%M).tar.gz" \
  -C /opt/minecraft world

# Server wieder starten, packwiz synchronisiert die Mods automatisch
sudo systemctl start minecraft

journalctl -u minecraft -f
```
