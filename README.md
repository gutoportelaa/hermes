# 🪽 Hermes: Assistente Pessoal Local em Android Reproveitado

![Licença](https://img.shields.io/badge/License-MIT-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10+-yellow.svg)
![Plataforma](https://img.shields.io/badge/Platform-Termux%20%7C%20Android-green.svg)

> Transformando um smartphone antigo (Samsung Galaxy M52) em um servidor de Inteligência Artificial 100% local, autônomo e focado em privacidade.

## 📖 Sobre o Projeto

O **PocketAgent** é uma prova de conceito e um laboratório pessoal de IA. O objetivo é contornar as limitações de hardware de um smartphone intermediário (Snapdragon 778G, 6GB RAM) para rodar Pequenos Modelos de Linguagem (SLMs) localmente, integrando-os a ferramentas do dia a dia.

Para economizar recursos e evitar _Out of Memory (OOM)_, este projeto **abandona frameworks pesados como LangChain/LangGraph**, utilizando uma arquitetura modular minimalista em Python puro e `llama.cpp`.

### ✨ Funcionalidades (Versão 1.0)
- **🧠 Inferência 100% Local:** Sem APIs de terceiros para processamento de texto, garantindo privacidade total usando modelos quantizados (GGUF).
- **💬 Interface via Telegram:** Comunicação fluida com o assistente usando a API oficial do Telegram.
- **📅 Automação Determinística:** Integração direta com o Google Calendar para agendamento de eventos sem risco de "alucinações" da IA.
- **🔋 Otimizado para Mobile:** Rodando sob um ambiente Proot/Ubuntu via Termux, projetado para baixo consumo de bateria e RAM.

---

## 🏗️ Arquitetura do Sistema

O sistema é dividido em três módulos principais que operam em paralelo:

1. **O Cérebro (`llama.cpp`):** Servidor HTTP leve rodando o modelo LLM.
2. **O Roteador (`bot_telegram.py`):** Recebe as mensagens, decide se é um comando estrito ou conversação, e faz o roteamento.
3. **As Ferramentas (`google_calendar.py`):** Scripts de execução determinística para APIs externas.

---

## 🛠️ Requisitos de Hardware e Software

- **Dispositivo:** Smartphone Android (Testado em Samsung M52 5G / Snapdragon 778G). Mínimo de 6GB de RAM recomendados.
- **Sistema Base:** [Termux](https://f-droid.org/packages/com.termux/) (Versão F-Droid, **não** usar a da Play Store) com permissões de bateria irrestritas.
- **Ambiente Linux:** `proot-distro` rodando Ubuntu ou Debian.
- **Modelo Recomendado:** Phi-3-Mini (4-bit) ou Qwen-1.5-1.8B (GGUF).

---

## 🚀 Como Instalar e Rodar

### 1. Preparação do Dispositivo (Termux)
Certifique-se de que o Termux tem acesso ao armazenamento e instale o ambiente base:
```bash
pkg update && pkg upgrade
pkg install proot-distro git
proot-distro install ubuntu
proot-distro login ubuntu
