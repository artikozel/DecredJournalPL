# Decred Journal – Czerwiec 2019

![abstrakcja](../img/journal-201906-384.jpg)

_Obraz: "Anomaly" aut. @saender._

Najważniejsze wydarzenia z czerwca:

* Na platformie Politeia zatwierdzono budżety dla Ditto (PR), programu nagród za wyszukiwanie błędów (Bug Bounty), programu badawczego open source, specyfikacji zdecentralizowanej giełdy wymian i zmiany konsensusowej w nagłówkach bloków, która zwiększy bezpieczeństwo SPV i utoruje drogę do kolejnych usprawnień.

* 10 lipca na App Store trafił portfel iOS v1.0.

* Wypuszczono dcrdata v5.0 zawierającą nowe wykresy i wizualizacje danych do badania danych Decred, poprawki wydajności, bezpieczeństwa i architektury.

* Uproszczenia w UX dla wykonawców zgłaszających faktury oraz poprawki błędów i usprawnienia interfejsu użytkownika w systemie zarządzania wykonawcami (CMS) - ważny krok milowy we wdrażaniu DCC i sprawozdawczości finansowej.

* W tym miesiącu pojawiły się popularne podcasty, a także wzrosła liczba wzmianek nt. Decred w artykułach i w mediach społecznościowych. Wyzwanie #DecredChallenge zyskuje na popularności i zachęca ludzi do przyjrzenia się Decred, zrozumienia go i przedyskutowania, czy zasługuje na bardziej widoczną pozycję w przestrzeni walut kryptograficznych.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Utrzymanie kodu i większa ilość testów.

Zmodernizowano kilka modułów w celu poprawy organizacji i jakości kodu. Wersja 2 modułu `dcrutil` [wprowadza](https://github.com/decred/dcrd/pull/1767) redukuje sprzężęnia oraz zapobiega subtelnym bugom w obsłudze adresów. [Ukończono](https://github.com/decred/dcrd/pull/1698) dużą zmianę polegająca na wprowadzeniu v2 modułu `chaincfg`. Korzyści z tego płynące to, m.in., zmniejszenie powierzchni krytycznego kodu konsensusowego poprzez zdefiniowanie wypłat z bloku 1 jako skryptów zamiast adresów, usunięcie niepożądanych efektów ubocznych po zaimportowaniu pakietu oraz poprawa organizacji parametrów sieci. Wersja 2 modułu `txscript` [wprowadza](https://github.com/decred/dcrd/pull/1774) również wykorzystanie nowych wersji modułów `chaincfg` i `dcrutil`. Okazja do podbicia wersji wykorzystana została również w celu rozwiązania kilku problemów z v1.

Restrukturyzacja generatorów wzorca tła opisana w [numerze majowym](201905.md) została [scalona](https://github.com/decred/dcrd/pull/1748).

Aktualizacje dużych cześci kodu przeprowadzane są bardzo ostrożnie. Najpierw wprowadzana jest nowa wersja modułu, po czym zależne od niej moduły są aktualizane tak, by korzystać z wyższej wersji. Przez cały czas wszystko musi pozytywnie przejść testy oraz budować się bez przeszkód a każdy commit musi z łatwością poddawac się recenzji.

Z drobniejszych udogodnień dodano [wsparcie](https://github.com/decred/dcrd/pull/1757) dla generowania certyfikatów Ed25519 TLS w Go 1.13.

[dcrwallet](https://github.com/decred/dcrwallet): Naprawa bugów oraz stopniowe ulepszenia.

Domyślny [TLS curve](https://github.com/decred/dcrwallet/pull/1468) został zmieniony do bezpieczniejszego P-256. Dodano wsparcie oraz umożliwiono domyślne korzystanie z certyfikatów TLS [Ed25519](https://github.com/decred/dcrwallet/pull/1477) dla Go 1.13.

Poprawiono obsługę biletów poprzez dodanie flagi [`ticketbuyer.limit`](https://github.com/decred/dcrwallet/pull/1476) w celu ograniczenia maksymalnej ilości biletów zakupionych na blok oraz poprawiono [kalkulację salda] (https://github.com/decred/dcrwallet/pull/1330) dla flagi `lockedbytickets` w celu rozwiązania kilku problemów dla  głosujących na  solo, VSP i posiadaczy dzielonych biletów. [Poprawka RPC](https://github.com/decred/dcrwallet/pull/1478) pozwoli VSP pokazywać [niedojrzałe bilety](https://github.com/decred/dcrstakepool/pull/404) oddzielnie. Dodano kilka nowych [API adresu portfela](https://github.com/decred/dcrwallet/pull/1474) w celu uproszczenia rozwoju funkcji związanych z adresami.

[Trwają prace](https://github.com/decred/dcrwallet/pull/1471) mające na celu umożliwienie arbitralnego importu kont xpub. Ta funkcja poprawi [prywatność](https://github.com/decredcommunity/issues/issues/25) umożliwiając automatycznemu ticketbuyerowi uzyskiwanie unikalnych adresów do głosowania, co pozwoli uniknąć ponownego wykorzystywania adresów.

[Decrediton](https://github.com/decred/decrediton): Trwają prace nad integracją [portfela LN](https://github.com/decred/decrediton/pull/2107). Wewnętrzne poprawki w obsłudze [konfiguracji](https://github.com/decred/decrediton/pull/2129), poprawki błędów oraz utrzymanie.

Trwają prace nad proof-of-concept korzystająym z [maszyny o ograniczonych stanach](https://github.com/decred/decrediton/pull/2130) w celu lepszej obsługi złożoności i ulepszenia poprawności przy uruchamianiu.

[Politeia](https://github.com/decred/politeia): Do bazu danych użytkowników Politeia dodano strukturę dla [pluginów](https://github.com/decred/politeia/pull/929), która ułatwia budowanie ogólnych aplikacji na serwerach Politeia (politeiawww). Umożliwi to aplikacjom łatwiejsze przechowywanie danych odnośnie użytkwników (takich jak dane z System Zarządzania Wykonawcami (CMS)) przy korzystaniu z dotychczasowych ścieżek. Stworzono również ogólną [implementację websocketu dcrdata](https://github.com/decred/politeia/pull/933) ułatwiającym tym samym monitorowanie sald adresów i innych danych z blockchaina przez aplikacje budujące na bazie politeiawww.

Wprowadzono szereg stopniowych ulepszeń i poprawek błędów związanych z CMS, aplikacją korzystającą z politeiawww, która ponownie wykorzystuje większość frontu Politei. Tarcie w procesie wystawiania faktur zostało znacznie zredukowane. CMS, zajmujące się przetwarzaniem faktur od wykonawców, jest w fazie produkcji od początku maja.

[Trwa kompletny redesign](https://twitter.com/lukebp_/status/1147528570581000193) Politei mający na celu poprawę interfejsu użytkownika i uspójnienie wyglądu platformy z brandingiem Decred. Prace nad redesignem powinny zakończyć się za około miesiąc. 

[Problem](https://github.com/decred/politeia/issues/882) z podwójnym głosowaniem został zidentyfikowany i ustalony w maju, ale nie został uwzględniony w majowym wydaniu Dziennika. 15 duplikatów głosów w sprawie propozycji Decentralize Treasury Spending trafiło do repozytorium Politeia ze względu na błąd polegający na sprawdzaniu głosów przychodzących z pamięci podręcznej, z jednoczesnym dodawaniem głosów przed ponownym sprawdzeniem pamięci podręcznej. Błąd został zidentyfikowany w momencie zgłoszenia pierwszego duplikatu głosów i szybko został [naprawiony](https://github.com/decred/politeia/pull/893).

Poczyniono postępy ws. wielu instacji Politei działających  [jednocześnie](https://github.com/decred/politeia/issues/665), uczynieniu [adresu email opcjonalnym](https://github.com/decred/politeia/issues/860) oraz publicznego [raportowania](https://github.com/decred/politeia/pull/921) o wydatkach.

[dcrstakepool](https://github.com/decred/dcrstakepool): oprogramowanie VSP w ostatnich miesiącach otrzymuje więcej uwagi. Po majowym [redesignie](https://github.com/decred/dcrstakepool/pull/339) miała miejsce duża refaktoryzacja mająca na celu osiągnięcie [oddzielenia warstw](https://github.com/decred/dcrstakepool/issues/227) pomiędzy elementami oprogramowania, co w małym stopniu przyczyni się do poprawy bezpieczeństwa i wydajności.

[dcrlnd](https://github.com/decred/dcrlnd): Kontynuowane są prace nad przeniesieniem [zmian](https://github.com/decred/dcrlnd/pull/36) z repozytorium [lnd](https://github.com/lightningnetwork/lnd); około 190 (z 270) PR-ów scalonych w lnd od czasu, gdy dcrlnd zostało sforkowane, w tym wiele poprawek błędów i dwie ważne funkcje: bezpieczne kopie zapasowe dla danych off-chain oraz klienci z ochroną przed włamaniami i odwetem.

W odpowiedzi na pytanie o swapy BTC-DCR na LN, @matheusd [wyjaśnił](https://www.reddit.com/r/decred/comments/c17xxh/is_it_possible_to_exchange_btclightning_for/ere1skv/) stan wielu elementów układanki.

[dcrandroid](https://github.com/decred/dcrandroid): Drobne poprawki błędów i ulepszenia interfejsu użytkownika, nowe tłumaczenia na [hiszpański](https://github.com/decred/dcrandroid/pull/363) i [portugalski (BR)](https://github.com/decred/dcrandroid/pull/367) oraz nowa funkcja [wysyłania i szacowania](https://github.com/decred/dcrandroid/pull/371).

[dcrios](https://github.com/raedahgroup/dcrios): v1.0.0 została [wydana](https://www.reddit.com/r/decred/comments/cbjqff/decred_wallet_for_ios_v100_on_the_app_store/) w [App Store](https://apps.apple.com/us/app/decred-wallet/id1462247643) po 6 miesiącach aktywnej pracy!

Pierwsze wydanie jest dostępne w języku angielskim, rosyjskim i uproszczonym chińskim, z większą ilością tłumaczeń w drodze. Poprawiono błędy zgłoszone w [Release Candidate 1](https://www.reddit.com/r/decred/comments/bxje6l/decred_wallet_for_ios_release_client_1/) i [Release Candidate 2](https://www.reddit.com/r/decred/comments/c7ir8d/decred_wallet_for_ios_release_client_2/) oraz wprowadzono drobne poprawki w interfejsie użytkownika.

Gratulacje dla zespołu dcrios: macsleven, itswisdomagain, collins, ensoreus, rktr09 (deweloperzy), DZ (design) i wszystkich testerów.

[dcrdata](https://github.com/decred/dcrdata): Poważne wydanie, v5.0 jest teraz online. Poza poprawą architektury, bezpieczeństwa i wydajności, v5.0 wprowadza szereg nowych wykresów i wizualizacji do badania danych Decred.

Nowa strona [rynków](https://explorer.dcrdata.org/market?chart=depth&xc=aggregated&bin=1h&stack=1) pokazuje dane z kilku głównych giełd, w tym zagregowane dane cenowe DCR, głębokość księgi zamówień, wykresy świecowe i inne. Strona [propozycji](https://explorer.dcrdata.org/proposals) wyszła z bety i pokazuje statystyki i wykresy głosowania (w czasie rzeczywistym i historycznym) dla wszystkich propozycji na Politei. Wykres [głosów nieoddanych](https://explorer.dcrdata.org/charts?chart=missed-votes) pokazuje ważny wskaźnik zdrowia sieci.

Ulepszenia architektury obejmują aktualizację do [PostgreSQL](https://github.com/decred/dcrdata/commit/676e2ae2381e900854c2fe664a92d39a122d6ed7) (tryb lite został usunięty), ulepszone wersjonowanie schematów baz danych, [refaktoryzację](https://github.com/decred/dcrdata/commit/856d0466c82338dd1aaec2945ab189da3c4ab060) strumienia powiadomień dcrd, domyślne wsparcie eksperymentalne dla [CockroachDB](https://github.com/decred/dcrdata/commit/3ddc034e672c84313fae789c558ead139ad39f8a), [block-prefetching](https://github.com/decred/dcrdata/commit/5ceb56b5c8e1ed53b6b92b5deee6e2a05903f61f) oraz nową wersję modułu pubsub z subskrypcjami adresowymi.

Wykresy powinny również ładować się szybciej wraz z poprawą wydajności, w tym [ulepszonym](https://github.com/decred/dcrdata/commit/5eb60c4633d128ab64783b75b851a012ed8024fa) zarządzaniem pamięcią i nowym wstępnie zakodowanym systemem buforowania wykresów.

Pełna lista zmian znajduje się w dokumencie [Release Notes](https://github.com/decred/dcrdata/releases/tag/release-v5.0.0).

[docs](https://github.com/decred/dcrdocs): Użycia sformułowania "DAE" (Distributed Autonomous Entity) zostały [zastąpione](https://github.com/decred/dcrdocs/pull/958) przez "DAO" (Distributed Autonomous Organization). Nowa strona dodaje szczegóły na temat tego, jak działa [algorytm](https://github.com/decred/dcrdocs/pull/963) używany do pseudolosowego wybierania biletów do głosowania.

Pozostałe:

* Pliki binarne Decred mają od teraz swoje mirrory na IPFS w przypadku, gdyby GitHub/AWS stał się niedostępny. Jeśli uruchomisz węzły IPFS, możesz spiąć hash dla dodatkowej redundancji i lepszej wydajności przy pobieraniu plików. Na liście znajdują się również 3 bramy HTTP, dzięki czemu osoby, które nie korzystają z IPFS, mogą również uzyskać dostęp do plików. Najnowszy skrót IPFS zawsze będzie wyświetlany tutaj: [dcr.jz.bz](https://dcr.jz.bz/).
* [Pliki binarne Decred](https://keybase.pub/jz_bz/decred/dcr-binaries/) i [filmy wideo](https://keybase.pub/jz_bz/decred/dcr-videos/) mają też swoje mirrory w bazie danych Keybase.
* Kod źródłowy znajduje się na stronie [GitLab](https://gitlab.com/dcr-bak).
* [dcr-setup](https://github.com/jzbz/dcr-setup): skrypt konfiguracji portfela do głosowania dla dystrybucji Linuksa opartych na Debianie i RedHacie.

Statystyki aktywności deweloperskiej na czerwiec: 283 aktywne PR-y, 321 master commitów, 62 tys. dodanych i 29 tys. usuniętych linijek kodu spośród 15 repozytoriów. Wkład pochodził od 1-8 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: Marton ([politeia](https://github.com/decred/politeia/commits?author=martonp)), Amos Ezeme ([dcrandroid](https://github.com/decred/dcrandroid/commits?author=crux25)), Quadri Anifowose ([dcrandroid](https://github.com/decred/dcrandroid/commits?author=Quadriyanney)), Lore ([dcrandroid](https://github.com/decred/dcrandroid/commits?author=hanelore)).

Podczas gdy commity autorstwa @DZ's zostały scalone z repozytorium   [dcrandroid](ttps://github.com/decred/dcrandroid/commits?author=denyszayets) zostały odnotowanee po raz pierwszy, należy zauważyć, że jest on długotrwałym współpracownikiem projektuy Decred.

## Zarządzanie

W czerwcu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 15 135 DCR i wydał 6 657 DCR. Wykorzystując średnią dzienną stawkę DCR/USD w czerwcu, wynoszącą 28,90 USD, daje to 437 tys. dolarów wpływów i 192 tys. dolarów kosztów. Ponieważ płatności te zostały dokonane za prace ukończone w maju, warto również rozważyć je w kontekście majowej średniej dziennej stawki 27,71 USD - w tym przypadku otrzymane/wydane kwoty USD wynoszą 419K/184K USD. Na dzień 1 lipca saldo Skarbca wynosi 622 472 DCR (18,36 mln USD po kursie 29,50 USD/DCR).

Poniżej przedstawiono stan propozycji na dzień 1 lipca.

Zatwierdzono następujące propozycje:

* [Faza 2 programu Decred Bug Bounty](https://proposals.decred.org/proposals/073694ed82d34b2bfff51e35220e8052ad4060899b23bc25791a9383375cae70) - 93.5% poparcia przy udziale 31.5% głosujących
* [Faza 2 Ditto Communications](https://proposals.decred.org/proposals/52ea110ea061c72d3b31ed2f5635720b212ce5e3eaddf868d60f53a3d18b8c04) - 75.8% poparcia przy udziale 29.2% głosujących
* [Faza 2 Decred Open Source Research](https://proposals.decred.org/proposals/67de0e901143400ae2f247391c4d5028719ffea8308fbc5854745ad859fb993f) - 90.2% poparcia przy udziale 32.4% głosujących
* [Dokument specyfikacyjny Zdecentralizowanej Giełdy Wymian](https://proposals.decred.org/proposals/a4f2a91c8589b2e5a955798d6c0f4f77f2eec13b62063c5f4102c21913dcaf32) - 98.4% poparcia przy udziale 30% głosujących
* [Zmiana zasad konsensusu dla nowego nagłowka bloków](https://proposals.decred.org/proposals/0a1ff846ec271184ea4e3a921a3ccd8d478f69948b984445ee1852f272d54c58) - 99.2% poparcia przy udziale 33.5% głosujących. Komentujący w temacie propozycji oraz na [Reddicie](https://www.reddit.com/r/decred/comments/buv18c/block_header_commitments_consensus_change_proposal/) docenili to, że propozycja posiada sekcje zarówno dla czytelników bardziej zapoznanych z technologią, jak i dla publiczności nietechnicznej, a także zauważyli to, jak system głosowania on-chain pozwala na gładkie aktualizacje bez lat bezproduktywnych sporów.

Opublikowano 2 nowe prpozycje:

* [Dodatkowa propozycja dla przewodników po Decred aut. Denniego Lovejoy'a](https://proposals.decred.org/proposals/d8d7ff7ad138ed322422aaa4d2a3e1c61f296ae56a2c2316cc5ecd10cf8dd8bd).
Propozycja ta wnosi o rozszerzenie oryginalnego budżetu na przewodniki wideo z 750 USD do 7500 USD. @Denni Lovejoy wniósł o porzucenie propozycji ze względu na komentarze wyrażające sprzeciw. Trwa dyskusja na temat tego, jak obchodzić się z sytuacjami, w których praca wykonana w ramach propozycji znacznie wychodzi poza jej budżet.

* [Kampania medialna Decred - Crypto Economy - 2019/2020](https://proposals.decred.org/proposals/1a367dcb91b55c60ad5fd038b219201154fcab965edd7a4639f157e409b1f4bf).
Propozycja wnosiła o 33 tys. dolarów w celu promowania Decred na szereg różnych sposóbów, wliczając w to reklamy na banerach, artykuły w prasie, rozdawanie DCR czy biuletyn. Komentującyli zauważyli, że niektóre z powyższych metod są już w użyciu a inne nie mają ich poparcia, przez co propozycja została porzucona.

Ten [wykres](https://twitter.com/RichardRed0x/status/1139860218010058753) pokazuje udział wyborców Politei w 28 propozycjach, które do tej pory zakończyły głosowanie.

Więcej informacji na temat tego, co dzieje się w Politei, można znaleźć w [dwóch](https://medium.com/politeia-digest/issue-17-may-28-june-9-bc5bb77e4f6c) [numerach](https://medium.com/politeia-digest/issue-18-june-10-june-29-97d140569ad0) Politeia Digest opublikowanych w czerwcu.

W związku z [pytaniami](https://www.reddit.com/r/decred/comments/bx00fu/so_about_the_exmo_exchange/) na Reddicie, Exmo zamieściło krótką [aktualizację](https://twitter.com/Exmo_Com/status/1138020825137930240) i [umieściło DCR](https://exmo.com/en/news_view?id=2776) na swojej giełdzie w dniu 18 czerwca.

Kilka postów na subreddicie r/decred dążyło do przebadania społeczności Decred na temat [optymalnego progu zatwierdzenia propozycji w Politei](https://www.reddit.com/r/decred/comments/bynidz/poll_optimal_politeia_pass_threshold/), [zmiany nazwy Decrediton na Declaration](https://www.reddit.com/r/decred/comments/c4ilpw/poll_rename_decrediton_to_declaration/), [nazwania Decreditona czymś innym niż portfelem](https://www.reddit.com/r/decred/comments/c52hqd/question_is_a_hybrid_finance_governance_tool/), oraz zapytania, czy Decred powinien rozpocząć [korzystanie z terminu DAO zamiast DAE](https://www.reddit.com/r/decred/comments/c02geh/poll_rename_dae_to_dao/) w celu opisania zdecentralizowanego zarządzania projektu przez interesariuszy.

Ostatni sondaż (zmiana nazwy DAE na DAO), może być uznany za "miękką propozycję" aut. @s\_ben. Uzasadnieniem tej propozycji jest to, że chociaż nazwa DAE (Distributed Autonomous Entity) została pierwotnie wybrana w celu uniknięcia skojarzenia z [hackiem DAO](https://www.google.com/search?q=ethereum+dao+hack) w sieci Ethereum, DAO stały się od tamtego czasu gorącym tematem w krypto, z niewielkim skojarzeniem z hackiem DAO w publicznej świadomości. Ponieważ Decred ma prawdopodobnie bardziej uzasadnione prawo do tego terminu niż inne projekty, zbudowawszy już wcześniej funkcjonujące DAO (które produkuje ten biuletyn), uczestniczenie w rozmowach na ten temat nabiera nowego sensu. Rozważano propozycję Politeia, jednakże, nie było żadnych zastrzeżeń do zmiany na różnych kanałach komunikacji (co zostało uchwycone w tym [komentarzu](https://www.reddit.com/r/decred/comments/c02geh/poll_rename_dae_to_dao/er1g4px)), a ogólny konsensus był taki, że bez silnego sprzeciwu, taka zmiana nie wymagała propozycji Politeia. @s\_ben zmienił odniesienia w [dokumentacji](https://docs.decred.org/governance/politeia/overview/#decentralized-autonomous-organization-dao) i złożył [pull request](https://github.com/decred/dcrweb/pull/681) w celu zmiany terminu na stronie decred.org. Działania i dyskusje na ten temat są śledzone w [tej kwestii](https://github.com/decredcommunity/issues/issues/134).

Choć niektóre z tych sondaży i dyskusji wokół nich były interesujące, członkowie społeczności zauważyli, że istnieją problemy z wykorzystaniem Reddita i stron z sondażami do oceny opinii interesariuszy Decred. Platformy te są otwarte dla osób, które nie są interesariuszami i pozwalają na to, aby sondaże były arbitralnie usuwane lub modyfikowane przez ich twórcę. W dyskusji na temat tego zjawiska wydaje się, że istnieje silne poparcie dla [decredowej wersji Reddita](https://github.com/decredcommunity/issues/issues/38), opartej na Politei, która pozwoliłaby na stworzenie ograniczonej liczby sondaży dla posiadaczy biletów.

## Sieć

Hashrate: czerwcowy hashrate na początku miesiąca wyniósł ~504 Ph/s a zamknął miesiąc w ok. ~540 Ph/s, zaliczając niż w ok. 369 Ph/s oraz szczyt w wys. 607 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 2 lipca wyglądała następująco: lab.antpool.com 18%, UUPool 17,7%, F2Pool 14%, Poolin 9,5%, BTC.com 9%, Luxor 2,2%, CoinMine 0,21%, BeePool 0,15%, suprnova 0,03%  oraz pozostałe 29%, za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu z okresu 30 dni wynosiła 120 DCR (+4) za danymi z dcrstats.com. Cena wahała się między 116,8-127,3 DCR. Zablokowana kwota wynosiła 4,75-4,84 mln DCR, co odpowiadało [48,01-49,03%](https://charts.dcr.farm/d/000000003/proof-of-stake?orgId=1&from=1559347200000&to=1561939200000) dostępnej podaży.

Węzły: w czerwcu było około 200 węzłów nasłuchujących i 340-510 węzłów normalnych za danymi z [dcr.farm](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1559347200000&to=1561939200000). Na dzień 8 lipca ok. 80% z nich to wersja v1.4.0, 9% korzysta z dcrwallet w wersji v1.4.0 (SPV) a 4% korzysta z wersji v1.5.0(pre) deweloperskiej.

dcr.farm otrzymało nowy dashboard [Lightning Network](https://charts.dcr.farm/d/DHPdAO4Wz/lightning-network?orgId=1). Na dzień 8 lipca sieć testnet DCR LN składa się z 15 węzłów, 45 kanałów i całkowitej pojemności 370 DCR.

W dniu 27 czerwca podaż DCR [przekroczyła](https://twitter.com/raedahgroup/status/1144655370234880000) 10 mln DCR. 10 milionów DCR w dystrybucji oznacza, że pierwotny [premine](https://docs.decred.org/advanced/premine/) stanowi 17% obecnego w DCR w obiegu, jak dotąd górnicy PoW otrzymali 50%, wyborcy PoS 25%, a Skarbiec 8%.

Były prośby o wsparcie ze strony posiadaczy biletów, którzy twierdzili, że ich bilety zostały [przegapione](https://www.reddit.com/r/decred/comments/c862ee/assistance_needed_missed_tickets/) przez niektórych VSP. Po przeprowadzeniu dochodzenia odkryto, że [Grassfed](https://dcr.grassfed.network/) i [d1pool](https://d1pool.com) zostały odcięte od sieci i nie wzięły udziału w głosowaniu biletów. Grassfed odpowiedział i obiecał nadążać za przyszłymi aktualizacjami klientów. Nie byliśmy w stanie dotrzeć do d1pool i obecnie trwa dyskusja na temat usunięcia ich z [listy VSP](https://decred.org/vsp/) na decred.org.

Poruszono też [kwestię na GitHubie](https://github.com/decred/dcrstakepool/issues/413) i na [czacie](https://matrix.to/#/!HEeJkbPRpAqgAqgAwhXWO:decred.org/$156207152510654HMiFp:decred.org) na temat tego, jak można uniknąć takich problemów w przyszłości. Innym omawianym pomysłem był stały wysiłek, aby nakłaniać ludzi do zakładania własnych [portfeli do głosowania](https://matrix.to/#/!dhHYPTtCtvPSUfTepT:decred.org/$156207972910815kERGq:decred.org).

## Integracje

Exmo dotrzymało obietnic w złożonej przez siebie [propozycji](https://proposals.decred.org/proposals/950e8149e594b01c010c1199233ab11e82c9da39174ba375d286dc72bb0a54d7) i [włączyło](https://exmo.com/en/news_view?id=2776) pary DCR/BTC, DCR/RUB i DCR/UAH w dniu 18 czerwca.

Vertbase dodało [zamówienia odnawialne](https://twitter.com/vertbase/status/1141826092564701184) oraz opcję [sprzedaży](https://twitter.com/vertbase/status/1141735926059716611) aktywów cyfrowych w USD dla klientów z USA.

EliteX [umieściło](https://twitter.com/elitexcrypto/status/1143044131800977409) DCR na swojej platformie i napisało [artykuł](https://medium.com/@elitexexchange/the-lowdown-on-decred-dcr-2a36520079f5) w celu przybliżenia Decred swoim użytkownikom.

MXC Exchange [dodało](https://twitter.com/wanbihou/status/1143846271645437952) parę DCR/USDT.

Bleutrade [ogłosiło](https://bleutrade.com/announcements/), że DCR ma zostać usunięte z ich gieły w ramach masowego sprzątania zaplanowanego na 15 lipca - drugiego już w tym roku ([dyskusja](https://www.reddit.com/r/decred/comments/c86a75/bleutrade_will_delist_dcr_20190715_1500_utc/)). Bleutrade okazało ogromne [wsparcie](https://twitter.com/BLEUTRADE/status/999683568791060481) dla Decred, gdyż było to pierwsze miejsce, gdzie można było wymienić Decred już w pierwszym dniu działania sieci w dniu [8 lutego 2016 r.](https://bitcointalk.org/index.php?topic=1290358.1640).

Część integracji z Trust Wallet leżąca po stronie Decred jest [bliska ukończenia](https://github.com/trezor/blockbook/pull/216). Zatwierdzona przez wyborców w marcu [propozycja](https://proposals.decred.org/proposals/2ababdea7da2b3d8312a773d477272135a883ed772ba99cdf31eddb5f261d571) podzieliła pracę pomiędzy zespół Trust Wallet, któremu powierzono zadanie integracji portfela podstawowego (ukończon)), oraz Decred, któremu powierzono zadanie integracji z serwerem Blockbook, który Trust Wallet wykorzystuje do przechowywania danych transakcyjnych.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

Nadal czynione są postępy w zakresie współpracy zewnętrznej i nawiązywania kontaktów, z dużym naciskiem na edukację i ułatwianie nauki o Decred. Prowadzane są konkretne prace nad stworzeniem podręcznika mediów społecznościowych, który umożliwi każdemu członkowi społeczności wniesienie swojego wkładu. [Checkmate](https://twitter.com/_Checkmatey_) pojawił się na Twitterze, wprowadzając hashtag [#DecredChallenge](https://twitter.com/hashtag/DecredChallenge) i [wyzwanie](https://twitter.com/_Checkmatey_/status/1145764832362319872), aby każdy pouczył się Decred przez 30 dni i wyjaśnił, dlaczego, jego zdaniem, Decred nie powinien być #2 według kapitalizacji rynkowej. Wyniki są bardzo pozytywne, a aktywność i skuteczność Decred w mediach społecznościowych znacznie wzrosła. To bardzo ważne, aby polubić i skomentować historie o Decred, ponieważ zwiększa to ich zasięg i umożliwia napisanie większej ilości historii.

Budując w kwestii edukacji, praca na stronie internetowej jest bliska fazy produkcji, z nowym filmem wprowadzającym i nowymi podstronami na temat bezpieczeństwa, adaptowalności, samofinansowania, historii i ogólnym repozytorium na temat edukacji. Praca ta pomoże wesprzeć rozwój społeczności poprzez ułatwienie zrozumienia Decred.

@anshawblack wydał odcinki podcastu Decred in Depth z udziałem @lukebp i Joela Monegro. @Dustorf i @jy-p nagrali odcinki Decred Assembly, w tym Decred Distributed z @akinsawyerr uwzględniającym Decred w Afryce, Dogłębną Analizę w udziałem @moo31337 na temat propozycji odnośnie Skarbca, oraz Decred Distributed z @richardred. Te dwa ostatnie odcinki ukażą się wkrótce.

Na całym świecie planowane są różne wydarzenia, w tym w Niemczech, Japonii, Chinach i Toronto. Projekt ma budżet na duże wydarzenie w Europie i Azji w 2019 r. i nie podjął jeszcze konkretnego zobowiązania. Jeśli masz konkretne pomysły, podziel się z nami na kanale #event_planning. Liczymy na to, że społeczność na całym świecie pomoże nam zidentyfikować i wykorzystać możliwości medialne.

Decred poczynił znaczące postępy w kwestii zarządzania. Wzmianka o stakingu w CoinDesk jest prekursorem manifestu zarządzania Decred, a @akinsawyerr [wziął udział](https://github.com/decredcommunity/events/blob/master/reports/20190701-wharton-governance-workshop-san-francisco-usa.md) w konferencji Wharton Governance wraz z czołowymi prelegentami w tej dziedzinie. Odbyło się wiele dyskusji na temat Decred, który spotkała się z powszechnym uznaniem jako pionier i lider w kwestii zarządzania. Decred został zaproszony do zabrania głosu na następnej takiej konferencji w Japonii.

Czerwcowe osiągnięcia Ditto:

* Umożliwiliśmy wywiad wprowadzający w temat zarządzania i stakingu między @jy-p i CoinDesk.
* Umożliwiliśmy wywiad między analitykiem Legacy Research Gregiem Wilsonem i @moo31337, który przedstawił przegląd i stan rozwoju Decred, z myślą o inwestorach.
* Zabezpieczyliśmy wystąpienie @jy-p w podcaście [Off the Chain](https://podcasts.apple.com/us/podcast/jake-yocom-piatt-project-lead-for-decred-crypto-ego/id1434060078?i=1000441486954)  z Anthonym Pompliano, założycielem Morgan Creek Digital.
* Zabezpieczyliśmy wywiad w podcaście [Chain Reaction](https://www.youtube.com/watch?v=kO_11gehyls) Toma Shaughnessy'ego z Delphi Digital z @jy-p.
* Zdobyliśmy wzmianki o Decred nt. Facebook Libra w [CNBC](https://www.cnbc.com/2019/06/18/facebooks-libra-will-give-billions-access-to-cryptocurrency.html), [Mashable](https://mashable.com/article/facebook-libra-experts/), [CoinTelegraph](https://cointelegraph.com/news/what-is-libra-breaking-down-facebooks-new-digital-currency) oraz [Forbes](https://www.forbes.com/sites/kenrapoza/2019/06/20/facebooks-libra-coin-is-both-vampire-project-and-regulatory-nightmare/) ([dwukrotnie](https://www.forbes.com/sites/rachelwolfson/2019/06/19/facebooks-cryptocurrency-libra-validates-blockchain-but-industry-experts-voice-concerns/)!). Uwaga: CNBC i Mashable to główne media docierające do ludzi, którzy niewiele wiedzą o krypto; przedstawiając im Decred, znacznie poszerzamy swój zasięg.
* Zamieściliśmy [cytat](https://www.coindesk.com/how-blockchain-voting-is-supposed-to-work-but-in-practice-rarely-does) od @jy-p na temat zarządzania w CoinDesk.
* Zamieściliśmy [cytat](https://cointelegraph.com/news/internet-authority-history-of-centralized-companies-being-hostile-toward-crypto) @richardred w artykule CoinTelegraph na temat "zamknięcia" CCN.
* Uczestniczyliśmy w spotkaniu Bitcoin w San Francisco, na którym organizatorzy wyrazili zainteresowanie zorganizowaniem panelu zarządzania z Decred w roli prelegenta.
* Stworzyliśmy [poradnik](https://github.com/decredcommunity/pr/blob/release/engagement-guide-delist.md) dla mediów społecznościowych na temat tego, jak reagować (lub nie) na geofencing lub wykreślenie z listy.
* Zmobilizowaliśmy społeczność do zaangażowania i podzielenia się relacjami w mediach społecznościowych.
* Zgłosiliśmy [2 fazę propozycji dot. komunikacji Ditto](https://proposals.decred.org/proposals/52ea110ea061c72d3b31ed2f5635720b212ce5e3eaddf868d60f53a3d18b8c04) na platformie Politeia, wzięliśmy udział w dyskusji, a następnie dzięki zainteresowaniu ze strony społeczności Decred nasza propozycja została zatwierdzona! Dziękujemy za wotum zaufania. To absolutna radość z pracy nad projektem Decred i nie możemy doczekac się pracy dla Was przez kolejne 6 miesięcy.

## Eventy

Na których byliśmy:

* 5 czerwca - [Decred x Blueyard](https://www.eventbrite.co.uk/e/decred-x-blueyard-berlin-meetup-tickets-61631192556) - Berlin, Niemcy. Pełny raport aut. @Haon jest [tutaj](https://github.com/decredcommunity/events/blob/master/reports/20190605-decred-x-blueyard-berlin-germany.md).
* 11 czerwca - Decred przemysłowe wykorzystania blockchaina - La Paz, Boliwia. @elian wygłosił przemówienie do 50-60 studentów inżynierii z Wyższego Uniwersytetu w San Andrés. ([zdjęcia](https://twitter.com/Decred_ES/status/1138899455346954240))
* 12 czerwca - [Decred: Zdecentralizowana Autonomiczna Organizacja](https://www.meetup.com/Decred-Washington-DC-Meetup-Group/events/261144707/) - Waszyngton DC, USA. W wydarzeniu uczestniczyło łącznie około 11 osób. @akinsawyerr wygłosił prezentację przeglądową na temat Decred i odpowiedział na pytania publiczności. Wydarzenie było współorganizowane przez TechSpace Balston i Dartmouth Entrepreneurial Network of DC. Zadano wiele pytań na temat naszego procesu zarządzania, tego, jak płacimy i jak zarządzamy wykonawcami oraz czym Decred różnił się od takich platform jak Ethereum z perspektywy uczestnictwa/wkładu.
* 13 czerwca - [CryptoMeeting](https://twitter.com/Decred_ES/status/1138908828370706432) - La Paz, Boliwia. @elian wygłosił wykład na temat zarządzania blockchainem dla lokalnej społeczności kryptograficznej. ([zdjęcia](https://twitter.com/gamelendrez/status/1139325915475959808))
* 18 czerwca - [TF Blockchain](https://www.eventbrite.com/e/tf-blockchain-portland-ep-03-june-18th-2019-tickets-61667348700) - Portland, USA.
* 18 czerwca - [NetEase](https://twitter.com/wanbihou/status/1142243367905943552) - Wuhan, Chiny. @Dominic wprowadził unikalny profil finansowania Decred i nadchodzącego DAO. ([zdjęcia](https://twitter.com/wanbihou/status/1142243367905943552))
* 19 czerwca - [Reston Virginia Golang meetup](https://www.meetup.com/Golang-Reston/events/sfsjmpyzjbzb/) - Reston, Virginia, USA. W wydarzeniu wzięło udział 21 osób, głównie programistów. @akinsawyerr wygłosił prezentację przeglądową na temat Decred i odpowiedział na pytania publiczności. Gospodarzem wydarzenia był Comcast. Większość pytań dotyczyła sposobu pozyskiwania kryptowalut, zrozumienia podstawowej terminologii oraz potencjalnego wpływu ekonomicznego kryptowalut. Po wydarzeniu, w którym uczestnik poprosił, aby dowiedzieć się więcej na temat tego, co Decred zbudował wykorzystując Golang, odczuć można pragnienie zobaczenia rzeczywistego dema kodu itp.
* 19-23 czerwca - [Campus Party Brasilia](https://brasil.campus-party.org/) - Brasilia, Brazylia. Decred był [dobrze](https://twitter.com/Decred_BR/status/1141782527637688322) [reprezentowany](https://twitter.com/Decred_BR/status/1141767693344935941) kolejny już raz na Campus Party. @matheusd napisał [raport](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$156172492478087gSMWo:matrix.org) na czacie, opisując udane wydarzenie, w którym Decred miał silną obecność i uczestniczył w 3 różnych zajęciach (krypto dla dzieci, warsztaty LN paywall i udział w panelu na głównej scenie). ([wideo](https://www.youtube.com/watch?v=w792TaZTxgA))
* 20 czerwca - [Beijing Decred Meetup](https://twitter.com/DecredCN/status/1138739545594220544) - Pekin, Chiny. Decred był reprezentowany przez @changhugo i @Dominic. W wydarzeniu wzięło udział 100 osób z transmisją na żywo do ponad 4000 widzów. Pełny raport @changhugo jest [tutaj](https://github.com/decredcommunity/events/blob/master/reports/20190620-first-meetup-beijing-china.md).
* 26 czerwca - [SF Decred Devs x Coinbase Custody Happy Hour](https://www.meetup.com/San-Francisco-Decred-Meetup/events/262420787/) - San Francisco, USA. ([zdjęcia](https://twitter.com/CryptoLeslie/status/1144092778017648641))
* 28 czerwca - [Aktualizacja społeczności o wszystkich rsprawach związanych z Decred](https://www.meetup.com/Decred-Australia/events/262550167/) - Melbourne, Australia.

Nadchodzące:

* 11 lipca - [Pogawędka z Joshuą Buirskim](https://www.eventbrite.com/e/fireside-chat-with-joshua-buirski-decred-asia-pacific-lead-tickets-64832494737) - Nowy Jork, USA. Współgospodarzami są Staked i TokenTax.
* 24 lipca - Decred Meetup - Chicago, USA.

W odnowionym [repozytorium raportów z wydarzeń](https://github.com/decredcommunity/events) jest teraz  14 przyzwoitych raportów.  [Przesyłajcie](https://github.com/decredcommunity/events/wiki/Submit-Event-Report) swoje raporty i podzielcie się nimi na stronie Reddit/Twitter, aby pokazać, jak wiele wydarzeń związanych z Decred ma miejsce każdego miesiąca.


## Media

Wytyczne Ditto w zakresie PR zostały zebrane w nowym [repozytorium](https://github.com/decredcommunity/pr), obecnie obejmującym [przekaz podstawowy](https://github.com/decredcommunity/pr/blob/release/foundational-messaging.md), [przekaz w kwestii biletów](https://github.com/decredcommunity/pr/blob/release/ticket-messaging.md) oraz [przewodnik](https://github.com/decredcommunity/pr/blob/release/engagement-guide-delist.md) o tym, jak reagować na usunięcie z wykazu/geofencing.

Uruchomiono nowe repozytorium [wiki dla społeczności](https://github.com/decredcommunity/wiki) dla informacji, które nie pasują na decred.org lub do dokumentacji. Pierwsza utworzona strona jest wyczerpującą listą grup [mediów społecznościowych](https://github.com/decredcommunity/wiki/blob/master/wiki/social-media.md) Decred.

Wybrane artykuły:

* Kwadrant zarządzania blockchainem aut. @Haon ([medium](https://medium.com/@NoahPierau/the-blockchain-governance-quadrant-2a878a9cacb9))
* Regulatorzy nadchodzą - kanarek w kopalni mocy obliczeniowej Decred: Część I, aut. u/Fiach\_Dubh ([medium](https://medium.com/coinmonks/the-regulators-are-coming-a1ba2f8c02be)) - zob. również [dyskusję](https://www.reddit.com/r/decred/comments/byffz1/the_regulators_are_coming_canary_in_the_decred/) na temat Reddit.
* Dlaczego nazwa 'Decred' jest świetna, aut. @Haon ([medium](https://medium.com/decred/why-the-name-decred-is-awesome-9627ae9b4e2))
* Przeszkody w adopcji kryptowalut w Afryce, aut. @George Pro ([medium](https://medium.com/@aappiahpro1/the-roadblocks-to-cryptocurrency-adoption-in-africa-3be2c656ec07))
* Decred Australia - Budowanie społeczności cegiełka po cegielce, aut. @zohand ([medium](https://medium.com/@sahand.bagheri/decred-australia-building-a-community-brick-by-brick-89928041687e))
* Staking to nie tylko sposób, żeby zarabiać w krypto - i nie powinien nim być, aut. @jy-p ([coindesk.com](https://www.coindesk.com/staking-isnt-just-a-way-to-earn-crypto-money-and-it-shouldnt-be)) - również [w języku koreańskim](https://www.coindeskkorea.com/staking/).
* Cała prawda o Decred, aut. EliteX Exchange ([medium](https://medium.com/@elitexchange/the-lowdown-on-decred-dcr-2a36520079f5)) - EliteX exchange przeprowadziła wywiad z @changhugo i napisała krótki przegląd, który opublikowała w tym samym czasie, co zamieszczenie DCR na swojej giełdzie.
* Kryptowaluty: pomylona tożsamość, aut. @nnnko56 ([write.as](https://write.as/nnnko56/cryptocurrency-a-mistaken-identity)) - ten artykuł traktuje kryptowaluty jako coś więcej niż ta etykieta sugeruje i opowiada się za szerszym zrozumieniem tych projektów jako posiadających ważne elementy społeczne, czyli "kryptospołeczeństwa".

Tłumaczenia:

* [Decred jako dostawca infrastruktury DAE](https://medium.com/@changhugo/decred-as-a-dae-infrastructure-provider-970677f38179) - [w języku włoskim](https://medium.com/decred-ita/decred-come-fornitore-di-infrastruttura-dae-310df09f8595) oraz [rosyjskim](https://medium.com/decred-russia/decred-%D0%BA%D0%B0%D0%BA-%D0%BF%D0%BE%D1%81%D1%82%D0%B0%D0%B2%D1%89%D0%B8%D0%BA-%D0%B8%D0%BD%D1%84%D1%80%D0%B0%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D1%8B-dae-1f89952b0bab), aut. @DZ.
* [Podstawowy przekaz Decred](https://github.com/decredcommunity/pr/blob/release/foundational-messaging.md) - [w języku wietnamskim](https://github.com/raedahgroup/translations/blob/master/vietnamese/decred_foundational_messaging.md), aut. @duyenemdo.
* [Decred: Od czego wszystko to się zaczęło?](https://thedecreddigest.com/2017/06/10/decred-where-did-it-all-begin/) - [w języku arabskim](https://insaf01.github.io/decred-arabic/articles/decred-where-did-it-all-begin.html), aut. @arij i [wietnamskim](https://github.com/raedahgroup/translations/blob/master/vietnamese/decred_where_did_it_all_begin.md), aut. @duyenemdo.
* [Dlaczego nazwa 'Decred' jest świetna](https://medium.com/decred/why-the-name-decred-is-awesome-9627ae9b4e2) - [w języku arabskim](https://insaf01.github.io/decred-arabic/articles/why-the-name-decred-is-awesome.html), aut. @arij.
* Nowe tłumaczenia Decred Journal - w języku arabskim przez @arij, w języku chińskim przez @guang i innych, w języku rosyjskim przez @DZ, w języku hiszpańskim przez @elian, w języku wietnamskim przez @duyenemdo. Trudno wymienić je wszystkie tutaj (miły problem!), zobaczyć wszystkie tłumaczenia na stronach [indeku](https://xaur.github.io/decred-news/) i [lustra](https://xaur.github.io/decred-news/mirrors.html).
* Przypomnienie: istnieje wysiłek, aby zbudować [indeks](https://github.com/artikozel/decred-translations/blob/master/article_index.md) wszystkich tłumaczeń i zebrać [statystyki](https://github.com/artikozel/decred-translations/blob/master/effort_stats.md) czasu potrzebnego na ich wykonanie. Prosimy nadsyłać swoje.

Wideo:

* Decred Assembly: Głęboka analiza: DEX ([youtube](https://www.youtube.com/watch?v=NuBkLA8o8ds))
* Decred na Consensus 2019 ([youtube](https://www.youtube.com/watch?v=h-AfggMHVvE)) - @jy-p podaje aktualizację i stan mapy rozwoju Decred.

Audio:

* Decred in Depth - Odc. 2 Luke Powell - Politeia + dcrtime ([soundcloud](https://soundcloud.com/decredindepth/ep2-luke-powell-politeia-decred-contractor-model), [youtube](https://www.youtube.com/watch?v=W6yUVq97cd8))
* Decred in Depth - Odc. 3 Joel Monegro - Placeholder Capital Teza inwestycyjna DCR + zarządzanie ([soundcloud](https://soundcloud.com/decredindepth/joel-monegro-placeholder-capital-dcr-investment-thesis))
* Decred Distributed: Afryka z udz. Akina Sawyerr'
a ([youtube](https://www.youtube.com/watch?v=0aZfkqdLOcI))
* Podcast Hackernoon E55 - Wgląd w budowanie zdecentralizowanej infrastruktury z Jake'iem Yocom-Piatt'em z Decred  ([hackernoon.com](https://podcast.hackernoon.com/e/the-insights-of-building-decentralized-infrastructure-with-jake-yocom-piatt-of-decred/), [youtube](https://www.youtube.com/watch?v=9i1d9C7DT9Y))
* Off the Chain z Anthonym Pompliano: Jake Yocom-Piatt, kierownik projektu Decred: zarządzanie ego w krypto ([player.fm](https://player.fm/series/off-the-chain-2428336/jake-yocom-piatt-project-lead-for-decred-crypto-ego-management))
* Chain Reaction z Tomem Shaughnessy'm: współzałożyciel Decred Jake Yocom-Piatt: projekt krypto stawiający przede wszystkim na zarządzanie rzuca wyzwanie Bitcoinowi([youtube](https://www.youtube.com/watch?v=kO_11gehyls), [player.fm](https://player.fm/series/chain-reaction-2478788/decreds-co-founder-jake-yocom-piatt-governance-first-crypto-aims-to-challenge-bitcoin), [podbean.com](https://fiftyonepercent.podbean.com/e/decreds-jake-yocom-piatt-a-differentiated-cryptos-goal-of-overtaking-bitcoin))
* Inkluzywność: gość Akin Sawyerr nt. blockchaina w Afryce ([jamesfeltonkeith.com](https://www.jamesfeltonkeith.com/radioshow/episode/c184d5d5/inclusionism-guest-akin-sawyerr-on-african-blockchain-crypto-and-serial-entrepreneur-in-fintech), temat Decred zaczyna się w 38. minucie)
* Podcast Decred Russia aut. @DZ ([soundcloud](https://soundcloud.com/decred-russia), w jęz. rosyjskim)

## Dyskusje społeczności

Statystyki społeczności na dzień 1 lipca:

* Użytkownicy platformy Politeia: 189 (+14)
* Obserwujący na Twitterze: 40,479 (+17)
* Subskrybenci na Reddit: 9,505 (+46)
* Użytkownicy na Matrixie: 364 (+27)
* Użytkownicy na Slacku: 6,769 (+48)
* Użytkownicy na Discordzie: 2310 (+53), zweryfikowani z możliwością pisania postów: 246 (+20)
* Użytkownicy na Telegramie: 3,407 (-169)
* Subskrybenci na YouTube: 3,787 (+18)
* Obserwujący na Facebooku: 3,230 (+11), polubień: 2,964 (+10)
* Obserwujący na LinkedIn: 567 (+23)
* GitHub: 494 gwiazdek (+5) i 1,337 forków repozytorium dcrd (+13)

Nowinki z platform komunikacyjnych:

* Kilka pomieszczeń Matrix zostało zmodernizowanych po [pierwszym stabilnym wydaniu](https://matrix.org/blog/2019/06/11/introducing-matrix-1-0-and-the-matrix-org-foundation/) protokołu Matrix. Użytkownicy muszą (ponownie) dołączyć do nowych pomieszczeń, ale proces jest bardzo prosty i cała historia jest zachowana.
* Funkcje Hot Matrix/Riot w potoku rozwojowym to: edytowalne wiadomości, reakcje, wątki i lepsza weryfikacja urządzeń UX do szyfrowania typu end-to-end.

Wybrane posty z Reddita:

* [Post](https://www.reddit.com/r/decred/comments/c60aho/governance_would_matrixlike_channel_discussions/) z pytaniem, czy dyskusje na kanale podobnym do Matrix, zamieszczane na Reddicie, zwiększyłyby adopcję i edukację nt. projektu.
* [SONDAŻ: optymalny próg przyjęcia propozycji Politeia](https://www.reddit.com/r/decred/comments/bynidz/poll_optimal_politeia_pass_threshold/) - 57% stwierdziło, że obecny poziom jest OK, 7% stwierdziło, że mniej niż 60%, 26% opowiedziało się za podniesieniem progu zatwierdzenia.
* [SONDAŻ: zmiana nazwy z Decrediton na Declaration](https://www.reddit.com/r/decred/comments/c4ilpw/poll_rename_decrediton_to_declaration/) - ma wynik 0 na Reddit, co prawdopodobnie powinno być interpretowane jako brak poparcia.
* [Pytanie](https://www.reddit.com/r/decred/comments/c52hqd/question_is_a_hybrid_finance_governance_tool/): Czy hybrydowe narzędzie finansowo-administracyjne nazywane jest "portfelem", czy też czymś zupełnie innym?
* [SONDAŻ: zmiana nazwy z DAE na DAO?](https://www.reddit.com/r/decred/comments/c02geh/poll_rename_dae_to_dao/) - uzyskała wynik 15 punktów, a najpopularniejszy komentarz brzmi: "Popieram zmianę na DAO" z 8 punktami. Przeczytaj również ten [komentarz](https://www.reddit.com/r/decred/comments/c02geh/poll_rename_dae_to_dao/er1g4px) z notatkami na temat wsparcia z dyskusji na czacie.

Wybrane dyskusje z Twittera:

Więcej dzikich nie0do0końca-maksymalistów, ludzi, którzy uważaliby się za Bitcoinerów, ale którzy również mają zamiłowanie do Decred zostało wypatrzonych na Twitterze w tym miesiącu. Najwyraźniej więcej jest takich zakonspirowanych fanów Decred, którzy nie ośmielają się mówić o DCR, ponieważ spowodowałoby to utratę statusu w ich kręgach.

* [Temat](https://twitter.com/Ammarooni/status/1145213941146181632)  @Ammarooni o tym, jak "Bitcoin zajmuje się strukturalnymi brakami pieniędzy fiat, które nie są od razu widoczne gołym okiem, ale z czasem wyjdą na jaw. Decred zajmuje się niedociągnięciami Bitcoina, które dziś nie są powszechne, ale mogą się zamanifestować w czasie".
* @\_Checkmatey\_ rozpoczął [temat](https://twitter.com/_Checkmatey_/status/1142918632546156544) o Decred jako cyfrowym organizmie napędzanym przez ludzki hivemind ryzykującym własną skórą, a następnie [porównał](https://twitter.com/_Checkmatey_/status/1145944145141411840) jego podaż i przepływ z  tymi Bitcoina aby wreszcie rzucić [wyzwanie](https://twitter.com/_Checkmatey_/status/1145764832362319872) wszystkim Bitcoinerom: spędźcie jeden miesiąc studiując Decred i wyjdźcie z niego wierząc, że nie jest to godny numer 2 do Bitcoin.
* @CryptoBrekkie stworzył ciekawy [sondaż](https://twitter.com/CryptoBrekkie/status/1145713705415372800), który otrzymał 720 odpowiedzi. "Zauważyłem trend wśród niektórych maksymalistów, którzy ostatnio wyrazili chęć posiadania prawdziwego, solidnego konkurenta pieniężnego dla Bitcoina, rywala, który ostatecznie mógłby pomóc Bitcoinowi w podniesieniu poziomu. Zauważyłem również, że wielu maksymalistów ma słabość do [@decredproject](https://twitter.com/decredproject). Czy to może być ten konkurent?". 36% stwierdziło, że tak, 52% stwierdziło, że nie.

## Rynki

W czerwcu kurs wymiany Decred wahał się pomiędzy 24,77-37,06 USD / BTC 0,0026-0,0035. Średni dzienny kurs wynosił 28,90 USD.

22 czerwca cena Btcoina przekroczyła 10 tys. dolarów i w zaledwie parę dni wzrosła do 13670 USD na niektórych rynkach. Wydarzenie to spowodowało, że większość altów, włącznie z Decred, straciła na kursie w porównaniu z BTC.

## Ważne kwestie i wiadomości poboczne

18 czerwca Facebook opublikował [białą księgę Libry](https://libra.org/en-US/white-paper/), co zdominowało wiadomości i dyskusje na trochę dłużej niż jakikolwiek inny temat ma od jakiegoś czasu. Cytaty od @jy-p pojawiły się w wielu artykułach o Librze na wysokoprofilowych stronach (patrz aktualizacja Ditto powyżej), kwestionując dotychczasowe osiągnięcia Facebooka i to, czy zaproszenie ich do obsługi naszych transakcji finansowych jest dobrym pomysłem. Nie będziemy tu powracać do dyskusji na temat Libry, z wyjątkiem tego, że biała księga odnosi się do tego, w jaki sposób będzie ona zarządzana - poprzez stowarzyszenie, w którym walidatorzy (zatwierdzone organizacje, które zapewniają niezbędny kapitał) głosują w celu podejmowania decyzji. 21 organizacji, głównie dużych międzynarodowych koncernów, zostało [ogłoszonych](https://www.theblockcrypto.com/2019/06/14/facebooks-cryptocurrency-partners-revealed-we-obtained-the-entire-list-of-inaugural-backers/) wraz z białą księgą, z zamiarem zarejestrowania 100 przed wprowadzeniem Libry na rynek. Ciekawe będzie to, jak zachowa się rozdystrybuowana księga prowadzona przez 100 (mega)korporacji w porównaniu z księgą prowadzoną przez interesariuszy Decred i ich ~40,960 biletów.

Parity Technologies [wydało](https://www.parity.io/parity-releases-zebra-in-collaboration-with-zcash-foundation/) wersję alfa Zebry, alternatywnej implementacji węzła Zcash napisanej w Rust. [Baza kodowa](https://github.com/ZcashFoundation/zebra) została przekazana Fundacji Zcash. Początkowo Parity [ogłosiło](https://www.parity.io/parity-teams-up-with-zcash-foundation-for-parity-zcash-client/), że  planuje zbudować alternatywny węzeł w październiku 2018 roku. Zebra została zaczerpnięta [implementacji Bitcoina w Rust](https://github.com/paritytech/parity-bitcoin) aut. Parity i położy podwaliny pod przyszły most Polkadot.

Dovey Wan [ogłosiła](https://www.coindesk.com/hard-core-fund-collects-50-btc-in-china-to-support-bitcoin-developers), że "Fundusz Hard Core" zgromadził 50 BTC, które mogą być wykorzystane na opłacenie deweloperów Bitcoin, i określiła poszukiwanie zrównoważonego finansowania dla deweloperów Bitcoin największym wyzwaniem stojącym przed ekosystemem w 2019 roku. Fundusz dokonuje wpłat na rzecz zatwierdzonych współpracowników Bitcoin, gdy wysyłają comiesięczne raporty o tym, nad czym pracowali.

Kolejnym wydarzeniem finansowym dla Bitcoin były dwa projekty dotyczące ochrony prywatności - [Portfel Wasabi](https://www.wasabiwallet.io/) i [JoinMarket](https://github.com/JoinMarket-Org/joinmarket-clientserver), które otrzymały [dotacje](https://bitcointalk.org/index.php?topic=279249.msg51274844#msg51274844) po 10 BTC z [funduszu nagród](https://bitcointalk.org/index.php?topic=279249.msg2983911#msg2983911) utworzonego w 2013 r. w celu zachęcenia do pracy nad CoinJoin. Fundusz jest dwu- lub trzyosobowym funduszem multisigowym kontrolowanym przez Grega Maxwella, Theymosa i Pietera Wuille.

Fundusz rozwojowy Bitcoin Cash również [ogłosił](https://news.bitcoin.com/bitcoin-cash-development-fund-receives-massive-support/) dobre postępy w zakresie finansowania rozwoju, zebrawszy 760 BCH z docelowych 800 BCH od 900 darczyńców.

Grin próbuje [iterować](https://www.grin-forum.org/t/proposal-grin-governance-iteration/5191) w kierunku mniej scentralizowanej formy zarządzania, po uznaniu, że brak formalnych procesów zarządzania oraz potrzeba posiadania zaufanych współpracowników do zarządzania wspólnymi zasobami (funduszami z dotacji) doprowadziła do faktycznej centralizacji odpowiedzialności za projekt. Rada Grin ma stać się głównym zespołem. Wprowadzany jest proces zapytania komentarzowego, w ramach którego poszukiwane są informacje zwrotne na temat proponowanych prac rozwojowych. Pod-zespoły będą organizować się samodzielnie z własnymi liderami.

Zcash nadal zmierza ku długoterminowemu finansowaniu rozwoju poprzez część nagrody blokowej, prawdopodobnie 10%. Zooko (CEO Electric Coin Company) [stwierdził](https://finance.yahoo.com/news/zooko-wilcox-gives-zcash-community-154140125.html), że ECC potrzebuje 12 miesięcy na rozpoczęcie funkcjonowania i jeśli nie zostanie utworzona kontynuacja finansowania dla ECC na rok przed (upływem) nagrody założyciela, ECC będzie musiało rozważyć skierowanie się w stronę innych projektów, które mogą generować przychody. Zooko wyraziła również opinię, że ECC nie powinno przewodzić w podejmowaniu decyzji o sposobie funkcjonowania tego mechanizmu finansowania i że powinien on być bardziej zdecentralizowany niż obecny system. Zooko [rzucił okiem](https://twitter.com/zooko/status/1137494548148416512) na zarządzanie Decred jako część tego procesu: "W systemie głosowania z dużą ilością monet niebędących obecnie w użyciu, jak w przypadku Zcasha, spodziewam się, że dobra frekwencja wyniesie około 1%.

System crowdfundingowy społeczności Monero [finansuje](https://ccs.getmonero.org/proposals/RandomX-audit.html) 3 audyty nowego algorytmu PoW, po przeprowadzeniu [procesu](https://www.reddit.com/r/Monero/comments/bozr0z/randomx_auditor_selection/), w którym 20 uczestników kanału #monero-dev IRC głosowało za przyznaniem priorytetu audytom. Stworzono propozycję CCS, która obejmuje wszystkie 3 audyty (kosztujące odpowiednio 18 tys. dolarów, 47 tys. dolarów i 53 tys. dolarów), i udzielono pozwolenia na ich przeprowadzene wraz z tym, jak dostępna stała się wystarczająca ilość środków na sfinansowanie preferowanych audytów.

Aragon Black [opublikowało](https://blog.aragon.black/aragon-fundraising-the-return-of-the-commons/) artykuł o Aragon Fundraising, który trafi do sieci głównej za kilka miesięcy. Jest to platforma do przeprowadzenia ofert kupna zdecentralizowanych autonomicznych monet (DAICO, koncepcja początkowo [opisana](https://ethresear.ch/t/explanation-of-daicos/465) przez Vitalika Buterina). Osoby, które zainwestują w DAICO, otrzymają tokeny, które przyznają im prawa głosu i pewien stopień własności aktywów DAO (co może obejmować również prawa do własności intelektualnej).

MakerDAO przeprowadzi [głosowanie](https://blog.makerdao.com/multi-collateral-dai-collateral-types/) w celu określenia kolejności, w jakiej 7 wstępnie wybranych aktywów zostanie zaproponowanych do przeglądu i ratyfikacji w ramach wielostronnej aktualizacji DAI.

Arthur Breitman, założyciel Tezos, opublikował [wpis na blogu](https://medium.com/@arthurb/potencjalny-design-for-a-simple-and-evolvable-on-chain-treasury-77cfe2176423) opisujący projekt "prostego i elastycznego skarbca sieciowego". Jako punkt wyjścia proponuje on, aby fundusze były gromadzone w ramach 3-5 kontraktu multisig, w którym podpisy są kontrolowane przez renomowane strony. Stamtąd skarbiec mógłby przekształcić się w system z wieloma uczestnikami, w którym składane byłyby propozycje on-chain. Brzmi znajomo.

Wystąpiły pewne tarcia między grupami programistów pracującymi nad oprogramowaniem Tezos. Zespół OCamlPro przedstawił propozycję rozwiązania problemu bezpieczeństwa i nagrodzenia się ze środków z tytułu inflacji w czasie, gdy inne zespoły programistów zgodziły się czekać i przedstawić swoją propozycję w późniejszym terminie. Wcześniejsze złożenie [propozycji](https://www.reddit.com/r/tezos/comments/by5xy8/proposal_for_amendment_brest_a/) przez OCamlPro  oznacza, że piekarze będą prawdopodobnie głosować za jej odrzuceniem, a tym samym potrwa to dłużej, zanim zostanie złożona "prawdziwa" propozycja. Po złożeniu raportu o błędzie i nieotrzymaniu żadnego uznania OCamlPro [poczuli się](https://www.reddit.com/r/tezos/comments/byqc9i/ocamlpro_what_is_the_real_motivation_behind/) wykluczeni przez inne zespoły. Następnie, Tezos commons opublikował [artykuł](https://medium.com/tezoscommons/a-cautionary-tale-ocamlpro-65d692af09f8), który rzekomo odkrywa szczegóły planu OCamlPro dotyczącego rozwidlenia sieci Tezos i przejęcia części społeczności Tezos oraz jego kapitalizacji rynkowej spekulując przy tym, że zespół OCamlPro działa na rzecz destabilizacji społeczności Tezos przed tym posunięciem.

Anonimowy użytkownik podający się za obecnego lub byłego pracownika Chainalysis wziął udział w AMA na r/Bitcoin, następnie usuniętym, ale zarchiwizowanym [tutaj](https://www.reddit.com/r/Bitcoin/comments/c4so58/i_am_a_current_or_former_employee_of_chainalysis/) (dzięki [u/Fiach_Dubh](https://www.reddit.com/r/Bitcoin/comments/c4so58/i_am_a_current_or_former_employee_of_chainalysis/eryukx6)). Odpowiedzi sugerowały, że techniki ochrony prywatności Bitcoin, takie jak portfel CoinJoin i Wasabi, a także wszystkie monety z elementami ochrony prywatności, były znienawidzone przez Chainalysis i nie rokowały dobrze dla sądowej i śledczej analizy blockchaina.

Skoro o CoinJoin mowa, społeczność skupiona wokół ceniącego prywatność portfela Wasabi [wykonała](https://www.coindesk.com/bitcoin-users-perform-what-might-be-the-largest-coinjoin-ever) 100-osobową transakcję CoinJoin, która jak dotąd może być największą. Im więcej transakcji w CoinJoin, tym więcej prywatności każdy otrzymuje, ale koordynowanie tak wielu ludzi jest nie lada wyzwaniem.

FATF [sfinalizowało](https://www.coindesk.com/fatf-crypto-travel-rule) swoje zalecenia dotyczące obsługi krypto. Zgodnie z nowymi standardami, firmy takie jak dostawcy usług w zakresie wymiany informacji i portfela muszą uzyskać i przechowywać informacje w celu identyfikacji zarówno nadawcy, jak i odbiorcy, oraz wymieniać te informacje między sobą, podobnie jak robią to banki ("trasa podróży"). Państwa członkowskie mają 12 miesięcy na przyjęcie wytycznych, które zostaną poddane przeglądowi w czerwcu 2020 r. Zalecenia nie są wiążące, ale kraje, które nie zastosują się do zasad, mogą zostać wpisane na czarną listę.

Niektórzy eksperci [ostrzegli](https://www.coindesk.com/beyond-kyc-global-regulators-appear-set-to-adopt-tough-new-rules-for-crypto-exchanges) FATF, że nowy standard "może mieć niezamierzone skutki w postaci "zachęcania do przekazywania P2P za pośrednictwem portfeli niepowierniczych..."". (co brzmi uderzająco znajomo z zamierzonym sposobem korzystania z krypto). Kolejny cytat z [CoinDesk](https://www.coindesk.com/regulators-begin-to-debate-cryptocurrency-legislation-ahead-of-g20-summit) na temat tej możliwej dynamiki: "powszechną obawą jest to, że nowe regulacje mogą wypchnąć społeczeństwo poza kontrolowane platformy".

W ostatnim czasie ciągnie się fala geofencingów: Bittrex [powstrzymał](https://bittrex.zendesk.com/hc/en-us/articles/360028996652) klientów amerykańskich przed obrotem 32 aktywami (DCR bez zmian) a Gate.io [ograniczyło](https://www.gate.io/article/16909) 19 aktywów dla klientów ze Stanów Zjednoczonych (w tym DCR).

Binance [wstrzymuje](https://techcrunch.com/2019/06/14/binance-begins-to-restrict-us-customers/) świadczenie usług dla klientów amerykańskich za pośrednictwem ich globalnej strony binance.com, jednocześnie [ogłaszając](https://www.binance.com/en/blog/346119082624540672/Binance-Announces-Partnership-with-BAM-to-Launch-US-Exchange) uruchomienie oddzielnej usługę opartej dla amerykańskiego rynku.

Bancor zamierza [zablokować dostęp](https://support.bancor.network/hc/en-us/articles/360029588431-US-Service-Restriction) dla użytkowników z USA do swojej aplikacji internetowej do wymiany aktywów.

Rząd indyjski [rozważa](https://www.theblockcrypto.com/tiny/indias-draft-bill-proposes-a-10-year-jail-sentence-for-using-cryptocurrencies/) projekt ustawy, która kryminalizowałaby tych, którzy wydobywają, przetrzymują lub dokonują transakcji za pomocą walut kryptograficznychkryptowalut, z surowymi karami do 10 lat więzienia i grzywnami w wysokości 3-krotności zysków sprawcy.

Wygląda na to, że giełda Bitsane, rozsławiona przez CNBC w teletutorialu na temat sposobu zakupu XRP, [dokonała exit scamu](https://thenextweb.com/hardfork/2019/06/28/cnbc-shilled-cryptocurrency-exchange-bitsane-pulls-exit-scam-on-246k-users/) i zniknęła wraz z kryptoaktywami wszystkich nieszczęsnych użytkowników, którzy przechowywali swoje krypto na ich giełdzie.

[Podatność na atak](https://www.yubico.com/support/security-advisories/ysa-2019-02/) w niektórych produktach YubiKey pozwoliła napastnikowi odgadnąć klucze prywatne.

Rozszerzenia przeglądarek blokujące reklamy, takie jak uBlock, zostaną wkrótce objęte nowymi [ograniczeniami](https://www.theregister.co.uk/2019/06/13/google_chrome_ad_blockers/) Google Chrome. To posunięcie było kontrowersyjne, częściowo dlatego, że deklarowany zamiar ochrony użytkowników przed złośliwymi rozszerzeniami również ogranicza ich zdolność do blokowania niechcianych i niebezpiecznych treści internetowych.

Rośnie tempo ataków [zamiany kart SIM rośnie](https://www.tonysheng.com/sim-swap); [doedukujcie się w tym temacie](https://medium.com/mycrypto/what-to-do-when-sim-swapping-happens-to-you-1367f296ef4d) i róbcie to, co jest konieczne, aby chronić swoje konta.

Zespół Komodo [wykorzystał](https://cryptobriefing.com/komodo-developers-hacked-users/) błąd celem przechwycenia KMD i BTC o wartości 13 milionów dolarów od użytkowników podczas prewencyjnego ataku typu "white hat". Wersja Komodo portfela Agama była wzięta za cel hakera, który spędził miesiące wnosząc do projektu użyteczny wkład przed wstawieniem zależności, która wykrada ziarna portfela. Złośliwy pakiet został wykryty przez zespół bezpieczeństwa npm, który [napisał](https://blog.npmjs.org/post/185397814280/plot-to-steal-cryptocurrency-foiled-by-the-npm), że ten atak staje się coraz bardziej popularny: opublikuj "użyteczny" pakiet, poczekaj aż zostanie użyty przez cel, a następnie zaktualizuj go tak, aby zawierał złośliwy ładunek. Po otrzymaniu powiadomienia od npm, zespół Komodo postanowił użyć tego samego exploita i zdołał zabezpieczyć większość zagrożonych funduszy, zanim haker mógł je ukraść. Dotknięci użytkownicy mogą przesłać formularz Google, aby odebrać swoje fundusze. Nie identyczne, ale związane z tym incydenty miały miejsce wcześniej, gdy pakiet npm został [zainfekowany](https://thehackernews.com/2018/11/nodejs-event-stream-module.html) w celu kradzieży monet z portfeli Copay, który z nich korzystał, oraz gdy łowca nagród dodał inflacyjny [błąd konsensusu](https://medium.com/@bitcoinprivate/official-statement-on-coinmetrics-report-6f1cef176c05) do Bitcoin Private. Te incydenty pokazują, że bardzo ważne jest dokładne sprawdzanie i weryfikowanie współpracowników oraz audytowanie nie tylko własnego kodu, ale także wszystkich zależności i wszystkich ich aktualizacji (co nie jest małym zadaniem).

Kto by pomyślał, że 27-letni _edytor tekstu_ nadal może mieć [lukę](https://www.theregister.co.uk/2019/06/12/vim_remote_command_execution_flaw/) arbitralnego wykonania kodu? Jest to przypomnienie, że poprawność jest trudna i dlaczego potrzeba tak wiele pracy, aby zbudować i przetestować solidne oprogramowanie.

## O tym wydaniu

To 15. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze opinie i komentarze są mile widziane na portalach Reddit, [GitHub](https://github.com/xaur/decred-news/issues) oraz [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Zasługi (kolejność alfabetyczna):

* redakcja treści: bee, cryptoleslie, degeri, Dustorf, kozel, lukebp, richardred, s\_ben
* recenzje i komentarze: jholdstock, jz, Haon, matheusd, raedah
* ilustracja tytułowa: saender
