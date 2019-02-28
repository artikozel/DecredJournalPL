# Decred Journal – Styczeń 2019

![abstract art](../img/journal-201901-384.jpg "Out of the abstract to more objective future")

Decred dynamicznie rozpoczął rok 2019 miesiącem, w którym ukazały się ważne wydania nowych wersji oprogramowania i znaczące zmiany w innych częściach projektu.

Została wydana [nowa wersja oprogramowania](https://github.com/decred/decred-binaries/releases/tag/v1.4.0) dla węzłów i portfeli (v1.4.0), co, między innymi, zainicjuje głosowanie nad zasadami konsensusu, a zatem zaleca się terminową aktualizację.

Portfel mobilny Dcrandroid, który wykorzystuje tryb peer to peer SPV dla Decred został wydany (v1.0) i jest dostępny w [Google Play Store](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet).

Na platformie Politeia opublikowany został [wniosek o przedstawienie propozycji na zdecentralizowaną infrastrukturę giełdy wymian](https://proposals.decred.org/proposals/5431da8ff4eda8cdbf8f4f2e08566ffa573464b97ef6d6bae78e749f27800d3a) opisaną przez @jy-p w poprzednim wpisie na blogu.

Zakończony został proces konsultacji społecznościowych w celu zdefiniowania [podstawowego przekazu Decred](https://pastebin.com/E5L6u2RV), tagline wybrany jako część tej wiadomości to: "Decred: Bezpieczny. Adaptacyjny. Samofinansujący się". Działania w zakresie nawiązywania kontaktów przeniosły się na planowanie działań w ciągu bieżącego roku, a wstępne propozycje dotyczące wydatków na [wydarzenia](https://www.reddit.com/r/decred/comments/anhh8n/proposal_to_get_events_spending_approved_via/) i [marketing](https://www.reddit.com/r/decred/comments/aolr79/politeia_proposal_to_fund_marketing_ops_for_2019/) zostały opublikowane na czatach i Reddicie.

To wydanie Decred Journal obejmuje również początek lutego, ponieważ w pierwszym tygodniu lutego miał omiejsce kilka ważnych wydarzeń i uznano, że warto było by je uwzględnić przed lutowym numerem.

## Aktualizacja do wersji 1.4.0 i głosowanie konsensusowe

Oprogramowanie v1.4.0 dla węzła i portfela  zostały wydane. Pełne informacje o wydaniu i pliki do pobrania znajdują się [na GitHub](https://github.com/decred/decred-binaries/releases/tag/v1.4.0). Jak zawsze, upewnijcie się, że [zweryfikowaliście pobierane pliki](https://docs.decred.org/advanced/verifying-binaries/).

Wydanie niesie ze sobą znaczące ulepszenia, wraz z proponowaną zmianą zasad konsensusu, która naprawia błąd przy wsparciu Lightning Network. Operatorom węzłów zaleca się aktualizację, aby pomóc sieci osiągnąć próg aktualizacji. Po aktualizacji, wyborcy powinni ustawić swoje [preferencje głosowania](https://docs.decred.org/governance/how-to-vote/). Postęp aktualizacji można śledzić na stronie [voting.decred.org](https://voting.decred.org/).

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

* Zidentyfikowano brakującą [funkcję administratorską](https://github.com/decred/politeia/issues/662) do cenzurowania publicznych propozycji: musi istnieć sposób na usunięcie publicznej propozycji, która została zredagowana w taki sposób, aby przedstawiać obraźliwe treści. W przeciwnym wypadku, administratorzy musieliby przeglądać wszystkie zmiany, zanim znajdą się one na stronie z propozycjami.
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

@jy-p złożył propozycję ["RFP: Decred Decentralized Exchange Infrastructure"](https://proposals.decred.org/proposals/5431da8ff4eda8cdbf8f4f2e08566ffa573464b97ef6d6bae78e749f27800d3a). Przedstawia ona motywację i wysoki poziom projektu DEX opisanego po raz pierwszy w [poście](https://blog.decred.org/2018/06/05/A-New-Kind-of-DEX/) z czerwca 2018 r. Szacuje się, że projekt zostanie ukończony w mniej niż 6 miesięcy, a jego budżet wyniesie od 100 000 USD do 1 000 000 USD. Głosowanie odbędzie się w dwóch fazach: pierwszy wniosek określi, czy interesariusze są zainteresowani propozycją budowy DEX; jeżeli pierwszy wniosek zostanie zatwierdzony, wówczas zainteresowane zespoły zostaną zaproszone do składania propozycji, a w drugiej fazie zostanie wybrany jeden z nich. Proces ten nosi nazwę [zapytania ofertowego](https://en.wikipedia.org/wiki/Request_for_proposal).

Uruchomiony został program [Bug Bounty](https://twitter.com/decredproject/status/1087486930093264897) po udanym przegłosowaniu [propozycji](https://proposals.decred.org/proposals/d33a2667469b56942adf42453def6cc2292325251e4cf791e806939ea9efc9e1) w grudniu. Sprawdź zasady działania programu na nowej stronie internetowej [bounty.decred.org](https://bounty.decred.org/) oraz w poście wprowadzającym na [hackernoon](https://hackernoon.com/decred-launches-debug-decred-bug-bounty-program-7e4d2af27ec9). Zasługi dla @fernandoabolafio i @jholdstock za większość pracy nad stroną. W skład zespołu, który decyduje o ważności zgłoszeń i wypłat wchodzą @degeri, @dnldd, @fernandoabolafio, @jholdstock i @matheusd. Gratulujemy zespołowi uruchomienia!

@Dustorf przygotowuje propozycje poprawy przejrzystości i zwiększenia kontroli interesariuszy nad alokacją środków na działania marketingowe. [Propozycja przedwstępna](https://www.reddit.com/r/decred/comments/anhh8n/proposal_to_get_events_spending_approved_via/) odnośnie wydatków na wydarzenia została opublikowana na Reddicie w celu uzyskania informacji zwrotnej po pierwszej iteracji [na czacie](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154896889724431Mxlvj:decred.org). Propozycja przedwstępna odnośnie budżetu na marketing również rozpoczęła się [na czacie](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154897255124536mFHoo:decred.org) i wylądowała [na Reddit](https://www.reddit.com/r/decred/comments/aolr79/politeia_proposal_to_fund_marketing_ops_for_2019/) po pierwszej turze informacji zwrotnej i komentarzy.

@oregonisaac  [szuka](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$15474111512672Whvns:decred.org) programistów Java w celu oceny wymagań dotyczących integracji z bankomatami kryptowalutowymi. Projekt propozycji został opublikowany i omówiony [na czacie](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$154828004015153jWdiD:decred.org). Uzgodniono, aby używać procesu 2-etapowego głosowania nad zapytaniami ofertowymi. Innym dobrym punktem dyskusji było to, czy poczekać na wydanie aplikacji mobilnych przed przystąpieniem do pracy nad bankomatami.

Dyskusje:

* Propozycja Baeond wywołała [dyskusję](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$154687339790vCEoH:decred.org) na temat wektora ataku, w którym interesariuszom proponuje się zrzut jakiegoś żetonu w zamian za zatwierdzenie przez nich propozycji.
* [Dyskusja](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$15481365491827928DiBLm:matrix.org) na temat zaangażowania i zadowolenia z dotychczasowej działalności Politeii.
* W jaki sposób [usprawnienia UX](https://github.com/decred/politeia/issues/678) mogą pomóc głosującym w zapobieganiu złym propozycjom i zachowaniu czujności.

## Sieć

Hashrate: w styczniu hashrate wynosił  ~187 Ph/s na początku i ~225 Ph/s na końcu miesiąca, osiągając niż 144 Ph/s i szczyt na poziomie 312 Ph/s w ciągu miesiąca. Na 8 lutego dystrybucja mocy obliczeniowej puli wydobywczych wygląda następująco: Poolin 29%, F2pool 26%, BTC.com 19%, UUPool 8%, Luxor 4%, CoinMine 1% oraz pozostałe na poziomie 13% na [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: w dniu 4 lutego, za dcrstats.com, średnia cena biletu z okresu 30 dni wynosiła 109,4 DCR (+6,4). Cena wahała się między 101,5-111,6 DCR. Zablokowana kwota wynosiła 4,20-4,38 mln DCR, co odpowiadało 46,3-47,5% dostępnej podaży.

W styczniu zakupiono 90 biletów dzielonych. [Dane](https://gist.github.com/oregonisaac/8eb4d50af9fa888c920666fb73ba44b2) od maja 2018 r. wykazują stały wzrost.

Węzły: Na dzień 4 lutego [dcred.eu](https://dcred.eu/nodeStats) podało 197 publicznych węzłów nasłuchujących i 369 normalnych. Dystrybucja wersji: v1.5.0 dev: 4,3% (+2,8%), v1,4.0 dev i rc: 13% (+6%), v1.3.0: 55%, v1.2.0: 14% (-6%), v1.1.2: 8% (-2%), v1.1.0: 3% (-1%).

## Wydobycie

Partie Obelisk 2-5 [są wysyłane](https://us16.campaign-archive.com/?u=393b2698d17bdfe48ac0422ac&id=4211e39081), [update](https://us16.campaign-archive.com/?u=393b2698d17bdfe48ac0422ac&id=c501bf724d) oprogrmowanie sprzętowego dla 2. generacji zawiera nowe funkcje i poprawki błędów. Złożono [pozew zbiorowy](https://www.reddit.com/r/decred/comments/ae8hy8/class_action_lawsuit_officially_filed_against/) w związku ze sprzedażą SC1 i DCR1 przez firmę Obelisk.

W toku jest opersource'owa [implementacja puli wydobywczej](https://medium.com/decred/decred-independent-contractor-roadmap-884faba3db39) Decred autorstwa @dnldd.

## Integracje

Nowy VSP [dcr.grassfed.network](https://dcr.grassfed.network) dołączył do listy usługodsawców, sprowadzając ich całkowitą liczbę do 23.

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

* Went through several iterations of the foundational messaging document with significant community input and received positive feedback on the [final version](https://pastebin.com/E5L6u2RV). (discussions: [second](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154706728112462ubmNo:decred.org) version, [final](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154880432321730DYSYl:decred.org) version)
* Worked with the community to source commentary on 51% attacks for future use with reporters when another attack inevitably happens - the goal being to get Decred's message in front of journalists even when it doesn't have any hard news to share.
* Media trained three Decred members.
* Secured media coverage: [feature article](https://www.forbes.com/sites/leslieankney/2019/01/11/who-should-hold-power-decred-governance-and-what-it-means-for-investors/) in Forbes ([report](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$1547232200845NiZnO:decred.org)), [video interview](https://www.youtube.com/watch?v=CUxDxJ4YAUA) with Joshua for Bitsonline, commentary by @richardred on the delay in Ethereum's hard fork in [Breaker Mag](https://breakermag.com/what-we-know-about-the-vulnerability-behind-ethereums-rollback-of-constantinople/) and [Crypto Briefing](https://cryptobriefing.com/scaling-delay-ethereum-constantinople/).
* Drafted an announcement of the bug bounty program and [placed](https://hackernoon.com/decred-launches-debug-decred-bug-bounty-program-7e4d2af27ec9) it in Hacker Noon - thereby reaching a much broader pool of developers, compared to Decred's own channels.
* Facilitated two interviews that are pending media coverage.
* Flew down to the North American Bitcoin Conference, where Ditto facilitated interviews between Decred and reporters (Cheddar TV, Altcoin Buzz, etc.) and spent quality time with the team.
* Worked closely with Dustin on an events plan that encompasses both events Decred wants to speak at and events it wants to have a booth at.
* Submitted an application for Jake to speak at Consensus 2019.
* Worked closely with Dustin on a marketing and communications plan for the first half of 2019, spanning messaging, media training, media relations, events and speaking, and strategy. This plan is still pending.

Individuals are advised to share media coverage because amplification is just as important as the media placement itself.

For even more detail see the biweekly updates on [Jan 7](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154688457110052CiWYd:decred.org) and [Jan 18](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15478384869864RTCsv:decred.org). Nice discovery in one of them:

> The community welcomes and encourages questions, even if the person asking fears that their questions are "stupid." We've observed a spirit of collaboration and willingness to help that we haven't seen in other communities. It's refreshing!

Inne:

* It is [rumored](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$15478503329998HCAzR:decred.org) that Ditto can arrange a mad beard that entitles one to wear Silver Decred Jacket.
* @anshawblack [dropped](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154792069410439nSRtR:decred.org) Decred merch in all record stores of Miami.
* Decredible shop was [renewed](https://www.reddit.com/r/decred/comments/ae07as/custom_decred_merch_with_19_discount_in_the/) with extra items and new Decred logos. All products can be personalized and tweaked.

Urgent Notice: new batch of Stakey plushies is [available](https://www.reddit.com/r/decred/comments/ahalex/new_batch_of_stakey_plushies_available/)!

## Eventy:

Na których byliśmy:

* [The North American Bitcoin Conference](https://btcmiami.com/) in Miami, USA. Attendance was surprisingly low: 6K people were expected but only 1.8K were claimed after the event. @jy-p's presentation [Applications of Blockchain Time-Stamping](https://btcmiami.com/session/applications-of-blockchain-time-stamping/) was well done and well attended given the overall numbers. 3 members went through media training and found it useful, 7 more are scheduled. Store of value, "Secure. Adaptable. Self-Funding.", and the accompanying messaging was found to be a very effective way of talking about Decred. It was found to be most clear and impactful. Full report with links to photos and videos [here](https://github.com/heyvj/decred-events/blob/master/reports/20190116-tnabc-miami.md).
* [OKEx Global Meetup Tour](https://www.eventbrite.hk/e/okex-global-meetup-tour-2019-taiwan-tickets-54689867867) in Taipei, Taiwan. @morphymore told the story of Decred and how it works. "Compared to 2018, people are starting to recognize Decred better. A few people told me that they know about Decred from the Chinese translation I did last year of the Placeholder's Investment Thesis. It was very encouraging and shows that the Decred awareness in Taiwan is indeed growing." ([report](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15478245399446fDEQa:decred.org), [photos](https://photos.app.goo.gl/rXd9PeYmyAGrVTQN7))
* [10 lat Bitcoina](https://10latbitcoina.com.pl/) in Warsaw, Poland. @karamble talked about longevity in cryptocurrencies on the basis of Decred. The team of 4 people established relations with several crypto outlets and engaged with a few businesses. BitHub.pl noted: "The Decred boys were intensely engaged in answering questions of those interested displaying tons of patience at that, since the questions poured in basically all the time!". ([report](https://github.com/heyvj/decred-events/blob/master/reports/20190126-10LatBitcoina-Warsaw.md))

Nadchodzące:

* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) in Sao Paulo, Brazil on Feb 12-17.
* [How To Keep Your Crypto Secure](https://www.meetup.com/Decred-Australia/events/258211699/) in Melbourne, Australia on Feb 18.
* [Decred in 30 minutes](https://www.eventbrite.com/e/decred-en-30-minutos-tickets-55764142050) in Mexico City, Mexico on Feb 27. Contact @elian for details.
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) in Guadalajara, Mexico on Apr 22-26. Contact @elian if you're interested in helping/attending.

Open source and hacker oriented events like DEFCON, CCC and FOSDEM were discussed and captured in [this issue](https://github.com/xaur/decred-issues/issues/83).

## Media

Inicjatywy społecznościowe:

* [blog.dcrclub.org](https://blog.dcrclub.org/) is a new website in Chinese that collects various articles and translations in one place. The source hosted [on GitHub](https://github.com/0x5826/blog.dcrclub.org) makes it easy to contribute or mirror the website on other domain for more resiliency. Credits to @TogT4V (Telegram) for starting the site.
* New [Arabic blog](https://decred-arabia.blogspot.com/2019/01/blog-post.html) about Decred started by @butterfly (@arij on Matrix). There are some challenges with publishing arabic text on the web, advice is welcome in #writers_room.
* Portuguese podcasts [started](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$1548814257223928fVjiP:matrix.org) by @michae2xl, available on [Soundcloud](https://soundcloud.com/user-770106247/), Spotify, Apple Podcasts and Google Podcasts - search for "Decred Brasil".
* [@decredexplorer](https://twitter.com/decredexplorer) is a new Twitter account dedicated to dcrdata. Thanks to @michae2xl for organizing.
* @Matt D [introduced](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154825336714293nfWdU:decred.org) [Decred Aggregator](https://t.me/DecredAgg) Telegram channel. It aims to collect news, press, videos, podcasts, Decred announcements, trending tweets and Reddit posts, as well as market stats.
* @anshawblack is planning a podcast.

[Decred page](https://en.wikipedia.org/wiki/Decred) on Wikipedia was deleted. On Jan 8 a user [removed](https://archive.today/ApV3P) a bunch of "bad sources" and on Jan 10 vandalized the page by removing a large and important part of content. Just 4 hours later another user nominated Decred page for deletion - the [3rd attempt](https://en.wikipedia.org/wiki/Wikipedia:Articles_for_deletion/Decred_%283rd_nomination%29) to take it down. For background, the author of [2nd nomination](https://en.wikipedia.org/wiki/Wikipedia:Articles_for_deletion/Decred_%282nd_nomination%29) for deletion had interesting [views](https://archive.today/QAlRp) on notability and was [banned](https://en.wikipedia.org/wiki/User:Prince_of_Thieves) as a sockpuppet. On Jan 11 content removal was reverted and its author was banned as sockpuppet, but next day the removal was [applied again](https://archive.today/fZUHW) by another user without much commentary. After the slicing the page became very small and all reviewers [voted](https://en.wikipedia.org/wiki/Wikipedia:Articles_for_deletion/Decred_%283rd_nomination%29) to delete it due to lack of reputable sources. All suggested recent articles in major crypto media were deemed [not good enough](https://archive.today/4xwaN) references. On Jan 18 the page was deleted and removed from [List of cryptocurrencies](https://en.wikipedia.org/wiki/List_of_cryptocurrencies) that was left with more notable coins. Details and links to discussions are captured in [this issue](https://github.com/xaur/decred-issues/issues/79). Experienced Wikipedia editors are welcome to help.

Selected articles (chronological order):

* Understanding Decred Governance by Dr. Bitcoin (Chinese, [qq.com](https://mp.weixin.qq.com/s/z3hzILiPBsLJR72Q2tP7TQ), [translation](https://translate.google.com/translate?sl=auto&tl=en&hl=en&u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2Fz3hzILiPBsLJR72Q2tP7TQ), _missed in Dec issue_)
* Fundamental Analysis: Decred by Piotr Arendarski ([linkedin.com](https://www.linkedin.com/pulse/funadamental-analysis-decred-dcr-piotr-arendarski-ph-d))
* How to Last the Crypto Winter? Seek Simplicity, Manage Complexity by @jy-p ([coindesk.com](https://www.coindesk.com/how-to-last-the-crypto-winter-seek-simplicity-manage-complexity), tagline was collectively brainstormed in #marketing)
* Decred - an Interview with the Community Manager @donmario by Janusz Zielinski ([bithub.pl](https://bithub.pl/wywiady/decred-wywiad-z-community-managerem/))
* Best Decred Wallets: Top 6 Places to Store Your DCR by Steve Walters ([coinbureau.com](https://www.coinbureau.com/analysis/best-decred-wallets/), a nice case when authors were responsive and corrected all [reported issues](https://github.com/xaur/decred-issues/issues/68))
* Who Should Hold Power? Decred Governance and What It Means For Investors by Leslie Ankney ([forbes.com](https://www.forbes.com/sites/leslieankney/2019/01/11/who-should-hold-power-decred-governance-and-what-it-means-for-investors/))
* Decred Independent Contractor Roadmap for 2019 ([medium](https://medium.com/decred/decred-independent-contractor-roadmap-884faba3db39))
* The Unique Consensus Mechanism of Decred - Is This True Decentralization? by Paul de Havilland ([bitsonline](https://bitsonline.com/consensus-mechanism-of-decred-decentralization/))
* Decred as Store of Value by Yin Guochao, inspired by Forbes article (Chinese, [qq.com](https://mp.weixin.qq.com/s/_-lY0rtWSPiyLPZeTRR7gg), [translation](https://translate.google.com/translate?sl=auto&tl=en&hl=en&u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2F_-lY0rtWSPiyLPZeTRR7gg))
* Blockchain Project Review: Decred: 8.4 Autonomous Digital Currency by Evaluape ([medium](https://medium.com/@EVALUAPE1/blockchain-project-review-decred-8-4-autonomous-digital-currency-323771d65529), Decred rated 8.4/10)
* Decred coin review: Replacing BTC? by Edwin (Dutch, [bitcoinsaltcoins.nl](https://www.bitcoinsaltcoins.nl/decred-coin-review-vervanger-van-btc/), Decred scored 8.8/10)
* 3 Cryptocurrencies to HODL during This Crypto Winter (Opinion) by Daniel Frumkin ([investinblockchain.com](https://www.investinblockchain.com/cryptocurrencies-hodl-during-crypto-winter/))
* Fundamental Value in Crypto; Bitcoin and Decred as Store of Value Investments by LCC Investment Research ([seekingalpha.com](https://seekingalpha.com/article/4235521-fundamental-value-crypto-bitcoin-decred-store-value-investments))
* The role of Decred voters in defending against majority attacks by @richardred ([medium](https://medium.com/@richardred/the-role-of-decred-voters-in-defending-against-majority-attacks-ec658af0a8fd))
* Decentralized off-chain governance in the context of digital currencies by @Haon ([goodaudience.com](https://blog.goodaudience.com/decentralized-off-chain-governance-in-the-context-of-digital-currencies-ef6db7d97412))
* Decred Infrastructure Interviews: Stephen, founder of crypto-only luxury goods marketplace CryptoEmporium by @kozel ([medium](https://medium.com/@artikozel/decred-infrastructure-interviews-stephen-founder-of-crypto-only-luxury-goods-marketplace-68d3214a4fd7))
* Decred Review by Lee Banfield ([weeklyglobalresearch.wordpress.com](https://weeklyglobalresearch.wordpress.com/2019/01/31/decred-dcr-review/))

Tłumaczenia:

* [Detailed analysis of Decred fork resistance](https://medium.com/decred/detailed-analysis-of-decred-fork-resistance-93022e0bcde7) by @Haon - [in Russian](https://medium.com/decred-russia/%D0%B4%D0%B5%D1%82%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9-%D0%B0%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7-%D1%83%D1%81%D1%82%D0%BE%D0%B9%D1%87%D0%B8%D0%B2%D0%BE%D1%81%D1%82%D0%B8-decred-%D0%BA-%D1%84%D0%BE%D1%80%D0%BA%D1%83-b30c78f764ea) by @DZ
* Decred Journal - December 2018 [in Chinese](https://www.jianshu.com/p/65e7a83ac27c) by @guang, [in Polish](https://github.com/artikozel/DecredJournalPL/blob/master/journal/201812_DecredJournalPL.md) by @kozel, [in Portuguese](https://medium.com/@maiconjunge/jornal-decred-dezembro-de-2018-947c616b894f) by @maiconjunge, [in Russian](https://medium.com/decred-russia/decred-journal-%D0%B4%D0%B5%D0%BA%D0%B0%D0%B1%D1%80%D1%8C-2018-9528f7a9d24d) by @DZ and [in Spanish](https://medium.com/@decred_es/revista-decred-diciembre-2018-79093f957aac) by @elian. Wow. Thank you all for spreading Decred Journal around the world! All translations are listed [here](https://xaur.github.io/decred-news/).

Wideo:

* Applications of Blockchain Time-Stamping - talk by @jy-p at TNABC ([youtube](https://www.youtube.com/watch?v=3RRTidXh_Lw))
* Interviews at TNABC: [with @joshuam](https://www.youtube.com/watch?v=Kyihc6Uh4XA) by Hack Crypto, [with @joshuam](https://bitsonline.com/decred-disputes-inevitable-buirski/) by Bitsonline, [with @DZ](https://www.youtube.com/watch?v=h3bII-vjOsA), [with @jz](https://www.youtube.com/watch?v=4oKRVXGN6Fs) by CNBC Crypto Trader.
* Governance: Blockchain's Most Overlooked Pillar - talk by @oregonisaac at Token Forum 2 ([tfblock.io](https://www.tfblock.io/post/governance-blockchain-s-most-overlooked-pillar))

Audio:

* Taking a Deep Dive into Autonomous Cryptocurrency with Decred - @moo31337 and @BAB talk how decentralized decision-making and self-funding have enabled Decred to build a robust, evolving digital currency, free from third party influence (The Crypto Chick Podcast with Rachel Wolfson, [badcryptopodcast.com](https://badcryptopodcast.com/2019/01/08/autonomous-crypto-decred/))
* Noah Pierau on Blockchain Governance: Decred, Bitcoin, Dash, Ethereum (51percent Crypto Research by Tom Shaughnessy, [itunes](https://itunes.apple.com/us/podcast/noah-pierau-on-blockchain-governance-decred-bitcoin/id1438148082?i=1000428113722&mt=2))
* How Decred Revolutionizes Funding in Crypto with Marco Peereboom - Michael Nye and Marco discuss current state of crypto, how Decred began, PoW vs PoS, Decred's funding model and more (Evolvement Podcast, [evolvement.io](https://evolvement.io/how-decred-revolutionizes-funding-in-crypto-with-marco-peereboom/))

## Dyskusje społeczności

Community stats as of Feb 4:

* Twitter followers: 39,778 (-106)
* Reddit subscribers: 9,330 (+89)
* Matrix users: 247 (+26)
* Slack users: 6,529 (+110)
* Telegram users: 4,503 (-231)
* YouTube subscribers: 3,752 (+14)
* Facebook followers: 3,132 (+11), likes: 2,891 (+11)
* LinkedIn followers: Decred page 466 (+16), Politeia page 27 (+3)
* GitHub dcrd stars: 468 (+10), forks: 1,221 (+29)

Comm systems news:

* Slow Twitter [follower bleed](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$1549500437341uJIFK:decred.org) continues for unkown reasons. Any ideas are welcome.
* Drop in Telegram user count is likely due to a bot purge.
* @sambiohazard wrote a thorough [plan](https://github.com/xaur/decred-issues/issues/16) to address Discord spam, implemented it, and reported no spam after first few weeks. Several important channels were bridged with Discord. With this in place we can finally appreciate Discord as an opportunity to onboard more people. Thank you!
* [decred.org/matrix](https://decred.org/matrix/) guides new matrix users into the system.
* [decred-issues](https://github.com/xaur/decred-issues) grew to 105 issues as of Feb 9. Check it out, perhaps you'll find something interesting to do!

[Criticism](https://twitter.com/tonevays/status/1086702239853379584) from Bitcoin maximalists triggered a [discussion](https://www.reddit.com/r/decred/comments/ahuawl/decred_launch_security_laws/) on how Decred looks in context of securities laws. One vector critics use is that Decred's premine and airdrop was not fair and "hand selected". This is a misrepresentation of the (huge) manual effort to filter out airdrop cheaters, per [this discussion](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154810656412322VrQLg:decred.org) that also has many useful links describing Decred's launch. One interesting insight shared is that ~300K (35%) airdropped coins never moved. Another related [chat](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$15467943549316LjeYZ:decred.org) was about Twitter attacks claiming how Decred's initial distribution was not transparent or fair, while avoiding inconvenient facts about Bitcoin's early mining and Satoshi's million BTC. Finally, a [history lesson](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15467944729319gvTvt:decred.org) explained early days of staking and made a point that original devs had no unilateral control of consensus rules from day 1.

Huge debate about importance of building Reddit community [here](https://www.reddit.com/r/decred/comments/aib2x3/noah_pierau_on_blockchain_governance_decred/).

## Rynki

In January DCR was trading between USD 15.5-19.5 / BTC 0.00435-0.00487. The average daily rate was $17.1.

## Ważne kwestie i wiadomości poboczne

Ethereum Classic (ETC) was subject to a 51% attack, with the alert being raised by [CoinNess](https://www.coinness.com/news/198264) on Jan 7. Coinbase then [announced](https://blog.coinbase.com/ethereum-classic-etc-is-currently-being-51-attacked-33be13ce32de) that it had detected a deep reorganization of the ETC chain and had halted ETC transactions. The article lists a number of reorgs that involved double spends, putting the total amount involved at $1.1 million, across 15 distinct reorg events. Coinbase was not itself a target for these attacks. The Gate.io exchange subsequently [announced](https://www.gate.io/article/16735) that it had been targeted and had lost around $200K, and that it would absorb the loss. Gate.io also significantly increased the number of confirmations required for ETC deposits. In an unusual development, the attacker then [returned](https://www.gate.io/article/16740) $100K of the ETC to Gate.io, they have tried but failed to make contact with the attacker and do not know the reason for the return of funds. Other victims of the ETC double spends have not come forward.

Ethereum's developers [decided](https://www.coindesk.com/ethereum-developers-give-tentative-greenlight-to-asic-blocking-code) (tentatively) on Jan 4 to go ahead with a change of mining algorithm from Ethash to ProgPoW. This move is intended to stop ASICs from mining Ethereum. The Block [outlined](https://www.theblockcrypto.com/2019/01/11/despite-core-dev-consensus-proposition-progpow-faces-community-concerns/) concerns like reduced attack cost after the switch, weaker incentives of GPU miners, questionable benefit of transfer of power from Bitmain and Innosilicon to AMD and Nvidia, and a possible chain split. They concluded that the debate around the algorithm switch will be a good test for Ethereum's governance process.

Ethereum developers also [delayed](https://breakermag.com/what-we-know-about-the-vulnerability-behind-ethereums-rollback-of-constantinople/) the Constantinople hard fork on Jan 15 after a security vulnerability which would have enabled a "reentrancy attack" was [detected](https://medium.com/chainsecurity/constantinople-enables-new-reentrancy-attack-ace4088297d9).

Fundamentals of Proof of Work [article](https://blog.sia.tech/fundamentals-of-proof-of-work-beaa68093d2b) by David Vorick makes the case for exclusive hardware cryptocurrencies and contrasts them with shared hardware cryptocurrencies that suffer from multiple issues, especially those pursuing ASIC resistance. One of the issues with non specialized hardware is that the hardware's value is not closely related to the asset (because it can mine many other chains). Another issue is hashrate marketplaces, they allow hardware owners to get more profit by not caring about which coin they mine, even if the hashrate is rented to attackers. Decred benefits from specialized hardware and is by far the dominant coin for its algorithm (Blake256r14). Although this hardware cannot be considered "exclusive" to Decred, in addition to current hashrate dominance for its algorithm Decred has the PoS factor which is capable of denying rewards to misbehaving miners.

The first round of Aragon proposal voting [concluded](https://blog.aragon.org/final-results-from-aragon-network-vote-1/) on Jan 26. Of the 12 submitted proposals, 3 were excluded from the vote by the Aragon Foundation (1 because of lack of full time leadership and engineering talent, 2 were excluded to reduce cognitive load on voters). 8 of the 9 proposals voted on were [approved](https://mainnet.aragon.org/#/governance.aragonproject.eth/0x277bfcf7c2e162cb1ac3e9ae228a3132a75f83d4) by ANT holders, with one proposal (to change the voting period duration from 48 hours to 1 week) rejected. ANT participation rates [ranged](https://mainnet.aragon.org/#/governance.aragonproject.eth/0x277bfcf7c2e162cb1ac3e9ae228a3132a75f83d4) from 2.3 to 7.8%. The most expensive [proposal](https://github.com/aragon/flock/blob/master/teams/Aragon%20One/2019.md) to be approved will pay Aragon One $4 million for 2019 operating costs plus an incentive package consisting of 1.675 million ANT on a 5 year vesting schedule. An incentive in ANT with a vesting schedule was included as part of most proposals, in addition to the main cost to be paid in DAI. In total this round of approved proposals will cost around $5.94 million + 2.52 million ANT (~$880K).

The EOS referendum system for constitutional amendments went [live](https://medium.com/@eosnationbp/the-fate-of-eos-is-in-the-hands-of-token-holders-3d345147ef6) on Jan 11. So far 77 proposals have been [submitted](https://bloks.io/vote/referendums). The voting period for these proposals is flexible and specified by the submitter, some last as long as four months. The proposals with the most votes (as of Jan 31) have votes from around 2% of circulating EOS, but most proposals have very low participation (only 10 have greater than 0.5% participation). So far the most popular proposals are to [change](https://bloks.io/vote/referendums/rex4all) where the fees for short names and RAM purchases go, [delete](https://bloks.io/vote/referendums/decaf) the EOS Core Arbitration Forum, and [burn](https://bloks.io/vote/referendums/burnsaving) the inflation funds in eosio.saving (to be used for funding the worker proposal system).

The NEM Foundation [announced](https://forum.nem.io/t/nem-foundation-message-to-the-community/21753) that it is in financial difficulty and needs to downsize its workforce. A new council took over the foundation on Jan 1 and when they opened the books they saw a problem. The previous council had a burn rate of 9 million XEM per month ($360K now, considerably more at the time) which was spent by independent regional entities on promotional activities with little accountability. This was deemed not sustainable, and the new council has restructured the foundation and is presently seeking additional funds.

Updated version of the "forkonomy" research by Wassim Alsindi (@parallelind) was [published](https://hackernoon.com/towards-an-analytical-discipline-of-forkonomy-summer-2018-e6da993ee3f9) along with an up-to-date [follow-up](https://medium.com/@parallelind/forkonomy-revisited-where-are-they-now-73fbfbec6b4d).

Hcash forked a few [more](https://archive.today/rEhWX) Decred projects: [Autonomy](https://archive.today/KTCdX) (Politeia), [hcexplorer](https://archive.today/2KTtW) and [hctime](https://archive.today/K151A). In Politeia, they accidentally [removed](https://archive.today/ECplt) copyright of Decred developers and forgot to rename the project. After being notified they quickly reacted by removing multiple repositories, [reinstating](https://github.com/TKFORKED/autonomy/commit/4b05c2c31829df64be69e546d939a563247e1927) the license and [renaming](https://github.com/TKFORKED/autonomy/commit/98d5f63f676e45e6a91eba99da3db985effdb1f2) the Politeia fork to Autonomy. A few [missed](https://twitter.com/michae2xl/status/1084270468234915840) subtle Decred icons were fixed. Some [projects](https://archive.today/https://github.com/HcashOrg/hc*) were forked with their commit history erased and without marking them as forks on GitHub. Complaints ([1](https://www.reddit.com/r/hcash/comments/adwmx2/hcash_being_shady_again/), [2](https://www.reddit.com/r/hcash/comments/afepsc/hcash_cant_be_bothered_to_change_the_decred_logo/)) on their subreddit were silently [censored](https://archive.today/Edy7T) with no reply. Oh, and [r/hcash](https://archive.today/Edy7T) styles look [familiar](https://archive.today/e1rAw). Discussed [here](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$154696507010921TRgid:decred.org).

A [sad example](https://twitter.com/BrianDColwell/status/1090286752831434752) of what can happen when the team runs out of money.

ICO projects [withdrew](https://diar.co/ethereum-ico-treasury-balances/) ~441K ETH ($52.5M as of Feb 9) from treasuries in December 2018.

[Staked](https://staked.us/about/), a startup that provides staking services for institutional investors, raised $4.5M from Pantera, Coinbase, DCG and others. Covered by [CoinDesk](https://www.coindesk.com/pantera-coinbase-join-4-5-million-round-in-staking-as-a-service-startup), [The Block](https://www.theblockcrypto.com/2019/01/31/winklevoss-twins-pantera-get-behind-a-new-business-thats-capitalizing-on-a-new-trend-sweeping-crypto-hedge-funds/) and [Bloomberg](https://www.bloomberg.com/news/articles/2019-02-01/some-crypto-investors-are-playing-it-safe-after-volatile-run). Staked operates a Decred [VSP](https://decred.staked.us/) since Nov 2018.

Binance now [allows](https://support.binance.com/hc/en-us/articles/360022498052) one to buy crypto with Visa and MasterCard (and the list of [restrictions](https://support.binance.com/hc/en-us/articles/360022204152) tells us something about fiat).

Coinbase [banned](https://cryptocoinspy.com/coinbase-bans-gab-again/) accounts of social media platform Gab. This is [not the first](https://www.cnbc.com/2018/04/23/coinbase-suspends-wikileaks-bitcoin-account.html) big case of account suspension by the exchange.

Medium [censored](https://bitcoinist.com/how-to-use-bitcoin-anonymously-ban-medium/) an article "How to use Bitcoin anonymously" which spurred discussion and an [issue](https://github.com/xaur/decred-issues/issues/70) about migrating away from it, or at least treating it as one of multiple content mirrors. Backup your Medium posts, just in case.

Bank for International Settlements released a very optimistic [study](https://www.bis.org/publ/work765.htm) of cryptocurrencies.

[Vulnerability](https://cryptoslate.com/researchers-discover-vulnerability-bitcoin-ethereum-ripple-digital-signatures/) was discovered in digital signatures of Bitcoin and a few other systems. A tiny set of signatures was generated using an incorrect implementation of signature algorithm which can be used to reveal private keys. Only a few thousand signatures were vulnerable out of nearly a billion Bitcoin signatures examined. According to researchers, the vast majority of cryptocurrency users need not worry.

Largest [data breach](https://www.troyhunt.com/the-773-million-record-collection-1-data-reach/) in history contains a collection of thousands of hacked databases. Choose wisely who you share data with.

Cryptopia was [hacked](https://www.investinblockchain.com/cryptopia-hack-estimated-16-million-lost/) with loss estimates varying between $3-16 million. Binance [froze](https://www.investinblockchain.com/binance-freezes-funds-cryptopia-hack/) some funds coming from the hack.

New wave of hAnt infections (first seen in August) was [reported](https://www.zdnet.com/article/new-ransomware-strain-is-locking-up-bitcoin-mining-rigs-in-china/) targeting Bitcoin mining rigs. The ransomware demands to infect 1,000 other devices or pay 10 BTC, else it threatens to burn the rig. There have been no reports of destroyed equipment so far.

Resource exhaustion vulnerability known as Fake Stake attack was [discovered](https://medium.com/@dsl_uiuc/fake-stake-attacks-on-chain-based-proof-of-stake-cryptocurrencies-b8b05723f806) in 26+ blockchains based on PoSv3, the majority of them deployed mitigations. Part of the root cause is that in many such systems the Proof of Stake layer was "grafted in" to the Bitcoin Core codebase insecurely. One of report's authors tweeted that Decred is [not affected](https://twitter.com/Sanket1729/status/1087829688347701254).

## O tym wydaniu

This is the 10th issue of Decred Journal. Index of all issues, mirrors and translations is available [here](https://xaur.github.io/decred-news/).

Most information from third parties is relayed directly from source after a minimal sanity check. The authors of Decred Journal have no ability to verify all claims. Please beware of scams and do your own research.

Your feedback and contributions are welcome on Reddit, [GitHub](https://github.com/xaur/decred-news/issues) and [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Credits (alphabetical order): bee, davecgh, degeri, Dustorf, guang, Haon, jholdstock, liz_bagot, lukebp, matheusd, richardred, saender, zubairzia0.
