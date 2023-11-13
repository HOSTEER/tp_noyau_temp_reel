# tp_noyau_temp_reel


le TOTAL_HEAP_SIZE utilise de l'espace RAM. Cette RAM est nécessaire à l'OS pour créer chaque tâche, sémaphore, mutex, etc...
Dans le header de configuration la definition de configTOTAL_HEAP_SIZE change

hook dispo
Idle Hook Function
Tick Hook Function
Malloc Failed Hook Function
Stack Overflow Hook Function
Daemon Task Startup Hook

stack size alloué à chaque tâche dans freertos correspond à un nombre de bloc de 32 bits donc le nombre d'octet occupé correspond 4 fois stack size
Une bonne pratique de code en os est majorer la taille de la pile par 20 à 50% de la taille observer en debug avec top stack et pour les plus critique plus 100%

### Reentrace

Le projet n'affiche pas le texte adéquat des fonctions car la fonction printf stocke sa *string* dans u nbuffer static, ce qui pose problème lorsque plusieurs fonctions l'appelent (pour faire du débug par exemple). La solution est donc d'utiliser un mutex pour empêcher les autres fonctions d'appeler printf quand une *string* est en cours d'écriture.
