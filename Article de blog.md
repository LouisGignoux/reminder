#How to get rid of your commits with git reset HEAD

It's a beautiful day, you're coding and everything goes fine, and suddenly you
realize that you forgot to get rid of logs in the last commit you push :

```bash
if diff > 0
  console.log "Team Jacob"
else
  console.log "Team Edward"
```

After staring motionless at your screen for 5 seconds, your first instinct is
to revert the commit, but it is not enough. That thing has to disappear
completely.

#Bien expliquer la différence entre revert et reset

```bash
git reset HEAD~
```

# TODO

After a few trials, you've become quite fluent with ```git reset HEAD~```,
but you've encountered another problem : what if you want to access to the
second parent of a commit ?

```bash
B     C
 \   /
  \ /
   A
```
Here you want to get rid of C, but git reset HEAD~2 only allows you to get to B

For this you will use a slightly different command :

```bash
git reset HEAD^2
```
With this you will access the second parent of the last commit

And the most beautiful thing in all that ? You can make combinations with ^
and ~ to access any commit you want in any tree :

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
```
Try to access every commit in the tree and check the solution below !
(A is HEAD)

# Ici je voudrais mettre une balise spoiler
```bash
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

# TODO

But what if you destroyed the wrong commit by mistake, well you have a choice
between smashing your head on your keyboard, blaming the weather and your
trackpad, or use :

```bash
git reflog
```

You will retrieve the commit you destroyed (its sha identifier to be more specific), and you will be able to recover it like this :

```bash
git checkout -b newBranch shaToRecover
```


```bash
```
