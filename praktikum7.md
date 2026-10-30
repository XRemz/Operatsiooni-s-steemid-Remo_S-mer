Ülesanne 7-1
Küsimus: Miks uued andmekandjad vajavad praktikumis sooritatud lähtestamist?

Vastus: Uued andmekandjad on tehases tühjad ja neil puudub failisüsteemi struktuur, mistõttu operatsioonisüsteem ei tea, kuidas sinna andmeid salvestada. Lähtestamine on vajalik partitsioonitabeli (nt GPT) ja failisüsteemi loomiseks, mis paneb paika reeglid andmete kirjutamiseks ja lugemiseks.


Ülesanne 7-2
Küsimus: Too välja vähemalt 4 erinevat tehnilist eelist GPT kasutamiseks võrreldes MBR-iga.

Vastus:

Toetab hiiglaslikke kettaid (MBR on piiratud 2 TB-ga, GPT toetab eksabaite).

Lubab rohkem partitsioone (GPT toetab standardina kuni 128 partitsiooni, MBR ainult 4 põhipartitsiooni).

Pakub suuremat andmete turvalisust tänu varutabelile ketta lõpus (MBR-il on info ainult ketta alguses ja see võib kergemini rikneda).

Kasutab kumatuid UUID/GUID identifikaatoreid, mis väldib nimesüsteemi konflikte.


Ülesanne 7-3

link:   https://kodu.ut.ee/~remosomer/opsys/hdd.png

Ül 7.4
Pilt 1
<img width="520" height="283" alt="Screenshot 2026-10-30 153916" src="https://github.com/user-attachments/assets/1284a341-455b-4336-b3e1-0e15fa55489d" />


Ülesanne 7-5 ja 7-6
Küsimus: Mida mõjutasid mount-käsu parameetrid -o ro ja -t auto ning mis väärtusega asendas Ubuntu auto-parameetri?

Vastus: Parameeter -o ro haakis mälupulga ainult lugemisrežiimile (read-only) ja -t auto pani süsteemi failisüsteemi tüübi ise ära arvama. 
Käsu mount | grep /media/usb väljundist selgus, et Ubuntu asendas auto-parameetri väärtusega ext4 (või vastavalt sinu virtuaalse ketta vormingule).

Ülesanne 7-7

Pilt 2
<img width="515" height="295" alt="Screenshot 2026-10-30 153953" src="https://github.com/user-attachments/assets/0e626e25-3b69-4be4-9d13-09bc5c5cd687" />


Enda kogemus: Selle nädala praktikum oli minu jaoks palju raskem kui eelmised, olin päris mitu korda lühises, et mis nüüd valesti on aga lõppudelõpuks sain tehtud.
