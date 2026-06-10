<div align="center">

# 🎙️ ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.9.43-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
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
| [**ModVozALN.zip**](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.zip) | **Recomendado** — contém `ModVozALN.exe` + `VERSION.txt` (~39 MB) |
| [ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe) | Direto (o navegador pode bloquear e deixar arquivos *Não confirmado* em Downloads) |

> ⚠️ Use o **ZIP** se o Chrome/Edge travar o download. Apague ZIP antigo na pasta Downloads antes de baixar de novo.

> **Como saber se baixou a versão certa:** dentro do ZIP, abra `VERSION.txt` — deve mostrar **v1.9.43**. O `ModVozALN.exe` deve ter **~39 MB** (versão antiga ~32 MB não instala voice).

### Conteúdo do ZIP (v1.9.43)

| Arquivo | Função |
|---------|--------|
| `ModVozALN.exe` | Instalador GUI (~39 MB) |
| `VERSION.txt` | Confirma a versão baixada |
| `LEIA-ME-DOWNLOAD.txt` | Instruções rápidas após extrair |

Ao abrir o instalador, a splash mostra o banner **ScriptClean SOLUTIONS** + **Modo de voz ALN**. O título da janela deve exibir **`v1.9.43`** com **4 campos**: Game, Libs, Voice, System.

<details>
<summary><b>Arquivos &quot;Não confirmado&quot; na pasta Downloads?</b></summary>

O navegador interrompeu o download do `.exe` (proteção do Windows). Pode **apagar** esses arquivos. Baixe o **ModVozALN.zip**, extraia com botão direito → *Extrair tudo*, e rode o `.exe` de dentro da pasta.

</details>

---

## ✨ O que o instalador faz

| Campo | Instala automaticamente |
|-------|-------------------------|
| 🖥️ **Game** | `l2jalnvoice.properties`, HTML, docs, `L2GameServer.exe`, `gs-voz-launch.cfg` |
| 📚 **Libs** | `l2voice-bridge.jar`, `jedis-5.1.2.jar`, `-javaagent` nos `.bat` |
| 📡 **Voice** | `L2VoiceServer.exe`, `voice-server.exe`, scripts |
| 🎮 **System** | `l2voice.dll`, `voice.ini`, `L2VoiceInject.exe` |

Tudo **sem editar `.java`** e **sem patch no `Engine.dll`**.

---

## 📂 Pastas no instalador

O instalador pede **quatro pastas** — cada componente no lugar certo:

| Campo | O que selecionar | Arquivos instalados |
|-------|------------------|---------------------|
| **Game** | Pasta `game/` ou `game/config/custom/` (ou raiz da pack) | `l2jalnvoice.properties`, HTML, docs, `.bat` do GS |

> **Campo Game:** selecione **`game/`** ou **`gameserver/`** (não use `login/` nem `libs/` aqui). Pode ser a **raiz da pack** (pasta com `login` + `game`).
| **Libs** | Pasta dos JARs do servidor | `l2voice-bridge.jar`, `jedis-5.1.2.jar`, `-javaagent` nos `.bat` |
| **Voice** | Pasta `voice/` na raiz da pack | `L2VoiceServer.exe`, `bin/voice-server.exe`, scripts |
| **System** | Pasta `system` do cliente L2 | `l2voice.dll`, `voice.ini`, `L2VoiceInject.exe` |

> Ao escolher **Game**, os campos **Libs** e **Voice** são sugeridos automaticamente. Confira antes de instalar.

> Marque **“Subpasta voice/”** (padrão) para gerar `SuaPack\voice\` com os executáveis do voice-server.

---

## 📚 Para onde vai cada arquivo

O instalador copia tudo nas pastas que **já existem** na sua pack. Use a mesma estrutura do seu `.bat` do GameServer.

### Mapa completo

| Arquivo | Pasta de destino |
|---------|------------------|
| `l2jalnvoice.properties` | `game/config/custom/` |
| `voip-link.htm` | `game/data/html/mods/voip/` |
| `L2GameServer.exe` | `game/` (janela L2j, sem CMD preto) |
| `gs-voz-launch.cfg` | `game/` (config Java/classpath do launcher) |
| `l2voice-bridge.jar` | pasta **libs** do servidor (onde está o `server.jar`) |
| `jedis-5.1.2.jar` | mesma pasta **libs** do `server.jar` |
| `L2VoiceServer.exe` | `voice/` (raiz da pack) |
| `voice-server.exe` | `voice/bin/` |
| `iniciar-voice-server.bat` | `voice/` |
| `l2voice.dll` | pasta do `L2.exe` (cliente) |
| `voice.ini` | pasta do `L2.exe` (cliente) |
| `L2VoiceInject.exe` | pasta do `L2.exe` (cliente) |

### Pasta **libs** — onde colocar os JARs

Os JARs do mod vão na **mesma pasta** onde o GameServer já carrega os JARs (`-cp` do `.bat`).  
**Não crie** uma pasta libs separada só com os arquivos do mod.

Abra o `.bat` do GS e veja o `-cp`:

| Se o `.bat` usa… | Os JARs vão para… |
|------------------|-------------------|
| `-cp "./libs/*"` dentro de `game/` | `game/libs/` |
| `-cp "../libs/*"` a partir de `game/` | `libs/` na **raiz da pack** |
| `-cp "./lib/*"` | `game/lib/` |

O instalador procura nesta ordem: `game/libs` → `game/lib` → `libs` na raiz da pack → cria `game/libs/` se nada existir.

### Exemplo — libs na raiz da pack

```
MinhaPack/
├── libs/              ← server.jar + l2voice-bridge.jar + jedis
├── game/
│   ├── config/
│   └── data/
└── voice/             ← criada pelo instalador
```

### Exemplo — libs dentro de game

```
MinhaPack/
├── game/
│   ├── config/
│   ├── data/
│   └── libs/          ← server.jar + l2voice-bridge.jar + jedis
└── voice/
```

### Conferir após instalar

Na pasta **libs** correta devem existir `l2voice-bridge.jar` e `jedis-5.1.2.jar`, e o `.bat` do GS deve ter `-javaagent` apontando para o bridge nessa mesma pasta.

Inicie o cliente pelo **L2VoiceInject.exe** — o `Engine.dll` **não** é alterado.

---

## 🚀 Como instalar

### 1️⃣ Execute o instalador

1. Baixe e extraia **`ModVozALN.zip`** e abra **`ModVozALN.exe`**
2. Preencha **Game**, **Libs**, **Voice** e **System**
3. Confira se **Libs** é a mesma pasta do `-cp` do `.bat` do GS
4. Informe o **IP do voice-server** (`127.0.0.1` local · IP público na VPS)
5. Clique em **INSTALAR**

### 2️⃣ Suba os serviços (nessa ordem)

```
Memurai/Redis  →  Login Server  →  L2VoiceServer.exe  →  GameServer
```

| Serviço | Como iniciar |
|---------|--------------|
| 🗄️ Redis | Memurai em `127.0.0.1:6379` |
| 📡 Voice | Duplo-clique em **`L2VoiceServer.exe`** (deixe aberto) |
| 🖥️ GS | **`L2GameServer.exe`** (voice auto · expande `%JAVA_HOME%` do BrProject) |
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
5. Confirme no log do instalador: `ModVozALN v1.9.43` e `[Pack] OK`.

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
- [ ] `VERSION.txt` no ZIP e log do instalador mostram **v1.9.43**

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

O bridge descobre sozinho **World**, **Player** e **posição** lendo o JAR do GameServer — **sem source** da revisão. O instalador **v1.9.43+** faz o mesmo: lê o `.bat` da pack, escaneia os JARs e instala `L2GameServer.exe` + `gs-voz-launch.cfg` + `fork.*` para **qualquer** revisão L2J (aCis, L2jMega, Mobius, Frozen, L2Off, BrProject, pack customizada).

| Pack | Suporte |
|------|---------|
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

Na mesma pasta onde o <code>server.jar</code> já está — a que o <code>.bat</code> do GS usa no <code>-cp</code> (<code>game/libs/</code>, <code>game/lib/</code> ou <code>libs/</code> na raiz da pack). Veja o <b>mapa completo</b> no README. Não crie uma libs separada só com os JARs do mod.
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

Problemas comuns: IP errado, firewall, ZIP antigo na pasta Downloads (apague e baixe de novo), `VERSION.txt` com versão antiga, cliente aberto pelo `L2.exe` em vez do `L2VoiceInject.exe`, Redis parado, **`L2GameServer.exe` antigo** (reinstale com v1.9.43+ para atualizar launcher e `gs-voz-launch.cfg`).

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

*Distribuição pública: apenas o instalador. Código-fonte e assets de desenvolvimento permanecem em repositório privado.*

</div>
