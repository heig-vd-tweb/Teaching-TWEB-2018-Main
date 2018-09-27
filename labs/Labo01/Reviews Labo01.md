# TWEB - Review Assignement 1
## HTML
- Mettre un titre aux pages (`<title>`).
- `<script>` à la fin du body (afin de s'assurer que le DOM soit pleinement chargé avant de lancer les scripts)
- `</br>` => `<br />`
- flexbox à la place des <table>
- On ferme les balise seules (`<img ... />`)
- alt sur les images
- Balises titres jusqu'à max `<h6>` y compris

## CSS
- On évite les pourcentages pour les marges (marges statiques), pareil pour les top/left à l'intérieur d'un autre élément (sauf pour centrer verticalement)
- Utiliser des em pour les tailles de police
- Animation css qui travaille sur le width / height (ça demande au navigateur de recalculer la position des éléments qui sont touchés par l'animation à chaque frame) => utiliser les propriétés sécurisées (https://www.html5rocks.com/en/tutorials/speed/high-performance-animations/) => repenser l'animation en la faisant utiliser uniquement des propriétés comme transform, translate, etc. (https://aerotwist.com/blog/flip-your-animations/) ; sur Chrome => maj-cmd-p => animations

## JS
- Utiliser `let` et `const` à la place de `var`.
- Utiliser `===` à la place de `==`.
- Concat : \`test-${foobar}\` au lieu de `'test-' + foobar`
- Ajout ou suppression de classes au lieu de modifier tous les attributs un à un en JS (JQuery => `addClass` / `removeClass` / `toggleClass` ; JS => `element.classList.remove('mystyle')`)

## Bonnes pratiques
- Application CLIENT, donc pas de packages npm (et on ne push jamais le dossier node_modules sur GitHub (car très volumineux certaines fois, et optionnel))
- Structurer le projet et ses assets (dossiers images, JS, CSS, etc.)
- Nettoyer les tests `console.log`
- Rester consistant (espaces ou non après les : en css, tabulations, échelles, etc.)
- Créer une fonction englobante pour isoler le scope et exécuter le JS losrque la page est pleinement chargée
	```
	function () {
	    console.log('loaded!');
	}();
	```

## Divers
- Adresse mail HEIG ou explicite (nom-prénom) sur le Google Form