# Démo client — Laverie du Floréal (Agen)

Ce workspace est dédié à la création d'une **démo de site vitrine** pour un prospect réel.
Objectif : impressionner pour signer la création (400-700 €) + maintenance mensuelle (30 ou 60 €).

Base de départ : structure réutilisée du site Laverie du Cygne, mais identité visuelle propre (palette botanique ivoire/vert/terracotta, fonts Fraunces + Hanken Grotesk, motif floral) pour éviter le site jumeau.

## Client

- **Nom** : Laverie du Floréal
- **Ville** : Agen (47000)
- **Adresse** : 16 rue Bajon, 47000 Agen (confirmée web)
- **Secteur** : laverie automatique + point relais colis (Colissimo / Pickup)
- **Téléphone** : 07 68 74 00 73 (trouvé en ligne, à confirmer)
- **Site actuel** : aucun
- **Atouts terrain** : grands séchoirs, point relais colis, en centre-ville d'Agen

## À CONFIRMER avec le prospect (placeholders flaggés dans index.astro)

- Horaires exacts (sources divergentes : 6h-22h / 7h-22h / 8h-20h ; mis 7h-22h)
- Tarifs réels des machines (valeurs actuelles = estimations)
- Capacités exactes des machines, lessive incluse ou vendue
- Photos réelles du lieu (remplacer les Unsplash génériques)
- Email de contact (laveriedufloreal@gmail.com = placeholder)

## Stratégie de la démo

1. Faire un site **éditorial premium**, type Linear/Apple, pas un template SaaS générique.
2. Le client doit ressentir « c'est mieux que tout ce qu'il y a dans ma ville ». C'est ça qui ferme la vente.
3. Sections probables : Hero, services (machines lavage/séchage, tarifs), horaires & accès, équipements, contact.
4. Si tu manques d'infos terrain (horaires exacts, photos), pose des **placeholders cohérents** et flag-les pour que je les remplace après visite réelle.
5. Photos : utiliser Unsplash en passant par WebFetch sur la page de recherche officielle pour vérifier les IDs (jamais inventer une URL). Sinon Picsum en fallback.

## Coordonnées dev (à insérer dans Contact)

- Email : `darysisowath@gmail.com`
- Téléphone : `06 99 46 17 22`

## Offres à mentionner si une page « tarifs site » est demandée

| Création (one-shot) | 400 à 700 € selon scope |
|---|---|
| Maintenance Basic | 30 €/mois (hébergement, sécurité, sauvegardes, petites modifs) |
| Maintenance Premium | 60 €/mois (Basic + Google Business Profile, SEO local, modif contenu, conseils visibilité) |

## Règles de design (héritées du portfolio Dary)

- **Pas d'esthétique IA générique** : pas de grille de cards bordées avec icône-dans-carré-arrondi. Préférer typographie éditoriale, hairlines, asymétrie. Utiliser la skill `frontend-design`.
- **Pas d'em-dashes (—) ni d'en-dashes (–)** dans aucun texte affiché. Utiliser virgule, point ou point médian (·).
- **Pas de listes nues 01/02/03/04** : préférer eyebrow textuels (« Premier contact », « Cadrage », etc.) ou simplement des sections.
- **Mobile-first réel** : la moitié des visiteurs scannera depuis leur téléphone devant la machine.
- **Charge mentale faible** : peu de texte, gros CTA, navigation évidente.
- **Vérifier les URLs d'images** avant de les utiliser (WebFetch puis curl HEAD), ne jamais fabriquer un ID Unsplash au feeling.

## Stack technique

- **Astro v6** + **Tailwind v4** (via `@tailwindcss/vite`)
- Pas d'islands React au démarrage (Astro pur). Ajouter `framer-motion` + island React seulement si une animation complexe le justifie.
- Pour smooth scroll premium : ajouter `lenis` quand pertinent (cf. portfolio Dary qui utilise déjà).
- Déploiement : **Cloudflare Pages**, en mode auto-deploy Git (chaque `git push` sur `main` déclenche un rebuild + redéploiement). Build command `pnpm build`, output `dist/`, Node 22 (épinglé via `.nvmrc`). Pas d'adaptateur SSR : site 100 % statique.

## Posture de travail

Tu es **Staff Fullstack Engineer top-tier** : qualité production, accessibilité, perf, mobile.
Tu es aussi **Senior UX Architect** : chaque section doit réduire la charge mentale du visiteur, pas l'augmenter. Pas d'over-engineering.

## Workflow recommandé pour démarrer

1. `pnpm install` (si pas déjà fait)
2. `pnpm dev` → http://localhost:4321
3. Concevoir Hero + sections en commit incrémental, voir en navigateur après chaque bloc.
4. Quand stable : `git push` sur `main`. Cloudflare Pages rebuild et redéploie automatiquement (projet `laverie-du-cygne`). Vérifier le build local avec `pnpm build` avant de pousser.
5. URL de la démo à envoyer au prospect au format `laverie-du-cygne.pages.dev` ou domaine custom rattaché dans Cloudflare.

## À demander au prospect (script DM/email à envoyer en parallèle)

- 3 ou 4 photos du lieu (intérieur, machines, façade)
- Horaires d'ouverture exacts
- Adresse postale précise
- Tarifs des machines (lavage par taille, séchage, lessive vendue)
- Téléphone éventuel ou seulement présence physique
- Compte Google Business Profile existant ou pas
