# Decred Journal – Grudzień 2019

![abstrakcja](../img/journal-201912-384.png)

_Obraz: Lodohedron, aut. @saender_

Szczęśliwego Nowego Roku! Oto najważniejsze wydarzenia w Decred z grudnia:

- Ostateczne wydanie wersji v1.5 poszło w świat 16 grudnia, dzięki wszystkim, którzy pomogli w testowaniu kandydatów do wydania.

- Progi aktualizacji PoS i PoW w celu uruchomienia agendy głosowania odn. zobowiązań nagłówka bloków zostały już osiągnięte. Okres głosowania rozpocznie się około 16 stycznia, gdy rozpocznie się nowy interwał na zmianę reguł.

- Lightning Network projektu Decred jest online w sieci mainnet! Rzućcie okiem na [eksplorator sieci](https://ln-map.jamieholdstock.com/) aut. @jholdstock. Jak dotąd @matheusd wygrywa z 11 otwartymi kanałami. Pamiętaj: Lightning Network jest nadal uważany za niestabilną, eksperymentalną, a może nawet niebezpieczną! Nawet eksperci tacy jak Matheus testują ją z zaledwie kilkoma kredytami.

- Interesariusze zatwierdzili budżet w wysokości 30 tys. dolarów na sfinansowanie trwającego rozwoju TinyDecred, open source'owego zestawu narzędzi Pythona.

## Ogłoszenie o aktualizacji do wersji v1.5

Wydanie wersji v1.5.0 poszło w świat po około 5 tygodniach testowania i polerowania. Nowa wersja przynosi wiele ulepszeń omówionych w [październikowym](201910.md#v15-release-candidates) numerze. Pełne informacje na temat wydania oraz pliki do pobrania można znaleźć na stronie [wersji do pobrania](https://github.com/decred/decred-binaries/releases/tag/v1.5.0) na GitHub. Jak zawsze, przed instalacją [zweryfikuj pobrane pliki](https://docs.decred.org/advanced/verifying-binaries/).

Jeśli wydobywasz Decred i nie zaktualizowałeś oprogramowania, zalecane jest zrobienie tego, aby uniknąć potencjalnego odrzucenia bloku z powodu jego starej wersji.

Postępy aktualizacji i głosowania są widoczne na stronie [voting.decred.org](https://voting.decred.org/), więcej szczegółów i wykresy są dostępne na stronie [agend głosowania](https://explorer.dcrdata.org/agendas) na dcrdata.

Na koniec, nie zapomnij ustawić preferencji dotyczących głosowania dla agendy `headercommitments` na swoich kontach VSP i konfiguracji do samodzielnego głosowania.

## Rozwój

[dcrd](https://github.com/decred/dcrd): uproszczono [logikę punktów kontrolnych](https://github.com/decred/dcrd/pull/2014), aby utorować drogę do obsługi punktów kontrolnych w oparciu o same nagłówki. Punkty kontrolne są teraz również [konfigurowalne](https://github.com/decred/dcrd/pull/2013) przez wywołującego. Obsługa osieroconych bloków została oddzielona i [przeniesiona](https://github.com/decred/dcrd/pull/2008) z blockchaina do menedżera bloków. W szerszym ujęciu, zmiany te pomogą oddzielić kod odpowiedzialny za połączenia od logiki pobierania, zgodnie z wymaganiami dla równoległego pobierania [multi-peer](https://github.com/decred/dcrd/issues/1145).

Zoptymalizowano wykorzystanie pamięci [logiki warunkowego wykonania](https://github.com/decred/dcrd/pull/2011) w txscript poprzez zastąpienie stosu warunków dwoma liczbami całkowitymi.

Dodano [obsługę adresów bech32](https://github.com/decred/dcrd/pull/2025) wzbogaconą o funkcje ułatwiające korzystanie oraz [zapewniające](https://github.com/decred/dcrd/pull/2024), że część czytelna dla człowieka jest zgodna z BIP173.

Naprawiono [wyciek z pamięci](https://github.com/decred/dcrd/pull/2027), który był szczególnie istotny w przypadku konfiguracji obejmujących portfele z bardzo dużą liczbą adresów.

[dcrwallet](https://github.com/decred/dcrwallet): zaimplementowano metodę [`createrawtransaction`](https://github.com/decred/dcrwallet/pull/1623) bezpośrednio w dcrwallet, więc może być ona wywołana w trybie synchronizacji SPV lub gdy portfel nie jest zsynchronizowany. Wcześniej była ona dostępna tylko w trybie synchronizacji RPC i wymagała uruchomienia instancji dcrd.

Wyeksportowano [pakiet txsizes](https://github.com/decred/dcrwallet/pull/1573) do wykorzystania przez dcrdex i dcrdata.

[Decrediton](https://github.com/decred/decrediton): Pozgniatano wiele błędów, w tym błąd w [portfelu Trezor](https://github.com/decred/decrediton/pull/2362), który mógł się pojawić, jeśli portfel Trezor otrzymał środki od nadawcy niekorzystającego z dcrwallet, który nie ustawił poprawnie pola „Sekwencja".

[Politeia](https://github.com/decred/politeia): Głównym celem rozwoju Politei na grudzień było naprawienie problemu, w którym [podpis zmiany statusu](https://github.com/decred/politeia/pull/1073) nie był zapisywany, a inny, w którym podpis [startu głosowania](https://github.com/decred/politeia/pull/1088) był tylko podpisem żetonu propozycji, podczas gdy powinien być podpisem całej struktury głosowania (która zawiera również parametry i opcje głosowania). Kwestie te nie miały żadnego wpływu na użytkowników. Poprawki nie są wstecznie kompatybilne, więc wymagały wersjonowania metadanych. Ponieważ i tak wymagana była wersja metadanych głosowania początkowego, druga poprawka dodaje również zmiany, które ułatwią obsługę [propozycji RFP (zapytań ofertowych)](https://github.com/decred/politeia/issues/966).

Kontynuowane są prace backendowe mające na celu wsparcie CMS, trwają prace nad przeprojektowaniem [interfejsu UI](https://github.com/decred/politeiagui/pull/1605).

[dcrpool](https://github.com/decred/dcrpool): Dodano obsługę backendu dla manualnego przetwarzania [wniosków o płatność](https://github.com/decred/dcrpool/pull/140), która pozwala na wyczyszczenie pozostałego salda przed opuszczeniem puli. Dla większości komponentów dodano obszerne [pokrycie testowe](https://github.com/decred/dcrpool/pull/141).

[dcrlnd](https://github.com/decred/dcrlnd): Mapa Decred LN w sieci mainnet jest już [online](https://ln-map.jamieholdstock.com/). Należy zauważyć, że chociaż LN zostało włączone do Decreditona, nadal powinno być rozpatrywane jako wersja alfa. Jeśli chcesz używać LN w sieci mainnet, zalecane jest rozpoczęcie prób w sieci testnet, upewnienie się, że operacje, które chce się wykonać na sieci głównej, nie sprawiają problemów, oraz używanie jedynie małych ilości DCR do testów.

Zmodyfikowano [wybór portów](https://github.com/decred/dcrlnd/pull/62), aby wzmocnić testy integracyjne. Dodano [build Dockera](https://github.com/decred/dcrlnd/pull/67) do Github Actions oraz usunięto [prefiks decred](https://github.com/decred/dcrlnd/pull/68). Trwają prace nad [Dockerowymi przykładami](https://github.com/decred/dcrlnd/pull/66) w celu zautomatyzowania środowisk simnetowych z wszystkim, czego potrzebujesz do uruchomienia klastra LN.

[dcrdex](https://github.com/decred/dcrdex): Nowe wdrożone komponenty obejmują [portfel wymiany BTC](https://github.com/decred/dcrdex/pull/72), [backend księgi zamówień klienta](https://github.com/decred/dcrdex/pull/79) oraz dalszą [integrację](https://github.com/decred/dcrdex/pull/85) pomiędzy menedżerem rynku, routerem zamówień i routerami ksiąg.

W innych zmianach: dodano do specyfikacji [zobowiązania zamówień](https://github.com/decred/dcrdex/pull/83), zmieniono rozdzielczość znacznika czasu zamówień z sekund na [milisekundy](https://github.com/decred/dcrdex/pull/96), zakończono przejście na [ID monet](https://github.com/decred/dcrdex/pull/91), co pozwala na obsługę większej ilości aktywów w przyszłości.

Pozostałe zadania dla DEX to:

- po stronie serwera: menadżer DEX, który spaja wszystkie podsystemy razem (w trakcie recenzji) oraz aplikacja terminalowa (w trakcie realizacji)
- po stronie klienta: web UI (w trakcie recenzji), terminal UI (w wersji roboczej), portfel DCR (w trakcie recenzji), menedżer ksiąg i stała baza danych (w trakcie recenzji)
- Serwery RPC dla serwera i klienta

[dcrandroid](https://github.com/decred/dcrandroid): Po wielu miesiącach pracy scalono duży [redesign](https://github.com/decred/dcrandroid/pull/401) interfejsu użytkownika. Zmiana ta obejmowała również obsługę wielu portfeli (uruchamianie więcej niż jednego portfela jednocześnie). Pozostały kod i pliki Java zostały przekonwertowane na Kotlin. Na backendzie dodano [obsługę wielu portfeli](https://github.com/raedahgroup/dcrlibwallet/pull/57) do dcrlibwallet, który używa zmodyfikowanej wersji modułu SPV dcrwallet do synchronizacji wszystkich portfeli w jednym procesie.

Inne ulepszenia interfejsu użytkownika obejmują wyświetlanie paska postępu i szacowany czas pozostały do zakończenia [ponownego skanowania łańcucha](https://github.com/decred/dcrandroid/pull/414) oraz skaner kodów QR, który zyskuje możliwość wykrywania [kwot płatności](https://github.com/decred/dcrandroid/pull/411).

Usprawnienia bezpieczeństwa: użytkownicy mogą teraz odblokować aplikację przez [odcisk palca](https://github.com/decred/dcrandroid/pull/413), a walidacja adresu została [przeniesiona](https://github.com/decred/dcrandroid/pull/421) do narzędzi bezpieczeństwa.

[dcrios](https://github.com/raedahgroup/dcrios): Ulepszenia UI są kontynuowane dzięki uaktualnionym [kolorom](https://github.com/raedahgroup/dcrios/pull/556) i [ulepszonym](https://github.com/raedahgroup/dcrios/pull/555) renderingiem menu.

Kontynuowane są prace nad obsługą [wielu portfeli](https://github.com/raedahgroup/dcrios/pull/558) i odświeżonym interfejsem UI dla widoków [wysyłania](https://github.com/raedahgroup/dcrios/pull/557) i [odbioru](https://github.com/raedahgroup/dcrios/pull/553).

[dcrdata](https://github.com/decred/dcrdata): Połączono początkowe [wykrywanie miksów](https://github.com/decred/dcrdata/pull/1610) CSPP, poprawki błędów i utrzymanie kodu.

[tinydecred](https://github.com/decred/tinydecred): Dodano wyświetlanie aktualnej agendy głosowania oraz menu do ustawiania [wyboru głosowania](https://github.com/decred/tinydecred/pull/25), zautomatyzowano formatowanie kodu za pomocą narzędzia [Black](https://github.com/decred/tinydecred/pull/27), wprowadzono poprawki błędów i ulepszenia testów.

[docs](https://github.com/decred/dcrdocs): Dokumentacja została [zaktualizowana](https://github.com/decred/dcrdocs/pull/1005) do wydania v1.5. Dodano ostrzeżenie przed [oszustwami airdrop](https://github.com/decred/dcrdocs/pull/1035). Do glosariusza dodano terminy związane z [podziałem sieci](https://github.com/decred/dcrdocs/pull/1018).

[decred.org](https://github.com/decred/dcrweb): Drobne aktualizacje zawartości, aktualizacje zależności.

Pozostałe:

- @degeri [uruchomił](https://twitter.com/degeri_crypto/status/1206639882485075968) notyfikator zgłaszający naruszenie bezpieczeństwa strony o nazwie [DownloadHawk](https://github.com/degeri/DownloadHawk), który obserwuje zasoby do pobrania Decred i wznosi alarm, jeśli zostają one naruszone.
- Jako [przypomnienie](https://twitter.com/decredproject/status/1208067535532437511), badacze bezpieczeństwa mogą zarobić do 25 tys. USD za znalezienie problemów z bezpieczeństwem w oprogramowaniu Decred. Szczegóły na stronie [bounty.decred.org](https://bounty.decred.org/).

Statystyki aktywności deweloperskiej na grudzień: 41 aktywnych PR-y, 242 master commity, 55K dodanych i 45K usuniętych linijek kodu spośród 15 repozytoriów. Wkład pochodził od 1-5 deweloperów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: vdg0 ([tinydecred](https://github.com/decred/tinydecred/commits?author=vdg0)).

Gratululacje dla nowego współpracownika dodanego do listy współtwórców na [decred.org](https://decred.org/contributors/):

- Amir Massarwa (@amass, programista)

Statystyki społeczności na dzień 3 stycznia:

- Obserwujący na Twitterze: 40 897 (+256)
- Subskrybenci na Reddit: 9708 (+5)
- Użytkownicy na Matrixie: 504 (+30)
- Użytkownicy na Slacku: 6881 (+9)
- Użytkownicy na Discordzie: 2628 (+36), zweryfikowani z możliwością pisania postów: 407 (+28)
- Użytkownicy na Telegramie: 2838 (-65)
- Subskrybenci na YouTube: 3960 (+40)
- Obserwujący na Facebooku: 3552 (+245), polubień: 3223 (+196)
- Obserwujący na LinkedIn: 674 (+12)
- GitHub: 528 gwiazdek (+8) i 1458 forków repozytorium dcrd (+58)

## Zarządzanie

W grudniu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 14 406 DCR i wydał 10 106 DCR. Stosując średni dzienny kurs DCR/USD z grudnia w wysokości 18,32 USD, do Skarbca wpłynęło 264 tys. dolarów, a wydano z niego 185 tys. dolarów. Przy średnim dziennym kursie listopadowym wynoszącym 19,97 USD, kwota dolarowa naliczona za prace wykonane w tym miesiącu wynosi 202 tys. dolarów. Na dzień 1 stycznia saldo Skarbca wynosi 643 836 DCR (10,9 mln USD po kursie 16,87 USD).

Grudzień był dla Politei niezwykle spokojnym miesiącem, w którym nie złożono żadnych nowych propozycji. W grudniu odbyły się głosowania nad dwiema propozycjami złożonymi w listopadzie:

- Propozycja [budżetu dla toolkitu TinyDecred](https://proposals.decred.org/proposals/ad0f9688b3467734e2581604914b2cc32c6eb7991dff460eff41d21f66d88451) została przyjęta przy 85% akceptacji i frekwencją w głosowaniu na poziomie 32,6%.
- Aplikacja [PlusBit POS](https://proposals.decred.org/proposals/e559188b0febcab29c49c1f7dd5c66645e31be00894a150ef7d0b8ceb6486605) została odrzucona z poparciem 39% głosów i udziałem głosujących na poziomie 30,6%.

Ditto przedstawiło [etap 3](https://proposals.decred.org/proposals/012b4e335f25704e28ef196d650316dca421f730225d39e37b31b3c646eb8497) swojej propozycji dot. usług komunikacyjnych 7 stycznia, dyskusja jest w toku.

W następstwie [analizy](https://www.blockcommons.red/publication/mm-tracking-1/) publicznych ksiąg zamówień, w których pojawiły się pytania o poziom zapewnienia płynności, i2 Trading dostarczyło pełne logi historii obrotu, które pozwolą na szczegółową analizę ich wyników. Company 0 pracuje nad zestawem narzędzi do audytu wyników i2 w odniesieniu do kryteriów określonych w ich propozycji.

Publikacja Politeia Digest robi sobie przerwę, na czas, gdy poziom aktywności platformy Politeia jest niski; powróci po złożeniu nowych propozycji.

## Sieć

Hashrate: grudniowy hashrate na początku miesiąca wyniósł ~370 Ph/s, a zamknął miesiąc w ok. 400 Ph/s, zaliczając niż w ok. 275 Ph/s oraz szczyt w wys. 522 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 2 stycznia wyglądała następująco: Poolin 32%, UUPool 24%, lab.antpool.com 12%, F2Pool 2,2%, BTC.com 1,8%, BeePool 0,09%, CoinMine 0,09%, suprnova 0,02%, Luxor 0,02% i pozostałe 28% za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Po stabilizacji w przedziale 400-450 Ph/s w listopadzie, w grudniu moc obliczeniowa zaliczyła dalsze spadki i chwilowo zeszła poniżej 300 Ph/s (ostatni romans z takim poziomem miał miejsce podczas krótkoterminowego spadku w kwietniu 2019 roku).

Staking: średnia cena biletu z okresu 30 dni wynosiła 137,5 DCR (+2,7) za danymi z dcrstats.com. Cena wahała się między 123,1-158,76 DCR. Zablokowana kwota wynosiła 5,37-5,61 mln DCR, co odpowiadało 49,75-51,90% dostępnej podaży.

Cena biletów po raz kolejny osiągnęła historyczne maksimum od wprowadzenia obecnego algorytmu sdiff w wysokości 158,76 wraz z nowym szczytem udziału w stakingu na poziomie 51,9% dostępnej podaży.

Węzły: Przez [grudzień](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1575158400000&to=1577836800000) było około 175 węzłów nasłuchujących i 391 w sumie za danymi z dcr.farm. Bazując na średnich danych odn. ilości węzłów, oto ich szacunkowy rozkład: 56% korzysta z dcrd v1.4, 10% używa dcrd v1.5, 8,8% korzysta z dcrd v1.5 w wersji deweloperskiej i buildów RC, 6% używa dcrwallet v1.4, a 1,9% korzysta z dcrwallet v1.5.

[12 grudnia](https://twitter.com/lefebvre_dustin/status/1205224368407748616), 16,1% wszystkich DCR w obiegu brało udział w miksowaniu przez CoinShuffle++.

Decredowa [mapa Lightning Network](https://ln-map.jamieholdstock.com/) dla sieci mainnet pokazuje 11 węzłów i 13 kanałów na dzień 8 stycznia.

## Integracje

Witamy [nowego usługodawcę](https://github.com/decred/dcrwebapi/pull/82) VSP [99split.com](https://99split.com/) z prowizją 0,99%.

VSP dcr.pos.fans został [usunięty](https://github.com/decred/dcrwebapi/pull/79) z [listy VSP](https://decred.org/vsp/) z racji swojej zawodności.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

Czynności w zakresie nawiązywania kontaktów i promocji w grudniu skupiały się na wersji v1.5.0 oprogramowania Decred, z udziałem @davecgh objaśniającym zmiany w zasadach konsensusu na łamach [Decred Assembly](https://www.youtube.com/watch?v=gGQuY0kOt7g) oraz [Decred in Depth](https://www.youtube.com/watch?v=D1527JwkDrs). Dodatkowe odcinki [Decred in Depth](https://www.youtube.com/watch?v=dZeqrQpf-aU) i [Decred Assembly](https://www.youtube.com/watch?v=N3WO5YXpD7M) gościły @matheusd w temacie Lightning Network. Treści do aktualizacji strony internetowej zostały umieszczone na GitHubie i przesłane do zespołu #web\_ops do montażu. Nowa strona ma zostać opublikowana w styczniu.

Duża część miesiąca przeznaczona była na skupienie się na refleksji, dyskusji i planowaniu na rok 2020. Post aut. @bee na temat [strategii marketingowych](https://xaur.github.io/writings/posts/20191127-marketing-strategies.html) wywołał [ożywioną dyskusję](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$157617150861861VoZeT:decred.org) w pokoju #proposals, w trakcie tego, jak Ditto i @Dustorf pracują nad swoimi nowymi propozycjami. @Dustorf przeprowadził [ankietę](https://www.surveymonkey.com/results/SM-9JRDSMFS7/) zwracając się do społeczności o informacje na temat priorytetów dotyczących rejonów działania, segmentów rynku i możliwych zastosowań. Opublikuje on również podsumowanie wydatków na marketing przed złożeniem następnej propozycji.

Grudniowe osiągnięcia Ditto:

- Umieściliśmy w CoinDesk [felieton](https://www.coindesk.com/its-time-to-walk-the-talk-on-decentralized-governance) aut. @jy-p o zdecentralizowanym zarządzaniu pt. „Czas przejść z teorii do praktyki w kwestii zdecentralizowanego zarządzania".
- [Artykuł](https://www.coindesk.com/planned-sale-of-org-angers-many-open-source-crypto-developers) w CoinDesk o sprzedaży domen .org, który zawiera cytat od @richardred.
- [Podcast](https://www.youtube.com/watch?v=NNg5G_EZxtU) Off the Chain z Anthonym Pompliano i @akinsawyerr, mówiący o kryptowalutach w Afryce i unikalnym zarządzaniu Decred.
- [Segment](https://www.nasdaq.com/videos/tradetalks%3A-blockchain-emerging-technologies-in-africa) NasdaqTV TradeTalks z @akinsawyerr, mówiący o technologii blockchain w Afryce.
- Zaaranżowaliśmy i wzięliśmy udział w tournee medialnym z @akinsawyerr w Nowym Jorku, gdzie osobiście spotkał się z dziennikarzami z The Block, Fortune, wziął udział w podcaście Off the Chain oraz podcaście Chain Reaction (w trakcie publikacji).
- Zdobyliśmy wystąpienie w podcaście [Cigars and Crypto](https://anchor.fm/investnoir3/episodes/Episode-73---AkinSawyerr-e9pnmu) z @akinsawyerr, który został wyemitowany w Boże Narodzenie.
- Przygotowaliśmy panel informacyjny oraz prowadziliśmy działania informacyjne dla mediów w związku z udziałem @akinsawyerr w Digital Money Forum na CES (7 stycznia). Zorganizowaliśmy dla niego wystąpienie w [panelu "The Libra Effect"](https://thedigitalmoneyforum.com/2020-agenda/), wraz z Michaelem Caseyem z CoinDesk i Dante Disparte z Libra Association.
- Zaprezentowaliśmy w [sondażu](https://twitter.com/decredproject/status/1207060170855141376) na Twitterze najbardziej godne uwagi osiągnięcie Decred w 2019 r. Zwycięzcą zostało wdrożenie prywatności, z 36,6% głosów, a następnie Politeia i DAO (33,1%). W ankiecie wzięło udział 475 osób.
- Zidentyfikowaliśmy i udostępniliśmy społeczności możliwości zaangażowania się w działalność kryptotwittera i edukowania osób z zewnątrz na temat Decred. Ostatnio, społeczność ciągle rozpisuje się o unikalnym modelu pracy dla wykonawców Decred, ze szczególnym uwzględnieniem deweloperów. Społeczność napisała ponad 40 unikalnych postów używając hasztagu [#cryptodevs](https://twitter.com/hashtag/cryptodevs) i nowego konta [@dcrgoodfirst](https://twitter.com/dcrgoodfirst) jako nowego agregatu pierwszych dobrych wyzwań dla deweloperów zainteresowanych współpracą z Decred.
- Opracowaliśmy propozycja Fazy 3 Ditto PR, która będzie przedstawiona na platformie Politeia w połowie stycznia.


## Eventy:

Na których byliśmy:

- 6 listopada - [Meetup Bitcoin & Blockchains](https://www.facebook.com/events/1444182132424731/) - Oaxaca, Meksyk. @evok3d reprezentował Decred. ([fotki](https://twitter.com/ev0k3d/status/1192945388329807874), _pominięto w wydaniu listopadowym_)
- 4 grudnia - [Decred Demo](https://www.meetup.com/blockchaincentre/events/266659342/) - Melbourne, Australia. @eSizeDave i @zohand zostali zaproszeni do zaprezentowania Decred w nowo wprowadzonym przez Blockchain Centre formacie Talk & Trade. Demo Politeia i Decrediton miało zająć 30 minut, ale łączny czas wystąpienia przekroczył 1,5 godziny, co pozwoliło na rozmowę o kluczowych aspektach Decred i przeprowadzenie debaty wśród ~20 uczestników. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191204-blockchain-centre-talk-and-trade-melbourne-australia.md))
- 7 grudnia - Meetup społeczności blockchain - Mexico City, Meksyk. Zorganizowane przez Blockchain Bajio w Bitcoin Embassy Bar. (zdjęcia: [1](https://twitter.com/Decred_ES/status/1204144823231488000), [2](https://twitter.com/BlockchainBajio/status/1209141039086362624), [3](https://twitter.com/NancyNSalazar/status/1209143989984808961))
- 12-13 grudnia - [Labitconf](https://www.labitconf.com/) - Montevideo, Urugwaj. Zadeklarowany 7-osobowy zespół Latam reprezentował projekt w ciągu 2 dni trwania imprezy. Wcześniejsze wysiłki w kwestii budowania świadomości w Ameryce Łacińskiej wyraźnie dały dobre plony, ponieważ wiele projektów biorących udział w imprezie wiedziało o Decred. Brak stoiska w jednym miejscu pozwolił ekipie być wszędzie i pojawiła się sugestia rozważenie takiego podejścia w przypadku imprez tej wielkości (~1000 odwiedzających). Przeczytaj [pełny raport](https://github.com/decredcommunity/events/blob/master/reports/20191212-labitconf-montevideo-uruguay.md), aby dowiedzieć się więcej na temat przeprowadzonych interakcji i innych szczegółów.
- 15 grudnia - [Crypto & Christmas](https://www.meetup.com/blockchaincentre/events/267037974/) - Melbourne, Australia. Decred Australia zorganizowało imprezę razem z Blockchain Centre, Cointree i e-Pocket. @eSizeDave i @zohand wygłosili krótkie wprowadzenie do Decred i jego osiągnięć dla ~20 uczestników i wykorzystali okazję do przeprowadzenia głębszych dyskusji i lepszej integracji. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191215-crypto-and-christmas-melbourne-australia.md))
- 20 grudnia - [Rocznica Ambasady Bitcoin](https://twitter.com/Decred_ES/status/1207380289107959809) - Mexico City, Meksyk. Ambasada Bitcoin zaprosiła zespół Decred Latam do udziału i sponsorowania tego wydarzenia, dzięki dobrym relacjom nawiązanym wcześniej. @francov\_, @victorarubin i @luisantoniocrag cały wieczór rozmawiali o Decred z uczestnikami spotkania. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191220-bitcoin-embassy-anniversary-mexico-city-mexico.md))


Na których będziemy:

- 14 stycznia - [GoCracow #7](https://www.meetup.com/en-AU/GoCracow/events/265765051/) - Kraków, Polska. @kozel zaprezentuje Decred publiczności złożonej z programistów Go i omówi kilka szczegółów dotyczących pracy dla DAO i sposobów wnoszenia wkładu w projekt.
- 29-31 stycznia - [Crypto 101 Online Summit](https://www.crypto2020summit.com/) - online. @lukebp przedstawi przegląd planów Decred na rok 2020.
- 4-6 lutego - Africa Tech Summit - Kigali, Rwanda. @akinsawyerr będzie prelegentem na Money & Blockchain Summit.
- 13-17 kwietnia - Blockchain Land na Talent Land - Guadalajara, Meksyk. Decred będzie sponsorem Talent Land i będzie obecny na stoisku w Blockchain Land.
- Maj, data do podania poźniej - [BitConf](https://www.bitconf.com.br/portal/) - São Paulo, Brazylia.

## Media

Wybrane artykuły:

- Decrediton z wykorzystaniem Tails, aut. @mm ([stakey.club](https://stakey.club/en/decrediton-on-tails/), również w [jęz. portugalskim](https://stakey.club/pt/decrediton-no-tails/), _przegapione w wydaniu listopadowym_)
- Czy Decred ma odpowiedzi na problemy zarządzania blockchainem?, aut. Kerman Kohli ([medium](https://medium.com/decred/does-decred-have-the-answers-to-on-chain-governance-d35bdd176f59), _przegapione w wydaniu listopadowym_)
- Decred On-Chain: VWAP puli biletów, aut. @permabullnino ([medium](https://medium.com/@permabullnino/decred-on-chain-the-ticket-pool-vwap-d0a3d1c42a3))
- Przegląd stakingu w różnych projektach, aut. @richardred ([blockcommons.red](https://www.blockcommons.red/publication/staking/))
- Czas przejść z teorii do praktyki w kwestii zdecentralizowanego zarządzania, aut. @jy-p, część rocznej retrospektywy CoinDesk ([coindesk](https://www.coindesk.com/its-time-to-walk-the-talk-on-decentralized-governance))
- Przedstawiamy DownloadHawk, aut. @degeri ([blog.decred.org](https://blog.decred.org/2019/12/16/Introducing-DownloadHawk/))

Tłumaczenia:

- Moje doświadczenie z konfiguracją pełnego węzła Decred - [w jęz. hiszpańskim](https://medium.com/decred-es/mi-experiencia-configurando-un-nodo-completo-de-decred-d5321304bc48), aut. @pablito.
- Listopadowe wydanie Decred Journal przetłumaczone zostało na jęz. arabski (@arij), jęz. chiński (@Dominic), jez. hiszpański (@luisantoniocrag and @francov\_), i jęz. polski (@kozel). Dziękujemy!

Wideo:

- Decred Assembly: Głęboka analiza - Lightning Network z udz. @matheusd ([youtube](https://www.youtube.com/watch?v=N3WO5YXpD7M))
- TradeTalks: Blockchain & nowopowstające technologie w Afryce. @akinsawyerr mówi o znaczeniu zarządzania dla perspektyw przemysłu krypto w Afryce. ([nasdaq.com](https://www.nasdaq.com/videos/tradetalks%3A-blockchain-emerging-technologies-in-africa))

Audio:

- POV Crypto 105 - Noc Walki XI: BTC vs ETH vs DCR, z udziałem @Checkmate. Dogłębna debata na temat Bitcoina, Ethereum i Decred na różne tematy związane z technologią blockchain. ([youtube](https://www.youtube.com/watch?v=7m1kfM0fqaE))
- Decred in Depth, odc. 15 gości @davecgh dogłębnie omawiającego zmiany w wersji v1.5 oraz propozycję zmiany zasad konsensusu dla zobowiązań nagłówka bloków. Dave ze szczegółami omawia to, czego dotyczy propozycja, oraz sposoby, w jakie wzmocni ona sieć, jeśli zostanie zatwierdzona. ([youtube](https://www.youtube.com/watch?v=D1527JwkDrs), [soundcloud](https://soundcloud.com/decredindepth/ep-15-dave-collins-btc-suite-origins-dcrd-15))
- Decred in Depth, odc. 14 - @matheusd opowiada o swoim wejściu w temat rozwoju Lightning Network dzięki swojej pracy nad dzieleniem biletów, o wyzwaniach związanych z przenoszeniem zmian wprowadzonych przez Lightning Labs w repozytorium lnd do Decred oraz o różnych sposobach, w jaki podstawa kodu oparta na btcd pomaga w tych wysiłkach. ([youtube](https://www.youtube.com/watch?v=dZeqrQpf-aU), [soundcloud](https://soundcloud.com/decredindepth/ep-14-matheus-degiovani-dcr-lightning-network))
- Off the Chain - Jak krypto wypełnia lukę między tymi z dostępem do bankowości oraz bez. @akinsawyerr daje obszerny wywiad Anthony'emu Pompliano o kryptowalutach i Afryce. ([youtube](https://www.youtube.com/watch?v=NNg5G_EZxtU), [spotify](https://open.spotify.com/episode/1FGOnQb84YpGTZfwbEzdAg))
- Cygara i Krypto 73 - @akinsawyer mówi o Afryce i projekcie Decred. ([anchor.fm](https://anchor.fm/investnoir3/episodes/Episode-73---AkinSawyerr-e9pnmu))

Według [LunarCRUSH](https://twitter.com/LunarCRUSH/status/1208975910013026304) byczy sentyment względem Decred osiąga najwyższy poziom na przestrzeni ostatnich 12 miesięcy.

@AGNFAB1 zamieścił [więcej](https://www.reddit.com/r/decred/comments/eevd8f/decred/) swoich dzieł sztuki związanych z Decred. Poprzednie prace: [Boże Narodzenie](https://twitter.com/AGNFAB1/status/1208044700634157056), [Bankowość na Decred](https://twitter.com/AGNFAB1/status/1199788339404181504), [Trylogia Tacotime](https://www.reddit.com/r/Monero/comments/dzh6vr/tacotime_trilogy/), [Zdecentralizowane Kredyty](https://www.reddit.com/r/decred/comments/dqocpf/decentralized_credits/).


## Dyskusje społeczności

Wybrane wątki z Reddita:

- Ten [post](https://www.reddit.com/r/decred/comments/ecvjaj/the_decred_security_curve_you_want_to_double/) odsyłający do wątku na Twitterze o bezpieczeństwie Decred przyciągnął 39 komentarzy, w których jeden z użytkowników długo przekonywał, że giełdy wymian mogą przeprowadzić atak, w którym osuszyłyby Skarbiec projektu.
- Ten [post](https://www.reddit.com/r/decred/comments/e8v7pd/other_than_staking_sending_to_exchanges_what/) pyta, do jakich celów poza stakingiem i wysyłaniem na giełdy wymian ludzie używają Decred.

Wybrane dyskusje z Twittera:

- [Ankieta](https://twitter.com/decredproject/status/1207060170855141376) @decredproject, w której pytano o najbardziej godne uwagi osiągnięcie roku 2019, otrzymała 475 odpowiedzi. 37% uczestników zagłosowało na prywatność, 33% wyróżniło platformę Politeia/DAO, 19% oddało głos na Lightning Network i 11% na DEX.
- [Merry Stakemas](https://twitter.com/DCRComic/status/1209541923737886721), aut. @DCRComic.
- [Kampania](https://twitter.com/blockchainbuck/status/1201988834575224832) aut. @buck54321 dla propozycji TinyDecred ewidentnie skierowana do starszych wyborców.
- @Exitus [tweetuje](https://twitter.com/coveryfire7777/status/1208499268987867138) o ciemnym motywie w wersji v1.5.
- @Dustorf podsumowuje [zeszły rok](https://twitter.com/lefebvre_dustin/status/1207756052382593026) w Decred.
- [Wątek](https://twitter.com/Ammarooni/status/1208060799736004611) aut. @ammarooni o Decred jako młodszym bracie Bitcoina.

DCRComic:

- [DEX](https://twitter.com/DCRComic/status/1211672109321248768).
- [Ticket Rick](https://twitter.com/DCRComic/status/1204049820350111744) - odniesienie do Ogóra Ricka z serialu animowanego pt. „Rick i Morty."
- [Zbiorowa inteligencja](https://twitter.com/DCRComic/status/1202601872919543811).

Dyskusje z platform komunikacyjnych:

- Pomysł ogrzewania [kurników](https://matrix.to/#/!NNzHoaSdnsbZDQOXJr:decred.org/$157534140455245zYGLX:decred.org) i farm grzybów za pomocą koparek DCR.

## Rynki

W grudniu kurs wymiany Decred wahał się pomiędzy 15,61-20,77 USD / BTC 0,0023-0,0029. Średni dzienny kurs wynosił 18,32 USD.

## Ważne kwestie i wiadomości poboczne

W listopadzie opublikowano [specyfikację](https://stratumprotocol.org/) dla protokołu górniczego Stratum V2 po jego ogłoszeniu w lecie. Nowy protokół odnosi się do wielu problemów obecnych w V1 i zapewnia bardziej wydajną i bezpieczną komunikację pomiędzy górnikami a pulą wydobywczą. Dużą zaletą V2 jest nowy tryb, w którym górnicy wybierają transakcje i bity wersji do włączenia do bloku, zabierając tym samym tę możliwość puli. Tryb ten będzie opcjonalny i [nie będzie domyślny](https://twitter.com/mor_pav/status/1194725696817553410), aby nie zaszkodzić przyjęciu nowej wersji. Braiins wraz z Mattem Corallo i Peterem Toddem urządzili na Reddit kompleksowe [AMA](https://www.reddit.com/r/Bitcoin/comments/dz1mgp/ama_bitcoin_mining_stratum_v2_we_are_braiins_the/).

VTC po raz kolejny [ucierpiało](https://cryptobriefing.com/vertcoin-51-attacked-once-again/) przez atak 51% i reorganizację łańcucha o głębokości 600 bloków, ale tym razem wydaje się, że atakujący prawdopodobnie nie zyskali na ataku, ponieważ Bittrex (prawdopodobny cel) wyłączył handel, gdy tylko atak został wykryty.

The Wharton Cryptogovernance Workshop [uruchomiło](https://twitter.com/ProfPieters/status/1205219084528431113) stronę cryptogov.net, która zawiera [„Oceny zarządzania”](https://cryptogov.net/view-responses-by-question/), udzielone przez zainteresowane projekty odpowiedzi na standardowy zestaw pytań dotyczący zarządzania blockchainem, opracowane przez członków różnych projektów. Decred był jednym z 3 projektów, który przygotował i wysłał swoje [odpowiedzi](https://cryptogov.net/participating-projects/entry/14/) przed uruchomieniem serwisu. @akinsawyerr wziął udział w [evencie](https://twitter.com/kwerb/status/1146505123876802564) organizowanym przez Wharton w lipcu 2019 roku, gdzie projekt został zainicjowany, a także, dzięki pomocy @richardred, przejął inicjatywę w przygotowaniu odpowiedzi dla projektu Decred.

Opublikowano [wyniki ankiety](https://www.zfnd.org/blog/community-sentiment-collection-results/) przeprowadzonej przez społeczność Zcash. Jej uczestnikami był panel doradczy społeczności oraz użytkownicy forum; żaden z górników PoW nie zdecydował się na sygnalizowanie za pomocą zaproponowanej im metody ankietowania. Głosujący mogli zasygnalizować poparcie dla wszystkich 13 propozycji, głosując tak/nie na każdą z nich.

Poparcie dla wniosków, które w dalszym ciągu nie przeznaczały 20% nagrody za wydobycie bloków na finansowanie rozwoju, było bardzo niewielkie.

Na ankietę odpowiedziało 48 z 62 członków Społecznościowego Panelu Doradczego. Warianty #12 (60% na EFF/Zfnd, 40% na program dużych grantów z dodatkowymi doradcami) i #10 („wielki kompromis”, podział podobny do tego w propozycji #12) poradziły sobie dobrze przy prawie 75% wsparcia. Opcja #13 („Keep it simple”, podział 50% ECC/Zfnd) również uzyskała >50% poparcia.

W głosowaniu wzięło udział 77 (spośród 104 uprawnionych) użytkowników forum (konta utworzone po marcu 2019 roku nie były uprawnione do głosowania). Propozycja #12 wypadła najlepiej w tej grupie z 70% akceptacją, #13 także dobrze wypadła z ponad 50% poparciem.

1% wszystkich ZEC w obiegu [głosowało](https://twitter.com/zooko/status/1200917828011876352) w nieoficjalnym sondażu ważonym stawką, najpopularniejszymi opcjami w tej metodzie były #10 i #8 (jeszcze tylko 2 lata z 20% finansowania dla ECC).

Fundacja Zcash zdecydowała się na opracowanie opcji nr 12 z pewnymi ulepszeniami, po czym [wycofała](https://www.zfnd.org/blog/proposed-nu4-zip/) większość z tych ulepszeń w odpowiedzi na napotkany opór. Ostateczna, nieznacznie poprawiona wersja propozycji zostanie przedstawiona innemu panelowi społecznościowemu i użytkownikom forum, aby ją zatwierdzić ją w drodze głosowania.

[ZIP 1012](https://github.com/ZcashFoundation/zips/blob/master/zip-1012.rst), w swojej obecnej formie, polega na przedłużeniu nagrody blokowej na 4 lata w wys. 20%, z czego 35% trafia do ECC, 25% do Zfnd, a 40% na dodatkowe „duże granty". Zmiany we wniosku polegają na uczynieniu go bardziej bezpośrednio kontrolowanym przez Zfnd oraz na usunięciu ograniczenia, które wykluczałoby ECC z otrzymywania jakichkolwiek środków finansowych w ramach "większych dotacji". Kolejna zmiana dodana do wniosku przez Zfnd to „wezwanie i zachęcanie do rozwoju zdecentralizowanego głosowania i zarządzania".

Fundacja Zcash [przekazała również](https://www.coindesk.com/zcash-foundation-funds-app-mixing-private-messaging-and-payments) 40 tys. USD na rzecz Open Privacy na rozwój [Cwtch](https://openprivacy.ca/work/cwtch/), zdecentralizowanej platformy komunikacyjnej i płatniczej.

Sieć IOTA wpadła w kłopoty i została [wstrzymana](https://cryptobriefing.com/iota-halts-15-hours-from-coordinator-bug/) na 15 godzin z powodu błędu w Koordynatorze.

Jack Dorsey z Twittera [ogłosił](https://twitter.com/jack/status/1204766078468911106), że Twitter będzie finansował badania nad zdecentralizowaną wersją swojej platformy.

Moocowmoo, doradca Dash Core i dostawca usługi powierniczych udziałów w master nodach, [zaginął](https://bitcoinist.com/making-a-dash-for-it-moocowmoo-disappears/) podczas procesu wygaszania usługi, pozostawiając część klientów oczekujących z powrotem na swoje DASH przez dłuższy okres czasu. Po nagłośnieniu sprawy Moocowmoo powrócił i DASH z powrotem [zaczął wracać](https://bitcoinist.com/dash-investors-funds-returned-moocowmoo-awakes/) do swoich prawowitych właścicieli w ciągu tygodnia.

Bitfinex [ogłosił](https://www.theblockcrypto.com/linked/48976/bitfinex-to-support-deposits-and-withdrawals-on-lightning-network), że od 3 grudnia zacznie wspierać wpłaty i wypłaty przez Lightning Network.

Etherscan.io, popularny eksplorator bloków Ethereum, został [zablokowany](https://www.coindesk.com/chinas-internet-firewall-has-blocked-access-to-ethereum-block-explorer-etherscan-io) przez chińską Wielką Zaporę Ogniową. Nie podano żadnych powodów; inne eksploratory bloków pozostają dostępne.

Google [zbanowało](https://news.bitcoin.com/google-bans-crypto-app-metamask-from-play-store/) Metamask, przeglądarkową aplikację do interakcji z Dapps, ze swojego Play Store, za rzekome prowadzenie tajnego wydobycia. Podczas gdy ich apelacja została początkowo [odrzucona](https://twitter.com/metamask_io/status/1210299207820570624), zakaz został [uchylony](https://thenextweb.com/hardfork/2020/01/03/google-lifts-ban-ethereum-wallet-app-metamask-mining-cryptocurrency/) kilka dni później.

Google przeprowadziło czystkę wśród filmów o tematyce krypto na YouTube, zanim przywrócił je po stwierdzeniu, że był to [błąd](https://www.bbc.co.uk/news/technology-50924494). Incydent ten najwyraźniej sprawił, że wielu producentów treści na YouTube [zaczęło rozglądać się](https://news.bitcoin.com/youtube-christmas-purge-has-content-creators-pointing-to-these-alternate-platforms/) za dostępnymi zdecentralizowanym alternatywami dla tej platformy.

Raport  [przeciwdziałania praniu brudnych pieniędzy](https://ciphertrace.com/wp-content/uploads/2019/11/CipherTrace-Cryptocurrency-Anti-Money-Laundering-Report-2019-Q3.pdf) związany z kryptowalutami od CipherTrace wspomniał o Decred jako kryptowalucie z funkcją ochrony prywatności.

Zrzut Stellar na Keybase został [zakończony](https://keybase.io/a/i/r/d/r/o/p/spacedrop2019) przedwcześnie z powodu gwałtownego wzrostu liczby śmieciowych zgłoszeń, z wykluczeniem 100 000 kont i ostatecznym podziałem Lumenów pomiędzy 282 000 użytkowników.

Eksperyment z pączkami na /r/ethtrader był kontynuowany wraz z [uruchomieniem](https://new.reddit.com/r/ethtrader/comments/eckj24/ethtrader_special_membership_is_now_live/) specjalnego członkostwa, w którym członkowie mogą płacić miesięczny abonament w wys. 5000 pączków, aby odblokować takie funkcje jak identyfikatory imienne i przywilej umieszczania gifów w komentarzach.

Fundacja Maker [sprzedała](https://www.theblockcrypto.com/post/51059/makerdao-receives-27-5m-from-dragonfly-and-paradigm-to-expand-into-asia) 5,5% całkowitej podaży MKR firmom Dragonfly Capital i Paradigm za 27,5 mln USD w ramach indywidualnej umowy, w której MKR położy większy nacisk na rynek azjatycki.

Parę miesięcy po uruchomieniu usługi powierniczego stakingu dla Tezos, giełda Coinbase jest [teraz](https://twitter.com/brian_armstrong/status/1207818862768480256) piekarzem #1 w sieci XTZ.

„MetaCartel”, próba stworzenia dochodowej inwestycji DAO na kształt oryginalnego, okrytego złą sławą DAO, ale zbudowanego na stroniącym od złożoności Moloch, wypuścił [whitepaper](https://github.com/metacartel/MCV/blob/master/Whitepaper.pdf). Moloch DAO [ogłosiło](https://twitter.com/ameensol/status/1212475508262363137) aktualizację do v2, która ułatwia łączenie Molocha z bytem prawnym bez naruszania przepisów dotyczących papierów wartościowych.

Węzły przekaźnikowe Algorand głosowały za [przyjęciem](https://algorand.foundation/long-term-vesting-plan-vote-result) i [poprawkami](https://algorandfoundation.cdn.prismic.io/algorandfoundation/eb2a8c69-2262-42f8-99a4-09df485207b5_EIP-11252019AF_+Conditional+Accelerated+Vesting+Nov+30.pdf) w sprawie harmonogramu nabywania uprawnień do tokenów, które otrzymały jako dotacje od Fundacji Algorand. Zmiana ta zwiększa liczbę żetonów Algo, które węzły przekaźnikowe otrzymają o 25%, ale wydłuża harmonogram nabywania uprawnień z 2 do 5 lat, z mechanizmem przyspieszającym w przypadku wzrostu cen żetonów Algo. W ten sposób kończy się [epizod](https://algorand.foundation/voting-procedure-eip09092019pc), który rozpoczął się i został pominięty w wydaniu z września, w którym węzły przekaźnikowe głosowały za zawieszeniem własnych nagród do czasu, gdy możliwe będzie uzgodnienie zmian w harmonogramie nabywania uprawnień.

Istnieje około 81 węzłów przekaźnikowych Algorand i wnioski te zostały zatwierdzone głosami na „tak" przez około 55 węzłów (plus wiele głosów wstrzymujących się i kilka głosów sprzeciwu). Węzły Algorand przeszły kontrolę KYC/AML i zawarły z fundacją porozumienie prawne, w którym część procesu głosowania nad tymi wnioskami obejmowała podpisanie i zwrot kopii poprawki do fundacji za pomocą DocuSign. Kontrole KYC/AML są również [obowiązkowe](https://algorand.foundation/200millionalgo-staking-rewards-kyc-extended) dla posiadaczy Algo, którzy chcą uczestniczyć w losowaniu i otrzymywać nagrody.

Nowy [atak](https://arstechnica.com/information-technology/2020/01/pgp-keys-software-security-and-much-more-threatened-by-new-sha1-exploit/) na funkcję hash SHA-1 opublikowany na początku stycznia ma praktyczne zastosowanie w podszywaniu się pod użytkowników PGP/GnuPG i podpisywaniu każdego dokumentu w ich imieniu. Koszt ataku szacowany jest na 45 000 dolarów i będzie się zmniejszał w miarę, jak koszty obliczeń będą coraz tańsze. Jeśli używasz GnuPG, skonfiguruj je tak, aby nie używało SHA-1 do podpisywania lub aktualizacji do wersji 2.2.18+. Podpisy do wydania [wersji v1.5.0](https://github.com/decred/decred-binaries/releases/tag/v1.5.0) oprogramowania Decred nie są zagrożone, ponieważ używają SHA-256.

## O tym wydaniu

To 21. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: akinsawyerr, bee, Dustorf, degeri, fguisso, kozel, margaret\_mei, richardred, s\_ben
- recenzje i komentarze: buck54321, chappjc, Checkmate, davecgh, dnldd, lukebp, matheusd, raedah
- ilustracja tytułowa: saender
