# Installation et premier test
## Vérifier les prérequis
```bash
node -v
npx playwright install-deps
code -v
```

## Init en ligne de commande
```bash
mkdir atelier-playwright
cd atelier-playwright
```

Puis on suit littéralement la doc <https://playwright.dev/docs/intro>

Quelques options de Playwright Test
```bash
npx playwright test --help
npx playwright test --headed
npx playwright test --project=chromium
```


> ℹ️ **note**  
> Faire un projet en TypeScript ou JavaScript ? Ca ne change pas grand-chose, sauf le style des imports (require vs import -> CommonJS Modules vs ES Modules)

Il est aussi possible d'initialiser un projet Playwright via l'extension VSCode.

---
Références  
<https://playwright.dev/docs/intro>  
<https://playwright.dev/docs/getting-started-vscode>  
