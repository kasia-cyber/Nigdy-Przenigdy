# Nigdy-Przenigdy
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <title>Nigdy Przenigdy - Gra</title>
  <link rel="icon" href="https://cdn-icons-png.flaticon.com/512/3771/3771518.png" type="image/png">
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;500;700&display=swap" rel="stylesheet">
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Outfit', sans-serif;
      background: linear-gradient(135deg, #4f46e5, #9333ea);
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      padding: 20px;
    }
    h1 {
      font-weight: 700;
      font-size: 2.5em;
      margin-bottom: 30px;
      text-shadow: 0 4px 8px rgba(0,0,0,0.2);
    }
    #question-box {
      max-width: 700px;
      text-align: center;
      font-size: 1.5em;
      background-color: rgba(255,255,255,0.1);
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.3);
      backdrop-filter: blur(10px);
      min-height: 150px;
      transition: opacity 0.5s ease;
      opacity: 1;
    }
    #controls {
      margin-top: 30px;
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
      justify-content: center;
    }
    select, button {
      padding: 12px 24px;
      font-size: 1em;
      border-radius: 12px;
      border: none;
      cursor: pointer;
      background-color: rgba(255,255,255,0.2);
      color: #fff;
      backdrop-filter: blur(5px);
      transition: background 0.3s ease, color 0.3s ease;
    }
    button:hover, select:hover {
      background-color: rgba(255,255,255,0.35);
      color: #000;
    }
    select option {
      color: #000;
      background-color: #fff;
    }
  </style>
</head>
<body>
  <h1>Nigdy Przenigdy</h1>
  <div id="question-box">Wybierz kategorię i kliknij "Losuj kolejne"</div>

  <div id="controls">
    <select id="category-select" onchange="resetHistory()">
      <option value="MIX">MIX</option>
      <option value="Klasyczne">Klasyczne</option>
      <option value="Pikantne">Pikantne</option>
      <option value="Zabawne">Zabawne</option>
      <option value="Nietypowe">Nietypowe</option>
      <option value="Dorośli">Dla dorosłych (18+)</option>
      <option value="Trendy">Trendy</option>
    </select>
    <button onclick="drawQuestion()">Losuj kolejne</button>
  </div>

  <script src="questions.js"></script>
  <script>
    const questions = {"Klasyczne": [
    "Nigdy przenigdy nie zaspałem do pracy.",
    "Nigdy przenigdy nie złamałem kości.",
    "Nigdy przenigdy nie zgubiłem telefonu.",
    "Nigdy przenigdy nie jechałem stopem.",
    "Nigdy przenigdy nie miałem mandatu.",
    "Nigdy przenigdy nie zapomniałem czyichś urodzin.",
    "Nigdy przenigdy nie śpiewałem pod prysznicem.",
    "Nigdy przenigdy nie byłem w szpitalu.",
    "Nigdy przenigdy nie uciekłem z lekcji.",
    "Nigdy przenigdy nie pomyliłem dnia tygodnia.",
    "Nigdy przenigdy nie zgubiłem się w innym mieście.",
    "Nigdy przenigdy nie jadłem owadów.",
    "Nigdy przenigdy nie pisałem ściągi.",
    "Nigdy przenigdy nie zrobiłem sobie selfie.",
    "Nigdy przenigdy nie zgubiłem kluczy.",
    "Nigdy przenigdy nie rozlałem napoju na kogoś.",
    "Nigdy przenigdy nie złamałem diety.",
    "Nigdy przenigdy nie powiedziałem \"kocham\" przez pomyłkę.",
    "Nigdy przenigdy nie uciekłem z domu.",
    "Nigdy przenigdy nie poszedłem nieprzygotowany na egzamin.",
    "Nigdy przenigdy nie zjadłem całej pizzy sam.",
    "Nigdy przenigdy nie śmiałem się na pogrzebie.",
    "Nigdy przenigdy nie zalałem telefonu wodą.",
    "Nigdy przenigdy nie zgubiłem paszportu.",
    "Nigdy przenigdy nie zapomniałem tekstu piosenki w trakcie śpiewania.",
    "Nigdy przenigdy nie płakałem na filmie.",
    "Nigdy przenigdy nie zrobiłem czegoś głupiego dla zakładu.",
    "Nigdy przenigdy nie byłem na imprezie do rana.",
    "Nigdy przenigdy nie zasnąłem w miejscu publicznym.",
    "Nigdy przenigdy nie mówiłem przez sen.",
    "Nigdy przenigdy nie spóźniłem się na ważne spotkanie.",
    "Nigdy przenigdy nie śmiałem się tak, że bolał mnie brzuch.",
    "Nigdy przenigdy nie byłem w telewizji.",
    "Nigdy przenigdy nie używałem fałszywego nazwiska.",
    "Nigdy przenigdy nie siedziałem na dachu.",
    "Nigdy przenigdy nie jadłem śniadania na obiad.",
    "Nigdy przenigdy nie wysłałem wiadomości do złej osoby.",
    "Nigdy przenigdy nie mówiłem do siebie na głos.",
    "Nigdy przenigdy nie zostałem wyrzucony z lekcji.",
    "Nigdy przenigdy nie myliłem kogoś z kimś innym.",
    "Nigdy przenigdy nie zgubiłem się w galerii handlowej.",
    "Nigdy przenigdy nie wpadłem do wody w ubraniach.",
    "Nigdy przenigdy nie próbowałem jeździć na deskorolce.",
    "Nigdy przenigdy nie przegapiłem przystanku.",
    "Nigdy przenigdy nie zasnąłem na filmie w kinie.",
    "Nigdy przenigdy nie zostałem zatrzymany przez policję.",
    "Nigdy przenigdy nie nosiłem czegoś na lewą stronę.",
    "Nigdy przenigdy nie zrobiłem sobie zdjęcia w lustrze.",
    "Nigdy przenigdy nie rozbiłem niczego w sklepie.",
    "Nigdy przenigdy nie byłem w muzeum."
  ],
  "Pikantne": [
    "Nigdy przenigdy nie całowałem się na pierwszej randce.",
    "Nigdy przenigdy nie wysłałem komuś odważnego zdjęcia.",
    "Nigdy przenigdy nie spałem nago.",
    "Nigdy przenigdy nie flirtowałem z nauczycielem.",
    "Nigdy przenigdy nie byłem na randce w ciemno.",
    "Nigdy przenigdy nie miałem przygody na jedną noc.",
    "Nigdy przenigdy nie pisałem pikantnych wiadomości.",
    "Nigdy przenigdy nie całowałem się z więcej niż jedną osobą tego samego dnia.",
    "Nigdy przenigdy nie byłem w klubie ze striptizem.",
    "Nigdy przenigdy nie przyłapano mnie nago.",
    "Nigdy przenigdy nie zakochałem się w przyjacielu.",
    "Nigdy przenigdy nie miałem randki z aplikacji.",
    "Nigdy przenigdy nie mówiłem komuś 'kocham cię' dla żartu.",
    "Nigdy przenigdy nie miałem randki z więcej niż jedną osobą w tygodniu.",
    "Nigdy przenigdy nie zrobiłem masażu z podtekstami.",
    "Nigdy przenigdy nie uprawiałem seksu w nietypowym miejscu.",
    "Nigdy przenigdy nie byłem zakochany w osobie niedostępnej.",
    "Nigdy przenigdy nie spałem u kogoś po pierwszym spotkaniu.",
    "Nigdy przenigdy nie rozebrałem się przed kamerą.",
    "Nigdy przenigdy nie miałem kaca miłosnego.",
    "Nigdy przenigdy nie flirtowałem dla korzyści.",
    "Nigdy przenigdy nie miałem swojej listy 'top 5'.",
    "Nigdy przenigdy nie fantazjowałem o nauczycielu.",
    "Nigdy przenigdy nie robiłem striptizu.",
    "Nigdy przenigdy nie miałem przygody wakacyjnej.",
    "Nigdy przenigdy nie próbowałem seksownego przebrania.",
    "Nigdy przenigdy nie czytałem erotycznej książki.",
    "Nigdy przenigdy nie zrobiłem nagiego selfie.",
    "Nigdy przenigdy nie byłeś zazdrosny o byłego partnera.",
    "Nigdy przenigdy nie miałem randki w nietypowym miejscu.",
    "Nigdy przenigdy nie odebrałem telefonu podczas seksu.",
    "Nigdy przenigdy nie udawałem, że śpię, by uniknąć rozmowy.",
    "Nigdy przenigdy nie powiedziałem 'kocham cię' przez przypadek.",
    "Nigdy przenigdy nie miałem sekretnych randek.",
    "Nigdy przenigdy nie miałem seksualnego snu o znajomym.",
    "Nigdy przenigdy nie widziałem kogoś nago przez przypadek.",
    "Nigdy przenigdy nie pocałowałem kogoś publicznie.",
    "Nigdy przenigdy nie miałem wpadki z garderobą.",
    "Nigdy przenigdy nie powiedziałem czegoś sprośnego przez pomyłkę.",
    "Nigdy przenigdy nie byłem zakochany w dwóch osobach naraz.",
    "Nigdy przenigdy nie fantazjowałem o sławnym celebrycie.",
    "Nigdy przenigdy nie dostałem miłosnego listu.",
    "Nigdy przenigdy nie pocałowałem się z osobą tej samej płci.",
    "Nigdy przenigdy nie podglądałem kogoś.",
    "Nigdy przenigdy nie flirtowałem z szefem.",
    "Nigdy przenigdy nie zakochałem się przez internet.",
    "Nigdy przenigdy nie miałem marzeń erotycznych o znajomym.",
    "Nigdy przenigdy nie rozmawiałem o seksie z rodzicem.",
    "Nigdy przenigdy nie miałem erotycznego koszmaru."
  ],
  "Zabawne": [
    "Nigdy przenigdy nie upadłem publicznie i udawałem, że to było celowe.",
    "Nigdy przenigdy nie powiedziałem \"kocham cię\" do zwierzaka.",
    "Nigdy przenigdy nie zrobiłem miny do lustra w toalecie publicznej.",
    "Nigdy przenigdy nie udawałem, że rozmawiam przez telefon, by uniknąć rozmowy.",
    "Nigdy przenigdy nie zjadłem czegoś, co spadło na podłogę.",
    "Nigdy przenigdy nie zaśmiałem się w złym momencie.",
    "Nigdy przenigdy nie mówiłem do siebie jak do innej osoby.",
    "Nigdy przenigdy nie zrobiłem głupiego selfie w miejscu publicznym.",
    "Nigdy przenigdy nie udawałem akcentu, by zaimponować komuś.",
    "Nigdy przenigdy nie wysłałem głupiego mema nie tej osobie.",
    "Nigdy przenigdy nie grałem w gry mobilne w toalecie.",
    "Nigdy przenigdy nie naśladowałem celebryty przed lustrem.",
    "Nigdy przenigdy nie zasnąłem podczas rozmowy.",
    "Nigdy przenigdy nie udawałem, że jestem kimś innym w internecie.",
    "Nigdy przenigdy nie opowiadałem żartu, którego nikt nie zrozumiał.",
    "Nigdy przenigdy nie zgubiłem się w centrum handlowym jako dorosły.",
    "Nigdy przenigdy nie miałem dziwnej rozmowy ze zwierzakiem.",
    "Nigdy przenigdy nie pomyliłem kogoś z celebrytą.",
    "Nigdy przenigdy nie tańczyłem bez muzyki.",
    "Nigdy przenigdy nie powiedziałem \"na zdrowie\" komuś, kto nie kichnął.",
    "Nigdy przenigdy nie zrobiłem żartu z własnego nazwiska.",
    "Nigdy przenigdy nie podśpiewywałem sobie w sklepie.",
    "Nigdy przenigdy nie użyłem dziecięcego głosu dla zabawy.",
    "Nigdy przenigdy nie krzyczałem do telewizora podczas meczu.",
    "Nigdy przenigdy nie udawałem, że gram na gitarze powietrznej.",
    "Nigdy przenigdy nie biegałem jak ninja po domu.",
    "Nigdy przenigdy nie grałem w berka jako dorosły.",
    "Nigdy przenigdy nie zrobiłem czegoś głupiego tylko po to, by kogoś rozśmieszyć.",
    "Nigdy przenigdy nie wysłałem wiadomości sam do siebie.",
    "Nigdy przenigdy nie rozmawiałem z przedmiotem, jakby był człowiekiem.",
    "Nigdy przenigdy nie udawałem zombie w domu.",
    "Nigdy przenigdy nie nagrałem siebie tańczącego.",
    "Nigdy przenigdy nie udawałem chorego, żeby nie wyjść z domu.",
    "Nigdy przenigdy nie rozmawiałem z lustrem.",
    "Nigdy przenigdy nie udawałem reklamy w łazience.",
    "Nigdy przenigdy nie śpiewałem w stylu operowym dla żartu.",
    "Nigdy przenigdy nie zakładałem ubrań na lewą stronę celowo.",
    "Nigdy przenigdy nie opowiadałem historii z wymyślonym zakończeniem.",
    "Nigdy przenigdy nie mówiłem do roślin.",
    "Nigdy przenigdy nie udawałem superbohatera.",
    "Nigdy przenigdy nie miałem wyimaginowanego przyjaciela po 10. roku życia.",
    "Nigdy przenigdy nie naśladowałem głosów z kreskówek.",
    "Nigdy przenigdy nie zrobiłem sobie sesji zdjęciowej z kubkiem kawy.",
    "Nigdy przenigdy nie próbowałem chodzić jak model na wybiegu.",
    "Nigdy przenigdy nie mówiłem sam do siebie w trzeciej osobie.",
    "Nigdy przenigdy nie przebierałem się dla żartu w domu.",
    "Nigdy przenigdy nie przebrałem się za coś dziwnego na Halloween.",
    "Nigdy przenigdy nie próbowałem mówić jak robot przez cały dzień.",
    "Nigdy przenigdy nie zagrałem w grę udając, że jestem postacią z bajki.",
    "Nigdy przenigdy nie udawałem narratora własnego życia."
  ],
  "Nietypowe": [
    "Nigdy przenigdy nie rozmawiałem z lustrem, które mi odpowiedziało.",
    "Nigdy przenigdy nie udawałem kanapki.",
    "Nigdy przenigdy nie myślałem, że mój kot ma supermoce.",
    "Nigdy przenigdy nie śpiewałem hymnów do lodówki.",
    "Nigdy przenigdy nie bałem się banana.",
    "Nigdy przenigdy nie myślałem, że jestem postacią z bajki.",
    "Nigdy przenigdy nie pytałem ryby o pogodę.",
    "Nigdy przenigdy nie próbowałem teleportować się z zamkniętymi oczami.",
    "Nigdy przenigdy nie udawałem, że mam niewidzialnego bliźniaka.",
    "Nigdy przenigdy nie nazywałem swojego nosa imieniem.",
    "Nigdy przenigdy nie mówiłem do butów, żeby szybciej chodziły.",
    "Nigdy przenigdy nie udawałem, że mój telefon to tost.",
    "Nigdy przenigdy nie planowałem randki dla dwóch kaktusów.",
    "Nigdy przenigdy nie myślałem, że jestem w Matrixie.",
    "Nigdy przenigdy nie robiłem prezentacji dla swojego psa.",
    "Nigdy przenigdy nie próbowałem latać z ręcznikiem jak peleryną.",
    "Nigdy przenigdy nie myślałem, że widzę ducha z serem.",
    "Nigdy przenigdy nie wyobrażałem sobie bitwy na poduszki w kosmosie.",
    "Nigdy przenigdy nie próbowałem porozumieć się z sygnalizatorem.",
    "Nigdy przenigdy nie nazwałem swojego kubka 'Stefan'.",
    "Nigdy przenigdy nie gadałem z drzwiami, prosząc je o otwarcie.",
    "Nigdy przenigdy nie myślałem, że ziemniak patrzy na mnie podejrzliwie.",
    "Nigdy przenigdy nie śpiewałem serenady do pizzy.",
    "Nigdy przenigdy nie planowałem ślubu z czekoladą.",
    "Nigdy przenigdy nie prowadziłem talk-show z pluszakami.",
    "Nigdy przenigdy nie udawałem, że jestem kapitanem statku na wannie.",
    "Nigdy przenigdy nie rozmawiałem z cieniem.",
    "Nigdy przenigdy nie próbowałem przekonać kota, że jestem jednym z nich.",
    "Nigdy przenigdy nie prowadziłem wywiadu z doniczką.",
    "Nigdy przenigdy nie myślałem, że umiem mówić językiem kosmitów.",
    "Nigdy przenigdy nie komentowałem serialu jak sportowego meczu.",
    "Nigdy przenigdy nie udawałem lodówki.",
    "Nigdy przenigdy nie pisałem listu do siebie w przyszłości, żeby zapytać o pogodę.",
    "Nigdy przenigdy nie chciałem adoptować chmurki.",
    "Nigdy przenigdy nie myślałem, że mój cień ma własne życie.",
    "Nigdy przenigdy nie szukałem teleportu w szafie.",
    "Nigdy przenigdy nie próbowałem przekonać lustra, że jestem jego szefem.",
    "Nigdy przenigdy nie chciałem rozmawiać z drzewem o polityce.",
    "Nigdy przenigdy nie wyobrażałem sobie, że jestem postacią z reklamy szamponu.",
    "Nigdy przenigdy nie podejrzewałem, że mój kubek mnie osądza.",
    "Nigdy przenigdy nie myślałem, że jestem we śnie innej osoby.",
    "Nigdy przenigdy nie jadłem zupy wyobraźni.",
    "Nigdy przenigdy nie udawałem, że jestem owocem.",
    "Nigdy przenigdy nie sądziłem, że drzwi się na mnie obraziły.",
    "Nigdy przenigdy nie żartowałem z własnym odbiciem.",
    "Nigdy przenigdy nie prowadziłem dziennika dla mojej skarpetki.",
    "Nigdy przenigdy nie robiłem próbnych przemówień do tłumu poduszek.",
    "Nigdy przenigdy nie chciałem zamieszkać w pudełku po butach.",
    "Nigdy przenigdy nie przekonywałem siebie, że jestem lodem."
  ],
  "Dorośli": [
    "Nigdy przenigdy nie wysłałem nagiego zdjęcia.",
    "Nigdy przenigdy nie miałem przygody na jedną noc.",
    "Nigdy przenigdy nie fantazjowałem o kimś w tej sali.",
    "Nigdy przenigdy nie uprawiałem seksu w miejscu publicznym.",
    "Nigdy przenigdy nie przebrałem się w kostium podczas zbliżenia.",
    "Nigdy przenigdy nie oglądałem filmu dla dorosłych z kimś innym.",
    "Nigdy przenigdy nie próbowałem zabawy z kajdankami.",
    "Nigdy przenigdy nie używałem zabawek erotycznych.",
    "Nigdy przenigdy nie miałem randki przez aplikację typu Tinder.",
    "Nigdy przenigdy nie flirtowałem z nauczycielem.",
    "Nigdy przenigdy nie uprawiałem seksu telefonicznego.",
    "Nigdy przenigdy nie chodziłem nago po mieszkaniu z gośćmi w środku.",
    "Nigdy przenigdy nie udawałem orgazmu.",
    "Nigdy przenigdy nie fantazjowałem o kimś niedozwolonym.",
    "Nigdy przenigdy nie miałem zbliżenia w samochodzie.",
    "Nigdy przenigdy nie wyszedłem z randki, zostawiając osobę bez słowa.",
    "Nigdy przenigdy nie pocałowałem dwóch osób w ten sam wieczór.",
    "Nigdy przenigdy nie uczestniczyłem w grze erotycznej.",
    "Nigdy przenigdy nie byłem nago poza domem.",
    "Nigdy przenigdy nie spałem w łóżku z więcej niż jedną osobą naraz.",
    "Nigdy przenigdy nie miałem wpadki związanej z seksem.",
    "Nigdy przenigdy nie użyłem jedzenia w łóżku.",
    "Nigdy przenigdy nie mówiłem brudnych rzeczy podczas seksu.",
    "Nigdy przenigdy nie udawałem kogoś innego dla przyjemności.",
    "Nigdy przenigdy nie miałem erotycznego snu o kimś znajomym.",
    "Nigdy przenigdy nie widziałem kogoś nago przez przypadek.",
    "Nigdy przenigdy nie powiedziałem 'kocham cię' tylko po to, żeby coś zdobyć.",
    "Nigdy przenigdy nie miałem więcej niż jednego partnera w tym samym czasie.",
    "Nigdy przenigdy nie poszedłem na randkę tylko dla seksu.",
    "Nigdy przenigdy nie usunąłem wiadomości, żeby ukryć flirt.",
    "Nigdy przenigdy nie dostałem nagiej fotki od nieznajomej osoby.",
    "Nigdy przenigdy nie miałem seksu na plaży.",
    "Nigdy przenigdy nie korzystałem z aplikacji randkowej wyłącznie dla seksu.",
    "Nigdy przenigdy nie całowałem się z przyjacielem tylko z ciekawości.",
    "Nigdy przenigdy nie zasnąłem nago w miejscu publicznym.",
    "Nigdy przenigdy nie myślałem o byłym podczas zbliżenia.",
    "Nigdy przenigdy nie miałem erotycznego koszmaru.",
    "Nigdy przenigdy nie flirtowałem z kimś zajętym.",
    "Nigdy przenigdy nie fantazjowałem o osobie publicznej.",
    "Nigdy przenigdy nie myliłem imienia partnera w łóżku.",
    "Nigdy przenigdy nie eksperymentowałem z kimś tej samej płci.",
    "Nigdy przenigdy nie związałem kogoś (albo siebie) dla zabawy.",
    "Nigdy przenigdy nie prowadziłem rozmowy erotycznej przez SMS.",
    "Nigdy przenigdy nie całowałem kogoś tylko dla zakładu.",
    "Nigdy przenigdy nie uczestniczyłem w imprezie typu 'prawda czy wyzwanie 18+'.",
    "Nigdy przenigdy nie korzystałem z aplikacji erotycznej.",
    "Nigdy przenigdy nie opowiadałem zmyślonej historii erotycznej.",
    "Nigdy przenigdy nie widziałem swoich znajomych nago.",
    "Nigdy przenigdy nie włączyłem porno w nieodpowiednim momencie."
  ],
  "Trendy": [
    "Nigdy przenigdy nie zrobiłem TikToka, którego później żałowałem.",
    "Nigdy przenigdy nie skasowałem posta, bo nie miał wystarczająco lajków.",
    "Nigdy przenigdy nie porównałem się do influencera w internecie.",
    "Nigdy przenigdy nie napisałem komentarza z fejkowego konta.",
    "Nigdy przenigdy nie udostępniłem fake newsa.",
    "Nigdy przenigdy nie odświeżałem feedu przez godzinę bez celu.",
    "Nigdy przenigdy nie dałem się złapać na clickbait.",
    "Nigdy przenigdy nie zrobiłem sobie selfie w lustrze na siłowni.",
    "Nigdy przenigdy nie wyłączyłem powiadomień, żeby nie widzieć rzeczywistości.",
    "Nigdy przenigdy nie pisałem z AI jak z człowiekiem.",
    "Nigdy przenigdy nie zacząłem czegoś tylko dlatego, że to trend na TikToku.",
    "Nigdy przenigdy nie śledziłem kogoś w sieci bez dodania do znajomych.",
    "Nigdy przenigdy nie miałem kryzysu egzystencjalnego przez social media.",
    "Nigdy przenigdy nie zablokowałem znajomego po kłótni politycznej.",
    "Nigdy przenigdy nie wstydziłem się starego posta sprzed lat.",
    "Nigdy przenigdy nie miałem fazy na inwestowanie w krypto.",
    "Nigdy przenigdy nie kłóciłem się z kimś online o politykę.",
    "Nigdy przenigdy nie udawałem, że wiem więcej niż wiem (Google w tle).",
    "Nigdy przenigdy nie zamknąłem komputera, bo bałem się rachunku za prąd.",
    "Nigdy przenigdy nie odinstalowałem aplikacji, żeby \"żyć zdrowiej\".",
    "Nigdy przenigdy nie wyłączyłem reklamy z zazdrości.",
    "Nigdy przenigdy nie nagrałem czegoś tylko po to, żeby wrzucić to na stories.",
    "Nigdy przenigdy nie miałem ulubionego mema politycznego.",
    "Nigdy przenigdy nie bałem się mówić na głos o swoich poglądach.",
    "Nigdy przenigdy nie udostępniłem czegoś, czego nie przeczytałem do końca.",
    "Nigdy przenigdy nie miałem zjazdu, bo porównałem swoje życie do czyjegoś Insta.",
    "Nigdy przenigdy nie przesunąłem budzika przez scrollowanie do późna.",
    "Nigdy przenigdy nie śmiałem się z teorii spiskowej, a potem... się bałem.",
    "Nigdy przenigdy nie zrobiłem konta, żeby podglądać bez śladu.",
    "Nigdy przenigdy nie przestałem obserwować influencera, bo \"za dużo mówił o polityce\".",
    "Nigdy przenigdy nie miałem problemu z fake kontem podszywającym się pode mnie.",
    "Nigdy przenigdy nie wkurzyłem się przez algorytmy.",
    "Nigdy przenigdy nie miałem cichej nadziei, że viral odmieni moje życie.",
    "Nigdy przenigdy nie skomentowałem czegoś politycznego, by później tego żałować.",
    "Nigdy przenigdy nie podałem błędnych informacji w dyskusji, by \"wygrać\".",
    "Nigdy przenigdy nie zastanawiałem się, czy social media mnie podsłuchują.",
    "Nigdy przenigdy nie kupiłem czegoś, bo widziałem to u influencera.",
    "Nigdy przenigdy nie miałem paranoi przez newsy.",
    "Nigdy przenigdy nie próbowałem rozkminić inflacji i zrezygnowałem.",
    "Nigdy przenigdy nie zapisałem się na newsletter i żałowałem po 5 minutach.",
    "Nigdy przenigdy nie udawałem, że oglądałem film, bo wszyscy go znali.",
    "Nigdy przenigdy nie miałem dość YouTube’a, ale dalej oglądałem.",
    "Nigdy przenigdy nie ukryłem lajków na Instagramie.",
    "Nigdy przenigdy nie zmieniłem zdania przez komentarz obcego w sieci.",
    "Nigdy przenigdy nie zaufałem opinii z internetu bardziej niż własnej mamie.",
    "Nigdy przenigdy nie kliknąłem \"kup teraz\" bez sprawdzenia ceny.",
    "Nigdy przenigdy nie udawałem, że coś mi się podoba, żeby nie wyjść na boomera.",
    "Nigdy przenigdy nie poczułem się staro przez nowy trend.",
    "Nigdy przenigdy nie sprawdziłem konta exa, mimo że nie chciałem.",
    "Nigdy przenigdy nie zrobiłem czegoś tylko \"dla contentu\"."
  ]
};


    let usedQuestions = [];

    function resetHistory() {
      usedQuestions = [];
    }

    function drawQuestion() {
      const box = document.getElementById('question-box');
      const selected = document.getElementById('category-select').value;
      let pool = [];

      if (typeof questions === 'undefined') return;

      if (selected === 'MIX') {
        Object.values(questions).forEach(arr => pool.push(...arr));
      } else {
        pool = [...questions[selected]];
      }

      const available = pool.filter(q => !usedQuestions.includes(q));

      box.style.opacity = 0;
      setTimeout(() => {
        if (available.length === 0) {
          usedQuestions = [];
          box.innerText = "Koniec pytań! Zaczynamy od nowa.";
        } else {
          const index = Math.floor(Math.random() * available.length);
          const selectedQuestion = available[index];
          usedQuestions.push(selectedQuestion);
          box.innerText = selectedQuestion;
        }
        box.style.opacity = 1;
      }, 300);
    }
  </script>
</body>
</html>
