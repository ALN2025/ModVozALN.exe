<div align="center">

# 🎙️ ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.9.6-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
[![Plataforma](https://img.shields.io/badge/plataforma-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/ALN2025/ModVozALN.exe)
[![Download](https://img.shields.io/badge/⬇️_download-ModVozALN.exe-ec4899?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe)
[![Dev](https://img.shields.io/badge/Dev-ALN-a855f7?style=for-the-badge)](https://github.com/ALN2025)

**Mod De Voz Dev ⩿ A.L.N/⪀**

*Instale o mod em poucos cliques — sem editar Java, sem mexer no Engine.dll*

</div>

---

## 📥 Download

| Arquivo | Descrição |
|---------|-----------|
| [**ModVozALN.exe**](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe) | Instalador único (~14 MB) — arquivos do mod já embutidos |

> ⚠️ Baixe **somente** o executável. Não é necessário pasta `pack/`, código-fonte ou JARs separados.

---

## 📂 Pastas no instalador

Informe **quatro pastas**. Cada campo corresponde à seção correta da pack ou do cliente:

| Campo | Selecione |
|-------|-----------|
| **Game** | Pasta do GameServer (`config`, `data`) |
| **Libs** | Pasta onde ficam os JARs do servidor |
| **Voice** | Pasta do voice-server (geralmente na raiz da pack) |
| **System** | Pasta `system` do cliente L2 |

---

## 📦 Arquivos em cada pasta

### 🖥️ Game — `config` + `data`

| Arquivo | Destino |
|---------|---------|
| `l2jalnvoice.properties` | `game/config/custom/` |
| `voip-link.htm` | `game/data/html/mods/voip/` |
| `INICIAR-GS-COM-VOZ.bat` | `game/` |

O instalador injeta `-javaagent:l2voice-bridge.jar` nos `.bat` de GameServer existentes.

### 📚 Libs — JARs do servidor

| Arquivo | Destino |
|---------|---------|
| `l2voice-bridge.jar` | pasta **libs** informada |
| `jedis-5.1.2.jar` | pasta **libs** informada |

Use a **mesma pasta libs** onde já está o JAR principal do GameServer (a que o `.bat` usa no `-cp`).

### 📡 Voice — raiz da pack

| Arquivo | Destino |
|---------|---------|
| `L2VoiceServer.exe` | pasta **voice** informada |
| `voice-server.exe` | `voice/bin/` |
| `iniciar-voice-server.bat` | pasta **voice** |

### 🎮 System — cliente L2

| Arquivo | Destino |
|---------|---------|
| `l2voice.dll` | pasta **system** informada |
| `voice.ini` | pasta **system** informada |
| `L2VoiceInject.exe` | pasta **system** informada |

Inicie o jogo pelo **L2VoiceInject.exe** — o `Engine.dll` não é alterado.

---

## ✨ O que o instalador faz

| Componente | Ação |
|------------|------|
| 🖥️ **GameServer** | Copia config, HTML e script `INICIAR-GS-COM-VOZ.bat` |
| 📚 **Libs** | Copia `l2voice-bridge.jar` e `jedis-5.1.2.jar` |
| 🔧 **Scripts** | Injeta `-javaagent` nos `.bat` do GS |
| 🎮 **Cliente** | Copia DLL, `voice.ini` e injetor para `system/` |
| 📡 **Voice** | Copia binários do voice-server para a pasta informada |

---

## 🚀 Como instalar

### 1️⃣ Execute o instalador

1. Baixe e abra **`ModVozALN.exe`**
2. Preencha **Game**, **Libs**, **Voice** e **System**
3. Informe o **IP do voice-server** (`127.0.0.1` local · IP público na VPS)
4. Clique em **INSTALAR**
5. Confira o log — arquivos copiados por pasta

### 2️⃣ Suba os serviços (nessa ordem)

```
Memurai/Redis  →  Login Server  →  L2VoiceServer.exe  →  GameServer
```

| Serviço | Como iniciar |
|---------|--------------|
| 🗄️ Redis | Memurai ou Redis em `127.0.0.1:6379` |
| 📡 Voice | **`L2VoiceServer.exe`** (deixe aberto) |
| 🖥️ GS | **`INICIAR-GS-COM-VOZ.bat`** ou `.bat` original (javaagent injetado) |
| 🎮 Cliente | **`L2VoiceInject.exe`** na pasta `system` |

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
| ☕ Java | Versão exigida pela sua pack no GameServer |
| 🗄️ Redis | Memurai ou Redis em `127.0.0.1:6379` |
| 🔥 Firewall | UDP **17666** + TCP **17667** (jogadores remotos) |

---

## 🧩 Revisões compatíveis

O bridge detecta automaticamente as classes **World**, **Player** e posição no JAR — sem source da revisão.

| Revisão | Suporte |
|---------|---------|
| ✅ BrProject / L2JBR | Nativo |
| ✅ L2jMega / L2JALN | Nativo |
| ✅ aCis / RusaCis | Nativo |
| ✅ L2jFrozen | Nativo |
| ✅ L2JServer | Nativo |
| ✅ L2Emu / EmuDev | Nativo |
| ✅ L2jMobius | Nativo |
| ⚙️ Revisão customizada | Scan automático do JAR; override opcional com `fork.*` |

---

## ❓ Perguntas frequentes

<details>
<summary><b>📁 Onde vai a pasta libs?</b></summary>

Na pasta onde o GameServer <b>já carrega os JARs</b> — pode ser <code>libs</code> na raiz da pack ou <code>game/libs</code>, conforme o <code>.bat</code> da sua revisão. Informe esse caminho no campo <b>Libs</b> do instalador. Não crie uma pasta libs separada só com os JARs do mod.
</details>

<details>
<summary><b>🔒 Preciso do código-fonte?</b></summary>

Não. O instalador embute os arquivos no <code>.exe</code>. O bridge usa <code>-javaagent</code> e reflexão no JAR que você já possui.
</details>

<details>
<summary><b>🛠️ Preciso editar GameServer.java?</b></summary>

Não. O mod usa <code>-javaagent:l2voice-bridge.jar</code> — o instalador configura nos <code>.bat</code> de subida.
</details>

<details>
<summary><b>🎯 O Engine.dll é alterado?</b></summary>

Não. Inicie o jogo pelo <code>L2VoiceInject.exe</code> na pasta <code>system</code>.
</details>

<details>
<summary><b>⚙️ Preciso configurar classes World/Player?</b></summary>

Em geral não — o bridge detecta no JAR. Só em revisões muito customizadas, opcionalmente em <code>l2jalnvoice.properties</code>:

<pre>
l2jalnvoice.fork.world = pacote.model.World
l2jalnvoice.fork.player = pacote.model.actor.Player
</pre>
</details>

<details>
<summary><b>🌐 Teste local vs VPS</b></summary>

<ul>
<li><b>Local:</b> IP <code>127.0.0.1</code> no instalador + Memurai + voice-server na mesma máquina</li>
<li><b>VPS:</b> IP público do voice-server + portas 17666/17667 liberadas no firewall</li>
</ul>
</details>

---

## 📞 Repositório

| Canal | Link |
|-------|------|
| 🐙 GitHub | [ALN2025/ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe) |

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

*Distribuição pública: apenas o instalador.*

</div>
