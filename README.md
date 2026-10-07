# Ce soir, on mange quoi ?

Un petit livre de recettes du quotidien en une seule page HTML, avec un module « Mon frigo » : tu dictes ce que tu as, il te propose les recettes faisables.

Projet perso, sans framework, sans backend, sans dépendance.

## Fonctionnalités

- **110 recettes simples** (6 ingrédients max hors placard), classées en pâtes & riz, viandes, poissons, œufs & légumes, desserts.
- **Index visuel** avec recherche par nom ou ingrédient (taper `healthy` filtre les recettes healthy).
- **Portions ajustables** : les quantités se recalculent.
- **Mon frigo** : dictée ou saisie des ingrédients, puis « On mange quoi ? » affiche les recettes faisables, celles où il manque 1 ingrédient, puis 2.
- **Option healthy** pour ne garder que les recettes légères.
- Illustrations dessinées en SVG dans la page : rien à charger à part les polices.

## Utilisation

Ouvrir la page publiée sur GitHub Pages, puis sur Android : Chrome › menu ⋮ › *Ajouter à l'écran d'accueil*.

La dictée utilise l'API de reconnaissance vocale de Chrome : elle ne fonctionne qu'en **https** (GitHub Pages) et a besoin d'une connexion. Sur un fichier ouvert en local, utiliser le micro du clavier ou la saisie.

## Structure

| Fichier | Rôle |
| --- | --- |
| `index.html` | L'application complète : style, script et données des recettes (bloc `<script id="donnees">`). |
| `recettes.json` | Copie des mêmes données, pour réutilisation ailleurs. Non lue par la page. |

## Format d'une recette

```json
{
  "id": "carbonara",
  "nom": "Spaghetti carbonara",
  "cat": "Pâtes & riz",
  "temps": 20,
  "p": 4,
  "healthy": false,
  "ing": [
    { "q": 400, "u": "g", "cle": "pates", "libelle": "spaghetti" },
    { "q": 4, "u": "", "cle": "oeuf" }
  ],
  "placard": "sel, poivre",
  "etapes": ["…", "…"]
}
```

- `cle` renvoie au dictionnaire `ingredients` : c'est elle qui sert au matching du frigo (ex. spaghetti, pennes et tagliatelles ont tous la clé `pates`).
- `libelle` (facultatif) remplace le nom affiché.
- Les ingrédients du placard (sel, poivre, épices…) sont en texte libre et ne comptent pas dans le matching.

## Crédits

Recettes classiques réécrites et simplifiées, inspirées de l'esprit de [Marmiton](https://www.marmiton.org) et [Jow](https://jow.fr). Aucun texte ni image n'en est repris. Projet sans lien avec ces sites.
