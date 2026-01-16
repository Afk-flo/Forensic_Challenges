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
