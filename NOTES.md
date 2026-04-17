# NOTES.md — Diário técnico do projecto
##EXEMPLO##
## [2025-04-17] Erro ao ligar via SSH — Connection refused

**Problema:**
Ao correr `ssh utilizador@192.168.1.50` recebi o erro:
`ssh: connect to host 192.168.1.50 port 22: Connection refused`

**O que tentei:**
- Verifiquei o IP com `hostname -I` — estava correcto
- Tentei fazer ping à máquina — respondia, portanto rede ok

**Causa:**
O serviço SSH não estava activo. Esqueci-me de correr
`sudo systemctl start ssh` após a instalação.

**Solução:**
```bash
sudo systemctl enable ssh   # para arrancar automaticamente
sudo systemctl start ssh
```

**O que aprendi:**
`enable` faz o serviço arrancar no boot. `start` arranca agora.
São dois comandos diferentes — um não implica o outro.

---

## [2025-04-17] VM sem acesso à internet

**Problema:** `sudo apt update` falhava com erro de rede.

**Causa:** Rede da VM estava em modo NAT em vez de Bridged.

**Solução:** VirtualBox → Settings → Network → Bridged Adapter.

---
