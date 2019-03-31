# Decred Journal – Luty 2019

![abstract art](../img/journal-201902-384.jpg "Objective Constructs by @saender")

Wszystkiego najlepszego, Decred! Minęły trzy lata od czasu, gdy [pierwszy blok](https://explorer.dcrdata.org/block/1) został wydobyty 8 lutego 2016 roku.

W lutym dużo się działo na platformie Politeia - 7 złożonych wniosków, 5 rozpoczęło głosowanie, a 4 przeszły w pierwszych dniach marca. Ogółem 490,000 dolarów z budżetu zostało formalnie zatwierdzone i przeznaczone na marketing i wydarzenia do końca roku 2019.

Sieć została [wystarczająco zmodernizowana](https://voting.decred.org/), aby umożliwić głosowanie konsensusowe, które ma się rozpocząć 14 marca i jest niezbędne do pełnego wsparcia Lightning Network.

Dla tych, którzy jeszcze nie zaktualizowali swoich węzłów i portfeli, [oprogramowanie w wersji v1.4.0](https://github.com/decred/decred-binaries/releases/tag/v1.4.0) zawiera wiele ulepszeń i będzie wymagane, aby węzły kontynuowały funkcjonowanie w przypadku pozytywnego wyniku głosowania. Jak zawsze, [zweryfikuj pobrane pliki](https://docs.decred.org/advanced/verifying-binaries/) i powiedz znajomym, aby zrobili to samo.

## Rozwój

[dcrd](https://github.com/decred/dcrd): polityka mempoola została zaostrzona poprzez zezwolenie na [jedno mniej podwójne wydanie](https://github.com/decred/dcrd/pull/1596) biletu i [odrzucenie](https://github.com/decred/dcrd/pull/1597) podwójnych wydatków w tym samym bloku. Typy portfeli zostały [usunięte](https://github.com/decred/dcrd/pull/1607) z dcrd i [przeniesione](https://github.com/decred/dcrwallet/pull/1394) do dcrwallet, do którego należą, co uprościło zmiany w dcrwallet, a także wywołało [refaktoryzację](https://github.com/decred/dcrd/pull/1613) w dcrd, aby zapewnić mocniejsze granice modułów i uprościć wykres zależności _(zwróć uwagę na to, jak pull request troszczy się o sprawdzających)_. Wymiana nieadministratorskich modułów Go została [usunięta](https://github.com/decred/dcrd/pull/1599) - pomaga to zapewnić, że testowany jest najnowszy kod ze wszystkich modułów i zachować ich niezależną dokładność dla zewnętrznych użytkowników.

[dcrwallet](https://github.com/decred/dcrwallet): v1 ticketbuyera została [usunięta](https://github.com/decred/dcrwallet/pull/1396) po tym, jak została wycofana z kilku wersji.

[Decrediton](https://github.com/decred/decrediton): [Aktualizacja](https://github.com/decred/decrediton/pull/2009) do wersji Electron 4 pozwoliła uczynić uruchomienie na Windowsie [bardziej wytrzymałym](https://github.com/decred/decrediton/pull/2017). Dodano [alert o wyjściu](https://github.com/decred/decrediton/pull/1989), gdy łączony jest ticketbuyer. Faza projektowania dla wielu [widoków responsywnych](https://github.com/decred/decrediton/issues?q=is%3Aissue+author%3AMariaPleshkova+created%3A2019-02-01..2019-02-28) jest zakończona i gotowa do wdrożenia.

[Politeia](https://github.com/decred/politeia): nowe funkcje obejmują podświetlanie nowych komentarzy od ostatniej wizyty i [powiadomienia drogą e-mail](https://github.com/decred/politeia/pull/680) po zmianie hasła ([zasugerowane](https://github.com/decred/politeia/issues/673) poprzez program bug bounty).

Scalono epicką robotę w [warstwie pamięci podręcznej cache'a](https://github.com/decred/politeia/pull/660)! Dzięki należą się @lukebp i wszystkim recenzentom/testerom. Toruje to drogę do wielu ulepszeń wydajności witryny. Wśród innych zakończonych prac są m.in. ulepszenia w [narzędziach wiersza polecenia](https://github.com/decred/politeia/pull/707) i [fsck](https://github.com/decred/dcrtime/pull/46) (narzędziu weryfikacji systemu plików) dla dcrtime.

W toku:

* Rozpoczęto [prace](https://github.com/decred/politeia/pull/689) nad skalowaniem bazy danych www przy użyciu CockroachDB.
* Podjęto [decyzję](https://matrix.to/#/!VFRvyndKpzcLrVslD:decred.org/$15507680085008gMbtf:decred.org) o przeniesieniu kodu dla systemu zarządzania wykonawcami do repozytoriów politeia i politeiagui, aby uniknąć utrzymywania dwóch forków bazy kodu i synchronizacji ich działania.
* Omawiana jest zmiana domyślnego algorytmu [sortowania komentarzy](https://github.com/decred/politeiagui/issues/1022).

[dcrandroid](https://github.com/decred/dcrandroid): wiele poprawek błędów i drobnych usprawnień czeka w kolejce do scalenia, spójrz na [tablicę projektu](https://github.com/decred/dcrandroid/projects/1), aby uzyskać szczegółowe informacje na temat postępu.

Tłumaczenia na jęz. [chiński](https://github.com/decred/dcrandroid/issues/336) i [wietnamski](https://github.com/decred/dcrandroid/pull/333) są w toku.

[dcrios](https://github.com/raedahgroup/dcrios): [beta](https://testflight.apple.com/join/dvq51tCh) TestFlight została zaktualizowana i trwają prace nad jej dostosowaniem do poziomu dcrandroid. Postępy można śledzić na [tej tablicy](https://github.com/raedahgroup/dcrios/projects/1).

Pierwsze wydanie kandydata jest planowane na za miesiąc, co prawdopodobnie będzie też punktem do wypuszczenia dcrandroid.

[dcrdata](https://github.com/decred/dcrdata): dodano funkcję pokazywania danych o [propozycjach na platformie Politeia](https://github.com/decred/dcrdata/pull/1016), dodano [konwersje do fiatów](https://github.com/decred/dcrdata/pull/1049) (podaż, Skarbiec, cena biletów), strona mempool przeszła [zmiany](https://github.com/decred/dcrdata/pull/982), punkty końcowe do uzyskania [surowych bloków](https://github.com/decred/dcrdata/pull/1032) i [surowych nagłówków](https://github.com/decred/dcrdata/pull/1035), oraz dodano [pakiet cache](https://github.com/decred/dcrdata/pull/1051).

Rozpoczęła się [dyskusja](https://github.com/decred/dcrdata/issues/1022) o tym, jak obliczyć koszt 51% ataku na dcrdata.

[Ticket splitting](https://github.com/matheusd/dcr-split-ticket-matcher): @matheusd [podzielił się](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$1549497567273IPjZq:decred.org) swoją perspektywą, przybliżył tło i plany odnośnie usługi podziału biletów. @david nagrał instrukcję [wideo](https://www.youtube.com/watch?v=9L8P7hL5v6w), która przechodzi przez konfigurację.

[Dokumentacja](https://github.com/decred/dcrdocs): nowa strona wyjaśniająca [cenzurę na platformie Politeia](https://docs.decred.org/governance/politeia/politeia-censorship/) i jak udowodnić, że zostało się ocenzurowanym, nowa strona odnośnie [aktualizacji portfela Decrediton](https://docs.decred.org/wallets/decrediton/upgrading-decrediton/), do strony [korzystanie z sieci testowej](https://docs.decred.org/advanced/using-testnet/) została dodana lista testnetowych VSP,  do strony [szczegóły adresów](https://docs.decred.org/advanced/address-details/) dodany został diagram generowania adresów P2PKH. Wróciła [opcja wyszukiwania](https://github.com/decred/dcrdocs/pull/846).

[decred.org](https://github.com/decred/dcrweb): aktualizacje zawartości strony i jej tłumaczeń. Rozpoczęło się [wdrożenie strony Aktualności i Publikacje](https://github.com/decred/dcrweb/issues/561).

Pierwsze wyniki programu [bug bounty](https://bounty.decred.org/): na dzień 3 marca złożono łącznie 27 raportów, z których 2 to podatności kwalifikujące się do wypłaty (72$ i 90$).

Pozostałe:

* Ciekawy szczegół z [bloga](https://matheusd.com/post/dcp0004-and-hardforks/) @matheusd o DCP0004: Komponent PoS sieci Decred może służyć jako dodatkowa ochrona przed niezamierzonymi błędami konsensusu.
* Dashboard [voting.decred.org](https://voting.decred.org/) pokazuje teraz również poprzednie agendy głosowania. jQuery zostało [usunięte](https://github.com/decred/hardforkdemo/pull/213) ku uciesze tych, którzy rozumieją, o co z nim chodzi.
* Zastąpienie Google reCAPTCHA samodzielnym rozwiązaniem zostało [scalone](https://github.com/decred/dcrstakepool/pull/281) - jest to ogromny krok w kierunku poprawy [prywatności interesariuszy](https://github.com/xaur/decred-issues/issues/25). Dzięki należą się wszystkim programistom i testerom tego patcha.
* Ciekawostka: czy wiedzieliście, że Decred [zniechęca](https://matrix.to/#/!HEeJkbPRpAqgAqgAwhXWO:decred.org/$15497657664963CvzUr:decred.org) tworzenie pyłowych danych wyjściowych?
* Wykonano parę kroków w kwestii [proof of concept interfejsu użytkownika](https://github.com/xaur/decred-issues/issues/8) dla atomic swaps.
* Wsparcie QTUM zostało [scalone](https://github.com/decred/atomicswap/pull/93) w atomicswap, a wsparcie POLIS [usunięte](https://github.com/decred/atomicswap/pull/99).
* Rozpoczęto prace nad dodaniem [wsparcia dla usługi DNSSEC](https://github.com/decred/dcrseeder/pull/19) do dcrseeder.
* [authit](https://github.com/decred/authit), interfejs użytkownika dla dcrtime jest teraz hostowany na stronie [timestamp.decred.org](https://timestamp.decred.org/). Informacje zwrotne są mile widziane w [dziale problemów/kwestii na GitHub](https://github.com/decred/authit/issues) lub na nowym kanale [#timestamp](https://matrix.to/#/!gltiHJRZiSJTzvjOEu:decred.org).

> Muszę powiedzieć, że Go to naprawdę niesamowity język. Nie sądziłem, że poczuję się tak komfortowo w nowym języku tak szybko. (@jholdstock na tym [czacie](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$15497080644503VtguR:decred.org))

Statystyki aktywności deweloperskiej na luty: 251 aktywnych PR-ów, 224 master commitów, 39 tys. dodanych i 24 tys. usuniętych linijek kodu rozsianych po 8 repozytoriach. Wkład pochodził od 3-8 programistów na każde repozytorium. Statystyki te obejmują tylko najbardziej aktywne repozytoria.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z repozytoriami Decred na GitHubie: @jozn ([dcrd](https://github.com/decred/dcrd/commits?author=jozn)), JoeGruffins ([dcrwallet](https://github.com/decred/dcrwallet/commits?author=JoeGruffins)), luoshang722 ([atomicswap](https://github.com/decred/atomicswap/commits?author=luoshang722)), rex4539 ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=rex4539)).

Gratulacje dla 3 wykonawców Ditto [umieszczonych](https://github.com/decred/dcrweb/issues/562) na decred.org:

* Elizabeth Bagot (@liz_bagot)
* Margaret Huang (@margaret_mei)
* Milvian Prieto (@milvian)

1 współpracownik został [usunięty](https://github.com/decred/dcrweb/pull/541) z decred.org: Jure Kralj (@praxis, kierownik Reddit).

## Zarządzanie

W lutym [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 14 878 DCR i wydał 17 311 DCR, co czyni go pierwszym miesiącem z ujemną sumą netto. Wykorzystując średni dzienny kurs DCR/USD w lutym w wysokości 16,51 USD, składa się to na 246 tys. USD wpływających do Skarbca i 286 tys. USD z niego wydanych. Ponieważ płatności te zostały dokonane za pracę wykonaną w styczniu, pouczające jest również rozważanie ich w kontekście styczniowej średniej dziennej stawki w wys. 17,06 USD - w tym przypadku otrzymane/wydane kwoty USD wynoszą odpowiednio 254 tys. i 295 tys. USD. Na dzień 9 marca saldo Skarbca wynosi 605 828 DCR (10,05 mln USD przy 16,6 USD/DCR).

Status propozycji na dzień 9 marca 2019:

* [Gra karciana Baeond](https://proposals.decred.org/proposals/f545b359fcf1b40b356e9cb556cb422cc7ff01b628b577f804cdc45ce414f5dd), aut. burst została odrzucona przez 97% głosujących przy uczestnictwie 29% uprawnionych do głosowania biletów (_przegapione w wydaniu styczniowym_).
* [Zapytanie ofertowe: Infrastruktura zdecentralizowanej giełdy Decred](https://proposals.decred.org/proposals/5431da8ff4eda8cdbf8f4f2e08566ffa573464b97ef6d6bae78e749f27800d3a), aut. @jy-p, otrzymała 82 komentarze na Politei, [11 komentarzy](https://www.reddit.com/r/decred/comments/ancxgx/rfp_decred_decentralized_exchange_infrastructure/) na Reddicie oraz 2 korekty, które ograniczyły zakres propozycji do MVP i jej koszt do 250 tys. dolarów (w dół z 1 mln dolarów). @bee opublikował osobistą [analizę](https://github.com/xaur/decred-proposals/blob/master/decred-dex-rfp-analysis.md). Propozycja ta wywołała również [dyskusję](https://www.reddit.com/r/DCR/comments/awbtbr/should_treasury_funded_marketing_resources_be/) na temat tego, czy Skarbiec powinien finansować promowanie takich propozycji jak ta. Głosowanie rozpoczęło się od 91,4% głosów na „tak” z 8K głosów na dzień 9 marca.
* Propozycja [Poradniki do portfeli](https://proposals.decred.org/proposals/a3def199af812b796887f4eae22e11e45f112b50c2e17252c60ed190933ec14f), aut. Denniego Lovejoya z Cryptocurrency.Market została opublikowana po wielokrotnych iteracjach i zebraniu informacji zwrotnych w [czatach](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154941035930084kFSjY:decred.org) i na [Reddicie](https://www.reddit.com/r/decred/comments/anksg2/proposed_statement_of_work_sow_for_decred/). Budżet w wysokości 750 USD został zatwierdzony z 80% głosów na tak i udziałem 24% biletów.
* [Fundusz na eventy na rok 2019](https://proposals.decred.org/proposals/d3e7f159b9680c059a3d4b398de2c8f6627108f28b7d61a3f10397acb4b5e509), aut. @Dustorf, został złożony po wstępnym przedstawieniu na [czacie](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154896889724431Mxlvj:decred.org) i [Reddicie](https://www.reddit.com/r/decred/comments/anhh8n/proposal_to_get_events_spending_approved_via/). Głosowanie zakończyło się zatwierdzeniem budżetu w wysokości 200 tys. dolarów przy 89% głosów na „tak” i frekwencji 34% uprawnionych do głosowania biletów.
* [Finansowanie marketingu w 2019 r.](https://proposals.decred.org/proposals/c84a76685e4437a15760033725044a15ad832f68f9d123eb837337060a09f86e), aut. @Dustorf, była szeroko omawiana w 68 komentarzach, oprócz [czatu](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154897255124536mFHoo:decred.org) i 44 komentarzy na [Reddicie](https://www.reddit.com/r/decred/comments/aolr79/politeia_proposal_to_fund_marketing_ops_for_2019/) poprzedzających propozycję. Budżet w wys. 290 tys. dolarów został zatwierdzony 83% głosów popierających, przy frekwencji 36% uprawnionych do głosowania biletów.
* Propozycja [integracji Decred z bankomatami kryptowalutowymi](https://proposals.decred.org/proposals/aea224a561cfed183f514a9ac700d68ba8a6c71dfbee71208fb9bff5fffab51d) złożona przez @oregonisaac jest wynikiem wielu tygodni badań, projektów i informacji zwrotnych od czasu dyskusji na temat [propozycji integracji z bankomatami kryptowalutowymi Bcash](https://proposals.decred.org/proposals/bb7e19283d5c65fed598d5a2f4afcc2b5d2eab187b9cb84fc4304430f80b5ad1) w listopadzie 2018 r. W obecnym wniosku zwrócono się do zainteresowanych stron z pytaniem, czy należy kontynuować planowanie. Jeśli wniosek zostanie zatwierdzony, zostanie przedłożony kolejny wniosek ze szczegółowymi informacjami na temat jego wdrożenia. Głosowanie nie rozpoczęło się.
* [Strona społeczności Decred](https://proposals.decred.org/proposals/fb8e6ca361c807168ea0bd6ddbfb7e05896b78f2576daf92f07315e6f8b5cd83), aut. @karamble, proponuje stronę internetową, która łączy wiele źródeł treści związanych z Decred, takich jak artykuły, filmy wideo, podcasty, raporty z wydarzeń i biznesy umożliwiające płatność DCR. Prototyp został już zbudowany przez @karamble, a propozycja zakłada 6 tys. dolarów na sfinansowanie strony przez 6 miesięcy. Głosowanie zakończyło się zatwierdzeniem 72,5% głosów na „tak”, z głosami 33% kwalifikujących się biletów.
* [Integracja Decred na giełdzie IDAX](https://proposals.decred.org/proposals/60adb9c0946482492889e85e9bce05c309665b3438dd85cb1a837df31fbf57fb), aut. acean, poszukuje 1000 DCR, aby dodać parę handlową DCR/BTC do giełdy IDAX z siedzibą w Mongolii. Głosowanie zakończyło się i propozycja została odrzucona z wynikiem 25% głosów wspierających, przy udziale 23,5% uprawnionych biletów.
* [Integracja Decred w Trust Wallet](https://proposals.decred.org/proposals/2ababdea7da2b3d8312a773d477272135a883ed772ba99cdf31eddb5f261d571), aut. @oregonisaac, proponuje włączenie Decred do „całkowicie zdecentralizowanego” Trust Wallet za około $3,300 i $100 miesięcznego wsparcia. Głosowanie nie rozpoczęło się.

Aktywność na platformie Politeia w okresie 1-28 lutego:

* 7 nowych wniosków złożonych, 5 wniosków rozpoczęło głosowanie.
* 300 komentarzy na temat propozycji od 46 różnych użytkowników (za kluczami publicznymi).
* 1 006 głosów w górę/w dół odnośnie komentarzy od 56 różnych użytkowników z prawem głosu (za kluczami publicznymi).
* 748 głosów w górę (70%) i 258 w dół (30%).

Całkowite statystyki na dzień 28 lutego 2019 r.:

* 802 komentarze na temat propozycji od 113 różnych użytkowników (za kluczami publicznymi).
* 2785 głosów w górę/w dół odnośnie komentarzy 122 od różnych użytkowników z prawem głosu (za kluczami publicznymi).
* 2 336 głosów w górę (80%) i 449 w dół (20%).
* 32 użytkowników, którzy głosowali na komentarze, ale nigdy nie komentowali, i łącznie oddali 374 głosy (13,4% wszystkich głosów).
* Około 238 komentarzy (30%) zostało oddanych przez ich autora.

Dzięki dla @richardred za automatyzację generowania powyższych statystyk.

Rozpoczęła się dyskusja na temat wprowadzenia poprawek do Konstytucji Decred i ratyfikacji nowej wersji za pomocą głosowania przez platformę Politeia. Pierwotnym celem było usunięcie przestarzałych/nieistotnych części i dodanie brakujących części z minimalnymi zmianami. Podczas dyskusji kilka osób zapytało, czy w ogóle potrzebujemy konstytucji, biorąc pod uwagę, że nie jest ona wiążąca. Linki do wszystkich dyskusji i proponowanych zmian są zebrane w [tej kwestii](https://github.com/xaur/decred-issues/issues/107).

Nowe konto [@pi_crumbs](https://twitter.com/pi_crumbs) na Twitterze powiadamia swoich obserwujących, gdy tworzone lub modyfikowane są propozycje oraz gdy zaczyna, lub kończy się głosowanie. Obecnie obsługiwane jest ręcznie przez @richardred, ale omawiana jest jego [automatyzacja](https://github.com/xaur/decred-issues/issues/102).

Kolejne konto o nazwie [@slices_of_pi] (https://twitter.com/slices_of_pi) zamieszcza komentarze na temat aktywności Politei napisane ludzką ręką.

W celu uzyskania bardziej szczegółowych informacji, analizy i komentarza przeczytaj [wydanie 10](https://medium.com/politeia-digest/issue-10-jan-1-feb-18-2018-202cde71a19d) i [wydanie 11](https://medium.com/politeia-digest/issue-11-feb-19-feb-28-2019-46befddb09fe) znakomitego Politeia Digest aut. @richardred, na podstawie których powstało powyższe podsumowanie.

## Sieć

Hashrate: na początku lutego hashrate sieci oscylował w granicy ~230 Ph/s, a miesiąc zamknął ok. ~300 Ph/s, osiągając dolną wartość 210 Ph/s i szczyt powyżej 420 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 5 marca wyglądała następująco: BTC.com 31%, Poolin 27%, F2Pool 18%, UUPool 15%, Luxor 4%, CoinMine 1% i pozostałe ok. 5% za [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu z okresu 30 dni wynosiła 111,6 DCR (+2,2) w dniu 1 marca za dcrstats.com. Cena wahała się między 98,4-124,1 DCR. Zablokowana kwota wynosiła 4,36-4,56 mln DCR, co odpowiadało 46,4-48,7% dostępnej podaży.

W lutym cena biletu i wielkość puli uległy pewnym wahaniom. 1265 biletów zakupionych w jednym interwale cenowym 11 lutego podniosło rozmiar puli do ~41 670 biletów, a cenę aż do 119,4 DCR w 7 następujących po sobie podwyżkach. Po tym nastąpiła seria 10 obniżek cen do 98,4 DCR, kiedy to pula spadła na krótko poniżej 40 tys. biletów (ostatni raz miało to miejsce w październiku 2017 r.). Na dołku cenowym, w jednym oknie cenowym zakupiono oszałamiające 2797 biletów, z maksymalnej możliwej liczby 2.880. [@ImacallyouJawdy](https://twitter.com/ImacallyouJawdy/status/1098296540290924544) zauważył, że tylko w tym oknie 282K DCR lub 3% aktualnej podaży zostało ulokowane w biletach. W rezultacie cena biletu wzrosła do 124,1 DCR, co jest nowym rekordowym osiągnięciem od czasu wdrożenia nowego algorytmu [stake diffucilty](https://github.com/decred/dcps/blob/master/dcp-0001/dcp-0001.mediawiki) w lipcu 2017 roku. Pula biletów przekroczyła 42 174 bilety, kiedy to zablokowano 48,7% dostaw DCR - to nowy rekord wszechczasów i +0,7% w stosunku do poprzedniego szczytu 7 czerwca 2018 roku. Dzięki [charts.dcr.farm](https://charts.dcr.farm/d/000000003/proof-of-stake?orgId=1) za przejrzyste wykresy.

Węzły: Na dzień 1 marca na [dcred.eu](https://dcred.eu/nodeStats) podało 205 publicznych węzłów nasłuchujących i 297 normalnych. Dystrybucja wersji: v1.5.0 dev build: 8,6% (+4,3%), v1.4.0 final: 43% (+43%), v1.4.0 dev i rc build: 7% (-6%), v1.3.0: 23% (-32%), v1.2.0: 10% (-4%), v1.1.2: 4% (-4%), v1.1.0: 2% (-1%).

[Progi aktualizacji](https://voting.decred.org/) dla PoW i PoS zostały spełnione, i automatyczne rozpoczęcie głosowania konsensusowego będzie miało miejsce około 14 marca. Podziękowania dla wszystkich, którzy zaktualizowali swoje węzły, a także dla osób, które dotarły do operatorów pul wydobywczych PoW oraz VSP za pośrednictwem różnych kanałów i poprosiły ich o aktualizację.

Choć głosowanie jeszcze się nie rozpoczęło, głosowanie blokowe już sygnalizuje głosy na agendę 'fixlnseqlocks'. Od 4 marca [były to](https://matrix.to/#/!wSdymYrEpBhsWlDJuk:decred.org/$155168912215429iStcp:decred.org) 8503 głosy na „tak” i 1 głos „nie". „Cóż za opozycja.... Przynajmniej jest to dowód na to, że przycisk „nie” działa". - @jz.

## Integracje

Nazwa kodowa VSP „Bravo” została zmieniona (https://github.com/decred/dcrwebapi/pull/59) z dcr.stakepool.net na [dcr.blue](https://dcr.blue/).

Integracje z giełdami wymian:

* [Vertbase](https://www.vertbase.com/) dodało parę DCR/USD. CEO Vertbase i współzałożyciel Justin dołączył do nas na kanale #general i [odpowiedział na pytania](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$155015221011045eRXdT:decred.org). Wśród odpowiedzi były m.in.: Vertbase obsługuje 39 z 50 stanów USA, aktywnie pracuje nad dodaniem GBP/EUR/AUD i korzysta z usług strony trzeciej w celu weryfikacji tożsamości. Ciekawą cechą Vertbase jest bardzo krótki okres przechowywania: po uregulowaniu przelewu bankowego będą oni wysyłać tokeny bezpośrednio do Twojego portfela.

> Wymagamy również podania adresu portfela, ponieważ nie chcemy przechowywać, ani nie chcemy też, abyście sami przetrzymywali swoje kryptowaluty na naszej platformie. Bądź swoim własnym bankiem! (@Justin w [#general](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$155017217111507BsAmt:decred.org))

Na dzień 8 marca zlecenia sprzedaży nie są dostępne. Zobacz również ten [post na Reddit](https://www.reddit.com/r/decred/comments/aqkl1p/vertbase_lists_decred_dcr_with_us_dollar_usd/).

* [Lykke](https://www.lykke.com/) [dodało](https://twitter.com/lykke/status/1095352586545319937) DCR w parach z BTC i USD.
* [ChainRift](https://www.chainrift.com/) zintegrowało DCR.
* [Livecoin](https://www.livecoin.net/) [dodało](https://twitter.com/livecoin_net/status/1098151449786118144) DCR w parach z BTC, ETH i USD.
* [BitMesh](https://bitmesh.com/) [uruchomiło](https://www.reddit.com/r/decred/comments/av8a69/bitmesh_has_launched_dcr_and_opened_dcrbtc/) DCR w parach z BTC i USDT.

Uwaga: autorzy Decred Journal nie mają pojęcia o wiarygodności którejkolwiek z powyższych giełd. Prosimy, zróbcie własny research [zanim](https://twitter.com/yeppoon/status/1095857386709893120) powierzycie swoje dane osobowe lub aktywa jakiemukolwiek podmiotowi.

## Adopcja

CoinFund [ogłosił](https://blog.coinfund.io/announcing-grassfed-network-and-decred-staking-pool-with-placeholder-55a32a312710) Grassfed Network, inicjatywę, która wykorzystuje "uogólnione wydobycie" do bezpośredniego udziału w sieciach zdecentralizowanych. Wiadomość ta została przedstawiona w [CoinDesk](https://www.coindesk.com/these-cryptofunds-say-generalized-mining-is-the-new-way-to-invest).

Wszelka działalność, która jest wynagradzana protokołowymi nagrodami rozliczanymi w postaci aktywów sieciowych, może być postrzegana jako [uogólnione górnictwo](https://grassfed.network/mining/). Zgodnie z tym podejściem inwestorzy mogą bezpośrednio angażować się w sieci i generować dodatkowe zyski, w porównaniu do spekulacji tylko na wartości aktywów.

Zgodnie z ogłoszeniem CoinFund połączył siły z [Placeholder](https://www.placeholder.vc/), który planuje przekazać swoje własne bilety do głosowania na [VSP Grassfed Network](https://dcr.grassfed.network) uruchomiony w styczniu. Plan ten został przedstawiony wcześniej przez Joela Monegro i Chrisa Burniske podczas [panelu](https://www.youtube.com/watch?v=tkllaH0Y0Y0ng) na konferencji Texas Bitcoin 2018. [CoinFund](https://coinfund.io/) jest firmą inwestycyjno-badawczą, założoną w 2015 r. z siedzibą w Nowym Jorku w Stanach Zjednoczonych.

## Nawiązywanie kontaktów

W lutym @Dustorf przedstawił swoje plany dotyczące [marketingu](https://proposals.decred.org/proposals/c84a76685e4437a15760033725044a15ad832f68f9d123eb837337060a09f86e) i [eventów](https://proposals.decred.org/proposals/d3e7f159b9680c059a3d4b398de2c8f6627108f28b7d61a3f10397acb4b5e509) na pozostałą część 2019 roku, które zostały przyjęte przez interesariuszy w głosowaniu. Jest to ekscytujące osiągnięcie, które jeszcze bardziej decentralizuje Decred poprzez dalsze przeniesienie bezpośredniej kontroli nad wydatkami na interesariuszy. Nad propozycjami miały miejsce burzliwe dyskusje, w których pojawiło się mnóstwo konkretów i dobrych pytań, jednak ostatecznie propozycje zostały zatwierdzone przez, odpowiednio, 83% i 89% głosujących biletów.

Wraz z zatwierdzonym budżetem rozpoczęły się poważne prace nad zakresem wniosków. Trwa planowanie w sprawie NYC Blockchain Week, który zbiega się w czasie z Consensusem. Więcej informacji na temat planów co do powyższych wydarzeń powinno zostać ogłoszone w ciągu dwóch tygodni.

Pierwszy podcast jest w toku i ma zostać ukończony i wypuszczony w marcu. Gościem będzie Decred Jesus, który uraczy nas barwnym przeglądem na temat Decred z perspektywy naziemnej. Toczą się prace nad stroną internetową, a architektura, copywriting i przygotowanie scenariusza już się rozpoczęły.

Decred Assembly i nasz biuletyn to inicjatywy, które mamy nadzieję dostarczyć do końca tego miesiąca.

Lutowa aktualizacja od Ditto:

* Przeszkoliliśmy 5 członków społeczności Decred w zakresie komunikacji z mediami.
* Uzyskaliśmy następujące relacje medialne: 15-minutowy [wywiad](https://blocktv.com/watch/2019-02-20/5c6d6a2be03e3-chain-breakers-promoting-constant-disruption-) między @jy-p i BlockTV, [felieton](https://www.forbes.com/sites/leslieankney/2019/02/04/no-more-trading-or-listing-fees-decred-releases-new-dex-proposal/) o propozycji DEX w Forbes, [felieton](https://breakermag.com/as-decred-turns-three-its-still-set-on-real-decentralization/) z okazji trzeciej rocznicy Decred w Breaker Mag, [artykuł](https://www.theblockcrypto.com/2019/02/13/they-asked-us-for-3-million-an-inside-look-into-getting-listed-on-a-crypto-exchange/) z okazji umieszczenia DCR na Vertbase w The Block Crypto z cytatami od @jz. Dziennikarz, Frank Chaparro, powiedział, że artykuł ten zyskał bardzo dużą popularność na Twitterze, a także wewnętrznie w redakcji The Block.
* Ułatwiliśmy przeprowadzenie 2 wywiadów ze środkami przekazu o tematyce krypto.
* Współpracowaliśmy ze społecznością w celu stworzenia repozytorium obrazów przyjaznych dla mediów, którymi możemy dzielić się z reporterami, aby dodawać wizualizacje do artykułów o Decred.
* Pomogliśmy zaplanować logistykę i treść wydarzenia prowadzonego przez Decred i OKCoin w San Francisco. Współpracowaliśmy z Dustinem i OKCoin, aby przygotować ogłoszenie dla Eventbrite, skoordynować wszystko z OKCoin, opracować program wydarzenia i przygotować komunikat prasowy.
* Opracowaliśmy plan, aby wypozycjonować Decred jako najlepszy środek przechowania wartości wśród różnych kanałów medialnych, włączając w to zainicjowanie długoterminowych rozmów z wybranymi reporterami z najwyższej mainstreamowych mediów.
* Współpracowaliśmy z Dustinem nad sześciomiesięcznym planem marketingowym i komunikacyjnym obejmującym PR, wydarzenia, treść itp. W ramach tej strategii staramy się budować zasadność i wiarygodność Decred wśród inwestorów instytucjonalnych. Wiąże się to z myśleniem wykraczającym poza relacje z mediami i obejmującym również inne dyscypliny: treści własne, Twitter, influencerów, wydarzenia itp.

Więcej szczegółów można znaleźć w aktualizacjach od Ditto, mających miejsce co dwa tygodnie, z [4 lutego](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154930816328395IaXDr:decred.org) oraz [15 lutego](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$155026927613161McEtC:decred.org).

Dyskusje:

* Długa [rozmowa](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org/$15498862365982zjzwP:decred.org) o percepcji i kształtowaniu narracji, wywołana kwestią tego, czy używać słowa „bug” w wiadomościach publicznych dla wersji 1.4 oprogramowania.
* [Opinie](https://www.reddit.com/r/decred/comments/ans7lg/what_do_we_think_of_converting_decreds_ticker/) na temat zmiany tickera Decred z DCR na CRED.
* [Krytyka](https://www.reddit.com/r/decred/comments/asg6kf/update_on_the_decred_14_release/) wykorzystywania nijakiego, bezdusznego stylu w kontekście ogłoszeń nt. projektu.

## Eventy

Na których byliśmy:

* [TabConf](https://tabconf.com/) w Atlancie, USA. @joshuam [stwierdził](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15497319564677Cmutw:decred.org), że: „Tabconf był niesamowity. Niezwykle zaangażowana publiczność - najlepsze pytania, jakie do tej pory otrzymałem na konferencji".
* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) w Sao Paulo, Brazylia. Około 60 tys. osób przewinęło się przez wydarzenie, które trwało 24 godziny na dobę przez 6 dni. Decred był jedyną kryptowalutą uczestniczącą oficjalnie i z ekskluzywną przestrzenią do prezentacji, wykładów i zajęć. Wszyscy brazylijscy wykonawcy-programiści wzięli w nim udział i zaprezentowali w sumie 6 prezentacji i 3 [warsztaty](https://twitter.com/matheusd_tech/status/1096434162091937792). @jy-p mówił o [bezpieczeństwie i adaptacyjności kryptowalut](https://www.youtube.com/watch?v=SMiHku6GmI). Było kilka problemów, takich jak przesunięcie i ograniczenie strefy Decred (stało się tak w przypadku prawie wszystkich uczestników) oraz słaba organizacja tłumaczeń - wszystko to wzięte pod uwagę przy planowaniu wydarzenia na przyszłość. Przeczytajcie [pełny raport](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155200602520229ditLj:decred.org) aut. @emiliomann i [notatki](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15519722647292913itWu:matrix.org) spisane przez @matheusd.
* Noc Miłości w Ghanie. Organizowany przez @George Pro. Ponieważ około 90% uczestników wiedziało o Bitcoinie, prezenterzy mogli pominąć podstawy i podkreślić wyjątkowe cechy Decred. Jednym z popularnych pytań było pytanie, gdzie DCR może być wymieniany na lokalną walutę. ([zdjęcia](https://twitter.com/deCRED_Ghana/status/1096714039978266624)))
* [Jak bezpiecznie przechowywać swoje krypto](https://www.meetup.com/Decred-Australia/events/258211699/) w Melbourne, Australia. Australijscy miłośnicy kryptowalut dyskutowali o najlepszych praktykach bezpieczeństwa i standardach bezpieczeństwa Decred. @Zohand [zauważył](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15504942691141LtOxa:decred.org), że: „Informacja zwrotna była niesamowita, a chłopaki z Coinstop i CTRL chcą zrobić kolejne wydarzenie w ciągu kilku miesięcy". ([zdjęcia](https://twitter.com/DecredAustralia/status/1097478053763018752))
* [Decred w 30 minut](https://www.eventbrite.com/e/decred-en-30-minutos-tickets-55764142050) w Mexico City, Meksyk. @elian [odnotował](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15517155592047249xtYGy:matrix.org), że: "Było to pierwsze spotkanie, na którym wszyscy byli całkiem dobrze poinformowani i świadomi o istnieniu Decred, było nas w sumie 7. Prezentacja przebiegała szybciej, ponieważ uczestnicy znali z wyprzedzeniem większość podstawowych treści, więc omówiliśmy bardziej złożone kwestie, takie jak wyzwania związane ze zdecentralizowanym zarządzaniem, najlepszy sposób stake'owania biletów i przyszły rozwój projektu, czyli kwestie takie jak LN, integracja płatności i najnowsze wydarzenia, marketing i propozycje społeczności w Politei. Bardzo miło było spotkać prawdziwych entuzjastów DCR w Meksyku. (....) Myślę, że jesteśmy dalecy od postrzegania cc jako środka wymiany w Meksyku, ale zdecydowanie przestrzeń szybko się zmienia. Aktualnie w kraju więcej Meksykanów ma kontakt z krypto niż z giełdami papierów wartościowych, to bardzo dobry wskaźnik". ([zdjęcia](https://twitter.com/DecredESP/status/1102594478664232960))
* Prezentacja na Uniwersytecie UAEM w Ecatepec, Meksyk. @elian [podzielił się spostrzeżeniami](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$1551994219193770GeoIk:matrix.org): „Mówiłem o historii pieniądza, Internecie, łańcuchu blokowym Bitcoina, łańcuchu hybrydowym Decred oraz o tym, jak pracować w przemyśle kryptowalutowym i blockchain. Zarówno studentów, jak i nauczycieli zafascynowała innowacyjność kryptowalut i blockchaina. Na publiczność składali się głównie studenci informatyki. Główne pytania dotyczyły tego, czym są pieniądze, jak oceniać wartość kryptowalut i jakie są możliwości pracy dla świeżych absolwentów w tej branży. (....) Prowadzenie rozmów na uniwersytetach jest dla mnie bardzo ważne, ponieważ wiem, że następne pokolenie programistów, prawników, księgowych itp., będzie bardzo chętnie uczyło się więcej o tej tematyce i tym, jakie okazje niesie ze sobą ta branża. Nauczyciele byli bardzo podekscytowani tym, że przedmioty te zostały przedstawione studentom, ponieważ przeprowadzać tak technologicznie zaawansowane prezentacje w uniwersytetach, które nie znajdują się w centrum miasta".
* [Meetup Decred](https://www.eventbrite.com/e/decred-meet-up-tickets-57073786231) w Winnebie, Ghana. Zorganizowany przez @George Pro, który [zauważył](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155133397211500yxtpJ:decred.org), że: "Nasze pierwsze spotkanie w Ghanie zakończyło się sukcesem. Poświęciliśmy czas na wyjaśnienie uczestnikom, jak stake'ować DCR, jak zdobyć DCR (przez proces Coinomi), używać go jako przekazy pieniężne, a także ustawienia portfela, szybkości i prywatności, między innymi". ([zdjęcia](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155133397211500yxtpJ:decred.org))
* Prezentacja na Uniwersytecie Qingdao w Qingdao, Chiny. [@wanbihou](https://twitter.com/wanbihou) opowiedział o modelu zarządzania Decred i zbliżającym się głosowaniu konsensusowym. „Studenci byli bardzo entuzjastyczni i pozytywnie nastawieni!” ([zdjęcia](https://twitter.com/wanbihou/status/1101131545010556928))

Na których będziemy:

* [Przyszłe 10 lat: kryptoboom, klapa, czy faza budowania?](https://www.eventbrite.com/e/decred-okcoin-present-the-next-10-years-crypto-boom-bust-or-buidl-tickets-57549671617) w San Francisco, USA, 12 marca. Zorganizowany przez Decred i OKCoin. CEO OKCoin Tim Byun, Jake Yocom-Piatt z Decred oraz Chris Burniske i Alex Evans z Placeholder opowiedzą o Decred i przyszłości kryptowalut.
* [Przywrócenie zaufania poprzez zarządzanie blockchainem](https://www.meetup.com/DecredCanada/events/259126224/) w Toronto, Kanada, 16 marca.
* [Konferencja Krypto 2019](https://crypto-conference.com/) w Berlinie, Niemcy, 27 marca. Wydarzenie jest częścią [berlińskiego tygodnia blockchain](https://www.berlin-blockchain-week.com/). @karamble będzie rozprawiał o adaptacyjności w walutach cyfrowych.
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) w Guadalajarze, Meksyk, 22-26 kwietnia. Skontaktuj się z @elian w celu uzyskania szczegółowych informacji.

Jak wspomniano powyżej w części „Zarządzanie”, zainteresowane strony zatwierdziły budżet w wysokości 200 tys. dolarów na [wydarzenia w 2019 r.](https://proposals.decred.org/proposals/d3e7f159b9680c059a3d4b398de2c8f6627108f28b7d61a3f10397acb4b5e509), który obejmuje silną obecność na 3 dużych imprezach i uczestnictwo w szeregu mniejszych wydarzeń.

## Media

Wybrane artykuły:

* Ocena Decred, aut. TokenGazer (chiński, [qq.com](https://mp.weixin.qq.com/s/7rMaTYXIhIpO37qiIvJX_A), _przegapione w wydaniu styczniowym_) - Decred został oceniony na 4.2
* Która kryptowaluta jest najlepsza poza Bitcoinem? - odpowiedź Pavla Svitka ([quora.com](https://www.quora.com/Which-one-is-the-best-cryptocurrency-next-to-bitcoin/answer/Pavel-Svitek)) - dzięki Pavlowi za zaprezentowanie Decred w serwisie Quora
* Koniec opłat handlowych i listingowych? Decred publikuje nową propozycję DEX, aut. Leslie Ankney ([forbes.com](https://www.forbes.com/sites/leslieankney/2019/02/04/no-more-trading-or-listing-fees-decred-releases-new-dex-proposal/))
* Jak długo będzie trwała krypto zima? Zapytaliśmy trzech ekspertów, aut. Julia Herbst ([breakermag.com](https://breakermag.com/what-the-longest-ever-bear-market-means-for-crypto/))
* Przy trzecich urodzinach Decred wciąż zmierza ku prawdziwej decentralizacji, aut. David Z. Morris ([breakermag.com](https://breakermag.com/as-decred-turns-three-its-still-set-on-real-decentralization/))
* Założyciel Decred proponuje zbudowanie zdecentralizowanej giełdy wymian jako alternatywy dla Binance, wywiad Liama Kelly'ego ([cryptoslate.com](https://cryptoslate.com/decred-founder-proposes-dex-binance-interview/))
* "Poprosili nas o 3 miliony dolarów": kulisy listingów na giełdach wymian krypto, aut. Frank Chaparro ([theblockcrypto.com](https://www.theblockcrypto.com/2019/02/13/they-asked-us-for-3-million-an-inside-look-into-getting-listed-on-a-crypto-exchange/)).
* Zarządzanie sieciami krypto jako kapitał, aut. Joel Monegro ([placeholder.vc](https://www.placeholder.vc/blog/2019/2/19/cryptonetwork-governance-as-capital))
* Korzystanie z zarządzania w celu decydowania o przyszłości: Czy Decred (DCR) zbuduje zdecentralizowaną giełdę wymian?, aut. @richardred ([investinblockchain.com](https://www.investinblockchain.com/is-decred-dcr-building-decentralized-exchange/), również w języku chińskim pod adresem [0xzx.com](https://0xzx.com/2019022708166553.html)).
* Decred wymieniony w artykułach w [Forbes](https://www.forbes.com/sites/samantharadocchia/2019/02/05/everything-about-the-digital-nomad-lifestyle-sounds-great-except-the-us-tax-system/) i [Breaker Mag](https://breakermag.com/bruce-schneier-is-right-about-blockchains-biggest-flaw-and-completely-wrong-about-its-longterm-significance/)

Wideo:

* Decred AMA TruStory - Preethi Kasireddy w rozmowie z Isaaciem J i Matheusem z Decred, aby dowiedzieć się więcej na temat hybrydowego mechanizmu konsensusu proof-of-work/proof-of-stake i ich modelu zarządzania ([youtube](https://www.youtube.com/watch?v=OKdaa630YDk)).
* Bezpieczeństwo i ć kryptowalut - prezentacja @jy-p na Campus Party w Brazylii ([youtube](https://www.youtube.com/watch?v=SMiHku6GmI))
* Potencjał decentralizacji - wywiad z @jy-p dla BlockTV ([blocktv.com](https://blocktv.com/watch/2019-02-20/5c6d6a2be03e3-chain-breakers-promoting-constant-disruption-))
* Decred wspomniany przez Chrisa DeRose w [wywiadzie](https://www.youtube.com/watch?v=W1tbPQOMxH8&t=3790) dla Crypto Insider

Audio:

* ITK Crypto #8 - Tom White i Crypto SI rozmawiają z @kozel na temat zarządzania w krypto ([youtube](https://www.youtube.com/watch?v=H-qZBsQY5BM))
* Murad Mahmudov i Aleks Svetski opowiadają o Bitcoinie, Lightning i aktualnych perspektywach rynkowych. „Mam więc nadzieję, że moi przyjaciele maksymaliści tego nie słyszą, ale....” ([podplayer.net](http://podplayer.net/?id=64230840), część o Decred zaczyna się od [1:36:45](http://podplayer.net/?id=64230840&t=5805)).

Tłumaczenia:

* Decred Journal - styczeń 2019 [w języku chińskim](https://www.jianshu.com/p/097265621ef6), aut. @guang (również Dominic, Hugo i Jill), [w języku hiszpańskim](https://medium.com/@decred_es/revista-decred-enero-2019-549e2b051f5a), aut. @elian. Dziękujemy!

## Dyskusje społeczności
Statystyki społeczności na dzień 1-2 marca:

* Obserwujący na Twitterze: 39,797 (+19)
* Subskrybenci na Reddit: 9,365 (+35)
* Użytkownicy na Matrixie: 266 (+19)
* Użytkownicy na Slacku: 6,581 (+52)
* Użytkownicy na Discordzie: 2,101, zweryfikowani z możliwością pisania postów: 131
* Użytkownicy na Telegramie: 4,272 (-231)
* Subskrybenci na YouTube: 3,746 (-6)
* Obserwujący na Facebooku: 3,141 (+9), polubień: 2,896 (+5)
* Obserwujący na LinkedIn: strona Decred 483 (+17), strona Politeia 29 (+2)
* GitHub: 474 gwiazdek (+6) i 1,237 forków repozytorium dcrd (+16)

Społeczności na Telegramie: chińska 866 (+53), włoska 160 (+28), portugalska 642 (+100), hiszpańska 73 (+11).

Chińska społeczność była w lutym całkiem aktywna:

* rozpoczęła [#chiński](https://matrix.to/#/!nUWpVrwhlJFyLuMlGw:decred.org) kanał na Matrixie
* Yin Guochao kontynuował relacjonowanie Decred: jeden artykuł o [dcrtime](https://mp.weixin.qq.com/s/ks48Piu3s2zy4btZW0kBDQ) i drugi o [atomic swaps](https://mp.weixin.qq.com/s/Lgem_BqFBnLUsY7AzC5x_w)
* Dominic zrobił [wprowadzenie](https://twitter.com/wanbihou/status/1101122114118184961) do technologii blockchain i Decred na uniwersytecie dla zainteresowanych studentów
* artykuł Yin zmotywował innego członka społeczności, aby [napisać więcej](https://teakki.com/p/5c774a9ab1029f607605bc76) o dcrtime i stworzyć [web UI](http://www.ibitlin.com/dcrtool#/dcrtime) dla plików znaczników czasu i surowego tekstu (UI dla dcrtime jest śledzony w [tym wydaniu](https://github.com/xaur/decred-issues/issues/9)).

Wiadomości z platform komunikacyjnych:

* dla zachowania spójności w nieanglojęzycznych pokojach czatu zmieniono nazwy po na takie, które odzwierciedlają języki w nich używane, a nieużywane pokoje zostały usunięte. Kanały [#chiński](https://matrix.to/#/!nUWpVrwhlJFyLuMlGw:decred.org), [#portugalski](https://matrix.to/#/!FBtUquQLhAvHeBIkac:decred.org), [#rosyjski](https://matrix.to/#/!TQzfaYsKyxAqQQQQeX:decred.org) i [#hiszpański](https://matrix.to/#/!pkeRzinGCRtjIIhAAK:decred.org) są już dostępne na Matrixie.
* Klient [Riot](https://riot.im/app/#/room/#general:decred.org) został [zaktualizowany](https://medium.com/@RiotChat/the-big-1-0-68fa7c6050be) do wersji 1.0 z przerobionym UI.

Kolejny wątek Reddit został [usunięty](https://www.reddit.com/r/decred/comments/an4b6z/forbes_no_more_trading_or_listing_fees_decred/) po wzbudzeniu pewnej dyskusji. Moderatorzy nie mają prawa zabraniać niszczenia wiedzy społeczności, z wyjątkiem obejścia problemu poprzez [ponowne założenie](https://www.reddit.com/r/decred/comments/ar29jd/forbes_no_more_trading_or_listing_fees_decred/) usuniętego wątku. Pomysły na bardziej trwałe, Redditopodobne forum są zbierane w [tej kwestii](https://github.com/xaur/decred-issues/issues/38).

[Post](https://www.reddit.com/r/decred/comments/api7e7/decreds_community_spaces_a_crude_analogy/) pt. „Przestrzenie społeczności Decred - prosta analogia” pióra @richardred porównuje wiele platform komunikacyjnych używanych przez społeczność Decred. W dalszej dyskusji zwrócono uwagę na problemy nadążania za czatami, znaczenie posiadania tętniącej życiem społeczności Reddit oraz kwestie związane z dyskusjami nad propozycjami poza platformą Politeia.

## Rynki

W lutym DCR kurs wymiany Decred wahał się pomiędzy 14,97-18,28 USD / BTC 0,0042-0,0048. Średni dzienny kurs wynosił 16,51 USD.

## Ważne kwestie i wiadomości poboczne

[Badanie](https://medium.com/@MoneroCrusher/analiza-more than-85-of-the-current-monero-hashrate-is-asics-asics-and-each-machine-is-doing-128-kh-s-f39e3dca7d78) wartości nonce a Monero dokumentuje różne wzorce w ich dystrybucji, gdy układy ASIC były wykorzystywane w wydobyciu, rozważa metody, jakie górnicy ASIC mogą podjąć w celu ukrycia ich obecności w sieci i jak można ich wykryć. Badanie spekuluje, że w momencie pisania 85% mocy obliczeniowej sieci Monero pochodzi z układów ASIC.

Na początku 2018 r. w Zcash odkryto [podatność na podrabianie](https://z.cash/blog/zcash-counterfeiting-vulnerability-successfully-remediated/). „Ta podatność jest tak subtelna, że omijała lata analiz prowadzonych przez kryptografów-ekspertów ze specjalizacją w systemach udowadniania zerowej wiedzy i zk-SNARKs". Została ona po cichu załatana wraz z aktualizacją sieci Sapling, która miała miejsce 28 października 2018 r. a ten [post](https://z.cash/blog/zcash-counterfeiting-vulnerability-successfully-remediated/) z 5 lutego wyjaśnia, w jaki sposób rozwiązano problem podatności w Zcash i w jaki sposób zostały o nim powiadomione inne dotknięte problemem monety (takie jak Horizen i Komodo). Natura kryptografii Zcash jest taka, że trudno jest określić, czy którekolwiek z ZEC zostało podrobione w czasie, gdy sieć była podatna na fałszerstwo. Zespół Zcash, który zgłosił błąd, uważa, że nie został on wykorzystany, ponieważ „odkrycie podatności wymagałoby wysokiego poziomu zaawansowania technicznego i kryptograficznego, które posiada bardzo niewiele osób".

Deweloper Grin opublikował [post na forum](https://www.grin-forum.org/t/solved-early-disappointments/3682) wyrażając rozczarowanie, że prośba o darowizny na rzecz jednego z deweloperów nie została wypełniona po dwóch tygodniach od uruchomienia sieci, grożąc tym samym pobraniem 20% z nagrody za wydobycie bloku na finansowanie rozwoju. Po rozpowszechnieniu tej wiadomości [kampania](https://grin-tech.org/yeastplume) szybko zebrała 67 580 EUR, przekraczając cel w wysokości 55 000 EUR. Jak [zauważył](https://breakermag.com/as-decred-turns-three-its-still-set-on-real-decentralization/) Breaker Mag, Grin „przyciągnął [dziesiątki milionów dolarów](https://www.coindesk.com/grin-launch-crypto-interest-from-deep-pocketed-investors) w inwestycjach górniczych, ale miał problemy z pozyskaniem zaledwie 62 tys. dolarów, aby opłacić głównego dewelopera na okres sześciu miesięcy".

Posiadacze Ethereum przeprowadzają kolejny [sygnalizujący carbonvote](http://www.progpowcarbonvote.com/) o tym, czy chcą zmienić algorytm wydobywczy na ProgPoW. Głosowanie rozpoczęło się silnym [sprzeciwem](https://www.trustnodes.com/2019/02/14/98-of-ethereum-vote-against-progpow) wobec zmiany (98% nie), ale później odwróciło się do silnego poparcia (94% tak) na dzień 4 marca (z 3% ETH w cyrkulacji biorących udział w głosowaniu). Chociaż carbonvoting nie ma oficjalnego miejsca w zarządzaniu Ethereum, metoda ta jest stosowana, ponieważ:

> Zauważyliśmy dużo trollingu i naganiactwa po obu stronach debaty z anonimowych kont na forach, youtube, telegramie, gitterze, reddicie i twitterze. Nie ma sposobu, aby wiedzieć, czy te konta należą do prawdziwych, którzy faktycznie mają finansowy udział w ethereum, czy też są to po prostu konta trolli i naganiaczy finansowane przez jedną ze stron debaty.

Tezos rozpoczął [głosowanie](https://blog.nomadic-labs.com/athens-proposals-injected.html) w sprawie pierwszej [poprawki](https://blog.nomadic-labs.com/athens-our-proposals-for-the-first-voted-amendment.html) do swojego protokołu w dniu 25 lutego ([prosty przewodnik](https://medium.com/tezos-spotlight/tezos-the-first-amendment-a-laymans-guide-7424ef1d3e13), [szczegółowy przewodnik](https://medium.com/tezos/amending-tezos-b77949d97e1e) do procesu zmian). Proces wprowadzania zmian składa się z 4 etapów, z których każdy trwa 8 „cykli” (cykl trwa około 3 dni, więc każdy etap trwa około 24 dni). W pierwszej fazie piekarze składają i głosują nad propozycjami. Obecnie w pierwszej fazie ocenie poddane są 2 wnioski, które zwiększają limit paliwa, lecz jedna z nich zmniejsza również minimalną „wielkość rolki” (ilość XTZ wymagana, aby zostać piekarzem). Interesujące jest to, że Kialo jest [wykorzystywane](https://www.kialo.com/tezos-protocol-amendment-1-25295) przez niektórych członków społeczności Tezos do przeprowadzania dyskusji nad tymi propozycjami. Kiedy pierwsza faza dobiegnie końca, propozycja z największym poparciem przejdzie do fazy 2, gdzie musi zostać zatwierdzona przez co najmniej 80% piekarzy. Jeśli kryteria będą spełnione, po tym nastąpi faza testowa, w której stworzony będzie testowy fork z zastosowanymi zmianami i która trwa 48 godzin (w pozostałej części tej fazy może być uruchomiona kolejna sieć testowa odpowiadająca propozycji, aby umożliwić dalsze testy). Po zakończeniu fazy testowej piekarze głosują nad tym, czy zmiany powinny zostać aktywowane, przy czym wymagana jest 80% ponadwiększość głosów. Po tej 4. fazie zmiany są aktywowane (lub nie) i cykl rozpoczyna się ponownie od nowych propozycji.

Oprogramowanie Dash v0.13.1 zostało [wydane](https://blog.dash.org/dash-core-v0-13-1-release-5d6e06031ba3) 8 lutego, aby „przyspieszyć przyjęcie Dash Core v0.13". Dash Core [v0.13](https://blog.dash.org/dash-core-v0-13-on-mainnet-dc9609b0f6f9) miało na celu aktywację [DIP3](https://github.com/dashpay/dips/blob/master/dip-0003.md), lecz posiadał próg aktywacji w wys. 80% bloków sygnalizujących wsparcie górników PoW i masternode'ów w oknie 7 dni przed rozpoczęciem aktywacji. Po niespełnieniu tych kryteriów przez około 24 dni zdecydowano, że są one zbyt rygorystyczne i że można zrezygnować z wymogu sygnalizacji masternodów. Kiedy wystarczająca liczba górników PoW przyjmie v0.13.1, zmiana zostanie aktywowana tydzień później ([aktywowana](https://blog.dash.org/product-update-february-21-2019-5f067b62df00) została około 26 lutego).

Protokół 0x (ZRX) przeprowadził [pierwsze](https://blog.0xproject.com/how-to-participate-in-the-zeip-23-vote-eaa861298033) głosowanie posiadaczy tokenów w okresie pomiędzy 18-25 lutym. Głosowanie miało na celu zatwierdzenie [ZEIP-23](https://blog.0xproject.com/zeip-23-trade-bundles-of-assets-fe69eb3ed960) i umożliwienie „handlu pakietami aktywów". Wniosek został [zatwierdzony](https://0x.org/vote) z 99% głosów na „tak”, przy udziale 5 061 033 ZRX (0,86% podaży w obiegu).

Propozycja finansowania Fundacji NEM [rozpoczęła](https://forum.nem.io/t/nem-foundation-update-vote-for-funding-proposal-2019/22007) głosowanie 15 lutego, które trwało 5 dni. Propozycja finansowania [uchwalona](https://forum.nem.io/t/vote-for-nem-foundation-funding-proposal-2019-approved-by-the-community/22060) została przy stosunku głosów 90% „za” i 10% głosów „przeciw” - pochodzącymi od 4,56% głosów „Proof of Importance” (sposób ważenia wpływu posiadaczy NEM). Głosowanie przeprowadzono w oparciu o założenie, że wymagana była 65% większość głosów na „tak”, a co najmniej 3% POI sieci musi zagłosować na „tak” jako wymóg osiągnięcia kworum. Głosowanie zostało przeprowadzone z portfela NEM poprzez wysłanie transakcji w wys. 0 XEM na adres „tak” lub „nie". Kolejna, równoczesna propozycja finansowania „NEM Labs” również zakończyła się sukcesem, przy podobnym poziomie uczestnictwa i 98,8% poparcia. Propozycja Fundacji NEM zwróciła się o 8 milionów dolarów w XEM (liczba jest zaskakująco trudna do znalezienia, można ją znaleźć tylko w [prezentacji google docs](https://docs.google.com/presentation/d/1nMR_1ajVcpdGW7g8I0p7ZGh88tZ1SL5RzG5RzG5TsLW6Qnk/edit#slide=id.p2)), podczas gdy propozycja NEM Labs opiewała na 3,27 miliona dolarów.

Raport transparentności sieci Aragon za IV kwartał 2018 r. został [opublikowany](https://blog.aragon.org/aragon-q4-2018-transparency-report/). Raport ten przedstawia szczegółowy podział wydatków związanych z projektem. Łączne wydatki w IV kwartale 2018 r. wyniosły ~1,05 mln EUR lub równowartość tej kwoty w kryptowalucie, w tym 268 tys. EUR na wynagrodzenia, 330 tys. EUR na płatności dla usługodawców, 45 tys. EUR na sponsorów/bilety na imprezy, 63 tys. na zorganizowanie konferencji AraCon i 260 tys. na zespoły [Nest](https://github.com/aragon/nest)(program grantów). Niniejszy raport opisuje również finansowe kroki [hedgingowe](https://twitter.com/AragonProject/status/1067349802365739008) podjęte przez Stowarzyszenie Aragon - wymianę części ETH zgromadzonych podczas ICO na zakup innych aktywów.

Czarna lista wydana przez forum arbitrażowe EOS Core (ECAF) w czerwcu 2018 r. miała prawo do [stracenia ważności](https://medium.com/@eos42/proposed-solution-for-a-broken-blacklist-ce1c18bdf81c), gdy nowy producent bloku, w którym nie skonfigurowano czarnej listy został wprowadzony. Pozwoliło to jednemu z wykluczonych adresów na przeniesienie ponad 2 mln EOS. Przypadek ten wynika z faktu, że czarna lista została zaimplementowana jako lista adresów, od których producenci bloków nie będą przetwarzać transakcji, przy czym każdy producent bloku jest odpowiedzialny za ręczne jej prowadzenie. Jeśli tylko jeden z 21 największych BP nie posiada zaktualizowanej czarnej listy, konta na czarnej liście są narażone na opróżnienie. Jednym z zaproponowanych rozwiązań jest „wyzerowanie kluczy” do momentu podjęcia decyzji, co zrobić z zamrożonymi środkami. To, co zrobić z funduszami z czarnej listy wciąż jest problemem dla EOS, a samo ECAF może zostać rozwiązany, jeśli otwarte referendum w sprawie „zlikwidowania ECAF” zostanie rozstrzygnięte (obecnie 99% na „tak”, przy 2,4% EOS, które oddały głos).

Binance [uruchamia](https://www.theblockcrypto.com/2019/02/07/binance-moves-away-from-ethereum-as-it-prepares-to-launch-dex/) swoją DEX na podstawie protokółu Tendermint i DPoS projektu Cosmos. Opłata za umieszczenie na giełdzie "prawdopodobnie będzie bliska 100 tys. dolarów”, aby „ograniczyć liczbę projektów spamerskich lub oszustw". W odróżnieniu od Binance, projekt DEX autorstwa Decred nie zawiera żadnych opłat za umieszczenie na liście i nie wymaga dodatkowego blockchaina dla jego działania.

Kanadyjska giełda QuadrigaCX [jest winna](https://www.coindesk.com/quadriga-creditor-protection-filing) swoim klientom 190 milionów dolarów. Do funduszy, podobno, [nie można uzyskać dostępu](https://www.coindesk.com/quadrigacx-crypto-exchange-users-say-they-still-cant-get-their-money-out) po śmierci jej założyciela, który miał wyłączną kontrolę lub wiedzę na temat kwestii przechowywania funduszy przez gieldę w zimnych portfelach. Kolejne 500 tys. dolarów w BTC zostało zablokowane „przez pomyłkę” za [tym artykułem](https://www.coindesk.com/quadriga-inadvertently-sent-btc-to-dead-ceos-cold-wallet-ey-report). Nigdy niekończący się sznureczek awarii scentralizowanych giełd wymiany pokazuje, jak trudne jest przechowywanie i opieka nad kryptowalutami.

Medium ponownie pokazało swoją moc poprzez [zawieszenie](https://archive.today/iKQlv) konta, które [zamieściło](https://medium.com/@zeroresearchproof/quadrigacx-chain-analiza-analiza-report-pt-1-bitcoin-wallets-19d3a375d389) analizę łańcuchową portfeli QuadrigaCX. Na szczęście ktoś zrobił [migawkę](https://archive.today/xsztt) posta. Zawieszenie ukrywa całą zawartość konta i jest zaimplementowane jako przekierowanie do tej samej dla wszystkich strony, która obwieszcza, że „ta strona jest niedostępna” i nie podaje tego przyczyny. Medium jest potężną platformą, ale w jej centrum znajduje się scentralizowana usługa, która może blokować dane tych, którzy nie tworzą kopii zapasowych. Wcześniejsze zachowanie takie jak to wywołało [dyskusję](https://github.com/xaur/decred-issues/issues/70) o migracji z Medium lub traktowaniu go jedynie jako lustro.

Złośliwe oprogramowanie na Androida zostało [wykryte](https://www.welivesecurity.com/2019/02/08/first-clipper-malware-google-play/) w Google Play Store. Zmienia ono adres (konta) kryptowaluty w schowku. Zawsze dokładnie sprawdź adres przed wysłaniem.

## O tym wydaniu

To 11. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze opinie i komentarze są mile widziane na portalach Reddit, [GitHub](https://github.com/xaur/decred-news/issues) oraz [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Zasługi (kolejność alfabetyczna): bee, davecgh, degeri, Dustorf, emiliomann, guang, jholdstock, liz_bagot, matheusd, raedah, sambiohazard. Szczególne dzięki dla richardred za obszerny przegląd zarządzania w sferze krypto, oraz dla saender za ilustrację dla tego wydania Journala.
