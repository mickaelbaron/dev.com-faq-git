7.3.2 Les remotes
- Comment lister les remotes d'un repository ?

```
$ git remote -v
origin https://www.domain.tld/git/repo.git (fetch)
origin https://www.domain.tld/git/repo.git (push)
```

Un remote est désigné par 2 urls, une url de `fetch` (indique où tirer les modifications effectuées par les autres développeurs) et une url de `push` (indique où pousser ses propres modifications).

Certaines organisations adoptent le forking model pour gérer la collaboration dans le projet. Un nouveau développeur clonera le projet depuis le repository central, forkera ensuite ce repository puis changera sa push url pour pousser sur son fork au lieu du repo central. Les modifications du fork vers le repo central seront effectuées au travers pull/merge request depuis l'outil web présent sur le repo central (github, gitlab, ...). Ce modèle a pour avantage de simplifier et de sécuriser fortement la gestion des droits en écriture sur le repository central.

- Comment ajouter un remote ?

```
$ git remote add <alias> <chemin/url>
```

Où `<alias>` désigne le nom du `remote`.

- Comment inspecter un remote ?

```
$ git remote show origin
```

Affiche l'état du repository distant (fetch et push urls, liste des branches, si elles sont trackées ou non, branches locales configurées pour un pull et pour un push.

- Comment supprimer un remote ?

```
$ git remote rm <remote>
```

Où `remote` désigne le nom du repository distant.

- Comment renommer un remote ?

```
$ git remote rename <old> <new>
```

Où `old` désigne le nom du repository distant à changer et `<new>` le nouveau nom à donner.

Par exemple :

```
$ git remote rename origin dist
```

A pour effet de modifier le nom du repository distant de 'origin' en 'dist'.

- Comment mettre à jour la représentation locale d'un remote ? (fetch)

```
$ git fetch <remote>
```

Où `<remote>` correspond au nom du remote (`origin` par défaut lors d'un clone).

- Comment mettre à jour une branche locale avec une branche distance ?

```
$ git checkout <branche>
$ git pull <remote> <branche>
```

Où `<remote>` correspond au nom du remote (`origin` par défaut lors d'un clone) et `<branche>` au nom de la branche.

La commande `pull` exécute en réalité un `fetch` suivi d'un `merge`, au détail cela donnerait  :

```
$ git checkout master
$ git fetch origin
$ git merge origin/master
```

L'exécution d'une commande `pull` peut donc nécessiter de résoudre des conflits puisqu'il s'agit d'un `merge`.

- Comment mettre à jour un remote ? (push)