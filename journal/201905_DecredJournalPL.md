# Decred Journal – May 2019

![abstract art](../img/journal-201905-384.jpg "Tap Into the Source by @saender. Movements and hierarchy of cubes on the volumetric grid remind of programming or the logic of it. Cubes flow upwards to where the light shines (the source).")

Najważniejsze wydarzenia z maja:

* DCP4 zostało aktywowane. Sieć główna Decred jest teraz gotowa na Lightning Network.
* Release candidate pierwszego portfela dla iOS wszedł z fazę publicznych testów.
* Pierwsza faza 3 propozycji finansowanych przez Skarbiec (Ditto, Research i Bug Bounty) dobiega końca, ich podsumowania są publikowane, a propozycje dalszego finansowania zostały już otwarte dla propozycji Ditto i programu badawczego. W sumie w maju złożono 6 wniosków, a 4 wnioski zostały poddane pod głosowanie na początku czerwca.
* Decred Assembly i podcast Decred in Depth zakończyły fazę wczesnej produkcji i pojawiły się pierwsze odcinki. Decred Distributed gości @elian, który w maju udał się na 3 eventy w 7 dni w Kolumbii i Urugwaju, i dostarczył szczegółowe opisy swoich doświadczeń z każdego z nich.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Wprowadzono poprawki błędów, zwiększono zakres testów i ulepszono infrastrukturę testową.

Rozpoczęto prace nad [portem](https://github.com/decred/dcrd/pulls?q=is%3Apr+updated%3A2019-05-01..2019-05-31+port) kilku zmianami z repozytorium btcd w celu zredukowania sprzężenia i podzielenia blockmanagera oraz rpcserver do swoich własnych paczek.

Kolejnym aktywnym obszarem był [kod górniczy](https://github.com/decred/dcrd/pulls?q=is%3Apr+updated%3A2019-05-01..2019-05-31+mining), który przechodzi serię ulepszeń kodu i optymalizacji wydajności, np. w celu [usunięcia getblocktemplate](https://github.com/decred/dcrd/pull/1736) oraz [wymagania](https://github.com/decred/dcrd/pull/1739) poprawnego adresu szablonu.

Główną oczekującą zmianą kodu górniczego, która zasługuje na specjalną uwagę, jest [kapitalna restrukturyzacja](https://github.com/decred/dcrd/pull/1748) generatora szablonów tła (funkcja, którą górnicy wywołują, aby otrzymywać szablony z których tworzą bloki). Obecnie, górnicy, którzy nie są zaznajomieni z zawiłościami głosowania w Decred, będą okazjonalnie produkować ważne bloki z minimum 3 głosami PoS, z możliwych 5, co jest niekorzystne dla górników PoW, którzy otrzymują obniżoną nagrodę za stworzenie bloków z mniejszą liczbą głosów. Jest to również niepożądane dla głosujących PoS, którzy mogą nie otrzymać nagrody za oddanie głosu, mimo tego, że głosowali, z powodu opóźnienia w propagacji. Aby rozwiązać ten problem, generator szablonów tła został zaktualizowany w celu dodania wsparcia dla inteligentnej propagacji głosów, jak również wielu innych funkcji, takich jak lepszej obsługi reorganizacji łańcucha do bloków alternatywnych, subskrypcji zapewniającej górnikom strumień aktualizacji szablonów oraz uwzględnienie stanu synchronizacji jako części określania, czy łańcuch jest aktualny. Należy zauważyć, że praca ta jedynie implementuje infrastrukturę i nie eksponuje jeszcze tej funkcjonalności w produkcji.

[dcrwallet](https://github.com/decred/dcrwallet): Poprawiono błędy, poprawiono [obsługę błędów](https://github.com/decred/dcrwallet/pull/1453), uproszczono [kod równoległy](https://github.com/decred/dcrwallet/pull/1451) i zwiększono równoczesne korzystanie z odblokowanego portfela. Rozpoczęto prace nad funkcją [CleanOutAccount](https://github.com/decred/dcrwallet/pull/1419), która jest podobna do funkcji SweepAccount, ale pozwala na wiele transakcji.

[Decrediton](https://github.com/decred/decrediton): Prace nad [responsywnym designem](https://github.com/decred/decrediton/issues/1820) kontynuowane są w od niedawna responsywnym widoku [Transakcja/Historia](https://github.com/decred/decrediton/pull/2124). Trwają prace nad wstępną integracją [portfela LN](https://github.com/decred/decrediton/pull/2107).

[Politeia](https://github.com/decred/politeia): Zmiany na front endzie obejmują ulepszony widok listy propozycji, ciągłe ładowanie propozycji podczas przewijania oraz brak konieczności przekierowywania po zakończeniu sesji - teraz pojawi się okno logowania. Backend otrzymał poprawki w wydajności oraz poprawki błędów, zmiany w bazie danych użytkowników (nieużywane dane użytkownika są teraz zaszyfrowane) oraz zaktualizowany punkt końcowy API, który umożliwia osobom niebędącym adminami wyszukiwanie identyfikatora użytkownika/nazwy użytkownika za pomocą klucza publicznego. Wyszukiwania te pozwolą, aby dane o komentarzach i głosach użytkowników były zorganizowane na podstawie konta użytkownika, a nie przez klucz publiczny.

System zarządzania wykonawcami (CMS) nadal otrzymuje [ciągły strumień](https://github.com/decred/politeia/pulls?q=is%3Apr+updated%3A2019-05-01..2019-05-31+cms) ulepszeń i poprawek.

[dcrlnd](https://github.com/decred/dcrlnd): [Trwają prace](https://github.com/decred/dcrlnd/pulls?q=is%3Apr+updated%3A2019-05-01..2019-05-31) nad przygotowaniem LN Decred do sieci głównej, wraz z poprawkami błędów, usprawnieniami testów integracyjnych, zwiększonym zasięgiem testów i usuwaniem nieużywanego kodu.

Rozpoczęto prace nad [redukcją sprzężenia](https://github.com/decred/dcrlnd/pull/29) z dcrwalletem oraz nad [portem](https://github.com/decred/dcrlnd/issues/12) związanych z Dockerem plików lnd do dcrlnd, aby umożliwić łatwiejsze nad nimi majstrowanie i rozwój przez społeczność. Napisany został [szybki przedownik](https://github.com/decred/dcrlnd/pull/8) po temacie dla tych, którzy chcą szybciej działać w sprawie LN. Rozpoczęto również prace nad przeniesieniem wielu zmian [z głównego repozytorium](https://github.com/decred/dcrlnd/pull/36) dokonanych w [lnd](https://github.com/lightningnetwork/lnd) od momentu, gdy dcrlnd rozgałęził się, aby rozpocząć początkowy port.

Repozytorium dcrlnd zostało dodane do programu [Bug Bounty Program](https://bounty.decred.org/) na zasadzie eksperymentu, z pewnymi [zastrzeżeniami](https://github.com/decred/dcrlnd#security).

[dcrandroid](https://github.com/decred/dcrandroid): Drobne poprawki błędów i optymalizacje interfejsu użytkownika, a także nowo dodana [funkcja](https://github.com/decred/dcrandroid/pull/371) wysyłania i szacowania. Kod został [zaktualizowany](https://github.com/decred/dcrandroid/pull/356), aby był zgodny z najnowszym [dcrlibwallet](https://github.com/raedahgroup/dcrlibwallet) - współdzielonym komponentem ponownie wykorzystywanym przez dcrandroid, dcrios i [godcr](https://github.com/raedahgroup/godcr).

[dcrios](https://github.com/raedahgroup/dcrios): Release Candidate 1 portfela dla systemu operacyjnego iOS Wallet jest [gotowy](https://www.reddit.com/r/decred/comments/bxje6l/decred_wallet_for_ios_release_client_1/) do szerszych publicznych testów. Wysiłki na rzecz rozwoju nabrały tempa w ramach przygotowań do oficjalnego wydania. Naprawiono błędy zgłoszone przez użytkowników aplikacji testowej, wprowadzono ulepszenia w zakresie interfejsu użytkownika oraz przeprowadzono dużą refaktoryzację w celu [oczyszczenia repozytorium](https://github.com/raedahgroup/dcrios/pull/391) i poprawy zasięgu testów. Wydanie w Apple Store jest tuż tuż!

[dcrdata](https://github.com/decred/dcrdata): Na wersję alfa strony dodana została zakładka ["rynki""](https://alpha.dcrdata.org/market), zawierająca najistotniejsze informacje rynkowe, takie jak: Cena i wolumen USD i BTC z rynków Decred, indeksy cen BTC/USD, wykresy głębokości księgi zamówień, wolumenu i historii rynku.

[docs](https://github.com/decred/dcrdocs): Dodano nową stronę ["zabezpieczenia"](https://docs.decred.org/advanced/general-security/), która zawiera cennej wiedzy na temat bezpiecznego przetwarzania danych, w tym konfiguracji systemu i OPSEC. Strona ["szczegóły transakcji"](https://docs.decred.org/advanced/transaction-details/) została zaktualizowana w celu uwzględnienia większej ilości informacji na temat konkretnych dla Decred typów transakcji, jak również i szczegółowej [przykładowej transakcji](https://github.com/decred/dcrdocs/pull/937). Strona ["archiwum głosowań konsensusu"](https://docs.decred.org/governance/consensus-rule-voting/consensus-vote-archive/) zawiera teraz więcej danych oraz ulepszony ich przepływ.

[decred.org](https://github.com/decred/dcrweb): [Zaktualizowano](https://github.com/decred/dcrweb/pull/662) stronę [mapy rozwoju](https://decred.org/roadmap/), mniej istotne treści oraz wprowadzono poprawki interfesju uzytkownika.

Pozostałe:

* dcrstakepool (oprogramowanie VSP) zostało poddane [redesignowi](https://github.com/decred/dcrstakepool/pull/339).
* dcrd z powodzeniem [synchronizuje się](https://twitter.com/marco_peereboom/status/1128763544118362112) na procesorach z architekturą RISC-V QEMU. [RISC-V](https://en.wikipedia.org/wiki/RISC-V) jest nadzieją na mniej okropną architekturę jednostek CPU.

Statystyki aktywności deweloperskiej na maj: 88 aktywnych PR-ów, 272 master commity, 52 tys. dodanych 57 tys. usuniętych linijek kodu spośród 15 repozytoriów. Wkład pochodził od 2-7 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami rezpotyrowiów Decred na GitHubie: duyenemdo ([dcrandroid](https://github.com/decred/dcrandroid/commits?author=duyenemdo)), njirap ([dcrdata](https://github.com/decred/dcrdata/commits?author=njirap)), Nelson Dornelas Jr ([politeiagui](https://github.com/decred/politeiagui/commits?author=dornelasN)) oraz Youssef Boukenken ([dcrtime](https://github.com/decred/dcrtime/commits?author=sefbkn)).

## Zarządzanie

W maju [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 15 616 DCR oraz wydał 8456 DCR. Używając majowych dziennych średnich kursów DCR/USD w wys. 27,71 USD, stanowi to 433 tys. USD wpływów i 234 tys. USD wydatków z budżetu. Ponieważ płatności te zostały dokonane za pracę wykonaną w kwietniu, warto rozważyć je w kontekście kwietniowych średnich dziennych kursów w wys. 24,22 USD - co odpowiednio przelicza się na 378 tys. USD we wpływach oraz 205 tys. USD w wydatkach ze Skarbca. Na 1. czerwca, saldo Skarbca wynosi 613 840 DCR (17,3 miliona dolarów po kursie 28,19 USD/DCR).

Status propozycji na dzień 1. czerwca:

Złożono 6 nowych propozycji:

* [Zmiana zasad konsensusu odn. commitmentów nagłówka bloku](https://proposals.decred.org/proposals/0a1ff846ec271184ea4e3a921a3ccd8d478f69948b984445ee1852f272d54c58) aut. @davecgh, propozycja zezwalająca na pracę nad [DCP](https://github.com/decred/dcps) i głosowaniem on-chain nad zmianą zasad konsensusu. Zmiana ta pozwoliłaby na zbliżenie bezpieczeństwa klientów SPV do poziomu w pełni zatwierdzających węzłów. Propozycja przewiduje koszt 20 000 USD na przygotowanie oprogramowania i DCP, do pokrycia z budżetu przeznaczonego na rozwój.

* [Ditto Communications Proposal for Decred: Phase 2](https://proposals.decred.org/proposals/52ea110ea061c72d3b31ed2f5635720b212ce5e3eaddf868d60f53a3d18b8c04) aut. @lizbagot, propozycja utrzymania usług Ditto na poziomie 25K USD/miesiąc, płatnych w DCR, przez kolejne 6 miesięcy. Propozycja zawiera podsumowanie z ostatnich 6 miesięcy oraz szczegółowe informacje na temat pięciostopniowego podejścia do pracy na najbliższe 6 miesięcy.

* [Decred Open Source Research proposal: Phase 2](https://proposals.decred.org/proposals/67de0e901143400ae2f247391c4d5028719ffea8308fbc5854745ad859fb993f) aut. @richard-red, propozycja dalszego finansowania programu badawczego kwotą 20 000 USD, szacowaną na 6 miesięcy. Propozycja zawiera raport z pierwszych 6-miesięcznych działań oraz opis różnic w podejściu do dalszych działań. Wniosek zaprasza również do zgłaszania uwag na temat projektów badawczych.

* [Dokument specyfikacyjnych zdecentralizowanej giełdy wymian](https://proposals.decred.org/proposals/a4f2a91c8589b2e5a955798d6c0f4f77f2eec13b62063c5f4102c21913dcaf32) aut. @jy-p, propozycja posunięcia naprzód ws. DEX poprzez stworzenie "pełnej specyfikacji typu RFC" wchodzących w nią procesów. Specyfikacja zostanie sporzadzona przez Company 0, we współpracy z @chappjc, @buck54321 i @jholdstock, a jej koszt wyniesie do 20 000 USD.

* [Motywowanie ewangelistów rozwoju biznesowego sposród ekosystemu Decred](https://proposals.decred.org/proposals/cb446a469987d6603d93f442ef0d4e45bacbea47a72b5ce89f9c3cac3868d627) aut. @betterfuture, propozycja powołania zespołu ds. rozwoju biznesu "Decred Evangelists", który organizowałby wspólne działania rozwojowe z organizacjami partnerskimi i otrzymywałby wynagrodzenie w postaci procentu każdego DCR wniesionego przez tych partnerów do Skarbca. Propozycja została zredagowana przez @betterfuture 31 maja, aby powiedzieć, że zostanie porzucona i ponownie złożona jako dwie oddzielne propozycje, w oparciu o informacje zwrotne otrzymane od społeczności.

* [Podróż ku przyszłości pracy - opowiadanie historii DCR przez platformę Politeia](https://proposals.decred.org/proposals/b9f342a0f917abb7a2ab25d5ed0aca63c06fe6dcc9d09565a9cde3b6fe7e6737) aut. @jer979, propozycja napisania artykułu o Politei i podróży autora w celu złożenia propozycji. Propozycja ta początkowo wydawała się mieć dobre poparcie, ale po [komentarzach](https://proposals.decred.org/proposals/b9f342a0f917abb7a2ab25d5ed0aca63c06fe6dcc9d09565a9cde3b6fe7e6737/comments/29) o przesłych konszachtach @jer979 z IOTA straciła część tego poparcia i została ostatecznie odrzucona z aprobatą na poziomie 48,6% (i udziałem wyborców na poziomie 44%, drugim co do wielkości udziałem w historii Politei).

  Choć propozycja została odrzucona, @jer979 mimo to [opublikował](https://www.neverstopmarketing.com/a-tale-of-two-daos-and-the-rise-of-contributor-experience/) relację swojej podróży na swojej stronie internetowej. W artykule argumentował, że "doświadczenia wykonawcy" (ang. *contributor experience* - CX) są ważne i porównał doświadczenia związane ze składaniem propozycji DAOstack i Decred, przedstawiając kilka punktów spornych. W następstwie [wymiany](https://twitter.com/lukebp_/status/1131195413925925638144) na Twitterze, @lukebp zebrał komentarze w [kwestii](https://github.com/decred/politeiagui/issues/1221) na GitHub.

1 dodatkowa propozycja zakończyła głosowanie i została przyjęta:

* [Decentralizacja wydatków ze Skarbca](https://proposals.decred.org/proposals/c96290a2478d0a1916284438ea2c59a1215fe768a87648d04d45f6b7ecb82c3f) aut. @moo31337, autor zaproponował metodę decentralizacji wydatków ze Skarbca z comiesięcznym głosowaniem na łańcuchu w celu zatwierdzenia płatności na rzecz kontrahentów. Została ona zatwierdzona przy 97,5% głosów na "tak" i udziale 22,5% biletów.

Pierwsza poprawka do konstytucji została [wprowadzona](https://docs.decred.org/governance/decred-constitution/) na stronie docs.decred.org.

15 maja @degeri opublikował [aktualizację statusu](https://bounty.decred.org/) programu nagród, informując, że na tamten dzień rozpatrzonych zostało 49 zgłoszeń, a 7 z nich kwalifikowało się do wypłaty.

Bardziej dogłębny opis tych propozycji i związanych z nimi zmian znajduje się w [wydaniu 15](https://github.com/RichardRed0x/politeia-digest/blob/master/issue-015.md) i [wydaniu 16](https://github.com/RichardRed0x/politeia-digest/blob/master/issue-016.md) Politeia Digest, które zostały opublikowane w maju.

[@pi_crumbs](https://twitter.com/pi_crumbs) kontynuuje tweetowanie, gdy publikowane lub redagowane są nowe wnioski, lub gdy rozpoczyna się głosowanie nad nimi.

## Sieć

Hashrate: majowy hashrate na początku miesiąca wyniósł ~524 Ph/s a zamknął miesiąc w ok. ~574 Ph/s, zaliczając niż w ok. 364 Ph/s oraz szczyt w wys. 626 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 1 czerwca wyglądała następująco: Poolin 20%, lab.antpool.com 18%, BTC.com 8,7%, F2Pool 7,7%, UUPool 7,7%, Luxor 2%, BeePool 0,86%, CoinMine 0.28%, suprnova 0,02% oraz pozostałe 35.4%, za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu z okresu 30 dni wynosiła 116 DCR (-1.2) za danymi z dcrstats.com. TCena wahała się między 109,7-124,7 DCR. Zablokowana kwota wynosiła 4,68-4,83 mln DCR, co odpowiadało 47,60-49,17% dostępnej podaży, za danymi z [dcr.farm](https://charts.dcr.farm/d/000000003/proof-of-stake).

Węzły: na dzień 2. czerwca istniało 270 publicznych węzłów. W owym snapshocie, 168 węzłów stanowiły węzły IPv4 z następującą dystrybucją pośród kontynentów: Europa 53%, Ameryka Północna 39%, Azja 7%. Czołowe kraje: USA 31,6%, Niemcy 14%, Francja 10%, Kanada 7,8%, Wielka Brytania 5,4%, Holandia 5,4%. Dzięki za snapshot należą się @chappjc.

Koleżnym uzytecznym źródłem statystyk węzłów jest dcr.farm. Na przestrzeni maja pokazuje ono dużą wariację w ilości węzłów wersji v1.4.0 (103-237), lecz posiada świetny [wykres](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1556582400000&to=1559390400000) historii wersji węzłów, który pokazuje, że sieć jest aktualnie oparta głównie na wersjach v1.4.0+.

Źródło, którego używaliśmy poprzednio w celach raportowania odn. węzłów (dcred.eu) zostało zamknięte. Jesteśmy wdzięczni za wszystkie podane informacje, z których skorzystaliśmy przy tworzeniu Journala; jest nam niezmiernie przykro żegnać się z tym portalem. Pomysł dodania podobnej funkcjonalności do dcrdata omawiany jest  [tutaj](https://github.com/decred/dcrdata/issues/1214).

Wkrótce po aktywacji nowych zasad konsensusu miała miejsce [transakcja](https://www.reddit.com/r/decred/comments/bnep6p/if_you_were_running_decrediton_at_13_or_earlier/) właśnie z nich korzystająca. Węzły, które nie rozpoznały jej jako poprawnej zostały odcięte od sieci i utknęły na bloku 342 913. Zauważyliśmy przyrost ludzi odwiedzających kanał #support w ciągu misiąca wraz z tym, jak wiele z ich portfeli przestawało się synchronizować, jednakże nie zaobserwowano żadnych awarii na poziomie sieci.

## Wydobycie

Mining pool ViaBTC [ogłosił](https://pool.viabtc.com/announcements/85) wsparcie dla wydobycia Decred.

## Integracje

Giełda HitBTC [dodała](https://twitter.com/hitbtc/status/1128226645280788480) pary DCR/BTC, DCR/ETH oraz DCR/USDT.

[Nomiddleman Crypto](https://nomiddlemancrypto.io/) [dodało](https://www.reddit.com/r/decred/comments/buhl35/decred_woocommerce_payment_gateway_open) wsparcie dla Decred w swojej wtyczce WooCommerce, która umożliwia płatności krypto wprost do portfeli sprzedawców bez wykorzystywania trzecich stron. Kod źródłowy dostępny jest na  [GitHubie](https://github.com/nomiddleman/nomiddleman-woocommerce).

[Ownbit](https://twitter.com/bitbillwallet/status/1126659323893968896) (poprzednio BitBill) dodało wsparcie dla DCR w swoim cold wallecie.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Adopcja

[Trippki.com](https://trippki.com/) [ogłosiło](https://twitter.com/Trippki_/status/1125131845673410561) wsparcie dla DCR w swojej usłudze rezerwacji hoteli.

[ADHOC](https://adhoc.zone/), a company that focuses on ethical and privacy-respecting hardware and software [announced](https://twitter.com/adhoc_zone/status/1126653081259839488) that they accept DCR as a payment method. As of writing, ADHOC sells refurbished Samsung Galaxy S2 and S3 with software for private communications and Replicant OS (fully free Android distribution that once [featured](https://www.fsf.org/blogs/community/replicant-developers-find-and-close-samsung-galaxy-backdoor) on fsf.org for finding a backdoor in a Samsung phone), Librebooted ThinkPad X220 with Tails, and a ebook reader. The products are mirrored on OpenBazaar [store](https://openbazaar.com/store/QmTQNzpvq1Lgx6NvXhnoiWirLV1oQbF9LJZwMENKoPYVon).

[Cryptwerk.com](https://cryptwerk.com/) directory collected a [list of businesses](https://www.reddit.com/r/decred/comments/bp035s/decred_accepted_here_the_list_of_businesses_where/) accepting DCR.

[ADHOC](https://adhoc.zone/), firma, która koncentruje się na etycznym i szanującym prywatność sprzęcie i oprogramowaniu [zapowiedziała](https://twitter.com/adhoc_zone/status/1126653081259839488_zone/status/1126653081259839488), że przyjmuje DCR jako metodę płatności. W trakcie pisania ADHOC sprzedaje odnowione Samsungi Galaxy S2 i S3 z oprogramowaniem do prywatnej komunikacji i Replicant OS (w pełni darmową dystrybucją Androida, która [znalazła się](https://www.fsf.org/blogs/community/replicant-developers-find-and-close-samsung-galaxy-backdoor) na fsf.org za znalezienie backdoora w telefonie Samsung), ThinkPad X220 z Tails i firmwarem Libreboot i czytnik e-booków. Produkty te można również znaleźć w [sklepie](https://openbazaar.com/store/QmTQNzpvq1Lgx6NvXhnoiWirLV1oQbF9LJZwMENKoPYVon) OpenBazaar.

Katalog [Cryptwerk.com](https://cryptwerk.com/) zebrał [listę firm](https://www.reddit.com/r/decred/comments/bp035s/decred_accepted_here_the_list_of_businesses_where/) akceptujących DCR.

## Nawiązywanie kontaktów

W maju Decred miał mnóstwo pracy przy kładzeniu podwalin pod bardziej zdecentralizowany charakter swoich działań. Duża część prac w maju skupiła się na Blockchain Week w Nowym Jorku i okolicach, gdzie około piętnastu członków społeczności zebrało się razem z większą grupą giełd wymian, górników, partnerów instytucjonalnych i nie tylko. Została uruchomiona grupa Telegram [Decred Africa](https://t.me/DecredAfrica) i koordynowała prezentację na Blockchain Nigeria w Lagos 24 maja. W Nowym Jorku, różni członkowie społeczności uczestniczyli w konferencji Magical Crypto w dniach 10-11 maja, a następnie w Consensus przez kolejne trzy dni. W ramach konferencji Consensus, @jy-p przedstawił zaktualizowane informacje na temat finansowania i mapy rozwoju Decred jako część panelu Changelogs. Dodatkowo, @jy-p przemawiał później tego dnia na pierwszej w historii konferencji Ditto PR & The Block, Atomic Swap. @jy-p był na panelu z przedstawicielami Beam, Dash i Orbs, na którym dyskutowano o decentralizacji i zarządzaniu. Decred koordynował kolację z członkami społeczności azjatyckiej i sformułował strategię penetracji rynku azjatyckiego, stawiając Chiny na pierwszym miejscu w najbliższym czasie. @Dominic i @changhugo planują organizację i promocję spotkania w Pekinie w najbliższej przyszłości, a Decred pracuje nad planem zorganizowania wydarzenia w Singapurze, potencjalnie we wrześniu.

@anshawblack udał się do Nowego Jorku na Blockchain Weeki nagrał podcasty z @jz, @MustStopMurad, Joelem Monegro, @lukebp, @jholdstock i Permabull Nino. Pierwszy podcast z @jz został [wydany](https://www.youtube.com/watch?v=rcEJuN7zh2M), z kolejnymi co dwa tygodnie.

@Dustorf wydał pierwszą część Decred Assembly, segment zatytułowany Decred Distributed, który przygląda się miejscom na całym świecie i rozmawia z lokalnymi organizatorami społeczności, aby zrozumieć, co Decred robi w tych obszarach. Gościem pierwszego [wydania](https://www.youtube.com/watch?v=N7GYD8zwOe8=N7GYD8zwOe8) był @elian, który przewodzi wysiłkom w Meksyku i wykonuje masę wspaniałej pracy w Ameryce Łacińskiej. Na początku czerwca zostaną opublikowane dodatkowe segmenty, w tym dogłębna dyskusja z @jy-p na temat propozycji DEX.

Majowe osiągnięcia Ditto:

* Ditto i The Block byli gospodarzami Atomic Swap, wydarzenia wyłącznie na zaproszenie podczas Blockchain Week w Nowym Jorku, w którym wzięło udział 150 osób wpływowych w sferze krypto, mediów, inwestorów i entuzjastów, a które sponsorowane było przez Decred. The Block opublikowało o wydarzeniu [artykuł](https://www.theblockcrypto.com/sponsored/atomic-swap-presented-by-decred-and-zebpay/) przed odbyciem się imprezy.
* @jy-p uczestniczył w panelu "Dylemat Idealisty" na Atomic Swap, gdzie debatował nad tym, co to znaczy być zdecentralizowanym protokołem wraz z przedstawicielami Beam, Dash i Orbs.
* Reporterzy z czołowych mediów, takich jak Bloomberg, The Block, Bitcoin Magazine, Fortune i innych, uczestniczyli w Atomic Swap. Zespół Ditto osobiście spotkał się z kilkoma członkami społeczności Decred, w tym @akinsawyerr, @anshawblack, @jholdstock, @lukebp, @jy-p, @jz, @Dustorf.
* @liz\_bagot i @treydpr z Ditto odpowiedzieli na pytania społeczności w [AMA](https://www.reddit.com/r/decred/comments/bm9as0/ama_livestream_with_liz_and_trey_from_ditto_pr/) na Reddit oraz udostępnili z niego livestream na [YouTube](https://www.youtube.com/watch?v=i8XjAOMX-VM).
* @jy-p i @MustStopMurad spotkali się z reporterami z BTC Manager, The Information i Bitcoin Magazine podczas Blockchain Week w Nowym Jorku.
* @jy-p został zacytowany w kwestii wejścia Facebooka w krypto w [Crowdfund Insider](https://www.crowdfundinsider.com/2019/05/147078-blockchain-industry-comments-on-expected-facebook-cryptocurrency-facebook-is-the-antithesis-of-what-cryptocurrency-stands-for/), [Live Bitcoin News](https://www.livebitcoinnews.com/facebook-coin-is-garnering-mixed-reactions/) i [The Daily Hodl](https://dailyhodl.com/2019/05/07/crypto-economist-behind-the-mit-bitcoin-experiment-is-reportedly-working-on-facebooks-new-coin/).
* @moo31337 [rozmawiał](https://soundcloud.com/matthew-aaron-690749808/horizen-decred-casino-coin-101) z Matthew Aaronem w podczas podcastu Crypto 101. Rozmowa rozpoczyna się o 17:32.
* @MustStopMurad [pojawił się](https://cheddar.com/media/after-40-million-hack-bitcoin-climbs-to-6-000-for-the-first-time-this-year) w Cheddar TV, gdzie wspomina o Decred w 2:07 trwania wywiadu.
* [Wzmianka](https://btcmanager.com/blockchains-neglect-social-contracts-will-likely-fail/) o Decred w BTCManager po spotkaniu na Blockchain Week.
* The Information zacytowało wypowiedź @jy-p w [artykule](https://www.theinformation.com/articles/can-crypto-crack-the-retail-market) o uruchomieniu Spedn.
* @MustStopMurad był [cytowany](https://www.forbes.com/sites/cbovaird/2019/05/10/why-is-bitcoin-leaving-top-cryptos-in-the-dust/) w Forbes, gdzie tak wspomina o Decred: "Podczas gdy Bitcoin przewyższa altcoiny od kwietnia, myślę, że altcoiny, które najściślej śledziły ruchy BTC, to te, które są gromadzone przez inwestorów i tzw. 'Smart money' i VC: projekty takie jak Decred, Tezos i Monero.
* Zabezpieczyliśmy wystąpienie @jy-p na temat decentralizacji i mechanizmu finansowania Decred w Voice of Blockchain - wydarzeniu, które odbędzie się jesienią tego roku w Chicago.
* Współpracowaliśmy ze społecznością w celu sfinalizowania zbiorowego podejścia Decred do stakingu.
* Złożyliśmy propozycję PR do Politei na najbliższe sześć miesięcy finansowania.


## Eventy

Na których byliśmy:

* 4-5 maja - [VII Bitconf](https://www.bitconf.com.br/portal/vii-bitconf/) - São Paulo, Brazylia. Decred miał dobrą [reprezentację](https://twitter.com/Decred_BR/status/1124763200984158208) na tym wydarzeniu, w którym udział wzięło ok. 1200 osób.
* 7 maja - [ThatCrypto Meetup](https://www.meetup.com/ThatCrypto/events/261086851/) - Toronto, Kanada. @michae2xl i @zubair [przedstawili](https://twitter.com/Decred_CA/status/1126168172472733696_CA/status/1126168172472733696) Decred. ([video](https://www.youtube.com/watch?v=Q47CDWYuIHc=Q47CDWYuIHc))
* 13 maja - [Consensus 2019](https://www.coindesk.com/events/consensus-2019) - Nowy Jork, USA. @jy-p przedstawił zaktualizowaną mapę rozwoju Decred, zawierającą szczegóły dotyczące finansowania i rozwoju. ([video](https://www.youtube.com/watch?v=h-AfggMHVvE=h-AfggMHVvE))
* 15 maja - [Atomic Swap](https://www.theblockcrypto.com/sponsored/atomic-swap-presented-by-decred-and-zebpay/) - Nowy Jork, USA. Decred współsponsorował imprezę Atomic Swap organizowaną przez The Block. @jy-p przemawiał na panelu "Dylemat Idealisty".
* 17 maja - Global Blockchain Forum - Hangzhou, Chiny. @Dominic [przedstawił](https://twitter.com/wanbihou/status/1129467061220941824) Decred.
* 18 maja - Chengdu, Chiny. @Dominic [reprezentował](https://twitter.com/wanbihou/status/1129750422611202048) Decred na imprezie z udziałem wielu górników.
* 18-19 maja - [CriptoLatinFest](https://criptolatinfest.com/) - Bogota, Kolumbia. @elian zaprezentował Decred na wydarzeniu z około 300 uczestnikami. Impreza przyciągnęła uczestników, którzy byli bardziej zainteresowani spekulacją niż podstawami technologii. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20190518-criptolatinfest-bogota-colombia.md))
* 20-21 maja - [La Conexión](https://www.la-conexion.com/) - Medellín, Kolumbia. @elian zaprezentował Decred na wydarzeniu z około 200 uczestnikami, międzynarodową mieszanką inwestorów, przedsiębiorców i profesjonalistów w dziedzinie kryptowalut. Wydarzenie to przyciągnęło ludzi, którzy byli zainteresowani zrozumieniem, jak działa technologia blockchain i wbudowaniem jej w swój biznes. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20190520-laconexion-medellin-colombia.md))
* 23 maja - [Decred AMA](https://twitter.com/DecredCN/status/1131487833137397760) - online. Sesja AMA została zorganizowana przez Cobo Wallet, na której @Dominic odpowiadał na pytania. AMA doprowadziło do przyłączenia się [300](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15587188721553ZAajQ:decred.org) ludzi do [chińskiego kanału](https://t.me/decred_cn) na Telegram.
* 24 maja - [Bitcoinday](https://bitcoinday.tv/) - Montevideo, Urugwaj. W wydarzeniu uczestniczyło około 200 osób, a @elian reprezentował Decred na panelu poświęconym blockchainowi i biznesowi, a także prowadził warsztaty na temat dcrtime i Politei, w których uczestniczyło około 20 osób. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20190524-bitcoinday-montevideo-uruguay.md))
* 24-25 maja - [Blockchain Nigeria Group](http://blockchainnigeria.group/) - Lagos, Nigeria. @collins i kilku innych deweloperów Grupy Raedah reprezentowało Decred na imprezie i przedstawiło prezentację.
* 28 maja - [Gophers Silesia](https://www.meetup.com/GophersSilesia/events/260673565/) - Katowice, Polska. @kozel przygotował [prezentację©](https://twitter.com/Decred_PL/status/1133452876716621824_PL/status/1133452876716621824) o Decred. Wideo wkrótce.

Nadchodzące:

* 12 czerwca - [Meetup](https://www.meetup.com/Decred-Washington-DC-Meetup-Group/events/261144707/) - Washington DC, USA. Dołącz do Decred, [The Dartmouth Entrepreneurial Network of DC](https://dendc.wildapricot.org/), i [TechSpace](https://www.techspace.com/coworking-space-near-washington-dc-virginia/) na wieczór rozmów i przegląd Decred: Zdecentralizowanej Autonomicznej Organizacji. Bilety są bezpłatne, ale ograniczone, dostępne [tutaj](https://www.meetup.com/Decred-Washington-DC-Meetup-Group/events/261144707/). Meetup organizowany przez @akinsawyerr.
* 18 czerwca - [TF Blockchain](https://www.tfblock.io/portland) - Portland, USA. @raedah będzie reprezentować Decred.
* 19-23 czerwca - [Campus Party](https://brasil.campus-party.org/campus-party-brasilia/) - Brasília, Brazylia. Zespół Decred [zaprezentuje](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15596690544084yAyIh:decred.org) 2 wykłady na głównych scenach i około 4 lub 5 na swojej przestrzeni. Społeczność brazylijska będzie sponsorować mistrzostwa CTF (Capture the Flag) z nagrodami w Decred. Impreza trwać będzie 24 godziny na dobę. W wydarzeniu weźmie udział około 60 000 uczestników i 6 000 zakwaterowanych na miejscu.
* 1-2 lipca [Wharton Roundtable on Cryptogovernance](https://zicklincenter.wharton.upenn.edu/event/wharton-cryptogovernance-workshop/) - San Francisco, USA. Zicklin Center for Business Ethics Research przy Wharton School Uniwersytetu w Pennsylwanii uruchamia nową inicjatywę dotyczącą zarządzania projektami, platformami i konsorcjami związanymi z blockchainem. Pierwsze spotkanie odbędzie się w Wharton, San Francisco dla około 25 wysoko cenionych ekspertów, reprezentujących różne perspektywy i środowiska. @akinsawyerr będzie obecny w imieniu Decred.

Repozytorium [wydarzeń](https://github.com/decredcommunity/events) zostało ponownie opublikowane w GitHubie [decredcommunity](https://github.com/decredcommunity) z 10 przeszłymi [raportami](https://github.com/decredcommunity/events/tree/master/reports), dopracowanymi i rozszerzonymi o linki do zdjęć i filmów. Uczestnicy imprez są zachęcani do [przesyłania](https://github.com/decredcommunity/events/wiki/Submit-Event-Report) raportów z wydarzeń w celu podzielenia się doświadczeniami z innymi przedstawicielami Decred i szerszą społecznością na temat sytuacji w zakresie kryptowalut w różnych miejscach na świecie.

## Media

@jy-p participated in an [AMA](https://www.reddit.com/r/CryptoCurrency/comments/bjubwv/ama_decred_project_lead_jake_yocompiatt/) on the /r/cryptocurrency subreddit, answering 18 questions.

Selected articles:

* How I Make a Living in the Crypto Gig Economy by @s\_ben ([medium](https://medium.com/@seth.benton/how-i-make-a-living-in-the-crypto-gig-economy-8674f3693858))
* The Basics of Blockchain Governance by @Haon ([medium](https://medium.com/@NoahPierau/the-basics-of-blockchain-governance-6669c098344d))
* Decred as DAE Infrastructure provider by @neil\_nie ([dcrclub](https://blog.dcrclub.org/chapter_05/dcr_DAE.html)), translated to English by @changhugo ([medium](https://medium.com/@changhugo/decred-as-a-dae-infrastructure-provider-970677f38179))
* Comparing Double Spend Resistance: Decred VS Bitcoin - Part 1 by @Fiach\_Dubh ([medium](https://medium.com/coinmonks/comparing-double-spend-resistance-decred-vs-bitcoin-part-1-330c8081b2a9))
* Bitcoin: an Accounting Revolution by Permabull Nino ([medium](https://medium.com/@permabullnino/bitcoin-an-accounting-revolution-40efcb903d7b)) - not Decred related
* The community of Decred is present around the world by @Haon ([medium](https://medium.com/decred/the-community-of-decred-is-present-around-the-world-64fcc9113924))
* Decred Governance: An Iterative Approach by @max\_bronstein ([medium](https://medium.com/@maxbronstein/decred-governnce-an-iterative-approach-2a89b9751f5e))
* Decred Price Analysis: Emergence as a digital store of value ([bravenewcoin.com](https://bravenewcoin.com/insights/decred-price-analysis-emergence-as-a-digital-store-of-value))

Translations:

* All issues of the Journal have been [translated](https://github.com/raedahgroup/decred-journal/tree/master/vietnamese) to Vietnamese by @duyenemdo - sponsored by Raedah Group. Since last mention in March the translations have been extended further into the Journal's history, now going all the way back to issue 1. Vietnamese now leads by the number of DJ translations being and is the only language that has all issues.
* March Journal [translated](https://insaf01.github.io/decred-journal-ar/journal/201903.html) to Arabic by @arij and reviewed by @abdulrahman4.

Videos:

* Decred Distributed with @elian, first release from the newly rebooted Decred Assembly ([youtube](https://www.youtube.com/watch?v=N7GYD8zwOe8))
* What is Decred - Explainer Video by blockgeeks ([youtube](https://www.youtube.com/watch?v=qT9oBsbzUos))
* Bitcoin's Big Brother... Introducing Decred - An Interview with @oregonisaac by BBOD ([youtube](https://www.youtube.com/watch?v=MscFEpWuWU4))

Audio:

* Decred: Everything You Ever Wanted to Know - Vexpoint podcast with @Haon ([vexpoint.com](http://www.vexpoint.com/decred-investment/))
* Crypto 101 podcast with @moo31337, introduction to Decred ([listennotes.com](https://www.listennotes.com/podcasts/crypto-101-with/horizen-decred-casino-coin-101-o_stJI2LaQC/), starts 17:32)
* CryptoBasic 101 Series: Decred - podcast with @richardred ([cryptobasicpodcast.com](https://www.cryptobasicpodcast.com/home/180))
* Decred in Depth episode 1 DCR 101 with @jz, hosted by @anshawblack ([youtube](https://www.youtube.com/watch?v=rcEJuN7zh2M), [soundcloud](https://soundcloud.com/decredindepth/ep-1-jonathan-zeppettini-jz-dcr-101))

## Community Discussions

Community stats as of Jun 1:

* Politeia users: 175 (+8)
* Twitter followers: 40,462 (+6)
* Reddit subscribers: 9,459 (+34)
* Matrix users: 337 (+25)
* Slack users: 6,721 (+36)
* Discord users: 2257 (+63), verified to post: 226 (+27)
* Telegram users: 3,576 (-92)
* YouTube subscribers: 3,769 (-2)
* Facebook followers: 3,219 (+1), likes: 2,954 (-2)
* LinkedIn followers: 544 (+29)
* GitHub dcrd stars: 489 (+3), forks: 1,324 (+39)

Comm systems news:

* Someone [trolled](https://www.reddit.com/r/decred/comments/bvw3pv/change_the_name_and_bring_back_tacotime_to_lead/) r/decred with some posts about @jy-p's dress sense or something in early June, and [deleted](https://www.removeddit.com/r/decred/comments/bvw3pv/change_the_name_and_bring_back_tacotime_to_lead) their posts after some time. Not feeding trolls with attention is the best known tactic.

Selected Reddit posts:

* A [resource](https://www.reddit.com/r/decred/comments/bp035s/decred_accepted_here_the_list_of_businesses_where/) tracking businesses that accept DCR in exchange for products or services.
* A post complaining that the Treasury is being [milked](https://www.reddit.com/r/decred/comments/bsk1l4/the_treasury_is_getting_milked_by_those_useless/) by useless marketing projects, written on the assumption that the "journey to the future of work" proposal would be approved. This post inspired spirited discussion about the merits of that particular proposal and marketing efforts generally.
* A [post](https://www.reddit.com/r/decred/comments/bnep6p/if_you_were_running_decrediton_at_13_or_earlier/) observing that people who did not update in time had now been forked off the network following a transaction which utilized the new rules. The post explained how to recover from this scenario.
* Ditto [AMA](https://www.reddit.com/r/decred/comments/bm9as0/ama_livestream_with_liz_and_trey_from_ditto_pr/).
* [Discussion](https://www.reddit.com/r/decred/comments/bpgv33/why_is_poloniex_delisting_decred/) about the geofencing of DCR on Poloniex. Many links on the topic are indexed in [this issue](https://github.com/decredcommunity/issues/issues/133).
* A [post](https://www.reddit.com/r/decred/comments/bth5od/microsoft_building_on_bitcoin_is_actually_amazing/) about why Microsoft building on Bitcoin is good news for Decred too inspired in depth discussion of the merits of blockchain-based identity systems.

Selected Twitter discussions:

* @BradyDale live [tweets](https://twitter.com/BradyDale/status/1128670013974622208) @jy-p's presentation at ChangeLog giving an update on Decred's progress over the last year and next steps.
* @lukebp [tweets](https://twitter.com/lukebp_/status/1132310565093879808) about misalignment of incentives in Bitcoin.
* @lukebp [tweets](https://twitter.com/lukebp_/status/1132452552317001730) about how Decred makes minority forks expensive to execute.
* @lukebp [explains](https://twitter.com/lukebp_/status/1124698848654438400) (once again) why "plutocracy" does not apply to blockchains.

## Markets

In May DCR was trading between USD 23.6-35.0 / BTC 0.0032-0.0045. The average daily rate was $27.71.

Bitcoin rose steadily from USD ~5,500 and even crossed USD 9,000 for a brief amount of time.

## Relevant External

EOS Block Producers [burned](https://www.reddit.com/r/eos/comments/bm75ih/the_mainnet_34m_eos_accumulated_4_inflation_is/) 34 million EOS (~$272 million) from the eosio.saving account. These funds had accumulated from the 4% inflation which was to be used to fund project development through a [Worker Proposal System](https://medium.com/eosys/eos-worker-proposal-system-announcement-6addcfb0134c). This idea fell out of favor with the EOS BPs and community, and 15 BPs supported the proposal to burn accumulated savings [on May 8](https://www.eosx.io/tx/26ca16319febafc0942a8c6e3be26c16b84846b7cfe5f6ade906a0b86a6c2bb7?listView=actions). New tokens are still accumulating in the savings account, but this seems likely to be removed as there is an open [referendum](https://eosauthority.com/polls_details?proposal=inflation_20190307&prev=search) to remove the 4% inflation for development entirely, which has almost unanimous support from around 2.7% of EOS tokens that have voted.

Zooko [commented](https://forum.zcashcommunity.com/t/the-future-of-zcash-in-the-year-2020/32372/173) on a long-running discussion about the future of Zcash development to express support for a new dev fund. Zcash currently allocates 20% of the block rewards to a founders reward but this is due to end in 2020. Zooko and many other advocates think the new dev fund needs to be more decentralized than the founder's reward's reliance on the Electronic Coin Company, and are encouraging community members to present and develop plans for decentralized governance of this fund.

Tezos Athens upgrade [activated](https://www.coindesk.com/in-first-tezos-blockchain-activates-upgrade-by-token-holder-voting) on May 30, marking the end of a process that began in February to select a proposal, endorse it, test it and activate it. One of the lesser discussed aspects of the protocol upgrade was the [generation](https://twitter.com/wisercharlie/status/1134240285238501376) of 100 new XTZ to be claimed by the upgrade's developers for a round of drinks. This has been described as a method of [funding development](https://medium.com/tocqueville-group/why-tezos-is-the-best-platform-for-tokenized-assets-89a960cfa828) through inflation in future, with the developers who make a protocol change proposal incorporating the generation of new XTZ which they can claim as a reward for their work.

Dash [Ventures](https://blog.dash.org/introducing-the-dash-investment-foundation-370cafcc48ee) investment foundation is nearing completion, and Dash will be holding an election to select a set of supervisors to oversee its operation. The Dash Investment Foundation will be able to take ownership of equity or other assets in consideration for network funding. The election to fill the remaining 4 of 6 supervisor seats [started](https://blog.dash.org/details-on-the-election-for-dash-investment-foundation-supervisors-25766c55a1f) on May 30, and will be followed by budgetary proposals to fund the foundation's administrative costs and allocate some capital for it to invest.

The [Open Money Initiative](https://medium.com/@openmoneyinitiative/announcing-the-open-money-initiative-61422b58ad06) was announced, a research nonprofit which will study how money is used in closed economies with collapsing monetary systems. The initiative's first project is an ethnographic study in Venezuela. The initiative is supported by funding from Zcash, Stellar, Tezos and the Cosmos supported Interchain Foundation - among others.

A Bitcoin Cash hard fork on May 15 was beset by [several](https://blog.bitmex.com/the-bitcoin-cash-hardfork-three-interrelated-incidents/) issues and in the ensuing chaos, 3,391 BCH (~$1.35 million) were double spent. A bug with Bitcoin ABC led to invalid transactions filling up the mempool and a series of empty blocks being mined. Some miners began mining blocks on the pre-hardfork chain, causing a chain split. Immediately after the bug was resolved, a 2 block reorg occurred in which funds that the hardfork made spendable by any miners were double spent. It seems likely the dominant BCH miners reorged the chain to remove transactions in which these coins were claimed by another miner - replacing with transactions where they take custody of these "free to claim" coins.

Poloniex has been busy in May, delisting [Peercoin](https://talk.peercoin.net/t/team-update-28-poloniex-delisting-legal-risks-memo-exchange-expansion-plans/9278) and a number of other cryptocurrencies, "[geofencing](https://medium.com/circle-trader/poloniex-to-stop-offering-trading-of-9-assets-to-us-customers-all-assets-remain-available-to-b4c5703c0e9)" DCR and 8 other cryptocurrencies so that US-based customers cannot trade it, and [announcing](https://medium.com/circle-trader/cosmos-atom-staking-is-coming-to-poloniex-d587d6c6615d) support for Cosmos staking. The decision to geofence DCR on the basis of regulatory uncertainty is perplexing, given the many [reasons](https://www.reddit.com/r/decred/comments/ahuawl/decred_launch_security_laws/eeiaa0n/) why DCR should not be considered a security, and Poloniex's concurrent support for ICO projects that seem to better fit the definition of a security. In a follow up [post](https://blog.circle.com/2019/05/20/us-crypto-policy-needs-to-change/), Circle CEO explained that the move is triggered by the [recent guidance](https://www.sec.gov/news/public-statement/statement-framework-investment-contract-analysis-digital-assets) from the SEC. Notably, the linked page says "This framework represents Staff views and is not a rule, regulation, or statement of the Commission. The Commission has neither approved nor disapproved its content. This framework, like other Staff guidance, is not binding on the Divisions or the Commission.". Another [post](https://blog.circle.com/2019/05/23/our-take-interpreting-recent-signals-from-us-regulatory-agencies/) from Circle further elaborated on their position and complained about the difficulties caused by uncertainty from US regulators.

Kin Foundation [started](https://twitter.com/ResearchCircle/status/1134541879675166722) a [Defend Crypto](https://www.defendcrypto.org/) initiative by which they collect donations to take SEC to court. On Jun 4 the SEC [opened](https://www.coindesk.com/the-sec-is-suing-kik-for-its-2017-ico) formal proceedings against Kik.

As part of Bitfinex's engagement with the New York District Attorney, it has [emerged](https://www.coindesk.com/tether-lawyer-confirms-stablecoin-74-percent-backed-by-cash-and-equivalents) that Tether was only 74% backed by USD on Apr 30, according to their legal representative.

Binance suffered a security [breach](https://binance.zendesk.com/hc/en-us/articles/360028031711) which resulted in the loss of 7,000 BTC. The breach was a result of hackers obtaining a large number of user API keys and 2FA codes. On twitter, @JeremyRubin [suggested](https://twitter.com/JeremyRubin/status/1125919526485254144) that if Binance released their private keys for the hacked coins (or a subset) they could coordinate a reorg to undo the theft. CZ was participating in an AMA soon after the breach was announced and mentioned that he was considering this proposition. This sparked uproar on crypto Twitter, with much discussion of whether this was a viable or advisable approach. The subject also received some in depth [treatment](https://research.circle.com/weekly-recaps/weekly-crypto-recap-to-reorg-or-not-to-reorg). Ultimately CZ decided [not](https://twitter.com/cz_binance/status/1125996194734399488) to pursue an attempted reorg because it would damage BTC's credibility and potentially split the chain/community. The losses would instead be covered by the Binance SAFU fund.

One of the articles that [quoted](https://dailyhodl.com/2019/05/07/crypto-economist-behind-the-mit-bitcoin-experiment-is-reportedly-working-on-facebooks-new-coin/) Decred on Facebook's coin had an interesting historic reference. Since 2014 MIT ran an experiment on students where Bitcoin was used to test the spreading of new technologies among the masses. A 2017 [article](http://news.mit.edu/2017/bitcoin-study-period-exclusivity-encourages-early-adopters-0713) outlining the study and conclusions noted that the insights could be used by "tech firms" who "could fulfill the early adopter's need to feel exclusive and capitalize on their potential to encourage wider adoption". A professor from another university commented "This paper helps us understand some of the challenges of launching such a currency, even without a technology-savvy population.". In May this year, CoinDesk [reported](https://www.coindesk.com/mit-economist-christian-catalini-said-to-be-working-on-facebooks-crypto-push) that one of the authors of the experiment is helping Facebook to build a cryptocurrency.

Another [sad story](https://medium.com/coinmonks/the-most-expensive-lesson-of-my-life-details-of-sim-port-hack-35de11517124) surfaced of a person's poor security practices leading to a loss of >$100K in crypto. Hint: SMS 2FA is insecure and of course, don't keep that much on an exchange.

Intel [disclosed](https://www.extremetech.com/computing/291474-intel-discloses-new-speculative-execution-security-vulnerabilities) a [new set](https://en.wikipedia.org/wiki/Microarchitectural_Data_Sampling) of speculative execution vulnerabilities. Mitigations for major operating systems were released in response.

Firefox users went through a frustrating experience of software that worked yesterday suddenly stopped working. Most Firefox addons were disabled around May 3 due to an (unexpected?) expiration of code signing certificate, a bug dubbed ['armagadd-on-2.0'](https://bugzilla.mozilla.org/show_bug.cgi?id=1548973). This included addons that protect user privacy and security by blocking tons of unwanted ad and spyware content on the web. Mozilla published a [notice](https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/) that as a part of the solution, a "fix will be automatically applied in the background" delivered via the Studies system while a more general fix was in the works.

## About This Issue

This is issue 14 of Decred Journal. Index of all issues, mirrors, and translations is available [here](https://xaur.github.io/decred-news/).

Most information from third parties is relayed directly from source after a minimal sanity check. The authors of Decred Journal have no ability to verify all claims. Please beware of scams and do your own research.

Your feedback and contributions are welcome on Reddit, [GitHub](https://github.com/xaur/decred-news/issues) and [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Credits (alphabetical order):

* writing and editing: bee, degeri, Dustorf, liz\_bagot, richardred, s\_ben
* reviews and feedback: chappjc, davecgh, dnldd, Haon, jholdstock, lukebp, matheusd, raedah
* title image: saender
