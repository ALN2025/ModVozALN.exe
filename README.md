<div align="center">

# 🎙️ ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.9.1-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
[![Plataforma](https://img.shields.io/badge/plataforma-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/ALN2025/ModVozALN.exe)
[![Download](https://img.shields.io/badge/⬇️_download-ModVozALN.exe-ec4899?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe)
[![Dev](https://img.shields.io/badge/Dev-ALN-a855f7?style=for-the-badge)](https://github.com/ALN2025)

**Mod De Voz Dev ⩿ A.L.N/⪀**

*Instale o mod completo em poucos cliques — sem editar Java, sem mexer no Engine.dll, sem pedir source*

</div>

---

## 📥 Download

| Arquivo | Descrição |
|---------|-----------|
| [**ModVozALN.exe**](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe) | Instalador único (~14 MB) — **tudo já embutido** |

> ⚠️ Baixe **somente** o executável. Não é necessário pasta `pack/`, código-fonte ou JARs separados.

---

## 📦 Onde vão os JARs? (`l2voice-bridge.jar` + `jedis-5.1.2.jar`)

Os dois JARs vão na **mesma pasta `libs` onde está o `server.jar`** (e os demais JARs do GameServer).

| Tipo de pack | Pasta correta | ❌ Não coloque aqui |
|--------------|---------------|---------------------|
| **BrProject / L2JBR** | `Brproject_Distribution/libs/` | `game/libs/` |
| **L2jMega / aCis** | `pack/libs/` ou `game/libs/` (onde o `.bat` aponta o `-cp`) | pasta vazia só com os JARs de voz |
| **Qualquer revisão** | A pasta **libs** que você informar no instalador (campo 3) | — |

### BrProject (uma `libs` só na raiz)

```
Brproject_Distribution/
  libs/              ← server.jar + dependências + l2voice-bridge.jar + jedis-5.1.2.jar
  game/              ← config, data (SEM libs aqui)
  login/
  voice/
```

O instalador copia os JARs para a pasta **libs** que você selecionar. No BrProject, selecione `...\Brproject_Distribution\libs`.

---

## ✨ O que o instalador faz

| Componente | Instala automaticamente |
|------------|-------------------------|
| 🖥️ **GameServer** | `l2voice-bridge.jar`, `jedis-5.1.2.jar` → pasta **libs** informada |
| ⚙️ **Config** | `l2jalnvoice.properties`, HTML `voip-link.htm` → pasta **game** |
| 🔧 **Scripts** | `INICIAR-GS-COM-VOZ.bat` + `-javaagent` nos `.bat` existentes |
| 🎮 **Cliente L2** | `l2voice.dll`, `voice.ini`, `L2VoiceInject.exe` → pasta **system** |
| 📡 **Voice-server** | binários do voice (se embutidos no pack) → pasta **voice** |

**Sem editar `.java`** — o bridge usa `-javaagent` e reflexão no JAR do GS.

---

## 🚀 Como instalar

### 1️⃣ Execute o instalador

1. Baixe e abra **`ModVozALN.exe`**
2. Informe **cada pasta separadamente**:

| Campo | O que é |
|-------|---------|
| **1. Raiz da pack** | Ex.: `Brproject_Distribution` (preenche as demais) |
| **2. Pasta game** | `config/custom` + `data/html` → `...\game` |
| **3. Pasta libs** | Onde está `server.jar` → `...\libs` na **raiz** |
| **4. Cliente system** | Pasta com `L2.exe` e `Engine.dll` |
| **5. Pasta voice** | Onde roda o voice-server → `...\voice` |

3. IP do voice-server (`127.0.0.1` local · IP público na VPS)
4. Clique em **INSTALAR**

O log mostra as classes detectadas no JAR (World/Player) — **não precisa de source** nem configurar `fork.*` manualmente.

### 2️⃣ Suba os serviços (nessa ordem)

```
Memurai/Redis  →  Login Server  →  L2VoiceServer.exe  →  GameServer
```

| Serviço | Como iniciar |
|---------|--------------|
| 🗄️ Redis | Memurai em `127.0.0.1:6379` |
| 📡 Voice | **`L2VoiceServer.exe`** (deixe aberto) |
| 🖥️ GS | **`INICIAR-GS-COM-VOZ.bat`** ou `.bat` original (javaagent injetado) |
| 🎮 Cliente | **`L2VoiceInject.exe`** (não use `L2.exe` direto) |

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
| ☕ Java | JDK 11+ no GameServer (conforme sua pack) |
| 🗄️ Redis | Memurai ou Redis em `127.0.0.1:6379` |
| 🔥 Firewall | UDP **17666** + TCP **17667** (jogadores remotos) |

---

## 🧩 Revisões suportadas (auto-detect no JAR)

O bridge descobre sozinho **World**, **Player** e **posição** lendo o `server.jar` — sem source da revisão.

| Pack | Suporte |
|------|---------|
| ✅ BrProject / L2JBR | Nativo |
| ✅ L2jMega / L2JALN | Nativo |
| ✅ aCis / RusaCis | Nativo |
| ✅ L2jFrozen | Nativo |
| ✅ L2JServer | Nativo |
| ✅ L2Emu / EmuDev | Nativo |
| ✅ L2jMobius | Nativo |
| ✅ Revisão custom | Scan automático do JAR; override opcional com `fork.*` |

Override só se a revisão for muito diferente (raro):

```properties
l2jalnvoice.fork.world = pacote.model.World
l2jalnvoice.fork.player = pacote.model.actor.Player
```

---

## ❓ Perguntas frequentes

<details>
<summary><b>📁 Os JARs vão em game/libs ou na libs da raiz?</b></summary>

Na pasta <b>libs onde o GameServer carrega os JARs</b>. No <b>BrProject</b> é só uma <code>libs</code> na raiz da pack (<code>Brproject_Distribution/libs</code>), junto com <code>server.jar</code>. <b>Não</b> crie <code>game/libs</code> só para o mod.
</details>

<details>
<summary><b>🔒 Preciso do código-fonte?</b></summary>

Não. O instalador embute tudo no <code>.exe</code>. O bridge usa reflexão no JAR que você já tem.
</details>

<details>
<summary><b>🛠️ Preciso editar GameServer.java?</b></summary>

Não. Use <code>-javaagent:l2voice-bridge.jar</code> (o instalador configura nos <code>.bat</code>).
</details>

<details>
<summary><b>🎯 O Engine.dll é alterado?</b></summary>

Não. Inicie pelo <code>L2VoiceInject.exe</code>.
</details>

<details>
<summary><b>🌐 Teste local vs VPS</b></summary>

<ul>
<li><b>Local:</b> IP <code>127.0.0.1</code> + Memurai + voice-server na mesma máquina</li>
<li><b>VPS:</b> IP público do voice-server + portas 17666/17667 no firewall</li>
</ul>
</details>

---

## 📞 Suporte

| Canal | Link |
|-------|------|
| 🐙 GitHub | [ALN2025/ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe) |
| 🌐 ScriptClean | [scriptclean.com.br](https://scriptclean.com.br) |

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

*Distribuição pública: apenas o instalador. Código-fonte e assets de desenvolvimento permanecem em repositório privado.*

</div>
