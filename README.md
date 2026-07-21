<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Szablony do rozwiązywania zadań z księgowości</title>
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
            flex-wrap: wrap;
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

        .tab-content { display: none; }
        .tab-content.active { display: block; }

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
        .btn-secondary { background-color: #95a5a6; color: white; }
        .btn-sm { padding: 4px 8px; font-size: 12px; }

        /* KONTAT-OWE */
        .accounts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(360px, 1fr));
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
            padding: 6px;
            width: 100%;
        }

        .t-body {
            display: flex;
            min-height: 250px;
        }

        .t-column {
            flex: 1;
            padding: 0 5px;
            display: flex;
            flex-direction: column;
        }

        .t-column:first-child { border-right: 2px solid #333; }

        .col-title {
            text-align: center;
            font-weight: bold;
            font-size: 14px;
            border-bottom: 1px solid #aaa;
            padding-bottom: 3px;
            margin-bottom: 5px;
        }

        .op-items { flex: 1; display: flex; flex-direction: column; gap: 4px; }
        .summary-items { display: flex; flex-direction: column; gap: 4px; margin-top: 10px; margin-bottom: 15px;}

        .t-row {
            display: flex;
            align-items: center;
            gap: 4px;
        }
        
        .t-row input {
            border: 1px solid #ddd;
            padding: 4px;
            font-size: 13px;
        }

        .edit-op-nr { width: 40px; text-align: center; }
        .edit-op-val, .edit-sum-val { flex: 1; text-align: right; }
        .edit-sum-txt { width: 70px; }

        .op-line {
            width: 100%;
            border-top: 2px solid #000;
            margin: 6px 0;
            flex: 1;
        }

        .op-line-double {
            width: 100%;
            border-top: 4px double #000;
            margin: 6px 0;
            flex: 1;
        }

        .col-controls {
            margin-top: auto;
            display: flex;
            flex-direction: column;
            gap: 5px;
            background: #f9f9f9;
            padding: 8px;
            border-radius: 4px;
            border: 1px dashed #ccc;
        }

        .control-row {
            display: flex;
            gap: 4px;
        }
        
        .control-row input {
            border: 1px solid #aaa;
            padding: 4px;
            font-size: 13px;
        }
        .flex-1 { flex: 1; }

        /* BILANS */
        .bilans-container { background: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        .bilans-header-inputs { display: flex; gap: 20px; margin-bottom: 20px; background: #eef2f5; padding: 15px; border-radius: 5px; }
        .bilans-header-inputs div { display: flex; flex-direction: column; flex: 1; }
        .bilans-header-inputs label { font-weight: bold; font-size: 13px; margin-bottom: 5px; }
        .bilans-header-inputs input { padding: 8px; border: 1px solid #ccc; border-radius: 4px; }
        .bilans-tables { display: flex; gap: 20px; overflow-x: auto; }
        .bilans-col { flex: 1; min-width: 400px; }
        .bilans-table { width: 100%; border-collapse: collapse; font-size: 13px; }
        .bilans-table th, .bilans-table td { border: 1px solid #ccc; padding: 5px 8px; }
        .bilans-table th { background: var(--primary-color); color: white; text-align: center; }
        .row-group-A { font-weight: bold; background: #eaeded; }
        .row-group-B { font-weight: bold; background: #f2f4f4; }
        .row-sub { font-weight: 600; padding-left: 15px !important; }
        .row-detail { padding-left: 30px !important; color: #555; }
        .row-total { font-weight: bold; background: #d5dbdb; font-size: 14px; }
        .bilans-table input { width: 130px; text-align: right; padding: 4px; border: 1px solid #ccc; }

        /* ZOS */
        .zos-container { background: white; padding: 20px; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        .zos-table-wrapper { overflow-x: auto; }
        .zos-table { width: 100%; border-collapse: collapse; font-size: 14px; margin-top: 15px; }
        .zos-table th, .zos-table td { border: 1px solid #000; padding: 8px; text-align: center; }
        .zos-table th { background: #e6e6e6; min-width: 140px; }
        .zos-table input { width: 100%; padding: 6px; border: 1px solid #ddd; font-size: 14px; box-sizing: border-box; }
        .zos-table input.acc-name { text-align: left; }
        .zos-table input.num { text-align: right; }
        .zos-total-row { font-weight: bold; background: #f0f0f0; }
        
        .status-msg { margin-top: 10px; padding: 10px; border-radius: 4px; font-weight: bold; text-align: center; }
    </style>
</head>
<body>

    <header>
        <h1>Szablony do rozwiązywania zadań z księgowości</h1>
    </header>

    <nav>
        <button class="active" onclick="showTab('konta')">Konta T-owe</button>
        <button onclick="showTab('bilans')">Bilans</button>
        <button onclick="showTab('zos')">Zestawienie Obrotów i Sald</button>
        <button onclick="showTab('notatnik')">Notatnik</button>
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
                <div class="bilans-col">
                    <table class="bilans-table">
                        <thead><tr><th>AKTYWA</th><th>Wartość</th></tr></thead>
                        <tbody>
                            <tr class="row-group-A"><td>A. Aktywa trwałe</td><td><input type="text" class="money-input" id="akt_A" readonly></td></tr>
                            <tr class="row-sub"><td>I. Wartości niematerialne i prawne</td><td><input type="text" class="money-input" id="akt_A_I"></td></tr>
                            <tr class="row-sub"><td>II. Rzeczowe aktywa trwałe</td><td><input type="text" class="money-input" id="akt_A_II" readonly></td></tr>
                            <tr class="row-detail"><td>- środki trwałe</td><td><input type="text" class="money-input" id="akt_A_II_1"></td></tr>
                            <tr class="row-detail"><td>- środki trwałe w budowie</td><td><input type="text" class="money-input" id="akt_A_II_2"></td></tr>
                            <tr class="row-sub"><td>III. Należności długoterminowe</td><td><input type="text" class="money-input" id="akt_A_III"></td></tr>
                            <tr class="row-sub"><td>IV. Inwestycje długoterminowe</td><td><input type="text" class="money-input" id="akt_A_IV" readonly></td></tr>
                            <tr class="row-detail"><td>- nieruchomości</td><td><input type="text" class="money-input" id="akt_A_IV_1"></td></tr>
                            <tr class="row-detail"><td>- długoterminowe aktywa finansowe</td><td><input type="text" class="money-input" id="akt_A_IV_2"></td></tr>
                            <tr class="row-sub"><td>V. Długoterminowe rozliczenia międzyokresowe</td><td><input type="text" class="money-input" id="akt_A_V"></td></tr>
                            <tr class="row-group-B"><td>B. Aktywa obrotowe</td><td><input type="text" class="money-input" id="akt_B" readonly></td></tr>
                            <tr class="row-sub"><td>I. Zapasy</td><td><input type="text" class="money-input" id="akt_B_I"></td></tr>
                            <tr class="row-sub"><td>II. Należności krótkoterminowe</td><td><input type="text" class="money-input" id="akt_B_II" readonly></td></tr>
                            <tr class="row-detail"><td>a) z tytułu dostaw i usług (do 12 mies.)</td><td><input type="text" class="money-input" id="akt_B_II_1"></td></tr>
                            <tr class="row-detail"><td>b) z tytułu dostaw i usług (pow. 12 mies.)</td><td><input type="text" class="money-input" id="akt_B_II_2"></td></tr>
                            <tr class="row-sub"><td>III. Inwestycje krótkoterminowe</td><td><input type="text" class="money-input" id="akt_B_III" readonly></td></tr>
                            <tr class="row-detail"><td>- środki pieniężne w kasie i na rachunkach</td><td><input type="text" class="money-input" id="akt_B_III_1"></td></tr>
                            <tr class="row-sub"><td>IV. Krótkoterminowe rozliczenia międzyokresowe</td><td><input type="text" class="money-input" id="akt_B_IV"></td></tr>
                            <tr class="row-group-A"><td>C. Należne wpłaty na kapitał podstawowy</td><td><input type="text" class="money-input" id="akt_C"></td></tr>
                            <tr class="row-group-A"><td>D. Udziały (akcje) własne</td><td><input type="text" class="money-input" id="akt_D"></td></tr>
                            <tr class="row-total"><td>AKTYWA RAZEM</td><td><input type="text" class="money-input" id="akt_SUMA" readonly></td></tr>
                        </tbody>
                    </table>
                </div>

                <div class="bilans-col">
                    <table class="bilans-table">
                        <thead><tr><th>PASYWA</th><th>Wartość</th></tr></thead>
                        <tbody>
                            <tr class="row-group-A"><td>A. Kapitał (fundusz) własny</td><td><input type="text" class="money-input" id="pas_A" readonly></td></tr>
                            <tr class="row-sub"><td>I. Kapitał (fundusz) podstawowy</td><td><input type="text" class="money-input" id="pas_A_I"></td></tr>
                            <tr class="row-sub"><td>II. Kapitał (fundusz) zapasowy</td><td><input type="text" class="money-input" id="pas_A_II"></td></tr>
                            <tr class="row-sub"><td>III. Kapitał z aktualizacji wyceny</td><td><input type="text" class="money-input" id="pas_A_III"></td></tr>
                            <tr class="row-sub"><td>IV. Pozostałe kapitały rezerwowe</td><td><input type="text" class="money-input" id="pas_A_IV"></td></tr>
                            <tr class="row-sub"><td>V. Zysk (strata) z lat ubiegłych</td><td><input type="text" class="money-input" id="pas_A_V"></td></tr>
                            <tr class="row-sub"><td>VI. Zysk (strata) netto</td><td><input type="text" class="money-input" id="pas_A_VI"></td></tr>
                            <tr class="row-sub"><td>VII. Odpisy z zysku netto (ujemna)</td><td><input type="text" class="money-input" id="pas_A_VII"></td></tr>
                            <tr class="row-group-B"><td>B. Zobowiązania i rezerwy na zobowiązania</td><td><input type="text" class="money-input" id="pas_B" readonly></td></tr>
                            <tr class="row-sub"><td>I. Rezerwy na zobowiązania</td><td><input type="text" class="money-input" id="pas_B_I"></td></tr>
                            <tr class="row-sub"><td>II. Zobowiązania długoterminowe</td><td><input type="text" class="money-input" id="pas_B_II"></td></tr>
                            <tr class="row-sub"><td>III. Zobowiązania krótkoterminowe</td><td><input type="text" class="money-input" id="pas_B_III" readonly></td></tr>
                            <tr class="row-detail"><td>a) kredyty i pożyczki</td><td><input type="text" class="money-input" id="pas_B_III_1"></td></tr>
                            <tr class="row-detail"><td>b) z tytułu dostaw i usług (do 12 mies.)</td><td><input type="text" class="money-input" id="pas_B_III_2"></td></tr>
                            <tr class="row-detail"><td>c) fundusze specjalne</td><td><input type="text" class="money-input" id="pas_B_III_3"></td></tr>
                            <tr class="row-sub"><td>IV. Rozliczenia międzyokresowe</td><td><input type="text" class="money-input" id="pas_B_IV"></td></tr>
                            <tr class="row-total"><td>PASYWA RAZEM</td><td><input type="text" class="money-input" id="pas_SUMA" readonly></td></tr>
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
                            <th rowspan="2" style="width: 250px;">Nazwa konta</th>
                            <th colspan="2">Salda na dzień otwarcia ksiąg</th>
                            <th colspan="2">Obroty za okres sprawozdawczy</th>
                            <th colspan="2">Obroty narastająco od początku roku</th>
                            <th colspan="2">Salda na koniec okresu sprawozdawczego</th>
                            <th rowspan="2" style="width:50px;">Akcja</th>
                        </tr>
                        <tr>
                            <th>Dt</th><th>Ct</th>
                            <th>Dt</th><th>Ct</th>
                            <th>Dt</th><th>Ct</th>
                            <th>Dt</th><th>Ct</th>
                        </tr>
                    </thead>
                    <tbody id="zos-body"></tbody>
                    <tfoot>
                        <tr class="zos-total-row">
                            <td>SUMA</td>
                            <td id="zos-s1">0 zł</td><td id="zos-s2">0 zł</td>
                            <td id="zos-s3">0 zł</td><td id="zos-s4">0 zł</td>
                            <td id="zos-s5">0 zł</td><td id="zos-s6">0 zł</td>
                            <td id="zos-s7">0 zł</td><td id="zos-s8">0 zł</td>
                            <td></td>
                        </tr>
                    </tfoot>
                </table>
            </div>
        </div>
    </div>

    <!-- TAB 4: NOTATNIK -->
    <div id="tab-notatnik" class="tab-content">
        <div class="section-header">
            <h2>Notatnik</h2>
        </div>
        <textarea style="width: 100%; height: 75vh; padding: 20px; box-sizing: border-box; font-size: 16px; font-family: inherit; border: 1px solid var(--border-color); border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.05);" placeholder="Tutaj możesz swobodnie zapisywać obliczenia i notatki z zadania..."></textarea>
    </div>

    <script>
        // SŁOWNIK PLANU KONT (W 100% dostosowany do sekcji Bilansu ze wzoru)
        const PLAN_KONT = {
            "010": "Środki trwałe",
            "020": "Wartości niematerialne i prawne",
            "080": "Środki trwałe w budowie",
            "100": "Środki pieniężne w kasie i na rachunkach",
            "130": "Środki pieniężne w kasie i na rachunkach",
            "134": "Kredyty i pożyczki",
            "200": "Należności z tytułu dostaw i usług (do 12 mies.)",
            "202": "Zobowiązania z tytułu dostaw i usług (do 12 mies.)",
            "220": "Należności krótkoterminowe / Zobowiązania",
            "230": "Rozrachunki z tytułu wynagrodzeń",
            "310": "Zapasy (Materiały)",
            "330": "Zapasy (Towary)",
            "600": "Zapasy (Wyroby)",
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
            "820": "Rozliczenie wyniku finansowego",
            "830": "Rezerwy na zobowiązania",
            "840": "Rozliczenia międzyokresowe",
            "860": "Zysk (strata) netto"
        };

        // ZARZĄDZANIE ZAKŁADKAMI
        function showTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('nav button').forEach(el => el.classList.remove('active'));
            document.getElementById('tab-' + tabName).classList.add('active');
            event.target.classList.add('active');
        }

        // FORMATOWANIE KSIĘGOWE (np. 1 000 000 zł)
        function formatMoneyVal(valStr) {
            if (!valStr && valStr !== 0) return '';
            let cleaned = valStr.toString().replace(/\s/g, '').replace('zł', '').replace(',', '.').trim();
            if (cleaned === '') return '';
            let num = parseFloat(cleaned);
            if (isNaN(num)) return valStr;
            return num.toLocaleString('pl-PL', { minimumFractionDigits: 0, maximumFractionDigits: 2 }) + ' zł';
        }

        function unformatMoneyVal(valStr) {
            if (!valStr) return '';
            return valStr.toString().replace(/\s/g, '').replace('zł', '').trim();
        }

        // Globalne eventy formatujące dla klas .money-input
        document.addEventListener('focusin', e => {
            if(e.target.classList.contains('money-input') && !e.target.readOnly) {
                e.target.value = unformatMoneyVal(e.target.value);
            }
        });

        document.addEventListener('focusout', e => {
            if(e.target.classList.contains('money-input') && !e.target.readOnly) {
                e.target.value = formatMoneyVal(e.target.value);
                // Automatyczne przeliczanie jeśli jesteśmy w Bilansie lub ZOS
                if(e.target.closest('#tab-bilans')) calculateBilans();
                if(e.target.closest('#tab-zos')) calculateZOS();
            }
        });

        function lookupAccount(val) {
            val = val.trim();
            const baseSymbol = val.split('-')[0];
            const accName = PLAN_KONT[val] || PLAN_KONT[baseSymbol];
            if(accName) return val + " " + accName;
            return val;
        }

        // KONTAT-OWE: TWORZENIE
        function addAccount(type) {
            const container = document.getElementById('container-' + type);
            const accId = 'acc_' + Date.now();

            const html = `
                <div class="t-account" id="${accId}">
                    <div class="t-account-header">
                        <input type="text" placeholder="Wpisz symbol (np. 100) + Enter" onchange="this.value = lookupAccount(this.value)">
                        <button class="btn btn-danger btn-sm" onclick="document.getElementById('${accId}').remove()">X</button>
                    </div>
                    <div class="t-body">
                        ${renderTColumn('Dt (Wn)')}
                        ${renderTColumn('Ct (Ma)')}
                    </div>
                </div>
            `;
            container.insertAdjacentHTML('beforeend', html);
        }

        function renderTColumn(title) {
            return `
            <div class="t-column">
                <div class="col-title">${title}</div>
                <div class="op-items"></div>
                <div class="summary-items"></div>
                <div class="col-controls">
                    <div class="control-row">
                        <input type="number" class="new-op-nr" placeholder="Nr" style="width: 45px;">
                        <input type="text" class="new-op-val money-input" placeholder="Kwota" style="flex:1;">
                        <button class="btn btn-success btn-sm" onclick="addNumberedOp(this)">Dodaj</button>
                    </div>
                    <div class="control-row mt-1">
                        <input type="text" class="new-sum-txt" placeholder="Opis (np. Saldo)" style="width: 80px;">
                        <input type="text" class="new-sum-val money-input" placeholder="Kwota" style="flex:1;">
                        <button class="btn btn-primary btn-sm" onclick="addSummaryOp(this)">+Tekst</button>
                    </div>
                    <div class="control-row mt-1">
                        <button class="btn btn-secondary btn-sm flex-1" onclick="addTLine(this, 'single')">Kreska (—)</button>
                        <button class="btn btn-secondary btn-sm flex-1" onclick="addTLine(this, 'double')">Zamknięcie (═)</button>
                    </div>
                </div>
            </div>`;
        }

        // KONTAT-OWE: LOGIKA OPERACJI I SORTOWANIA
        function addNumberedOp(btn) {
            const col = btn.closest('.t-column');
            const itemsContainer = col.querySelector('.op-items');
            const nrInput = col.querySelector('.new-op-nr');
            const valInput = col.querySelector('.new-op-val');

            let nr = nrInput.value;
            let val = valInput.value;
            if(!val) return;

            const div = document.createElement('div');
            div.className = 't-row op-numbered';
            div.innerHTML = `
                <input type="number" class="edit-op-nr" value="${nr}" onchange="sortNumberedOps(this)">
                <span>)</span>
                <input type="text" class="edit-op-val money-input" value="${val}">
                <button class="btn btn-danger btn-sm" onclick="this.parentElement.remove();">x</button>
            `;
            itemsContainer.appendChild(div);
            
            formatMoneyValDirect(div.querySelector('.edit-op-val'));
            sortNumberedOps(div.querySelector('.edit-op-nr'));

            nrInput.value = '';
            valInput.value = '';
        }

        function sortNumberedOps(element) {
            const container = element.closest('.op-items');
            const rows = Array.from(container.querySelectorAll('.op-numbered'));
            rows.sort((a, b) => {
                let numA = parseFloat(a.querySelector('.edit-op-nr').value) || Number.MAX_SAFE_INTEGER;
                let numB = parseFloat(b.querySelector('.edit-op-nr').value) || Number.MAX_SAFE_INTEGER;
                return numA - numB;
            });
            rows.forEach(row => container.appendChild(row));
        }

        function addSummaryOp(btn) {
            const col = btn.closest('.t-column');
            const container = col.querySelector('.summary-items');
            const txtInput = col.querySelector('.new-sum-txt');
            const valInput = col.querySelector('.new-sum-val');

            let txt = txtInput.value;
            let val = valInput.value;
            if(!val && !txt) return;

            const div = document.createElement('div');
            div.className = 't-row sum-row';
            div.innerHTML = `
                <input type="text" class="edit-sum-txt" value="${txt}">
                <input type="text" class="edit-sum-val money-input" value="${val}">
                <button class="btn btn-danger btn-sm" onclick="this.parentElement.remove()">x</button>
            `;
            container.appendChild(div);
            
            formatMoneyValDirect(div.querySelector('.edit-sum-val'));
            txtInput.value = ''; valInput.value = '';
        }

        function addTLine(btn, type) {
            const col = btn.closest('.t-column');
            const container = col.querySelector('.summary-items');
            const lineClass = type === 'single' ? 'op-line' : 'op-line-double';
            
            const div = document.createElement('div');
            div.className = 't-row';
            div.innerHTML = `
                <div class="${lineClass}"></div>
                <button class="btn btn-danger btn-sm" onclick="this.parentElement.remove()">x</button>
            `;
            container.appendChild(div);
        }

        function formatMoneyValDirect(input) {
            input.value = formatMoneyVal(input.value);
        }

        // BILANS: OBLICZENIA
        function updateBilansTitle() {
            document.getElementById('disp-company').innerText = document.getElementById('bilans-company').value || '--';
            document.getElementById('disp-date').innerText = document.getElementById('bilans-date').value || '--';
        }

        function getNum(id) {
            let el = document.getElementById(id);
            if(!el) return 0;
            let clean = unformatMoneyVal(el.value).replace(',', '.');
            return parseFloat(clean) || 0;
        }

        function setNum(id, val) {
            let el = document.getElementById(id);
            if(el) el.value = val === 0 ? '' : formatMoneyVal(val.toString());
        }

        function calculateBilans() {
            const akt_A_II = getNum('akt_A_II_1') + getNum('akt_A_II_2'); setNum('akt_A_II', akt_A_II);
            const akt_A_IV = getNum('akt_A_IV_1') + getNum('akt_A_IV_2'); setNum('akt_A_IV', akt_A_IV);
            const akt_A = getNum('akt_A_I') + akt_A_II + getNum('akt_A_III') + akt_A_IV + getNum('akt_A_V'); setNum('akt_A', akt_A);

            const akt_B_II = getNum('akt_B_II_1') + getNum('akt_B_II_2'); setNum('akt_B_II', akt_B_II);
            const akt_B_III = getNum('akt_B_III_1'); setNum('akt_B_III', akt_B_III);
            const akt_B = getNum('akt_B_I') + akt_B_II + akt_B_III + getNum('akt_B_IV'); setNum('akt_B', akt_B);
            
            const akt_Suma = akt_A + akt_B + getNum('akt_C') + getNum('akt_D'); setNum('akt_SUMA', akt_Suma);

            const pas_A = getNum('pas_A_I') + getNum('pas_A_II') + getNum('pas_A_III') + getNum('pas_A_IV') + getNum('pas_A_V') + getNum('pas_A_VI') - Math.abs(getNum('pas_A_VII')); setNum('pas_A', pas_A);

            const pas_B_III = getNum('pas_B_III_1') + getNum('pas_B_III_2') + getNum('pas_B_III_3'); setNum('pas_B_III', pas_B_III);
            const pas_B = getNum('pas_B_I') + getNum('pas_B_II') + pas_B_III + getNum('pas_B_IV'); setNum('pas_B', pas_B);

            const pas_Suma = pas_A + pas_B; setNum('pas_SUMA', pas_Suma);

            const statusDiv = document.getElementById('bilans-status');
            if (akt_Suma === pas_Suma && akt_Suma > 0) {
                statusDiv.style.backgroundColor = '#d4edda'; statusDiv.style.color = '#155724';
                statusDiv.innerText = `BILANS ZGODNY! Suma bilansowa wynosi: ${formatMoneyVal(akt_Suma)}`;
            } else if (akt_Suma !== pas_Suma) {
                statusDiv.style.backgroundColor = '#f8d7da'; statusDiv.style.color = '#721c24';
                statusDiv.innerText = `BRAK ZGODNOŚCI BILANSOWEJ! Różnica: ${formatMoneyVal(Math.abs(akt_Suma - pas_Suma))} (Aktywa: ${formatMoneyVal(akt_Suma)}, Pasywa: ${formatMoneyVal(pas_Suma)})`;
            } else {
                statusDiv.innerText = '';
            }
        }

        // ZOS (ZESTAWIENIE OBROTÓW I SALD)
        function updateZOSTitle() {
            document.getElementById('zos-disp-date').innerText = document.getElementById('zos-date').value || '--';
        }

        function addZosRow() {
            const tbody = document.getElementById('zos-body');
            const row = document.createElement('tr');
            row.innerHTML = `
                <td><input type="text" class="acc-name" placeholder="Symbol konta + Enter" onchange="this.value = lookupAccount(this.value)"></td>
                <td><input type="text" class="num zos-c1 money-input"></td>
                <td><input type="text" class="num zos-c2 money-input"></td>
                <td><input type="text" class="num zos-c3 money-input"></td>
                <td><input type="text" class="num zos-c4 money-input"></td>
                <td><input type="text" class="num zos-c5 money-input"></td>
                <td><input type="text" class="num zos-c6 money-input"></td>
                <td><input type="text" class="num zos-c7 money-input"></td>
                <td><input type="text" class="num zos-c8 money-input"></td>
                <td><button class="btn btn-danger btn-sm" onclick="this.closest('tr').remove()">×</button></td>
            `;
            tbody.appendChild(row);
        }

        function calculateZOS() {
            for (let i = 1; i <= 8; i++) {
                let sum = 0;
                document.querySelectorAll(`.zos-c${i}`).forEach(input => {
                    let clean = unformatMoneyVal(input.value).replace(',', '.');
                    sum += parseFloat(clean) || 0;
                });
                document.getElementById(`zos-s${i}`).innerText = formatMoneyVal(sum.toString());
            }
        }
    </script>
</body>
</html>
