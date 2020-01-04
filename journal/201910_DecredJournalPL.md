# Decred Journal – Październik 2019

![abstrakcja](../img/journal-201910-384.png)

_Obraz: Przekaźnik źródłowy, aut. @saender_

Najważniejsze wydarzenia z października:

- Kandydaci do wydania dla głównego oprogramowania v1.5 są gotowi do testów. Najważniejsze zmiany obejmują zmianę zasad konsensusu w celu dodania zobowiązań do nagłówka bloków, które w czerwcu zostały sfinansowane przez interesariuszy, oraz kapitalny przegląd infrastruktury górniczej (dcrd), początkowe wdrożenie w zakresie ochrony prywatności (dcrwallet), eksperymentalną integrację LN i poprawki do interfejsu użytkownika (Decrediton) oraz przeniesienie ogromnego zestawu aktualizacji (dcrlnd).
- i2 Trading rozpoczęło zapewnianie płynności na 3 giełdach (4 pary), w następstwie ich zaakceptowanej propozycji.
- Przeprojektowany frontend platformy Politeia jest już dostępny. Warto sprawdzić go pod kątem nowej estetyki, która jest bardziej zgodna z innymi programami Decred, oraz ulepszeń wydajności.
- Październik był ogromnym miesiącem dla wydarzeń z obecnością Decred. Na całym świecie członkowie lokalnej społeczności reprezentują Decred na wydarzeniach, które organizują i w których uczestniczą.
- W październiku ukazały się również główne publikacje ze wszystkich trzech aktywnych programów badawczych oraz czwartego, który został zatwierdzony na początku listopada. Pojawiło się również wiele artykułów i innych mediów dotyczących pierwszego roku istnienia Politei (rocznica przypadła na 16 października).

## Przygotujcie się na nadchodzące głosowanie nad zmianą w zasadach konsensusu!

Głosowanie w sprawie zmiany zasad konsensusu odbędzie się w wersji 1.5. Pliki binarne kandydatów są już [dostępne](https://github.com/decred/decred-binaries/releases/tag/v1.5.0-rc1), a ostateczne wydanie nastąpi wkrótce.

Przygotujcie się na głosowanie, aktualizując oprogramowanie i dokonując wyboru dla swoich głosów w biletach solo, czy korzystających z VSP.

Postępy można śledzić na stronie [Agendy](https://explorer.dcrdata.org/agendas) dcrdata oraz na stronie [voting.decred.org](https://voting.decred.org/).

Wysokie zaangażowanie wyborców wysyła silny sygnał. Zróbmy to!

## Kandydaci do wydania wersji v1.5

Kandydaci do wydania dcrd, dcrwallet, Decrediton i dcrlnd są dostępni do testowania. Poniżej znajdują się najważniejsze informacje z ich notatek do wydania.

**dcrd v1.5****

Zobowiązania dotyczące nagłówków blokowych są wprowadzone i gotowe do uruchomienia w razie pomyślnego głosowania na łańcuchu. Po uaktualnieniu do wersji 1.5, interesariusze mogą ustawić swoje preferencje dotyczące głosowania poprzez swój portfel lub stronę internetową dostawcy usług głosowań (VSP). Głównym celem tej zmiany jest zwiększenie bezpieczeństwa i wydajności lekkich klientów, takich jak Decrediton w trybie SPV i mobilnych portfeli dcrandroid/dcrios. Doda ona również infrastrukturę, która toruje drogę do kilku przyszłych usprawnień skalowalności. Generalny opis zmian można znaleźć w [propozycji Politeia](https://proposals.decred.org/proposals/0a1ff846ec271184ea4e3a921a3ccd8d478f69948b984445ee1852f272d54c58), która sfinansowała prace nad zmianą.

Wprowadzono nowe filtry blokowe. Filtry te, używane przez lekkie klienty, takich jak portfele SPV, zostały zaktualizowane w celu poprawy ich wydajności, ergonomii. Zawierają dodatkowe informacje, takie jak pełny skrypt zobowiązania biletów. Nowe filtry blokowe to wersja 2. Starsza wersja 1 filtrów jest teraz przestarzała i ma zostać usunięta w następnej wersji, więc użytkownicy powinni jak najszybciej przejść na nowe filtry. Należy pamiętać, że ma przy tym miejsce jednorazowa aktualizacja bazy danych w celu zbudowania i przechowywania nowych filtrów dla wszystkich istniejących bloków historycznych, co prawdopodobnie zajmie trochę czasu (zazwyczaj około 8 do 10 minut na dyskach twardych i 4 do 5 minut na dyskach SSD).

Infrastruktura wydobywcza dla budowania szablonów blokowych oraz dostarczania pracy górnikom została w znacznym stopniu przebudowana. Ulepszenia obejmują wsparcie dla asynchronicznego generowania szablonów tła z inteligentną obsługą propagacji głosów, lepszą obsługę reorganizacji łańcucha, niezbędnych w sytuacji, gdy aktualny szczyt nie jest w stanie uzyskać wystarczającej ilości głosów, lepszą synchronizację stanu bieżącego, prawie całkowite wyeliminowanie zużytych szablonów w przypadku otrzymania nowych bloków i głosów oraz subskrypcje do aktualizacji szablonów do strumieniowej transmisji danych. Standardowy [getwork RPC](https://github.com/decred/dcrd/blob/master/docs/json_rpc_api.mediawiki#getwork), którego górnicy PoW obecnie używają do wykonywania procesu wydobywczego, został zaktualizowany w celu wykorzystania tej nowej infrastruktury, więc istniejący górnicy PoW płynnie uzyskają większość korzyści, bez konieczności żadnych aktualizacji. Ponadto dostępne jest nowe [Notifywork RPC](https://github.com/decred/dcrd/blob/master/docs/json_rpc_api.mediawiki#notifywork), które umożliwia górnikom zarejestrowanie się do pracy dostarczanej asynchronicznie w miarę jej udostępniania za pośrednictwem WebSocketowego [powiadomienia o pracy](https://github.com/decred/dcrd/blob/master/docs/json_rpc_api.mediawiki#work). Powiadomienia te zawierają te same informacje, które dostarcza getwork wraz z dodatkowym parametrem powodu. Parametr ten pozwala górnikom na podejmowanie lepszych decyzji co do tego, kiedy powinni poinstruować maszyny, aby natychmiast odrzuciły obecny szablon lub miały możliwość zakończenia bieżącej rundy przed otrzymaniem nowego szablonu.

Górnicy są zachęcani do aktualizacji oprogramowania w celu wykorzystania nowej asynchronicznej infrastruktury powiadamiania, ponieważ jest ona bardziej wytrzymała, wydajna i szybsza niż sondowanie getwork w celu ręcznego określenia wyżej wymienionych warunków. **WAŻNE:** Górnicy, którzy nie rolują pola znacznika czasu przy wydobyciu, powinni upewnić się, że ich oprogramowanie jest zaktualizowane do rolowania znacznika czasu do najnowszego za każdym razem, gdy przekazują pracę do górnika. Pomaga to zapewnić, że znaczniki czasu bloku są tak dokładne, jak to tylko możliwe. Korzystanie z powiadomień i rolowanie znacznika czasu zostało wdrożone w [dcrpool](https://github.com/decred/dcrpool).

Walidacja skryptu transakcyjnego została prawie całkowicie przerobiona w celu znacznego zwiększenia jego szybkości i zmniejszenia liczby alokacji pamięci. Wprowadza to wymierne korzyści, w tym 20-25% szybsze początkowe przetwarzanie synchronizacji, szybsze oddawanie głosów (co pomaga zmniejszyć liczbę przegapionych głosów) i szybsze propagowanie bloków.

Automatyczne wykrywanie zewnętrznych adresów IP umożliwia teraz pełnym węzłom łatwiejsze wykrywanie innych węzłów w sieci w sposób zdecentralizowany. Zautomatyzuje to wcześniej wykonywane ręcznie czynności konfiguracyjne, takie jak ustawienie zewnętrznego adresu IP w wierszu polecenia, konfigurację zapory sieciowej i/lub routera dla połączeń przychodzących oraz przekierowanie portu na wewnętrzny adres IP uruchomionego dcrd.

Dodano obsługę protokołu Tor IPv6. Możliwe jest teraz rozwiązywanie i łączenie się z peerami IPv6 poprzez Tor oprócz istniejącej wsparcia IPv4.

**dcrwallet v1.5**

Główną cechą tego wydania jest wstępna implementacja [CoinShuffle++](https://github.com/decred/dcrwallet/pull/1541), która pozwala na zakup biletów z mieszanej transakcji CoinJoin. Ochrona prywatności poszczególnych interesariuszy jest kluczowa, ponieważ poprawia również bezpieczeństwo sieci. Początkowa wersja ma szereg ograniczeń, w szczególności brak wsparcia dla biletów VSP, brak graficznego interfejsu użytkownika oraz poleganie na centralnym serwerze do koordynacji mieszania. Kwestie te zostaną rozwiązane w przyszłych wersjach. Warto zauważyć, że w przeciwieństwie do starszych projektów CoinJoin, serwer nie jest w stanie określić tego, do którego z użytkownika należą konkretne dane wyjściowe.

Inne cechy obejmują agendę głosowania nad zmianą konsensusu w sprawie zobowiązań nagłówka bloków, możliwość [importowania](https://github.com/decred/dcrwallet/pull/1471) dowolnych rozszerzonych kluczy publicznych (ważny krok w kierunku zaprzestania ponownego używania adresów), flagę uniemożliwiającą aktualizację typu monety w portfelu, szereg pomocnych metod RPC, zwiększoną wydajność i mnóstwo poprawek błędów.

**Decrediton v1.5**

Główne cechy tego wydania to wstępna integracja z siecią Lightning Network, responsywnośc rozmiaru okien dla większości stron, zaktualizowany tryb ciemny, mnóstwo poprawek interfejsu użytkownika, poprawka [nadmiernego pobierania danych](https://github.com/decred/decrediton/issues/2166) i inne poprawki błędów.

**dcrlnd v0.2**

Zmiany z głównego zdalnego repozytorium zostały [sportowane](https://github.com/decred/dcrlnd/pull/42) aż do wersji [v0.8.0-beta](https://github.com/lightningnetwork/lnd/releases/tag/v0.8.0-beta). Łącznie 379 commitów i 90 PRów zostało scalonych. Zaowocowało to takimi funkcjami jak zobowiązania Safu, wieże obserwacyjne i faktury Hodl (_na serio, to są oficjalne określenia_). Praca po stronie Decred została ukończona po to, aby umożliwić bardziej bezproblemową integrację dcrlnd w Decreditonie.

Algorytm haszujący do obliczania hashu płatności został [przełączony](https://github.com/decred/dcrlnd/pull/46) z początkowego BLAKE-256 z powrotem na oryginalny SHA-256. Umożliwia to dokonywanie płatności międzyłańcuchowych w sieciach LN BTC/DCR/LTC. Jest to **potencjalnie niebezpieczna zmiana**. Płatności dokonywane za pośrednictwem kanałów pomiędzy węzłami działającymi w wersji v0.1 i v0.2 NIE będą działać i spowodują automatyczne wymuszone zamknięcie kanału. Ponieważ liczba węzłów jest wciąż niewielka, nie oczekuje się, że spowoduje to znaczne zakłócenia.

Działają już [zdalne portfele](https://github.com/decred/dcrlnd/pull/40); pozwalają one użytkownikom na uruchomienie dcrlnd poprzez podłączenie go do istniejącego zdalnego dcrwallet zamiast uruchamiania portfela wbudowanego w dcrlnd. Tego właśnie użyje LN w Decrediton, zamiast wymagać od użytkowników ręcznego określania danych uwierzytelniających.

Szczegóły i pliki do pobrania dla wszystkich 4 projektów można znaleźć na stronie [wydania RC1 v1.5](https://github.com/decred/decred-binaries/releases/tag/v1.5.0-rc1). Jak zawsze, należy [sprawdzić pliki binarne](https://docs.decred.org/advanced/verifying-binaries/). Jest to dodatkowa przeszkoda, ale jest to najlepszy sposób, aby upewnić się, że pliki nie zostały podmienione.

Bardzo doceniamy pomoc w testowaniu, ponieważ pozwala ona na naprawę znalezionych błędów przed końcowym wydaniem. Prosimy o zgłaszanie wszelkich problemów, które znajdziecie w kandydatach do wydania.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Implementacja algorytmu haszującego RIPEMD-160 została [zaimportowana](https://github.com/decred/dcrd/pull/1907) do repozytorium dcrd, motywowana jego deprecjacją w `x/crypto` i niewygodnym zarządzaniem zależnościami. Chociaż nie jest to zalecane do użytku w nowych aplikacjach, dcrd będzie musiał obsługiwać ripemd160 _po wsze czasy_ w celu weryfikacji historycznych transakcji i obsługi skryptów p2sh, które na nim bazują. Ogólnie rzecz biorąc, dobrym pomysłem jest zinternalizowanie całej kryptografii, na której opiera się dcrd, ponieważ aplikacje konsensusu mają _dużo bardziej_ rygorystyczne wymagania niż ich zależności, co zostało zademonstrowane przez [problemy](https://bitcoin.org/en/alert/2014-04-11-heartbleed) OpenSSL w Bitcoinie.

Po wydaniu wersji v1.5 rozpoczęły się prace nad ulepszeniami dla wersji v1.6. Szybsze [wyszukiwanie indeksów](https://github.com/decred/dcrd/pull/1969) zostało umożliwione poprzez wykorzystanie spend journala. Rozpoczęto oczyszczanie kodu, którego nie można było wykonać do czasu uruchomienia wersji 1.5. Kontynuowane są prace nad podziałem serwera RPC na własny pakiet w ramach większego planu zmierzającego do rozdzielenia komponentów. Warte odnotowania jest to, że niektóre zmiany z tej pracy są przenoszone do zdalnego repozytorium btcd.

[dcrwallet](https://github.com/decred/dcrwallet): Kod został zaktualizowany w celu wykorzystania nowych modułów z dcrwallet i najnowszych modułów z dcrd, dodano śladowy kod w celu zebrania wskaźników wydajności.

[Politeia](https://github.com/decred/politeia): Przeprojektowany front-end Politeia został uruchomiony 29 października, z wyglądem, który pasuje do reszty oprogramowania Decred i znacznie poprawionymi wrażeniami korzystania z wersji mobilnej. W tym samym czasie wdrożono również szereg ulepszeń wydajności. Jest to zwieńczenie wielu miesięcy pracy, a zatem gratulacje dla zespołu Politeia!

`politeiavoter` zostało bardziej uodpornione na [błędy sieci](https://github.com/decred/politeia/pull/1022).

Kontynuowane są prace nad funkcjonalnością DCC dla systemu zarządzania wykonawcami. System fakturowania został [rozszerzony](https://github.com/decred/politeia/pull/1023) o sposób wprowadzania godzin przepracowanych przez podwykonawców. Informacje te będą niezbędne do przypisania mocy głosu w przypadku rozstrzygania sporów w głosowaniu wszystkich wykonawców.

[dcrstakepool](https://github.com/decred/dcrstakepool): Poprawki UI, naprawione błędy, sprzątanie, które zostało wstrzymane do czasu wydania v1.2. Cały javascript wtopiony w kod został [usunięty](https://github.com/decred/dcrstakepool/pull/560). Liczne moduły zostały [zaktualizowane](https://github.com/decred/dcrstakepool/pull/554) do ich najnowszych wersji.

Kontynuowane są prace nad wdrożeniem [bezkontowego](https://github.com/decred/dcrstakepool/pull/515) zakupu biletów, które uczyni e-mail opcjonalnym, poprawi UX i utoruje drogę do wyeliminowania ponownego użycia adresu do głosowania.

[dcrpool](https://github.com/decred/dcrpool): Precyzja trudności i obliczania celów została [zwiększona](https://github.com/decred/dcrpool/pull/135). Pula została przełączona z sondowania pracy na uzyskiwanie pracy przez [powiadomienia](https://github.com/decred/dcrpool/pull/136) dzięki nowemu `notifywork` w dcrd i wykorzystanie nowego parametru `reason`. Dodano również rolowanie pola znacznika czasu. Dzięki temu dcrpool spełnia wszystkie zalecenia dotyczące pracy z dcrd v1.5 z maksymalną wydajnością.


[cspp](https://github.com/decred/cspp): Dodano możliwość zapisywania raportów z miksów w formatach JSON i CSV oraz wprowadzono poprawki błędów.

[dcrdex](https://github.com/decred/dcrdex): Specyfikacja otrzymała kilka [zmian](https://github.com/decred/dcrdex/pulls?q=is%3Apr+merged%3A2019-10-01..2019-10-31+label%3Aspec), w tym zamianę kontraktu atomic swap na P2SH i zastąpienie JSON-RPC niestandardowym protokołem wiadomości. Zbudowano nowe elementy fundamentalne: [węzeł komunikacyjny](https://github.com/decred/dcrdex/pull/33), [koordynator wymiany](https://github.com/decred/dcrdex/pull/39), [trwałe przechowywanie zamówień](https://github.com/decred/dcrdex/pull/47), [router subskrypcji księgi zamówień](https://github.com/decred/dcrdex/pull/62), [router zamówień](https://github.com/decred/dcrdex/pull/65). Dodano [uprząż testową](https://github.com/decred/dcrdex/pull/34) Simnet.

[dcrandroid](https://github.com/decred/dcrandroid): Kontynuowane prace nad nowym interfejsem użytkownika zaowocowały przebudowaną [stroną główną](https://github.com/decred/dcrandroid/pull/401) i innymi usprawnieniami w celu dostosowania aplikacji do standardowych zaleceń dotyczących projektowania aplikacji dla systemu Android. Trwają prace nad [obsługą wielu portfeli](https://github.com/raedahgroup/dcrlibwallet/pull/57). Pozwoli to użytkownikom na import klucza publicznego z Decreditona, aby mogli monitorować status swoich biletów z telefonów.

[dcrios](https://github.com/raedahgroup/dcrios): Trwają prace nad udoskonaleniami interfejsu użytkownika dla [odzyskiwania portfela z ziarna](https://github.com/raedahgroup/dcrios/pull/527), stron [widoku głównego](https://github.com/raedahgroup/dcrios/pull/526) oraz [menu nawigacyjnego](https://github.com/raedahgroup/dcrios/pull/524).

[dcrdata](https://github.com/decred/dcrdata): Przeprojektowany widok [listy bloków](https://github.com/decred/dcrdata/pull/1577), poprawa łączności i wydajności, poprawki błędów.

[docs](https://github.com/decred/dcrdocs): Dodano nową stronę wyjaśniającą [czasy produkcji bloków](https://github.com/decred/dcrdocs/pull/995), nowe [terminy słownikowe](https://github.com/decred/dcrdocs/pull/1003), drobne aktualizacje i porządki w treściach.

[devdocs](https://github.com/decred/dcrdevdocs): Dokumentacja deweloperska została przeniesiona do organizacji Decred na GitHubie. Strona nie została jeszcze oficjalnie uruchomiona, ale można ją podejrzeć pod adresem [devdocs.decred.org](https://devdocs.decred.org/). Jeżeli chciałbyś zasugerować dodanie jakichś treści, daj nam znać w dziale [issues](https://github.com/decred/dcrdevdocs/issues) lub na kanale [#documentation](https://matrix.to/#/!tfqymymiNgzSUJTHqS:decred.org)!

[decred.org](https://github.com/decred/dcrweb): Strona [Giełdy wymian](https://decred.org/exchanges/) została zaktualizowana (usunięto [Easyrabbit](https://github.com/decred/dcrweb/pull/741) oraz [portfel depozytowy Cobo](https://github.com/decred/dcrweb/pull/745), dodano [Koi Trading](https://github.com/decred/dcrweb/pull/731) OTC). Keybase zostało [dodane](https://github.com/decred/dcrweb/pull/729) do strony [Społeczność](https://decred.org/community/). Zamieściliśmy wiadomość w konsoli deweloperskiej, żeby [zrekrutować](https://github.com/decred/dcrweb/pull/743) hakerów stron internetowych. Piwik analytics zostało [usunięte](https://github.com/decred/dcrweb/pull/738) (a przedtem było samodzielnie hostowane).

Szata graficzna dla odnowionej strony internetowej jest w większości kompletna, zaś pisanie treści dla nowych podstron jest w toku.

Statystyki aktywności deweloperskiej na październik: 243 aktywne PR-y, 317 master commitów, 67 tys. dodanych i 16 tys. usuniętych linijek kodu spośród 12 repozytoriów. Wkład pochodził od 1-8 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: Enrico Bonetti Vieno ([dcrweb](https://github.com/decred/dcrweb/commits?author=ebonetti)).

Ponieważ nasz [detektor](https://github.com/degeri/decred_contributor_track) nowych współpracowników wykrywa jedynie commity, na liście zabrakło nam dwóch nowych projektantów:

- Vlad Kharlantsev (projektant z Block 42) współtworzy [dcrtimegui](https://github.com/decred/dcrtimegui/issues?q=author%3Aharlovski) i [dcrdata](https://github.com/decred/dcrdata/issues?q=author%3Aharlovski) od maja.
- Hannes Dvorjanski (projektant z EETER) współtworzy [Decrediton](https://github.com/decred/decrediton/issues?q=author%3Ahqnnes) od końca września.

Trochę późno, ale nadal serdecznie witamy na pokładzie!

Witamy z powrotem @praxis, który ponownie został [uwzględniony](https://github.com/decred/dcrweb/pull/742) na stronie [decred.org](https://decred.org/contributors/).

Statystyki społeczności:

- Użytkownicy platformy Politeia: 190 (+9)
- Obserwujący na Twitterze: 40,632 (+54)
- Subskrybenci na Reddit: 9,656 (+25)
- Użytkownicy na Matrixie: 456 (+20)
- Użytkownicy na Slacku: 6,858 (+7)
- Użytkownicy na Discordzie: 2,542 (+55), zweryfikowani z możliwością pisania postów: 358 (+33)
- Użytkownicy na Telegramie: 2,967 (-81)
- Subskrybenci na YouTube: 3,860 (+30)
- Obserwujący na Facebooku: 3,296 (+18), polubień: 3,019 (+16)
- Obserwujący na LinkedIn: 638 (+16)
- GitHub: 517 gwiazdek (+0) i 1400 forków repozytorium dcrd (+6)

## Zarządzanie

Zapłata na rzecz wykonawców za sierpień/wrzesień została dokonana 2 października i ujęta w [poprzednim wydaniu](201909.md) Journala, a zatem jest wyłączona z poniższych danych.

W październiku [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 14 970 DCR i wydał 12 539 DCR. Wykorzystując średnią dzienną stawkę DCR/USD w październiku, wynoszącą 15,59 USD, daje to 233 tys. USD w przychodach i 195 tys. USD w wydatkach. Przy średniej dziennej stawce we wrześniu wynoszącej 22,02 USD, kwota USD naliczona za pracę wykonaną w tym miesiącu wynosi 276 tys. USD. Na dzień 5 listopada saldo Skarbca wynosi 643 041 DCR (12,8 mln USD po kursie 20,00 USD).

W październiku opublikowano 5 nowych propozycji (stan na 8 listopada):

- Propozycja [DCR Comic](https://proposals.decred.org/proposals/2ef74fa5f0b558442cb85b1235c8c551a51ff5d8b8de44dead48b8b59c8fc1de), aby wyprodukować 6 kolejnych komiksów za cenę 10 800 USD została zatwierdzona z 65% poparciem i frekwencją 28%.
- Propozycja [Coffee Points](https://proposals.decred.org/proposals/1b4b72fa08792b6500ef770546c24ee751c2b0fee2975db769722524a2754829) zabiegająca o 283 tys. USD na otwarcie sieci kawiarń i zbudowanie systemu Decred Points została odrzucona z 3% poparciem i 25% udziałem głosujących.
- Propozycja [Decred: badanie zjawiska ekonomicznego i edukacja](https://proposals.decred.org/proposals/65bde4146b845e7e839d6916d4d8f642bc39c250df5379c2f1e26c4ab778ec1a) aut. @ammarooni wnosi o 2000 dolarów za pracę już wykonaną i 6000 dolarów za 3 kolejne miesiące pracy. Propozycja została zatwierdzona przy 80% poparciu i 29% udziałem głosujących.
- Propozycja [sfinansowania nagrody](https://proposals.decred.org/proposals/5a1bd4116565d107c1672799ed16cae9e92ec633c6e39d9b463b8218e66ff759) dla rozgrywek DotA 2 online prosiła o 450 USD na nagrody pieniężne i koszty administracyjne. Została ona odrzucona z 3% głosów "za" i 28% udziałem głosujących.
- Propozycja dotycząca [częściowego sfinansowania](https://proposals.decred.org/proposals/42b16d2741d58903963d8535e04017bbc3a8193391a83b305f44c082b62e3aa8)  udziału @evok3d w Kongresie Hakerów kwotą 2050 USD została porzucona. Amin zredagował propozycję z linkami do przemówienia oraz raportu i oświadczył, że nie zamierza kontynuować propozycji, dodając zamiast tego adres na darowizny.

16 października Politeia świętowała jeden rok działalności, a z tej okazji ukazały się liczne publikacje:

- Tweety ze statystykami od [@Dustorf](https://twitter.com/lefebvre_dustin/status/1184511963965079552) oraz [@BlockCommons](https://twitter.com/BlockCommons/status/1184581107578298369)
- [Raport](https://blockcommons.red/publication/politeia-at-1/) na temat danych z pierwszego roku działalności Politei napisany przez @richardred.
- [Artykuł](https://cryptobriefing.com/decred-politeia-decentralized-governance/) z wywiadu z @jy-p rozpisany w Crypto Briefing
- [Wideo](https://www.youtube.com/watch?v=58gTCW7DTMg) recenzja aut. @Exitus
- [Retrospektywa](https://blockcommons.red/post/year-of-politeia/) od @richardred

Przeprojektowana Politeia trafiła do odbiorców 29 października, dostosowując swój wygląd do innych projektów ze stajni Decred i wprowadzając szereg dodatkowych ulepszeń w zakresie wydajności, o czym @lukebp opublikował [tweeta](https://twitter.com/lukebp_/status/1189219953855082497), wspominając też, że Politeia mogłaby skorzystać z usług jeszcze jednego utalentowanego programisty-frontendowca.

@degeri podał [aktualizację](https://bounty.decred.org/2019/10/status-update/) na temat programu nagród. Od lipca rozpatrzono 16 nowych raportów, z których 1 kwalifikował się do wypłaty - problem w kwestii [bezpieczeństwa](https://github.com/decred/dcrdata/pull/1563) w dcrdata (obecnie już rozwiązany).

Repozytorium [propozycji (proposals)](https://github.com/decredcommunity/proposals) zostało uruchomione w sierpniu z generalnym założeniem, aby stać się miejscem, gdzie interesariusze będą mogli szybko znaleźć wszystkie ważne informacje na temat propozycji. Zebrano tam wstępne dane dotyczące wniosków [DEX](https://github.com/decredcommunity/proposals/tree/master/dex) i [animatorów rynku](https://github.com/decredcommunity/proposals/tree/master/market-makers), w tym indeksy ważnych dokumentów i dyskusji oraz analizy tych wniosków. W październiku zakres repozytorium został rozszerzony tak, aby objąć nim również wykazy zobowiązań i aktualizacje postępów w pracach nad zatwierdzonymi wnioskami. Pierwsza partia indeksów i aktualizacji została dodana dla programów [Open Source Research](https://github.com/decredcommunity/proposals/tree/master/research-richardred), [Ditto PR](https://github.com/decredcommunity/proposals/tree/master/pr-ditto) i [programu bug bounty](https://github.com/decredcommunity/proposals/tree/master/bug-bounty-program), z następnymi wkrótce. Nadrzędnym celem istnienia repozytorium jest poprawa raportowania i nadzoru.

W repozytorium [wytycznych (guideline)](https://github.com/decredcommunity/guidelines) rozpoczęto zbieranie dokumentów przewodnich od wielu współpracowników Decred. Teraz zostało ono przeniesione pod organizację Decred na GitHubie, gdzie mieści się przewodnik dla organizatorów społeczności (Community Organizer Playbook).

Więcej szczegółowych informacji na temat zarządzania można znaleźć w [wydaniu 23](https://www.blockcommons.red/politeia-digest/issue023/) i [wydaniu 24](https://www.blockcommons.red/politeia-digest/issue024/) naszego Politeia Digest.

## Sieć

Hashrate: październikowy hashrate na początku miesiąca wyniósł ~446 Ph/s, a zamknął miesiąc w ok. ~452 Ph/s, zaliczając niż w ok. 339 Ph/s oraz szczyt w wys. 686 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 2 listopada wyglądała następująco: UUPool 19%, Poolin 15%, F2Pool 5,6%%, lab.antpool.com 5%, BTC.com 2,4%, Luxor 1,95%, Coinmine 0,10%, BeePool 0,10%, suprnova 0,01% i pozostałe 50% za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

Warto zauważyć, że w migawce danych nt. mocy obliczeniowej sieci na 2 listopada, odsetek "innych" (nieznanych) źródeł osiągnął 50%, w porównaniu z 30% z dnia 2 października.

Na dzień 8 listopada, zmiana mocy obliczeniowej w ciągu ostatnich 30 dni na [dcrdata](https://explorer.dcrdata.org/) wynosi -24%. Między 9-25 października średnia mocy obliczeniowej spadła z ~500 do ~400 Ph/s, a trudności z ~38B do ~29B. Spadek ten skorelowany był ze spadkiem ceny DCR/USD poniżej 16,5 USD do 13 USD.

Staking: średnia cena biletu z okresu 30 dni wynosiła 132,3 DCR (+3,6) za danymi z dcrstats.com. Cena wahała się między 120,8-142,3 DCR. Zablokowana kwota wynosiła 5,22-5,38 mln DCR, co odpowiadało 49,59-50,97% dostępnej podaży.

W okresie 18-19 października, dzięki nowym wykresom, odnotowano [gwałtowny wzrost](https://explorer.dcrdata.org/charts?chart=missed-votes&zoom=jo8rgw2w-k2qdkju0&bin=window&axis=time) przegapionych biletów. Brak informacji o przyczynie tego zjawiska.

Węzły: Przez [październik](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1569888000000&to=1572566400000) było około 146 węzłów nasłuchujących i 402 węzły ogółem za danymi z dcr.farm. Bazując na średnich danych odn. ilości węzłów, około 76% z nich operowało na dcrd v1.4.0, 7,5% oparte było na wersji v1.5.0, a 0,7% to v.1.6.0 (pre)developerskie. 9,4% węzłów działało na dcrwallet v1.4 w trybie SPV.

Na dzień 8 listopada, około 17% głosujących PoS sygnalizuje, że zaktualizowało swoje oprogramowanie i jest gotowych głosować nad zmianą reguł konsensusu za danymi z [dcrdata](https://explorer.dcrdata.org/agendas). Biorąc pod uwagę fakt, że nie było jeszcze ostatecznej wersji 1.5, pokazuje to, że wielu wyborców dba o to, aby zainstalować kandydatów do wydania lub zbudować ich z kodu źródłowego.

Według [tweeta](https://twitter.com/decredproject/status/1183770504580206593) z 14 października, około 15% biletów wykorzystuje transakcje prywatne, tworząc zestaw anonimowości 7,5% wszystkich DCR w obiegu.

## Nawiązywanie kontaktów

W ramach nawiązywanie kontaktów nadal prowadzono działania w związku z niedawnym wydaniem funkcji prywatności, w tym [odcinek](https://www.youtube.com/watch?v=iWdA1C-SHSk) Decred Assembly z udziałem @jrick, lecz główny nacisk powrócił na tematy związane z tematami podstawowymi, takimi jak zarządzanie, DAO i projekty w przygotowaniu. Opublikowano [podręcznik organizatora społeczności](https://github.com/decredcommunity/guidelines/blob/master/community-organizer-playbook.md) w celu podzielenia się najlepszymi praktykami z członkami społeczności, który zawiera przewodnik po wydarzeniach zainicjowany przez @eSizeDave i @zohand z Australii. Narzędzia te zostały zaprojektowane, aby pomóc członkom społeczności w budowaniu ekosystemu użytkowników, programistów, partnerów i mediów na całym świecie. Jeśli widzisz sposoby na jego ulepszenie, podziel się z nami swoimi przemyśleniami [tutaj](https://github.com/decredcommunity/guidelines/pull/5).

Decred in Depth wydał dwa odcinki w październiku: z udziałem @zubair na temat [bezpieczeństwa DCR](https://www.youtube.com/watch?v=FX2ZncHIAd4) i Alexem Feinbergiem na temat [perspektywy OKCoin](https://www.youtube.com/watch?v=UBRjkjbmYDc). Członkowie społeczności z całego ekosystemu wnieśli ogromny wkład w działania informacyjne i edukacyjne, zwłaszcza [@BlackBearXVII](https://medium.com/@imagnusholdings), który publikuje dziesięcioczęściową serię Medium o Decred; @permabullnino, który opublikował [Decred On-Chain: rzut oka na nagrody blokowe](https://medium.com/@permabullnino/decred-on-chain-a-look-at-block-subsidies-6f5180932c9b); @Checkmate, który wydał szeroką gamę badań i wątków na Twitterze; @Exitus, który nagrał [wideo](https://twitter.com/coveryfire7777/status/118606075335076528130) o pierwszym roku istnienia Politei; oraz @richardred, który wydał [wątek tweetowy](https://twitter.com/BlockCommons/status/1184581107578298369) z danymi dotyczącymi pierwszego roku istnienia Politei, a także [Produkcja równorzędna we wspólnej sprawie (Peer Production on the Crypto Commons)](https://twitter.com/RichardRed0x/status/1190315513043472385), bezpłatną książkę, nad którą pracuje od początku 2019 roku.

Wraz z odświeżoną stroną internetową, ożywieniem działalności w mediach społecznościowych oraz ciągłym napływem badań i publikacji, Decred jest na dobrej drodze do zlikwidowania luki w asymetrii informacyjnej.

Październikowe osiągnięcia Ditto:

- Zdobyliśmy 13 relacji w mediach, wliczając w to:

  - Wywiad z Jake'iem na kanale [YouTube](https://www.youtube.com/watch?v=dF7hkxzggvk) CryptoWendyO na temat DAO i Decred.
  - Artykuł w [Crypto Slate](https://cryptoslate.com/data-shows-autonomous-coin-decred-has-a-power-law-relationship-with-bitcoin/) zatytułowany "Dane wskazują, że niezależna waluta Decred ma proporcjonalny związek z Bitcoinem".
  - Dedykowany artykuł w [Crypto Briefing](https://cryptobriefing.com/decred-politeia-decentralized-governance/) z okazji pierwszej rocznicy działania Politei.
  - Komentarz @jz na temat Bitcoin jako środka przechowania wartości w [CCN](https://www.ccn.com/bitcoin-best-store-of-value-over-last-decade/).
  - Komentarz Jake'a na temat Libry w czterech źródłach: [AMB Crypto](https://eng.ambcrypto.com/facebooks-libra-project-loses-support-from-visa-mastercard-ebay-stripe/), [Mobile Payments Today](https://www.mobilepaymentstoday.com/articles/zuckerberg-faces-grilling-as-skeptical-house-panel-hears-case-for-libra-digital-currency/), [Daily Hodl](https://dailyhodl.com/2019/10/12/facebooks-david-marcus-cites-intense-pressure-as-ebay-visa-mastercard-stripe-paypal-abandon-crypto-project/amp/) oraz [Crowdfund Insider](https://www.crowdfundinsider.com/2019/10/152831-terrifying-the-idea-that-global-centralized-monopolies-like-facebook-would-also-control-money/).
  - Wywiad z Zubair w [Bloxlive](https://bloxlive.tv/video/MTc0Mg==/zubair-zia-explains-the-decred-digital-currency-and-its-origins).
  - Wywiad z Jake'iem w podcaście [The Crypto Conversation Podcast](https://bravenewcoin.com/insights/podcasts/decreds-privacy-flow-building-a-better-bitcoin-and-the-legend-of-satoshi) serwisu Brave New Coin - stanowiący jeden z najlepszych dotychczasowych występów Jake'a.
  - Wywiad z Luke'iem w podcaście [The Daily Chain](https://anchor.fm/thedailychain/episodes/Decred---a-Bitcoin-Hedge-e5rhmt), w którym elokwentnie wyjaśnia problem hard forków w Bitcoinie.
  - Artykuł w [Crypto Briefing](https://cryptobriefing.com/eos-governance-ico-settlement/), w którym Jake omawia zarządzanie EOS i frekwencję wyborczą w Decred.

- Zapewniliśmy wsparcie w zakresie relacji z mediami dla obecności Decred na WebSummit: stworzono najwyższej klasy książkę informacyjną dla mediów, zidentyfikowano reporterów, z którymi przedstawiciele Decred mieli się spotkać, itp.

- Zaplanowaliśmy cztery wywiady z mediami z Akinem na Światowej Konferencji Krypto, w tym z Anthonym "Pomp" Pompliano, Nicole Grinstead dla Crypto TV News Show, Jimmy'm Peraltą dla programu Digit-All i Gregiem Wilsonem z Legacy Research.

- Rozpoczęliśmy rozmowy z mainstreamowymi dziennikarzami na temat koncepcji DAO i przyszłości (anonimowego) miejsca pracy.

## Eventy

Na których byliśmy:

- 18 września - [Bitcoin & Blockchains Common Meetup](https://www.facebook.com/events/959839374354073/) - Oaxaca, Meksyk. Był to praktyczny warsztat zorganizowany przez @evok3d, w którym wzięło udział 10 osób. Tematyka warsztatów obejmowała bezpieczeństwo, zarządzanie, system propozycji i zastosowania technologii blockchain. ([zdjęcia](https://twitter.com/Decred_ES/status/1174803011610259456), _pominięto w wydaniu wrześniowym_)
- 4-5 października - [Konferencja nt. Blockchaina i zasobów cyfrowych](https://www.eventbrite.com/e/abuja-blockchain-digital-assets-conference-2019-tickets-67571336687) - Abudża, Nigeria. Zespół Grupy Raedah prowadził stoisko Decred i odpowiadał na pytania. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191004-blockchain-digital-asset-conference-abuja-nigeria.md), zdjęcia: [1](https://twitter.com/beansgum/status/1180117854240288768), [2](https://twitter.com/raedahgroup/status/1180930491244937216))
- 4-6 października - [Kongres Hakerów](https://opt-out.hcpp.cz/) - Praga, Republika Czeska. @evok3d przedstawił zarządzanie w Decred, model finansowania i prywatność jako część swojego [wykładu](https://www.youtube.com/watch?v=fmgNbLGCO5U) (od [23:53](https://www.youtube.com/watch?v=fmgNbLGCO5U&t=23m53s)), a także opowiedział o Decred podczas [wywiadu](https://www.youtube.com/watch?v=dq2SGpI5-Gw) dla World Crypto Network (od [22:37](https://www.youtube.com/watch?v=dq2SGpI5-Gw&t=22m37s)). Pełny raport został opublikowany na [Medium](https://medium.com/@evok3d/decred-report-hackers-congress-paralelni-polis-hcpp19-bd8e634f93de) i [powielony](https://github.com/decredcommunity/events/blob/master/reports/20191004-hackers-congress-prague-czech.md) w repozytorium wydarzeń. Przeczytaj również powiązaną [propozycję](https://proposals.decred.org/proposals/42b16d2741d58903963d8535e04017bbc3a8193391a83b305f44c082b62e3aa8) na Politei.
- 8 października - [Tech Tuesday](https://www.meetup.com/PermanentBeta/events/qtcrhryznblb/) - Utrecht, Holandia. Była to część większego spotkania, które koncentrowało się na technologii w szerszym znaczeniu (inteligentne miasta, IoT, biohacking, itp.). @evok3d znał organizatorów, więc podczas spotkania poprowadził ścieżkę poświęconą blockchainowi. Pojawiły się 4 zainteresowane osoby (w tym jedna studentka która była pod wrażeniem po warsztatach). @Haon zaprezentował krótkie demo portfela Decred.
- 10 października - [Devcon 5](https://devcon.org/) - Osaka, Japonia. @joshuam opowiadał o zarządzaniu w Decred. ([zdjęcie](https://twitter.com/kate_sills/status/1182474689995653120))
- 13 października - [O-link](http://odaily001.huodongxing.com/event/2511153700300) - Xi'an, Chiny. @Dominic wziął udział w panelu i mówił na temat prywatności w Decred. ([zdjęcie](https://twitter.com/wanbihou/status/1184183795940880384))
- 16 października - [DAOfest Meetup](https://thenextweb.com/hardfork-summit/events/daofest-amsterdam-meetup) - Amsterdam, Holandia. @evok3d [opowiedział](https://www.youtube.com/watch?v=Jt_2vk-hf4o&t=19m38s) o modelu zarządzania Decred a wraz z @Haon przyłączył się do panelu dyskusyjnego na temat DAO. Po głównym wydarzeniu odbyła się sesja networkingu. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191016-daofest-amsterdam-netherlands.md))
- 17 października - Uniwersytet Technologiczny - Morelia, Meksyk. @luisantoniocrag i @francov_ wprowadzili ponad 100 osób (głównie studentów i paru nauczycieli) w świat technologii blockchain, kryptowalut, oraz Decred. Ludzie usłyszeli o nim po raz pierwszy i temat bardzo ich zaciekawił. Wśród rzeczy, które przyciągnęły ich uwagę, było to, że "nie ma znaczenia stopień naukowy, wiek, narodowość czy cokolwiek innego, aby móc pracować i robić wielkie rzeczy". Publiczność poprosiła o dodatkowe warsztaty. Po rozmowach zespół został zaproszony na Talent Nights, ważne wydarzenie dla przedsiębiorców. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191017-decred-meetup-morelia-mexico.md), [zdjęcia](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$1571354151416323TNRDg:matrix.org)).
- 18 października - [Crypto Friday](https://www.meetup.com/Crypto010-Rotterdam-Virtual-Currency-Blockchain-Meetup/events/264476624/) - Rotterdam, Holandia. Około 20-30 osób wzięło w nim udział, @evok3d opowiedział o DAO i Politei. Relacja audio wkrótce zostanie udostępniona. ([zdjęcia](https://mega.nz/#!R2pgAKSB!bHjwi3t3N687xNpec4YDTnl0pBhJcMJ1HFtdDk0ou28)))
- 20 października - Stowarzyszenie Wafaa - Casablanca, Maroko. Podczas wrześniowego [spotkania](https://github.com/decredcommunity/events/blob/master/reports/20190921-decred-meetup-casablanca-morocco.md) Decred w Casablance @arij została poproszona o zaprezentowanie technologii blockchain w Stowarzyszeniu Wafaa. W spotkaniu wzięło udział około 20 osób, głównie studentów. @arij opowiadała o podstawach technologii blockchain i systemach konsensusu przez pełne 2 godziny. Ludzie nie mieli wcześniej styczności z tą technologią i poprosili o kolejną prezentację, aby dowiedzieć się więcej. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191020-wafaa-casablanca-morocco.md))
- 23 października - World Bank Innovation Lab - Waszyngton D.C., USA. @akinsawyerr przeprowadził prezentację przeglądową Decred dla pracowników Laboratorium Innowacji Banku Światowego. Rozmowa dotyczyła również sposobów, w jakie Bank Światowy mógłby wykorzystać infrastrukturę Decred w niektórych projektach koncepcyjnych.
- 24 października - [Noc Byków](https://www.eventbrite.com/e/bullish-night-at-bull-and-bear-academy-tickets-77415737555) - Mexico City, Meksyk. @elian rozmawiał ze społecznością traderów w Meksyku i Ameryce łacińskiej i przedstawił krótki opis tego, o co chodzi w Decred. Decred był sponsorem spotkania. ([zdjęcia](https://twitter.com/Decred_ES/status/1187534463569289216))
- 24 października - [Warsztaty kryptowalutowe](https://twitter.com/Decred_ES/status/1187206051000655872) - Morelia, Meksyk. @francov_ i @luisantoniocrag zorganizowali 4-godzinne warsztaty na Uniwersytecie Technologicznym w Morelii, gdzie pokazali, jak korzystać z portfela Decred. W przeciwieństwie do wykładu z 17 października warsztat był znacznie bardziej szczegółowy i wzięło w nim udział 15 studentów, wszyscy dokładnie zrozumieli działanie blockchaina i Decred, nie tylko od strony technicznej, ale również finansowej. ([zdjęcia](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$157202936428052qbfho:matrix.org))
- 29 października - [Warsztaty zarządzania Decred](https://www.meetup.com/Blockchain-innovation-Singapore/events/265738541/) - Singapur. Po raz pierwszy w Singapurze, @joshuam i @zohand zaprezentowali Decred na kameralnym spotkaniu w WeWork. Było to głębokie zanurzenie się w tematykę zarządzania blockchainem i stabilnego pieniądza, model zarządzania Decred i ogólną konstrukcję projektu. Tłum był dobrze zaznajomiony z kryptografią, treść była bardzo pouczająca i przemieniła sesję pytań i odpowiedzi w godzinną, głęboką dyskusję. Poproszono w kolejne spotkanie. ([raport](https://github.com/decredcommunity/events/blob/master/reports/20191029-decred-governance-workshop-singapore.md), [zdjęcia](https://twitter.com/GuangGuang168/status/1189381286458089473))
- 29 października - [Meetup Decred](https://www.eventbrite.com/e/que-hace-a-decred-una-criptomoneda-diferente-primer-meetup-oficial-tickets-78464211569) - Bogota, Kolumbia. @elian i @victorarubin zaprezentowali ogólny przegląd projektu od jego cypherpunkowych początków do hybrydowego konsensusu, poprzez platformę Politeia, prywatność, po omówienie jego globalnego zespołu i przyszłości. W wydarzeniu wzięło udział około 60 osób w każdym wieku od 20 do 50 lat, głównie entuzjaści krypto. Z tej grupy około 10 w przeszłości wydobywało DCR przy użyciu kart graficznych. Podczas sesji pytań i odpowiedzi, zespół otrzymał kilka dobrych pytań dotyczących centralizacji zarządzania Decred, roli układów ASIC, planów adopcyjnych w Ameryce Łacińskiej oraz tego, kiedy DCR będzie można wykorzystać do zakupu piwa. Gospodarzami wydarzenia byli Blockchain Academy Colombia, Panda Exchange, [Cointelegraph en Español](https://es.cointelegraph.com/news/decred-starts-series-of-meetings-in-colombia) oraz [Diario Bitcoin](https://www.diariobitcoin.com/index.php/2019/10/28/colombia-blockchain-academy-realizara-primer-meetup-sobre-decred-en-bogota/). Dwa ostatnie portale opisały wydarzenie na swoich stronach internetowych. (zdjęcia: [1](https://twitter.com/Decred_ES/status/1188496680133500934), [2](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$157244810128246sZnzI:decred.org))
- 29 października - [Światowa Konferencja Krypto](https://worldcryptocon.com/) - Las Vegas, USA. @akinsawyerr reprezentował Decred na panelu "Zarządzanie w praktyce" i wygłosił prezentację "Zarządzanie wspólnymi zasobami krypto", w której nakreślił proces zarządzania Decred i podzielił się spostrzeżeniami zaczerpniętymi z rocznych danych Politei. Akin udzielił również kilku wywiadów i spotkań zorganizowanych przez Ditto.

Na których będziemy:

- 15-16 listopada - [CriptoBlock](https://criptoblock.com.br/) - São Paulo, Brazylia. Dwie poprzednie edycje były małe i Decred nie brał w nich udziału, ale tym razem organizatorzy oczekują ~1000 uczestników. Decred będzie brązowym sponsorem wydarzenia, @Rhama i @girino zaprezentują podstawy Decred.
- 16 listopada - [BitConf](https://www.bitconf.com.br/portal/) - São Paulo, Brazylia. Jedno z największych wydarzeń branży krypto w Ameryce Łacińskiej. Planowane są około 3 wykłady związane z tematyką Decred.
- 21 listopada - [Africa Fintech Summit](https://africafintechsummit.com/addis/) - Addis Abeba, Etiopia. @akinsawyerr wystąpi na panelu poświęconym blockchainowi.
- 21 listopada - Decred Meetup - Berlin, Niemcy. Odbędzie się wprowadzenie do funkcji prywatności w Decred i porównanie jej z innymi rozwiązaniami. Meetup prowadzony będzie przez BlueYard.

Pełne raporty dotyczące wielu przeszłych eventów zgłoszonych w poprzednich wydaniach zostały dodane do repozytorium wydarzeń: [Konferencja technologiczna UMSA](https://github.com/decredcommunity/events/blob/master/reports/20190611-bolivia-blockchain-community-la-paz-bolivia.md) + Mind Blockchain Meetup w Boliwii; [Blockchain Summit Latam](https://github.com/decredcommunity/events/blob/master/reports/20190704-blockchain-summit-latam-mexico-city-mexico.md) w Meksyku; [Blockchain Bootcamp](https://github.com/decredcommunity/events/blob/master/reports/20190828-blockchain-bootcamp-melbourne-australia.md) w Australii; [La Conexión + Crypto Fest](https://github.com/decredcommunity/events/blob/master/reports/20190925-la-conexion-buenos-aires-argentina.md) w Argentynie; [Decred Meetup](https://github.com/decredcommunity/events/blob/master/reports/20190921-decred-meetup-casablanca-morocco.md) w Maroku.

Dodano około 11 nowych raportów, co daje w sumie 30. Przyczyniło się to do ulepszenia szablonu raportu i [przewodnika składania raportów](https://github.com/decredcommunity/events/wiki/Submit-Event-Report). Dziękujemy wszystkim za dzielenie się i pomoc w gromadzeniu wiedzy.

MeetUp.com [testuje](https://withoutbullshit.com/blog/to-meetup-if-youre-going-to-change-your-prices-be-clear-about-it) nowe metody zdobywania zysku. Niewielka liczba wybranych użytkowników zapłaci 2$, gdy zarezerwują miejsce na imprezie. Na razie organizatorzy mogą [zrezygnować](https://www.meetup.com/lp/payment-test-20191016) z brania udziału w testach.

## Media

W tym miesiącu ukazały się dwie nowe strony internetowe, które powstały w ramach programu [Decred Open Source Research](https://proposals.decred.org/proposals/67de0e901143400ae2f247391c4d5028719ffea8308fbc5854745ad859fb993f).

[Peer Production on the Crypto Commons](https://www.cryptocommons.cc/) jest darmową książką autorstwa @richardred. Rozważa ona, w jaki sposób wiele różnych bytów (górnicy, programiści, traderzy, użytkownicy) współpracuje ze sobą, aby tworzyć blockchain i nadać mu wartość. Rozpatruje również blockchainy pod kątem bycia wspólnym zasobem zbudowanym przy użyciu oprogramowania typu open source i płynące z tego szersze konsekwencje.

[BlockCommons.red](https://www.blockcommons.red/) to strona, na której znajdują się materiały badawcze i edukacyjne na temat "wspólnych kryptozasobów", w tym publikacje [Pi Research](https://www.blockcommons.red/#reports) i [Crypto Governance Research](https://www.blockcommons.red/crypto-governance-research/overviews/). [Politeia Digest](https://www.blockcommons.red/politeia-digest/) również się tam przeniosła (chociaż nadal będzie publikowana na Medium i GitHub).

Repozytorium [textassets](https://github.com/decredcommunity/textassets) zostało stworzone w celu zbierania fragmentów tekstu z różnych stron internetowych i platform mediów społecznościowych. Posiadanie wszystkich tekstów w jednym miejscu pozwala na szybkie odnalezienie nieaktualnych tekstów za pomocą prostego wyszukiwania tekstu. Pozwala również na wykorzystanie funkcji GitHub do dyskusji i współpracy nad przyszłymi zmianami przed ich wdrożeniem (najnowszym przykładem jest [aktualizacja](https://github.com/decredcommunity/textassets/pull/1) paska bocznego Reddit).

Wybrane artykuły:

  - Delphi Digital [opublikowało](https://twitter.com/Delphi_Digital/status/1181228136274518016) głęboką analizę Decred dla swoich abonentów instytucjonalnych (niedostępne publicznie).
  - Decred - Kandydat alternatywny, aut. @ammarooni ([medium](https://medium.com/@Ammarooni/decred-an-alternative-contender-a3547a014745)).
  - Decred, śladem za Bitcoinem, aut. @Checkmate ([medium](https://medium.com/@_Checkmatey_/decred-following-in-bitcoins-footsteps-f8d0e0bbaff5)) - jako część jego [propozycji](https://proposals.decred.org/proposals/78b50f218106f5de40f9bd7f604b048da168f2afbec32c8662722b70d62e4d36).
  - Dane wskazują, że niezależna waluta Decred ma proporcjonalny związek z Bitcoinem ([cryptoslate](https://cryptoslate.com/data-shows-autonomous-coin-decred-has-a-power-law-relationship-with-bitcoin/)).
  - @BlackBearXVII jest w trakcie [wydawania](https://twitter.com/BarnardTheBear/status/1185200240770670596) 10-częściowej serii na Medium (Decred X), jedna część co 3 dni. W październiku ukazały się:
    - [Część I - Narracja](https://medium.com/@imagnusholdings/decred-x-part-i-narrative-41f3e08599be)
    - [Część II - Talia kart](https://medium.com/@imagnusholdings/decred-x-part-ii-deck-of-cards-33d488751f16)
    - [Część III - Technologia](https://medium.com/@imagnusholdings/decred-x-part-iii-tech-6f1ca4546108)
    - [Część IV - Kod](https://medium.com/@imagnusholdings/decred-x-part-iv-code-c04e71c29ca4)
    - [Część V - Własność](https://medium.com/@imagnusholdings/decred-x-part-v-property-8b1a5570b924)

- Decred On-Chain: Rzutem oka na nagrody za wydobycie bloków, aut. @permabullnino ([medium](https://medium.com/@permabullnino/decred-on-chain-a-look-at-block-subsidies-6f5180932c9b)) - jako część jego [propozycji](https://proposals.decred.org/proposals/f0d1bd7447182328b44c691de88cb660b63df17f1f3a94990af19acea57c09bb).
- Decred: Stabilny środek przechowania wartości, aut. @Haon ([medium](https://medium.com/coinmonks/decred-4cb7eb66db14)) - rozpowszechniony również wśród subskrybentów Coinmonks oraz na [Twitterze](https://twitter.com/coinmonks/status/1186294858903736323).
- Rok działalności Politei projektu Decred w liczbach i wykresach, aut. @richardred ([blockcommons.red](https://www.blockcommons.red/publication/politeia-at-1/)).
- Politeia: Lekcje wyciągnięte z roku zdecentralizowanego zarządzania aut. Darrena Kleine'a ([cryptobriefing](https://cryptobriefing.com/decred-politeia-decentralized-governance/)) - warto wejść choćby ze względu na samą ilustrację!
- Pierwszy rok Politei projektu Decred, aut. @richardred ([blockcommons.red](https://www.blockcommons.red/post/year-of-politeia/))


Tłumaczenia:

- Decred Journal z września 2019 przetłumaczony został na jęz. arabski (@arij), chiński (@Dominic i spółka), polski (@kozel) i hiszpański (@francov\_ and @luisantoniocrag). Dziękujemy pięknie!

Wideo:

- Jeden rok Politei - recenzja, aut. @Exitus ([youtube](https://www.youtube.com/watch?v=58gTCW7DTMg))
- @jy-p wygłasza prezentację na temat Decred i prywatności na spotkaniu w Los Angeles, którego gospodarzem było Blockhead Capital ([youtube](https://www.youtube.com/watch?v=JNPPMwr9TU8)).
- Wywiad z @jy-p dla BlockTV na temat Libry i bardzo odmiennego podejścia Decred do zarządzania. ([BlockTV](https://blocktv.com/watch/2019-10-30/5db9ab4487a7e-resolving-corporate-governance-in-cryptocurrency))
- Niefortunnie zatytułowany, ale naszpikowany faktami, bardzo pouczający 10-minutowy film o Decred od Ready Set Crypto ([youtube](https://www.youtube.com/watch?v=DtzDBnenYYY)).
- Czym jest DAO? Wywiad z @jy-p w programie CryptoWendyO ([youtube](https://www.youtube.com/watch?v=dF7hkxzggvk))
- @zubair przedstawia Decred i jego początki publiczności bloxlive ([bloxlive.tv](https://bloxlive.tv/video/MTc0Mg==/zubair-zia-explains-the-decred-digital-currency-and-its-origins)).
- Decred Assembly - Głęboka analiza - Prywatność, z udziałem @jrick ([youtube](https://www.youtube.com/watch?v=iWdA1C-SHSk))
- Próba wygenerowania muzyki za pomocą blockchainu Decred, aut. @pablito ([youtube](https://www.youtube.com/watch?v=BzTCwsmnPJ8))

Audio:

- Decred in Depth, odc. 9 z @zubair - Zubair mówi o bezpieczeństwie blockchainów, jak działa PoW, ataki większościowe, omawia kwestie PoS i jak Decred wykorzystuje mocne strony PoW i PoS w celu zwiększenia bezpieczeństwa. ([youtube](https://www.youtube.com/watch?v=FX2ZncHIAd4), [soundcloud](https://soundcloud.com/decredindepth/ep-9-zubair-zia-security-dcr-spend))
- Decred in Depth, odc. 10 z Alexem Feinbergiem z OKCoin - Alex opowiada o swoim doświadczeniu i początkach, zainteresowaniu blockchainem, słabościach walut fiat, programie "Wspólnie budujmy Bitcoina", zdecentralizowanych giełdach wymian, oraz o tym, jak OKCoin postrzega swoją rolę w przestrzeni krypto. ([youtube](https://www.youtube.com/watch?v=UBRjkjbmYDc), [soundcloud](https://soundcloud.com/decredindepth/ep-10-alex-feinberg-blockchain-exchange-process))
- Decred in Depth, odc. 11 z [@liz_bagot](https://twitter.com/liz_bagot/status/1190279034132815872) z Ditto PR, która mówi o PR w krypto, pracy Ditto nad Decred, dlaczego Bitcoin nie potrzebuje PRu, ale inne projekty tak, i dlaczego naganiacze mają zły wpływ na długoterminowy, zrównoważony rozwój. ([soundcloud](https://soundcloud.com/decredindepth/ep-11-liz-bagot-pr-marketing))
- Crypto Conversation, odc. 11 - @jy-p opowiada o prywatności w Decred i historii powstania projektu, interakcjach z pseudoanonimowym @tacotime i @\_ingsoc oraz spekulacjach na temat ich intencji. ([bravenewcoin.com](https://bravenewcoin.com/insights/podcasts/decreds-privacy-flow-building-a-better-bitcoin-and-the-legend-of-satoshi))
- Podcast The Daily Chain - Decred - zabezpieczenie dla Bitcoina - @lukebp mówi o Decred jako o Bitcoinie ulepszonym o zarządzanie koordynację, a także o silnym zespole deweloperskim i kulturze open source, które zachęciły go do rozpoczęcia pracy nad projektem. ([anchor.fm](https://anchor.fm/thedailychain/episodes/Decred---a-Bitcoin-Hedge-e5rhmt))


## Dyskusje społeczności

Nowinki z platform komunikacyjnych:

- Nowy styl Reddit [wstrzykuje](https://archive.today/3HoCx) "promowane", nigdy niepublikowane na naszym subreddicie posty bezpośrednio na naszą listę, kradnąc około 2,5x pionowej przestrzeni zajmowanej przez zwykły post.
- Pasek boczny Reddit został zaktualizowany poprzez dodanie nowego repozytorium [textassets](https://github.com/decredcommunity/textassets/pull/1) i przy użyciu najnowszej wersji [przekazu medialnego](https://github.com/decredcommunity/pr/blob/release/foundational-messaging.md). Być może będziesz musiał skorzystać z [old.reddit.com](https://old.reddit.com/r/decred/) aby go zobaczyć.
- Dodano nowe aliasy czatu, aby zredukować klepanie w klawiaturę i lepiej odzwierciedlać zawartość kanału: #events (było #event\_planning), #media (było #social\_media) i #writers (było #writers\_room).

Wybrane wątki z Reddita:

- Rozważna [dyskusja](https://www.reddit.com/r/decred/comments/dku88o/what_does_decreds_governance_model_incentivize/) pomiędzy @bee i @oiezz na temat zachęt związanych z zarządzaniem Decred.
- [Post](https://reddit.com/r/decred/comments/dgycc3/long_term_decred_believer_and_investor_any/) o dużym spadku cen przyciągnął 40 komentarzy.
- [Post](https://old.reddit.com/r/decred/comments/doinau/concerning_zksnarks/) omawiający możliwość wprowadzenia zk-SNARKS w Decred.
- [Post](https://reddit.com/r/decred/comments/dmaza0/does_decred_have_bounties_for_github_issues/) z pytaniem, czy Decred oferuje nagrody za kwestie/problemy na GitHub, zebrał 35 komentarzy i wywołał dogłębną dyskusję na temat podejścia open source projektu i potrzeby zaangażowanych współpracowników ze skórą w grze, jeśli chodzi o podstawowy rozwój. Z jakiegoś powodu ten post otrzymał tylko 6 punktów.
- [Post](https://reddit.com/r/decred/comments/dhrq4i/why_tickets_be_so_expensive/) z pytaniem, dlaczego bilety są tak drogie. Otrzymał 22 komentarze.

Wybrane dyskusje z Twittera:

- Aktualizacja odnośnie do korzystania z [funkcji prywatności](https://twitter.com/decredproject/status/1183770504580206593): ~15% zakupionych biletów korzysta z nowej funkcji.
- @DCRComic publikuje na Twitterze komiksy o [zgłaszaniu propozycji](https://twitter.com/DCRComic/status/1181647636492963844) i [górnictwie](https://twitter.com/DCRComic/status/1184471574784741376).
- Miesięczny [update](https://twitter.com/DCRtheSOV/status/1188943254223372289) @DCRtheSOV na temat Politei.
- @lukebp [tweetuje](https://twitter.com/lukebp_/status/1189219953855082497) o wdrażaniu przeprojektowania Politei.
- @akinsawyerr [tweetuje](https://twitter.com/AkinSawyerr/status/1186718327219130368) o redukcji kosztów transakcyjnych jako historii postępu ludzkości.

## Rynki

W październiku kurs wymiany Decred wahał się pomiędzy 12,91-17,59 USD / BTC 0,0015-0,0021. Średni dzienny kurs wynosił 15,59 USD.

Od początku miesiąca cena spadała z 17,5 USD do poziomu poniżej 13 USD. Trend odwrócił się około 25 października i pod koniec miesiąca cena wróciła do 17 USD.

i2 Trading zgłosił w kanale [#proposals](https://matrix.to/#/!MIGqWXfLFBwhipPKYL:decred.org/$157176144520723FSmYA:decred.org), że ich działania rynkowe oficjalnie rozpoczęły się 22 października na wszystkich giełdach z wyjątkiem OKCoin, gdzie jest opóźnienie. i2 rozpocznie rozliczanie za swoje usługi od 22 października, a za poprzednie testy nie pobierze wynagrodzenia.

## Ważne kwestie i wiadomości poboczne

Iterative Capital [wprowadził](https://iterative.capital/introducing-escher-hub-making-every-foss-wallet-a-cheap-and-fast-way-to-transact-bitcoin/) Escher, rampę do i z BTC-USD z funkcją Lightning, która może połączyć portfele Bitcoin i kanały Lightning z kontami bankowymi użytkowników. Twórcy portfeli kryptowalutowych typu FOSS mogą zintegrować się z Escher Hub, co pozwoli użytkownikom na łatwe zarządzanie portfelami i kanałami, które kontrolują i przenoszenie fundusze pomiędzy BTC i USD. Chris Dannen [stwierdził](https://twitter.com/chrisdannen/status/1187387952386707457) na Twitterze, że DCR jest jedyną inną walutą kryptograficzną, dla której planowane jest wsparcie.

W [recenzji](https://blog.coincodecap.com/dead-coins-on-crypto-exchanges/) 3162 projektów aut. CoinCodeCap stwierdzono, że 1240 z nich nie miało żadnych commitów do kodu źródłowego w ciągu ostatnich 90 dni i według tego kryterium zostały uznane za martwe. Raport uwzględnia również scentralizowane i zdecentralizowane giełdy wymian w świetle liczb martwych projektów, które mają w swojej ofercie.

W społeczności Ethereum Classic złożono [propozycję](https://ethereumclassic.org/blog/2019-10-06-pow-mining-explicit-social-contract/) w sprawie wyraźnego kontraktu społecznego na rzecz górnictwa PoW. Na niedawnej konferencji ETC w Vancouver osiągnięto najwyraźniej silny konsensus społeczny w tej sprawie, z ECIP w przygotowaniu. Redaktorzy ECIP zdecydują, czy propozycja zostanie przyjęta, a intencją jej zatwierdzenia byłoby zasygnalizowanie górnikom PoW, że społeczność zamierza ich wspierać w dłuższej perspektywie czasowej.

Zaproponowano powołanie [Parlamentu Wydobycia Bitcoin](https://coinspice.io/news/radical-proposal-bitcoin-mining-parliament-drama-ending-governance-or-more-alienating-devs/) przez Javiera Gonzaleza jako sposób na koordynację działań górników poprzez głosowanie za pomocą mocy obliczeniowej w sprawie propozycji dotyczących zasad konsensusu.

Zakończono trzecią rundę kwadratowego finansowania Gitcoin z napisaniem przez Vitalika Buterina [postu](https://vitalik.ca/general/2019/10/24/gitcoin.html) na ten temat. W sumie 163 tys. dolarów zostało przekazane na rzecz 80 projektów przez 477 darczyńców, powiększone o dodatkową, odpowiadającą im pulę 100 tys. dolarów. Buterin porównał finansowanie Gitcoina z finansowaniem Fundacji Ethereum i stwierdził, że jest bardziej skłonny finansować projekty cenione przez społeczność. Wersja finansowania kwadratowego została zmieniona z poprzednich rund, aby była mniej podatna na manipulacje, które miały miejsce wcześniej.

StakerDAO, DAO do inwestowania w blockchainy PoS, zostało [uruchomione](https://www.coindesk.com/theres-now-a-dao-for-deciding-which-blockchains-to-stake-on). StakerDAO jest tworzone przez Prezesa Zarządu Tezos Capital, z Polychain Capital jako inwestorem głównym. W momencie uruchomienia opublikowali oni szereg raportów ze swoich badań, w tym [jeden](https://medium.com/stakerdao/decred-research-833585a988d5) dla Decred.

Coinbase Custody od teraz [wspiera](https://blog.coinbase.com/coinbase-custody-now-supports-maker-governance-ced7aabfa054) zarządzanie w Maker, pozwalając osobom, które posiadają swoje MKR w Coinbase Custody na udział w głosowaniu bez wycofywania tokenów.

Prezes Fundacji Maker [ogłosił](https://blog.makerdao.com/breaking-launch-date-of-multi-collateral-dai-announced-at-devcon-5/), że Multi-Collateral Dai rozpocznie działalność 18 listopada, oraz [ogłosił](https://blog.makerdao.com/say-goodbye-to-cdps-and-hello-to-maker-vaults/) zmianę nazw kilku kluczowych komponentów 31 października.

Prezydent Chin Xi Jinping wydał pozytywne [oświadczenie](https://www.coindesk.com/president-xi-says-china-should-seize-opportunity-to-adopt-blockchain) na temat technologii blockchain i powiedział, że Chiny powinny wykorzystać okazję do jej przyjęcia.

CryptoBridge, "_bramka_ do _zecentralizowanej_ platformy tradingowej BitShares", wymaga od użytkowników [weryfikacji](https://twitter.com/CryptoBridge/status/1178913681117196293) ich tożsamości w odpowiedzi na piątą dyrektywę UE w sprawie przeciwdziałania praniu brudnych pieniędzy (AMLD5). Podlinkowany [post na blogu](https://crypto-bridge.org/2019/10/01/introducing-user-verification/) zapewnia, że jest to świetne rozwiązanie dla użytkowników.

Na Deribit i Coinbase Pro miał miejsce [gwałtowny spadek](https://www.coindesk.com/bitcoin-prices-slides-2-after-deribit-coinbase-flash-crash) ceny BTC z $9150 do $7720 na kilka minut przed odbiciem. Deribit [ogłosiło](https://twitter.com/DeribitExchange/status/1190047067365953536), że zwrócą 1,3 miliona dolarów strat dla osób, które zostały negatywnie dotknięte.

Zmęczony brakiem dostępu do globalnym rynku krypto, Poloniex [opuszcza](https://blog.circle.com/2019/10/18/poloniex-to-spin-out-of-circle/) jurysdykcję Stanów Zjednoczonych, aby skupić się na międzynarodowej wymianie kryptowalut wspieranej przez azjatycką grupę inwestycyjną. Klienci amerykańscy nie będą w stanie utworzyć nowych kont. Istniejące rachunki będą musiały zakończyć handel do 1 listopada i wycofać środki do 15 grudnia. Aby uczcić to posunięcie, Poloniex ustalił 0% opłaty transakcyjne do końca 2019 roku. Jak zwykle w przypadku akwizycji, dane klientów ponownie przejdą z rąk do rąk. Zobaczmy, czy klienci zostaną poproszeni o zgodę, zanim ich dane zostaną przekazane nowym osobom.

13 listopada Huobi [zamrozi](https://huobiglobal.zendesk.com/hc/en-us/articles/360000659122-Arrangement-to-freeze-US-user-accounts-on-13-November-2019-GMT-8-) wszystkie amerykańskie konta w ramach egzekwowania umowy użytkownika, która zakazuje amerykańskim użytkownikom handlu.

Międzynarodowy Fundusz Pomocy Dzieciom Organizacji Narodów Zjednoczonych (UNICEF) [ogłosił](https://www.unicef.org/press-releases/unicef-launches-cryptocurrency-fund), że jest teraz w stanie przyjmować, przechowywać i wypłacać darowizny w BTC i ETH. Fundusz nie będzie sprzedawał kryptowalut za fiat, ale będzie je przechowywał i wypłacał. Pierwsze darowizny pochodzą od Fundacji Ethereum.

W Stanach Zjednoczonych, IRS uaktualniło główny formularz stosowany przez indywidualnych podatników w celu dodania pytania o to, czy dana osoba miała styczność z kryptowalutami w ciągu roku. Zgodnie z tym [tweetem](https://twitter.com/allyversprille/status/1184827340737654785), główny radca prawny IRS Michael Desmond uważa, że istnieje około 12 milionów podatników, którzy powinni zgłaszać aktywa w walutach kryptograficznych.

IRS ["wyjaśniło"](https://www.journalofaccountancy.com/news/2019/oct/irs-income-cryptocurrency-hard-forks-airdrops-201922209.html) również  swoje stanowisko w sprawie odbioru monet z hardforków i zrzutów. Stanowisko to było szeroko krytykowane, ponieważ oznaczałoby to, że za każdym razem, gdy księga jest rozwidlana, wszyscy posiadacze muszą zgłaszać otrzymane na nowym łańcuchu monety.

W Hongkongu ludzie wycofali z bankomatów tyle gotówki, że zabrakło im zapasów. Wolumen LocalBitcoins [wzrósł](https://blockonomi.com/hong-kong-bank-run-bitcoin/) tymczasowo, po czym powrócił do normalnego zakresu.

Rezerwa Federalna USA kupi około [$60B bonów skarbowych](https://www.ft.com/content/baa7e796-ec38-11e9-85f4-d00e5018f061) miesięcznie przez co najmniej 6 miesięcy. Nazywają to "_organicznym wzrostem_ salda banku centralnego" i starają się bardzo mocno nie nazywać go _poluzowaniem polityki pieniężnej wer.4_, co wreszcie wydaje się nabierać negatywnych skojarzeń po wielu rundach tworzenia pieniędzy, które nie rozwiązały problemu. Interwencje rynkowe Fed [rozpoczęły się](https://www.newyorkfed.org/markets/opolicy/operating_policy_190917) w dniu 17 września, kiedy z jakichś powodów nie było wystarczającej płynności na "rynku repo". Pare obserwacji: 1) Fed nie musiał tego robić od czasu kryzysu finansowego w 2008 r.; 2) Fed i EBC rozpoczęły swoje interwencje mniej więcej w tym samym czasie; 3) podobnie jak w przypadku EBC, bardzo trudno jest zrozumieć, jak to dokładnie działa. Podobnie jak w przypadku [poprzedniego](201909.md#relevant-external) pytania do EBC, nie wiadomo, jak ciężko pracował Fed, aby zarobić pieniądze. Nie krępujcie się, by w komentarzach Reddita dodać sprawie trochę klarowności.

Prezes austriackiego banku centralnego uważa, luzowanie polityki pieniężnej przez EBC przynosi skutki [odwrotne do zamierzonych](https://www.bloomberg.com/news/articles/2019-10-13/ecb-s-holzmann-says-draghi-s-qe-policy-is-counterproductive).

[Odkryto](https://www.engadget.com/2019/10/14/linux-unix-sudo-command-security-flaw/?guccounter=1) lukę we wszechobecnej w Linuxie komendzie sudo. Umożliwiłaby ona uzyskanie pełnych przywilejów root każdemu, kto ma uprawnienia sudo na maszynie, w przypadku jego wykorzystania. Upewnij się, że Twoje systemy są zaktualizowane.

Internet obchodził 50 lat. 29 października 1969 roku, pierwsze dane zostały przesłane pomiędzy dwoma komputerami - wtedy był to szalony pomysł. Pierwszą wiadomością, którą wysłano, było "zaloguj", ale komputer odbierający zawiesił się po otrzymaniu "o". Tak więc pierwszą wiadomością było "zalo" ("lo" jak w "Lo and behold"). Nie mogliśmy mieć lepszej, bardziej zwięzłej pierwszej wiadomości" [stwierdził](https://usa.inquirer.net/44807/ucla-anniversary-kleinrocks-technology-lab) Leonard Kleinrock, który przeprowadzał eksperyment. Mówiąc o "ciemnej stronie" Internetu, pozostał optymistą: "Nadal uważam, że korzyści są o wiele bardziej znaczące; nie wyłączyłbym Internetu, gdybym mógł" i wyraził zainteresowanie technologią "blockchain".

## O tym wydaniu

To 19. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

* redakcja treści: akinsawyerr, bee, degeri, Haon, kozel, richardred, s\_ben
* recenzje i komentarze: davecgh, Dominic, jholdstock, emiliomann, evok3d, jz, linnutee, lukebp, raedah, zohand
* ilustracja tytułowa: saender
