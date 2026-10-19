1) a) Faili sisu lugemiseks:
      Kataloogil /tmp/kaust on vaja minimaalselt käivitusõigust (--x ehk 1), et kasutaja saaks kataloogist läbi minna.
      Failil minufail.txt on vaja minimaalselt lugemisõigust (r-- ehk 4), et faili sisu avada ja lugeda.
b) Faili kustutamiseks:
      Kataloogil /tmp/kaust on vaja minimaalselt kirjutus- ja käivitusõigust (-wx ehk 3), sest faili kustutamine tähendab kataloogi sisu muutmist.
      Failil endal ei ole kustutamiseks vaja mingeid õigusi (000), kuna faili eemaldamine sõltub täielikult selle vanemkataloogi õigustest.

Ülesanne 6-2: Skriptifaili käivitamine
        Antud käivitusõiguse andmine (chmod a=x) ei ole kesta/shelli-skripti (.sh) käivitamiseks piisav, kuna see käsk seab failile ainult käivitusõiguse (x) ning eemaldab kõik muud õigused (sh lugemis- ja kirjutamisõigused).
        Selleks, et kest (shell) saaks skriptifaili sisu käivitada, peab süsteem saama faili reaalselt avada ja selle read läbi lugeda. Seetõttu on lisaks käivitusõigusele hädavajalik ka lugemisõigus (r) – näiteks kujul chmod a+rx või chmod a=rx. Kui lugemisõigus puudub, annab süsteem veateate, et faili pole võimalik avada või sellele ligi pääseda.
  Ülesanne 6-3: Kasutaja privaatgrupp (UPG) ja umask
      Linuxis luuakse igale uuele kasutajale vaikimisi samanimeline privaatgrupp (User Private Group, UPG), mis sisaldab ainult seda ühte kasutajat.
      See aitab tagada turvalisust koos vaikimisi umask-i seadistusega (nt 0002 või 0022) seetõttu, et iga kord, kui kasutaja loob uue faili või kataloogi, määratakse selle grupiks automaatselt tema isiklik privaatgrupp, mitte mingi üldine ühine grupp (nagu vanemates Unixi süsteemides users).
      Tänu sellele on uute failide grupi- ja teiste õigused vaikimisi piisavamalt kitsendatud ning teised tavakasutajad ei saa automaatselt ligipääsu kasutaja isiklikele failidele, mis tõstab oluliselt süsteemi ja andmete turvalisust.
<img width="959" height="599" alt="image1" src="https://github.com/user-attachments/assets/5cedf91a-c452-44b5-9308-580c5f91d45e" />

Käsuga id on näha, et meie tavakasutaja kuulub gruppi majasisene.
Käsuga ls -la kontrollisime faili uusfail.txt õiguseid ja omanikke (omanik on peeter, grupp on majasisene).
Käsuga cat uusfail.txt õnnestus faili sisu edukalt kuvada, kuna failile on määratud grupi õigusekslugemisõigus (g=r) ning meie tavakasutaja kuulub samasse gruppi (majasisene), olemata ise faili omanik või root.


<img width="959" height="599" alt="image2" src="https://github.com/user-attachments/assets/a34d2e2f-b213-4bab-8d02-670614b6eaf1" />


Ülesanne 6-5: setuid-õiguse kasutamine ja vajadus
      Setuid (Set User ID) õigus võimaldab käivitada programmi faili omaniku õigustes, mitte selle käivitaja enda õigustes. See on vajalik näiteks selleks, et tavakasutaja saaks teatud kindlat programmi kasutada ja selle kaudu andmeid lugeda, kuigi tal failile endale otsest ligipääsu ei ole.
Ülesanne 6-6: setuid-i turvamõju (plussid ja miinused)
      Miks seda vaja on (probleemi lahendus): Setuid lahendab olukorra, kus kasutajal on vaja sooritada mingi konkreetne tegevus, mis nõuab kõrgemaid õigusi. See võimaldab anda kasutajale ligipääsu ainult ühele kindlale programmile, ilma et peaks talle andma ohtlikke administraatoriõigusi või avama ligipääsu teistele tundlikele failidele.
      Turvariskid: Setuid-funktsionaalsusega kaasnevad ka tõsised ohud. Kui sellises programmis (eriti C-keeles kirjutatud koodis) on mõni turvaauk või viga – näiteks puhvri ületäitumine –, võib ründaja seda ära kasutada. Selle tulemusena võib ta saada programmi omaniku (tihti isegi süsteemi ülemkasutaja ehk root) õigused ja kogu arvuti oma kontrolli alla.




Ülesanne 6-7: Sticky bit ja failide kustutamine
      Sticky bit-õigustega kataloogis saavad kasutaja peeter poolt loodud faile kustutada:
    Faili omanik ehk kasutaja peeter ise.
      Kataloogi omanik ehk kasutaja opetaja (kes kataloogi lõi).
      Süsteemi ülemkasutaja ehk root.
Ülesanne 6-8: ACL (Access Control List) õiguste uurimine
      Mida märkad ls -la väljundis: Faili õiguste lõppu on ilmunud tähemärk + (näiteks -rw-r-----+), mis annab märku, et failile on lisatud täiendavad ACL-põhised pääsuõigused, mis lähevad tavapärase Unixi (omanik, grupp, teised) õiguste süsteemi piiridest kaugemale.
Ülesanne 6-9: Täiendavad failiatribuudid (chattr +i)
      Kes saab +i atribuudiga faili sisu muuta? Mitte keegi (isegi mitte root-kasutaja), sest fail on täielikult lukustatud.
Kuidas sellist faili kustutada? Kuna faili otse kustutada ei saa, tuleb see esmalt lahti lukustada ja alles siis eemaldada järgmises järjekorras:
      $ sudo chattr -i testfail-2 (eemaldab lukustuse)
      $ rm testfail-2 (kustutab faili)

Arvamus: Praktikum oli huvitav, pole varem linuxis rolle teinud niiet sain seda omal käel katsetada. Arusaamatus tekkis siis, 
kui lisasin uue rolli, nt opetaja või jukuisa ja siis küsis programm uut parooli, mida ta sisestades isegi tärnidena ei kuvanud.
Algul arvasin, et viga programmis niiet proovisin paar korda uuesti kuid lõpuks sain aru, et ta ei pidanudki seda kuvama.
