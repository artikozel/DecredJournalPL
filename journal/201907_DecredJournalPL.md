# Decred Journal – July 2019

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

W lipcu [Skarbiec](https://explorer.dcrdata.org/address/Dcur2mcGjmENx4DhNqDctW5wJCVyT3Qeqkx) otrzymał 15517 DCR i wydał 10344 DCR. Wykorzystując dzienną średnią dzienną stawkę DCR/USD w lipcu, wynoszącą 28,97 USD, jesto to odpowiednio 450 tys. dolarów USD i 300 tys. dolarów. Są to opłaty za pracę wykonaną w czerwcu po stawce w wysokości 28,90 dolarów, więc kwota na fakturze jest prawie taka sama. Na dzień 1 sierpnia saldo Skarbca wynosi 627 514 DCR (16,8 mln USD po kursie 26,75 USD).

W lipcu złożono 2 nowe propozycje:

* [Faza 1 - badania nad fundamentalnymi metrykami Decred](https://proposals.decred.org/proposals/78b50f218106f5de40f9bd7f604b048da168f2afbec32c8662722b70d62e4d36) autorstwa @Checkmate, nowego współpracownika, wnoszącego o 12 tys. dolarów na 3-miesięczną pracę nad badaniami i obecnością w mediach społecznościowych, plus 2000 dolarów za wcześniej wykonaną pracę (nad artykułem o [zabezpieczeniach pieniężnych](https://medium.com/@_Checkmatey_/monetary-premiums-can-altcoins-compete-with-bitcoin-54c97a92c6d4)). Głosowanie zostało zakończone, a wniosek został zatwierdzony przy 92% poparciu.

* [TinyDecred: A Python Toolkit for Decred](https://proposals.decred.org/proposals/20e967dad9e7398901decf3cfe0acf4e0853f6558a62607265c63fe791b8b124), aut. @buck54321, wykonawcy pracującego nad dcrdata w zeszłym roku, który wnosi o 8 tys. dolarów za pracę już wykonaną nad TinyDecred, zestawem narzędzi do interakcji z blockchainem Decred napisanym w jęz. Python. Głosowanie nad propozycją otwarto 6 sierpnia, obecnie ma 89% poparcia.

Kolejne 5 propozycji zostało złożonych w sierpniu, 4 dotyczące animatorów rynku i 1 związana z rozwojem DEX. Najbliższe wydanie magazynu Politeia Digest omówi je dogłębnie a ponadto zostaną one również omówione w sierpniowym wydaniu Dziennika.

[Wydanie 19](https://medium.com/politeia-digest/issue-19-june-30-july-31-2019-c591fcb79d98) Politeia Digest zawiera więcej szczegółów na temat lipcowej działalności propozycyjnej i dyskusji.

Przygotowano [zbiór danych](https://github.com/RichardRed0x/pi-research/blob/master/data/comments-and-updown-votes/pi-users.csv) i [krótki raport](https://github.com/RichardRed0x/pi-research/blob/master/analysis/comments-and-updown-votes/users-review.md), który agreguje dane Politei na podstawie nazwy użytkownika, dając dokładne dane liczbowe dotyczące tego, jak często każdy użytkownik komentował i głosował oraz tego, jak dobrze jego komentarze zostały ocenione.

## Sieć

Hashrate: lipcowy hashrate na początku miesiąca wyniósł ~503 Ph/s a zamknął miesiąc w ok. ~583 Ph/s, zaliczając niż w ok. 319 Ph/s oraz szczyt w wys. 687 Ph/s w ciągu miesiąca. Dystrybucja mocy obliczeniowej na 2 sierpnia wyglądała następująco: F2Pool 21%, UUPool 19%, lab.antpool.com 16,5%, Poolin 9,5%, BTC.com 7,3%, Luxor 2,2%, BeePool 0,14%, Coinmine 0,12%, suprnova 0,08% i pozostałę 24%, za danymi z [dcrstats.com](https://dcrstats.com/pow). Są to liczby jedynie szacunkowe i nie można ich dokładnie określić.

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

[Everstake](https://everstake.one/), provider of staking services, [announced](https://medium.com/everstake/welcome-decred-voting-on-everstake-b2d0371426ad) the launch of their Decred VSP at [decred.everstake.one](https://decred.everstake.one/).

[Exodus](https://www.exodus.io/) wallet [gained](https://twitter.com/exodus_io/status/1148593861549334528) Trezor support for managing and exchanging of DCR.

[Vertbase](https://www.vertbase.com/), an exchange offering DCR with a fiat gateway, [announced](https://twitter.com/vertbase/status/1147840898564120577) that they will be starting a foundation. An interesting event in the space, the foundation will donate to the development of projects that Vertbase lists and supports, and have its board composed of volunteer core team members from these project.

[MixinNetwork](https://twitter.com/Mixin_Network/status/1153272304790433793) integrated Decred. From their [website](https://mixin.one/), "Mixin is a publicly distributed ledger aimed to help other publicly distributed ledgers gain trillions of TPS, achieve sub second final confirmations, zero transaction fees, enhanced privacy, and unlimited extensibility.".

Warning: the authors of Decred Journal have no idea about the trustworthiness of any of the services above. Please do your own research before trusting your personal information or assets to any entity.

## Adoption

Portuguese unprocessed honeybee products maker DrApis [announced](https://twitter.com/drapiscom/status/1146539277028909058) that they accept DCR.

Blockhead Capital [announced](https://twitter.com/jyashouafar/status/1152238301593657344) their investment in Decred and shared a [research paper](https://www.blockheadcap.com/post/decred-investment-thesis). Their conclusion:

> Decred is an adaptive cryptocurrency with a rigid monetary policy. The rigid monetary policy provides the base required to achieve monetary premium while the adaptive nature of its on-chain governance allows for integration of more dynamic features. The hybrid consensus mechanism creates adequate checks and balances between the various ecosystem parties while eliminating contentious hardforks as the primary method to resolve disputes - a highly desirable feature for an aspiring global reserve asset. Further, the hybrid consensus creates for more secure blockspace, making the blockspace more valuable, and provides for a more censorship resistant currency. Decred iterates on Bitcoin's strengths and shores up many of its shortcomings, putting it in a position to complement or compete with it as a digital store of value.

## Outreach

Infrastructure continued to build in July that will help Decred streamline outreach and education. The website update is close to complete, and should be live by the end of August with new subpages on Decred's Security, Adaptability, Self-Funding, and History. Additionally, we've agreed upon a schema and are currently assembling a resource repository building on Max Bronstein's [Canon](https://github.com/maxbron08/Decred-Canon) that will help form a natural funnel of learning for people taking the #DecredChallenge.

In order to achieve this, we're slightly refining the messaging, focusing largely on the fundamental principles of Decred, as all messaging flows from there. That will appear in chat within the next week for community input. Other resources for the community that have been in the works include the Social Media Playbook, featuring best practices for how to engage with others in a constructive way that reflects well on Decred and helps educate others about the project.

Additionally, a Community Organizer Handbook will be shared for community input shortly. This well help clarify roles and responsibilities in order to gain alignment, improve efficiency, and share best practices around the world. Along these lines, Decred is looking for geographic marketing leads to help run areas of the world. Various proposals from different regions are in the works, and should hit Politeia in the next couple of months. We are still looking for leaders in Europe and Asia, so join us in #marketing or #local\_ops in Matrix to discuss helping to decentralize the organization.

We're also working to coordinate a week-long events blitz in October featuring various Decred community members in some of the most important cities across Asia. Details should be released within the next month.

Decred in Depth episodes featuring [Murad Mahmudov](https://soundcloud.com/decredindepth/murad-mahmudov-dcr-investment-thesis-sov-narrative-crypto-economics) and [Permabull Nino](https://soundcloud.com/decredindepth/ep-5-decred-as-strong-accounting-ticket-metrics-with-permabull-nino) were released which were very well received and created a lot of chatter about Decred on social media.

Ditto's July achievements:

* Escalated our work with various community members on strategies and tactics for engaging in a productive/educational way on Twitter.
* Built out a wider list of Decred spokespeople, along with a new wish list of media targets.
* Strategized with the community on how to best build visibility for the Decred tagline.
* Secured four interviews, and will share more details when published.
* Secured an article in financial advisory newsletter, Legacy Research, as a result of an interview we hosted with @moo31337.
* Secured a 10-minute segment on [BlockTV](https://blocktv.com/watch/2019-07-30/5d404e65ea3f5-decred-s-jake-yocom-piatt-talks-decentralized-governance) with @jy-p discussing his take on Libra and how Decred's progress towards becoming a DAO.
* Secured publication of @jy-p's byline on Libra in [CCN](https://www.ccn.com/news/libra-friend-or-foe/2019/07/21/).
* Worked with the community to amplify/engage with the [#DEX tweet storm](https://twitter.com/decredproject/status/1156652694502817793) announcing Decred's DEX spec.
* Began a messaging refresh, adding FAQs to counter common misunderstandings.
* Put the finishing touches on the schema for an educational resources repository for the Decred website that makes it easier for journalists and newbies to find out about us in one place.
* Put together a long-term media relations plan that targets all of Decred's audiences (investors, developers, crypto enthusiasts), as well as media who haven't covered Decred in the past.
* Did media training refresher with @jy-p to prepare for broadcast interviews.

## Events

Attended:

* Jul 4-5 - [Blockchain Summit Latam](https://twitter.com/Decred_ES/status/1146093986806976513) - Mexico City, Mexico. Ana Dalia [represented](https://twitter.com/AnaDaliacd23/status/1146873685229416450) Decred. After the conference there was a [dinner](https://twitter.com/Decred_ES/status/1147522846513618945) sponsored by Decred.
* Jul 10 - [Decred meetup](https://twitter.com/Decred_BR/status/1147201276058505216) - São Paulo, Brazil. Organized by @guisso.
* Jul 10 - [StakingCon](https://twitter.com/BlockBeatsChina/status/1147570186519638017) - Beijing, China. @Dominic "managed to charm the organizer to slot in a Decred video and particpated in the roundtable discussion". Organized by @BlockBeatsChina. ([photos](https://twitter.com/DecredCN/status/1148983482732830720))
* Jul 11 - [Staked US event](https://twitter.com/staked_us/status/1148687292032323584) - New York, USA. Fireside chat with @joshuam, co-hosted by Staked and TokenTax.
* Jul 19 - Meetup - Buenos Aires, Argentina. The meetup was a preparation for the upcoming Crypto Monday on Aug 12. [@Camilolwi](https://twitter.com/Camilolwi) [presented](https://twitter.com/cryptorocketok/status/1152260099072778240) Decred. Hosted by [Crypto Rocket Group](https://twitter.com/cryptorocketok).
* Jul 21 - [OKEx meetup](https://twitter.com/wanbihou/status/1151704823533723648) - Qingdao, China. Chat with @Dominic.
* Jul 25 - [Computational Law + Blockchain Festival CDMX 2019](https://twitter.com/LegalHackersMX/status/1153832499333795840) - Mexico City, Mexico. @elian [represented](https://twitter.com/elianhuesca/status/1154452590983299073) the project.
* Jul 25-26 - Cointime Summit 2019 - Ho Chi Minh City, Vietnam. Duyen Em introduced Decred to individuals in the conference area. Some guest speakers from other projects were already familiar and spoke highly of Decred, but most Vietnamese speakers are just learning about it. Duyen Em suggests that Decred deserves a much bigger presence in the thriving cryptocurrency space of Vietnam and shares ideas for establishing connections and growing the community. Full report will be published on Reddit.
* Jul 28 - Vietnam Staking Economy - Ho Chi Minh City, Vietnam. Duyen Em represented Decred and answered questions to many young people interested in cryptocurrencies. The details are in the report for Cointime Summit.
* Jul 31 - [Open Banking Summit](https://theopenbankingsummit.com/) preliminary meetup - Mexico City, Mexico. @elian represented the project and [gave a talk](https://twitter.com/elianhuesca/status/1157313830969630725) on Decred. The summit will start on Nov 13.

Upcoming:

* Aug 8 - [Blockchain Bajio](https://www.eventbrite.com/e/blockchain-bajio-2do-meetup-tickets-66510186759) - Leon, Guanajuato, Mexico.
* Aug 12 - [Crypto Monday](https://www.meetup.com/Bitcoin-Argentina/events/263594472) - Buenos Aires, Argentina. Crypto Monday is a monthly event hosted at Espacio Bitcoin, a local coworking space with a strong bond with the main Argentina Bitcoin NGO, Bitcoin Argentina.
* Aug 13-14 - [Futurist Conference](https://eventmobi.com/futurist/) - Toronto, Canada. Decred announced as a sponsor and has a slot on the [panel](https://twitter.com/decredproject/status/1157416657670868997) "Blockchain Social Impact & Governance for Good", where @zubair will represent the project.
* Aug 16-18 - [Campus Party Natal](https://brasil.campus-party.org/campus-party-natal/) - Natal, Brazil. @guisso will talk about how Decred works as an organization.
* Aug 20 - [Crypto Alchemy: Mining and Staking Decred](https://www.meetup.com/Philadelphia-Technology-for-Blockchain-and-Cryptocurrency/events/ffssfryzlbbc/) - Philadelphia, USA. Hosted by [@mikeghen](https://twitter.com/mikeghen/status/1155594343702511616).
* Aug 28 - [Blockchain Bootcamp](https://www.blockchainbootcamp.net/) - Docklands, Australia. @zohand and co have been [invited](https://matrix.to/#/!aNPTuiryMFmdMQWUzb:decred.org/$15644812201506dzVgU:decred.org) to run a blockchain governance event as part of one of the main streams. The event is part of the annual [Digital Innovation Festival](https://dif.vic.gov.au/) hosted by Victorian State Government.
* Sep 30 - Oct 1 - [Voice of Blockchain](https://twitter.com/BlockchainVoice/status/1154772731575099392) - Chicago, USA. @jy-p will present a keynote "Why Direct Sovereignty & Multi-Stakeholder Inclusive Governance Will Last".
* Nov 4-7 - [Websummit](https://websummit.com/) - Lisbon, Portugal. @moo31337 will speak on a panel TBD, and Decred will have a 2x2m exhibit booth.

## Media

Selected articles:

* Decred: What Gold and Bitcoin Wanted to Be by Pascal Thellmann ([seekingalpha.com](https://seekingalpha.com/instablog/49962360-pascal-thellmann/5324856-decred-gold-bitcoin-wanted))
* Monetary Premiums, Can Altcoins Compete with Bitcoin? by @Checkmate ([medium](https://medium.com/@_Checkmatey_/monetary-premiums-can-altcoins-compete-with-bitcoin-54c97a92c6d4))
* Libra: Friend or Foe? by @jy-p ([ccn.com](https://www.ccn.com/news/libra-friend-or-foe/2019/07/21/))
* Bitcoin & Decred / Historical Documents of a Digital Financial Revolution by BlackBearXVII ([medium](https://medium.com/@imagnusholdings/bitcoin-decred-historical-documents-of-a-digital-financial-revolution-4debfa0d10d9))
* Sovereign (Crypto) Networks by Joel Monegro ([placeholder.vc](https://www.placeholder.vc/blog/2019/7/31/lvhpfydo4m3uoezhwhicyxo06og0mn)) - mentions Decred as an example
* Introduction to Crypto-Accounting: An Analysis of Decred as an Accounting System by Permabull Nino ([medium](https://medium.com/@permabullnino/introduction-to-crypto-accounting-an-analysis-of-decred-as-an-accounting-system-4d3e67fce28))
* Blockhead Capital: Decred Investment Thesis ([blockheadcap.com](https://www.blockheadcap.com/post/decred-investment-thesis))

Translations:

* @Dominic translated the whole [Decred DEX spec](https://github.com/decred/dcrdex/blob/master/README.mediawiki) draft into [Chinese](https://github.com/DominicTing/dcrdexStandard-CN-/blob/master/README.mediawiki). The link was submitted to Chinese Binance [info page](https://info.binance.com/cn/currencies/decred).
* May and June issues of Decred Journal were translated to Arabic (@arij), Chinese (@Dominic, @guang, @changhugo), Italian and Russian (@DZ), Polish (@kozel) and Vietnamese (Duyen Em). Thank you all.

Videos:

* Libra: Friend or Foe? - @jy-p interview on [Block TV](https://blocktv.com/watch/2019-07-30/5d404e65ea3f5-decred-s-jake-yocom-piatt-talks-decentralized-governance)

Audio:

* Decred in Depth Ep. 4 Murad Mahmudov - DCR Investment Thesis + SoV Narrative + Crypto Economics ([libsyn](https://decredindepth.libsyn.com/murad-mahmudov-dcr-investment-thesis-sov-narrative-crypto-economics-0), [soundcloud](https://soundcloud.com/decredindepth/murad-mahmudov-dcr-investment-thesis-sov-narrative-crypto-economics), [twitter](https://twitter.com/decredproject/status/1150836740665552896))
* Decred in Depth Ep. 5 Permabull Nino - Decred as Strong Accounting + Ticket Metrics ([libsyn](https://decredindepth.libsyn.com/ep-5-decred-as-strong-accounting-ticket-metrics-with-permabull-nino-0), [twitter](https://twitter.com/decredproject/status/1157000762611896320))
* POV Crypto: Decred: Splitting the Difference Between Bitcoin and Ethereum with Luke Powell ([medium](https://medium.com/@TrustlessState/decred-splitting-the-difference-between-bitcoin-and-ethereum-with-luke-powell-758cf6e1218d), [libsyn](http://povcryptopod.btc.libsynpro.com/decred-splitting-the-difference-between-bitcoin-and-ethereum))
* The Sound Money Podcast: On-Chain Atomic Swaps with @joshuam ([spotify](https://open.spotify.com/episode/1SuzMUUmtm6xR7ofGN6t4a), [itunes](https://podcasts.apple.com/us/podcast/the-sound-money-podcast/id1470774235?i=1000443695629))

## Community Discussions

Comm systems news:

* [chat.decred.org](https://chat.decred.org/) now hosts the Riot web client for the Matrix protocol. There are multiple [advantages](https://github.com/decredcommunity/issues/issues/62) of self-hosted Riot. The most visible one is that the link is easy to remember and sets you up faster than the [onboarding page](https://decred.org/matrix/) - new people were often confused about setting the homeserver correctly. Less obvious benefit is that it helps to stay connected during incidents like the matrix.org server compromise reported [in April](201904.md). Finally, the [privacy](https://github.com/decredcommunity/issues/issues/25) is increased by removing Google recaptcha fingerprinting from the registration page and reducing the traffic to external domains. Not every project can afford to self-host such infrastructure and be autonomous. Huge thanks to our admin wizards.
* Riot users are now enjoying reactions and can edit their messages, following the [release](https://medium.com/@RiotChat/%EF%B8%8Fmessage-editing-%EF%B8%8F-reactions-5cffec8f71a2) of new versions. Riot users please be aware that editing your messages will replay them across the bridge to people using Slack and Discord.

Selected topics:

* The #DecredChallenge [started](https://twitter.com/_Checkmatey_/status/1145764832362319872) on Jul 1 when @Checkmate challenged Bitcoiners to spend a month looking into Decred and come out believing it should not be #2, inviting people who are not persuaded of its merits to engage in a debate about it. It [evolved](https://twitter.com/RichardRed0x/status/1146132909713240065) [quickly](https://twitter.com/_Checkmatey_/status/1146136667448913921) into a meme, got a [hash tag](https://twitter.com/Ammarooni/status/1146171552213479425), and then (thanks mostly to @Checkmate) it grew into a tweet course of reasons why Decred merits serious investigation (see below).
* Another [article](https://bravenewcoin.com/insights/decred-price-analysis-a-sustained-increase-in-mining-activity-2) was published which described Decred as a "Bitcoin fork", likely based on the use of this term in descriptions on [CoinMarketCap](https://coinmarketcap.com/currencies/decred/) and [Messari](https://messari.io/asset/decred) (which, to be fair, uses the more limited "Bitcoin codebase fork"). This is a mischaracterization which frustrates the community because "Bitcoin fork" would usually be interpreted to mean a coin which forked the Bitcoin Core software and/or BTC UTXO set - neither of which are true in Decred's case. "Bitcoin fork" does not reflect the fact that Decred's software was created from scratch by the same people who launched Decred, beginning its life as btcd, an independent Go implementation of a Bitcoin full node. @lukebp [tweeted](https://twitter.com/lukebp_/status/1155886623147429889) about this and received a response from Messari, @Checkmate [expanded](https://twitter.com/_Checkmatey_/status/1155901635257929728) on @lukebp's comment to produce another chapter in the #DecredChallenge.
* @Ammarooni took the #DecredChallenge and came out with some [concerns](https://twitter.com/Ammarooni/status/1148013517016113152) about attack vectors related to stakeholder liability for illegal proposals and the susceptibility of the LLC to seizure of funds. @lukebp and @jz responded with an explanation of how Decred is moving towards a full DAO and how this will address the issues.
* The subject of whether to change the name for Decred's smallest units (atoms) or to integrate "credits" in the names for another denomination came up on [Twitter](https://twitter.com/OfficialCryptos/status/1151603316167720960) and was discussed in chats and in this GitHub [issue](https://github.com/decredcommunity/issues/issues/129). Developers pointed out that "atom" is used thousands of times in the Decred codebase, which discouraged some proponents of the change but not others.

@Checkmate has been very active on Twitter and generating good engagement around the #DecredChallenge and #DontSleepOnDecred hashtags, here are some highlights:

* [Announcement](https://twitter.com/_Checkmatey_/status/1148682397875167233) of the Monetary Premiums article
* [Not a Bitcoin fork](https://twitter.com/_Checkmatey_/status/1155901635257929728)
* [Skin in the game](https://twitter.com/_Checkmatey_/status/1148354974390390784)
* [The hedge](https://twitter.com/_Checkmatey_/status/1149560942654414848) for Bitcoiners and Ethereuns
* [Differentiate](https://twitter.com/_Checkmatey_/status/1150831105081298944) where it matters
* [Treasury Fund](https://twitter.com/_Checkmatey_/status/1157342578787913733)
* [Politeia Proposals](https://twitter.com/_Checkmatey_/status/1156293040509739010)
* [A digital organism](https://twitter.com/_Checkmatey_/status/1155567971823226881) designed to deliver the most resilient sound money

Other selected tweets:

* #DecredChallenge: Find an engineering team that takes the challenge of [limiting its own power](https://twitter.com/RichardRed0x/status/1146917561751212032) and influence as seriously as Company 0 has done with Decred
* Chris Burniske on what got him [interested](https://twitter.com/lefebvre_dustin/status/1156316679040901125) in the Decred project
* Decred's hybrid PoW + PoS [enables](https://twitter.com/NoahPierau/status/1155466908738686977) 3 formal governance mechanisms
* The Decred Journal is now being [circulated](https://twitter.com/Binance_Info/status/1153575996487954432) on Binance Info

@lukebp's Decred investment thesis in one [tweet](https://twitter.com/lukebp_/status/1154398108538658816):

> Technological change is hard to predict. A protocol needs to be able to adapt to those changes. The people making decisions about those changes should be the people with skin in the game, i.e. the stakeholders.

Selected Reddit threads:

* Decred [community growth](https://www.reddit.com/r/decred/comments/c9xtml/decred_community_growth/)
* I am a [time-traveler from the future](https://www.reddit.com/r/decred/comments/c9jxml/i_am_a_timetraveler_from_the_future_here_to_beg/), here to beg you to continue what you are doing
* [Suggestion](https://www.reddit.com/r/decred/comments/casb4b/decred_project_live_chat_infrastructure/) to remove #random chat room
* Format to keep an eye and discuss [past proposals](https://www.reddit.com/r/decred/comments/cb7g8g/general_is_there_an_optimal_rdecred_format_that/); reporting, Reddit-like forum, language of doing
* The balance between privacy of individual [contractor payments](https://www.reddit.com/r/decred/comments/cf773y/discussion_per_delivery_vs_per_hour/) and transparency for stakeholders
* Whether stakers can ensure that a block with a [double spend](https://www.reddit.com/r/decred/comments/cgz12h/in_a_scenario_in_which_a_miner_submits_a_block/) is not validated and the role of stakers in preventing majority/51% attacks
* Decred's [governance model](https://www.reddit.com/r/decred/comments/cirkvr/decreds_governance_model/); it's hard to add governance after launch
* Why Decred Wins in the End? [Incrementalism](https://www.reddit.com/r/decred/comments/cc8c0h/why_decred_wins_in_the_end_incrementalism/)
* Can [Flair](https://www.reddit.com/r/decred/comments/ch0gey/governance_can_flair_increase_the_odds_of/) increase the odds of self-guided education on r/decred?
* David Ogilvy talks [Direct Response Advertising](https://www.reddit.com/r/decred/comments/ci82iy/david_ogilvy_talks_direct_response_advertising/); targeting groups that share our values and value sovereignty as high as we do
* What [metaphor/analogy](https://www.reddit.com/r/decred/comments/cc40hb/general_what_metaphoranalogy_helps_you_understand/) helps you understand different actors within the project?

## Markets

In July DCR was trading between USD 25.20-35.64 / BTC 0.00262-0.00296. The average daily rate was $28.97.

After brefiely making a run for USD 13,000, Bitcoin price went down and has been mostly bobbing the USD 10,000 mark most of July.

## Relevant External

Chris Burniske of Placeholder VC (holders of Decred and Zcash) provided a good [summary](https://forum.zcashcommunity.com/t/placeholder-considerations-resources-governance-and-legitimacy-in-nu4/34045) of the situation facing the Zcash community as the founders reward expires, advocating for a continuation of 20% block reward to fund project development for another 4 years, with a split of 70% to "Protocol Development" and 30% to "Growth Funds".

Zooko Wilcox published a [personal letter](https://medium.com/@zooko_25893/a-personal-letter-about-the-possibility-of-a-new-zcash-dev-fund-f6d30df64392) about the possibility of a new Zcash dev fund, which explains that he always knew that the time would come when funding would run out and create a problem that could only be solved through a "messy and difficult process" such as the Zcash community is currently going through. Zooko stated again that he cannot be the one to make the decision and that it should come from the community, but as the CEO of ECC he has considerable influence in the community, and the community has no established method of making decisions.

All of the various options being considered have been helpfully summarized in this [megathread](https://forum.zcashcommunity.com/t/future-of-zcash-dev-funding-megathread-everything-in-one-place/34063). As Chris Burniske remarked in his post, the first question is how to make the decision about the decision in a way which is perceived as legitimate. Given time constraints Chris advocates the use of polling to gauge preference for the various options, with a final decision made using the ECC and Zcash Foundation 2-of-2 multisig. Zooko stated that the ECC will announce a method of decision-making in early Aug.

Nebulous, the company building the Sia network, announced the [completion](https://sia.tech/funding2019) of a $3.25 million seed round with participation by a number of venture capitalists.

Funding has also been the subject of some discussion in the Ethereum community, with more [attention](https://research.circle.com/insights/the-great-ethereum-funding-debate) being paid to [EIP-2025](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2025.md), which would add 0.0055 ETH per block for 18 months (17K ETH in total) to fund ETH 1.X development (as the main developers focus on ETH 2.0). The block rewards would be used to pay back a loan which the teams working in 4 different areas would receive to multisig contract addresses.

As with any controversial Ethereum Improvement Proposal, it is difficult for outsiders to know if EIP-2025 will go anywhere. A [tweet](https://twitter.com/VitalikButerin/status/1154733914881179648) from Vitalik stating that it seems to have little support probably indicates that it won't be included in the Istanbul hard fork.

Another Circle Research [article](https://research.circle.com/insights/degrees-of-architectural-decentralization-to-infura-and-beyond) published about Ethereum concerns the centrality of Infura, a service company created by Consensys which allows dapp developers to sidestep setting up and running their own nodes. The article considers the difficulty and increasing demands of running a full node (space requirements have increased 25-48% year to date) as causing a decrease in the number of full nodes from 12,000 in Dec 2018 to 8,000 in Jul 2019. Infura is welcome because it allows Ethereum developers to avoid the inconvenience of interfacing with the blockchain directly, but it introduces a central point of failure for the 50,000 dapps and developers who rely on it. Infura is in turn reliant on AWS services to run its nodes.

The /r/ethtrader [Donuts experiment](https://www.reddit.com/r/ethtrader/wiki/donuts), where subreddit participants earn points based on their subreddit karma and use these to participate in polls, is moving into another [phase](https://www.reddit.com/r/ethtrader/comments/c3f1ku/the_next_phase_for_donuts/). Smart contracts have been prepared which will allow Donuts to be moved to the Ethereum blockchain, and some Reddit admins are facilitating this on the Reddit end. As the Donuts are being "decentralized", the polls are to become non-binding signal votes, due to fears in the community about on-chain governance. This appears to be controversial choice, based on comments on the announcement, and there is some confusion about what the purpose of Donuts are.

Aragon [completed](https://blog.aragon.org/final-results-from-aragon-network-vote-3/) its 3rd round of governance proposal voting, 11 proposals were submitted and 8 were allowed to be included in the vote by the Aragon Association. 7 of these proposals were approved, all with 99% or greater yes votes, 4 were unanimous (with 1 or less ANT token voting no). ANT turnout was 2.6% averaged across the 8 proposals.

[AGP-64](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-64.md) signals support for Quiet Ending Voting, which would extend the duration of AGP voting if the outcome is flipped towards the end of the voting period. This is in response to the [observation](https://www.evanvanness.com/post/184616403861/aragon-vote-shows-the-perils-of-onchain-governance) that late voting by a whale had swayed the outcome of previous AGPs. This proposal does not specify a particular implementation but signals support for resources to be invested in developing quiet ending voting for Aragon.

[AGP-59](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-59.md) mandates a minimum length for discussion period on AGP submissions. [AGP-70](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-70.md) signals support for shifting management of the Nest grant program away from the Aragon Association and to a DAO, AGP-71 extended the budget of the Nest program by 600K DAI and 300K ANT. [AGP-73](https://github.com/aragon/AGPs/blob/master/AGPs/AGP-73.md) is the biggest budget proposal, with further flock funding for Autark of 1.6 million DAI and 487K ANT to cover one year. The rejected proposal called for development of a native mobile app for Aragon voting.

Dash [completed](https://blog.dash.org/the-dash-investment-foundation-supervisor-election-results-96a28309744b) the first annual elections for positions as supervisors of the Dash Investment Foundation, using some software custom [made](https://blog.dash.org/trust-protector-election-software-93ed67c7455b) for this purpose.

Another round of the Tezos protocol amendment process is underway, after the Brest proposal by TzScan Baker failed to achieve enough upvotes to progress. Cryptium Labs [injected](https://blog.nomadic-labs.com/babylon-proposal-injected.html) a proposal called Babylon, prepared jointly with Nomadic Labs, on Jul 26, then an amended version 2.0 on Aug 2. This proposal would make a number of changes to the protocol, including a new variant of the consensus algorithm and new Michelson features, and a new proposal quorum requirement would be introduced which would prevent the proposal with the most upvotes progressing to the second phase unless it has support from at least 5% of the stake. This would allow for proposals with little support (like Brest) to be rejected earlier, and the proposal cycle to restart more quickly thereafter.

The 0x decentralized exchange protocol team [announced](https://blog.0xproject.com/shut-down-of-0x-exchange-v2-0-contract-and-migration-to-patched-version-6185097a1f39) that a security vulnerability had been reported by a 3rd party security researcher, and shut down the exchange contract as a precaution. The 0x smart contract pipeline was patched and re-deployed the next day.

StopAndDecrypt published an [overview](https://medium.com/hackernoon/betterhash-decentralizing-bitcoin-mining-with-new-hashing-protocols-291de178e3e0) of ways how mining pools could abuse the hash power trusted to them and made the case for BetterHash - the working name for alternative mining protocols that aim to give the power back to individual miners and strip mining pools of their influence.

A backdoor [sneaked](https://nakedsecurity.sophos.com/2019/07/09/backdoor-discovered-in-ruby-strong_password-library/) into a Ruby library for checking password strength. The injected malware fetches and runs the code from pastebin.com, giving the attackers the power of remote code execution. The irony here is that the hijacking was possible because the author of the password strength checking library had [weak and reused password](https://news.ycombinator.com/item?id=20382779), and had no 2FA on his RubyGems account. It is important to audit dependencies in a world where it is getting common to blindly pull in dozens or hundreds of dependencies using automated tools.

The network of OpenPGP keyservers was subject to certificate flooding [attack](https://gist.github.com/rjhansen/67ab921ffb4084c865b3618d6955275f). Someone uploaded a ton of certifications for public keys of two GnuPG contributors, effectively "poisoning" them. Anyone who attempts to import a poisoned key into a vulnerable installation risks making their keyring unusable because of a massive performance degradation. Flaws of the keyserver network design were known for a long time. It basically maintains a decentralized censorship-resistant write-only database but with no robust abuse protection. During more than a decade of this vulnerability being known, the network was unable to coordinate the development and deployment of an upgrade. This once again reminds us how challenging it is to design a resilient decentralized protocol and how critical it is for a decentralized network to have a governance mechanism to adapt.

## About This Issue

This is issue 16 of Decred Journal. Index of all issues, mirrors and translations is available [here](https://xaur.github.io/decred-news/).

Most information from third parties is relayed directly from source after a minimal sanity check. The authors of Decred Journal have no ability to verify all claims. Please beware of scams and do your own research.

Your [feedback](https://github.com/xaur/decred-news/blob/docs/contributing.md#feedback) and [contributions](https://github.com/xaur/decred-news/blob/docs/contributing.md) are always welcome.

Credits (alphabetical order):

* writing and editing: bee, cryptoleslie, degeri, Dustorf, lukebp, raedah, richardred, s\_ben
* reviews and feedback: chappjc, davecgh, jholdstock, jy-p, margaret\_mei, matheusd
