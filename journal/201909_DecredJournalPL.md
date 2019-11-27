# Decred Journal – Wrzesień 2019

![abstrakcja](../img/journal-201909-384.jpg)

_Obraz: Sezonowość na łańcuchu, aut. @saender_

* Do rodziny projektów Decred dołączyło nowe oprogramowanie do wydobycia PoW typu stratum, dcrpool. Wysokiej jakości oprogramowanie wydobywcze open source jest rzadkością, a konieczność dysponowania takim oprogramowaniem jest barierą w uruchomieniu nowych pul wydobywczych PoW. dcrpool wypełnia tę lukę, wyrównując pole do gry tak, że każdy może rozpocząć swój prywatny lub publiczny mining pool. Powinno to przynieść korzyści w postaci decentralizacji mocy wydobywczej PoW poprzez ograniczenie korzyści płynących z ekonomii skali, która sprzyja dużym poolom.
* Wyszedł dcrstakepool v1.2.0. To wydanie jest zwieńczeniem prac rozwojowych, które rozpoczęły się we wrześniu 2017 r. i przynosi szereg ulepszeń, w tym odpowiedni interfejs dla administratorów do obsługi biletów zakupionych z niewystarczającymi opłatami, odnowiony wygląd front-endu, udoskonalenia bezpieczeństwa, zaktualizowaną terminologię, zmniejszone uzależnienie od stron trzecich i różne poprawki błędów.
* Wrzesień był wielkim miesiącem integracji, owocujący, między innymi, obsługą DCR dodaną do portfela Trust, portfela Exodus mobile, oraz rozszerzeniem Joule do przeglądarki Chrome do płatności w LN.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Zaimplementowano [wersję 2 filtrów kompaktowych](https://github.com/decred/dcrd/pull/1856). Wykorzystują one mniej miejsca niż filtry v1, co będzie usprawnieniem dla lekkich klientów (SPV). Ponadto, filtry v2 będą stosowane w [zobowiązaniach nagłówków bloków](https://proposals.decred.org/proposals/0a1ff846ec271184ea4e3a921a3ccd8d478f69948b984445ee1852f272d54c58).

Moduł `mempool` [otrzymał](https://github.com/decred/dcrd/pull/1901) drobniejsze i dokładniejsze kody błędów. Usunięto kilka starych kodów związanych z wydobyciem, w tym [usunięcie](https://github.com/decred/dcrd/pull/1736) `getblocktemplate` na rzecz `getwork`.

Oprócz tego wprowadzono wiele mniejszych zmian w zakresie refaktoringu, ulepszonego zakresu testów i dokumentacji oraz poprawek błędów.

[dcrwallet](https://github.com/decred/dcrwallet): Kod Go dcrwallet używa teraz w nazwie modułu `decred.org` zamiast `github.com`. Pomysł, aby wdrożyć to rozwiązanie szerzej w celu zmniejszenia zależności od GitHub, jest omawiany [tutaj](https://github.com/decred/dcrd/issues/1264).

Dodano obsługę kompilacji dla Go 1.13 i porzucono dla 1.11.

Kontynuowane są prace nad integracją [wsparcia CoinShuffle++](https://github.com/decred/dcrwallet/pull/1541).

[Decrediton](https://github.com/decred/decrediton): wyświetlanie kont otrzymało stopniowe [ulepszenia](https://github.com/decred/decrediton/pull/2178), podczas gdy zakładka bezpieczeństwo wzbogacona została o wyświetlanie informacji [pochodnych](https://github.com/decred/decrediton/pull/2184) dla adresów należących do portfela (przydatne do celów debuggingu).

Integracja z siecią Lightning Network jest [bliska ukończenia](https://github.com/decred/decrediton/pull/2107). Kontynuowane są prace nad [refaktoryzacją fazy uruchamiania](https://github.com/decred/decrediton/pull/2182) na maszynie stanu skończonego, aby uczynić ją bardziej wytrzymałą.

[Politeia](https://github.com/decred/politeia): Zmiana designu Politei jest dostępna na stronie [testnet](https://test-proposals.decred.org/); testowanie i opinie są mile widziane.

Poczyniono znaczne postępy w zakresie CMS, z [podwalinami](https://github.com/decred/politeia/pull/980) pod system propozycji DCC i scaleniem [funkcjonalności](https://github.com/decred/politeia/pull/981), która umożliwia wykonawcom interakcję z systemem, wraz z szeregiem mniejszych usprawnień i poprawek błędów zarówno na stronie CMS, jak i propozycji. Nadchodzącymi priorytetami na stronach z propozycjami są [propozycje RFP](https://github.com/decred/politeia/issues/966) i [integracja Trillian](https://github.com/google/trillian), która umożliwi oznaczanie czasem poszczególnych elementów treści.

[dcrstakepool](https://github.com/decred/dcrstakepool): ważna nowa wersja 1.2 właśnie wylądowała na gałęzi master.

Do front-endu dodano nową stronę administracyjną do obsługi biletów z niskimi opłatami. Strona ta wyświetli wszystkie bilety, które zostały zakupione z niewystarczającą opłatą i pozwoli administratorowi na ręczne dodanie lub usunięcie tych biletów z listy kwalifikujących się biletów do głosowania. Wcześniej operacja ta musiała być wykonywana ręcznie poprzez bezpośrednią manipulację bazą danych.

Nowy design front-endu podnosi dcrstakepool do profesjonalnego standardu stawianego innym programom, np. Decrediton.

Na prośbę operatorów VSP zaimplementowano obsługę szyfrowanych połączeń SMTP, w tym obsługę certyfikatów z własnym podpisem. Dzięki temu VSP mogą chronić wiadomości e-mail dotyczące rejestracji i odzyskiwania konta w trakcie przesyłu za pomocą protokołu SMTPS.

Cała komunikacja z dcrwallet przechodzi teraz przez stakepoold. Ta zmiana architektoniczna obniża liczbę połączeń RPC przechodzących przez sieć, zmniejsza złożoność kodu i pozwala na zamknięcie portów pomiędzy dcrstakepool i dcrwallet.

Własny magazyn danych MySQL zastąpił rozwiązanie oparte na przechowywaniu plików do przechowywania ciasteczek sesji. Rozwiązanie to rozwiązuje kilka znanych problemów bezpieczeństwa związanych z danymi sesji.

reCAPTCHA od Google zostało zastąpione przez utrzymywane na własnych serwerach rozwiązanie zaimplementowane [w języku Go](https://github.com/dchest/captcha). Wszystkie wymagane do tego zasoby są teraz hostowane przez VSP, a nie przez stronę trzecią. Frontend zawarty w tym wydaniu w ogóle nie wykonuje zewnętrznego JavaScriptu, co znacznie zwiększa bezpieczeństwo i prywatność użytkowników.

Wprowadzono kilka ulepszeń w zakresie bezpieczeństwa, aby zapobiec atakom typu "cross-site forgery" (CSRF), wyciekom danych prywatnych do osób trzecich, złośliwym połączeniom i buforowaniu poufnych informacji przez przeglądarki.

Wydanie to jest wynikiem 160 pull requestów od 20 autorów, złożonych od września 2017 r. Szczegółowe informacje na temat tego wydania można znaleźć w dokumencie [notatki do wydania](https://github.com/decred/dcrstakepool/releases/tag/v1.2.0).

[dcrpool](https://github.com/decred/dcrpool): Po ponad roku pracy, opensource'owy mining pool dla Decred wreszcie został [wydany](https://twitter.com/decredproject/status/1176914732399439873) wraz z [postem na blogu](https://blog.decred.org/2019/09/25/Introducing-Dcrpool/) na jego temat. Funkcje dcrpool:

* może działać jako prywatny lub publicznie dostępny pool
* Wspiera wszystkie rodzaje maszyn do wydobycia
* dostępne tryby płatności to PPS i PPLNS
* ma internetowy interfejs użytkownika ze statystykami i danymi konta
* szczegóły połączenia dla wszystkich urządzeń
* analiza pracy i wypłat dla konta

Opracowane przez @dnldd w Go, oprogramowanie to jest ważnym krokiem w decentralizacji wydobycia PoW dla Decred. Gratulujemy wydania!

[dcrlnd](https://github.com/decred/dcrlnd): W końcu [scalono](https://github.com/decred/dcrlnd/pull/36) ogrom pracy w zakresie sportowania pull requestów z głównego repozytorium projektu.

Rozpoczęły się prace nad włączeniem funkcji [zdalnego portfela](https://github.com/decred/dcrlnd/pull/40). Dzięki temu użytkownicy mogą korzystać z istniejącego portfela zamiast korzystania z innego portfela z osobnym ziarnem dla dcrlnd. Pozwala to również na uruchomienie portfela LN bezpośrednio dla portfela działającego w Decrediton, poprawiającym i ułatwiając tym samym doświadczenie użytkownika.

[cspp](https://github.com/decred/cspp): dodano obsługę [ponownego połączenia](https://github.com/decred/cspp/pull/18), zaktualizowano instrukcje konfiguracji, dodano kompilacje Go 1.13, oraz wprowadzono poprawki błędów.

[dcrdex](https://github.com/decred/dcrdex): kładzione są [fundamenty](https://github.com/decred/dcrdex/issues/8) w postaci tysięcy linijek kodu scalonych z gałęzią master. Dodano początkowe backendy dla [DCR](https://github.com/decred/dcrdex/pull/17) i [BTC](https://github.com/decred/dcrdex/pull/26). Specyfikacja przeszła kilka drobnych [zmian](https://github.com/decred/dcrdex/pulls?q=is%3Apr+is%3Aclosed+label%3Aspec+merged%3A2019-09-01..2019-09-30).

W przeciwieństwie do innych programów wykorzystujących licencję ISC, dcrdex wybrał BlueOak. Motywacja tego rozwiązania została omówiona w [tej dyskusji](https://matrix.to/#/!EzTSRQITaqHuFBDFhM:decred.org/$RaxvOZy5x4cby5rwhph7gUED6LR0yQkKIihst4C5Og4).

[dcrandroid](https://github.com/decred/dcrandroid): Prace nad nowym interfejsem użytkownika są kontynuowane w ramach przebudowy [strony domowej](https://github.com/decred/dcrandroid/pull/401) i innych usprawnień w celu dostosowania aplikacji do standardowych zaleceń dotyczących projektowania aplikacji dla systemu Android. Rozpoczęły się prace nad [wsparciem dla wielu portfeli](https://github.com/raedahgroup/dcrlibwallet/pull/57). Pozwoli to użytkownikom na zaimportowanie klucza publicznego z Decrediton, aby mogli monitorować status swoich biletów z telefonu.

[dcrios](https://github.com/raedahgroup/dcrios): Refaktoryzacja jest w toku, aby wykorzystać nowe [metody filtrowania transakcji](https://github.com/raedahgroup/dcrlibwallet/pull/48) w dcrlibwallet. Obejmuje to przebudowę [strony historii](https://github.com/raedahgroup/dcrios/pull/515), nową [strukturę danych](https://github.com/raedahgroup/dcrios/pull/520) do przechowywania transakcji oraz przebudowę [strony wysyłania](https://github.com/raedahgroup/dcrios/pull/521), aby umożliwić użytkownikom wysyłanie DCR do wielu miejsc docelowych jednocześnie.

[Synchronizacja w tle](https://github.com/raedahgroup/dcrios/pull/518) została usprawniona i stała się bardziej niezawodna. Dotyczy to problemu, który napotkali niektórzy użytkownicy, gdy synchronizacja łańcucha została przerwana z powodu uśpienia telefonu.

Optymalizacja interfejsu użytkownika trwa wraz z przebudową [strony głównej](https://github.com/raedahgroup/dcrios/pull/512).

[docs](https://github.com/decred/dcrdocs): Dodano [stronę](https://github.com/decred/dcrdocs/pull/960) dla [dcrtime](https://docs.decred.org/advanced/dcrtime/).

Kontynuowane są prace nad dokumentacją deweloperską, która wkrótce ma zostać przeniesiona z prywatnego repozytorium do organizacji Decred na GitHub dla lepszej widoczności.

[decred.org](https://github.com/decred/dcrweb): aktualizacja stron [mapy rozwoju](https://decred.org/roadmap/), [portfeli](https://decred.org/wallets/) i [giełd wymian](https://decred.org/exchanges/).

Kilka projektów zmieniło system ciągłej integracji (CI) z Travis CI na GitHub Actions. Actions jest szybszy, lepiej zintegrowany, ma charakter open source, jest współdzielony i ogólnie rzecz biorąc jest znacznie bardziej elastyczny, jeśli chodzi o to, na co zezwala.

Statystyki aktywności deweloperskiej na wrzesień: 248 aktywnych PR-ów, 201 master commitów, 28 tys. dodanych i 17 tys. usuniętych linijek kodu spośród 15 repozytoriów. Wkład pochodził od 2-8 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: imestin ([dcrdocs](https://github.com/decred/dcrdocs/commits?author=imestin)), Muharem Hrnjadovic ([politeia](https://github.com/decred/politeia/commits?author=al-maisan)), Amir Massarwa ([politeiagui](https://github.com/decred/politeiagui/commits?author=amassarwi)).

@s\_ben napisał świetny [artykuł](https://medium.com/@seth.benton/i-dump-coins-on-you-ee6db4331e18) na portalu Medium odnośnie swoich odczuć i doświadczeń w kwestii pracy dla DAO Decred, gdzie popełnia obserwacje o płynności finansowej,  zmienności rynku, nagabywaniu na kupno i podbijaniu cen, oraz swoich planów na przyszłość.

Statystyki społeczności na dzień 2 października:

* Użytkownicy platformy Politeia: 181 (+7)
* Obserwujący na Twitterze: 40578 (-19)
* Subskrybenci na Reddit: 9631 (+37)
* Użytkownicy na Matrixie: 436 (+24)
* Użytkownicy na Slacku: 6851 (+17)
* Użytkownicy na Discordzie: 2487 (+45), zweryfikowani z możliwością pisania postów: 325 (+15)
* Użytkownicy na Telegramie: 3048 (-100)
* Subskrybenci na YouTube: 3830 (+11)
* Obserwujący na Facebooku: 3278 (+7), polubień: 3003 (+4)
* Obserwujący na LinkedIn: 622 (+19)
* GitHub: 517 gwiazdek (+1) i 1394 forki repozytorium dcrd (+11)

## Zarządzanie

We wrześniu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 14 510 DCR i wydał 7 810 DCR (uwaga: wydatki miały miejsce na początku października). Wykorzystując dzienną średnią dzienną stawkę DCR/USD we wrześniu, wynoszącą 22,02 USD, otrzymaliśmy 320 000 USD i wydaliśmy 172 000 USD. Ponieważ płatności te zostały dokonane za pracę wykonaną w sierpniu, warto również rozważyć je w kontekście średniej dziennej stawki z sierpnia wynoszącej 26,23 USD - w tym przypadku kwota wydana w USD wynosi 205 000 USD. Na dzień 2 października saldo Skarbca wynosi 641 802 DCR (11 mln USD po kursie 17,12 USD).

i2 Trading wygrał konkurs, aby stać się wyznaczonym animatorem rynku Decred, z zatwierdzeniem propozycji na poziomie 68% vs 49% dla Tantra Labs i 47% dla Grapefruit Trading. i2 przyciągnęło również wyższy udział biletów, wynoszący 41%, w porównaniu z 36% dla Tantry i 33% dla Grapefruit (frekwencja jest teraz widoczna na [dcrdata alpha](https://alpha.dcrdata.org/proposals)).

Tantra Labs pogratulowała i2, opublikowała [post](https://medium.com/@TantraLabs/proof-of-politeia-ac87f52243f4) na temat swoich doświadczeń z Politeią i oświadczyła, że zamierza kontynuować swój plan tworzenia rynków DCR i skonsultuje się w tej sprawie z i2.

[Propozycja](https://proposals.decred.org/proposals/f0d1bd7447182328b44c691de88cb660b63df17f1f3a94990af19acea57c09bb) @permabullnino  zatytułowana "Badanie i publikacja wskaźników on-chain dla par DCRUSD i DCRBTC została przyjęta stosunkiem 83% głosów za i 27% frekwencji. Permabull napisze 4-6 artykułów na temat HODLer's Price (HHP) w ciągu około 3 miesięcy. Za już opublikowane prace Permabulla zostanie naliczone 3500 USD, a za nowe prace publikacje 13000 USD.

[Propozycja](https://proposals.decred.org/proposals/fdd68c87961549750adf29e178128210cb310294080211cf6a35792aa1bb7f63) dotycząca "Eventów i wydarzeń Decred w CIS w 2019-2020" została odrzucona przy 4 % głosów za i 25 % frekwencji.

[Wydanie 22](https://medium.com/politeia-digest/issue-22-september-1-12-2019-d82f5f617c92) Politeia Digest zawiera więcej informacji na temat tych propozycji. Druga połowa września była spokojna na platformie Politeia; nowy numer Politeia Digest zostanie opublikowany, gdy pojawią się nowe propozycje.

## Sieć

Hashrate: wrześniowy hashrate na początku miesiąca wyniósł ~619 Ph/s a zamknął miesiąc w ok. ~472 Ph/s, zaliczając niż w ok. 404 Ph/s oraz szczyt w wys. 679 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 2 października wyglądała następująco: UUPool 21%, Poolin 19%, F2Pool 19%, lab.antpool.com 5,8%, BTC.com 2,9%, Luxor 2,12%, Coinmine 0,10%, BeePool 0,10%, suprnova 0,03% i pozostałe 30% za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu z okresu 30 dni wynosiła 128,70 DCR (-1,35) za danymi z dcrstats.com. Cena wahała się między 121,92-134,4 DCR. Zablokowana kwota wynosiła 5,22-5,33 mln DCR, co odpowiadało 49,87-51,15% dostępnej podaży.

Węzły: Przez cały [wrzesień](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1567296000000&to=1569888000000) były około 182 węzły nasłuchujące i 406 węzłów normalnych za danymi z dcr.farm. Około 81% z nich operowało na dcrd v1.4.0, 6,5% dcrwallet v1.4.0 a 6% to wersje v1.5.0(pre) dev na dzień 4 października.

Średnia z miesiąca [września](https://charts.dcr.farm/d/DHPdAO4Wz/lightning-network?orgId=1&from=1567296000000&to=1569888000000) przedstawia dane testnetu LN DCR następująco: 17 węzłów, 35 kanałów, oraz całkowitą pojemność 227 DCR.

## Integracje

[Trust Wallet](https://trustwallet.com/), oficjalny [portfel Binance](https://www.binance.com/en/blog/295063453682311168/Trust-Wallet-20-One-App-for-All-Your-Crypto), [zapowiedział](https://twitter.com/TrustWalletApp/status/1175864708961845253) dodanie Decred.

Exodus [dodał](https://twitter.com/exodus_io/status/1168886493617840131) Decred do swojego mobilnego portfela, o co bardzo często prosili użytkownicy. W odpowiedzi na pytanie zadane na Twitterze, Exodus zalinkował ich [stanowisko](https://support.exodus.io/article/89-is-exodus-open-source) w sprawie oprogramowania typu open source.

Wsparcie dla Decred zostało [dodane](https://github.com/joule-labs/joule-extension/pull/230) do [Joule](https://lightningjoule.com/), popularnego rozszerzenia Chrome, które pozwala użytkownikom płacić za pośrednictwem Lightning Network i używać swojego węzła jako tożsamości w sieci.

Giełda [Uphold](https://uphold.com/) dodała [wsparcie](https://twitter.com/UpholdInc/status/1172526504837693440) dla [Decred](https://twitter.com/decredproject/status/1172564615546511362) jako część swojej kampanii #15daysofcrypto.

[StealthEX](https://stealthex.io/) [dodało](https://twitter.com/StealthEX_io/status/1172201037958008837) DCR. Serwis oferuje anonimową i natychmiastową wymianę kryptowalut bez konieczności zakładania konta.

Giełda wymian błyskawicznych [InstaEx](https://instaex.io/) [dodała](https://twitter.com/instaex_io/status/1174367851139850241) handel DCR i złożyła [pull request](https://github.com/decred/dcrweb/pull/720), aby zostać dodaną na decred.org. W krótkim [porównaniu](https://medium.com/@instaex/instant-crypto-exchange-comparison-instaex-vs-changelly-vs-changenow-47770175bd54) z konkurencją, serwis twierdzi, że, między innymi, nie wymaga podawania adresu e-mail ani żadnej weryfikacji tożsamości.

Warunki zarówno [StealthEx](https://stealthex.io/terms), jak i [InstaEx](https://instaex.io/) zabraniają korzystania z serwisów w wielu krajach.

[Tokenview](https://tokenview.com/en) [dodał](https://twitter.com/tokenview2018/status/1176394157327147008) wyświetlanie [danych blockchaina](https://dcr.tokenview.com/en) Decred do swojego wielowalutowego eksploratora bloków.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

Wrześniowe wysiłki w dziedzinie nawiązywania kontaktów skupiały się na edukacji i szerzeniu świadomości w zakresie niedawnego wdrażania polityki prywatności. Dla artykułów [Analiza krajobrazu prywatności](https://www.notion.so/Transaction-Privacy-75c4bd707c194de18ff5d943f8909e26) i [prywatność Decred](https://www.notion.so/Privacy-Keynote-4902c63379894765a545351f8fcc7d7f) stworzone zostały prezentacje, a organizatorzy społeczności Decred na całym świecie zaprezentowali funkcję prywatności na różnych spotkaniach. @jy-p udał się do San Francisco i Los Angeles, prezentując prywatność na spotkaniach Decred w obu miastach oraz prezentując krajobraz prywatności na San Francisco Bitcoin Meetup. @Dustorf opublikował wpis na blogu pt. [Prywatność Decred - dłuższa droga do celu](https://medium.com/decred/decred-privacy-taking-the-long-road-62d218223db6), kontekstualizujący prywatność z perspektywy wartości i rozwoju.

Decred in Depth wydał [odcinek](https://soundcloud.com/decredindepth/dcr-checkmate) goszczący @Checkmate, gdzie zagłębił się w swoje badania nad Decred. Decred Assembly opublikuje wkrótce odcinek Deep Dive z udziałem developera Decred @jrick, gdzie omawia on wiele niuansów związanych z dążeniem do osiągnięcia prywatności przez projekt Decred, jej implementacji oraz dalszych kroków w temacie.

Decred i Exodus przeprowadzili [giveaway](https://twitter.com/decredproject/status/1171900177365569536) Trezora Model Ts dla 3 najlepszych tweetów wyjaśniających, dlaczego autor kocha Decred. Gratulujemy zwycięzcom [@encldi](https://twitter.com/decredproject/status/1172577786227281920), [@OfficialCryptos](https://twitter.com/decredproject/status/1172578137948983297) i [@dcrstack](https://twitter.com/decredproject/status/1172578432343040000)!

Wrześniowe osiągnięcia Ditto:

* Zdobyliśmy następujące relacje w mediach: artykuł o Skarbcu Decred w [Crypto Briefing](https://cryptobriefing.com/decred-venture-capital-centralizing/) oparty na wywiadzie z @richardred; wywiad z @jy-p na POV Crypto Podcast, odcinek trafnie zatytułowany "[W poszukiwaniu niezależności](https://povcryptopod.libsyn.com/77-discovering-decred-w-jake-y-p)"; [wywiad](https://open.spotify.com/show/4y3hF660v5FNPpRlg9muCC) z @lukebp w podcaście The Daily Chain; profil Decred w [Blockchain Tech News](https://www.blockchaintechnews.com/articles/company-profile-decred-aims-to-deliver-decentralized-future/).
* Zdobyliśmy slot dla głównego przemówienia dla @jy-p na SF Bitcoin Meetup, gdzie wygłosił on prezentację na temat krajobrazu prywatności. W spotkaniu wzięło udział ponad 50 uczestników z różnych projektów. Ogólnie rzecz biorąc, obecność Decred na SF Bitcoin Meetup była dużym zwycięstwem! Przemówienie Jake'a było [transmitowane na żywo](https://www.youtube.com/watch?v=LgLfMLFfOHQ?t=191). Ditto spędził również świetny czas z @anshaw i @jy-p podczas ich wizyty w San Francisco.
* Skoordynowaliśmy wysiłki z dziennikarzami i innymi entuzjastami krypto w LA i SF, aby zawieźć uczestników na spotkania w ostatnim tygodniu września.
* Skoordynowaliśmy wysiłki z organizatorami Voice of Blockchain w Chicago, gdzie @jy-p wygłosi nie 1, ale 2 prezentacje: jedną na temat zdecentralizowanego procesu przyznawania grantów i finansowania (jako część panelu z The Block) oraz jedną na temat tego, dlaczego bezpośrednia suwerenność i zarządzanie w oparciu o mnogość interesariuszy nigdzie się nie wybiera.
* Zabezpieczyliśmy dwa wywiady z @jy-p.
* @liz\_bagot wzięła udział podcaście Decred in Depth z @anshaw - odcinek już wkrótce.
* Zbliżamy się do ukończenia prac nad repozytorium zasobów edukacyjnych.
* Skoordynowaliśmy promocję narracji nt. prywatności Decred na Twitterze ze społecznością.
* Nowy członek zespołu Ditto, Anastasia, dołączyła do Margaret Mei, Leslie Ankney i Liz Bagot na wszystkich naszych różnych projektach Decred. Witamy!

## Eventy

Na których byliśmy:

* 25 sierpnia - Poolin China Mining Tour - Szanghaj, Chiny. @Dominic został zaproszony do wzięcia udziału w panelu dyskusyjnym na temat PoW i wygłosił przemówienie na temat Decred. Ciekawostka - Poolin stał się ostatnio [2. co do wielkości](https://twitter.com/officialpoolin/status/1171451086999191557) mining poolem dla Bitcoin, i wnosi około [90 Ph/s](https://twitter.com/NoahPierau/status/1171527633391079424) mocy obliczeniowej do sieci Decred. ([statystyki eventu](https://twitter.com/officialpoolin/status/1166702227727310848), [zdjęcia](https://twitter.com/wanbihou/status/1166028812305321985), _pominięte w wydaniu sierpniowym_)
* 4 września - [Campus Party](https://brasil.campus-party.org/campus-party-goias/) - Goiânia, Brazylia. Członkowie zespołu Decred przeprowadzili łącznie 5 prezentacji na temat sieci blokchain, konsensusu, Decred i Lightning Network. (zdjęcia: [1](https://twitter.com/Decred_BR/status/1171402110031847424), [2](https://twitter.com/Decred_BR/status/1170136831272325121), [3](https://twitter.com/Decred_BR/status/1169812440051109888).
* 5 września - [Blockchain Summit](https://blockchainsummit.uy/) - Montevideo, Urugwaj. @camilolwi i @pablito przedstawili przegląd projektu Decred zatytułowany "Wspólne zarządzanie" i rozmawiali z programistami i dziennikarzami po zakończeniu imprezy. Pełny raport ze wszystkimi odnośnikami medialnymi został [opublikowany](https://github.com/decredcommunity/events/blob/master/reports/20190905-blockchainsummituy-montevideo-uruguay.md) w repozytorium wydarzeń.
* 5 września - [Digital Economy](https://twitter.com/Decred_ES/status/1169677346506297344) - La Paz, Boliwia. Zespół @elian zaprezentował projekt lokalnej społeczności przedsiębiorców i entuzjastów z Bolivian Mind Blockchain. ([raport](https://twitter.com/elianhuesca/status/1170055934284111872) ze zdjęciami)
* 7 września - Tech4Amazonia - La Paz, Boliwia. Wydarzenie to polegało na zbieraniu datków na walkę z pożarami po boliwijskiej stronie Amazonki. @elian zaprezentował projekt studentom inżynierii Uniwersytetu Publicznej El Alto. ([zdjęcia](https://twitter.com/elianhuesca/status/1171034359027195904))
* 10 września - [Decred Privacy](https://www.meetup.com/Permissionless-Society/events/dnkzvqyzmbnb/) - Amsterdam, Holandia. @Haon przedstawił przegląd istniejących projektów w zakresie ochrony prywatności i wprowadził podejście Decred do tej tematyki. Pełny raport z linkami do mediów jest [tutaj](https://github.com/decredcommunity/events/blob/master/reports/20190910-decred-privacy-amsterdam-netherlands.md).
* 12 września - [Decred Meetup](https://twitter.com/Decred_ES/status/1171471998989389824) - Morelia, Meksyk. @francov_ i @luisantoniocrag zorganizowali pierwsze spotkanie w Morelii i, między innymi, odpowiadali na pytania małego dziecka, które wydawało się kumać, o co chodzi w projekcie Decred. ([zdjęcia](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$1568342471606746ojsnf:matrix.org))
* 18 września - [Warsztaty Bitcoin i Blokchain](https://www.facebook.com/events/959839374354073/) - Oaxaca, Meksyk.
* 18 września - [Wielka Debata nt. Bitcoin vs Blockchain](https://www.meetup.com/BlockchainMelbourne/events/264425160/) - Melbourne, Australia. @eSizeDave wziął udział w debacie na temat "Czy blokchain ma konkretny przypadek wykorzystania oprócz bezpiecznego pieniądza?" jako członek drużyny Bitcoina, przeciwko drużynie Blockchaina, którzy reprezentowali mentalność "blockchain rozwiązaniem na wszystko". Organizacja imprezy nie była korzystna dla zespołu Bitcoin, który przegrał w ostatecznym głosowaniu. Jednakże, @eSizeDave zdołał umieścić Decred i zarządzanie w centrum uwagi kilka razy, wraz z bajeczną koszulką Decred. Przeczytaj jego przemyślenia, wraz z pewną mądrością na temat efektywnego uczestniczenia w wydarzeniach, w [tym raporcie](https://github.com/decredcommunity/events/blob/master/reports/20190918-the-great-bitcoin-vs-blockchain-debate-melbourne-australia.md).
* 20 września - [Szkielet zarządzania blockchainem](https://www.eventbrite.com/e/a-framework-for-blockchain-governance-tickets-70134180221) - Waszyngton DC, USA. @akinsawyerr uczestniczył w prezentacji na temat zarządzania z Thomasem Coxem z [StrongBlock](https://strongblock.io/) w [Blockshop](https://www.blockshopdc.com/). Udzielał się w sesji pytań i odpowiedzi na temat zarządzania blockchainem oraz perspektyw procesu zarządzania w projekcie Decred.
* 21 września - [French Vibes Connection](https://twitter.com/Decred_ES/status/1160669435989856256) - Mexico City, Meksyk. Był to promocyjny eksperyment, w którym logo Decred zostało zmieszane z efektami wizualnymi, a elektroniczne zespoły zagrały swoje utwory tłumowi ludzi. @francov_ zauważa: "To było niezwykłe, projekty Decred były niesamowite i wraz z muzyką, stworzono środowisko, w którym Decred bardzo się wyróżniał, pojawiły się zainteresowane osoby, które pytały kim jesteśmy."" (filmy wideo: [1](https://twitter.com/elianhuesca/status/1175609208705863681), [2](https://twitter.com/elianhuesca/status/1175610899006197761); [instagram](https://www.instagram.com/p/B268Uougtbo/))
* 21 września - [Decred Meetup](https://twitter.com/DecredArabia/status/1171117988461854721) - Casablanca, Maroko. @arij (@butterfly) opowiedziała o swoich doświadczeniach jako współpracowniczka Decred, zarządzaniu w Decred, prywatności i jej przyszłych planach. Ludzie byli bardzo zainteresowani i chętni do nauki do tego stopnia, że zostali na godzinę po zakończeniu imprezy, i poprosili o więcej spotkań, a nawet kursów na uniwersytetach i w stowarzyszeniach. ([raport](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$156914094936513JoWdj:decred.org), [zdjęcia](https://twitter.com/in_insaf/status/1175692906826481664))
* 23 września - [SF Bitcoin Meetup](https://www.meetup.com/San-Francisco-Bitcoin-Social/events/dhdhsqyzmbgc/) - San Francisco, USA. @liz\_bagot odnotowała: "@jy-p dał solidny przegląd monet nastawionych na prywatność i otrzymał wiele pytań na koniec. Pojawiło się około 50 osób z różnych projektów i środowisk. Wielki sukces Decred - nikt z Decred nigdy wcześniej nie przemawiał na spotkaniu Bitcoin!". _(choć całkowicie szczerze, @camilolwi i @pablito dzielnie [zaryzykowali](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$156529022111295SCOiX:decred.org) swoje życie miesiąc [wcześniej](201908.md#events) na Espacio Bitcoin)_. Gospodarzem wydarzenia był [Starfish](https://twitter.com/starfishsf), a prezentacja była [transmitowana na żywo](https://www.youtube.com/watch?v=LgLfMLFfOHQ?t=191) na YouTube.
* 24 września - [Decred Privacy](https://twitter.com/decredproject/status/1174374566359183360) - San Francisco, USA. @jy-p dał przegląd krajobrazu prywatności i dogłębną analizę podejścia Decred do tego zagadnienia. Wydarzenie było sponsorowane i prowadzone przez Coinbase Custody. ([zdjęcia](https://twitter.com/HaileyLennonBTC/status/1176697168196849664))
* 25 września - [La Conexión](https://twitter.com/Conexion_Events/status/1165075848782852101) - Buenos Aires, Argentyna. @elian zaprezentował wysokopoziomowy przegląd Decred i jego historii, prowadził małe stanowisko Decred i rozmawiał z uczestnikami. Dzień przed imprezą @elian i @victorubin zjedli lunch z kilkoma lokalnymi osobistościami z branży krypto. Argentyńczycy są bardzo technologicznie zaawansowani i szukają alternatywy dla swojej waluty, która w tym roku może osiągnąć 50% inflację: "Od taksówkarzy po sprzedawców sklepowych, wszyscy wiedzą o bitcoinie i innych kryptowalutach". ([raport](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15704543735491DFGIA:decred.org), zdjęcia: [1](https://twitter.com/victorarubin/status/1176926844916043782), [2](https://twitter.com/victorarubin/status/1176933542762287104)).
* 26 września - [Inauguracyjny meetup Decred](https://twitter.com/MattDavidKaye/status/1164974520081342464) - Los Angeles, USA. @jy-p mówił o podstawach, technologii, zarządzaniu i przyszłości Decred. Wydarzenie prowadzone przez Blockhead Capital. (zdjęcia: [1](https://twitter.com/Tantra_Labs/status/1177412535059808256), [2](https://twitter.com/degeri_crypto/status/1177412554101932032))
* 27 września - [Crypto Fest](https://argentinacryptofest.com/) - Córdoba, Argentyna. @elian i @victorarubin przedstawili kolejny wysokopoziomowy przegląd Decred i skorzystali z okazji, aby nawiązać kontakt z członkami lokalnej społeczności Bitcoin i blockchain. Warto wspomnieć, że wydarzenie to zostało wspierane przez władze lokalne. Przeczytaj pełny raport @elian i wrażenia na temat Argentyny [tutaj](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15704543735491DFGIA:decred.org). (lub poczekaj na wersję GitHub). (zdjęcia: [1](https://twitter.com/victorarubin/status/1177976167145586693), [2](https://twitter.com/victorarubin/status/1178038340505030658)).
* 27 września - [Blockchain dla biznesów i rządów](https://www.eventbrite.com/e/blockchain-para-empresas-y-gobierno-tickets-72417321157) - Monterrey, Meksyk. Alteumx (meksykańska giełda wymian) zaprosiła @luisantoniocrag do wzięcia udziału w tym wydarzeniu, podczas którego miał okazję porozmawiać z opinią publiczną (biznesmenami i politykami) na temat Decred. ([zdjęcia](https://twitter.com/Decred_ES/status/1178690139008229376))
* 28 września - [Bali Block Confex](https://bali.blockconfex.com/) - Legian, Indonezja. Duyen Em rozmawiał z ludźmi na imprezie o Decred, rozdał pocztówki i nawiązał kilka znajomości. Większość ludzi słyszy o Decred po raz pierwszy i wielu z nich dość szybko interesuje się projektem. Pełny raport jest [tutaj](https://github.com/decredcommunity/events/blob/master/reports/20190928-bali-block-confex-legian-indonesia.md).
* 30 września - [Voice of Blockchain](https://twitter.com/BlockchainVoice/status/1154772731575099392) - Chicago, USA. @jy-p mówił o decentralizacji alokacji kapitału i dlaczego bezpośrednia suwerenność będzie trwać w przyszłości. (zdjęcia: [1](https://twitter.com/BlockchainVoice/status/1179100328102203392), [2](https://twitter.com/BlockchainVoice/status/1179088345638621185))

Na których będziemy:

* 17 października - Blockchain and Decred - Morelia, Meksyk. @luisantoniocrag i @francov_ będą mówić o blockchainie i Decred na uniwersytecie w mieście Morelia.
* 29-31 października - [Światowa Konferencja Krypto](https://worldcryptocon.com/) - Las Vegas, USA. @akinsawyerr wystąpi na panelu zatytułowanym "Praktyki zarządzania" oraz wygłosi prezentację zatytułowaną: "Zarządzanie wspólnymi zasobami krypto". Prezentacja będzie uwydatniać proces zarządzania Decred w przeciwieństwie do innych działań w przestrzeni publicznych blockchainów.
* 31 października - Blockchain APAC - Do potwierdzenia i ogłoszenia.
* 4-7 listopada - [Web Summit](https://websummit.com/) - Lizbona, Portugalia. Decred będzie miał stoisko.
* 16 listopada - [BitConf](https://www.bitconf.com.br/portal/) - São Paulo, Brazylia. Jest to jedno z największych wydarzeń branży krypto w Ameryce Łacińskiej. Zespół Decred zaprezentuje około 3 wykłady.

W sumie do [repozytorium wydarzeń](https://github.com/decredcommunity/events) dodano 4 nowe raporty, a w najbliższym czasie pojawi się jeszcze 1. Dla przypomnienia, repozytorium służy do zbierania doświadczeń z wydarzeń na całym świecie w jednym miejscu i udostępnia linki do raportu, które można rozpowszechniać. Repozytorium można łatwo kopiować w celu ochrony danych, a raport można składać nawet bez opuszczania swojego terminala.

Dziękujemy wszystkim za pisanie i przesyłanie raportów w celu poszerzenia naszej bazy wiedzy!

## Media

Wybrane artykuły:

* Decred: Teza inwestycyjna, aut. Wally Hansen ([medium](https://medium.com/coinmonks/decred-an-investment-thesis-bf9ba3cd1042)) - To wyczerpujące streszczenie Decred oraz ocena możliwości i ryzyka pojawiły się znikąd, zestawione ze źródeł publicznych przez entuzjastyczną zainteresowaną stronę.
* Przedstawiamy dcrpool, aut. @dnldd ([blog.decred.org](https://blog.decred.org/2019/09/25/Introducing-Dcrpool/)) - Wpis na blogu przedstawiający i opisujący przesłanki budowy mining poola stratum typu open source dla Decred.
* Zasypuję Was swoimi monetami, aut. @s\_ben ([medium](https://medium.com/@seth.benton/i-dump-coins-on-you-ee6db4331e18))
* Prywatność Decred - dłuższa droga do celu, aut. @Dustorf ([medium](https://medium.com/decred/decred-privacy-taking-the-long-road-62d218223db6))
* Pisanie propozycji na platformie Politeia (Pi) , aut. Decred Dragon ([medium](https://medium.com/@decreddragon/writing-proposals-on-politeia-pi-e345621652a2))
* Jak Decred dąży do zbudowania zdecentralizowanego modelu zarządzania, aut. @evok3d ([bitsonline](https://bitsonline.com/decred-decentralized-governance/))
* Eksperyment Decred: Czy decentralizacja może pomóc Meksykowi? aut. @evok3d ([medium](https://medium.com/@evok3d/the-decred-experiment-can-decentralization-help-mexico-1e0e8156430c))
* Dowód Politei, aut. Tantra Labs ([medium](https://medium.com/@TantraLabs/proof-of-politeia-ac87f52243f4))
* DAOs i brakujące ogniwo: protokoły reputacji, aut. @s\_ben ([medium](https://medium.com/sourcecred/the-dao-missing-link-reputation-protocols-8e141355cef2))
* Decred Lead: Firmy kapitału wysokiego ryzyka są "bardzo centralizującą" siłą, aut. Paddy Baker ([cryptobriefing.com](https://cryptobriefing.com/decred-venture-capital-centralizing/))

Tłumaczenia:

* Iterując prywatność [w jęz. arabskim](https://github.com/Insaf01/decred-arabic/blob/master/articles/iterating-privacy.md), aut. @arij, [w jęz. rosyjskim](https://medium.com/decred-russia/iterating-privacy-6d242f78a648), aut. @DZ oraz [w jęz. portugalskim](https://stakey.club/translated/iterating-privacy/), aut. @mm
* Okazuje się, że wiele wcześniejszych artykułów zostało przetłumaczonych na jęz. portugalski dzięki uprzejmości [stakey.club](https://stakey.club/pt/translated/)
* Kolejne tłumaczenia Decred Journal na jęz. arabski (@arij), chiński (@Dominic i spółka), polski (@kozel), rosyjski (@DZ), hiszpański (@francov\_ i  @luisantoniocrag) oraz wietnamski (@duyenemdo). Dziękujemy za szerzenie dobrego słowa!

Wideo:

* Decred Assembly Deep Dive: Decentralizacja Skarbca, z udziałem Marco Peereboom ([youtube](https://www.youtube.com/watch?v=4N8Fq1tU3XM))
* @jy-p mówi o prywatności na San Francisco Bitcoin Meetup ([youtube](https://www.youtube.com/watch?v=LgLfMLFfOHQ?t=191))
* @akinsawyerr mówi o wpływie blockchaina i zdecentralizowanych finansów na rynki wschodzące i przygraniczne podczas Global Startup Movement ([youtube](https://www.youtube.com/watch?v=OIO1q1UO4qM)).

Audio:

* Decred in Depth odc. 8 z udziałem @Checkmate - Checkmate mówi o stosie wartości DCR i stosunku *stock to flow*, metrykach on-chain dla Bitcoina i Decred, zabezpieczeniach pieniężnych, zrównoważonym finansowaniu w celu przyciągnięcia zaangażowanych współpracowników oraz własnych planach badawczych. ([youtube](https://www.youtube.com/watch?v=2JbMWgJUoSQ), [soundcloud](https://soundcloud.com/decredindepth/dcr-checkmate))
* POV Crypto Podcast odc. 76 - @jy-p dołącza do załogi POV Crypto w odcinku zatytułowanym "W poszukiwaniu niezależności", w którym rozważane są podstawy Bitcoina i Decred, suwerenność, wsteczna kompatybilność i prywatność. ([youtube](https://www.youtube.com/watch?v=WnY3c-F5caw), [libsyn](https://povcryptopod.libsyn.com/77-discovering-decred-w-jake-y-p))

## Dyskusje społeczności

Nowinki z platform komunikacyjnych:

* Konto Telegram Chrisa Burniske zostało [zhakowane](https://twitter.com/cburniske/status/1177747319426621440) a osoby, które je przejęły prosiły ludzi o przesłanie mu krypto. Upewnij się, że [masz ustawione hasło](https://twitter.com/cburniske/status/1180527281350955008) na Telegramie. Jest to również dobre przypomnienie, aby sprawdzić swoją obronę przed atakami zamiany kart SIM.
* Podszywanie się pod innych na Discordzie poprzez Discord Nitro staje się coraz bardziej powszechne. Nitro pozwala na zmianę imienia _oraz_ kodu identyfikacyjnego.
* [Airdrop](https://archive.today/GXimX) Decred, gdzie dostajesz darmowe ETH bez dwóch zdań nie jest twoim przyjacielem.
* Ogólnie rzecz biorąc, zwracajcie uwagę i zgłaszajcie wszelkie podejrzane konta i grupy na wszystkich platformach.

Wybrane wątki z Reddita:

W tej sekcji zazwyczaj znajdują się wątki z Reddita, które miały znaczną liczbę komentarzy, przy czym wiele z tych postów ma niskie wyniki, a zatem niską widoczność na Reddicie.

* Abstrakcyjna terminologia dotycząca [poziomów prywatności](https://www.reddit.com/r/decred/comments/d0jg3l/abstract_terminology_about_levels_of_privacy/) - dyskusja na temat postu na blogu poświęconego przeglądowi prywatności.
* Zaskakująca dyskusja społeczności Decred za [pytaniem](https://www.reddit.com/r/decred/comments/d6kt1v/random_decred_reddit_community_question/) o to, dlaczego liczba członków online na subreddicie /r/decred jest konsekwentnie wysoka w stosunku do całkowitej liczby subskrybentów.
* Z jakiej [funkcji lub narzędzia](https://www.reddit.com/r/decred/comments/dappgf/what_decred_feature_or_tool_would_you_want_more/) Decred chciałbyś, żeby korzystało najwięcej członków społeczności?
* Czy dostępny jest przewodnik po kupnie i korzystaniu z [dzielonych biletów?](https://www.reddit.com/r/decred/comments/d50wkw/ticket_splitting_guide_available/)
* [Analiza](https://www.reddit.com/r/decred/comments/d1c69a/analysis_of_ticket_voting_so_far_on_the_market/) dotychczasowego głosowania na propozycje animatora rynku.

Wybrane dyskusje z Twittera:

* Teza Decred w dwie minuty, aut. @Dustorf ([9 tweetów](https://twitter.com/lefebvre_dustin/status/1174789127105105928)), na podstawie pracy Wally'ego Hansena.
* [Wideo](https://twitter.com/karamblez/status/1178346009178644481) wizualizujące działalność repozytoriów btcsuite i Decred od 2013 r., aut. @karamblez
* @Checkmate w temacie [hashrate'u](https://twitter.com/_Checkmatey_/status/1177650799050133504) w porównaniu z innymi aktywami.
* @Checkmate na temat [Stock to Flow](https://twitter.com/_Checkmatey_/status/1173672584933777408) dla Bitcoina i Decred.
* [Tweet](https://twitter.com/decredproject/status/1176914732399439873) ogłaszający i podsumowujący dcrpool.
* [Scalony](https://twitter.com/JamieHoldstock/status/1171347711536357378) pull request do Joule, aut. @jholdstock.
* @matheusd [tweetuje](https://twitter.com/matheusd_tech/status/1168897318432706561) o przeniesieniu 400+ pull request z repozytorium upstream Lightning Network do dcrlnd.
* @fernandoabolafio [zaprasza](https://twitter.com/oxfernando/status/1174268398458609664) ludzi do zapoznania się z designem Politei.
* @moo31337 [sugeruje](https://twitter.com/marco_peereboom/status/1176856040991801345), że kiedy rynki są w dołku, jest to dobra okazja do przyłączenia się do projektu takiego jak Decred i otrzymania zapłaty za swój wkład w rozwój projektu.
* [Przewydiwania](https://twitter.com/lukebp_/status/1175441776041058304) @lukebp o inteligentnych platformach kontraktowych vs pieniądzach niewymagających zezwolenia i transformacjach społecznych.
* [Podsumowanie](https://twitter.com/jcliff42/status/1170039176277835776) technologii prywatności Decred autorstwa Jordana Clifforda ze Scalar Capital.

## Rynki

We wrześniu kurs wymiany Decred wahał się pomiędzy 16,49-25,20 USD / BTC 0,0020-0,0024. Średni dzienny kurs wynosił 22,02 USD.

Kurs DCR/USD stracił ponad 20% wraz z BTC/USD około 24 września. Wśród możliwych przyczyn omawianych w mediach są m.in: [gwałtowny spadek](https://www.ccn.com/bitcoin-hashrate-flashcrash-price-slump/) mocy obliczeniowej sieci Bitcoin, [rozczarowujące uruchomienie](https://cryptobriefing.com/bakkt-crypto-launch/) platformy Bakkt, które nie przyniosło oczekiwanego rynku byka napędzanego przez wejście instytucji w krypto oraz [likwidacje](https://bitcoinist.com/yes-bitmex-liquidations-caused-bitcoin-price-to-crash-heres-how/) na platformach obrotu instrumentami pochodnymi.

## Ważne kwestie i wiadomości poboczne

[Ogłoszono](https://blog.coinbase.com/introducing-the-crypto-rating-council-d6ee33a8f34d) powstanie [rady ds. ratingu kryptowalut](https://www.cryptoratingcouncil.com/). Jest to grupa przedsiębiorstw zajmujących się kryptowalutami, sporządzających ratingi tego, czy aktywa kryptowalutowe mogą być uznawane przez SEC za papiery wartościowe. Wydany został początkowy zestaw 20 [ratingów](https://www.cryptoratingcouncil.com/asset-ratings), które pozycjonują aktywa w skali od 1 (nie uznawane za papier wartościowy) do 5 (bardzo prawdopodobne , że zostanie uznane za papier wartościowy). Bitcoin, Litecoin, Monero i DAI otrzymały najlepszy wynik (1). Aktywa takie jak EOS, Tezos, Stellar i Hedera Hashgraph otrzymały 3,75 punktu, XRP 4, a Polymath 4,5.  CRC nie opublikuje nazw projektów, które otrzymały ocenę 5.  Więcej ocen zostanie opublikowanych w przyszłości.  Podczas gdy metodologia nie jest opublikowana, z punktowych podsumowań ocen można wywnioskować, że nacisk kładzie się na to, czy miała miejsce sprzedaż tokenów, czy miało to miejsce zanim system stał się użyteczny, czy w materiałach promocyjnych do sprzedaży tokenów istniał język podobny do inwestycyjnego oraz czy istnieje zdecentralizowany rozwój i wykorzystanie systemu.

Ponad 640 projektów kryptowalutowych nie opublikowało żadnego nowego kodu w 2019 roku, według [badania](https://blog.coincodecap.com/analyzing-cryptocurrencies-github-activity/) autorstwa CoinCodeCap. Łączna kapitalizacja tych walut wynosi około 415 milionów dolarów, z najwyższą indywidualną kapitalizacją w wys. 85 milionów dolarów. Dane dotyczące giełd kapitalizacji rynkowej dla tych tokenów są niekompletne, ale w tym, co jest dostępne, giełda YoBit prowadzi w rankingu posiadając 62 takich tokenów.

[Ogłoszono](https://www.sec.gov/news/press-release/2019-202) ugodę między SEC i EOS, w którym Block.One musi zapłacić 24 miliony dolarów w karach za prowadzenie sprzedaży niezarejestrowanych papierów wartościowych. Dotyczy to sprzedaży żetonów ERC-20 EOS w rocznym ICO, które zebrało 4,1 mld USD, gdzie grzywna opiewa na 0,6% zebranej kwoty. Zgodnie z [komunikatem prasowym](https://block.one/news/block-one-announces-settlement-with-us-securities-and-exchange-commission/) Block.One ugoda dotyczy tylko żetonów ERC-20, które od tego czasu zostały zamienione na żetony EOS na sieci mainnet, uważane za bez zarzutów i nie wymagające rejestracji SEC do celów handlowych.

Sieć Bisq [ogłosiła](https://bisq.network/blog/bisq-dao-first-four-cycles/), że cztery miesięczne cykle jej finansowania DAO zostały zakończone. Bisq DAO może wybijać kolorowe monety BSQ w celu sfinansowania prac rozwojowych, które są spalane, gdy są używane do uiszczania opłat handlowych. Propozycje obejmują wnioski o wzrot kosztów, zakontraktowane funkcje, które otrzymują bieżącą rekompensatę, zmiany parametrów (opłaty handlowe zostały podniesione) oraz sygnalizowanie zgody na inne decyzje rozwojowe. W każdym cyklu liczba wniosków wynosiła około 20, a liczba głosów 200-300. Pierwszy i drugi cykl były bardzo inflacyjne, z dużo większą ilością wybitych BSQ, niż spalonych, ale trzeci cykl miał podobny poziom spalania i produkcji, a w czwartym cyklu więcej BSQ zostało spalonych niż wybitych. _(pominięto w numerze sierpniowym)_

Giełda OKCoin [uruchomiła](https://twitter.com/OKCoin/status/1168917669493579776) 3 września [inicjatywę](https://www.okcoin.com/1000btc), aby przekazać do 1000 BTC na rzecz twórców oprogramowania BTC, BCH i BSV. Zweryfikowani użytkownicy OKCoin mogą głosować na preferowany przez siebie projekt, a twórcy projektu otrzymają 0,02 BTC za każdy oddany głos. Inicjatywa ta była szeroko omawiana na Twitterze, przy czym niektórzy Bitcoinerzy promowali ją w celu wsparcia deweloperów, podczas gdy inni przyjęli bardziej pogardliwą postawę, powołując się na kwestie związane z włączeniem BCH i BSV oraz przedstawioną historyczną linią czasową. Na dzień 2 października głosowanie zostało zamknięte i oddano tylko 47 głosów ogółem (co odpowiada 0,94 BTC), ale OKCoin podbiło łączną kwotę przekazaną do 20 BTC.

CasperLabs, startup prowadzony przez Vlada Zamfira, [otrzymał 14,5 miliona dolarów](https://www.theblockcrypto.com/post/39087/vlad-zamfir-led-blockchain-project-casperlabs-bags-14-5m-series-a-to-improve-ethereum-2-0-scalability) w serii A finansownia na pracę nad skalowalnością Ethereum 2.0.

Górnicy Ethereum [zagłosowali](https://decrypt.co/9573/ethereum-expands-blockchain-capacity-by-25-percent) w celu zwiększenia limitu gazu dla bloków (a tym samym wielkości bloku) o 25%, w odpowiedzi na rosnące opłaty transakcyjne. Górnicy w Ethereum bezpośrednio kontrolują limit gazu i każdy z nich może nieznacznie go zwiększać lub zmniejszać, dlatego uzgodnienie podwyżki o 25% zajęło trochę czasu.

Ethereum było też świadkiem uruchomienia hard forka Istanbul na testnecie Ropsten w tym miesiącu, co [miało miejsce](https://www.coindesk.com/ethereums-istanbul-upgrade-arrives-early-causes-testnet-split) wcześniej niż się spodziewano i spowodowało rozłam łańcucha. Ten hard fork ma zerwać szereg inteligentnych kontraktów używanych w sieci głównej Ethereum, [w tym](https://www.coindesk.com/ethereums-istanbul-upgrade-will-break-680-smart-contracts-on-aragon) około 680 inteligentnych kontraktów Aragon.

Stellar [uruchomił](https://www.coindesk.com/stellar-to-airdrop-2-billion-xlm-into-keybase-wallets) kampanię airdropową dająca użytkownikom Keybase darmowe XLM. W ciągu najbliższych 20 miesięcy użytkownicy Keybase otrzymają comiesięczne zrzuty 100 milionów XLM. W ciągu 20 miesięcy ta metoda dystrybucji zwiększy podaż cyrkulacyjną XLM o 10%. Obecny obrót wynosi 20 miliardów XLM z 105 miliardów, z dystrybucją kontrolowaną przez Stellar Development Foundation.

Stellar Development Foundation [ogłosiła](https://medium.com/stellar-development-foundation/our-proposal-to-disable-inflation-8c9f8b80387) również plan wyłączenia inflacji XLM w ramach aktualizacji wersji 12. Podmioty zatwierdzające w sieci Stellar zagłosują za przyjęciem lub odrzuceniem tej zmiany. Inflacja XLM miała być sposobem finansowania projektów przez posiadaczy poprzez ustalenie adresu, pod który miały one otrzymywać nagrody inflacyjne. W praktyce posiadacze XLM mieli tendencję do wyznaczania adresów, nad którymi sprawują kontrolę, lub przystępowania do pul, tak, aby sami mogli otrzymać inflację za swoje udziały w XLM. Mechanizm inflacyjny nie służy swojemu wyznaczonemu celowi i dlatego SDF chce go rozwiązać.

Dash uruchomił [Fundację Inwestycyjną Dash](https://www.dashinvests.org), podmiot, który będzie ubiegał się o fundusze ze Skarbca Dash a następnie inwestował je w projekty mające na celu wzmocnienie jego ekosystemu Dash. DIF jest podmiotem prawnym, który może udzielać pożyczek lub inwestować w zamian za udziały w przedsięwzięciach, w które inwestuje. Decyzje o tym, w co inwestować, będą podejmowane przez radę wybranych nadzorców.

Fundacja Tezos [ogłosiła](https://tezos.foundation/news/announcing-second-cohort-of-tezos-ecosystem-grants) dofinansowanie dla drugiej kohorty 14 grantów Tezos Ecosystem, ponownie bez szczegółów, ile zostało przyznane lub na jakich warunkach. W odpowiedzi na najczęściej zadawane pytania Fundacja wyjaśniła, że nie ujawnia szczegółów dotyczących dotacji, ponieważ zaszkodziłoby to jej pozycji negocjacyjnej. Drugi z co sześciomiesięcznych [update'ów](https://tezos.foundation/news/tezos-foundation-releases-first-biannual-report) (*wydany i pominięte w numerze sierpniowym*) Fundacji Tezos posiada pewne informacje o tym, jak Fundacja wydaje swoje środki. W poprzednim roku 14,8 mln USD wydano na badania, edukację i rozwój główny, 14,1 mln USD wydano na granty wspólnotowe, a 8,5 mln USD wydano na narzędzia ekosystemowe i granty dla aplikacji. W dniu 31 lipca 2019 r. Fundacja posiadała aktywa wycenione na 652 mln USD, 61% w BTC, 15% w XTZ, 15% w "funduszu stabilizacyjnym" (zdywersyfikowanym portfelu obligacji, ETF, towarów), a 6% w fiat USD.

[Miniscript](http://bitcoin.sipa.be/miniscript/) został [ogłoszony](https://twitter.com/pwuille/status/1163592166062473217) przez Pietera Wuille'a. Jest to sposób na napisanie kilku skryptów Bitcoin w uporządkowany sposób, który pozwala na statyczną analizę, ogólne podpisywanie i kompilację polityk. Jest to skuteczny zestaw narzędzi ułatwiających pisanie skryptów Bitcoin i upewnienie się, jak będą się zachowywać. _(pominięte w wydaniu sierpniowym)_

Duża transakcja Bitcoin o wartości 1 miliarda dolarów spowodowała [spekulacje](https://cointelegraph.com/news/someone-just-moved-1b-in-bitcoin-for-700-fee-overpaying-20-times) o tym, kto za nią stał i jaki był jej cel.

Francja [postanowiła](https://cointelegraph.com/news/france-wont-tax-crypto-only-trades-will-tax-crypto-to-fiat-sales) nie opodatkowywać transakcji typu krypto-do-krypto. Opodatkowaniu podlegać będą tylko transakcje sprzedaży krypto-do-fiat.

Europejski Bank Centralny (EBC) [rozpoczął](https://www.bloomberg.com/news/articles/2019-09-12/ecb-cuts-rates-restarts-qe-to-fight-slowdown-as-draghi-era-ends) kolejną rundę luzowania ilościowego (QE). Będzie on "kupował" obligacje (pompując cenę) w tempie 20 mld euro miesięcznie przez "tak długo, jak to konieczne", aby osiągnąć cel dewaluacji euro. Ma to "pobudzić" wzrost gospodarczy. Albo, jak [ujmuje to w słowa](https://www.youtube.com/watch?v=XkvcdjSH0c0&t=9m21s) Murad, "porażenie prądem" ludzi. Przychodzi na myśl kolejny dobry [cytat](https://www.youtube.com/watch?v=XkvcdjSH0c0&t=6m21s): "ludzie w kryptowalutach uważają, że żadna żywa istota ludzka nie powinna mieć siły tworzenia bogactwa z powietrza". Jeśli posiadasz EUR lub chciałeś kupić obligacje na uczciwym rynku, dobrym pytaniem do EBC jest, skąd pochodzą pieniądze i czy pracowali tak ciężko, jak ty, aby na nie zarobić. Zauważmy również, jak starannie dobrany jest język, aby nie nazywać go tym, czym jest i jak trudno jest znaleźć artykuł informacyjny, który wyraźnie wspomniałby o źródle pieniędzy na te "zakupy".

Użytkownik GitHub "DecredCoin" zarejestrowany 1 października 2019 roku wydał ["obowiązkową aktualizację v1.5.0 "](https://archive.today/Huxft) dla Decred. Jest to oczywiście oszustwo, co zostało potwierdzone przez [skanowanie w poszukiwaniu wirusów](https://www.virustotal.com/gui/file/ffac37aab22c85952ba022079205700864514f44ea39cdf2bb01504ce2bb9d56/detection). Prosimy o zgłaszanie takich rzeczy, gdy tylko je zobaczycie.

Dla osób, które lubią śledzić dyskusję o Bitcoinie na Twitterze, uważajcie, co mówicie, ponieważ wydaje się, że próg dla zostania [zablokowanym](https://twitter.com/NickSzabo4/status/1169992390339227648) jest coraz niższy, a okno overtona dla dopuszczalnych punktów dyskusji lub opinii kurczy się.

## O tym wydaniu

To 18. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

* redakcja treści:  akinsawyerr, anastasia, bee, degeri, Dustorf, richardred, s\_ben
* recenzje i komentarze: davecgh, emiliomann, isuldor, jholdstock, lukebp, matheusd, raedah
* ilustracja tytułowa: saender
