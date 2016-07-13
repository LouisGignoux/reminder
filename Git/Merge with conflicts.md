Quand une branche ne peut pas être mergée automatiquement :

```bash
git pull --rebase origin/master
```
(origin/master est la cible sur laquelle on veut merge)

Il va ensuite falloir résoudre les conflits 1 par 1, à chaque conflit
résolu on le commitera puis on passera au suivant :

```bash
git commit
git rebase --continue
```
(on passe au conflit suivant)

Une fois qu'on a traité tous les conflits, il ne reste plus qu'à faire
le merge automatiquement

Si on veut arrêter le rebase, on peut le faire très simplement er revenir
là où on en était avant de lancer le rebase :

```bash
git rebase --abort
```
