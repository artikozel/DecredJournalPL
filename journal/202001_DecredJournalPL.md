# Decred Journal – Styczeń 2020

![abstrakcja](../img/journal-202001-384.png)

_Obraz: Horyzont zdarzeń, aut. @saender_

Najważniejsze wydarzenia ze stycznia:

- Wydano wersję v1.5.1 oprogramowania dla pełnego węzła i portfela Decred, która zawiera kilka poprawek błędów i nowe funkcje.
- Politeia przeżyła swój najaktywniejszy miesiąc od dłuższego czasu, z 6 nowymi propozycjami i 5 już po zakończonym głosowaniu.
- Głosowanie w sprawie zmiany zasad konsensusu dla DCP0005 powoli się kończy, a poparcie dla niego wynosi >99%.
- Globalny ciąg wydarzeń i meetupów społeczności rozwija się, aby uczcić 4. rocznicę pierwszego bloku Decred w dniu 8 lutego, choć niektóre grupy świętowały wcześnie, bo już 6 lutego. Stakey już spakował torby na tournee po swiecie.

## Oddaj głos!

Głosowanie w sprawie zmian konsensusu w celu uruchomienia zobowiązań dotyczących nagłówków bloków określonych w [DCP0005](https://github.com/decred/dcps/blob/master/dcp-0005/dcp-0005.mediawiki) ciągle [trwa](https://explorer.dcrdata.org/agenda/headercommitments). Z 61% aktywnie oddanych na opcje tak/nie głosów, 99,94% to głosy poparcia dla nowej wersji zasad, a pozostałe 39% to bilety wstrzymujące się od głosu.

Do zakończenia głosowania pozostał jeszcze około tydzień. Jeśli macie preferencję w konkretną stronę, prosimy [skonfigurować je](https://docs.decred.org/governance/consensus-rule-voting/how-to-vote/) w swoich portfelach do głosowania solo i/lub VSP.

## Wersja v1.5.1 oprogramowania Decred

Wydanie v1.5.1 naprawia błędy znalezione w v1.5.0 i dodaje kilka funkcji.

dcrd: naprawiono drobny wyciek pamięci dotyczący uwierzytelnionych klientów WebSocket RPC na połączeniach przerywanych. Jest to szczególnie istotne w przypadku konfiguracji, które dotyczą portfeli z bardzo dużą liczbą adresów.

dcrwallet: naprawiono błąd ponownego użycia adresu, który można było wywołać restartem synchronizacji sieci (np. przy utracie połączenia z dcrd), błąd w ticketbuyerze, który mógł wysłać resztę na niewłaściwe konto oraz pare innych błędów. Nowymi funkcjami są komendy `auditreuse` oraz możliwość użycia `createrawtransaction` w trybie synchronizacji SPV (tj. bez uruchomionego dcrd).

Decrediton: naprawiono nieprawidłowe wyświetlanie aktywnych biletów, wyczerpanie luki podczas generowania reszty z transakcji i kilka problemów z interfejsem użytkownika. Kody QR są teraz [bardziej sexy](https://github.com/decred/decrediton/issues/2380) dzięki niebiesko-zielonemu logo Decred w środku.

Pełne informacje dotyczące wydania i pobierania można znaleźć na [stronie wydania](https://github.com/decred/decred-binaries/releases/tag/v1.5.1). Jak zawsze, prosimy [weryfikować pliki binarne](https://docs.decred.org/advanced/verifying-binaries/) przed ich instalacją.


## Rozwój

[dcrd](https://github.com/decred/dcrd): Skrypt obsługi dla OpenBSD rc.d został [dodany](https://github.com/decred/dcrd/pull/2030) jako dodatek do [istniejących](https://github.com/decred/dcrd/tree/master/release/services) konfiguracji systemd i SMF. Obsługa seedera HTTP została dodana [do dcrseeder](https://github.com/decred/dcrseeder/pull/25) i [do dcrd](https://github.com/decred/dcrd/pull/2017). Pakiet 'chainec' został [usunięty](https://github.com/decred/dcrd/pull/2039) z powodu napotkanych praktycznych problemów z tym ogólnym krypto API. Generacja liczb nonce została [ulepszona i zoptymalizowana](https://github.com/decred/dcrd/pull/2044) poprzez wyspecjalizowanie implementacji specjalnie pod secp256k1 i zmodyfikowanie jej w taki sposób, że podpisanie nie może już zawieść nawet w skrajnie małoprawdopodobnym przypadku, gdy zwrócona liczba nonce spowoduje powstanie nieprawidłowego podpisu.

[dcrwallet](https://github.com/decred/dcrwallet): Liczne poprawki błędów dla wydania v1.5.1.

[Decrediton](https://github.com/decred/decrediton): Wiele poprawek błędów i ulepszeń interfejsu użytkownika dla wersji v1.5.1.

Kontynuowane są prace nad [refaktoryzacją procesu uruchamiania](https://github.com/decred/decrediton/issues/2121), aby korzystał on z maszyny o stanie hierarchicznym.

[Politeia](https://github.com/decred/politeia): Komponent Decred Contractor Clearance (DCC) systemu zarządzania wykonawcami został uruchomiony i rozpoczął przetwarzanie i wydawanie DCC (licencji wykonawców Decred). CMS otrzymał szereg poprawek i ulepszeń interfejsu użytkownika.

Trwają prace nad [przeprojektowaniem](https://github.com/decred/politeiagui/pull/1625) interfejsu użytkownika CMS i dodaniem do Politei trybu „dark mode".

[dcrstakepool](https://github.com/decred/dcrstakepool): Wersja v1.5.0 została wydana. To wydanie zawiera wszystkie prace rozwojowe i ulepszenia ukończone od wersji v1.2.0 (wrzesień 2019). Od tego czasu, 7 współautorów stworzyło i scaliło 37 pull requestów. Zmiany obejmują drobne ulepszenia GUI, ulepszone logowanie żądań HTTP, usprawnienie istniejącego kodu i różne poprawki błędów. Pełna lista zmian oraz ścieżka aktualizacji znajdują się w [uwagach do wydania](https://github.com/decred/dcrstakepool/blob/master/docs/release-note-1.5.0.md).

Zaproponowano nowy, [wysokopoziomowy projekt](https://github.com/decred/dcrstakepool/issues/574) usunięcia kont VSP, który usuwa również opłaty z transakcji sprzedaży biletów przy udziale VSP, co umożliwi zarówno interesariuszom  stakującym solo, jak i tym, korzystającym z VSP zakup mieszanych biletów przy korzystaniu z tego samego zestawu anonimowości.

[dcrpool](https://github.com/decred/dcrpool): Ukończono dużą [refaktoryzację](https://github.com/decred/dcrpool/pull/143) w celu rozłączenia elementów i ułatwienia zwiększenia pokrycia kodu testami.

[dcrlnd](https://github.com/decred/dcrlnd): Poprawki błędów i ulepszenia dokumentacji. Ukończono [przykłady Dockerów](https://github.com/decred/dcrlnd/pull/66), które automatyzują wdrażanie środowisk simnet z użyciem docker-compose. W serwisie Medium opublikowano również [przewodnik dla początkujących](https://medium.com/decred/beginner-guide-to-the-decred-dcr-lightning-network-917f8ad304aa) do testowania Decred LN.

Kontynuowane są prace nad [portowaniem zmian z głównego repozytorium](https://github.com/decred/dcrlnd/pull/74) aż do najnowszej wydanej wersji [v0.9.0-beta](https://github.com/lightningnetwork/lnd/releases/tag/v0.9.0-beta). Portowany zestaw zmian zawiera 503 commity, które dodają 37 tys. i usuwają 11 tys. linijek kodu.

[cspp](https://github.com/decred/cspp): Poprawki błędów i utrzymanie kodu. Usunięto [kopię wewnętrznego w Go pakietu chacha20](https://github.com/decred/cspp/pull/38) na rzecz niedawno wydanego publicznego API.

[dcrdex](https://github.com/decred/dcrdex): Kolejne klocki wielkiej układanki zostają ukończone. Najważniejsze elementy to: [kliencki portfel](https://github.com/decred/dcrdex/pull/92) wymiany DCR, oparta na bbolt kliencka [baza danych](https://github.com/decred/dcrdex/pull/99), kliencki [web serwer](https://github.com/decred/dcrdex/pull/103) umożliwiający dostęp do klienta przez przeglądarkę, wstępna aplikacja [rdzeń klienta](https://github.com/decred/dcrdex/pull/120), [szkielet aplikacji klienta](https://github.com/decred/dcrdex/pull/100), rejestracja nowego [konta DEX](https://github.com/decred/dcrdex/pull/140) po stronie klienta poprzez interfejs WWW, konfiguracja aplikacji serwera i [system](https://github.com/decred/dcrdex/pull/81) sterowników zasobów, oraz implementacja 64-bitowego generatora liczb pseudolosowych [Mersenne Twister](https://github.com/decred/dcrdex/pull/137).

Był to kolejny pracowity miesiąc w kwestii rozwoju: w sumie scalono 27 pull requestów, dodając przy tym 22 tys. i usuwając 4 tys. linijek kodu.

[dcrandroid](https://github.com/decred/dcrandroid): Ulepszono layout [strony przywracania portfela](https://github.com/decred/dcrandroid/pull/422).

Biblioteka mobilna dcrlibwallet współdzielona pomiędzy aplikacjami Android i iOS otrzymała kilka poprawek błędów i została [ulepszona](https://github.com/raedahgroup/dcrlibwallet/pull/93) do wersji v1.5.0 wydania dcrd i dcrwallet.

[dcrios](https://github.com/raedahgroup/dcrios): Ulepszenia UI i optymalizacja wydajności. Strona główna została ulepszona dzięki [poprawkom w procesie synchronizacji i UI](https://github.com/raedahgroup/dcrios/pull/566), wprowadzono [optymalizację](https://github.com/raedahgroup/dcrios/pull/572) dla obsługi wielu portfeli, przeprowadzono wstępną [migrację](https://github.com/raedahgroup/dcrios/pull/558) do dcrlibwallet dla funkcji wsparcia wielu portfeli, przechowywanie konfiguracji [przełączono na dcrlibwallet](https://github.com/raedahgroup/dcrios/pull/576). Wdrożono nowy UI dla funkcji [password/PIN](https://github.com/raedahgroup/dcrios/pull/551), [backupu ziarna](https://github.com/raedahgroup/dcrios/pull/530) i [odzyskiwania z ziarna](https://github.com/raedahgroup/dcrios/pull/527).

[dcrdata](https://github.com/decred/dcrdata): Małe poprawki i ulepszenia UI.

[tinydecred](https://github.com/decred/tinydecred): Dodano [klienta RPC](https://github.com/decred/tinydecred/issues/45) z większością zaimplementowanych do tej pory poleceń. Dodano przycisk do [odwołania](https://github.com/decred/tinydecred/pull/30) przegapionych i wygasłych już biletów. Baza danych została [przeprojektowana](https://github.com/decred/tinydecred/pull/42), aby obsługiwać niestandardowe kodowanie, wstawianie partii, przestrzenie nazw, i więcej. Zwiększono [pokrycie testami](https://github.com/decred/tinydecred/pull/47) do ~73%. Zrestrukturyzowano projekt, aby uczynić go [pakietowalnym](https://github.com/decred/tinydecred/pull/59).

[docs](https://github.com/decred/dcrdocs): polecenia i argumenty [dcrlnd](https://docs.decred.org/wallets/lightning/) dla interfejsu wiersza poleceń zostały [udokumentowane](https://github.com/decred/dcrdocs/pull/1055). Instrukcje dotyczące konfiguracji portfeli sprzętowych [Trezor](https://docs.decred.org/wallets/decrediton/trezor/) w użyciu z portfelem Decrediton zostały [dodane](https://github.com/decred/dcrdocs/pull/1062). Do sekcji Getting Started zawierającej starannie dobierany zakres artykułów, podcastów, wideo i innych materiałów (na podstawie Repozytorium Zasobów Edukacyjnych Ditto) [dodana](https://github.com/decred/dcrdocs/pull/1043) została [lista czytelnicza](https://docs.decred.org/getting-started/reading-list/). Strona poświęcona algorytmowi [BLAKE-256](https://docs.decred.org/research/blake-256-hash-function/) została znacznie [rozszerzona](https://github.com/decred/dcrdocs/pull/1034), aby wyjaśnić jej wybór do projektu Decred. Do [słownika pojęć ](https://docs.decred.org/glossary/) dodane zostały [dwie nowe definicje](https://github.com/decred/dcrdocs/pull/1057) - typ monety oraz portfel HD.

[decred.org](https://github.com/decred/dcrweb): Zaktualizowano stronę [współpracowników](https://github.com/decred/dcrweb/pull/774), oczyszczono kod.

Statystyki aktywności deweloperskiej na styczeń: 246 aktywnych PR-ów, 210 master commitów, 58K dodanych i 25K usuniętych linijek kodu spośród 17 repozytoriów. Wkład pochodził od 3-6 deweloperów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: @termoose ([dcrlnd](https://github.com/decred/dcrlnd/commits?author=termoose)) oraz @pablito ([dcrweb](https://github.com/decred/dcrweb/commits?author=pLabarta)).

Gratulacje dla pierwszych wykonawców, którym przyznano licencje wykonawców Decred (DCC) przez nowy proces CMS: [@bgptr](https://github.com/bgptr) (rozwój), [@teknico](https://github.com/teknico) (rozwój) oraz [@decreddragon](https://twitter.com/DecredDragon) (marketing).

Następujące osoby zostały usunięte z listy [aktywnych współpracowników](https://decred.org/contributors/): Leslie Ankney, Elizabeth Bagot, Margaret Huang, Milvian Prieto, Denys Zayets, Tim Hebel, Phillip Conrad, Justin Santoro, Bill Xing. Dziękujemy za ogrom dobrej pracy i nie wahajcie się wpadać w odwiedziny!

Strona [współtwórców](https://decred.org/contributors/) jest regularnie aktualizowana w celu tworzenia listy osób, które obecnie budują Decred. Konsekwencją tego jest to, że kiedy nieaktywni współpracownicy są usuwani, na stronie nie pozostaje żaden zapis, że byli niegdyś współpracownikami. Aby temu zaradzić, zaproponowano stworzenie listy [byłych współpracowników](https://github.com/decred/dcrweb/issues/744) i/lub [panteonu sław](https://github.com/decredcommunity/issues/issues/52).

Statystyki społeczności:

- Obserwujący na Twitterze: 40 860 (-37)
- Subskrybenci na Reddit: 9723 (+15)
- Użytkownicy na Matrixie: 533 (+29)
- Użytkownicy na Slacku: 6880 (-1)
- Użytkownicy na Discordzie: 2670 (+42), zweryfikowani z możliwością pisania postów: 433 (+26)
- Użytkownicy na Telegramie: 2728 (-110)
- Subskrybenci na YouTube: 3950 (-10)
- Obserwujący na Facebooku: 3563 (+11), polubień: 3234 (+11)
- Obserwujący na LinkedIn: 689 (+15)
- GitHub: 533 gwiazdki (+5) i 1476 forków repozytorium dcrd (+18)


Historyczne wykresy statystyk z serwisów Twitter, YouTube, Reddit i GitHub są od teraz dostępne na stronie [dcrextdata](http://dcrextdata.planetdecred.org/community).

## Zarządzanie

W styczniu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 14 121 DCR i wydał 15 560 DCR. Stosując średni dzienny kurs DCR/USD ze stycznia w wysokości 18,00 USD, do Skarbca wpłynęło 254 tys. dolarów, a wydano z niego 280 tys. dolarów. Przy średnim dziennym kursie grudniowym wynoszącym 18,32 USD, kwota dolarowa naliczona za prace wykonane w tym miesiącu wynosi 285 tys. dolarów. Na dzień 1 lutego saldo Skarbca wynosi 642 082 DCR (12,2 mln USD po kursie 18,96 USD).

W styczniu złożono 6 propozycji, z których dla pięciu proces głosowania już się zakończył, a nad jedną trwa jeszcze dyskusja.

- Propozycja [Monde](https://proposals.decred.org/proposals/bdd02d82547bd78fc95939c1e2b3df21ebec6e8d31444df5bea3c133b0199f05) Public Relations została przyjęta przy 72% akceptacji i frekwencji na poziomie 25%.
- Propozycja [Ditto](https://proposals.decred.org/proposals/012b4e335f25704e28ef196d650316dca421f730225d39e37b31b3c646eb8497) PR została odrzucona z akceptacją na poziomie 17% i frekwencją na poziomie 35%.
- Odnowienie programu badawczego Decred Open Source: [etap 3](https://proposals.decred.org/proposals/e3675649075a2f92269d8cdc2e1dfd71b16796477df31de7d2868cccfcffb13f) zostało zatwierdzone przy 82% akceptacji i frekwencji na poziomie 29%.
- [Propozycja](https://proposals.decred.org/proposals/063e38270b475ad680e98c12d1a48e322f4e8defe40b265272ea60c6d2202b13) aut. @dezryth odnośnie zarządzania kontem projektu na Facebooku i reprezentowania Decred na wydarzeniach została zatwierdzona z 76% głosów na „tak” i frekwencją na poziomie 21%.
- Propozycja stworzenia [naklejek](https://proposals.decred.org/proposals/4acb95564d36488a7ee64683a84dd7954982b2f4743e2f7a15477231f863442f) została odrzucona z 5% głosów poparcia i udziałem 21%.
- Dyskusja na temat [propozycji](https://proposals.decred.org/proposals/95cfb73254a032b2c199c37bb499d6f172d044b1f38016279c5bbca6572251f0) złożonej przez @Exitus w celu produkowania materiałów wideo dla Decred jest aktualnie w toku.

[Wydanie 26.](https://blockcommons.red/politeia-digest/issue026/) Politeia Digest zawiera więcej szczegółów na temat wszystkich propozycji i audytu propozycji animatora rynku. Opracowano narzędzia do audytu, które przetwarzają historię otwarć/zamknięć zleceń i2 w celu procentowego obliczenia czasu sprawności. Jeśli czas sprawności jest krótszy niż 90% podany w propozycji i2, ich wynagrodzenie za dany miesiąc zostanie proporcjonalnie obniżone.

W styczniu CoinDesk opublikowało też [artykuł](https://www.coindesk.com/is-bitcoin-in-2020-really-like-the-early-internet), który odnosił się do danych dotyczących wydatków ze Skarbca Decred. Dla tego artykułu wyliczono wówczas kilka dodatkowych liczb (koniec listopada 2019 roku). Skarbiec wypłacił na tamten czas równowartość 6,55 mln dolarów, z czego 54,7% zostało wypłacone deweloperom. Od momentu uruchomienia Politei w październiku 2018 r. ponad 10% wydatków ze Skarbca zostało przeznaczonych na projekty zaproponowane i zatwierdzone za pośrednictwem platformy Politeia. Patrząc na regiony geograficzne, 30% deweloperów Decred znajduje się w Ameryce Środkowej i Południowej, 25% w USA, 20% w Europie, 15% w Afryce i 10% w Azji.

## Sieć

Hashrate: styczniowy hashrate na początku miesiąca wyniósł ~396 Ph/s, a zamknął miesiąc w ok. 435 Ph/s, zaliczając niż w ok. 315 Ph/s oraz szczyt w wys. 528 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 1 lutego wyglądała następująco: Poolin 26%, UUPool 18%, lab.antpool.com 10%, F2Pool 2%, Luxor 1,78%, BTC.com 1,46%, BeePool 0,08%, CoinMine 0,07%, suprnova 0,01% i pozostałe ok. 40% za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu z okresu 30 dni wynosiła 138,3 DCR (+0,8) za danymi z dcrstats.com. Cena wahała się między 128,1-150,4 DCR. Zablokowana kwota wynosiła 5,55-5,71 mln DCR, co odpowiadało 50,83-51,96% dostępnej podaży.

Węzły: Przez [styczeń](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1577836800000&to=1580515200000) było około 137 węzłów nasłuchujących i 323 w sumie za danymi z dcr.farm. Średnia dystrybucja wersji na styczeń wygląda następująco: 50,8% korzysta z dcrd v1.4, 21,1% używa dcrd v1.5, 9% korzysta z dcrd v1.5 w wersji deweloperskiej i buildów RC, 3,1% korzysta z dcrd v1.6 w wersji deweloperskiej, 2,2% to dcrd v1.5.1, 5,6% używa dcrwallet v1.4, 3,4% korzysta z dcrwallet w wersji v1.5, a 0,6% korzysta z dcrwallet v1.5.1.

[dcrextdata](http://dcrextdata.planetdecred.org/) cieszy się odświeżonym designem oraz uruchomionymi wykresami mempoola oraz propagacji bloków. Niektóre z nich są nieco powolne, ale już teraz da się z nich wyczytać ciekawe informacje. Feedback jest zawsze mile widziany w [issue trackerze](https://github.com/raedahgroup/dcrextdata) lub w pokoju [#planetdecred](https://matrix.to/#/!gruHpujXftcsHcghjx:planetdecred.org).

Dane z węzła, który działa od bloku 0 [pokazują](https://matrix.to/#/!vGasNHFXqjoEWUBTIi:decred.org/$15792934191332SWDSY:decred.org), że łańcuch sieci głównej Decred miał 2517 reorganizacji łańcucha o głębokości 1, 25 reorgów o głębokości 2, 3 reorgi o głębokości 3 i żadnych reorganizacji o głębokości większej niż 3.

[Mapa Lightning Network](https://ln-map.jamieholdstock.com/) sieci mainnet projektu Decred pokazuje 14 węzłów i 31 kanałów o całkowitej pojemności 6 DCR (stan z 6 lutego).

## Integracje

Nowości od VSP:

- YieldWallet, dostawca usług typu staking-as-a-service, uruchomił nowy VSP, dostępny pod adresem [decred.yieldwallet.io](https://decred.yieldwallet.io/). Prowizja wynosi 2%.
- VSP [decredvoting.com](https://decredvoting.com/) [ogłosił](https://www.reddit.com/r/decred/comments/euqd4h/introducing_split_ticket_dashboard_on/) nowy panel dla współdzielonych biletów, który "zapewnia użytkownikom dzielonych biletów pełen widok podsumowujący wszystkie ich dzielone bilety wraz ze spersonalizowanymi danymi analitycznymi".
- Następujące VSP zostały usunięte z [listy](https://decred.org/vsp/) z powodu ich słabej wydajności: [d1pool.com](https://github.com/decred/dcrwebapi/pull/63), [dcr.grassfed.network](https://github.com/decred/dcrwebapi/pull/70) oraz [dcr.pos.fans](https://github.com/decred/dcrwebapi/pull/79).

Okazuje się, że VSP [dcr.farm](https://dcr.farm/) prowadzi kilka użytecznych usług bez należnej im reklamy:

- [seed.dcr.farm](https://seed.dcr.farm/) jest seedującym węzłem dcrd z dedykowaną przepustowością, znajdującym się we Francji.
- [explorer.dcr.farm](https://explorer.dcr.farm/) jest alternatywnym eksploratorem bloków blockchaina Decred.
- Wyrafinowany [panel statusu](https://status.dcr.farm/) dla wszystkich usług, w tym 6 portfeli do głosowania.
- Jest też na bieżąco wykorzystywany przez DJ, ale wymieniony dla kompletności serwis [charts.dcr.farm](https://charts.dcr.farm/), który oferuje [~16 paneli](https://charts.dcr.farm/dashboards) z unikalnymi wykresami, takimi jak [węzły](https://charts.dcr.farm/d/000000014/nodes) (wersje węzłów DCR na przestrzeni czasu), [VSP](https://charts.dcr.farm/d/000000016/proof-of-stake-pools) (statystyki VSP w czasie) i [opłaty transakcyjne](https://charts.dcr.farm/d/000000013/transaction-fees) (nieregularne wysokie i niskie opłaty).

Giełdy wymian i kantory:

- Widzieliśmy doniesienia o tym, że portfele zarówno [Bittrex](https://twitter.com/Cjfan23/status/1218727480854446081), jak i [Binance](https://www.reddit.com/r/decred/comments/ew1vyc/binance_dcr_withdrawls_disabled/) przez dłuższy czas znajdowały się w trybie konserwacji. Na czas zamknięcia tego wydania obydwa już działają.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

8 lutego Decred skończył cztery lata, co społeczność świętowała wydarzeniem [#DecredGlobalMeetup](https://twitter.com/hashtag/DecredGlobalMeetup). W co najmniej [kilkunastu miastach](https://twitter.com/decredproject/status/1225440495108841475) na całym świecie odbyły się wydarzenia, aby uczcić społeczność i technologię, którą zbudował projekt Decred.

W styczniu zostały ukończone i przesłane do tłumaczeń nowe podstrony strony internetowej projektu, a w lutym spodziewane jest jednoczesne uruchomienie strony we wszystkich językach, co jest planem na wizualne odświeżenie strony i jest zgodne z obecną wersją [przekazu](https://github.com/decredcommunity/pr/blob/release/foundational-messaging.md). Strona internetowa została uproszczona, a wszystkie przyszłe aktualizacje będą możliwe do zrealizowania w ciągu nie więcej niż trzech miesięcy.

Złożono różne propozycje dotyczące marketingu i PR, z kolejnymi w trakcie przygotowania, jak również raport zawierający podsumowanie prac i wydatków w 2019 r. oraz wezwanie do działania na 2020 r. w celu decentralizacji, przełamania bańki, edukacji i wzmocnienia suwerenności społeczności.

W ramach podcastu Decred in Depth ukazały się dwa odcinki: @matheusd w temacie decredowej sieci Lightning, oraz @permabullnino w temacie subsydiów blokowych, wskaźnika VWAP ticketpoola oraz współczynników konwersji HODLerów. Nie zapomnijcie zasubskrybować i ocenić podcast.

## Eventy

Na których byliśmy:

- 7 stycznia - [Digital Money Forum](https://thedigitalmoneyforum.com/) - Las Vegas, USA. @akinsawyerr przemawiał na korzyść zdecentralizowanych sieci i suwerenności jednostki podczas panelu [The Libra Effect](https://thedigitalmoneyforum.com/Sessions/the-problem-with-old-money-a-great-debate/), który gościł się na łamach [CoinDesk](https://www.coindesk.com/libra-association-exec-world-needs-us-because-bitcoin-is-not-a-means-of-payment), a także rozmawiał z kilkoma dziennikarzami. ([raport](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$157859800075195pLJde:decred.org), [zdjęcia](https://twitter.com/AkinSawyerr/status/1214614201517232128))
- 14 stycznia - [premiera filmu dokumentalnego pt. „Cryptopia”](https://www.meetup.com/en-AU/BC-Aus/events/267242503/) - Melbourne, Australia. Decred został zaproszony do zostania sponsorem wydarzenia i partnerem inauguracyjnym filmu „Cryptopia”, dokumentu o kluczowych zagadnieniach z dziedziny kryptowalut, które obejmują regulacje prawne, prywatność, usługi finansowe, zarządzanie, marketing i rozwój. Zarezerwowano cały teatr dla ponad 140 gości ze społeczności kryptowalut i blockchain. @eSizeDave i @zohand omawiali Decred na panelu dyskusyjnym i zostali zacytowani w oficjalnym [komunikacie prasowym](https://prwire.com.au/r/87706). ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200114-cryptopiafilm-world-premiere-melbourne-australia.md))
- 14 stycznia - [GoCracow #7](https://www.meetup.com/en-AU/GoCracow/events/265765051/) - Kraków, Polska. @kozel przedstawił publiczności złożonej z ok. 30 programistów Go zagadnienia ze świata kryptowalut oraz Decred. Publiczność z zainteresowaniem wysłuchała prezentacji, ale najbardziej aktywnymi uczestnikami byli ci, którzy sami określili się jako już jako obeznani lub entuzjastycznie nastawieni do tematyki krypto. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20200114-gocracow7-meetup-krakow-poland.md))
- 24 stycznia - Technologia blockchain i przypadki jej wykorzystania - Casablanca, Maroko. @arij została zaproszona do rozmowy podczas wydarzenia współorganizowanego przez marokańskie Ministerstwo Młodzieży na temat „Roli nowych technologii w promowaniu pozytywnego rozwoju młodych ludzi". @arij opowiedziała o technologii blockchain i przedstawiła platformę Politeia i LN publiczności około 50 osób z różnych środowisk, głównie młodych ludzi. ([zdjęcia](https://twitter.com/DecredArabia/status/1220819101586685952))
- Jan 29-31 - [Crypto 101 Online Summit](https://www.crypto2020summit.com/) - Internet. @lukebp nakreślił plany Decred na rok 2020; prezentacja zostanie zamieszczona na YouTube, gdy będzie gotowa.

Na których będziemy:

- 8 lutego - [Blockchain i AI](https://www.eventbrite.com/e/blockchain-and-ai-best-tools-for-the-development-of-nations-tickets-91389994935) - Casablanca, Maroko. @arij będzie mówiła o osiągnięciach Decred w ciągu 4 lat jego istnienia. Na zakończenie odbędzie się mała impreza z okazji urodzin projektu.
- 8 lutego - [Decred Crypto Hangouts](https://www.eventbrite.com/e/decred-crypto-hangout-learn-about-career-opportunities-in-the-industry-tickets-91830803405) - Ikeja, Lagos. Huobi, Yellowcard i Telos4Africa będą obecne.
- 8 lutego - [Decred Global Meetup](https://www.meetup.com/pt-BR/DecredBrasil/events/268496816/) - Salwador, Brazylia.
- 12-13 marca - [Blockchain Summit Latam](https://www.blockchainsummit.la) - Panama City, Panama. Decred będzie srebrnym sponsorem.
- 18 marca - [Campus Party Amazonia](https://brasil.campus-party.org/campus-party-amazonia-2020/) - Manaus, Brazylia. Decred będzie prowadził 2 prelekcje i kilka innych działań.
- 20 marca - [BlockchainUA](https://blockchainua.com/en/) - Kijów, Ukraina. Poszukujemy chętnych do zaprezentowania Decred na największym wydarzeniu w Europie Wschodniej. Kontaktujcie się z @cryptotexty w pokoju [#events](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org) w celu uzyskania szczegółów.
- 20-21 marca - [CIBTC Blockchain Summit](http://cibtc.es/) - Motril, Hiszpania. Decred będzie złotym sponsorem. Impreza jest częścią dużego tournee Decred en Español w Hiszpanii, gdzie @elian będzie organizować spotkania i warsztaty z lokalnymi społecznościami w Madrycie, Barcelonie, Bilbao, Walencji, Vigo i Motril.
- 30-31 maja - [Bitconf](https://www.bitconf.com.br/portal/) - São Paulo, Brazylia. Decred będzie prowadził wiele prelekcji na różne tematy.


## Media

[Decred Drive](https://medium.com/@decreddrive), nowy cotygodniowy biuletyn, został [uruchomiony](https://twitter.com/DecredDragon/status/1215309738293985280) przez @decreddragon 9 stycznia i opublikował dotychczas 5 numerów.

Decred pojawił się w nowym cotygodniowym biuletynie Our Network, w wydaniach [#2](https://ournetwork.substack.com/p/our-network-issue-2) i [#6](https://ournetwork.substack.com/p/our-network-issue-6), gdzie @Checkmate zaprezentował wykresy i spostrzeżenia na temat danych on-chain z blockchaina Decred, a @richardred opracował jeden wykres na temat Politei. Każdego tygodnia biuletyn prezentuje 5 wykresów i komentarzy dla wielu różnych projektów blockchain.

Checkmate zaprezentował niedźwiedzią wizję dla Ethereum w ramach zaplanowanego „[krypto-grzmotu](https://bankless.substack.com/p/why-eth-wont-sustain-a-monetary-premium)” w biuletynie Bankless. Vitalik Buterin [odpowiedział](https://www.reddit.com/r/ethereum/comments/ewb9as/why_eth_wont_sustain_a_monetary_premium/fg2x4oz/) na kilka komentarzy na Reddit, a na chwilę obecną są już 3 [odpowiedzi](https://bankless.substack.com/p/why-eth-will-sustain-a-monetary-premium) na substacku Bankless od znanych członków społeczności Ethereum.

Decrypt [opisało](https://decrypt.co/17371/we-found-the-no-coiner-troll-guarding-wikipedia) niektóre z [doświadczeń](https://github.com/decredcommunity/issues/issues/79) Decred z Wikipedią, co wywołało konstruktywną twitterową [wymianę zdań](https://twitter.com/decryptmedia/status/1220069033405485057) z jednym z ekspertów od krypto serwisu Wikipedia.

Wybrane artykuły:

- Budowanie transparentnej przyszłości z blockchainem Decred, aut. @ammarooni ([medium](https://medium.com/decred/building-a-transparent-future-with-the-decred-blockchain-e77471d28059))
- Decred On-Chain: współczynniki konwersji HODLerów, aut. @permabullnino ([medium](https://medium.com/@permabullnino/decred-on-chain-hodler-conversion-rates-87e16a4c78cd))
- Przegląd roku 2019: Rozproszone zarządzanie ([Smith and Crown](https://sci.smithandcrown.com/research/2019-governance-review)) - ten obszerny przegląd zarządzania blockchainem w 2019 roku zawiera wiele celnych spostrzeżeń na temat Decred, ze szczególnym wskazaniem na temat wskaźników udziału w platformie Politeia.
- Przyszłość cyfrowanych walut w Afryce? Poznaj niezależną cyfrową walutę Decred ([appsafrica.com](https://www.appsafrica.com/the-future-of-digital-currencies-in-africa-meet-decred-the-autonomous-digital-currency/))
- Czy Bitcoin naprawdę jest jak wczesny Internet?, aut. Leigh Cuen ([coindesk.com](https://www.coindesk.com/is-bitcoin-in-2020-really-like-the-early-internet)) - ten rozbudzający przemyślenia fragment o podobieństwach między Bitcoinem a wczesnym Internetem zawiera wywiady z @moo31337 i Zooko Wilcox z Zcash. Artykuł zawiera również kilka danych liczbowych związanych z wydatkami ze Skarbca Decred, jak zauważono w dziale Zarządzanie.

> Byliśmy równie podekscytowani debatą zapoczątkowaną przez zeszłotygodniowy [artykuł](https://www.coindesk.com/is-bitcoin-in-2020-really-like-the-early-internet) w CoinDesk! Z pewnością ciekawie było obserwować, jak różne projekty dyskutują o tym, kto w końcu został wymieniony w artykule, przy czym tylko Decred i garstka innych zostały do tego zaproszone. Ten rodzaj relacji jest wynikiem miesięcy komunikacji z dziennikarzami: edukacji, terminowych odpowiedzi, wywiadów, dostarczania informacji i statystyk, itp. Takie artykuły nie zdarzają się z dnia na dzień ani z własnej woli - a stare porzekadło „co z oczu, to z serca” z pewnością tyczy się też mediów. ([@liz_bagot](https://proposals.decred.org/proposals/012b4e335f25704e28ef196d650316dca421f730225d39e37b31b3c646eb8497/comments/71))

Tłumaczenia:

- Przewodnik dla początkujących do testowania Lightning Network projektu Decred - [w jęz. arabskim](https://insaf01.github.io/decred-arabic/articles/beginner-guide-to-the-decred-lightning-network.html), aut. @arij, [w jęz. hiszpańskim](https://medium.com/decred-es/gu%C3%ADa-para-probar-el-lightning-network-de-decred-dcr-344cad6be20e), aut. @francov\_.
- Grudniowe wydanie Decred Journal przetłumaczone zostało na jęz. arabski (@arij), jęz. chiński (@Dominic) oraz jęz. hiszpański (@francov\_). Dziękujemy za Waszą pracę!

Wideo:

- Czy firma public relations w krypto jest warta swej ceny? Interesariusze Decred głosują i decydują z wykorzystaniem platformy Politeia, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=uzhc2CKI2wk))
- Akin Sawyerr z projektu Decred mówi, że blockchain jest częścią politycznej przyszłości Afryki ([coindesk.com](https://www.coindesk.com/decreds-akin-sawyerr-says-blockchain-is-part-of-africas-political-future), [youtube](https://www.youtube.com/watch?v=8w7uCSVuuVw))
- Efekt Libry na targach CES2020: najlepsze fragmenty z udz. @akinsawyerr, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=5Zi5wYZhEDE)) - pełny panel dyskusyjny można znaleźć [tutaj](https://www.youtube.com/watch?v=prz6ILpLNLE) (wypowiedź @akinsawyerr zaczyna się około [17 min](https://www.youtube.com/watch?v=prz6ILpLNLE&t=17m00s))

Audio:

- @akinsawyerr pojawił się w podcaście Toma Shaugnessy'ego Chain Reaction, aby porozmawiać o wyobrażeniu sobie zarządzania na nowo. ([podbean](https://fiftyonepercent.podbean.com/e/decred/))
- Crypto 101, odc. 302 - Zarządzanie rzeszą ludzi na przykładzie Decred, z udziałem @lukebp. ([podbean](https://www.podbean.com/media/share/dir-j5baa-7c90e87), [soundcloud](https://soundcloud.com/crypto101podcast/ep-302-governing-the-masses-w-decred))
- Decred in Depth, odc. 16 - @permabullnino omawia proces propozycji Politeia i jego bieżącą pracę nad analizą ruchu biletów w sieci Decred, wprowadzając takie pojęcia jak TVWAP i współczynniki konwersji HODLerów. ([libsyn](https://decredindepth.libsyn.com/permabull-nino-block-subsidies-ticket-pool-vwap-hodler-conversion-rates), [soundcloud](https://soundcloud.com/decredindepth/ep-16-permabull-nino-block-subsidies-ticket-pool-vwap-hodler-conversion-rates))
- Decred in Depth, odc. 17 - @ammarooni rozprawia o bogatej historii krypto miasta Toronto, tokenomice DCR, BTC i ETH, i rozpatruje Decred pod kątem bycia dostawcą infrastruktury, atutem produkcyjnym i przełomem gospodarczym. ([libsyn](http://decredindepth.libsyn.com/ammar-nasier-decred-an-economic-breakthrough))

@AGNFAB1 opublikował dwa nowe dzieła sztuki: [Pirat Politeia](https://www.reddit.com/r/decred/comments/end3lc/d_e_c_r_e_d/) (nieoficjalny tytuł), [DCR i BTC, jak ogień i woda](https://twitter.com/AGNFAB1/status/1220091425737580544).


## Dyskusje społeczności

Wiadomości z platform komunikacyjnych:

- Opuszczamy Slacka i palimy za sobą mosty, więc uciekajcie na [Matrix](https://decred.org/matrix/) póki jeszcze możecie!

Wybrane wątki z Reddita:

- [Aktualizacja](https://www.reddit.com/r/decred/comments/eo3tje/decred_dex_progress_the_client_and_server_are/) w repozytorium dcrdex, następny przystanek: testnet dla handlu z wykorzystaniem atomic swaps.
- [Jak przenieść dcrd do tła](https://www.reddit.com/r/decred/comments/ervlvw/how_to_runstartmove_decrd_to_the_background_i_can/) - często pojawiające się pytanie nowych użytkowników narzędzi wiersza polecenia.
- Czy Decred [umarł](https://www.reddit.com/r/decred/comments/ekhi2l/is_decred_dead_hash_rate_has_stagnated_and/)? Nie.
- Ciekawa dyskusja na temat [niedźwiedzich rozważań](https://www.reddit.com/r/ethereum/comments/ewb9as/why_eth_wont_sustain_a_monetary_premium/fg1q9q7/) @Checkmate na temat Ethereum bear na subreddicie /r/ethereum, w tym dyskusja z Vitalikiem Buterinem.

Wybrane dyskusje z Twittera:

- Stakey przypomina wszystkim o [kontrolowaniu swoich kluczy](https://twitter.com/DCRComic/status/1212754642481881088).
- Pierwszy na rynku vs adaptacyjny, historyczny [przykład](https://twitter.com/BarnardTheBear/status/1213893268351672320).
- Dlaczego Decred jest [nudny](https://twitter.com/marco_peereboom/status/1218178834786324480).
- Jak często Twój prezes/prowadzący projekt mówi Ci, żebyś zaplanował projekt tak, aby nie miał on w nim [nic do powiedzenia](https://twitter.com/marco_peereboom/status/1212849047456927744)?
- @DCRComic: komiks o [Atomic Swaps](https://twitter.com/DCRComic/status/1222874521507717121), [analiza](https://twitter.com/DCRComic/status/1220367582479425537) o podejściu do finansowania rozwoju BCH, [wątek](https://twitter.com/DCRComic/status/1218189767759859713) o dcrdata.
- [Aktualizacja](https://twitter.com/chappjc/status/1222004371199864834) w temacie dcrdex od @chappjc, zapowiada, że jest na co czekać „już tej wiosny".
- @richardred [otwiera](https://twitter.com/RichardRed0x/status/1219381114768429057) drzwi do głosowania nad programem badawczym open source.
- @lukebp [tweetuje](https://twitter.com/lukebp_/status/1217871970420711424) o korzyściach płynących z możliwości zmiany zasad konsensusu w celu zwiększenia bezpieczeństwa sieci i UX.
- Propozycje Ditto i Monde PR przyciągnęły uwagę dziennikarzy z branży, w tym również [Franka Chaparro](https://twitter.com/fintechfrank/status/1215704016564428802) z The Block.
- @Dustorf w temacie cyfrowego [kolektywu wykonawców Decred](https://twitter.com/lefebvre_dustin/status/1220397690602901504).
- @degeri zwraca uwagę, że strony internetowe większości najbardziej znanych projektów blockchainowych [przekazują mnóstwo danych](https://twitter.com/degeri_crypto/status/1217372695483965441) do Google.
- Konkurs #NarysujStakiego - [#DrawStakey](https://twitter.com/DCRComic/status/1220732376088809477).


## Rynki

W styczniu kurs wymiany Decred wahał się pomiędzy 16,24-22,44 USD / BTC 0,00195-0,00257. Średni dzienny kurs wynosił 18,00 USD.

Ruchy cenowe Bitcoina w przedziale ~6500 - ~9000 USD spowodowały wzrosty cenowe licznych [altcoinów](https://cointelegraph.com/news/dash-price-up-70-bsv-gains-200-is-a-price-correction-imminent), w tym Dash, Zcash oraz licznych forków Bitcoina.


## Ważne kwestie i wiadomości poboczne

Bitcoin obchodził swoje 11-lecie. Od 3 stycznia 2009 roku uptime sieci Bitcoin wynosi [99,9848%](http://bitcoinuptime.com/).

Grudniowy raport wydobywczy CoinShares odnotowuje 80% wzrost mocy obliczeniowej Bitcoin od czerwca 2019 roku, z ~50 do ~90 Eh/s (Exahashy na sekundę). Szacuje się, że 70% z dodanej mocy ~40 Eh/s pochodzi z Chin, podczas gdy udział Chin w całej mocy obliczeniowej szacowany jest na 65%. Ceny „wyjścia na zero” i „kapitulacji górników” szacowane są odpowiednio na ~6100 USD i ~3900 USD. Sprawdź [najważniejsze informacje](https://medium.com/coinshares/bitcoins-hash-rate-grew-more-than-80-since-june-mostly-within-china-7444b20b2c89) i podlinkowany pełny raport, aby uzyskać więcej interesujących danych.

Artykuł o stanie sieci w r. 2019, [analiza roku](https://coinmetrics.substack.com/p/state-of-the-network-2019-year-in), aut. Coin Metrics porównuje wyniki największych 18 kryptozasobów (w tym DCR) pod kątem mnogości rynków oraz metryk.

Monero ogłosiło [RPC-Pay](https://www.monerooutreach.org/stories/RPC-Pay.html), nowy plan dla natychmiastowych i prywatnych mikrotransakcji, w którym klienci płacą hashami górniczymi za używanie zgodnego serwera, takiego jak węzeł Monero. „Hashe otrzymane jako zapłata są wykorzystywane przez serwer w celu uzyskania dochodu, a dzięki RandomX w Monero hashe górnicze mogą być wydajnie obliczane przy użyciu najpopularniejszych procesorów. Płacenie tylko haszami zamiast samym Monero oznacza, że RPC-Pay nie obciąża sieci Monero ani nie pozostawia po sobie śladów. Dzięki RPC-Pay, hashe górnicze stają się nową, prywatną, najmniejszą jednostką płatniczą w uniwersum Monero". Projekt Primo jest pierwszą zewnętrzną aplikacją tej koncepcji do realizacji dostarczania płatnych treści internetowych.

[Nakamoto](https://nakamoto.com/), nowa publikacja o tematyce kryptowalutowej, uruchomiona w 11. rocznicę bloku genesis Bitcoina z wybranymi artykułami od wybitnych osobistości z branży blockchain. Czasopismo samo siebie (i jego autorów) określa jako „pro-Bitcoin”, co wywołało sporo [kontrowersji](https://cryptoslate.com/nakamowho-blog-by-pro-bitcoin-technologists-bashed-by-btc-maximalists/) wśród niektórych maksymalistów Bitcoina, którzy poczuli się dotknięci artykułami, które dotyczyły innych, niż tylko Bitcoin, projektów związanych z kryptowalutami. Wiele osób wymienionych jako współtwórcy [nie opublikowało jeszcze][https://modernconsensus.com/cryptocurrencies/bitcoin/bitcoin-journal-nakamotos-rocky-start/] artykułów w czasopiśmie, ale lista nazwisk takich jak Roger Ver i Brendan Blumer (prezes Block.one) wydaje się być wystarczająca, by inni wspóltwórcy, tacy jak Tuur Demeester, [wycofali się](https://twitter.com/TuurDemeester/status/1213939900476743680) z projektu.

DigixDAO ma zostać zlikwidowane po [głosowaniu](https://www.coindesk.com/digixdao-votes-to-liquidate-64m-treasury), w którym 58 interesariuszy zagłosowało [przeważającą większością głosów](https://community.digix.global/#/proposals/0xe7d5d8aefc5f73c4c8bbc716f0c3c2dd52d5282d18217db331da4435b8e6966e) (97%) za likwidacją jego puli środków i odzyskaniem swoich ETH. DigixDAO zostało utworzone po to, aby wspierać ekosystem wokół złotego żetonu Digix (DGX) i promować go. Digix [przeprowadził](https://www.coindesk.com/digixdao-votes-to-liquidate-64m-treasury) ICO w 2016 roku i pozyskał 466 648 ETH, wówczas o wartości 7 mln USD, a obecnie posiada 380 000 ETH (o wartości 71 mln USD według cen ze stycznia 2019 roku). Po uruchomieniu platformy DAO w marcu 2019 roku w celu zarządzania funduszem, założyciele zaczęli słyszeć niezadowolenie członków DAO i wnioski o jego rozwiązanie. Wprowadzili oni [Projekt Ragnarok](https://community.digix.global/#/proposals/0xe7d5d8aefc5f73c4c8bbc716f0c3c2dd52d5282d18217db331da4435b8e6966e) jako opcję rozwiązania DAO i umożliwienia członkom odzyskania ich ETH, z czego członkowie skorzystali. Z żetonu podaży żetonu DAO (DGD) w ilości 2 milionów, 1 milion był przeznaczony na udział w zarządzaniu DAO. Pobieżna analiza propozycji na [stronie internetowej](https://community.digix.global/#/) społeczności DigixDAO sugeruje, że frekwencja w głosowaniu nad wnioskami była regularnie niższa niż 10% DGD, przy czym na większość wniosków głosowało około 20-30 osób. Wniosek dotyczący likwidacji miał znacznie większą frekwencję, przy czym 66% głosujących będącymi z obiegu DGD opowiedziało się za zamknięciem całego przedsięwzięcia. Niniejszy [artykuł](https://blog.coinfund.io/digixdao-divorce-story-6ed74b00e2bd) zawiera dalsze szczegóły, w tym kluczową rolę, jaką odegrały 4 wieloryby DGD, o których mówi się, że są założycielami projektu.

Kolejnym projektem ICO, który w tym miesiącu kończy działalność i zwraca środki jest [TruStory](https://medium.com/trustory-app/why-trustory-is-shutting-down-6d50175628eb).

Decentraland ponownie wykorzystuje swoją platformę zarządzania Agora, do [dwóch](https://decentraland.org/blog/announcements/back-to-the-polls-two-new-agora-votes/) kolejnych głosowań w celu określenia parametrów ekosystemu. Posiadacze MANA głosowali nad tym, jak wysoka powinna być rynkowa [opłata](https://agora.decentraland.org/polls/1d955723-5158-4403-b026-32e974e2fae9) (opłaty są pobierane w MANA i spalane), przy czym 90% głosowało za zwiększeniem opłaty z 1% do 2,5% (pozostałe opcje dotyczyły większych podwyżek). Posiadacze MANA głosowali również nad tym, jaka waga powinna być przypisana posiadaniu [LAND](https://agora.decentraland.org/polls/0387cebc-31a3-4e12-a7b4-e9926dd5b392) w zarządzaniu, po tym, jak wcześniej [zagłosowano](https://agora.decentraland.org/polls/8c4fdc25-1876-4ca5-a2ac-809c13ab840c), aby wskazać, że posiadacze MANA powinni również mieć możliwość głosowania, a w tym sondażu posiadacze MANA głosowali, aby dać każdemu LAND równoważną siłę głosu do 2K MANA (najniższa dostępna opcja). Udział w tych sondażach dotyczących zarządzania wyniósł około 3,5 - 4% znajdującej się w obiegu podaży MANA i około 50 indywidualnych adresów.

Saga o finansowaniu rozwoju Zcash wydaje się wreszcie być [skończona](https://electriccoin.co/blog/dev-fund-poll-shows-consensus/), przynajmniej w tej epoce, jednak nie przed rozwiązaniem niektórych końcowych sporów. Pierwszy z nich dotyczył tego, czy finansowanie ECC powinno być ograniczone w kategoriach USD (ograniczając ekspozycję ECC na aprecjację ZEC). ECC opublikowała [stanowisko](https://electriccoin.co/blog/dev-funds-should-be-in-zcash-not-united-states-dollars/) na temat znaczenia pakietów motywacyjnych wyliczanych w ZEC dla przyciągania i zatrzymywania utalentowanych pracowników, z czteroletnim harmonogramem nabywania uprawnień, aby zachęcić do długiego stażu pracy. Stanowisko to sprzeciwiało się określeniu limitu zarobków ECC w kategoriach USD, ponieważ naruszyłoby to dostosowanie motywacyjne poprzez zmniejszenie ekspozycji ECC na wzrost wartości ZEC.

Było to jedno z pytań, które zadawano długoletnim członkom forum w [ankiecie](https://www.zfnd.org/blog/zip-1014-poll-results/) na platformie do głosowania [Helios](https://vote.heliosvoting.org/faq), z których [wyniki](https://vote.heliosvoting.org/helios/elections/43b9bec8-39a1-11ea-914c-b6e34ffa859a/view) wskazywały, że 56 użytkowników nie chciało limitu, a 18 było przeciwnego zdania. Wyborcy zdecydowali się również na ograniczenie udziału ECC w nagrodach do 35%, co stanowi najmniejszą z przedstawionych opcji. Pozostaje tylko sfinalizowanie szczegółów umowy przez Fundację Zcash i ECC, a 20% nagród ZEC trafi do ECC (35%), Fundacji Zcash (25%) i dużych grantów (zgodnie z decyzją wybranego przez Fundację panelu, 40%) - do kolejnego halveningu epoki, kiedy to zabawa rozpocznie się na nowo.

Związana z tym różnica zdań w ramach tej ostatniej tury głosowania dotyczyła znaczenia przeprowadzenia głosowania monetowego. Dotyczyło to [dwóch](https://forum.zcashcommunity.com/t/staked-poll-on-zcash-dev-fund-debate/34846/121) [kompleksowych](https://forum.zcashcommunity.com/t/community-sentiment-polling-results-nu4-and-draft-zip-1014/35560/375) dyskusji na forum ZEC (miło widzieć, że [wspomniano](https://forum.zcashcommunity.com/t/staked-poll-on-zcash-dev-fund-debate/34846/210) w nich Decred; wydaje się, że istnieje kontyngent społeczności ZEC, która chciałaby przejść na podejście w stylu Decred). Koniec końców temat głosowania monetowego zmienił się w dyskusję, co widać na tym panelu (ostrzeżenie: [link](https://docs.google.com/spreadsheets/d/e/2PACX-1vSlHXhA_NoJy0RW3Gc6YY3bmYcKT_YF8oS_BrSkBnvEGGaJ56WYo7iL_9shuoh-z_DZMYojA6FpLoJv/pubhtml) do Google Drive.

Odbyła się 4. runda eksperymentu Gitcoin Quadratic Funding, a ten [opis](https://vitalik.ca/general/2020/01/28/round4.html) autorstwa Vitalika Buterina opowiada o jej przebiegu. W tej rundzie dodano strumień dotacji medialnych, z mniejszym budżetem (75 tys. USD) niż główny strumień dotacji technicznych (125 tys. USD). Na wczesnym etapie @antiprosynth, wybitna osobowość twitterowa związana z Ethereum, był w kolejce do otrzymania 20 tys. dolarów w środkach wyrównawczych, ale po odrobinie agitacji na ten temat inne inicjatywy otrzymały większe dofinansowanie, a udział funduszy wyrównawczych dla tego konta twitterowego został zmniejszony do 11 393 dolarów. Pojawiło się kilka dalszych [kontrowersji](https://twitter.com/TrustlessState/status/1217894717909848067) w kategorii dotacji medialnych, ponieważ jeden z projektów dotyczył prywatnej grupy, która uzyskała uprzywilejowany dostęp do środków. Głównym beneficjentem w kategorii dotacji na technologię był Tornado.cash, mikser ETH oparty na smart kontraktach.

Jiang Zhuoer ujawnił [plan](https://medium.com/@jiangzhuoer/infrastructure-funding-plan-for-bitcoin-cash-131fdcd2412e) sfinansowania rozwoju oprogramowania Bitcoin Cash pochodzący z 12,5% nagrody blokowej BCH. Obowiązywałoby to wszystkich górników i w swojej pierwotnej formie skierowałoby wszystkie fundusze do określonej firmy. Po otrzymaniu odpowiedzi zwrotnej od niektórych osób ze społeczności BCH opublikowana została zmieniona [wersja](https://read.cash/@Jiang_Zhuoer_BTC.TOP_CEO/bch-miner-donation-plan-update-a45daad6) planu. W tej nowej wersji górnicy będą wybierać, któremu z zestawu wstępnie zatwierdzonych projektów rozwojowych przekazać 12,5% swoich nagród blokowych. Jeśli górnikowi nie spodoba się żadna z dostępnych opcji, może on zdecydować się na spalenie tej części swoich nagród zamiast ich przekazywania. Stanowisko to wydaje się również sugerować obniżenie wskaźnika darowizn z 12,5% do 2-3% i wyraźnie wskazuje, że szczegóły planu są nadal formułowane i pozostają otwarte na dyskusję. Przed wdrożeniem planu odbędzie się runda głosowania hashowego, a tymczasowa fundacja otrzyma darowizny od górników i innych osób, które otrzymają głosy proporcjonalnie do przekazanych przez siebie środków.

Po latach opóźnień w Dash Evolution (pakiet zmian w użytkowaniu takich jak nazwy użytkowników i książki adresowe), w publicznej sieci testowej [uruchomiono jego wersję](https://dashnews.org/long-awaited-dash-evolution-platform-released-on-testnet-with-developer-documentation-hub/) zwaną teraz Dash Platform. Ma to być pierwsze z wielu wydań testnetowych wyprzedzających jakiekolwiek wydanie mainnetowe.

Po tym, jak [nie udało się](https://www.reddit.com/r/dashpay/comments/egl6eu/dash_force_news_defunded_by_masternodes/) zapewnić finansowania ze Skarbca Dash po raz pierwszy od 3 lat, Dash Force zdecydował się na [rozwiązanie](https://app.dashnexus.org/proposals/dash-force-q1-2020/overview) swoich działań po [krytyce](https://www.reddit.com/r/dashpay/comments/esaf38/lets_talk_about_dash_force_news/) ze strony społeczności.

[Dokument roboczy](https://www.ecb.europa.eu/pub/pdf/scpwps/ecb.wp2351~c8c18bbd60.en.pdf?9bd63a4ddea2300dca05f2ccaa08c0e0) Europejskiego Banku Centralnego wskazał, że EBC będzie musiał kontrolować ilość jakiejkolwiek używanej waluty cyfrowej Banku Centralnego (CBDC). Jedna z [analiz](https://cointelegraph.com/news/europe-central-bank-proposes-unattractive-rates-for-digital-currency) z dokumentu sugerowała, że dla portfeli akcji miałyby zostać ustalone nieatrakcyjne kursy, aby zniechęcić do intensywnego używania waluty cyfrowej. Jedną z obaw związanych z intensywnym korzystaniem z CBDC byłoby to, że posiadacze mogliby łatwiej przenosić swoje środki poza jurysdykcję EBC w czasach kryzysu.

Sprawcy stojący za scamem PlusToken są [nadal przerzucają i sprzedają](https://blog.chainalysis.com/reports/plustoken-scam-bitcoin-price) nielegalnie zdobyte 180 000 BTC ze swojej piramidy finansowej. Mimo że w związku z PlusTokenem aresztowano 6 osób, środki wciąż się przemieszczają i są sprzedawane w ramach transakcji pozagiełdowych na [najwyraźniej](https://blog.chainalysis.com/reports/plustoken-scam-bitcoin-price) na Huobi - co może mieć wpływ na cenę BTC. Żetony oszustów są śledzone pomimo stosowania przez nich miksowania i utworzenia 24 000 transakcji obejmujących 71 000 adresów, aby to utrudnić - tylko dlatego, bo wykorzystali użyty już poprzednio adres. Podczas gdy BTC o szacowanej na 185 mln. dolarów wartości zostały sprzedane, 790 z 800 tys. ETH pozostaje nietknięte.

Powierniczy dostawca portfeli bitcoin Bottle Pay [zakończył działalność](https://www.coindesk.com/bitcoin-app-bottle-pay-shuts-down-over-impending-eu-money-laundering-laws) w grudniu, powołując się na rozporządzenie UE w sprawie przeciwdziałania praniu pieniędzy, które wchodzi w życie 10 stycznia 2020 r. Z [ogłoszenia](https://bottlepay.helpscoutdocs.com/article/40-official-announcement-on-the-shutdown-of-bottle-pay): „Ilość i rodzaj dodatkowych danych osobowych, które bylibyśmy zobowiązani zebrać od naszych użytkowników, zmieniłyby obecne doświadczenia użytkowników tak radykalnie i tak negatywnie, że nie jesteśmy skłonni do narzucania takich wymogów na naszą społeczność". Trzymanie się zasad i zamykanie działalności jest przeciwieństwem robienia [czegokolwiek by to nie było](https://thenextweb.com/hardfork/2018/09/05/shapeshift-cryptocurrency-exchange-kyc/), aby utrzymać się na rynku. Przypadek ten może posłużyć jako kolejny sygnał do skoncentrowania wysiłków na ulepszaniu samoobsługowego oprogramowania kryptowalutowego.

Kraken Security Labs [ujawniło](https://blog.kraken.com/post/3662/kraken-identifies-critical-flaw-in-trezor-hardware-wallets/) krytyczną wadę bezpieczeństwa zarówno w portfelach sprzętowych modelu Trezor One, jak i Trezor Model T, która umożliwia wyodrębnienie z nich ziarna w ciągu 15 minut od uzyskania fizycznego dostępu do urządzenia. „Atak wykorzystuje nieodłączną wadę mikrokontrolera używanego w portfelach Trezor. Oznacza to niestety, że zespołowi Trezor trudno jest zrobić cokolwiek z tą luką bez przeprojektowania sprzętu". Zalecane zabezpieczenia mają na celu uniemożliwienie nikomu fizycznego dostępu do urządzenia oraz włączenie funkcji Passphrase w oprogramowaniu klienta Trezor.

500 miliardów dolarów wpompowanych przez Fed w rynek pożyczek krótkoterminowych (rynek repo) zwróciło uwagę Colina Harpera z Bitcoin Magazine, w dobrym [artykule](https://bitcoinmagazine.com/articles/the-fed-has-pumped-500-billion-into-the-repo-market-where-does-it-end), który przedstawia ten temat i pyta, co się dzieje.


## O tym wydaniu

To 22. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: bee, degeri, Dustorf, kozel, richardred, s\_ben
- recenzje i komentarze: ammarooni, buck54321, davecgh, dnldd, emiliomann, jholdstock, lukebp, matheusd
- ilustracja tytułowa: saender
