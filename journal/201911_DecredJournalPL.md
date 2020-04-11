# Decred Journal – Listopad 2019

![abstrakcja](../img/journal-201911-384.png)

_Obraz: Okazanie siły, aut. @saender_

Najważniejsze wydarzenia z listopada:

- Kandydaci do wydania 2 i 3 dla v1.5.0 zostali wydani i w obu odnalezione zostały błędy (problem w RC3 dotyczy portfela Decrediton w Windows), zatem należy oczekiwać, że wkrótce pojawi się kolejny kandydat do wydania. Podziękowania dla wszystkich, którzy przyczynili się do tego, pobierając nasze oprogramowanie i zgłaszając wszelkie napotkane błędy.
- Projekt infrastruktury Decred DEX odnotował w tym miesiącu znaczne postępy, poprzez dodanie początkowej wersji portfela Decred, zarządzania uwierzytelnianiem i przetwarzania epok.
- Propozycja @elian dotycząca marketingu i eventów w Ameryce Łacińskiej została zatwierdzona, co czyni ją pierwszym regionalnym projektem marketingowym, który został zatwierdzony z budżetem niezależnym od głównych działań marketingowych.
- @matheusd opublikował długą serię esejów na blogu, przedstawiających plan rozwoju ticket splittingu na Lightning Network, zalety takiego podejścia do sprawy (niska minimalna kwota uczestnictwa, lepsze doświadczenia użytkownika), a także zmiany w zasadach konsensusu, które wymagane są, aby zrobić to porządnie.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Poprawa wydajności i oczyszczenie kodu.

Podczas gdy v1.5 czeka na swoje ostateczne wydanie, rozwój zmierza w kierunku kamienia milowego, którym będzie wersja [1.6.0](https://github.com/decred/dcrd/milestone/24).

Wprowadzono komendę [`regentemplate`](https://github.com/decred/dcrd/pull/1979) w celu wymuszenia generowania najnowszego szablonu z wszelkimi nowymi transakcjami.

Mempool będzie [porzucał](https://github.com/decred/dcrd/pull/1982) wszelkie pozostałe osierocone transakcje, gdy wysyłający je peer rozłączy się. Wprowadzono również [modyfikację](https://github.com/decred/dcrd/pull/1984) polityki co do transakcji osieroconych zgodnie z ostatnimi ulepszeniami.

Dodano [nowy parametr łańcucha](https://github.com/decred/dcrd/pull/2000) dla określenia jego minimalnej łącznej znanej pracy. Kod sprawdzający, czy łańcuch jest aktualny, jest aktualizowany w celu użycia całkowitej pracy zamiast wysokości końcowego punktu kontrolnego. Metoda ta nie opiera się na zaufanych znanych punktach kontrolnych, jest ważna bez względu na kolejność otrzymywania i przetwarzania bloków i ogólnie rzecz biorąc, jest bardziej obiektywną wartością, która nie może być unieważniona przez reorganizację łańcucha.

Pakiet `lru` został [rozszerzony](https://github.com/decred/dcrd/pull/2002), aby umożliwić wstawianie i pobieranie par klucz-wartość (oprócz samych wartości).

Trawersowanie przodków bloków zostało znacząco zoptymalizowane poprzez wprowadzenie [deterministycznej listy pominięć](https://github.com/decred/dcrd/pull/2010).

[dcrwallet](https://github.com/decred/dcrwallet): Poprawki błędów, wprowadzone nowe metody, oczyszczenie kodu.

Dodana została metoda w celu wykrycia [ponownie używanych adresów](https://github.com/decred/dcrwallet/pull/1616) i odpowiadających im punktów końcowych.

[Decrediton](https://github.com/decred/decrediton): Liczne poprawki błędów i usprawnień interfejsu użytkownika, oczyszczenie kodu.

Dodano przełącznik do [utworzenia](https://github.com/decred/decrediton/pull/2310) w portfelu konta do wykorzystania z LN przy pierwszym jego uruchomieniu. Zachęca to użytkowników do niekorzystania z domyślnego konta w portfelu, które prawdopodobnie posiada większość środków, co może spowodować automatyczne otwarcie wielu kanałów, jeśli zaznaczono funkcję autopilota.

Wdrożono nową partię [widoków responsywnych](https://github.com/decred/decrediton/pulls?q=is%3Apr+merged%3A2019-11-01..2019-11-30+responsive).

Poprawiono wiele błędów znalezionych podczas testów RC1 i RC2.

Ogółem w listopadzie scalono [54 pull requesty](https://github.com/decred/decrediton/pulls?q=is%3Apr+merged%3A2019-11-01..2019-11-30).

[Politeia](https://github.com/decred/politeia): Do backendu dodano [informacje o płatności](https://github.com/decred/politeia/pull/1051), pozwalając systemowi CMS na pełne odzyskanie informacji o fakturach zakotwiczonych w politeiad.

Od teraz obsługiwana jest kompilacja kodu politeiavoter na systemie operacyjnym [Windows](https://github.com/decred/politeia/pull/1046).

Przeprojektowanie frontendu systemu CMS jest w trakcie realizacji.

Rozpoczęto wdrażanie [procesu zapytań ofertowych (RFP)](https://github.com/decred/politeia/pull/1054).

[dcrstakepool](https://github.com/decred/dcrstakepool): Rozpoczęto prace nad [uruchomieniem](https://github.com/decred/dcrstakepool/pull/571) arbitralnego głosowania biletów, do których serwer posiada klucze prywatne. Kontynuowana jest praca nad implementacją uwierzytelnienia na zasadzie [per-bilet](https://github.com/decred/dcrstakepool/issues/568) i zakupem biletów w celu usunięcia kont użytkowników, ponownego użycia adresów do głosowania i wymagań dotyczących poczty elektronicznej.

[dcrpool](https://github.com/decred/dcrpool): Trwają prace nad dodaniem bardziej obszernego [zakresu testów](https://github.com/decred/dcrpool/pull/141).

[dcrlnd](https://github.com/decred/dcrlnd): Naprawiono błędy, poprawiono testy i infrastruktura kompilacji. Zaktualizowano [Dockerfile](https://github.com/decred/dcrlnd/pull/56) dla dcrlnd.

[cspp](https://github.com/decred/cspp): zwiększony limit czasu timeoutu dla RPC, ulepszona obsługa błędów klient-serwer, umożliwienie korzystania z serwera stagingowego LetsEncrypt.

[dcrdex](https://github.com/decred/dcrdex): Rozwój idzie jak burza! Nowe komponenty zaimplementowane w listopadzie to: [menadżer uwierzytelniania](https://github.com/decred/dcrdex/pull/50), [rejestrator kont](https://github.com/decred/dcrdex/pull/58), początkowa wersja klienta [portfela Decred](https://github.com/decred/dcrdex/pull/49), [websocket](https://github.com/decred/dcrdex/pull/55) łączności dla klienta, oraz początkowe [przetwarzanie epok](https://github.com/decred/dcrdex/pull/66) i przechowywanie matchów, oraz przejście. Sposób identyfikacji niewykorzystanych funduszy zmienił się z txid/vout, aby bardziej wyabstrahować [ID monety](https://github.com/decred/dcrdex/issues/75) tak, aby w przyszłości móc obsługiwać aktywa nieoparte na UTXO.

[dcrandroid](https://github.com/decred/dcrandroid): Trwają pracę nad dodaniem wsparcia dla [wielu portfeli](https://github.com/decred/dcrandroid/pull/401).

[dcrios](https://github.com/raedahgroup/dcrios): Przeprojektowanie, usprawnienie interfejsu użytkownika, naprawa błędów.

Menu nawigacyjne zostało [przeprojektowane](https://github.com/raedahgroup/dcrios/pull/524). Dodano powiadomienie, aby pokazać [stan synchronizacji](https://github.com/raedahgroup/dcrios/pull/529), gdy aplikacja pracuje w tle.

Kontynuowane są prace nad przeglądem [widoków](https://github.com/raedahgroup/dcrios/issues/506), [odtworzeniem portfela](https://github.com/raedahgroup/dcrios/pull/527) i [sprawdzeniem ziarna portfela](https://github.com/raedahgroup/dcrios/pull/530).

[dcrdata](https://github.com/decred/dcrdata): v5.2 jest teraz dostępna!

Najważniejsze wieści z frontendu: zaktualizowano stronę nagłówków i bloków, ulepszono wykresy, oraz dodano przycisk do kopiowania tekstu do schowka w przypadku adresów i haszów. Na backendzie: obsługa dcrd w wersji 1.5, rezygnacja z obsługi SQLite celem skupienia się na PostgreSQL, poprawki API Insight, poprawa wydajności. Sprawdźcie [notatki do wydania](https://github.com/decred/dcrdata/releases/tag/v5.2.0), aby zobaczyć wszystkie zmiany. Wydanie to jest kulminacją 83 commitów autorstwa 9 osób w ciągu 4 miesięcy. Gratulacje dla zespołu dcrdata!

Trwają prace nad pokazaniem [mieszanych transakcji CSPP](https://github.com/decred/dcrdata/pull/1610) (podgląd jest aktywny na wersji alfa na stronie [bloków](https://alpha.dcrdata.org/block/403513)) i obliczaniem [kosztu ataku](https://github.com/decred/dcrdata/pull/1617).

[docs](https://github.com/decred/dcrdocs): Nowy [poradnik dotyczący prywatności](https://github.com/decred/dcrdocs/pull/1029), przegląd [sekcji dot. zarządzania](https://github.com/decred/dcrdocs/pull/1030), linki do nowych dokumentów deweloperskich [devdocs](https://github.com/decred/dcrdocs/pull/1017), drobne aktualizacje i sprzątanie.

[decred.org](https://github.com/decred/dcrweb): Drobne aktualizacje i sprzątanie.

Portfel Cobo został [usunięty](https://github.com/decred/dcrweb/pull/745), z myślą o tym, że nie należy promować rozwiązań wymagających przekazania środków stronom trzecim. Strona giełd wymian została [zaktualizowana](https://github.com/decred/dcrweb/pull/746) (Nanex oraz OOOBTC zostały usunięte).

Pozostałe:

- @matheusd [nakreślił](https://blog.decred.org/2019/11/11/LN-Multi-Owner-Tickets/) ścieżkę do zaimplementowania biletów posiadanych przez wielu użytkowników ("ticket splitting") na Lightning Network. Prawidłowe wykonanie tego zadania wymaga kilku stopniowych ulepszeń i paru nowych opcodów w ramach zasad konsensusu. Wpis jest dość techniczny, ale dla najsilniejszych z czytelników zawiera linki do 4 jeszcze głębszych postów w tej tematyce. [Dyskusja z Reddita](https://www.reddit.com/r/decred/comments/duzv3m/ln_multiowner_tickets_blog_post_from_matheus/) uzupełnia wpisy i odnosi się do kilku obaw aut. @bee (tl;dr: nie jest to epicka inwestycja tylko dla dzielonych biletów, ponieważ większość proponowanych zmian to przydatne ulepszenia same w sobie).
- @karamble [wydał](https://twitter.com/karamblez/status/1197676296240861186) decredowy [dashboard](https://github.com/karamble/dcraspaper) dla Raspberry Pi z wyświetlaczem EPaper.
- Deweloperzy testują odtwarzalne kompilacje za pomocą Go 1.13 i narzędzia do [wydań](https://github.com/jrick/release) (omówione [tutaj](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$157308464734953aRCth:decred.org)) aut. @jrick. Pomoc w postaci większej ilości osób kompilujących wydania będzie bardzo mile widziana.

Statystyki aktywności deweloperskiej na listopad: 173 aktywne PR-y, 342 master commity, 67 tys. dodanych i 16 tys. usuniętych linijek kodu spośród 12 repozytoriów. Wkład pochodził od 1-8 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: zeoio ([dcrdex](https://github.com/decred/dcrdex/commits?author=zeoio)), githubsands ([dcrlnd](https://github.com/decred/dcrlnd/commits?author=githubsands)), eharris128 ([dcrweb](https://github.com/decred/dcrweb/commits?author=eharris128)).

Wcześniej pominięto wkład od dwóch nowych osób: neddoz ([dcrios](https://github.com/raedahgroup/dcrios/commits?author=neddoz) z nami od czerwca) oraz quacklabs ([dcrios](https://github.com/raedahgroup/dcrios/commits?author=quacklabs) od września). Witamy na pokładzie!

Statystyki społeczności:

- Obserwujący na Twitterze: 40 641 (+9)
- Subskrybenci na Reddit: 9703 (+47)
- Użytkownicy na Matrixie: 474 (+18)
- Użytkownicy na Slacku: 6872 (+14)
- Użytkownicy na Discordzie: 2592 (+40), zweryfikowani z możliwością pisania postów: 379 (+21)
- Użytkownicy na Telegramie: 2903 (-63)
- Subskrybenci na YouTube: 3920 (+60)
- Obserwujący na Facebooku: 3307 (+11), polubień: 3027 (+8)
- Obserwujący na LinkedIn: 662 (+24)
- GitHub: 520 gwiazdek (+3) i 1400 forków repozytorium dcrd (+0)

## Zarządzanie

W listopadzie do [Skarbca](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) wpłynęło 14 096 DCR i wydano z niego 17 889 DCR. Stosując średni dzienny kurs DCR/USD z listopada w wysokości 19,97 USD, Skarbiec otrzymał 281 tys. USD i wydał 357 tys. USD. Przy średnim dziennym kursie październikowym wynoszącym 15,59 USD, wartość dolara naliczona za prace wykonane w tym miesiącu wynosi 279 tys. dolarów. Na dzień 2 grudnia saldo Skarbca wynosi 640 201 DCR (12,4 mln USD po 19,44 USD).

Złożono dwie nowe propozycje, jedną za 650 USD za wersję DCR aplikacji Point of Sale [PlusBit](https://proposals.decred.org/proposals/e559188b0febcab29c49c1f7dd5c66645e31be00894a150ef7d0b8ceb6486605), a drugą aut. @buck54321 z prośbą o 30 000 USD na dalszy rozwój aplikacji [TinyDecred](https://proposals.decred.org/proposals/ad0f9688b3467734e2581604914b2cc32c6eb7991dff460eff41d21f66d88451). Głosowanie nad wnioskami rozpoczęło się 3 grudnia.

Propozycja [budżetu na marketing i eventy w Ameryce Łacińskiej](https://proposals.decred.org/proposals/5af0ce1cd325be6be39109c2750f34095c4e8feeea962ede058a1e4f4a61473e) for aut. @elian została zatwierdzona stosunkiem głosów 75% na "tak", przy udziale 29% bietów uprawionych do głosowania, propozycja dot. [badań i edukacji](https://proposals.decred.org/proposals/65bde4146b845e7e839d6916d4d8f642bc39c250df5379c2f1e26c4ab778ec1a) aut. @ammarooni przeszła stosunkiem głosów 80% na "tak" oraz frekwencją w wys. 29%. Wniosek o [ufundowanie nagrody Dota2](https://proposals.decred.org/proposals/5a1bd4116565d107c1672799ed16cae9e92ec633c6e39d9b463b8218e66ff759) został odrzucony przy 5% poparciu i udziale 29% głosujących.

@richardred opracował [raport](https://www.blockcommons.red/publication/mm-tracking-1/) na temat giełdowego orderbooka DCR od połowy października do połowy listopada, ponieważ i2 Trading rozpoczęło animację rynków DCR zgodnie z ich zatwierdzoną [propozycją](https://proposals.decred.org/proposals/2eb7ddb29f151691ba14ac8c54d53f6692c1f5e8fe06244edf7d3c33fb440bd9). Dodatkowa płynność jest dostępna, choć zależnie od sposobu jej pomiaru w tym czasie (gdzie wahania cen tworzyły trudne warunki), prawdopodobnie nie była ona dostępna z 90% czasem pracy na wszystkich giełdach i parach.

Więcej informacji na temat działalności Politeia Digest można znaleźć w [wydaniu 25](https://blockcommons.red/politeia-digest/issue025/) Politeia Digest.

## Sieć

Hashrate: listopadowy hashrate na początku miesiąca wyniósł ~442 Ph/s, a zamknął miesiąc w ok. ~381 Ph/s, zaliczając niż w ok. 322 Ph/s oraz szczyt w wys. 571 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 4 grudnia wyglądała następująco: Poolin 35%, UUPool 32%, F2Pool 11,6%, lab.antpool.com 6,8%, BTC.com 2,8%, Luxor 2,3%, Coinmine 0,11%, BeePool 0,10%, suprnova 0,01% i pozostałe 9,45% za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: średnia cena biletu z okresu 30 dni wynosiła 134,8 DCR (+2,5) za danymi z dcrstats.com. Cena wahała się między 123,9-150,4 DCR. Zablokowana kwota wynosiła 5,29-5,49 mln DCR, co odpowiadało 49,50-51,17% dostępnej podaży.

Cena biletów zaliczyła kolejny szczyt od momentu zmiany algorytmu sdiff, podczas gdy 51,17% oznacza nowy szczyt [uczestnictwa kredytów w stakingu](https://explorer.dcrdata.org/charts?chart=stake-participation).

Ponadto, odnotowano kolejny przypadek gwałtownego wzrostu liczby przegapionych biletów dnia [29 listopada](https://explorer.dcrdata.org/charts?chart=missed-votes&zoom=k0x6wa44-k3ucpasw&bin=window&axis=time).

Węzły: Przez [listopad](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1572566400000&to=1575158400000) było około 189 węzłów nasłuchujących i 398 węzły ogółem za danymi z dcr.farm. Bazując na średnich danych odn. ilości węzłów, około 73% z nich operowało na dcrd v1.4.0, 9,6% to wersje v1.5 oraz RC, a 2% to v1.6 (pre)developerskie. 8,8% węzłów działało na dcrwallet v1.4.

Od 4 grudnia około 24% głosujących PoS sygnalizuje, że zaktualizowało swoje oprogramowanie i jest gotowych zagłosować za zmianą w zasadach konsensusu, za danymi z [dcrdata](https://explorer.dcrdata.org/agendas).

W dniu 24 listopada wydobyto i zatwierdzono blok [400 000](https://www.reddit.com/r/decred/comments/e0yvyb/block_400000/).

## Integracje

Bittrex [dodał](https://twitter.com/BittrexExchange/status/1194330471385186316) parę [DCR/USD](https://global.bittrex.com/Market/Index?MarketName=USD-DCR) do swojej oferty. Całej sytuacji [kontekstu](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$157358651139766wUsaK:decred.org) nadał @jz i wyjaśnił, że i2trading będzie zapewniało płynność na tym rynku.

Portfel/giełda Abra [dodała wsparcie](https://support.abra.com/hc/en-us/articles/360001777271-We-ve-added-new-cryptocurrencies-) dla Decred zarówno dla klientów amerykańskich, jak i międzynarodowych. Zgodnie z [tą stroną](https://www.abra.com/cryptocurrency/investing-guide/) Abra nie przechowuje kilku największych aktywów, lecz DCR nie jest jednym z nich, a zatem jest przechowywany.

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Nawiązywanie kontaktów

W listopadzie Decred gościł na wielu imprezach o wysokim profilu na całym świecie. Wielu z tych samych członków zespołu z ubiegłego roku powróciło na tegoroczny Web Summit w Lizbonie, gdzie Decred był [jedynym][https://twitter.com/NoahPierau/status/1192045467435188224] projektem kryptowalutowym o znaczącej obecności. @moo31337 reprezentował branżę kryptowalutową podczas panelu pt. "Czy naprawdę możesz ufać swojemu bankowi?", który można obejrzeć [tutaj](https://vimeo.com/375884648). @Dominic [reprezentował](https://twitter.com/wanbihou/status/1193218449721311233) Decred na konferencji World Blockchain 2019 w Jiaxing, Chiny, 8 listopada.

@Dustorf udostępnił szkice wszystkich nowych podstron decred.org na kanale #writers, a po wkładzie społeczności, wszystko zostało przesłane do EETER do ostatecznego montażu, testowania i publikacji.

W ramach Decred Assembly zaprezentowano [głęboką analizę RC1 v1.5](https://www.youtube.com/watch?v=gGQuY0kOt7g) z udziałem @davecgh, oraz odcinki Decred in Depth z [@liz_bagot on PR](https://soundcloud.com/decredindepth/ep-11-liz-bagot-pr-marketing) i [@akinsawyer na temat Afryki i zarządzania](https://soundcloud.com/decredindepth/ep-12-akin-sawyerr-dcr-africa-governance).

Listopadowe osiągnięcia Ditto to m.in. 9 artykułów medialnych:

- Artykuł komentujący dla @jy-p w [Cointelegraph](https://cointelegraph.com/news/secrets-they-missed-at-devcon-what-its-really-like-in-a-working-dao) zatytułowany "Sekrety przeoczone na DevConie: jak naprawdę wygląda działające DAO".
- [Podcast](https://podcasts.apple.com/us/podcast/base-layer-episode-086-jake-yocom-piatt-decred/id1445373535?i=1000457565007) z @jy-p dla Base Layer Podcast z Davidem Nage.
- [Artykuł](https://www.forbes.com/sites/cbovaird/2019/11/11/who-will-win-the-race-for-digital-currency-supremacy/) w Forbes z komentarzem @jy-p na temat wyścigu między rządami, korporacjami, i zdecentralizowanymi kryptowalutami o przebudowanie systemu finansowego.
- Skoordynowanie [wywiadu](https://podcasts.apple.com/us/podcast/market-disruptors/id1463411709) z @jy-p dla podcastu Market Disruptors.
- [Dwa pełne artykuły](https://cryptotradernews.com/technology/our-data-privacy-is-under-attack-decred-is-fighting-back/) o funkcji prywatności Decred w nowej publikacji krypto o nazwie Crypto Trader News.
- [Wywiad](https://www.youtube.com/watch?v=4r6z9JZxRRI) pomiędzy @akinsawyerr oraz Nakamoto News Network podczas Światowej Konferencji Krypto w Las Vegas.
- [Wywiad](https://messari.io/podcast/developer-funding-governance-and-the-evolution-of-decred-with-jake-yocom-piat) z @jy-p dla podcastu Unqualified Opinions w serwisie Messari o finansowaniu prac rozwojowych, zarządzaniu, i Decred.
- [Telewizyjne wystąpienie](https://blocktv.com/watch/2019-10-30/5db9ab4487a7e-resolving-corporate-governance-in-cryptocurrency) w BlockTV o rozwiązaniach korporacyjnego zarządzania w kryptowalutach.

Ponadto:

- @liz\_bagot pojawiła się w [podcaście](https://podcasts.apple.com/us/podcast/liz-bagot-pr-marketing/id1466716734?i=1000455667566) Decred in Depth, aby porozmawiać o współpracy pomiędzy Ditto i Decred.
- Ditto wsparło obecność Decred w mediach na Web Summit. Firma umówiła wywiad z BBC, a także ułatwiła spotkania z CoinDesk i Cointelegraph. Stworzyła również brief najlepszych dziennikarzy, z którymi rozmawiał zespół Decred i pomogła @moo31337 przygotować się do jego dyskusji panelowej, aby zmaksymalizować jej wpływ na wydarzenie.
- Ditto wsparło @akinsawyerr w obecności podczas Światowej Konferencji Krypto w Las Vegas, organizując wywiady w terenie z takimi mediami jak Legacy Research, Nakamoto News Network, Crypto TV News i innymi.
- Zabezpieczono kilka podcastów i wywiadów online dla różnych członków społeczności.
- Zidentyfikowano i udostępniono społeczności możliwości współpracy z krypto-Twitterem i edukowania osób z zewnątrz na temat Decred.
- Ściśle współpracowano, aby wspierać osiągnięcia społeczności deweloperskiej Decred w ciągu ostatniego roku.

@bee napisał przegląd potencjalnych [strategii marketingowych](https://xaur.github.io/writings/posts/20191127-marketing-strategies.html) do zbadania. Niektóre z kluczowych tematów to poprawa sprawozdawczości, użycie słowa "pieniądze", promowanie faktycznego wykorzystania DCR do rozdawania napiwków, darowizn i finansowania projektów, przedstawianie DCR społecznościom i osobom indywidualnym jako sposobu na przekazanie wartości i zwiększenie obecności w mediach społecznościowych. ([Reddit](https://www.reddit.com/r/decred/comments/e2lhwd/marketing_strategies/))

## Eventy

Na których byliśmy:

- 4-7 listopada - [Web Summit](https://websummit.com/) - Lizbona, Portugalia. Zespół Decred przez 2 dni [prowadził stoisko](https://twitter.com/marco_peereboom/status/1191651269640888320). Jedynie [nieliczne](https://twitter.com/NoahPierau/status/1192045467435188224) projekty typu blockchain zabukowały wystąpienia na konferencji, prawdopodobnie ze względu na trwający rynek niedźwiedzia. @moo31337 [rozmawiał](https://twitter.com/decredproject/status/1192469998175948801) na scenie z przedstawicielami branży finansowej na temat "Czy naprawdę możesz ufać swojemu bankowi?" (zdjęcia: [1](https://twitter.com/JamieHoldstock/status/1191760511878279168), [2](https://twitter.com/NoahPierau/status/1192056049764904960), [3](https://twitter.com/kakalordao/status/1192131145141555201), [4](https://twitter.com/marco_peereboom/status/1192990143822454784))
- 6 listopada - [Decred Meetup](https://twitter.com/amxromero/status/1192241858816217089) - Medellín, Kolumbia. @elian i @victorarubin rozmawiali z około 40 osobami w wieku 20-50 lat, które zadały niesamowite pytania na temat Politei, planów Decred dotyczących Ameryki Łacińskiej, wektorów ataku na PoS i smart kontraktów. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191106-decred-meetup-medellin-colombia.md))
- 7 listopada - [Journey 4.0](https://twitter.com/legal_medellin/status/1189918302061187073) - Medellín, Kolumbia. @elian został zaproszony przez Legal Hackers Medellín, aby opowiedzieć o wyzwaniach technologii blockchain dla prawa międzynarodowego na Uniwersytecie EAFIT, największej uczelni zajmującej się administracją biznesu w Kolumbii. Studenci zainteresowali się koncepcją istniejącego zarówno wszędzie, jak i nigdzie DAO, która nie do końca wpisuje się w istniejące ramy prawne. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191107-journey-4-medellin-colombia.md))
- 8 listopada - [Światowa Konferencja Blockchain](https://www.8btc.com/wbc-2019/) - Jiaxing, Chiny. @Dominic reprezentował Decred i mówił o DAO i funkcjach ochrony prywatności. Pojawiły się doniesienia, że został zamieniony w [cyborga](https://twitter.com/wanbihou/status/1192484367626424321) na imprezie poprzedzającej to wydarzenie. Członkom społeczności w tym regionie zaleca się przestrzeganie standardowych protokołów i podejmowanie niezbędnych środków ostrożności. Nagranie wideo [robotycznego tańca](https://twitter.com/wanbihou/status/1193154668601327617) wyciekło i zapoczątkowało [#DecredDanceChallenge](https://twitter.com/hashtag/DecredDanceChallenge). (zdjęcia: [1](https://twitter.com/wanbihou/status/1192806081568722944), [2](https://twitter.com/wanbihou/status/1193218449721311233))
- 15 listopada - [Szczyt otwartej bankowości, oraz branży fintech i blockchain](https://twitter.com/Decred_ES/status/1195025379255144448) w Mexico City, Meksyk. @elian został zaproszony do rozmowy o cyfrowych tożsamościach. Podczas panelu przedstawił krótkie wprowadzenie do Decred oraz znaczenie bezpieczeństwa i prywatności danych osobowych, a także zwrócił uwagę na trudny do pogodzenia kompromis pomiędzy wygodą (przycisk "zapomniałeś hasła?") a kontrolą zapewnianą przez tożsamości suwerenne. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191115-open-banking-summit-mexico-city-mexico.md))
- 15-16 listopada - [CriptoBlock](https://criptoblock.com.br/) - São Paulo, Brazylia. @Rhama i @girino mówili o Decred. Mimo że organizatorzy ciężko pracowali, tylko około 250 osób wzięło udział w wydarzeniu z 1000-1200 uczestników oczekiwanych, co odzwierciedla dzisiejszy rynek. Decred był brązowym sponsorem.
- 21 listopada - [Africa Blockchain Summit](https://www.africablockchainsummit.com/agenda.html) - Rabat, Maroko. @arij skorzystała z okazji, by odkryć punkt widzenia organizacji scentralizowanych i zaprezentować Decredszerokiemu gronu ludzi z różnych środowisk. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191121-africa-blockchain-summit-rabat-morocco.md))
- 21 listopada - [Africa Fintech Summit](https://africafintechsummit.com/addis/) - Addis Ababa, Etiopia. @akinsawyerr przemawiał na panelu blockchainowym i nawiązał kilka cennych kontaktów. Tydzień później [rozmawiał](https://www.youtube.com/watch?v=WOqCjQELpao) o Decred i podróży w @VOANews. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191121-africa-fintech-summit-addis-ababa-ethiopia.md))
- 21 listopada - [Konferencja Blockchain](https://www.eventbrite.com.ar/e/conferencia-blockchain-tickets-81397410847) - Veracruz, Meksyk. Impreza odbyła się na największej uczelni technologicznej w mieście. @francov\_ i @luisantoniocrag przedstawili studentom blockchain, Bitcoina i Decred oraz poddali w wątpliwość fiatowe przekonania kilku nauczycieli. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191121-blockchain-and-decred-veracruz-mexico.md))
- 30 listopada - [Decred Meetup](https://twitter.com/RodgersJabz/status/1194309441774063617) - Kampala, Uganda. Zespół @jabz zapoznał publiczność z Decred i jego cechami oraz dał praktyczną sesję pokazującą, jak korzystać z portfela. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191130-decred-meetup-kampala-uganda.md)).

Na których będziemy:

- 12-13 grudnia - Labitconf - Montevideo, Urugwaj. Członkowie ekipy Decred będą obecni na największej konferencji z tematyki kryptowalut i blockchain w Ameryce Łacińskiej.
- 7 stycznia - [Digital Money Forum](https://thedigitalmoneyforum.com/) - Las Vegas, USA. Wydarzenie jest częścią konferencji CES 2020. @akinsawyerr będzie uczestniczył w [sesji](https://thedigitalmoneyforum.com/Sessions/the-problem-with-old-money-a-great-debate/) o gospodarce przyszłości.
- 29-31 stycznia - [Crypto 101 Online Summit](https://www.crypto2020summit.com/) - strona internetowa. @lukebp przedstawi przegląd planów Decred na rok 2020.
- 13-17 kwietnia - Blockchain Land na Talent Land - Guadalajara, Mexico. Decred będzie sponsorem Talent Land i będzie obecny na stoisku w Blockchain Land.
- Maj, data do ogłoszenia - [BitConf](https://www.bitconf.com.br/portal/) - São Paulo, Brazylia. Impreza została przeniesiona na maj 2020 roku.
- Impreza świętująca 5 lat społeczności Bitcoin Vietnam. Szczegóły wkrótce.

Pełny raport z październikowego spotkania Decred w Bogocie, Kolumbia, został [dodany](https://github.com/decredcommunity/events/blob/master/reports/20191029-decred-meetup-bogota-colombia.md) do [repozytorium wydarzeń](https://github.com/decredcommunity/events). W sumie jest w nim 37 raportów. Dziękujemy wszystkim za zgłoszenia!

## Media

Wybrane artykuły:

- LN i bilety z wieloma właścicielami, aut. @matheusd ([blog.decred.org](https://blog.decred.org/2019/11/11/LN-Multi-Owner-Tickets/))
- Wprowadzenie "Peer Production on the Crypto Commons" aut. @richardred ([blockcommons.red](https://blockcommons.org/post/crypto-commons/))
- Kto wygra w wyścigu o dominację cyfrowych walut? aut. Charles Bovaird ([forbes](https://www.forbes.com/sites/cbovaird/2019/11/11/who-will-win-the-race-for-digital-currency-supremacy/), [tweet](https://twitter.com/ForbesCrypto/status/1193953360422080512)) - zawiera cytaty od @jy-p
- Nazwa "Decred" ssie, i cieszy mnie to!, aut. @Dustorf ([medium](https://medium.com/@dlefebvr/decreds-name-sucks-and-i-m-glad-853af487034e))
- Czym jest Decred (DCR)? Dlaczego powstała ta kryptowaluta?, aut. @Haon ([medium](https://medium.com/@NoahPierau/what-is-decred-dcr-why-was-this-cryptocurrency-created-4e5cae085bc7)) - często zadawane pytania
- Sekrety przeoczone na DevConie: jak naprawdę wygląda działające DAO, aut. @jy-p ([cointelegraph.com](https://cointelegraph.com/news/secrets-they-missed-at-devcon-what-its-really-like-in-a-working-dao))
- Decred: gospodarczy przełom, aut. @ammarooni ([medium](https://medium.com/@Ammarooni/decred-an-economic-breakthrough-4d2e3ea27338))
- Nasze dane osobowe są atakowane: Decred stawia na walkę, aut. Matthew Harris ([cryptotradernews.com](https://cryptotradernews.com/technology/our-data-privacy-is-under-attack-decred-is-fighting-back/))
- Wywiad na wyłączność dla CTN: Wewnątrz Decred ze współzałożycielem projektu Jake Yocom-Piattem, aut. Matthew Harris ([cryptotradernews.com](https://cryptotradernews.com/cryptocurrency/ctn-exclusive-inside-decred-with-co-founder-jake-yocom-piat/))
- Decred, Hiperbezpieczny, niepodrabialnie rzadki, aut. @Checkmate ([medium](https://medium.com/@_Checkmatey_/decred-hypersecure-unforgeably-scarce-e076b91a2be))
- Seria Decred X aut. BlackBearXVII poszerzona została o następujące wpisy:
  - Decred X / Część VI - Trójjedynośc zaufania ([medium](https://medium.com/@imagnusholdings/decred-x-part-vi-triune-of-trust-3fa7ad1476a5))
  - Decred X / Część VII - Podręcznik terenowy A ([medium](https://medium.com/@imagnusholings/decred-x-part-vii-field-manual-a-68306f23d2ca))
  - Decred X / Część VIII - Iskierka nadziei - Podręcznik terenowy B ([medium](https://medium.com/@imagnusholings/decred-x-part-viii-silver-linings-field-manual-b-d38cb0e6e17c))
  - Decred X / Część IX - Podekonomia ([medium](https://medium.com/@imagnusholdings/decred-x-part-ix-sub-economics-e3b0a5e948e1))

Tłumaczenia:

- Październikowy Decred Journal przetłumaczony został na jęz. arabski (@arij), jęz. chiński (@Dominic), jęz. polski (@kozel) oraz jęz. hiszpański (@francov\_ and @luisantoniocrag). Dzięki Wam świat jest na bieżąco!

Wideo:

- Budowanie środka przechowania wartości z Jake'iem Yocom-Piattem z Decred w podcaście Unqualified Opinions serwisu Messari ([player.fm](https://player.fm/series/messaris-unqualified-opinions/building-a-store-of-value-with-decreds-jake-yocom-piatt), [apple](https://podcasts.apple.com/us/podcast/building-a-store-of-value-with-decreds-jake-yocom-piatt/id1455666979?i=1000457903445)) - widzowie na żywo ([youtube](https://www.youtube.com/watch?v=LMJp8rKLkkM)) byli świadkami boskiego występu @jy-p, który odpowiadał na ciekawe pytania o historię i podejście Decred.
- Decred Assembly: Głęboka analiza z @davecgh ([youtube](https://www.youtube.com/watch?v=gGQuY0kOt7g)) - dogłębne omówienie zasad konsensusu i RC1 v1.5.0.
- Digit-All, odcinek na temat Decred z @akinsawyerr ([youtube](https://www.youtube.com/watch?v=4r6z9JZxRRI))
- Recenzja Decred: Dlaczego DCR zasługuje na uwagę! aut. Coin Bureau ([youtube](https://www.youtube.com/watch?v=elfBK5QBVmo))
- Dlaczego Decred już dawno należy się listing na Coinbase, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=Og3kGX_fYho), przedyskutowane na [Reddit](https://www.reddit.com/r/decred/comments/dyl6vr/why_decred_is_overdue_for_a_coinbase_listing/))
- Czy naprawdę możesz ufać swojemu bankowi? ([vimeo](https://vimeo.com/375884648)) - @moo31337 bierze udział w panelu dyskusyjnym na Web Summit. @Exitus popełnił kilka przezabawnych, memowych wycinków ([pierwszy](https://www.youtube.com/watch?v=0Bq48X3cO_s), [drugi](https://twitter.com/coveryfire7777/status/1199866746192171010))

Audio:

- Base Layer, odcinek 086 - Jake Yocom Piatt (Decred) ([podbean](https://www.podbean.com/media/share/pb-9ah38-c88678), [spotify](https://open.spotify.com/episode/4vMtWg6lejqR9pfKkmsgXc))
- Zakłócacze rynku: Rozwijanie prywatności na blockchainie z Jakei'em Yocom-Piattem ([anchor.fm](https://anchor.fm/markmoss/episodes/Developing-Privacy-On-The-Blockchain-With-Jake-Yocom-e934qv), [stitcher](https://www.stitcher.com/podcast/anchor-podcasts/market-disruptors/e/65439848))
- Decred in Depth, odc. 12 - @akinsawyerr mówi o nieprzejrzystym zarządzaniu w [#kryptowalutach](https://twitter.com/hashtag/cryptocurrency) jako o barierze dla nowych uczestników rynku, o tym, jak Decred stawia zasady w jasnym świetle, i o możliwościach oferowanych przez beztarciowe, niewymagające zaufania płatności globalne w Afryce. ([libsyn](https://decredindepth.libsyn.com/akin-sawyerr-dcr-africa-governance), [soundcloud](https://soundcloud.com/decredindepth/ep-12-akin-sawyerr-dcr-africa-governance))
- Decred in Depth, odc. 13 - @richardred na temat wnoszenia wkładu w rozwój Decred, badania zarządzania blockchainem, pisania [cryptocommons.cc](https://cryptocommons.cc), oraz o wyborze pozostania pseudoanonimowym członkiem społeczności. ([libsyn](https://decredindepth.libsyn.com/richard-red-dcr-research-politeia-mm-proposal), [soundcloud](https://soundcloud.com/decredindepth/ep-13-richard-red-dcr-research-politeia-mm-proposal))

LunarCRUSH podzieliło się kilkoma [wykresami](https://twitter.com/LunarCRUSH/status/1191017614971027458), które łączą podstawowe dane rynkowe, takie jak cena i wolumen, z analizą sentymentu wobec Decred w mediach społecznościowych.

## Dyskusje społeczności

Wybrane wątki z Reddita:

- Odpowiedź nnnko56 [na pytanie](https://www.reddit.com/r/decred/comments/e2yiou/what_happens_when_we_reach_max_supply/): "Co się stanie, gdy osiągniemy maksymalną podaż?"
- [Twitterowe](https://twitter.com/AGNFAB1/status/1197455821380243457) obrazy aut. @AGNFAB1 pt. [Zdecentralizowane Kredyty](https://www.reddit.com/r/decred/comments/dqocpf/decentralized_credits/), oraz [Trylogia Tacotime](https://www.reddit.com/r/decred/comments/dznwsr/tacotime_trilogy/).
- 2 posty z największą ilością komentarzy mają również najniższą ocenę (0), jeden to [pytanie](https://www.reddit.com/r/decred/comments/dyvrht/so_what_makes_decred_a_better_cryptocurrency_than/) o to, co sprawia, że Decred jest lepszą kryptowalutą niż Nano, a drugi [sugerujący](https://www.reddit.com/r/decred/comments/e3vs1o/wouldnt_1_dcr_1_vote_be_fairer/), że stosunek 1 DCR = 1 głos byłby bardziej sprawiedliwy.

Wybrane dyskusje z Twittera:

- [Tweetowy](https://twitter.com/DCRtheSOV/status/1191215059680149505) wątek aut. @DCRtheSOV wprowadzający w tematykę Decred.
- Comiesięczne [podsumowanie](https://twitter.com/DCRtheSOV/status/1194480106892185601) październikowego postępu aut. @DCRtheSOV.
- [Tweet](https://twitter.com/karamblez/status/1197676296240861186) o decredowym dashboardzie dla Raspberry Pi aut. @karamble został dobrze przyjęty.
- [Wrócił](https://twitter.com/dcrstakey/status/1193758944587657216) nasz @dcrstakey.
- W Chinach wybuchło [#DecredDanceChallenge](https://twitter.com/wanbihou/status/1193154668601327617) dzięki tanecznemu talentowi kogoś ubranego w naszą sławną kosmiczną kurtkę kowbojską. Najciekawsze z nich to: [@Dustorf/Stakey](https://twitter.com/lefebvre_dustin/status/1195107934839230465), [@karamble](https://twitter.com/karamblez/status/1194664973030641664), [@Camilolwi](https://twitter.com/Camilolwi/status/1194358146027814912), [@JeonHaWoo2](https://twitter.com/JeonHaWoo2/status/1194389449062469634), [@treyditto](https://twitter.com/treyditto/status/1194351696522158080), [@liz_bagot](https://twitter.com/liz_bagot/status/1194393447035224065), [@elian](https://twitter.com/elianhuesca/status/1196526382970540032), [@Francov99_](https://twitter.com/Francov99_/status/1194410868001382401), [@s_ben](https://twitter.com/zen_bacon/status/1194756298987855872), [@luisantoniocrag](https://twitter.com/luisantoniocrag/status/1194438312678887425) i [@degeri](https://twitter.com/degeri_crypto/status/1194522586417225728).
- [Tweet](https://twitter.com/DCRComic/status/1199325669055979520) autorstwa @DCRComic o tematyce "weź ze sobą swój talent i ciesz się DAO".
- @jholdstock [spotyka się](https://twitter.com/JamieHoldstock/status/1192146283835854849) z premierem Portugalii.
- [Tweet](https://twitter.com/_Checkmatey_/status/1197225489959718913) aut. @Checkmate na temat bezpieczeństwa Decred.
- @permabullnino [tweetuje](https://twitter.com/PermabullNino/status/1195356846778912769) o aspektach przewagi konkurencyjnej Decred.
- @ammarooni [na temat](https://twitter.com/Ammarooni/status/1199804834133762054) przełomu gospodarczego.
- [Tweet](https://twitter.com/jessewldn/status/1194632275389898753) Jesse Waldena o raporcie z działaności platformy Politeia po roku istnienia.
- @lukebp [tweetuje](https://twitter.com/lukebp_/status/1199134933773500416) o tym, jak to jest pracować dla Decred, zaczyna hashtag #cryptodevs z wieloma innymi ludźmi, którzy dodali swoje obserwacje na ten temat.

> - Praca z zespołem światowej klasy
> - Budowa najnowocześniejszej technologii open source
> - Praca z dowolnego miejsca
> - Asynchroniczna komunikacja (bez spotkań!)
> - Ustawiasz swój własny harmonogram (na część lub pełny etat)


## Rynki

W listopazie kurs wymiany Decred wahał się pomiędzy 15,68-24,73 USD / BTC 0,0020-0,0029. Średni dzienny kurs wynosił 19,97 USD.

## Ważne kwestie i wiadomości poboczne

Coinbase opublikowało [post](https://blog.coinbase.com/how-coinbase-views-proof-of-work-security-f4ba1a139da0) na temat bezpieczeństwa PoW, przedstawiając swoje stanowisko, że dla bezpieczeństwa korzystne jest, aby monety były wydobywane przez sprzęt, dla którego jest to zastosowanie dominujące (tj. ASIC), oraz że różnorodności produkcji i posiadania dobrze służą algorytmy wydobycia przyjazne dla urządeń ASIC.

Dyrektor generalny MicroBT (producent Whatsminer D1, jednego z najpopularniejszych obecnie ASICów dla Decred) został [aresztowany](https://insidebitcoins.com/news/chinese-police-conduct-snap-raid-of-microbt-premises-arrests-ceo/242367) w Shenzhen w Chinach, w związku z naruszeniem patentu górniczego.

Przez błąd w implementacji Zcash [wyciekły metadane](https://duke.leto.net/2019/10/01/zcash-metadata-leakage-cve-2019-16930.html), co pozwoliło napastnikowi połączyć adresy IP z osłoniętymi adresami  Zcash (_przegapione w wydaniu z października_). Od dewelopera, który odkrył sprawę: "Wszystkie osoby korzystające z zaddrs i dzielące zaddrs z osobami trzecimi. (...) Uznajcie swój adres IP i związane z nim informacje geolokalizacyjne za powiązane z Waszym zaddr". Błąd został skopiowany z bazy kodowej Bitcoin Core i wprowadzony do Zcash w 2016 roku. Wyciek został naprawiony w v2.0.7-3, chociaż [komunikat bezpieczeństwa](https://z.cash/support/security/announcements/security-announcement-2019-09-24/) zalecał jedynie natychmiastową aktualizację bez wchodzenia w szczegóły. Problem dotyczy również wielu projektów dziedziczących kod po Zcash. Pokazuje to, że technologia ochrony prywatności jest bardzo delikatna i wymaga prostoty, solidnego podejścia do programowania oraz niezwykle rzetelnego przeglądu i testowania.

Fundacja Zcash i ECC osiągnęły [porozumienie](https://www.zfnd.org/blog/zcash-trademark-resolution/) w sprawie sposobu postępowania ze znakiem towarowym Zcash, który został przeniesiony na Fundację, na mocy porozumienia, w którym dzieli ona dwustronne uprawnienia do egzekwowania prawa do znaku z ECC. W niniejszym [artykule CoinDesk](https://www.coindesk.com/zcash-trademark-talks-were-about-more-than-a-logo) wyjaśniono, że spór dotyczył czegoś więcej niż tylko logo, a właściciel znaku towarowego ma prawo do *de facto* decydowania o tym, który łańcuch tak naprawdę jest Zcash.

Decred dodaje kolejny wymiar, w którym prawowitość łańcucha jest ustalana przez wyborców, a przed mniejszościowymi forkami chronią  poważne przeszkody, które stoją takim na drodze. Nawet jeśli ktoś spróbowałby ukraść "znak towarowy" Decred, nie powinno być żadnej wątpliwości co do tego, który łańcuch jest oryginalny, ponieważ wyborcy sygnują swoją aprobatą każdy blok. Ponadto, Decred bardzo jasno odpowiada na pytania typu "kto dokładnie zatrudnia deweloperów projektu?" oraz "czym jest 'społeczność'?" - w obu przypadkach są to interesariusze.

Rozwiązanie kwestii znaku towarowego ZEC pozwoliło na przeprowadzenie [ankiety](https://www.zfnd.org/blog/community-sentiment-collection-poll/) dla NU4, w której ekosystem/społeczność Zcash może zasygnalizować poparcie dla 13 opcji finansowania rozwoju. ECC i Fundacja Zcash uwzględnią wyniki 3 [lub 4](https://twitter.com/zooko/status/1200917828011876352) różnych metod ankietowania przy podejmowaniu decyzji o wyborze planu.

Aragon [zakończyło](https://blog.aragon.org/final-results-from-aragon-network-vote-4/) swoją 4. rundę głosowania na AGP, w której głosowano nad 15 wnioskami, a udział ANT wynosił około 3-18%. Wśród zatwierdzonych wniosków znalazła się [AGP-103](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-103.md), wprowadzająca maksymalny budżet sieci wynoszący 5% wartości skarbca lub 250 000 DAI (w zależności od tego, która z tych wartości będzie większa) na kwartalny cykl głosowania. Największą zatwierdzoną propozycją (z 9% frekwencją, i 91% poparcia) jest [AGP-106](https://github.com/aragon/AGPs/raw/1bee7c003d2e0dbfdc8cfe698198adeaf2cf0c7b/AGPs/AGP-106.md), opracowanie i uruchomienie sieci Aragon Chain, kosztem 500 000 USD. Jej celem jest stworzenie nowego protokołu warstwy 1 i zaoferowanie go jako alternatywy dla opartej na Ethereum sieci Aragon. Wśród przytoczonych powodów znalazły się rosnące koszty nadążania za zmianami w sieci Ethereum. [AGP-112](https://github.com/aragon/AGPs/raw/1bee7c003d2e0dbfdc8cfe698198adeaf2cf0c7b/AGPs/AGP-112.md), które również przeszło, wyraziło sprzeciw Aragon wobec ProgPoW na Ethereum, lub jakiejkolwiek innej nieawaryjnej zmianie algorytmu wydobywczego przed uruchomieniem Ethereum 2.0. Najwyższą frekwencją cieszyła się propozycja [AGP-81](https://github.com/aragon/AGPs/raw/1bee7c003d2e0dbfdc8cfe698198adeaf2cf0c7b/AGPs/AGP-81.md), przy czym 17% ANT okazało się głosować na "nie" w sprawie współpracy z Klerosem odnośnie systemu sądowego.

Aragon Court został [uruchomiony](https://blog.aragon.org/aragon-court-is-live-on-mainnet/) na sieci mainnet. Jest to system do orzekania w sprawie "subiektywnych sporów, których nie można rozwiązać za pomocą smart kontraktów". Posiadacze ANT mogą stawiać swoje żetony na żetony ANJ, które następnie mogą być zastawiane do udziału w rozstrzyganiu spraw wnoszonych przed sąd. Decyzje są podejmowane w ramach gry Schelling, w której ci, którzy poprawnie odgadną decyzję większości, są nagradzani, a tym, którzy zrobią to błędnie, obcina się stawkę. Rejestracja na jurorów ANJ rozpocznie się w styczniu 2020 roku.

Dragonfly Research opublikowało [artykuł](https://medium.com/dragonfly-research/breaking-mimblewimble-privacy-model-84bcd67bfe52) o "łamaniu modelu prywatności Mimblewimble" poprzez monitorowanie sieci w czasie rzeczywistym. @jy-p zwrócił wcześniej na to zagadnienie uwagę jako część swojego przeglądu rozwiązań dotyczących prywatności, a następnie omówił je podczas [podcastu](https://acrabaselayer.podbean.com/e/base-layer-episode-086-jake-yocom-piatt-decred/) Base Layer. Deweloper Grin [odpowiedział](https://medium.com/grin-mimblewimble/factual-inaccuracies-of-breaking-mimblewimbles-privacy-model-8063371839b9) na ten artykuł, stwierdzając, że sensacjonalizuje on znane ograniczenie, które nie stanowi możliwego frontu ataku.

Ogłoszono ["Nieznany fundusz"](https://www.unknown.fund/press-release), zobowiązujący się do zainwestowania i przekazania 75 milionów dolarów w Bitcoinie startupom, które bezpośrednio lub pośrednio wspierają ideę anonimowości. "Preferowane będą następujące nisze: ochrona danych osobowych, narzędzia do anonimowości, kryptowaluty i blockchain". Fundusz jest dość nieprzejrzysty, a komunikat na stronie głosi, że "składanie wniosków do Nieznanego Funduszu zostało zamknięte. Ich ccena zajmie kilka miesięcy". Ludzie zaczynają [pytać](https://twitter.com/hasufl/status/1202927790082932736), czy  mogło to być zwykłe oszustwo.

Fundacja Rozwoju Stellar (SDF) [ogłosiła](https://www.stellar.org/blog/sdfs-next-steps/), że [spaliła](https://www.theblockcrypto.com/linked/45793/the-stellar-foundation-has-burned-over-50-of-the-total-xlm-token-supply-canceling-airdrop-programs) 55 miliardów XLM, wartych ponad 4,4 miliarda dolarów (domniemanie), reprezentujących ponad 50% całkowicie wydobytej podaży XLM. Powodem było przekonanie, że fundacja może osiągnąć swoje cele przy mniejszych środkach finansowych, a kampanie zrzutów na dużą skalę okazały się nieskuteczne.

Blockchain EOS [wszedł w "tryb przeciążenia"](https://cointelegraph.com/news/eos-blockchain-congested-eidos-airdrop-95-of-transfers) w związku z gwałtownym wzrostem liczby transakcji związanych z programem zrzutów (EIDOS), które na jednym etapie stanowiły 95% wszystkich transakcji EOS. Jednym ze skutków powyższego jest to, że użytkownicy, którzy mają mniej udziałów w EOS, nie są w stanie dokonać transakcji do czasu, gdy popyt na zrzut nie zmniejszy się, lub w terminie 30 dni nie wygaśnie jego dzierżawa CPU. Innym skutkiem był gwałtowny wzrost o 100 000% kosztu czasu CPU w sieci.

Block.One [ogłosiło](https://cointelegraph.com/news/eos-creator-blockone-to-vote-for-block-producers-with-95-of-coins), że rozpocznie głosowanie na producentów bloków z 9,5% EOS, które kontroluje - klasyfikując się jako "mały, ale znaczący posiadacz żetonów EOS". Block.One nie ogłosiło, jak będzie głosować.

EOS New York [zatweetowało](https://twitter.com/eosnewyork/status/1199813240307568641), aby ujawnić fakt, że 6 z zarejestrowanych na EOS producentów bloków wydaje się być prowadzone przez ten sam podmiot. Chociaż rzeczeni BP [nie znajdują się](https://twitter.com/BlockCommons/status/1200133433009287168) w pierwszej dwudziestce 21 aktywnych BP, regularnie otrzymywały nagrody jako BP w stanie gotowości.

Eksperyment Donuts-on-Ethereum w /r/EthTrader [przechodzi](https://www.reddit.com/r/ethtrader/comments/dwiu4f/donutsonethereum_registration_is_open/) na łańcuchu do DAO Aragon. Członkowie subreddita mieli 2 tygodnie na zarejestrowanie się, aby odebrać swoje pączki, począwszy od 15 listopada. Jak zauważono w poprzednich wydaniach, społeczność /r/EthTrader już teraz jest podzielona w kwestii sposobu przeprowadzania decentralizacji pączków.

Justin Sun z Tron [ujawnił](https://www.coindesk.com/despite-denials-tron-founder-confirms-investment-in-poloniex-crypto-exchange), że jest częścią grupy inwestorów, którzy kupili giełdę Poloniex. W połowie listopada Poloniex wprowadził na giełdę TRX i rozpoczął "konkurs depozytowy" dla TRX, a później [TRC20-USDT](https://support.poloniex.circle.com/hc/en-us/articles/360035962012-Poloniex-x-TRC20-USDT-Rush-Campaign-Information). Później [ogłoszono](https://www.theblockcrypto.com/post/48603/poloniex-acquires-tron-based-dex-to-offer-decentralized-trading), że Poloniex nabył TRXMarket DEX oparte o TRON i przeprowadził rebranding na Poloni DEX, aby oferować zdecentralizowany handel. Kilka dni później konto Poloniex na Twitterze [zachęcało](https://beincrypto.com/poloniex-caught-telling-followers-to-buy-tron-in-deleted-tweet/): "Kupujmy #TRON", ale zaraz potem tweet został skasowany.

Z BitMEX niestety [wyciekły dane](https://www.coindesk.com/bitmex-exchange-exposes-user-base-in-email-mishap) poprzez wysłanie maila do wszystkich użytkowników wykorzystując cc zamiast bcc. Ups. Prowadzić to może do zrobienia potencjalnych celów z użytkowników, ujawniając jeden aspekt ich tożsamości stronom o niecnych zamiarach.

Koreańskie [OKEx](https://cointelegraph.com/news/cryptocurrency-exchange-okex-delists-xmr-dash-zec-zen-sbtc) i [Upbit](https://cointelegraph.com/news/upbit-exchange-delists-privacy-coins-due-to-money-laundering-concerns) ogłosiły wycofanie ze swojej oferty monet prywatnych, takich jak Monero, Zcash, Dash i innych, chociaż wycofanie DASH i ZEC zostało wstrzymane do czasu [recenzji](https://www.coindesk.com/okex-korea-reviewing-decision-to-delist-privacy-coins-zcash-and-dash) na OKEx. (_pominięte we wrześniu i październiku_)

Bittrex [przyjęło](https://www.coindesk.com/bittrex-chainalysis-kyt) oprogramowanie [Know Your Transaction](https://blog.chainalysis.com/reports/real-time-alerts-press-release) od Chainalysis, które monitoruje 15 kryptozasobów pod kątem podejrzanej aktywności w czasie rzeczywistym. (_przegapione w wydaniu wrześniowym_)

Na CoinDesk zaobserwowano przypadki niewyświetlania się stron, gdy javascript i pewne funkcje przeglądarki nie były włączone, o czym świadczy [brak migawek](https://archive.today/https://www.coindesk.com/*) z października i listopada. Powodami do wyłączenia javascript są: znacznie zwiększone bezpieczeństwo (niewykonywanie tony przypadkowego kodu), prywatność (wiele wektorów fingerprintingu przestaje działać) i wydajność (strony ładują się bardzo szybko). Niektóre strony internetowe stosują renderowanie tylko po stronie klienta za pomocą javascripta, co ma niefortunny efekt uboczny w postaci uniemożliwienia archiwom internetowym wykonywania migawek (i zmniejszenia odpowiedzialności stron). Inne strony o tematyce krypto, które stosują podobny zabieg to [Brave New Coin](https://bravenewcoin.com/) i [The Block](https://www.theblockcrypto.com/).

Amerykański Bank Rezerw Federalnych (Fed) [ogłosił](https://www.newyorkfed.org/markets/opolicy/operating_policy_191114), że rozszerzy swoje interwencje rynkowe, oferując 42-dniowe "repo" (swoiste pożyczki), oprócz 1-dniowych i 14-dniowych repo, które rozpoczęły się we wrześniu i "zakupy" bonów skarbowych, które rozpoczęły się w październiku. Jeśli kiedykolwiek zastanawialiście się, kto te pożyczki otrzymuje, musicie poczekać [dwa lata](http://gata.org/node/19583) na ich ujawnienie.

Spółki amerykańskie [gromadzą środki pieniężne](https://www.axios.com/businesses-spending-indicators-recession-533481fc-dba7-4b5c-add4-c11628c335bc.html), aby przygotować się na spowolnienie gospodarcze. Godny uwagi cytat z artykułu Axios: "Dane z Instytutu Spółek Inwestycyjnych pokazują, że choć rynek akcji wzrósł w tym roku o prawie 25%, inwestorzy byli sprzedawcami netto akcji, wyciągając z funduszy akcji 100 miliardów dolarów". [Artykuł](https://www.zerohedge.com/markets/conundrum-2019-equity-outflows-are-biggest-ever-yet-stocks-are-all-time-highs-what-happens) Zero Hedge pokazuje dziwne zjawisko wypływu pieniędzy z akcji, podczas gdy ich ceny osiągają nowe szczyty. Jak? Niektóre czynniki, które to umożliwiają, to fakt, że to same spółki są największymi nabywcami akcji poprzez ich odkupywanie, oraz tworzenie pieniędzy przez banki centralne, który płyną w akcje, przy jednoczesnym spadku wolumenu obrotów.

Najzabawniejsza część całego tego procederu, w którym inwestorzy [przechodzą z powrotem na gotówkę](https://www.bloomberg.com/news/articles/2019-11-12/world-s-rich-readying-for-major-stock-sell-off-ubs-wealth-says) jest taka, że choć chroni on wartość ich środków przed bardziej ryzykownymi aktywami i ujemnymi stopami procentowymi, to i tak zostanie rozwodniony przez tworzenie pieniądza fiat, które jest teraz [prawie niemożliwe](https://www.home.saxo/en-hk/insights/content-hub/articles/2019/11/20/investing-themes-to-watch-over-the-next-decade) do zatrzymania.

Sam Bank Rezerw Federalnych [przyznał](https://realinvestmentadvice.com/powells-fantasy-the-economy-should-grow-faster-than-debt/), że amerykański dług publiczny, rosnący szybciej, niż gospodarka, jest "nie do utrzymania", wkrótce po tym, jak wysokość długu [przekroczyła](https://cointelegraph.com/news/united-states-national-debt-hits-23-trillion-over-1m-per-bitcoin) 23 biliony dolarów.

Globalny dług cały czas osiąga nowe szczyty. Liczby te różnią się w zależności od źródła: szacunkowe wartości 188 bln dolarów i 230% światowej produkcji pochodzą od [szefa MFW](https://www.ibtimes.com/global-debt-surges-record-high-188-tn-imf-chief-2861715), a 250 bln dolarów i 320% światowej produkcji pochodzi z [Axios](https://www.axios.com/capital-markets-eye-world-soaring-debt-400f9f37-46b5-45ad-9487-c09ba8958c09.html), który cytował Instytut Finansów Międzynarodowych.

Niektórzy dostawcy zabezpieczeń fizycznych donoszą o zwiększonym [zapotrzebowaniu](https://www.bloomberg.com/news/articles/2019-11-20/world-s-rich-are-rattled-and-looking-for-old-fashioned-security) na skrytki depozytowe do przechowywania metali szlachetnych, gotówki i kryptowalut. Przytaczane motywy to obawy przed światową recesją, unikanie ujemnych stóp procentowych i klęsk żywiołowych.

Według [artykułu CoinDesk](https://www.coindesk.com/trump-administration-popped-2017-bitcoin-bubble-ex-cftc-chair-says) kilka amerykańskich organizacji działało w zmowie, aby "przebić bańkę Na Bitcoinie z 2017 roku"  _(przegapione w wydaniu z października)_. "Jedną z nieopowiedzianych historii ostatnich kilku lat jest to, że CFTC, Skarb Państwa, SEC i ówczesny dyrektor (Krajowej Rady Gospodarczej), Gary Cohn, sądzili, że uruchomienie kontraktów przyszłościowych wywoła efekt przebicia bitcoinowej bańki. I zadziałało." Podczas gdy ruch ten jest przedstawiany jest jako pomoc dla rynku poprzez "przebicie bańki", dający inwestorom możliwość "wyrażenia pesymistycznego poglądu", nawet jeśli _nie są właścicielami omawianych aktywów_, i zapobiegający powstania "rynku wierzących", przypomina to nieco inteligentne wykorzystanie kontraktów terminowych [w 1974 roku](http://www.gata.org/node/17081) w celu zwiększenia niestabilności złota i zniechęcenia ludzi do jego posiadania.

Czeski Bank Centralny zakazuje używania słowa "moneta" i jest [przygotowany](https://www.bitcoininsider.org/article/77479/czech-central-bank-prepares-fine-calling-physical-bitcoins-coins), aby ukarać grzywną firmy, które nazywają fizyczne monety zawierające papierowe portfele Bitcoin z 0,1 BTC "mince" ("moneta" w języku czeskim).

Niemiecki parlament [uchwalił ustawę](https://www.theblockcrypto.com/linked/48738/with-parliament-approval-german-banks-to-sell-and-custody-crypto-in-2020), która umożliwi bankom sprzedaż i przechowywanie kryptowalut od 1 stycznia 2020 r., pod warunkiem posiadania wymaganych licencji.

Podczas październikowych [protestów](https://twitter.com/dalalmawad/status/1186705664229466112) w Libanie banki były [zamknięte](https://www.cnbc.com/2019/10/23/lebanon-protests-fears-of-a-cash-crisis-as-banks-remain-shut.html) przez dwa tygodnie ze względów bezpieczeństwa. Po ponownym otwarciu w dniu 1 listopada ustanowiono [kontrole kapitałowe](https://www.counterpunch.org/2019/11/07/how-unofficial-capital-controls-stopped-a-run-on-the-banks-in-lebanon/) ograniczające codzienne wypłaty i przelewy za granicę.

GitHub [usunął](https://techcrunch.com/2019/10/30/github-removes-tsunami-democratics-apk-after-a-takedown-order-from-spain/) APK aplikacji do organizowania protestów w Katalonii, działają na wniosek sądu o zaprzestanie działań wysłany przez hiszpańską policję.

Dyrektor generalny mongolskiej giełdy IDAX [zaginął](https://idax.zendesk.com/hc/en-us/articles/360037327571-Urgent-announcement-about-current-situation-of-IDAX-Global) wraz z kluczami do zimnego portfela tej giełdy. Pięć dni wcześniej giełda ogłosiła [problemy z wyciąganiem środków](https://idax.zendesk.com/hc/en-us/articles/360036736211-Announcement-of-IDAX-withdrawal-channel-congestion) oraz to, że nie będzie już obsługiwać użytkowników w [Chinach](https://idax.zendesk.com/hc/en-us/articles/360036736691-IDAX-no-longer-provide-services-for-users-in-China). Przypomina to przypadek kanadyjskiej QuadrigaCX, której klucze również tajemniczo zniknęły wraz z prezesem giełdy. Płynie z tego następująca nauczka: konieczne jest posiadanie kilku osób z kluczami zapasowymi, jeśli prowadzi się ważną usługę, audotyowanie swoich gieł wymian, oraz w idealnym przypadku, przyczynianie się do zastępowania wymian sprawujących kontrolę nad środkami przez [rozwiązania z nich niekorzystające](https://github.com/decred/dcrdex).

Wersja przeglądarki Tor z włączoną obsługą trojanów [brała na cel](https://www.welivesecurity.com/2019/10/18/fleecing-onion-trojanized-tor-browser/) użytkowników Bitcoina, jak odkryło ESET. Trojańska wersja przeglądarki rozprzestrzeniała się z domen `tor-browser[...]org` i `torproect[...]org`.

Zabezpieczenia znanej strony getmonero.org zostały [złamane](https://arstechnica.com/information-technology/2019/11/official-monero-website-is-hacked-to-deliver-currency-stealing-malware/), a binarki z portfelami zostały zastąpione złośliwym kodem. Problem został zidentyfikowany przez użytkownika, który sprawdził podpis i stwierdził, że nie pasuje, co natychmiast [naprawił](https://web.getmonero.org/2019/11/19/warning-compromised-binaries.html) zespół Monero. Co najmniej jeden użytkownik zgłosił utratę środków.

Fałszywy portfel Zcash był [rozprowadzany](https://twitter.com/mineZcash/status/1185908172105453568) poprzez domenę github.su. (_przegapione w wydaniu październikowym_)

Odkryto, zgłoszono, oraz usnięto kolejny fałszywy portfel Decred, dzięki GitHub. Konto o nazwie `decredCoin` i sposób, w jaki została opublikowana podróbka [wydania v1.5.0 ](https://archive.today/ivVRO) wyglądały podobnie do poprzedniej "obowiązkowej aktualizacji v1.5.0 " autorstwa `DecredCoin` opisanej we [wrześniowym numerze](201909.md). Wydaje się, że hakerzy wręcz nie mogą się doczekać finalnego wydania v1.5 _(my też!)_. Jeśli napotkacie coś takiego na GitHubie lub w innym miejscu, prosimy natychmiast zgłosić ten fakt GitHubowi i powiadomić społeczność, aby zminimalizować ewentualne szkody.

Jeśli nie udało Ci się przesłać wystarczającej ilości swoich danych do Google, to firma [planuje](https://www.cnbc.com/2019/11/13/google-reportedly-offering-checking-accounts-next-year.html) wejść do branży bankowej i zaoferować konta czekowe w przyszłym roku. Nazwa kodowa projektu - "Cache" - jest nieco ironiczna, ponieważ w informatyce [cache](https://en.wikipedia.org/wiki/Cache_%28computing%29) często są kasowane.

## O tym wydaniu

To 20. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

- redakcja treści: bee, ekipa Ditto, Dustorf, elian, richardred, s\_ben
- recenzje i komentarze: akinsawyerr, chappjc, davecgh, kyle, lukebp, matheusd, Haon, emiliomann
- ilustracja tytułowa: saender
