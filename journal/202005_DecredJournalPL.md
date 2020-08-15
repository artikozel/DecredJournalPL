# Decred Journal – Maj 2020

![abstrakcja](../img/journal-202005-384.png)

_Obraz: Unoszące się bity, aut. @saender_

Najważniejsze wydarzenia z maja:

- Ogłoszono nowe oprogramowanie o nazwie vspd, które zastąpi istniejący dotychczas dcrstakepool używany przez operatorów VSP, a po wydaniu wersji 1.6 znacząco poprawi też jakość usługi VSP dla wszystkich użytkowników  poprzez wyeliminowanie konieczności zakładania indywidualnych kont, aby z niej skorzystać.
- Oprogramowanie Decred DEX jest w fazie otwartych testów. Jeśli czujecie się odważni, to może spróbujecie wymienić trochę testnetowych kredytów?
- Wchodzą w życie nowe, znaczące komponenty Politei: propozycje dla zapytań ofertowych (RFP) oraz funkcjonalność głosowania dla wszystkich wykonawców po stronie CMS.
- Wersje testowe aktualizacji v1.5 dla obu aplikacji mobilnych są już dostępne w odpowiednich serwisach z aplikacjami - testerzy zgłaszający problemy na GitHubie są bardzo mile widziani.


## Rozwój

O ile nie zaznaczono inaczej, prace zgłaszane poniżej mają status „scalonych z repozytorium głównym (master)”. Oznacza to, że prace są ukończone, zrecenzowane i zintegrowane z kodem źródłowym, który zaawansowani użytkownicy mogą kompilować i uruchamiać, ale ich efekty nie są jeszcze dostępne w wersji plików binarnych dla zwykłych użytkowników.

[dcrd](https://github.com/decred/dcrd):

- przeprojektowano [seeding HTTPS](https://github.com/decred/dcrd/pull/2188) (dla punktu odniesienia, sieć [migruje](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$156556717014681nMMAT:decred.org) do seedingu przez HTTPS, ponieważ jest on bezpieczniejszy, nie wymaga dużej powierzchni zależnościowej, jak DNSSEC, oraz jest bardziej elastyczny)
- [banowanie](https://github.com/decred/dcrd/pull/2110) peerów, którzy nie przestrzegają protokołu przewodowego
- więcej kodu zostało zmigrowane do obsługi błędów Go w wersji 1.13

Prace w toku:

- opcode TSPEND konieczny do zdecentralizowania kontroli nad Skarbcem [pomyślnie przeszedł testy](https://twitter.com/marco_peereboom/status/1263185839028350976) w sieci testnet

[dcrwallet](https://github.com/decred/dcrwallet):

- dodano kliencką [paczkę](https://github.com/decred/dcrwallet/pull/1726) do obsługi wywołań JSON-RPC
- dodano możliwość żądania [wielu bloków jednocześnie](https://github.com/decred/dcrwallet/pull/1730) od tego samego peera (jedna ze zmian do wspierania trybu SPV w dcrlnd)
- możliwość zapisywania preferencji głosowania [dla poszczególnych biletów](https://github.com/decred/dcrwallet/pull/1737) (krok ku bezkontowej usłudze VSP opartej jedynie na biletach)

Prace w toku:

- [ulepszono](https://github.com/decred/dcrwallet/pull/1743) wsparcie kont dla API VSP opartych jedynie na biletach

[Decrediton](https://github.com/decred/decrediton):

- refaktoryzacja kodu oraz zwiększenie liczby komponentów wykorzystywanych w pi-ui
- [upiększenie bazy kodowej ](https://github.com/decred/decrediton/pull/2481) przy użyciu zautomatyzowanych zasad celem ulepszenia czytelności
- ulepszenia interfejsu użytkownika

Prace w toku:

- [transakcje mieszane](https://twitter.com/_vctt/status/1265397168317366283)

[Politeia](https://github.com/decred/politeia):

- na backendzie zaimplementowano [proces zapytań ofertowych](https://github.com/decred/politeia/pull/1054) oraz [GUI](https://github.com/decred/politeiagui/pull/1910) - jest to jedna z większych, ostatnio wdrożonych zmian w rozwoju Politei, która wchodzi w fazę testów
- narzędzie dla administratora do [zmiany adresu e-mail](https://github.com/decred/politeia/pull/1178)
- [skrócone linki URL](https://github.com/decred/politeia/issues/900) o propozycji
- nawigacja za pomocą [strzałek kierunkowych](https://github.com/decred/politeiagui/pull/1878) dla załączonych obrazów
- poczyniono postępy w kierunku wyświetlania Politei [bez korzystania ze środowiska javascript](https://github.com/decred/politeiagui/pull/1834)
- wprowadzono dwa, tymczasowe obejścia irytującego problemu podwójnego wyświetlania się komentarzy: jedno, w którym [raz dziennie](https://github.com/decred/politeia/pull/1205), zamiast co godzinę, przeprowadzany jest skan poprawności plików, oraz drugie, które [blokuje](https://github.com/decred/politeiagui/pull/1944) możliwość zostawiania komentarzy w czasie, gdy pojawić mógłby się omawiany bug
- dużo poprawek błędów

CMS:

- [głosowanie obejmujące wszystkich wykonawców](https://github.com/decred/politeia/pull/1104) w sprawie spornych DCC, ważonych liczbą godzin rozliczeniowych w ciągu poprzednich 6 miesięcy - ostatnia część procesu wdrażania [wniosków DCC](https://proposals.decred.org/proposals/fa38a3593d9a3f6cb2478a24c25114f5097c572f6dadf24c78bb521ed10992a4)
- [narzędzie](https://github.com/decred/politeia/pull/1179) w celu przetestowania procesu wydawania DCC i głosowania nad nimi

Prace w toku:

- funkcja administratorska do kwerendowania [statystyk kodu](https://github.com/decred/politeia/pull/1185) wykonawców

[vspd](https://github.com/decred/vspd):

vspd to napisana od podstaw implementacja oprogramowania VSP, która przyniesie ogromną poprawę prywatności użytkowników VSP, a co za tym idzie, bezpieczeństwa sieci Decred. Będzie ona również znacznie łatwiejsza w użyciu ze względu na brak rejestracji, brak konieczności korzystania z e-maila, brak CAPTCHA i brak skryptów do wykupywania/odwoływania biletów. Więcej informacji na temat vspd można znaleźć [we wpisie ogłaszającym usługę](https://blog.decred.org/2020/06/02/A-More-Private-Way-to-Stake/).

[MVP](https://en.wikipedia.org/wiki/Minimum_viable_product) dla vspd jest bliski ukończenia i rozpoczyna się jego integracja z dcrwallet. Jedyną nieopracowaną jeszcze cechą MVP jest krzyżowa kontrola spójności portfeli w celu upewnienia się, że wszystkie portfele głosują właściwymi biletami i z właściwymi dla nich wyborami.

[dcrpool](https://github.com/decred/dcrpool):

Kandydat do wydania dla wersji v1.1 jest gotowy do testów! Wydanie to zawiera [przeprojektowane](https://github.com/decred/dcrpool/pull/207) przetwarzanie płatności, odświeżone UI/UX, zwiększoną wydajności poprzez powiadomienia o pracy z dcrd, oraz mnóstwo innych, pomniejszych usprawnień i poprawek błędów. Przejrzyj [notatki do wydania](https://github.com/decred/dcrpool/releases/tag/v1.1.0-rc1), aby uzyskać więcej informacji.

[dcrlnd](https://github.com/decred/dcrlnd):

@matheusd zamieścił [demo](https://twitter.com/matheusd_tech/status/1263118566418776065) swapu pomiędzy fakturami BTC i DCR na odpowiednich dla nich LN. Jest to, w zasadzie, „wymiana natychmiastowa”, z wyjątkiem tego, że wykorzystuje się w niej LN i nie wymaga przekazania kontroli nad funduszami. Zauważ, że ten prototyp obarczony jest znanym wektorem ataku, i do jego rozwiązania potrzeba więcej badań i prac rozwojowych (najlepiej w oparciu o [PTLC](https://suredbits.com/payment-points-monotone-access-structures/), ale jest to dość odległa przyszłość). Więcej szczegółów na ten temat znajdziecie w [tym czacie](https://matrix.to/#/!LtiDnUlfuRJMekjFSx:decred.org/$ILkQ49LXwBrUcMq5R_JRIkTcjR7FG9lxwMWsxDve2K0).


[dcrdex](https://github.com/decred/dcrdex):

- bardziej bezpieczna [obsługa](https://github.com/decred/dcrdex/pull/291) hasła szyfrującego
- przegląd konfiguracji portfela klienta, pozwalający użytkownikowi na określenie pliku konfiguracyjnego portfela lub ręczne wprowadzenie ustawień (części): [1](https://github.com/decred/dcrdex/pull/311), [2](https://github.com/decred/dcrdex/pull/335), [3](https://github.com/decred/dcrdex/pull/346), [4](https://github.com/decred/dcrdex/pull/352))
- wsparcie dla serwera w zakresie [zawieszania handlu](https://github.com/decred/dcrdex/pull/287) i powiadomień klientów, które są wykorzystywane do planowanych prac konserwacyjnych i rekonfiguracji rynku.
- [rozszerzono](https://github.com/decred/dcrdex/pull/378) tabelę "Twoje zamówienia" w interfejsie przeglądarki klienta
- [wyświetlanie](https://github.com/decred/dcrdex/pull/348) epokowych (oczekujących) zleceń na wykresie głębokości jako osobnej linii przerywanej. Zlecenia epokowe są zleceniami, które zostały złożone, ale nie zostały jeszcze przetworzone przez algorytm łączenia zleceń. Daje to podgląd na to, jak zmienia się rynek podczas otwartej epoki, która trwa ok. 10 sekund.
- ulepszenia w kwestii [aktualizacji salda](https://github.com/decred/dcrdex/pull/418) klienta w celu uzyskania bardziej aktualnej wartości salda
- [Wsparcie Litecoin](https://github.com/decred/dcrdex/pull/372) dla klienta. LTC było już obsługiwane przez serwer, dcrdex, ale teraz klient może korzystać z portfeli LTC i składać zamówienia dla rynków LTC.
- [polecenie handlu](https://github.com/decred/dcrdex/pull/315) umożliwiające zawieranie transakcji z wiersza polecenia
- [polecenie wymiany](https://github.com/decred/dcrdex/pull/314), aby umożliwić wystawianie zleceń i konfigurowanie wymiany z wiersza polecenia
- [pole wyszukiwania rynków](https://github.com/decred/dcrdex/pull/426) dla strony Rynków w interfejsie przeglądarki klienta
- ulepszone [powiadomienie](https://github.com/decred/dcrdex/pull/343) o zdarzeniach związanych z rejestracją (np. zakończone potwierdzenia uiszczenia opłaty)
- funkcja [wylogowywania się](https://github.com/decred/dcrdex/pull/347)
- naprawa wielu błędów i refaktoryzacja kodu


Łącznie 59 PR-ów od 10 współpracowników zostało [scalonych](https://github.com/decred/dcrdex/pulls?q=is%3Apr+merged%3A2020-05-01..2020-05-31+sort%3Aupdated-asc), dodając 10K i usuwając 3K linijek kodu.

Nadchodzące prace obejmują: obsługę serwera dla aktywnych swapów (stan swapów), lepszą obsługę zwrotów inicjowanych przez klienta lub zakończenia wymiany (zwrot) w przypadku awarii negocjacji swapów spowodowanych brakiem działania serwera lub drugiej strony transakcji, rozbudowę RPC klienta, rozbudowę komend administratora serwera, ulepszoną obsługę klienta dla wiadomości o zawieszeniu/wznowieniu pracy serwera.

Rozpoczęło się [testowanie w sieci testnet](https://twitter.com/chappjc/status/1267115398610255874), do uczestnictwa w którym [zapraszamy wszystkich](https://github.com/decred/dcrdex/wiki/Testnet-Testing). Wciąż jest duża szansa na to, że DEX w sieci mainnet zostanie uruchomiony jeszcze tego lata.

[dcrandroid](https://github.com/decred/dcrandroid):

- wsparcie dla portfeli [tylko do obserwacji](https://github.com/decred/dcrandroid/pull/471)
- [szyfrowanie](https://github.com/raedahgroup/dcrlibwallet/pull/131) ziarna portfela oraz wzmocnienie prywatności [wprowadzania ziarna](https://github.com/decred/dcrandroid/pull/473) (_[problemy wokół prywatności](https://github.com/decred/dcrandroid/issues/351) Google Keyboard - kto by się spodziewał?_)
- prośba o [hasło](https://github.com/decred/dcrandroid/pull/467) przed wyświetleniem czy weryfikacją ziarna
- [ograniczenie](https://github.com/decred/dcrandroid/pull/472) użytkownika do 1 portfela na każdy 1 GB RAMu
- tłumaczenie na [jęz. polski](https://github.com/decred/dcrandroid/pull/405)
- liczne poprawki błędów

Testnetowy build wydania v1.5 jest dostępny na [Google Play](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.testnet). Raporty o bugach są mile widziane na naszym [GitHub](https://github.com/decred/dcrandroid/issues).

[dcrios](https://github.com/raedahgroup/dcrios):

- wsparcie dla portfeli [tylko do obserwacji](https://github.com/raedahgroup/dcrios/pull/685)
- wprowadzono funkcję [ponownego skanowania](https://github.com/raedahgroup/dcrios/pull/675) blockchaina
- [logo Decred](https://github.com/raedahgroup/dcrios/pull/674) pojawiło isę na kodach QR
- tłumaczenie na [jęz. polski](https://github.com/raedahgroup/dcrios/pull/683) zostało przeniesione z Androida
- liczne poprawki błędów

Testnetowy build wydania v1.5 jest dostępny na [Apple TestFlight](https://testflight.apple.com/join/7KL4VnB2). Raporty o bugach są mile widziane na naszym [GitHub](https://github.com/raedahgroup/dcrios/issues).

[dcrdata](https://github.com/decred/dcrdata):

- strona kosztu ataku od teraz bierze pod uwagę [ilość DCR w cyrkulacji](https://github.com/decred/dcrdata/pull/1736)
- wersja v5.3 beta została [uruchomiona](https://twitter.com/decredexplorer/status/1262827698986127360) na [stronie głownej dcrdata](https://dcrdata.decred.org/)

Prace w toku:

- [prognoza](https://github.com/decred/dcrdata/pull/1738) wzrostu ceny DCR na stronie kosztu ataku w oparciu o aktualne giełdowe księgi zamówień (wersja "w toku" dostępna jest na [planetdecred.org](https://explorer.planetdecred.org/attack-cost) do testów)
- wyświetlanie etykiet Swap Contract oraz Swap Redemption dla transakcji [atomic swap](https://github.com/decred/dcrdata/pull/1733)
- strona [/nextreduction](https://github.com/decred/dcrdata/pull/1753) z licznikiem do następnej redukcji nagrody blokowej oraz podstawowymi informacjami o tym zjawisku (fajne narzędzie oraz punkt wejścia dla osób odkrywających Decred)

[tinydecred](https://github.com/decred/tinydecred):

- podwaliny pod wsparcie [peerów SPV](https://github.com/decred/tinydecred/pulls?q=is%3Apr+merged%3A2020-05-01..2020-05-31+sort%3Aupdated-asc+spv)
- dodano [parametry](https://github.com/decred/tinydecred/pull/184) sieci Bitcoin (pierwszy krok na drodze do wspierania wielu kryptowalut)
- przymiarki do mierzenia [pokrycia testami](https://github.com/decred/tinydecred/pull/180)
- wersja [v0.1.0](https://github.com/decred/tinydecred/releases/tag/v0.1.0) jest pierwszym otagowanym wydaniem (_gratulacje!_)

[docs](https://github.com/decred/dcrdocs):

- [przeprojektowano](https://github.com/decred/dcrdocs/pull/1090) stronę [weryfikacji plikow binarnych](https://docs.decred.org/advanced/verifying-binaries/), która wyjaśnia teraz, co użytkownik powinien zrobić, oraz dlaczego i zaktualizowano wiele stron tak, aby [zachęcały do tego](https://github.com/decred/dcrdocs/pull/1094) użytkowników (_i Wy też powinniście to robić!_)
- [dodano](https://github.com/decred/dcrdocs/pull/1089) nową stronę odn. [skryptu do odzyskiwania środków](https://docs.decred.org/proof-of-stake/redeem-script/), która wyjaśnia, czym jest, kopie zapasowe, oraz odzyskiwanie

Pozostałe:

- @mm opublikował [InvalidationGame](https://github.com/mmartins000/invalidationgame), skrypt symulujący atak podwójnego wydatkowania na symulowanej sieci opartej jedynie na PoW, lub na hybrydowym konsensusie PoW + PoS, jak w Decred.
- strona Bug Bounty zamieściła [aktualizację](https://bounty.decred.org/2020/05/status-update/): w sumie przetworzono 123 zgłoszenia (+19), z których 13 nadawało się do wypłacenia nagrody (+2).
- Niektórzy z naszych programistów stali się aktywniejsi na Twitterze, postując aktualizacje z postępów w swojej pracy. Możecie śledzić [@lukebp_](https://twitter.com/lukebp_), [@marco_peereboom](https://twitter.com/marco_peereboom), [@degeri_crypto](https://twitter.com/degeri_crypto), oraz innych, aby uraczyć się wiadomościami prosto ze źródła. Jeśli jesteś programistą z kontem na Twitterze możesz pomóc krzewić kulturę budowania, którą wyznaje Decred, tweetując podobne aktualizacje (i nie wahaj się proponować ich do retweetowania w pokoju [#media](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org)!).

Statystyki aktywności deweloperskiej za maj (w przybliżeniu): ok. 300 aktywnych PR-ów, ~340 commitów do gałęzi master, ~51K dodanych i ~26K usuniętych linijek kodu spośród 16 repozytoriów (ważne: statystyki pomijają PR [#2481](https://github.com/decred/decrediton/pull/2481) dla repozytorium Decrediton, który dokonał reformatu ogromnego repozytorium). Wkład pochodził od 2-10 deweloperów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: @blaltarriba ([politeiagui](https://github.com/decred/politeiagui/commits?author=blaltarriba)), @dreacot ([dcrandroid](https://github.com/decred/dcrandroid/commits?author=dreacot)), @Ekeh ([dcrdata](https://github.com/decred/dcrdata/commits?author=Ekeh)), @guilhermemntt ([decrediton](https://github.com/decred/decrediton/commits?author=guilhermemntt)), @rstaudt2 ([dcrd](https://github.com/decred/dcrd/commits?author=rstaudt2)) oraz @song50119 ([dcrdex](https://github.com/decred/dcrdex/commits?author=song50119)).

Gratulacje dla nowych współpracowników, którym przyznano licencje wykonawców Decred (DCC): [@camilolwi](https://twitter.com/Camilolwi) (marketing), [@itswisdomagain](https://github.com/itswisdomagain) (rozwój), [@nachito](https://github.com/Reidiojed) (marketing), [@tomee](https://twitter.com/tomasgroos) (marketing).

Trzech członków społeczności Decred [znalazło się na liście](https://twitter.com/Decred_BR/status/1262454667700768769) 50 najważniejszych nazwisk w brazylijskim rynku krypto według Cointelegraph: Rafaela Romano na miejscu #35, Gabriel Rhama na pozycji #31, a pierwsze miejsce zajął Edilson Osório Jr.

Statystyki społeczności na 1 czerwca:

- Obserwujący na Twitterze: 40 492 (-78)
- Subskrybenci na Reddit: 9792 (+31)
- Użytkownicy na Matrixie: 655 (+31)
- Użytkownicy na Discordzie: 1222 (+38)
- Użytkownicy na Telegramie: 2603 (+46)
- Subskrybenci na YouTube: 4030 (+40), wyświetlenia: 144K (+3,5K od 8 maja)
- Obserwujący na Facebooku: 3632 (+14), polubień: 3291 (+11)
- Obserwujący na LinkedIn: 810 (+36)
- Repozytorium dcrd na GitHub: 543 gwiazdki (+6) i 240 forków (+5)

## Zarządzanie

W maju [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 13 594 DCR i wydał 19 153 DCR. Stosując średni dzienny kurs DCR/USD z maja w wysokości 14,11 USD, do Skarbca wpłynęło 192 tys. dolarów, a wydano z niego 270 tys. dolarów. Przy średnim dziennym kursie kwietniowym wynoszącym 12,34 USD, kwota dolarowa naliczona za prace wykonane w tym miesiącu wynosi 236 tys. dolarów. Na dzień 5 czerwca saldo Skarbca wynosi 630 983 tys. DCR (11,4 mln USD po kursie 18,12 USD).

W maju przedstawiono 5 nowych propozycji, z których nad czterema rozpoczęto głosowanie na początku czerwca. W maju nie odbyły się głosowania na platformie Politeia.

Nowe propozycje zostały opisane w [31. wydaniu](https://blockcommons.red/politeia-digest/issue031/) Politeia Digest, a wyniki głosowania nad nimi opisane zostaną w kolejnym wydaniu.

## Sieć

Hashrate: [majowy hashrate](https://explorer.dcrdata.org/charts?chart=hashrate&zoom=k9nb7wvw-kavn2b1a&scale=linear&bin=block&axis=time) na początku miesiąca wyniósł ~357 Ph/s, a zamknął miesiąc w ok. 386 Ph/s, zaliczając niż w ok. 260 Ph/s oraz szczyt w wys. 541 Ph/s w ciągu miesiąca. [Dystrybucja mocy obliczeniowej](https://dcrstats.com/pow) na 1 czerwca wyglądała następująco (w przybliżeniu): UUPool 38%, Poolin 18%, lab.antpool.com 12%, F2Pool 1,5%, Luxor 1,3%, BTC.com 1,3%, BeePool 0,1%, CoinMine 0,03%, Suprnova 0,02% i pozostałe ok. 28%.

Staking: średnia cena biletu [z okresu 30 dni](https://dcrstats.com/) wynosiła 141,5 DCR (+3,7). [Cena](https://explorer.dcrdata.org/charts?chart=ticket-price&zoom=k9nb7wvw-kavn2b1a&bin=window&axis=time&visibility=true-false&mode=stepped) wahała się między 132,9-159,2 DCR. [Zablokowana kwota](https://explorer.dcrdata.org/charts?chart=ticket-pool-value&zoom=k9nb7wvw-kavn2b1a&scale=linear&bin=block&axis=time) wynosiła 5,59-5,80 mln DCR, co odpowiadało 48,7-50,3% dostępnej podaży [biorącej udział](https://explorer.dcrdata.org/charts?chart=stake-participation&zoom=k9nb7wvw-kavn2b1a&scale=linear&bin=block&axis=time) w elemencie PoS.

Węzły: przez [maj](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1588291200000&to=1590969600000) były około 144 węzły nasłuchujące i 229 ogółem, za danymi z dcr.farm. Średnia dystrybucja wersji na maj wygląda następująco: 48% korzysta z dcrd v1.5.1, 11% używa dcrd v1.5.0, 6% korzysta z dcrd v1.6.0 w wersji deweloperskiej, 4% korzysta z dcrd v1.5 w wersji deweloperskiej oraz RC, 2% to dcrd v.1.4, 9% używa dcrwallet v1.5.1, 1,4% korzysta z dcrwallet v1.5, a 1,4% korzysta z dcrwallet v1.4 z 13% rozłożonymi między pozostałe wersje.

Lewis Harland opublikował [badanie](https://formalverification.substack.com/p/in-the-network-decred) dotyczące sieci Decred analizujące szereg metryk, w skład których wchodzą stosunek mocy obliczeniowej do wysokości nagrody za wydobycie bloku denominowanej w USD, która reprezentuje ryzyko ponoszone przez górników. Badanie odnotowuje spadek kilku metryk od stycznia 2020 i sugeruje, że handel DCR odbywa się po stracie w stosunku do całościowego wkładu w sieć w USD.

@PermabullNino opublikował kolejny [artykuł badawczy](https://medium.com/@permabullnino/decred-on-chain-mining-pulse-3b28d5155a04) z danych on-chain, w którym bada czas wydobycia bloków Decred oraz wprowadza wskaźnik pulsu wydobywczego (mining pulse).

## Integracje

[Transak](https://global.transak.com/) umożliwił rezydentom Stanów Zjednoczonych, Unii Europejskiej, oraz wielu innych krajów nowy sposób zakupu DCR za pomocą karty debetowej dzięki [umowie partnerskiej](https://twitter.com/transak_finance/status/1265690509844131846) z Wyre. „Transak korzysta ze smart kontraktów, aby połączyć użytkownika końcowego z płynnością na scentralizowanych i zdecentralizowanych giełdach. Użytkownicy będą musieli wprowadzić podstawowe informacje KYC, ale proces od początku do końca zajmie mniej niż 5 minut". Obecnie Transak jest dostępny w 32 krajach, obsługuje 14 walut fiat i ponad 300 kryptonwalut.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

Decred był obecny na konferencji Consensus: Distributed, wirtualnym evencie, podczas którego 6 członków społeczności poprowadziło 4 sesje, z których wszystkie są teraz dostępne na YouTube. Oprócz tego wydarzenia, które miało miejsce w USA, wszystkie inne (znane) wydarzenia w maju były skierowane na region Latam/Brazylia.

Podcasty Decred in Depth oraz Rough Consensus opublikowały w sumie 4 nowe odcinki.

Po rozpoczęciu swojego [bloga](https://medium.com/@Phoenixgreen) na Medium w kwietniu, Phoenix Green rozszerzył swoją działalność o tworzenie filmów na YouTube i od czasu pisania tego, na jego [kanale](https://www.youtube.com/channel/UCZSFAqUMp8v58eEQl_bzWYg) znajduje się już 10 filmów o tematyce Decred. Gratulujemy uruchomienia i życzymy utrzymania jakości oryginalnych treści!

PR-owe osiągnięcia Monde za maj:

- stworzyliśmy i przedstawiliśmy 3 pomysły na artykuły do publikacji o tematyce inwestycyjnej, finansowej, oraz krypto
- zgłosiliśmy komentarze i uwagi od przedstawicieli Decred do 7 artykułów o bieżych wydarzeniach w krypto
- zdobyliśmy jeden wywiad z mediami i jedną sesję Q&A z publikacjami o tematyce kryptowalutowej


Obecność w mediach dzięki Monde PR:

- artykuł w [Forbes](https://www.forbes.com/sites/cbovaird/2020/05/05/is-this-the-perfect-time-for-central-bank-digital-currencies/) zawierający komentarz @jy-p na temat obaw w kwestii prywatności dotyczących walut cyfrowych wydawanych przez banki centralne (CBDC)
- artykuł w [Cointelegraph](https://cointelegraph.com/news/bitcoin-s-halving-incentivizes-miners-to-sell-for-double-decred-co-founder-says) zawierający komentarz @jy-p na temat wpływu halvingu Bitcoina, syndykowany do 12 serwisów informacyjnych, w tym [FXStreet](https://www.fxstreet.com/cryptocurrencies/news/decred-co-founder-expects-bitcoin-halving-to-spike-btcs-price-202005070208). Komentarze zostały również zawarte w artykule [Zero Hedge](https://www.zerohedge.com/markets/paul-tudor-jones-buys-bitcoin-hedge-against-central-bank-money-printing) i w drugim artykule od [Cointelegraph](https://cointelegraph.com/news/top-experts-make-bitcoin-price-predictions-as-btc-halving-approaches), powielonym w 12 serwisach informacyjnych, w tym [Miami Diario](https://miamidiario.com/bitcoin-a-la-mitad-los-expertos-creen-que-solo-se-debe-comprar-si-se-retiene-a-largo-plazo/) i [Crypto News Australia](https://cryptonews.com.au/story/top-experts-make-bitcoin-price-predictions-as-btc-halving-approaches-121382).
- artykuł w [Finance Magnates](https://www.financemagnates.com/cryptocurrency/news/will-the-upcoming-halving-increase-bitcoins-price/) zawierający komentarz @raedah na temat zmniejszenia nagrody za wydobycie bloku Bitcoina o połowę. Komentarze @raedah zostały również zamieszczone w drugim artykule [Finance Magnates](https://www.financemagnates.com/cryptocurrency/news/will-the-bitcoin-halving-kill-independent-miners/) na ten temat.
- artykuł w [Cointelegraph](https://cointelegraph.com/news/stairway-to-scarcity-bitcoin-sentiment-to-rise-despite-halving-impact) zawierający komentarz aut. @Checkmate na temat halvingu Bitcoina, który został zamieszczony w 5 serwisach informacyjnych, w tym [Investing.com](https://www.investing.com/news/cryptocurrency-news/stairway-to-scarcity-bitcoin-sentiment-to-rise-despite-halving-impact-2164431).
- artykuł w [Reuters](https://www.reuters.com/article/crypto-currencies-bitcoin/as-pandemic-rages-anything-goes-for-bitcoins-third-halving-idUSL1N2CP13B) zawierający komentarz @jy-p, syndykowany do 70 serwisów informacyjnych, w tym w [The New York Times](https://www.nytimes.com/reuters/2020/05/08/business/08reuters-crypto-currencies-bitcoin.html). (obecnie usunięty), [Business Insider](https://www.businessinsider.com/as-pandemic-rages-anything-goes-for-bitcoins-third-halving-2020-5) i [Nasdaq](https://www.nasdaq.com/articles/as-pandemic-rages-anything-goes-for-bitcoins-third-halving-2020-05-08). Komentarze @jy-p zostały również zebrane w kolejnych artykułach o halvingu w [Yahoo Finance](https://finance.yahoo.com/news/bitcoin-halved-price-165148071.html), [CryptoSlate](https://cryptoslate.com/bitcoin-goes-through-the-most-brutal-halving-ever-recorded-heres-why/) i [msn.com](https://www.msn.com/en-us/money/markets/demand-for-bitcoin-surges-as-halving-countdown-approaches/ar-BB13RavI).
- artykuł w [8btc.com](https://m.8btc.com/article/594407) zawierający komentarz @jy-p na temat halvingu Bitcoina.
- artykuł w [Cointelegraph](https://cointelegraph.com/news/bitcoin-halving-was-not-the-apocalyptic-event-some-in-crypto-feared) z komentarzem @Checkmate na temat halvingu Bitcoina.
- artykuł w [AMB Crypto](https://eng.ambcrypto.com/xrp-trades-wide-as-iota-decred-look-to-make-room/) zawierający komentarz @jy-p na temat CBDC
- W sumie w maju w 21 krajach pojawiły się 123 artykuły z dzięki działaniom Monde PR; pełną ich listę znajdziecie [tutaj](https://docs.google.com/spreadsheets/d/1oef5U9R_JZ7hxmRRNKDCQNia7u-1lRuGk6w3w3LU-p0/edit?usp=sharing)


## Eventy

Na których byliśmy:

- 2 kwietnia - [AMA z Walicj.com](https://twitter.com/DecredCN/status/1245279133082324997) - Internet. DecredCN i Walicj.com wspólnie zorganizowali AMA na grupie WeChat, głównie wprowadzając uczestników do modelu zarządzania w Decred, atomic swapów i dcrdex. Zapis eventu został [umieszczony](http://walicj.com/#/layout/article_detail/16720) na ich stronie. (_pominięty w kwietniu_)
- 23 kwietnia - [Jueves CryptoDrinks Decred](https://twitter.com/Decred_ES/status/1253427311707213824) - Internet. [@elian](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158898257628136ERmQY:decred.org): „To była bardzo swobodna rozmowa wideo z członkami społeczności Blockchain Land, a Decred był jednym z jej gospodarzy. Przedstawiłem krótki brief na temat projektu, a reszta odpowiadała na pytania o krypto w ogólnym sensie (gdzie kupić, jak przechowywać, jak wykrywać oszustwa, przemyślenia na temat halvingu, strategie handlu, czy wydobycie jest opłacalne). Wydarzenie trwało ok. półtorej godziny i gościło 20-25 uczestników". (_pominięte w kwietniu_)
- 28 kwietnia - [Panel ds. bezpieczeństwa w krypto](https://twitter.com/elianhuesca/status/1255293877373800448) - Internet. [@elian](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158898257628136ERmQY:decred.org): „Wydarzenie było zorganizowane przez Binance w języku hiszpańskim i było to coś w rodzaju AMA, ale w kwestii bezpieczeństwa w branży kryptowalutowej, gdzie część pytań dotyczyła tego, jak przechowywać krypto i najlepszych praktyk OPSEC. Miałem parę okazji, aby podkreślić pracę Decred nad hybrydowym blockchainem, DEX-em, oprogramowaniem open source i odpornością na hard forki. Zarówno publiczność, jak i inni goście AMA bardzo dobrze przyjęli wystąpienie". (_przegapione w kwietniu_)
- 2 maja - [Bitconf Live](https://www.eventbrite.com.br/e/bitconf-live-edition-tickets-103094542552) - Internet. Decred był sponsorem. Edilson Osorio Jr, twórca i CEO OriginalMy wygłosił wykład pt. „Wpływ blockchaina podczas pandemii" i wprowadził [nową aplikację](https://devpost.com/software/open-prescription) w celu uwierzytelnienia i walidacji procesu przepisywania leków bez fizycznego kontaktu z pacjentem (Decred jest jednym z 4 łańcuchów blokowych używanych przez aplikację). João Ferreira (@girino) mówił o „Decentralizacji i zarządzaniu”, DEX, atomic swapach, i platformie Politeia, a ta prezentacja była oglądana przez [~2500](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$158859699024140OzoCg:decred.org) ludzi. Filmy są dostępne na [Facebooku](https://www.bitconf.com.br/portal/2020/05/03/assista-as-palestras-da-bitconf-live-edition/) oraz na kanale YouTube [Decred Brasil](https://www.youtube.com/channel/UC73wa2ddXuPWsmenVfeFTYg).
- 6 maja - [Crypto Resources Livestream](https://twitter.com/cryptorc_tech/status/1257765517626130433) - Internet. Transmisja trwała 2 godziny i była oglądana przez ~300 osób. @camilolwi wprowadził uczestników w świat blockchainów i Bitcoina, a następnie @elian mówił o Decred przez prawie godzinę. ([wideo](https://www.youtube.com/watch?v=x2QUGV4ezZQ))
- 7 maja - [Hablemos Decred 5](https://twitter.com/Decred_ES/status/1257774155677630464) - Internet. Na piątej edycji \#HablemosDecred zespół Latam rozmawiał o kryptowalutach i dziennikarstwie z [Fernando Quiros](https://twitter.com/ferquiros_com) z [hiszpańskiego Cointelegraph](https://twitter.com/EsCointelegraph).
- 12 maja - [Consensus: Distributed](https://www.coindesk.com/events/consensus-2020) - Internet. Decred był reprezentowany przez @lukebp w temacie Politei, @matheusd w temacie LN, @chappjc oraz @buck54321 w tematyce dcrdex oraz dcrdata, @Checkmate w kwestii wglądów wyciągniętych z danych on-chain, oraz, oczywiście, przez @jy-p , który przedstawił wysokopoziomowe podsumowanie roku prac rozwojowych nad projektem Decred. Wszystkie linki znajdziecie w sekcji [Media](#media) poniżej.
- 13 maja - [Digital Governance](https://twitter.com/Decred_ES/status/1260574384667983875) - Internet. Ten ~20 osobowy webinar o Decred, zarządzaniu łańcuchem blokowym i zdecentralizowanych walutach cyfrowych został zorganizowany wspólnie z [Hack por la Paz](https://www.facebook.com/HackporlaPaz/). Pytania dotyczyły pojmowania zarządzania w naszym codziennym życiu, tego, jak można to ekstrapolować na waluty cyfrowe i bogactwo oraz wpływu CBDC na rynki kryptowalutowe. ([wideo](https://www.facebook.com/HackporlaPaz/videos/900552810355885/))
- 14 maja - [Panel Zdecentralizowanego Zarządzania](https://twitter.com/Decred_ES/status/1258905004510973953) - Internet. @caibarrad i @adcade reprezentowali Decred w panelu „Czym jest zdecentralizowane zarządzanie i DAO?”, który został zorganizowany wspólnie z BlockchainEx i był częścią rozwoju ekosystemu Decred w Kolumbii. ([wideo](https://www.youtube.com/watch?v=Pvqp_1skrxM))
- 16 maja - [Webinar o fundowaniu projektów typu open source](https://twitter.com/Decred_ES/status/1259984598102093828) - Internet. @victorarubin i @tomee współorganizowali to wydarzenie wraz z Hack Space Peru w ramach współpracy w regionie. @pablito wygłosił prezentację na temat jednego z największych wyzwań związanych z otwartym oprogramowaniem, finansowaniem, zbadał kilkanaście podejść do tematu, a na koniec przedstawił rozwiązanie Decred. ([wideo](https://www.youtube.com/watch?v=UVtOBAAerXk))
- 19 maja - [Latoken Blockchain Economic Forum](https://latoken.com/events/Keynote-133) - Internet. @elian wygłosił 36-minutową prezentację o Decred, finansowaniu i kwestii wydatków na projekty, Politei, LN i wdrażania prywatności. ([wideo](https://www.youtube.com/watch?v=xZvp0us44wo))
- 20 maja - Panel Bitcoin i krypto - Internet. [@elian](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$159001320735424sZqPg:decred.org): „Byłem na panelu dotyczącym przypadków użycia Bitcoin i kryptowalut jako część Business Land w Talent Land, i podkreśliłem Politeię i dcrtime jako infrastrukturę FOSS z przypadkami użycia dla rządów i przedsiębiorstw, i to, jak DAO płaci swoim globalnym pracownikom. Rozmawiałem również o rynku przekazów pieniężnych dla DCR i infrastruktury przetwarzania płatności w celu zwiększenia adopcji". ([wideo](https://www.youtube.com/watch?v=gmWSmxb5yvg))
- 25 maja - [BlockConf Digital](https://blockconf.digital/) - Internet. Decred był [brązowym sponsorem](https://twitter.com/BlockconfD/status/1251194332079697922). Wbrew temu, czego się spodziewano, nie można było stwierdzić, czy ludzie uczestniczą w wirtualnym stoisku i było łatwego sposobu na interakcję z ludźmi. @elian wygłosił przemówienie na temat kryptowalut w Ameryce Łacińskiej oraz brief na temat Decred, Politei, oraz propozycji dla regionu Latam.


## Media

Wybrane artykuły:

- Decred on-chain: puls wydobycia, aut. @PermabullNino ([medium](https://medium.com/@permabullnino/decred-on-chain-mining-pulse-3b28d5155a04))
- Cena Decred: Badanie sezonowości, aut. OneAnalyst ([medium](https://medium.com/coinmonks/decred-price-a-seasonality-study-414bac98bc99))
- W sieci - Decred, aut. Lewis Harland ([formalverification.substack.com](https://formalverification.substack.com/p/in-the-network-decred))
- Bardziej prywatne podejście do stakingu, aut. @jholdstock ([blog.decred.org](https://blog.decred.org/2020/06/02/A-More-Private-Way-to-Stake/))
- Decred. Na rozdrożach, aut. @mrbulb ([github](https://github.com/monsieurbulb/forksintheroad/blob/master/Decred_forks_in_the_road.md))
- Cztery możliwe punkty porażki, aut. Phoenix Green ([medium](https://medium.com/@Phoenixgreen/four-points-of-failure-2b1b2199397b))

Tłumaczenia:

- Nowy rodzaj DEX - [w jęz. hiszpańskim](https://medium.com/decred-es/un-nuevo-tipo-de-dex-8d7b5f8681c9), aut. @francov\_
- Politeia Digest 31 - [w jęz. hiszpańskim](https://medium.com/decred-es/politeia-digest-edici%C3%B3n-31-abril-16-mayo-22-2020-28fc2fc75784), aut. @pablito. Gratulujemy pierwszego tłumaczenia PD!
- Kwietniowy Decred Journal przetłumaczony został na jęz. arabski (@arij), jęz. chiński (@Dominic), jęz. polski (@kozel), oraz jęz. hiszpański (@francov\_). Co więcej, wszystkie cztery tłumaczenia dostępne są na GitHub, Dziękujemy Wam wszystkim!

Wideo:

- Dwutygodniowy update wiadomości Decred z dnia 3 maja 2020, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=oHqzvN3TMU0))
- Decred Construct z udz. deweloperów Luke'a Powell'a w temacie Politei & Matheusa Degiovani na temat LN - Consensus 2020 ([youtube](https://www.youtube.com/watch?v=HexsUmqA7-Y))
- Decred Construct, wywiad nt. DEX z deweloperami Brianem Staffordem oraz Jonem Chappelowem - Consensus 2020 ([youtube](https://www.youtube.com/watch?v=fS9j7RaawjY))
- Sekrety handlu z decredowym analitykiem danych on-chain Checkmate - Consensus 2020 ([youtube](https://www.youtube.com/watch?v=NOyyAx6Ab_0)) - @Checkmate omawia sygnały świadczące o sile przekonania do HODLowania, zrealizowaną cenę, a także MVRV, sumę wartości w puli biletów w okresie 142 dni, wycenę nagrody blokowej, popyt na transakcje oraz wpływy oraz odpływy ze Skarbca
- Przegląd Decred Changelog z udz. project leada Jake'a Yocom-Piatta - Consensus 2020 ([youtube](https://www.youtube.com/watch?v=OmwI62HZerg)) oraz Q&A ([youtube](https://www.youtube.com/watch?v=Uzf2ZGXWoss))
- 365 dni w Decred - CoinDesk ([coindesk.com](https://www.coindesk.com/video/365-decred-days)) - o pełny program o fundamentach Decred. Transmitowany jest przez platformę Zoom, więc jakość nie jest aż tak dobra, jak w źródłach powyżej
- Byczy argument za Decred, metryki on-chain oraz premie/zabezpieczenia monetarne z Checkmatey w Nugget's News ([youtube](https://www.youtube.com/watch?v=QWfq1tn8xs0))
- Akin Sawyerr dołącza do @JillMalandrino w @Nasdaq \#TradeTalks, aby omówić zarządzanie blockchainem celem budowania sprawiedliwszego systemu finansowego dla wszystkich ([youtube](https://www.youtube.com/watch?v=NW-pwO9PUG4))
- Znajdowanie wartości w kryptowalutach - sfera ekonomiczna, społeczna, oraz środowiskowa, aut. Phoenix Green ([youtube](https://www.youtube.com/watch?v=4fwMXos3u3A)) - pierwsze wideo autora na YouTube, po których wyprodukował [6 kolejnych](https://www.youtube.com/channel/UCZSFAqUMp8v58eEQl_bzWYg), które wyjaśniają możliwe sposoby zakupu DCR
- Dwutygodniowy update wiadomości Decred z dnia 22 maja 2020, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=9i56ly5SS6M))

Audio:

- Podcast Gold Goats N Guns, odc. 34 - @jy-p i argument za powrotem do suwerennego pieniądza ([tomluongo.me](https://tomluongo.me/2020/05/19/podcast-episode-34-jake-yocom-piatt-and-the-case-for-a-return-to-sovereign-money/))
- Decred in Depth, odc. 24 - @chappjc i @buck54321 rozmawiają o dcrdex ([libsyn](https://decredindepth.libsyn.com/chappj-buck-the-decred-dex))
- Decred in Depth, odc. 25 - @raedah opowiada o latach pracy nad Decred, począwszy od swojego wkładu w DCP-0001 i dcrdata, aż do nowszych projektów tj. portfele mobilne, stworzeniu grupy deweloperów z Afryki i Azji, oraz nowej propozycji Planet Decred ([libsyn](https://decredindepth.libsyn.com/raedah-planet-decred-development), [soundcloud](https://soundcloud.com/decredindepth/raedah-planet-decred-dcr))
- Rough Consensus, odc. 5 - deflacja, dolary i Decred. @mr.black, @Checkmate, i @PermabullNino dyskutują o halvingu na Bitcoinie , uldze na tradycyjnych rynkach spowodowanej wzrostami notowań, realiach i wpływach deflacji i inflacji na gospodarkę oraz o tym, jak Decred wyróżnia się z tłumu jako niedoceniany kandydat na miano środka przechowania wartości. ([libsyn](https://roughconsensus.libsyn.com/episode-5-deflation-dollars-decred))
- Rough Consensus, odc. 6 - Narracje z udz. Setha Simmonsa. Seth dołącza do spajdermenów, aby omówić to, jak narracje napędzają przestrzeń kryptowalutową. ([libsyn](https://roughconsensus.libsyn.com/episode-6-narratives-with-seth-simmons))


## Dyskusje społeczności

Wiadomości z platform komunikacyjnych:

- Riot wypuścił [wielki update](https://blog.riot.im/e2e-encryption-by-default-cross-signing-is-here/), który został wcielony na chat.decred.org. Szyfrowanie typu end-to-end jest domyślnie włączone dla wszystkich wiadomości prywatnych. Upewnijcie się, że zrobiliście kopię zapasową swoich kluczy, żeby nie stracić dostępu do historii swoich rozmów.

Wybrane wątki z Reddita:

- [post](https://www.reddit.com/r/decred/comments/gnfjci/decred_forks_in_the_road/) aut. @mrbulb o jego artykule „Na rozdrożach” doczekał się 19 komentarzy, głównie od ludzi, którzy byli wdzięczni za napisanie artykułu, lecz trafił się jeden użytkownik, który swoje komentarze usunął
- praktykujący prawnik [nie kryje swojego podziwu](https://www.reddit.com/r/decred/comments/gqewwe/really_impressed_by_decred/) dla Decred
- pre-propozycja dla programu nawiązywania kontaktów w [Iranie](https://www.reddit.com/r/decred/comments/glzckw/preproposal_decredforiran/)
- możliwe zastosowania funkcji tymczasowej blokady, czyli [time lock](https://www.reddit.com/r/decred/comments/gcyquz/decred_timelocks/)

Wybrane dyskusje z Twittera:

- w dzień halvingu na Bitcoinie @ammarooni [przypomina](https://twitter.com/Ammarooni/status/1259985075460063232), że szkoła ekonomii austriackiej zaleca unikanie wprowadzania nagłych zmian w emisji pieniądza
- @lukebp coraz głośniej komunikuje [prace nad platformą](https://twitter.com/lukebp_/status/1258139602516193280) Politeia
- @lukebp [wyjaśnia](https://twitter.com/lukebp_/status/1262871839035977728) Politeię, CMS oraz proces DCC w paru krótkich tweetach
- @lukebp i jego tłumaczenie tego, co widać w konsoli @moo31337 [na angielski](https://twitter.com/lukebp_/status/1263213648471707648) otrzymało lawinę polubień i odpowiedzi w dyskusji nt. mechaniki głosowania nad transakcjami dotyczącymi środków ze Skarbca
- @chappjc [oficjalnie](https://twitter.com/chappjc/status/1267115398610255874) ogłasza dcrdex w fazie pre-alpha na testnecie
- zaktualizowano rynkowe [wykresy](https://twitter.com/BlockCommons/status/1265379141995712512) dla DCR po zakończeniu działalności animatora rynku, dzięki @richardred
- @elian uchyla rąbka [brutalnych realiów](https://twitter.com/elianhuesca/status/1263463096401747970) tego, co stanie się z kontami bankowymi

> Dałem mojemu synowi trochę Bitcoina na Boże Narodzenie i bałem się, że w nie zainteresuje się tematem, bo do tej pory o nim nie wspominał. W zeszłym tygodniu przyszedł do mnie i zapytał „tato, a nie powinniśmy akumulować Decred?” Definiujący moment ojca z synem ([@veganreboot](https://twitter.com/veganreboot/status/1265952035280732160))


## Rynki

W maju kurs wymiany Decred wahał się pomiędzy 12,62-15,66 USD / BTC 0,0014-0,00167. Średni dzienny kurs wynosił 14,11 USD.

[Badanie sezonowości](https://medium.com/coinmonks/decred-price-a-seasonality-study-414bac98bc99) autorstwa OneAnalyst zbadało efekt dnia oraz miesiąca na dzienny zwrot z DCR (wydaje się, że DCR lepiej radzi sobie w soboty).

[Podsumowanie](https://blockcommons.red/publication/mm-phase1-wrapup/) 1. fazy działalności animatora rynku aut. @richardred poddało analizie głębokość ksiąg zamówień na przestrzeni czasu, jak i również innych zasobów, stwierdzając, że DCR nie doczekało się organicznego wzrostu w płynności rynkowej poza tą, która udostępniana była przez i2.

## Ważne kwestie i wiadomości poboczne

Długo oczekiwany trzeci halving emisji Bitcoina miał miejsce 11 maja, dominując przez pewien czas agendę i dyskusje związane z krypto wokół tej daty, a nawet [przebijając się bardziej](https://www.cnbc.com/2020/05/11/bitcoin-halving-heres-what-you-need-to-know.html) do [źródeł](https://www.bbc.co.uk/news/business-52628034) [głównego nurtu](https://www.independent.co.uk/life-style/gadgets-and-tech/features/bitcoin-halving-price-prediction-2020-a9488506.html) - wiele z nich koncentruje się na tym, jaki wpływ to wydarzenie może mieć na cenę.

Jedno z kilku wydarzeń na żywo z tej okazji, siedmiogodzinny livestream zorganizowany przez Cointelegraph, został bezceremonialnie [wstrzymany](https://cointelegraph.com/news/youtube-cancels-cointelegraphs-btc-halving-livestream-for-being-harmful-content) w połowie trwania i usunięty przez YouTube za przedstawianie "szkodliwych treści".

Fundacja Dash Investment zareagowała na pewne tarcia (odrzucone propozycje i prywatną krytykę ze strony masternode'ów), [ogłaszając](https://github.com/DashInvests/dif-communication/blob/master/DIF_Statement_15.05.2020-For_Immediate_Release.pdf), że nie będzie już dążyć do autonomii w podejmowaniu decyzji i ograniczy swoje żądania względem Skarbca Dash, przedstawiając nową strategię VC w drugim kwartale 2020 roku.

Reddit wprowadził nowe, oparte na blockchainie tokeny, które mają być testowane na subreddicie /r/cryptocurrency ([Moony](https://www.reddit.com/r/CryptoCurrency/comments/gj96lb/introducing_rcryptocurrency_moons/)) oraz /r/FortNiteBR ([cegły](https://www.reddit.com/r/FortNiteBR/comments/gj8tm1/introducing_rfortnitebr_bricks/)). Żetony będą przyznawane użytkownikom subredditów w stosunku do ich punktów karmy (50%), 10% dla moderatorów, 20% dla Reddita i 20% dla „szerszej społeczności Reddita". Punkty te, oprócz tego, że służą jako odznaka reputacji na subreddicie, mogą być wykorzystane do odblokowania takich funkcji jak umieszczanie prezentów w komentarzach. Opisano również warianty ankiety ważonych punktami.

Giganci branży tech i dziesiątki rządów zdecydowały, że smartfony mają _zbyt mało backdoorów_ i zainicjowały bezprecedensowy masowy program [nadzoru](https://en.wikipedia.org/wiki/COVID-19_surveillance#Digital_surveillance) (z racji COVID-19). Wiele [technologii](https://en.wikipedia.org/wiki/COVID-19_apps) dodało gdzieś w tytule zapis w stylu „chroniąca prywatność i tym razem mogą być [rzeczywiście bezpieczne](https://en.wikipedia.org/wiki/List_of_data_breaches). Jest nawet obietnica [zamknięcia](https://www.cnet.com/news/apple-and-google-say-they-will-shut-down-covid-19-tracking-tools-once-pandemic-ends/) systemów śledzenia po „zakończeniu pandemii". Pomijając sarkazm, dla użytkowników kryptowalut oznacza to szereg nowych zagrożeń dla prywatności i bezpieczeństwa w ich urządzeniach mobilnych oraz silną zachętę do rozważenia [alternatywnych](https://itsfoss.com/open-source-alternatives-android/) systemów operacyjnych, a nawet sprzętu.


## O tym wydaniu

To 26. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: bee, chappjc, degeri, elian, Exitus, l1ndseymm, richardred
- recenzje i komentarze: davecgh, dnldd, Dominic, emiliomann, jholdstock, jrick, lukebp, matheusd, raedah
- ilustracja tytułowa: saender
