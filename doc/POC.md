# PoC: GitOps з Argo CD на локальному Kubernetes (k3d)

Ціль: підняти локальний кластер Kubernetes у **k3d**, встановити **Argo CD**, надати команді доступ до веб‑інтерфейсу та задеплоїти демо‑застосунок через GitOps.

---

## 1) Передумови

- macOS / Linux / Windows (WSL2)
- Docker Engine / Docker Desktop (для k3d). *Як альтернатива*: Podman (експериментально для k3d; бажано rootful + `podman-docker`).
- `kubectl` v1.27+  
- (Опційно) `argocd` CLI

> Примітка про ліцензії: Docker Desktop має бізнес‑обмеження (комерційна ліцензія для компаній >250 співробітників або доходу >$10M). Для PoC — ок, на проді розглядаємо Podman/Colima/Minikube‑VM.

---

## 2) Розгортання Kubernetes у k3d

### Встановлення k3d
```bash
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
# перевірка
k3d version