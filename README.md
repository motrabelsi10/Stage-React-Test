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


## Explication 
Voyons comment Jest et RTL sont complémentaires dans cet exemple :

- Jest fournit la structure et les fonctionnalités de base pour écrire et exécuter des tests JavaScript. Il gère l'exécution des tests, fournit des assertions (comme expect()) pour vérifier les résultats, et génère des rapports de couverture de code.
- RTL (React Testing Library) est une bibliothèque qui se concentre sur la manière dont les utilisateurs interagissent avec les composants React. Elle fournit des utilitaires (comme render() et screen.getByText()) pour faciliter les tests basés sur le comportement réel de l'interface utilisateur.
- Dans notre exemple, nous utilisons Jest pour exécuter le test et RTL pour rendre le composant, rechercher l'élément de bouton et effectuer des assertions sur celui-ci. Jest nous donne l'infrastructure de test et les outils de base, tandis que RTL nous aide à adopter une approche centrée sur l'utilisateur pour tester notre composant React.

