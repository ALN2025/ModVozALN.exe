<div align="center">

# ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.9.5-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
[![Plataforma](https://img.shields.io/badge/plataforma-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/ALN2025/ModVozALN.exe)
[![Download](https://img.shields.io/badge/download-ModVozALN.exe-ec4899?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe)

**Mod De Voz Dev ⩿ A.L.N/⪀**

</div>

---

## Download

Baixe apenas o arquivo [**ModVozALN.exe**](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe). O instalador já contém os arquivos do mod — não é necessário pasta `pack/` nem código-fonte.

---

## Pastas no instalador

Informe **quatro pastas** no instalador. Cada uma corresponde a uma seção da sua pack ou do cliente:

| Campo | Selecione |
|-------|-----------|
| **Game** | Pasta do GameServer (`config`, `data`) |
| **Libs** | Pasta onde ficam os JARs do servidor |
| **Voice** | Pasta do voice-server na raiz da pack |
| **System** | Pasta `system` do cliente L2 |

---

## Arquivos instalados em cada pasta

### Game (`config` + `data`)

| Arquivo | Destino |
|---------|---------|
| `l2jalnvoice.properties` | `game/config/custom/` |
| `voip-link.htm` | `game/data/html/mods/voip/` |
| `INICIAR-GS-COM-VOZ.bat` | `game/` (script de subida com javaagent) |

O instalador também injeta `-javaagent:l2voice-bridge.jar` nos `.bat` de GameServer que já existirem.

### Libs (JARs do servidor)

| Arquivo | Destino |
|---------|---------|
| `l2voice-bridge.jar` | pasta **libs** informada |
| `jedis-5.1.2.jar` | pasta **libs** informada |

Coloque na **mesma pasta libs** onde já está o JAR principal do GameServer (o que o `.bat` usa no `-cp`). Não crie uma pasta libs separada só com os JARs do mod.

### Voice (raiz da pack)

| Arquivo | Destino |
|---------|---------|
| `L2VoiceServer.exe` | pasta **voice** informada |
| `voice-server.exe` | `voice/bin/` |
| `iniciar-voice-server.bat` | pasta **voice** (se incluído no pack) |

### System (cliente L2)

| Arquivo | Destino |
|---------|---------|
| `l2voice.dll` | pasta **system** informada |
| `voice.ini` | pasta **system** informada |
| `L2VoiceInject.exe` | pasta **system** informada |

Inicie o jogo pelo **L2VoiceInject.exe**, não pelo `L2.exe` direto. O `Engine.dll` não é alterado.

---

## Como instalar

1. Execute **ModVozALN.exe**
2. Preencha **Game**, **Libs**, **Voice** e **System**
3. Informe o **IP do voice-server** (`127.0.0.1` em teste local, IP público na VPS)
4. Clique em **INSTALAR**
5. Confira o log — deve listar os arquivos copiados em cada pasta

---

## Ordem para subir o servidor

```
Redis/Memurai  →  Login Server  →  L2VoiceServer.exe  →  GameServer
```

| Etapa | Ação |
|-------|------|
| 1 | Redis ou Memurai em `127.0.0.1:6379` |
| 2 | Login Server da pack |
| 3 | **L2VoiceServer.exe** na pasta voice (deixe a janela aberta) |
| 4 | GameServer pelo `.bat` com `-javaagent` (`INICIAR-GS-COM-VOZ.bat` ou script original) |
| 5 | Cliente via **L2VoiceInject.exe** na pasta system |

No log do GameServer deve aparecer que o javaagent L2Voice foi carregado.

---

## Requisitos

| Item | Detalhe |
|------|---------|
| Sistema | Windows 10/11 |
| Java | Versão exigida pela sua pack no GameServer |
| Redis | Memurai ou Redis em `127.0.0.1:6379` |
| Firewall | UDP **17666** e TCP **17667** (jogadores fora da máquina local) |

---

## No jogo

| Tecla | Função |
|-------|--------|
| INSERT | Painel de voz |
| H (segurar) | Falar por proximidade (PTT) |

---

## Perguntas frequentes

**Preciso do código-fonte do GameServer?**  
Não. O mod usa `-javaagent` e reflexão no JAR que você já tem.

**Preciso editar `GameServer.java`?**  
Não. Basta o `-javaagent:l2voice-bridge.jar` no `.bat` de subida.

**Onde vai a pasta libs?**  
Na pasta onde o GameServer já carrega os JARs — pode ser `libs` na raiz da pack ou `game/libs`, conforme o `.bat` da sua revisão. Use o mesmo caminho no campo **Libs** do instalador.

**Classes World/Player precisam ser configuradas?**  
Em geral não. O bridge detecta automaticamente no JAR. Só em revisões muito customizadas, opcionalmente em `l2jalnvoice.properties`:

```properties
l2jalnvoice.fork.world = pacote.model.World
l2jalnvoice.fork.player = pacote.model.actor.Player
```

---

## Repositório

[github.com/ALN2025/ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe)

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

</div>
