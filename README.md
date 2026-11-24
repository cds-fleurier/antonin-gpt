# AntoninGPT 🍷

> Le kiné de la team 0 to 100 prend quelques jours de repos.
> AntoninGPT assure l'intérim : vous dites où vous avez mal, il prescrit **1 exercice de kiné** et **1 verre de vin** pour aller avec.

🔗 https://cds-fleurier.github.io/antonin-gpt/

## Fonctionnement

- Page statique, zéro backend, zéro IA : la « base de connaissances » est en dur dans `index.html`
  (15 zones, ~30 exercices, 12 vins, tirage aléatoire).
- Mots-clés reconnus avec ou sans accents ; si rien ne matche, AntoninGPT propose des zones à cliquer.
- Look 0 to 100 (mêmes tokens que le calendrier et le player de séance).

## Accessibilité / vie privée

- `noindex, nofollow` (blague interne, pas pour Google).
- Champ de saisie en 16 px (pas de zoom automatique sur iPhone) avec un `<label>` masqué visuellement.
- Zone de chat `role="log" aria-live="polite"` : les réponses sont lues par VoiceOver.
- `--text-muted` #7a8798 (contraste lisible).

## Déploiement

`git push origin main` → GitHub Pages (branche `main`, racine).

## Avertissement

AntoninGPT n'est pas kiné. Antonin, lui, oui. Et il revient bientôt.

## Journal

- 2026-11-24 : noindex, champ 16 px + label, chat `role=log`, contraste `--text-muted`.
- 2026-09-21 : barre d'onglets partagée du hub.
- 2026-09-18 : v1.0.
