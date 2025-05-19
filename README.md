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


## Programmatūras izmantošanas metodes

