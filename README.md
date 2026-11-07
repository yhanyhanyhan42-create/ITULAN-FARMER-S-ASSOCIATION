<!DOCTYPE html>
<html lang="tl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Itulan Farmers Association - Master Profile System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f1f5f9;
            margin: 0;
            padding: 20px;
            color: #334155;
        }
        .container {
            max-width: 900px;
            background: #ffffff;
            margin: auto;
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .security-banner {
            background: #fef2f2;
            color: #991b1b;
            text-align: center;
            font-size: 11px;
            padding: 8px;
            font-weight: bold;
            margin-bottom: 20px;
            border: 1px solid #fecaca;
            border-radius: 4px;
        }
        h2.title {
            text-align: center;
            margin-bottom: 2px;
            color: #0f172a;
        }
        .subtitle {
            text-align: center;
            font-size: 13px;
            color: #64748b;
            margin-bottom: 20px;
        }
        .section-header {
            background: #e2e8f0;
            color: #1e293b;
            padding: 8px 12px;
            font-weight: bold;
            font-size: 13px;
            margin-top: 20px;
            border-left: 4px solid #0284c7;
            border-radius: 2px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 8px;
            margin-bottom: 15px;
            font-size: 13px;
        }
        table, th, td {
            border: 1px solid #cbd5e1;
        }
        th, td {
            padding: 8px 10px;
            text-align: left;
        }
        th {
            background: #f8fafc;
            color: #334155;
        }
        input[type="text"], input[type="number"], select {
            width: 100%;
            padding: 6px;
            box-sizing: border-box;
            border: 1px solid #cbd5e1;
            border-radius: 4px;
            font-size: 13px;
        }
        input:focus {
            outline: none;
            border-color: #0284c7;
            box-shadow: 0 0 0 2px rgba(2, 132, 199, 0.2);
        }
        .btn-container {
            text-align: center;
            margin-top: 25px;
        }
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            font-size: 13px;
        }
        .btn-print { background: #0284c7; color: white; }
        .btn-print:hover { background: #0369a1; }
        .btn-close { background: #dc2626; color: white; margin-left: 8px; }
        .btn-close:hover { background: #b91c1c; }
        .footer {
            text-align: center;
            font-size: 11px;
            color: #94a3b8;
            margin-top: 30px;
            border-top: 1px solid #e2e8f0;
            padding-top: 12px;
        }
        #loading { display: none; text-align: center; color: #0284c7; font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>

<div class="container">
    <div class="security-banner">
        PROTECTED SYSTEM: Mahigpit na ipinagbabawal ang pag-screenshot, pag-record, o pamamahagi ng data ng asosasyon.
    </div>

    <h2 class="title">Itulan Farmers Association</h2>
    <div class="subtitle">Zone 3, Itulan, Pasacao, Camarines Sur</div>

    <form id="masterForm">
        <!-- Personal na Impormasyon at Bayarin -->
        <div class="section-header">1. Personal na Impormasyon at Bayarin ng Miyembro</div>
        <table>
            <tr><td width="30%"><strong>ID ng Miyembro:</strong></td><td><input type="text" id="idMiyembro" value="IFA-2024-001"></td></tr>
            <tr><td><strong>Buong Pangalan:</strong></td><td><input type="text" id="pangalan" value="Guavar, Rayan D." required></td></tr>
            <tr><td><strong>Posisyon / Katayuan sa Asosasyon:</strong></td><td><input type="text" id="posisyon" value="Kasaping Magsasaka"></td></tr>
            <tr><td><strong>Member Since (Taon ng Pagsali):</strong></td><td><input type="text" id="memberSince" value="2024"></td></tr>
            <tr><td><strong>Edad:</strong></td><td><input type="text" id="edad" value="31"></td></tr>
            <tr><td><strong>Kasarian:</strong></td><td><input type="text" id="kasarian" value="Lalaki"></td></tr>
            <tr><td><strong>Petsa ng Kapanganakan:</strong></td><td><input type="text" id="dateOfBirth" value="1995-03-10"></td></tr>
            <tr><td><strong>Katayuang Sibil:</strong></td><td><input type="text" id="civilStatus" value="May Asawa"></td></tr>
            <tr><td><strong>RSBSA No.:</strong></td><td><input type="text" id="rsbsaNo" value="Wala"></td></tr>
            <tr><td><strong>NCFRS No.:</strong></td><td><input type="text" id="ncfrsNo" value="Wala"></td></tr>
            <tr><td><strong>Tirahan / Purok:</strong></td><td><input type="text" id="address" value="Zone 3, Itulan, Pasacao"></td></tr>
            <tr><td><strong>Numero ng Kontak:</strong></td><td><input type="text" id="contactNo" value="9637657151"></td></tr>
            <tr><td><strong>Bayad sa Pagpapatala:</strong></td><td><input type="text" id="registrationFee" value="500"></td></tr>
            <tr><td><strong>Taunang Butaw:</strong></td><td><input type="text" id="taunangButaw" value="600"></td></tr>
            <tr><td><strong>Katayuan ng Bayarin:</strong></td><td><input type="text" id="katayuanBayarin" value="Bayad na"></td></tr>
            <tr><td><strong>Food Consumption:</strong></td><td><input type="text" id="foodConsumption" value="30 sako (Palay)"></td></tr>
        </table>

        <!-- Ulat ng Pinsala ng Kalamidad -->
        <div class="section-header">2. Ulat ng Pinsala ng Kalamidad</div>
        <table>
            <tr><td width="30%"><strong>Uri ng Kalamidad:</strong></td><td><input type="text" id="uriNgKalamidad" value="Wala"></td></tr>
            <tr><td><strong>Niyog (Nasirang Puno):</strong></td><td><input type="text" id="niyogPuno" value="Wala"></td></tr>
            <tr><td><strong>Palay (Nasirang %):</strong></td><td><input type="text" id="palayNasirangPct" value="Wala"></td></tr>
            <tr><td><strong>Gulay (Nasirang %):</strong></td><td><input type="text" id="gulayNasirangPct" value="Wala"></td></tr>
        </table>

        <!-- Produksyon at Kita -->
        <div class="section-header">3. Produksyon at Kita (Base sa Planting Season)</div>
        <table>
            <thead>
                <tr>
                    <th>Produkto</th>
                    <th>Sukat / Detalye</th>
                    <th>Ani / Cropping</th>
                    <th>Kita (₱)</th>
                </tr>
            </thead>
            <tbody id="prodTable">
                <tr><td>Palay</td><td><input type="text" value="1.5 Hektarya"></td><td><input type="text" value="145 Kaban"></td><td>₱ <input type="number" class="kita-input" value="166750" oninput="computeTotal()"></td></tr>
                <tr><td>Niyog</td><td><input type="text" value="1 Hektarya (Kopra)"></td><td><input type="text" value="2400 Kilo"></td><td>₱ <input type="number" class="kita-input" value="87600" oninput="computeTotal()"></td></tr>
                <tr><td>Gulay</td><td><input type="text" value="-"></td><td><input type="text" value="-"></td><td>₱ <input type="number" class="kita-input" value="0" oninput="computeTotal()"></td></tr>
                <tr><td>Kalabaw</td><td><input type="text" value="-"></td><td><input type="text" value="-"></td><td>₱ <input type="number" class="kita-input" value="0" oninput="computeTotal()"></td></tr>
                <tr><td>Baka</td><td><input type="text" value="-"></td><td><input type="text" value="-"></td><td>₱ <input type="number" class="kita-input" value="0" oninput="computeTotal()"></td></tr>
                <tr><td>Kambing</td><td><input type="text" value="-"></td><td><input type="text" value="-"></td><td>₱ <input type="number" class="kita-input" value="0" oninput="computeTotal()"></td></tr>
                <tr><td>Baboy</td><td><input type="text" value="-"></td><td><input type="text" value="-"></td><td>₱ <input type="number" class="kita-input" value="0" oninput="computeTotal()"></td></tr>
            </tbody>
        </table>
        <div style="text-align: right; font-weight: bold; font-size: 14px; margin-bottom: 15px;">
            Kabuuang Kita (Seasonal): <span id="kabuuangKitaDisplay" style="color: #0284c7;">₱254,350</span>
        </div>

        <div class="btn-container">
            <button type="button" class="btn btn-print" onclick="submitData()">I-save sa Master Database at I-print</button>
            <button type="button" class="btn btn-close" onclick="window.close()">Isara</button>
            <div id="loading">Nagsasave sa Google Cloud Database... Sandali lang po.</div>
        </div>
    </form>

    <div class="footer">
        Itulan Farmers Association &copy; 2026. Master Database Management System.
    </div>
</div>

<script>
    // Palitan ito ng iyong Google Apps Script Web App URL
    const SCRIPT_URL = "YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE";

    function computeTotal() {
        let inputs = document.querySelectorAll('.kita-input');
        let total = 0;
        inputs.forEach(input => {
            let val = parseFloat(input.value) || 0;
            total += val;
        });
        document.getElementById('kabuuangKitaDisplay').innerText = '₱' + total.toLocaleString();
    }

    function submitData() {
        if(!confirm("I-save ba ang mga detalyeng ito sa Master Database ng Asosasyon?")) return;

        document.getElementById('loading').style.display = 'block';

        let prodRows = document.querySelectorAll('#prodTable tr');
        let produksyonList = [];
        let prodNames = ["Palay", "Niyog", "Gulay", "Kalabaw", "Baka", "Kambing", "Baboy"];

        prodRows.forEach((row, index) => {
            produksyonList.push({
                produkto: prodNames[index],
                detalye: row.cells[1].children[0].value,
                ani: row.cells[2].children[0].value,
                kita: row.cells[3].children[1].value
            });
        });

        let formData = {
            idMiyembro: document.getElementById('idMiyembro').value,
            pangalan: document.getElementById('pangalan').value,
            posisyon: document.getElementById('posisyon').value,
            memberSince: document.getElementById('memberSince').value,
            edad: document.getElementById('edad').value,
            kasarian: document.getElementById('kasarian').value,
            dateOfBirth: document.getElementById('dateOfBirth').value,
            civilStatus: document.getElementById('civilStatus').value,
            rsbsaNo: document.getElementById('rsbsaNo').value,
            ncfrsNo: document.getElementById('ncfrsNo').value,
            address: document.getElementById('address').value,
            contactNo: document.getElementById('contactNo').value,
            registrationFee: document.getElementById('registrationFee').value,
            taunangButaw: document.getElementById('taunangButaw').value,
            katayuanBayarin: document.getElementById('katayuanBayarin').value,
            foodConsumption: document.getElementById('foodConsumption'].value,
            uriNgKalamidad: document.getElementById('uriNgKalamidad').value,
            niyogPuno: document.getElementById('niyogPuno').value,
            palayNasirangPct: document.getElementById('palayNasirangPct').value,
            gulayNasirangPct: document.getElementById('gulayNasirangPct').value,
            kabuuangKita: document.getElementById('kabuuangKitaDisplay').innerText,
            produksyon: produksyonList
        };

        if(SCRIPT_URL.includes("YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE")) {
            document.getElementById('loading').style.display = 'none';
            alert("Paalala: Ilagay muna ang iyong Google Apps Script Web App URL sa SCRIPT_URL variable.");
            window.print();
            return;
        }

        fetch(SCRIPT_URL, {
            method: 'POST',
            mode: 'no-cors',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(formData)
        }).then(() => {
            document.getElementById('loading').style.display = 'none';
            alert("Matagumpay na na-save sa Master Database!");
            window.print();
        }).catch(error => {
            document.getElementById('loading').style.display = 'none';
            alert("May nangyaring error sa pag-save: " + error);
        });
    }
</script>

</body>
</html>
