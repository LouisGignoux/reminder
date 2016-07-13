Quand on veut revenir sur un commit fait par erreur ou inutile, on
commence par :

```bash
git reset HEAD~
```
(Note que si on veut seulement ajouter plus de changements aux précédents
commits, on pourra utiliser ```git reset --soft HEAD~``` qui conserve commités
les changements que l'on a déjà effectué)

Si on veut faire disparaître à tout jamais le dernier commit, on
utilisera ```git reset --hard HEAD~```

On peut ensuite éditer les fichiers, puis ajouter les fichiers dans notre
commit, et enfin :

```bash
git commit -c ORIG_HEAD
```

```reset``` a copié l'ancienne HEAD dans .git/ORIG_HEAD, c'est là qu'on va
pouvoir éditer notre vieux commit

A retenir : HEAD est un pointeur vers le dernier commit, on peut le
faire reculer de n commits avec ```HEAD~n```

Et maintenant, quid si on a détruit un commit et qu'on veut le récupérer ?
Et bien il y a toujours un moyen :

```bash
git reflog
```

On retrouve le commit détruit (son sha) et on termine avec :

```bash
git checkout -b newBranch shaToRecover
```

Pour comprendre la différence entre HEAD^ et HEAD~ :

```bash
G   H   I   J
 \ /     \ /
  D   E   F
   \  |  / \
    \ | /   |
     \|/    |
      B     C
       \   /
        \ /
         A
A =      = A^0
B = A^   = A^1     = A~1
C = A^2  = A^2
D = A^^  = A^1^1   = A~2
E = B^2  = A^^2
F = B^3  = A^^3
G = A^^^ = A^1^1^1 = A~3
H = D^2  = B^^2    = A^^^2  = A~2^2
I = F^   = B^3^    = A^^3^
J = F^2  = B^3^2   = A^^3^2
```
