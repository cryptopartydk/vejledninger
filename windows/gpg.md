# GnuPG på Windows

## Hvad er GnuPG

... hvad er GnuPG for noget?

## Indhold
[Installation](#installation)  
[Generering af nøglepar](#generering-af-nøglepar)  
[Tips og tricks](#tips-og-tricks)

## Installation
* Hent den seneste version af GnuPG til Windows [her](http://gpg4win.org/).  

## Generering af nøglepar
Sådan genererer du dit første nøglepar...  
...  
...  

## Tips og tricks
I dette afsnit følger en stribe små tips og tricks til at optimere din GnuPG installation.  
Mange af tipsne kræver at du enten redigerer i konfigurationsfilen for GnuPG eller kører kommandoer fra kommandolinien.  
  
Konfigurationsfilen til GnuPG finder du ved at trykke Start -> Kør og skrive `%APPDATA%/gnupg`. I folder, der åbnes, ligger en fil ved navn gpg.conf - den skal du bare åbne i Notepad. 

### Brug sikre algoritmer
Som standard er GnuPG opsat til at bruge en form for laveste fællesnævner i forhold til, hvilke algortmer, der bruges til signaturer og krytpering. Nogle af disse algoritmer anses i dag for at være usikre (f.eks. SHA1).  
  
For at sætte nogle sikrere standardindstillinger skal du tilføje følgende linier i gpg.conf:  
``` 
default-preference-list SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP Uncompressed
personal-cipher-preferences AES256 TWOFISH AES192 AES
personal-digest-preferences SHA512 SHA384 SHA256 SHA224
cert-digest-algo SHA512
```
Hvis du allerede har genereret dit nøglepar, så kan du sætte de nye standardindstillinger på dit nøglepar som følger (Start -> Kør -> cmd <enter>): 
```
gpg --edit-key <din emailadresse>
setpref
... tryk Y for at godkende
save
```
