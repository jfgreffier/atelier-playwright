# Assertions
Nous avons généré du code avec Codegen, des Locators robustes, mais nous n'avons rien testé ! Pour vérifier que les résultats obtenus correspondent à ce que l'on attend, on utilise les **assertions**.
## Assertions génériques
<https://playwright.dev/docs/api/class-genericassertions>  
En vous servant de la doc, faites un test qui vérifie que :
1. `true` est vrai
2. `0.1 + 0.2` est égal à `0.3`
3. `"$ 128"` correspond au format de prix attendu ($, puis espace, puis le prix) et le prix est un nombre, supérieur à 100
## Web-first assertions
Les assertions orientées web (Web-first assertions) sont spécifiquement faite pour tester le DOM. Elles sont conçues avec des notions de HTML et CSS en tête. De plus, il y a un mécanisme d'auto-retry.

Par exemple
```ts
expect(locator).toBeChecked()
expect(locator).toBeDisabled()
expect(locator).toBeEditable()
expect(locator).toBeEmpty()
expect(locator).toBeEnabled()
expect(locator).toBeFocused()
expect(locator).toBeHidden()
expect(locator).toBeVisible()
expect(locator).toContainText(text)
expect(locator).toHaveAttribute(name)
expect(locator).toHaveClass(expected)
expect(locator).toHaveCount(count)
expect(locator).toHaveCSS(name, value)
expect(locator).toHaveId(id)
expect(locator).toHaveText(expected)
expect(locator).toHaveValue(value)
```

Reprenons le test du chapitre [Des locators robustes et efficaces](locators/README.md#Solution).  
Vérifions que :
1. Salade, Tomate, Oignons ont été ajoutés
2. Il reste 3 items
3. Quand on check Tomate, il reste 2 items
4. Quand on clique sur 'completed', il y a 'Tomate' mais ni Salade, ni Oignons

> ℹ️ **note**  
> Pour éviter les erreurs et aller plus vite, je conseille de configurer **ESLint Plugin Playwright**
> <https://www.npmjs.com/package/eslint-plugin-playwright>

---
Références  
<https://playwright.dev/docs/api/class-genericassertions>  
<https://playwright.dev/docs/test-assertions>  
