# Spécification de Cap Web

1. Quand on envoie un message vide ou fait seulement d'espaces, Cap Web le refuse et affiche une erreur.
   Vérifié par : test « refuse le vide et les espaces seuls ».

2. Quand on envoie un message plus long que notre limite (espaces autour non comptés), Cap Web le refuse et l'erreur cite notre limite.
   Vérifié par : tests « accepte <notre limite> caractères et refuse <notre limite + 1> » et « mesure la longueur après avoir retiré les espaces ».

3. Quand on écrit « salut », « SALUT » ou « bonjour », même avec des espaces autour, Cap Web donne la même réponse d'accueil.
   Vérifié par : tests « ignore la casse et les espaces autour » et « donne la même réponse à « bonjour » et à « salut » ».

4. Quand on écrit une phrase qu'il ne connaît pas, Cap Web donne une réponse à part, qui renvoie vers « aide ».
   Vérifié par : test « répond à une phrase inconnue par un repli distinct ».

5. Quand on envoie `<b>gras</b>`, Cap Web l'affiche tel quel, chevrons compris, sans le mettre en gras.
   Vérifié par : test « view.js affiche du texte et ne décide pas des réponses », et un essai de 30 secondes dans la page.
