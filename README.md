<div align="center">

# 🎙️ ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.9.13-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
[![Plataforma](https://img.shields.io/badge/plataforma-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/ALN2025/ModVozALN.exe)
[![Download](https://img.shields.io/badge/⬇️_download-ModVozALN.zip-ec4899?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.zip)
[![Dev](https://img.shields.io/badge/Dev-ALN-a855f7?style=for-the-badge)](https://github.com/ALN2025)

**Mod De Voz Dev ⩿ A.L.N/⪀**

*Instale o mod completo em poucos cliques — sem editar Java, sem mexer no Engine.dll, sem pedir source*

</div>

---

## 📥 Download

| Arquivo | Descrição |
|---------|-----------|
| [**ModVozALN.zip**](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.zip) | **Recomendado** — extraia e execute `ModVozALN.exe` (~39 MB) |
| [ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe) | Direto (o navegador pode bloquear e deixar arquivos *Não confirmado* em Downloads) |

> ⚠️ Use o **ZIP** se o Chrome/Edge travar o download. Não precisa de pasta `pack/`, código-fonte ou JARs separados.

<details>
<summary><b>Arquivos &quot;Não confirmado&quot; na pasta Downloads?</b></summary>

O navegador interrompeu o download do `.exe` (proteção do Windows). Pode **apagar** esses arquivos. Baixe o **ModVozALN.zip**, extraia com botão direito → *Extrair tudo*, e rode o `.exe` de dentro da pasta.

</details>

---

## ✨ O que o instalador faz

| Componente | Instala automaticamente |
|------------|-------------------------|
| 🖥️ **GameServer** | `l2jalnvoice.properties`, HTML, `INICIAR-GS-COM-VOZ.bat` |
| 📚 **Libs** | `l2voice-bridge.jar`, `jedis-5.1.2.jar` |
| 🔧 **Scripts** | Injeta `-javaagent` nos `.bat` existentes — **sem editar `.java`** |
| 🎮 **Cliente L2** | `l2voice.dll`, `voice.ini`, `L2VoiceInject.exe` |
| 📡 **Voice-server** | `L2VoiceServer.exe`, `voice-server.exe`, scripts de inicialização |

---

## 📂 Pastas no instalador

Informe **quatro pastas** — cada uma vai para a seção correta:

| Campo | Selecione |
|-------|-----------|
| **Game** | Pasta do GameServer (`config/custom` + `data/html`) |
| **Libs** | Pasta onde ficam os JARs do servidor (`server.jar`, etc.) |
| **Voice** | Pasta do voice-server na raiz da pack |
| **System** | Pasta `system` do cliente L2 (`L2.exe`, `Engine.dll`) |

### 📦 Arquivos em cada pasta

<details>
<summary><b>🖥️ Game — config + data</b></summary>

| Arquivo | Destino |
|---------|---------|
| `l2jalnvoice.properties` | `game/config/custom/` |
| `voip-link.htm` | `game/data/html/mods/voip/` |
| `INICIAR-GS-COM-VOZ.bat` | `game/` |

</details>

<details>
<summary><b>📚 Libs — JARs do servidor</b></summary>

| Arquivo | Destino |
|---------|---------|
| `l2voice-bridge.jar` | pasta **libs** informada |
| `jedis-5.1.2.jar` | pasta **libs** informada |

Use a **mesma pasta libs** onde o `.bat` do GameServer já carrega os JARs (`-cp`).

</details>

<details>
<summary><b>📡 Voice — raiz da pack</b></summary>

| Arquivo | Destino |
|---------|---------|
| `L2VoiceServer.exe` | pasta **voice** informada |
| `voice-server.exe` | `voice/bin/` |
| `iniciar-voice-server.bat` | pasta **voice** |

</details>

<details>
<summary><b>🎮 System — cliente L2</b></summary>

| Arquivo | Destino |
|---------|---------|
| `l2voice.dll` | pasta **system** informada |
| `voice.ini` | pasta **system** informada |
| `L2VoiceInject.exe` | pasta **system** informada |

Inicie pelo **L2VoiceInject.exe** — o `Engine.dll` **não** é alterado.

</details>

---

## 🚀 Como instalar

### 1️⃣ Execute o instalador

1. Baixe e abra **`ModVozALN.exe`**
2. Preencha **Game**, **Libs**, **Voice** e **System**
3. Informe o **IP do voice-server** (`127.0.0.1` local · IP público na VPS)
4. Clique em **INSTALAR**

### 2️⃣ Suba os serviços (nessa ordem)

```
Memurai/Redis  →  Login Server  →  L2VoiceServer.exe  →  GameServer
```

| Serviço | Como iniciar |
|---------|--------------|
| 🗄️ Redis | Memurai em `127.0.0.1:6379` |
| 📡 Voice | Duplo-clique em **`L2VoiceServer.exe`** (deixe aberto) |
| 🖥️ GS | **`INICIAR-GS-COM-VOZ.bat`** (ou `.bat` do GS — javaagent já injetado) |
| 🎮 Cliente | **`L2VoiceInject.exe`** na pasta `system` |

---

## 🌐 Teste em VPS (guia para quem for testar online)

> ✅ **Testado local** pelo autor (`127.0.0.1`). **VPS/online** é para a comunidade testar — siga este guia.

### Cenário típico

| Onde roda | O quê |
|-----------|--------|
| **VPS Windows** | Login + GameServer + Redis/Memurai + `L2VoiceServer.exe` |
| **PC do jogador** | Cliente L2 com `l2voice.dll` + `voice.ini` + `L2VoiceInject.exe` |

### Passo a passo na VPS

1. **Instale o mod** com `ModVozALN.exe` na pack do servidor (Game, Libs, Voice, System do cliente pode ser em outro PC).
2. No campo **IP do voice-server**, use o **IP público da VPS** (ex.: `191.44.11.151`) — **não** use `127.0.0.1` se jogadores forem de outro PC.
3. **Firewall da VPS** — libere:
   - UDP **17666** (áudio)
   - TCP **17667** (WebSocket / controle)
4. Suba na ordem: **Redis** → **Login** → **`L2VoiceServer.exe`** → **GameServer**.
5. Confirme no log do instalador: `ModVozALN v1.9.13` e `[Pack] OK`.

### No PC do jogador (cliente)

1. Rode o instalador apontando **System** para a pasta do `L2.exe`.
2. Use o **mesmo IP público** da VPS no instalador (gera o `voice.ini` com `ws://IP:17667/ws`).
3. Inicie o jogo pelo **`L2VoiceInject.exe`** — não pelo `L2.exe` direto.

### `voice.ini` — preciso mexer?

**Em geral, não.** O instalador gera assim:

```ini
overlay = 1
audio_profile = auto
```

A DLL **detecta sozinha** o hardware:

| Seu equipamento | Comportamento |
|-----------------|---------------|
| **Headset** USB/BT com mic | Fala + escuta + painel |
| Notebook (mic integrado) | Só escuta |
| Fone sem mic | Só escuta |
| Mic de mesa | Fala + escuta |

Quem tem **headset** pode deixar o padrão — não precisa editar nada (como no teste local do autor).

Só edite `voice.ini` se quiser **forçar** um modo:

```ini
audio_profile = headset      ; sempre tenta falar
audio_profile = notebook     ; sempre só escuta
audio_profile = receive_only ; nunca transmite
```

### Checklist rápido VPS

- [ ] IP público no instalador (servidor **e** cliente)
- [ ] Portas **17666/17667** abertas no firewall da VPS
- [ ] Memurai/Redis rodando na VPS
- [ ] `L2VoiceServer.exe` aberto e sem erro
- [ ] GameServer com `-javaagent` (instalador injeta nos `.bat`)
- [ ] Cliente abre via **`L2VoiceInject.exe`**
- [ ] Log do instalador mostra **v1.9.13**

### 3️⃣ No jogo

| Tecla | Função |
|-------|--------|
| **INSERT** | Abrir painel de voz |
| **H** (segurar) | Falar por proximidade (PTT) |

---

## 📋 Requisitos

| Item | Detalhe |
|------|---------|
| 💻 SO | Windows 10/11 |
| ☕ Java | JDK conforme sua pack no GameServer |
| 🗄️ Redis | Memurai ou Redis em `127.0.0.1:6379` |
| 🔥 Firewall | UDP **17666** + TCP **17667** (jogadores remotos) |

---

## 🧩 Packs suportadas (auto-detect)

O bridge descobre sozinho **World**, **Player** e **posição** lendo o JAR do GameServer — **sem source** da revisão.

| Pack | Suporte |
|------|---------|
| ✅ BrProject / L2JBR | Nativo |
| ✅ L2jMega / L2JALN | Nativo |
| ✅ aCis / RusaCis | Nativo |
| ✅ L2jFrozen | Nativo |
| ✅ L2JServer | Nativo |
| ✅ L2Emu / L2Off / EmuDev | Nativo |
| ✅ L2jMobius | Nativo |
| ⚙️ Pack personalizada | Scan automático do JAR; override opcional com `fork.*` |

Override só se a revisão for muito diferente (raro):

```properties
l2jalnvoice.fork.world = pacote.model.World
l2jalnvoice.fork.player = pacote.model.actor.Player
```

---

## ❓ Perguntas frequentes

<details>
<summary><b>📁 Onde vai a pasta libs?</b></summary>

Na pasta onde o GameServer <b>já carrega os JARs</b> — pode ser <code>libs</code> na raiz da pack ou <code>game/libs</code>, conforme o <code>.bat</code> da sua revisão. Informe esse caminho no campo <b>Libs</b>. Não crie uma pasta libs separada só com os JARs do mod.
</details>

<details>
<summary><b>🔒 Preciso do código-fonte ou da pasta pack?</b></summary>

Não. O instalador traz <b>tudo embutido</b> no <code>.exe</code>. Basta baixar, executar e instalar.
</details>

<details>
<summary><b>🛠️ Preciso editar GameServer.java?</b></summary>

Não. O bridge usa <code>-javaagent</code> e é configurado automaticamente pelo instalador nos <code>.bat</code> de subida.
</details>

<details>
<summary><b>🎯 O Engine.dll é alterado?</b></summary>

Não. O cliente inicia pelo <code>L2VoiceInject.exe</code>, que carrega a DLL de voz sem patch no engine.
</details>

<details>
<summary><b>⚙️ Preciso configurar classes World/Player?</b></summary>

Em geral não — o bridge detecta no JAR automaticamente. Só em packs muito customizadas, use <code>fork.*</code> em <code>l2jalnvoice.properties</code> (veja seção acima).
</details>

<details>
<summary><b>🌐 Local vs VPS (resumo)</b></summary>

<ul>
<li><b>Local:</b> IP <code>127.0.0.1</code> — tudo na mesma máquina (testado pelo autor)</li>
<li><b>VPS:</b> IP público + firewall — veja seção <b>Teste em VPS</b> acima</li>
</ul>
</details>

<details>
<summary><b>🎧 Headset / notebook / fone sem mic</b></summary>

O <code>voice.ini</code> padrão usa <code>audio_profile = auto</code>. A DLL detecta o dispositivo no Windows — não é necessário configurar por jogador. Headset = fala e escuta; notebook com mic integrado = só escuta.
</details>

---

## ⚠️ Suporte

> **Não há suporte individual.** Leia este README e a documentação antes de instalar.

| O quê | Onde |
|-------|------|
| 📖 Este guia | README do repositório |
| 📖 Integração / packs | Arquivos em `game/docs/l2voice/` após instalar |
| 🐙 Releases | [ALN2025/ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe) |
| ❌ DM / WhatsApp / pedido de source | **Não atendido** |

Problemas comuns: IP errado, firewall, exe antigo do GitHub, cliente aberto pelo `L2.exe` em vez do `L2VoiceInject.exe`, Redis parado.

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

*Distribuição pública: apenas o instalador. Código-fonte e assets de desenvolvimento permanecem em repositório privado.*

</div>
