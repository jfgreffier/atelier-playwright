# Débugger
Voici un test Playwright buggé :
```ts
import { test, expect } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://playwright.dev/');

  const [page1] = await Promise.all([
    page.waitForEvent('popup'),
    page.locator('[aria-label="GitHub repository"]').click()
  ]);

  await page1.locator('text=mxschmitt').click();
  await expect(page1).toHaveURL('https://github.com/microsoft/playwright/commits?author=mxschmitt');
  await expect(page1.locator('text=woof')).toBeVisible();
});

```

Exécutez-le. Quelles conclusions ?  
Nous allons débugger ce test avec différents outils.
## Débugger avec Playwright Inspector
```bash
npx playwright test mytest --debug
```

Lancer un test avec cette option fait plusieurs choses :
- Un seul navigateur sera lancé
- En mode headed (avec interface graphique)
- Pas de timeout
- Un objet `playwright` est accessible dans la console

Mise en pratique
## Débugger avec VSCode
L'extension VSCode permet de débugger avec point d'arrêt et pas à pas.

Mise en pratique
## Trace Viewer
Playwright peut enregistrer des traces au moment de passer un test. On peut le spécifier dans la configuration de Playwright Test, ou le forcer en ligne de commande

playwright.config.ts
```ts
import { defineConfig } from '@playwright/test';
export default defineConfig({
  use: {
    trace: 'retain-on-failure',
  },
});
```

Ou en ligne de commande
```bash
npx playwright test --trace on
```

![Playwright Trace Viewer](https://user-images.githubusercontent.com/13063165/212869694-61368b16-f176-4083-bbc2-fc85b95131f0.png)
Le Trace Viewer de Playwright peut être utilisé en local via `npx playwright show-trace trace.zip` ou en ligne https://trace.playwright.dev

> ℹ️ **note**  
> Le Trace Viewer de Playwright est extrêmement utile pour débugger après coup, par exemple en analysant les traces de tests fait dans une Intégration Continue

[Exemple de Trace](https://trace.playwright.dev/?trace=https://demo.playwright.dev/reports/todomvc/data/cb0fa77ebd9487a5c899f3ae65a7ffdbac681182.zip)

---
Références  
<https://playwright.dev/docs/debug>  
[Debugging Playwright tests in VS Code](https://www.youtube.com/watch?v=tJF7UhA59Gc)  
<https://playwright.dev/docs/test-configuration#record-test-trace>  
