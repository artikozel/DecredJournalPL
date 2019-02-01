# Decred Journal – Grudzień 2018

![Decred Journal - December 2018](../img/journal-201812-384.jpg "Decred Journal - December 2018")

Grudzień był miesiącem znacznych postępów, które zakończyły wyjątkowo produktywny rok dla Projektu Decred. Niektóre z najwcześniejszych propozycji zatwierdzonych przez Politeię zaczynają nabierać rozpędu, a personel Ditto dołącza do kanałów komunikacyjnych, aby dalej pracować nad przekazem i planami w zakresie poszerzania i nawiązywania kontaktów na 2019 r. we współpracy z szerszą społecznością.

Release Candidate wersji v1.4.0 oprogramowania jest dostępny do pobrania [na GitHub](https://github.com/decred/decred-binaries/releases/tag/v1.4.0-rc2). Entuzjastów zachęcamy do wypróbowania, podczas gdy regularnym uzytkownikom zalecamy wstrzymanie się ze zmianą do czasu wydania wersji ostatecznej. Jak zawsze, [sprawdź podpisy](https://docs.decred.org/advanced/verifying-binaries/), aby upewnić się, że oprogramowanie w niezmienionej formie pochodzi wprost od naszych programistów.

Portfel [dcrandroid](https://github.com/decred/dcrandroid) dla systemu Android OS również ujrzał swoich pierwszych kandydatów do wydania dostępnych w [sklepie Google Play]((https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet). Korzysta on z trybu SPV, który pozwala mu chronić prywatność użytkowników, żądając bloków bezpośrednio z sieci P2P zamiast od scentralizowanego dostawcy usług, co jest rzadkością wśród portfeli mobilnych. Oprócz ostrzeżenia dotyczącego kandydatów do wydania, należy pamiętać, że środowisko mobilne stanowi dodatkowe zagrożenie bezpieczeństwa i nie jest zalecane do przetrzymywania dużych ilości DCR.

Podczas gdy grudzień był trudnym miesiącem dla całej przestrzeni z związku ze spadającymi cenami, co odbiło się na kwocie płynącej ze Skarbca na finansowane projekty, jednak Decred pozostaje niewzruszony, a scena wciąż jest przygotowana pod ciągłą ekspansję i przyspieszenie prac nad rozwojem przez cały rok 2019.

Szczęśliwego Nowego Roku dla wszystkich czytelników od zespołu Decred Journal!

## Rozwój

[dcrd](https://github.com/decred/dcrd): RC2 v1.4.0 został wydany. Ta wersja zawiera [inteligentny estymator opłat](https://github.com/decred/dcrd/pull/1434), który pozwala użytkownikowi zminimalizować opóźnienie wydobycia lub opłatę, w zależności od potrzeb. [Funkcja ta](https://github.com/decred/dcrd/issues/1412) jest ważna dla Lightning Network i jako ogólny mechanizm radzenia sobie z przeciążeniem sieci. Dołączone do białej strony przychodzące połączenia peer są teraz [dozwolone](https://github.com/decred/dcrd/pull/1516) niezależnie od limitu połączeń, dzięki czemu operatorzy mogą zawsze zezwalać na korzystanie z własnych klientów SPV. Wprowadzono kilka ulepszeń wydajności początkowej synchronizacji, sprawdzania poprawności i operacji sieciowych. Użytkownicy wybierający aktualizację powinni pamiętać o jednorazowej migracji bazy danych, która zajmie 30-60 minut w zależności od sprzętu. Zobacz pełną listę zmian w [uwagach do wydania](https://github.com/decred/decred-binaries/releases/tag/v1.4.0-rc2).

Podatność w narzędziu `go get`, która zezwalała na zdalne wykonywanie kodu podczas korzystania ze złośliwego repozytorium, została [załatana](https://seclists.org/oss-sec/2018/q4/254). Oprogramowanie Decred nie było narażone na wyżej wymienioną podatność. Nawiązując do tematu, w przypadku dcrd wszystkie zmiany zależności, z wyjątkiem środowiska wykonawczego Go, są poddawane audytowi. Jest to jeden z powodów, dla których przygotowanie tak wielu wersji dcrd wymaga tyle wysiłku i przez który liczba zależności powinna być ograniczona. Więcej szczegółów w [tym czacie](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$154476448242812wqgkf:decred.org).

Rozpoczęła się [dyskusja](https://github.com/decred/dcrd/issues/1556) na temat wdrożenia Child Pays For Parent (CPFP) w dcrd.

[dcrwallet](https://github.com/decred/dcrwallet): wersja 1.4.0 RC2 naprawia wiele błędów związanych z SPV i obsługą błędów oraz dodaje wiele nowych punktów końcowych gRPC, które umożliwią nowe funkcje w interfejsach użytkownika końcowego. Połączenia Tor z węzłem dcrd są teraz możliwe dzięki [trybowi proxy](https://github.com/decred/dcrwallet/pull/1294). Domyślna opłata za przekazywanie transakcji spadła do 0,0001 DCR przy wystarczającej rozbudowie sieci. Więcej zmian w [uwagach do wydania](https://github.com/decred/decred-binaries/releases/tag/v1.4.0-rc2).

[Decrediton](https://github.com/decred/decrediton): v1.4.0 Wydanie RC2 zawiera początkowe wsparcie dla Trezora, ulepszenia designu i wiele poprawek. Początkowe [wsparcie Trezor](https://github.com/decred/decrediton/pull/1547) umożliwia użytkownikom korzystanie z Decrediton jako portfela "tylko do obserwacji", który podpisuje transakcje za pomocą urządzenia Trezor. Ta funkcja będzie ukryta za opcją konfiguracji, dopóki nie zostanie wystarczająco przetestowana. Staking nie jest jeszcze obsługiwany, ale jest planowany w najbliższej przyszłości. Mówiąc bardziej ogólnie, portfele typu "tylko do obserwacji" są teraz w stanie [tworzyć niepodpisane transakcje](https://github.com/decred/decrediton/pull/1864), które można przesłać do innego urządzenia w celu podpisania i wysłania do sieci. Strona Governance została poddana gruntownej przebudowie i otrzymała ważną funkcję  [powiadamiania](https://github.com/decred/decrediton/pull/1835) użytkowników o nowych propozycjach i głosowaniach. [Nowa strona](https://github.com/decred/decrediton/pull/1766) do wyboru pomiędzy SPV i trybem pełnego sprawdzania poprawności bloków jest teraz wyświetlana przy pierwszym załadowaniu portfela. Wstępną wersję ciemnego motywu można włączyć w ustawieniach (kolory są jeszcze ostatecznie finalizowane). Więcej informacji na temat tych i innych zmian można znaleźć w [uwagach do wydania](https://github.com/decred/decred-binaries/releases/tag/v1.4.0-rc2).

Na gałęzi głównej (tj. nie zawartej w wydaniu 1.4.0) Decrediton można teraz zbudować dla [Raspberry Pi](https://github.com/decred/decrediton/pull/1904).

Wiele [prac projektowych](https://github.com/decred/decrediton/issues?utf8=%E2%9C%93&q=is%3Aissue+author%3Alinnutee+created%3A2018-12-01..2018-12-31) zostało ukończonych i gotowe są do wdrożenia.

[Politeia](https://github.com/decred/politeia): najnowsze [zaostrzenie bezpieczeństwa](https://github.com/decred/politeiagui/pull/935) zdobyło dla Politei ocenę A + od [securityheaders.com](https://securityheaders.com/?q=test-proposals.decred.org&followRedirects=on), który umieścił ją w top 3% witryny i (na krótko) w Hall of Fame. Funkcja do przeglądania [starych wersji propozycji](https://github.com/decred/politeiagui/pull/949) jest dodawana jako część większego [podglądu diff wersji](https://github.com/decred/politeiagui/issues/973), która wymaga więcej pracy. Politeiavoter teraz [ponawia nieudane zapytania](https://github.com/decred/politeia/pull/639), co naprawia korzystanie z Tora. Obliczenie wyniku głosowania komentarzem zostało naprawione dzięki [przeniesieniu go](https://github.com/decred/politeia/pull/610) z politeiad do politeiawww. Od teraz propozycje [nie mogą być porzucone](https://github.com/decred/politeiagui/pull/936) po zatwierdzeniu głosowania. Te i mniejsze poprawki będą dostępne [na stronie propozycji](https://proposals.decred.org/) po następnym wdrożeniu.

W toku jest tworzenie administracyjnych [kopii danych](https://github.com/decred/politeia/issues/605) i dwie duże zmiany w celu skalowania serwera: [warstwa pamięci podręcznej](https://github.com/decred/politeia/issues/546) i [wsparcie dla websocketów](https://github.com/decred/politeia/issues/547).

[dcrandroid](https://github.com/decred/dcrandroid): 2. kandydat do wydania wersji v1.0.0 jest dostępny w Google Play dla [sieci głównej](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet) i [sieci testowej](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.testnet). Przerobiono w nim całkowicie weryfikację ziarna (ang. *seed*) i interfejsy jego przywracania oraz naprawiono kilka błędów. Listę ulepszeń można znaleźć [na GitHubie](https://github.com/decred/dcrandroid/tree/v1.0.0-rc2). Dyskusja i opinie znajdują się [tutaj](https://www.reddit.com/r/decred/comments/a846ch/decred_wallet_for_android_release_candidate/).

Kolejny RC, który zostanie wkrótce wydany, będzie zawierał kilka drobnych poprawek, jak również lepsze wyświetlanie statusu podczas początkowej synchronizacji, o które prosili niektórzy użytkownicy.

Kładziemy nacisk na usprawnienie konfiguracji dla nowych użytkowników, ponieważ jest to pierwsza rzecz, którą zobaczą, a czasami może być nużąca.

Ograniczenia szyfrowania portfela i ryzyko stawiania na niepewnych smartfonach z Androidem omówiono w [tym czacie](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$154533559847474ZIrlD:decred.org).

[dcrios](https://github.com/raedahgroup/dcrios): progres w większości po prostu synchronizował się ze zmianami z Androida. Wersje testowe dla systemu iOS zostaną udostępnione, gdy tylko zostanie ukończona zostanie wersja Android 1.0.

[dcrdata](https://github.com/decred/dcrdata): wersja 3.1.1 wypuszczona jest na [głównej stronie](https://explorer.dcrdata.org/). Najważniejsze to nowe strony dla [łańcuchów pobocznych](https://explorer.dcrdata.org/side) i [odrzuconych bloków](https://explorer.dcrdata.org/rejects), duże usprawnienia wydajności, wsparcie dla modułów Go, usprawnienia dla trybu [niewymagającego javascript](https://github.com/decred/dcrdata/pull/852) _(dzięki od anty-js dinozaura!)_. Pełne informacje o wydaniu dostępne są [tutaj](https://github.com/decred/dcrdata/releases/tag/v3.1.0). Wydanie obejmuje 129 commitów z 4 miesięcy pracy wykonanych przez 16 autorów kodu. Gratulacje dla zespołu dcrdata!

Na gałęzi master ukończona została funkcja pobierania transakcji dla pojedynczego adresu [jako pliku CSV](https://github.com/decred/dcrdata/pull/894). Połączono kilka dużych refaktorów w celu zastosowania najlepszych nowoczesnych praktyk frontendowych.

Publiczna usługa Tor dla dcrdata została tymczasowo wyłączona po ataku DDoS. Po [dłuższej dyskusji](https://matrix.to/#/!YwropUjOvDAjfbVSzi:decred.org/$154480347443065mKiKp:decred.org) została ona przywrócona pod adresem [dcrdata2opeenddl.onion](http://dcrdata2opeenddl.onion/).

Programiści mogą sprawdzić nowy [obraz Docker](https://github.com/decred/dcrdocker/pull/45), aby zbudować i przetestować dcrdata i nową stronę [FAQ](https://github.com/decred/dcrdata/wiki/FAQ) na wiki.

[Ticket splitting](https://github.com/matheusd/dcr-split-ticket-matcher): wersje [v0.7.0](https://github.com/matheusd/dcr-split-ticket-matcher/releases/tag/v0.7.0) i [v0.7.2](https://github.com/matheusd/dcr-split-ticket-matcher/releases/tag/v0.7.2) zostały opublikowane. Najważniejsze informacje: obsługa klienta SPV (przeczytaj [zastrzeżenia dotyczące prywatności](https://github.com/matheusd/dcr-split-ticket-matcher/releases/tag/v0.7.0)), lepsze zabezpieczenia dzięki tokenowi sesji, obsługa OpenBSD i lepsze raportowanie. Znajdź pliki do pobrania [na GitHub](https://github.com/matheusd/dcr-split-ticket-matcher/releases). Zweryfikuj podpisy, aby upewnić się, że pliki binarne rzeczywiście pochodzą od @matheusd.

[docs](https://github.com/decred/dcrdocs): w oparciu o wcześniej opracowaną infrastrukturę przekierowania, rozpoczęto prace nad [uporządkowaniem adresów URL](https://github.com/decred/dcrdocs/issues/659) i struktury katalogów. Termin "agenda głosowania" został [zmieniony](https://github.com/decred/dcrdocs/pull/733) na "głosowanie nad zasadami konsensusu". Usunięto [strukturę do tłumaczeń](https://github.com/decred/dcrdocs/issues/736), glosariusz został rozszerzony o nowe pojęcia i dodano nowy [przewodnik dla SPV](https://docs.decred.org/wallets/spv/). Dokumentacja dotycząca Politei została [zaktualizowana](https://github.com/decred/dcrdocs/pull/758) poprzez zgrupowanie stron Politei, dodanie strony dla [wytycznych dotyczących propozycji](https://docs.decred.org/governance/politeia/propozycja-wytyczne/) i [przykładowej propozycji](https://docs.decred.org/governance/politeia/example-proposals/).

[decred.org](https://github.com/decred/dcrweb): nagłówki stron zostały [zmienione](https://github.com/decred/dcrweb/pull/457) z javascript na wideo, [usunięto Rocket.Chat](https://github.com/decred/dcrweb/pull/460) ze strony społeczności, a Decred Business Brief jest teraz dostępny jako [strona internetowa](https://decred.org/brief/) poza byciem do pobrania w formacie PDF.

Pozostałe:

* @matheusd zaproponował dowód słuszności koncepcji dla [urządzenia podpisującego transakcje w trybie offline](https://www.reddit.com/r/decred/comments/a3bfyi/raspberry_pi_offline_transaction_signer/), które umożliwia podpisywanie transakcji na innym komputerze (Raspberry Pi). [Daj mu znać](https://www.reddit.com/r/decred/comments/a3bfyi/raspberry_pi_offline_transaction_signer/), jeśli chcesz chciałbyś, żeby bardziej rozwijał ten pomysł.
* [authit](https://authit.co/) jest interfejsem użytkownika dla znaczenia plików sygnaturami czasowymi za pośrednictwem [dcrtime](https://github.com/decred/dcrtime). Jego [kod źródłowy](https://github.com/decred/authit) znajduje się teraz pod szydelm organizacyjnym Decred; dyskusja [tutaj](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$154454253739832PpXgR:decred.org). Zasługi należą się @fernandoabolafio, @tiagoalvesdulce i @vctt.
* @devwarrior [pracuje](https://github.com/xaur/decred-issues/issues/8#issuecomment-447220453) nad proof-of-concept dla interfejsu użytkownika do atomic swaps. Skontaktuj się z nim [na czacie](https://decred.slack.com/team/U6056C1NE), aby rozpocząć współpracę z nim i sprowadzić takie rozwiązanie do ekosystemu Decred.
* Otwarto pull request o dodanie [wsparcia dla QTUM](https://github.com/decred/atomicswap/pull/93) do narzędzia atomicswap; zachęcamy do przeglądu i testowania. Wcześniejszy pull request dotyczący [Ethereum](https://github.com/decred/atomicswap/pull/76) również może skorzystać z dodatkowego przejrzenia.
* Narzędzia wiersza polecenia można teraz budować na systemie Alpine Linux, który korzysta z [musl](https://www.musl-libc.org/) (czystszej implementacji libc), przeczytaj [ten czat](https://matrix.to/#/!HEeJkbPRpAqgAwhXWO:decred.org/$15457968071823GYapk:decred.org) aby uzyskać bardziej szczegółowe informacje.
* Podejmowane są wysiłki w celu skoordynowania tłumaczenia [najważniejszych artykułów dotyczących Decred](https://github.com/artikozel/decred-translations) w celu przedstawienia podstawowych pojęć i założeń Decred większej ilości nieanglojęzycznych użytkowników.

Statystyki aktywności deweloperskiej dla grudnia: 230 aktywnych PR, 196 master commitów, 33K dodanych i 106K usuniętych linijek kodu w 8 repozytoriach. Wkład pochodził od 3-9 programistów na repozytorium.

## Ludzie

Witamy na pokładzie nowych współtwórców, którzy po raz pierwszy dorzucili swoją cegiełkę do projektu: [aerth](https://github.com/decred/dcrwallet/commits?author=aerth) (dcrwallet), [@guang](https://github.com/decred/decrediton/commits?author=Guang168) (decrediton) i [tpkeeper](https://github.com/decred/politeia/commits?author=tpkeeper) (politeia).

[30000fps](http://30000fps.com) jest współtwórcą Decred od roku 2018. Jednym z celów jego pracy było wprowadzenie iluminacji poprzez znalezienie sensownych sposobów wizualizacji i zilustrowania procesów i funkcji, które w innym przypadku byłyby niewidoczne. Przykłady jego pracy można zobaczyć w najnowszych wizualizacjach rozwoju (nadchodzące wydanie [wersji 1.4.0](https://user-images.githubusercontent.com/17774057/50576201-3e124e80-0e15-11e9-83cd-28b50cfd9357.gif) (4 MB), [uruchomienie Politei](https://twitter.com/decredproject/status/1052203697986363392), wydanie [wersji 1.3.3](https://twitter.com/decredproject/status/1044693349205200896)), a także [przebudowa](https://github.com/decred/dcrdesign/issues/27) animowanych nagłówków podstron decred.org.

3 współpracowników zostało [usuniętych](https://github.com/decred/dcrweb/pull/472) ze strony internetowej decred.org.

Kilku współtwórców podzieliło się swoimi doświadczeniami na temat na dołączenia do ekipy Decred [w tym czacie](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org/$154508806344819aIkBV:decred.org), co jest dobrym, pochodzącym z pierwszej ręki opisem do przeczytania jeśli chce się zrozumieć, jak może wyglądać proces wdrażania. Może on być szczególnie przydatny w przypadku osób potencjalnie zainteresowanych uzyskaniem statusu współtwórcy/wykonawcy dla projektu Decred. @richardred opublikował doskonały artykuł pod tytułem [praca dla zdecentralizowanej autonomicznej organizacji Decred](https://medium.com/@richardred/working-for-the-decred-dae-a9cfb17686fa), który szczegółowo opisuje jego podróż z projektem Decred.

## Zarządzanie

W grudniu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 17016 DCR i wydał 12570 DCR. Korzystając ze średniej dziennego kursu DCR/USD w grudniu, równej 17,5 USD, otrzymujemy 298 000 USD we wpływach i 220 000 USD w kosztach. Ponieważ te płatności były przeznaczone na prace zakończone w listopadzie, warto je również rozważyć w kontekście średniej dziennej stawki z listopada w wysokości 32,5 USD - w takim przypadku otrzymane/wykorzystane kwoty USD wyniosą 553 000 USD/409 000 USD.

Oto krótka aktualizacja propozycji od 10 stycznia. Prosimy nie polegać na nich w celu sformułowania własnej opinii na ich temat i polecamy przeczytać oryginalne ich treści i dyskusje na [platformie Politeia](https://proposals.decred.org/).

* [Open Source Research 2](https://proposals.decred.org/proposals/5d9cfb07aefb338ba1b74f97de16ee651beabc851c7f2b5f790bd88aea23b3cb): badania danych z platformy Politeia i analiza współpracowników Git postępują; we wniosku opublikowano 4 propozycje nowych badań.. Prosimy o komentowanie i oddawanie głosów z komentarzami, aby dać autorom badań znać, co jest najbardziej przydatne.
* [Stablecoin](https://proposals.decred.org/proposals/85fc65cef080cfc3564906fd3d488b827d74fc99bb29143ed8aa6c400b765be9) wniosek został w większości skrytykowany, autor anulował propozycję.
* [Integracja Coffee Wallet](https://proposals.decred.org/proposals/45de9806c952c5ffc2fc6782fddbc74c852c26e3fb0e950144b92d75082c4731): właściciel zaproponował zmniejszenie kwoty, o która zabiegał, ale społeczność nie była zbytnio podekscytowana płaceniem za integrację. Wniosek był przez jakiś czas nieaktywny i został oznaczony jako porzucony. Właściciel propozycji później wrócił, aby [powiedzieć](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$15467875879232uBQcG:decred.org), że nie miał na celu porzucenia propozycji.
* Odrzucone wnioski: [reklamy radiowe](https://proposals.decred.org/proposals/7fe5d07a4ffff7dc6a83383018823d880b1c1db0a29305e74934817cf2b4e2ce) (69% Nie), [Decredex](https://proposals.decred.org/proposals/e78bc28631d0e682912e3ece25944481bf978b906ea44b1ed36470c0f48b27fc) (96% Nie), [integracja bankomatów kryptowalut](https://proposals.decred.org/proposals/bb7e19283d5c65fed598d5a2f4afcc2b5d2eab187b9cb84fc4304430f80b5ad1) autorstwa Bcash (89% nie); udział wynosił od 24 do 31% biletów.
* [Baeond](https://proposals.decred.org/proposals/f545b359fcf1b40b356e9cb556cb422cc7ff01b628b577f804cdc45ce414f5dd) autonomiczna gra karciana futurepunk: dyskusje trwają, autor angażuje się w komentarze i czat oraz aktualizuje propozycję w odpowiedzi na opinie. Wiele osób jest zdezorientowanych tym, jaką  korzyść ekosystemowi Decred może przynieść ta propozycja.
* [Partnerstwo ze Smart Reach](https://proposals.decred.org/proposals/cf7143c93d35f886be03d749396e9202c7837a3d3cbbe876f93c3a7d18ec2028): dyskusje trwają.

[Nagroda za znalezione bugi:](https://proposals.decred.org/proposals/d33a2667469b56942adf42453def6cc2292325251e4cf791e806939ea9efc9e1) propozycja została zaakceptowana przy 90% głosów na tak i udziałem głosujących na poziomie 30%. @degeri pokazał doskonały przykład przechodzenia przez wszystkie etapy: dołącz do społeczności i zademonstruj umiejętność wykonywania pożytecznej pracy, określ coś, czego w ekosystemie brakuje, przygotuj pomysł i przepuść go przez parę rund opinii, prześlij propozycję, zaangażuj się w dyskusję z osobami komentującymi i dostosuj propozycję uwzględniając opinię społeczności i ostatecznie uzyskaj poparcie i zgodę na wdrożenie. [Znamiennym faktem](https://twitter.com/lukebp_/status/1078691610253250560) jest to, że Decred jest jednym z nielicznych projektów, w których autor znany jedynie pod pseudonimem może zbudować zaufanie i odnieść sukces poprzez ustanowienie historii dostarczania wysokiej jakości pracy.

Aby uniknąć typowych błędów i stworzyć udaną propozycję, przeczytaj [wytyczne dotyczące wniosków](https://docs.decred.org/governance/politeia/proposal-guidelines/) autorstwa @s_ben (zainspirowane doskonałym [komentarzem](https://proposals.decred.org/proposals/85fc65cef080cfc3564906fd3d488b827d74fc99bb29143ed8aa6c400b765be9/comments/2) autorstwa @nnnko56).

Company 0 nie pobiera ze Skarbca opłat za prace prowadzone nad prywatnością, co wyjaśniono w [tym wątku](https://www.reddit.com/r/decred/comments/a6l00i/why_is_the_community_not_voting_on_implementing/).

Dyskusje: [w tym czacie](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org/$154502025444491kdLiq:decred.org) omawiane jest zachowanie oszczędności przy wydatkach ze Skarbca, zwłaszcza w złych warunkach rynkowych. [Ten wątek](https://www.reddit.com/r/decred/comments/aa5jvn/any_updates_on_antonopouloss_veiw_of_decred/) rozłożył na części pierwsze często występujące argumenty przeciwko systemowi zarządzania Decred: "nie wiemy, czy system zarządzania działa, ponieważ jeszcze nie zawiódł" i "w systemie nie zaistniała jeszcze żadna kontrowersja". Okazuje się, że trudno jest nawarstwić się kontrowersjom w systemie, który zaprojektowany został właśnie z myślą o tym, aby ich unikać.

O wiele bardziej zniuansowany opis działalności Politei daje nam @richardred w [wydaniu 8.](https://medium.com/politeia-digest/issue-8-dec-5-dec-11-2018-23bb061a08a0) oraz [wydaniu 9.](https://medium.com/politeia-digest/issue-9-dec-12-dec-31-2018-67b65b5bf30) Politeia Digest. Podsumowanie to zawiera wiele interesujących szczegółów odnośnie każdej propozycji. Numer 9 zawiera przegląd danych z Politei z roku 2018 od momentu jej uruchomienia. Wszystkie poprzednie wydania możesz znaleźć i wystawić o nich opinię [tutaj](https://github.com/RichardRed0x/politeia-digest).

## Sieć

Hashrate: grudniowy hashrate na początku miesiąca plasował się na poziomie 167 Ph/s i zakończył go w okolicach 183 Ph/s, osiągając szczyt w ok. 207 Ph/s oraz najniższy poziom w granicach 110 Ph/s. Przez większość miesiąca hashrate miał średnią wartość ok. 150 Ph/s. Na dzień 10. stycznia, moc obliczeniowa puli wydobywczych przedstawiałą się następująco: poolin 34%, F2pool 27%, UUPool 7.4%, btc.com 7%, Luxor 3.8%, BeePool 2.6%, coinmine 1.1%, oraz pozostałe na poziomie 17% za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Staking: 30-day average ticket price was 103 DCR (+0) per dcrstats.com. The price varied between 101 DCR and 107 DCR. Locked amount was 4.14-4.23 million DCR, which corresponded to 46.3-47.1% of the available supply.

Nodes: As of Jan 1 there were 192 public listening nodes and 253 normal ones per [dcred.eu](https://dcred.eu/nodeStats). Version distribution: 1.5% are v1.5.0(pre) dev builds, 1.8% on v1.4.0(rc1), 5.3% on v1.4.0(pre) (-1.2%), 55% on v1.3.0 (+5%), 20% on v1.2.0 (-5%), 10% on v1.1.2 (-1%), 4% on v1.1.0 (-1%).

There are many more [interesting stats](https://github.com/xaur/decred-news/issues/41) we'd like to present in this section, let us know if you can help.

Block 300,000 was mined in December and the mined DCR is now over 9,000,000. Congratulations to all!

## Mining

Whatsminer D1:

* review was posted [in Chinese](https://www.cybtc.com/forum.php?mod=viewthread&tid=41377&fromuid=6) ([Google translation](https://translate.google.com/translate?sl=auto&tl=en&hl=en&u=https%3A%2F%2Fwww.cybtc.com%2Fforum.php%3Fmod%3Dviewthread%26tid%3D41377%26fromuid%3D6))
* Luxor posted a [setup guide](https://medium.com/luxor/whatsminer-d1-decred-setup-guide-182eeccaed99)
* Whatsminer.net [reported](https://twitter.com/whatsminer/status/1075810531838091265) to have shipped all batch 1 orders

Bitmain's Antminer DR5 miner was [introduced](https://twitter.com/Antminer_main/status/1072435004142182400) on Twitter and met with some criticism. [Specs](https://www.asicminervalue.com/miners/bitmain/antminer-dr5-34th): 34 Th/s at 1,800 W, prices start [from $1,400](https://www.asicminervalue.com/miners/bitmain/antminer-dr5-34th). [This](https://www.reddit.com/r/decred/comments/a9iqbl/got_voted_to_0_in_rcryptocurrency_maybe_ill_get/) thread discussed the unit along with challenges for small or hobbyist miners.

Be careful when ordering miners from eBay, you may get [just the weight](https://matrix.to/#/!NNzHoaSdnsbZDQOXJr:decred.org/$154491308943809bYuYs:decred.org).

## Integrations

The hardware wallet company Ledger announced that the long-awaited DCR integration is complete:

> We are excited to announce that the Ledger Nano S and Ledger Blue are now compatible with Decred. Decred is now available on Ledger Live and marks the first native Ledger Live integration since its launch. Read more [here](https://www.ledger.fr/2018/12/11/ledger-nano-s-ledger-blue-and-ledger-live-now-support-decred-transactions/) ([@LedgerHQ](https://twitter.com/LedgerHQ/status/1072446149863329792))

DCR storage is possible through Ledger Live, an application that now acts as a one-stop-shop for accessing and interacting with your crypto assets since Ledger discontinued the use of their respective apps earlier this year.

Cobo Wallet [announced](https://twitter.com/cobo_wallet/status/1070805250376900609) a custodial staking service. Discussed [here](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$154413818735775gNTIq:decred.org).

For any wallet software and hardware, always do your own research and ask how it works. Do you control the keys? Do you lose consensus and Politeia voting rights? Does it talk to Decred full nodes directly or through intermediaries? Does the service share your data with 3rd parties? Is the source code open and auditable?

## Outreach

> December marked an exciting month for Decred, as Ditto began work. The first initiative was to make introductions and determine workflow. You'll now see our good friends, Liz Bagot (@liz\_bagot), Trey Ditto (@treydpr), Margaret Mei (@margaret\_mei), Blain Rethmeier (@blainr), and Milvian Preito (@milvian) in various Matrix rooms, including #marketing, #ditto\_pr, and #writers\_room.
>
> Work began in earnest on messaging, which can be viewed [here](https://docs.google.com/document/d/1BCah1EKLHpwgkvVcWRWJTRC68iWeGPdbGSrhEw35XhU/edit). Continued input is always valued. Concurrently, we're working with the design team to integrate new messaging into the site and to expand the content with new pages further explaining important aspects of Decred.
>
> Messaging should be agreed upon in January, and a work will begin on the website. A plan including events and other tactics will also be published in January. (@Dustorf)

Ditto people joined #marketing and the room was very hot throughout the month with lots of brainstorming and discussions about messaging.

@Dustorf, @jy-p and Ditto met in New York and posted a report [in chat](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154413732235771XIVBH:decred.org). Among other things, they discussed challenges related to attracting new developers and contributors, spreading the word about Decred to knowledgeable investors, institutions, and governments, as well as going over the long term vision for the project.

Trey [published](https://medium.com/decred/decred-and-ditto-in-2019-c9063a6bca06) Ditto's big picture look at 2019 and the strategy for Decred. Following that a [survey](https://www.reddit.com/r/decred/comments/a7cul1/decred_and_ditto_in_2019_share_your_ideas/) was held on Reddit asking the community how would they describe Decred, what media do they read and how they think Decred should target developers.

Mid-December @liz_bagot gave the inaugural Ditto [Bi-Weekly Update](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154482468943386bBAIp:decred.org), and later summarized the work for December:

* Had a 2.5-hour onboarding session with Dustin and Jake in our Brooklyn office in early December.
* Created a foundational messaging platform containing a breakdown of Decred's audiences, an about section, a mission statement, a vision statement, and positioning statements for each unique audience. We [submitted](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154524074346294yVYFR:decred.org) the messaging platform to the Decred community for feedback and intend to do another iteration of the document that incorporates the feedback in January.
* Attended and sent reporters from Breaker Mag, Forbes, and Fortune to Decred's meet up in NYC.
* Arranged and staffed interviews between couple big outlets and Decred community members. No set publication dates yet.
* We pitched Jake's commentary on 2019 crypto predictions with crypto reporters and secured coverage in [NullTX](https://nulltx.com/decred-co-founder-pronounces-2018-as-the-death-of-the-ico-model/), [Crypto Briefing](https://cryptobriefing.com/crypto-2019-institutional-adoption/), [The Daily Hodl](https://dailyhodl.com/2018/12/21/after-bitcoin-rallies-18-industry-insiders-weigh-in-on-a-bull-run-and-cryptos-next-turn/) and [CCN](https://www.ccn.com/2018-in-4-words-icos-and-ethereum-are-dead/).

Now a total of 5 well-known community members have the rights to tweet via @decredproject Twitter account. You can read about how it works [here](https://medium.com/@richardred/working-for-the-decred-dae-a9cfb17686fa#bd70).

## Events

Decred held it's first meetup in New York City on Dec 5 at Distributed Global in the flatiron district in NYC. The audience of about 80 people included VC's, developers from other projects, media, and members of the Decred community. @jy-p gave a Decred overview presentation ([photo](https://twitter.com/CryptoLeslie/status/1070769160878219266)), then delved into the technical details of the Politeia Proposal System including how it works and the potential breadth of its applications.

Next, Chris Dannen, Founder of Iterative Capital, discussed the way work has evolved, particularly in the era of free open-source software. Iterative Capital's [Thesis](https://iterative.capital/thesis/) explains this thinking in much greater detail. He explained how Decred's treasury brilliantly dovetails into a massive work trend that gives workers desired autonomy and enables them to do their best work.

Finally, Chris Burniske and Joel Monegro of Placeholder VC held a fireside chat explaining Decred's value from the perspective of an institutional investor. Chris revealed the financial reasoning, including:

1. Team - btcsuite when released was as good as anything put out by Bitcoin Core
2. Hybrid PoW/PoS system is more secure than any other network
3. Treasury funding allows development to be funded long term
4. Fork resistance - Decred is designed to keep the community together through consensus

Joel shared his appreciation for Decred's governance system, and its ability to make Decred polymorphic, adding features and functionality as the community decides. They concluded that Decred is built/designed for a multi-decade horizon. They shared some of the good work they're doing to on behalf of Decred with respect to custodianship, exchanges, and institutional staking, and concluded that the biggest issue Decred currently faces is liquidity.

Founders Night took place next day on Dec 6, and was Distributed Global's holiday party. They brought in all their fund managers from various offices, and invited their investors, partners, and members of various projects within their portfolio. It was a great opportunity to meet those various constituencies and build relationships for future events in NYC. Spring is being targeted for the next Decred event in NYC.

Other attended events:

* Presentation in Technology University in Amozoc, Mexico. @elian talked to students about skills for the future and [noted](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15466174667748MPUAY:decred.org): "As part of my experience, I briefly talk about Decred as an innovative project in which digital skills become essential tools for collaboration. This was not a crypto meetup but rather a motivational talk for BA students to push them to acquire digital skills, this is a small university far outside big cities so this kind of content is very appreciated. As part of my experience in technology and digital industries, I share with them my experience working in an open source project like Decred as an example of the opportunities that arise from the internet industries. I think it was very interesting for them to realize that there is a massive economy flowing through the Internet with endless possibilities.". ([photo](https://twitter.com/Decred_MX/status/1071230180398641154))
* [Introduction to Decred](https://cryptocanucks.com/events/an-introduction-to-decred-toronto/) in Toronto, Canada. @michae2xl and @zubairzia0 hosted the event and [noted](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15464604416182ZLeNH:decred.org) that despite small attendance the people were looking to connect with a local Decred community and were excited to help to organize next event. ([photo](https://twitter.com/Decred_CA/status/1079191530362101760))

Upcoming:

* [OKEx Taiwan MeetUp](https://www.eventbrite.hk/e/okex-global-meetup-tour-2019-taiwan-tickets-54689867867) in Taipei, Taiwan on Jan 17. The first half of the event will be intros by the 3 projects (Decred, EOS and NEM, 20 min each), and the other half will be a panel discussing around on-chain voting (30 min). @morphymore will be speaking.
* [Binance Blockchain Week](https://www.binancefair.com/) in Singapore on Jan 21-22. @guang will attend and represent Decred.
* [10 lat Bitcoina](https://10latbitcoina.com.pl/) in Warsaw, Poland on Jan 26. @karamble will deliver a presentation at the conference celebrating the 10th anniversary of the Bitcoin whitepaper and Bitcoin itself. Decred specifics are to be announced.
* [TabConf](https://tabconf.com/) in Atlanta, USA on Feb 8-10. @moo31337 will present "Decred 101: An introduction to Decred" on Feb 9.
* [The North American Bitcoin Conference](https://btcmiami.com/) in Miami, USA on Jan 16-18. @jy-p will present Politeia and explore a wide variety of applications that could utilize it. Please message @Dustorf if you're interested to help out at the show.
* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) in Sao Paulo, Brazil on Feb 12-17. Decred will have speakers and a dedicated area for hackathons.
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) in Guadalajara, Mexico on Apr 22-26. Decred will have a booth. @elian will present an overview of Decred with Q&A, plus there will be walkthroughs how to use software and vote. Contact @elian if you're interested in helping/attending.

Ask in [#event_planning](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org) room for any questions.

## Media

Selected articles:

* Bitcoin Miners Go Silent As Price Falls ([cryptobriefing.com](https://cryptobriefing.com/bitcoin-miners-silent-price-falls/), also [in Chinese](https://www.jinse.com/bitcoin/288904.html))
* Detailed analysis of Decred fork resistance by @Haon ([medium](https://medium.com/decred/detailed-analysis-of-decred-fork-resistance-93022e0bcde7))
* Decred and Ditto in 2019 by Trey Ditto ([medium](https://medium.com/decred/decred-and-ditto-in-2019-c9063a6bca06), community survey and discussion [here](https://www.reddit.com/r/decred/comments/a7cul1/decred_and_ditto_in_2019_share_your_ideas/))
* Fundamental Pick: Decred by BBOD Research ([blog.bbod.io](https://blog.bbod.io/decred-dcr-fundamental-analysis/), also [in Chinese](https://www.weibo.com/ttarticle/p/show?id=2309404313596447316959) and [Japanese](https://cointyo.jp/article/10005567))
* Decred Co-founder Pronounces 2018 as the "Death of the ICO Model" ([nulltx.com](https://nulltx.com/decred-co-founder-pronounces-2018-as-the-death-of-the-ico-model/))
* 2018 in 4 Words - ICOs and Ethereum Died ([ccn.com](https://www.ccn.com/2018-in-4-words-icos-and-ethereum-are-dead/))
* The practical cypherpunk: Marco Peereboom of Decred ([coinrivet.com](https://coinrivet.com/the-practical-cypherpunk-marco-peereboom-of-decred/))
* Decred: Governance and Funding Reimagined ([51pct.io](https://51pct.io/decred-governance-and-funding-reimagined/))
* Working for the Decred DAE by @richardred ([medium](https://medium.com/@richardred/working-for-the-decred-dae-a9cfb17686fa))

Translations:

* Decred Journal - November 2018 [in Spanish](https://medium.com/@decred_es/revista-decred-noviembre-2018-a3e52c5fc1a9) by @elian, [in Polish](https://github.com/artikozel/DecredJournalPL/blob/master/journal/201811_DecredJournalPL.md) by @kozel and [in Russian](https://medium.com/decred-russia/decred-journal-%D0%BD%D0%BE%D1%8F%D0%B1%D1%80%D1%8C-2018-d0aceacfd72a) by @DZ, [in Chinese](https://medium.com/@guang.dcr/decred%E6%9C%88%E6%8A%A5-11%E6%9C%88-1ddac6598830) by @guang. November issue was the biggest so far (59 KiB), thank you all for the epic translation effort!
* All translations of Decred Journal are linked on the [home page](https://xaur.github.io/decred-news/)
* [Detailed analysis of Decred fork resistance](https://medium.com/decred/detailed-analysis-of-decred-fork-resistance-93022e0bcde7) by @Haon - [in Polish](https://github.com/artikozel/decred-articles/blob/master/Polish/into-polish/decredforkresistance.md) by @kozel
* [How to Get Hired as a Decred Contractor](https://medium.com/decred/how-to-get-hired-as-a-decred-contractor-e1435842df10) by @Haon - [in Chinese](https://www.weibo.com/ttarticle/p/show?id=2309404315589245067163) by @guang

Videos:

* On The Record w/ Murad Mahmudov - Bitcoin for 2019 on Tone Vays show ([youtube](https://www.youtube.com/watch?v=pjXzrAOhAPo), Decred explanation around 1h mark)

Audio:

* Free Talk Live 2018-10-27 Interview with Marco Peereboom of Decred at the Texas Bitcoin Conference ([soundcloud](https://soundcloud.com/freetalklive/free-talk-live-2018-10-27#t=40:50), _missed in Oct issue_)
* Unchained episode 100, Past Guests and Listeners Take Over the Show ([unchainedpodcast.co](http://unchainedpodcast.co/100th-episode-past-guests-and-listeners-take-over-the-show-ep100), @joshuam at 55:12)
* Episode 18: Murad Mahmudov on Bitcoin ([didyouknowcrypto.com](http://didyouknowcrypto.com/episode-18-murad-on-bitcoin/)). Topics covered are utopianism, Austrian economics, the coming recession, the future of Bitcoin, and that Decred should be in top 3.

## Community Discussions

Community stats as of Jan 1:

* Twitter followers: 39,884 (-120)
* Reddit subscribers: 9,241 (+110)
* Matrix users: 221 (+18)
* Slack users: 6419 (+66)
* Telegram users: 4734 (+92)
* YouTube subscribers: 3738 (+2)
* Facebook followers: 3121 (+16), likes: 2880 (+13)
* LinkedIn followers: Decred page 450 (+17), Politeia page 24 (+4)
* GitHub dcrd stars: 458 (+11), forks: 1192 (+33)

On top of that there are Telegram communities in Chinese (661, +119), Portuguese (435, +99) and Italian (120) languages. Also, @michae2xl is running @decredproject on Instagram with 396 followers as of Jan 6.

Comm systems news:

* @dhill shot down [a bug](https://github.com/42wim/matterbridge/pull/644) in matterbridge that blocked the relay of messages from Slack to other platforms. Please report any bridge issues you notice.
* #smart\_contracts channel was archived due to inactivity.
* Rocket.Chat is being [retired](https://github.com/decred/dcrweb/pull/460).

Prototype [community issue tracker](https://github.com/xaur/decred-issues) was started to discuss actionable ideas in a more structured format. Any idea that benefits the project can be discussed. As of Jan 10 there are [73 issues](https://github.com/xaur/decred-issues/issues) like [article ideas](https://github.com/xaur/decred-issues/labels/article), [PR](https://github.com/xaur/decred-issues/labels/PR), [archiving](https://github.com/xaur/decred-issues/labels/archiving) and data preservation, or discussion of [communication platforms](https://github.com/xaur/decred-issues/labels/comms). For example, [this issue](https://github.com/xaur/decred-issues/issues/54) captures a challenging task to find a good name for Decred's hybrid PoW/PoS consensus algorithm and lists all options suggested so far. You can subscribe to everything with the Watch button on top, or to individual issues with Subscribe button on the right panel. There is a popular belief that "GitHub is for developers" - this is not the case. Posting issues and comments and '+1' is no harder than using Reddit or chat and in fact multiple non-developers already contribute doing just that.

Reddit incident showed us another weakness in the platform. Multiple threads were started and spurred useful discussion, but were later removed by the author. This wasted the effort of all people who bothered to reply. The deleted threads were somewhat [resurrected](https://www.reddit.com/r/decred/comments/a6ywpj/deleted_threads_with_valuable_discussion/), but generally this incident shows an attack/sabotage vector: trigger the discussion and then delete the thread, wasting community's energy. Reddit has no defense from this as moderators cannot disallow users to delete their content. The event has led to a discussion of a [Reddit replacement](https://github.com/xaur/decred-issues/issues/38) that could probably derive from Politeia.

For yet another time, a lot of strange Reddit activity was timed close to our major release. It is either an unusual amount of questions about less relevant issues, or "innocent" questions about trivial things, or something similar. All coming from accounts never seen before and that stay after the short interaction. This notice is to inform people who care about the project to watch out for weird activity that can sap project's, as well as your individual energy. Read [this chat](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$154531182347084ccYxu:decred.org) for more details.

## Markets

In December DCR was trading between USD 14.2-21.4 / BTC 0.0042-0.0058. The average daily rate was $17.5. A short price rise to USD 20.9 / BTC 0.0058 happened on volume increased to USD 5-6 million compared to USD 0.8-1.2 million on other days. Note that the trading volume data is not reliable, as noted below.

## Relevant External

Vertcoin (VTC) was the subject of a majority (51%) [attack](https://medium.com/coinmonks/vertcoin-vtc-is-currently-being-51-attacked-53ab633c08a4) (4 incidents) in which 22 reorgs and 15 double spends occurred, costing the victims around $100,000. This reaffirms the vulnerability of coins that are not the dominant use for their miners (GPU-mineable or ASIC-resistant, but also Bitcoin forks) to be attacked by miners who have appropriate hardware and no interest in the health of the blockchain. One of the impacts of these attacks is that the coin comes to be regarded as insecure, because it has failed in its purpose before. Anyone who is still willing to accept it may require a very high number of confirmations before confirming a transfer, making the coin slow to move.

The [Horizen](https://www.horizen.global/) (previously ZenCash) team lead recently announced a [strategic action](https://blog.zencash.com/re-strategic-actions-for-horizen-from-rolf-versluis/) to increase the Treasury block rewards from 10% to 20%, reducing the share of rewards for miners. After a 90% reduction in price, and significant reductions to staffing and other costs, it was felt that to cut costs any further would mean jeopardizing the project. As the Treasury system being developed by IOHK is still a [prototype](https://blog.zencash.com/dao-prototype/) not yet ready for use, the Horizen team felt the need to make a unilateral decision to change the block reward.

EOS block producer [began paying](https://cointelegraph.com/news/eos-node-offers-users-financial-rewards-for-votes-reignites-decentralization-debate) holders that voted for it.

The first round of voting on Aragon Governance Proposals (AGPs) has been [delayed](https://forum.aragon.org/t/agp-vote-delay-announcement/426) due to potential network instability around the Ethereum Constantinople hard fork - hopefully "blockchain down for maintenance" is not a problem Decred will encounter with Politeia. The CEO of Aragon Association [published](https://forum.aragon.org/t/agp-wishlist-and-blacklist/355) a blacklist and wishlist for proposals before proposal submissions opened. In the first proposal the AGP [process](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-1.md) itself was [approved](https://blog.aragon.org/final-results-from-the-agp-1-vote/) by 99.97% of the ANT that voted. In total 2.6% of all ANT tokens voted on the first proposal, from 45 unique addresses, with ~60% of ANT votes coming from one address. AGPs go through a review by the board of the Aragon Association, then a community review, before a 48 hour voting period opens.

2 million BTCP were mined via an exploit and went unnoticed for months until CoinMetrics [noticed](https://coinmetrics.io/bitcoin-private) that something is wrong with the supply. Developer team [posted](https://medium.com/@bitcoinprivate/official-statement-on-coinmetrics-report-6f1cef176c05) an official statement confirming the inflation exploit. The bug was merged on Jan 5 2018 together with a patch from a bounty hunter that disengaged after receiving the reward for his work. Just one missing line of code caused huge damage to the network's value proposition. We can learn a lot from this unfortunate experience: extensive test coverage, super critical review of consensus code, established reputation of developers working on mission critical parts, and having multiple implementations of the protocol are all very important to build a system we can trust money to.

There was an [attack](https://www.reddit.com/r/CryptoCurrency/comments/a9yji3/electrum_wallet_hacked_200_btc_stolen_so_far/) on Bitcoin's Electrum infrastructure. Someone started a lot of malicious Electrum servers that prompted the user to "upgrade" to a malware version and stole 200+ BTC. The Electrum model involves a network of servers that sit between clients and full nodes. Each client depends on the server they connect to, this compromises user privacy as the owners of those servers can infer which wallets the users own. If Electrum servers were compromised this would open up some additional attacks. Decred chose not to develop Electrum infrastructure but instead go straight for SPV based on client-side filters. This delayed the development of light clients, but the SPV mode now working in dcrwallet, Decrediton and drcandroid connects to full nodes directly and functions independently of any service provider, which enhances users' privacy as a result.

Security researchers [demonstrated](https://media.ccc.de/v/35c3-9563-wallet_fail) multiple ways to hack most popular hardware wallets, if in physical possession of the device.

Latest exchanges trading volume report by [blockchaintransparency.org](https://www.blockchaintransparency.org/) concluded that of the coinmarketcap.com top 25 BTC pairs over 80% of volume is wash traded. Another unhappy finding is that the average project spent over $50,000 on listing fees. The report has spurred [the idea](https://github.com/xaur/decred-issues/issues/34) to analyze the trading volume for DCR.

Coinbase [seeks](https://www.coindesk.com/coinbase-wants-to-own-buidl-trademark-filing-reveals) to own the term "BUIDL".

Many cryptocurrency services and projects [seem to be](https://twitter.com/tangleblog/status/1068094875533479937) owned or co-owned by just a handful of entities with banks at the top.

Several centralized exchanges [failed](https://www.ccn.com/several-exchanges-said-to-be-failing-bitcoin-ownership-event/) to serve withdrawals during the annual [Proof-of-Keys](https://www.proofofkeys.com/) event.

Slack accidently [blocked](https://www.engadget.com/2018/12/22/iran-sanctions-slack/) people who visited Iran before. Later Slack [apologized](https://slackhq.com/an-apology-and-an-update) for the incident and clarified the situation. But the signal is clear and not surprising: Slack Technologies is a ([venture funded](https://en.wikipedia.org/wiki/Slack_Technologies)) U.S. corporation that complies with U.S. laws. In contrast, Matrix rooms can be federated over multiple servers, so even if some participating servers are shut down, servers in other jurisdictions can keep serving the chat and history.

There have been a [number](https://www.wsj.com/articles/layoffs-become-the-latest-thing-in-cryptocurrency-1544471449) [of](https://www.newsbtc.com/2019/01/09/cryptocurrency-shapeshift-layoffs/) [articles](https://www.businessinsider.com/bitmain-layoffs-2018-12) in December about layoffs in the cryptocurrency space (and some saying it's [not so bad](https://cointelegraph.com/news/better-than-corporations-layoffs-in-crypto-are-on-the-rise-still-lower-than-in-other-industries) relative to other sectors). For other projects with Treasuries, these are also hard times, as noted for Horizen above and can be seen in some Dash [community discussions](https://www.reddit.com/r/dashpay/comments/ac9ca4/dash_nigeria_defunding_statement_and_path_forward/). We can thank the people who managed the Treasury in the pre-Politeia era for its healthy balance, this is the reason that Decred is still looking to expand its workforce while other projects contract. With DCR at $17.5 for December, that will likely be the first month where Treasury outgoings are greater than the incoming block rewards. Even if DCR/USD stays low for some time, the Treasury could maintain its current USD-equivalent spending for several years (rough estimate is 8) at this rate before cut-backs became necessary.

Amid the larger wave of layoffs in the crypto sphere, Bitmain [allegedly](https://cointelegraph.com/news/reports-bitmain-allegedly-fires-all-bch-developers-in-wave-of-redundancies) fired its entire staff of Bitcoin Cash developers, which included the Copernicus team.

[Copernicus](https://github.com/copernet/copernicus) is an implementation of the Bitcoin Cash protocol written in Go that utilizes btcsuite. The pre-release version of software was [announced](https://news.bitcoin.com/an-alternative-client-has-mined-bitcoin-cash-block-558847/) and mined its first block in December. On their website the authors [thank](https://www.copernicuscore.org/btcd.html) btcsuite developers for their work and acknowledge their contribution to the Bitcoin ecosystem. On the blog Copernicus team [noted](https://medium.com/@copernicusbit/the-copernicus-project-launched-the-pre-release-v0-0-6-dc572a924214) that the software "reorganizes and redesigns the software structure for the original client in order to make the structure more concise, reduce the learning difficulty for developers and increase diversity of clients to ensure safety of the entire BCH network".

Copernicus is not the first effort to diversify Bitcoin Cash's network that already had several C++, Rust and JavaScript implementations in development. In September, two other implementations of Bitcoin Cash written in Go were [unveiled](https://news.bitcoin.com/developers-unveil-two-new-bitcoin-cash-full-node-clients-written-in-go/). [Gocoin-cash](https://github.com/CounterpartyXCPC/gocoin-cash) comes from the creators of [counterparty.cash](http://counterparty.cash/) and is based on [gocoin](https://github.com/piotrnar/gocoin) (another full Bitcoin node implementation in Go). [bchd](https://github.com/gcash/bchd) in turn comes from OpenBazaar developer [Chris Pacia](https://github.com/cpacia). In the initial [announcement](https://www.yours.org/content/introducing-bchd-aee6a07feb00) of bchd Chris noted that btcsuite is "one of the best designed and well-written Bitcoin codebases" and explained that it allows to engage more developers and build new features faster, compared to C++ implementations. It also gave them the private client-side SPV "for free". The beta was [announced](https://medium.com/@bchd.cash/bchd-beta-release-46f89c677c47) in November - two months since forking from btcd the team grew to 9 contributors and implemented several improvements over btcd.

The relevance and good news for Decred here is that a lot more developers are looking at btcsuite codebase now, on which Decred is based and can benefit from.

## About This Issue

This is the 9th issue of Decred Journal. It is available on [GitHub](https://xaur.github.io/decred-news/journal/201812). Past issues and translations are available [here](https://xaur.github.io/decred-news/).

Chinese translation by @guang is available on [Medium](https://medium.com/@guang.dcr/decred%E6%9C%88%E6%8A%A5-12%E6%9C%88-eb8b42a5e4fd), [Weibo](https://www.weibo.com/ttarticle/p/show?id=2309404327424178422533) and [GitHub](https://github.com/Guang168/DecredCNJournal/blob/master/201812_DecredJournalCN.md).

Most information from third parties is relayed directly from source after a minimal sanity check. The authors of Decred Journal have no ability to verify all claims. Please beware of scams and do your own research.

Your feedback and contributions are welcome on Reddit, [GitHub](https://github.com/xaur/decred-news/issues) and [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Credits (alphabetical order): bee, Dustorf, guang, Haon, kozel, liz_bagot, oregonisaac, raedah, richardred, saender, zubairzia0.
