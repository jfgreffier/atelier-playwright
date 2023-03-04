# Introduction
![Bannière Playwright](https://repository-images.githubusercontent.com/221981891/8c5c6942-c91f-4df1-825f-4cf474056bd7)

## Qu'est-ce que Playwright ?
[Playwright](https://playwright.dev/) est une incroyable solution de test bout en bout multi navigateurs. Il offre une API unifiée qui permet de piloter les principaux navigateurs web : Chromium, Webkit et Firefox. Le projet a commencé en 2020, mais se base sur plusieurs principes de Puppeteer, le célèbre outil permettant d’automatiser Chrome headless (sans interface graphique). En effet, une partie de l’équipe a quitté Google pour créer une solution plus ambitieuse, supportant les familles de navigateur les plus populaires. Playwright permet non seulement d’automatiser des navigateurs, mais aussi facilite les tests end-to-end fiables pour le web moderne.

> **Playwright**  
> Une solution d’automatisation de navigateur  
> axée vers les tests end-to-end  
> qui déchire !

Playwright permet de faire de l'automatisation et du test de bout en bout (end-to-end). Playwright permet aussi de faire du test de composant (React, Vue, Svelte...) de façon isolée, mais nous ne le verrons pas pendant cet atelier.

## Prérequis de l'atelier
Il est préférable d'être à l'aise avec TypeScript ou JavaScript.

### Prérequis système
- Windows ou WSL (Windows Subsystem for Linux)
- macOS 11 (Big Sur) ou plus
- Selon votre distribution Linux, il se peut que vous ayez à installer des dépendances supplémentaires pour les navigateurs

> ℹ️ **note**  
> Seulement Debian 11, Ubuntu 20.04 et 22.04 sont supportées officiellement.

### Node.js LTS
Playwright a besoin de Node.js 14 ou plus. Je recommande d'utiliser la version LTS, installée via [nvm](https://github.com/nvm-sh/nvm) ou [NVM for Windows](https://github.com/coreybutler/nvm-windows).

### VS Code + Playwright Test for VS Code
- [Visual Studio Code](https://code.visualstudio.com/)
- L'extension officielle [Playwright Test for VSCode](https://marketplace.visualstudio.com/items?itemName=ms-playwright.playwright)

---
Références  
[Playwright : l’outil qui va révolutionner les tests end-to-end](https://medium.com/@jfgreffier/playwright-loutil-qui-va-r%C3%A9volutionner-les-tests-end-to-end-384ff7ebb22d)  
<https://playwright.dev/docs/troubleshooting>  
