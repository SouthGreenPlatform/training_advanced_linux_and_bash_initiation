## Lancer plusieurs commandes successives

`cmd1 ; cmd2` → cmd2 exécutée une fois la cmd1 finie  
`cmd1 && cmd2` → cmd2 exécutée uniquement si cmd1 correctement finie

!!! example
        `wget linux.tar.gz && tar -zxvf linux.tar.gz`

## Lancer un processus en “arrière plan”



* `cmd1 &`  Lancer un processus en arrière plan
* `jobs` Connaître les processus qui tournent en arrière-plan
* `fg <job_number>` Récupérer un processus au premier plan
* `bg <job_number>` Envoyer un processus en arrière plan
* `nohup cmd1 &` “Détacher” le processus de la console. Fonctionne même quand la console est fermée, si deconnexion
* `Ctrl + Z` Stopper un processus


--8<-- "pages/practice/pratice3.md"