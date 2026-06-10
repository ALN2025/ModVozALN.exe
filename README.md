<div align="center">

# 🎙️ ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.9.6-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
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
<summary><b>🌐 Teste local vs VPS</b></summary>

<ul>
<li><b>Local:</b> IP <code>127.0.0.1</code> no instalador + Memurai + voice-server na mesma máquina</li>
<li><b>VPS:</b> IP público do voice-server + portas 17666/17667 liberadas no firewall</li>
</ul>
</details>

---

## 📞 Suporte

| Canal | Link |
|-------|------|
| 🐙 GitHub | [ALN2025/ModVozALN.exe](https://github.com/ALN2025/ModVozALN.exe) |

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

*Distribuição pública: apenas o instalador. Código-fonte e assets de desenvolvimento permanecem em repositório privado.*

</div>
