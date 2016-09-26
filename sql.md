# SQL (avec mysql)

<!-- MarkdownTOC -->

- [Bases](#bases)
  - [Création de base](#création-de-base)
  - [Suppression de base](#suppression-de-base)
  - [Modification](#modification)
- [Tables](#tables)
  - [Création de table](#création-de-table)
  - [Requetes](#requetes)
    - [UNION](#union)

<!-- /MarkdownTOC -->


<a name="bases"></a>
## Bases
<a name="création-de-base"></a>
### Création de base

```sql
CREATE DATABASE formation COLLATE 'utf8_general_ci';
```

Exemple avec `IF NOT EXIST` (Création **seulement** si la base n'existe pas) :
```sql
CREATE DATABASE IF NOT EXISTS formation COLLATE 'utf8_general_ci';
```

<a name="suppression-de-base"></a>
### Suppression de base

```sql
DROP DATABASE formation;
```

Exemple avec `IF EXISTS` (Suppression **seulement** si la base existe) :
```sql
DROP DATABASE IF EXISTS formation;
```

<a name="modification"></a>
### Modification

```sql
ALTER DATABASE formation COLLATE 'latin1_swedish_ci';
```

<a name="tables"></a>
## Tables
<a name="création-de-table"></a>
### Création de table

```sql

```

<a name="requetes"></a>
### Requetes

<a name="union"></a>
#### UNION

```sql
(SELECT v.nom, v.couleur, v.annee, m.marque from voitures v INNER JOIN modeles m ON m.id=v.modele_id)
UNION
(SELECT vv.nom, vv.couleur, vv.annee, m.marque from voituresbis vv INNER JOIN modeles m ON m.id=vv.modele_id)
ORDER BY nom;
```