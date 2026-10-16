# Studio QL — site vitrine

Site vitrine de **Studio QL**, l'activité freelance de **Quentin LUCAS** (ingénieur informatique) : création de sites internet sur-mesure pour particuliers et indépendants. Le site sert de vitrine : il doit **montrer le savoir-faire** (motion design, animations au scroll, effets interactifs) et **amener des demandes de devis**.

Réponds et écris le contenu du site **en français**.

## Stack et fichiers

- HTML/CSS/JS **vanilla**, sans framework, sans build, sans dépendance JS. Ne pas en ajouter sans demande explicite.
- `index.html` : tout le site (CSS dans `<style>`, JS dans `<script>` en fin de fichier).
- `mentions-legales.html` : mentions légales et RGPD, même style, autonome.
- Seule ressource externe : la police Inter via Google Fonts, chargée sans bloquer l'affichage.
- Hébergement : **GitHub Pages**, branche `main`, dossier racine. Pas encore de nom de domaine.

## Configuration

Le bloc `CONFIG`, en haut du `<script>` d'`index.html`, centralise `brand`, `email`, `prenom`, `nom`, `titre`, `initiales` et `photo`. Les éléments marqués `data-cfg="…"` sont remplis depuis ce bloc. Modifier ces valeurs là, pas en dur dans le HTML.

## Sections d'index.html (dans l'ordre)

1. **Navigation** : barre globale, bandeau « Nouveau », barre fixe flottante (`#lnav`) qui apparaît au scroll avec le lien actif.
2. **Hero** (`#top`) : sphère 3D en shader WebGL (raymarching) qui réagit à la souris. Le titre « Des sites qui se vivent. » apparaît mot par mot. Pastille « Sites sur-mesure · sur devis ».
3. **Ma promesse** (`#device`) : section épinglée. Les mots « Clair. », « Rapide. », « Mémorable. » apparaissent l'un après l'autre, avec un halo coloré.
4. **Manifeste** (`#manifesto`) : texte révélé mot par mot au scroll.
5. **Savoir-faire** (`#savoir-faire`) : grille de tuiles (60 images/s, 3D, responsive, performance, référencement, sur-mesure).
6. **Pourquoi un bon site** (`#impact`) : 3 chiffres sourcés (voir plus bas).
7. **Marquee** : bandeau défilant infini qui s'incline et accélère selon la vitesse de scroll.
8. **Démos** (`#demos`) : 6 effets interactifs (carte 3D, bouton magnétique, texte décodé, particules, projecteur, formes liquides).
9. **Process** (`#process`) : scroll horizontal épinglé en 4 étapes.
10. **À propos** (`#a-propos`) : Quentin LUCAS, ingénieur informatique. Portrait avec les initiales QL, ou une photo via `CONFIG.photo`.
11. **Contact** (`#contact`) : formulaire de demande de devis.
12. **Footer** : lien vers `mentions-legales.html`.

Une seule boucle `requestAnimationFrame` pilote tout : `scrollFx()` pour les sections liées au scroll, `demoTicks` pour les démos. Les éléments hors écran ne sont pas calculés (IntersectionObserver `vio`). Les éléments `.rv` apparaissent à l'entrée dans l'écran, et les `.count` sont des compteurs animés (attribut `data-dec` pour les décimales).

## Formulaire de contact

- Envoi via **FormSubmit** : action `https://formsubmit.co/` suivie de `CONFIG.email`, soit `quentinlcs@outlook.fr`. Champs cachés `_subject`, `_replyto` et `_next` (retour sur `#merci`, qui affiche le message de remerciement).
- Champ « Type de projet » : Je ne sais pas encore / Site une page / Site vitrine complet.
- La toute première soumission du site en ligne déclenche un email d'activation FormSubmit à valider.

## Design system (style Apple, sombre)

- Fond `#000`, panneaux `#1d1d1f`, texte `#f5f5f7`, texte secondaire `#86868b`, bordures fines `#333336`.
- Bleu `#0071e3` réservé aux boutons d'action, `#2997ff` pour les liens sur fond sombre. Jaune `#ffd500` uniquement pour la tuile 60 images/s.
- Typo : système Apple (SF Pro), Inter en repli. Titres en 600 avec un interlettrage négatif.
- Rayons : 28px pour les cartes et médias, 980px pour les boutons et les champs, 20px pour la navigation.
- Pas d'ombres portées. On sépare par contraste de surface et par des bordures de 1px.
- Toujours penser mobile (gouttière de 16px, aucun scroll horizontal) et respecter `prefers-reduced-motion`.

## Règles et décisions de Quentin

- **Aucun prix sur le site** : tout se fait sur devis via le contact. Pas de section Offres.
- **Pas de faux site démo** ni de maquette de site client. Les visuels restent **simples et épurés**, pas trop « tech ».
- Les textes sont à la première personne (« je »). Le nom affiché est « Quentin LUCAS ».
- **Chiffres uniquement sourcés et vérifiés**, avec lien vers la source. Ne jamais inventer de statistique. Chiffres actuels :
  - +8,4 % de conversion pour 0,1 s gagnée sur mobile — Deloitte et 55 pour Google, « Milliseconds Make Millions », 2020 ;
  - 53 % du trafic des sites vient de la recherche naturelle — BrightEdge, 2019 ;
  - 58 % des internautes préfèrent un contenu au design soigné — Adobe, « The State of Content », 2015.
  - Écartés car invérifiables : « 75 % jugent sur le design » (attribué à Stanford), « +200 % / +400 % de conversion » (attribué à Forrester).
- **Performance** : la note Lighthouse mobile est de 100/100 sans le shader. Le shader démarre après le chargement, avec une résolution réduite sur mobile et une qualité adaptative. Ne pas dégrader ces réglages.

## État d'avancement

Fait :
- site complet et responsive, testé sans erreur JS ni débordement horizontal ;
- formulaire branché sur FormSubmit ;
- section À propos ;
- section chiffres sourcés ;
- mentions légales avec RGPD ;
- optimisation de la performance ;
- marque renommée en « Studio QL ».

À faire :
- [ ] Compléter les champs `[À COMPLÉTER]` de `mentions-legales.html` : statut, SIRET, TVA, adresse, téléphone, téléphone de l'hébergeur.
- [ ] Valider l'email d'activation FormSubmit après la mise en ligne.
- [ ] Ajouter une vraie photo (`CONFIG.photo`).
- [ ] Acheter un domaine (ex. `studioql.fr`) et le configurer sur GitHub Pages : 4 enregistrements A `185.199.108.153` à `.111.153`, un CNAME `www` vers `<pseudo>.github.io`, puis cocher « Enforce HTTPS ».
- [ ] Mesurer la vraie performance une fois en ligne sur pagespeed.web.dev.

## Façon de travailler

- Faire des modifications ciblées. Ne pas réécrire tout le fichier ni renommer les ids ou les classes existants sans raison.
- Après chaque changement, vérifier dans le navigateur, sur ordinateur et en largeur mobile (390 px), et vérifier la console.
- Expliquer simplement ce qui a changé. Proposer un message de commit clair, en français.
