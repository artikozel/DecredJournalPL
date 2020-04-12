# Decred Journal – Marzec 2020

![abstrakcja](../img/journal-202003-384.png)

_Obraz: Wektor ekspansji, aut. @saender_

Najważniejsze wydarzenia z marca:

- Zmiana zasad konsensusu określona w DCP-0005 została aktywowana, wprowadzając do sieci Decred prawdopodobnie najbardziej bezpieczną i chroniącą prywatność implementację SPV dla lekkich klientów. Wszystkie węzły v1.4, które nadal działały, zostały odłączone od sieci.
- Budowany DEX skoordynował zlecenie pierwszej transakcji wymiany z wykorzystaniem atomic swaps w sieci testnet.
- W tym miesiącu nastąpił spektakularny postęp w prawie wszystkich kluczowych repozytoriach oprogramowania, o czym ze szczegółami można przeczytać poniżej.
- Roczne budżety na czynności w zakresie nawiązywania kontaktów i promocji dla społeczności amerykańsko-angielskich oraz brazylijskich zostały zatwierdzone na łączną kwotę 286 tys. dolarów, w tym część środków na kontynuację produkcji Dziennika.
- Jest to 24. wydanie Decred Journal, co oznacza dwa lata nieprzerwanego, comiesięcznego raportowania o projekcie Decred!


## Rozwój

O ile nie zaznaczono inaczej, prace zgłaszane poniżej mają status "scalonych z repozytorium głównym (master)". Oznacza to, że prace są ukończone, zrecenzowane i zintegrowane z kodem źródłowym, który zaawansowani użytkownicy mogą kompilować i uruchamiać, ale ich efekty nie są jeszcze dostępne w wersji plików binarnych dla zwykłych użytkowników.


[dcrd](https://github.com/decred/dcrd):

- podpisy ECDSA zostały [odłączone](https://github.com/decred/dcrd/pull/2139) od pakietu secp256k1, aby wyraźnie zaznaczyć, że ECDSA jest tylko jednym z możliwych algorytmów podpisu cyfrowego oraz aby umożliwić sygnaturom Schnorr stanie się obywatelem pierwszej kategorii bazy kodowej
- wyeksportowano [typ wartości pola](https://github.com/decred/dcrd/pull/2134), aby umożliwić zewnętrznym wywoływaczom wykonywanie zoptymalizowanej matematyki pól
- weryfikacja podpisu została dodatkowo zoptymalizowana poprzez minimalizację kosztownych operacji
- dodano metodę [czyszczenia](https://github.com/decred/dcrd/pull/2117) kluczy prywatnych z pamięci oraz [zredukowano](https://github.com/decred/dcrd/pull/2131) liczbę wewnętrznych kopii kluczy prywatnych w celu zwiększenia bezpieczeństwa przed scrapingiem pamięci
- duże liczby całkowite zostały [usunięte](https://github.com/decred/dcrd/pull/2107) całkowicie z operacji parsowania i podpisywania na rzecz specjalistycznego kodu skalarnego mod n
- testy weryfikacyjne Schnorra zostały [przerobione](https://github.com/decred/dcrd/pull/2128) w celu rozwiązania wielu problemów
- zapobieżenie niewłaściwemu wykorzystaniu kodu w kilku obszarach
- usunięto nieużywany kod


Ujawniono [lukę w oprogramowaniu](https://bounty.decred.org/2020/03/status-update/), która pozwalała na potencjalny wielodniowy atak wyczerpujący pamięć, który mógł doprowadzić do awarii węzła w dcrd v1.4.0. 13 marca sieć forkowała na nowe zasady konsensusowe, zaimplementowane w dcrd v1.5.0, co oznacza, że wszystkie węzły w sieci są zobowiązane do korzystania z conajmniej tej wersji oprogramowania. Ponieważ ta i późniejsze wersje zawierają poprawkę łatającą tę lukę, jej szkodliwość została teraz zneutralizowana.

dcrd pokrywa się kodem z btcd w mniej niż 16%, co oznacza, że pozostałe 84% to nowa praca deweloperska, według [analizy](https://coincode.sh/c/dcr/) autorstwa CoinCode.sh. @davecgh [potwierdził](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$15862843869377LGlSK:decred.org), że liczby wyglądają wiarygodnie, biorąc pod uwagę, jak dużo nowego kodu zostało napisane i zauważył, że rozbieżność ta jest jeszcze bardziej widoczna w dcrwallet (który nie był analizowany).


[dcrwallet](https://github.com/decred/dcrwallet):

- polecenie` fundrawtransaction` zostało [wdrożone](https://github.com/decred/dcrwallet/pull/1706); dodaje ono niepodpisane wejścia i zmienia wyjście do surowej transakcji
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
- zrefaktoryzowano [kod połączenia](https://github.com/decred/dcrpool/pull/171) aby uprościć testowanie
- zwiększono pokrycie testami
- drobne usprawnienia w UX, konfiguracji oraz parę poprawek błędów
- powyższe prace są przygotowaniem do nadchodzącego wydania 1.1.0

[dcrlnd](https://github.com/decred/dcrlnd):

- ulepszenia w [systemie builda](https://github.com/decred/dcrlnd/pull/84)

Prace w toku:

- nowa paczka [chainscan](https://github.com/decred/dcrlnd/pull/83), która wykorzystuje dedykowane filtry do skuteczniejszego wykrywania transakcji istotnych dla węzła LN i może również działać w trybie SPV
- [implementacje](https://github.com/decred/dcrlnd/pull/92) dla paczek chainntnfs, które wykorzystują wbudowany i zdalny dcrwallet jako źródło wydarzeń łańcucha. Pozwala to na dalsze odseparowanie dcrlnd od bazowego dcrd, co jest wymogiem dla posiadania instancji dcrlnd działającej w trybie SPV.
- bazując na powyższym, możliwość włączenia i testowania [trybu SPV](https://github.com/decred/dcrlnd/pull/95) dla zdalnych portfeli ("remote wallet" jest trybem połączenia, w którym dcrlnd łączy się z już uruchomioną instancją dcrwallet, tzn. nie potrzebuje własnego wbudowanego portfela z oddzielnym seedem)

 > tryb SPV jest wymagany dla mobilnych portfeli LN. Jest prawdopodobne, że SPV będzie dominującym trybem synchronizacji nawet w portfelach stacjonarnych, więc niezbędne jest, aby dcrlnd obsługiwało tryb SPV. Jest to również ostatnia pozycja w sekcji prac "na już" w mojej swoistej "mapie rozwoju", którą nakreśliłem w [poście ogłaszającym](https://matheusd.com/post/announcing-dcrlnd/) LN, więc jest to podsumowanie większości wysiłków związanych z portowaniem z lnd do dcrlnd. Ukończenie prac nad SPV oznacza, że możemy zacząć badać bardziej egzotyczne zmiany, które są dostępne w Decred (takie jak [PTLC](https://suredbits.com/payment-points-monotone-access-structures/), które zależą od prac nad Schnorrem, które @davecgh również ma na ukończeniu). ([@matheusd](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$1586258547807544APZNe:matrix.org))

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
- nowy interfejs użytkownika dla [menu "więcej"](https://github.com/raedahgroup/dcrios/pull/559)
- nowy widżet [wyboru portfela](https://github.com/raedahgroup/dcrios/pull/600) dla strony "transakcje"
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
- strona "inflacja" została [przemianowana](https://github.com/decred/dcrdocs/issues/1074) na ["emisja"](https://docs.decred.org/advanced/issuance/) aby uniknąć dwuznaczności
- [udokumentowano](https://github.com/decred/dcrdocs/pull/1073) dostęp do serwera CoinShuffle++ jako [ukrytej usługi Tor](https://docs.decred.org/privacy/cspp/how-to-cspp/#tor-hidden-service)

[decred.org](https://github.com/decred/dcrweb):

- large cleanup pass fixing minor issues with the new website
- updated VSP [copy](https://github.com/decred/dcrweb/pull/853)
- strona rekrutacji została usunięta, a decred.org/recruiting od teraz przekierowuje do strony [wnoszenia wkładu](https://docs.decred.org/contributing/overview/)
- usunięto stronę [mapy rozwoju](https://github.com/decred/dcrweb/pull/857)

Pozostałe:

- większość projektów została zaktualizowana, aby budować się na Go 1.14 i porzuciła wsparcie dla Go 1.12
- @mm wypuścił na świat DigiSign Oracle, darmową aplikację webową typu open source, która pomaga użytkownikom w weryfikacji podpisów cyfrowych. Narzędzie to zostało stworzone, aby pomóc użytkownikom Decred w weryfikacji podpisów paczek bez konieczności korzystania ze skomplikowanych narzędzi wiersza polecenia. Można z niego skorzystać po wejściu na stronę [stakey.club](https://stakey.club/digisign-oracle/), lub pobrać [kod źródłowy](https://github.com/mmartins000/digisign-oracle) na swój komputer i odpalić go w przeglądarce.

## Plany co do wersji v1.6

> The rough plan is for v1.6 to get released at end of Q2. We're planning to include: decentralized treasury consensus change, Decrediton staking and non-staking CSPP support, ticket-based VSP support, and a myriad dcrd improvements. (@jy-p on [2020-03-20](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15855719584400kpyNr:decred.org))

## Ludzie

Welcome to new first time contributors with code merged to master: @unimere ([decrediton](https://github.com/decred/decrediton/commits?author=unimere)).

Community stats:

- Twitter followers: 40,694 (-207)
- Reddit subscribers: 9,760 (+22)
- Matrix users: 601 (+36)
- Discord users: 1,160 (+73), verified to post: 479 (+29)
- Telegram users: 2,607 (-71)
- YouTube subscribers: 3,980 (-10)
- Facebook followers: 3,606 (+26), likes: 3,273 (+24)
- LinkedIn followers: 744 (+25)
- GitHub dcrd stars: 536 (+1), forks: 1,507 (+11)

## Governance

In March the [Treasury](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) received 13,713 DCR and spent 17,153 DCR. Using March's daily average DCR/USD rate of $13.40, this is $184K received and $230K spent. At February's average daily rate of $20.48, the USD figure billed for work completed in that month is $281K. As of Apr 3, Treasury balance is 640K DCR (7.41 million USD at $11.58).

This month saw the publication of 4 new proposals.

The new [proposal](https://proposals.decred.org/proposals/2f08f8518bc7672069a10ac6461fd9ab341d4a9e4c343fd4a7ec426250f3896f) from the DCRComic team requested an increased budget of $16,200 for 12 more comics plus supporting activity, with an extra $150 per comic added for extra time spent adapting the assets for social media use. The proposal was put on [hold](https://twitter.com/DCRComic/status/1243197581104041984) to reformulate the cast of characters, after some criticism that Stakey was being over-used in representing many different roles in the Decred ecosystem. On Apr 6 the proposal was edited to add new [characters](https://github.com/pLabarta/dcrwebcomic/blob/master/Proposal2/NewChars.md) that will join the line-up alongside Stakey, and on Apr 9 voting opened.

The US Marketing [proposal](https://proposals.decred.org/proposals/c830ea5afea45a0aabf4092d1bea51fb10b8bfa2d8474aac03224f0f94d3d1af) was, after being edited down to $177,800 to remove the community organizing of events in light of COVID-19, approved with 74% support and voter turnout of 31%.

The Brazilian marketing [proposal](https://proposals.decred.org/proposals/bc20f986c3ea2fed2ea074c377a89f1a4b956ea0d527a8b6c099a5a8f175beb5), which requests $108K for the rest of the year was also approved, with 65% support and turnout of 34%. This proposal was edited to say that events will not be organized or billed for while the COVID-19 situation persists, but the item was not removed from the budget and some of this activity may take place later in the year.

Two further proposals were submitted and are under discussion. A [proposal](https://proposals.decred.org/proposals/d3b16861a7e555db2fdd25b589123f4b6c4289c857fbdff329a4ffb1cb60c4d9) from PolisPay App seeks $5,000 to support DCR. There is also a [proposal](https://proposals.decred.org/proposals/7d42c6f4bf3059b64789185af615c1df97cb61a379425933be5ff01d074ed4d5) to fund the Decred Daily twitter [account](https://twitter.com/Decred_Daily) for 6 months and make a website for it (total budget $5,280). The Decred Daily proposal started voting on Apr 9.

Shortly before publication on Apr 9 another proposal was published, requesting $24,450 for a [billboard](https://proposals.decred.org/proposals/bce7bf3cd1f74d571d23ac8a330ddf29a14a547ed0cc9c995f1a97dce733d1e1) marketing campaign.

The Market Making proposal from i2 Trading is nearing the end of the six months of market making activity, this commenced in late October 2019 and so will come to an end in late April 2020. i2's trading logs continue to be audited monthly by Company 0 and performance has been found to be satisfactory. i2 are planning to submit a proposal to continue MM activity for Decred, but it will be scaled down to reflect the current market conditions.

For more detail on the month's Politeia activity see Politeia Digest [issue 29](https://blockcommons.red/politeia-digest/issue029/).

## Network

Hashrate: [March's hashrate](https://explorer.dcrdata.org/charts?chart=hashrate&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) opened at ~359 Ph/s and closed ~309 Ph/s, bottoming at 274 Ph/s and peaking at 556 Ph/s throughout the month. Pool [hashrate distribution](https://dcrstats.com/pow) as of Apr 1: UUPool 55%, Poolin 18%, lab.antpool.com 17%, Luxor 2.5%, BTC.com 2.2%, F2Pool 1.5%, BeePool 0.13%, CoinMine 0.08%, Suprnova 0.02% and others ~3.8%. Pool distribution numbers are approximate and cannot be accurately determined.

Staking: [30-day average](https://dcrstats.com/) ticket price was 141.9 DCR (+9.8). The [price](https://explorer.dcrdata.org/charts?chart=ticket-price&zoom=k73pwcch-k8jayo3s&bin=window&axis=time) varied between 130.9-166.8 DCR. [Locked amount](https://explorer.dcrdata.org/charts?chart=ticket-pool-value&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) was 5.50-5.75 million DCR, which corresponded to 49.05-51.27% of the available supply [participating](https://explorer.dcrdata.org/charts?chart=stake-participation&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) in PoS.

The ticket price topped at 166.82 which is again a new high since the stake difficulty algorithm change.

Block size: This month, the blockchain size grew by 129 MB. Blocks had an average [size](https://explorer.dcrdata.org/charts?chart=block-size&zoom=k73pwcch-k8jayo3s&bin=block&axis=time) of 14.5 KB. The smallest block had a size of 1.62 KB and the largest one, 374.98 KB. So far the major source of nearly full blocks is the Treasury: this month the payouts created a range of 9 full blocks on [Mar 16](https://explorer.dcrdata.org/blocks?height=432590&rows=20).

Transactions: In March, Decred users made 49,078 regular transactions and bought 44,149 tickets. 43,791 tickets were rewarded for voting and 728 were revoked. On average, there were 1,583 regular DCR transactions and 1,424 new tickets per day.

Nodes: Throughout [March](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1583020800000&to=1585699200000) there was an average of 146 public listening nodes and 246 total nodes per dcr.farm. Average version distribution for Mar: 28% dcrd v1.5.1, 20% dcrd v1.4, 15% dcrd v1.5, 8% dcrd v1.5 dev and RC builds, 5% dcrd v1.6 dev builds, 5% dcrwallet v1.5.1, 5% dcrwallet v1.4, 2% dcrwallet v1.5. On Mar 13 the new consensus rules activated and after that dcrd v1.4 can no longer follow the chain.

## Integrations

Probit [added](https://twitter.com/ProBit_Exchange/status/1235450770100649986) support for DCR/KRW and DCR/USDT pairs to their exchange.

Exmo.com had a sudden DCR [outage](https://twitter.com/Exmo_Com/status/1240255377507303431) a few days after the Mar 13 fork, the services [resumed](https://twitter.com/Exmo_Com/status/1240627750005870592) the next day. Currently, Exmo is the only integration [funded](https://proposals.decred.org/proposals/950e8149e594b01c010c1199233ab11e82c9da39174ba375d286dc72bb0a54d7) by stakeholders.

[NOWPayments](https://nowpayments.io/) payment processor that was launched in 2019 by ChangeNOW supports DCR among [40+](https://nowpayments.io/supported-coins/) other assets.

ChainRift [announced](https://twitter.com/ChainRift/status/1228010062163202049) in Feb that they will be shutting down exchange operations and pivoting to a software development company.

DCR was [added](https://twitter.com/Checkmatey/status/1244030247558729729) to FTX PRIV-PERP index future contract that tracks a basket of 9 privacy coins. Index calculation can be found [here](https://help.ftx.com/hc/en-us/articles/360027668812-Index-Calculation).

User AGspearo was not able to access their [funds](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/) due to the VSP d1pool.com shutting down without notice and them not having access to their redeem script. AGspearo spent a lot of time on support trying to resolve this issue but ultimately they were unable to get their funds. @davecgh broke down the issue as a [comment](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/fkiac45) and also said a possible consensus change might solve these [issues](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/fkku35k). If you are reading this and do not have your redeem scripts backed up please take this a warning and do a [backup](https://docs.decred.org/wallets/decrediton/using-decrediton/#backup-redeem-script) and store then along with your seed.

Some VSPs that had broken signup pages/out of date/returning errors had been [put on notice](https://github.com/decred/dcrwebapi/pulls?q=is%3Apr+author%3Ajholdstock+created%3A2020-03-01..2020-03-31) that they will be removed from the [listing](https://decred.org/vsp/). Some of them have responded and fixed the issues. raqamiya.net, tokensmart.io, and dcrpos.idcray.com have been removed since they failed to respond.

Warning: the authors of Decred Journal have no idea about the trustworthiness of any of the services above. Please do your own research before trusting your personal information or assets to any entity.

## Outreach

[Decred in Depth](https://decredindepth.libsyn.com) released two new episodes in March and one in early April, while [Rough Consensus](https://roughconsensus.libsyn.com/) also released 2 episodes (see [Media](#media) below).

@Dustorf [posted](https://proposals.decred.org/proposals/c830ea5afea45a0aabf4092d1bea51fb10b8bfa2d8474aac03224f0f94d3d1af/comments/56) that he will be operating in a reduced capacity for the next couple months and that the cost of the proposal will be reduced accordingly. The executions affected include: newsletter, original content generation, Decred Assembly, PR, and release coordination, and update work. This specifically means that the DEX release will have to be managed by the developers and the community at large.

@dezryth [posted](https://scottrchristian.com/2020/03/15/dezryth-proposal-updates/) a second update about his operation of Decred's Facebook account for the month of February. This one is more detailed and includes stats for each post, comparison to competitors, and shares some ideas about next steps. @dezryth acknowledges that current stats are not great and that organic following is hard to build, but on the good side active posting brought a 30% increase in daily views.

@bee has extensively (really) [commented](https://www.reddit.com/r/decred/comments/fa70c3/decred_2019_marketing_report/) on the 2019 Marketing Report and shared his vision for moving forward.

A comprehensive compilation of [common misconceptions](https://github.com/decredcommunity/wiki/blob/master/wiki/misconceptions.md) and criticism of Decred was added to decredcommunity wiki, along with responses to them. Feedback/contributions welcome, discussion is [here](https://www.reddit.com/r/decred/comments/frqkt0/your_favorite_misconceptions_about_decred_in_one/).

Monde PR's achievements for March:

- outreach and introductions to target journalists
- pitched reactive comments to current news stories
- submitted comments from Decred spokespeople to 7 news stories
- pitched Decred to 3 upcoming features
- submitted thought leadership piece written by @richardred to ValueWalk
- secured 2 media interviews

News coverage secured by Monde PR:

- an [article](https://cointelegraph.com/news/proof-of-stake-vs-proof-of-work-which-one-is-fairer) in Cointelegraph featuring commentary from @jy-p on consensus models
- an [article](https://www.financemagnates.com/cryptocurrency/news/fintech-experts-share-tips-for-remote-work-during-coronavirus-quarantine/) in Finance Magnates featuring commentary from @richardred on remote working
- an [article](https://www.coindesk.com/remote-working-proves-unexpected-hero-as-half-of-us-economy-shifts-to-home-offices) in CoinDesk featuring commentary from @jy-p on rapid scaling which was also syndicated to Yahoo Finance

## Events

Attended:

- Mar 4 - [Decred Meetup](https://www.eventbrite.com/e/decred-meetup-la-plata-tickets-95666770887) - La Plata, Argentina. It was an introduction to Decred project in which @camilolwi, @tomee, and @pablito talked about the fundamentals of Decred, its security and hybrid consensus model, governance, voting and how to become a contractor for the project. There were around 20 attendees to the meetup and a session of networking. ([photos](https://twitter.com/cryptorc_tech/status/1238180910513733634))
- Mar 4 - [Decred Meetup](https://www.eventbrite.com/e/decred-en-uninet-business-school-caracas-venezuela-tickets-97157792573) - Caracas, Venezuela. The meetup was co-hosted by Uninet Business School and Innova Consultants. There were 15 attendees to the meetup, there was an introduction to Decred, its security and hybrid model, privacy, how to contribute, followed by a session of Q&A and networking. ([photos](https://twitter.com/Decred_ES/status/1235324847338795009))
- Mar 4 - [Crypto and Blockchain 2020 and Beyond](https://www.meetup.com/BC-Aus/events/268793182/) - Melbourne, Australia. This 80+ person event directed entry fees to Crypto Fire Alliance to help with the bushfire emergency (the event raised $1K while the entire program [raised](https://www.finder.com.au/crypto-bushfire-fundraiser) $27K in crypto). @eSizeDave joined an hour-long panel discussion, [noting](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158381267934685XUpiS:decred.org): "the audience had more questions for me than anyone else, and got a lot of follow-up meetings as a result of it". ([report](https://github.com/decredcommunity/events/blob/master/reports/20200304-crypto-and-blockchain-2020-and-beyond-melbourne-australia.md), [video](https://twitter.com/DecredAustralia/status/1235390840307978245))
- Mar 5 - [Decred Meetup](https://www.eventbrite.com/e/decred-meetup-en-valencia-venezuela-tickets-97804334397) - Valencia, Venezuela. Co-hosted by ClicTechNova y CoWorking Lab. The meetup was an introduction to the Decred ecosystem, hybrid blockchain, governance mechanism, privacy, and elements that make Decred a DAO. There were ~50 attendees that asked interesting questions about social attacks on the network, how to contribute and the incentive model of DCR. ([photos](https://twitter.com/Decred_ES/status/1236079742643773440), [video](https://twitter.com/Decred_ES/status/1236080559752916998))
- Mar 6 - [Impact Hub](https://www.eventbrite.com/e/decred-meetup-impact-hub-caracas-venezuela-tickets-97159680219) - Caracas, Venezuela. Co-hosted by El Dorado y Cointigo. The meetup was an introduction to the Decred ecosystem, its governance structure and what makes it a different cryptocurrency from the rest. Around 30 people attended, several entrepreneurs and developers but also several new users of cryptocurrencies looking for more information about the technology and investment opportunities. ([photos](https://twitter.com/Decred_ES/status/1236337867095343104), [video](https://twitter.com/Decred_ES/status/1236340242698752001))
- Mar 8 - [International Women's Day](https://www.meetup.com/GDGCasablanca/events/268661463/) - Casablanca, Morocco. The event was held at ENSAM, a University of Science. Most of the 70 attendees were data science students and developers. @arij gave a 1-hour talk about blockchains and Decred and a workshop afterwards: "What I've learned from my experiences talking and explaining blockchain technology and Decred, is that people are more interested when you show them how things really work with demo and videos, especially when it is their first time learning about it". ([notes](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158374584733992NOIMZ:decred.org), [photos](https://www.flickr.com/photos/187387360@N04/albums/72157713440754483))
- Mar 12 - [Bitcoin Woman to Woman](https://twitter.com/bitcoinemb/status/1233500964566523911) - Mexico City, Mexico. Co-hosted by the Bitcoin Embassy, the ~30 person meetup was to discuss women's involvement in the cryptocurrency industry and how to empower women to use crypto. @francov\_ did a presentation on how to contribute to the Decred project and her experience working in the industry. "The highlight of the talk was to express that we do not need your title, gender, nationality, age, even your real name, we only need your talent and your aspiration to help the Decred ecosystem grow". The meetup was followed by a networking session. ([report](https://github.com/decredcommunity/events/blob/master/reports/20200312-bitcoin-woman-to-woman-mexico-city-mexico.md))
- Mar 12 - [Decred Meetup](https://www.meetup.com/es-ES/BitcoinBlockchainUruguay/events/269160706/) - Montevideo, Uruguay. Around 25 people attended the meetup. @tomee presented an introduction to Decred and its security, adaptability, and sustainability, Politeia, governance and how to contribute. The meetup was also a networking session and some of the people knew the project from Labitconf. (photos: [1](https://twitter.com/ivarese/status/1238628854379536389), [2](https://twitter.com/cryptorc_tech/status/1241081659669315585))
- Mar 12 - [Blockchain Summit Latam](https://twitter.com/Decred_ES/status/1237552322596593665) - Panama City, Panama. The event was rescheduled to Oct 15-16, but this change occurred 24 hours before the event when some speakers were already in the area (~35 people). The event staff took the opportunity and hosted a small meetup where presenters got the chance to network and to know about the projects from close up. @adcade and @elian talked with a few representatives and secured an [interview](https://es.cointelegraph.com/news/decred-how-does-your-development-continue-during-the-bear-market) for Spanish Cointelegraph. ([report](https://github.com/decredcommunity/events/blob/master/reports/20200312-blockchain-summit-latam-meetup-panama-city-panama.md))
- Mar 12 - [Hablemos Decred 01](https://twitter.com/Decred_ES/status/1238242352306614273) - Internet. "Let's Talk Decred", the first Spanish online meeting used Decred's Discord server. Most questions were about Decred's PoS voting system. Those who had some prior knowledge of crypto asked how to stake, and those who didn't wanted to know more about voting rights and what can stakeholders do with their tickets. About a third of ~15 people were new to the project. ([report](https://github.com/decredcommunity/events/blob/master/reports/20200312-hablemosdecred-01-internet.md))
- Mar 18 - [Exchanges in LATAM](https://twitter.com/Decred_ES/status/1240428280756310018) - Internet. @elian talked about centralized and decentralized exchanges in a virtual meetup with people from [@AvaLatam](https://twitter.com/AvaLatam), [@blockchain_land](https://twitter.com/blockchain_land) and virica.io Mexico. Around 16 people attended and one lesson learned was that online talks should be 30 min or less.
- Mar 24 - [Decred Webinar](https://www.meetup.com/es-ES/blockacademycl/events/269108758/) - Internet. @tomee and @camilolwi talked all things Decred and the challenges of decentralized blockchain governance in a webinar co-organized with Blockchain Academy Chile. ([video](https://www.youtube.com/watch?v=U07ZL_qFAQM))
- Mar 27 - [Hablemos Decred 02](https://twitter.com/Decred_ES/status/1243214184793485314) - Internet. Second Spanish online meetup explored Jitsi to connect 13 participants from Argentina, Mexico, Bolivia, Chile, of which 7 were new to the project. This time the call started with an intro talk about Decred, a demo of Decrediton, and an open mic for questions and comments. ([report](https://github.com/decredcommunity/events/blob/master/reports/20200327-hablemosdecred-02-internet.md))
- Mar 29 - [Binance AMA](https://twitter.com/Decred_ES/status/1244360357843533825) - Internet. The event was hosted in the Binance Spanish Telegram group with 8,000+ members and received a high level of engagement. @adcade, @elian, and @pablito got 155 questions from 73 participants and gifted 0.333 DCR to the best questions. A good amount of knowledge was gathered that can signal where prospect Decred users lack information. This was the second Decred AMA with the Binance Spanish community and the longest AMA they had so far (~2.5 hours). ([report](https://github.com/decredcommunity/events/blob/master/reports/20200329-decred-ama-binance-spanish-community-internet.md))
- Mar 30 - [Decred and Sound Money Virtual Meetup](https://www.meetup.com/Decred-Australia/events/269640276/) - Internet. The event was hosted by @eSizeDave and @zohand and joined by @Checkmate to discuss key topics such as sound money, the macroeconomic environment, gold, and Decred. Participants were quite impressed by the quality and left good feedback, one of them enjoying that it was "mentally stimulating". ([report](https://github.com/decredcommunity/events/blob/master/reports/20200330-decred-and-sound-money-internet.md))

Cancelled:

- Apr 5 - [Toronto Blockchain Week](https://www.eventbrite.ca/e/discover-decred-an-autonomous-digital-currency-toronto-blockchain-week-tickets-91562362491) - Toronto, Canada.

Upcoming:

- Apr 13-17 - [Jalisco Talent Land @ Home](https://www.talent-land.tv/) - Internet. In a panel called "Decred, crypto and the future of money" Decred LATAM team will give a brief on Decred and explore how crypto will transform remote work and our interaction with money. The panel will be streamed on [talent-land.tv](https://www.talent-land.tv/) on Apr 15, 21:00 (CST, UTC-5).
- Apr 16 - [Decred Webinar](https://twitter.com/Decred_ES/status/1245452957417684992) - Internet. The topic will be "Let's talk about cryptocurrencies and the future of money" - a webinar hosted by Ibero (university) to discuss crypto and give an overview of Decred.
- May 14 - [BlockConf](https://blockconf.digital/) - Internet. Decred LATAM team will run a virtual booth for Decred to answer questions from the attendees. If anyone wants to help with keeping the booth active in several time zones during the 48-hour event, please contact @elian.
- May 30-31 - [Bitconf](https://www.bitconf.com.br/portal/) - São Paulo, Brazil. Decred will have multiple talks on various subjects.
- June or later - [Campus Party Amazonia](https://brasil.campus-party.org/campus-party-amazonia-2020/) - Manaus, Brazil. Moved from March.
- June or later - [Jalisco Talent Land](https://www.talent-land.mx/en/home/) - Guadalajara, Mexico. Moved from April.
- End of 2020 - [DevOpsDays](https://devopsdays.org/events/2020-natal/welcome/) - Natal, Brazil. Moved from March.

Postponed until further notice:

- [CIBTC Blockchain Summit](http://cibtc.es/) - Motril, Spain.
- Decred Meetup - La Paz, Bolivia.
- [Bitcoinference](https://www.eventbrite.com/e/bitcoinference-where-the-blockchain-meets-you-tickets-94598812595) - Cancún, Mexico.

## Media

[decredpower.info](https://decredpower.info/) is a new single-page directory to explore all things Decred. Suggestions are welcome [here](https://github.com/raedahgroup/decredpower/issues).

Selected articles:

- Observing Ethereum governance during the ProgPoW debate by @Checkmate ([medium](https://medium.com/@_Checkmatey_/observing-ethereum-governance-during-the-progpow-debate-9bf1aec724ad))
- Crypto risk is not what you think by @Dustorf ([medium](https://medium.com/@dlefebvr/crypto-risk-is-not-what-you-think-8a2662840b70))
- Theory of three pillars in the cypherpunk social contract by @Cato\_io ([medium](https://medium.com/@cato_io/threepillarstheory-cd6b57c5d88a))
- Public service, pandemics and crypto networks by @mrbulb ([medium](https://medium.com/@decentpartners/public-service-pandemics-and-crypto-networks-379dce1594d1))
- Decred: how does your development continue during the bear market? by @adcade (in Spanish, [es.cointelegraph.com](https://es.cointelegraph.com/news/decred-how-does-your-development-continue-during-the-bear-market))

The Brazil Marketing and Events [proposal](https://proposals.decred.org/proposals/bc20f986c3ea2fed2ea074c377a89f1a4b956ea0d527a8b6c099a5a8f175beb5) was covered in the media from an interesting "investment in Brazil" perspective (in Portuguese):

- "Decred's community allows more than 500,000 BRL to be invested in Brazil" ([criptofacil.com](https://www.criptofacil.com/comunidade-decred-permite-que-mais-r-500-mil-sejam-investidos-brasil/))
- "Cryptocurrency will invest more than half a million in Brazil" ([livecoins.com.br](https://livecoins.com.br/criptomoeda-vai-investir-mais-meio-milhao-brasil/))
- "'Whales' approve and Decred can invest more than 500,000BRL to promote cryptocurrency in Brazil" ([cointelegraph.com.br](https://cointelegraph.com.br/news/decred-pode-investir-ate-us-500-mil-para-promover-criptomoeda-no-brasil)) - this one is poorly written and is based on another interview (@emiliomann)
- "The cryptocurrencies that invest the most in Brazil" ([cointimes.com.br](https://cointimes.com.br/as-criptomoedas-que-mais-investem-no-brasil/))

Translations:

- Theory of three pillars in the cypherpunk social contract - [in Spanish](https://medium.com/decred-es/teor%C3%ADa-de-los-tres-pilares-en-el-contrato-social-del-cypherpunk-40f569836b6a) by @francov\_
- Decred Technical Brief - [in Arabic](https://insaf01.github.io/decred-arabic/articles/decred-technical-brief-ar.html) by @arij
- Decred Journal February 2020 was translated to Arabic (@arij), Chinese (@Dominic) and Spanish (@francov\_). All three are stored [in Git](https://github.com/xaur/decred-news/blob/docs/guidelines.md#why-git) which helps to preserve the work long-term and protect it from censorship. Thank you all for spreading the word!

Videos:

- Decred's 2020 marketing and publishing proposals for the USA & Brazil breakdown by @Exitus ([youtube](https://www.youtube.com/watch?v=Liol1lLCinQ))
- Decred bi-Weekly news update - March 12, 2020 by @Exitus ([youtube](https://www.youtube.com/watch?v=N4U1FwYUaKA))
- Decred bi-Weekly news update - March 31, 2020 by @Exitus ([youtube](https://www.youtube.com/watch?v=MBi7d263HvE))
- Top 5 staking coins in 2020 by Coin Bureau ([youtube](https://www.youtube.com/watch?v=znx7H7JWtfg))

Audio:

- Decred in Depth Ep. 19 - Leo Zhang of Iterative Capital talks about Proof of Work mining, gives a first-hand account of mining economics, and considers the benefits of a hybrid PoS component and formal stakeholder decision-making. ([libsyn](https://decredindepth.libsyn.com/leo-zhang-dcr-mining), [youtube](https://www.youtube.com/watch?v=iWi3nK0HIHE), [soundcloud](https://soundcloud.com/decredindepth/leo-zhang-dcr-mining))
- Decred in Depth Ep. 21 - @Exitus talks about producing video content for the Decred DAO, becoming a contractor and the challenges crypto marketing faces during the bear market. ([libsyn](https://decredindepth.libsyn.com/-exitus-dcr-community-managment-media), [youtube](https://www.youtube.com/watch?v=oGi3NA14CZU))
- Rough Consensus Ep. 2 - Distributed consensus. @mr.black, @Checkmate, and @permabullnino discuss the concept of triple entry accounting and how it provides a framework for analyzing consensus mechanisms. The theory is that PoW, PoS and hybrid security systems provide different security and ledger assurances. ([libsyn](https://roughconsensus.libsyn.com/rough-consensus-2-distributed-consensus))
- Rough Consensus Ep. 3 - The long road ahead. @mr.black, @Checkmate, and @permabullnino discuss the latest macro shift triggered by COVID-19, the popping of the longest equities bull market in history, and how cryptocurrencies can play a role in the future. ([libsyn](https://roughconsensus.libsyn.com/rough-consensus-3-the-long-road-ahead))
- POV Crypto Podcast Ep. 127 - Hard money in the time of brrr with @permabullnino ([libsyn](https://povcryptopod.libsyn.com/127-hard-money-in-the-time-of-brrr-with-permabullnino), Decred mentioned around 30 min mark)
- What is Decred? by @elian (in Spanish, [criptotendencias.com](https://www.criptotendencias.com/podcast/episodio-30-que-es-decred-entrevista-con-elian-huesca-community-builder-business-dev-del-proyecto/))
- Decred Brief by @elian (in Spanish, [Territorio Bitcoin](https://www.ivoox.com/episodio-111-especial-comunidad-blockchain-cuarentena-audios-mp3_rf_49382826_1.html))

## Community Discussions

Comm systems news:

- A guide on how to join the Decred Matrix community was published at [docs.decred.org](https://docs.decred.org/getting-started/joining-matrix-channels/). If you prefer to be guided by Stakey, a slightly different version is available at [dcrcomic.org](https://dcrcomic.org/guide-enter-the-matrix.html).
- FYI you can watch the [r/decred comment feed](https://www.reddit.com/r/decred/comments/) to never miss a new comment.

Selected Reddit posts:

- u/oiezz has suggested using the monthly Journal posts as discussion spaces, and last month's [post](https://www.reddit.com/r/decred/comments/fgo0p4/decred_journal_february_2020/) has accumulated 18 comments.
- A [post](https://www.reddit.com/r/decred/comments/fhrsqn/austerity_mindset/fkd6nrn/) from u/Corp-Por asking whether Decred should adopt an austerity mindset with Treasury funds had 22 comments and a score of 7. Most of the commenters were not as keen as the OP to make drastic changes, citing the Treasury's ample reserves and capacity to maintain funding at current rates for 5 years.
- A [post](https://www.reddit.com/r/decred/comments/frb863/next_privacy_iteration_how_private_and_fungible/) asking about Decred's next privacy iteration had @jy-p respond to say that the approach is to pick the low-hanging fruit (Decrediton support, post-quantum security), continue to increase mixing uptake, then revisit questions about how to enhance privacy further.
- @davecgh [responded](https://www.reddit.com/r/decred/comments/fim5j2/stakepool_failure_caused_me_to_lose_all_my/) to the unfortunate story of a Decred stakeholder who has lost access to their staked DCR because the VSP they were using went offline, their Decrediton machine was destroyed, and they had not saved the redeem script (see details [here](https://docs.decred.org/wallets/decrediton/using-decrediton/#backup-redeem-script)). @davecgh explained that the redeem script is shared with the VSP as a multi-sig where either the user or VSP can redeem locked DCR and revoke tickets. As redeem scripts are reused and revealed when the first ticket is redeemed, this stuck DCR scenario can only occur when the wallet of the user or VSP has never been online to redeem any of the tickets that used it. Once a single ticket has been redeemed by that wallet/VSP combination, the script is effectively stored in the blockchain.
- @bee [thinks](https://www.reddit.com/r/decred/comments/frqvmc/checkmate_on_twitter_ftx_has_finally_listed_dcr/flxb7s0/) that derivatives are evil and is hoping to get enlightened about their benefit for the public.
- @bee made a [point](https://www.reddit.com/r/decred/comments/frqkt0/your_favorite_misconceptions_about_decred_in_one/fm1jrmc/?context=3) that not all consensus changes are as undesirable as frequent PoW algorithm changes necessary to maintain ASIC resistance.

Selected Twitter discussions:

- @swack lost his hammer and tweeted this [thread](https://twitter.com/swack0/status/1239674494526111747) about Decred as the only non-Bitcoin cryptoasset that deserves consideration as SoV and fiat alternative, citing adaptability, sustainability, and lack of associated leveraged financial products.
- DCP-0006 Social Media Governance, [announced](https://twitter.com/decredproject/status/1245399765489254400?s=20) Apr 1, is in doubt with an unexpectedly large proportion of respondents (66%) to the Twitter poll voting to give Twitter the greatest weighting - this raises serious questions about the sampling methodology.
- @chappjc [tweets](https://twitter.com/chappjc/status/1245075450625511425) about the first dcrdex order-driven atomic swap being coordinated.
- @davecgh comes out of twitter retirement with a popular [tweet](https://twitter.com/davecgh/status/1238309416270790658?s=20) about the activation of DCP0005 Block Header Commitments.

## Markets

In March DCR was trading between USD 8.68-19.78 / BTC 0.0017-0.0021. The average daily rate was $13.40.

On Mar 7 BTC/USD started its decline from $9,100 mark down to $7,800 on Mar 11. On Mar 12 it joined the global COVID-19 panic and tanked below ~$4,500 (and [even lower](https://twitter.com/HsakaTrades/status/1239227306863820801) in some markets). Most cryptoassets lost around 40% that day, demonstrating their mostly speculative price levels and persisting dependence on BTC. This dump took DCR/USD with it down to ~$8.

Fred Wilson [noted](https://avc.com/2020/03/correlation-and-market-meltdowns/) that "in panics, all assets are correlated", but when the panic settles cryptocurrency fundamentals might start kicking in.

## Relevant External

Markets everywhere had a [very bad time](https://www.bloomberg.com/news/articles/2020-03-08/yen-slides-as-oil-price-war-adds-to-global-worries-markets-wrap) as the severity of the COVID-19 situation became clear and nations began to lock down. Cryptocurrency prices declined as much or more than most other assets, all Decred meetups and events are canceled or moving online, and some contributors have more childcare to do than before, but those seem to be the only changes that are directly relevant to Decred. Nevertheless, the situation obviously has an effect on all of us and the broader macroeconomic environment and outlook. Stay safe.

It was a challenging month for DeFi, as a sharp drop in the price of ETH strained the stability of the DAI stablecoin. When ETH price moves too much some DAI loans will be liquidated in auctions if their holders do not add more ETH to reach the required collateralization, but on this occasion, the price appears to have moved too quickly for the liquidation auctions to keep up. This [article](https://medium.com/@whiterabbit_hq/black-thursday-for-makerdao-8-32-million-was-liquidated-for-0-dai-36b83cac56b6) explains how $8.32 million worth of DAI was liquidated for $0, as unforeseen conditions in the auction process (including ETH chain congestion) resulted in 36% of all liquidation auctions going to the highest bidder at $0.00. "The greatest Vault has lost ~35,000 ETH whereas the most successful liquidator has had a profit of 30,000 ETH". This left the Maker Foundation and community in a difficult [position](https://www.coindesk.com/defi-leader-makerdao-weighs-emergency-shutdown-following-eth-price-drop), considering changing the rules on the fly or triggering an emergency shutdown. The Foundation [decided](https://www.coindesk.com/makerdao-debts-grow-as-defi-leader-moves-to-stabilize-protocol) not to use its power to intervene directly by triggering a shutdown, and moved to introduce proposals that modified risk parameters and set up an auction of newly printed MKR tokens to pay the protocol debt and "refund CDPs that lost funds".

The Steem-Sun conflict began last month when the Steemit company (and its "ninja mined" STEEM tokens) was acquired by Justin Sun - Steem (DPoS) witnesses adopted a hard fork to nullify those tokens, then Sun mobilized exchange support to oust the established witnesses and replace them with puppets that would not adopt the fork, preserving his STEEM tokens. In March the strategy of the Steem community changed, as an influential group decided to [migrate](https://www.coindesk.com/steem-will-hard-fork-in-just-hours-over-community-fears-of-justin-sun-power-grab) away from the Steem blockchain to a new one called Hive. Exchanges Binance and Huobi are said to be supportive of this move, in a remarkable turnaround from their actions last month when they voted with Sun. Prominent members of the Steem community thanked community members for withdrawing their STEEM from exchanges, to put pressure on exchanges to backtrack on supporting the Sun-powered witnesses. It seems the exchange operators were also misled about the significance of their votes in that context, believing that they were voting for a regular protocol upgrade.

Hive is the same as Steem in most regards, with 1 STEEM being exchangeable for 1 HIVE - the main difference is that Sun's Steemit STEEM tokens will not be redeemable on the HIVE chain, effectively cutting them out of the ecosystem. When this [story](https://www.coindesk.com/splinter-cryptocurrency-hive-outperforms-justin-suns-steem-after-one-week-trading) was written the price of HIVE was almost double that of STEEM, but as of Apr 4, the two tokens are trading for similar prices. This case should be of interest to those who say coin voting is plutocratic, as it shows what can happen when whales try to use their coins to impose their will on an unwilling community.

It has been a good month for people who like to buy, hold or sell cryptocurrency without being considered a criminal. The governments in [South Korea](https://thenews.asia/amendment-to-special-reporting-act-passes-cryptocurrency-trading-now-legal-in-south-korea/) and supreme court in [India](https://news.bitcoin.com/bitcoin-legal-india-supreme-court-verdict-cryptocurrency/) made moves to nullify previously imposed restrictions on cryptocurrency trading.

Since Mar 18 Tether has issued over $400M USDT in batches of $60M and surpassed the [$6 billion](https://beincrypto.com/tether-usdt-quietly-surpasses-the-6-billion-mark/) mark. On Mar 25 USDT held on exchanges has set a new ATH of [$1.2 billion](https://twitter.com/glassnodealerts/status/1242849119456157699). The timing is interesting as it comes quickly after the market crash of Mar 12. Use USDT with caution, because even its co-founder believes ["it doesn't really matter"](https://beincrypto.com/tether-co-founder-it-doesnt-really-matter-if-usdt-backed-by-equal-amount-of-dollars/) if it's backed by an equal amount of dollars.

U.S. government approved an exceptionally large [$2 trillion](https://www.zerohedge.com/economics/anatomy-2-trillion-covid-19-stimulus-bill) "stimulus" plan attributed to COVID-19. Discussion of the source of funds is still rare in the media. One politician [argued](https://twitter.com/RepThomasMassie/status/1243565651391897603) that the bill creates even more secrecy around the Fed that is already not auditable.

U.S. Fed made multiple unprecedented moves attributed to COVID-19, succinctly [summarized](https://www.bloomberg.com/news/articles/2020-03-25/fed-unbound-all-the-u-s-central-bank-s-corona-related-moves) by Bloomberg. Most of that means [creating money](https://seekingalpha.com/article/4335693-inflation-alert-money-supply-expanding-26x-rate-of-qe1) out of thin air without any labor, and then loaning out that money to people and businesses who will need to _work_ to pay it back. Among the measures are swap lines built to "pump USD out across the world to ease access to the world's most important currency".

President of one of the 12 Federal Reserve Banks openly admitted in an [interview](https://www.zerohedge.com/markets/kashkari-says-fed-has-infinite-amount-cash-we-create-it-electronically) that "there's an infinite amount of cash at the Federal Reserve".

ECB [announced](https://www.ecb.europa.eu/press/pr/date/2020/html/ecb.pr200318_1~3949d6f266.en.html) a EUR 750 billion "Pandemic Emergency Purchase Programme" and [noted](https://twitter.com/Lagarde/status/1240414918966480896) "There are no limits to our commitment to the euro. We are determined to use the full potential of our tools, within our mandate". The bank is ready to further increase the size of asset purchase programmes and revise any self-imposed limits.

## Happy Birthday DJ!

24th issue marks the second anniversary of Decred Journal.

Retrospective and a bit of trivia from @bee:

- The DJ team has grown from 2 to ~5 stable contributors, ~3-8 translators, and ~7-11 people reviewing and sharing feedback.
- The byte size of an issue has grown from 20 KB to ~50 KB. The biggest issue was [64.5 K](https://xaur.github.io/decred-news/journal/201908.html) (7.5K words).
- Our production process has evolved significantly and is now extensively [documented](https://github.com/xaur/decred-news/blob/docs/guidelines.md).
- You may have noticed that [Decred](https://xaur.github.io/decred-news/journal/201805.html) [Cakes](https://xaur.github.io/decred-news/journal/202002.html) have a special meaning for me.
- To publish the very [first](https://xaur.github.io/decred-news/journal/201804.html) issue we needed a title. Among the candidates considered were "Monthly Stakeholder Entertainment Session" and "Deep in Decred". The latter was rejected for its sexual connotations.
- In March 2019 I got somewhat exhausted and [announced](https://xaur.github.io/decred-news/journal/201903.html#psa-decred-journal-takes-a-break) that the production of future issues is uncertain. Luckily, a few more people have [stepped in](https://github.com/xaur/decred-news/issues/65) and we continued.
- Problem of the first year: when starting every issue I worried that I wouldn't collect enough content and that it would look poor compared to previous months that had so much. I was wrong every single time. Problem of the second year: when finishing every issue I worried that it is too big and it got hard to track everything that is happening.
- I couldn't imagine what the [index](https://xaur.github.io/decred-news/) of all issues and translations would look like in 2 years!
- After pioneering the use of Git and GitHub for DJ I began to annoy pretty much everyone in the community to do the same for other documents. I believe that knowledge preservation is [important](https://github.com/xaur/decred-news/blob/docs/guidelines.md#why-git) and will keep annoying you guys. Thank you for your patience.
- About 6 months after starting DJ I got upset about declining Reddit upvotes. Then I talked to people and learned two things. First is that people who've been here for years say it is common: humans get less sensitive to any stimulus over time, even a good one. Second is that I took upvotes seriously without even knowing who is behind those numbers. But people I do know, talk to every day, people of highest intelligence and wisdom who are the reason why I'm still here, keep telling me I'm doing a good job. And they keep doing an amazing job for years without chasing the likes. So I asked myself, why do I care about these numbers more than I care what the best people around me think? It makes no sense! So I stopped worrying about that. (No offense to our dear readers, we value your feedback greatly, just not the number of clicks! I'm sharing this for anyone who gets too focused on stats).
- Thanks to Decred stakeholders for funding this work and helping us deliver the scale and quality of this production.
- We received a lot of positive [feedback](https://xaur.github.io/decred-news/testimonials.html) over these two years. Praise is not the goal, but kind words let us know that we're still on the right track. Thank you for all the support!

## About This Issue

This is issue 24 of Decred Journal. Index of all issues, mirrors, and translations is available [here](https://xaur.github.io/decred-news/).

Most information from third parties is relayed directly from source after a minimal sanity check. The authors of Decred Journal have no ability to verify all claims. Please beware of scams and do your own research.

Your [feedback](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) and [contributions](https://github.com/xaur/decred-news/blob/docs/contributing.md) are always welcome.

Credits (alphabetical order):

- writing and editing: bee, elian, degeri, l1ndseymm, kozel, pablito, richardred, s\_ben
- reviews and feedback: adcade, ammarooni, chappjc, davecgh, emiliomann, guisso, jholdstock, jrick, lukebp, matheusd, michae2xl, raedah
- title image: saender
