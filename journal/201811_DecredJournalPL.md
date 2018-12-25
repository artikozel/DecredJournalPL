# Decred Journal – Listopad 2018

![Web Summit w Lizbonie](../img/NOV18_websummit18-300.jpg "Web Summit w Lizbonie")

Listopad był ekscytującym i produktywnym miesiącem dla projektu Decred. Społeczność projektu zaczęła czerpać korzyści płynące z rozwoju platformy Politeia przez uruchomione głosowanie i pierwsze zatwierdzone projekty. Interesariusze razem podjęli kluczowe decyzje odnośnie przyszłego zarządzania wykonawcami, public relations, robiąc rozpoznanie w kwestiach poddanych pod głosowanie wygodnie, z poziomu wybranego portfela Decred (Decrediton bądź wiersza polecenia za pomocą narzędzia politeiavoter).

Do ekosystemu Decred dołączyły kolejne firmy i pojedynczy deweloperzy, podczas gdy długoterminowi współpracownicy przypisali się do istniejących projektów według ich zainteresowań i umiejętności.

Pośród ekscytacji, rozrostu i zmian w społeczności, rozwój projektu postępował dynamicznie i z wymiernymi efektami.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Dwie duże zmiany rozpoczęte w zeszłym miesiącu zostały scalone po rozległych testach. Pierwsza to [reversed UTXO set semantics](https://github.com/decred/dcrd/pull/1471) i towarzysząca jej [migracja bazy danych](https://github.com/decred/dcrd/pull/1520), ważna zmiana umożliwiająca łatwiejszą i efektywniejszą obsługę niewydanych danych wyjściowych, czego efektem ubocznym jest to, że testy reorganizacyjne pełnych bloków odbywają się o 40% szybciej. Druga to [zoptymalizowana obsługa reorganizacji](https://github.com/decred/dcrd/pull/1500). Nowy argument[--maxsameip](https://github.com/decred/dcrd/pull/1517) pozwala ograniczyć liczbę połączeń z tym samym adresem IP. Fix na ultra rzadkiego buga został [sportowany](https://github.com/decred/dcrd/pull/1533) z repozytorium btcd.

[dcrwallet](https://github.com/decred/dcrwallet): Dodano nowe RPC do [ticketbuyer v2](https://github.com/decred/dcrwallet/pull/1307), umożliwiające [kupowanie pojedynczych biletów](https://github.com/decred/dcrwallet/issues/1317) oraz [konsolidację środków z kont](https://github.com/decred/dcrwallet/pull/1098). Dodano [możliwość](https://github.com/decred/dcrwallet/pull/1282) korzystania z alternatywnych backendów baz danych, co jest użyteczne dla platform mobilnych. Naprawiono bugi: [obserwacja adresów](https://github.com/decred/dcrwallet/pull/1320) w mocno wykorzystywanych portfelach, [przeoczone bądź podwójnie wydane transakcje](https://github.com/decred/dcrwallet/pull/1321), [brakujące adresy i transakcje](https://github.com/decred/dcrwallet/issues/1333).

Rozpoczęto prace nad dużą zmianą w poprawieniu obliczania ["zablokowanego" salda](https://github.com/decred/dcrwallet/pull/1330) co powinno rozwiązać niektóre problemy dla głosujących solo, przez VSP, i z częściowymi biletami.

[Decrediton](https://github.com/decred/decrediton): Dodano funkcje: [nowa strona](https://github.com/decred/decrediton/issues/1755) do wyboru pomiędzy trybem SPV a pełnowęzłowym oraz wyświetlania [salda Skarbca](https://github.com/decred/decrediton/pull/1764). Przełączono automatyczne kupowanie biletów na [ticketbuyer v2](https://github.com/decred/decrediton/pull/1744). Ma on mniej opcji i jest łatwiejszy w obsłudze niż v1 dzięki ustabilizowanym cenom biletów. Teraz jedyne, co użytkownik musi zrobić, to ustawić saldo do utrzymania, oraz konto i VSP, z którego funkcja ma korzystać. Wydajność [dużych portfeli](https://github.com/decred/decrediton/pull/1727) przy startupie została usprawniona. Integracja Politei doczekała się ulepszeń, m.in. [bardziej responsywnego](https://github.com/decred/decrediton/pull/1825) wgrywania propozycji oraz [powiadomień o nowych propozycjach i głosowaniach](https://github.com/decred/decrediton/pull/1835). Tuning UI/UX: zaktualizowano [design listy propozycji](https://github.com/decred/decrediton/pull/1771), [ulepszenia w dizajnie](https://github.com/decred/decrediton/issues/1818), [ikonki kont](https://github.com/decred/decrediton/issues/1811) wprowadzono ulepszenia w [ikonkach nawigacyjnych i mikroanimacjach](https://github.com/decred/decrediton/issues/1809). Aby zapewnić ciągłą wieloplatformową stabilność i wydajność Decrediton został [zaktualizowany do Electron 3](https://github.com/decred/decrediton/pull/1777).

Wymienione wyżej funkcje i cechy zostały scalone z główną gałęzią i będą dostępne w następnym wydaniu portfela Decrediton.

Trezor: wersja 2.0.9 firmware'u Modelu T została [udostępniona](https://blog.trezor.io/firmware-updates-2-0-9-and-1-7-1-developed-by-the-community-for-the-community-c4b965741ca3) ze wsparciem Decred. Dzięki dla @matheusd za to, że uczynił to możliwym! Teraz nasi deweloperzy Decrediton mogą pracować nad integracją z portfelem.

Uwaga: Odkryto fałszywego Trezora One. Przeczytajcie [wpis](https://blog.trezor.io/psa-non-genuine-trezor-devices-979b64e359a7) o tym, jak zweryfikować urządzenie i gdzie szukać oryginałów.

[Politeia](https://github.com/decred/politeia): [politeiavoter](https://github.com/decred/politeia/tree/master/politeiavoter) prywatność i wydajność zostały usprawnione dzięki losowej [kolejności głosowania biletów](https://github.com/decred/politeia/issues/565), losowym [opóźnieniom pomiędzy głosom](https://github.com/decred/politeia/pull/579) oraz [filtrowaniu](https://github.com/decred/politeia/issues/562) biletów, które oddały już głos. Dzięki powszechnym prośbom stworzono system powiadomień e-mail w celu zwiększania świadomości na temat [nowych propozycji](https://github.com/decred/politeiagui/pull/848) i [komentarzy](https://github.com/decred/politeiagui/pull/919). Weryfikacja oddanych głosów umożliwiona została przez funkcję [wyszukiwania według biletu](https://github.com/decred/politeiagui/pull/899), w której wyszukiwanie odbywa się po stronie klienta celem zachowania prywatności. [Permalinki komentarzy](https://github.com/decred/politeiagui/issues/753) i [wyróżnienie komentarzy autorów](https://github.com/decred/politeiagui/issues/877) są już dostępne. Nowy [stan "porzucony"](https://github.com/decred/politeiagui/issues/889) został dodany, aby obsługiwać nieaktywne propozycje. Zakładka "zakończone" została [podzielona](https://github.com/decred/politeiagui/issues/904) na zakładki "zatwierdzone" i "odrzucone". Wsparcie SVG zostało [wyłączone](https://github.com/decred/politeia/pull/626) do momentu znalezienia sposobu oczyszczania oprzyrządowania SVG. [Drobna podatność](https://github.com/decred/politeia/issues/563) została załatana, dzięki dla @iemlisted za zgłoszenie. Poza tym, wiele różnych, mniejszych ulepszeń i bugfixów.

Niektóre z powyższych ulepszeń będą dostępne na [stronie sieci głównej](https://proposals.decred.org/) po następnym wdrożeniu.

Rozpoczęły się prace nad funkcjonalnością [wyświetlania różnic](https://github.com/decred/politeiagui/issues/754) pomiędzy korektami propozycji i   [wyszczególniania nowych komentarzy](https://github.com/decred/politeiagui/pull/897).

[Android wallet](https://github.com/decred/dcrandroid): wersja pre-release dla mainnet jest dostępna na [Google Play Store](https://play.google.com/store/apps/details?id=com.decred.dcrandroid.mainnet)! Wersja Play Store zawiera zaktualizowaną konwersję walutową, która wyświetla [opłatę w walucie lokalnej](https://github.com/decred/dcrandroid/issues/192) i [zaawansowaną ochronę haseł](https://github.com/decred/dcrandroid/issues/134) z możliwością [blokowania wszystkich danych](https://github.com/decred/dcrandroid/issues/187) i wykorzystania [kodów dostępu PIN](https://github.com/decred/dcrandroid/issues/180). Wersja ta zawiera też menu bezpieczeństwa, które daje użytkownikom możliwość [podpisywania wiadomości](https://github.com/decred/dcrandroid/issues/226) tym samym udowadniając posiadanie adresów. Kolejną innowacją zasugerowaną przez społeczność są [ukryte konta](https://github.com/decred/dcrandroid/issues/175). Ukryte konta pozwolą użytkownikom na trzymanie środków w portfelach mobilnych bez wyświetlania ich na ekranie głównym salda. Dodatkowa prywatność, którą daje ta funkcja, będzie przydatna dla ludzi kupujących i sprzedających Decred na lokalnych spotkaniach. Przesyłanie środków pomiędzy kontami zostało uproszczone przez [wybór rozwijany](https://github.com/decred/dcrandroid/issues/119).

[iOS wallet](https://github.com/raedahgroup/dcrios): portfel jest obecnie w fazie beta testów i wymagać będzie dodatkowych cykli deweloperskich do wcielenia zestawu funkcji dostępnych na Androidzie.


[dcrdata](https://github.com/decred/dcrdata): Nowe funkcje zintegrowane z bazą kodów w tym miesiącu to, m.in. [wykres hashrate'u sieci](https://github.com/decred/dcrdata/issues/723), dodanie [Skarbca Decred](https://github.com/decred/dcrdata/issues/784) do menu nawigacyjnego, pokazując, że [dane wyjściowe wydane są w mempoolu](https://github.com/decred/dcrdata/issues/825) i pokazywanie [typ transakcji przy wyświetlaniu adresu](https://github.com/decred/dcrdata/issues/741). [Ulepszono](https://github.com/decred/dcrdata/issues/776) dokładność grupowania czasowego.

Podgląd [nowej strony domowej](https://github.com/decred/dcrdata/pull/718), wraz ze wszystkimi nowymi funkcjami dostępny jest na [stronie alpha](https://alpha.dcrdata.org/nexthome), która działa na wersji v3.2.0-pre budowana z gałęzi master. Bardziej stabilna [strona beta](https://beta.dcrdata.org/) oparta jest na v3.1.0-beta. Najbardziej stabilna wersja strony [explorer.dcrdata.org](https://explorer.dcrdata.org/), zbudowana jest na v3.0.2-release. Dla spójności z linkami Insight, ta druga jest również dostępna pod adresem [mainnet.dcrdata.org](https://mainnet.dcrdata.org/).

Po stronie deweloperskiej, @gozart [rozpoczął](https://matrix.to/#/!LmKzrmxJIXNHNiEmIh:decred.org/$154214092215095eeuIR:decred.org) epicką refaktoryzację w celu [przekonwertowania](https://github.com/decred/dcrdata/pull/805) bazy kodów javascript do modułów ES6, dodania webpacka dla oprzyrządowania front end devu i pakowania zasobów produkcyjnych, egzekwowania stylu kodu oraz konwersji CSS do [partiali SCSS](https://github.com/decred/dcrdata/pull/839).

[dcrstakepool](https://github.com/decred/dcrstakepool): to oprogramowanie używane przez większośc, o ile nie wszystkich VSP. Dokument README został [zaktualizowany](https://github.com/decred/dcrstakepool/pull/285) o instrukcje budowania z modułami Go. Linki zmieniono z Insight na [dcrdata](https://github.com/decred/dcrstakepool/issues/264).

Odkryto i omówiono wiele problemów natury prywatności. Testujemy łatkę, która zastąpi recaptcha Google [CAPTCHA na własnym hostingu](https://github.com/decred/dcrstakepool/pull/281), żeby uniknąć identyfikacji interesariuszy - zachęcamy operatorów VSP do dołączenia do testów. [Usunięto](https://github.com/decred/dcrstakepool/pull/283) zapytanie do Cloudflare. Powstało też zagadnienie [uczynienia emaili nieobowiązkowymi](https://github.com/decred/dcrstakepool/issues/274).

[Ticket splitting](https://github.com/matheusd/dcr-split-ticket-matcher): wersja beta rozwijała się przez cały listopad z codziennie kupowanymi cześciowymi biletami i wypełnianymi sesjami zakupu. Dwóch operatorów VSP zintegrowało ticket splitting w swoich usługach, [decredbrasil.com](https://stake.decredbrasil.com/) i [decredvoting.com](https://decredvoting.com/), opublikowało [poradnik qudeo](https://www.youtube.com/watch?v=3RGoUQK0g24) w jęz. portugalskim i angielskim oraz generalny [opis ticket splittingu](https://www.reddit.com/r/decred/comments/9vhpby/decred_ticket_splitting_overview/), poza zamieszczonymi już na ich stronach poradnikami. Opgoramowanie zostało zaktualizowane, aby wspierać SPV light mode. Przeczytajcie [zagadnienie](https://github.com/matheusd/dcr-split-ticket-matcher/issues/29) opisujące kwestie prywatności.

Mamy grupy wsparcia ticket splittingu na [Decred Slack](https://decred.slack.com) oraz w [grupie Telegram](https://t.me/dcrticketsplit) gdzie dostępne są ogólne [instrukcje korzystania](https://t.me/dcrticketsplit/2666).

[design](https://github.com/decred/dcrdesign): @kyle z [Firethought](https://firethought.net/) ogłosił [paczkę ruchomych ikon dla Decred](https://medium.com/@firethought/base-iconset18-motion-pack-readme-a96f96e868), która obiecuje dostarczyć "bardziej wciagające doświadczenia dla aplikacji Decred" i opiera się na paczce ikon zaprojektowanych przez [EETER](http://www.eeter.co/).

[docs](https://github.com/decred/dcrdocs): Listopad był niesamowity dla dokumentacji dzięki mnogości wspartych przez społeczność zmian i aktualizacji. [Propozycja](https://proposals.decred.org/proposals/522652954ea7998f3fca95b9c4ca8907820eb785877dcf7fba92307131818c75) zmiany terminów "PoS Mining" na "PoS Voting" oraz "stakepool" na "Voting Service Provider" zostały zatwierdzone, co potwierdza chęć wprowadzenia nowej terminologii przez społeczność w całej dokumentacji Decred. Pierwsza partia zmian jest już [scalona](https://github.com/decred/dcrdocs/pull/590). Dokonano też aktualizacji, żeby [przyjąć termin "Skarbiec Decred"](https://github.com/decred/dcrdocs/pull/690). Dla tych, którzy chcą dać głębszego nura w system Politeia, stworzono nową stronę pt. [nawigowanie wśród danych Politei](https://docs.decred.org/advanced/navigating-politeia-data/). Opracowany został długo wyczekiwany [glosariusz Decred](https://github.com/decred/dcrdocs/pull/675) dzięki niesamowitemu wysiłkowi @s_ben i wielu ludzi, którzy wspierali prace swoimi sugestiami i komentarzami. Gorąco zachęcamy do korzystania z [glosariusza](https://docs.decred.org/glossary/), by ulepszać nasze grupowe zrozumienie tematu oraZ komunikację.

Statystyki aktywności deweloperskiej dla listopada: 266 aktywnych PRów, 268 master commity, 45K dodanych i 25K usuniętych linijek pomiędzy 8 repozytoriami. Wkład pochodził od 3-11 deweloperów na repozytorium. ([wykres](https://twitter.com/decredproject/status/1070413196555636736))

## Ludzie

Gorąco witamy ludzi wnoszących swój wkład do projektu po raz pierwszy: [logicminds](https://github.com/decred/dcrd/commits?author=logicminds) (dcrd, _przegapione w wydaniu październikowym_), [@itswisdomagain](https://github.com/decred/dcrdata/commits?author=itswisdomagain) (dcrdata), [rocknet](https://github.com/decred/decrediton/commits?author=rocknet) (decrediton), [@brunobraga](https://github.com/decred/politeiagui/commits?author=brunobraga95) (politeiagui).

Gratulacje dla 5 nowych wykonawców [ujętych](https://github.com/decred/dcrweb/pull/444) na decred.org: Insaf Nori (@butterfly, community manager - Środkowy Wschód), Guang (@guang, community manager - Azja), Seth Benton (@s_ben, deweloper), Youssef Boukenken (@sef, deweloper), Zubair Zia (@zubairzia0, research i strategia).

@kozel przeprowadził wywiad z Feeleepem, operatorem ugruntowanego mining poola [coinmine.pl](https://www2.coinmine.pl/), w którym [zagłębiają się w infrastrukturę Decred](https://medium.com/decred/decred-intriguing-and-extraordinary-an-interview-with-coinmine-pl-mining-pool-operator-5c5592443cb4).

> Muszę przyznać, że Decred jest chyba najbardziej stabilnym rozwiązaniem pod względem technicznym, bo to chyba jedyny daemon, który nie miał żadnych problemów ze stabilnością i synchronizacją w całej mojej historii.

Październikowe wydanie zawierało króciutką wzmiankę o nowej firmie-wykonawcy, więc nadszedl czas, by przywitać i przedstawić ich porządnie.
[Block 42](https://42block.io/) jest firmą zajmująca się rozwojem technologii blockchain z siedzibą w Mińsku na Ukrainie, która wykorzystuje blockchain do wprowadzenia jawności i poprawienia wydajności w sektorze finansowym, ubezpieczeniowym, logistycznym i zaopatrzeniowym. Ich spółka dominująca, [Grinteq](https://grinteq.com/), ma siedzibę w Nowym Jorku, USA. Zespół Block 42 to do tej pory:

* Nick Kaeshko (@Nick) - współzałożyciel, upewnia się, że wszystko sprawnie działa.
* Maria Pleshkova (@Maria) - UI/UX designer, z wkładem w [przebudowę motywu stakepoola](https://github.com/decred/dcrdesign/issues/23), czuwa nad tym, żeby był bardziej spójny z obecnym UI Decreditona. Obecnie pracuje nad [redesignem Politei](https://github.com/decred/dcrdesign/issues/77), w który wchodzą aktualizacje UI/UX oraz wdrożenie nowych funkcji.
* Dmitry Fedorov (@klka) - deweloper Golang, obecnie pracujący nad przerobieniem indeksów blockchain na [asynchroniczne](https://github.com/decred/dcrd/issues/1470) w celu przyspieszenia przetwarzania bloków.
* Wkrótce oficjalnie dołączy do nich jeszcze jedna osoba.

Witamy na pokładzie!

## Zarządzanie

Jak poinformowaliśmy wcześniej, finansowanie dla propozycji [Ditto PR services](https://proposals.decred.org/proposals/27f87171d98b7923a1bd2bee6affed929fa2d2a6e178b5c80a9971a92a5c7f50) i [Open Source Research](https://proposals.decred.org/proposals/c68bb790ba0843980bb9695de4628995e75e0d1f36c992951db49eca7b3b4bcd) otrzymały wsparcie w pierwszej połowie listopada. W połowie listopada społeczność Decred omawiała kwestie zarządzania wykonawcami i podjęła decyzję o zatwierdzeniu projektu [Decred Contractor Clearance (poświadczanie dla wykonawców Decred)](https://proposals.decred.org/proposals/fa38a3593d9a3f6cb2478a24c25114f5097c572f6dadf24c78bb521ed10992a4), czyli procesu, który ma na celu sformalizowanie najlepszych praktyk będących w użyciu przez projekty open source. [Notowanie premium](https://proposals.decred.org/proposals/34707d34b09c3ebcf0d4aa604e8a08244e8f0f082c0af3f33d85778c93c81434) na giełdzie Easyrabbit zostało odrzucone.

Nowe propozycje na dzień 6 grudnia wymienione są poniżej.

[Zmiana algorytmu wydobycia PoW na ProgPoW](https://proposals.decred.org/proposals/0aaab331075d08cb03333d5a1bef04b99a708dcbfebc8f8c94040ceb1676e684) złożona przez engineerking 11. listopada

* Autor proponuje zmianę algorytmu wydobycia Decred na [ProgPoW](https://github.com/ifdefelse/ProgPOW).
* Status: porzucona.

[Decred Open Source Research, propozycja nr 2 - projekty badań](https://proposals.decred.org/proposals/5d9cfb07aefb338ba1b74f97de16ee651beabc851c7f2b5f790bd88aea23b3cb) złożona przez @richardred 21. listopada

* Kontynuacja pierwszej [propozycji badań](https://proposals.decred.org/proposals/c68bb790ba0843980bb9695de4628995e75e0d1f36c992951db49eca7b3b4bcd) mającej na celu zebranie pomysłów na projekty badań i określenie najbardziej potrzebnych.
* Status: Autor nie zezwolił jeszcze na rozpoczęcie głosowania.

[Integracja Decred z bankomatami kryptowalut](https://proposals.decred.org/proposals/bb7e19283d5c65fed598d5a2f4afcc2b5d2eab187b9cb84fc4304430f80b5ad1) złożona przez bcashgr 24. listopada

* Propozycja od firmy Bcash szuka finansowania na integrację Decred ze swoją siecią bankomatów kryptowalutowych. Koszta deweloperskie to 25 tys. euro i 1650 euro/miesiąc w kosztach utrzymania.
* Status: Głosowanie w toku od 4. grudnia.

[Decred Radio Advertising, 190+ FM and AM Stations, + Intl. Satellite](https://proposals.decred.org/proposals/7fe5d07a4ffff7dc6a83383018823d880b1c1db0a29305e74934817cf2b4e2ce) złożona przez ftl_ian 26. listopada

* Propozycja reklamy Decred w programie radiowym "Free Talk Live". Całkowity koszt to $22,750 za okres 13 tygodni.
* Status: Głosowanie w toku od 4. grudnia.

[Decredex](https://proposals.decred.org/proposals/e78bc28631d0e682912e3ece25944481bf978b906ea44b1ed36470c0f48b27fc) złożona przez fabianreum 26. listopada

* Propozycja prosi o sfinansowanie prac nad zdecentralizowaną giełdą wymian przez firmę REUM Ltd i zakłada maksymalny budżet w wysokości $1,086,500.
* Status: Głosowanie w toku od 4. grudnia.

[Add Decred support to Coffee Wallet](https://proposals.decred.org/proposals/45de9806c952c5ffc2fc6782fddbc74c852c26e3fb0e950144b92d75082c4731) złożona przez francio 29. listopada

* Propozycja szuka finansowania pracy poświęconej dla wsparcia Decred w aplikacji "Coffee Wallet". Koszt pracy wynosiłby 150 DCR a jej zakończenie to wczesny styczeń 2019.
* Status: Autor nie zezwolił jeszcze na rozpoczęcie głosowania.

[Stable coin - USDD](https://proposals.decred.org/proposals/85fc65cef080cfc3564906fd3d488b827d74fc99bb29143ed8aa6c400b765be9) złożona przez fabianreum 29. listopada

* Ta propozycja szuka finansowania dla pracy nad stablecoinem (USDD) opartym na Decred i wiąże się ze współpracą partnerską między wieloma firmami. Budżet zakłada $1,576,000 i rozłożony jest na 4 lata realizacji całego projektu; jego dokładna analiza znajduje się w propozycji.
* Status: Autor nie zezwolił jeszcze na rozpoczęcie głosowania.

[Decred Bug Bounty Proposal](https://proposals.decred.org/proposals/d33a2667469b56942adf42453def6cc2292325251e4cf791e806939ea9efc9e1) złożona przez @degeri 30. listopada

* Ta propozycja ma na celu utworzenie programu nagród za wykrywanie bugów w kodzie Decred, w którym każdy, kto zgłosi buga czy podatność na atak, będzie mógł otrzymać nagrodę. Proponujący prosi o budżet w wysokości $5000 na okres 6 miesięcy w celu pokrycia kosztów założenia programu i kosztów operacyjnych, oraz szacuje górny limit wypłacalnych w tym czasie nagród na $100 000. @degeri włożył znaczący wysiłek w skonsultowanie tego programu ze społecznością w kwestii tego, w jaki sposób ów program powinien operować, dokładając specjalnej troski o to, by pracujący przy programie wykonawcy byli programowi przychylni.
* Status: Autor nie zezwolił jeszcze na rozpoczęcie głosowania.

Wielu ludzi rozpoczęło pracować na danych z Politei na kanałach #proposals i #research. @snr01 opublikował [wykresy ewolucji w głosowaniach](https://github.com/snr01/PiVotingCharts).

Słabe pod względem merytorycznym propozycje zaśmiecające system Politeia zostały dogłębnie omówione i zaproponowano wiele pomysłów na radzenie sobie z nimi, czego dobry przegląd dał @richardred w [Politeia Digest # 4] (https://medium.com/politeia-digest/politeia-digest-issue-4-nov-7-nov-13-2018-685e18e7491a).

Kanał #proposals jest bardzo aktywny i prowadzi wiele wnikliwych dyskusji na temat Politei i nadchodzących propozycji. Dołącz do [Matrixa](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org) lub [Slacka](https://decred.slack.com/messages/CDL5DRZU6).

Cotygodniowe Politeia Digest autorstwa @richardred szczegółowo omawia wszystkie ważne działania związane z Politeią, sprawdź [wydanie 4.](https://medium.com/politeia-digest/politeia-digest-issue-4-nov-7-nov-13 -2018-685e18e7491a), [wydanie 5.](https://medium.com/politeia-digest/issue-5-nov-14-nov-20-2018-62e8aed223b7) i [wydanie 6.](https: // medium .com / politeia-digest / issue-6-nov-21-nov-27-2018-3260d03d26a1), wydane w tym miesiącu (i [wydanie 7.] (https://medium.com/politeia-digest/issue-7-nov-28-dec-4-2018-bac012414d36) z początku grudnia). Dyskusje z Reddita można znaleźć za pomocą [tego zapytania](https://www.reddit.com/r/decred/search?include_over_18=on&restrict_sr=on&q=politeia%20digest).

## Sieć

Hashrate: hashrate na początku listopada wynosił około 156 PH/s i zamknął się w okolicy 159 PH/s, osiągając niż na poziomie 125 PH/s i wyż ok. 234 PH/s pomiędzy początkiem a końcem miesiąca. Udział BeePool w mocy obliczeniowej wahał się między 19-30%, F2Pool 15-46%, Luxor 1,6-4%, a Coinmine 1,9-4%. Moc obliczeniowa nieznanych źródeł mieściła się w przedziale 25-50%, a minimalnie wyniosła 15%, ze skokami do 75%. Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Ciekawostka: spodziewana całkowita liczba obliczeń użytych do wygenerowania aktualnego wierzchołka łańcucha [jest coraz bardziej zbliżona](https://matrix.to/#/!NNzHoaSdnsbZDQOXJr:decred.org/$154234658617707JUWKl:decred.org) do liczby obliczeń potrzebnych do przeprowadzenia ataku urodzinowego na pojedynczym RIPEMD160.

Staking: 30-dniowa średnia cena biletu wynosiła 103 DCR (+3,2). Cena wahała się od 96,7 do 110,2 DCR. Zablokowana kwota wynosiła 4,02-4,18 mln DCR, co odpowiadało 45,9-47,2% dostępnej podaży.

Po spadku ceny do 96,7, w jednym oknie zakupiono 1378 biletów, co po 9 kolejnych podwyżkach podbiło cenę do ​​110.2. Jest to nowy rekord pod algorytmem [sdiff](https://github.com/decred/dcps/blob/master/dcp-0001/dcp-0001.mediawiki), który działa od lipca 2017 r.

[@permabull nino] (https://twitter.com/ImacallyouJawdy) udostępnił [parę](https://twitter.com/ImacallyouJawdy/status/1065272779447009281) [nowych](https://twitter.com/ImacallyouJawdy/status/1060990375064522752) wykresów pokazujących wzrost depozytów DCR.

Węzły: od 1 grudnia na [dcred.eu](https://dcred.eu/nodeStats) jest 204 publicznych węzłów nasłuchujących i 332 węzłów normalnych. Rozkład wersji: 6,5% to wersje v1.4.0 (pre) dev (+ 0,5%), 50% to v1.3.0 (+ 5%), 25% jest na v1.2.0 (-3%), 11% na v1.1.2 (-3%), oraz 5% na v1.1.0.

## Wydobycie

Obelisk [rozpoczął produkcję](https://us16.campaign-archive.com/?u=393b2698d17bdfe48ac0422ac&id=28096412c5) partii 2-5 swoich jednostek i oczekuje, że rozpocznie wysyłkę na początku grudnia, i że wypełnienie wszystkich zamówień zajmie ok. 4 tygodni. 4 grudnia ogłosili kilka nowych ofert: płyty SC1 mogą być kupowane i instalowane w jednostkach DCR1, DCR1 mogą być konwertowane na SC1 z partii 6., lub sprzedane z powrotem do firmy Obelisk. Szczegóły znajdują się w [biuletynie](https://us16.campaign-archive.com/?u=393b2698d17bdfe48ac0422ac&id=88576cef2a).

[Okazało się](https://twitter.com/Pangolinminer/status/1061521332498624512), że faktyczna specyfikacja Whatsminer D1 wyniesie ok. 48 TH/s, czyli 9% więcej, niż oczekiwano (z 44 TH/s.) Przez ten fakt, cena została podbita o 350 dolarów do ostatecznej sumy 4850 dolarów [przez Pangolin](https://pangolinminer.com/product/whatsminer-dcr-with-psu-shipout-on-dec-5/). Zmiany cen MicroBT i opóźnienia wysyłki były różnie obsługiwane przez odsprzedawców i wywołały [mieszane opinie](https://bitcointalk.org/index.php?topic=5068845.msg47865706#msg47865706) wśród społeczności na temat najlepszego podejścia do sprawy.

Bitmain ogłosił Decred [Antminer DR5](https://shop.bitmain.com.cn/product/detail?pid=0002018111918225889369SR3N9s0646) ze specyfikacjami 34 TH/s przy 1800 W, cenie 19 000 CNY (2750 USD) i wysyłką pod koniec grudnia. Europejscy [importerzy DR5](https://www.antminerdistribution.com/antminer-dr5/) wstępnie mówią o dostępności w tygodniu 21 grudnia, a ceny maszyn wahają się od [3329 USD](https://french.alibaba.com/product-detail/asic-miner-bitmain-antmin-dr5-34th-blake256r14-dcr-digging-machine-decred-mining-machine-ant-miner-w-psu-60820041330.html) do [3291 EUR](https://miningwholesale.eu/product/bitmain-antmin-dr5-34th/) (3724 USD).

Wideorecenzja DCR1 od Obelisk została opublikowana na [youtube](https://www.youtube.com/watch?v=U0QjhvaoQpc). Na czacie [wyciekły](https://matrix.to/#/!NNzHoaSdnsbZDQOXJr:decred.org/$154146601110108OYpjf:decred.org) również zdjęcia innowacyjnej, kanadyjskiej metody chłodzenia koparek ASIC.

## Integracje

Pool Luxor [ogłosił](https://twitter.com/LuxorTechTeam/status/1067110171057381376) optymalizacje i wzrost mocy obliczeniowej dla maszyn wydobywających Decred o 3-5%.

Nowi VSP:

* [decred.staked.us] (https://decred.staked.us/) z opłatą 5%. [Staked](https://staked.us/about/) to firma, która świadczy usługi stakingu dla [wielu](https://staked.us/yields/) kryptowalut i niedawno opublikowała [poradnik](https://medium.com/coinmonks/decred-staking-guide-2e569d0390ff)  na temat tego, jak brać udział w stakingu Decred za pomocą ich VSP.
* [dcrpool.dittrex.com](https://dcrpool.dittrex.com) z 1% opłatą.

Integracje z giełdami wymian:

* [Bitqist](https://bitqist.com/) ogłosił integrację Decred na [r/decred](https://www.reddit.com/r/decred/comments/9y5dru/you_can_now_instantly_exchange_decred_on_bitqist/). Giełda ma [siedzibę](https://support.bitqist.com/hc/en-us/articles/360003566512-About-Us) w Holandii. @Haon, po sprawdzeniu giełdy, [ogłosił](https://matrix.to/#/!kdpEDksmOMNrlMqff::decred.org/$154342154026995puxog:decred.org), że wypłaty działają, ale depozyty nie są możliwe.
* [Kaiserex](https://www.kaiserex.com/) oficjalnie [uruchomiło](https://twitter.com/kaiserexcom/status/1064494181224206336) [biuro wymian OTC](https://www.kaiserex.com/kaiserex-otc-desk/) po prowadzeniu obrotu OTC od 2015 roku. DCR jest jedną z obsługiwanych kryptowalut, po stronie walut fiat są: USD, EUR, GPB i JPY. Min. wielkość transakcji wynosi 50 000 EUR, a opłaty wynoszą 0,05-1%.
* DragonEx [dodało](https://twitter.com/Dragonex_io/status/1062613644276428800) parę handlową DCR/BTC.

## Adopcja

Robiący świąteczne zakupy z Wielkiej Brytanii mają kolejne miejsce, gdzie mogą wydać Decred w tym sezonie. MonetaryUnit [ogłosiło](https://twitter.com/monetaryunit/status/1062127668769050626), że DCR jest [akceptowane](https://blog.flubit.com/pay-crypto-flubit-com/) na [Flubit](https://flubit.com/), brytyjskim serwisie handlowym, który nabyli w lecie. Oto parę informacji z [posta na blogu](https://blog.flubit.com/crypto-coins-drive-xmas-strategy-largest-eshop-200bn-cryptocurrency-industry-goes-mainstream-online-shopping-flubit-com/): Flubit to 8-letnia firma eCommerce, która w zeszłym roku obsłużyła ponad 3 miliony klientów, integracja kryptowalut jest bezproblemowa dla sprzedawców.

[Coinstop](https://coinstop.io/), australijski odsprzedawca urządzeń Trezor, Ledger i KeepKey, od teraz [akceptuje](https://twitter.com/COINSTOPio/status/1067927790320664576) DCR jako płatność.

## Nawiązywanie kontaktów

Nawiązywanie kontaktów było w dużej mierze związany z planowaniem, chociaż na całym świecie odbyło się wiele lokalnych spotkań, w tym ważne wydarzenia w Melbourne i Ho Chi Minh City. @eSizeDave i @joshuam wykonują świetną robotę rozprzestrzeniając Decred w Azji i w obszarze Pacyfiku.

@Dustorf opublikował [obszerny wpis](https://medium.com/@dlefebvr/pr-in-politeia-process-progress-and-pitching-in-d88771183dd4) szczegółowo opisujący proces zatwierdzania propozycji Ditto począwszy od wstępnej weryfikacji, dyskusji nad propozycją i głosowania, kończąc na kolejnych krokach w planowaniu i realizacji. Wpis ten otrzymał mnóstwo przedpremierowych informacji zwrotnych [na kanale #marketing](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$1542337694484551cyyyn:matrix.org), co pokazuje moc, umiejętności, i zaangażowanie naszych pisarzy. Wykonano ogrom pracy, gromadząc dane do przesłania i udostępnienia zespołowi Ditto, abyśmy mogli zacząć działać w grudniu. @Dustorf odbył rozmowę organizacyjną w poniedziałek, 3. grudnia, i wraz z @jy-p planują spotkanie z Ditto osobiście w tym samym tygodniu.

W odniesieniu do wpisu na blogu autorstwa @Dustorf, początkowy nacisk zostanie położony na dostosowanie społeczności do pozycjonowania i komunikacji, a następnie przeniesienie tych aspektów do niektórych aktualizacji internetowych, jednocześnie  czyniąc plany na wdrożenie strategii komunikacyjnej na 2019 rok. Ditto zaangażuje się publicznie na platformie Matrix w [#marketing](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org), a poufne informacje zostaną zarezerwowane dla nowego kanału Matrix o nazwie "Ditto PR". Jeśli sądzisz, że możesz pomóc i chcesz zostać zaproszony na ten kanał, skontaktuj się z @jz lub @Dustorf, celem dodania.

Grudzień będzie miesiącem planowania, a @jy-p przedstawi "Wykorzystanie znaczników czasu za pomocą technologii blockchain" podczas konferencji North American Bitcoin Conference w Miami, USA, w dniach 16-18 stycznia. Inne wydarzenia prawdopodobnie zostaną potwierdzone w pierwszym tygodniu grudnia i zostaną upublicznione na kanale #marketing.

Poza planowaniem średnio- i długoterminowej strategii, nasz PR będzie również działał w ustalonych już wcześniej sferach, jak wyjaśniono [w #marketing](https://matrix.to/#/!OfChXgczrIlpEZSFAv:decred.org/$154385900031974cIHsk:decred.org).

@Haon rozpoczął [dyskusję](https://www.reddit.com/r/decred/comments/a1bsv8/what_to_expect_from_the_ditto_partnership/) na Reddit o tym, czego można oczekiwać od partnerstwa z Ditto i podzielił się przemyśleniami na podstawie jego doświadczeń ze społecznością Decred i współpraca z poprzednią firmą PR (PRWithBrains).

## Eventy

Na których byliśmy:

* Szkolenie i sesja planowania przeprowadzona przez Raedah Group w Portland w USA. ([zdjęcie](https://twitter.com/raedahgroup/status/1058493594452004864))
* [Web Summit](https://twitter.com/WebSummit) w Lizbonie, Portugalia. Event tętnił życiem i wielu ludzi podeszło do stoiska Decred. @moo31337 [przybliżył](https://twitter.com/marco_peereboom/status/1059790693802094592) wizję Decred premierowi Portugalii, Antonio Coście. @vj i @jholdstock opublikowali raport z wydarzenia [tutaj](https://github.com/heyvj/decred-events/blob/master/reports/20181106-Web-Summit-Lisbon.md). @karamble, który "wykonał dobrą robotę, wykorzystując analogię małego i dużego Stakey'ego, aby zilustrować etapy dojrzewania biletów" zamieścił więcej notatek [tutaj](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154258437019744ukkoN:decred. org) odnośnie rozprzestrzeniania się firm funkcjonujących na prywatnych blockchainach. (zdjęcia: [1](https://twitter.com/NoahPierau/status/1059742659974193153) [2](https://twitter.com/NoahPierau/status/1060107159411810304) [3](https://twitter.com/NoahPierau/status/1060489795485478912) [4](https://twitter.com/blockblanc/status/1060541037733658625) [5](https://twitter.com/NoahPierau/status/1059837388225236992) [compo](https://twitter.com/LolekBolek74/status/1060551925563826183), filmiki poniżej)
* [PDX Blockchain Summit & Hackathon](https://pdxblockchainsummit.org) w Portland w USA. Grupa Raedah przedstawiła zdecentralizowane zarządzanie w Decred. (zdjęcia: [1](https://twitter.com/raedahgroup/status/1061722513615527936) [2](https://twitter.com/dantrevino/status/1061283707099594752))
* [Token Forum](https://www.thetokenforum.com/) w Seattle, USA. @oregonisaac wystąpił z prezentacją na temat na Decred i Blockchain Governance. @Eli-RG [zauważył](https://decred.slack.com/archives/C66363X44/p1542039292115100), że prezentacja była dużym sukcesem z wieloma opiniami, takimi jak: "najciekawsza prezentacja dnia" i "otworzyłeś mi oczy" lub, jak ujął to jeden z organizatorów: "On jest ... świetny!!!!". Więcej komentarzy od @oregonisaac [tutaj](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154183054312819Bkteq:decred.org). ([zdjęcie](https://matrix.decred.org/_matrix/media/v1/download/decred.org/RtgfjRzYbrvNjslhOZQNsNtc))
* [Blockmaster](https://www.blockmaster.com.br/eventos/forum-blockmaster-2018-sao-paulo/) w Sao Paulo w Brazylii. @Rhama przedstawił Decred i Politeię. (zdjęcia: [1](https://matrix.decred.org/_matrix/media/v1/download/decred.org/TgiORGBFSiEAQcuPzPvtZczZ) [2](https://matrix.decred.org/_matrix/media/v1 /download/decred.org/UFigpyKJeaOozzbiCeIiNSdH))
* [Sieć społeczności FinTech Melbourne](https://www.meetup.com/Melbourne-FinTech-Startups-Meetup/events/256195153/) w Melbourne w Australii. @eSizeDave [pisze](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154217119815341VaPZS:decred.org): "Frekwencja byla świetna, zwłaszcza biorąc pod uwagę, że mieliśmy tylko tydzień na promocję na MeetUp. Wielu zapytało, czy będziemy organizować to wydarzenie regularnie sposób, co oczywiście jest naszym planem. Gościliśmy osoby z instytucji finansowych, z analizy regulacyjnej FinTech, promotorów blockchain, startupowców, a także ludzi z innych projektów blockchain. Dwóch analityków danych z banku ANZ powiedziało mi, że proaktywnie szukali takiego wydarzenia i przypadkowo je znaleźli, nie będąc już członkami grupy FinTech Melbourne MeetUp, więc domyślam się, że istnieje popyt na takie wydarzenia. To był dobry wynik, więc będziemy wkładać jeszcze większy wysiłek w następną imprezę skoncentrowaną na FinTech.". Zobacz także [dyskusję](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154220759315790UMKqT:decred.org) na temat tego, dlaczego warto skoncentrować się na "fintechu", podczas gdy jest to branża, którą Decred powinien zakłócać. (zdjęcia: [1](https://twitter.com/coder_bec/status/1062251105198002177) [2](https://www.instagram.com/p/BqHJmarns8B/))
* [BlockchainFiesta](http://blockchainfiesta.io/) w Krakowie. @kozel i @donmario udzielili wywiadu [FXMag](https://www.fxmag.pl/), który zostanie opublikowany później. Fragment [pełnego raportu](https://github.com/heyvj/decred-events/blob/master/reports/20181116-Blockchain-Fiesta-Krakow.md): "Niektórzym z prelegentów, z którymi rozmawialiśmy, zaimponowało przyszłościowe myślenie i przezorność Decred i podejście "najpierw buduj, później rób szum". ([Reportaż z wydarzenia](https://krakow.tvp.pl/39996203/kryptowaluty-przyszlosc-platnosci-xxi-wieku), zdjęcia: [album](https://photos.google.com/share/AF1QipOhLa_L0g5NrBWzKFTxMeDD7VJeUBzHzEyker- DRdZGuQoXS9ogpN3waxW26vj0CQ?Key=Ty1jZ1NYRkdTY0dRRmNLc1JGcTdNby1BUlZ0eGZ3))
* [Blockchain Melbourne](https://www.meetup.com/BlockchainMelbourne/events/256295215/) w Melbourne w Australii. @eSizeDave przedstawił Decred, a następnie wystąpili dwaj przedstawiciele Apollo Capital. Najpierw przedstawili swoje usługi i mówili o tym, jak przeprowadzać analizę projektu dokładając przy tym należytej staranności, kładąc nacisk na punkty, które są mocną stroną Decred, a następnie wypowiadali się konkretnie o Decred. Z notatek: "Świetna, dobrze wykształcona widownia ... Zaskoczyło nas, że mamy tak dobry tłum do analizy inwestycji, z zaledwie około 1,5-tygodniową promocją, i to jeszcze z rynkami, na których leje się krew", oraz "należy zauważyć, że większość zasług należy się @Zohand, ponieważ ma wypracowaną  stałą relację z Apollo Capital.". Dyskusja na temat wydarzenia jest [tutaj](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154165462111747igExP:decred.org), uwagi po evencie z dodatkowymi przemyśleniami znajdziecie [tutaj](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154271915121075kJobf:decred.org) i [tutaj](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154312938324664CVmxQ:decred.org). ([zdjęcia](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154271920421079Uwail:decred.org))
* [Lekcje ze szczytu DevCon4 i Web3](https://www.meetup.com/Web3-Melbourne/events/bnrhmqyxpblc/) w Melbourne w Australii. Od @eSizeDave: "impreza odbywa się w RMIT Blockchain Innovation Hub. Royal Melbourne Institute of Technology (RMIT) jest uniwersytetem w Melbourne i pierwszym w Australii, który założył własny, dedykowany ośrodek innowacji blockchain w ramach swojej School of Economics (...) Oficjalni organizatorzy niedawno wrócili z Devconu w Pradze i przedstawią wnioski wyciągnięte z konferencji. Wzięli udział w naszym wydarzeniu 20. listopada i poprosili nas i Apollo Capital o przedstawienie Decred, a konkretnie Politei". W wydarzeniu brali udział ludzie głównie związani z Ethereum, ale prezentacja Politei przez Jamesa z Apollo Capital [zdała się](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154340368426560pechG:decred.org) zrobić dobre wrażenie. ([zdjęcia](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$154340368426560pechG:decred.org))
* Kolacja z Decred w Ho Chi Minh City, Wietnam. @joshuam opowiedział o Decred. Organizatorzy ([@BitcoinSaigon] (https://twitter.com/BitcoinSaigon)) następnie [stwierdzili](https://www.facebook.com/BitcoinSaigon/posts/938886146306840): "Zeszłej nocy zapoczątkowane zostały bardzo interesujące i fundamentalne rozmowy wokół istoty, znaczenia i wykonalności zdecentralizowanych systemów. To bardzo orzeźwiające dyskusje w czasie, gdy marketingowa nijakość wydaje się przeważać nad konkretami w tej przestrzeni." (zdjęcia: [1](https://www.facebook.com/BitcoinSaigon/posts/938886146306840) [2] (https://twitter.com/DominikWeil/status/1068425588258435072))

Na których będziemy:

* [North American Bitcoin Conference](https://btcmiami.com/) w Miami, USA, w dniach 16-18 stycznia. @jy-p wygłosi 15-minutową prezentację na głównej scenie na temat Politei. Wejdzie także w szczegóły nt. szerokiej gamy aplikacji, które mogą wykorzystywać platformę Politeia, w tym kryptowaluty, korporacyjne i rządowe. Przykłady to tokeny, prowadzenie rejestrów i systemy głosowania. Decred będzie miał także stoisko wystawowe o wymiarach 3x2,5m , więc musimy zebrac na tę okazję ekipę. Szukamy członków społeczności, którzy dołączą do nas, aby wziąć udział w evencie. Prosimy o wiadomość do @Dustorf, jeśli jesteście zainteresowani.
* [Campus Party](http://brasil.campus-party.org/cpbr12/patrocinadores/) w Sao Paulo, Brazylia, 12-17 lutego. Decred będzie miał prelegentów i ekskluzywny obszar dla hackathonów.
* [Jalisco Talent Land](https://www.talent-land.mx/#entradas) w Guadalajara w Meksyku w dniach 22-26 kwietnia. Decred będzie miał stoisko 3x3 m z 10 przepustkami konferencyjnymi. @elian zaprezentuje przegląd Decred (45 min) z sesją Q&A (15 min). Odbędzie się też dwugodzinna sesja, w której omówimy sposób korzystania z Decrediton, proces stakingu, cykl życia biletów i głosowania, oraz jak korzystać z Politei. Skontaktuj się z @elian, jeśli chcesz pomóc/uczestniczyć.

@jz opublikował [wytyczne](https://gist.github.com/jzbz/4431f620f2bad8032dc3caef2ed9112b) odnośnie reprezentowania Decred na konferencjach.

## Media

Artykuły:

* Forki Blockchain i podziały łańcucha: dlaczego powinniśmy ich unikać, aut. @Haon ([medium](https://blog.goodaudience.com/blockchain-forks-and-chain-splits-why-we-ould-avoid-them-f54c693a90f1), _przegapiony w wydaniu październikowym_)
* Wywiad z Marco Peereboom: Zarządzanie, Decred i Politeia ([coinbureau.com](https://www.coinbureau.com/interview/marco-peereboom-decred/))
* Wywiady infrastrukturalne: feeleep, Operator, coinmine.pl, aut. @kozel ([medium](https://medium.com/decred/decred-intriguing-and-extraordinary-an-interview-with-coinmine-pl-mining-pool-operator-5c5592443cb4), dostępny również [po polsku](https://medium.com/decred-polska/decred-interesuj%C4%85cy-i-nieszablonowy-wywiad-z-operatorem-coinmine-pl-11e92657136e))
* PR w Politei: proces, postęp i dokładanie swojej cegiełki, aut. @Dustorf ([medium](https://medium.com/@dlefebvr/pr-in-politeia-process-progress-and-pitching-in-d88771183dd4))
* Zarządzanie w Blockchainie: jak Decred iteruje na podstawie Bitcoina, aut. @zubairzia0 ([medium](https://medium.com/decred/blockchain-governance-how-decred-iterates-upon-bitcoin-3cc7030c655e))
* Podział biletów DCR - Wszystko, co musisz o nim wiedzieć! autor: @David ([medium](https://medium.com/decred/dcr-ticket-splitting-all-you-need-to-know-b8edc6b65db3), [reddit](https://www.reddit.com/r/decred/comments/9vhpby/decred_ticket_splitting_overview/))
* Hash War Theatre: kosztowny spektakl, aut. @richardred ([medium](https://medium.com/@richardred/hash-war-theater-67d3fcac3e97))
* Czym jest Decred? aut. @kozel (polski, [bithub.pl](https://bithub.pl/artykuly/czym-jest-decred/))
* Decred Review - Demokratyczne zarządzanie przekazuje użytkownikom kontrolę ([coiniq.com](https://coiniq.com/decred-review/))
* Mniejsze monety PoW są w ciągłym niebezpieczeństwie ataków 51% - model zarządzania Decred jest rozwiązaniem ([captainaltcoin.com](https://captainaltcoin.com/smaller-pow-coins-are-in-constant-danger-of-51-attacks-decred-dcr-governance-model-is-the-solution/))
* Podział biletów DCR, aut. @guang (chiński, [medium](https://medium.com/@guang.dcr/%E6%89%AB%E7%9B%B2-decred%E5%88%86%E7%A5%A8-ffe3eb2de64d))

Opublikowano więcej artykułów na różnych stronach internetowych, ale wymieniliśmy tylko wybrane. Projekt [decred-media-tracker](https://github.com/RichardRed0x/decred-media-tracker) służy do śledzenia wszystkich artykułów.

Tłumaczenia:

* [Zarządzanie w Blockchainie: jak Decred iteruje na podstawie Bitcoina](https://medium.com/decred/blockchain-governance-how-decred-iterates-upon-bitcoin-3cc7030c655e) aut. @zubairzia0 - [w jęz. chińskim](https://medium.com/@guang.dcr/%E8%AF%91%E6%96%87-%E5%8C%BA%E5%9D%97%E9%93%BE%E6%B2%BB%E7%90%86-decred%E5%A6%82%E4%BD%95%E8%BF%AD%E4%BB%A3%E6%AF%94%E7%89%B9%E5%B8%81-53f434b26105), tłum. @guang
* [Decred: Od czego wszystko to się zaczęło?](https://thedecreddigest.com/2017/06/10/decred-where-did-it-all-begin/) aut. @thedecreddigest - [w jęz. hiszpańskim](https://medium.com/@decred_es/decred-d%C3%B3nde-comenz%C3%B3-todo-aaa49fed0091), tłum. @elian
* [Rekrutacja w Decred](https://blog.decred.org/2017/07/25/Decred-Recruiting/) aut. @jy-p - [w jęz. hiszpańskim](https://medium.com/@decred_es/c%C3%B3mo-ser-contratista-en-decred-d0f05386f799), tłum. @elian
* [Politeia w fazie produkcji](https://blog.decred.org/2018/10/15/Politeia-in-Production/) aut. @jy-p - [w jęz. portugalskim](https://stakey.club/translated/politeia-em-producao/), tłum. @mm
* Decred Journal - Październik 2018 [w jęz. rosyjskim](https://medium.com/decred-russia/decred-journal-%D0%BE%D0%BA%D1%82%D1%8F%D0%B1%D1%80%D1%8C-2018-1eeffc65344c) oraz [w jęz. włoskim](https://medium.com/decred-ita/decred-journal-ottobre-2018-a68e88c926ff) tłum. @DZ. To kawał epickiej roboty; na październikowe wydanie składało się 53 kilobajtów tekstu, 1.5x więcej, niż poprzedni rekord.

Materiały wideo:

* Kilka filmów zostało dodanych do [playlisty Decred](https://www.youtube.com/playlist?list=PLaMrpvQ0yJ_x4L3vtUwfZOM6euh3P8-fx) z Texas Bitcoin Conference, która zawiera teraz 18 pozycji. Wszystkie 52 filmy z eventu znajdują się na [tej liście odtwarzania](https://www.youtube.com/playlist?list=PLlLSsIJ2O_cTIaALNXExlEqu3jP6IQyc).
* @moo31337 udzielił obszernego [wywiadu z Paulem Snowem](https://www.youtube.com/watch?v=MgtBRlAfu2k) po konferencji Texas Bitcoin omawiającej zakulisową historię projektu Decred i innych projektów Open Source.
* Filmy wideo z @moo31337 z Web Summit: [Inwestowanie w krypto](https://www.youtube.com/watch?v=GO_Iv4vRjZs), [Czy krypto tu pozostanie?](https://www.youtube.com/watch?v=L-OzMPHbDi4).
* Crypto with Chingas [zrobił wywiad z @joshuam](https://www.youtube.com/watch?v=o5jSLGiAdb8) na temat znaczenia rozstrzygania sporów w zdecentralizowanym projekcie.
* @michae2xl wyprodukował nowe odcinki Decred Weekly oraz wywiad z @TiagoAlves i @fernandoabolafio o Politei. Te i poprzednie filmy w języku portugalskim znajdziesz na kanale [Decred Brazil](https://www.youtube.com/channel/UC73wa2ddXuPWsmenVfeFTYg).

Standard & Consensus ocenili Decred na C+. Oryginalny raport jest [w jęz. chińskim](https://michelangelo.sncrating.com/report/168), a @guang napisał [jego recenzję](https://medium.com/@guang.dcr/%E8%A7%A3%E6%9E%90%E8%AF%84%E7%BA%A7-dcr-%E9%80%9A%E8%BF%87%E6%B7%B7%E5%90%88%E5%85%B1%E8%AF%86%E6%9C%BA%E5%88%B6%E5%B9%B3%E8%A1%A1%E6%9D%83%E7%9B%8A%E5%88%86%E9%85%8D-%E6%A0%87%E5%87%86%E5%85%B1%E8%AF%86%E8%AF%84%E7%BA%A7-5edc6f03dc1c) również w jęz. chińskim. Słabe strony wskazane przez raport wskazują na niską aktywność w mediach społecznościowych, niski wolumen obrotu i wysokie ryzyko płynności. Mocnymi aspektami są hybrydowy system PoW + PoS, który wprowadza równowagę pomiędzy posiadaczami, górnikami i deweloperami, doświadczony zespół programistów i lepszą suwerenność i niezależność społeczności dzięki systemom głosowania.

## Dyskusje społeczności

Statystyki społeczności na dzień 1. grudnia:

* Obserwujący na Twitterze 40,004 (-1598)
* Subskrybenci na Reddit 9,131 (+147)
* Użytkownicy na Matrixie 203 (+10)
* Użytkownicy na Slacku 6,353 (+82)
* Użytkownicy na Telegramie 4,642 (+213)
* Subskrybenci kanału YouTube 3,736 (+10)
* Obserwujący na Facebooku 3,105 (+20) i 2,867 (+18) polubień
* Obserwujący na LinkedIn: strona Decred 433 (+27), strona Politeia 20 (+8)
* GitHub 447 (+17) gwiazdek i 1,159 (+41) forków repozytorium dcrd

Wiadomości z systemów komunikacyjnych:

* Stworzono nowy kanał [#research](https://matrix.to/#/!vGasNHFXqjoEWUBTIi:decred.org) do pracy nad projektami w ramach propozycji Open Source Research.
* Zakłócenia na mostach doprowadziły do ​​tego, że niektóre wiadomości nie były dostarczane ze Slacka na Matrixa.
* Rozpoczęto nowy subreddit, aby przezwyciężyć niepokojący rozwój cenzury r/decred, dyskusję znajdziesz [tutaj](https://matrix.to/#/!MgQoetFiyjrHAywokv:decred.org/$154302771624142JbZDI:decred.org). _(bee: tak, tylko trolluję)_
* Dodano dwie nowe [zasady](https://www.reddit.com/r/decred/about/rules/) na r/decred: "Jeden temat dotyczący ceny na raz" i "Zakaz zachęcania". Motywacja została wyjaśniona w [tym poście](https://www.reddit.com/r/decred/comments/9zy3xt/new_rule_one_price_thread_at_a_time/).
* Nadal poszukujemy dodatkowych modów na Discorda i kogoś, kto wprowadzi odporność na spam.
* Podjęto próbę wyłudzania informacji użytkownikom MyEtherWallet. Zachowaj czujność!

Twitter: [ankieta](https://twitter.com/KyleSamani/status/1062382292860059648) o tym, czy otwarte głosowanie na platformie Politeia jest dobrym procesem, więcej ukochanej dyskusji o plutokracji; blockchainy z zarządzaniem bezpośrednio na łancuchu (on-chain) [nie są jednakowe](https://twitter.com/spencernoon/status/1062482562482868224), systemy zarządzania w Decred vs Tezos.

Reddit: czy wieloryby DCR są [dobre, czy złe](https://www.reddit.com/r/decred/comments/9t9sju/the_placeholder_whales_good_or_bad_for_decred_in/) dla projektu; [inwestowanie](https://www.reddit.com/r/decred/comments/9wpx1b/treasuryenhancing_products_built_in_top_decred/) z wykorzystaniem funduszy ze Skarbca i konfliktówy interesów; Politeia [system piasty i szprych](https://www.reddit.com/r/decred/comments/9yu6pr/politeia_hubandspoke_model_for_private_torrent/) dla prywatnych trackerów torrentów; [zaufanie](https://www.reddit.com/r/decred/comments/9zi8tz/will_it_be_possible_to_sign_tickets_with_ledger/) wobec portfeli sprzętowe; [ile](https://www.reddit.com/r/decred/comments/a0utmf/how_many_atomic_swaps_have_actually_been_achieved/) atomic swapów zostało dokonanych.

Indeks czatu został pominięty w tym wydaniu. W planie jest zastąpienie go kolaboratywnym dokumentem.

## Rynki

Rynek krypto odnotował w listopadzie spadek o 70 miliardów dolarów, przy czym większość aktywów z listy najważniejszych 100 straciła od 30% do 60% wartości rynkowej. Bitcoin ustanowił zagregowany niż w wys. 3660$ po spadku z miesięcznego maksimum w wysokości 6540 USD, co daje 45% szczytowy spread. Pomiędzy 14-15 listopada większość ze 100 największych aktywów straciło 10-20% wartości USD w ciągu jednego dnia - dzień przed niesławnym podziałem BCH. [Forbes](https://www.forbes.com/sites/ginaclarke/2018/11/27/latest-crypto-crash-caused-by-bitcoin-civil-war-say-experts/1) i [Bloomberg](https://www.bloomberg.com/news/articles/2018-11-16/crypto-winter-comes-early-as-bitcoin-slide-spurs-viability-fears) przypisały spadki BTC rozłamowi Bitcoin Cash, ten drugi powołując się na strach, niepewność i zwątpienie niektórych ludzi. Pod koniec miesiąca obie monety wyłoniły się z forka jako podtrzymywane nowe łańcuchy, ale razem ich cena jest o 40% niższa od najniższych poziomów przed rozłamem. Inni, tacy jak [Yahoo Finance](https://finance.yahoo.com/news/major-cryptocurrencies-drop-again-bitcoin-111026294.html) przypisują spadki [orzeczeniom SEC](http://www.bitcoinpower101.com/ 2018/11/24 / the-secs-recent-rulings-is-more-about-exchange-than-icos /) w sprawach ICO.

Decred nie był odporny na ruchy na rynku i spadł z 40 USD do 19,8 USD pod koniec miesiąca.

## Ważne kwestie i wiadomości poboczne

Nvidia [odnotowała](https://cointelegraph.com/news/nvidia-q3-results-reveal-crypto-hangover-due-to-disappearance-of-miner-sales) spadek sprzedaży GPU przeznaczonych do wydobycia kryptowalut. Na pewno nie ma to nic wspólnego z Ethereum, Zcash i innymi dostawcami ASIC dla algorytmów górniczych zorientowanych typowo na GPU, ale raczej "to naprawdę kanarek w kopalni dla Bitcoina i innych kryptowalut" jak rzeczą [eksperci](https://www.bloomberg.com/news/articles/2018-11-16/crypto-winter-comes-early-as-bitcoin-slide-spurs-viability-fears). Serio, to właśnie [upadek](https://www.bloomberg.com/news/articles/2018-11-15/nvidia-gives-weak-forecast-citing-inventory-stock-slumps) wydobywania kryptowalut.

[Nowe badanie](https://twitter.com/C_Bendiksen/status/1068221424777814016) wydobycia Bitcoina daje pewne szacunkowe wyliczenia kosztów eksploatacji i wydobycia oraz sugeruje, że niektórzy górnicy wyłączają swoje urządzenia. Kolejnym interesującym odkryciem jest to, że prawie 80% zużywanej energii pochodzi z odnawialnych źródeł energii.

W czasopiśmie Nature Climate opublikowano [artykuł](https://www.nature.com/articles/s41558-018-0321-8), który sugeruje, że wydobycie Proof-of-Work Bitcoina będzie miało znaczący negatywny wpływ na zmiany klimatyczne. [Dyskusja](https://matrix.to/#/!NKtIRqGOEGaZvSQkKl:decred.org/$15412120277994HzToF:decred.org) w #random odnotowała głębokie nieporozumienie dotyczące działania PoW i alarmująco niską jakość merytoryczną artykułu, a także parę domysłów o tym, dlaczego został opublikowany.

Fundacja Ethereum finansuje [starania](https://www.coindesk.com/ethereum-foundation-filecoin-back-plan-to-make-proof-of-storage-hardware) w celu stworzenia ASIC, które obliczają [funkcje weryfikowalnego opóźnienia](https://vdfresearch.org/) (VDF) jako zamiennik dla wydobywania metodą dowodu pracy (Proof-of-Work) dla bezpieczeństwa blockchaina. [Ten artykuł](https://medium.com/@djrtwo/vdfs-are-not-proof-of-work-91ba3bec2bf4) porównuje VDF i Proof-of-Work.

Zcash [zaaprobował](https://github.com/ZcashFoundation/GrantProposals-2018Q2/issues/15#issuecomment-436106276) finansowanie prototypu ProgPoW dla Zcash. Ten odporny na jednostki ASIC, przyjazny dla GPU algorytm został również [zaproponowany](https://proposals.decred.org/proposals/0aaab331075d08cb03333d5a1bef04b99a708dcbfebc8f8c94040ceb1676e684) ostatnio na Politei.

Zcash interesuje się również [hybrydowym układem ASIC-GPU](https://forum.zcashcommunity.com/t/announcing-zcash-blossom-and-proposed-feature-goals/31891), a także innymi ulepszeniami planowanymi na przyszłoroczną aktualizację protokołu.

Według [tego wątku](https://www.reddit.com/r/CryptoCurrency/comments/9sq0jj/shady_behavior_from_groestlcoin_grs_developers/), dla kolejnej monety z deklarowaną odpornością na jednostki ASIC opracowano układ ASIC, podczas gdy deweloperzy usunęli stwierdzenia o odporności na ASIC ze strony internetowej swojego projektu. Wątek na reddit, który poruszył tę kwestię, został [wymazany](https://archive.today/SzoHs). Przykład, w którym przejrzysta cenzura może być przydatna. (_przegapiono w październikowym wydaniu_)

Nowa biblioteka rdzenia napisana w Rust została [wydana](https://github.com/brentongunning/rust-bch) dla Bitcoin Cash. To dodatek do istniejących już [rust-bitcoin](https://github.com/rust-bitcoin/rust-bitcoin), [parity-bitcoin](https://github.com/paritytech/parity-bitcoin) i [bitcrust ](https://github.com/tomasvdw/bitcrust). Rust to kolejny nowoczesny język poza Go, w którym ceni się bezpieczeństwo i wydajność. Miło jest zobaczyć taki dodatek, ponieważ może się on przydać Decred, który jest otwarty na wiele implementacji.

Bitcoin Cash, narodzony jako rozwiązanie dla długotrwałej debaty skalowania Bitcoin, w tym miesiącu sam przeszedł kontrowersyjnego hard forka. Ten [artykuł](https://bitcoinmagazine.com/articles/when-fork-forks-what-you-need-know-bitcoin-cash-goes-war/) dobrze podsumowuje to, o co w nim chodziło. Strony zaczęto nazywać względem dominującej implementacji oprogramowania, Bitcoin ABC oraz Bitcoin SV (Satoshi's Vision - wizja Satoshiego). BCH ABC planował hard forka, aby dodać kanoniczne porządkowanie transakcji i nowy op code - BCH SV odrzuca te zmiany, a zamiast tego planuje powrócić do zestawu reguł opartych na wersji 0.1.0 Bitcoina.

Wydaje się, że górnicy i wyrocznie podzielili się względnie równomiernie pomiędzy obie strony, z Rogerem Ver i Jihanem Wu po stronie ABC i Craigiem S Wrightem i Calvinem Ayre po stronie BCH SV. Ten kłótliwy hard fork był jeszcze bardziej kontrowersyjny niż większość, ponieważ strona BCH SV ogłosiła, że ​​unieważni ochronę przed powtórnymi transakcjami dodaną przez ABC (kolejny [dobry artykuł](https://medium.com/circle-research/bitcoin-cash- hard-fork-report-4e4377d514a) o przygotowaniach do forka). SV w rzeczywistości planowało złagodzić ochronę przed powtórnymi transakcjami oferowaną przez ABC, umożliwiając górnikom zbieranie wszelkich przesłanych BCH przy użyciu nowych OP kodów ABC - tak, aby użycie tych nowych funkcji spowodowało utratę BCH w łańcuchu SV. Istniały również groźby ataku na łańcuch ABC i zabicia go, lub uczynienia go niezdatnym do użytku na długi okres, jeśli łańcuch SV uzyskałby wystarczającą moc obliczeniową.

Ten [post na r/btc](https://www.reddit.com/r/btc/comments/9xasgg/bitcoin_cash_hard_fork_mega_thread/) skompilował listę zasobów do śledzenia forka w trakcie jego trwania. Strona [cash.coin.dance](https://cash.coin.dance/) ma wiele narzędzi do śledzenia forka w czasie rzeczywistym. Ten [artykuł](https://bitcoinmagazine.com/articles/one-day-after-bitcoin-cash-hard-fork-takeaways-and-latest-developments/) to dobry raport z 24 godzin po rozłamie. @richardred napisał także krótką perspektywę tego [teatru wojny mocy obliczeniowej](https://medium.com/@richardred/hash-war-theater-67d3fcac3e97). 26. listopada strona SV wycofała się i oświadczyła, że ​​wojna mocy obliczeniowej została [zakończona](https://coingeek.com/original-bitcoin-reborn-bitcoin-sv-bsv-bch-hash-war-ends/), tym samym pozwalając obu łańcuchom współistnieć w pokoju. Ponieważ wydaje się, że oba łańcuchy współistnieją bez przewagi którejkolwiek ze stron pod kątem moby obliczeniowej, wydaje się, że w przypadku tego forka koszty wyrażane są przede wszystkim w kategoriach rozłamu i pogorszenia stosunków wśród społeczności. Społeczność posiadaczy BCH w tym przypadku tak naprawdę nie miała roli do odegrania, ani sposobu, aby wpłynąć na wynik; był to spór jedynie do rozegrania przez górników.

W zaistniałej sytuacji to dobre uczucie, gdy posiadasz bilety Decred, które można wykorzystać do zapobiegania ciągnącym się, kontrowersyjnym podziałom łańcucha, i karania górników, którzy mogą chcieć zmieniac łańcuch w podwórko dla swoich własnych rozgrywek, jeśli kiedykolwiek stanie się to problemem.

W tym miesiącu wystartował również [SharkPool](https://www.ccn.com/war-bitcoin-cash-startup-launches-mining-pool-to-attack-altcoins-bch-forks/), mający na celu aatakowanie innych forków łańcucha Bitcoin poprzez wydobywanie pustych bloków i sprzedaż zysków dla BCH.

Wydaje się, że w społeczności RChain zaistniał jakiś dramat, w skład którego wchodzą zwolnienia ludzi i potencjalny rozłam sieci. Trudno znaleźć na ten temat jakiekolwiek źródła, poza [tym postem na blogu](https://joshyorndorff.com/blog/keeping-the-rchain-community-together). To nie pierwszy wewnętrzny konflikt dla RChain, ponieważ on sam zrodził się z nieporozumienia wewnątrz projektu Synereo, które w przeszłości doprowadziło do podziału ([dyskusja](https://matrix.to/#/!tIDEIWechmqCLjPiui:decred .org / 154272469321222NLqFX: decred.org)).

Patrząc na wszystkie walki w innych społecznościach (ja, @bee) nie mogę nie wstawić osobistego komentarza. Wydaje mi się, że społeczności marnują mnóstwo energii na wszystkie te kontrowersje. Ta energia nie buduje żadnej wartości. Podziały łańcuchów i podziały społeczności zostawiają obie strony z mniejszą liczbą ludzi, mniejszym talentem i mniejszą szansą na wywieranie długoterminowego wpływu. Ironią losu jest to, że w przestrzeni zaprogramowanych zdecentralizowanych systemów konsensusu tak wielu ludzi nie osiąga konsensusu ludzkiego. Projektowi Decred udaje się brnąć do przodu z przyzwoitą szybkością, ponieważ unika zewnętrznych, a co ważniejsze wewnętrznych konfliktów. Zachowajmy motywację i utrzymujmy społeczność razem.

Aragon [wydał](https://blog.aragon.org/aragon-06-is-live-on-mainnet/) nową wersję 30. października, która pozwala użytkownikom tworzyć organizacje na głównej sieci Ethereum. Wcześniej, ponad 15 000 organizacji powstało na poprzednich wersjach sieci testowej Ethereum. Aragon może być użyty do tworzenia "organizacji", dodawaniania członków i przypisywania im tokenów, a następnie przeprowadzania głosowań sygnalizujących za pomocą tych tokenów.  Również niedawno społeczność zagłosowała [w przeważającej części](https://twitter.com/AragonProject/status/1063590019749855237) (99,97%!), za zatwierdzeniem[AGP-1](https://raw.githubusercontent.com/aragon/AGPs/8c945258fc58c842752a49946514815a4fdd971d/AGPs/AGP-1.md), procesu propozycji zarządzania.

Fundusz społecznościowy NavCoin (https://navcoin.org/en/community-fund/) został [uruchomiony](https://medium.com/@NAVCoin/community-fund-activated-edc72207a0c0) 16. listopada. Fundusz wspólnotowy NavCoin działa na zasadzie "konsensusu dwóch głosów", z pierwszym głosowaniem w celu ustalenia, czy wniosek zostanie zatwierdzony, a następnie kolejnym głosowaniem w celu ustalenia, czy należy dokonać wypłaty (po zakończeniu pracy). Głosujący są uczestnikami stakingu NavCoin i głosują zgodnie z wagą ich wkładu. Fundusz wspólnotowy otrzymuje 0,25 NAV z każdego wybitego bloku, 500 000 NAV rocznie lub około 93 000 USD według dzisiejszych cen. Propozycja głosowania trwa jeden tydzień i wymaga udziału 50% stakujących, a próg akceptacji wymaga aprobaty 70% głosujących.

Rząd Wielkiej Brytanii odwołał [projekt stablecoin](https://github.com/BitGo/prova) oparty o fork btcd. [@alexbosworth komentuje](https://twitter.com/alexbosworth/status/1056318062176145414): "Rzecz w stablecoins jest taka, że pewnego dnia ktoś może przyjść i odwołać cały projekt.".

Wiadomości DEX: IDEX [zdecydował](https://medium.com/aurora-dao/pragmatic-decentralization-how-idex-will-approach-industry-regulations-8b109212128a) wdrożyć blokowanie IP i KYC, SEC [postawiło zarzuty]( https://www.sec.gov/news/press-release/2018-258) założycielowi EtherDelta kierowania niezarejestrowaną giełdą wymian.

Umieszczenie na Coinbase [nie zawsze](https://www.ccn.com/why-did-bat-lose-28-of-its-value-overnight-after-coinbase-listing/) kończy się pompą.

Odcinek podcastu Unchained [omawia](https://twitter.com/laurashin/status/1059791476102754305) "dlaczego ICO spadły o 90% od zimy, dlaczego zrzuty mogą być lepsze niż ICO do zasiewania wykorzystania sieci, czy są one "zgodne z prawem, czy nie, i jakie portfele obierać za cel". ([link poza-itunes](http://unchainedpodcast.co/down-94-since-winter-what-has-happened-to-icos-ep91)).

Bitfinex [porzucił](https://www.ccn.com/op-ed-is-tether-trying-to-price-ithere-out-of-the-stablecoin-wars/) konwersję 1: 1 między USD i USDT, podczas gdy Tether.to [ponownie otworzył](https://tether.to/tether-reopens-account-verification-and-direct-redemption-of-fiat-from-its-platform/) weryfikacje i bezpośrednie wypłaty USDT, w wys. min. 100 000 USD.

Wiadomości dotyczące bezpieczeństwa: zostało ujawnionych siedem nowych ataków Spectre i Meltdown (https://www.zdnet.com/article/researchers-discover-seven-new-meltdown-andspectre-attacks/) co w różnym stopniu ma wpływ na procesory Intel, AMD i ARM. Następuje to po odkryciu [podatności nowej technologii Intel Hyper-Threading](https://thehackernews.com/2018/11/portsmash-intel-vulnerability.html) odkrytej na początku tego samego miesiąca. Te rewelacje nadal pokazują, że potrzebujemy bezpieczniejszego i bardziej otwartego sprzętu do obsługi naszych kryptowalut.

SMS-y i poleganie na operatorach komórkowych w ogólnym sensie okazało się złym wyborem dla 2FA. W tym [niedawnym incydencie](https://techcrunch.com/2018/11/15/millions-sms-text-messages-leaked-two-factor-codes/), z serwera niechronionego nawet hasłem niemalże w czasie rzeczywistym wyciekały miliony wiadomości SMS zawierające kody 2FA, resety haseł i inne poufne informacje. W innym przypadku, procesy sądowe [takie jak te](https://www.coindesk.com/victims-sue-att-t-mobile-over-sim-swap-crypto-hacks/), miejmy nadzieję, zmotywują dostawców usług komórkowych do poprawy bezpieczeństwa, lecz nie odzyskają twoich monet. Mówiąc jeszcze bardziej ogólnie, większość smartfonów ma [chip pasma podstawowego](https://pl.wikipedia.org/wiki/Baseband_processor) i inne zastrzeżone części - nikt tak naprawdę nie wie, co one robią i jak bardzo są podatne na ataki.

Oprogramowanie do słuchawek [zostało przyłapane](https://twitter.com/spazef0rze/status/1067583791596781570) na instalowaniu certyfikatu głównego, który można potencjalnie nadużywać do podszywania się pod witryny.

Portfel Copay został zainfekowany złośliwym oprogramowaniem, które kradło kryptowaluty. Jeśli korzystałeś z tego portfela lub takiego, który jest na nim oparty, być może będziesz musiał przenieść swoje monety na nowe ziarno. Teno [sprawozdanie](https://thehackernews.com/2018/11/nodejs-event-stream-module.html) zawiera szczegóły, takie jak dotknięte oprogramowanie i wersje. Przyczyną była kompromitacja repozytorium jednej z zależności npm. Nie miało to wpływu na żadne znane oprogramowanie Decred.

W tym miesiącu wyniknęło sporo problemów związanych z bezpieczeństwem, ale mam nadzieję, że te ostrzeżenia pomogą Ci wyciągnąć wnioski płynące z tych błędów oraz chronić swoje monety.

## O tym wydaniu

To 8. wydanie Decred Journal. Jest on dostępny na [GitHub](https://xaur.github.io/decred-news/journal/201811). Wcześniejsze wydania są dostępne [tutaj](https://xaur.github.io/decred-news/).

Chińskie tłumaczenie aut. @guang jest dostępne na [medium](https://medium.com/@guang.dcr/decred%E6%9C%88%E6%8A%A5-11%E6%9C%88-1ddac6598830) i [GitHub](https://github.com/Guang168/DecredCNJournal/blob/master/201811_DecredJournalCN.md).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanch stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze opinie i komentarze są mile widziane na portalu [Reddit](https://www.reddit.com/r/decred/comments/a3tq54/decred_journal_november_2018/), [GitHub](https://github.com/xaur/decred-news/issues) i [Matrixie](https://matrix.to/#/!lbzTjhzNbIaDbuAxkS:decred.org).

Zasługi (w kolejności alfabetycznej): bee, degeri, guang, Haon, kozel, oregonisaac, richardred, zubairzia0.
