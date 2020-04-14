# Decred Journal – Marzec 2020

![abstrakcja](../img/journal-202003-384.png)

_Obraz: Wektor ekspansji, aut. @saender_

Najważniejsze wydarzenia z marca:

- Zmiana zasad konsensusu określona w DCP-0005 została aktywowana, wprowadzając do sieci Decred prawdopodobnie najbardziej bezpieczną i chroniącą prywatność implementację SPV dla lekkich klientów. Wszystkie węzły v1.4, które nadal działały, zostały odłączone od sieci.
- Budowany przez nas DEX skoordynował zlecenie pierwszej transakcji wymiany z wykorzystaniem atomic swaps w sieci testnet.
- W tym miesiącu nastąpił spektakularny postęp w prawie wszystkich kluczowych repozytoriach oprogramowania, o czym ze szczegółami można przeczytać poniżej.
- Roczne budżety na czynności w zakresie nawiązywania kontaktów i promocji dla społeczności amerykańsko-angielskich oraz brazylijskich zostały zatwierdzone na łączną kwotę 286 tys. dolarów, w tym część środków na kontynuację produkcji Dziennika.
- Jest to 24. wydanie Decred Journal, co oznacza dwa lata nieprzerwanego, comiesięcznego raportowania o projekcie Decred!


## Rozwój

O ile nie zaznaczono inaczej, prace zgłaszane poniżej mają status „scalonych z repozytorium głównym (master)". Oznacza to, że prace są ukończone, zrecenzowane i zintegrowane z kodem źródłowym, który zaawansowani użytkownicy mogą kompilować i uruchamiać, ale ich efekty nie są jeszcze dostępne w wersji plików binarnych dla zwykłych użytkowników.

[dcrd](https://github.com/decred/dcrd):

- podpisy ECDSA zostały [odłączone](https://github.com/decred/dcrd/pull/2139) od pakietu secp256k1, aby wyraźnie zaznaczyć, że ECDSA jest tylko jednym z możliwych algorytmów podpisu cyfrowego oraz aby umożliwić sygnaturom Schnorr stanie się obywatelem pierwszej kategorii bazy kodowej
- wyeksportowano [typ wartości pola](https://github.com/decred/dcrd/pull/2134), aby umożliwić zewnętrznym wywoływaczom wykonywanie zoptymalizowanej matematyki pola
- weryfikacja podpisu została dodatkowo zoptymalizowana poprzez minimalizację kosztownych operacji
- dodano metodę [czyszczenia](https://github.com/decred/dcrd/pull/2117) kluczy prywatnych z pamięci oraz [zredukowano](https://github.com/decred/dcrd/pull/2131) liczbę wewnętrznych kopii kluczy prywatnych w celu zwiększenia bezpieczeństwa przed scrapingiem pamięci
- duże liczby całkowite zostały [usunięte](https://github.com/decred/dcrd/pull/2107) całkowicie z operacji parsowania i podpisywania na rzecz specjalistycznego kodu skalarnego mod n
- testy weryfikacyjne Schnorra zostały [przerobione](https://github.com/decred/dcrd/pull/2128) w celu rozwiązania wielu problemów
- zapobieżenie niewłaściwemu wykorzystaniu kodu w kilku obszarach
- usunięto nieużywany kod

Ujawniono [lukę w oprogramowaniu](https://bounty.decred.org/2020/03/status-update/), która pozwalała na potencjalny wielodniowy atak wyczerpujący pamięć, który mógł doprowadzić do awarii węzła w dcrd v1.4.0. 13 marca sieć forkowała na nowe zasady konsensusowe, zaimplementowane w dcrd v1.5.0, co oznacza, że wszystkie węzły w sieci są zobowiązane do korzystania z co najmniej tej wersji oprogramowania. Ponieważ ta i późniejsze wersje zawierają poprawkę łatającą tę lukę, jej szkodliwość została teraz zneutralizowana.

dcrd pokrywa się kodem z btcd w mniej niż 16%, co oznacza, że pozostałe 84% to nowa praca deweloperska, według [analizy](https://coincode.sh/c/dcr/) autorstwa CoinCode.sh. @davecgh [potwierdził](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$15862843869377LGlSK:decred.org), że liczby wyglądają wiarygodnie, biorąc pod uwagę, jak dużo nowego kodu zostało napisane i zauważył, że rozbieżność ta jest jeszcze bardziej widoczna w dcrwallet (który nie był analizowany).


[dcrwallet](https://github.com/decred/dcrwallet):

- polecenie `fundrawtransaction` zostało [wdrożone](https://github.com/decred/dcrwallet/pull/1706); dodaje ono niepodpisane wejścia i zmienia wyjście do surowej transakcji
- operacje w portfelu zostały [przełączone](https://github.com/decred/dcrwallet/pull/1648) na korzystające z 2. wersji scommitowanych filtrów (filtry v1 są przestarzałe, ale nadal są obsługiwane przez sieć i używane przez dcrwallet; następne wydanie będzie korzystać z filtrów v2)
- polecenie `getaddressesbyaccount` zostało [naprawione](https://github.com/decred/dcrwallet/pull/1695), aby zwracać również zaimportowane adresy dla konta `imported`
- nieszyfrowane skrypty P2SH do wykupu biletów (redeem scripts) zostają [przeniesione](https://github.com/decred/dcrwallet/pull/1688) do pamięci menedżera adresów (upraszcza to przechowywanie i usuwa wymóg odblokowania portfela w celu przeglądania lub przechowywania skryptów)
- wewnętrzne udoskonalenia w zakresie efektywności i semantyki
- czyszczenie w celu usunięcia przestarzałego i nieużywanego kodu


[Decrediton](https://github.com/decred/decrediton):

- wsparcie dla [stakingu offline (cold staking)](https://github.com/decred/decrediton/pull/2424) (wymagane również dla stakingu z wykorzystaniem portfeli sprzętowych)
- wsparcie dla [importowania skryptów](https://github.com/decred/decrediton/pull/2423) w portfelach typu tylko do obserwacji (watch-only)
- pobranie przegłosowanych [propozycji](https://github.com/decred/decrediton/pull/2442) z dcrdata
- sprawdzanie w poszukiwaniu [nowych propozycji](https://github.com/decred/decrediton/pull/2420) w zakładce "Zarządzanie"
- responsywny [widok propozycji](https://github.com/decred/decrediton/pull/2444), wyświetlanie [adresów](https://github.com/decred/decrediton/pull/2416) w trybie podglądu i widoku transakcji oraz inne ulepszenia interfejsu użytkownika


Prace w toku:

- wsparcie dla [CoinShuffle++](https://github.com/decred/decrediton/pull/2452)

[Politeia](https://github.com/decred/politeia):

- [unieważnienie](https://github.com/decred/politeia/pull/1159) sesji przy zmianie hasła
- ulepszenia testów oraz poprawki błędów

Rozpoczęła się integracja tlog, która ma potrwać [~2 miesiące](https://github.com/decred/politeia/issues/1112#issuecomment-606147106). W [lipcu 2019](201907.md#development) niedokładnie poinformowaliśmy o rozpoczęciu integracji tlogów, ale praca ta była w rzeczywistości wdrożeniem odniesienia, które miało służyć jako weryfikacja pomysłu i pokazać, że googlowski magazyn danych [Trillian](https://github.com/google/trillian) może zastąpić istniejący backend Gita. Został on [scalony](https://github.com/decred/politeia/pull/951) w sierpniu i zawierał [klienta/serwer](https://github.com/decred/politeia/tree/master/tlog) z podstawową funkcjonalnością do przechowywania dokumentów. To doświadczenie dało wystarczający wgląd, aby stwierdzić, że będzie działać. Następnym krokiem jest napisanie backendu Politeia, który korzysta z Trilliana.

Główną zaletą backendu tlog jest to, że uczyni on Politeię bardziej skalowalną i pozwoli na cenzurowanie treści po jej upublicznieniu, zachowując jednocześnie ścieżkę audytu wszystkich przesłanych danych. Pozwoli to również na poprawne usunięcie błędu zduplikowanych komentarzy.

CMS:

- dodano możliwość przypisania [autorstwa (własności)](https://github.com/decred/politeia/pull/1135) propozycji, która zostanie wykorzystana w nadchodzących zmianach, aby właściciele propozycji mogli zobaczyć, co jest rozliczane w ramach ich wniosków
- dodano możliwość [dezaktywacji](https://github.com/decred/politeia/pull/1154) konta wykonawcy tymczasowego na fakturze, która wymaga zgody administratora w celu dopuszczenia go do rozliczenia w kolejnej fakturze
- prace nad redesignem rozpoczęte w październiku wreszcie zostały [scalone](https://github.com/decred/politeiagui/pull/1828). Ta duża zmiana dodaje 9K i kasuje 24K linijek kodu.

Za aktualizacjami wizualnymi, przeprojektowanie CMS zamyka [proces](https://matrix.to/#/!VFRvyndKpzcLrVslQD:decred.org/$158644942810878cUwaw:decred.org) migracji kodu politeiagui z biblioteki [snew classic-ui](https://github.com/decred/snew-classic-ui) do [pi-ui](https://github.com/decred/pi-ui). W 2018 roku snew pozwolił na szybkie wydanie Politei z redditopodobnym wyglądem i odczuciem, ale szybko stała się trudna do rozwijania w ten sposób. Zbudowanie pi-ui i przejście na nie poprawiło modularyzację kodu i dało elastyczność w komponowaniu i stylizowaniu komponentów UI w sposób, jaki był wymagany do dopasowania ich do specyfikacji projektowych, a także zwiększyło wydajność.


[dcrstakepool](https://github.com/decred/dcrstakepool):

- utrzymanie kodu celem poprawienia obsługi oraz anulowania błędów, dodano dokumentację, zaktualizowano zależności oraz dodano testy

[dcrpool](https://github.com/decred/dcrpool):

- wsparcie dla koparek [Obelisk DCR1](https://github.com/decred/dcrpool/issues/110)
- baza danych przeprowadza [backup](https://github.com/decred/dcrpool/pull/164) przed zamknięciem
- dodano [paginację](https://github.com/decred/dcrpool/pull/163) dla wydobytych bloków
- zrefaktoryzowano [kod połączenia](https://github.com/decred/dcrpool/pull/171), aby uprościć testowanie
- zwiększono pokrycie testami
- drobne usprawnienia w UX, konfiguracji oraz parę poprawek błędów
- powyższe prace są przygotowaniem do nadchodzącego wydania 1.1.0

[dcrlnd](https://github.com/decred/dcrlnd):

- ulepszenia w [systemie builda](https://github.com/decred/dcrlnd/pull/84)

Prace w toku:

- nowa paczka [chainscan](https://github.com/decred/dcrlnd/pull/83), która wykorzystuje dedykowane filtry do skuteczniejszego wykrywania transakcji istotnych dla węzła LN i może również działać w trybie SPV
- [implementacje](https://github.com/decred/dcrlnd/pull/92) dla paczek chainntnfs, które wykorzystują wbudowany i zdalny dcrwallet jako źródło wydarzeń łańcucha. Pozwala to na dalsze odseparowanie dcrlnd od bazowego dcrd, co jest wymogiem dla posiadania instancji dcrlnd działającej w trybie SPV.
- bazując na powyższym, możliwość włączenia i testowania [trybu SPV](https://github.com/decred/dcrlnd/pull/95) dla zdalnych portfeli („remote wallet” jest trybem połączenia, w którym dcrlnd łączy się z już uruchomioną instancją dcrwallet, tzn. nie potrzebuje własnego wbudowanego portfela z oddzielnym ziarnem)

> tryb SPV jest wymagany dla mobilnych portfeli LN. Jest prawdopodobne, że SPV będzie dominującym trybem synchronizacji nawet w portfelach stacjonarnych, więc niezbędne jest, aby dcrlnd obsługiwało tryb SPV. Jest to również ostatnia pozycja w sekcji prac „na już” w mojej swoistej „mapie rozwoju”, którą nakreśliłem w [poście ogłaszającym](https://matheusd.com/post/announcing-dcrlnd/) LN, więc jest to podsumowanie większości wysiłków związanych z portowaniem lnd do dcrlnd. Ukończenie prac nad SPV oznacza, że możemy zacząć badać bardziej egzotyczne zmiany, które są dostępne w Decred (takie jak [PTLC](https://suredbits.com/payment-points-monotone-access-structures/), które zależą od prac nad Schnorrem, które @davecgh również ma na ukończeniu). ([@matheusd](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$1586258547807544APZNe:matrix.org))

[dcrdex](https://github.com/decred/dcrdex):

- [aplikacja kontrola](https://github.com/decred/dcrdex/pull/181) wiersza polecenia dla klienta DEX
- możliwość [składania zleceń](https://github.com/decred/dcrdex/pull/195) za pośrednictwem wbudowanego w klienta graficznego interfejsu użytkownika
- tworzenie [kopii zapasowych i odtwarzanie](https://github.com/decred/dcrdex/pull/210) dla kluczy klientów i innych danych konta (wcześniejszy [PR #183](https://github.com/decred/dcrdex/pull/183) dodał kopię zapasową danych zamówień klienta)
- śledzenie przez klienta [zamówień z epoki](https://github.com/decred/dcrdex/pull/188) oraz weryfikacja [tasowania i dopasowywania](https://github.com/decred/dcrdex/pull/189) zamówień przeprowadzona pod koniec epoki
- obliczenia [współczynnika anulowania](https://github.com/decred/dcrdex/pull/206), które pozwalają serwerowi na niezawodne śledzenie zrealizowanych przez użytkownika zamówień w stosunku do anulowanych, z możliwością rekonstrukcji z bazy danych historii ostatnich zamówień dowolnego użytkownika. Jest to ważny element w egzekwowaniu pożądanych zachowań społeczności.
- refaktoryzacja i oczyszczenie bazy kodowej


Ważnym kamieniem milowym jest zakończenie [negocjacji dopasowań](https://github.com/decred/dcrdex/pull/213). Jest to ostatni duży kawałek klienta, który w końcu pozwala mu dokonać wymiany. Ten PR konkretnie sprawia, że klient przechodzi przez cały proces wymiany (match negotiation), komunikuje się z serwerem, dokonuje niezbędnego audytu transakcji drugiej strony transakcji (kontrahenta) oraz tworzy i przesyła własny kontrakt i transakcje wykupu zgodnie z wymogami procesu wymiany.

Łącznie scalono 19 pull requestów od 6 programistów, dodających 11K i usuwających 3K linijek kodu (podsumowanie commitów znajduje się [tutaj](https://github.com/decred/dcrdex/compare/94310f66c06fdf5ca31eeb80c9f6af7aecf4c31d...d3bd07f822200041092bdc85f5c1b752b3c9ee24)).

Gratulujemy zespołowi dcrdex za [koordynację](https://twitter.com/chappjc/status/1245075450625511425) pierwszego atomic swapa w wyniku zlecenia wymiany na testnet!

[dcrandroid](https://github.com/decred/dcrandroid):

- dodano [stronę statystyk](https://github.com/decred/dcrandroid/pull/440)
- ulepszenia UI i poprawki błędów

Testnetowa wersja następnego wydania dostępna jest [tutaj](https://play.google.com/apps/testing/com.decred.dcrandroid.testnet).

[dcrios](https://github.com/raedahgroup/dcrios):

- odnowiona [strona wysyłania](https://github.com/raedahgroup/dcrios/pull/557)
- nowy interfejs użytkownika dla [menu „więcej”](https://github.com/raedahgroup/dcrios/pull/559)
- nowy widżet [wyboru portfela](https://github.com/raedahgroup/dcrios/pull/600) dla strony „transakcje”
- odczytywanie ilości DCR z [kodów QR](https://github.com/raedahgroup/dcrios/pull/581)
- poprawki wielu błędów oraz usprawnienia interfejsu użytkownika

Testnetowa wersja następnego wydania dostępna jest [tutaj](https://testflight.apple.com/join/7KL4VnB2).

[dcrdata](https://github.com/decred/dcrdata):

- URL dla danych do wykresów w [surowym formacie JSON](https://github.com/decred/dcrdata/pull/1716), o który często pytacie, został dodany do strony wykresów
- drobne usprawnienia i poprawki błędów

[tinydecred](https://github.com/decred/tinydecred):

- [widok stakingu](https://github.com/decred/tinydecred/pull/53) pokazuje bilety w stanach: wydany (spent), niewydany (unspent) oraz gotowy do głosowania (live)
- prosty [widok kont](https://github.com/decred/tinydecred/pull/94)
- proste [widoki](https://github.com/decred/tinydecred/pull/125) tworzenia kont oraz wysyłania DCR
- [odkrywanie kont](https://github.com/decred/tinydecred/pull/124)
- zmieniono testy na wykorzystujące bazy danych [in-memory](https://github.com/decred/tinydecred/pull/116)
- zwiększono całkowite pokrycie testami [do 98%](https://github.com/decred/tinydecred/issues/70#issuecomment-606669036) oraz naprawiono przy tej okazji parę błędów; na wszystkie pliki jest obecnie 94% pokrycia testami

Łącznie scalono 56 pull requestów od 3 programistów, dodających 11K i usuwających 6K linijek kodu (podsumowanie commitów znajduje się [tutaj](https://github.com/decred/tinydecred/compare/fa081e7f17d303f0eea31e9f07499db4e0acc53a...e1ef1ff72cb924d27098f9df151f6805d5db3e90)).

[docs](https://github.com/decred/dcrdocs):

- dokumentacja [dcrlnd](https://docs.decred.org/lightning-network/overview/) została [zaktualizowana](https://github.com/decred/dcrdocs/pull/1083) do najnowszego wydania 0.2.1, polecenia zostały pogrupowane w kategorie
- dodano [poradnik](https://docs.decred.org/getting-started/joining-matrix-channels/) na temat tego, jak dołączyć do [Matrixa](https://github.com/decred/dcrdocs/pull/1081)
- strona „inflacja” została [przemianowana](https://github.com/decred/dcrdocs/issues/1074) na [„emisja”](https://docs.decred.org/advanced/issuance/), aby uniknąć dwuznaczności
- [udokumentowano](https://github.com/decred/dcrdocs/pull/1073) dostęp do serwera CoinShuffle++ jako [ukrytej usługi Tor](https://docs.decred.org/privacy/cspp/how-to-cspp/#tor-hidden-service)

[decred.org](https://github.com/decred/dcrweb):

- fala generalnych poprawek naprawiających drobniejsze problemy z nową stroną
- zaktualizowano [treść strony](https://github.com/decred/dcrweb/pull/853) VSP
- strona rekrutacji została usunięta, a decred.org/recruiting od teraz przekierowuje do strony [wnoszenia wkładu](https://docs.decred.org/contributing/overview/)
- usunięto stronę [mapy rozwoju](https://github.com/decred/dcrweb/pull/857)

Pozostałe:

- większość projektów została zaktualizowana, aby budować się na Go 1.14 i porzuciła wsparcie dla Go 1.12
- @mm wypuścił na świat DigiSign Oracle, darmową aplikację webową typu open source, która pomaga użytkownikom w weryfikacji podpisów cyfrowych. Narzędzie to zostało stworzone, aby pomóc użytkownikom Decred w weryfikacji podpisów paczek bez konieczności korzystania ze skomplikowanych narzędzi wiersza polecenia. Można z niego skorzystać po wejściu na stronę [stakey.club](https://stakey.club/digisign-oracle/) lub pobrać [kod źródłowy](https://github.com/mmartins000/digisign-oracle) na swój komputer i odpalić go w przeglądarce.


## Plany co do wersji v1.6

> Generalny plan dla wersji v1.6 to wypuszczenie jej pod koniec 2. kwartału. Planujemy zawrzeć w niej: zmianę zasad konsensusu odnośnie decentralizacji wydatków ze Skarbca, wsparcie CSPP w Decreditonie przez staking oraz bez niego, bezkontowe wsparcie biletów u VSP, oraz całą masę usprawnień dcrd. (@jy-p dn. [2020-03-20](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15855719584400kpyNr:decred.org))

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: @unimere ([decrediton](https://github.com/decred/decrediton/commits?author=unimere)).

Statystyki społeczności:

- Obserwujący na Twitterze: 40 694 (-207)
- Subskrybenci na Reddit: 9760 (+22)
- Użytkownicy na Matrixie: 601 (+36)
- Użytkownicy na Discordzie: 1160 (+73), zweryfikowani z możliwością pisania postów: 479 (+29)
- Użytkownicy na Telegramie: 2607 (-71)
- Subskrybenci na YouTube: 3980 (-10)
- Obserwujący na Facebooku: 3606 (+26), polubień: 3273 (+24)
- Obserwujący na LinkedIn: 744 (+25)
- GitHub: 536 gwiazdek (+1) i 1507 forków repozytorium dcrd (+11)

## Zarządzanie

W marcu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 13 713 DCR i wydał 17 153 DCR. Stosując średni dzienny kurs DCR/USD z marca w wysokości 13,48 USD, do Skarbca wpłynęło 184 tys. dolarów, a wydano z niego 230 tys. dolarów. Przy średnim dziennym kursie lutowym wynoszącym 20,48 USD, kwota dolarowa naliczona za prace wykonane w tym miesiącu wynosi 281 tys. dolarów. Na dzień 3 kwietnia saldo Skarbca wynosi 640 tys. DCR (7,41 mln USD po kursie 11,58 USD).

W tym miesiącu opublikowane zostały 4 nowe propozycje.

Nowa [propozycja](https://proposals.decred.org/proposals/2f08f8518bc7672069a10ac6461fd9ab341d4a9e4c343fd4a7ec426250f3896f) od zespołu DCRComic prosi o zwiększenie budżetu do 16 200 USD na 12 kolejnych komiksów plus działalność wspierającą, z dodatkowym 150 USD na każdy komiks za dodatkowy czas poświęcony na dostosowanie zasobów do wykorzystania w mediach społecznościowych. Propozycja ta została [odłożona na później](https://twitter.com/DCRComic/status/1243197581104041984), aby przeformułować obsadę postaci, po tym, jak pojawiła się pewna krytyka, że Stakey był nadmiernie wykorzystywany do reprezentowania wielu różnych ról w ekosystemie Decred. W dniu 6 kwietnia br. wniosek został zredagowany w celu dodania nowych [postaci](https://github.com/pLabarta/dcrwebcomic/blob/master/Proposal2/NewChars.md), które dołączą do składu obok Stakey'ego, a w dniu 9 kwietnia rozpoczęto nad nim głosowanie.

Propozycja [marketingu w USA](https://proposals.decred.org/proposals/c830ea5afea45a0aabf4092d1bea51fb10b8bfa2d8474aac03224f0f94d3d1af), po redukcji budżetu do 177 800 dolarów w celu usunięcia wydarzeń organizowanych przez społeczność w świetle COVID-19, została zatwierdzona przy 74% poparciu i 31% frekwencji.

Zatwierdzono także propozycję [marketingu w Brazylii](https://proposals.decred.org/proposals/bc20f986c3ea2fed2ea074c377a89f1a4b956ea0d527a8b6c099a5a8f175beb5), która wnosi o 108 tys. dolarów na resztę roku 2020, przy 65% poparciu i frekwencji wyborczej na poziomie 34%. Propozycja ta została zredagowana w taki sposób, aby powiedzieć, że wydarzenia nie będą organizowane lub rozliczane w czasie trwania sytuacji związanej z COVID-19, ale pozycja ta nie została usunięta z budżetu, a niektóre z tych działań mogą odbyć się w późniejszym okresie.

Złożono dwa kolejne wnioski, które są obecnie przedmiotem dyskusji. Propozycja [aplikacji Polis Pay](https://proposals.decred.org/proposals/d3b16861a7e555db2fdd25b589123f4b6c4289c857fbdff329a4ffb1cb60c4d9) wnosi o 5000 dolarów na wdrożenie wsparcia dla DCR. Jest także [propozycja](https://proposals.decred.org/proposals/7d42c6f4bf3059b64789185af615c1df97cb61a379425933be5ff01d074ed4d5) sfinansowania [konta twitterowego Decred Daily](https://twitter.com/Decred_Daily) na 6 miesięcy i stworzenie dla niego strony internetowej (całkowity budżet 5280 USD). Głosowanie nad propozycją Decred Daily rozpoczęło się 9 kwietnia.

Na krótko przed publikacją 9 kwietnia opublikowano kolejną propozycję, wnioskującą o 24 450 dolarów na [billboardową kampanię marketingową](https://proposals.decred.org/proposals/bce7bf3cd1f74d571d23ac8a330ddf29a14a547ed0cc9c995f1a97dce733d1e1).

Propozycja animatora rynku (market making) złożona przez i2 Trading zbliża się do końca przewidzianego dla niej sześciomiesięcznego okresu aktywności, który rozpoczął się pod koniec października 2019 r., a więc zakończy się pod koniec kwietnia 2020 r. Dzienniki transakcyjne i2 są nadal sprawdzane co miesiąc przez Company 0, a wyniki aktywności zostały uznane za zadowalające. i2 planuje złożyć propozycję kontynuacji działalności MM dla Decred, ale zostanie ona zmniejszona w celu odzwierciedlenia obecnych warunków rynkowych.

Aby uzyskać więcej informacji na temat działalności na platformie Politeia z marca zajrzyjcie do [wydania 29](https://blockcommons.red/politeia-digest/issue029/) Politeia Digest.

## Sieć

Hashrate: [marcowy hashrate](https://explorer.dcrdata.org/charts?chart=hashrate&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) na początku miesiąca wyniósł ~359 Ph/s, a zamknął miesiąc w ok. 309 Ph/s, zaliczając niż w ok. 274 Ph/s oraz szczyt w wys. 556 Ph/s w ciągu miesiąca. [Dystrybucja mocy obliczeniowej](https://dcrstats.com/pow) na 1 kwietnia wyglądała następująco: UUPool 55%, Poolin 18%, lab.antpool.com 17%, Luxor 2,5%, BTC.com 2,2%, F2Pool 1,5%, BeePool 0,13%, CoinMine 0,08%, Suprnova 0,02% i pozostałe ok. 3,8%. Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu [z okresu 30 dni](https://dcrstats.com/) wynosiła 141,9 DCR (+9,8). [Cena](https://explorer.dcrdata.org/charts?chart=ticket-price&zoom=k73pwcch-k8jayo3s&bin=window&axis=time) wahała się między 130,9-166,8 DCR. [Zablokowana kwota](https://explorer.dcrdata.org/charts?chart=ticket-pool-value&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) wynosiła 5,50-5,75 mln DCR, co odpowiadało 49,05-51,27% dostępnej podaży [biorącej udział](https://explorer.dcrdata.org/charts?chart=stake-participation&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) w elemencie PoS.

Cena biletów osiągnęła maksimum w wys. 166,82 DCR, co stanowi kolejny szczyt od czasu zmiany algorytmu trudności stakingu.

Rozmiar bloków: W tym miesiącu blockchain powiększył się o 129 MB. Średni [rozmiar bloków](https://explorer.dcrdata.org/charts?chart=block-size&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) wynosił 14.5 KB. Najmniejszy blok miał rozmiar 1.62 KB, a największy 374.98 KB. Do tej pory najczęstszym źródłem pełnych bloków są transakcje wypływające ze Skarbca: w tym miesiącu wypłata z niego całkowicie wypełniła 9 bloków dn. [16 marca](https://explorer.dcrdata.org/blocks?height=432590&rows=20).

Transakcje: W marcu użytkownicy Decred dokonali 49 078 zwykłych transakcji oraz zakupili 44 149 biletów. 43 791 bilety zostały nagrodzone za głosowanie, a 728 zostało odwołanych. Średnio każdego dnia odbywało się 1583 zwykłe transakcje DCR oraz zakup 1424 nowych biletów.

Węzły: przez [marzec](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1583020800000&to=1585699200000) było około 146 węzłów nasłuchujących i 246 w sumie za danymi z dcr.farm. Średnia dystrybucja wersji na marzec wygląda następująco: 28% korzysta z dcrd v1.5.1, 20% to dcrd v1.4, 15% używa dcrd v1.5, 8% korzysta z dcrd v1.5 w wersji deweloperskiej i buildów RC, 5% korzysta z dcrd v1.6 w wersji deweloperskiej, 5% to dcrwallet v1.5.1, 5% używa dcrwallet v1.4, a 2% korzysta z dcrwallet v1.5. 13 marca wezły w życie nowe zasady konsensusu sieci, po czym węzły w wersji v1.4 nie śledzą już głównego łańcucha.

## Integracje

Probit [dodał](https://twitter.com/ProBit_Exchange/status/1235450770100649986) wsparcie dla par walutowych DCR/KRW i DCR/USDT do swojej giełdy wymian.

Giełda Exmo.com doświadczyła nagłego [przestoju](https://twitter.com/Exmo_Com/status/1240255377507303431) usług DCR kilka dni po hard forku z 13 marca; usługi [wznowiono](https://twitter.com/Exmo_Com/status/1240627750005870592) następnego dnia. Obecnie Exmo jest jedyną integracją [finansowaną](https://proposals.decred.org/proposals/950e8149e594b01c010c1199233ab11e82c9da39174ba375d286dc72bb0a54d7) przez interesariuszy Decred.

Procesor płatności [NOWPayments](https://nowpayments.io/) uruchomiony w 2019 r. przez ChangeNOW, od teraz wspiera DCR wśród [40+](https://nowpayments.io/supported-coins/) innych aktywów.

ChainRift [ogłosiło](https://twitter.com/ChainRift/status/1228010062163202049) w lutym, że zamyka działalność giełdową i przekształca się w firmę związaną z rozwojem oprogramowania.

DCR zostało [dodane](https://twitter.com/Checkmatey/status/1244030247558729729) do indeksu kontraktów przyszłościowych FTX PRIV-PERP, który śledzi koszyk 9 monet z funkcją ochrony prywatności. Obliczenia indeksu można znaleźć [tutaj](https://help.ftx.com/hc/en-us/articles/360027668812-Index-Calculation).

Użytkownik AGspearo stracił dostęp do swoich [funduszy](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/) z powodu zamknięcia VSP d1pool.com bez uprzedzenia i braku dostępu do skryptu wykupu (redeem script). AGspearo spędził wiele czasu na kanale wsparcia próbując rozwiązać ten problem, ale ostatecznie nie udało im się uzyskać dostępu do swoich funduszy. @davecgh opisał problem w [komentarzu](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/fkiac45) i powiedział, że ewentualna zmiana zasad konsensusu może rozwiązać te [problemy](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/fkku35k). Jeśli czytacie to i nie macie kopii zapasowej swoich skryptów wykupu, posłuchajcie tego ostrzeżenia i zróbcie [kopię](https://docs.decred.org/wallets/decrediton/using-decrediton/#backup-redeem-script), a następnie schowajcie ją i przechowujcie bezpiecznie wraz z ziarnem portfeli.

Niektóre VSP, których strony zapisu były popsute, przeterminowane, lub wypluwały błędy zapisu/zwrotu, zostały [powiadomione](https://github.com/decred/dcrwebapi/pulls?q=is%3Apr+author%3Ajholdstock+created%3A2020-03-01..2020-03-31), że zostaną usunięte z [listy](https://decred.org/vsp/) VSP. Niektóre z nich odpowiedziały i naprawiły problemy. raqamiya.net, tokensmart.io, oraz dcrpos.idcray.com zostały usunięte, ponieważ nie odpowiedziały na komunikat.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

Podcast [Decred in Depth](https://decredindepth.libsyn.com) wypuścił w marcu dwa nowe odcinki i jeden na początku kwietnia, podczas gdy [Rough Consensus](https://roughconsensus.libsyn.com/) również uraczył nas dwoma nowymi epizodami (więcej w sekcji [media](#media) poniżej).

@Dustorf [ogłosił](https://proposals.decred.org/proposals/c830ea5afea45a0aabf4092d1bea51fb10b8bfa2d8474aac03224f0f94d3d1af/comments/56), że w ciągu najbliższych kilku miesięcy będzie wykonywał powierzoną mu funkcję w ograniczonym zakresie i że budżet jego propozycji zostanie odpowiednio zmniejszony, aby odzwierciedlać tę zmianę. Zmiana dotyczy m.in.: biuletynu informacyjnego, generowania oryginalnych treści, Decred Assembly, koordynacji działań w zakresie PR i procesu wydawniczego oprogramowania oraz prac aktualizacyjnych. Oznacza to w szczególności, że nad koordynacją wydania DEX będzie musiała pracować cała społeczność wraz z deweloperami.

@dezryth [zamieścił](https://scottrchristian.com/2020/03/15/dezryth-proposal-updates/) drugą aktualizację dotyczącą działania konta Decred na Facebooku w lutym. Ta jest bardziej szczegółowa i zawiera statystyki dla każdego postu, porównanie z konkurencją, oraz dzieli się kilkoma pomysłami na kolejne kroki. @dezryth przyznaje, że obecne statystyki nie powalają i że zbudowanie organicznej społeczności jest trudne, ale dobrą stroną aktywnego postowania jest to, że o 30% wzrosła liczba dziennych odsłon zamieszczanych treści.

@bee (naprawdę) obszernie [skomentował](https://www.reddit.com/r/decred/comments/fa70c3/decred_2019_marketing_report/) raport marketingowy za rok 2019 i podzielił się swoją wizją rozwoju.

Do wiki decredcommunity dodano kompleksową kompilację [powszechnych błędnych wyobrażeń](https://github.com/decredcommunity/wiki/blob/master/wiki/misconceptions.md) i krytyki pod adresem projektu Decred wraz z odpowiedziami na nie. Mile widziana jest krytyka oraz komentarze, a dyskusja znajduje się [tutaj](https://www.reddit.com/r/decred/comments/frqkt0/your_favorite_misconceptions_about_decred_in_one/).

PR-owe osiągnięcia Monde za marzec:

- nawiązanie kontaktów z, oraz przedstawienie projektu docelowym dziennikarzom
- promocja komentarzy w odpowiedzi na aktualne newsy
- zgłoszenie komentarzy od przedstawicieli projektu Decred do 7 artykułów
- promocja Decred w 3 nadchodzących oryginalnych artykułach
- zgłoszenie pionierskiego artykułu @richardred do ValueWalk
- zaklepanie 2 wywiadów z mediami

Obecność w mediach dzięki Monde PR:

- [artykuł](https://cointelegraph.com/news/proof-of-stake-vs-proof-of-work-which-one-is-fairer) w Cointelegraph z komentarzem @jy-p w temacie modeli konsensusu
- [artykuł](https://www.financemagnates.com/cryptocurrency/news/fintech-experts-share-tips-for-remote-work-during-coronavirus-quarantine/) w Finance Magnates zawierający komentarz @richardred w temacie pracy zdalnej
- [artykuł](https://www.coindesk.com/remote-working-proves-unexpected-hero-as-half-of-us-economy-shifts-to-home-offices) w CoinDesk z komentarzem od @jy-p w temacie szybkiej skalowalności, który rozpowszechniony został też do i przez Yahoo Finance

## Eventy

Na których byliśmy:

- 4 marca - [Meetup Decred](https://www.eventbrite.com/e/decred-meetup-la-plata-tickets-95666770887) - La Plata, Argentyna. Było to wprowadzenie do projektu Decred, w którym @camilolwi, @tomee i @pablito mówili o podstawach związanych z Decred, jego bezpieczeństwie i hybrydowym modelu konsensusu, zarządzaniu, głosowaniu i tym, jak zostać wykonawcą projektu. W spotkaniu i sesji networkingowej wzięło udział około 20 osób. ([zdjęcia](https://twitter.com/cryptorc_tech/status/1238180910513733634))
- 4 marca - [Meetup Decred](https://www.eventbrite.com/e/decred-en-uninet-business-school-caracas-venezuela-tickets-97157792573) - Caracas, Wenezuela. Spotkanie było współorganizowane przez Uninet Business School i Innova Consultants. W spotkaniu wzięło udział 15 uczestników, odbyło się wprowadzenie do Decred, jego bezpieczeństwa i modelu hybrydowego, prywatności, sposobu, w jaki można wnieść swój wkład, a następnie sesja pytań i odpowiedzi oraz networkingu. ([zdjęcia](https://twitter.com/Decred_ES/status/1235324847338795009))
- 4 marca - [Crypto and Blockchain 2020 and Beyond](https://www.meetup.com/BC-Aus/events/268793182/) - Melbourne, Australia. To 80+ osobowe wydarzenie przeznaczyło opłaty wejściowe na Crypto Fire Alliance, aby pomóc w katastrofie związanej z pożarem buszu (zebrano $1K, podczas gdy cały program [zebrał](https://www.finder.com.au/crypto-bushfire-fundraiser) $27K w krypto). @eSizeDave dołączył do godzinnego panelu dyskusyjnego, [stwierdzając](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158381267934685XUpiS:decred.org): „publiczność miała do mnie więcej pytań niż do kogokolwiek innego, w wyniku czego odbyło się wiele kolejnych spotkań". ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200304-crypto-and-blockchain-2020-and-beyond-melbourne-australia.md), [wideo](https://twitter.com/DecredAustralia/status/1235390840307978245))
- 5 marca - [Meetup Decred](https://www.eventbrite.com/e/decred-meetup-en-valencia-venezuela-tickets-97804334397) - Valencia, Wenezuela. Współprowadzone przez ClicTechNova y CoWorking Lab. Spotkanie było wprowadzeniem do ekosystemu Decred, jego hybrydowego blockchaina, mechanizmu zarządzania, prywatności i elementów, które sprawiają, że Decred jest DAO. Obecnych było ~50 uczestników, którzy zadawali interesujące pytania dotyczące ataków społecznych na sieć, sposobów wnoszenia wkładu oraz modelu motywacyjnego DCR. ([zdjęcia](https://twitter.com/Decred_ES/status/1236079742643773440), [wideo](https://twitter.com/Decred_ES/status/1236080559752916998))
- 6 marca - [Impact Hub](https://www.eventbrite.com/e/decred-meetup-impact-hub-caracas-venezuela-tickets-97159680219) - Caracas, Wenezuela. Współgospodarzem było El Dorado y Cointigo. Spotkanie było wprowadzeniem do ekosystemu Decred, jego struktury zarządzania i tego, co odróżnia Decred od reszty kryptowalut. W spotkaniu wzięło udział około 30 osób, kilku przedsiębiorców i deweloperów, ale także kilku nowych użytkowników kryptowalut, którzy szukali więcej informacji na temat technologii i możliwości inwestycyjnych. ([zdjęcia](https://twitter.com/Decred_ES/status/1236337867095343104), [wideo](https://twitter.com/Decred_ES/status/1236340242698752001))
- 8 marca - [Międzynarodowy Dzień Kobiet](https://www.meetup.com/GDGCasablanca/events/268661463/) - Casablanca, Maroko. Impreza odbyła się w ENSAM, Uniwersytecie Naukowym. Większość z 70 uczestników to studenci i programiści data science. @arij wygłosiła 1-godzinną prezentację na temat technologii blockchain i Decred, a następnie odbyły się warsztaty: „Z moich doświadczeń z rozmów i wyjaśniania technologii blockchain i Decred dowiedziałam się, że ludzie są bardziej zainteresowani, gdy pokazujesz im, jak niektóre rzeczy naprawdę działają poprzez dema i filmy wideo, zwłaszcza gdy słyszą o czymś po raz pierwszy". ([uwagi](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158374584733992NOIMZ:decred.org), [zdjęcia](https://www.flickr.com/photos/187387360@N04/albums/72157713440754483))
- 12 marca - [Bitcoin - jak kobieta kobiecie](https://twitter.com/bitcoinemb/status/1233500964566523911) - Mexico City, Mexico. Współorganizowane przez Bitcoin Embassy, ~30 osób spotkało się w celu przedyskutowania zaangażowania kobiet w branżę kryptowalutową oraz tego, jak dać kobietom narzędzia i zachęcić do kobiety do korzystania z krypto. @francov\_ zrobiła prezentację na temat tego, jak wnieść wkład w projekt Decred i jej doświadczenia w pracy w branży. „Najważniejszym punktem wystąpienia było wyrażenie, że nie potrzebujemy twojego tytułu naukowego, płci, narodowości, wieku, a nawet twojego prawdziwego imienia, a jedynie tylko twojego talentu i aspiracji, aby pomóc w rozwoju ekosystemu Decred". Po spotkaniu odbyła się sesja networkingowa. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200312-bitcoin-woman-to-woman-mexico-city-mexico.md))
- 12 marca - [Meetup Decred](https://www.meetup.com/es-ES/BitcoinBlockchainUruguay/events/269160706/) - Montevideo, Urugwaj. W spotkaniu wzięło udział około 25 osób. @tomee zaprezentował wprowadzenie do Decred i jego bezpieczeństwa, adaptacyjności i samofinansowania się, platformy Politeia, zarządzania i sposobu wnoszenia wkładu. Spotkanie było również sesją networkingową, a niektórzy uczestnicy znali już projekt z Labitconf. (zdjęcia: [1](https://twitter.com/ivarese/status/1238628854379536389), [2](https://twitter.com/cryptorc_tech/status/1241081659669315585))
- 12 marca - [Blockchain Summit Latam](https://twitter.com/Decred_ES/status/1237552322596593665) - Panama City, Panama. Wydarzenie zostało przesunięte na 15-16 października, ale zmiana ta nastąpiła 24 godziny przed wydarzeniem, kiedy niektórzy prelegenci byli już w okolicy (~35 osób). Organizatorzy wydarzenia skorzystali z okazji i zorganizowali małe spotkanie, na którym prezenterzy mieli okazję nawiązać kontakty i bardziej bezpośrednio dowiedzieć się o projektach. @adcade i @elian rozmawiali z kilkoma przedstawicielami i udzielili [wywiadu](https://es.cointelegraph.com/news/decred-how-does-your-development-continue-during-the-bear-market) dla hiszpańskiego Cointelegrapha. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200312-blockchain-summit-latam-meetup-panama-city-panama.md))
- 12 marca - [Hablemos Decred 01](https://twitter.com/Decred_ES/status/1238242352306614273) - Internet. „Porozmawiajmy o Decred”, pierwsze hiszpańskie spotkanie online odbyło się na decredowym serwerze Discord. Większość pytań dotyczyła systemu głosowania PoS w projekcie Decred. Ci, którzy mieli już wstępną wiedzę na temat krypto zaciekawieni byli stakingiem, a ci, którzy takiej wiedzy nie mieli, chcieli wiedzieć więcej o prawach do głosowania i o tym, na co interesariuszom pozwalają ich bilety. Około jedna trzecia z ~15 osób nie miała wcześniej styczności z projektem. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200312-hablemosdecred-01-internet.md))
- 18 marca - [Giełdy wymian w Ameryce Łacińskiej](https://twitter.com/Decred_ES/status/1240428280756310018) - Internet. @elian mówił o scentralizowanych i zdecentralizowanych giełdach wymian w wirtualnym spotkaniu z ludźmi z [@AvaLatam](https://twitter.com/AvaLatam), [@blockchain_land](https://twitter.com/blockchain_land) i virica.io Mexico. W spotkaniu wzięło udział około 16 osób, a jednym z wniosków płynących ze spotkania było to, że spotkania i prezentacje online powinny trwać 30 minut lub mniej.
- 24 marca - [Webinar Decred](https://www.meetup.com/es-ES/blockacademycl/events/269108758/) - Internet. @tomee i @camilolwi rozmawiali o wszystkich rzeczach związanych z Decred i wyzwaniach związanych ze zdecentralizowanym zarządzaniem blockchainem w ramach webinaru współorganizowanego z Blockchain Academy Chile. ([wideo](https://www.youtube.com/watch?v=U07ZL_qFAQM))
- 27 marca - [Hablemos Decred 02](https://twitter.com/Decred_ES/status/1243214184793485314) - Internet. Drugie hiszpańskie spotkanie online skorzystało z Jitsi, aby połączyć ze sobą 13 uczestników z Argentyny, Meksyku, Boliwii, Chile, z czego dla 7 było pierwsze zetknięcie z projektem. Tym razem spotkanie rozpoczęło się od wstępu do Decred, później przeszło do demo portfela Decrediton i oraz otwartej sesji pytań i odpowiedzi wraz z komentarzami. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200327-hablemosdecred-02-internet.md))
- 29 marca - [Binance AMA](https://twitter.com/Decred_ES/status/1244360357843533825) - Internet. Impreza została zorganizowana na hiszpańskiej grupie telegramowej Binance z udziałem ponad 8000 członków i odnotowała wysoki poziom zaangażowania. @adcade, @elian, i @pablito otrzymali 155 pytań od 73 uczestników, a autorzy najlepszych pytań zostali nagrodzeni 0,333 DCR. Pytania zasugerowały potencjalne zakresy wiedzy, o których wypełnienie można się w przyszłości pokusić, aby ułatwić nowicjuszom zrozumienie założeń oraz mechaniki projektu. Było to drugie decredowe AMA za pośrednictwem Binance i najdłuższe AMA, jakie zorganizowali do tej pory (~2,5 godziny). ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200329-decred-ama-binance-spanish-community-internet.md))
- 30 marca - [Wirtualny meetup w temacie Decred i solidnego pieniądza](https://www.meetup.com/Decred-Australia/events/269640276/) - Internet. Wydarzenie zostało zorganizowane przez @eSizeDave i @zohand, a dołączył do niego @Checkmate, aby omówić kluczowe tematy, takie jak solidny pieniądz, środowisko makroekonomiczne, złoto i Decred. Uczestnicy byli pod dużym wrażeniem jakości i pozostawili pochlebne, jeden z nich cieszył się z faktu, że spotkanie było „umysłowo stymulujące". ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200330-decred-and-sound-money-internet.md))

Odwołane:

- 5 kwietnia - [Toronto Blockchain Week](https://www.eventbrite.ca/e/discover-decred-an-autonomous-digital-currency-toronto-blockchain-week-tickets-91562362491) - Toronto, Kanada.

Na których będziemy:

- 13-17 kwietnia - [Jalisco Talent Land @ Home](https://www.talent-land.tv/) - Internet. W panelu zatytułowanym „Decred, krypto i przyszłość pieniędzy” zespół Decred z Ameryki Łacińskiej przedstawi krótki opis Decred i zbada, jak krypto przeobrazi zdalną pracę i naszą interakcję z pieniędzmi. Panel będzie transmitowany na stronie [talent-land.tv](https://www.talent-land.tv/) 15 kwietnia, 21:00 (CST, UTC-5).
- 16 kwietnia - [Webinar Decred](https://twitter.com/Decred_ES/status/1245452957417684992) - Internet. Tematem będzie „Porozmawiajmy o kryptowalutach i przyszłości pieniędzy” - webinar prowadzony przez Ibero (uniwersytet), celem omówienia tematyki krypto oraz wprowadzenia do projektu Decred.
- 14 maja - [BlockConf](https://blockconf.digital/) - Internet. Zespół Decred z Ameryki Łacińskiej poprowadzi dla Decred wirtualne stoisko, aby odpowiedzieć na pytania od uczestników. Jeśli ktoś chce pomóc w utrzymaniu aktywności stoiska w kilku strefach czasowych podczas 48-godzinnego wydarzenia, prosimy o kontakt z @elian.
- 30-31 maja - [Bitconf](https://www.bitconf.com.br/portal/) - São Paulo, Brazylia. Decred będzie prowadził wiele prezentacji na różne tematy.
- Czerwiec lub później - [Campus Party Amazonia](https://brasil.campus-party.org/campus-party-amazonia-2020/) - Manaus, Brazylia. Wydarzenie przeniesione z marca.
- Czerwiec lub później - [Jalisco Talent Land](https://www.talent-land.mx/en/home/) - Guadalajara, Meksyk. Event przeniesiony z kwietnia.
- Koniec 2020 roku - [DevOpsDays](https://devopsdays.org/events/2020-natal/welcome/) - Natal, Brazylia. Wydarzenie przeniesione z marca.

Przesunięte do odwołania:

- [CIBTC Blockchain Summit](http://cibtc.es/) - Motril, Hiszpania.
- Meetup Decred - La Paz, Bolivia.
- [Bitcoinference](https://www.eventbrite.com/e/bitcoinference-where-the-blockchain-meets-you-tickets-94598812595) - Cancún, Meksyk.

## Media

Strona [decredpower.info](https://decredpower.info/) to nowy jednostronicowy spis katalogujący wszystko związane z projektem Decred. Zapraszamy do składania sugestii odnośnie treści [tutaj](https://github.com/raedahgroup/decredpower/issues).

Wybrane artykuły:

- Obserwując zarządzanie w Ethereum podczas debaty nad ProgPoW, aut. @Checkmate ([medium](https://medium.com/@_Checkmatey_/observing-ethereum-governance-during-the-progpow-debate-9bf1aec724ad))
- Ryzyko w krypto nie jest tym, czym myślisz, aut. @Dustorf ([medium](https://medium.com/@dlefebvr/crypto-risk-is-not-what-you-think-8a2662840b70))
- Teoria trzech filarów w cypherpunkowym kontrakcie społecznym, aut. @Cato\_io ([medium](https://medium.com/@cato_io/threepillarstheory-cd6b57c5d88a))
- Usługi publiczne, pandemie i sieci kryptograficzne, aut. @mrbulb ([medium](https://medium.com/@decentpartners/public-service-pandemics-and-crypto-networks-379dce1594d1))
- Decred: a jak u Was przebiega rozwój podczas rynku niedźwiedzia? aut. @adcade (w jęz. hiszpańskim, [es.cointelegraph.com](https://es.cointelegraph.com/news/decred-how-does-your-development-continue-during-the-bear-market))

Propozycja [brazylijskiego marketingu i wydarzeń](https://proposals.decred.org/proposals/bc20f986c3ea2fed2ea074c377a89f1a4b956ea0d527a8b6c099a5a8f175beb5) została przedstawiona w mediach z ciekawej perspektywy „inwestycji w Brazylię” (w jęz. portugalskim):

- „Społeczność Decred zatwierdza inwestycję w Brazylii na ponad 500 000 BRL” ([criptofacil.com](https://www.criptofacil.com/comunidade-decred-permite-que-mais-r-500-mil-sejam-investidos-brasil/))
- „Kryptowaluta zainwestuje ponad pół miliona w Brazylii” ([livecoins.com.br](https://livecoins.com.br/criptomoeda-vai-investir-mais-meio-milhao-brasil/))
- „Wieloryby' dają zielone światło, więc Decred może zainwestować ponad 500 000BRL w promocję kryptowalut w Brazylii” ([cointelegraph.com.br](https://cointelegraph.com.br/news/decred-pode-investir-ate-us-500-mil-para-promover-criptomoeda-no-brasil)) - ten artykuł jest słabo napisany i opiera się na innym wywiadzie (@emiliomann)
- „Kryptowaluty najbardziej inwestujące w Brazylii” ([cointimes.com.br](https://cointimes.com.br/as-criptomoedas-que-mais-investem-no-brasil/))

Tłumaczenia:

- Teoria trzech filarów w cypherpunkowym kontrakcie społecznym - [w jęz. hiszpańskim](https://medium.com/decred-es/teor%C3%ADa-de-los-tres-pilares-en-el-contrato-social-del-cypherpunk-40f569836b6a), aut. @francov\_
- Brief techniczny Decred - [w jęz. arabskim](https://insaf01.github.io/decred-arabic/articles/decred-technical-brief-ar.html), aut. @arij
- Wydanie Decred Journal z lutego 2020 przetłumaczone zostało na jęz. arabski (@arij), jęz. chiński (@Dominic) oraz jęz. hiszpański (@francov\_). Wszystkie wersje językowe przechowywane są za pośrednictwem [Gita](https://github.com/xaur/decred-news/blob/docs/guidelines.md#why-git), co pomaga w długoterminowym przechowywaniu oraz chroni treści przed cenzurą. Dziękujemy Wam wszystkim za głoszenie dobrej nowiny!

Wideo:

- Analiza propozycji marketingu i publikacji Decred dla USA i Brazylii na rok 2020, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=Liol1lLCinQ))
- Dwutygodniowy update wiadomości Decred - 12 marca, 2020, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=N4U1FwYUaKA))
- Dwutygodniowy update wiadomości Decred - 31 marca, 2020, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=MBi7d263HvE))
- 5 najlepszych monet do stakingu w roku 2020, aut. Coin Bureau ([youtube](https://www.youtube.com/watch?v=znx7H7JWtfg))

Audio:

- Decred in Depth, odc. 19 - Leo Zhang z Iterative Capital mówi o wydobyciu Proof of Work, z pierwszej ręki przedstawia sytuację ekonomii górnictwa i rozważa korzyści płynące z hybrydowego komponentu PoS i formalnego podejmowania decyzji przez interesariuszy. ([libsyn](https://decredindepth.libsyn.com/leo-zhang-dcr-mining), [youtube](https://www.youtube.com/watch?v=iWi3nK0HIHE), [soundcloud](https://soundcloud.com/decredindepth/leo-zhang-dcr-mining))
- Decred in Depth, odc. 21 - @Exitus mówi o produkcji treści wideo dla DAO Decred, zostaniu wykonawcą i wyzwaniach stojących przed marketingiem w sferze krypto podczas trwającego rynku niedźwiedzia. ([libsyn](https://decredindepth.libsyn.com/-exitus-dcr-community-managment-media), [youtube](https://www.youtube.com/watch?v=oGi3NA14CZU))
- Rough Consensus, odc. 2 - Rozproszony konsensus. @mr.black, @Checkmate i @permabullnino omawiają zagadnienie księgowości potrójnego zapisu i sposób, w jaki zapewnia ona ramy dla analizy mechanizmów konsensusu. Teoria jest taka, że PoW, PoS i hybrydowe systemy zabezpieczeń zapewniają różne zabezpieczenia i zabezpieczenia księgowe. ([libsyn](https://roughconsensus.libsyn.com/rough-consensus-2-distributed-consensus))
- Rough Consensus, odc. 3 - Przed nami długa droga. @mr.black, @Checkmate, oraz @permabullnino omawiają najnowszą makro zmianę wywołaną przez COVID-19, pojawienie się najdłuższej hossy na rynku akcji w historii, oraz to, jak kryptowaluty mogą odegrać ważną rolę w przyszłości. ([libsyn](https://roughconsensus.libsyn.com/rough-consensus-3-the-long-road-ahead))
- POV Crypto Podcast, odc. 127 - Solidny pieniądz w czasach, gdy drukarka robi „brrr”, z udziałem @permabullnino ([libsyn](https://povcryptopod.libsyn.com/127-hard-money-in-the-time-of-brrr-with-permabullnino), wspomnienie o Decred ok. 30 minuty)
- Czym jest Decred? aut. @elian (w jęz. hiszpańskim, [criptotendencias.com](https://www.criptotendencias.com/podcast/episodio-30-que-es-decred-entrevista-con-elian-huesca-community-builder-business-dev-del-proyecto/))
- Brief Decred, aut. @elian (w jęz. hiszpańskim, [Territorio Bitcoin](https://www.ivoox.com/episodio-111-especial-comunidad-blockchain-cuarentena-audios-mp3_rf_49382826_1.html))


## Dyskusje społeczności

Wiadomości z platform komunikacyjnych:

- Opublikowano poradnik o tym, jak dołączyć do społeczności Decred na Matrixie w dokumentacji projektu pod adresem [docs.decred.org](https://docs.decred.org/getting-started/joining-matrix-channels/). Jeśli wolicie, aby to Stakey był Waszym przewodnikiem, dostępna jest nieco inna wersja przewodnika na stronie [dcrcomic.org](https://dcrcomic.org/guide-enter-the-matrix.html).
- Dla Waszej informacji, możecie bezproblemowo śledzić [komentarze na subreddicie r/decred](https://www.reddit.com/r/decred/comments/) tak, że nigdy już żadnego nie przegapicie.

Wybrane wątki z Reddita:

- Użytkownik u/oiezz zasugerował wykorzystanie postów o publikacji miesięcznika DJ jako miejsca do dyskusji, a [post](https://www.reddit.com/r/decred/comments/fgo0p4/decred_journal_february_2020/) z zeszłego miesiąca zebrał 18 komentarzy.
- [Post](https://www.reddit.com/r/decred/comments/fhrsqn/austerity_mindset/fkd6nrn/) od u/Corp-Por pytający, czy Decred powinien przyjąć postawę oszczędnościową względem funduszy ze Skarbca otrzymał 22 komentarze i ocenę 7. Większość komentatorów nie była tak chętna, jak OP do wprowadzenia drastycznych zmian, powołując się na duże rezerwy w Skarbcu i zdolność do utrzymania finansowania na obecnym poziomie przez 5 lat.
- [Post](https://www.reddit.com/r/decred/comments/frb863/next_privacy_iteration_how_private_and_fungible/) pytający o następny krok w rozwijaniu prywatności Decred doczekał się odpowiedzi od @jy-p, który napisał, że obrane zostało podejście łatwo osiągalnego celu (wsparcie w Decrediton, bezpieczeństwo w epoce post-kwantowej), dalszym zwiększaniu ilości mieszanych kredytów, a dopiero po tym powrót do pytań o to, jak jeszcze bardziej zwiększyć prywatność.
- @davecgh [odpowiedział](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/) na przykrą historię interesariusza Decred, który stracił dostęp do swoich DCR, ponieważ VSP, z którego ów użytkownik korzystał, zaprzestał działalności, a jego maszyna z portfelem Decrediton uległa zniszczeniu, przy czym sam użytkownik nie zapisał skryptu wykupu (szczegóły [tutaj](https://docs.decred.org/wallets/decrediton/using-decrediton/#backup-redeem-script)). @davecgh wyjaśnił, że skrypt wykupu jest współdzielony z VSP jako multi-sig, gdzie użytkownik lub VSP może wykupić zablokowane DCR i wycofać bilety. Ponieważ skrypty do realizacji wykupu są ponownie wykorzystywane i ujawniane podczas realizacji pierwszego zgłoszenia, ten konkretny scenariusz z zablokowanymi DCR może wystąpić tylko wtedy, gdy portfel użytkownika lub VSP nigdy nie był online, aby wycofać którykolwiek z wykupionych przez nich biletów. Po wykorzystaniu pojedynczego zgłoszenia przez tę kombinację portfel/VSP, skrypt jest już w zasadzie przechowywany na blockchainie.
- @bee [jest zdania](https://www.reddit.com/r/decred/comments/frqvmc/checkmate_on_twitter_ftx_has_finally_listed_dcr/flxb7s0/), że instrumenty pochodne to samo zło i ma nadzieję, że ktoś oświeci nas odnośnie ich korzyści dla społeczności Decred.
- @bee [argumentował](https://www.reddit.com/r/decred/comments/frqkt0/your_favorite_misconceptions_about_decred_in_one/fm1jrmc/?context=3), że nie wszystkie zmiany konsensusu są tak niepożądane, jak częste zmiany algorytmu PoW, niezbędne do utrzymania odporności przeciw urządzeniom ASIC.

Wybrane dyskusje z Twittera:

- @swack zgubił swój młotek i wytweetował ten [wątek](https://twitter.com/swack0/status/1239674494526111747) o Decred jako jedynym niebędącym Bitcoinem zasobie, który zasługuje na uwagę jako środek przechowania wartości i alternatywa dla pieniądza fiat, powołując się na jego adaptacyjność, samofinansowanie się, oraz brak związanych z nim instrumentów finansowych wykorzystujących dźwignię.
- Propozycja DCP-0006 o zarządzaniu przez media społecznościowe dn. 1 kwietnia [ogłasza](https://twitter.com/decredproject/status/1245399765489254400?s=20) konsternację w związku z niespodziewanie dużym udziałem respondentów (66%), uważających, że opiniom wygłaszanym przez Twittera należy się większa waga głosu, w odpowiedzi na sondę przeprowadzoną na Twitterze - wszystko to poddaje w wątpliwość zastosowaną metodologię próbkowania.
- @chappjc [tweetuje](https://twitter.com/chappjc/status/1245075450625511425) o skoordynowaniu pierwszej wymiany przez atomic swaps zapoczątkowanej zleceniem wymiany na rozwijanej przez projekt zdecentralizowanej giełdzie.
- @davecgh powraca z twitterowej emerytury cieszącym się popularnością [tweetem](https://twitter.com/davecgh/status/1238309416270790658?s=20) o aktywacji nowych zasad konsensusu określonych w dokumencie DCP0005 Block Header Commitments.

## Rynki

W marcu kurs wymiany Decred wahał się pomiędzy 8,68-19,78 USD / BTC 0,0017-0,0021. Średni dzienny kurs wynosił 13,40 USD.

7 marca kurs wymiany BTC/USD rozpoczął swój spadek z 9100 dolarów do 7800 dolarów, który osiągnął 11 marca. 12 marca dołączył do światowej paniki związanej z chorobą COVID-19 i przepadł poniżej ~4500 USD (a na niektórych rynkach [jeszcze niżej](https://twitter.com/HsakaTrades/status/1239227306863820801)). Większość aktywów krypto straciła tego dnia około 40% wartości, co świadczy o ich przeważnie spekulacyjnym poziomie cen i utrzymującej się zależności od BTC. Ten dumping spowodował, że kurs DCR/USD spadł wraz z nim do poziomu ~8 USD.

Fred Wilson [zauważył](https://avc.com/2020/03/correlation-and-market-meltdowns/), że „w panice wszystkie aktywa są skorelowane”, ale kiedy panika się uspokaja, wtedy fundamenty krypto mogą ponownie zacząć działać.

## Ważne kwestie i wiadomości poboczne

Rynki na całym świecie przechodzą [bardzo trudny okres](https://www.bloomberg.com/news/articles/2020-03-08/yen-slides-as-oil-price-war-adds-to-global-worries-markets-wrap), ponieważ wszyscy zdali sobie sprawę z powagi sytuacji związanej z COVID-19, a państwa, zarówno w kwestii działalności, jak i granic, zaczęły się zamykać. Ceny kryptowalut spadły tak samo lub bardziej niż większość innych aktywów, wszystkie spotkania i wydarzenia związane z Decred są odwoływane lub przenoszone do sieci, a niektórzy współpracownicy mają na głowie więcej spraw związanych z opieką nad dziećmi i rodziną niż zwykle, ale wydają się to być jedyne zmianami, które bezpośrednio związane są z Decred. Niemniej jednak sytuacja ta ma oczywiście wpływ na nas wszystkich oraz na szersze otoczenie makroekonomiczne i perspektywy. Bądźcie bezpieczni.

To był trudny miesiąc dla DeFi, ponieważ gwałtowny spadek cen ETH nadwyrężył stabilność stablecoina DAI. Kiedy cena ETH przesunie się za bardzo, część pożyczek DAI zostanie zlikwidowana na aukcjach, jeśli ich posiadacze nie dodadzą więcej ETH, aby osiągnąć wymagane zabezpieczenie, ale przy tej okazji wydaje się, że cena zmieniła się zbyt szybko, aby aukcje likwidacyjne za nią nadążyły. Ten [artykuł](https://medium.com/@whiterabbit_hq/black-thursday-for-makerdao-8-32-million-was-liquidated-for-0-dai-36b83cac56b6) wyjaśnia, jak DAI o wartości 8,32 mln USD zostało upłynnione za 0 USD, wraz z tym, jak nieprzewidziane warunki w procesie aukcyjnym zaskutkowało tym, że 36% wszystkich aukcji likwidacyjnych poszło za najwyższą ofertę w wys. 0 USD. „Największy Skarbiec stracił ~35 000 ETH, podczas gdy najbardziej udany likwidator odnotował zysk w wysokości 30 000 ETH". Pozostawiło to Fundację Maker i społeczność w trudnej [pozycji](https://www.coindesk.com/defi-leader-makerdao-weighs-emergency-shutdown-following-eth-price-drop), rozważając zmianę zasad w locie lub uruchomienie awaryjnego zamknięcia. Fundacja [zdecydowała](https://www.coindesk.com/makerdao-debts-grow-as-defi-leader-moves-to-stabilize-protocol), aby nie korzystać ze swoich uprawnień do bezpośredniej interwencji poprzez uruchomienie wyłączenia, a zamiast tego wprowadziła propozycje, które zmieniły parametry ryzyka i zorganizowała aukcję nowo wydrukowanych żetonów MKR, aby spłacić dług protokolarny i „zwrócić utracone fundusze".

W zeszłym miesiącu rozpoczął się konflikt na linii Steem-Sun, kiedy to firma Steemit (i jej „wydobyte po cichaczu” żetony STEEM) została przejęta przez Justina Sun - świadkowie Steem (DPoS) przyjęli hard forka, aby te żetony unieważnić, w efekcie czego Sun zmobilizował wsparcie giełd wymian, aby wyprzeć istniejących świadków i zastąpić ich marionetkami, które nie przyjęłyby hard forka, zachowując swoje żetony STEEM. W marcu strategia społeczności Steem zmieniła się, ponieważ wpływowa grupa zdecydowała się na [migrację](https://www.coindesk.com/steem-will-hard-fork-in-just-hours-over-community-fears-of-justin-sun-power-grab) z blockchaina Steem na nowy o nazwie Hive. Mówi się, że giełdy Binance i Huobi popierają ten ruch, w niezwykłym zwrocie akcji od ich działań w zeszłym miesiącu, kiedy to głosowali zgodnie z Sunem. Znani członkowie społeczności Steem podziękowali społeczności za wycofanie swoich STEEM z giełd wymian, aby wywrzeć presję na giełdy, by te cofnęły swoje poparcie dla promowanych przez Suna świadków. Wydaje się, że operatorzy giełd byli również wprowadzeni w błąd co do znaczenia ich głosów w tym kontekście, wierząc, że głosowali za zwykłą aktualizacją protokołu.

Hive jest taki sam jak Steem w większości przypadków, a 1 STEEM może być wymieniony na 1 HIVE - główna różnica polega na tym, że żetony STEEM od Steemit Suna nie będą mogły być wykupione w łańcuchu HIVE, skutecznie usuwając je z ekosystemu. Kiedy pisano tę [historię](https://www.coindesk.com/splinter-cryptocurrency-hive-outperforms-justin-suns-steem-after-one-week-trading) cena HIVE była prawie dwukrotnie wyższa niż STEEM, ale od 4 kwietnia dwa żetony są sprzedawane po podobnych cenach. Ten przypadek powinien zainteresować tych, którzy twierdzą, że głosowanie monetowe jest plutokratyczne, ponieważ pokazuje, co może się stać, gdy wieloryby próbują wykorzystać swoje monety do narzucenia swojej woli niechętnej do tego społeczności.

To był dobry miesiąc dla ludzi, którzy lubią kupować, przechowywać lub sprzedawać kryptowaluty, nie będąc przy tym uznawani za przestępców. Rządy w [Korei Południowej](https://thenews.asia/amendment-to-special-reporting-act-passes-cryptocurrency-trading-now-legal-in-south-korea/) i Sąd Najwyższy w [Indiach](https://news.bitcoin.com/bitcoin-legal-india-supreme-court-verdict-cryptocurrency/) podjęły działania mające na celu unieważnienie wcześniej nałożonych ograniczeń na handel kryptowalutami.

Od 18 marca Tether wyemitował ponad 400 mln USDT w partiach po 60 mln USD, przekroczywszy całkowitą sumę tokenów w wys. [6 mld USD](https://beincrypto.com/tether-usdt-quietly-surpasses-the-6-billion-mark/). 25 marca liczba tokenów USDT przechowywana na giełdach wyznaczyła nowe ATH w wysokości [1,2 miliarda dolarów](https://twitter.com/glassnodealerts/status/1242849119456157699). Moment tej operacji jest interesujący, gdyż ma miejsce tuż po krachu na rynku 12 marca. Używajcie USDT z ostrożnością, ponieważ nawet jego współzałożyciel uważa, że [„to nie ma znaczenia”](https://beincrypto.com/tether-co-founder-it-doesnt-really-matter-if-usdt-backed-by-equal-amount-of-dollars/), czy Tether ma równowarte pokrycie w dolarach.

Rząd Stanów Zjednoczonych zatwierdził wyjątkowo duży plan „stymulacyjny” w wys. [2 bilionów dolarów](https://www.zerohedge.com/economics/anatomy-2-trillion-covid-19-stimulus-bill) w związku z COVID-19. Dyskusja na temat źródła tego finansowego zastrzyku w mediach jest nadal rzadkością. Jeden z polityków [argumentował](https://twitter.com/RepThomasMassie/status/1243565651391897603), że projekt ustawy tworzy jeszcze większą tajemnicę wokół Systemu Rezerwy Federalnej, który i tak nie podlega kontroli.

Amerykański System Rezerwy Federalnej dokonał wielu bezprecedensowych posunięć w związku z COVID-19, które zostały zwięźle [streszczone](https://www.bloomberg.com/news/articles/2020-03-25/fed-unbound-all-the-u-s-central-bank-s-corona-related-moves) przez Bloomberg. Większość z nich oznacza [tworzenie pieniędzy](https://seekingalpha.com/article/4335693-inflation-alert-money-supply-expanding-26x-rate-of-qe1) z powietrza bez żadnej pracy stojącej u ich podstawy, a następnie pożyczanie tych pieniędzy ludziom i firmom, które będą musiały _pracować_, aby je spłacić. Wśród tych środków znajdują się linie wymian zbudowane w celu „wypompowania USD na cały świat, aby ułatwić dostęp do najważniejszej waluty świata".

Prezes jednego z 12 banków Rezerwy Federalnej otwarcie przyznał w [wywiadzie](https://www.zerohedge.com/markets/kashkari-says-fed-has-infinite-amount-cash-we-create-it-electronically), że „w Rezerwie Federalnej jest nieskończona ilość gotówki".

Europejski Bank Centralny [ogłosił](https://www.ecb.europa.eu/press/pr/date/2020/html/ecb.pr200318_1~3949d6f266.en.html) „program awaryjnego zakupu aktywów związany z pandemią” o wartości 750 mld EUR oraz [odnotował](https://twitter.com/Lagarde/status/1240414918966480896), że „nie ma żadnych ograniczeń dla naszego zaangażowania w euro. Jesteśmy gotowi wykorzystać pełen potencjał naszych narzędzi, w ramach naszego mandatu". Bank jest gotowy do dalszego zwiększania rozmiarów programów zakupu aktywów i zmiany wszelkich narzuconych przez siebie limitów.

## Wszystkiego najlepszego, Decred Journal! Sto lat!

24-te wydanie jest jednocześnie drugą rocznicą istnienia dziennika Decred Journal.

Moment na refleksję oraz parę ciekawostek od @bee:

- Zespół DJ rozrósł się z 2 do ~5 stałych współpracowników, ~3-8 tłumaczy, oraz ~7-11 osób recenzujących treść i dzielących się opiniami.
- Rozmiar wydań dziennika w bajtach wzrósł z 20 KB do ~50 KB. Najobszerniejsze wydanie ważyło [64.5 K](https://xaur.github.io/decred-news/journal/201908.html) (7.5K słów).
- Nasz proces produkcyjny znacznie się rozwinął i jest obecnie obszernie [udokumentowany](https://github.com/xaur/decred-news/blob/docs/guidelines.md).
- Być może zauważyliście, że [decredowe](https://xaur.github.io/decred-news/journal/201805.html) [torty](https://xaur.github.io/decred-news/journal/202002.html) mają dla mnie szczególnie duże znaczenie.
- Przed opublikowaniem [pierwszego](https://xaur.github.io/decred-news/journal/201804.html) wydania potrzebowaliśmy tytułu. Wśród rozważanych kandydatów były „Miesięczna sesja rozrywkowa dla interesariuszy” oraz „Głęboko w Decred”; to ostatnie zostało odrzucone ze względu na jego seksualne konotacje.
- W marcu 2019 roku byłem dość wyczerpany i [ogłosiłem](https://xaur.github.io/decred-news/journal/201903.html#psa-decred-journal-takes-a-break), że produkcja przyszłych numerów stoi pod znakiem zapytania. Na szczęście kilka osób [wystąpiło](https://github.com/xaur/decred-news/issues/65) przed szereg i kontynuowaliśmy pracę.
- Problem pierwszego roku: rozpoczynając każdy numer, martwiłem się, że nie będę w stanie zebrać wystarczającej ilości treści i że będzie on kiepsko wyglądał w porównaniu z poprzednimi miesiącami, które obfitowały w wydarzenia i wiadomości. Za każdym razem się myliłem. Problem drugiego roku: kiedy kończyłem każdy numer, martwiłem się, że jest za duży i trudno było mi śledzić wszystko, co się dzieje.
- Nie byłem w stanie sobie wyobrazić, jak będzie wyglądał [indeks](https://xaur.github.io/decred-news/) wszystkich wydań i tłumaczeń za 2 lata!
- Po pionierskim wykorzystaniu Gita i GitHuba do produkcji DJ zacząłem nękać prawie wszystkich w społeczności, aby zrobić to samo dla innych dokumentów. Wierzę, że zachowanie wiedzy jest [ważne](https://github.com/xaur/decred-news/blob/docs/guidelines.md#why-git) i będzie Was w tym celu dalej dręczył. Dziękuję za waszą cierpliwość.
- Około 6 miesięcy po założeniu DJ zacząłem denerwować się z powodu spadającej liczby łapek w górę na Reddicie. Potem porozmawiałem z ludźmi i dowiedziałem się dwóch rzeczy: po pierwsze, ludzie, którzy są tu od lat, mówią, że to normalka, bo ludzie z czasem stają się mniej wrażliwi na każdy bodziec, nawet ten dobry. Po drugie, brałem te łapki w górę zbyt poważnie, nie wiedząc nawet, kto za tymi liczbami stoi. Jednak ludzie, których znam, z którymi rozmawiam dzień w dzień, ludzie nieprzeciętnie inteligentni i niesamowicie mądrzy, którzy są powodem, dla którego wciąż tu jestem, mówią mi, że robię dobrą robotę, a oni sami latami wykonują niesamowitą pracę, nie uganiając się za „lajkami". Zadałem sobie więc pytanie, dlaczego zależy mi na tych liczbach bardziej niż na tym, co myślą najlepsi ludzie wokół mnie? To nie ma sensu! Więc przestałem się o to martwić. (Bez urazy dla naszych drogich czytelników, bardzo cenimy sobie wasze opinie, tylko nie liczbę kliknięć! Dzielę się tą anegdotą dla osób, które zbyt mocno skupiają się statystykach).
- Podziękowania dla interesariuszy Decred za sfinansowanie tych prac i pomoc w dostarczaniu produkcji tej skali i jakości.
- W ciągu tych dwóch lat otrzymaliśmy wiele pozytywnych [opinii](https://xaur.github.io/decred-news/testimonials.html). Pochwała nie jest celem, ale miłe słowa dają nam do zrozumienia, że wciąż jesteśmy na dobrej drodze. Dziękujemy za całe wsparcie!

## O tym wydaniu

To 24. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: bee, elian, degeri, l1ndseymm, kozel, pablito, richardred, s\_ben
- recenzje i komentarze: adcade, ammarooni, chappjc, davecgh, emiliomann, guisso, jholdstock, jrick, lukebp, matheusd, michae2xl, raedah
- ilustracja tytułowa: saender
