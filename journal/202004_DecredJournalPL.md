# Decred Journal – Kwiecień 2020

![abstrakcja](../img/journal-202004-384.png)

_Obraz: Wertykale pomostowe, aut. @saender_

Najważniejsze wydarzenia z kwietnia:

- Kontynuowane są optymalizacje dla dcrd, które przyspieszyło do tego stopnia, że starsze wersje zaczęły banować połączenia z nimi, wobec czego kryteria banowania muszą zostać zaktualizowane.
- @moo31337 opublikował PR dla trwających prac nad decentralizacją wydatków ze Skarbca projektu.
- Witamy 5 nowych współpracowników w repozytoriach Decred na GitHub!
- To był wielki miesiąc dla integracji, w którym dodano bramki płatności Transak i Metal Pay. Steelbackup (metalowe rozwiązanie do przechowywania ziaren DCR) dodał również nową opcję budżetową.
- Frekwencja w spotkaniach face-to-face spadła, ale wydarzenia wirtualne odnotowują gwałtowną tendencję wzrostową, szczególnie w Ameryce Łacińskiej!


## Rozwój

O ile nie zaznaczono inaczej, prace zgłaszane poniżej mają status „scalonych z repozytorium głównym (master)”. Oznacza to, że prace są ukończone, zrecenzowane i zintegrowane z kodem źródłowym, który zaawansowani użytkownicy mogą kompilować i uruchamiać, ale ich efekty nie są jeszcze dostępne w wersji plików binarnych dla zwykłych użytkowników.

[dcrd](https://github.com/decred/dcrd):

- więcej części bazy kodowej zmigrowało ze standardowych dużych liczb całkowitych Go do wyspecjalizowanych typów pól, co znacznie poprawiło wydajność
- pakiet 'schnorr': poprawa bezpieczeństwa, testowania i działania, jak również kompleksowy dokument [README](https://github.com/decred/dcrd/blob/master/dcrec/secp256k1/schnorr/README.md) opisujący niestandardowy system podpisu oparty na Schnorr stosowany w Decred.

> Podpis Schnorr jest schematem podpisu cyfrowego znanym ze swojej prostoty, sprawdzalnego bezpieczeństwa i skutecznego generowania krótkich podpisów. W porównaniu do podpisów ECDSA ma wiele zalet, które sprawiają, że są one idealne do stosowania, a ich jedyną prawdziwą wadą jest to, że w momencie pisania nie są one dobrze ustandardyzowane.

Podczas gdy zasady konsensusu wspierają sygnatury Schnorr, reszta infrastruktury niezbędna do pełnego wykorzystania ich zalet nie jest dobrze rozwinięta, a zatem nie są one jeszcze w powszechnym użyciu. Celem jest zmiana tego stanu rzeczy.

Przy wszystkich ostatnich pracach, weryfikacja podpisów ECDSA i Schnorr jest około [25% szybsza](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$15862341309060voZvJ:decred.org) w porównaniu do v1.5.1.

Mnóstwo optymalizacji w dcrd dokonanych w ciągu ostatnich miesięcy doprowadziło do [mema](https://twitter.com/degeri_crypto/status/1248522626210897921) „cierpienia na sukces”: starsze węzły uważają teraz, że nowa wersja żąda za dużo danych zbyt szybko i [banują](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$158650272611269MJQhM:decred.org) takie zachowanie. Parametry „tempa banowania” będą musiały być ustawione tak, aby odzwierciedlały nowe prędkości.

Repozytorium dcrd nie jest już skonfigurowane jako fork [btcd](https://github.com/btcsuite/btcd). Dodano tak wiele nowych funkcji i dokonano ogólnych ulepszeń, że istnieje już bardzo mało wspólnego kodu pomiędzy repozytoriami. Ponadto, jednym z głównych powodów posiadania takiego forka jest możliwość łatwego wciągania zmian do głównego repozytorium. Tak jednak już nie jest, ponieważ kod jest tak różny, że wszelkie zmiany, które chcielibyśmy zobaczyć w dcrd i tak musiałyby zostać przeniesione, a nawet wtedy, większość zmian dokonanych w btcd po prostu nie można już odnieść do dcrd. „Odforkowanie” usuwa również zamieszanie związane z liczbą forków, gdzie strona dcrd pokazywała liczbę wszystkich forków z repozytorium btcd (1500+). Teraz pokazuje 235 forków dla dcrd i 1290 dla btcd. Ponadto usuwa to irytację i szansę na błąd, gdzie naciśnięcie przycisku „nowy pull request” otworzyłoby PR wobec repozytorium btcd ze wszystkimi zmianami z głównej gałęzi Decred.

Aplikacja 'dcrctl' wiersza polecenia, która kontroluje dcrd i dcrwallet została wydzielona z dcrd do własnego [repozytorium](https://github.com/decred/dcrctl), aby odnieść się do [problemów](https://github.com/decred/dcrd/issues/2133) z zależnościami i utrzymaniem.

Prace w toku:

- Opublikowano sprawozdanie z [postępów prac](https://github.com/decred/dcrd/pull/2170) nad decentralizacją wydatków ze Skarbca celem nagłośnienia procesu i zachęcenia większej ilości ludzi do wzięcia udziału w dyskusji nad nim. Wysiłek ten opiera się na [propozycji](https://proposals.decred.org/proposals/c96290a2478d0a1916284438ea2c59a1215fe768a87648d04d45f6b7ecb82c3f), lecz dodaje znaczące zmiany do specyfikacji.

[dcrwallet](https://github.com/decred/dcrwallet):

- wprowadzono nowe polecenie ['addtransaction'](https://github.com/decred/dcrwallet/pull/1712), które będzie szczególnie przydatne w nadchodzących pracach nad nowym VSP opartym jedynie na biletach
- poprawki błędów i utrzymanie kodu
- dcrwallet nie jest już forkiem [btcwallet](https://github.com/btcsuite/btcwallet) z tych samych powodów, co dcrd, a na czas pisania posiada 137 własne forki

Prace w toku:

- [wsparcie](https://github.com/decred/dcrwallet/pull/1714) dla prac nad decentralizacją wydatków ze Skarbca odpowiadające pracom w repozytorium dcrd.

[Decrediton](https://github.com/decred/decrediton):

- [pierwsze](https://github.com/decred/decrediton/pull/2448) [kroki](https://github.com/decred/decrediton/pull/2449) ku migracji do komponentów funkcjonalnych (nowsze [podejście](https://programmingwithmosh.com/react/react-functional-components/) we frameworku React - są one łatwiejsze do logicznego ogarnięcia oraz testowania)
- nowa czynność służąca do [porzucania transakcji](https://github.com/decred/decrediton/pull/2467), które nie są wydobywane bądź „utknęły”
- [rozpoczęto](https://github.com/decred/decrediton/pull/2457) ponowne wykorzystanie biblioteki pi-ui dla kilku komponentów celem osiągnięcia spójnego wyglądu oraz odczucia pośród gamy produktów Decred
- pierwsze [kroki](https://github.com/decred/decrediton/pull/2452) ku [wsparciu CSPP](https://github.com/decred/decrediton/issues/2455)

[Politeia](https://github.com/decred/politeia):

- nowa [metoda](https://github.com/decred/politeia/pull/1137) wyszukiwania pozycji w fakturach, które zostały rozliczone w ramach danej propozycji
- [oddzielono](https://github.com/decred/politeia/pull/1175) metadane z propozycji Politeia i faktur CMS - usuwa to niefortunny sposób przechowywania tytułu propozycji, który był wcześniej używany i pozwala na dodawanie dowolnych metadanych, w tym pól wymaganych przez propozycje RFP.
- część pracy pozwalająca na oglądanie Politei [bez javascriptu](https://github.com/decred/politeiagui/pull/1833)
- znormalizowano i dodano [buforowanie](https://github.com/decred/politeiagui/pull/1844) dla danych za ścianą opłat
- [zakończono](https://github.com/decred/politeiagui/pull/1857) [refaktoryzację](https://github.com/decred/politeiagui/issues/1490) systemu zarządzania stanami
- wykonano partię prac związanych z interfejsem użytkownika w celu wsparcia [zapytań ofertowych (RFP)](https://github.com/decred/politeiagui/pull/1820)
- kilka usprawnień UI dla CMS
- różnorakie poprawki błędów w Politei i CMS

[dcrstakepool](https://github.com/decred/dcrstakepool):

- aktualizacja zależności oraz poprawki błędów

[dcrpool](https://github.com/decred/dcrpool):

- dodano [bufor](https://github.com/decred/dcrpool/pull/180), co poprawiło przepływ danych (hub teraz wypycha nowe dane do bufora zamiast interfejsu graficznego wysyłającego zapytania o nie)
- dodano paginację w kilku miejscach - jest to dopełnienie pracy nad [właściwym UI](https://github.com/decred/dcrpool/issues/146) przez projektantów
- konfigurowalne [konto](https://github.com/decred/dcrpool/pull/191) do wypłaty nagród
- dodano GUI do ręcznej [prośby o płatność](https://github.com/decred/dcrpool/pull/198) i wyczyszczenia pozostałego salda (przydatne przy opuszczaniu puli)
- zwiększono pokrycie testami

[dcrlnd](https://github.com/decred/dcrlnd): Prace w toku:

- uruchomienia i testy nad [trybem SPV](https://github.com/decred/dcrlnd/pull/95) dla zdalnych portfeli (opisane precyzyjniej w [wydaniu marcowym](202003.md#development))
- [przeniesienie](https://github.com/decred/dcrlnd/pull/99) zmian z głównego repozytorium lnd między wersjami v0.9.0-beta oraz 0.10.0-beta - w sumie 139 PR-y (plus parę commitów) zostały przeanalizowane pod kątem scalenia.

[dcrdex](https://github.com/decred/dcrdex):

- System [powiadamiania](https://github.com/decred/dcrdex/pull/244) umożliwiający aktualizacje na żywo w GUI przeglądarki
- [serwer sieciowy](https://github.com/decred/dcrdex/pull/221) dla poleceń administratora
- [szyfrowanie](https://github.com/decred/dcrdex/pull/259) dla klucza do podpisywania
- ustawienia [anarchii](https://github.com/decred/dcrdex/pull/268)
- ukończono [stronę rynków](https://github.com/decred/dcrdex/pull/278)
- [bezpieczne wprowadzanie](https://github.com/decred/dcrdex/pull/246) wrażliwych argumentów z wiersza poleceń
- poprawki błędów, refaktoryzacja kodu, usprawnienia logowania i testowania

[dcrandroid](https://github.com/decred/dcrandroid):

- przemodelowano [stronę produktową](https://github.com/decred/dcrandroid/pull/451)
- [zmiana widoku](https://github.com/decred/dcrandroid/pull/461) między DCR a odpowiednikiem w fiat na stronie wysyłania poprzez kliknięcie
- dodano tłumaczenie na jęz. [francuski](https://github.com/decred/dcrandroid/pull/423)
- inne zmiany w UX i poprawki błędów

[dcrios](https://github.com/raedahgroup/dcrios):

- wsparcie dla uwierzytelniania [biometrycznego](https://github.com/raedahgroup/dcrios/pull/613) przy uruchamianiu z wykorzystaniem Touch ID lub Face ID
- przemodelowano [stronę produktową](https://github.com/raedahgroup/dcrios/pull/615) oraz [scalono](https://github.com/raedahgroup/dcrios/pull/628) ją z konfiguracją portfela
- nowa strona [statystyk](https://github.com/raedahgroup/dcrios/pull/627) wraz z aktualizacjami w [czasie rzeczywistym](https://github.com/raedahgroup/dcrios/pull/666)
- powiadamianie [sygnałem dźwiękowym](https://github.com/raedahgroup/dcrios/pull/667) przy dołączeniu nowych bloków do łańcucha
- zmiany w UX i poprawki błędów

[dcrdata](https://github.com/decred/dcrdata):

- [optymalizacja](https://github.com/decred/dcrdata/pull/1690) i refaktoryzacja [bazy danych](https://github.com/decred/dcrdata/pull/1720) dla wykresu monet mieszanych
- nowe API do zapytania o [istnienie](https://github.com/decred/dcrdata/pull/1714) adresów
- nowe proste API dla [ilości monet w obiegu](https://github.com/decred/dcrdata/pull/1697)
- wyszukiwanie [outpointów transakcji](https://github.com/decred/dcrdata/pull/1711)
- poprawki błędów

Szczegółowe instrukcje na temat tego, jak [wysyłać zapytania do dcrdata](https://stakey.club/en/querying-dcrdata/) i jak uruchomić [własną instancję](https://stakey.club/en/dcrdata-running-your-own-block-explorer/) eksploratora bloków zostały opublikowane przez @mm zarówno w języku angielskim, jak i [portugalskim](https://stakey.club/pt/articles/).

[tinydecred](https://github.com/decred/tinydecred):

- [formularze i ustawienia](https://github.com/decred/tinydecred/pull/156) niezbędne do podłączenia z dcrd
- podstawowe wsparcie dla [filtrów GCS](https://github.com/decred/tinydecred/pull/149)
- dalsze zwiększenie zasięgu testów w [krucjacie](https://github.com/decred/tinydecred/issues/70) po bezlitosny zestaw testów
- wszystkie testy zostały przeniesione do [pytest](https://github.com/decred/tinydecred/pull/161)
- zwiększono wydajność podstaw kryptograficznych za pomocą [Cython](https://github.com/decred/tinydecred/pull/160), skracając czas wykonania testów z 21 do 4 sekund (szybkie testy umożliwiają produktywny rozwój i są źródłem radości w życiu)

[docs](https://github.com/decred/dcrdocs):

- [dodano](https://github.com/decred/dcrdocs/pull/1087) [stronę](https://docs.decred.org/advanced/mnemonic-seed/) dokumentującą różnice między ziarnami Decred i BIP-0039

[decred.org](https://github.com/decred/dcrweb):

- usprawnienia [trybu nojs](https://github.com/decred/dcrweb/pull/875)
- zaktualizowano listę giełd wymian, kantorów i procesorów płatniczych

Pozostałe:

- narzędzie do budowania odtwarzalnych [wersji do wydania](https://github.com/decred/release) plików wykonywalnych zostało przeniesione pod organizację 'decred' na GitHub
- @Checkmate opublikował [obliczenia](https://github.com/checkmatey/checkonchain/blob/master/research_articles/checkonchain_charts/checkonchain_charts.md) odnośnie wdrożenia swoich metryk
- GitHub udostępnił wszystkie podstawowe funkcje [bezpłatnie dla wszystkich](https://help.github.com/en/github/getting-started-with-github/faq-about-changes-to-githubs-plans), w co wchodzą prywatne repozytoria dla nieograniczonej liczby użytkowników.

Statystyki aktywności deweloperskiej za kwiecień: 313 aktywne PR-y, 247 commity do gałęzi master, 39K dodanych i 23K usuniętych linijek kodu spośród 16 repozytoriów. Wkład pochodził od 2-7 deweloperów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: @jdambron ([dcrandroid](https://github.com/decred/dcrandroid/commits?author=jdambron)), @matthawkins90 ([dcrd](https://github.com/decred/dcrd/commits?author=matthawkins90)), @leRequinNoir ([dcrdata](https://github.com/decred/dcrdata/commits?author=leRequinNoir)), @kevinstl ([dcrdex](https://github.com/decred/dcrdex/commits?author=kevinstl)) oraz @chillviben ([dcrios](https://github.com/raedahgroup/dcrios/issues?q=is%3Aissue+author%3Achillviben)).

Statystyki społeczności na 1 maja:

- Obserwujący na Twitterze: 40 570 (-124)
- Subskrybenci na Reddit: 9761 (+1)
- Użytkownicy na Matrixie: 624 (+23)
- Użytkownicy na Discordzie: 1184 (+24)
- Użytkownicy na Telegramie: 2557 (-50)
- Subskrybenci na YouTube: 3990 (+10)
- Obserwujący na Facebooku: 3618 (+12), polubień: 3280 (+7)
- Obserwujący na LinkedIn: 774 (+30)
- GitHub: 539 gwiazdki (+3) i 235 forków repozytorium dcrd (-1272) - poprzednia metryka zawierała wszystkie forki repozytorium btcd, co mogło wprowadzać w błąd. Teraz, gdy związek z forkami btcd został formalnie uregulowany liczba ta przedstawia forki jedynie repozytorium dcrd


## Zarządzanie

W kwietniu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 13 250 DCR i wydał 17 228 DCR. Stosując średni dzienny kurs DCR/USD z kwietnia w wysokości 12,34 USD, otrzymano 164 tys. USD i wydano 213 tys. USD. Przy średnim dziennym kursie z marca wynoszącym 13,40 USD, kwota dolarowa naliczona za prace wykonane w tym miesiącu wynosi 234 tys. Na dzień 3 maja saldo Skarbca wynosi 636 000 DCR (9,17 mln USD po kursie 14,42 USD).

W kwietniu złożono dwie nowe propozycje; [jedna](https://proposals.decred.org/proposals/bce7bf3cd1f74d571d23ac8a330ddf29a14a547ed0cc9c995f1a97dce733d1e1), na kampanię reklamową w formie billboardów, została odrzucona z akceptacją na poziomie 17% głosów na „tak” (31% frekwencja) a [druga](https://proposals.decred.org/proposals/83b59ef5ab40193a86073abbd93cea13ed6d071eecc78918ab5cf98cba7c7a67) od CryptoNoticias, na kampanię marketingową w postaci tworzenia treści również została odrzucona z poparciem na poziomie 31% i 30% udziałem głosujących.

Odrzucono również dwie propozycje z marca, dla których głosowanie odbyło się w tym miesiącu. Propozycja [DCR Comic 2](https://proposals.decred.org/proposals/2f08f8518bc7672069a10ac6461fd9ab341d4a9e4c343fd4a7ec426250f3896f) uzyskała poparcie 49,4% głosujących (przy udziale 19% głosujących), natomiast propozycja [Decred Daily](https://proposals.decred.org/proposals/7d42c6f4bf3059b64789185af615c1df97cb61a379425933be5ff01d074ed4d5) uzyskała 44% poparcia od 17% głosujących. Żadna z tych propozycji nie przekroczyła wymaganego kworum wynoszącego 20% głosów.

Więcej szczegółów na ten temat głosowań przeprowadzonych w tym okresie można znaleźć w [numerze 30](https://blockcommons.red/politeia-digest/issue030/) Politeia Digest.


## Sieć

Hashrate: [kwietniowy hashrate](https://explorer.dcrdata.org/charts?chart=hashrate&zoom=k8f3rvwm-k9oqhibz&scale=linear&bin=block&axis=time) na początku miesiąca wyniósł ~302 Ph/s, a zamknął miesiąc w ok. 360 Ph/s, zaliczając niż w ok. 240 Ph/s oraz szczyt w wys. 470 Ph/s w ciągu miesiąca. [Dystrybucja mocy obliczeniowej](https://dcrstats.com/pow) na 1 maja wyglądała następująco: UUPool 46%, Poolin 22%, lab.antpool.com 17%, F2Pool 2%, Luxor 2%, BTC.com 1,6%, BeePool 0,12%, CoinMine 0,05%, Suprnova 0,02% i pozostałe ~9%. Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu [z okresu 30 dni](https://dcrstats.com/) wynosiła 137,8 DCR (-4,1). [Cena](https://explorer.dcrdata.org/charts?chart=ticket-price&zoom=k8f3rvwm-k9oqhibz&bin=window&axis=time&visibility=true-false&mode=stepped) wahała się między 131,7-142,8 DCR. [Zablokowana kwota](https://explorer.dcrdata.org/charts?chart=ticket-pool-value&zoom=k8f3rvwm-k9oqhibz&scale=linear&bin=block&axis=time) wynosiła 5,62-5,71 mln DCR, co odpowiadało 49,2-50,3% dostępnej podaży [biorącej udział](https://explorer.dcrdata.org/charts?chart=stake-participation&zoom=k8f3rvwm-k9oqhibz&scale=linear&bin=block&axis=time) w elemencie PoS.

Węzły: przez [kwiecień](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1585699200000&to=1588291200000) było około 131 węzłów nasłuchujących i 206 w sumie za danymi z dcr.farm. Średnia dystrybucja wersji na kwiecień wygląda następująco: 44% korzysta z dcrd v1.5.1, 16% to dcrd v1.5, 6% używa dcrd v1.6 w wersji deweloperskiej, 5% korzysta z dcrd v1.5 w wersji deweloperskiej i buildów RC, 4% korzysta z dcrd v1.4, 9% to dcrwallet v1.5.1, 2,4% używa dcrwallet v1.4, a 1,5% korzysta z dcrwallet v1.5.


Nowości od @Checkmate:

- Sekcja biuletynu [OurNetwork](https://ournetwork.substack.com/p/our-network-issue-15) poświęcona Decred ([tweet](https://twitter.com/_Checkmatey_/status/1247649984473894912)). Wielorakie wskaźniki oparte na modelu Stock-to-Flow @Checkmate, dochodach górników PoW oraz badaniach danych z biletów @permabullnino sygnalizują, że sieć jest zbyt nisko wyceniana.
- Znaczny wolumen on-chain w stosunku do wyceny sieci, [wskaźniki NVT i RVT](https://twitter.com/_Checkmatey_/status/1252754120345182210).
- Wzrost [wolumenu transakcji](https://twitter.com/_Checkmatey_/status/1255084712386654209) z powodu zwiększonego wykorzystania funkcji prywatności.

## Integracje

VSP [dcr.blue](https://dcr.blue/) w zweryfikowanej wiadomości wysłanej 20 kwietnia do wszystkich użytkowników ogłosił, że zamyka działalność. Usługodawca ten został [usunięty](https://github.com/decred/dcrwebapi/pull/97) z [działu VSP](https://www.decred.org/vsp/) na stronie internetowej Decred i Decrediton, ale pozostanie online do końca 2020 roku. Ponieważ maksymalny czas życia biletu wynosi około 4,7 miesiąca, daje to użytkownikom około 3 miesięcy na zaprzestanie zakupu biletów przypisanych do DCR.Blue. Użytkownicy powinni wykonać kopię zapasową swoich skryptów do wykupu, jeśli jeszcze tego nie zrobili (kopia jest dostępna na koncie VSP) i zacząć kupować bilety przez innego VSP. Uprasza się o niedołączanie do zbyt dużych VSP, aby utrzymać zdrową dystrybucję biletów i lepsze bezpieczeństwo sieci. Jest to pierwszy VSP, który podjął próbę „wdzięcznego zamknięcia”, zamiast zniknięcia bez uprzedzenia, jak to miało miejsce w przeszłości w przypadku innych VSP.

VSP [decred.raqamiya.net](https://decred.raqamiya.net/), który został [usunięty z listy](https://github.com/decred/dcrwebapi/pull/95) w marcu, jest teraz znów aktywny i został [z powrotem dodany](https://github.com/decred/dcrwebapi/pull/96) do listy. Na dzień dzisiejszy posiada około 330 biletów gotowych do głosowania (0,8%), ma 4 serwery i posiada własny UI.

Metal Pay [dodał](https://twitter.com/metalpaysme/status/1249745420206686208) [wsparcie](https://blog.metalpay.com/metal-pay-welcomes-decred/) dla DCR w swojej usłudze. Daje to kolejną rampę wejściową fiat i działa w większości stanów w USA. Swoje ogłoszenie okrasili też garstką [tweetów](https://twitter.com/metalpaysme/status/1250424090172612615) o Decred.

[Transak](https://global.transak.com/) [ogłosił](https://twitter.com/transak_finance/status/1256654711412776961), że wymiana między DCR oraz EUR, GBP i INR jest [dostępna](https://global.transak.com/?defaultCryptoCurrency=DCR) w ich usłudze bramki płatniczej fiat < > krypto. Para z USD pojawi się wkrótce.

Błyskawiczna giełda wymian [SwapSpace](https://swapspace.co/) [dodała](https://twitter.com/SwapSpaceCo/status/1250078395884539906) wsparcie dla Decred.

[Steelbackup](https://steelbackup.com/), fizyczne rozwiązanie do tworzenia kopii zapasowych ziaren dodało [wersję light](https://twitter.com/steelbackup/status/1248058631523905538) swojego produktu. Obecnie istnieją dwa rodzaje blach stalowych: [grawerowane laserowo](https://steelbackup.com/product/decred-laser-engraved/) oraz [znakowane laserowo](https://steelbackup.com/product/decred-laser-marked/). Ta wygrawerowana jest najbardziej wytrzymałym rozwiązaniem, ponieważ stal jest usuwana, co sprawia, że siatka znakująca jest równie trwała jak stal. Produkt znakowany laserowo jest oznaczany roztworem dwusiarczku molibdenu, co czyni go odpornym na zarysowania, kwasy i wysokie temperatury (do 340 stopni C). Produkty są zaprojektowane tak, aby były proste, bez ruchomych części, a użytkownicy potrzebują tylko stempla centrującego (do zakupienia w lokalnym sklepie z narzędziami), aby wybić na blachach swoje ziarno. W zestawie znajdują się torby z zabezpieczeniem antysabotażowym. SteelBackup został wprowadzony na rynek w lutym 2020 roku przez @zubair i wysyła swoje produkty na cały świat.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.


## Nawiązywanie kontaktów

Decredowy [kanał YouTube](https://www.youtube.com/decredchannel) powiększył się o 4 nowe filmy, natomiast podcasty Decred in Depth oraz Rough Consensus wydały w sumie 3 odcinki (więcej w dziale [Media](#media) poniżej).

Kanał [Decred Brazil](https://www.youtube.com/channel/UC73wa2ddXuPWsmenVfeFTYg) nadal aktywnie generuje treści. Decred Semanal („Decred Weekly”) opublikował w kwietniu 5 nowych odcinków, które otrzymały średnio ~150 odsłon w porównaniu do ~50 odsłon w poprzednich miesiącach (prawdopodobnie w wyniku [ulepszonej](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$158896614628001Awmom:decred.org) strategii dystrybucji). Seria jest również dostępna w formacie podcastów na wszystkich głównych platformach takich jak [Apple](https://podcasts.apple.com/podcast/decred-brasil/id1451017413) (łącznie 59 odcinków), Google, Spotify, [SoundCloud](https://soundcloud.com/decredbrasil) i innych.

Na Medium, [Decred Drive](https://twitter.com/decreddrive) stale dostarcza cotygodniowych aktualizacji, [Decred Spanish](https://medium.com/decred-es) dodaje nowe artykuły i tłumaczenia, a [Phoenix Green](https://medium.com/@kencameron77) pojawił się ze swoimi opisami na temat swojej podróży z krypto/Decred.

@jy-p wypowiedział się w kwestii emisji pieniądza fiat oraz pracy zdalnej w ankiecie projektowej przeprowadzanej przez [8btc.com](https://news.8btc.com/8btc-interview-cryptos-and-coronavirus-what-we-learned-from-foreign-communities). 8btc jest najstarszym forum Bitcoin w Chinach.

PR-owe osiągnięcia Monde za kwiecień:

- stworzyliśmy i rozwinęliśmy artykuł skierowany do publikacji inwestycyjnych, VC i świata technologii.
- stworzyliśmy i rozwinęliśmy artykuł skierowany do publikacji o tematyce krypto i fintech.
- stworzyliśmy i rozwinęliśmy artykuł skierowany do publikacji z dziedziny finansów osobistych
- zgłosiliśmy komentarze od przedstawicieli Decred do 8 artykułów o tematyce bieżącej
- zdobyliśmy wywiad z mediami mainstreamowymi oraz 3 e-mailowe sesje Q&A z publikacjami mainstreamowymi i z tematyki kryptowalutowej

Obecność w mediach dzięki Monde PR:

- pionierski artykuł w [ValueWalk](https://www.valuewalk.com/2020/04/open-source-response-covid-19/), aut. @richardred
- artykuł w [Cointelegraph](https://cointelegraph.com/news/harsh-stablecoin-recommendations-from-g-20-are-a-step-in-the-right-direction-but-regulators-need-more-education) zawierający komentarz @jy-p na temat przyszłości stablecoinów, powielony w [Investing.com](https://www.investing.com/news/cryptocurrency-news/g20s-harsh-stance-on-stablecoin-is-a-step-forward-but-regulators-have-more-to-learn-2144200) i [Bitcoin News Network](https://www.btcnn.com/harsh-stablecoin-recommendations-from-g-20-are-a-step-in-the-right-direction-but-regulators-need-more-education/).

## Eventy

Na których byliśmy:

- 4 kwietnia - [Paxful Conversations](https://twitter.com/paxful_LATAM/status/1245066931155148800) - Internet. @elian został zaproszony przez Paxful LATAM do rozmowy o tym, jak rozpoznawać oszustwa i na co należy zwracać uwagę podczas analizy fundamentalnej w krypto. Nie była to rozmowa bezpośrednio związana z Decred, ale została ona wymieniona jako przykład dobrych praktyk w branży. Webinar był „powered by Decred” i został obejrzany przez ~70 osób.
- 9 kwietnia - Hablemos Decred 03 - Internet. @pablito i @elian wyjaśnili system PoS. Tym razem było tylko 3 nowych widzów, choć wyciągnięto z tego faktu pewne wnioski na temat promocji wydarzeń i wyboru optymalnego czasu. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200409-hablemosdecred-03-internet.md))
- 16 kwietnia - [Jalisco Talend Land @ Home](https://www.talent-land.tv/) - Internet. Zespół Decred przedstawił panel zatytułowany „Przyszłość pieniędzy i pracy zdalnej” w celu zbadania płaszczyzny przecinania się pieniędzy, technologii i pracy zdalnej przez obiektyw i doświadczenia 4 wykonawców Decred w Ameryce Łacińskiej. Podzielili się oni swoimi doświadczeniami z pracy w Argentynie, Kolumbii i Meksyku, a także omówili wyzwania i możliwości pracy zdalnej dla Decred. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200416-talent-land-at-home-internet.md))
- 16 kwietnia - Hablemos de Criptomonedas - Internet. Webinar został zorganizowany we współpracy z Uniwersytetem Ibero poprzez centrum innowacji IDIT. @adcade i @elian opowiadali o kryptowalutach i technologii blockchain 22 osobom (na 34 zarejestrowane), głównie studentom. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200416-hablemos-de-criptomonedas-internet.md))
- 23 kwietnia - Hablemos Decred 04 - Internet. @pablito i @elian koncentrują się na giełdach i DEX-ie, który Decred buduje. Tym razem frekwencja wyniosła do 15 osób, a zespół LATAM kontynuuje poszukiwania najlepszych sposobów na organizację tego typu imprez. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200423-hablemosdecred-04-internet.md))
- 30 kwietnia - [Wirtualny meetup Decred](https://www.meetup.com/Decred-Australia/events/270252645/) - Internet. @Checkmate zaprezentował swoją analizę on-chain dla BTC i DCR. Nagranie zostało zamieszczone w serwisie [YouTube](https://www.youtube.com/watch?v=H_COE9A-t3I).

Na których będziemy:

- 12 maja - [Podstawy Decred na Consensus Distributed](https://next.brella.io/events/consensusdistributed/schedule/118434) (wymaga wpisania się na brella.io, aby oglądać i „uczestniczyć”) - Internet. Consensus Distributed jest zdalnym zamiennikiem dla corocznej konferencji Consensus, a Decred jest jednym z projektów, który został zaproszony do zaprezentowania godziny materiału, w podziale na 3 segmenty. W Construct, @richardred rozmawia z uczestnikami niektórych ważnych podprojektów Decred, aby dowiedzieć się, na czym polegają i jakie są najświeższe doniesienia. Gośćmi są @lukebp, który opowiada o Politei, @matheusd wyjaśnia dcrlnd, a @chappjc, oraz @buck54321 omawiają dcrdex, dcrdata i TinyDecred. Drugim segmentem jest Trade Secrets, gdzie @Checkmate przeprowadzi szybkie wprowadzenie do swoich 5 ulubionych wskaźników on-chain dla Decred. Na zakończenie @jy-p zaprezentuje w ChangeLogu przegląd postępów roku we wszystkich głównych aspektach projektu, a następnie odbędzie się 10 minutowe Q&A na żywo z Lucasem Nuzzi. Następnie wideo będzie dostępne na stronie Coindesk, a rozszerzona wersja Trade Secrets zostanie wgrana na Youtube.
- 14 maja - [Wirtualny meetup z BlockchainEx](https://twitter.com/Decred_ES/status/1258905004510973953) - Internet. Decred weźmie udział w panelu „Czym jest zdecentralizowane zarządzanie oraz DAO?”, którego współgospodarzami są @adcade i @caibarrad z Decred, Nadia Alvarez z MakerDAO, Gustavo Segovia z Colony i Jhonny Gomez z BlockchainEx. Ten panel będzie transmitowany na żywo do społeczności blockchain w Kolumbii.
- 14 maja - [Meetup Decred z BlockConf](https://twitter.com/Decred_ES/status/1258165218204618759) - Internet. Będzie to wirtualne spotkanie mające na celu zaprezentowanie platformy oraz pogawędkę przed główną konferencją. Zespół przedstawi brief na temat podstaw Decred i nowych wydarzeń, które są na horyzoncie.
- 25 maja - [BlockConf](https://blockconf.digital/) - Internet. Decred jest [brązowym sponsorem](https://twitter.com/BlockconfD/status/1251194332079697922). Zespół Decred LATAM będzie prowadził dla Decred wirtualne stoisko, aby odpowiadać na pytania uczestników. Jeśli ktoś chciałby pomóc w utrzymaniu aktywnego stoiska w kilku strefach czasowych podczas 48-godzinnej imprezy, prosimy o kontakt z @elian.


![Ujęcie z Jalisco Talent Land @ Home](../img/latam-stakeys-360.jpg)

_Obraz: Stakey'ego w Ameryce Lacińskiej nie brakuje_

## Media

Wybrane artykuły:

- Decred on-chain: Kapitalizacja rynku oraz współczynniki najsilniejszych rąk, aut. @PermabullNino ([medium](https://medium.com/@permabullnino/decred-on-chain-stronomast-hand-market-cap-ratio-146d6854e1d6))
- Monitorowanie animatorów rynku Decred - podsumowanie fazy 1, aut. @richardred ([blockcommons.red](https://blockcommons.red/publication/mm-phase1-wrapup/))
- Our Network #15 - zawierające aktualizacje nt. Decred od @Checkmate ([substack.com](https://ournetwork.substack.com/p/our-network-issue-15))
- Propozycja zarządzania w Decred: Ochrona Skarbca, aut. Phoenix Green ([medium](https://medium.com/phoenix-green/decred-governance-proposal-protecting-the-treasury-2bcab84800ad))
- Finanse 2.0, aut. Phoenix Green ([medium](https://medium.com/@kencameron77/finance-2-0-5dea40e4b60e))
- Mindset open-source dla finansów, aut. Phoenix Green ([medium](https://medium.com/@kencameron77/open-sourced-finance-7ce8a3fdb648)) - nawołuje do  zbiorczego myślenia i znalezienia punktów zbieżnych oraz wymienia narzędzia do budowania społeczności
- 3 rzeczy, które każdy powinien wiedzieć o kryptowalutach, aut. Phoenix Green ([medium](https://medium.com/@kencameron77/3-things-everyone-should-know-about-cryptocurrencies-e38c3db4127b))
- Bitcoinowy wehikuł czasu, aut. Phoenix Green ([medium](https://medium.com/@kencameron77/the-bitcoin-time-machine-29f228656cd3)) - porównanie Bitcoina z Decred
- Co by było, gdyby Bitcoin miał Skarbiec?, aut. Ryan Watkins ([messari.io](https://messari.io/article/what-if-bitcoin-had-a-treasury), dostęp płatny)
- Wywiad na temat projektu Decred, aut. The Capital (dawny Altcoin Magazine, [medium](https://medium.com/the-capital/project-rundown-interview-with-decred-on-the-capital-8b647919a339))
- Porozmawiajmy o Decred oraz pracy zdalnej, aut. @adcade (w jęz. hiszpańskim, [medium](https://medium.com/decred-es/hablemos-decred-sobre-el-proyecto-y-sobre-el-trabajo-remoto-e5a2510364ae))
- Artykuł dotyczący czwartego wirtualnego spotkania Decred na temat centralnych oraz zdecentralizowanych giełd wymian (w języku hiszpańskim, [es.cointelegraph.com](https://es.cointelegraph.com/news/decred-organizes-virtual-meeting-on-decentralized-exchanges-for-the-spanish-speaking-community))


Tłumaczenia:

- „Sekrety przeoczone na DevConie: jak naprawdę wygląda działające DAO” - [w jęz. portugalskim](https://stakey.club/translated/working-dao/), aut. @mm.
- Wydanie Decred Journal z marca 2020 przetłumaczone zostało na jęz. arabski (@arij), jęz. chiński (@Dominic), jęz. polski (@kozel), oraz jęz. hiszpański (@francov\_). @kozel powraca z czterema przetłumaczonymi wydaniami od grudnia. Skrócone wersje w jęz. hiszpańskim dostępne są na [Medium](https://medium.com/decred-es/revista-2020/home). Dziękujemy Wam za szerzenie świadomości o projekcie!

Wideo:

- DCR 101 - Praca dla DAO Decred, aut. @Exitus ([youtube](https://www.youtube.com/watch?Ud4LVhFwL9g))
- Dwutygodniowy update wiadomości Decred - 18 kwietnia 2020 r., aut. @Exitus ([youtube](https://www.youtube.com/watch?v=3TLeEO8Mz1k))
- Wirtualny meetup Decred Australia - analiza danych on-chain dla BTC & DCR z @Checkmate ([youtube](https://www.youtube.com/watch?v=H_COE9A-t3I))
- Medium Andre ma dobre przeczucie odnośnie tego, co się dzieje; film jest głównie o Rezerwie Federalnej, ale na temat Decred Andre mówi, że „są w porządku” ([youtube](https://www.youtube.com/watch?v=ddjelXN5KZs))
- Rezerwa Federalna własnymi słowami. Chroń swoje bogactwo, kupuj zdecentralizowane kredyty ([twitter](https://twitter.com/coveryfire7777/status/1246169256020107266))
- DCR 101 - Jak brać udział w stakingu Decred, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=m5lcm6yttEk))
- Analiza ceny Decred - 17 kwietnia 2020 r., aut. Brave New Coin ([youtube](https://www.youtube.com/watch?v=Q33i6xK_SPg))

Audio:

- Rough Consensus, odc. 4 - Złoto, Bitcoin, i Decred. @mr.black, @Checkmate i @PermabullNino omawiają stan rynków makro i kryptowalutowych w kontekście załamujących się gospodarek i nieograniczonej luzowania ilościowego. Rozmowa rozważa naturę solidnego pieniądza i to, jak złoto, Bitcoin i Decred reprezentują różne obszary jego. ([libsyn](https://roughconsensus.libsyn.com/rough-consensus-4-gold-bitcoin-and-decred))
- Decred in Depth - Podsumowanie nr 2 z udziałem @mr.black, @Checkmate oraz @PermabullNino. ([libsyn](https://decredindepth.libsyn.com/dcr-round-up-2-with-checkmate-permabull-nio), [youtube](https://www.youtube.com/watch?v=eb_GFdOkjwA), [soundcloud](https://soundcloud.com/decredindepth/dcr-round-up-2-with-checkmate))
- Decred in Depth (zrezygnowano z numeracji) - Chris Burniske z Placeholder VC mówi o ostatnich wydarzeniach, dlaczego Decred MA to „coś” (bo jest, z jęz. angielskiego, *Hypersecure, Adaptable, Sustainable*), możliwościach dcrdex i Politei do rozszerzenia ekosystemu Decred, i wiele więcej! ([libsyn](https://decredindepth.libsyn.com/chris-burniske-institutional-investment-dcr-as-a-sov-current-events-dcr-custody-solutions), [youtube](https://www.youtube.com/watch?v=Q4wbt0JLA5k), [soundcloud](https://soundcloud.com/decredindepth/chris-burniske-crypto-in-the))

## Dyskusje społeczności

Wybrane wątki z Reddita:

- Regularny [post](https://www.reddit.com/r/decred/comments/fy493y/decred_journal_march_2020/) o publikacji Decred Journal był najbardziej omawianym w tym miesiącu na naszym subreddicie z 42 komentarzami!
- Dyskusja na temat pomysłu autorstwa @bee, aby dodać [powód głosowania](https://github.com/decredcommunity/issues/issues/118) do głosów na platformie Politeia [doprowadziła do wniosku](https://www.reddit.com/r/decred/comments/g2ozqc/reason_bits_for_politeia_no_votes_feature_idea/), że jego prawidłowe wdrożenie wymaga rozwiązania w zakresie ochrony prywatności, takiego jak system głosowania w ciemno.
- [Dyskusja](https://www.reddit.com/r/decred/comments/g5he83/decred_market_maker_monitoring_phase_1_wrapup/) nad raportem z fazy 1 działalności animatora rynku Decred spekulowała na temat tempa adopcji Decred.
- Wątek pt. [Perspektywy](https://www.reddit.com/r/decred/comments/g66onn/perspectives/) zebrał 33 komentarze, z których wiele to dokładnie sformułowane i wyartukułowane, wysokiej jakości przemyślenia.
- Mini-gra pt. [Decred: Do Different](https://www.reddit.com/r/decred/comments/g66msa/decred_challenge_do_different/).
- [Post](https://www.reddit.com/r/decred/comments/fyi49j/checkmate_on_twitter_cost_to_launch_a_1hr_double/) omawiający metodologię @Checkmate odnośnie porównywania kosztu ataku na Decred oraz inne łańcuchy.


Wybrane dyskusje z Twittera:

- @Checkmate [zatweetował](https://twitter.com/_Checkmatey_/status/1248498765113126912) o kosztach ataku podwójnego wydatkowania w DCR będących 54x droższymi, niż w przypadku BTC, co bardzo ożywiło dyskusję na ten temat.
- @Checkmate [ogłosił](https://twitter.com/_Checkmatey_/status/1253116008639811585) rozpoczęcie nowego projektu wraz z zespołem współpracowników pracujących nad nową stroną metryk on-chain dla Decred.
- Messari [duma](https://twitter.com/MessariCrypto/status/1255579343973232640) na temat tego, co by było, gdyby Bitcoin miał taki skarbiec, jak Decred, oraz [pokazuje na wykresach](https://twitter.com/MessariCrypto/status/1255579345319596033), ile byłby on wart, gdyby Bitcoin wydawał ~23% swojego miesięcznego przychodu do skarbca i oszczędzał resztę.
- @moo31337 [tweetuje](https://twitter.com/marco_peereboom/status/1251174260925779977) o PR-rze dotyczącym prac w toku nad propozycją decentralizacji wydatków ze Skarbca, ale ponad połowa komentarzy tak naprawdę była zaciekawiona jego kolejną kulinarną przygodą.


![wieprzowinka](../img/marco-cooking.jpg "pork")

## Rynki

W kwietniu kurs wymiany Decred wahał się pomiędzy 11,08-15,01 USD / BTC 0,00151-0,00179. Średni dzienny kurs wynosił 12,34 USD.

@richardred sporządził [raport](https://blockcommons.red/publication/mm-phase1-wrapup/) o wynikach rynkowych w trakcie działania animatora rynku w ramach jego pierwszej [propozycji](https://proposals.decred.org/proposals/2eb7ddb29f151691ba14ac8c54d53f6692c1f5e8fe06244edf7d3c33fb440bd9).

## Ważne kwestie i wiadomości poboczne

Miał miejsce [kolejny](https://www.coindesk.com/dforce-hacker-returns-almost-all-of-stolen-25m-in-crypto) atak na DeFi, chociaż tym razem dForce odzyskał od napastnika większość z utraconych 25 milionów dolarów, a użytkownikom wypłacane są zwroty pieniędzy.

W jednej z mniej popularnych sieci stablecoinów, [PegNet](https://www.coindesk.com/miners-trick-stablecoin-protocol-pegnet-turning-11-into-almost-7m-hoard), nieuczciwi górnicy zamienili saldo $11 pJYP na 6,7 miliona pUSD poprzez manipulację wyroczniami cenowymi przez formę ataku 51%. Napastnicy nie byli w stanie upłynnić więcej niż tylko małej części pUSD, a następnie sami przyznali się do czynu, mówiąc, że w ten sposób próbowali przetestować sieć i spalili magicznie stworzone pUSD.

Ludzie [zastanawiają się](https://twitter.com/econoar/status/1254063336779444226), dlaczego temat ProgPoW powrócił na tapet wśród deweloperów Ethereum Core i czy niezdolność do jego usunięcia oznacza, że coś [nie działa](https://twitter.com/hasufl/status/1254065039105024001) w zarządzaniu Ethereum.

Program kredytowy rządu Stanów Zjednoczonych dla małych przedsiębiorstw o wartości 349 miliardów dolarów wygenerował do tej pory 10 miliardów dolarów w [opłatach](https://www.npr.org/2020/04/22/840678984/small-business-rescue-earned-banks-10-billion-in-fees) dla banków, 1-5% dla każdej obsługiwanej pożyczki, pomimo bardzo niskiego ryzyka, jakie pożyczki te stwarzały dla banków, biorąc pod uwagę, że w rzeczywistości tylko przekazywały je do Administracji Małych Przedsiębiorstw, która gwarantowała wszystkie pożyczki. ([wersja plaintext](https://www.npr.org/2020/04/22/840678984/small-business-rescue-earned-banks-10-billion-in-fees))

Fundacja Maker jest przedmiotem [pozwu](https://www.coindesk.com/makerdao-users-sue-stablecoin-issuer-following-black-thursday-losses) inwestorów, którzy stracili pieniądze w Czarny Czwartek.

Miała miejsce istna [nawałnica](https://www.theblockcrypto.com/post/60930/top-crypto-exchanges-token-issuers-named-in-friday-barrage-of-u-s-class-action-lawsuits) pozwów zbiorowych złożonych przeciwko giełdom kryptowalut i emitentom żetonów.

Saldo USDT utrzymywane na giełdach osiągnęło nowe ATH w wysokości [1,8 miliarda dolarów](https://twitter.com/glassnodealerts/status/1253343292403724294) w dniu 23 kwietnia, według alertów Glassnode.

YouTube zaktualizował swoją politykę, aby nie powielać czegokolwiek, co jest sprzeczne z „autorytatywnymi źródłami”, takimi jak wytyczne Światowej Organizacji Zdrowia, co zostało ujawnione w [wywiadzie](https://reclaimthenet.org/youtube-ceo-coronavirus-right-information-misinformation/) z CEO YouTube. O ile cenzurowanie przez YouTube filmów na pewne tematy nie jest nowe, o tyle podejmowanie takich decyzji w sposób płynny w odniesieniu do tego, co mówią „autorytatywne źródła” i celowe kierowanie ruchu do tych źródeł jest nowością.

Jako aktualizację do wzmianki o sprzedaży domeny .org firmie private equity, ICANN [przegłosowało](https://twitter.com/EFF/status/1256053946289774594) odrzucenie tej sprzedaży, w efekcie blokując ją.


## O tym wydaniu

To 25. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: bee, degeri, elian, Exitus, l1ndseymm, pablito, richardred, s\_ben, zubair
- recenzje i komentarze: chappjc, davecgh, emiliomann, jholdstock, jrick, lukebp
- ilustracja tytułowa: saender
