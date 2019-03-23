# Decred Journal – Luty 2019

![abstract art](../img/journal-201902-384.jpg "Objective Constructs by @saender")

Wszystkiego najlepszego, Decred! Minęły trzy lata od czasu, gdy [pierwszy blok](https://explorer.dcrdata.org/block/1) został wydobyty 8 lutego 2016 roku.

W lutym dużo się działo na platformie Politeia - 7 złożonych wniosków, 5 rozpoczęło głosowanie, a 4 przeszły w pierwszych dniach marca. Ogółem 490,000 dolarów z budżetu zostało formalnie zatwierdzone i przeznaczone na marketing i wydarzenia do końca roku 2019.

Sieć została [wystarczająco zmodernizowana](https://voting.decred.org/), aby umożliwić głosowanie konsensusowe, które ma się rozpocząć 14 marca i jest niezbędne do pełnego wsparcia Lightning Network.

Dla tych, którzy jeszcze nie zaktualizowali swoich węzłów i portfeli, [oprogramowanie w wersji v1.4.0](https://github.com/decred/decred-binaries/releases/tag/v1.4.0) zawiera wiele ulepszeń i będzie wymagane, aby węzły kontynuowały funkcjonowanie w przypadku pozytywnego wyniku głosowania. Jak zawsze, [zweryfikuj pobrane pliki](https://docs.decred.org/advanced/verifying-binaries/) i powiedz znajomym, aby zrobili to samo.

## Rozwój

[dcrd](https://github.com/decred/dcrd): polityka mempoola została zaostrzona poprzez zezwolenie na [jedno mniej podwójne wydanie](https://github.com/decred/dcrd/pull/1596) biletu i [odrzucenie](https://github.com/decred/dcrd/pull/1597) podwójnych wydatków w tym samym bloku. Typy portfeli zostały [usunięte](https://github.com/decred/dcrd/pull/1607) z dcrd i [przeniesione](https://github.com/decred/dcrwallet/pull/1394) do dcrwallet, do którego należą, co uprościło zmiany w dcrwallet, a także wywołało [refaktoring](https://github.com/decred/dcrd/pull/1613) w dcrd, aby zapewnić mocniejsze granice modułów i uprościć wykres zależności _(zwróć uwagę na to, jak wniosek o pociągnięcie troszczy się o sprawdzających)_. Wymiana nieadministratorskich modułów Go została [usunięta](https://github.com/decred/dcrd/pull/1599) - pomaga to zapewnić, że testowany jest najnowszy kod ze wszystkich modułów i zachować ich niezależną dokładność dla zewnętrznych użytkowników.

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
* Dashboard [voting.decred.org](https://voting.decred.org/) pokazuje teraz również poprzednie agendy głosowania. jQuery zostało [usunięte](https://github.com/decred/hardforkdemo/pull/213) ku uciesze tych, którzy rozumieją o co z nim chodzi.
* Zastąpienie Google reCAPTCHA samodzielnym rozwiązaniem zostało [scalone](https://github.com/decred/dcrstakepool/pull/281) - jest to ogromny krok w kierunku poprawy [prywatności interesariuszy](https://github.com/xaur/decred-issues/issues/25). Dzięki należą się wszystkim programistom i testerom tego patcha.
* Ciekawostka: czy wiedzieliście, że Decred [zniechęca](https://matrix.to/#/!HEeJkbPRpAqgAqgAwhXWO:decred.org/$15497657664963CvzUr:decred.org) tworzeniepyłowych danych wyjściowych?
* Wykonano parę kroków w kwestii [proof of concept interfejsu użytkownika](https://github.com/xaur/decred-issues/issues/8) dla atomic swaps.
* Wsparcie QTUM zostało [scalone](https://github.com/decred/atomicswap/pull/93) w atomicswap, a wsparcie POLIS [usunięte](https://github.com/decred/atomicswap/pull/99).
* Rozpoczęto prace nad dodaniem [wsparcia dla usługi DNSSEC](https://github.com/decred/dcrseeder/pull/19) do dcrseeder.
* [authit](https://github.com/decred/authit), interfejs użytkownika dla dcrtime jest teraz hostowany na stronie [timestamp.decred.org](https://timestamp.decred.org/). Informacje zwrotne są mile widziane w [dziale problemów/kwestii na GitHub](https://github.com/decred/authit/issues) lub na nowym kanale [#timestamp](https://matrix.to/#/!gltiHJRZiSJTzvjOEu:decred.org).

> Muszę powiedzieć, że Go to naprawdę niesamowity język. Nie sądziłem, że poczuję się tak komfortowo w nowym języku tak szybko. (@jholdstock na tym [czacie](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$15497080644503VtguR:decred.org))

Statystyki aktywności deweloperskiej na luty: 251 aktywnych PR-ów, 224 master commitów, 39 tys. dodanych i 24 tys. usuniętych linijek kodu rozsianych po 8 repozytoriach. Wkład pochodził od 3-8 programistów na każdego repozytorium. Statystyki te obejmują tylko najbardziej aktywne repozytoria.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z repozytoriami Decred na GitHubie: @jozn ([dcrd](https://github.com/decred/dcrd/commits?author=jozn)), JoeGruffins ([dcrwallet](https://github.com/decred/dcrwallet/commits?author=JoeGruffins)), luoshang722 ([atomicswap](https://github.com/decred/atomicswap/commits?author=luoshang722)), rex4539 ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=rex4539)).

Gratulacje dla 3 wykonawców Ditto [umieszczonych](https://github.com/decred/dcrweb/issues/562) na decred.org:

* Elizabeth Bagot (@liz_bagot)
* Margaret Huang (@margaret_mei)
* Milvian Prieto (@milvian)

1 współpracownik został [usunięty](https://github.com/decred/dcrweb/pull/541) z decred.org: Jure Kralj (@praxis, kierownik Reddit).

## Zarządzanie

W lutym [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 14 878 DCR i wydał 17 311 DCR, co czyni go pierwszym miesiącem z ujemną sumą netto. Wykorzystując średni dzienny kurs DCR/USD w lutym w wysokości 16,51 USD, składa się to na  246 tys. USD wpływających do Skarbca i 286 tys. USD z niego wydanych. Ponieważ płatności te zostały dokonane za pracę wykonaną w styczniu, pouczające jest również rozważanie ich w kontekście styczniowej średniej dziennej stawki w wys. 17,06 USD - w tym przypadku otrzymane/wydane kwoty USD wynoszą odpowiednio 254 tys. i 295 tys. USD. Na dzień 9 marca saldo Skarbca wynosi 605 828 DCR (10,05 mln USD przy 16,6 USD/DCR).

Status propozycji na dzień 9 marca 2019:

* [Gra karciana Baeond](https://proposals.decred.org/proposals/f545b359fcf1b40b356e9cb556cb422cc7ff01b628b577f804cdc45ce414f5dd), aut. burst została odrzucona przez 97% głosujących przy uczestnictwie 29% uprawnionych do głosowania biletów (_przegapione w wydaniu styczniowym_).
* [Zapytanie ofertowe: Infrastruktura zdecentralizowanej giełdy Decred](https://proposals.decred.org/proposals/5431da8ff4eda8cdbf8f4f2e08566ffa573464b97ef6d6bae78e749f27800d3a), aut. @jy-p, otrzymała 82 komentarze na Politei, [11 komentarzy](https://www.reddit.com/r/decred/comments/ancxgx/rfp_decred_decentralized_exchange_infrastructure/) na Reddicie oraz 2 korekty, które ograniczyły zakres propozycji do MVP i jej koszt do 250 tys. dolarów (w dół z 1 mln dolarów). @bee opublikował osobistą [analizę](https://github.com/xaur/decred-proposals/blob/master/decred-dex-rfp-analysis.md). Propozycja ta wywołała również [dyskusję](https://www.reddit.com/r/DCR/comments/awbtbr/should_treasury_funded_marketing_resources_be/) na temat tego, czy Skarbiec powinien finansować promowanie takich propozycji jak ta. Głosowanie rozpoczęło się od 91,4% głosów na "tak" z 8K głosów na dzień 9 marca.
* Propozycja [Poradniki do portfeli](https://proposals.decred.org/proposals/a3def199af812b796887f4eae22e11e45f112b50c2e17252c60ed190933ec14f), aut. Denniego Lovejoya z Cryptocurrency.Market została opublikowana po wielokrotnych iteracjach i zebraniu informacji zwrotnych w [czatach](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154941035930084kFSjY:decred.org) i na [Reddicie](https://www.reddit.com/r/decred/comments/anksg2/proposed_statement_of_work_sow_for_decred/). Budżet w wysokości 750 USD został zatwierdzony z 80% głosów na tak i udziałem 24% biletów.
* [Fundusz na eventy na rok 2019](https://proposals.decred.org/proposals/d3e7f159b9680c059a3d4b398de2c8f6627108f28b7d61a3f10397acb4b5e509), aut. @Dustorf, został złożony po wstępnym przedstawieniu na [czacie](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154896889724431Mxlvj:decred.org) i [Reddicie](https://www.reddit.com/r/decred/comments/anhh8n/proposal_to_get_events_spending_approved_via/). Głosowanie zakończyło się zatwierdzeniem budżetu w wysokości 200 tys. dolarów przy 89% głosów na "tak" i frekwencji 34% uprawnionych do głosowania biletów.
* [Finansowanie marketingu w 2019 r](https://proposals.decred.org/proposals/c84a76685e4437a15760033725044a15ad832f68f9d123eb837337060a09f86e), aut. @Dustorf, była szeroko omawiana w 68 komentarzach, oprócz [czatu](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154897255124536mFHoo:decred.org) i 44 komentarzy na [Reddicie](https://www.reddit.com/r/decred/comments/aolr79/politeia_proposal_to_fund_marketing_ops_for_2019/) poprzedzających propozycję. Budżet w wys. 290 tys. dolarów został zatwierdzony 83% głosów popierających, przy frekwencji 36% uprawnionych do głosowania biletów.
* Propozycja [integracji Decred z bankomatami kryptowalutowymi](https://proposals.decred.org/proposals/aea224a561cfed183f514a9ac700d68ba8a6c71dfbee71208fb9bff5fffab51d) złożona przez @oregonisaac jest wynikiem wielu tygodni badań, projektów i informacji zwrotnych od czasu dyskusji na temat [propozycji integracji z bankomatami kryptowalutowymi Bcash](https://proposals.decred.org/proposals/bb7e19283d5c65fed598d5a2f4afcc2b5d2eab187b9cb84fc4304430f80b5ad1) w listopadzie 2018 r. W obecnym wniosku zwrócono się do zainteresowanych stron z pytaniem, czy należy kontynuować planowanie. Jeśli wniosek zostanie zatwierdzony, zostanie przedłożony kolejny wniosek ze szczegółowymi informacjami na temat jego wdrożenia. Głosowanie nie rozpoczęło się.
* [Strona społeczności Decred](https://proposals.decred.org/proposals/fb8e6ca361c807168ea0bd6ddbfb7e05896b78f2576daf92f07315e6f8b5cd83), aut. @karamble, proponuje stronę internetową, która łączy wiele źródeł treści związanych z Decred, takich jak artykuły, filmy wideo, podcasty, raporty z wydarzeń i biznesy umożliwiającce płatność DCR. Prototyp został już zbudowany przez @karamble, a propozycja zakłada 6 tys. dolarów na sfinansowanie strony przez 6 miesięcy. Głosowanie zakończyło się zatwierdzeniem 72,5% głosów na "tak", z głosami 33% kwalifikujących się biletów.
* [Integracja Decred na giełdzie IDAX](https://proposals.decred.org/proposals/60adb9c0946482492889e85e9bce05c309665b3438dd85cb1a837df31fbf57fb), aut. acean, poszukuje 1000 DCR, aby dodać parę handlową DCR/BTC do giełdy IDAX z siedzibą w Mongolii. Głosowanie zakończyło się i propozycja została odrzucona z wynikiem 25% głosów wspierających, przy udziale 23,5% uprawnionych biletów.
* [Integracja Decred w Trust Wallet](https://proposals.decred.org/proposals/2ababdea7da2b3d8312a773d477272135a883ed772ba99cdf31eddb5f261d571), aut. @oregonisaac, proponuje włączenie Decred do "całkowicie zdecentralizowanego" Trust Wallet za około $3,300 i $100 miesięcznego wsparcia. Głosowanie nie rozpoczęło się.

Aktywność na platformie Politeia w okresie 1-28 luty:

* 7 nowych wniosków złożonych, 5 wniosków rozpoczęło głosowanie.
* 300 komentarzy na temat propozycji od 46 różnych użytkowników (za kluczami publicznymi).
* 1 006 głosów w górę/w dół odn. komentarzy od 56 różnych użytkowników z prawem głosu (za kluczami publicznymi).
* 748 głosów w górę (70%) i 258 w dół (30%).

Całkowite statystyki na dzień 28 lutego 2019 r:

* 802 komentarze na temat propozycji od 113 różnych użytkowników (za kluczami publicznymi).
* 2.785 głosów w górę/w dół odn. komentarzy 122 od różnych użytkowników z prawem głosu (za kluczami publicznymi).
* 2 336 głosów w górę (80%) i 449 w dół (20%).
* 32 użytkowników, którzy głosowali na komentarze, ale nigdy nie komentowali, i łącznie oddali 374 głosy (13,4% wszystkich głosów).
* Około 238 komentarzy (30%) zostało oddanych przez ich autora.

Dzięki dla @richardred za automatyzację generowania powyższych statystyk.

Rozpoczęła się dyskusja na temat wprowadzenia poprawek do Konstytucji Decred i ratyfikacji nowej wersji za pomocą głosowania przez platformę Politeia. Pierwotnym celem było usunięcie przestarzałych/nieistotnych części i dodanie brakujących części z minimalnymi zmianami. Podczas dyskusji kilka osób zapytało, czy w ogóle potrzebujemy konstytucji, biorąc pod uwagę, że nie jest ona wiążąca. Linki do wszystkich dyskusji i proponowanych zmian są zebrane w [tej kwestii](https://github.com/xaur/decred-issues/issues/107).

Nowe konto [@pi_crumbs](https://twitter.com/pi_crumbs) na Twitterze powiadamia swoich obserwujących, gdy  tworzone lub modyfikowane są propozycje oraz gdy zaczyna lub kończy się głosowanie. Obecnie obsługiwane jest ręcznie przez @richardred, ale omawiana jest jego [automatyzacja](https://github.com/xaur/decred-issues/issues/102).

Kolejne konto o nazwie [@slices_of_pi] (https://twitter.com/slices_of_pi) zamieszcza komentarze na temat aktywności Politei napisane ludzką ręką.

W celu uzyskania bardziej szczegółowych informacji, analizy i komentarza przeczytaj [wydanie 10](https://medium.com/politeia-digest/issue-10-jan-1-feb-18-2018-202cde71a19d) i [wydanie 11](https://medium.com/politeia-digest/issue-11-feb-19-feb-28-2019-46befddb09fe) znakomitego Politeia Digest aut. @richardred, na podstawie których powstało powyższe podsumowanie.

## Sieć

Hashrate: February's hashrate opened at ~230 Ph/s and closed ~300 Ph/s, bottoming at 210 Ph/s and peaking above 420 Ph/s throughout the month. Pool hashrate distribution as of Mar 5: BTC.com 31%, Poolin 27%, F2Pool 18%, UUPool 15%, Luxor 4%, CoinMine 1% and others are 5% per [dcrstats.com](https://dcrstats.com/pow). Pool distribution numbers are approximate and cannot be accurately determined.

Staking: 30-day average ticket price was 111.6 DCR (+2.2) on Mar 1 per dcrstats.com. The price varied between 98.4-124.1 DCR. Locked amount was 4.36-4.56 million DCR, which corresponded to 46.4-48.7% of the available supply.

Ticket price and pool size experienced some volatility in February. 1,265 tickets purchased in a single interval on Feb 11 raised the pool size to ~41,670 tickets and the price to 119.4 DCR in 7 subsequent increases. This was followed by a streak of 10 price reductions down to 98.4 DCR, when the pool briefly dropped below 40K tickets (last time this happened in Oct 2017). At the bottom, a stunning 2,797 tickets were purchased in a single window, out of a maximum possible 2,880. [@ImacallyouJawdy](https://twitter.com/ImacallyouJawdy/status/1098296540290924544) noted that in this window alone 282K DCR or 3% of current supply was locked in tickets. As a result, the ticket price jumped to 124.1 DCR which is a new all time high since the deployment of the new [stake difficulty algorithm](https://github.com/decred/dcps/blob/master/dcp-0001/dcp-0001.mediawiki) in Jul 2017. Ticket pool topped at 42,174 tickets when 48.7% of the DCR supply was locked - a new all time high and +0.7% from previous peak on Jun 7, 2018. Thanks to [charts.dcr.farm](https://charts.dcr.farm/d/000000003/proof-of-stake?orgId=1) for the sharp charts.

Nodes: As of Mar 1 there were 205 public listening nodes and 297 normal nodes per [dcred.eu](https://dcred.eu/nodeStats). Version distribution: v1.5.0 dev builds: 8.6% (+4.3%), v1.4.0 final: 43% (+43%), v1.4.0 dev and rc builds: 7% (-6%), v1.3.0: 23% (-32%), v1.2.0: 10% (-4%), v1.1.2: 4% (-4%), v1.1.0: 2% (-1%).

[Upgrade thresholds](https://voting.decred.org/) for PoW and PoS were met and the consensus vote locked in to start around Mar 14. Thanks to everybody who upgraded their nodes, and also to people who reached out to PoW pool and VSP operators via different channels and asked them to upgrade.

The vote did not start yet but block votes already signal their choices for `fixlnseqlocks` agenda. As of Mar 4 there [were](https://matrix.to/#/!wSdymYrEpBhsWlDJuk:decred.org/$155168912215429iStcp:decred.org) 8,503 Yes and 1 No vote. "Dat contrarian... At least it's proof that the no button works." - @jz.

## Integrations

VSP codenamed "Bravo" was [renamed](https://github.com/decred/dcrwebapi/pull/59) from dcr.stakepool.net to [dcr.blue](https://dcr.blue/).

Exchange integrations:

* [Vertbase](https://www.vertbase.com/) added DCR/USD pair. Vertbase CEO and cofounder Justin joined #general and [answered questions](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$155015221011045eRXdT:decred.org). Among the answers were: Vertbase supports 39 of the 50 U.S. states, is actively working to add GBP/EUR/AUD trading, and uses 3rd party to handle ID verification. An interesting feature of Vertbase is very short duration of custody: they will send tokens directly to your wallet once bank transfer settles.

  > We also require you to provide a wallet address because we don't want to hold nor do we want you to hold your cryptocurrency on our platform. Be your own bank! (@Justin in [#general](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$155017217111507BsAmt:decred.org))

  As of Mar 8, sell orders are not available. See also this [Reddit post](https://www.reddit.com/r/decred/comments/aqkl1p/vertbase_lists_decred_dcr_with_us_dollar_usd/).

* [Lykke](https://www.lykke.com/) [added](https://twitter.com/lykke/status/1095352586545319937) DCR pairs with BTC and USD.
* [ChainRift](https://www.chainrift.com/) integrated DCR.
* [Livecoin](https://www.livecoin.net/) [added](https://twitter.com/livecoin_net/status/1098151449786118144) DCR pairs with BTC, ETH and USD.
* [BitMesh](https://bitmesh.com/) [launched](https://www.reddit.com/r/decred/comments/av8a69/bitmesh_has_launched_dcr_and_opened_dcrbtc/) DCR pairs with BTC and USDT.

Warning: the authors of Decred Journal have no idea about the trustworthiness of any of the exchanges above. Please do your own research [before](https://twitter.com/yeppoon/status/1095857386709893120) trusting your personal information or assets to any entity.

## Adoption

CoinFund [announced](https://blog.coinfund.io/announcing-grassfed-network-and-decred-staking-pool-with-placeholder-55a32a312710) Grassfed Network, an initiative that uses 'generalized mining' to directly participate in decentralized networks. The story was featured in [CoinDesk](https://www.coindesk.com/these-cryptofunds-say-generalized-mining-is-the-new-way-to-invest).

Any activity that is compensated with on-protocol rewards denominated in network assets can be seen as [generalized mining](https://grassfed.network/mining/). Following this approach investors can directly engage in the networks and generate additional returns, compared to just speculating on the value of assets.

Per the announcement, CoinFund partnered with [Placeholder](https://www.placeholder.vc/) who plans to delegate its own voting tickets to the [Decred VSP](https://dcr.grassfed.network) launched in January. This plan was voiced earlier by Joel Monegro and Chris Burniske during the [panel](https://www.youtube.com/watch?v=tkllaH0Y0ng) at Texas Bitcoin Conference 2018. [CoinFund](https://coinfund.io/) is a cryptoasset-focused investment and research firm founded in 2015 and based in New York, USA.

## Outreach

In February, @Dustorf proposed his plans for [marketing](https://proposals.decred.org/proposals/c84a76685e4437a15760033725044a15ad832f68f9d123eb837337060a09f86e) and [events](https://proposals.decred.org/proposals/d3e7f159b9680c059a3d4b398de2c8f6627108f28b7d61a3f10397acb4b5e509) for the remainder of 2019 and these were passed by stakeholder voting. This is an exciting development that further decentralizes Decred by shifting more direct control over spending to the stakeholders. There was vigorous discussion and many good questions, but the proposals were approved by 83% and 89% of tickets that voted.

With an approved budget, work began in earnest on the scope of the proposals. Planning is underway on NYC Blockchain Week, which coincides with Consensus. More information should be announced within two weeks on these plans.

The first podcast is underway and scheduled to deliver in March. It will feature Decred Jesus, who will provide a colorful overview discussion of Decred as seen from the ground. Work on the website is underway, with architecture, copy-writing and video scripting already begun.

The Decred Assembly and the newsletter are tactics we hope to deliver by the end of this month.

February update from Ditto:

* Media trained 5 Decred community members.
* Secured media coverage: 15-minute [interview](https://blocktv.com/watch/2019-02-20/5c6d6a2be03e3-chain-breakers-promoting-constant-disruption-) between @jy-p and BlockTV, a feature [article](https://www.forbes.com/sites/leslieankney/2019/02/04/no-more-trading-or-listing-fees-decred-releases-new-dex-proposal/) for the DEX proposal in Forbes, a feature [article](https://breakermag.com/as-decred-turns-three-its-still-set-on-real-decentralization/) in honor of Decred's 3rd anniversary in Breaker Mag, an [article](https://www.theblockcrypto.com/2019/02/13/they-asked-us-for-3-million-an-inside-look-into-getting-listed-on-a-crypto-exchange/) on the Vertbase listing in The Block Crypto featuring quotes by @jz. The journalist, Frank Chaparro, said the story was very popular on Twitter and also internally at The Block.
* Facilitated 2 interviews with crypto media outlets.
* Worked with the community to create a repository of media-friendly images that we can share with reporters to add visuals to stories about Decred.
* Helped plan the logistics and content for the event hosted by Decred and OKCoin in San Francisco. Worked with Dustin and OKCoin to draft the Eventbrite copy, coordinate with OKCoin, develop the agenda for the event, and draft a press release.
* Put together a plan to position Decred as a superior store of value among a variety of channels, including initiating long-term conversations with select top tier mainstream reporters.
* Worked with Dustin on a master six-month marketing and communications plan spanning PR, events, content, etc. As part of this strategy, we aim to build Decred's legitimacy and credibility among institutional investors. That entails thinking beyond media relations to span other disciplines as well: owned content, Twitter, influencers, events, etc.

For more detail see Ditto's biweekly updates on [Feb 4](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154930816328395IaXDr:decred.org) and [Feb 15](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$155026927613161McEtC:decred.org).

Discussions:

* Long [chat](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org/$15498862365982zjzwP:decred.org) about perception and framing was triggered by a question whether to use word "bug" in public messaging for 1.4 release.
* [Opinions](https://www.reddit.com/r/decred/comments/ans7lg/what_do_we_think_of_converting_decreds_ticker/) on changing Decred's ticket from DCR to CRED.
* [Criticism](https://www.reddit.com/r/decred/comments/asg6kf/update_on_the_decred_14_release/) of the use of "lifeless corporate" style in announcements.

## Events

Attended:

* [TabConf](https://tabconf.com/) in Atlanta, USA. @joshuam [noted](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15497319564677Cmutw:decred.org): "Tabconf was awesome. Extremely engaged audience - best questions I have received at a conference to date".
* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) in Sao Paulo, Brazil. About 60,000 people passed through the event which was running 24 hours a day for 6 days. Decred was the only cryptocurrency participating officially and with an exclusive space to present lectures and classes. All Brazilian developer contractors attended and presented a total of 6 talks and 3 [workshops](https://twitter.com/matheusd_tech/status/1096434162091937792). @jy-p presented [Cryptocurrency Security and Adaptability](https://www.youtube.com/watch?v=SMiHku6GGmI). There were a few problems like Decred's zone moved and reduced (happened to almost all participants) and poor organization of translations - all taken into account for future planning. See [full report](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155200602520229ditLj:decred.org) by @emiliomann and [notes](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155197226472913itWWu:matrix.org) by @matheusd. ([photo](https://twitter.com/matheusd_tech/status/1095836141104828416))
* Love Night in Ghana. Organized by @George Pro. Since about 90% of participants knew about Bitcoin, presenters could skip the basics and highlight unique features of Decred. One popular question was where DCR can be exchanged to local currency. ([photos](https://twitter.com/deCRED_Ghana/status/1096714039978266624))
* [How To Keep Your Crypto Secure](https://www.meetup.com/Decred-Australia/events/258211699/) in Melbourne, Australia. Australia's cryptocurrency enthusiasts discussed best security practices and Decred's security standards. @Zohand [noted](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15504942691141LtOxa:decred.org): "Feedback was awesome, and the guys from coinstop and CTRL want to run the event again in a couple of months.". ([photos](https://twitter.com/DecredAustralia/status/1097478053763018752))
* [Decred in 30 minutes](https://www.eventbrite.com/e/decred-en-30-minutos-tickets-55764142050) in Mexico City, Mexico. @elian [reported](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15517155592047249xtYGy:matrix.org): "It was the first meetup where everyone knew about Decred quite well, we were 7 in total. The presentation went faster because attendees knew most of the fundamental content in advance so we went to discuss more complex issues like what are the challenges to decentralized governance, best way to stake tickets and future developments that are happening in the project like LN, payments integration and the most recent events, marketing and community proposals in Politeia. Was very nice to meet proper DCR enthusiasts in Mexico. (...) I think we are far from seeing cc as MoE in Mexico but definitely the space is moving fast. At the moment there are more Mexicans in contact with crypto than with the stocks markets in the country, this is a very good indicator.". ([photos](https://twitter.com/DecredESP/status/1102594478664232960))
* Talk in UAEM University in Ecatepec, Mexico. @elian [shared](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$1551994219193770GeoIk:matrix.org): "I spoke about the history of money, the Internet, Bitcoin's blockchain, Decred's hybrid blockchain and how to work in the cryptocurrency & blockchain industries. They were fascinated by the innovation of cryptocurrencies and blockchain, both students and teachers. The audience was mainly composed by computer science students. The main questions went around what is money, how to value cryptocurrencies and what are the potential work opportunities for fresh grads in the industry. (...) Doing talks in universities is a big deal for me because I know that the next generation of devs, lawyers, accountants, etc, that will be working on the industry is there and they are eager to know more about what opportunities this industry brings. Teachers were very excited to have this subjects presented to their students because is not easy to get such high tech talks to universities that are not in the centre of the city.".
* [Decred Meetup](https://www.eventbrite.com/e/decred-meet-up-tickets-57073786231) in Winneba, Ghana. Organized by @George Pro, who [noted](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155133397211500yxtpJ:decred.org): "Our first meetup in Ghana was successful. We took our time to explain to the participants how to stake DCR, how to get DCR (Coinomi process), using it as remittances, wallet set up, speed and privacy among others.". ([photos](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$155133397211500yxtpJ:decred.org))
* Talk at Qingdao University in Qingdao, China. [@wanbihou](https://twitter.com/wanbihou) talked about Decred's community governance model and the upcoming on-chain consensus vote. "The students were very enthusiastic!". ([photos](https://twitter.com/wanbihou/status/1101131545010556928))

Upcoming:

* [The Next 10 Years: Crypto Boom, Bust, or Buidl?](https://www.eventbrite.com/e/decred-okcoin-present-the-next-10-years-crypto-boom-bust-or-buidl-tickets-57549671617) in San Francisco, USA on Mar 12. Organized by Decred and OKCoin. CEO of OKCoin Tim Byun, Decred's Jake Yocom-Piatt, Chris Burniske and Alex Evans of Placeholder will talk about Decred and the future of cryptocurrencies.
* [Restoring Trust through Blockchain Governance](https://www.meetup.com/DecredCanada/events/259126224/) in Toronto, Canada on Mar 16.
* [Crypto Conference 2019](https://crypto-conference.com/) in Berlin, Germany on Mar 27. The event is part of [Berlin Blockchain Week](https://www.berlin-blockchain-week.com/). @karamble will talk "Adaptability in Digital Currencies".
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) in Guadalajara, Mexico on Apr 22-26. Contact @elian for details.

As noted in Governance above, stakeholders approved a $200K budget for [2019 events](https://proposals.decred.org/proposals/d3e7f159b9680c059a3d4b398de2c8f6627108f28b7d61a3f10397acb4b5e509), which includes a strong presence at 3 large scale events and attendance at a number of smaller events.

## Media

Selected articles:

* Decred evaluation by TokenGazer (Chinese, [qq.com](https://mp.weixin.qq.com/s/7rMaTYXIhIpO37qiIvJX_A), _missed in Jan issue_) - Decred was rated 4.2
* Which one is the best cryptocurrency next to Bitcoin? answer by Pavel Svitek ([quora.com](https://www.quora.com/Which-one-is-the-best-cryptocurrency-next-to-bitcoin/answer/Pavel-Svitek)) - thanks to Pavel for presenting Decred on Quora
* No More Trading or Listing Fees? Decred Releases New DEX Proposal by Leslie Ankney ([forbes.com](https://www.forbes.com/sites/leslieankney/2019/02/04/no-more-trading-or-listing-fees-decred-releases-new-dex-proposal/))
* How Long Will Crypto Winter Last? We Asked Three Experts by Julia Herbst ([breakermag.com](https://breakermag.com/what-the-longest-ever-bear-market-means-for-crypto/))
* As Decred Turns Three, It's Still Set on Real Decentralization by David Z. Morris ([breakermag.com](https://breakermag.com/as-decred-turns-three-its-still-set-on-real-decentralization/))
* Decred Founder Proposes Building DEX as Alternative to Binance (Interview) by Liam Kelly ([cryptoslate.com](https://cryptoslate.com/decred-founder-proposes-dex-binance-interview/))
* "They asked us for $3 million": an inside look into getting listed on a crypto exchange by Frank Chaparro ([theblockcrypto.com](https://www.theblockcrypto.com/2019/02/13/they-asked-us-for-3-million-an-inside-look-into-getting-listed-on-a-crypto-exchange/))
* Cryptonetwork Governance as Capital by Joel Monegro ([placeholder.vc](https://www.placeholder.vc/blog/2019/2/19/cryptonetwork-governance-as-capital))
* Using Governance to Decide the Future: Is Decred (DCR) Going to Build a Decentralized Exchange? by @richardred ([investinblockchain.com](https://www.investinblockchain.com/is-decred-dcr-building-decentralized-exchange/), also in Chinese at [0xzx.com](https://0xzx.com/2019022708166553.html))
* Decred mentioned in [Forbes](https://www.forbes.com/sites/samantharadocchia/2019/02/05/everything-about-the-digital-nomad-lifestyle-sounds-great-except-the-us-tax-system/) and [Breaker Mag](https://breakermag.com/bruce-schneier-is-right-about-blockchains-biggest-flaw-and-completely-wrong-about-its-longterm-significance/) stories.

Videos:

* Decred AMA TruStory - Preethi Kasireddy chats with Isaac J and Matheus of Decred to learn more about the hybrid proof of work/proof of stake consensus mechanism and their governance model ([youtube](https://www.youtube.com/watch?v=OKdaa630YDk))
* Cryptocurrency Security and Adaptability - talk by @jy-p at Campus Party Brazil ([youtube](https://www.youtube.com/watch?v=SMiHku6GGmI))
* The Potential of Decentralization - interview with @jy-p for BlockTV ([blocktv.com](https://blocktv.com/watch/2019-02-20/5c6d6a2be03e3-chain-breakers-promoting-constant-disruption-))
* Mentioned by Chris DeRose in an [interview](https://www.youtube.com/watch?v=W1tbPQOMxH8&t=3790) to Crypto Insider

Audio:

* ITK Crypto #8 - Tom White and Crypto SI speak to @kozel about crypto governance ([youtube](https://www.youtube.com/watch?v=H-qZBsQY5BM))
* Murad Mahmudov and Aleks Svetski talk about Bitcoin, Lightning and the current market outlook. "So I hope my Bitcoin ultra maximalist friends don't hear this but..." ([podplayer.net](http://podplayer.net/?id=64230840), Decred part starts at [1:36:45](http://podplayer.net/?id=64230840&t=5805))

Translations:

* Decred Journal - January 2019 [in Chinese](https://www.jianshu.com/p/097265621ef6) by @guang (also Dominic, Hugo and Jill), [in Spanish](https://medium.com/@decred_es/revista-decred-enero-2019-549e2b051f5a) by @elian. Thank you!

## Community

Community stats as of Mar 1-2:

* Twitter followers: 39,797 (+19)
* Reddit subscribers: 9,365 (+35)
* Matrix users: 266 (+19)
* Slack users: 6,581 (+52)
* Discord users: 2,101, verified to post: 131
* Telegram users: 4,272 (-231)
* YouTube subscribers: 3,746 (-6)
* Facebook followers: 3,141 (+9), likes: 2,896 (+5)
* LinkedIn followers: Decred page 483 (+17), Politeia page 29 (+2)
* GitHub dcrd stars: 474 (+6), forks: 1,237 (+16)

Telegram communities: Chinese 866 (+53), Italian 160 (+28), Portuguese 642 (+100), Spanish 73 (+11).

Chinese community was pretty active in Feb:

* started a [#chinese](https://matrix.to/#/!nUWpVrwhlJFyLuMlGw:decred.org) room in Matrix
* Yin Guochao continued to write about Decred: one piece about [dcrtime](https://mp.weixin.qq.com/s/ks48Piu3s2zy4btZW0kBDQ) and another about [atomic swaps](https://mp.weixin.qq.com/s/Lgem_BqFBnLUsY7AzC5x_w)
* Dominic did a [intro](https://twitter.com/wanbihou/status/1101122114118184961) to blockchain and Decred in a university to some students
* article by Yin triggered another community member to [write more](https://teakki.com/p/5c774a9ab1029f607605bc76) about dcrtime and create a [web UI](http://www.ibitlin.com/dcrtool#/dcrtime) for timestamping files and raw text (UI for dcrtime is tracked in [this issue](https://github.com/xaur/decred-issues/issues/9)).

Comm systems news:

* non-English chat rooms were renamed after languages used in them for consistency, unused rooms were removed. [#chinese](https://matrix.to/#/!nUWpVrwhlJFyLuMlGw:decred.org), [#portuguese](https://matrix.to/#/!FBtUquQLhAvHeBIkac:decred.org), [#russian](https://matrix.to/#/!TQzfaYsKyxAqQDZQeX:decred.org) and [#spanish](https://matrix.to/#/!pkeRzinGCRtjIIhAAK:decred.org) are now available in Matrix.
* [Riot](https://riot.im/app/#/room/#general:decred.org) client was [upgraded](https://medium.com/@RiotChat/the-big-1-0-68fa7c6050be) to version 1.0 with a reworked UI.

Another Reddit thread was [deleted](https://www.reddit.com/r/decred/comments/an4b6z/forbes_no_more_trading_or_listing_fees_decred/) after receiving some discussion. Moderators have no power to forbid this destruction of community knowledge, except the workaround to [resubmit](https://www.reddit.com/r/decred/comments/ar29jd/forbes_no_more_trading_or_listing_fees_decred/) the deleted thread. Ideas for more persistent Reddit-like forum are collected in [this issue](https://github.com/xaur/decred-issues/issues/38).

"Decred's community spaces - a crude analogy" [post](https://www.reddit.com/r/decred/comments/api7e7/decreds_community_spaces_a_crude_analogy/) by @richardred compares multiple comm platforms used by the Decred community. The follow-up discussion noted problems of keeping up with chats, the importance of having a vibrant Reddit community, and issues with proposal discussions outside Politeia.

## Markets

In February DCR was trading between USD 14.97-18.28 / BTC 0.0042-0.0048. The average daily rate was $16.51.

## Relevant External

A [study](https://medium.com/@MoneroCrusher/analysis-more-than-85-of-the-current-monero-hashrate-is-asics-and-each-machine-is-doing-128-kh-s-f39e3dca7d78) of Monero nonces documented differing patterns in the nonce distribution when ASICs were mining on the network, it considers the methods ASIC miners may take to disguise their presence and how they can be detected. The study speculates that 85% of the Monero hashrate comes from ASICs at time of writing.

A counterfeiting vulnerability was [discovered](https://z.cash/blog/zcash-counterfeiting-vulnerability-successfully-remediated/) in Zcash in early 2018. "This vulnerability is so subtle that it evaded years of analysis by expert cryptographers focused on zero-knowledge proving systems and zk-SNARKs.". It was silently patched with the Sapling network upgrade that occurred on Oct 28, 2018, and this [post](https://z.cash/blog/zcash-counterfeiting-vulnerability-successfully-remediated/) on Feb 5 explained how the vulnerability had been dealt with within Zcash and how other affected coins (like Horizen and Komodo) were notified. The nature of Zcash cryptography is such that it is difficult to determine if any ZEC was counterfeited while the vulnerability was present. The Zcash team reporting on the bug believes it had not been exploited because "discovery of the vulnerability would have required a high level of technical and cryptographic sophistication that very few people possess."

A Grin developer published a forum [post](https://www.grin-forum.org/t/solved-early-disappointments/3682) expressing disappointment that a request for donations to fund one of the developers had not been filled after two weeks of the network being online - and threatening to take 20% of the block rewards to fund development. After the news spread, the [campaign](https://grin-tech.org/yeastplume) quickly raised EUR 67,580, surpassing the EUR 55,000 target. As Breaker Mag [noted](https://breakermag.com/as-decred-turns-three-its-still-set-on-real-decentralization/), Grin "attracted [tens of millions of dollars](https://www.coindesk.com/grin-launch-crypto-interest-from-deep-pocketed-investors) in mining investment, but had some trouble raising a mere $62,000 to pay its lead developer for six months".

Ethereum holders are holding another [signaling carbonvote](http://www.progpowcarbonvote.com/) about whether they want to change mining algorithm to ProgPoW. The vote started with strong [opposition](https://www.trustnodes.com/2019/02/14/98-of-ethereum-vote-against-progpow) to the change (98% No), but later flipped to strong support (94% Yes) as of Mar 4 (with 3% of circulating ETH having voted). While carbonvote has no official place in Ethereum's governance, the method is being used because:

> We have noticed a lot of trolling and shills on both sides of the debates from anonymous accounts on forums, youtube, telegram, gitter, reddit and twitter. There is no way to know if these accounts are real people who actually have economic stakes in ethereum, or are simply fake troll or shill accounts funded by one side of the debate.

Tezos started [voting](https://blog.nomadic-labs.com/athens-proposals-injected.html) for the first [amendment](https://blog.nomadic-labs.com/athens-our-proposals-for-the-first-voted-amendment.html) to its protocol on Feb 25 ([simple guide](https://medium.com/tezos-spotlight/tezos-the-first-amendment-a-laymans-guide-7424ef1d3e13), [detailed guide](https://medium.com/tezos/amending-tezos-b77949d97e1e) to amendment process). The amendment process has 4 phases, each lasting 8 "cycles" (a cycle lasts around 3 days, so each phase lasts for around 24 days). In the first phase bakers submit and upvote proposals. There are 2 proposals being evaluated now in the first phase, they both increase the gas limit but one also decreases the minimum "roll size" (amount of XTZ required to be a baker). It is interesting to note that Kialo is being [used](https://www.kialo.com/tezos-protocol-amendment-1-25295) by some Tezos community members to discuss these proposals. When the first phase ends, the most upvoted proposal will progress to phase 2, where it must be approved by at least 80% of bakers. If the criteria are met, this is followed by a testing phase in which a testnet fork with the changes applied is created and runs for 48 hours (a further testnet matching the proposal may be run for the rest of this phase to allow further testing). After the testing phase, bakers vote on whether the changes should be activated, with an 80% supermajority required. After this 4th phase the changes are activated (or not) and the cycle begins again with new proposals.

Dash v0.13.1 was [released](https://blog.dash.org/dash-core-v0-13-1-release-5d6e06031ba3) on Feb 8 to "accelerate adoption of the Dash Core v0.13". Dash Core [v0.13](https://blog.dash.org/dash-core-v0-13-on-mainnet-dc9609b0f6f9) was intended to activate [DIP3](https://github.com/dashpay/dips/blob/master/dip-0003.md) but it had an activation threshold of 80% blocks signaling support from the PoW miners and masternodes in a 7 day window before activation would begin. After failing to meet these criteria for around 24 days, it was decided that the criteria are too stringent and that the requirement for masternodes to signal could be dropped. When enough PoW miners adopt v0.13.1 the change would activate one week later (it [activated](https://blog.dash.org/product-update-february-21-2019-5f067b62df00) around Feb 26).

0x protocol (ZRX) held its [first](https://blog.0xproject.com/how-to-participate-in-the-zeip-23-vote-eaa861298033) token holder vote between Feb 18-25. The vote was to approve [ZEIP-23](https://blog.0xproject.com/zeip-23-trade-bundles-of-assets-fe69eb3ed960) and enable "trade bundles of assets". The proposal was [approved](https://0x.org/vote) with 99% Yes votes by 5,061,033 ZRX (0.86% of the circulating supply).

The NEM Foundation's funding proposal [started](https://forum.nem.io/t/nem-foundation-update-vote-for-funding-proposal-2019/22007) voting on Feb 15 and voting was open for 5 days. The funding proposal [passed](https://forum.nem.io/t/vote-for-nem-foundation-funding-proposal-2019-approved-by-the-community/22060) with 90% Yes votes and 10% No votes - with votes from 4.56% of the "Proof of Importance" (NEM's way of weighting holders' influence). The vote was conducted on the basis that a 65% supermajority of Yes votes was required, and at least 3% of the network's POI must vote Yes as a quorum requirement. Voting was conducted from within the NEM wallet by sending 0 XEM transactions to a Yes or No address. Another concurrent proposal to fund "NEM Labs" was also successful, with a similar level of participation and 98.8% approval. The NEM Foundation proposal asked for $8 million in XEM (figure is surprisingly hard to find, could only be found in a [google doc presentation](https://docs.google.com/presentation/d/1nMR_1ajVcpdGW7g8I0p7ZGh88tZ1SL5RzG5TsLW6Qnk/edit#slide=id.p2)), while the NEM Labs proposal asked for $3.27 million.

The Aragon Transparency Report for Q4 2018 was [released](https://blog.aragon.org/aragon-q4-2018-transparency-report/). This report presents a detailed breakdown of spending related to the project. The total spent in Q4 2018 was ~€1,055,484.43 or equivalent in cryptocurrency, with €268K on salaries, €330K on payments to service providers, €45K on sponsoring/tickets for events, €63K on hosting the AraCon conference and €260K on [Nest](https://github.com/aragon/nest) teams (a grants program). This report also describes financial [hedging](https://twitter.com/AragonProject/status/1067349802365739008) steps which have been taken by Aragon Association - exchanging some of the ETH raised during the ICO to buy other assets.

The blacklist issued by the EOS Core Arbitration Forum (ECAF) in Jun 2018 was allowed to [lapse](https://medium.com/@eos42/proposed-solution-for-a-broken-blacklist-ce1c18bdf81c) when a new Block Producer was rotated in which had not configured the blacklist. This allowed one of the blacklisted addresses to move over 2 million EOS. The lapse occurred because the blacklist has been implemented as a list of addresses from which block producers will not process transactions, with each block producer being responsible for maintaining the blacklist manually. If only one top 21 BP does not have an updated blacklist, blacklisted accounts are vulnerable to being emptied. One solution that has been suggested is to "null the keys" until a decision has been made about what to do with the frozen funds. What to do with the blacklisted funds is already an issue for EOS, and the ECAF itself may be disbanded if an open referendum to "Delete the ECAF" passes (currently on 99% Yes with 2.4% of EOS having voted).

Binance is [launching](https://www.theblockcrypto.com/2019/02/07/binance-moves-away-from-ethereum-as-it-prepares-to-launch-dex/) its DEX based on Cosmos' Tendermint protocol and DPoS. The listing fee will "probably be close to $100,000" to "reduce the number of spam or scam projects". In contrast, Decred's DEX design has no listing fees and doesn't require an extra blockchain for its operation.

Canadian exchange QuadrigaCX [owes](https://www.coindesk.com/quadriga-creditor-protection-filing) its customers $190 million. The funds reportedly [cannot be accessed](https://www.coindesk.com/quadrigacx-crypto-exchange-users-say-they-still-cant-get-their-money-out) after its founder died, who had sole control or knowledge of exchange's cold storage solution. Another $500K in BTC were locked "by mistake" per [this story](https://www.coindesk.com/quadriga-inadvertently-sent-btc-to-dead-ceos-cold-wallet-ey-report). The never ending trail of failures by centralized exchanges shows just how challenging the custody of cryptocurrencies is.

Medium showed its power again by [suspending](https://archive.today/iKQlv) the account that [posted](https://medium.com/@zeroresearchproof/quadrigacx-chain-analysis-report-pt-1-bitcoin-wallets-19d3a375d389) chain analysis of QuadrigaCX wallets. Luckily, someone made a [snapshot](https://archive.today/xsztt). The suspension hides all account's content and is implemented as a redirect to a same-for-all page that says "This page is unavailable" and does not state the reason. Medium is a powerful platform, but at its core is a centralized service that can lock in data of those who don't make backups. Earlier behavior like this triggered a [discussion](https://github.com/xaur/decred-issues/issues/70) about migrating from Medium or treating it as just a mirror.

Android malware was [discovered](https://www.welivesecurity.com/2019/02/08/first-clipper-malware-google-play/) on Google Play Store that changes cryptocurrency address in the clipboard. Always double check the address before sending.

## About This Issue

This is the 11th issue of Decred Journal. Index of all issues, mirrors and translations is available [here](https://xaur.github.io/decred-news/).

Most information from third parties is relayed directly from source after a minimal sanity check. The authors of Decred Journal have no ability to verify all claims. Please beware of scams and do your own research.

Your feedback and contributions are welcome on Reddit, [GitHub](https://github.com/xaur/decred-news/issues) and [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Credits (alphabetical order): bee, davecgh, degeri, Dustorf, emiliomann, guang, jholdstock, liz_bagot, matheusd, raedah, sambiohazard. Special thanks to richardred for extensive review of the crypto governance space, and to saender for abstract art images.
