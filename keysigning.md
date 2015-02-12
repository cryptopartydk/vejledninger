# Key Signing Party Vejledning
*Tid og sted: Den 27/2 kl 18:00 på Ørsted Ølbar, Nørre Farimagsgade 13, 1364 Kbh K*  
[Tilmelding](http://doodle.com/ckh8btspqz8mxgrs)
## Hvordan forbereder jeg mig til keysigning?
* Generér et PGP nøglepar
* Eksportér din offentlige nøgle og send den i en email til Jesper på keysigning@graffen.dk *senest den 26. kl 12:00*
* Umiddelbart inden vi mødes vil Jesper udskrive listen i samme antal eksemplarer som har skrevet sig op til signing. 
* Det er altså kun de keys, der står på listen, der deltager i key signingen. 
* Et link til Listen med alle deltagende nøgler bliver offentliggjort her, på [doodle-siden](http://doodle.com/ckh8btspqz8mxgrs), på [Facebook](https://www.facebook.com/events/857599447611478/) og på [Twitter](http://twitter.com/graffen) den 26. om aftenen. Sørg for at udskrive listen og tag den med. Tag også en kuglepen med. 
  
## Hvordan foregår det så på selve aftenen?
I løbet af aftenen er det din opgave, at mingle og opsøge så mange på listen som muligt. Har du glemt din liste eller ikke adgang til en printer, så tager Jesper nogle ekstra lister med (husk at verificere at din liste er identisk med de andre deltageres)  

Når du finder en ny person som du ikke har verificeret før: 
* Start med at verificér hinandens fingerprints på begge jeres lister (for at sikre, at den ene part ikke har en anden liste end din). Stemmer det, så kryds af i feltet 'Key Info Matches?'
* Hvis fingerprints stemmer så verificér hinandens identitet ved at kontrollere navnet på enten pas eller kørekort imod det, der står på listen.
* Kryds nu af i 'Owner ID Matches?'
* Bliv og snak lidt, det her er også en fantastisk mulighed for at møde nye mennesker! - eller søg videre til næste person. 

## Hvad så bagefter?
Når keyparty'et er overstået så går vi igen hver til sit, med hver vores liste af verificerede keys. Når du kommer hjem og har god tid, så skal du signere
nøglerne. Det kan gøres efter følgende opskrift: 
* Start en kommandoprompt/terminal
* For hvert KeyID på listen gøres følgende: 
  * gpg --recv-keys 0x&lt;keyid> (hent nøgle fra server - bemærk at KeyIDs skal startes med 0x, f.eks. 0xD9FA2EE5)
  * gpg --fingerprint &lt;email> (verificér fingerprint med sedlen - vær sikker på, at hele fingerprintet passer)
  * gpg --sign-key --ask-cert-level &lt;email> (signér nøglen med niveau 3)
  * gpg -a --export &lt;email> > &lt;filename> (eksporter den signerede nøgle f.eks. til <KeyID>.signed.asc)
  * Send den eksporterede fil via email til den adresse, der tilhører den nøgle du lige har signeret. 
* Når du modtager en mail fra en af de andre indeholdende en signeret nøgle, skal du importere den til din nøglering: 
  * gpg --import &lt;filnavn>  
  Hvis du vil sende de nye signaturer til de offentlige keyservers skriver du  
  gpg --send-key 0x&lt;Dit KeyID>
  
