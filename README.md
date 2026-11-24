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

## v2.2 (24/11/2026)
- Zone intime prévue (vulve, « chatte », testicules, périnée…) : AntoninGPT rougit, blague vétérinaire si « chatte/minou », seul conseil utile = anti-frottement, renvoi médecin / gynéco / urologue (pas Antonin). Pas de vulgarité. « queue » et « lèvres » seuls exclus (queue de cheval = nerfs du bas du dos ; lèvres = bouche).

## v2.3 (24/11/2026) — parties communes du corps
- Remontée de Charles : « clavicule » non reconnue. Test de couverture sur 117 parties du corps : 55 inconnues → 0.
- Nouvelles zones : clavicule, haut du bras (biceps/triceps), abdos, côtes/sternum/pectoraux/seins, mâchoire/dents, yeux,
  gorge/nez/oreilles, peau (soleil, ronces), souffle (essoufflement normal en montée) ; région « visage » qui demande de préciser.
  Clés ajoutées : doigts, paume, colonne, vertèbres, dorsaux, deltoïde, fémur, péroné, front, tempe, nombril, vessie, tendon…
- **Zone sérieuse** (`serious: true`) : poitrine, palpitations, cœur qui s'emballe, malaise, vertiges, difficulté à respirer →
  pas d'exercice, pas de vin, pas de blague : médecin sans attendre, 15 / 112 si intense. « Mal au cœur » = nausée → ventre.
- Bug corrigé : « œ » n'était pas normalisé (« cœur » jamais reconnu).
- Test : `agpt-body.cjs` (117 parties) + test des puces + phrases réelles.

## v2.4 (24/11/2026)
- Zone intime : abréviations et argot (clito/clit, teub, zob, burnes, valseuses…), zone anale, règles, organes génitaux → médecin. Argot seins → côtes/brassière ; « mal au cul / au derrière » → fesses. Les tests (117 parties + puces) passent toujours.
