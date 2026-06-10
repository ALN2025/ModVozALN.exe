<div align="center">

# 🎙️ ModVozALN — Instalador L2Voice

**Mod de voz por proximidade para servidores Lineage 2**

[![Versão](https://img.shields.io/badge/versão-1.8.0-7c3aed?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe)
[![Plataforma](https://img.shields.io/badge/plataforma-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/ALN2025/ModVozALN.exe)
[![Download](https://img.shields.io/badge/⬇️_download-ModVozALN.exe-ec4899?style=for-the-badge)](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe)
[![Dev](https://img.shields.io/badge/Dev-ALN-a855f7?style=for-the-badge)](https://github.com/ALN2025)

**Mod De Voz Dev ⩿ A.L.N/⪀**

*Instale o mod completo em poucos cliques — sem editar Java, sem mexer no Engine.dll*

</div>

---

## 📥 Download

| Arquivo | Descrição |
|---------|-----------|
| [**ModVozALN.exe**](https://github.com/ALN2025/ModVozALN.exe/raw/main/ModVozALN.exe) | Instalador único (~31 MB) — **tudo já embutido** |

> ⚠️ Baixe **somente** o executável. Não é necessário pasta `pack/`, código-fonte ou JARs separados.

---

## ✨ O que o instalador faz

| Componente | Instala automaticamente |
|------------|-------------------------|
| 🖥️ **GameServer** | `l2voice-bridge.jar`, `jedis`, `l2jalnvoice.properties`, HTML, `INICIAR-GS-COM-VOZ.bat` |
| 🔧 **GameServer** | Injeta `-javaagent` nos `.bat` existentes — **sem editar `.java`** |
| 🎮 **Cliente L2** | `l2voice.dll`, `voice.ini`, `L2VoiceInject.exe` |
| 📡 **Voice-server** | `L2VoiceServer.exe`, `voice-server.exe`, scripts de inicialização |

---

## 🚀 Como instalar

### 1️⃣ Execute o instalador

1. Baixe e abra **`ModVozALN.exe`**
2. Selecione as pastas:
   - **GameServer** → pasta `game` ou `gameserver` da sua pack
   - **Cliente** → pasta `system` do L2
   - **Voice** → pasta onde rodar o voice-server (ex.: `C:\L2Voice`)
3. Informe o **IP do voice-server** (`127.0.0.1` local · IP público na VPS)
4. Clique em **INSTALAR**

### 2️⃣ Suba os serviços (nessa ordem)

```
Memurai/Redis  →  Login Server  →  L2VoiceServer.exe  →  GameServer
```

Ou use **`INICIAR-SERVIDOR-COM-VOZ.bat`** na raiz da pack (criado pelo instalador).

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
| ☕ Java | JDK 17+ no GameServer |
| 🗄️ Redis | Memurai ou Redis em `127.0.0.1:6379` |
| 🔥 Firewall | UDP **17666** + TCP **17667** (jogadores remotos) |

---

## 🧩 Packs suportadas (auto-detect)

| Pack | Suporte |
|------|---------|
| ✅ L2jMega / L2JALN | Nativo |
| ✅ aCis / RusaCis | Nativo |
| ✅ L2jFrozen | Nativo |
| ✅ L2JServer | Nativo |
| ✅ L2Emu / L2Off / EmuDev | Nativo |
| ✅ L2jMobius | Nativo |
| ⚙️ Pack personalizada | Configure `fork.*` em `l2jalnvoice.properties` |

---

## ❓ Perguntas frequentes

<details>
<summary><b>🔒 Preciso do código-fonte ou da pasta pack?</b></summary>

Não. O instalador v1.7.0 traz **tudo embutido** no `.exe`. Basta baixar, executar e instalar.
</details>

<details>
<summary><b>🛠️ Preciso editar GameServer.java?</b></summary>

Não. O bridge usa <code>-javaagent</code> e é configurado automaticamente pelo instalador.
</details>

<details>
<summary><b>🎯 O Engine.dll é alterado?</b></summary>

Não. O cliente inicia pelo <code>L2VoiceInject.exe</code>, que carrega a DLL de voz sem patch no engine.
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
| 🌐 ScriptClean | [scriptclean.com.br](https://scriptclean.com.br) |

---

<div align="center">

**© 2026 Dev ALN — ModVozALN / L2Voice**

*Distribuição pública: apenas o instalador. Código-fonte e assets de desenvolvimento permanecem em repositório privado.*

</div>
