# Tests automatisés en React avec Jest et RTL

Ce projet utilise Jest et RTL pour les tests automatisés de l'application React.

## Qu'est-ce que Jest ?

Jest est un framework de test puissant et facile à utiliser pour JavaScript. Il est spécialement conçu pour les projets React et fournit une suite d'outils pour écrire, exécuter et analyser les tests.

Principales fonctionnalités de Jest :
- Syntaxe simple et expressive pour écrire des tests.
- Prise en charge des tests unitaires, des tests de snapshot et des tests d'intégration.
- Génération de rapports de couverture de code.
- Possibilité de mocker des modules, des fonctions et des dépendances externes.

## Qu'est-ce que RTL (React Testing Library) ?

RTL (React Testing Library) est une bibliothèque de tests pour React qui encourage les bonnes pratiques en matière de tests. Elle se concentre sur la manière dont les utilisateurs interagissent avec l'application et facilite les tests basés sur le comportement réel de l'interface utilisateur.

Principales fonctionnalités de RTL :
- Approche centrée sur l'utilisateur pour tester les composants React.
- Prise en charge de la recherche de texte, de l'interaction avec les éléments, de la navigation et de l'accessibilité.
- Encouragement à tester le rendu et le comportement réels des composants plutôt que les détails d'implémentation.
- Intégration transparente avec Jest pour une configuration et une exécution faciles des tests.

## Différence entre Jest et RTL

Jest est un framework de test qui fournit une infrastructure complète pour écrire et exécuter des tests JavaScript, tandis que RTL est une bibliothèque de tests spécifique à React qui se concentre sur la manière dont les utilisateurs interagissent avec les composants.

En résumé, Jest est responsable de l'exécution des tests et fournit des fonctionnalités avancées telles que la couverture de code et le mocking, tandis que RTL fournit des outils pour tester les composants React en se concentrant sur leur rendu et leur interaction utilisateur.

## Comment Jest et RTL sont complémentaires

Jest et RTL sont complémentaires dans l'écosystème de test de React. Jest offre une base solide pour l'exécution des tests et fournit des fonctionnalités avancées pour les tests JavaScript, tandis que RTL s'intègre à Jest pour offrir une approche centrée sur l'utilisateur pour tester les composants React.

En utilisant Jest avec RTL, vous pouvez bénéficier de l'infrastructure de test puissante de Jest tout en adoptant les bonnes pratiques de test recommandées par RTL. Cela vous permet de créer des tests complets et robustes pour vos applications React, en vous assurant que vos composants fonctionnent correctement du point de vue de l'utilisateur.


## Exemple 

Voici un exemple de test utilisant Jest et RTL pour le composant `Button` :

```jsx
import { render, screen } from '@testing-library/react';
import Button from './Button';

test('affiche le texte correct', () => {
  render(<Button text="Cliquez-moi" />);
  const buttonElement = screen.getByText(/Cliquez-moi/i);
  expect(buttonElement).toBeInTheDocument();
});

```
## Explication 
Voyons comment Jest et RTL sont complémentaires dans cet exemple :

- Jest fournit la structure et les fonctionnalités de base pour écrire et exécuter des tests JavaScript. Il gère l'exécution des tests, fournit des assertions (comme expect()) pour vérifier les résultats, et génère des rapports de couverture de code.
- RTL (React Testing Library) est une bibliothèque qui se concentre sur la manière dont les utilisateurs interagissent avec les composants React. Elle fournit des utilitaires (comme render() et screen.getByText()) pour faciliter les tests basés sur le comportement réel de l'interface utilisateur.
- Dans notre exemple, nous utilisons Jest pour exécuter le test et RTL pour rendre le composant, rechercher l'élément de bouton et effectuer des assertions sur celui-ci. Jest nous donne l'infrastructure de test et les outils de base, tandis que RTL nous aide à adopter une approche centrée sur l'utilisateur pour tester notre composant React.

## Utilisation 

### Avec les nombres 
```jsx
test('deux plus deux', () => {
  const value = 2 + 2;
  expect(value).toBeGreaterThan(3);
  expect(value).toBeGreaterThanOrEqual(3.5);
  expect(value).toBeLessThan(5);
  expect(value).toBeLessThanOrEqual(4.5);
  expect(value).toBe(4);
  expect(value).toEqual(4);
});
```

### Avec les chaines de caracteres 
```jsx
test('Il ya bon dans bonjour', () => {
  expect('bonjour').toMatch(/bon/); // ajouter expect ().not.toMatch() dans le cas contraire 
});


const players = ["messi","msakni","neymar"];

test('test tab', () => {
  expect(players).toContain("messi");
  expect(players).not.toContain("mbappé");
});
```

### Exemple d'execution 
```jsx
PASS  src/App.test.js // le test est validé 
  √ deux plus deux (7 ms) // le nom de la fonction test 
  √ Il ya bon dans bonjour (1 ms)
  √ test tab (1 ms)

Test Suites: 1 passed, 1 total
Tests:       3 passed, 3 total
Snapshots:   0 total
Time:        5.872 s
Ran all test suites related to changed files.
```

### Syntaxe 
```jsx
import { render, screen } from '@testing-library/react'; // importation des render et screen 

test('should render input and button', () => {
  render(<App />); // rendre l'interface a tester ( RTL ) 
  
  const input = screen.getByLabelText('Text Field'); // getter l'element a tester 
  expect(input).toBeInTheDocument(); // tester cette element se trouve dans cette fenetre ou non ! 
  
  const btn = screen.getByTestId('btn-ajouter');
  expect(btn).toBeInTheDocument();
});

```

### Comment recuperer les elements 
```jsx
// code dans App.js
    <p>tester en react</p>
    <input type="text" data-testid="my-input" />
    <button data-testid="my-button">Cliquez-moi</button> // ici on peut mettre un id pour un element. 
// code dans App.test.js
test("get by",() => {
  render(<App />);
  const element = screen.getByText("tester en react"); // on recupere le texte qui se trouve dans la balise <p>
  const btn = screen.getByRole("button"); // getter un bouton
  const input = screen.getByRole("textbox"); // getter un input 
  expect(element).toBeInTheDocument();

  const buttonElement = screen.getByTestId('my-button'); // on recupere l'element by son id 
});
```

### Exemple de totoList - FireEvent
```jsx
  const inputElement = screen.getByTestId('todo-input');
  const addButtonElement = screen.getByTestId('add-button');
  const todoListElement = screen.getByTestId('todo-list');

  fireEvent.change(inputElement, { target: { value: 'Nouvelle tâche' } }); // methode .change prend deux parametre , le premier l'elemenet , le deuxieme est pour la valeur 
  fireEvent.submit(addButtonElement); // L'action du button 

  expect(screen.getByText('Nouvelle tâche')).toBeInTheDocument();
  expect(inputElement.value).toBe('');
```

### Tester le code asynchone 

```jsx
  test('renders a count of 1 after clicking the increment button', async () => {
    user.setup()
    render(<Counter />)
    const incrementButton = screen.getByRole('button', { name: 'Increment' })
    await user.click(incrementButton)
    const countElement = screen.getByRole('heading')
    expect(countElement).toHaveTextContent('1')
  })

  test('renders a count of 2 after clicking the increment button twice', async () => {
    user.setup()
    render(<Counter />)
    const incrementButton = screen.getByRole('button', { name: 'Increment' })
    await user.click(incrementButton)
    await user.click(incrementButton)
    const countElement = screen.getByRole('heading')
    expect(countElement).toHaveTextContent('2')
  })

```
#### Explication 
Dans ce code de test, les mots-clés async et await sont utilisés pour gérer les opérations asynchrones de manière synchrone et séquentielle.
Dans les tests donnés, le mot-clé async est utilisé pour déclarer les fonctions de test comme des fonctions asynchrones.

Le mot-clé await est utilisé pour attendre la fin des opérations asynchrones. Dans ce cas, il est utilisé avec la fonction user.click() pour attendre que le bouton soit cliqué et que l'action correspondante soit terminée avant de passer à l'instruction suivante.

Cela garantit que les tests se déroulent de manière séquentielle, en attendant la fin des opérations asynchrones avant de vérifier les résultats attendus à l'aide des assertions, comme expect(countElement).toHaveTextContent('1') et expect(countElement).toHaveTextContent('2').









