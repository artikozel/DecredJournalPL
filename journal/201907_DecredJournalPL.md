# Decred Journal – Lipiec 2019

![Obraz: dyskusja nt. stakingu na StakingCon 2019 w Pekinie](../img/stakingcon2019-384.jpg)

_Obraz: Dyskusja nt. stakingu na StakingCon 2019 w Pekinie_

Główne wiadomości z lipca:

* Projekt [specyfikacji](https://github.com/decred/dcrdex) dla DEX został wydany, co stanowi ważny krok w kierunku jego realizacji. [Propozycja](https://proposals.decred.org/proposals/417607aaedff2942ff3701cdb4eff76637eca4ed7f7ba816e5c0bd2e971602e1) przeprowadzenia prac rozwojowych została złożona na początku sierpnia przez deweloperów dcrdata i zostanie uwzględniona w wydaniu sierpniowym.
* W dniu 7 sierpnia opublikowano 3 propozycje firm oferujących usługi animatora rynku (market making), a 10 sierpnia opublikowano kolejną propozycję RFP, w której poproszono interesariuszy, aby najpierw zasygnalizowali, czy w ogóle są zainteresowani animacją rynku. Propozycje te zostaną omówione w Politeia Digest (wkrótce) i w przyszłym miesiącu w Dzienniku.
* TinyDecred, zestaw narzędzi napisanych w jęz. Python, został wydany przez @buck54321, wykonawcę, który pracował nad dcrdata przez ostatni rok. TinyDecred był początkowo osobistym projektem dla Briana, ale z czasem rozwinął się w użyteczny zestaw narzędzi [które](https://proposals.decred.org/proposals/20e967dad9e7398901decf3cfe0acf4e0853f6558a62607265c63fe791b8b124) mogą umożliwić dużej liczbie programistów związanych z Pythonem prace nad projekt. W związku z powyższym została tez złożona propozycja z prośbą o 8000 dolarów za pracę włożoną w TinyDecred do tego momentu i wydaje się mieć silne poparcie.
* dcrdata beta v5.1 jest już dostępna, pełna przyrostowych ulepszeń. Nastąpił również duży postęp w kwestii dcrextdata, w którym zbierane są większe ilości danych rynkowych, a węzły są wdrażane w sieci w celu zbierania danych o mempoolu i czasach propagacji bloków.
* Światło dzienne ujrzało parę świetnych podcastów Decred in Depth z [@muststopmurad](https://www.youtube.com/watch?v=XkvcdjSH0c0) i [@permabullnino](https://www.youtube.com/watch?v=HxECplK3kAs) mówiących o tym, dlaczego i jak znaleźli się w Decred i o możliwościach i wyzwaniach, które widzą dla projektu w przyszłości.
* Dyskusje na tematy związane z Decred wydają się narastać w mediach społecznościowych, a krąg osób zaangażowanych w te dyskusje ciągle się poszerza. Jest to bez wątpienia efekt wywołany i wzmocniony przez #DecredChallenge i związane z nim memy, zainicjowane i spopularyzowane przez @Checkmate - który również opublikował [artykuł](https://medium.com/@_Checkmatey_/monetary-premiums-can-altcoins-compete-with-bitcoin-54c97a92c6d4) o zabezpieczeniach monetarnych Decred, i złożył [propozycję](https://proposals.decred.org/proposals/78b50f218106f5de40f9bd7f604b048da168f2afbec32c8662722b70d62e4d36) kontynuowania tej linii badań (obecnie zatwierdzoną). Artykuł @Checkmate'a został już zacytowany w [tezie inwestycyjnej](https://www.blockheadcap.com/post/decred-investment-thesis) z Blockhead Capital - który miał również kilka innych miłych rzeczy do powiedzenia na temat DCR.

## Rozwój

[dcrd](https://github.com/decred/dcrd): Optymalizacje i uzupełnienia infrastruktury dla różnych planowanych przyszłych funkcji, utrzymanie kodu, poprawki błędów.

Wprowadzono nowe główne wersje modułów [rpcclient](https://github.com/decred/dcrd/pull/1807), [bazy danych](https://github.com/decred/dcrd/pull/1799), [blockchain/stake](https://github.com/decred/dcrd/pull/1803) i [dcrjson](https://github.com/decred/dcrd/pull/1779) w celu wykorzystania ostatnich ulepszeń w innych modułach. Nowy moduł dcrjson został poddany gruntownemu przeglądowi, przy jednoczesnym zachowaniu wstecznie kompatybilnego API. Pozwoli to modułom konsumenckim na pobranie większości usprawnień za pośrednictwem starego API, zanim zostaną one w pełni zaktualizowane do nowego API. Zaistniała okazja przejścia na wyższe wersje pozwoliła na zerwanie szczelnego połączenia i usunięcia nieużywanego kodu.

Dodano [obejście](https://github.com/decred/dcrd/pull/1801) do problemów z generowaniem kodu kompilatora Go aby uniknąć eksplozji rozmiaru binarnego modułu chaincfg/v2.

[dcrwallet](https://github.com/decred/dcrwallet): Aktualizacje bazy kodowej i poprawki błędów. Scalono dużą [refaktoryzację](https://github.com/decred/dcrwallet/pull/1509) kodu JSON-RPC i [usunięto](https://github.com/decred/dcrwallet/pull/1496) przestarzały kod gRPC.

[Decrediton](https://github.com/decred/decrediton): Drobne ulepszenia w zakresie interfejsu użytkownika i poprawki błędów. Wdrożono [responsywny widok kupna biletów](https://github.com/decred/decrediton/pull/2146) i [zmodernizowano](https://github.com/decred/decrediton/pull/2156) tony zależności, aby zamknąć wiele luk.

[Politeia](https://github.com/decred/politeia): Kontynuowane są prace nad [przeprojektowaniem](https://github.com/decred/dcrdesign/issues/77) interfejsu Politei. Drugie ważne zadanie w lipcu dotyczyło [integracji](https://github.com/decred/politeia/pull/951) tloga z otwartego źródła Google [Trillian](https://github.com/google/trillian) przechowywanego w backendzie jako zamiennik tlogu Git. Tlog ([transparent log](https://research.swtch.com/tlog)) poprawi skalowalność, umożliwi indywidualne oznaczanie wpisów czasem i pozwoli w przyszłości na przejście na system plików taki jak [IPFS](https://ipfs.io).

Logowanie poprzez email zostało [zastąpione](https://github.com/decred/politeia/pull/940) w celu wykorzystania nazwy użytkownika jako części wysiłku włożonego w uczynienie [emaila opcjonalnym](https://github.com/decred/politeia/issues/554) i zostanie wdrożone na Politeię podczas następnej aktualizacji.

[dcrstakepool](https://github.com/decred/dcrstakepool): poprawa wydajności i interfejsu użytkownika, poprawki błędów. Zmieniono widok ["Połącz z portfelem"](https://github.com/decred/dcrstakepool/pull/427) i dodano wyświetlanie wysokości bloku VSP (https://github.com/decred/dcrstakepool/pull/440) jako wskaźnika stanu zdrowia. Trwają prace nad [rozłączeniem](https://github.com/decred/dcrstakepool/issues/227) dcrstakepool i dcrwallet (dcrstakepool powinien rozmawiać tylko z usługą stakepoold, która z kolei zarządza portfelem do głosowania).

Grupa Raedah rozpoczęła prace nad [poprawą](https://github.com/raedahgroup/dcrstakepool/pull/4) uwierzytelniania API dla VSP. Umożliwi to korzystanie z [bezkontowych VSP](https://github.com/decredcommunity/issues/issues/100), co znacznie uprości proces konfigurowania stakingu dla nowych użytkowników i pozwoli na uczynienie [emaila opcjonalnym](https://github.com/decred/dcrstakepool/issues/274) ([dyskusja](https://matrix.to/#/!wSdymYrEpBhsWlDJuk:decred.org/$15605505894685ViDcj:decred.org)).

[dcrlnd](https://github.com/decred/dcrlnd): Zmiany z głównego repozytorium [lnd](https://github.com/lightningnetwork/lnd) zostały [sportowane](https://github.com/decred/dcrlnd/pull/36#issuecomment-509370199), a prywatne gałęzie deweloperów są w większości zsynchronizowane z główną gałęzią lnd w upstreamie. Ostatni zgłoszony dla gałęzi master [pull request](https://github.com/lightningnetwork/lnd/commit/add905d17f7bbb11d0df2761cdf8accf2fef2b00) czekający na przegląd pochodzi z 25 lipca.

Repozytorium [lightning-faucet](https://github.com/decred/lightning-faucet) przeniosło się z GitHub @matheusd do oficjalnego, nalezącego do organizacji Decred, gdzie w tym miesiącu w kranie w tym miesiącu wprowadzono niewielkie ulepszenia do formularza generowania [faktur Lightning](https://github.com/decred/lightning-faucet/pull/9) i [dodanie](https://github.com/decred/lightning-faucet/pull/10) ciągłej integracji. Rozpoczęły się prace nad nowym formularzem Pay Invoice, który pozwoli użytkownikom płacić za pośrednictwem kranu (obecnie użytkownicy muszą płacić faktury w wierszu polecenia za pomocą `dcrlncli`).

[dcrandroid](https://github.com/decred/dcrandroid): Drobne optymalizacje interfejsu użytkownika i poprawki błędów, a także możliwość zmiany nazwy konta (https://github.com/decred/dcrandroid/pull/386).

Trwają prace nad dodaniem [uwierzytelniania biometryczneego](https://github.com/decred/dcrandroid/pull/343), [dźwięku i wibracji](https://github.com/decred/dcrandroid/pull/399) do powiadomień oraz [strony statystyk](https://github.com/decred/dcrandroid/pull/397).

[dcrios](https://github.com/raedahgroup/dcrios): Optymalizacja interfejsu użytkownika i poprawki błędów, nowe tłumaczenia na [hiszpański](https://github.com/raedahgroup/dcrios/pull/500), [wietnamski](https://github.com/raedahgroup/dcrios/pull/498) i [portugalski](https://github.com/raedahgroup/dcrios/pull/497).

[dcrdata](https://github.com/decred/dcrdata): v5.1 jest teraz [dostępna](https://explorer.dcrdata.org/). To wydanie dodaje liczne ulepszenia w zakresie interfejsu użytkownika, w tym [dodatek](https://github.com/decred/dcrdata/pull/1487) wartości procentowych i fiat do [dashboardu rynków](https://explorer.dcrdata.org/market), nową [stylizację](https://github.com/decred/dcrdata/pull/1446) na [stronie propozycji](https://explorer.dcrdata.org/proposal/decentralized-exchange-specification-document), [korektę](https://github.com/decred/dcrdata/pull/1448) do "przewidywanego" wykresu podaży monet, pełnoekranowy [wykres adresów](https://github.com/decred/dcrdata/pull/1443) (przydatny dla adresu [Skarbca](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx)) oraz [pasek postępu](https://github.com/decred/dcrdata/pull/1447) dla odwołania biletów.

Interfejsowi API Insight poświęcono więcej uwagi poprzez ulepszenia w zakresie [punktu końcowego adresu](https://github.com/decred/dcrdata/pull/1438), kilka poprawek błędów oraz [zwiększenie](https://github.com/decred/dcrdata/pull/1481) maksymalnej liczby połączeń z klientami z 1000 do 16384.

> dcrdata jest teraz oficjalnym API Insight dla Decred. Portfel Exodus wykorzystuje teraz host insight.dcrdata.decred.org dla potrzeb Insight API. W każdej chwili istnieje około 800 połączeń klienckich socket.io (bitów sieciowych Insight) z dcrdata i nie mieliśmy od tych użytkowników żadnych zastrzeżeń. (@chappjc in [chat](https://matrix.to/#/!LmKzrmxJIXNHNiEmIh:decred.org/$15651246158457opycs:decred.org))

[Wcielono](https://github.com/decred/dcrdata/pull/1491) zmiany w dcrd. Zależności npm zostały [zaktualizowane](https://github.com/decred/dcrdata/pull/1467) w celu usunięcia znanych luk.

Prace nad usunięciem [sqlite](https://github.com/decred/dcrdata/pull/1480) są kontynuowane.

Grupa Raedah kontynuuje prace nad [dcrextdata](https://github.com/raedahgroup/dcrextdata), pakietem do zbierania zewnętrznych (poza łańcuchem [*off-chain*]) danych, które nie znalazły się jeszcze na dcrdata. Poczyniono postępy w gromadzeniu danych na poziomie węzłów na temat czasu propagacji mempoolu i bloków. Teraz  są one śledzone z jednego węzła, a pełna historia śledzonych danych zostanie udostępniona (wraz z wykresami) po dodatkowych pracach kosmetycznych. Dcrextdata pobiera i przechowuje również dane z puli PoW i VSP, co pozwoli na zachowanie historycznego zapisu tych atrybutów. Demo danych na żywo jest dostępne [tutaj](http://dcrextdata.raedahgroup.com/).

Pozostałe:

* Projekt specyfikacji DEX został wydany i dodany do nowego repozytorium [dcrdex](https://github.com/decred/dcrdex).
* Grupa Raedah pracuje nad aplikacją mobilną dla lokalnego handlu BTC/DCR face-to-face (praca jest obecnie w prywatnych repozytoriach).
* [Zaktualizowano](https://twitter.com/degeri_crypto/status/1154776087374770176) stronę internetową [nagród za znalezienie błędów](https://bounty.decred.org/): dodano szczegóły dotyczące 3 nowych podatności. Program przetworzył łącznie 67 zgłoszeń, z czego 9 kwalifikuje się do wypłaty, z których 8 zostało poprawionych i ujawnionych.

Statystyki aktywności deweloperskiej na lipiec: 51 aktywnych PR-ów, 219 master commitów, 50 tys. dodanych i 29 tys. usuniętych linijek kodu spośród 15 repozytoriów. Wkład pochodził od 1-6 programistów na każde repozytorium.

## Ludzie

Witamy nowych, początkujących współpracowników, których kod scalono z głównymi gałęziami repozytoriów Decred na GitHubie: bgptr ([decrediton](https://github.com/decred/decrediton/commits?author=bgptr)), emesterhazy ([decrediton](https://github.com/decred/decrediton/commits?author=emesterhazy)), ReevesAk ([dcrwallet](https://github.com/decred/dcrwallet/commits?author=ReevesAk)).

Gratulacje dla 6 nowych współpracowników wymienionych na stronie [decred.org](https://decred.org/contributors/):

* Akin Sawyerr (@akinsawyerr, kierownik obsz. afrykańskiego & strategia)
* Kevin Hebert (@klebe, deweloper)
* Leslie Ankney (@cryptoleslie, relacje publiczne)
* Victor Guedes (@VictorGuedes, deweloper)

Australijska społeczność Decred kształtuje się bardzo prężnie. [Aktualizacja](https://medium.com/@sahand.bagheri/decred-australia-building-a-community-brick-by-brick-89928041687e) udostępniona w zeszłym miesiącu podsumowuje nawiązane partnerstwa, zorganizowane wydarzenia, przyciągnięte osoby, a także kolejne cele. Zostało to omówione w [czerwcowym wydaniu](201906.md) w sekcji "media", ale okazało się czymś więcej, niż tylko artykuł.

Statystyki społeczności na dzień 1 sierpnia:

* Użytkownicy platformy Politeia: 154 (-35, wzięto poprawkę dzięki bardziej dokładnej metodzie pomiaru)
* Obserwujący na Twitterze: 40,572 (+93)
* Subskrybenci na Reddit: 9,556 (+51)
* Użytkownicy na Matrixie: 384 (+20)
* Użytkownicy na Slacku: 6,809 (+40)
* Użytkownicy na Discordzie: 2,377 (+67), zweryfikowani z możliwością pisania postów: 281 (+35)
* Użytkownicy na Telegramie: 3,290 (-115)
* Subskrybenci na YouTube: 3,800 (+13)
* Obserwujący na Facebooku: 3,253 (+23), polubień: 2,983 (+19)
* Obserwujący na LinkedIn: 591 (+24)
* GitHub: 498 gwiazdek (+4) i 1,365 forków repozytorium dcrd (+28)

## Zarządzanie

W lipcu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 15517 DCR i wydał 10344 DCR. Wykorzystując dzienną średnią dzienną stawkę DCR/USD w lipcu, wynoszącą 28,97 USD, jest to odpowiednio 450 tys. dolarów i 300 tys. dolarów. Są to opłaty za pracę wykonaną w czerwcu po stawce w wysokości 28,90 dolarów, więc kwota na fakturze jest prawie taka sama. Na dzień 1 sierpnia saldo Skarbca wynosi 627 514 DCR (16,8 mln USD po kursie 26,75 USD).

W lipcu złożono 2 nowe propozycje:

* [Faza 1 - badania nad fundamentalnymi metrykami Decred](https://proposals.decred.org/proposals/78b50f218106f5de40f9bd7f604b048da168f2afbec32c8662722b70d62e4d36) autorstwa @Checkmate, nowego współpracownika, wnoszącego o 12 tys. dolarów na 3-miesięczną pracę nad badaniami i obecnością w mediach społecznościowych, plus 2000 dolarów za wcześniej wykonaną pracę (nad artykułem o [zabezpieczeniach pieniężnych](https://medium.com/@_Checkmatey_/monetary-premiums-can-altcoins-compete-with-bitcoin-54c97a92c6d4)). Głosowanie zostało zakończone, a wniosek został zatwierdzony przy 92% poparciu.

* [TinyDecred: A Python Toolkit for Decred](https://proposals.decred.org/proposals/20e967dad9e7398901decf3cfe0acf4e0853f6558a62607265c63fe791b8b124), aut. @buck54321, wykonawcy pracującego nad dcrdata w zeszłym roku, który wnosi o 8 tys. dolarów za pracę już wykonaną nad TinyDecred, zestawem narzędzi do interakcji z blockchainem Decred napisanym w jęz. Python. Głosowanie nad propozycją otwarto 6 sierpnia, obecnie ma 89% poparcia.

Kolejne 5 propozycji zostało złożonych w sierpniu, 4 dotyczące animatorów rynku i 1 związana z rozwojem DEX. Najbliższe wydanie magazynu Politeia Digest omówi je dogłębnie a ponadto zostaną one również omówione w sierpniowym wydaniu Dziennika.

[Wydanie 19](https://medium.com/politeia-digest/issue-19-june-30-july-31-2019-c591fcb79d98) Politeia Digest zawiera więcej szczegółów na temat lipcowej działalności propozycyjnej i dyskusji.

Przygotowano [zbiór danych](https://github.com/RichardRed0x/pi-research/blob/master/data/comments-and-updown-votes/pi-users.csv) i [krótki raport](https://github.com/RichardRed0x/pi-research/blob/master/analysis/comments-and-updown-votes/users-review.md), który agreguje dane Politei na podstawie nazwy użytkownika, dając dokładne dane liczbowe dotyczące tego, jak często każdy użytkownik komentował i głosował oraz tego, jak dobrze jego komentarze zostały ocenione.

## Sieć

Hashrate: lipcowy hashrate na początku miesiąca wyniósł ~503 Ph/s a zamknął miesiąc w ok. ~583 Ph/s, zaliczając niż w ok. 319 Ph/s oraz szczyt w wys. 687 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 2 sierpnia wyglądała następująco: F2Pool 21%, UUPool 19%, lab.antpool.com 16,5%, Poolin 9,5%, BTC.com 7,3%, Luxor 2,2%, BeePool 0,14%, Coinmine 0,12%, suprnova 0,08% i pozostałe 24%, za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

5 lipca według dcrstats.com zaobserwowany ostry spadek mocy obliczeniowej z 550 do 319 Ph/s, który w przeciągu ~20 godzin wrócił do stanu poprzedniego. Odbyła się długa [dyskusja](https://matrix.to/#/!NNzHoaSdnsbZDQQOXJr:decred.org/$156238052013967KGajR:decred.org) na temat możliwych przyczyn spadku i jego [dokładności](https://matrix.to/#/!NNzHoaSdnsbZDQDQOXJr:decred.org/$1562452219144sRKEL:decred.org).

Staking: średnia cena biletu z okresu 30 dni wynosiła 125,8 DCR (+5,8) za danymi z dcrstats.com. Cena wahała się między 118,8-129,5 DCR. Zablokowana kwota wynosiła 4,83-5,06 mln DCR, co odpowiadało 48,25-49,84% dostępnej podaży.

Cena biletu osiągnęła najwyższy poziom (129,46) od czasu algorytmu trudności w lipcu 2017 roku. Wysunięto [argument](https://matrix.to/#/!kdpEDksmOMNrlMqffD:decred.org/$156359151625133psHEo:decred.org), że wartość ta nie powinna być uważana za "ATH", ponieważ cena biletu wyniosła nawet i 238,9 DCR przed zmianą algorytmu.

Historyczne wykresy [danych VSP](https://charts.dcr.farm/d/000000016/proof-of-stake-pools?orgId=1&from=1514764800000&to=now) są dostępne na dcr.farm. Podobne dane zostały ostatnio udostępnione na stronie [dcrextdata](http://dcrextdata.raedahgroup.com/), jednakże dcr.farm dysponuje danymi od stycznia 2018 roku. Ustalenie długiego odstępu czasowego ujawnia interesujące trendy w konkurencji między VSP:

* dcr.stakeminer.com osiągnął najniższy poziom 14% w czerwcu i od tego czasu odzyskał poprzedni poziom z ponad 15% biletów w puli.
* Stakey.net wzrósł z 2,8% do 6,9% biletów w puli w 2019 roku, co koreluje ze wzrostem liczby użytkowników z 300 do 500.
* Megapool wzrósł do 3,5% od momentu powstania w październiku 2018 roku.
* tokensmart miał wyboistą drogę: od momentu powstania w kwietniu 2018 r. wzrosł do 2%, w kwietniu 2019 r., spadł do 0,8%, następnie szybko wybił do prawie 3% w czerwcu, po czym ponownie zaliczył  spadek do 0,8%.

Interesujący jest również wykres średniej kroczącej odsetka pominiętych biletów, który może być przydatny przy wyborze VSP.

Węzły: Przez cały [lipiec](https://charts.dcr.farm/d/000000014/nodes?orgId=1&from=1561939200000&to=1564617600000) było około 173 węzłów nasłuchujących i 360-530 węzłów normalnych za danymi z dcr.farm. Na dzień 2 sierpnia, około 70% korzysta z dcrd v1.4.0, 7,5% to dcrwallet v1.4.0, a 6% używa v1.5.0(pre) dev.

Na dzień 2 sierpnia, [testnet LN](https://charts.dcr.farm/d/DHPdAO4Wz/lightning-network?orgId=1) DCR pokazuje 18 węzłów i 52 kanały z łączną pojemnością 410 DCR.

## Integracje

[Everstake](https://everstake.one/), dostawca usług stakingowych, [ogłosił](https://medium.com/everstake/welcome-decred-voting-on-everstake-b2d0371426ad) uruchomienie VSP dla Decred pod adresem [decred.everstake.one](https://decred.everstake.one/).

Portfel [Exodus](https://www.exodus.io/) [zyskał](https://twitter.com/exodus_io/status/1148593861549334528) wsparcie dla urządzeń Trezor do zarządzania i wymiany DCR.

[Vertbase](https://www.vertbase.com/), giełda oferująca DCR z bramką fiat, [zapowiedział](https://twitter.com/vertbase/status/1147840898564120577), że będzie zakładać fundację. Jest to ciekawe wydarzenie w przestrzeni, ponieważ Fundacja przekazywać będzie środki na rozwój projektów, które Vertbase wymienia i wspiera, a jej zarząd będzie się składał z kluczowych członków zespołu wolontariuszy z tego projektu.

[MixinNetwork](https://twitter.com/Mixin_Network/status/1153272304790433793) zintegrowało Decred ze swoją platformą. Wzmianka z ich [strony internetowej](https://mixin.one/) głosi: "Mixin jest publicznie rozpowszechnioną księgą, której celem jest pomoc innym publicznie rozpowszechnianym księgom w uzyskaniu trylionów TPS, uzyskaniu ostatecznych potwierdzeń w czasie poniżej sekundy, zerowych opłat transakcyjnych, zwiększonej prywatności i nieograniczonej rozszerzalności".

Uwaga: autorzy Decred Journal nie są w stanie ocenić wiarygodności żadnego z powyższych podmiotów czy ich usług. Uprasza się o dołożenie należnych starań i własnoręczną weryfikację informacji przed powierzeniem jakichkolwiek środków innym stronom.

## Adopcja

Portugalski producent nieprzetworzonych produktów pszczelich DrApis [ogłosił](https://twitter.com/drapiscom/status/1146539277028909058), że akceptuje DCR.

Blockhead Capital [ogłosił](https://twitter.com/jyashouafar/status/1152238301593657344) swoją inwestycję w Decred i udostępnił [artykuł badawczy](https://www.blockheadcap.com/post/decred-investment-thesis). Ich wnioski:

> Decred jest adaptacyjną kryptowalutą o sztywnej polityce pieniężnej. Sztywna polityka pieniężna stanowi podstawę niezbędną do uzyskania zabezpieczenia monetarnego, podczas gdy adaptacyjny charakter zarządzania bezpośrednio na łańcuchu (*on-chain*) pozwala na integrację bardziej dynamicznych cech. Hybrydowy mechanizm konsensusu tworzy odpowiednie mechanizmy kontroli i równowagi pomiędzy różnymi stronami w ekosystemie, eliminując jednocześnie kontrowersyjne rozłamy sieci jako podstawową metodę rozwiązywania sporów, co jest wysoce pożądaną cechą aspirujących globalnych aktywów rezerwowych. Ponadto hybrydowy konsensus tworzy bezpieczniejszą przestrzeń blokową, czyniąc przestrzeń blokową bardziej wartościową i zapewnia walutę bardziej odporną na cenzurę. Decred buduje w oparciu o mocne strony Bitcoina i stanowi przeciwwagę do jego wad, umożliwiając mu uzupełnienie go lub konkurowanie z nim jako cyfrowym środkiem przechowania wartości.

## Nawiązywanie kontaktów

W lipcu kontynuowano budowę infrastruktury, która pomoże Decred w usprawnieniu działań informacyjnych i edukacyjnych. Aktualizacja strony internetowej jest bliska ukończenia i powinna być gotowa do końca sierpnia z nowymi podstronami dotyczącymi bezpieczeństwa, zdolności adaptacyjnych, samofinansowania i historii Decred. Dodatkowo, uzgodniliśmy schemat i obecnie tworzymy repozytorium zasobów na podstawie [kanonu Maxa Bronsteina](https://github.com/maxbron08/Decred-Canon), które pomoże w naturalny sposób pokierować procesem odkrywczym dla osób podejmujących #DecredChallenge.

Aby to osiągnąć, udoskonalamy nieco nasz przekaz, skupiając się głównie na podstawowych zasadach Decred, ponieważ stąd właśnie wypływa. Zaktualizowana jego wersja pojawi się na czacie w ciągu najbliższego tygodnia, aby uzyskać wkład i komentarze od społeczności. Inne zasoby dla społeczności, nad którymi trwały prace, obejmują Social Media Playbook, zawierający najlepsze praktyki, jak zaangażować się w kontakt z innymi i dotrzeć do nich w konstruktywny sposób, który przedstawia Decred w odpowiednim świetle i pomaga edukować innych o projekcie.

Dodatkowo, wkrótce zostanie udostępniony Podręcznik dla organizatorów społeczności, w celu uzyskania wkładu społeczności. Pomoże on w wyjaśnieniu ról i obowiązków w celu uzyskania zgodności, poprawy wydajności i dzielenia się najlepszymi praktykami stosowanymi na całym świecie. Zgodnie z tymi założeniami Decred poszukuje osób gotowych by przewodzić wysiłkom marketingowym w paru obszarach geograficznych, aby pomóc w zarządzaniu obszarami na świecie. Różne propozycje z wielu regionów są aktualnie w toku i powinny trafić na Politeię w ciągu najbliższych kilku miesięcy. Nadal poszukujemy liderów w Europie i Azji, więc dołącz do nas na kanale #marketing lub #local_ops na Matrixie, aby omówić pomoc w decentralizacji organizacji.

Pracujemy również nad koordynacją burzy tygodniowych wydarzeń, które odbędą się w październiku i w których udział wezmą różni członkowie społeczności Decred w najważniejszych miastach w Azji. Szczegóły powinny zostać opublikowane w ciągu najbliższego miesiąca.

Odcinki Decred in Depth z udziałem [Murada Mahmudova](https://soundcloud.com/decredindepth/murad-mahmudov-dcr-investment-thesis-sov-narrative-crypto-economics) i [Permabull Nino](https://soundcloud.com/decredindepth/ep-5-decred-as-strong-accounting-ticket-metrics-with-permabull-nino) zostały opublikowane. Zostały one bardzo dobrze przyjęte i wywołały wiele dyskusji na temat Decred w mediach społecznościowych.

Lipcowe osiągnięcia Ditto:

* Poszerzyliśmy zakres naszych prac z różnymi członkami społeczności odnośnie strategii i sposobów produktywnego angażowania się w dyskusje na Twitterze.
* Stworzyliśmy szerszą listę rzeczników Decred wraz z nową listą celów medialnych.
* Wspólnie ze społecznością ustaliliśmy, w jaki sposób najlepiej zbudować widoczność dla Decred i jego przekazu.
* Zabezpieczyliśmy przestrzeń dla czterech wywiadów a po ich opublikowaniu podzielimy się większą ilością szczegółów.
* Umieściliśmy artykuł w biuletynie doradztwa finansowego, Legacy Research, w wyniku wywiadu, który przeprowadziliśmy z @moo31337.
* Zabezpieczyliśmy 10-minutowy segment w [BlockTV](https://blocktv.com/watch/2019-07-30/5d404e65ea3f5-decred-s-jake-yocom-piatt-talks-decentralized-governance) z @jy-p omawiając jego podejście do Libry i postępy Decred w kierunku przemiany w DAO.
* Zabezpieczyliśmy publikację wzmianki @jy-p na temat Libry w [CCN](https://www.ccn.com/news/libra-friend-or-foe/2019/07/21/).
* Pracowaliśmy wraz ze społecznością, aby wzmocnić/zaangażować się w [burzę tweetów na temat #DEX](https://twitter.com/decredproject/status/1156652694502817793) ogłaszając specyfikację zdecentralizowanej giełdy wymian Decred.
* Rozpoczęliśmy odświeżanie przekazu medialnego, dodając FAQ, aby wyjść naprzeciw powszechnym nieporozumieniom.
* Dodaliśmy ostatnie szlify do schematu repozytorium zasobów edukacyjnych dla strony Decred, który ułatwi dziennikarzom i nowicjuszom poznanie bez nawigowania po przeróżnych stronach.
* Opracowaliśmy długoterminowy plan relacji z mediami, który skierowany jest do wszystkich odbiorców Decred (inwestorów, deweloperów, entuzjastów kryptografii), jak również do mediów, które nie pisały o Decred w przeszłości.
* Odświeżyliśmy szkolenie medialne z @jy-p, aby przygotować się do wywiadów telewizyjnych.

## Eventy

Na których byliśmy:

* 4-5 lipca - [Blockchain Summit Latam](https://twitter.com/Decred_ES/status/1146093986806976513) - Mexico City, Meksyk. Ana Dalia [reprezentowała](https://twitter.com/AnaDaliacd23/status/1146873685229416450) Decred. Po konferencji odbyła się [kolacja](https://twitter.com/Decred_ES/status/1147522846513618945) sponsorowana przez Decred.
* 10 lipca - [Meetup Decred](https://twitter.com/Decred_BR/status/1147201276058505216) - São Paulo, Brazylia. Zorganizowane przez @guisso.
* 10 lipca - [StakingCon](https://twitter.com/BlockBeatsChina/status/1147570186519638017) - Pekin, Chiny. @Dominic "oczarował organizatora na tyle, by przedstawić wideo o Decred i wziął udział w dyskusji przy okrągłym stole". Wydarzenie zorganizowane przez @BlockBeatsChina. ([zdjęcia](https://twitter.com/DecredCN/status/1148983482732830720))
* Jul 11 - [Event Staked US](https://twitter.com/staked_us/status/1148687292032323584) - Nowy Jork, USA. Pogawędka z @joshuam, której współgospodarzami byli Staked i TokenTax.
* 19 lipca - Meetup - Buenos Aires, Argentyna. Spotkanie było przygotowaniem do zbliżającego się krypto poniedziałku 12 sierpnia. [@Camilolwi](https://twitter.com/Camilolwi) [przedstawił](https://twitter.com/cryptorocketok/status/1152260099072778240) Decred. Wydarzenie prowadzone przez [Crypto Rocket Group](https://twitter.com/cryptorocketok).
* 21 lipca - [Spotkanie OKEx](https://twitter.com/wanbihou/status/1151704823533723648) - Qingdao, Chiny. Czat z @Dominic.
* 25 lipca - [Prawo komputerowe + Blockchain Festival CDMX 2019](https://twitter.com/LegalHackersMX/status/1153832499333795840) - Mexico City, Meksyk. Projekt [reprezentował](https://twitter.com/elianhuesca/status/1154452590983299073) @elian.
* 25-26 lipca - Cointime Summit 2019 - Ho Chi Minh City, Wietnam. Duyen Em przedstawił Decred osobom z obszaru konferencji. Niektórzy prelegenci z innych projektów byli już dobrze z nim zapoznani i mówili dużo o Decred, lecz większość wietnamskich prelegentów dopiero uczy się o Decred. Duyen Em sugeruje, że Decred zasługuje na znacznie większą obecność w tętniącej życiem przestrzeni kryptowalutowej Wietnamu i dzieli się pomysłami na nawiązanie kontaktów i rozwój społeczności. Pełny raport zostanie opublikowany na Reddicie.
* 28 lipca - Vietnam Staking Economy - Ho Chi Minh City, Wietnam. Duyen Em reprezentował Decred i odpowiadał na pytania wielu młodych ludzi zainteresowanych kryptowalutami. Szczegóły znajdują się w raporcie z Cointime Summit.
* 31 lipca - [Otwarty Szczyt Bankowy](https://theopenbankingsummit.com/) wstępne spotkanie - Mexico City, Meksyk. @elian reprezentował projekt i [wygłosił przemówienie](https://twitter.com/elianhuesca/status/1157313830969630725) na temat Decred. Szczyt rozpocznie się 13 listopada.

Nadchodzące:

* 8 sierpnia - [Blockchain Bajio](https://www.eventbrite.com/e/blockchain-bajio-2do-meetup-tickets-66510186759) - Leon, Guanajuato, Meksyk.
* Aug 12 - [Crypto Monday](https://www.meetup.com/Bitcoin-Argentina/events/263594472) - Buenos Aires, Argentyna. Crypto Monday jest comiesięcznym wydarzeniem organizowanym w Espacio Bitcoin, lokalnej przestrzeni współpracy z główną argentyńską organizacją pozarządową Bitcoin, Bitcoin Argentina.
* 13-14 sierpnia - [Konferencja Futurystów](https://eventmobi.com/futurist/) - Toronto, Kanada. Decred został ogłoszony sponsorem i ma miejsce w [panelu dyskusyjnym](https://twitter.com/decredproject/status/1157416657670868997) "Społeczny wpływ Blockchaina i zarządzanie w imieniu dobra", podczas którego @zubair będzie reprezentował projekt.
* 16-18 sierpnia - [Campus Party Natal](https://brasil.campus-party.org/campus-party-natal/) - Natal, Brazylia. @guisso opowie o tym, jak działa Decred jako organizacja.
* 20 sierpnia - [Kryptoalchemia: wydobycie i staking Decred](https://www.meetup.com/Philadelphia-Technology-for-Blockchain-and-Cryptocurrency/events/ffssfryzlbbc/) - Filadelfia, USA. Prowadzony przez [@mikeghen](https://twitter.com/mikeghen/status/1155594343702511616).
* 28 sierpnia - [Blockchain Bootcamp](https://www.blockchainbootcamp.net/) - Docklands, Australia. @zohand i spółka zostali [zaproszeni](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15644812201506dzVgU:decred.org) do przeprowadzenia wydarzenia o zarządzaniu blockchainem jako części jednego z głównych strumieni. Wydarzenie to jest częścią corocznego [Festiwalu Innowacji Cyfrowych](https://dif.vic.gov.au/) organizowanego przez samorząd obszaru Victoria.
* 30 września - 1 października - [Głos Blockchain](https://twitter.com/BlockchainVoice/status/1154772731575099392) - Chicago, USA. @jy-p zaprezentuje hasło przewodnie "Dlaczego bezpośrednia suwerenność i multiinkluzywność stron przetrwa próbę czasu".
* 4-7 listopada - [Websummit](https://websummit.com/) - Lizbona, Portugalia. @moo31337 będzie przemawiać na panelu TBD, a Decred będzie obecny na stoisku wystawowym 2m x 2m.

## Media

Wybrane artykuły:

* Decred: To, czym złoto i Bitcoin chciały być, aut. Pascal Thellmann ([seekingalpha.com](https://seekingalpha.com/instablog/49962360-pascal-thellmann/5324856-decred-gold-bitcoin-wanted))
* Zabezpieczenia monetarne; czy altcoiny mogą konkurować z Bitcoinem?, aut. @Checkmate ([medium](https://medium.com/@_Checkmatey_/monetary-premiums-can-altcoins-compete-with-bitcoin-54c97a92c6d4))
* Libra: Sprzymierzeniec czy wróg?, aut. @jy-p ([ccn.com](https://www.ccn.com/news/libra-friend-or-foe/2019/07/21/))
* Bitcoin & Decred/Historyczne dokumenty cyfrowej rewolucji finansowej, aut. BlackBearXVII ([medium](https://medium.com/@imagnusholdings/bitcoin-decred-historical-documents-of-a-digital-financial-revolution-4debfa0d10d9))
* Niezależne (krypto) sieci, aut. Joel Monegro ([placeholder.vc](https://www.placeholder.vc/blog/2019/7/31/lvhpfydo4m3uoezhwhicyxo06og0mn)) - wymienia Decred jako przykład
* Wprowadzenie do kryptorachunkowości: Analiza Decred jako systemu rachunkowego, aut. Permabull Nino ([medium](https://medium.com/@permabullnino/introduction-to-crypto-accounting-analysis-of-decred-as-an-accounting-system-4d3e67fce28)).
* Blockhead Capital: Teza inwestycyjna Decred ([blockheadcap.com](https://www.blockheadcap.com/post/decred-investment-thesis))

Tłumaczenia:

* @Dominic przetłumaczył cały szkic dokumentu [specyfikacyjnego Decred DEX ](https://github.com/decred/dcrdex/blob/master/README.mediawiki) na [jęz. chiński](https://github.com/DominicTing/dcrdexStandard-CN-/blob/master/README.mediawiki). Link został zgłoszony do chińskiej [strony informacyjnej Binance](https://info.binance.com/cn/currencies/decred).
* Majowe i czerwcowe wydania Decred Journal zostały przetłumaczone na jęz. arabski (@arij), chiński (@Dominic, @guang, @changhugo), włoski oraz rosyjski (@DZ), polski (@kozel) i wietnamski (Duyen Em). Dziękujemy wszystkim tłumaczom.

Wideo:

* Libra: Sprzymierzeniec czy wróg? - wywiad z @jy-p dla [Block TV](https://blocktv.com/watch/2019-07-30/5d404e65ea3f5-decred-s-jake-yocom-piatt-talks-decentralized-governance)

Audio:

* Decred in Depth odc. 4 Murad Mahmudov - Teza inwestycyjna DCR  + narracja środka przechowania wartości + kryptoekonomia ([libsyn](https://decredindepth.libsyn.com/murad-mahmudov-dcr-investment-thesis-sov-narrative-crypto-economics-0), [soundcloud](https://soundcloud.com/decredindepth/murad-mahmudov-dcr-investment-thesis-sov-narrative-crypto-economics), [twitter](https://twitter.com/decredproject/status/1150836740665552896))
* Decred in Depth odc. 5 Permabull Nino - Decred jako silne narzędzie rachunkowe + metryki biletowe ([libsyn](https://decredindepth.libsyn.com/ep-5-decred-as-strong-accounting-ticket-metrics-with-permabull-nino-0), [twitter](https://twitter.com/decredproject/status/1157000762611896320))
* POV Crypto: Decred: dzieląc różnice między Bitcoinem i Ethereum z udz. Luke'a Powella ([medium](https://medium.com/@TrustlessState/decred-splitting-the-difference-between-bitcoin-and-ethereum-with-luke-powell-758cf6e1218d), [libsyn](http://povcryptopod.btc.libsynpro.com/decred-splitting-the-difference-between-bitcoin-and-ethereum))
* The Sound Money Podcast: On-Chain Atomic Swaps z udz. @joshuam ([spotify](https://open.spotify.com/episode/1SuzMUUmtm6xR7ofGN6t4a), [itunes](https://podcasts.apple.com/us/podcast/the-sound-money-podcast/id1470774235?i=1000443695629))

## Dyskusje społeczności

Nowinki z platform komunikacyjnych:

* Domena [chat.decred.org](https://chat.decred.org/) jest hostem dla Riota, sieciowego klienta protokołu  Matrix. Jest wiele [zalet](https://github.com/decredcommunity/issues/issues/62) hostowania Riota na własnych serwerach. Najbardziej widocznym z nich jest to, że link staje się łatwy do zapamiętania i upraszcza wprowadzanie ustawień bardziej niż dedykowana [strona pokładowa](https://decred.org/matrix/) - nowi ludzie często byli zdezorientowani co do prawidłowego ustawienia serwera domowego. Mniej oczywistą korzyścią jest to, że pomaga zachować łączność podczas takich incydentów, jak zgłoszona [w kwietniu](201904.md) awaria serwera matrix.org. Wreszcie, zwiększona jest [prywatność](https://github.com/decredcommunity/issues/issues/25) poprzez usunięcie fingerprintingu przez Google recaptcha ze strony rejestracji i zmniejszenie ruchu do zewnętrznych domen. Nie każdy projekt może sobie pozwolić na samodzielne prowadzenie takiej infrastruktury i bycie niezależnym. Ogromne podziękowania dla naszych adminów-czarodziejów.
* Użytkownicy Riota cieszą się teraz z reakcji i mogą edytować swoje wiadomości, po [wydaniu](https://medium.com/@RiotChat/%EF%B8%8Fmessage-editing-%EF%B8%8F-reakcje-5cffec8f71a2) nowych wersji. Użytkownicy Riota powinni jednak być świadomi tego, że edycja wiadomości będzie powtarzać je po drugiej stronie mostu dla osób używających Slacka i Doscorda.

Wybrane tematy:

* 1 lipca rozpoczęło się [wyzwanie #DecredChallenge](https://twitter.com/_Checkmatey_/status/1145764832362319872), kiedy to @Checkmate rzucił wyzwanie Bitcoinowcom, aby spędzili miesiąc przyglądając się projektowi Decred i zakończyli miesiąc bez przekonania, że powinien to być projekt #2 w skali świata, zapraszając ludzi, którzy nie są przekonani do jego zalet, do wzięcia udziału w debacie na jego temat. Wydarzenie to [ewoluowało](https://twitter.com/RichardRed0x/status/1146132909713240065) [szybko](https://twitter.com/_Checkmatey_/status/1146136667448913921) do rangi mema, zostało okraszone [hasztagiem](https://twitter.com/Ammarooni/status/1146171552213479425), a następnie (głównie dzięki @Checkmate) przerodziło się w tweetowy kurs na temat powodów, dla których Decred poważnie zasługuje na uwagę (patrz poniżej).
* Kolejny [artykuł](https://bravenewcoin.com/insights/decred-price-analysis-a-sustained-increase-in-mining-activity-2) opisujący Decred jako "fork Bitcoina" został opublikowany, prawdopodobnie w oparciu o użycie tego terminu w opisach na [CoinMarketCap](https://coinmarketcap.com/currencies/decred/) i [Messari](https://messari.io/asset/decred) (który, aby być sprawiedliwym, używa bardziej ograniczonego opisu "fork bazy kodowej Bitcoina"). Jest to błędny opis, który frustruje społeczność, ponieważ "fork Bitcoina" oznaczałby zazwyczaj monetę, która rozwidla oprogramowanie Bitcoin Core i/lub zestaw BTC UTXO, a w przypadku Decred żadne z tych określeń nie ma odzwierciedlenia w faktach. "Fork Bitcoina" nie odzwierciedla faktu, że oprogramowanie Decred zostało stworzone od zera przez tych samych ludzi, którzy uruchomili Decred, rozpoczynając swoje życie jako btcd, niezależną implementację pełnego węzła Bitcoina napisaną w Go. @lukebp [zatweetował](https://twitter.com/lukebp_/status/1155886623147429889) o tym fakcie i otrzymał odpowiedź od Messari, @Checkmate [rozszerzył](https://twitter.com/_Checkmatey_/status/1155901635257929728) komentarz @lukebp do produkcji kolejnego rozdziału w #DecredChallenge.
* @Ammarooni podjął #DecredChallenge i przedstawił pewne [obawy](https://twitter.com/Ammarooni/status/1148013517016113152) dotyczące wektorów ataku związanych z odpowiedzialnością interesariuszy za nielegalne propozycje i podatnością LLC na konfiskatę funduszy. @lukebp i @jz odpowiedzieli wyjaśnieniem, w jaki sposób Decred zmierza w kierunku przeistoczenia się w pełne DAO i w jaki sposób rozwiąże te problemy.
* Temat, czy zmienić nazwę najmniejszych jednostek (atomów) Decred, czy też włączyć "kredyty" do nazw innych nominałów, pojawił się na [Twitterze](https://twitter.com/OfficialCryptos/status/1151603316167720960) i był omawiany na czatach i w tym wydaniu GitHub [wydanie](https://github.com/decredcommunity/issues/issues/129). Deweloperzy zwrócili uwagę, że "atom" jest używany tysiące razy w bazie kodowej Decred, co zniechęciło niektórych zwolenników zmiany, lecz nie wszystkich.

@Checkmate był bardzo aktywny na Twitterze i wygenerował mnóstwo szumu i zaangażowania wokół hasztagów #DecredChallenge i #DontSleepOnDecred, oto kilka najważniejszych punktów:

* [Ogłoszenie](https://twitter.com/_Checkmatey_/status/1148682397875167233) artykułu o zabezpieczeniach monetarnych.
* [Żaden fork Bitcoina](https://twitter.com/_Checkmatey_/status/1155901635257929728).
* [Ryzykując własną skórą](https://twitter.com/_Checkmatey_/status/1148354974390390784).
* [Zabezpieczenie](https://twitter.com/_Checkmatey_/status/1149560942654414848) dla Bitcoinowców i Ethernian.
* [Odznaczaj się tam](https://twitter.com/_Checkmatey_/status/1150831105081298944), gdzie ma to znaczenie.
* [Fundusz Skarbowy](https://twitter.com/_Checkmatey_/status/1157342578787913733).
* [Propozycje Politeia](https://twitter.com/_Checkmatey_/status/1156293040509739010).
* [Cyfrowy organizm](https://twitter.com/_Checkmatey_/status/1155567971823226881) zaprojektowany, aby dostarczyć najbardziej odporne, solidny pieniądz.

Inne wybrane tweety:

* #DecredChallenge: Znajdź zespół inżynierów, którzy podejmą wyzwanie [ograniczenia własnej władzy i wpływów](https://twitter.com/RichardRed0x/status/1146917561751212032) tak mocno, jak Company 0 zrobiła z Decred.
* Chris Burniske na temat tego, co go [zainteresowało](https://twitter.com/lefebvre_dustin/status/1156316679040901125) w projekcie Decred.
* Hybrydowy system PoW + PoS w Decred [umożliwia](https://twitter.com/NoahPierau/status/1155466908738686977) 3 formalne mechanizmy zarządzania.
* The Decred Journal jest obecnie [rozpowszechniany](https://twitter.com/Binance_Info/status/1153575996487954432) na stronie internetowej Binance Info.

Teza inwestycyjna Decred aut. @lukebp [w jednym tweecie](https://twitter.com/lukebp_/status/1154398108538658816):

> Technologiczne zmiany sa trudne do przewidzenia. Protokół powinien mieć możliwość dostosowywania się do tych zmian. Ludzie podejmujący decyzje o tych zmianach powinni odpowiadać za nie własną skórą, mowa tu o interesariuszach.

Wybrane wątki z Reddita:

* [Rozwój społeczności](https://www.reddit.com/r/decred/comments/c9xtml/decred_community_growth/) Decred.
* Jestem [podróżnikiem w czasie z przyszłości](https://www.reddit.com/r/decred/comments/c9jxml/i_am_a_timetraveler_from_the_future_here_to_beg/) i błagam Was: róbcie dalej to, co robicie.
* [Sugestia](https://www.reddit.com/r/decred/comments/casb4b/decred_project_live_chat_infrastructure/) aby usunąć kanał #random.
* Format do śledzenia i omawiania [wcześniejszych propozycji](https://www.reddit.com/r/decred/comments/cb7g8g/general_is_there_an_optimal_rdecred_format_that/); raportowanie, redditopodobne forum, język działania.
* Równowaga między prywatnością indywidualnych [płatności dla wykonawców](https://www.reddit.com/r/decred/comments/cf773y/discussion_per_delivery_vs_per_hour/) a przejrzystością dla interesariuszy.
* Czy interesariusze mogą zagwarantować, że blok z [podwójnym wydaniem tych samych środków](https://www.reddit.com/r/decred/comments/cgz12h/in_a_scenario_in_which_a_miner_submits_a_block/) nie zostanie zatwierdzony, oraz rola stakerów w zapobieganiu atakom większościowym/51%.
* [Model zarządzania](https://www.reddit.com/r/decred/comments/cirkvr/decreds_governance_model/) Decred; trudno jest dodać zarządzanie po uruchomieniu.
* Czemu ostatecznie Decred wygra? [Inkrementyzm](https://www.reddit.com/r/decred/comments/cc8c0h/why_decred_wins_in_the_end_incrementalism/)
* Czy redditowy [flair](https://www.reddit.com/r/decred/comments/ch0gey/governance_can_flair_increase_the_odds_of/) może zwiększyć szanse na samodzielną edukację na subreddicie r/decred?
* David Ogilvy mówi o [reklamie bezpośredniej reakcji](https://www.reddit.com/r/decred/comments/ci82iy/david_ogilvy_talks_direct_response_advertising/); skierowanie do grup docelowych, które podzielają nasze wartości i cenią suwerenność tak samo wysoko, jak my.
* Jaka [metafora/analogia](https://www.reddit.com/r/decred/comments/cc40hb/general_what_metaphoranalogy_helps_you_understand/) pomogła Wam zrozumieć różne role/aktorów w ramach projektu?

## Rynki

W lipcu kurs wymiany Decred wahał się pomiędzy 25,20-35,64 USD / BTC 0,00262-0,00296. Średni dzienny kurs wynosił 28,907 USD.

Po krótkim wzroście w kierunku 13 tys. dolarów cena Bitcoina spadła i oscylowała w okolicy 10 tys. dolarów przez większość lipca.

## Ważne kwestie i wiadomości poboczne

Chris Burniske z Placeholder VC (posiadacze Decred i Zcash) przedstawił dobre [podsumowanie](https://forum.zcashcommunity.com/t/placeholder-considerations-resources-governance-and-legitimacy-in-nu4/34045) sytuacji, w jakiej znalazła się społeczność Zcash po wygaśnięciu nagrody założycieli, opowiadając się za kontynuacją 20% nagrody blokowej w celu finansowania rozwoju projektu przez kolejne 4 lata, z podziałem 70% na "rozwój protokołu" i 30% na "fundusze wzrostu".

Zooko Wilcox opublikował [list osobisty](https://medium.com/@zooko_25893/a-personal letterer-about-the-possibility-of-a-new-zcash-dev-fund-f6d30df64392) o możliwości utworzenia nowego funduszu deweloperskiego Zcash, w którym wyjaśnia, że zawsze wiedział, że nadejdzie czas, gdy skończy się finansowanie i powstanie problem, który można rozwiązać jedynie poprzez "brudny i trudny proces", taki, jak ten, przez który społeczność Zcash obecnie przechodzi. Zooko ponownie stwierdził, że nie może być tym, który podejmie decyzję i że powinna ona pochodzić od społeczności, ale jako prezes ECC ma znaczący wpływ na społeczność, a społeczność nie ma ustalonej metody podejmowania decyzji.

Wszystkie rozważane opcje zostały streszczone w tym [megatemacie](https://forum.zcashcommunity.com/t/future-of-zcash-dev-funding-megathread-everything-in-one-place/34063). Jak zauważył Chris Burniske w swoim poście, pierwszym pytaniem jest to, jak podjąć decyzję o podjęciu decyzji w sposób, który będzie postrzegany jako uzasadniony. Biorąc pod uwagę ograniczenia czasowe, Chris opowiada się za wykorzystaniem narzędzi sondażowych celem przebadania opinii publicznej by określić jej preferencje dla różnych opcji, przy podjęciu ostatecznej decyzji z wykorzystaniem 2-z-2 multisiga ECC i Fundacji Zcash. Zooko oświadczył, że ECC ogłosi metodę podejmowania decyzji na początku sierpnia.

Nebulous, firma budująca sieć Sia, ogłosiła [zakończenie](https://sia.tech/funding2019) rundy pozyskiwania kapitału początkowego o wartości 3,25 mln USD z udziałem wielu inwestorów kapitału podwyższonego ryzyka.

Finansowanie było również przedmiotem dyskusji w społeczności Ethereum, z większą [uwagą](https://research.circle.com/insights/the-great-ethereum-funding-debate) zwracaną na [EIP-2025](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2025.md), który dodałby 0,0055 ETH za każdy blok przez 18 miesięcy (łącznie 17K ETH) w celu sfinansowania rozwoju ETH 1.X (jako, że główni deweloperzy skupiają się na ETH 2.0). Nagrody blokowe zostałyby wykorzystane na spłatę kredytu, który zespoły pracujące w 4 różnych obszarach otrzymałyby na adresy z kontraktami multisig.

Podobnie jak w przypadku każdej kontrowersyjnej propozycji ulepszenia Ethereum (EIP), osobom z zewnątrz trudno jest przewidzieć, czy EIP-2025 cokolwiek zdział. [Tweet](https://twitter.com/VitalikButerin/status/1154733914881179648) Vitalika stwierdzający, że owa propozycja wydaje się mieć niewielkie poparcie, prawdopodobnie wskazuje, że nie zostanie uwzględniona w hard forku Istanbul.

Kolejny [artykuł](https://research.circle.com/insights/degrees-of-architectural-decentralization-to-infura-and-beyond) Circle Research  opublikowany na temat Ethereum dotyczy centralizacji Infura, firmy usługowej stworzonej przez Consensys, która pozwala deweloperom dapp na pominięcie tworzenia i uruchamiania własnych węzłów. W artykule uznano, że trudność i rosnące wymagania związane z uruchomieniem pełnego węzła (zapotrzebowanie na miejsce wzrosło od początku roku o 25-48%) spowodowało spadek liczby pełnych węzłów z 12 000 w grudniu 2018 roku do 8 000 w lipcu 2019 roku. Infura jest dobrze odbierana, ponieważ pozwala deweloperom Ethereum uniknąć niedogodności związanych z bezpośrednią interakcją z blockchainem, ale wprowadza centralny punkt awarii dla 50000 dappsów i deweloperów, którzy na niej polegają. Z kolei Infura jest uzależniona od usług AWS w zakresie uruchamiania swoich węzłów.

[Eksperyment z pączkami](https://www.reddit.com/r/ethtrader/wiki/donuts) z /r/ethtrader, gdzie uczestnicy subreddita zbierają punkty na podstawie swojej subredditowej karmy i wykorzystują je do udziału w badaniach, przechodzi w kolejną [fazę](https://www.reddit.com/r/ethtrader/comments/c3f1ku/the_next_phase_for_donuts/). Przygotowano inteligentne kontrakty, które pozwolą na przeniesienie pączków na blockchai Ethereum, z niektórymi adminami ułatwiającymi proces po stronie Reddita. W miarę tego, jak pączki są "decentralizowane", sondaże mają stać się niewiążącymi głosami sygnalizacyjnymi, z powodu obaw społeczności o zarządzanie łańcuchem. Opierając się na komentarzach do ogłoszenia, wydaje się, że jest to wybór kontrowersyjny i istnieje pewne zamieszanie co do celu istnienia pączków.

Aragon [ukończył](https://blog.aragon.org/final-results-from-aragon-network-vote-3/) swoją trzecią rundę głosowania nad propozycją dotyczącą zarządzania. Złożono 11 propozycji, z których 8 zostało dopuszczonych do głosowania przez Stowarzyszenie Aragon. 7 z tych propozycji zostało przyjętych, wszystkie z 99% lub więcej głosów na "tak", 4 były jednogłośne (z 1 lub mniej tokenami ANT na "nie"). Frekwencja w ANT wyniosła średnio 2,6% w przypadku 8 wniosków.

[AGP-64](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-64.md) sygnalizuje poparcie dla "potajemnego zakończenia głosowania", co wydłużyłoby czas trwania głosowania w AGP, gdyby wynik głosowania gwałtowanie zmieniłby się pod koniec okresu głosowania. Jest to odpowiedź na [obserwację](https://www.evanvanness.com/post/184616403861/aragon-vote-shows-the-perils-of-onchain-governance), że późne głosowanie wieloryba wpłynęło na wynik poprzednich AGP. Propozycja ta nie określa konkretnej implementacji, ale sygnalizuje wsparcie dla środków, które mają być zainwestowane w rozwój potajemnego zakonczenia głosowania w projekcie Aragon.

[AGP-59](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-59.md) nakazuje minimalny czas trwania dyskusji na temat wniosków AGP. [AGP-70](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-70.md) sygnalizuje wsparcie dla przesunięcia zarządzania programem grantowym Nest ze Stowarzyszenia Aragon do DAO, a AGP-71 rozszerza budżet programu Nest o 600K DAI i 300K ANT. [AGP-73](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-73.md) jest największą propozycją budżetu, z dalszym finansowaniem stadnym dla Autark w wysokości 1,6 mln DAI i 487K ANT na okres jednego roku. W odrzuconym wniosku wezwano do opracowania rodzimej aplikacji mobilnej do głosowania w Aragon.

Dash [zakończył](https://blog.dash.org/the-dash-investment-foundation-supervisor-election-results-96a28309744b) pierwsze coroczne wybory na stanowiska nadzorców Fundacji Inwestycyjnej Dash, wykorzystując do tego celu [pewne oprogramowanie](https://blog.dash.org/trust-protector-election-software-93ed67c7455b) napisane do tego celu właśnie.

Kolejna runda procesu nowelizacji protokołu Tezos jest w toku, po tym, jak propozycja Brest złożona przez TzScan Baker nie doprowadziła do uzyskania wystarczającej liczby głosów potrzebnej do przejścia dalej. 26 lipca Cryptium Labs [wstrzyknęło](https://blog.nomadic-labs.com/babylon-proposal-injected.html) propozycję zwaną Babylon, przygotowaną wspólnie z Nomadic Labs, a następnie zmieniło jej wersję na 2.0 w dniu 2 sierpnia. Propozycja ta wprowadziłaby szereg zmian w protokole, w tym nowy wariant algorytmu konsesusowego i nowe funkcje Michelsona, a także wprowadziłaby nowy wymóg dotyczący kworum propozycji, który uniemożliwiłby przejście propozycji z największą liczbą głosów do drugiej fazy, o ile nie uzyskałaby ona poparcia co najmniej 5% puli. Pozwoliłoby to na wcześniejsze odrzucenie wniosków o niewielkim poparciu (takich jak Brest), a następnie szybsze wznowienie cyklu wniosków.

Zespół ds. zdecentralizowanego protokołu wymiany danych 0x [ogłosił](https://blog.0xproject.com/shut-down-of-0x-exchange-v2-0-contract-and-migration-to-patched-version-6185097a1f39), że zewnętrzny badacz zgłosił podatność na zagrożenia bezpieczeństwa i na wszelki wypadek zamknął kontrakt wymiany. Strumień inteligentnych kontraktów 0x został naprawiony i ponownie wdrożony następnego dnia.

StopAndDecrypt opublikował [przegląd](https://medium.com/hackernoon/betterhash-decentralizing-bitcoin-mining-with-new-hashing-protocols-291de178e3e0) sposobów, w jaki pule górnicze mogą nadużywać powierzonej im mocy obliczeniowej i przedstawił argumenty przemawiające za BetterHash - roboczą nazwą alternatywnych protokołów wydobywczych, których celem jest zwrócenie mocy poszczególnym górnikom i pulom wydobywczym ich wpływu.

Do biblioteki Ruby [wkradł się](https://nakedsecurity.sophos.com/2019/07/09/backdoor-discovered-in-ruby-strong_password-library/) backdoor sprawdzający siłę haseł. Wstrzyknięte złośliwe oprogramowanie pobiera i uruchamia kod z pastebin.com, dając napastnikom moc zdalnego wykonywania kodu. Ironia polega na tym, że owo porwanie było możliwe, ponieważ autor biblioteki sprawdzającej siłę hasła miał [słabe i ponownie użyte hasło](https://news.ycombinator.com/item?id=20382779) i nie miał 2FA na swoim koncie RubyGems. Ważne jest, aby kontrolować zależności w świecie, w którym powszechne jest ślepe wciąganie dziesiątek lub setek zależności przy użyciu zautomatyzowanych narzędzi.

Sieć serwerów kluczy OpenPGP padła ofiarą [ataku zalania certyfikatami](https://gist.github.com/rjhansen/67ab921ffb4084c865b3618d6955275f). Ktoś wrzucił tonę certyfikatów dla kluczy publicznych dwóch dostawców GnuPG, skutecznie "zatruwając" je. Każdy, kto spróbuje zaimportować zatruty klucz do podatnej instalacji, ryzykuje, że ich klucz nie będzie nadawał się do użytku z powodu ogromnej degradacji wydajności. Błędy w projektowaniu sieci serwerów kluczy były znane od dłuższego czasu. Sieć zasadniczo utrzymuje zdecentralizowaną, odporną na cenzurę bazę danych, ale bez solidnej ochrony przed nadużyciami. W ciągu ponad dekady istnienia tej luki sieć nie była w stanie koordynować rozwoju i wdrożyć aktualizacji. To po raz kolejny przypomina nam, jak trudne jest zaprojektowanie odpornego, zdecentralizowanego protokołu i jak ważne jest, aby zdecentralizowana sieć posiadała mechanizm zarządzania, który pozwoli jej na wdrażanie zmian.

## O tym wydaniu

To 16. wydanie Decred Journal. Spis wszystkich wydań, mirrorów i tłumaczeń dostępny jest [tutaj](https://xaur.github.io/decred-news/).

Większość informacji od stron trzecich jest przekazywana bezpośrednio ze źródła po minimalnym sprawdzeniu poprawności. Autorzy Decred Journal nie mają możliwości zweryfikowania wszystkich publikowanych stwierdzeń. Proszę uważać na oszustwa i przeprowadzać własny research.

Wasze [komentarze](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) oraz [wkład](https://github.com/xaur/decred-news/blob/docs/contributing.md) są zawsze mile widziane.

Zasługi (kolejność alfabetyczna):

* redakcja treści: bee, cryptoleslie, degeri, Dustorf, lukebp, raedah, richardred, s\_ben
* recenzje i komentarze: chappjc, davecgh, jholdstock, jy-p, margaret\_mei, matheusd
