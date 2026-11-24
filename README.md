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

## v2 (24/11/2026) — anatomie détaillée
- 41 zones précises (structure réelle + syndrome classique du coureur : fémoro-patellaire, tendon rotulien, bandelette ilio-tibiale,
  patte d'oie, ménisque, poplité, talo-fibulaire, fibulaires, tibial postérieur, aponévrose, Morton, métatarses, ongle noir, ampoules,
  jumeaux, soléaire, crampes, Achille corps/insertion, périostite, tibial antérieur, quadriceps, ischios, adducteurs, DOMS,
  moyen fessier, piriforme, psoas/aine, trochanter, lombaires, sacro-iliaque, rhomboïdes, coiffe, épicondyle, De Quervain,
  trapèzes, point de côté, frottements, ventre, tête, partout, nulle part, cœur).
- Chaque réponse : carte « Diagnostic (très sérieux) » + 1 exercice + 1 vin.
- Région seule (« genou », « pied », « dos »…) → AntoninGPT demande de préciser avec des puces (`REGIONS`, `subChips`).
- Contexte repris dans la réponse (`CONTEXT`) : côté, moment (descente, montée, matin, nuit, escaliers), sensation (brûle, tire,
  gonfle, « crac ») ; gonflement / « crac » / douleur la nuit → renvoi vers le vrai Antonin.
- Clés : chaîne = expression, tableau = tous les mots présents ; la plus spécifique gagne ; une zone précise de la même région
  l'emporte sur la question de précision. Test : script Node qui vérifie que chaque puce retombe sur sa zone + ~35 phrases réelles.

## v2.1 (24/11/2026) — demande de Charles
- Plus aucun vrai diagnostic : carte « L'avis d'AntoninGPT (zéro diplôme) » = surnom drôle + « suspects habituels », jamais d'affirmation.
- Renvoi systématique vers le vrai Antonin dans chaque réponse (carte en pointillés), en plus des signaux d'alerte (gonflement, « crac », nuit).
- 37 vins (12 avant), dont le parcours CCC : Blanc de Morgex et de La Salle, Torrette, Fumin, Petite Arvine, Fendant, Cornalin, Savoie ; + options sans alcool.
