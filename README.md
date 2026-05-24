# grappe-registry

Registry [shadcn/ui](https://ui.shadcn.com/) maison de la **grappe CRM** (Wepo, Réservation Salles, futures apps).

Distribue les **tokens design**, **styles partagés** et **blocks de layout** consommables par n'importe quelle app de la grappe via `npx shadcn add @grappe/<nom>`.

## Spec normative

La spec humaine (tokens, composants par wave, blocks, contrat HTTP) vit dans **[`acetibo/grappe-crm`](https://github.com/acetibo/grappe-crm)** → `crm-maison/charte-graphique.md`. Ce repo n'est que le distributable machine-readable.

## Structure

```
registry.json              # index des items disponibles
tokens/grappe-tokens.json  # CSS vars communes (couleurs, radius, shadows, fonts, nav)
styles/grappe-base.json    # reset @layer base partagé
blocks/admin-shell.json    # layout sidebar admin + topbar minimaliste
```

## Utilisation depuis une app grappe

Configurer le registry dans `components.json` de l'app :

```json
{
  "registries": {
    "@grappe": "https://raw.githubusercontent.com/acetibo/grappe-registry/main/{name}.json"
  }
}
```

Puis installer :

```bash
npx shadcn add @grappe/tokens
npx shadcn add @grappe/base
npx shadcn add @grappe/admin-shell
```

## Évolution

Toute modification de tokens ou de block doit :
1. Être discutée et actée dans `grappe-crm/crm-maison/CONTEXT.md` §3.
2. Mettre à jour `grappe-crm/crm-maison/charte-graphique.md` (spec normative).
3. Mettre à jour les fichiers JSON ici en parallèle.

Si breaking change : incrémenter la version du schéma `GrappeCharte` (cf charte-graphique.md §8.4).

---

*Repo public, sans secret. Versionné séparément de `acetibo/grappe-crm` (privé) pour permettre `npx shadcn add` sans authentification.*
