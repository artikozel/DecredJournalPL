# Decred Journal – Grudzień 2018

![Decred Journal - December 2018](../img/journal-201812-384.jpg "Decred Journal - December 2018")

Grudzień był miesiącem znacznych postępów, które zakończyły wyjątkowo produktywny rok dla Projektu Decred. Niektóre z najwcześniejszych propozycji zatwierdzonych przez Politeię zaczynają nabierać rozpędu, a personel Ditto dołącza do kanałów komunikacyjnych, aby dalej pracować nad przekazem i planami w zakresie poszerzania i nawiązywania kontaktów na 2019 r. we współpracy z szerszą społecznością.

Release Candidate wersji v1.4.0 oprogramowania jest dostępny do pobrania [na GitHub](https://github.com/decred/decred-binaries/releases/tag/v1.4.0-rc2). Entuzjastów zachęcamy do wypróbowania, podczas gdy regularnym uzytkownikom zalecamy wstrzymanie się ze zmianą do czasu wydania wersji ostatecznej. Jak zawsze, [sprawdź podpisy](https://docs.decred.org/advanced/verifying-binaries/), aby upewnić się, że oprogramowanie w niezmienionej formie pochodzi wprost od naszych programistów.

Portfel [dcrandroid](https://github.com/decred/dcrandroid) dla systemu Android OS również ujrzał swoich pierwszych kandydatów do wydania dostępnych w [sklepie Google Play](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet). Korzysta on z trybu SPV, który pozwala mu chronić prywatność użytkowników, żądając bloków bezpośrednio z sieci P2P zamiast od scentralizowanego dostawcy usług, co jest rzadkością wśród portfeli mobilnych. Oprócz ostrzeżenia dotyczącego kandydatów do wydania, należy pamiętać, że środowisko mobilne stanowi dodatkowe zagrożenie bezpieczeństwa i nie jest zalecane do przetrzymywania dużych ilości DCR.

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

[30000fps](http://30000fps.com) jest współtwórcą Decred od roku 2018. Jednym z celów jego pracy było wprowadzenie iluminacji poprzez znalezienie sensownych sposobów wizualizacji i zilustrowania procesów i funkcji, które w innym przypadku byłyby niewidoczne. Przykłady jego pracy można zobaczyć w najnowszych wizualizacjach rozwoju (nadchodzące wydanie [wersji 1.4.0](https://user-images.githubusercontent.com/17774057/50576201-3e124e80-0e15-11e9-83cd-28b50cfd9357.gif) (4 MB), [uruchomienie Politei](https://twitter.com/decredproject/status/1052203697986363392), wydanie [wersji 1.3.0](https://twitter.com/decredproject/status/1044693349205200896)), a także [przebudowa](https://github.com/decred/dcrdesign/issues/27) animowanych nagłówków podstron decred.org.

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

Staking: 30-dniowa średnia cena biletu wynosiła 103 DCR (+0) zgodnie z danymi z dcrstats.com. Cena wahała się od 101 DCR do 107 DCR. Zablokowana kwota wynosiła 4,14-4,23 miliona DCR, co odpowiadało 46,3-47,1% dostępnej podaży.

Węzły: od 1 stycznia istniało 192 publicznych węzłów nasłuchujących i 253 normalnych za [dcred.eu](https://dcred.eu/nodeStats). Dystrybucja wersji: 1,5% to v1.5.0 (pre) dev buildy, 1.8% było na v1.4.0 (rc1), 5.3% na v1.4.0 (pre) (-1.2%), 55% na v1.3.0 (+ 5% ), 20% na v1.0.0 (-5%), 10% na v1.1.2 (-1%), 4% na v1.0 (-1%).

Istnieje wiele innych [interesujących statystyk](https://github.com/xaur/decred-news/issues/41), które chcielibyśmy zaprezentować w tej sekcji; daj nam znać, jeśli możesz nam w tym pomóc.

W grudniu wydobyto blok nr. 300,000 a wykopane DCR liczą już ponad 9 milionów. Gratulacje dla wszystkich!

## Wydobycie

Whatsminer D1:

* recenzja urządzenia została opublikowana [w języku chińskim](https://www.cybtc.com/forum.php?mod=viewthread&tid=41377&fromuid=6) ([tłumaczenie Google](https://translate.google.com/translate?sl=auto&tl=en&hl=en&u=https%3A%2F%2Fwww.cybtc.com%2Fforum.php%3Fmod%3Dviewthread%26tid%3D41377%26fromuid%3D6))
* Luxor opublikował [przewodnik do konfiguracji](https://medium.com/luxor/whatsminer-d1-decred-setup-guide-182eeccaed99)
* Whatsminer.net [ogłosił](https://twitter.com/whatsminer/status/1075810531838091265), że wysłał wszystkie zamówienia z pierwszej partii

Koparka Bitmain Antminer DR5 została [ogłoszona](https://twitter.com/Antminer_main/status/1072435004142182400) na Twitterze i spotkała się z pewną krytyką. Jej [specyfikacja to](https://www.asicminervalue.com/miners/bitmain/antminer-dr5-34th): 34 Th/s przy 1800 W, ceny zaczynają się [od 1400 dolarów](https://www.asicminervalue.com/miners/bitmain/antminer-dr5-34th). Ponadto, [ten](https://www.reddit.com/r/decred/comments/a9iqbl/got_voted_to_0_in_rcryptocurrency_maybe_ill_get/) wątek omawia urządzenie wraz z wyzwaniami dla kopiących na małą skalę lub hobbystów.

Zachowaj ostrożność przy zamawianiu górników z serwisu eBay, ponieważ możesz otrzymać [jedynie odważnik](https://matrix.to/#/!NNzHoaSdnsbZDQOXJr:decred.org/$154491308943809bYuYs:decred.org).

## Integracje

Produkująca portfwele sprzętowe firma Ledger, ogłosiła, że ​​długo oczekiwana integracja DCR została ukończona:

> Z przyjemnością ogłaszamy, że Ledger Nano S i Ledger Blue są teraz kompatybilne z Decred. Decred jest teraz dostępny w usłudze Ledger Live i stanowi pierwszą natywną integrację w Ledger Live od momentu jego uruchomienia. Więcej dowiesz się [tutaj](https://www.ledger.fr/2018/12/11/ledger-nano-s-ledger-blue-and-ledger-live-now-support-decred-transactions/) ([@ LedgerHQ](https://twitter.com/LedgerHQ/status/1072446149863329792))

Przechowywanie DCR jest dostępne za pośrednictwem Ledger Live, aplikacji, która działa teraz jako pojedynczy, wszechstronny punkt dostępu i interakcji z Twoimi zasobami krypto, ponieważ na początku bieżącego roku Ledger zaprzestał wykorzystywania osobnych aplikacji do poszczególnych projektów.

Cobo Wallet [ogłosił](https://twitter.com/cobo_wallet/status/1070805250376900609) powierniczą usługę stakingową. Dyskusja na jej temat znajduje się [tutaj](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$154413818735775gNTIq:decred.org).

W przypadku każdego portfela, sprzętowego, czy programowego zawsze sam badaj sprawę i pytaj, jak to działa. Czy to Ty kontrolujesz klucze? Czy przy korzystaniu z portfela tracisz prawa do głosowania nad zasadami konsensusu oraz na Politei? Czy portfel komunikuje się z pełnymi węzłami Decred bezpośrednio lub przez pośredników? Czy usługa udostępnia Twoje dane stronom trzecim? Czy kod źródłowy jest otwarty i możliwy do skontrolowania?

## Nawiązywanie kontaktów

> Grudzień był ekscytującym miesiącem dla Decred, ponieważ zespół Ditto rozpoczął pracę. Pierwszą inicjatywą było wprowadzenie i określenie przepływu pracy. Naszych dobrych przyjaciół, Liz Bagot (@liz\_bagot), Treya Ditto (@treydpr), Margaret Mei (@margaret\_mei), Blaina Rethmeiera (@blainr) i Milvian Preito (@milvian) znajdziesz od teraz na różnych kanałach Matrix, w tym #marketing, #ditto\_pr i #writers\_room.
>
> Rozpoczęły się poważne prace nad przekazem, które można zobaczyć [tutaj](https://docs.google.com/document/d/1BCah1EKLHpwgkvVcWRWJTRC68iWeGPdbGSrhEw35XhU/edit). Dalsze sugestie są bardzo mile widziane. Równolegle pracujemy z zespołem projektowym nad integracją nowego przekazu z naszą stroną i poszerzaniem jej zawartości o nowe strony, które wyjaśniają ważne aspekty Decred.
>
> Kwestia przekazu powinna zostać uzgodniona w styczniu, a nad stroną rozpocznie się praca. Plan obejmujący wydarzenia i strategię również zostanie opublikowany w styczniu. (@Dustorf)

Zespół Ditto dołączył do kanału #marketing, na którym kipiało od pracy przez cały miesiąc przez ciągłe burze mózgów i dyskusje na temat przekazu.

@Dustorf, @jy-p i Ditto spotkali się w Nowym Jorku i opublikowali raport ze spotkania [na czacie](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154413732235771XIVBH:decred.org). Przedyskutowali, między innymi, wyzwania związane z przyciąganiem do projektu nowych programistów i współpracowników, rozpowszechnianie informacji o Decred wśród dobrze poinformowanych inwestorów, instytucji i rządów, a także przeanalizowali długoterminową wizję projektu.

Trey z Ditto [opublikował](https://medium.com/decred/decred-and-ditto-in-2019-c9063a6bca06) szerszą perspektywę na rok 2019 i strategię dla Decred. W następnej kolejności na Reddit przeprowadzono [ankietę](https://www.reddit.com/r/decred/comments/a7cul1/decred_and_ditto_in_2019_share_your_ideas/), pytając społeczność, jak opisałaby Decred, jakie media czytają i w jaki sposób uważąją, że Decred powinien ukierunkować się na programistów.

W połowie grudnia @liz_bagot opublikowała inauguracyjny [dwutygodniowy update](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154482468943386bBAIp:decred.org) od Ditto, a następnie podsumowała zadania na grudzień:

* Odbyliśmy 2,5-godzinną sesję wdrożeniową z Dustinem i Jake'iem w naszym biurze na Brooklynie na początku grudnia.
* Stworzyliśmy fundamentalną platformę komunikacyjną zawierającą analizę  publiczności Decred, sekcję "na temat", deklarację misji, deklarację wizji i instrukcje dotyczące pozycjonowania dla każdej wyjątkowej publiczności. [Przekazaliśmy](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154524074346294yVYFR:decred.org) platformę przekazu społeczności Decred w celu uzyskania opinii i zamierzamy dokonać kolejnej iteracji dokumentu, który uwzględniać będzie feedback, w styczniu.
* Wzięliśmy udział w oraz wysłaliśmy reporterów z Breaker Mag, Forbes i Fortune na spotkanie Decred w Nowym Jorku.
* Rozplanowaliśmy wywiady między paroma dużymi portalami i członkami społeczności Decred. Nie ma jeszcze dat publikacji.
* Rozpropagowaliśmy komentarz Jake'a odnośnie prognoz na rok 2019 wśród reporterów z branży krypto i uzyskaliśmy relacje w [NullTX](https://nulltx.com/decred-co-founder-pronounces-2018-as-the-death-of-the-ico-model/), [Crypto Briefing](https://cryptobriefing.com/crypto-2019-institutional-adoption/), [The Daily Hodl](https://dailyhodl.com/2018/12/21/after-bitcoin-rallies-18-industry-insiders-weigh-in-on-a-bull-run-and-cryptos-next-turn/) i [CCN](https://www.ccn.com/2018-in-4-words-icos-and-ethereum-are-dead/).

Teraz w sumie 5 znanych członków społeczności ma prawo do tweetowania za pośrednictwem konta Twitter @decredproject. O tym, jak to działa, możesz przeczytać [tutaj](https://medium.com/@richardred/working-for-the-decred-dae-a9cfb17686fa#bd70).

## Eventy

Decred zorganizował pierwsze spotkanie w Nowym Jorku 5. grudnia w Distributed Global w dzielnicy Flatiron. Wśród około 80 osób znalazły się spółki VC, deweloperzy z innych projektów, media i członkowie społeczności Decred. @jy-p przedstawił poglądową prezentację ([zdjęcie](https://twitter.com/CryptoLeslie/status/1070769160878219266)), a następnie zagłębił się w szczegóły techniczne systemu propozycji Politeia, w tym sposób jego działania i potencjalną szeroką gamę jego zastosowań.

Następnie Chris Dannen, założyciel Iterative Capital, omówił sposób, w jaki rozwinęła się praca, szczególnie w dobie darmowego oprogramowania typu open source. [Teza](https://iterative.capital/thesis/) Iterative Capital wyjaśnia ten wątek znacznie bardziej szczegółowo. Chris wyjaśnił, w jaki sposób skarbiec Decred znakomicie wpisuje się w ogromny trend pracy, który zapewnia pracownikom pożądaną niezależność i pozwala im wykonywać najlepszą pracę.

Na koniec Chris Burniske i Joel Monegro z Placeholder VC zorganizowali pogawędkę wyjaśniającą wartość Decred z perspektywy inwestora instytucjonalnego. Chris podzielił się finansowym uzasadnieniem, mówiąc o:

1. Ekipie - btcsuite po wydaniu było tak dobry, jak cokolwiek wypuszczone przez Bitcoin Core
2. Hybrydowym systemie PoW/PoS, ktory jest bezpieczniejszy niż jakakolwiek inna sieć
3. Finansowaniu ze Skarbca, które pozwala na długoterminowe finansowanie rozwoju
4. Odporności na rozszczepienie sieci - Decred ma na celu utrzymanie społeczności poprzez konsensus

Joel podzielił się swoim uznaniem dla systememu zarządzania Decred i jego zdolności do uczyenienia Decred polimorficznym, dodającym funkcje i funkcjonalności, wraz z tym jak zapragnie tego społeczność. Doszli do wniosku, że Decred jest zbudowany/zaprojektowany w sposob umożliwiający funkcjonowanie przez wiele dekad. Podzielili się przykładami dobrej pracy, którą wykonują w imieniu Decred w odniesieniu do powiernictwa, giełd wymian, instytucjonalnego stakingu, i doszli do wniosku, że największym problemem, z którym obecnie mierzy się Decred, jest płynność.

Noc Założycieli odbyła się następnego dnia 6 grudnia i była imprezą świąteczną Distributed Global. Sprowadzili oni wszystkich swoich menedżerów funduszy z różnych biur i zaprosili swoich inwestorów, partnerów i członków różnych projektów, które znajduja sie w ich portfolio. Była to świetna okazja, aby spotkać się z przedstawicielami różnych okręgów i zbudować relacje na przyszłe wydarzenia w Nowym Jorku. Następne wydarzenie Decred w Nowym Jorku planowane jest na wiosnę.

Inne wydarzenia, w których wzięliśmy udział:

* Prezentacja na Uniwersytecie Technologicznym w Amozoc w Meksyku. @elian rozmawiał z uczniami o umiejętnościach przydatnych na przyszłość i [stwierdził](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15466174667748MPUAY:decred.org): "W ramach mojego doświadczenia wspomniałem o Decred jako innowacyjnym projekcie, w którym umiejętności cyfrowe stają się niezbędnymi narzędziami współpracy. Nie był to zwyczajny krypto meetup, ale raczej przemowa motywacyjna dla studentów studiów licencjackich, aby popchnąć ich do zdobycia umiejętności cyfrowych; to mały uniwersytet znajdujący się daleko poza dużymi miastami, więc taki rodzaj treści jest bardzo doceniany. W ramach mojego doświadczenia w branży technologicznej i cyfrowej podzieliłem się z nimi swoim doświadczeniem pracując w projekcie typu open source, takim jak Decred, jako przykład możliwości, które pojawiają się w branży internetowej. Wydaje mi się, że ciekawe było, gdy uświadomili sobie, że w Internecie istnieje ogromna gospodarka z nieskończonymi możliwościami. ([zdjęcie](https://twitter.com/Decred_MX/status/1071230180398641154))

* [Wprowadzenie do Decred](https://cryptocanucks.com/events/an-introduction-to-decred-toronto/) w Toronto w Kanadzie. @michae2xl i @zubairzia0 byli gospodarzami wydarzenia i [zauważyli](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15464604416182ZLeNH:decred.org), że pomimo niewielkiej frekwencji ludzie chcieli nawiązać kontakt z lokalną społecznością Decred i byli podekscytowani, żeby pomóc zorganizować kolejne wydarzenie. ([zdjęcie](https://twitter.com/Decred_CA/status/1079191530362101760))

Nadchodzące:

* [OKEx Taiwan MeetUp](https://www.eventbrite.hk/e/okex-global-meetup-tour-2019-taiwan-tickets-54689867867) w Taipei, Tajwan, 17 stycznia. Pierwsza połowa będzie złożona z wprowadzenia do 3 projektów (Decred, EOS i NEM, 20 min każda), druga zaś będzie panelem omawiającym głosowanie on-chain (30 minut). Z ramienia Decred przedstawiac będzie @morphymore.
* [Binance Blockchain Week](https://www.binancefair.com/) w Singapurze w dniach 21-22 stycznia. Uczestniczyć i reprezentować Decred będzie @guang.
* [10 lat Bitcoina](https://10latbitcoina.com.pl/) w Warszawie, Polska, 26 stycznia. @Karamble przedstawi prezentację na konferencji z okazji 10-lecia istnienia Bitcoin i samego Bitcoina. Szczegóły dotyczące prezentacji zostaną ogłoszone wkrótce.
* [TabConf](https://tabconf.com/) w Atlancie w USA w dniach 8-10 lutego. @moo31337 zaprezentuje "Decred 101: Wprowadzenie do Decred" 9. lutego.
* [North American Bitcoin Conference](https://btcmiami.com/) w Miami, USA, w dniach 16-18 stycznia. @jy-p zaprezentuje Politeię i wejdzie na temat wielu możliwych zastosowań i aplikacji, które mogą z niej skorzystać. Proszę o wiadomość do @Dustorf, jeśli chcesz pomóc przy konferencji.
* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) w Sao Paulo, Brazylia, 12-17 lutego. Decred będzie miał prelegentów i wydzielony obszar dla hackathonów.
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) w Guadalajara w Meksyku w dniach 22-26 kwietnia. Decred będzie miał stoisko. @elian zaprezentuje przegląd Decred z sesją pytań i odpowiedzi, a także omówi, jak korzystać z oprogramowania i głosować. Skontaktuj się z @elian, jeśli chcesz pomóc/uczestniczyć.

Jeśli masz jakieś pytania, zajrzyj do pokoju [#event_planning](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org).

## Media

Wybrane artykuły:

* Koparki Bitcoinów milkną wraz z tym, jak spada cena ([cryptobriefing.com](https://cryptobriefing.com/bitcoin-miners-silent-price-falls/), również [w jęz. chińskim](https://www.jinse.com/bitcoin/288904.html))
* Szczegółowa analiza odporności na rozszczepienie łańcucha sieci Decred, aut. @Haon ([medium](https://medium.com/decred/detailed-analysis-of-decred-fork-resistance-93022e0bcde7))
* Decred i Ditto w roku 2019, aut. Trey Ditto ([medium](https://medium.com/decred/decred-and-ditto-in-2019-c9063a6bca06), dyskusja i ankieta społecznościowa są [tutaj](https://www.reddit.com/r/decred/comments/a7cul1/decred_and_ditto_in_2019_share_your_ideas/))
* Wybór fundamentalny: Decred, aut. BBOD Research ([blog.bbod.io](https://blog.bbod.io/decred-dcr-fundamental-analysis/), również [w jęz. chińskim](https://www.weibo.com/ttarticle/p/show?id=2309404313596447316959) i [japońskim](https://cointyo.jp/article/10005567))
* Współzałożyciel Decred ogłasza 2018 rokiem "Śmierci modelu ICO" ([nulltx.com](https://nulltx.com/decred-co-founder-pronounces-2018-as-the-death-of-the-ico-model/))
* 2018 w 4 słowach - ICO, oraz Ethereum umarły ([ccn.com](https://www.ccn.com/2018-in-4-words-icos-and-ethereum-are-dead/))
* Praktyczny cypherpunk: Marco Peereboom z projektu Decred ([coinrivet.com](https://coinrivet.com/the-practical-cypherpunk-marco-peereboom-of-decred/))
* Decred: Zarządzanie i finansowanie w nowej odsłonie ([51pct.io](https://51pct.io/decred-governance-and-funding-reimagined/))
* Praca dla Zdecentralizowanej Jednostki Autonomicznej Decred, aut. @richardred ([medium](https://medium.com/@richardred/working-for-the-decred-dae-a9cfb17686fa))

Tłumaczenia:

* Decred Journal - Listopad 2018 [w jęz. hiszpanskim](https://medium.com/@decred_es/revista-decred-noviembre-2018-a3e52c5fc1a9), aut. @elian, [w jęz. polskim](https://github.com/artikozel/DecredJournalPL/blob/master/journal/201811_DecredJournalPL.md), aut. @kozel, oraz [w jęz. rosyjskim](https://medium.com/decred-russia/decred-journal-%D0%BD%D0%BE%D1%8F%D0%B1%D1%80%D1%8C-2018-d0aceacfd72a), aut. @DZ, i [w jęz. chińskim](https://medium.com/@guang.dcr/decred%E6%9C%88%E6%8A%A5-11%E6%9C%88-1ddac6598830), aut. @guang. Wydanie listopadowe było do tej pory największym (59 KiB), dziękujemy wszystkim za epicki wysiłek włożony w tłumaczenia!
* Wszystkie tłumaczenia Decred Journal są podpięte na jego [stronie domowej](https://xaur.github.io/decred-news/)
* [Szczegółowa analiza odporności na rozszczepienie łańcucha sieci Decred](https://medium.com/decred/detailed-analysis-of-decred-fork-resistance-93022e0bcde7), aut. @Haon - [w jęz. polskim](https://github.com/artikozel/decred-articles/blob/master/Polish/into-polish/decredforkresistance.md), aut. @kozel
* [Jak zostać zatrudnionym jako wykonawca Decred](https://medium.com/decred/how-to-get-hired-as-a-decred-contractor-e1435842df10), aut. @Haon - [w jęz. chińskim](https://www.weibo.com/ttarticle/p/show?id=2309404315589245067163), aut. @guang

Materiały wideo:

* Do protokołu z udz. Murada Mahmudova - Bitcoin na rok 2019 w Tone Vays show ([youtube](https://www.youtube.com/watch?v=pjXzrAOhAPo), opis i wyjaśnienie projektu Decred w okolicach 1h nagrania)

Audio:

* Free Talk Live 2018-10-27 wywiad z  Marco Peereboom z Decred na Texas Bitcoin Conference ([soundcloud](https://soundcloud.com/freetalklive/free-talk-live-2018-10-27#t=40:50), _przegapione w wydaniu październikowym_)
* Unchained odcinek 100, byli goście i słuchacze przejmują program ([unchainedpodcast.co](http://unchainedpodcast.co/100th-episode-past-guests-and-listeners-take-over-the-show-ep100), @joshuam od 55:12)
* Odcinek 18: Murad Mahmudov o Bitcoinie ([didyouknowcrypto.com](http://didyouknowcrypto.com/episode-18-murad-on-bitcoin/)). Poruszone tematy to utopianizm,  Topics covered are utopianism, ekonomia austriacka, nadchodząca recesja, przyszłość Bitcoina, i fakt, że Decred powinien znajdowac się w top 3 kryptowalut.

## Dyskusje społeczności

Statystyki społeczności na dzień 1. stycznia:

* Obserwujący na Twitterze: 39,884 (-120)
* Subskrybenci na Reddit: 9,241 (+110)
* Użytkownicy na Matrixie: 221 (+18)
* Użytkownicy na Slacku: 6419 (+66)
* Użytkownicy na Telegramie: 4734 (+92)
* Subskrybenci na YouTube: 3738 (+2)
* Obserwujący na Facebooku: 3121 (+16), polubień: 2880 (+13)
* Obserwujący na LinkedIn: strona Decred 450 (+17), strona Politeia 24 (+4)
* GitHub: 458 (+11) gwiazdek i 1192 (+33) forków repozytorium dcrd

Ponadto, nowe społeczności na Telegramie powstały w jęz. chińskim (661, +119), portugalskim (435, +99) i włoskim (120). W dodatku, @michae2xl zarządza kontem @decredproject na Instagramie z 396 obserwującymi na dzień 6. stycznia.

Wiadomości z platform komunikacyjnych:

* @dhill zestrzelił [buga](https://github.com/42wim/matterbridge/pull/644) w serwisie materbridge, który blokował przekazywanie wiadomości ze Slacka na inne platformy. Prosimy zgłaszać wszelkie zauważone problemy z mostkiem.
* Kanał #smart\_contracts został zarchiwizowany z powodu braku aktywności.
* Platforma Rocket.Chat zostaje [wycofana z użytku](https://github.com/decred/dcrweb/pull/460).

Założono prototypowy [tracker pomysłów/problemów społeczności](https://github.com/xaur/decred-issues) by zapoczątkować dyskusję na temat możliwych do zrealizowania pomysłów w bardziej ustrukturyzowanym formacie. Każdy pomysł, który przyniesie korzyści projektowi, może zostać omówiony. Od 10 stycznia istnieją [73 wpisy](https://github.com/xaur/decred-issues/issues) odnośnie [pomysłów na artykuły](https://github.com/xaur/decred-issues/labels/article ), [PR](https://github.com/xaur/decred-issues/labels/PR), [archiwizacji](https://github.com/xaur/decred-issues/labels/archiving) i ochrony danych lub omówienia [platform komunikacyjnych](https://github.com/xaur/decred-issues/labels/comms). Na przykład, [ten problem](https://github.com/xaur/decred-issues/issues/54) rejestruje trudne zadanie znalezienia dobrej nazwy dla hybrydowego algorytmu konsensusu PoW/PoS i zawiera listę wszystkich sugerowanych do tej pory opcji. Możesz zasubskrybować wszystko za pomocą przycisku "obserwuj" na górze lub poszczególne wpisy za pomocą przycisku "subskrybuj" na prawym panelu. Istnieje powszechne przekonanie, że "GitHub jest dla programistów" - tak nie jest. Publikowanie problemów i komentarzy oraz "+1" nie jest trudniejsze niż korzystanie z Reddit lub czatu, a tak naprawdę współtwórców niebędących programistami pomaga robiąc właśnie to.

Incydent na Reddit pokazał nam kolejną słabość platformy. Rozpoczęto wiele wątków, co zachęciło do dyskusji, lecz później zostały one usunięte przez autora. To zmarnowało wysiłek wszystkich ludzi, którzy zadali sobie trud, żeby napisać odpowiedź. Usunięte wątki zostały w pewnym stopniu [wskrzeszone](https://www.reddit.com/r/decred/comments/a6ywpj/deleted_threads_with_valuable_discussion/), ale generalnie ten incydent ukazał nowy wektor ataku/sabotażu: wywołaj dyskusję, a następnie usuń wątek marnując energię społeczności. Reddit nie ma przed tym żadnej obrony, ponieważ moderatorzy nie mogą zabronić użytkownikom usuwania swoich treści. Wydarzenie doprowadziło do dyskusji na temat [zastąpienia Reddit czymś innym](https://github.com/xaur/decred-issues/issues/38), co prawdopodobnie mogłoby wywodzić się z Politei.

Po raz kolejny, na Reddit miało miejsce wiele dziwnych wydarzeń blisko daty kolejnego głównego wydania oprogramowania. Jest to albo niezwykła ilość pytań o mniej istotne sprawy, albo "niewinne" pytania na temat drobiazgów lub czegoś podobnego. Aktywność ta pochodzi z kont nigdy wcześniej niewidzianych i niepozostających na subreddicie po tej krótkiej interakcji. Niniejsze zawiadomienie ma na celu poinformowanie ludzi, którzy mają na sercu dobro projektu, aby zwracali uwagę na dziwną aktywność, która może wysysać energię zarówno pojedynczych użytkowników, jak i całego projektu. Przeczytaj [ten czat](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$154531182347084ccYxu:decred.org), aby dowiedzieć się więcej.

## Rynki

W grudniu DCR kursowało w przedziale 14,2-21,4 USD / BTC 0,0042-0,0058. Średnia dzienna stawka wynosiła 17,5 USD. Krótki wzrost cen do 20,9 USD / BTC 0,0058 nastąpił na wolumenie zwiększonym do 5-6 mln USD w porównaniu do 0,8-1,2 mln USD w pozostałe dni. Pragniemy zauwazyć, że dane dotyczące wolumenu obrotu nie są wiarygodne, jak podano poniżej.

## Ważne kwestie i wiadomości poboczne

Vertcoin (VTC) był przedmiotem [ataku większości (51%)](https://medium.com/coinmonks/vertcoin-vtc-is-current-being-51-attacked-53ab633c08a4) (4 incydenty), w trakcie którego miały miejsca 22 reorganizacje i 15 podwójnych wydatków, co kosztowało ofiary około 100 000 USD. Potwierdza to wrażliwość monet, które nie są stanowią głównego zainteresowania górników (wydobywalnych na GPU lub odpornych na ASIC, ale także forki Bitcoina), na atak przez górników, którzy mają odpowiedni sprzęt i nie mają na uwadze zdrowia danego blockchaina. Jednym z efektów tych ataków jest to, że moneta zyskuje miano niepewnej, ponieważ wcześniej zawiodła w swoim zadaniu i każdy, kto nadal chce ją zaakceptować, może wymagać bardzo dużej liczby potwierdzeń przed zaksięgowaniej transferu, co sprawia, że ​​moneta wolniej się porusza.

Niedawno zespół [Horizen](https://www.horizen.global/) (wcześniej ZenCash) ogłosił [działanie strategiczne](https://blog.zencash.com/re-stategic-actions-for-horizen-from-rolf-versluis/) w celu zwiększenia nagród z bloku dla Skarbca z 10% do 20%, zmniejszając tym samym pulę do podziału między górników. Po spadku ceny o 90% i znacznym obniżeniu kosztów personelu i innych, uznano, że dalsze obniżanie kosztów oznaczałoby zagrożenie dla projektu. W związku z tym, że opracowany przez IOHK system skarbca nadal jest [prototypem](https://blog.zencash.com/dao-prototype/), który nie jest jeszcze gotowy do użycia, zespół Horizen uznał, że należy podjąć jednostronną decyzję o zmianie nagrody za wydobycie bloku

Producenci bloków EOS [zaczął płacić](https://cointelegraph.com/news/eos-node-offers-users-financial-rewards-for-votes-reignites-decentralization-debate) posiadaczom, którzy na niego głosowali.

Pierwsza runda głosowania nad propozycjami zarządzania Aragon (AGP) została [opóźniona](https://forum.aragon.org/t/agp-vote-delay-announcement/426) z powodu potencjalnej niestabilności spowodowanej forkiem Ethereum - Constantinople - mamy nadzieję, że "blockchain wyłączony z użycia na czas prac konserwacyjnych" nie będzie czymś, z czym Decred spotka się w ramach platformy Politeia. CEO Stowarzyszenia Aragon [opublikował](https://forum.aragon.org/t/agp-wishlist-andblacklist/355) czarną listę i listę życzeń do składania wniosków przed otwarciem zgłoszeń propozycji. W pierwszym wniosku sam [proces AGP](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-1.md) został [zatwierdzony](https://blog.aragon.org/final-results-from-the-agp-1-vote/) przez 99,97% ANT, które głosowało. Łącznie 2,6% wszystkich żetonów ANT z 45 unikalnych adresów głosowało nad pierwszą propozycją, gdzie ~ 60% głosów ANT pochodziło z jednego adresu. AGP poddane są przeglądowi przez zarząd Stowarzyszenia Aragon, następnie przez społeczność, przed tym, jak otwarty zostaje 48-godzinnym okres głosowania.

2 miliony BTCP zostały wydobywane przez exploit i pozostały niezauważone przez wiele miesięcy, dopóki CoinMetrics [zauważyło](https://coinmetrics.io/bitcoin-private), że coś jest nie tak z podażą. Zespół deweloperów [opublikował](https://medium.com/@bitcoinprivate/official-statement-on-coinmetrics-report-6f1cef176c05) oficjalne oświadczenie potwierdzające exploit w inflacji monety. Błąd został scalony 5. stycznia 2018 wraz z patchem łowcy bugow, który zniknął po otrzymaniu nagrody za swoją pracę. Tylko jedna brakująca linijka kodu spowodowała ogromne szkody dla propozycji wartości sieci. Możemy się wiele nauczyć z tego niefortunnego doświadczenia: obszerny zasięg testów, niesamowicie krytyczna recenzja kodu konsensusu, uznana reputacja programistów pracujących nad częściami o znaczeniu krytycznym oraz posiadanie wielu implementacji protokołu są bardzo ważne dla zbudowania systemu, któremu możemy powierzyć pieniądze.

Miał miejsce [atak](https://www.reddit.com/r/CryptoCurrency/comments/a9yji3/electrum_wallet_hacked_200_btc_stolen_so_far/) na infrastrukturę Electrum Bitcoina. Ktoś uruchomił wiele złośliwych serwerów Electrum, które skłaniały użytkownika do "aktualizacji" oprogramowania do złośliwej wersji i skradły ponad 200 BTC. Model Electrum obejmuje sieć serwerów, które znajdują się pomiędzy klientami i pełnymi węzłami. Każdy klient jest uzależniony od serwera, z którym się łączy, co narusza prywatność użytkownika, ponieważ właściciele tych serwerów mogą określić, które portfele są własnością użytkowników. Jeśli serwery Electrum zostałyby naruszone, otworzyłoby to sieć na dodatkowe ataki. Decred zdecydował się nie rozwijać infrastruktury Electrum, ale zamiast tego idzie prosto do SPV w oparciu o filtry po stronie klienta. Opóźniło to rozwój lekkich klientów, ale tryb SPV działający obecnie w dcrwallet, Decrediton i Drcandroid łączy się bezpośrednio z pełnymi węzłami i działa niezależnie od dowolnego dostawcy usług, co w rezultacie zwiększa prywatność użytkowników.

Badacze bezpieczeństwa [demonstrowali](https://media.ccc.de/v/35c3-9563-wallet_fail) wiele sposobów na zhackowanie najpopularniejszych portfeli sprzętowych, jeśli są w fizycznym posiadaniu urządzenia.

Raport o obrotach giełdowych autorstwa [blockchaintransparency.org](https://www.blockchaintransparency.org/) stwierdził, że dla najwyżej notowanych 25 par BTC ponad 80% wolumenu z coinmarketcap.com jest zmanipulowane. Kolejnym niefortunnym odkryciem jest to, że statystyczny projekt wydał ponad 50 000 USD na opłaty za umieszczenie na giełdach wymian. Raport pobudził [pomysł](https://github.com/xaur/decred-issues/issues/34) analizy obrotów handlowych dla DCR.

Coinbase [próbuje](https://www.coindesk.com/coinbase-wants-to-own-buidl-trademark-filing-reveals), nabyć prawa do terminu "BUIDL".

Wiele usług i projektów kryptowalutowych zdaje się, w całości lub cześciowo, [być w kieszeni](https://twitter.com/tangleblog/status/1068094875533479937) jedynie garstki ludzi czy organizacji, na szczycie których figurują banki.

Kilku scentralizowanym giełdom [nie udało](https://www.ccn.com/several-exchanges-said-to-be-failing-bitcoin-ownership-event/) się realizować wypłat w ciągu corocznego wydarzenia pt. ["dowód kluczy](https://www.proofofkeys.com/).

Slack przypadkowo [zablokował](https://www.engadget.com/2018/12/22/iran-sanctions-slack/) osoby, które wcześniej odwiedzały Iran. Później Slack [przeprosił](https://slackhq.com/an-apology-and-an-update) za incydent i wyjaśnił sytuację. Sygnał jest jednak jasny i nie jest zaskakujący: Slack Technologies jest spółką amerykańską ([finansowaną przez venture capital](https://en.wikipedia.org/wiki/Slack_Technologies), która jest zgodna z amerykańskimi przepisami. W przecwieństwie do Slacka, pokoje Matrix mogą być stowarzyszone na wielu serwerach, więc nawet jeśli niektóre serwery uczestniczące są wyłączone, serwery w innych jurysdykcjach mogą nadal obsługiwać czat i historię.

W grudniu powstało wiele [artykułów](https://www.wsj.com/articles/layoffs-become-the-latest-thing-in-cryptocurrency-1544471449) [na](https://www.newsbtc.com/2019/01/09/cryptocurrency-shapeshift-layoffs/) [temat](https://www.businessinsider.com/bitmain-layoffs-2018-12) zwolnień w przestrzeni kryptowalut (a niektórzy mówią, że to wcale [nie tak źle](https://cointelegraph.com/news/better-than-corporations-layoffs-in-crypto-are-on-the-rise-still-lower-than-in-other-industries) w porównaniu do innych sektorów). W przypadku innych projektów ze skarbcami, są to również ciężkie czasy, jak wspomniano powyżej w przypadku Horizen i jak można zobaczyć w niektórych [dyskusjach społecznościowych](https://www.reddit.com/r/dashpay/comments/ac9ca4/dash_nigeria_defunding_statement_and_path_forward/) w Dash. Możemy podziękować osobom, które zarządzały Skarbcem w epoce przed Politeią za utrzymanie zdrowej rownowagi; to dlatego Decred wciąż dąży do powiększenia swoich mocy przerobowych, podczas gdy inne projekty kurczą się. Przy DCR na poziomie 17,5 USD w grudniu, będzie to prawdopodobnie pierwszy miesiąc, w którym wypłaty ze Skarbca przekroczą wpływające do niego środki z wydobycia bloków. Nawet jeśli DCR/USD przez jakiś czas pozostanie na niskim poziomie, Skarbiec może utrzymać obecne wydatki na poziomie równoważnika w USD przez kilka lat (szacunkowa wartość szacunkowa to 8) przy obecnym tempie, zanim konieczne będą cięcia.

Wśród większej fali zwolnień w sferze krypto, Bitmain [rzekomo](https://cointelegraph.com/news/reports-bitmain-allegedly-fires-all-bch-developers-in-wave-fundedundions) zwolnił cały personel deweloperów Bitcoin Cash, co objęło zespół Copernicus.

[Copernicus](https://github.com/copernet/copernicus) to implementacja protokołu Bitcoin Cash napisanego w Go, która wykorzystuje btcsuite. Wersja przedpremierowa oprogramowania została [ogłoszona](https://news.bitcoin.com/an-alternative-client-has-mined-bitcoin-cash-block-558847/) i wydobyła swój pierwszy blok w grudniu. Na ich stronie autorzy [dziękują](https://www.copernicuscore.org/btcd.html) programistom btcsuite za pracę i uznają ich wkład w ekosystem Bitcoin. Na blogu zespół Copernicus [zauważył](https://medium.com/@copernicusbit/the-copernicus-project-launched-tre-release-v0-0-6-dc572a924214), że oprogramowanie "reorganizuje i przeprojektowuje strukturę oprogramowania dla oryginalnego klienta, aby struktura była bardziej zwięzła, obniżyć próg trudności w nauce dla programistów i zwiększyć różnorodność klientów, aby zapewnić bezpieczeństwo całej sieci BCH".

Copernicus nie jest pierwszą próbą dywersyfikacji sieci Bitcoin Cash, która miała już w rozwoju kilka implementacji w językach C ++, Rust i JavaScript. We wrześniu odsłonięto dwie inne implementacje Bitcoin Cash [napisane w Go](https://news.bitcoin.com/developers-unveil-two-new-bitcoin-cash-full-node-clients-written-in-go/). [Gocoin-cash](https://github.com/CounterpartyXCPC/gocoin-cash) pochodzi od twórców [counterparty.cash](http://counterparty.cash/) i jest oparty na [gocoin](https://github.com/piotrnar/gocoin) (kolejnej pełnej implementacji węzła Bitcoin w Go). [bchd](https://github.com/gcash/bchd), z kolei, pochodzi od programisty OpenBazaar [Chrisa Pacii](https://github.com/cpacia). We wstępnym [ogłoszeniu](https://www.yours.org/content/introducing-bchd-aee6a07feb00) bchd Chris zauważył, że btcsuite jest "jednym z najlepiej zaprojektowanych i dobrze napisanych baz kodu Bitcoin" i wyjaśnił, że pozwala ono angażować więcej programistów i budować nowe funkcje szybciej, w porównaniu do implementacji C++. Dało im także "za darmo" prywatne SPV po stronie klienta. Wersja beta została [ogłoszona](https://medium.com/@bchd.cash/bchd-beta-release-46f89c677c47) w listopadzie - w dwa miesiące od rozwidlenia z btcd zespół powiększył się do 9 autorów i wprowadził wiele ulepszeń w stosunku do btcd.

Istotą i dobrą wiadomością dla Decred jest to, że dużo więcej programistów patrzy teraz na bazę kodu btcsuite, na której opiera się Decred i z czego może skorzystać.

## O tym wydaniu

To 9. wydanie Decred Journal. Jest on dostępny na [GitHub](https://xaur.github.io/decred-news/journal/201812). Wcześniejsze wydania i tłumaczenia są dostępne [tutaj](https://xaur.github.io/decred-news/).

Chińskie tłumaczenie aut. @guang jest dostępne na [Medium](https://medium.com/@guang.dcr/decred%E6%9C%88%E6%8A%A5-12%E6%9C%88-eb8b42a5e4fd), [Weibo](https://www.weibo.com/ttarticle/p/show?id=2309404327424178422533) oraz [GitHub](https://github.com/Guang168/DecredCNJournal/blob/master/201812_DecredJournalCN.md).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanch stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze opinie i komentarze są mile widziane na portalach [GitHub](https://github.com/xaur/decred-news/issues) oraz [Matrix](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Zasługi (w kolejności alfabetycznej): bee, Dustorf, guang, Haon, kozel, liz_bagot, oregonisaac, raedah, richardred, saender, zubairzia0.
