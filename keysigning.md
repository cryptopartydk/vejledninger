# Key Signing Party Vejledning
*Tid og sted: Den 27/2 kl 18:00 på Ørsted Ølbar, Nørre Farimagsgade 13, 1364 Kbh K*  
[Tilmelding](http://doodle.com/ckh8btspqz8mxgrs)

## Hvordan forbereder jeg mig til keysigning?

* Det forudsættes at du allerede har genereret et PGP-nøglepar, som du gerne vil have andre til at signere.
* Eksportér din offentlige nøgle. I kommandoprompten/terminalen gøres det med:  
  `gpg --export -a <din emailadresse> > pubkey.asc`
* Vedhæft filen pubkey.asc til en email som sendes til Jesper på keysigning@graffen.dk *senest den 26. kl 21:00*
* Efter kl 21 den 26. februar, vil der blive genereret en HTML-fil som indeholder en liste med alle de indsendte nøgle-ID'er, fingerprints og navne.
* ~~Et link til listen med alle deltagende nøgler bliver offentliggjort her, på [doodle-siden](http://doodle.com/ckh8btspqz8mxgrs), på [Facebook](https://www.facebook.com/events/857599447611478/) og på cryptoparty.dks IRC kanal (#cryptopartydk på Freenode) den 26. om aftenen.~~   
* Listen med deltagernøgler ligger [her](http://graffen.dk/keysigning). Bemærk, at emailadresser er masket indtil videre. De bliver afmasket aftenen inden arrangementet. Sørg for at udskrive listen og tag den med. Og en kuglepen.

## Hvordan foregår det så på selve aftenen?
I løbet af aftenen er det din opgave, at mingle og opsøge så mange på listen som muligt. Har du glemt din liste eller ikke adgang til en printer, så tager Jesper nogle ekstra lister med (husk at verificere at din liste er identisk med de andre deltageres)  
Når du finder en ny person som du ikke har verificeret før:

* Start med at verificér hinandens fingerprints på begge jeres lister (for at sikre, at den ene part ikke har en anden liste end din). Stemmer det, så kryds af i feltet 'Key Info Matches?'  
Hvis du vil være ekstra sikker, så skriv gerne dit eget fingerprint ned på et stykke papir inden keysigningen, og brug dét til at verificere imod.
* Hvis fingerprints stemmer så verificerer i hinandens identitet ved at kontrollere navnet på enten pas eller kørekort imod det, der står på listen.
* Kryds nu af i 'Owner ID Matches?'
* Bliv og snak lidt, det her er også en fantastisk mulighed for at møde nye mennesker! - eller søg videre til næste person.

## Hvad så bagefter?
Når keyparty'et er overstået så går vi igen hver til sit, med hver vores liste af verificerede keys. Når du kommer hjem og har god tid, så skal du signere
de nøgler, du har verificeret. Det kan f.eks. gøres efter følgende opskrift:

* Start en kommandoprompt/terminal
* For hvert KeyID på listen gøres følgende:
* `gpg --recv-keys 0x<keyid>` (hent nøgle fra server - bemærk at KeyIDs skal startes med 0x, f.eks. 0xD9FA2EE5)
* `gpg --fingerprint <email>` (verificér fingerprint med sedlen - vær sikker på, at hele fingerprintet passer)
* `gpg --sign-key --ask-cert-level <email>` (signér nøglen med niveau 3)
* `gpg -a --export <email> > <filename>` (eksporter den signerede nøgle f.eks. til &lt;KeyID>.signed.asc)
* Send den eksporterede fil via email til den adresse, der tilhører den nøgle du lige har signeret.
* Når du modtager en mail fra en af de andre indeholdende en signeret nøgle, skal du importere den til din nøglering:
* `gpg --import <filnavn>`
* `gpg --send-key 0x<Dit KeyID>` og til sidst sender du din nøgle med de nye signaturer på, til keyserveren.  
Keyserverne lægger altid kun til. Du kan altså ikke overskrive eller slette signaturer. 

## Hvorfor overhovedet signere hinandens nøgler?
Når du genererer et PGP-nøglepar så angiver du dit navn og en emailadresse. Det er selvfølgelig for at det skal synliggøres at den nøgle tilhører dig. Men der er ikke noget i PGP
der forhindrer dig i, at angive noget andet end dit eget navn, og så publicere nøglen ud på keyserverne. Jeg kunne f.eks. kalde mig selv for Bill Gates eller Barack Obama, og så publicere nøglen
i håb om, at nogen vil sende mig noget interessant.  
  
Hvordan undgår man så det?  

Det gør man ved, at få folk, der kender én til at stå inde for, at din nøgle rent faktisk tilhører dig. I praksis gøres det ved, at man laver en digital signatur på nøglen.
Når så du skal sende f.eks. mig en krypteret email, så går du ind og finder min nøgle på en keyserver. Tag f.eks. et kig på en af mine nøgler på [MIT's keyserver](http://pgp.mit.edu/pks/lookup?op=vindex&search=0x416C5A0DD9FA2EE5). 
Her kan du se, at der er flere signaturer på nøglen. Der er altså en række folk som enten kender mig personligt, og som har verificeret mit fingerprint ad andre veje (f.eks. over telefonen eller ved personligt møde), eller 
folk, der har verificeret at min identitet stemmer overens med de informationer, der findes i nøglen. På PGP-nøgler er det typisk navnet, man verificerer. Identitet verificeres normalt ved, at man fremviser et gyldigt og officielt udstedt ID. Det kunne
f.eks. være et pas eller et kørekort.  
  
Jo flere forskellige signaturer, du kan få på din nøgle, og jo flere nøgler du selv signerer, jo stærkere et "netværk" kommer din nøgle med i. I PGP kaldes dette netværk for
Web Of Trust. WoT kan bruges til, at give en indikation af, hvorvidt man kan stole på en given nøgle, også selvom man måske ikke kender ejeren eller har mødt vedkommende før.  

