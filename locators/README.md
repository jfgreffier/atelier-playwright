# Des locators robustes et efficaces
Un **Locator** est un objet qui permet de localiser un élément dans une page web. Il est utilisé pour identifier et accéder à des éléments tels que des boutons, des liens, des formulaires et des images dans le code de test. Nous allons voir comment créer des Locators avec différentes stratégies.

## Locators et sélecteurs
On peut créer un Locator avec un sélecteur, comme les sélecteurs XPath ou CSS par exemple.

```ts
await page.locator('data-test-id=directions').click();
//         ⮤ Locator ⮤ Selector              ⮤ méthode
```

Pour mettre en pratique, nous allons tester cette application de liste à faire <https://demo.playwright.dev/todomvc/>

Pour vous aider :
- L'inspecteur de votre navigateur va vous aider à trouver le Selector
- <https://playwright.dev/docs/other-locators>
- <https://playwright.dev/docs/api/class-locator>

### XPath
```ts
import { test } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://demo.playwright.dev/todomvc/');

  // TODO Créer un Locator avec un sélecteur XPath ciblant le champ 'What needs to be done ?'
  // Remplir le champ avec 'Salade'
  // Appuyer sur entrée
});

```

### CSS
```ts
import { test } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://demo.playwright.dev/todomvc/');

  // ..
  // TODO Créer un Locator avec un sélecteur CSS ciblant le champ 'What needs to be done ?'
  // Remplir le champ avec 'Tomate'
  // Appuyer sur entrée
});

```

### Texte
```ts
import { test } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://demo.playwright.dev/todomvc/');

  // ..
  // TODO Créer un Locator avec un sélecteur texte ciblant le bouton 'Completed'
  // Le mettre en surlignement (highlight)
});

```

Bonus : essayez de sélectionner et de remplir le champ 'What needs to be done ?'

### Conclusion
Quelles différences entre ces sélecteurs ?

## Testing Library
Playwright offre en plus une syntaxe inspirée de Testing Library. Ca n'est pas un hasard puisque c'est le créateur de [Testing Library](https://testing-library.com/), [Kent C. Dodds](https://kentcdodds.com/), est ambassadeur Playwright.

- `page.getByRole()` to locate by explicit and implicit accessibility attributes.
- `page.getByText()` to locate by text content.
- `page.getByLabel()` to locate a form control by associated label's text.
- `page.getByPlaceholder()` to locate an input by placeholder.
- `page.getByAltText()` to locate an element, usually image, by its text alternative.
- `page.getByTitle()` to locate an element by its title attribute.
- `page.getByTestId()` to locate an element based on its `data-testid` attribute (other attributes can be configured).

```js
await page.getByLabel('User Name').fill('John');

await page.getByLabel('Password').fill('secret-password');

await page.getByRole('button', { name: 'Sign in' }).click();

await expect(page.getByText('Welcome, John!')).toBeVisible();
```

Documentation complète <https://playwright.dev/docs/locators>  

Mise en pratique
```ts
import { test } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://demo.playwright.dev/todomvc/');

  // ..
  // TODO Créer un Locator ciblant le champ 'What needs to be done ?'
  // Remplir le champ avec 'Tomate'
  // Appuyer sur entrée
});

```

### Conclusion
Quelles différences avec les sélecteurs ?

---
Solution
```ts
import { test } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://demo.playwright.dev/todomvc/');
  
  const locatorXPath = page.locator('xpath=/html/body/section/div/header/input');
  await locatorXPath.fill('Salade');
  await locatorXPath.press('Enter');

  const locatorCSS = page.locator('css=.new-todo');
  await locatorCSS.fill('Tomate');
  await locatorCSS.press('Enter');

  await page.locator('text=Completed').highlight();

  const locatorTestingLibrary = page.getByPlaceholder('What needs');
  await locatorTestingLibrary.fill('oignons');
  await locatorTestingLibrary.press('Enter');
});

```

---
Références  
<https://playwright.dev/docs/other-locators>  
<https://playwright.dev/docs/locators>  
<https://playwright.dev/docs/best-practices>  
