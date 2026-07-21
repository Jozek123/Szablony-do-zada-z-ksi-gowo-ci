# Szablony_do_zadan_z_ksiegowosci
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Narzędzie Edukacyjne Księgowości - Konta T, Bilans, ZOS</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --accent-color: #3498db;
            --bg-color: #f4f6f9;
            --card-bg: #ffffff;
            --border-color: #bdc3c7;
            --danger-color: #e74c3c;
            --success-color: #2ecc71;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            margin: 0;
            padding: 20px;
            color: #333;
        }

        header {
            text-align: center;
            margin-bottom: 25px;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 10px;
        }

        nav {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 25px;
        }

        nav button {
            padding: 10px 20px;
            font-size: 16px;
            font-weight: bold;
            border: none;
            background-color: #e0e0e0;
            cursor: pointer;
            border-radius: 5px;
            transition: all 0.2s;
        }

        nav button.active {
            background-color: var(--primary-color);
            color: white;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .section-header {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            margin-top: 20px;
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .btn {
            padding: 8px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.2s;
        }

        .btn-primary { background-color: var(--accent-color); color: white; }
        .btn-success { background-color: var(--success-color); color: white; }
        .btn-danger { background-color: var(--danger-color); color: white; }
        .btn-sm { padding: 4px 8px; font-size: 12px; }

        /* KONTAT-OWE */
        .accounts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .t-account {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 6px;
            padding: 12px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            display: flex;
            flex-direction: column;
        }

        .t-account-header {
            display: flex;
            gap: 5px;
            margin-bottom: 10px;
            padding-bottom: 5px;
            border-bottom: 2px solid #333;
        }

        .t-account-header input {
            font-weight: bold;
            font-size: 15px;
            border: 1px solid #ccc;
            padding: 4px;
            width: 100%;
        }

        .t-body {
            display: flex;
            min-height: 180px;
            position: relative;
        }

        .t-column {
            flex: 1;
            padding: 0 5px;
            display: flex;
            flex-direction: column;
        }

        .t-column:first-child {
            border-right: 2px solid #333;
        }

        .col-title {
            text-align: center;
            font-weight: bold;
            font-size: 14px;
            border-bottom: 1px solid #aaa;
            padding-bottom: 3px;
            margin-bottom: 5px;
        }

        .operations-list {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .op-item {
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .op-item input {
            width: 100%;
            border: 1px solid #ddd;
            padding: 2px 4px;
            font-size: 13px;
        }

        .op-line {
            width: 100%;
            border-top: 1px solid #000;
            margin: 6px 0;
        }

        .op-line-double {
            width: 100%;
            border-top: 3px double #000;
            margin: 6px 0;
        }

        .col-controls {
            margin-top: 8px;
            display: flex;
            gap: 3px;
            flex-wrap: wrap;
        }

        /* BILANS */
        .bilans-container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .bilans-header-inputs {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
            background: #eef2f5;
            padding: 15px;
            border-radius: 5px;
        }

        .bilans-header-inputs div {
            display: flex;
            flex-direction: column;
            flex: 1;
        }

        .bilans-header-inputs label {
            font-weight: bold;
            font-size: 13px;
            margin-bottom: 5px;
        }

        .bilans-header-inputs input {
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        .bilans-tables {
            display: flex;
            gap: 20px;
            overflow-x: auto;
        }

        .bilans-col {
            flex: 1;
            min-width: 400px;
        }

        .bilans-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 13px;
        }

        .bilans-table th, .bilans-table td {
            border: 1px solid #ccc;
            padding: 5px 8px;
        }

        .bilans-table th {
            background: #2c3e50;
            color: white;
            text-align: center;
        }

        .row-group-A { font-weight: bold; background: #eaeded; }
        .row-group-B { font-weight: bold; background: #f2f4f4; }
        .row-sub { font-weight: 600; padding-left: 15px !important; }
        .row-detail { padding-left: 30px !important; color: #555; }
        .row-total { font-weight: bold; background: #d5dbdb; font-size: 14px; }

        .bilans-table input {
            width: 90px;
            text-align: right;
            padding: 3px;
            border: 1px solid #ccc;
        }

        /* ZOS (ZESTAWIENIE OBROTÓW I SALD) */
        .zos-container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .zos-table-wrapper {
            overflow-x: auto;
        }

        .zos-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 12px;
            margin-top: 15px;
        }

        .zos-table th, .zos-table td {
            border: 1px solid #000;
            padding: 4px;
            text-align: center;
        }

        .zos-table th {
            background: #e6e6e6;
        }

        .zos-table input {
            width: 95%;
            padding: 2px;
            border: 1px solid #ddd;
            font-size: 12px;
        }

        .zos-table input.acc-name {
            text-align: left;
        }

        .zos-table input.num {
            text-align: right;
        }

        .zos-total-row {
            font-weight: bold;
            background: #f0f0f0;
        }

        .status-msg {
            margin-top: 10px;
            padding: 10px;
            border-radius: 4px;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>

    <header>
        <h1>Platforma Edukacyjna Rachunkowości</h1>
        <p>Interaktywne narzędzie do nauki księgowości (Konta T-owe, Bilans, ZOS)</p>
    </header>

    <nav>
        <button class="active" onclick="showTab('konta')">Konta T-owe</button>
        <button onclick="showTab('bilans')">Bilans</button>
        <button onclick="showTab('zos')">Zestawienie Obrotów i Sald</button>
    </nav>

    <!-- TAB 1: KONTA T-OWE -->
    <div id="tab-konta" class="tab-content active">
        <div class="section-header">
            <h2>Konta bilansowe</h2>
            <button class="btn btn-success" onclick="addAccount('bilansowe')">+ Dodaj konto bilansowe</button>
        </div>
        <div id="container-bilansowe" class="accounts-grid"></div>

        <div class="section-header">
            <h2>Konta wynikowe</h2>
            <button class="btn btn-success" onclick="addAccount('wynikowe')">+ Dodaj konto wynikowe</button>
        </div>
        <div id="container-wynikowe" class="accounts-grid"></div>
    </div>

    <!-- TAB 2: BILANS -->
    <div id="tab-bilans" class="tab-content">
        <div class="bilans-container">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
                <h2>Sporządzanie Bilansu</h2>
                <button class="btn btn-primary" onclick="calculateBilans()">Przelicz Bilans</button>
            </div>

            <div class="bilans-header-inputs">
                <div>
                    <label>Nazwa jednostki:</label>
                    <input type="text" id="bilans-company" placeholder="np. ABC Sp. z o.o." oninput="updateBilansTitle()">
                </div>
                <div>
                    <label>Data bilansu:</label>
                    <input type="date" id="bilans-date" onchange="updateBilansTitle()">
                </div>
            </div>

            <div id="bilans-print-header" style="text-align: center; margin-bottom: 15px; font-weight: bold; font-size: 16px;">
                BILANS sporządzony na dzień: <span id="disp-date">--</span><br>
                Jednostka: <span id="disp-company">--</span>
            </div>

            <div class="bilans-tables">
                <!-- AKTYWA -->
                <div class="bilans-col">
                    <table class="bilans-table">
                        <thead>
                            <tr>
                                <th>AKTYWA</th>
                                <th>Wartość (zł)</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr class="row-group-A"><td>A. Aktywa trwałe</td><td><input type="number" id="akt_A" readonly></td></tr>
                            <tr class="row-sub"><td>I. Wartości niematerialne i prawne</td><td><input type="number" class="calc-akt-A" id="akt_A_I"></td></tr>
                            <tr class="row-sub"><td>II. Rzeczowe aktywa trwałe</td><td><input type="number" id="akt_A_II" readonly></td></tr>
                            <tr class="row-detail"><td>- środki trwałe</td><td><input type="number" class="calc-akt-A-II" id="akt_A_II_1"></td></tr>
                            <tr class="row-detail"><td>- środki trwałe w budowie</td><td><input type="number" class="calc-akt-A-II" id="akt_A_II_2"></td></tr>
                            <tr class="row-sub"><td>III. Należności długoterminowe</td><td><input type="number" class="calc-akt-A" id="akt_A_III"></td></tr>
                            <tr class="row-sub"><td>IV. Inwestycje długoterminowe</td><td><input type="number" id="akt_A_IV" readonly></td></tr>
                            <tr class="row-detail"><td>- nieruchomości</td><td><input type="number" class="calc-akt-A-IV" id="akt_A_IV_1"></td></tr>
                            <tr class="row-detail"><td>- długoterminowe aktywa finansowe</td><td><input type="number" class="calc-akt-A-IV" id="akt_A_IV_2"></td></tr>
                            <tr class="row-sub"><td>V. Długoterminowe rozliczenia międzyokresowe</td><td><input type="number" class="calc-akt-A" id="akt_A_V"></td></tr>

                            <tr class="row-group-B"><td>B. Aktywa obrotowe</td><td><input type="number" id="akt_B" readonly></td></tr>
                            <tr class="row-sub"><td>I. Zapasy</td><td><input type="number" class="calc-akt-B" id="akt_B_I"></td></tr>
                            <tr class="row-sub"><td>II. Należności krótkoterminowe</td><td><input type="number" id="akt_B_II" readonly></td></tr>
                            <tr class="row-detail"><td>a) z tytułu dostaw i usług (do 12 mies.)</td><td><input type="number" class="calc-akt-B-II" id="akt_B_II_1"></td></tr>
                            <tr class="row-detail"><td>b) z tytułu dostaw i usług (pow. 12 mies.)</td><td><input type="number" class="calc-akt-B-II" id="akt_B_II_2"></td></tr>
                            <tr class="row-sub"><td>III. Inwestycje krótkoterminowe</td><td><input type="number" id="akt_B_III" readonly></td></tr>
                            <tr class="row-detail"><td>- środki pieniężne w kasie i na rachunkach</td><td><input type="number" class="calc-akt-B-III" id="akt_B_III_1"></td></tr>
                            <tr class="row-sub"><td>IV. Krótkoterminowe rozliczenia międzyokresowe</td><td><input type="number" class="calc-akt-B" id="akt_B_IV"></td></tr>

                            <tr class="row-group-A"><td>C. Należne wpłaty na kapitał podstawowy</td><td><input type="number" class="calc-akt-tot" id="akt_C"></td></tr>
                            <tr class="row-group-A"><td>D. Udziały (akcje) własne</td><td><input type="number" class="calc-akt-tot" id="akt_D"></td></tr>

                            <tr class="row-total"><td>AKTYWA RAZEM</td><td><input type="number" id="akt_SUMA" readonly></td></tr>
                        </tbody>
                    </table>
                </div>

                <!-- PASYWA -->
                <div class="bilans-col">
                    <table class="bilans-table">
                        <thead>
                            <tr>
                                <th>PASYWA</th>
                                <th>Wartość (zł)</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr class="row-group-A"><td>A. Kapitał (fundusz) własny</td><td><input type="number" id="pas_A" readonly></td></tr>
                            <tr class="row-sub"><td>I. Kapitał (fundusz) podstawowy</td><td><input type="number" class="calc-pas-A" id="pas_A_I"></td></tr>
                            <tr class="row-sub"><td>II. Kapitał (fundusz) zapasowy</td><td><input type="number" class="calc-pas-A" id="pas_A_II"></td></tr>
                            <tr class="row-sub"><td>III. Kapitał z aktualizacji wyceny</td><td><input type="number" class="calc-pas-A" id="pas_A_III"></td></tr>
                            <tr class="row-sub"><td>IV. Pozostałe kapitały rezerwowe</td><td><input type="number" class="calc-pas-A" id="pas_A_IV"></td></tr>
                            <tr class="row-sub"><td>V. Zysk (strata) z lat ubiegłych</td><td><input type="number" class="calc-pas-A" id="pas_A_V"></td></tr>
                            <tr class="row-sub"><td>VI. Zysk (strata) netto</td><td><input type="number" class="calc-pas-A" id="pas_A_VI"></td></tr>
                            <tr class="row-sub"><td>VII. Odpisy z zysku netto (ujemna)</td><td><input type="number" class="calc-pas-A" id="pas_A_VII"></td></tr>

                            <tr class="row-group-B"><td>B. Zobowiązania i rezerwy na zobowiązania</td><td><input type="number" id="pas_B" readonly></td></tr>
                            <tr class="row-sub"><td>I. Rezerwy na zobowiązania</td><td><input type="number" class="calc-pas-B" id="pas_B_I"></td></tr>
                            <tr class="row-sub"><td>II. Zobowiązania długoterminowe</td><td><input type="number" class="calc-pas-B" id="pas_B_II"></td></tr>
                            <tr class="row-sub"><td>III. Zobowiązania krótkoterminowe</td><td><input type="number" id="pas_B_III" readonly></td></tr>
                            <tr class="row-detail"><td>a) kredyty i pożyczki</td><td><input type="number" class="calc-pas-B-III" id="pas_B_III_1"></td></tr>
                            <tr class="row-detail"><td>b) z tytułu dostaw i usług (do 12 mies.)</td><td><input type="number" class="calc-pas-B-III" id="pas_B_III_2"></td></tr>
                            <tr class="row-detail"><td>c) fundusze specjalne</td><td><input type="number" class="calc-pas-B-III" id="pas_B_III_3"></td></tr>
                            <tr class="row-sub"><td>IV. Rozliczenia międzyokresowe</td><td><input type="number" class="calc-pas-B" id="pas_B_IV"></td></tr>

                            <tr class="row-total"><td>PASYWA RAZEM</td><td><input type="number" id="pas_SUMA" readonly></td></tr>
                        </tbody>
                    </table>
                </div>
            </div>
            <div id="bilans-status" class="status-msg"></div>
        </div>
    </div>

    <!-- TAB 3: ZESTAWIENIE OBROTÓW I SALD -->
    <div id="tab-zos" class="tab-content">
        <div class="zos-container">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
                <h2>Zestawienie Obrotów i Sald (ZOS)</h2>
                <div>
                    <button class="btn btn-success" onclick="addZosRow()">+ Dodaj wiersz</button>
                    <button class="btn btn-primary" onclick="calculateZOS()">Przelicz SUMĘ</button>
                </div>
            </div>

            <div style="margin-bottom: 15px;">
                <label><strong>Data sporządzenia:</strong> </label>
                <input type="date" id="zos-date" onchange="updateZOSTitle()">
            </div>

            <h3 id="zos-header-title" style="text-align: center;">
                Zestawienie obrotów i sald kont księgi głównej sporządzone na dzień: <span id="zos-disp-date">--</span>
            </h3>

            <div class="zos-table-wrapper">
                <table class="zos-table" id="zos-table">
                    <thead>
                        <tr>
                            <th rowspan="2" style="width: 220px;">Nazwa konta</th>
                            <th colspan="2">Salda na dzień otwarcia ksiąg</th>
                            <th colspan="2">Obroty za okres sprawozdawczy</th>
                            <th colspan="2">Obroty narastająco od początku roku</th>
                            <th colspan="2">Salda na koniec okresu sprawozdawczego</th>
                            <th rowspan="2">Akcja</th>
                        </tr>
                        <tr>
                            <th>Dt</th><th>Ct</th>
                            <th>Dt</th><th>Ct</th>
                            <th>Dt</th><th>Ct</th>
                            <th>Dt</th><th>Ct</th>
                        </tr>
                    </thead>
                    <tbody id="zos-body">
                        <!-- Wiersze generowane dynamicznie -->
                    </tbody>
                    <tfoot>
                        <tr class="zos-total-row">
                            <td>SUMA</td>
                            <td id="zos-s1">0</td><td id="zos-s2">0</td>
                            <td id="zos-s3">0</td><td id="zos-s4">0</td>
                            <td id="zos-s5">0</td><td id="zos-s6">0</td>
                            <td id="zos-s7">0</td><td id="zos-s8">0</td>
                            <td></td>
                        </tr>
                    </tfoot>
                </table>
            </div>
        </div>
    </div>

    <script>
        // SLOWNIK PLANU KONT (NA PODSTAWIE ZDJĘĆ)
        const PLAN_KONT = {
            "010": "Środki trwałe",
            "010-1": "Grunty",
            "010-2": "Budynki, lokale, obiekty inżynierii",
            "010-3": "Urządzenia techniczne i maszyny",
            "010-4": "Środki trwałe - Środki transportu",
            "010-5": "Inne środki trwałe",
            "020": "Wartości niematerialne i prawne",
            "030": "Inwestycje długoterminowe",
            "030-1": "Nieruchomości inwestycyjne",
            "030-2": "Inwestycje w WNiP",
            "030-3": "Udziały i akcje w innych jednostkach",
            "030-4": "Inne długoterminowe papiery wartościowe",
            "030-5": "Inne długoterminowe aktywa finansowe",
            "070": "Umorzenie środków trwałych",
            "070-4": "Umorzenie środków transportu",
            "075": "Umorzenie wartości niematerialnych i prawnych",
            "080": "Środki trwałe w budowie",
            "099": "Konta pozabilansowe",
            "100": "Kasa",
            "130": "Rachunki bankowe podstawowe",
            "130-1": "Rachunek bieżący",
            "130-2": "Rachunek VAT",
            "132": "Rachunki bankowe pomocnicze",
            "133": "Lokaty bankowe",
            "134": "Kredyty bankowe",
            "134-1": "Kredyty bankowe - długoterminowe",
            "134-2": "Kredyty bankowe - krótkoterminowe",
            "139": "Środki pieniężne w drodze",
            "140": "Pozostałe krótkoterminowe aktywa finansowe",
            "160": "Udziały (akcje) własne",
            "200": "Rozrachunki z odbiorcami",
            "202": "Rozrachunki z dostawcami",
            "220": "Rozrachunki publicznoprawne",
            "220-1": "Rozrachunki z tytułu VAT",
            "220-4": "Rozrachunki z ZUS",
            "221": "Rozliczenie VAT należnego i naliczonego",
            "230": "Rozrachunki z tytułu wynagrodzeń",
            "234": "Pozostałe rozrachunki z pracownikami",
            "240": "Rozrachunki z tytułu nabycia i rozchodu aktywów",
            "241": "Udzielone pożyczki",
            "242": "Otrzymane pożyczki",
            "300": "Rozliczenie zakupu",
            "310": "Materiały",
            "330": "Towary",
            "400": "Amortyzacja",
            "401": "Zużycie materiałów i energii",
            "402": "Usługi obce",
            "403": "Podatki i opłaty",
            "404": "Wynagrodzenia",
            "405": "Ubezpieczenia społeczne i inne świadczenia",
            "409": "Pozostałe koszty rodzajowe",
            "490": "Rozliczenie kosztów rodzajowych",
            "500": "Koszty działalności podstawowej",
            "540": "Koszty sprzedaży",
            "550": "Koszty ogólnego zarządu",
            "600": "Wyroby (produkty)",
            "600-1": "Wyroby (produkty) gotowe",
            "640": "Rozliczenia międzyokresowe",
            "700": "Przychody ze sprzedaży produktów",
            "711": "Koszt wytworzenia sprzedanych produktów",
            "730": "Przychody ze sprzedaży towarów",
            "731": "Wartość sprzedanych towarów",
            "750": "Przychody finansowe",
            "751": "Koszty finansowe",
            "760": "Pozostałe przychody operacyjne",
            "761": "Pozostałe koszty operacyjne",
            "800": "Kapitał (fundusz) podstawowy",
            "811": "Kapitał (fundusz) zapasowy",
            "812": "Pozostałe kapitały rezerwowe",
            "820": "Rozliczenie wyniku finansowego",
            "830": "Rezerwy na zobowiązania",
            "840": "Rozliczenia międzyokresowe przychodów",
            "850": "Fundusze specjalne",
            "860": "Wynik finansowy"
        };

        // ZARZĄDZANIE ZAKŁADKAMI
        function showTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('nav button').forEach(el => el.classList.remove('active'));
            document.getElementById('tab-' + tabName).classList.add('active');
            event.target.classList.add('active');
        }

        // AUTO-UZUPEŁNIANIE NAZWY KONTA
        function lookupAccount(val) {
            val = val.trim();
            if(PLAN_KONT[val]) {
                return val + " " + PLAN_KONT[val];
            }
            return val;
        }

        // LOGIKA KONT T-OWYCH
        function addAccount(type, defaultSymbol = "") {
            const container = document.getElementById('container-' + type);
            const accId = 'acc_' + Date.now();

            const html = `
                <div class="t-account" id="${accId}">
                    <div class="t-account-header">
                        <input type="text" placeholder="Wpisz symbol (np. 100)" value="${defaultSymbol}" onchange="handleAccHeaderChange(this)">
                        <button class="btn btn-danger btn-sm" onclick="document.getElementById('${accId}').remove()">X</button>
                    </div>
                    <div class="t-body">
                        <div class="t-column" data-col="dt">
                            <div class="col-title">Dt (Wn)</div>
                            <div class="operations-list"></div>
                            <div class="col-controls">
                                <input type="text" placeholder="Nowy wpis + Enter..." onkeydown="handleOpEnter(event, this)">
                                <button class="btn btn-sm btn-primary" onclick="addLine(this, 'single')">—</button>
                                <button class="btn btn-sm btn-primary" onclick="addLine(this, 'double')">═</button>
                            </div>
                        </div>
                        <div class="t-column" data-col="ct">
                            <div class="col-title">Ct (Ma)</div>
                            <div class="operations-list"></div>
                            <div class="col-controls">
                                <input type="text" placeholder="Nowy wpis + Enter..." onkeydown="handleOpEnter(event, this)">
                                <button class="btn btn-sm btn-primary" onclick="addLine(this, 'single')">—</button>
                                <button class="btn btn-sm btn-primary" onclick="addLine(this, 'double')">═</button>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            container.insertAdjacentHTML('beforeend', html);
        }

        function handleAccHeaderChange(input) {
            input.value = lookupAccount(input.value);
        }

        function handleOpEnter(e, input) {
            if (e.key === 'Enter' && input.value.trim() !== '') {
                const list = input.parentElement.previousElementSibling;
                const itemHtml = `
                    <div class="op-item">
                        <input type="text" value="${input.value}">
                        <button class="btn btn-danger btn-sm" onclick="this.parentElement.remove()">×</button>
                    </div>
                `;
                list.insertAdjacentHTML('beforeend', itemHtml);
                input.value = ''; // wyczyszczenie pola
                input.focus(); // zachowanie fokusu
            }
        }

        function addLine(btn, type) {
            const list = btn.parentElement.previousElementSibling;
            const lineClass = type === 'single' ? 'op-line' : 'op-line-double';
            const html = `
                <div class="op-item">
                    <div class="${lineClass}"></div>
                    <button class="btn btn-danger btn-sm" onclick="this.parentElement.remove()">×</button>
                </div>
            `;
            list.insertAdjacentHTML('beforeend', html);
        }

        // LOGIKA BILANSU
        function updateBilansTitle() {
            document.getElementById('disp-company').innerText = document.getElementById('bilans-company').value || '--';
            document.getElementById('disp-date').innerText = document.getElementById('bilans-date').value || '--';
        }

        function calculateBilans() {
            const getVal = id => parseFloat(document.getElementById(id)?.value) || 0;
            const setVal = (id, val) => { if(document.getElementById(id)) document.getElementById(id).value = val; };

            // Aktywa A
            const akt_A_II = getVal('akt_A_II_1') + getVal('akt_A_II_2');
            setVal('akt_A_II', akt_A_II);

            const akt_A_IV = getVal('akt_A_IV_1') + getVal('akt_A_IV_2');
            setVal('akt_A_IV', akt_A_IV);

            const akt_A = getVal('akt_A_I') + akt_A_II + getVal('akt_A_III') + akt_A_IV + getVal('akt_A_V');
            setVal('akt_A', akt_A);

            // Aktywa B
            const akt_B_II = getVal('akt_B_II_1') + getVal('akt_B_II_2');
            setVal('akt_B_II', akt_B_II);

            const akt_B_III = getVal('akt_B_III_1');
            setVal('akt_B_III', akt_B_III);

            const akt_B = getVal('akt_B_I') + akt_B_II + akt_B_III + getVal('akt_B_IV');
            setVal('akt_B', akt_B);

            // Suma Aktywa
            const akt_Suma = akt_A + akt_B + getVal('akt_C') + getVal('akt_D');
            setVal('akt_SUMA', akt_Suma);

            // Pasywa A
            const pas_A = getVal('pas_A_I') + getVal('pas_A_II') + getVal('pas_A_III') + getVal('pas_A_IV') + getVal('pas_A_V') + getVal('pas_A_VI') - Math.abs(getVal('pas_A_VII'));
            setVal('pas_A', pas_A);

            // Pasywa B
            const pas_B_III = getVal('pas_B_III_1') + getVal('pas_B_III_2') + getVal('pas_B_III_3');
            setVal('pas_B_III', pas_B_III);

            const pas_B = getVal('pas_B_I') + getVal('pas_B_II') + pas_B_III + getVal('pas_B_IV');
            setVal('pas_B', pas_B);

            // Suma Pasywa
            const pas_Suma = pas_A + pas_B;
            setVal('pas_SUMA', pas_Suma);

            // Sprawdzenie zgodności bilansowej
            const statusDiv = document.getElementById('bilans-status');
            if (akt_Suma === pas_Suma && akt_Suma > 0) {
                statusDiv.style.backgroundColor = '#d4edda';
                statusDiv.style.color = '#155724';
                statusDiv.innerText = `BILANS ZGODNY! Suma bilansowa wynosi: ${akt_Suma.toLocaleString()} zł`;
            } else if (akt_Suma !== pas_Suma) {
                statusDiv.style.backgroundColor = '#f8d7da';
                statusDiv.style.color = '#721c24';
                statusDiv.innerText = `BRAK ZGODNOŚCI BILANSOWEJ! Różnica: ${(akt_Suma - pas_Suma).toLocaleString()} zł (Aktywa: ${akt_Suma.toLocaleString()}, Pasywa: ${pas_Suma.toLocaleString()})`;
            } else {
                statusDiv.innerText = '';
            }
        }

        // LOGIKA ZESTAWIENIA OBROTÓW I SALD (ZOS)
        function updateZOSTitle() {
            document.getElementById('zos-disp-date').innerText = document.getElementById('zos-date').value || '--';
        }

        function addZosRow(symbol = "", values = Array(8).fill("")) {
            const tbody = document.getElementById('zos-body');
            const row = document.createElement('tr');

            row.innerHTML = `
                <td><input type="text" class="acc-name" value="${symbol}" placeholder="Symbol konta + Enter" onkeydown="handleZosAccEnter(event, this)"></td>
                <td><input type="number" class="num zos-c1" value="${values[0]}"></td>
                <td><input type="number" class="num zos-c2" value="${values[1]}"></td>
                <td><input type="number" class="num zos-c3" value="${values[2]}"></td>
                <td><input type="number" class="num zos-c4" value="${values[3]}"></td>
                <td><input type="number" class="num zos-c5" value="${values[4]}"></td>
                <td><input type="number" class="num zos-c6" value="${values[5]}"></td>
                <td><input type="number" class="num zos-c7" value="${values[6]}"></td>
                <td><input type="number" class="num zos-c8" value="${values[7]}"></td>
                <td><button class="btn btn-danger btn-sm" onclick="this.closest('tr').remove()">×</button></td>
            `;
            tbody.appendChild(row);
        }

        function handleZosAccEnter(e, input) {
            if (e.key === 'Enter') {
                input.value = lookupAccount(input.value);
                // Przejście do następnego pola
                const nextInput = input.parentElement.nextElementSibling?.querySelector('input');
                if (nextInput) nextInput.focus();
            }
        }

        function calculateZOS() {
            for (let i = 1; i <= 8; i++) {
                let sum = 0;
                document.querySelectorAll(`.zos-c${i}`).forEach(input => {
                    sum += parseFloat(input.value) || 0;
                });
                document.getElementById(`zos-s${i}`).innerText = sum.toLocaleString('pl-PL', { minimumFractionDigits: 0 });
            }
        }

        // Domyślne załadowanie kilku kont na start
        window.onload = function() {
            addAccount('bilansowe', '100');
            addAccount('bilansowe', '130-1');
            addAccount('wynikowe', '700');
            
            // Domyślne wiersze ZOS z obrazka
            addZosRow('010-4', [140000, 0, 0, 0, 140000, 0, 140000, 0]);
            addZosRow('100', [1000, 0, 2500, 2000, 3500, 2000, 1500, 0]);
            addZosRow('130-1', [20000, 0, 30000, 34500, 50000, 34500, 15500, 0]);
            calculateZOS();
        }
    </script>
</body>
</html>
