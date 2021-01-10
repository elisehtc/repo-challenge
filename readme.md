1. Corriger les typos du message du commit 03. 
Le message doit être redressé comme suit: 03- Started Hello World Feature

Les étapes:
git rebase -i HEAD~9
reword ec440b7 03- StArrtid Helo Volrd feature
esc :wq
03- Started Hello World Feature
esc :wq

2. Permuter l'ordre des commits 02 et 03 de manière à ce que le commit Started Hello ... 
apparaisse avant Finished Hello... dans l'historique. 
On doit faire ici une permutation des transactions de commit et non pas juste la permutation des messages. 
En effet, l'effet de l'actuelle transaction 2762d2bd doit apparaitre avant l'effet de la transaction 87da3d43 
et portera le message 02- Started Hello World Feature. 
La transaction 87da3d43 portera alors le message 03- Finished Hello World Feature.

Les étapes:
git rebase -i HEAD~10
esc :m 2
reword 03- Started Hello World Feature
reword 02- Finished Hello World Feature
esc :wq
02- Started Hello World Feature
esc :wq
03- Finished Hello World Feature
esc :wq

3. Changer l'auteur du commit 05 pour qui'il soit Me, the Challenger. 
On veut cacher que Le Pompier était à notre secours !

Les étapes:
git rebase -i HEAD~7
edit e0a21ce 05- debugging
esc :wq
git commit --amend --author="Me, the Challenger" --no-edit
git rebase --continue
 

4. Ecraser l'actuel commit numéro 06. 
On ne veut pas divulguer cette opération critique dans l'historique par peur que certains curieux viendront 
y chercher des données sensibles.

Les étapes:
git rebase -i HEAD~6
drop bed5816 06- important secret
esc :wq
 
5. Fusionner les 3 commits 07, 08, et 09 en un seul commit portant le message Add doc.

Les étapes:
git rebase -i HEAD~5
squash 08ba6cb 08- Add doc - step 2
squash 931ff11 09- Add doc - step 3
:wq

6. Faire en sorte que le commit 11 soit une continuité du commit 10 et qu'il en conserve le message.

Les étapes:
git rebase -i HEAD~2
squash e5ae586 11- I forgot a semicolon
:wq
Premier message: 10- Test for feature hello world
Squashed - 11- I forgot a semicolon
:wq