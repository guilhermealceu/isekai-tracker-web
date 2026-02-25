# Isekai;Tracker

O **Isekai;Tracker** é uma aplicação PWA (Progressive Web App) moderna para rastreamento automático de animes, projetada para funcionar em conjunto com uma extensão de navegador que captura o progresso de animes assistidos em sites como a Crunchyroll.

## 🚀 Como Funciona

O sistema é composto por três partes principais:

1.  **Aplicação Web (PWA):** A interface do usuário onde você visualiza seus animes, estatísticas e gerencia sua lista. 

2. **Acesse:** https://isekai-tracker.discloud.app/

3.  **Servidor Local (WebSocket):** Um servidor Node.js que roda na sua máquina (porta 3005) e serve como ponte entre a extensão do navegador e a aplicação web.
4.  **Extensão do Navegador:** Captura o título, episódio e tempo de reprodução do anime que você está assistindo e envia para o servidor local.
   
5.  **Baixar aqui:** https://github.com/guilhermealceu/isekai-tracker-web/releases/download/Extension_1.1.0/isekai-extension-2.0.zip

### Fluxo de Dados

1.  Você assiste a um anime na Crunchyroll.
2.  A extensão detecta a atividade e envia os dados (título, episódio, tempo) para `ws://localhost:3005`.
3.  O servidor local recebe esses dados e os retransmite para a aplicação web (se estiver aberta).
4.  A aplicação web atualiza sua lista de animes e o player ativo em tempo real.

## 🛠️ Tecnologias Utilizadas

-   **Frontend:** React, TypeScript, Vite, Tailwind CSS.
-   **PWA:** Vite PWA Plugin (para instalação e funcionamento offline).
-   **Backend/Servidor Local:** Node.js, Express, WebSocket (`ws`).
-   **API Externa:** Jikan API (para buscar capas e metadados dos animes).
-   **Ícones:** Lucide React.

## ⚙️ Configuração e Instalação

### 1. Aplicação Web

Para rodar a aplicação web localmente:

```bash
# Instalar dependências
npm install

# Iniciar servidor de desenvolvimento (Frontend + Backend)
npm run dev
```

A aplicação estará disponível em `http://localhost:3000` (ou a porta definida pelo sistema).

### 2. Servidor WebSocket (Importante para a Extensão)

A aplicação web já inicia o servidor WebSocket necessário na porta 3005 quando você roda `npm run dev` (através do arquivo `server.ts`).

Certifique-se de que a porta **3005** esteja livre. A extensão do navegador deve estar configurada para conectar em `ws://localhost:3005`.

### 3. PWA (Instalação no Desktop/Mobile)

1.  Acesse a aplicação pelo navegador (Chrome/Edge recomendados).
2.  Clique no ícone de instalação na barra de endereço ou vá em Configurações > Instalar App.
3.  O app funcionará como um aplicativo nativo.

## 🎮 Integração com Discord (Rich Presence)

Para que o Discord mostre o que você está assistindo (Rich Presence), você precisará de um script adicional ou uma extensão que leia os dados do nosso servidor local (`http://localhost:3005`) e atualize o status do Discord.

Atualmente, o foco do projeto é o rastreamento web, mas como os dados já estão no servidor local, criar um script de integração com Discord RPC é simples.

## 📱 Mobile

Como é um PWA, você pode acessar o site pelo seu celular (se estiver na mesma rede Wi-Fi que o PC rodando o servidor) e instalar o app.

Para que o celular receba os dados do PC (onde você está assistindo o anime), o celular deve conseguir acessar o IP do seu PC na porta 3005.

## 🐛 Não Comercial

---

Desenvolvido com 💜 para a comunidade otaku by RUNE
