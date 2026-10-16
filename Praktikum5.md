<img width="959" height="599" alt="Screenshot 2026-10-16 113652" src="https://github.com/user-attachments/assets/3b4f3a5e-b460-4890-8148-51afe322ed37" />
<img width="959" height="599" alt="Screenshot 2026-10-16 114501" src="https://github.com/user-attachments/assets/2713ac31-3e15-44e6-af5d-c93dab01f53d" />
<img width="959" height="599" alt="Screenshot 2026-10-16 114655" src="https://github.com/user-attachments/assets/4881debb-617c-4418-b2d1-04e7b5f0d53a" />
<img width="959" height="599" alt="Screenshot 2026-10-16 115147" src="https://github.com/user-attachments/assets/725f1123-f3d2-414e-903b-81eb1bb9d94f" />


Praktikum oli huvitav, pole ise väga linuxit kasutanud praktikumidest väljaspool niiet on head ülesanded selle op-süsteemiga tutvumiseks. Kõige raskem oli commandide kirjutamine, tegin seda päris mitu korda algusest peale.


esimene käsk:  ps -axu | grep daemon | grep -v grep | tr -s ' ' | cut -d' ' -f11- 

teised käsud: 
 ip a | grep "inet " | grep -v "127.0.0.1" | tr -s ' ' | cut -d' ' -f3 | cut -d'/' -f1 > ipaddress.txt

cat ipaddress.txt

xargs -n1 ping -c 2 < ipaddress.txt

Programmi WinTeated.exe käivitamisel ja selle aknas tegevuste tegemisel (hiire liigutamine, klõpsamine, klaviatuuril trükkimine ning akna nihutamine) saatis Windowsi operatsioonisüsteem protsessile mitmeid sõnumeid, mis salvestati sulgemisel faili teatedOut.txt 

Esimene valitud sõnum Sõnumi nimi ja ID: WM_LBUTTONDOWN (ID: 513 / hex 0x0201) Mis tegevuse peale saadeti: Sõnum saadetakse protsessile siis, kui kasutaja vajutab hiire vasakut nuppu akna tööalal. wParam: Näitab, kas vajutamise hetkel olid all ka teatud lisaklahvid või muud hiirenupud. lParam: Sisaldab hiirekursori täpseid koordinaate akna sees, kus madalamad 16 bitti määravad X-koordinaadi ja kõrgemad 16 bitti Y-koordinaadi.
Teine valitud sõnum Sõnumi nimi ja ID: WM_KEYDOWN (ID: 256 / hex 0x0100) Mis tegevuse peale saadeti: Sõnum saadetakse protsessile siis, kui kasutaja vajutab klaviatuuril mõnda mitte-süsteemset klahvi. wParam: Sisaldab vajutatud klahvi virtuaalset koodi, mis identifitseerib vajutatud klaviatuuriklahvi. lParam: Sisaldab lisainfot klahvivajutuse kohta, näiteks korduste arvu ja skaneerimiskoodi.
Tõlketabelis puuduv sõnum Tekitatud sõnum: Sõnum ID-ga 32 (hex 0x0020), mille nimeks oli failis märgitud ???.


