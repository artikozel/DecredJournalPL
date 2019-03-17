# Decred Journal – Styczeń 2019

![abstract art](../img/journal-201901-384.jpg "Out of the abstract to more objective future")

Decred dynamicznie rozpoczął rok 2019 miesiącem, w którym ukazały się ważne wydania nowych wersji oprogramowania i znaczące zmiany w innych częściach projektu.

Została wydana [nowa wersja oprogramowania](https://github.com/decred/decred-binaries/releases/tag/v1.4.0) dla węzłów i portfeli (v1.4.0), co, między innymi, zainicjuje głosowanie nad zasadami konsensusu, a zatem zaleca się terminową aktualizację.

Portfel mobilny Dcrandroid, który wykorzystuje tryb peer to peer SPV dla Decred został wydany (v1.0) i jest dostępny w [Google Play Store](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet).

Na platformie Politeia opublikowany został [wniosek o przedstawienie propozycji na zdecentralizowaną infrastrukturę giełdy wymian](https://proposals.decred.org/proposals/5431da8ff4eda8cdbf8f4f2e08566ffa573464b97ef6d6bae78e749f27800d3a) opisaną przez @jy-p w poprzednim wpisie na blogu.

Zakończony został proces konsultacji społecznościowych w celu zdefiniowania [podstawowego przekazu Decred](https://pastebin.com/E5L6u2RV), tagline wybrany jako część tej wiadomości to: "Decred: Bezpieczny. Adaptacyjny. Samofinansujący się". Działania w zakresie nawiązywania kontaktów przeniosły się na planowanie działań w ciągu bieżącego roku, a wstępne propozycje dotyczące wydatków na [wydarzenia](https://www.reddit.com/r/decred/comments/anhh8n/proposal_to_get_events_spending_approved_via/) i [marketing](https://www.reddit.com/r/decred/comments/aolr79/politeia_proposal_to_fund_marketing_ops_for_2019/) zostały opublikowane na czatach i Reddicie.

To wydanie Decred Journal obejmuje również początek lutego, ponieważ w pierwszym tygodniu lutego miało miejsce kilka ważnych wydarzeń i uznano, że warto było by je uwzględnić przed lutowym numerem.

## Aktualizacja do wersji 1.4.0 i głosowanie konsensusowe

Oprogramowanie v1.4.0 dla węzła i portfela zostały wydane. Pełne informacje o wydaniu i pliki do pobrania znajdują się [na GitHub](https://github.com/decred/decred-binaries/releases/tag/v1.4.0). Jak zawsze, upewnijcie się, że [zweryfikowaliście pobierane pliki](https://docs.decred.org/advanced/verifying-binaries/).

Wydanie niesie ze sobą znaczące ulepszenia, wraz z proponowaną zmianą zasad konsensusu, która naprawia błąd przy wsparciu Lightning Network. Operatorom węzłów zaleca się aktualizację, aby pomóc sieci osiągnąć próg aktualizacji. Po aktualizacji wyborcy powinni ustawić swoje [preferencje głosowania](https://docs.decred.org/governance/how-to-vote/). Postęp aktualizacji można śledzić na stronie [voting.decred.org](https://voting.decred.org/).

Szczegóły techniczne zmiany konsensusu można znaleźć w [DCP0004](https://github.com/decred/dcps/blob/master/dcp-0004/dcp-0004.mediawiki) i [poście](https://matheusd.com/post/dcp0004-and-hardforks/) autorstwa @matheusd.

Z wyjątkiem porządku obrad głosowania, wersja ostateczna v1.4.0 nie zawiera innych istotnych zmian od czasu wydania "Release Candidate 2", które zostało opisane w [grudniowym wydaniu Decred Journal](https://xaur.github.io/decred-news/journal/201812.html).

## Rozwój

[dcrd](https://github.com/decred/dcrd): odkryto [problem](https://github.com/decred/dcrd/issues/1568) w v1.4.0 RC1. Duża zmiana w zestawie semantyki UTXO przypadkowo naprawiła błąd w zasadach konsensusu. Stare, nieprawidłowe zachowanie zostało [zachowane](https://github.com/decred/dcrd/pull/1570) do czasu, aż będzie można odbyć głosowanie w celu skorygowania go poprzez zasady konsensusu. Dziękujemy wszystkim, którzy pomogli odkryć i naprawić błąd w RC1.

Kod do głosowania konsensuowego został [ukończony](https://github.com/decred/dcrd/pull/1579) i zawarty w ostatecznej wersji [v1.4.0](https://github.com/decred/decred-binaries/releases/tag/v1.4.0). Poprawka i głosowanie były priorytetowe, ponieważ są wymagane do poprawnego działania Lightning Network. [DCP004](https://github.com/decred/dcps/blob/master/dcp-0004/dcp-0004.mediawiki) (Decred Change Proposal) szczegółowo wyjaśnia zmianę i przypomina o użytecznych zastosowaniach zamków względnych poza LN. Efektem ubocznym tej pracy była [refaktoryzacja](https://github.com/decred/dcrd/pull/1583) i wzmocnienie testów w tym obszarze. @matheusd opublikował [wpis na blogu](https://matheusd.com/post/dcp0004-and-hardforks/), który zawiera przegląd błędu oraz opis sposobu jego znalezienia i odpowiedzi na niego.

Rozpoczęła się [dyskusja](https://github.com/decred/dcrd/issues/1593) o tym, jak jeszcze bardziej ulepszyć algorytm trudności stakingu poprzez usunięcie oscylacji, co może sprawić, że cena biletu będzie jeszcze bardziej płynna.

[Decrediton](https://github.com/decred/decrediton): poprawki błędów i przygotowanie do wydania v1.4.0.

Funkcja określania opcji konfiguracyjnych jako argumentów z wiersza polecenia została [scalona](https://github.com/decred/decrediton/pull/1975) do gałęzi master projektu.

[Politeia](https://github.com/decred/politeia): włączono funkcję przeglądania poprzednich wersji propozycji.

W toku: wyskakujące okienko w trakcie procesu wdrażania zostało [zastąpione](https://github.com/decred/politeiagui/pull/986) odpowiednimi linkami do dokumentacji. Dziękujemy użytkownikowi Lemonkabir za odkrycie kilku [problemów](https://github.com/decred/politeia/issues/647) z [zabezpieczeniami](https://github.com/decred/politeia/issues/650). [Warstwa pamięci podręcznej](https://github.com/decred/politeia/pull/660) weszła w fazę przeglądu.

Dyskusje:

* Zidentyfikowano brakującą [funkcję administratorską](https://github.com/decred/politeia/issues/662) do cenzurowania publicznych propozycji: musi istnieć sposób na usunięcie publicznej propozycji, która została zredagowana w taki sposób, aby przedstawiać obraźliwe treści. W przeciwnym wypadku administratorzy musieliby przeglądać wszystkie zmiany, zanim znajdą się one na stronie z propozycjami.
* [Zautomatyzowane testy typu end-to-end](https://github.com/decred/politeiagui/issues/976) i [lista kontrolna QA](https://github.com/decred/politeiagui/issues/977) w dla większych zmian.
* Duża [refaktoryzacja](https://github.com/decred/politeiagui/issues/990) kodu frontendowego w celu rozwiązania problemów związanych ze złożonością, wydajnością i produktywnością deweloperską. Pierwszym proponowanym [rozwiązaniem](https://github.com/decred/politeiagui/issues/990#issuecomment-454535696) jest wykorzystanie GraphQL.

[dcrandroid](https://github.com/decred/dcrandroid): wydano ostateczną wersję 1.0! Pobierz go w Google Play Store dla portfeli [mainnetowych](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet) lub [testnetowych](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.testnet). Kredyty testowe można otrzymać za pośrednictwem [kranu](http://faucet.decred.org/). Mile widziane są komentarze i opinie [na Reddit](https://www.reddit.com/r/decred/comments/am7j40/decred_wallet_for_android_v10_release/) i zgłoszenia błędów [na GitHub](http://github.com/decred/dcrandroid/issues).

Od wersji release candidate 2, wersja ostateczna dodała wyświetlanie postępu synchronizacji, brak powiadomienia wifi, nowy ekran startowy i drobne poprawki błędów - pełna lista zmian [tutaj](https://github.com/decred/dcrandroid/compare/v1.0.0-rc2...v1.0.0-rc3). Gratulacje dla zespołu dcrandroid!

[dcrios](https://github.com/raedahgroup/dcrios): podgląd jest [dostępny](https://testflight.apple.com/join/dvq51tCh) na Apple TestFlight.

[dcrdata](https://github.com/decred/dcrdata): dokonuje się postęp w [nowym wyglądzie strony głównej](https://github.com/decred/dcrdata/pull/921). Wartości na stronie głównej są teraz [aktualizowane automatycznie](https://github.com/decred/dcrdata/pull/961) po znalezieniu nowego bloku. Dodano [monitorowanie kursu wymiany](https://github.com/decred/dcrdata/pull/951) do backendu, które umożliwia wyświetlanie wartości USD na interfejsie użytkownika.  Na subdomenach `explorer` i `mainnet` jest teraz wymuszane HTTPS. ([dyskusja](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$154818146313660CWvZy:decred.org)).

Nowy wygląd strony głównej, który zawiera kurs wymiany, nowe odsłony tabel adresowych, ulepszone wykresy i optymalizację prędkości są [dostępne](https://twitter.com/decredexplorer/status/1093182831487053825) w wersji beta v4 na stronie [beta.dcrdata.org](https://beta.dcrdata.org/). Szczegółowe informacje o wydaniu zostaną skompilowane wraz z kandydatem do wydania.

Od strony deweloperskiej: @buck54321 [niszczy](https://github.com/decred/dcrdata/pull/915) imperatywne zapytania jQuery. Zespół przygotowuje stress testing API Insight _(nazywają to testem tortur, auć)_.

[Ticket splitting](https://github.com/matheusd/dcr-split-ticket-matcher): wewnętrzne ulepszenia kodu, wstępne prace nad integracją z Decreditonem. Stworzono [stronę monitorującą](https://mainnet-split-tickets.matheusd.com/), która pokazuje aktywne sesje dzielenia biletów ze wszystkich VSP, które ją obsługują.

[Dokumentacja](https://github.com/decred/dcrdocs): nowe strony: [Obsługa VSP](https://docs.decred.org/advanced/operating-a-vsp/) przedstawia wymagania konfiguracyjne i pożądane umiejętności operatorów VSP, [Głosowanie Solo PoS](https://docs.decred.org/advanced/solo-proof-of-stake-voting/) udostępnia przewodnik autorstwa @jz wszystkim czytelnikom dokumentacji Decred, [Dane adresowe](https://docs.decred.org/advanced/address-details/) opisuje wszystkie możliwe rodzaje adresów, [Udzielanie się w Decred i wnoszenie swojego wkładu](https://docs.decred.org/contributing/contributing-to-decred/) wyjaśnia, w jaki sposób stać się odpłatnym wykonawcą Decred.

Dogłębna dyskusja na temat bezpieczeństwa na kanale #documentation wykazała, że możliwe jest zebranie ogólnych [wytycznych dotyczących bezpieczeństwa komputerowego](https://github.com/xaur/decred-issues/issues/101), które będą korzystne dla całej przestrzeni.

[decred.org](https://github.com/decred/dcrweb): ogromny wysiłek włożony w migrację strony do Hugo został [ukończony](https://github.com/decred/dcrweb/pull/491) przez @peter_zen. Hugo jest statycznym generatorem stron napisanym w Go, który znacznie ułatwia aktualizację zawartości strony. Zawarto kilka [optymalizacji](https://github.com/decred/dcrweb/pull/513) w prędkości działania strony. Dashboard strony [vote.decred.org](https://voting.decred.org/) jest [aktualizowany](https://github.com/decred/hardforkdemo/commits/master) w ramach przygotowań do zbliżającego się głosowania konsensusowego - gratulacje dla @jholdstock za zagłębienie się w Go!

Pozostałe:

* Nowa strona [Bug Bounty](https://bounty.decred.org/) również jest zbudowana na Hugo. Kod [repozytorium](https://github.com/decred/dcrbounty) jest otwarty na zgłoszenia błędów i wkład od użytkowników.
* Więcej zmian terminologii w dcrwallet, dcrdocs i dcrweb.
* Projekty stopniowo przechodzą na szybszy linter golangci-lint.
* Więcej nagłówków bezpieczeństwa zostało [włączonych](https://github.com/decred/dcrweb/pull/537) na decred.org.
* [Interfejs SQL](https://www.reddit.com/r/decred/comments/agpkjv/sql_interface_to_live_onchain_decred_data/) do danych na-łańcuchu Decred może okazać się interesującym dla badaczy.
* GitHub teraz [umożliwia tworzenie](https://github.blog/2019-01-07-new-year-new-github/) prywatnych repozytoriów z maksymalnie 3 współpracownikami dla darmowych kont.

Statystyki aktywności deweloperskiej dla stycznia: 242 aktywne PR-y, 243 master commity, 60K dodanych i 47K usuniętych linijek kodu rozsianych po 8 repozytoriach. Wkład pochodził od 2-8 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono na GitHubie: Sarlor ([dcrd](https://github.com/decred/dcrd/commits?author=Sarlor)), laszlolm ([decrediton](https://github.com/decred/decrediton/commits?author=laszlolm)), dezryth ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=dezryth)).

Gratulacje dla 6 nowych współpracowników [wymienionych](https://github.com/decred/dcrweb/pull/486) na decred.org:

* David Habibi (@eSizeDave, menadżer społeczności - Australia)
* Elian Huesca (@elian, menadżer społeczności - Meksyk)
* Marcelo Martins (@mm, menadżer społeczności - Portugalia)
* Mariusz Szyma (@donmario, menadżer społeczności - Polska)
* Morphy Tsai (@morphymore, menadżer społeczności - Tajwan)
* Tomasz Porwit (@kozel, edukacja i nawiązywanie kontaktów)

[Usunięto](https://github.com/decred/dcrweb/issues/528) 4 nieaktywnych programistów z decred.org: Cruz Molina (@freethinkingaway, dcrdata), Huy Nguyen Tuan (@huyntsgs, dcrwallet), Macaulay Davies (@mcedward), Rohit Nagori.

Niezależni wykonawcy Decred [opublikowali](https://medium.com/decred/decred-independent-contractor-roadmap-884faba3db39) swoje plany na rok 2019, dzięki ~15 osobom, które wniosły swój wkład. Publikacja wywołała [dyskusję](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15476119656176jVTYW:decred.org) o mapach rozwoju, centralnym planowaniu i autonomii wykonawców, jak również komentarz od Ditto.

## Zarządzanie

W styczniu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 16 776 DCR i wydał 9 991 DCR. Przy zastosowaniu styczniowej średniej dziennej stawki DCR/USD w wysokości 17,1 USD, daje to 286 tys. dolarów otrzymanych i 170 tys. wydanych. Ponieważ płatności te zostały dokonane za pracę wykonaną w grudniu, ciekawą perspektywę daje rozważenie ich w kontekście grudniowej średniej dziennej stawki 17,5 USD - w tym przypadku otrzymane/wydane kwoty w USD wynoszą 294 tys/175 tys.

Wykonawcy otrzymują teraz [wynagrodzenie](https://docs.decred.org/contributing/contributor-compensation/) około 15. dnia każdego miesiąca za pracę w poprzednim miesiącu. Opóźnienie pomiędzy wystawieniem faktury a otrzymaniem zapłaty zostało skrócone o połowę; wcześniej wypłaty miały miejsce ok 30. dnia. Trwają prace mające na celu dalsze zmniejszenie tego opóźnienia.

@jy-p złożył propozycję [RFP: Decred Decentralized Exchange Infrastructure](https://proposals.decred.org/proposals/5431da8ff4eda8cdbf8f4f2e08566ffa573464b97ef6d6bae78e749f27800d3a). Przedstawia ona motywację i wysoki poziom projektu DEX opisanego po raz pierwszy w [poście](https://blog.decred.org/2018/06/05/A-New-Kind-of-DEX/) z czerwca 2018 r. Szacuje się, że projekt zostanie ukończony w mniej niż 6 miesięcy, a jego budżet wyniesie od 100 000 USD do 1 000 000 USD. Głosowanie odbędzie się w dwóch fazach: pierwszy wniosek określi, czy interesariusze są zainteresowani propozycją budowy DEX; jeżeli pierwszy wniosek zostanie zatwierdzony, wówczas zainteresowane zespoły zostaną zaproszone do składania propozycji, a w drugiej fazie zostanie wybrany jeden z nich. Proces ten nosi nazwę [zapytania ofertowego](https://en.wikipedia.org/wiki/Request_for_proposal).

Uruchomiony został program [Bug Bounty](https://twitter.com/decredproject/status/1087486930093264897) po udanym przegłosowaniu [propozycji](https://proposals.decred.org/proposals/d33a2667469b56942adf42453def6cc2292325251e4cf791e806939ea9efc9e1) w grudniu. Sprawdź zasady działania programu na nowej stronie internetowej [bounty.decred.org](https://bounty.decred.org/) oraz w poście wprowadzającym na [hackernoon](https://hackernoon.com/decred-launches-debug-decred-bug-bounty-program-7e4d2af27ec9). Zasługi dla @fernandoabolafio i @jholdstock za większość pracy nad stroną. W skład zespołu, który decyduje o ważności zgłoszeń i wypłat wchodzą @degeri, @dnldd, @fernandoabolafio, @jholdstock i @matheusd. Gratulujemy zespołowi uruchomienia!

@Dustorf przygotowuje propozycje poprawy przejrzystości i zwiększenia kontroli interesariuszy nad alokacją środków na działania marketingowe. [Propozycja przedwstępna](https://www.reddit.com/r/decred/comments/anhh8n/proposal_to_get_events_spending_approved_via/) odnośnie wydatków na wydarzenia została opublikowana na Reddicie w celu uzyskania informacji zwrotnej po pierwszej iteracji [na czacie](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154896889724431Mxlvj:decred.org). Propozycja przedwstępna odnośnie budżetu na marketing również rozpoczęła się [na czacie](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154897255124536mFHoo:decred.org) i wylądowała [na Reddit](https://www.reddit.com/r/decred/comments/aolr79/politeia_proposal_to_fund_marketing_ops_for_2019/) po pierwszej turze informacji zwrotnej i komentarzy.

@oregonisaac  [szuka](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$15474111512672Whvns:decred.org) programistów Java w celu oceny wymagań dotyczących integracji z bankomatami kryptowalutowymi. Projekt propozycji został opublikowany i omówiony [na czacie](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$154828004015153jWdiD:decred.org). Uzgodniono, aby używać procesu 2-etapowego głosowania nad zapytaniami ofertowymi. Innym dobrym punktem dyskusji było to, czy poczekać na wydanie aplikacji mobilnych przed przystąpieniem do pracy nad bankomatami.

Dyskusje:

* Propozycja Baeond wywołała [dyskusję](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$154687339790vCEoH:decred.org) na temat wektora ataku, w którym interesariuszom proponuje się zrzut jakiegoś żetonu w zamian za zatwierdzenie przez nich propozycji.
* [Dyskusja](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$15481365491827928DiBLm:matrix.org) na temat zaangażowania i zadowolenia z dotychczasowej działalności Politei.
* W jaki sposób [usprawnienia UX](https://github.com/decred/politeia/issues/678) mogą pomóc głosującym w zapobieganiu złym propozycjom i zachowaniu czujności.

## Sieć

Hashrate: w styczniu hashrate wynosił  ~187 Ph/s na początku i ~225 Ph/s na końcu miesiąca, osiągając niż 144 Ph/s i szczyt na poziomie 312 Ph/s w ciągu miesiąca. Na 8 lutego dystrybucja mocy obliczeniowej puli wydobywczych wygląda następująco: Poolin 29%, F2pool 26%, BTC.com 19%, UUPool 8%, Luxor 4%, CoinMine 1% oraz pozostałe na poziomie 13% na [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: w dniu 4 lutego, za dcrstats.com, średnia cena biletu z okresu 30 dni wynosiła 109,4 DCR (+6,4). Cena wahała się między 101,5-111,6 DCR. Zablokowana kwota wynosiła 4,20-4,38 mln DCR, co odpowiadało 46,3-47,5% dostępnej podaży.

W styczniu zakupiono 90 biletów dzielonych. [Dane](https://gist.github.com/oregonisaac/8eb4d50af9fa888c920666fb73ba44b2) od maja 2018 r. wykazują stały wzrost.

Węzły: Na dzień 4 lutego [dcred.eu](https://dcred.eu/nodeStats) podało 197 publicznych węzłów nasłuchujących i 369 normalnych. Dystrybucja wersji: v1.5.0 dev: 4,3% (+2,8%), v1,4.0 dev i rc: 13% (+6%), v1.3.0: 55%, v1.2.0: 14% (-6%), v1.1.2: 8% (-2%), v1.1.0: 3% (-1%).

## Wydobycie

Partie Obelisk 2-5 [są wysyłane](https://us16.campaign-archive.com/?u=393b2698d17bdfe48ac0422ac&id=4211e39081), [update](https://us16.campaign-archive.com/?u=393b2698d17bdfe48ac0422ac&id=c501bf724d) oprogramowania sprzętowego dla 2. generacji zawiera nowe funkcje i poprawki błędów. Złożono [pozew zbiorowy](https://www.reddit.com/r/decred/comments/ae8hy8/class_action_lawsuit_officially_filed_against/) w związku ze sprzedażą SC1 i DCR1 przez firmę Obelisk.

W toku jest opersource'owa [implementacja puli wydobywczej](https://medium.com/decred/decred-independent-contractor-roadmap-884faba3db39) Decred autorstwa @dnldd.

## Integracje

Nowy VSP [dcr.grassfed.network](https://dcr.grassfed.network) dołączył do listy usługodaawców, sprowadzając ich całkowitą liczbę do 23.

Integracje z giełdami wymian:

* Turecka giełda Bitturk [ogłosiła](https://twitter.com/bitturkcom/status/1082201314912862209) parę fiat DCR/TRY, dyskusja i odrobina kontekstu sytuacji są [tutaj](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15468134682383442wDSE:matrix.org).
* Brazylijska giełda BitJa [ogłosiła](https://twitter.com/bitjabr/status/1090066185302036480) parę fiat DCR/BRL.

Portfel Ellipal [ogłosił](https://twitter.com/ellipalwallet/status/1089850526202613760) wsparcie dla Decred w najnowszej wersji oprogramowania sprzętowego.

Portfel Exodus [zintegrował](https://twitter.com/exodus_io/status/1090263399122923520) USDC, token powiązany z wartością USD od firmy Circle.

Drugi odcinek z serii wywiadów infrastrukturalnych przeprowadzanych przez @kozel [gości Stephena](https://medium.com/@artikozel/decred-infrastructure-interviews-stephen-founder-of-crypto-only-luxury-goods-marketplace-68d3214a4fd7), założyciela punktu sprzedaży towarów luksusowych Crypto Emporium. W wywiadzie Stephen dzieli się spostrzeżeniami na temat prowadzenia biznesu, przyjmowania płatności krypto, przetwarzania zamówień, łańcucha dostaw i planów na przyszłość.

> Naszym najlepiej sprzedającym się produktem na stronie internetowej niewątpliwie była słynna [kurtka Decred](https://www.cryptoemporium.eu/product/decred-jacket/)! To  zaszczyt służyć społeczności Decred przez tak długi czas i pomagać w promocji projektu, w który naprawdę wierzę.

Zawsze zrób dobre, własne rozeznanie i research _zanim_ użyjesz portfeli lub usług, zwłaszcza tych, które zajmują się przechowywaniem Twoich funduszy.

## Adopcja

BlueYard [ogłosiło](https://medium.com/@BlueYard/blueyard-2-3d0bbaf1f1b6) drugą rundę zbiórki środków i wyjaśniło swoją strategię inwestowania w projekty płynące pod prąd.

## Nawiązywanie kontaktów

Zespół marketingowy [planuje](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15468814029997AWtQJ:decred.org), aby zwracać się do reporterów publikujących nieścisłości dotyczące Decred. Jako przypadek testowy dla tego przepływu pracy jeden straszny artykuł został przeanalizowany przez społeczność i Ditto zebrało opinie na temat tego przypadku oraz na przyszłość. Ditto dyspouje [systemami](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154690407510431bVTJQ:decred.org), które wyłapują każdy element medialny napisany o Decred. Wraz z tym, jak lepiej poznają społeczność, możliwe będzie zajęcie się nieścisłościami w czasie rzeczywistym. Kolejną omawianą kwestią było zintegrowanie [przepływu pracy dot. poprawek](https://github.com/xaur/decred-issues/issues/71) Ditto z dobrowolnymi zgłoszeniami od społeczności.

Tagline dla Decred został obszernie omówiony [na kanale #marketing](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154711632712869dqRko:decred.org) oraz [na Reddit](https://www.reddit.com/r/decred/comments/afctai/tagline_to_capture_the_decred_project/). W ostatecznej wersji przekazu występuje on w formie "Decred: Bezpieczny. Adaptacyjny. Samofinansujący się"", która otrzymała najwięcej wsparcia. W miarę upływu czasu będzie ona modyfikowana w celu dostosowania się do ciągle zmieniającej się przestrzeni.

Styczniowy update od Ditto:

* Przebrnęliśmy przez kilka iteracji dokumentu odnośnie podstawowego przekazu informacyjnego dla Decred ze znacznym wkładem społeczności i otrzymaliśmy pozytywne opinie na temat [wersji ostatecznej](https://pastebin.com/E5L6u2RV). (dyskusje: odnośnie jego [drugiej](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154706728112462ubmNo:decred.org), oraz [końcowej](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154880432321730DYSYl:decred.org) wersji)
* Pracowaliśmy ze społecznością w celu uzyskania komentarzy na temat ataków typu 51% do wykorzystania w przyszłości z reporterami, kiedy nieuchronnie dojdzie do kolejnego ataku - celem jest przedstawienie przekazu Decred przed dziennikarzami, nawet jeśli nie ma żadnych konkretnych informacji do przekazania.
* Przeszkoliliśmy trzech członków zespołu Decred w zakresie prezencji medialnej.
* Umieściliśmy następujące relacje w mediach: [artykuł](https://www.forbes.com/sites/leslieankney/2019/01/11/who-should-hold-power-decred-governance-and-what-it-means-for-investors/) w Forbes ([raport](https://matrix.to/#/!OfChgczrIlpEZSFAv:decred.org/$1547232300845NiZnO:decred.org)), [wywiad wideo](https://www.youtube.com/watch?v=CUxDxJ4YAUA) z Joshuą dla Bitsonline, komentarz @richardred na temat zwłoki w hardforku Ethereum w [Breaker Mag](https://breakermag.com/what-we-know-about-the-vulnerability-behind-ethereums-rollback-of-constantinople/) i [Crypto Briefing](https://cryptobriefing.com/scaling-delay-ethereum-constantinople/).
* Przygotowaliśmy ogłoszenie o programie bug bounty i [umieściliśmy je](https://hackernoon.com/decred-launches-debug-decred-bug-bounty-program-7e4d2af27ec9) w Hacker Noon - tym samym docierając do znacznie szerszej puli programistów, w porównaniu do własnych kanałów Decred.
* Pomogliśmy zrealizować dwa wywiady, które oczekują na publikację w mediach.
* Polecieliśmy na północnoamerykańską konferencję Bitcoin, gdzie Ditto zorganizowało wywiady pomiędzy Decred i reporterami (Cheddar TV, Altcoin Buzz, itp.) i spędziliśmy wysokiej jakości, produktywny czas z zespołem.
* Współpracowaliśmy ściśle z Dustinem nad planem wydarzeń, który obejmuje zarówno wydarzenia, podczas których Decred chce zabrać głos, jak i wydarzenia, na których chce mieć stoisko.
* Złożyliśmy wniosek odn. wystapienia Jake'a na Consensus 2019.
* Współpracowaliśmy ściśle z Dustinem nad planem marketingowym i komunikacyjnym na pierwszą połowę 2019 roku, obejmującym przekaz, szkolenia medialne, relacje z mediami, eventy i wystąpienia oraz strategię. Plan ten jest nadal w toku.

Zaleca się dzielenie się relacjami z mediami nt. Decred z innymi osobami, ponieważ wzmocnienie przekazu jest równie ważne, jak samo umieszczenie go w mediach.

Jeszcze więcej szczegółów można znaleźć w dwutygodniowych aktualizacjach z [7 stycznia](https://matrix.to/#/!OfChGczrIlpEZSFAv:decred.org/$154688457110052CiWYd:decred.org) oraz [18 stycznia](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15478384869864RTCsv:decred.org). W jednym z nich znajduje się taka perełka:

> Społeczność przyjmuje i zachęca do zadawania pytań, nawet jeśli osoba zadająca obawia się, że jej pytania są "głupie". Zaobserwowaliśmy ducha współpracy i chęć pomocy, którego nie widzieliśmy w innych społecznościach. To orzeźwiające!

Pozostałe:


* [Mówi się](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15478503329998HCAzR:decred.org), że Ditto jest w stanie załatwić oszałamiającą brodę, która uprawnia do noszenia srebrnej kurtki Decred.
* @anshawblack [poroznosił](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154792069410439nSRtR:decred.org) fanty Decred we wszystkich sklepach płytowych Miami.
* Odnowiony został [sklep Decredible](https://www.reddit.com/r/decred/comments/ae07as/custom_decred_merch_with_19_discount_in_the/) z dodatkowymi elementami i nowymi logo Decred. Wszystkie produkty mogą być spersonalizowane i dopracowane.

Pilna uwaga: nowa partia pluszaków Stakey jest [dostępna](https://www.reddit.com/r/decred/comments/ahalex/new_batch_of_stakey_plushies_available/)!

## Eventy:

* [Północnoamerykańska Konferencja Bitcoin](https://btcmiami.com/) w Miami, USA. Frekwencja była zaskakująco niska: oczekiwano 6 tys. osób, ale lecz oficjalnie udział wzięło jedynie 1,8 tys. osób. Prezentacja @jy-p pt. [Zastosowanie znaczników czasowych na blockchainie](https://btcmiami.com/session/applications-of-blockchain-time-stamping/) była dobrze przygotowana i cieszyła się dużym zainteresowaniem, biorąc pod uwagę ogólną liczbę uczestników. 3 członków przeszło szkolenie medialne i uznało je za przydatne, zaplanowano 7 kolejnych. Środek przechowania wartości, "Bezpieczny. Adaptacyjny. Samofinansujący się", i towarzyszący im przekaz okazały się bardzo skutecznym sposobem mówienia o Decred. Okazało się, że jest to najbardziej czytelne i skuteczne podejście. Pełny raport z linkami do zdjęć i filmów [tutaj](https://github.com/heyvj/decred-events/blob/master/reports/20190116-tnabc-miami.md).
* [OKEx Global Meetup Tour](https://www.eventbrite.hk/e/okex-global-meetup-tour-2019-taiwan-tickets-54689867867) w Tajpej, na Tajwanie. @morphymore opowiedział historię Decred i o tym, jak działa. "W porównaniu do 2018 roku, ludzie zaczynają kojarzyć Decred lepiej. Kilka osób powiedziało mi, że wiedzą o Decred z chińskiego tłumaczenia tezy inwestycyjnej Placeholder, które wykonałem w zeszłym roku. Było to bardzo zachęcające i pokazuje, że świadomość o Decred na Tajwanie rzeczywiście rośnie". ([raport](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15478245399446fDEQa:decred.org), [zdjęcia](https://photos.app.goo.gl/rXd9PeYmyAGrVTQN7))
* [10 lat Bitcoina](https://10latbitcoina.com.pl/) w Warszawie, Polska. @karamble mówił o długowieczności w kryptowalutach na podstawie Decred. Zespół 4 osób nawiązał relacje z kilkoma portalami krypto i zaangażował się w rozmowę z kilkoma firmami. BitHub.pl zauważył: "Chłopaki z Decred z wielkim zaangażowaniem odpowiadali na pytania zainteresowanych, wykazując się przy tym dużą dozą cierpliwości, ponieważ pytania spadały na nich praktycznie cały czas!". ([raport](https://github.com/heyvj/decred-events/blob/master/reports/20190126-10LatBitcoina-Warsaw.md))

Nadchodzące:

* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) w Sao Paulo, Brazylia, 12-17 lutego.
* [Jak bezpiecznie przechowywać swoje krypto](https://www.meetup.com/Decred-Australia/events/258211699/) w Melbourne, Australia, 18 lutego.
* [Decred w 30 minut](https://www.eventbrite.com/e/decred-en-30-minutos-tickets-55764142050) w Mexico City, Meksyk, 27 lutego. Zagadajcie z @elian po więcej szczegółów.
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) w Guadalajarze, Meksyk, 22-26 kwietnia. Skontaktuj się z @elian, jeśli jesteś zainteresowany pomocą/udziałem.

Wydarzenia zorientowane na hakerów i tematykę open source, takie jak DEFCON, CCC i FOSDEM zostały omówione i uchwycone w [tym wątku](https://github.com/xaur/decred-issues/issues/83).

## Media

Inicjatywy społecznościowe:

* [blog.dcrclub.org](https://blog.dcrclub.org/) jest nową stroną internetową w języku chińskim, która zbiera różne artykuły i tłumaczenia w jednym miejscu. Jej źródło hostowane [na GitHub](https://github.com/0x5826/blog.dcrclub.org) ułatwia dodawanie lub powielanie strony internetowej na innych domenach w celu zwiększenia jej odporności. Zasługi za uruchomienie strony należą się @TogT4V (Telegram).
* Nowy [blog w jęz. arabskim](https://decred-arabia.blogspot.com/2019/01/blog-post.html) o Decred został uruchomiony przez @butterfly (@arij na platformie Matrix). Istnieją pewne wyzwania związane z publikowaniem tekstu w jęz. arabskim w Internecie; wszelkie porady są mile widziane na kanale #writers_room.
* @michae2xl rozpoczął [podcast w jęz. portugalskim](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$1548814257223928fVjiP:matrix.org), dostępny na stronie [Soundcloud](https://soundcloud.com/user-770106247/), Spotify,  i serwisach Apple Podcasts i Google Podcasts - w wyszukiwarce wpisz "Decred Brasil".
* [@decredexplorer] (https://twitter.com/decredexplorer) to nowe konto na Twitterze poświęcone dcrdata. Dziękujemy @michae2xl za jego założenie i prowadzenie.
* @Matt D [założył](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154825336714293nfWdU:decred.org) kanał [agregator Decred](https://t.me/DecredAgg) na Telegramie. Jego celem jest zbieranie wiadomości, prasy, filmów wideo, podcastów, ogłoszeń Decred, trendów tweetów i postów na Reddit, a także statystyk rynkowych.
* @anshawblack planuje podcast.

[Strona Decred](https://en.wikipedia.org/wiki/Decred) na Wikipedii została usunięta. 8 stycznia użytkownik [usunął](https://archive.today/ApV3P) kilka "złych źródeł" a 10 stycznia zdewastował stronę, usuwając dużą i ważną część treści. Zaledwie 4 godziny później inny użytkownik nominował stronę Decred do usunięcia - była to już [3. próba](https://en.wikipedia.org/wiki/Wikipedia:Articles_for_deletion/Decred_%283rd_nomination%29) usunięcia jej. Dla odrobiny kontekstu, autor [2. nominacji](https://en.wikipedia.org/wiki/Wikipedia:Articles_for_deletion/Decred_%282nd_nomination%29) do usunięcia miał interesujące [poglądy](https://archive.today/QAlRp) na temat tego, co stanowi rzetelne źródło i został [zbanowany](https://en.wikipedia.org/wiki/User:Prince_of_Thieves) za używanie wielu kont. 11 stycznia usunięte treści zostały przywrócone, a autor zamieszania został zbanowany za wspomniany wyżej występek, ale następnego dnia [ponownie](https://archive.today/fZUHW) usunięto treści, za czym stał inny użytkownik i nie zaoferował do sprawy żadnego bardziej obszernego komentarza. Po wycięciu dużej ilości treści strona skurczyła się i wszyscy recenzenci [zagłosowali](https://en.wikipedia.org/wiki/Wikipedia:Articles_for_deletion/Decred_%283rd_nomination%29) aby ją usunąć z powodu braku wiarygodnych źródeł. Wszystkie zaproponowane ostatnie artykuły w głównych mediach z branży krypto zostały uznane za [nie dość dobre](https://archive.today/4xwaN) odniesienia. 18 stycznia strona została skasowana i usunięta z [listy kryptowalut](https://en.wikipedia.org/wiki/List_of_cryptocurrencies), na której znajdują się bardziej znaczące monety. Szczegóły i linki do dyskusji znajdują się w [tym wątku](https://github.com/xaur/decred-issues/issues/79). Zapraszamy doświadczonych redaktorów Wikipedii do pomocy.

Wybrane artykuły (kolejność chronologiczna):

* Ku zrozumieniu systemu zarządzania Decred, aut. dr Bitcoin (w jęz. chińskim, [qq.com](https://mp.weixin.qq.com/s/z3hzILiPBsLJR72Q2tP7TQ), [tłumaczenie](https://translate.google.com/translate?sl=auto&tl=en&hl=en&u=https%3A%2F%2F%2Fmp.weixin.qq.com%2Fs%2Fz3hzILiPBsLJR72Q2tP7TQ), _przegapione w wydaniu grudniowym_)
* Analiza fundamentalna: Decred, aut. Piotr Arendarski ([linkedin.com](https://www.linkedin.com/pulse/funadamental-analysis-decred-dcr-piotr-arendarski-ph-d))
* Jak przetrwać krypto zimę? Szukaj prostoty, Zarządzaj złożonością, aut. @jy-p ([coindesk.com](https://www.coindesk.com/how-to-last-the-crypto-winter-seek-simplicity-manage-complexity), tagline został wymyślony wspólnie na kanale #marketing)
* Decred- Wywiad z menadżerem społeczności @donmario przeprowadzony przez Janusza Zielińskiego ([bithub.pl](https://bithub.pl/wywiady/decred-wywiad-z-community-managerem/))
* Najlepsze portfele dla Decred: 6 najlepszych miejsc do przechowywania DCR, aut. Steve Walters ([coinbureau.com](https://www.coinbureau.com/analysis/best-decred-wallets/), miły przypadek tego, kiedy autorzy reagowali i poprawili wszystkie [zgłoszone problemy](https://github.com/xaur/decred-issues/issues/68)).
* Kto powinien posiadać władzę? Zarządzanie w Decred i co to oznacza dla inwestorów, aut. Leslie Ankney ([forbes.com](https://www.forbes.com/sites/leslieankney/2019/01/11/who-should-hold-power-decred-governance-and-what-it-means-for-investors/))
* Mapa rozwoju niezależnych wykonawców Decred na 2019 r. ([medium](https://medium.com/decred/decred-independent-contractor-roadmap-884faba3db39))
* Unikalny mechanizm konsensusu Decred- czy tak wygląda prawdziwa decentralizacja? aut. Paul de Havilland ([bitsonline](https://bitsonline.com/consensus-mechanism-of-decred-decentralization/))
* Decred jako środek przechowania wartości, aut. Yin Guochao, zainspirowany artykułem Forbesa (w jęz. chińskim, [qq.com](https://mp.weixin.qq.com/s/_-lY0rtWSPiyLPZeTRR7gg), [tłumaczenie](https://translate.google.com/translate?sl=auto&tl=en&hl=en&u=https%3A%2F%2F%2Fmp.weixin.qq.com%2Fs%2F_-lY0rtWSPiyLPZeTRR7gg))
* Przegląd projektów blockchain: Decred: Autonomiczna waluta cyfrowa, aut. Evaluape([medium](https://medium.com/@EVALUAPE1/blockchain-project-review-decred-8-4-autonomiczna waluta cyfrowa-323771d65529), Decred oceniony na 8.4/10)
* Recenzja Decred: następca BTC? aut. Edwin (w jęz. holenderskim, [bitcoinsaltcoins.nl](https://www.bitcoinsaltcoins.nl/decred-coin-review-vervanger-van-btc/), ocena: 8,8/10)
* 3 kryptowaluty do HODLingu podczas tej krypto zimy (opinia) Daniela Frumkina ([investinblockchain.com](https://www.investinblockchain.com/cryptocurrencies-hodl-during-crypto-winter/))
* Wartośc fundamentalna w krypto; Bitcoin i Decred inwestycje w środki przechowania wartości, aut. LCC Investment Research ([seekingalpha.com](https://seekingalpha.com/article/4235521-fundamental-value-crypto-bitcoin-decred-store-value-investments))
* Rola głosujących Decred w obronie przed atakami większościowymi, aut. @richardred ([medium]([https://medium.com/@richardred/therole-of-decred-voters-in-defendinging-agresja wobec ataków większościowych-ec658af0a8fd))
* Zdecentralizowane zarządzanie poza łańcuchem w kontekście walut cyfrowych, aut. @Haon ([goodaudience.com](https://blog.goodaudience.com/decentralized-off-chain-governance-in-the-context-of-digital-currencies-ef6db7d97412))
* Wywiady infrastrukturalne Decred: Stephen, założyciel punktu sprzedaży towarów luksusowych CryptoEmporium, aut. @kozel ([medium]([https://medium.com/@artikozel/decred-infrastructure-interviews-stephen-founder-of-crypto-only-luxury-goods-marketplace-68d3214a4fd7)).
* Recenzja Decred, aut. Lee Banfield ([weeklyglobalresearch.wordpress.com](https://weeklyglobalresearch.wordpress.com/2019/01/31/decred-dcr-review/))

Tłumaczenia:

* [Szczegółowa analiza odporności na rozszczepienie łańcucha sieci Decred](https://medium.com/decred/detailed-analysis-of-decred-fork-resistance-93022e0bcde7), aut. @Haon - [w jęz. rosyjskim](https://medium.com/decred-russia/%D0%B4%D0%B5%D1%82%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9-%D0%B0%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7-%D1%83%D1%81%D1%82%D0%BE%D0%B9%D1%87%D0%B8%D0%B2%D0%BE%D1%81%D1%82%D0%B8-decred-%D0%BA-%D1%84%D0%BE%D1%80%D0%BA%D1%83-b30c78f764ea), aut. @DZ
* Decred Journal - Grudzień 2018 [w jęz. chińskim](https://www.jianshu.com/p/65e7a83ac27c), aut. @guang, [w jęz. polskim](https://github.com/artikozel/DecredJournalPL/blob/master/journal/201812_DecredJournalPL.md), aut. @kozel, [w jęz. portugalskim](https://medium.com/@maiconjunge/jornal-decred-dezembro-de-2018-947c616b894f), aut. @maiconjunge, [w jęz. rosyjskim](https://medium.com/decred-russia/decred-journal-%D0%B4%D0%B5%D0%BA%D0%B0%D0%B1%D1%80%D1%8C-2018-9528f7a9d24d), aut. @DZ oraz [w jęz. hiszpańskim](https://medium.com/@decred_es/revista-decred-diciembre-2018-79093f957aac), aut. @elian. Wow. Dziękujemy Wam wszystkim za szerzenie Decred Journal na całym świecie! Wszystkie tłumaczenia wymienione są [tutaj](https://xaur.github.io/decred-news/).

Wideo:

* Zastosowanie znaczników czasowych na blockchainie - prezentacja aut. @jy-p na TNABC ([youtube](https://www.youtube.com/watch?v=3RRTidXh_Lw))
* Wywiady podczas TNABC: [z @joshuam](https://www.youtube.com/watch?v=Kyihc6Uh4XA), aut. Hack Crypto, [z @joshuam](https://bitsonline.com/decred-disputes-inevitable-buirski/), aut. Bitsonline, [z @DZ](https://www.youtube.com/watch?v=h3bII-vjOsA), [with @jz](https://www.youtube.com/watch?v=4oKRVXGN6Fs), aut. CNBC Crypto Trader.
* Zarządzanie: Najbardziej pomijany filar technologii blockchain, prezentacja aut. @oregonisaac podczas Token Forum 2 ([tfblock.io](https://www.tfblock.io/post/governance-blockchain-s-most-overlooked-pillar))

Audio:

* Dogłębna analiza niezależnych kryptowalut na podstawie Decred - @moo31337 oraz @BAB mówią o tym, jak zdecentralizowane systemy podejmowania decyzji oraz samofinansowania się umożliwiły Decred zbudowanie solidnej, ewoluującej waluty cyfrowej wolnej od wpływów stron trzecich (The Crypto Chick Podcast z Rachel Wolfson, [badcryptopodcast.com](https://badcryptopodcast.com/2019/01/08/autonomous-crypto-decred/))
* Noah Pierau na temat zarządzania w technologii blockchain : Decred, Bitcoin, Dash, Ethereum (51percent Crypto Research aut. Toma Shaughnessy, [itunes](https://itunes.apple.com/us/podcast/noah-pierau-on-blockchain-governance-decred-bitcoin/id1438148082?i=1000428113722&mt=2))
* Jak Decred rewolucjonizuje kwestię finansowania w krypto. Marco Peereboom w rozmowie z Michaelem Nye omawiają obecny stan krypto, początki Decred, kwestię PoW kontra PoS, model finansowania Decred oraz wiele więcej (Evolvement Podcast, [evolvement.io](https://evolvement.io/how-decred-revolutionizes-funding-in-crypto-with-marco-peereboom/))

## Dyskusje społeczności

Statystyki społeczności na dzień 4 lutego:

* Obserwujący na Twitterze: 39,778 (-106)
* Subskrybenci na Reddit: 9,330 (+89)
* Użytkownicy na Matrixie: 247 (+26)
* Użytkownicy na Slacku: 6,529 (+110)
* Użytkownicy na Telegramie: 4,503 (-231)
* Subskrybenci na YouTube: 3,752 (+14)
* Obserwujący na Facebooku: 3,132 (+11), polubień: 2,891 (+11)
* Obserwujący na LinkedIn: strona Decred 466 (+16), Pstrona Politeia 27 (+3)
* GitHub: 468 gwiazdek (+10) i 1,221 forków repozytorium dcrd (+29)

Wiadomości z platform komunikacyjnych:

* [Powolny spadek](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$1549500437341uJIFK:decred.org) liczby obserwujących na Twitterze trwa z nieznanych powodów. Wszelkie pomysły i teorie są mile widziane.
* Spadek liczby użytkowników Telegrama jest prawdopodobnie wynikiem czystek usuwających boty.
* @sambiohazard napisał szczegółowy [plan](https://github.com/xaur/decred-issues/issues/16) rozwiązania problemu spamu na Discordzie, wdrożył go i  po kilku pierwszych tygodniach odnotował i zgłosił brak spamu. Kilka ważnych kanałów zostało zmostkowanych z Discordem. Dzięki temu możemy w końcu docenić Discord jako narzędzie, dzięki któremu możemy powiększyć grono społeczności Decred o większą liczbę osób. Dziękujemy!
* [decred.org/matrix](https://decred.org/matrix/) wprowadza nowych użytkowników do systemu.
* Repozytorium [decred-issues](https://github.com/xaur/decred-issues) rozrosło się do 105 kwestii na dzień 9 lutego. Sprawdź, może znajdziesz coś ciekawego do zrobienia!

[Krytyka](https://twitter.com/tonevays/status/1086702239853379584) ze strony maksymalistów Bitcoina wywołała [dyskusję](https://www.reddit.com/r/decred/comments/ahuawl/decred_launch_security_laws/) na temat tego, jak Decred wygląda w kontekście prawa papierów wartościowych. Jeden z wektorów ataku użytych przez krytyków twierdzi, że przedwstępne wydobycie i zrzut Decred nie były sprawiedliwe i były poddane "ręcznej selekcji". Jest to błędna reprezentacja (ogromnego) wysiłku włożonego w ręczny odsiew oszustów, za [tą dyskusją](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154810656412322VrQLg:decred.org), która również zawiera wiele użytecznych linków opisujących uruchomienie sieci Decred. Jedną z ciekawostek jest to, że ~300K (35%) zrzuconych monet nigdy nie ruszyło się z miejsca. Inna powiązana [rozmowa](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$15467943549349316LjeYZ:decred.org) była o atakach na Twitterze, gdzie padło stwierdzenie, że początkowa dystrybucja Decred nie była przejrzysta lub uczciwa, unikając niewygodnych faktów na temat wczesnego wydobycia Bitcoina i miliona BTC Satoshiego. Wreszcie, [lekcja historii](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15467944729319gvt:decred.org) wyjaśniła, jak wyglądały wczesne dni stakingu i zwróciła uwagę na to, że pierwsi deweloperzy Decred nie mieli jednostronnej kontroli nad zasadami konsensusu od pierwszego dnia działania sieci głównej Decred.

Ogromna debata na temat znaczenia budowania społeczności Reddit miała miejsce [w tym wątku](https://www.reddit.com/r/decred/comments/aib2x3/noah_pierau_on_blockchain_governance_decred/).

## Rynki

W styczniu kurs wymiany Decred wahał się pomiędzy 15,5 - 19,5 USD / BTC 0,00435 - 0,00487. Średni dzienny kurs wynosił 17,1 USD.

## Ważne kwestie i wiadomości poboczne

Ethereum Classic (ETC) padło ofiarą ataku 51%, o czym na alarm zabiło [CoinNess](https://www.coinness.com/news/198264) 7 stycznia. Następnie Coinbase [ogłosiło](https://blog.coinbase.com/ethereum-classic-etc-is-currently-being-51-attacked-33be13ce32de), że wykryli głęboką reorganizację sieci ETC i wstrzymali transakcje ETC. W artykule wymieniono szereg reorganizacji, które wiązały się z podwójnymi wydatkami, na łączną kwotę 1,1 mln USD na przestrzeni 15 osobnych zdarzeń związanych z reorganizacją sieci. Sama giełda Coinbase nie była celem tych ataków. Giełda Gate.io [ogłosiła](https://www.gate.io/article/16735) następnie, że padłą ofiarą ataków, w których straciła około 200 tys. USD i że pokryje poniesione przez siebie straty. Gate.io znacznie zwiększyła również liczbę potwierdzeń wymaganych dla depozytów ETC. W nietypowej zwrocie akcji atakujący, następnie, [zwrócili](https://www.gate.io/article/16740) giełdzie Gate.io $100K w ETC. Giełða próbowała, ale nie udało jej się nawiązać kontaktu z atakującymi i nie znają powodu zwrotu środków. Inne ofiary podwójnych wydatków ETC nie zgłosiły się.

Programiści Ethereum 4 stycznia (wstępnie)[zdecydowali](https://www.coindesk.com/ethereum-developers-give-tentative-greenlight-to-asic-blocking-code) przejść z algorytmu wydobywczego Ethash na ProgPoW. To posunięcie ma na celu powstrzymanie ASIC-ów przed wydobywaniem Ethereum. The Block [nakreśliło](https://www.theblockcrypto.com/2019/01/11/despite-core-dev-consensus-proposition-progpow-faces-community-concerns/) obawy takie, jak zmniejszenie kosztów ataku po przełączeniu, mniejsze incentywy dla górników wykorzystujących procesory graficzne, wątpliwe korzyści z przeniesienia mocy z Bitmain i Innosilicon do AMD i Nvidii oraz możliwy podział łańcucha. Ich konkluzją było to, że debata na temat zmiany algorytmu będzie dobrym sprawdzianem dla procesu zarządzania w Ethereum.

Programiści Ethereum [opóźnili](https://breakermag.com/what-we-know-about-the-vulnerability-behind-ethereums-rollback-of-constantinople/) również planowany na 15 stycznia hard fork Constantinople, po tym, jak odkryto [luki bezpieczeństwa](https://medium.com/chainsecurity/constantinople-enables-new-reentrancy-attack-ace4088297d9), które umożliwiłyby atak wielobieżny (ang. *reentrancy attack*).

Artykuł zatytułowany [Podstawy Proof of Work](https://blog.sia.tech/fundamentals-of-proof-of-work-beaa68093d2b) Davida Voricka przemawia za rozwiązaniami sprzętowymi wyłącznie na potrzeby kryptowalut i kontrastuje je z kryptowalutami wykorzystującymi sprzęt ogólnego przeznaczenia, które cierpią z powodu wielu problemów, skupiając się szczególnie na tych, które za cel stawiają sobie odporność na układy ASIC. Jednym z problemów z niewyspecjalizowanym sprzętem jest to, że wartość sprzętu nie jest ściśle związana z aktywem (ponieważ może on wydobywać na wielu różnych łańcuchach). Kolejną kwestią są targowiska/rynki mocy obliczeniowej, które pozwalają właścicielom sprzętu na uzyskanie większego zysku, nie dbając o to, którą monetę wydobywają, nawet jeśli hashrate jest wynajmowany napastnikom. Decred korzysta ze specjalistycznego sprzętu i jest zdecydowanie dominującą monetą dla wykorzystywanego przez nią algorytmu (Blake256r14). Chociaż sprzętu tego nie można uznać za istniejący dla Decred "na wyłączność", oprócz obecnej dominacji hashrate dla jego algorytmu Decred ma czynnik PoS, który jest w stanie pozbawić źle zachowujących się górników nagrody za wydobycie bloku.

Pierwsza tura głosowania nad propozycjami w projekcie Aragon została [zakończona](https://blog.aragon.org/final-results-from-aragon-network-vote-1/) 26 stycznia. Spośród 12 złożonych propozycji 3 zostały wyłączone z głosowania przez Fundację Aragon (1 z powodu braku pełnoetatowego przywództwa i talentu inżynieryjnego, a 2 w celu zmniejszenia obciążenia poznawczego wyborców). 8 z 9 propozycji poddanych pod głosowanie zostało [zatwierdzonych](https://mainnet.aragon.org/#/governance.aragonproject.eth/0x277bfcf7c2e162cb1ac3e9ae228a3132a75f83d4) przez posiadaczy ANT, przy czym jedna propozycja (zmiany okresu głosowania z 48 godzin na 1 tydzień) została odrzucona. Wskaźniki uczestnictwa ANT [wahały się](https://mainnet.aragon.org/#/governance.aragonproject.eth/0x277bfcf7c2e162cb1ac3e9ae228a3132a75f83d4) od 2,3 do 7,8%. Najdroższa [propozycja](https://github.com/aragon/flock/blob/master/teams/Aragon%20One/2019.md), która ma zostać zatwierdzona, zapłaci Aragon One 4 miliony dolarów na koszty operacyjne w 2019 r., plus pakiet motywacyjny składający się z 1,675 miliona ANT w ramach pięcioletniego harmonogramu nabywania uprawnień. Zachęta w ANT z harmonogramem nabywania uprawnień została włączona jako część większości propozycji, oprócz kosztów głównych, które mają być zapłacone w DAI. W sumie ta runda zatwierdzonych wniosków będzie kosztować około 5,94 mln USD + 2,52 mln ANT (~880 tys. USD).

System referendalny do wprowadzania konstytucyjnych poprawek w EOS został [uruchomiony](https://medium.com/@eosnationbp/the-fate-of-eos-is-in-the-hands of-token-holders-3d345147ef6) 11 stycznia. Do tej pory złożono [77 propozycji](https://bloks.io/vote/referendums). Okres głosowania nad tymi wnioskami jest elastyczny i określony przez zgłaszającego; niektóre trwają nawet cztery miesiące. Propozycje z największą liczbą głosów (na dzień 31 stycznia) mają głosy pochodzące z ok. 2 % EOS w cyrkulacji, jednak większość propozycji ma bardzo niski udział głosujących (tylko 10 ma więcej niż 0,5 % udziału). Do tej pory najpopularniejsze propozycje to: [zmiana](https://bloks.io/vote/referendums/rex4all) tego, dokąd idą opłaty za krótkie nazwy i zakupy pamięci RAM, [usunięcie](https://bloks.io/vote/referendums/decaf) Głównego Forum Arbitrażowego EOS oraz [spalenie](https://bloks.io/vote/referendums/burnsaving) funduszy inflacyjnych w eosio.saving (do wykorzystania do finansowania systemu propozycji pracowniczych).

Fundacja NEM [ogłosiła](https://forum.nem.io/t/nem-foundation-message-to-the-community/21753), że ma trudności finansowe i musi zmniejszyć liczbę pracowników. Nowa rada przejęła fundację 1 stycznia i kiedy otworzyła księgi, zauważyła problem. Poprzednia rada zużywała środki w tempie ok. 9 milionów XEM miesięcznie (obecnie 360 tys. dolarów, znacznie więcej w tamtym czasie), które były wydawane przez niezależne jednostki regionalne z niewielką odpowiedzialnością na działania promocyjne, co uznane zostało za nietrwałe. Obecnie nowa rada zrestrukturyzowała fundację i poszukuje dodatkowych funduszy.

Opublikowana została [uaktualniona wersja badania pt. "forkonomia"](https://hackernoon.com/towards-an-analytical-discipline-of-forkonomy-summer-2018-e6da993ee3f9) aut. Wassima Alsindiego (@parallelind) wraz ze zaktualizowaną [kontynuacją](https://medium.com/@parallelind/forkonomia-revisited-where-are-they-now-73fbfbfbec6b4d).

Hcash sforkował [kolejne](https://archive.today/rEhWX) projekty Decred: [Autonomy](https://archive.today/KTCdX) (Politeia), [hcexplorer](https://archive.today/2KTtW) i [hctime](https://archive.today/K151A). W Politei, przypadkowo [usunęli](https://archive.today/ECplt) prawa autorskie programistów Decred i zapomnieli zmienić nazwę projektu. Po otrzymaniu powiadomienia szybko zareagowali usuwając wiele repozytoriów, [przywracając](https://github.com/TKFORKED/autonomy/commit/4b05c2c31829df64be69e546d939a563247e1927) licencję i [zmieniając nazwę](https://github.com/TKFORKED/autonomy/commit/98d5f63f676e45e6a91eba99da3db985effdb1f2) forka Politei na Autonomy. Kilka [pominiętych](https://twitter.com/michae2xl/status/1084270468234915840) subtelnych ikonek Decred zostało naprawionych. Niektóre [projekty](https://archive.today/https://github.com/HcashOrg/hc*) zostały sforkowane z wymazaną historią commitów i bez oznaczenia ich jako forki na GitHubie. Skargi ([1](https://www.reddit.com/r/hcash/comments/adwmx2/hcash_being_shady_again/), [2](https://www.reddit.com/r/hcash/comments/afepsc/hcash_cant_be_bothered_to_change_the_decred_logo/)) na ich subreddicie były po cichu [cenzurowane](https://archive.today/Edy7T) i pozostały bez odpowiedzi. Przy okazji, styl subreddita [r/hcash](https://archive.today/Edy7T) wygląda bardzo [znajomo](https://archive.today/e1rAw). Temat omówiony [tutaj](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$154696507010921TRgid:decred.org).

[Smutny przykład](https://twitter.com/BrianDColwell/status/1090286752831434752) tego, co może się stać, gdy zespołowi kończą się fundusze.

Projekty ICO [wycofały](https://diar.co/ethereum-ico-treasury-balances/) ~441K ETH (52,5 mln dolarów na 9 lutego) ze skarbców w grudniu 2018 r.

[Staked](https://staked.us/about/), startup świadczący usługi stakingowe dla inwestorów instytucjonalnych, pozyskał 4,5 mln USD od firm Pantera, Coinbase, DCG i innych. Relacja autorstwa [CoinDesk](https://www.coindesk.com/pantera-coinbase-join-4-5-million-round-in-staking-as-a-service-startup), [The Block](https://www.theblockcrypto.com/2019/01/31/winklevoss-twins-pantera-get-behind-a-new-business-thats-capitalizing-on-a-new-trend-sweeping-crypto-hedge-funds/) i [Bloomberg](https://www.bloomberg.com/news/articles/2019-02-01/some-crypto-investors-are-playing-it-safe-after-volatile-run). Od listopada 2018 roku Staked prowadzi [usługę VSP](https://decred.staked.us/) dla Decred.

Od teraz Binance [umożliwia](https://support.binance.com/hc/en-us/articles/360022498052) zakup krypto za pomocą kart Visa i MasterCard (a lista [ograniczeń](https://support.binance.com/hc/en-us/articles/360022204152) mówi nam coś na temat walut fiat).

Coinbase [zbanowało](https://cryptocoinspy.com/coinbase-bans-gab-again/) konta platformy społecznościowej Gab. Jest to [nie pierwszy](https://www.cnbc.com/2018/04/23/coinbase-suspends-wikileaks-bitcoin-account.html) duży przypadek zawieszenia kont przez tę giełdę.

Medium [ocenzurowało](https://bitcoinist.com/how-to-use-bitcoin-anonymously-ban-medium/) artykuł "Jak anonimowo korzystać z Bitcoina", który wywołał dyskusję i poruszył [kwestię](https://github.com/xaur/decred-issues/issues/70) odejścia od serwisu, lub przynajmniej traktowanie go jako jednego z wielu mirrorów treści. Na wszelki wypadek utwórz kopię zapasową swoich wpisów na Medium.

Bank Rozrachunków Międzynarodowych opublikował bardzo optymistyczne [badanie](https://www.bis.org/publ/work765.htm) na temat kryptowalut.

Odkryto [podatność na atak](https://cryptoslate.com/researchers-discover-vulnerability-bitcoin-ethereum-ripple-digital-signatures/) w podpisach cyfrowych Bitcoina i kilku innych systemów. Niewielki zestaw podpisów został wygenerowany przy użyciu nieprawidłowej implementacji algorytmu podpisu, co może  być wykorzystane do ujawnienia kluczy prywatnych. Jedynie parę tysięcy podpisów było podatnych na atak z prawie miliarda zbadanych podpisów Bitcoin. Według badaczy zdecydowana większość użytkowników kryptowalut nie musi się obawiać.

Największy [przypadek naruszenia danych](https://www.troyhunt.com/the-773-million-record-collection-1-data-reach/) w historii zawiera zbiór tysięcy zhakowanych baz danych. Dobrze się zastanów, komu udostępniasz swoje dane.

Cryptopia została [zhakowana](https://www.investinblockchain.com/cryptopia-hack-estimated-16-million-lost/) z szacunkowymi stratami wahającymi się od 3 do 16 milionów dolarów. Binance [zamroziło](https://www.investinblockchain.com/binance-freezes-funds-cryptopia-hack/) niektóre fundusze pochodzące z włamania.

Zgłoszono, że nowa fala infekcji hAnt (po raz pierwszy zaobserwowana w sierpniu) [obiera za cel](https://www.zdnet.com/article/new-ransomware-strain-is-locking-up-bitcoin-mining-rigs-in-china/) urządzenia do wydobycia Bitcoina. Oprogramowanie ransomware wymaga zainfekowania 1000 innych urządzeń lub zapłacenia 10 BTC, a w przeciwnym razie grozi spaleniem urządzenia. Do tej pory nie ma doniesień o zniszczonym sprzęcie.

Podatność na wyczerpanie zasobów, znana jako atak Fake Stake [została odkryta](https://medium.com/@dsl_uiuc/fake-stake-atake-attacks-on-chain-based-based-proof-of-stake-cryptocurrencies-b8b05723f806) w ponad 26 łańcuchach opartych na PoSv3, z których większość wdrożyła środki zaradcze. Częścią pierwotnej przyczyny jest to, że w wielu takich systemach warstwa Proof of Stake została "wszczepiona" do bazy kodu Bitcoin Core w sposób nie do końca bezpieczny. Jeden z autorów raportu na Twitterze stwierdził, że Decred [nie jest narażony na ów atak](https://twitter.com/Sanket1729/status/1087829688347701254).

## O tym wydaniu

To 10. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze opinie i komentarze są mile widziane na portalach Reddit, [GitHub](https://github.com/xaur/decred-news/issues) oraz [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Zasługi (w kolejności alfabetycznej): bee, davecgh, degeri, Dustorf, guang, Haon, jholdstock, liz_bagot, lukebp, matheusd, richardred, saender, zubairzia0.
