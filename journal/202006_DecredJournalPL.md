# Decred Journal – Czerwiec 2020

![abstrakcja](../img/journal-202006-384.png)

_Obraz: Atmosfera przy 3000 st. K, aut. @saender_

Najważniejsze wydarzenia z czerwca:

- Aplikacje mobilne dla systemów Android i iOS zostały zaktualizowane do wersji v1.5.
- Wydano wdrożenie nowego standardu Rosetta od Coinbase, co znacznie uprości proces dodawania obsługi DCR dla wszelkich handlowców/giełd za jego pośrednictwem.
- @richardred opublikował pierwsze wyniki swoich badań on-chain. Zajrzyjcie również do działu Integracje tego wydania, po dane z monitoringu usługi stakingu od KuCoin.
- Decred DEX wydaje się przygotowany na ograniczone wydanie wstępne, które wspiera DEXing w sieci mainnet.
- Na Reddicie nastąpił wzrost aktywności dyskusyjnej, a na Twitterze pojawiło się kilku nowych artystów zainspirowanych DEX-em Decred.

## Wydanie wersji v1.5 portfeli mobilnych

Po ~1 roku rozwoju, portfele na platformy Android i iOS w wersji v1.5 są już dostępne w [Google Play](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet) i [Apple Store](https://apps.apple.com/us/app/decred-wallet/id1462247643). Zmiany obejmują:

- Całkowicie przeprojektowany interfejs użytkownika, który jest zgodny z wytycznymi dotyczącymi stylu platformy.
- Wsparcie dla wielu portfeli i portfeli tylko do obserwacji.
- Opóźnione potwierdzenie utworzenia kopii zapasowej ziarna w celu szybkiego rozpoczęcia pracy.

Wszystkim naszym współpracownikom w tych projektach należą się ogromne gratulacje!

Przeczytajcie pełne [ogłoszenie](https://www.reddit.com/r/decred/comments/hc5jut/decred_mobile_wallet_v150_has_been_released_for/) na Reddicie i wesprzyjcie związany z tym tematem [tweet](https://twitter.com/planetdecred/status/1274041667520090112).


## Decredowa implementacja middleware'u Rosetta

Na początku lipca [wydano](https://twitter.com/decredproject/status/1279127834137636866) [implementację](https://community.rosetta-api.org/t/decreds-rosetta-middleware-implementation/79) [Rosetta API](https://www.rosetta-api.org/) dla Decred, zaledwie 2 tygodnie po tym, jak sama Rosetta została [wydana](https://twitter.com/coinbase/status/1273269255610531841) przez Coinbase:

> Coinbase początkowo opracowało Rosettę jako oprogramowanie pośredniczące służące do bezpiecznego i bezbolesnego integrowania blockchainów ze swoją platformą (...)
>
> Dla programistów nowych projektów blockchainowych interfejs Rosetta ułatwia zapewnienie kompatybilności z giełdami wymian, które korzystają z systemu Rosetta i może znacznie przyspieszyć czas integracji giełd z nowymi blockchainami i chronić fundusze klientów poprzez zapewnienie określonych warunków bezpieczeństwa.
>
> Dla szerszej społeczności twórców oprogramowania kryptowalutowego, Rosetta ułatwia tworzenie aplikacji typu cross-blockchain, takich jak eksploratory bloków, portfele i dappsy. Zamiast pisać niestandardowe mechanizmy przetwarzania dla każdego obsługiwanego łańcucha, aplikacje mogą korzystać z implementacji  Rosetta dla danego blockchaina do odczytu danych z łańcucha i konstruowania transakcji w standardowym formacie, minimalizując kod i upraszczając obsługę.

Implementacja Rosetta charakteryzuje się ciekawymi [zasadami](https://www.rosetta-api.org/docs/principles_introduction.html) konstrukcji, polityką [braku strażników](https://www.rosetta-api.org/docs/no_gatekeepers.html), ścisłymi wymogami bezpieczeństwa dla implementacji [portfeli](https://www.rosetta-api.org/docs/wallet_api_introduction.html), wsparciem dla [stakingu](https://www.rosetta-api.org/docs/staking_contract_support.html) oraz [zestawem testów](https://github.com/coinbase/rosetta-cli) w celu walidacji implementacji. Pierwsze wydane [SDK](https://www.rosetta-api.org/docs/rosetta_sdk_go.html) jest dla języka Go, ponieważ jest on mocno [używany](https://github.com/coinbase/rosetta-specifications#user-content-sdks-in-more-languages) w infrastrukturze Coinbase.


## Rozwój

O ile nie zaznaczono inaczej, prace zgłaszane poniżej mają status „scalonych z repozytorium głównym (master)”. Oznacza to, że prace są ukończone, zrecenzowane i zintegrowane z kodem źródłowym, który zaawansowani użytkownicy mogą kompilować i uruchamiać, ale ich efekty nie są jeszcze dostępne w wersji plików binarnych dla zwykłych użytkowników.


[dcrd](https://github.com/decred/dcrd):

- zrefaktoryzowano pakiet [rpcserver](https://github.com/decred/dcrd/pull/2211) tak, aby łatwiej poddawał się testom.
- konstrukcja wyświetlania [mempoola](https://github.com/decred/dcrd/pull/2232) przy obsłudze odrzuconych bloków (rozwiązuje pewne problemy względem transakcji na testnecie, które są odrzucane przez mempool, choć nie powinny być odrzucane pod pewnymi warunkami) została naprawiona
- naprawiono [skrajny](https://github.com/decred/dcrd/pull/2218) [przypadek](https://github.com/decred/dcrd/pull/2221) wykrzaczania się serwera RPC ze spreparowanym JSON-em
- [usunięto](https://github.com/decred/dcrd/pull/2222) funkcje szyfrowania i odszyfrowywania, aby zniechęcić do ich używania i zamiast tego zaleca się stosowanie nowoczesnego schematu szyfrowania (np. [szyfrów AEAD](https://crypto.stackexchange.com/a/27248)).


 W trakcie prac:

- [asynchroniczne](https://github.com/decred/dcrd/pull/2219) indeksowanie

Większość wysiłków w pracach nad dcrd w czerwcu poszła w kierunku decentralizacji kontroli nad Skarbcem. [Rzeczony pull requestu](https://github.com/decred/dcrd/pull/2170) przechodzi teraz proces przeglądu i dodawania testów w celu zapewnienia poprawności, ale wydaje się on być kompletny, jeśli chodzi o dodawane funkcje. Po jego zakończeniu pojawi się [Decred Change Proposal](https://github.com/decred/dcps).


[dcrwallet](https://github.com/decred/dcrwallet):

- dodano [metody](https://github.com/decred/dcrwallet/pull/1705) do pobierania filtrów i bloków niezwiązanych z danymi z portfela, co jest przydatne dla aplikacji wykonujących wywołania zewnętrzne takich jak dcrlnd
- unikanie [nietypowych](https://github.com/decred/dcrwallet/pull/1751) kwot dla transakcji CoinJoin
- [wprowadzenie limitu](https://github.com/decred/dcrwallet/pull/1759) transakcji wyjściowych danych w ramach downmixingu
- poprawki błędów


[Decrediton](https://github.com/decred/decrediton):

- opracowano następną część [integracji CSPP](https://github.com/decred/decrediton/pull/2475), która wprowadza ograniczenia w kwestii bezpieczeństwa dla rachunków/kont mieszanych
- ujednolicono [przetwarzanie](https://github.com/decred/decrediton/pull/2468) transakcji zwykłych oraz stakingowych
- zezwolono na [wielokrotne](https://github.com/decred/decrediton/pull/2491) nieuregulowane płatności LN
- nowy komponent dla biletów [kwalifikujących się](https://github.com/decred/decrediton/pull/2510) do głosowania
- widok przedstawiający skonfigurowane usługi [VSP](https://github.com/decred/decrediton/pull/2482)
- więcej kodu zostało [przekształcone](https://github.com/decred/decrediton/pull/2537) w celu wykorzystania komponentów funkcjonalnych i modułów CSS
- ponowne wykorzystanie większej ilości komponentów z pi-ui
- poprawki w UI oraz poprawki błędów


W trakcie prac:

- [integracja](https://github.com/decred/decrediton/pull/2516) proof of concept dla nowego vspd

[Politeia](https://github.com/decred/politeia):

- lepsze [buforowanie](https://github.com/decred/politeia/pull/1226) wyników głosowania
- [leniwe ładowanie](https://github.com/decred/politeia/pull/1219) głosów na komentarze, korzystając z faktu, że stare propozycje są rzadko odwiedzane
- zwiększenie [zasięgu testów](https://github.com/decred/politeia/pull/1203) nowego kodu dla funkcji tworzenia zapytań ofertowych (RFP)
- funkcja trwałego [wylogowania](https://github.com/decred/politeiagui/pull/1903), która usuwa tożsamość użytkownika i szkice dokumentów z przeglądarki. Zmiana ta przestaje też korzystać z poczty elektronicznej jako klucza do przechowywania mniejszej ilości danych osobowych w pamięci lokalnej przeglądarki.
- wprowadzono [krótkie adresy URL](https://github.com/decred/politeiagui/pull/1962) w UI
- ulepszono [diff viewer](https://github.com/decred/politeiagui/pull/1988) dla wersji propozycji
- [zapobieżono](https://github.com/decred/politeiagui/pull/1966) publikacji komentarzy i wniosków w trakcie procesu kotwiczenia
- CMS: przeglądarka poprzednich [wersji](https://github.com/decred/politeiagui/pull/1980) faktur
- CMS: bezprocesowe zapytania dotyczące [danych nt. wniosków](https://github.com/decred/politeia/pull/1171) w celu uniknięcia zapytań cross-site, które powodują problemy z bezpieczeństwem.
- mnóstwo poprawek błędów w UI oraz na backendzie

W trakcie prac:

- wsparcie dla TOTP 2FA
- możliwość recenzowania [wydatków](https://github.com/decred/politeiagui/pull/2032) zatwierdzonych propozycji przed administratorów CMS
Wdrożenie [tlogu](https://github.com/decred/politeia/pull/1180) w backendzie bazy kodowej politeiad zostało zakończone. Prace nad dodaniem do niego wtyczek są w toku. Funkcjonalność wtyczek obejmuje komentarze, komentarze typu „lubię to” oraz głosy oddane na propozycje. Następnym krokiem będzie załadowanie implementacji tlogu istniejącymi danymi z sieci mainnet i przeprowadzenie testów wydajności na ich podstawie. Możliwe, że niektóre rzeczy będą musiały zostać poprawione w przypadku wykrycia jakichkolwiek problemów.

[vspd](https://github.com/decred/vspd):

- wprowadzono [tolerancję](https://github.com/decred/vspd/pull/104) dla awarii połączeń z dcrwallet
- odrzucono [nienadające się do głosowania](https://github.com/decred/vspd/pull/93) bilety
- wstępna wersja przewodnika po [uruchamianiu](https://github.com/decred/vspd/pull/95) vspd
- [podpisanie](https://github.com/decred/vspd/pull/109) odpowiedzi na błędy
- wstępna [strona administratora](https://github.com/decred/vspd/pull/119)
- [odświeżono](https://github.com/decred/vspd/pull/138) projekt UI
- wielokrotne zmiany w celu poprawy walidacji danych wejściowych, obsługi błędów, wyłączania itp.

Podstawowa funkcjonalność jest kompletna, a programiści są w trakcie dokładnego testowania i sprawdzania przypadków krańcowych z mieszanymi/niemieszanymi biletami, a także z/bez automatycznego ticketbuyera. W tej fazie vspd zostało już użyte do głosowania na dziesiątki tysięcy biletów w sieci testnet.

[dcrpool](https://github.com/decred/dcrpool):

- 7 lipca [ogłoszono](https://twitter.com/dnldd/status/1280455233945194496) finalną wersję wydania v1.1, która nastąpiła po dwóch kandydatach do wydania, które naprawiły błędy pojawiające się w RC1. Sprawdź pełne [notatki do wydania](https://github.com/decred/dcrpool/releases/tag/v1.1.0), aby uzyskać więcej informacji.

[dcrdex](https://github.com/decred/dcrdex):

- komendy z wiersza poleceń klienta: [anulowanie](https://github.com/decred/dcrdex/pull/411) zamówień, [wycofywanie](https://github.com/decred/dcrdex/pull/422), [wylogowywanie](https://github.com/decred/dcrdex/pull/423)
- lista [kont](https://github.com/decred/dcrdex/pull/441) dla administratora serwera
- UI przeglądarki klienckiej do dodawania dodatkowych [serwerów](https://github.com/decred/dcrdex/pull/404) DEX
- widżet w UI przeglądarki klienta do wyświetlania [sald](https://github.com/decred/dcrdex/pull/454)
- obsługa klienta w zakresie [zawieszenia handlu](https://github.com/decred/dcrdex/pull/269)
- [automatyczny zwrot](https://github.com/decred/dcrdex/pull/401) swapów w przypadku niepowodzenia transakcji
- bezpieczne [wyłączenie](https://github.com/decred/dcrdex/pull/406) silnika wymian oraz zapis/odczyt jego stanu
- [ukrycie](https://github.com/decred/dcrdex/pull/353) formularzy zamówień do czasu zakończenia rejestracji
- aktualizacje [specyfikacji](https://github.com/decred/dcrdex/pull/482) dotyczące zawieszenia transakcji i API administratora
- [uprząż testowa](https://github.com/decred/dcrdex/pull/432) dla handlu na simnecie oraz parę testów
- usunięto [okres oczekiwania](https://github.com/decred/dcrdex/pull/435) z testów, aby uczynić je solidniejszymi
- wymóg minimalnych potwierdzeń finansowania został [usunięty](https://github.com/decred/dcrdex/pull/499) w celu zmniejszenia złożoności i poprawy UX
- [zmapowano](https://github.com/decred/dcrdex/issues/361) i przeanalizowano wielokrotne zakłócenia w handlu

W sumie 48 PR-ów od 8 współpracowników zostało [scalonych](https://github.com/decred/dcrdex/pulls?q=is%3Apr+merged%3A2020-06-01..2020-06-30+sort%3Aupdated-asc), dodając 11K i usuwając 4K linijek kodu.

W trakcie prac:

- obsługa [wznowienia](https://github.com/decred/dcrdex/pull/442) handlu
- konwersja backendu zasobów do [pluginów](https://github.com/decred/dcrdex/pull/362) Go

Odnosząc się do obaw odnośnie osi czasu projektu, @chappjc pisze:

> Beta w sieci mainnet będzie tego lata. Plan rozwoju jest taki, aby zrobić to do końca drugiego kwartału 2020 roku, i tego się trzymamy. Ponadto, interfejs przeglądarki klienckiej był ledwie poruszony w [propozycji](https://proposals.decred.org/proposals/417607aaedff2942ff3701cdb4eff76637eca4ed7f7ba816e5c0bd2e971602e1) projektu i dramatycznie rozszerzyliśmy jego zakres, aby wszystko się ze sobą spinało i wyglądało dobrze. Wsparcie dla LTC i ogólne wsparcie dla klonów BTC nie było częścią propozycji, ale to też zrobiliśmy. Stworzyliśmy również nowy algorytm dopasowujący epoki, oparty na kryptograficznych zobowiązaniach klientów, których preimage ujawniają się w momencie zamknięcia epoki, i wdrożyliśmy go ponownie od nowa w połowie projektu. Nie jest to łatwe ani szybkie, ale też zostało zrobione i jest to duża poprawa w stosunku do pierwotnej specyfikacji. ([2020-06-01](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15910318461825cyXfI:decred.org))

Zespół pracuje nad pozostałymi problemami z UX i przygotowuje się do ograniczonego wdrożenia w sieci mainnet w ciągu kilku tygodni.

[dcrandroid](https://github.com/planetdecred/dcrandroid):

- repozytorium przeniesiono pod organizację planetdecred
- wdrożono testy [Espresso](https://github.com/planetdecred/dcrandroid/pull/481) i ukończono migrację z Travis CI do GitHub Actions

[dcrios](https://github.com/planetdecred/dcrios):

- repozytorium przeniesiono pod organizację planetdecred
- wprowadzono tłumaczenie [na jęz. chiński](https://github.com/planetdecred/dcrios/pull/695)
- różnorakie [poprawki i usprawienia](https://github.com/planetdecred/dcrios/pull/694) interfejsu użytkownika

[godcr](https://github.com/planetdecred/godcr):

godcr jest powstającym międzyplatformowym desktopowym portfelem SPV dla Decred zbudowanym za pomocą [Gio](https://gioui.org/), pakietu narzędzi GUI w trybie bezpośrednim napisanego w Go. To sprawia, że cała aplikacja zbudowana wyłącznie za pomocą Go nie posiada w sobie przeglądarki internetowej ani javascriptu, a za to ma znacznie mniejszy wykres zależności (i powierzchnię audytu), co jest ważną cechą dla oprogramowania, które kontroluje pieniądze. W momencie pisania, skompilowany plik binarny waży ~30 MB.

Projekt w oparciu o Gio rozpoczął się w styczniu 2020 roku, ale przed decyzją o użyciu Gio, deweloperzy zbudowali wiele prototypów GUI (terminal, przeglądarka, Nucular, Fyne), które są obecnie zarchiwizowane w repozytorium [godcr-old](https://github.com/raedahgroup/godcr-old). Prace nad badaniem i prototypowaniem tych podejść rozpoczęły się we wrześniu 2018 roku.

Kolejne kroki to wydanie publicznie dostępnego dema z podstawową funkcjonalnością portfela i zintegrowanie nowej stakingu przez vspd.

[docs](https://github.com/decred/dcrdocs):

- [dodano](https://github.com/decred/dcrdocs/pull/1106) stronę [kopii zapasowej danych LN](https://docs.decred.org/lightning-network/backups/), obowiązkową lekturę dla testujących LN w Decred, aby zapobiec utracie środków.
- Na stronie [współtworzenia](https://docs.decred.org/contributing/overview/) znajduje się teraz kilka osobistych [historii](https://github.com/decred/dcrdocs/pull/1101) o zostaniu wykonawcą


## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: @svitekpavel ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=svitekpavel)), @Daniel-Leedan ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=Daniel-Leedan)), @shjackson ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=shjackson)).

Gratulacje dla nowych współpracowników, którym przyznano licencje wykonawców Decred (DCC): [@ammarooni](https://twitter.com/ammarooni) (zarządzanie społecznością), [@guilhermemntt](https://github.com/guilhermemntt) (rozwój).

Statystyki społeczności na 2 lipca:

- Obserwujący na Twitterze: 40 510 (+25)
- Subskrybenci na Reddit: 9854 (+62)
- Użytkownicy pokoju #general na Matrixie: 622 (-33) (wykopano 56 starych botów ze Slacka, +23 użytkowników)
- Użytkownicy na Discordzie: 1288 (+66)
- Użytkownicy na Telegramie: 2607 (+4)
- Subskrybenci na YouTube: 4110 (+80), wyświetlenia: 148K (+4K)
- Obserwujący na Facebooku: 3655 (+23), polubień: 3311 (+20)
- Obserwujący na LinkedIn: 836 (+26)
- Repozytorium dcrd na GitHub: 549 gwiazdek (+6) i 241 forki (+1)

## Zarządzanie

W czerwcu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 12 629 DCR i wydał 8340 DCR. Stosując średni dzienny kurs DCR/USD z czerwca w wysokości 16,05 USD, do Skarbca wpłynęło 203 tys. dolarów, a wydano z niego 134 tys. dolarów. Przy średnim dziennym kursie majowym wynoszącym 14,11 USD, kwota dolarowa naliczona za prace wykonane w tym miesiącu wynosi 118 tys. dolarów. Na dzień 1 lipca saldo Skarbca wynosi 633 820 tys. DCR (9,08 mln USD po kursie 14,32 USD).

Odbyły się głosowania nad sześcioma propozycjami, z których 4 zostały zaakceptowane przy względnie dużej frekwencji głosujących w porównaniu z innymi. Propozycjami, któ©e pomyślnie przeszły proces głosowania były:

- Decred OnChain - Narzędzie badawczo - wykresowe, aut. @Checkmate - 86% poparcia (38% frekwencja).
- Propozycja marketingu oraz organizacji eventów w Ameryce łacińskiej dla Decred nr 2, aut. @elian - 61% poparcia (41% frekwencja).
- Badania nad DCR On-Chain: faza 2, aut. @PermabullNino - 74% poparcia (31% frekwencja).
- Program Decred Bug Bounty: faza 3, aut. @degeri - 98% poparcia (32% frekwencja). Odsetek poparcia dla propozycji stale rośnie od jej [fazy 1](https://proposals.decred.org/proposals/d33a2667469b56942adf42453def6cc2292325251e4cf791e806939ea9efc9e1) (90%) oraz [fazy 2](https://proposals.decred.org/proposals/073694ed82d34b2bfff51e35220e8052ad4060899b23bc25791a9383375cae70) (94%).

[Propozycja](https://proposals.decred.org/proposals/4affceb07f5b8126366e8b73ed3d164ebc010bc6fefba19375c4c2e2b252beb0) sponsorowania książki (CoinStory) za 500 dolarów została odrzucona z akceptacją na poziomie 11,6% i przy 34% frekwencji, podczas gdy [propozycja](https://proposals.decred.org/proposals/9eaafc20f206776e38642e272233390f351c5562c3835369a558cc7d7e341018) marketingu telewizyjnego przepadła z 8% akceptacją i 29% frekwencją.

[Wydanie 32](https://blockcommons.red/politeia-digest/issue032/) Politeia Digest zawiera w sobie więcej szczegółów na temat wszystkich powyższych kwestii.

Nowa [propozycja](https://proposals.decred.org/proposals/df11d7ac85061e6a02d6503555e585a1a37fffd82101eeea14670537c951926f) od @ivandecredfan odnośnie produkcji treści w jęz. rosyjskim została opublikowana w czerwcu i przeszła przez głosowanie w lipcu. @ivandecredfan przedłożył już podobną [propozycję](https://proposals.decred.org/proposals/92e3f2176b332c1aea5887acd2324c2cd730ec450e563df52ddae9d5927d5d36) w lutym, która została odrzucona z poparciem w wys. 21% głosujących, ale kontynuował produkcję wideo i zebrał nieco komentarzy jej dotyczących.

Złożono propozycję, która sugeruje wybór nowej nazwy dla projektu („Bitcoin Evolution”). Administratorzy Politei wskazali, że właściciel propozycji (@decredinator) powinien dodać do niej budżet i plan wdrożenia zanim propozycja zostanie uznana za nadającą się do publikacji na stronie platformy. @decredinator [zamieścił](https://www.reddit.com/r/decred/comments/hh2ult/a_better_name_for_decred_to_broaden_the_reach_of/) swoją propozycję na Reddit, aby społeczność mogła ją przeczytać i przyczynić się do wprowadzenia jej w życie. Większość komentujących nie była zainteresowana tym pomysłem, a autor nie odpowiedział na żaden z uzyskanych komentarzy. Autorowi propozycji [wygarnięto](https://www.reddit.com/r/decred/comments/hh2ult/a_better_name_for_decred_to_broaden_the_reach_of/fwbfmst/) również spamowanie linku do swojego postu w wielu niezwiązanych z tym tematem tweetach.

Aby otrzymywać powiadomienia o nowych propozycjach lub odbywających się głosowaniach, możesz śledzić [@pi_crumbs](https://twitter.com/pi_crumbs) na Twitterze, lub ustawić powiadomienia e-mail na stronie Politei.

## Sieć

Hashrate: [czerwcowy hashrate](https://explorer.dcrdata.org/charts?chart=hashrate&zoom=kavllavw-kc326nyn&scale=linear&bin=block&axis=time) na początku miesiąca wyniósł ~390 Ph/s, a zamknął miesiąc w ok. 412 Ph/s, zaliczając niż w ok. 280 Ph/s oraz szczyt w wys. 569 Ph/s w ciągu miesiąca. [Dystrybucja mocy obliczeniowej](https://dcrstats.com/pow) na 1 lipca wyglądała następująco (w przybliżeniu): UUPool 36%, Poolin 32%, lab.antpool.com 11%, BTC.com 3,4%, Luxor 1,07%, F2Pool 0,86%, BeePool 0,09%, CoinMine 0,04%, Suprnova 0,02% i pozostałe ok. 15%.

Staking: średnia cena biletu [z okresu 30 dni](https://dcrstats.com/) wynosiła 139,4 DCR (-2,1). [Cena](https://explorer.dcrdata.org/charts?chart=ticket-price&zoom=kavllavw-kc326nyn&axis=time&visibility=true-false&mode=stepped) wahała się między 135,1-149,8 DCR. [Zablokowana kwota](https://explorer.dcrdata.org/charts?chart=ticket-pool-value&zoom=kavllavw-kc326nyn&scale=linear&bin=block&axis=time) wynosiła 5,63-5,86 mln DCR, co odpowiadało 48,7-50,6% dostępnej podaży [biorącej udział](https://explorer.dcrdata.org/charts?chart=stake-participation&zoom=kavllavw-kc326nyn&scale=linear&bin=block&axis=time) w elemencie PoS.

W dniach 29-31 maja nastąpił niezwykły skok wykorzystania wielkości bloku (niezwiązany z dużymi transakcjami wypłat ze Skarbca). Wydobyto dziesiątki prawie pełnych [bloków](https://explorer.dcrdata.org/blocks?height=453840&rows=50) zostały z transakcjami o rozmiarze 90-100 KB, które skonsolidowały wiele małych transakcji wyjściowych w wyjścia w kwocie 6 DCR. W dniu 31 maja rozmiar łańcucha urósł o [rekordowe](https://explorer.dcrdata.org/charts?chart=block-size&bin=day&axis=time) 13 MB, podczas gdy średni wzrost wynosi ok. 4 MB/dzień. [Wygląda to tak](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15913552414776FisdN:decred.org), jakby VSP konsolidował opłaty za bilety. Wiele z tych transakcji zostało później [połączone](https://explorer.dcrdata.org/tx/ef562befa1f8eeee6250d98b6ccb1722b8fba508dd4919d5b85139df9c761e0c) z rachunkiem o końcowym saldzie ok. 240K DCR (ok. 3,4M USD, ~2% podaży), znany z powiązania z popularną giełdą wymian kryptowalut. W skrócie: operator VSP wysłał około 200 DCR (opłaty za głosowanie płacone przez użytkowników VSP) na giełdę, wykorzystując dużo miejsca w blokach, ponieważ wiązało się to z tysiącami drobnych opłat związanych z poszczególnymi biletami przetwarzanymi przez rzeczonego VSP.

Węzły: przez [czerwiec](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1583020800000&to=1585699200000) było około 126 węzłów nasłuchujących i 208 ogółem, za danymi z dcr.farm. Średnia dystrybucja wersji na czerwiec wygląda następująco: 50% korzysta z dcrd v1.5.1, 9,5% używa dcrd v1.5, 5,6% korzysta z dcrd v1.6.0 w wersji deweloperskiej, 3,2% korzysta z dcrd v1.5.0 w wersji deweloperskiej, 1,8% to dcrd v.1.4.0, 9,5% używa dcrwallet v1.5.1, 1% korzysta z dcrwallet v1.5.0, a 0,9% korzysta z dcrwallet v1.4.0 z 18,7% rozłożonymi między pozostałe wersje.

@Checkmate opublikował [wykres](https://twitter.com/_Checkmatey_/status/1269825167133306881), który pokazuje wzrost wolumenu DCR na łańcuchu.

@PermabullNino [wytweetował](https://twitter.com/PermabullNino/status/1278055245050855424) zaktualizowane wykresy dot. pulsu wydobywczego, kokardy trudności, przypływu biletów, oraz silnych dłoni. Trochę wcześniej [udostępnił](https://twitter.com/PermabullNino/status/1272512290814902275) wykres dot. pędu stakingu.

@richardred opublikował [cz. 1](https://blockcommons.red/post/dcr-on-chain-1/) w serii poświęconej analizie danych z łańcucha blokowego Decred, a najsmakowitsze z niej kąski to:

- 465K z 840K [premine'u założycielskiego](https://docs.decred.org/advanced/premine/#bring-up-costs) pozostaje nietknięte.
- 290K z 840K [monet ze zrzutu](https://docs.decred.org/advanced/premine/#airdrop) również się nie poruszyło
- ~27% z 345 tys. DCR płaconego przez Skarbiec wykonawcom nie zostało dotknięte od momentu otrzymania go przez wykonawcę, ~24% zostało wrzucone w staking, ~24% skończyło na znanym adresie giełdy wymian, a ~1,7% wzięło udział w mieszaniu
- z ~5,8 mln nagród za wydobycia bloków DCR metodą PoW, 60% skończyło na adresach związanych z giełdami, 10% zostało wrzucone w staking, a reszta zostaje nietknięta (6%) lub jej los jest nieznany (24%)

Ten sam rodzaj analizy powtórzono z nowymi danymi i udoskonaleniami formatowania dla [wydania 27](https://ournetwork.substack.com/p/our-network-issue-27) biuletynu OurNetwork.


## Integracje

VSP DecredVoting [ogłosił](https://www.reddit.com/r/decred/comments/hbofz4/tired_of_keeping_track_of_your_staking_activities/) nowy, analityczny pulpit, który wyświetla użytkownikom dane na temat ich biletów, włączając w to również niektóre dane dotyczące biletów współdzielonych. Jest to funkcja, którą zakodował sam @decreddave, i jest ona niedostępna nigdzie indziej.

11 czerwca Hotbit [ogłosił](https://hotbit.zendesk.com/hc/en-us/articles/360049302534-Hotbit-s-Announcement-Regarding-the-Launch-of-DCR-Investment-Product-and-Current-Deposit-Investment-Plan-on-June-11th-2020-UTC-8-) produkt inwestycyjny dla Decred, z roczną stopą zwrotu 4,27% i „okresem wykupu (T+30)". Minimalny zakup wynosi 100 DCR i wydaje się, że „minimalną jednostką do obliczenia odsetek od aktualnego planu inwestycyjnego depozytów będzie 1 DCR”, cokolwiek to oznacza.

Po [uruchomieniu](https://www.kucoin.com/news/en-decred-soft-staking-official-rules) w marcu 2020 r. przez KuCoin powierniczej usługi stakingowej, @richardred przebadał działalność stakingową na adresach związanych z KuCoin. Z obserwacji wynika, że do końca czerwca 2020 r. KuCoin kupił 213 biletów, z których 185 zagłosowało. Najwcześniejsze bilety zakupione przez adresy, które miały być kontrolowane przez KuCoin, zostały zakupione w grudniu 2019 r., kilka miesięcy przed ogłoszeniem usługi w lutym, a klienci zostali automatycznie woptowani w usługę w ciągu 48 godzin od tego ogłoszenia. Wszystkie te bilety wstrzymały się od głosu w głosowaniu agendy on-chain, i żaden z nich nie głosował nad propozycjami Politeia - KuCoin nie bierze udziału w podejmowaniu decyzji za pośrednictwem swoich biletów. Zgodnie z raportami, salda DCR użytkowników wydają się być wyższe o ok. 0,45% dzięki stakingowi, biorąc pod uwagę, że od tego czasu upłynął już kwartał, znaczyłoby to, że stopa zwrotu po rocznym stakingu wynosiłaby około 1,8%, co jest znacznie niższe od tej prognozowanej dla samodzielnego stakingu przez [dcrdata](https://explorer.dcrdata.org/) (~6% na czas pisania).

Procesor płatności [CoinPayments](https://www.coinpayments.net/) usunął z listy obsługiwanych zasobów 37 pozycji, łącznie z DCR po tym, jak [ogłosili to](https://twitter.com/CoinPaymentsNET/status/1264645627750649856) w maju. Po tym, jak niektórzy z ich użytkowników [podnieśli krytykę](https://twitter.com/CryptoEmporium_/status/1268860197038166016) tego posunięcia, tłumaczyli się, że spowodowane było ono [niskim wolumenem](https://twitter.com/CoinPaymentsNET/status/1268925474052268032).

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

@Checkmate przejął inicjatywę na Reddicie i rozpoczął skoncentrowane i ustrukturyzowane dyskusje w celu poprawy zasięgu i nawiązywania kontaktów przez projekt Decred. Pierwszy jego post badał pomysły na oddolną kampanię/strategię marketingową i nawiązanie kontaktów z ludźmi, którzy chcą pomóc w jej realizacji. Jednym z rezultatów jest kampania hashtagowa [#DidYouKnowDecred](https://twitter.com/hashtag/DidYouKnowDecred) na Twitterze. Po niej nastąpiły dwie „niedziele sceptycyzmu” i dwa piątkowe wątki Forward Thinking (Perspektywiczny piątek), mające na celu analizę słabych stron i ich rozwiązań, a także pomysłów, które mogą popchnąć Decred dalej. W sumie, tematy zebrały 155 komentarzy i były jednymi z najbardziej aktywnych postów w tym miesiącu.

Druga [propozycja](https://proposals.decred.org/proposals/3c02b677462d6d22d61bf786798e975b38df7a203c2467429d4ec91f75ef0c40) marketingowo-eventowa dla Ameryki Łacińskiej została zaakceptowana, ale w ostatnich godzinach głosowania ledwo przekroczyła próg akceptacji na poziomie 60%. Aby odpowiedzieć na prawie 40% głosów na „nie”, @elian rozpoczął [ankietę](https://www.reddit.com/r/decred/comments/gzw6hl/what_are_the_thoughts_of_the_394/) na Reddicie, prosząc o iformacje zwrotne, aby dowiedzieć się, czego ludziom w propozycji brakowało, oraz co można na przyszłosc poprawić.

Na początku lipca zespół Decred Latam opublikował [raport](https://www.reddit.com/r/decred/comments/hn4sve/activities_report_decred_en_espa%C3%B1ol_proposal_2/) ze swoich działań za pierwszy miesiąc swojej nowej propozycji.

PR-owe osiągnięcia Monde za czerwiec:

- utworzenie oraz promocja dwóch pomysłów na artykuły do publikacji z branży finansowej, przedsiębiorczej, oraz technologicznej
- przeprowadzenie dwóch e-mailowych sesji Q&A z publikacjami z branży krypto

Obecność w mediach dzięki Monde PR:

- artykuł w [Cointelegraph](https://cointelegraph.com/news/bitcoin-still-faces-on-chain-scaling-trouble-ahead-decred-co-founder-says) zawierający komentarz od @jy-p na temat skalowania Bitcoina, rozpowszechniony w 8 serwisach informacyjnych.
- artykuł w [Cointelegraph](https://cointelegraph.com/news/decred-co-founder-cbdcs-can-facilitate-crony-capitalism) zawierający komentarz @jy-p na temat pojawienia się CBDC, rozpowszechniony w 7 serwisach informacyjnych
- artykuł w [Cointelegraph](https://cointelegraph.com/news/decred-co-founder-calls-paypal-and-crypto-an-odd-combination) zawierający komentarz @jy-p na temat pogłosek o tym, że PayPal akceptuje kryptowaluty, rozpowszechniony w 19 serwisach informacyjnych. Został on również umieszczony jako top story w Holder's Digest w [Cointelegraph](https://cointelegraph.com/news/paypal-crypto-rumors-rip-wirecard-telegram-settles-hodlers-digest-june-2228), oraz powielony w 5 serwisach informacyjnych.

Na GitHubie dostępny jest [arkusz wszystkich relacji medialnych](https://github.com/decredcommunity/pr/blob/release/monde-pr-media-coverage.csv) zdobytych przez Monde PR od lutego 2020 roku.


## Eventy

Na których byliśmy:

- 11 czerwca - [Wirtualny meetup Decred](https://www.meetup.com/Decred-Australia/events/271159615/) - Internet. Zorganizowany przez @DecredAustralia, była to druga odsłona analizy on-chain dla BTC i DCR aut. @Checkmate ([wideo](https://www.youtube.com/watch?v=HbquQIv9EYw))
- 25 czerwca - [Criptotips con Lorena](https://twitter.com/bitcoinemb/status/1276289966440681473) - Internet. Na tej imprezie zorganizowanej przez Bitcoin Embassy Bar (Mexico City) @elian opowiadał o przekrętach na i w branży krypto. ([wideo](https://www.youtube.com/watch?v=Bxdxzs6Bgpw))
- 25 czerwca - [Hablemos Decred 6](https://twitter.com/Decred_ES/status/1275164449448607748) - Internet. @pablito wprowadził publiczność w tematykę Git i GitHub w języku hiszpańskim jako część strategii zespołu Latam mającej na celu tworzenie treści zorientowanych na deweloperów. ([video](https://www.youtube.com/watch?v=4b0xYYk6xlY))
- 30 czerwca - [Webinar Decred](https://www.meetup.com/BlockchainMelbourne/events/271516517/) - Internet. @eSizeDave, @richardred, @elian, @mrbulb i @degeri omówili „Socjologię, przyszłość pracy i wyrównywanie mechanizmów zachęty” wraz z Ellie Rennie i dr Julianem Waters-Lynchem z RMIT University. Wydarzenie zorganizowane przez Decred Australia. ([wideo](https://www.youtube.com/watch?v=1dcHwap7xHQ))

Na których będziemy:

- 11 lipca - [Campus Party](https://brasil.campus-party.org/) - Internet. Brazylijska społeczność Decred będzie miuała trójkę swoich prelegentów. Rafaela Romano opowie o decentralizacji w świecie kryptowalut na scenie Living Better w prezentacji pod tytułem „Monetyzacja poprzez blockchain". Dwójka pozostałych spikerów zostanie potwierdzona bliżej daty wydarzenia.

## Media

Wybrane artykuły:

- Część 1 analizy blockchaina Decred, aut. @richardred ([blog.decred.org](https://blog.decred.org/2020/06/08/Decred-blockchain-analysis-Part-1/))
- Decred on-chain: Urzeczywistniona kapitalizacja, stosunek MVRV i oscylatory gradientowe, aut. @Checkmate ([medium](https://medium.com/decred/decred-on-chain-realised-cap-mvrv-ratio-and-gradient-oscillators-a36ed2cc8182))
- Dlaczego potrzebujemy Decred: inkluzywne podejście do solidnego pieniądza, aut. @ammarooni ([medium](https://medium.com/@Ammarooni/why-we-need-decred-an-inclusive approach-to-sound-money-db2f990c107b))
- Węzeł Decred, lub jak nauczyłem się przestać się martwić i pokochałem wiersz polecenia, aut. @kozel ([część pierwsza](https://medium.com/@artikozel/the-decred-node-or-how-i-learned-to-stop-worrying-and-love-the-command-line-part-one-1eca9420a1b2), [część druga](https://medium.com/@artikozel/the-decred-node-or-how-i-learned-to-stop-worrying-and-love-the-command-line-part-two-e629b8579ce2))
- BTC, ETH i DCR są częścią największej ekonomicznej i technologicznej rewolucji naszego pokolenia, aut. Fernando Quirós (w języku hiszpańskim, [es.cointelegraph.com](https://es.cointelegraph.com/news/elian-huesca-btc-eth-and-decred-are-part-of-the-greatest-technological-and-economic-revolution-of-our-generation)) - wywiad z @elian

Tłumaczenia:

- Bardziej prywatne podejście do stakingu - [w jęz. arabskim](https://insaf01.github.io/decred-arabic/articles/a-more-private-way-to-stake.html) , aut. @arij i [w jęz. hiszpańskim](https://medium.com/decred-es/una-forma-m%C3%A1s-privada-de-hacer-staking-en-dcr-36785ad54a47), aut. @francov\_.
- Konto Medium [Decred Spanish](https://medium.com/decred-es) wzbogaciło się o pełny miesiąc wydań [Decred Drive](https://medium.com/decred-es/decred-drive-spanish/home) dzięki @francov\_ i nowe wydanie [Politeia Digest](https://medium.com/decred-es/politeia-digest-spanish/home) dzięki @pablito.
- @ivandecredfan przetłumaczył [5 artykułów](https://medium.com/@ivandecredfan) i [3 filmy](https://www.youtube.com/channel/UCFjXbEDeyhhj2bH2t_eGKGA/videos) na język rosyjski.
- Transkrypt poradnika konfiguracji pełnego węzła Decred oraz TOR na Raspberry Pi \[2020\] - [w jęz. chińskim](https://github.com/DominicTing/decred-ZH-translations/blob/master/%E6%A0%91%E8%8E%93%E6%B4%BE%E8%BE%85%E5%8A%A9%E5%AE%89%E8%A3%85%E8%84%9A%E6%9C%AC.md), aut. @Dominic.
- Majowy Decred Journal został przetłumaczony na jęz. arabski (@arij), jęz. chiński (@Dominic) i jęz. hiszpański (@francov\_). Dziękujemy wszystkim za [tłumaczenie](https://xaur.github.io/decred-news/) DJ przez tyle miesięcy!

Wideo:

- Konto @Bitcoin zamieściło na Twitterze film z cytatami o nieskończonej zdolności Rezerwy Federalnej do drukowania pieniędzy z memetycznymi przebitkami aut. @Exitus, w tym bezczelną , niewykrytą wzmianką o zdecentralizowanych kredytach na końcu. Tweet został dobrze przyjęty, z 41K wyświetleń, ~900 polubieniami, i ~300 retweetami. ([twitter](https://twitter.com/Bitcoin/status/1269313539056922624))
- Decred otrzymał wzmiankę w programie Good Morning Crypto na kanale Ivan on Tech ([youtube](https://www.youtube.com/watch?v=JZhl2Atm4VI&t=42m50s), start 42:50). Wideo ma 24k wyświetleń. Podziękowania dla Steve'a de boo za zadanie tego pytania na czacie na żywo - to dobry przykład precyzyjnej pracy outreachowej!
- Animacja budzącego się Stakey'ego ([youtube](https://www.youtube.com/watch?v=LHgGyoDcFPI))
- Dwutygodniowy update wiadomości Decred z dnia [10 czerwca](https://www.youtube.com/watch?v=INKSkBpCT_0) i [23 czerwca](https://www.youtube.com/watch?v=4GqdgsgUX7c) aut. @Exitus.
- Poradnik konfiguracji pełnego węzła Decred oraz TOR na Raspberry Pi \[2020\] aut. @Exitus ([youtube](https://www.youtube.com/watch?v=B-5O_GBcbV0))
- Kanał Decred Society autorstwa Phoenixa Greena dodał 7 nowych filmów na temat [społeczności krypto](https://www.youtube.com/watch?v=zM4dfmPYXfo), [rynku krypto w oparciu o 21 milionów monet](https://www.youtube.com/watch?v=yhEAXTJHr3o), dlaczego 21 milionów monet [jest liczbą wybraną celowo](https://www.youtube.com/watch?v=0b241mW8Yto), dzielącego charakteru [hard forków](https://www.youtube.com/watch?v=PZ4aAgz2JcM), doświadczeń z [płatnościami peer-to-peer](https://www.youtube.com/watch?v=0VjKIHCXD50), [Skarbca](https://www.youtube.com/watch?v=-1zmojjvGtg) i samofinansującej się przyszłości oraz wypracowywania [strategii](https://www.youtube.com/watch?v=R1F_GVj76Qw), aby nie zostać całkowicie rozjechanym w krypto.
- Wirtualny meetup Decred Australia #2 z udz. analityka on-chain @Checkmate ([youtube](https://www.youtube.com/watch?v=HbquQIv9EYw))

> Jedyną rzeczą, która powstrzymuje Decred, w mojej uczciwej opinii, jest brak większej liczby ludzi wymyślających kreatywne sposoby na to, by o rozgłaszać o projekcie innym. To jedyne, czego Decred potrzebuje. Bo kiedy już dostaniesz pewien poziom uwagi, to fundamenty projektu po prostu mówią same za siebie.

FIlmy o tematyce Decred od teraz są również zamieszczane [na BitChute](https://www.bitchute.com/channel/decred/) jako plan B na wypadek, gdyby coś stało się z kanałem YouTube. Jest to dobry moment, ponieważ zgodnie z wcześniejszymi oczekiwaniami, YouTube [usunął](https://cointelegraph.com/news/youtubes-algorithm-is-punishing-crypto-content-and-no-one-knows-why) parę filmów o tematyce kryptowalutowej podczas oczyszczania platformy z nieortodoksyjnych opinii związanych z COVID-19.

Audio:

- Decred in Depth, odc. 26 - przypadki użycia DCR oraz rozwój z udz. @Checkmate, @akinsawyerr oraz @mrbulb ([libsyn](https://decredindepth.libsyn.com/akin-checkmate-mr-bulb-dcr-use-case-growth))
- Decred in Depth, odc. 27 - Kradzież pod inną nazwą z udz. @jy-p ([libsyn](https://decredindepth.libsyn.com/jake-yocom-piatt-theft-by-another-name))
- Rough Consensus, odc. 7 - Ustawiona gra ([libsyn](https://roughconsensus.libsyn.com/episode-7-the-rigged-game)) - @mr.black, @Checkmate i @PermabullNino omawiają aktualny stan globalnej unii z rosnącymi niepokojami społecznymi, odbicie na giełdzie typu V oraz ustawioną grę, która wszystkie te elementy łączy.
- Rough Consensus, odc. 8 - Rozmowa makro z Ammarem ([libsyn](https://roughconsensus.libsyn.com/episode-8-talking-macro-with-ammar)) - Ammar dołącza do plutonu Spajdermenów, aby omówić inflację, deflację, bycze tezy w krypto, inwestowanie i sznurki, które wiążą te elementy w całość
- Zach Segal (szef działu listingów w Coinbase) wymienił Decred jako ciekawy projekt w podcaście „Trading Places” ([spotify](https://open.spotify.com/episode/7BkEEDgSDPU1XQsmveksgv), skrócony [klip](https://www.youtube.com/watch?v=IDGQsWE3eeg), _pominięte w wydaniu majowym_).

W tym miesiącu odnotowano wzrost w ilości pojawiających się [dzieł sztuki inspirowanych Decred](https://twitter.com/_Checkmatey_/status/1278972757796159489). @OfficialCryptos zrobił na ludziach wrażenie [smokiem Decred](https://twitter.com/OfficialCryptos/status/1273926304027508738) (może to być [pancerną jaszczurką](https://www.youtube.com/watch?v=XkvcdjSH0c0&t=50m24s), o której mówi Murad w podcaście), [jednorożcem](https://twitter.com/OfficialCryptos/status/1275426618610196480) i [wiertnicą](https://twitter.com/OfficialCryptos/status/1275507751511371780) btcsuite. @aithzakaria1 zamieścił na swoim Twitterze [cyfrowe miasto](https://twitter.com/aithzakaria1/status/1277109552857710592), [prom kosmiczny](https://twitter.com/aithzakaria1/status/1277472194256347137) i inne zdjęcia. @AGNFAB [ogłosił](https://twitter.com/AGNFAB1/status/1271157067097792514), że niektóre z jego dzieł sztuki będą dostępne wyłącznie na stronie [decentralizedboutique.com](https://decentralizedboutique.com/?product_cat=art), nowym sklepie sprzedającym biżuterię i dzieła sztuki związane z kryptografią/kryptowalutami [za krypto](https://decentralizedboutique.com/?page_id=150) (w tym za DCR).


## Dyskusje społeczności

Wiadomości z platform komunikacyjnych:

- Decredowy [serwer Discord](https://discord.gg/GJ2GXfz) został zrestrukturyzowany, a kanały zostały pogrupowane w 3 kategorie: kanały dostępne jedynie przez Discorda dla mniej zobowiązujących rozmów w porównaniu z Matrixem (gdzie wiele pokojów to wirtualne biura, istniejące po to, bo koordynować pracę między wykonawcami), kanały tylko do odczytu zmostkowane do Matrixa (jako równowaga pomiędzy przejrzystością i produktywnością w pokojach Matrixa) oraz dwukierunkowe pokoje zmostkowane #decred-101, #proposals, #support, #ticket-splitting i #trading.
- Na Telegramie utworzono nowy kanał [DecredSupport](https://t.me/DecredSupport) zmostkowano go do pokoju #support na Matrixie.
- Twórcy Matrixa [wydali](https://matrix.org/blog/2020/06/02/introducing-p-2-p-matrix/) zaktualizowaną wersję prototypu klienta peer-to-peer, która daje użytkownikom większą kontrolę nad swoimi danymi.

Wybrane wątki z Reddita:

- Najczęściej omawiany [post](https://www.reddit.com/r/decred/comments/hbb3iz/decred_grassroots_marketing_campaign/) miesiąca (i jeszcze przez pewien czas) został opublikowany przez @Checkmate, podsumowując szereg oddolnych inicjatyw marketingowych poddanych pod dyskusję i rekrutacji uczestników.
- Perspektywiczny piątek z [18 czerwca](https://www.reddit.com/r/decred/comments/hbp6y4/forward_thinking_friday_1_moving_the_peg_forwards/) (idąc dalej) i [26 czerwca](https://www.reddit.com/r/decred/comments/hg2a9k/forward_thinking_friday_decred_narratives_26_june/) (narracje Decred).
- Niedziela sceptycyzmu z [21 czerwca](https://www.reddit.com/r/decred/comments/hd4mwv/decred_skepticism_sunday_21_june_2020/) i [28 czerwca](https://www.reddit.com/r/decred/comments/hh7lo2/decred_skepticism_sunday_28_june_2020/).
- u/g687 [opublikował](https://www.reddit.com/r/decred/comments/hghw3a/why_people_do_not_care_about_decred/) analizę tego, ile razy nazwy różnych projektów są wymieniane w komentarzach w różnych subredditach, zwracając uwagę na to, że Decred był wymieniany stosunkowo rzadko na subredditach innych niż r/decred. Sprowokowało to 36 komentarzy w odpowiedzi, w tym [jeden](https://www.reddit.com/r/decred/comments/hghw3a/why_people_do_not_care_about_decred/fw4u90p) wysoko punktowany komentarz od @jy-p, który podał kilka możliwych przyczyn braku wzmianek. Wskazano również, że pozostałe projekty uwzględnione w porównaniu miały znacznie większą kapitalizację rynkową.
- Pomysł na [sponsorowanie](https://www.reddit.com/r/decred/comments/hcfkei/draft_decred_cypherpunk_prize/) badań i rozwoju oprogramowania, które odgrywa ważną rolę w Decred, spotkał się z mieszanymi reakcjami, częściowo z powodu braku szczegółów i osób chętnych do jego realizacji.
- u/OpenWithRuiLopez zauważył, że Coinbase [nabyło](https://www.reddit.com/r/decred/comments/guri3s/coinbase_acquires_tagomi_tagomi_lists_decred/) instytucjonalną platformę kryptowalutową Tagomi, która handluje DCR jako jednym z 14 aktywów.

Wybrane dyskusje z Twittera:

- @moo31337 [opublikował](https://twitter.com/marco_peereboom/status/1271200577272385538) teaser-bombę o swojej następnej propozycji.
- @Doctor\_ Bitcoin\_ [porównał](https://twitter.com/Doctor_Bitcoin_/status/1277352638502375424) Decred tdo wirtualnego kontynentu, do którego każdy może przystąpić i zamieszkać.
- @Checkmate stworzył nowe [#DecredChallenge](https://twitter.com/_Checkmatey_/status/1272680543612628997) gdzie musisz zgadnąć, która metryka jest pokazana na wykresie.
- @Frenchy\_DCR [wyjawił](https://twitter.com/Frenchy_DCR/status/1273811301844709387), dlaczego DCR nie cieszy się popularnością.
- Po wielu wykresach z analizą techniczną @Mattgetsbarrel1 znalazł ostateczną [strategię](https://twitter.com/Mattgetsbarrel1/status/1274072597597024257) na handel DCR.

![zdjęcie](../img/pl-mountains-360.jpg "@LolekBolek74 enjoying DCR in Polish mountains")

_Obraz: @LolekBolek74 rozkoszujący się DCR w polskich [górach](https://twitter.com/LolekBolek74/status/1269333625352396800)_

## Rynki

W czerwcu kurs wymiany Decred wahał się pomiędzy 14,01-18,76 USD / BTC 0,0015-0,0019. Średni dzienny kurs wynosił 16,05 USD.

W swoim najnowszym [poście](https://medium.com/decred/decred-on-chain-realised-cap-mvrv-ratio-and-gradient-oscillators-a36ed2cc8182) @Checkmate przeanalizował, w jaki sposób urzeczywistniona kapitalizacja, stosunek MVRV i oscylatory gradientowe mają zastosowanie w Decred. Urzeczywistniona kapitalizacja ma tendencję do działania jako poziom wsparcia lub oporu zarówno dla Decred , jak i Bitcoina, ale dla Decred jest to bardziej zbliżone do kapitalizacji rynkowej, ponieważ monety są wyceniane znacznie częściej.

> Urzeczywistniona kapitalizacja w Decred przechwytuje ważny psychologiczny poziom w tym, że reprezentuje zagregowaną cenę, po której rynek ostatnio oddziaływał ze swoimi monetami, przechwytując rodzaj „nastawienia na niedawność". Osoby, które regularnie wchodzą w interakcje ze swoimi portfelami DCR za pomocą biletów, mieszanek CoinShuffle++ lub głosów zarządzających, prawdopodobnie mają większą świadomość ceny monet. W związku z tym koszty realizowania zysków lub strat związanych z DCR są wliczone w każdą transakcję. Konkretna decyzja o zakupie biletu zamiast wysłania monet na giełdę w celu ich sprzedaży jest odzwierciedleniem znaczącego byczego sentymentu dla każdej osoby i na odwrót.

Inna związana z rynkiem [analiza](https://twitter.com/_Checkmatey_/status/1267945637980463104) aut. @Checkmate zauważyła byczą dywergencję RSI w stosunku zarówno do DCR, jak i USD i wykreśliła cenę w stosunku do wskaźników on-chain.

@PermabullNino pokazał, w jaki sposób DCR testuje [urzeczywistnioną kapitalizację](https://twitter.com/PermabullNino/status/1268181399879790592) i jaka jest możliwa korelacja pomiędzy historycznymi przypadkami [odpływów](https://twitter.com/PermabullNino/status/1268270041759432704) dużej puli biletów a trendami spadkowymi na rynku.


## Ważne kwestie i wiadomości poboczne

Pojawiły się pewne kontrowersje dotyczące [błędu](https://medium.com/blockstream/patching-the-liquid-timelock-issue-b4b2f5f9a973) w usłudze Liquid od Blockstream, w ramach której „awaryjne klucze rezerwowe” posiadane przez Blockstream wielokrotnie przejmowały kontrole nad środkami w sposób, który powinien był nastąpić tylko w sytuacji awaryjnej. Kontrowersje dotyczą głównie sposobu, w jaki potraktowano ujawnienie błędu, przy czym James Prestwich (który go odkrył) nie [był pod wrażeniem](https://twitter.com/_prestwich/status/1277090512126660608) z powodu sposobu, w jaki Blockstream bagatelizował jego wagę. Ten [komentarz](https://www.reddit.com/r/CryptoCurrency/comments/hhwwcb/vulnerability_discovered_in_liquid_allowing/fwdqbxc/) na subreddicie r/cryptocurrency dobrze obrazuje linię czasu wydarzenia, włączając w to spostrzeżenie, że wydarzenie to nie było opisane na r/bitcoin.

Reddit ogłosił otwarte [zapytanie](https://www.reddit.com/r/ethereum/comments/hbjx25/the_great_reddit_scaling_bakeoff/) w sprawie pomysłów na to, jak mogą skalować niedawno uruchomiony system punktów (obecnie działający w sieci testowej Ethereum Rinkeby) do całej platformy.

Koszt transakcji na Ethereum od kwietnia [wzrósł o 500%](https://www.coindesk.com/ethereum-developers-consider-new-fee-model-as-gas-costs-climb), a deweloperzy szukają sposobów na jego obniżenie, w tym EIP (1559), w ramach którego użytkownicy płaciliby „opłatę podstawową” do sieci plus napiwek dla górników przy dokonywaniu transakcji.

Jeden użytkownik Ethereum płaci [szczególnie](https://www.coindesk.com/whale-sent-130-ether-transaction-fee) wysokie opłaty w tym miesiącu, z dwoma oddzielnymi transakcjami, w których każda przesyła po 2,6 miliona dolarów w ETH w opłatach transakcyjnych dla górników za przelew niewielkiej kwoty ETH (~100 dolarów). Spekulacje na temat przyczyny wysokich opłat obejmowały błędy i próby [szantażu](https://twitter.com/VitalikButerin/status/1271463564440678401). Dodając do tej tajemnicy, pula, która wydobyła jedną z transakcji, [zaoferowała](https://twitter.com/sparkpool_eth/status/1270688700968480768) zwrot części opłaty, ale nikt się niego nie zgłosił.

Wykryto [błąd](https://cointelegraph.com/news/bancors-bug-exposes-dangerously-common-practice-in-ethereum-defi) w smartkontraktach Bancor, które pozwoliłyby napastnikom na uszczuplenie funduszy każdego, kto z nim współpracował, więc „Bancor zadziałał prewencyjnie, aby „ukraść” fundusze użytkowników, nim mogliby to zrobić napastnicy". Powaga problemu została spotęgowana przez zastosowanie „nieskończonych zatwierdzeń”, które oszczędzają na opłatach transakcyjnych i oferują lepsze UX, ale narażają użytkowników na znacznie większe ryzyko (w tym przypadku potencjalny napastnik mógł otrzymać wszystkie tokeny deponenta, a nie tylko kwotę, którą wybrał do depozytu). Korzystanie z nieskończonej liczby zatwierdzeń jest powszechne w wielu aplikacjach DeFi.

Podaż USDT [przekroczyła](https://bitcoinexchangeguide.com/tether-usdt-surpasses-10-billion-in-market-capitalization/) 10 miliardów dolarów, wzrastając z sumy ~5 miliardów dolarów w tym roku.

[CoinGecko](https://www.coingecko.com/) podjął współpracę partnerską z firmą Hacken, aby dodać ratingi [cyberbezpieczeństwa](https://cointelegraph.com/news/coingecko-adds-crypto-exchanges-cybersecurity-ratings-to-trust-score) dla giełd notowanych na stronie (patrz zakładka Trust Score).

Chainalysis [ogłosiło](https://cointelegraph.com/news/chainalysis-can-now-track-your-privacy-coins-zcash-dash) wsparcie dla monet z funkcją prywatności Zcash i Dash w swoich produktach. Zdecydowana większość transakcji w tych sieciach może być śledzona, ponieważ funkcje ochrony prywatności są wykorzystywane przez bardzo niewiele osób. Ma to miejsce po majowych wiadomościach o [skreśleniu](https://cointelegraph.com/news/another-exchange-delists-monero-amidst-ongoing-sex-scandal) Monero przez kilka giełd, ponieważ Monero lepiej chroni prywatność użytkowników, a naukowcy z Carnegie Mellon University [twierdzą](https://cointelegraph.com/news/researchers-claim-999-of-zcash-transactions-are-traceable), że 99%+ transakcji Zcash jest identyfikowalnych, a dane wejściowe z transakcji Monero mogą być ujawnione z dokładnością do 30% (pełny [artykuł](https://eprint.iacr.org/2020/593.pdf)).


## Zgłoś swój artykuł do następnego wydania Decred Journal

W związku z rozszerzaniem się ekosystemów Decred i szerzej rozumianego środowiska kryptowalut, trudno jest śledzić wszystkie ważne wydarzenia. Możesz pomóc DJ uchwycić bardziej istotne historie, przesyłając je na GitHub. Aby to zrobić, otwórz [GitHub issues](https://github.com/xaur/decred-news/issues), znajdź kwestię odpowiednią dla [następnego wydania](https://github.com/xaur/decred-news/labels/next%20release) (np. „DJ Lipiec 2020”) i skomentuj ją wraz z linkiem i krótkim opisem historii.


## O tym wydaniu

To 27. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: bee, degeri, l1ndseymm, richardred
- recenzje i komentarze: chappjc, davecgh, jholdstock, jz, lukebp, raedah
- ilustracja tytułowa: saender
