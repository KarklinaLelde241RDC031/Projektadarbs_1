# Projektadarbs_1
## Projekta uzdevums
Projekta uzdevums ir izveidot Webscraping programmatūru, kas ļauj efektīvi atlasīt datus no kādas izvēlētas interneta vietnes. 
Mūsu izvēlētā mājaslapa ir https://books.toscrape.com/, jo šī saite ir piemērota Webscraping programmatūras veidošanai un tā nesagādāja liekas problēmas ar piekļuves iegūšanu. Attiecīgi tieši mūsu uzdevums un mērķis bija izveidot grāmatu meklētāja programmu, kura ļauj atlasīt grāmatas pēc noteiktiem nosacījumiem. 
Izveidotā programma ļauj izvēlēties grāmatas pēc tās kategorijas/žanra, meklēt grāmatas pēc to reitinga (zvaigžņu skaita), meklēt grāmatas pēc nosaukuma, ļauj atlasīt grāmatas pēc noteikta cenu diapazona, kā arī dod iespēju izvēlēties vēlamo darbību no izvēlnes un saņemt rezultātu. 

## Izmantotās bibliotēkas
### request
Bibliotēka "request" ļauj ļoti vienkārši nosūtīt HTTP pieprasījumus, arī saņem HTML atbildes. Nav nepieciešams manuāli pievienot vaicājumu virknes.
Savā programmā esam to iekļāvušas, jo tā ir vienkārša un stabila bibliotēka, kas mums atļauj ērti iegūt tīmekļa lapas saturu.

### BeautifulSoup
"BeautifulSoup" ir bibliotēka, kas atvieglo informācijas atlasīšanu no tīmekļa lapām, piemēram, ar tādām metodēm kā "find", "find_all".
Mēs to izmantojam, jo tā ļauj viegli atrast un apstrādāt datus, piemēram, virsrakstus, cenas, kategorijas utt.

### concurrent.futures
Galvenā bibliotēkas "concurrent.futures" loma ir nodrošināt vairākpavedienu darbību-paralēlu lapu pārmeklēšanu. 
Mūsu programmā šī bibliotēka tiek izmantota, lai uzlabotu meklēšanas ātrumu, jo ir nepieciešams veikt grāmatu meklēšanu vairākās lapās.


## Izmantotās datu struktūras
Mūsu programmā ir izmantotas dažādas datu struktūras, kuras nodrošina ērtu informācijas apstrādi, meklēšanu un attēlošanu.
### Vārdnīca (dictionary)
Šī datu struktūra ļauj lietotājam izvēlēties kategoriju pēc skaitļa. Turklāt tā nodrošina ātru un efektīvu piekļuvi konkrētai kategorijai, izmantojot ".get()". Vārdnīcas atslēga ir kategorijas numurs (int).

Mūsu programmā šī datu struktūra ir izmantota funkcijā "get_categories()", lai saglabātu grāmatu kategorijas kopā ar to URL saiti.
### Saraksts (list)
Datu struktūra "list" ļauj dinamiski pievienot datus (.append() vai .extend()). Saraksti arī ir labi piemēroti gadījumiem, kad rezultātus ir nepieciešams saglabāt noteiktā secībā, kā arī tos ir viegli filtrēt un apvienot vairākus sarakstus vienā.

Saraksti ir izmantoti vairākos gadījumos, piemēram,:
+ books=[] - grāmatu meklēšana no lapām, piemēram, "get_books_from_category";
+ found_books=[] - uzkrāj meklēšanas rezultātus funkcijā "search_by_name()";
+ matches=[] - atrod konkrētās/atbilstošās grāmatas;
+ futures=[] - satur paralēlos izpildes uzdevumus (tiek pārmeklētas vairākas lapas/kategorijas vienlaicīgi).
### Simbolu virknes (str)
Izmantojot simbolu virknes, teksta salīdzināšana ir daudz ērtāka, kā arī tās tiek izmantotas struktūru identificēšanai HTML dokumentā. 

Mūsu prgrammā simbolu virknes ir izamntotas kategoriju nosaukumos un grāmatu virsrakstos, kā arī lietotāja ievadē, piemēram, kas tiek ievadīts vēlamais gramatas nosaukums.
### Skaitļi (int, float)
Skaitļu izmantošana nodrošina precīzu skaitlisku salīdzināšanu un intervālu pārbaudi, piemēram, cenai vai reitingam. Protams, skaitļi mūsu programmā ir nepieciešami, lai interpretētu lietotāja izvēles.

Skaitļi tiek izmantoti šādos gadījumos:
+ Kategorijas izvēles numuros (int);
+ Reitingos (int);
+ Cenu diapazona noteikšanā (float).
## Programmatūras izmantošanas metodes
Mūsu programmatūra ir izstrādāta kā komandrindas interfeiss (CLI), kas nodrošina interaktīvu lietotāja saskarni datu iegūšanai no vietnes. Tas ir līdzeklis, lai mijiedarbotos ar programmatūru un izmantojot komandas, katra komanda ir formatēta kā teksta rindiņa. 
### Interaktīva izvēlne
Programma sākas ar izvēlnes attēlošanu, kas ļauj lietotājam izvēlēties vienu no šādām darbībām:
+ 1-Meklēt grāmatas pēc kategorijas;
+ 2-Filtrēt grāmatas pēc reitinga;
+ 3-Filtrēt grāmatas pēc cenas;
+ 4-Meklēt grāmatu pēc nosaukuma;
+ 5-Iziet no programmas

Lietotājam ir jāievada attiecīgais skaitlis, kurš atbilst vēlamajai darbībai. Kad darbība ir izvēlēta, programma attiecīgi to izpilda.
### Meklēšana pēc kategorijas
Šajā metodē lietotājam tiek parādīts visu pieejamo kategoriju saraksts ar attiecīgajiem kārtas numuriem. 

Ievadot kādu numuru, programma apmeklē attiecīgo kategorijas lapu un izvada visus grāmatu nosaukumus, kas attiecīgajā kategorijā ir iekļauti.
### Filtrēšana pēc reitinga
Filtrēšana pēc reitinga ir izmantota, lai atrastu grāmatu, kura ir pēc iespējas labāk novērtēta (no 1 zvaigznes līdz 5 zvaigznēm), katrā kategorijā. Lietājs izvēlas kuru kategoriju vēlas apskatīt.

Lietotājs ievada sev vēlamo zvaigžņu skaitu (1-5). Kad tas ir izdarīts, programma pārskata grāmatas, meklējot tās, kurām atbilst šis reitings, piemēram, 3 zvaigznes.

Rezultātā, atbilstošie grāmatu nosaukumi tiek izvadīti uz ekrāna.
### Filtrēšana pēc cenas
Izmantojam "Cena", lai atrastu grāmatas, kuras maksā kādu konkrētu summu. 

Lietotājam ir dota iespēja ievadīt minimālo un maksimālo cenu, piemēram, 10 līdz 30. Programma pārskata grāmatas, analizējot katras cenas lauku. 

Rezultātā programma izvada tikai to grāmatu nosaukumus, kuras ietilpst norādītajā cenu diapazonā.
### Meklēšana pēc nosaukuma
Ar metodi "Atrast" lietotājs var brīvi meklēt jebkuru grāmatu, ievadot tās nosaukumu. 

Programma ar paralēlo apstrādi pārbauda visas lapas, meklējot visus ierakstus, kas atbilst ievadītajam nosaukumam, kurš tiek meklēts. 

Rezultāti tiek apkopoti un izvadīti kā saraksts.
### Iziešana no programmas
Mūsu programmai ir lietots "loop", kas nozīmē, ka programma turpina savu darbību līdz tā tiek apstādināta. To arī nodrošina šī metode.

Ievadot izvēlni "5", tiek izvadīts paziņojums "Darbs pārtraukts." un programma beidz darbību.

