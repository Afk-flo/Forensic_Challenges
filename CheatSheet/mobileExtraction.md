@todo 

# Extraction iOS 

## Extraction depuis un appareil iOS
--

## Extraction depuis une backup iOS 
### Cas backup chiffrée - Avec mot de passe 
L'outil "mvt-ios" est très pratique pour de l'analyse Forensic sur téléphone iOS. 
Il peut également être utilisé pour déchiffrer une backup [(documentation ici)](https://docs.mvt.re/en/latest/ios/backup/check/) et peut être utilisé de la sorte depuis un dossier chiffré (! Attention à bien vérifier la présence des fichiers Manifest.db, et les principaux plist)
```
mvt-ios decrypt-backup -p '<password>' -d '<decrypted-backup-directory>' '<backup path>'
```


### Cas backup chiffrée - Sans mot de passe 


### Fichier SQLite endommagé 
Pendant l'intervention, il se peut qu'une base de donneés sqlite rencontre quelques problèmes de structure. Voici un exemple d'un extract lors d'un CTF : 
```
# Base de données sms.db

sqlite> .tables
Error: database disk image is malformed

# Et pourtant, file identifie bien le fichier (le header est bon)
sms.db: SQLite 3.x database, last written using SQLite version 3028000, writer version 2, read version 2, file counter 2, data.......
```
iOS va manipuler différents ses fichiers .sqlite. Dans certains cas, il seront configurés en mode WAL Mode (Write-Ahead Log), dans ce cas, les éléments sont écrits sur un fichier "sms.db-whal" avant d'être introduit dans le fichier sqlite principal.

Pour ce faire : 
```
sqlite3 sms.db ".recover" > repair.sql
sqlite3 sms_repare.db < repair.sql
```

Si tout se déroule sans problème, vous serez en mesure d'exploiter ces fichiers.
