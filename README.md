<!DOCTYPE html>
<html lang="tl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Itulan Farmers Association - Public & Officers Portal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f1f5f9;
            margin: 0;
            padding: 20px;
            color: #334155;
        }
        .container {
            max-width: 950px;
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
        h2.title { text-align: center; margin-bottom: 2px; color: #0f172a; }
        .subtitle { text-align: center; font-size: 13px; color: #64748b; margin-bottom: 20px; }
        
        /* Navigation Tabs */
        .nav-tabs {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }
        .tab-btn {
            padding: 10px 20px;
            font-weight: bold;
            border: 1px solid #0284c7;
            background: #ffffff;
            color: #0284c7;
            border-radius: 4px;
            cursor: pointer;
        }
        .tab-btn.active { background: #0284c7; color: #ffffff; }

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
        table, th, td { border: 1px solid #cbd5e1; }
        th, td { padding: 8px 10px; text-align: left; }
        th { background: #f8fafc; color: #334155; }

        .badge-paid { color: #16a34a; font-weight: bold; }
        .badge-bal { color: #dc2626; font-weight: bold; }

        input[type="text"], input[type="number"], select {
            width: 100%; padding: 6px; box-sizing: border-box;
            border: 1px solid #cbd5e1; border-radius: 4px; font-size: 13px;
        }

        .btn { padding: 10px 20px; border: none; border-radius: 4px; cursor: pointer; font-weight: bold; font-size: 13px; }
        .btn-print { background: #0284c7; color: white; }
        .btn-delete { background: #dc2626; color: white; margin-left: 8px; }
        .btn-logout { background: #64748b; color: white; margin-left: 8px; }
        .footer { text-align: center; font-size: 11px; color: #94a3b8; margin-top: 30px; border-top: 1px solid #e2e8f0; padding-top: 12px; }
        #loading { display: none; text-align: center; color: #0284c7; font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>

<div class="container">
    <h2 class="title">Itulan Farmers Association</h2>
    <div class="subtitle">Zone 3, Itulan, Pasacao, Camarines Sur</div>

    <!-- TABS MENU -->
    <div class="nav-tabs">
        <button class="tab-btn active" id="tabPublic" onclick="switchTab('public')">📢 Public Transparent View</button>
        <button class="tab-btn" id="tabOfficer" onclick="switchTab('officer')">🔒 Officers Portal</button>
    </div>

    <!-- 1. PUBLIC TRANSPARENT VIEW (WALANG PASSWORD / READ-ONLY) -->
    <div id="publicView">
        <div class="section-header">Pangkalahatang Talaan ng Miyembro at Bayarin (Monthly Dues Target: ₱120)</div>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Pangalan</th>
                    <th>Posisyon</th>
                    <th>Reg. Fee (₱100 Target)</th>
                    <th>Monthly Dues Naibayad</th>
                    <th>Kulang sa Monthly Dues</th>
                    <th>Katayuan</th>
                </tr>
            </thead>
            <tbody id="publicTableBody">
                <!-- Halimbawang Data sa Public View -->
                <tr>
                    <td>IFA-2024-001</td>
                    <td>Guavar, Rayan D.</td>
                    <td>Kasaping Magsasaka</td>
                    <td><span class="badge-paid">₱100 (Bayad na)</span></td>
                    <td>₱20</td>
                    <td><span class="badge-bal">₱100 (Kulang)</span></td>
                    <td><span class="badge-bal">May Balanse</span></td>
                </tr>
                <tr>
                    <td>IFA-2024-002</td>
                    <td>Alcantara, Danilo M.</td>
                    <td>Pangulo</td>
                    <td><span class="badge-paid">₱100 (Bayad na)</span></td>
                    <td>₱120</td>
                    <td><span class="badge-paid">₱0 (Kumpleto)</span></td>
                    <td><span class="badge-paid">Bayad na</span></td>
                </tr>
                <tr>
                    <td>IFA-2024-003</td>
                    <td>Mendoza, Elena S.</td>
                    <td>Ingat-Yaman</td>
                    <td><span class="badge-paid">₱100 (Bayad na)</span></td>
                    <td>₱120</td>
                    <td><span class="badge-paid">₱0 (Kumpleto)</span></td>
                    <td><span class="badge-paid">Bayad na</span></td>
                </tr>
            </tbody>
        </table>
        <p style="font-size: 11px; color: #64748b; text-align: center;">* Ang pampublikong talaan na ito ay para sa transparency ng ating asosasyon. Ang pag-edit ay para sa mga opisyal lamang.</p>
    </div>

    <!-- 2. OFFICERS PORTAL (MAY PASSWORD AT MAG-EDIT / DELETE / PRINT) -->
    <div id="officersView" style="display: none;">
        <!-- Password Login Section -->
        <div id="officerLogin" style="text-align: center; padding: 30px;">
            <h3>Officers Access Control</h3>
            <p style="font-size: 13px; color: #64748b;">Ilagay ang password ng Opisyal para mag-edit, mag-delete, o mag-add:</p>
            <input type="password" id="officerPassword" placeholder="Ilagay ang Password" style="width: 250px; padding: 8px;">
            <button class="btn btn-print" onclick="loginOfficer()">Pumasok</button>
            <div id="loginError" style="color: #dc2626; font-size: 12px; margin-top: 8px; display: none;">Mali ang password!</div>
        </div>

        <!-- Form Editor (Lalabas pag naka-login ang Opisyal) -->
        <div id="officerEditor" style="display: none;">
            <div class="security-banner">
                OFFICERS PORTAL: May buong akses ka na mag-edit, mag-add, mag-delete, at mag-print ng profile.
            </div>

            <form id="masterForm">
                <div class="section-header">1. Personal na Impormasyon at Bayarin</div>
                <table>
                    <tr><td width="30%"><strong>ID ng Miyembro:</strong></td><td><input type="text" id="idMiyembro" value="IFA-2024-001"></td></tr>
                    <tr><td><strong>Buong Pangalan:</strong></td><td><input type="text" id="pangalan" value="Guavar, Rayan D."></td></tr>
                    <tr><td><strong>Posisyon:</strong></td><td><input type="text" id="posisyon" value="Kasaping Magsasaka"></td></tr>
                    <tr><td><strong>Member Since:</strong></td><td><input type="text" id="memberSince" value="2024"></td></tr>
                    <tr><td><strong>Edad / Kasarian:</strong></td><td><input type="text" id="edadKasarian" value="31 | Lalaki"></td></tr>
                    <tr><td><strong>Date of Birth:</strong></td><td><input type="text" id="dateOfBirth" value="1995-03-10"></td></tr>
                    <tr><td><strong>Civil Status:</strong></td><td><input type="text" id="civilStatus" value="May Asawa"></td></tr>
                    <tr><td><strong>RSBSA No.:</strong></td><td><input type="text" id="rsbsaNo" value="Wala"></td></tr>
                    <tr><td><strong>NCFRS No.:</strong></td><td><input type="text" id="ncfrsNo" value="Wala"></td></tr>
                    <tr><td><strong>Address:</strong></td><td><input type="text" id="address" value="Zone 3, Itulan, Pasacao"></td></tr>
                    <tr><td><strong>Contact No.:</strong></td><td><input type="text" id="contactNo" value="9637657151"></td></tr>
                    <tr><td><strong>Registration Fee Naibayad (₱):</strong></td><td><input type="number" id="registrationFee" value="100"></td></tr>
                    <tr><td><strong>Monthly Dues Naibayad (₱):</strong></td><td><input type="number" id="monthlyDuesPaid" value="20" oninput="calcDuesBalance()"></td></tr>
                    <tr><td><strong>Kulang sa Monthly Dues (₱):</strong></td><td><input type="number" id="monthlyDuesBalance" value="100" readonly style="background: #f8fafc;"></td></tr>
                    <tr><td><strong>Food Consumption:</strong></td><td><input type="text" id="foodConsumption" value="30 sako (Palay)"></td></tr>
                </table>

                <div class="section-header">2. Ulat ng Pinsala ng Kalamidad</div>
                <table>
                    <tr><td width="30%"><strong>Uri ng Kalamidad:</strong></td><td><input type="text" id="uriNgKalamidad" value="Wala"></td></tr>
                    <tr><td><strong>Niyog (Nasirang Puno):</strong></td><td><input type="text" id="niyogPuno" value="Wala"></td></tr>
                    <tr><td><strong>Palay (Nasirang %):</strong></td><td><input type="text" id="palayNasirangPct" value="Wala"></td></tr>
                    <tr><td><strong>Gulay (Nasirang %):</strong></td><td><input type="text" id="gulayNasirangPct" value="Wala"></td></tr>
                </table>

                <div class="section-header">3. Produksyon at Kita</div>
                <table>
                    <thead>
                        <tr><th>Produkto</th><th>Sukat / Detalye</th><th>Ani / Cropping</th><th>Kita (₱)</th></tr>
                    </thead>
                    <tbody id="prodTable">
                        <tr><td>Palay</td><td><input type="text" value="1.5 Hektarya"></td><td><input type="text" value="145 Kaban"></td><td>₱ <input type="number" class="kita-input" value="166750" oninput="computeTotal()"></td></tr>
                        <tr><td>Niyog</td><td><input type="text" value="1 Hektarya"></td><td><input type="text" value="2400 Kilo"></td><td>₱ <input type="number" class="kita-input" value="87600" oninput="computeTotal()"></td></tr>
                    </tbody>
                </table>
                <div style="text-align: right; font-weight: bold; margin-bottom: 15px;">
                    Kabuuang Kita: <span id="kabuuangKitaDisplay" style="color: #0284c7;">₱254,350</span>
                </div>

                <div class="btn-container">
                    <button type="button" class="btn btn-print" onclick="submitData('save')">I-save sa Database & I-print</button>
                    <button type="button" class="btn btn-delete" onclick="submitData('delete')">I-delete ang Profile</button>
                    <button type="button" class="btn btn-logout" onclick="logoutOfficer()">Mag-logout</button>
                    <div id="loading">Nagsasave sa Google Cloud Database... Sandali lang po.</div>
                </div>
            </form>
        </div>
    </div>

    <div class="footer">
        Itulan Farmers Association &copy; 2026. Transparent Member Management System.
    </div>
</div>

<script>
    const OFFICER_PASS = "Int3rn3tWisp2021";
    const SCRIPT_URL = "YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE"; // Palitan ng totoong Web App URL

    function switchTab(tab) {
        if(tab === 'public') {
            document.getElementById('publicView').style.display = 'block';
            document.getElementById('officersView').style.display = 'none';
            document.getElementById('tabPublic').classList.add('active');
            document.getElementById('tabOfficer').classList.remove('active');
        } else {
            document.getElementById('publicView').style.display = 'none';
            document.getElementById('officersView').style.display = 'block';
            document.getElementById('tabOfficer').classList.add('active');
            document.getElementById('tabPublic').classList.remove('active');
        }
    }

    function loginOfficer() {
        let pass = document.getElementById('officerPassword').value;
        if(pass === OFFICER_PASS) {
            document.getElementById('officerLogin').style.display = 'none';
            document.getElementById('officerEditor').style.display = 'block';
        } else {
            document.getElementById('loginError').style.display = 'block';
        }
    }

    function logoutOfficer() {
        document.getElementById('officerPassword').value = '';
        document.getElementById('officerLogin').style.display = 'block';
        document.getElementById('officerEditor').style.display = 'none';
    }

    function calcDuesBalance() {
        let paid = parseFloat(document.getElementById('monthlyDuesPaid').value) || 0;
        let bal = 120 - paid;
        if (bal < 0) bal = 0;
        document.getElementById('monthlyDuesBalance').value = bal;
    }

    function computeTotal() {
        let inputs = document.querySelectorAll('.kita-input');
        let total = 0;
        inputs.forEach(input => { total += parseFloat(input.value) || 0; });
        document.getElementById('kabuuangKitaDisplay').innerText = '₱' + total.toLocaleString();
    }

    function submitData(actionType) {
        let msg = actionType === 'delete' ? "Sigurado ka bang gusto mong I-DELETE ang miyembrong ito sa database?" : "I-save ba ang mga bagong detalye sa Google Cloud Database?";
        if(!confirm(msg)) return;

        document.getElementById('loading').style.display = 'block';

        let formData = {
            action: actionType,
            idMiyembro: document.getElementById('idMiyembro').value,
            pangalan: document.getElementById('pangalan').value,
            posisyon: document.getElementById('posisyon').value,
            memberSince: document.getElementById('memberSince').value,
            edadKasarian: document.getElementById('edadKasarian').value,
            dateOfBirth: document.getElementById('dateOfBirth').value,
            civilStatus: document.getElementById('civilStatus').value,
            rsbsaNo: document.getElementById('rsbsaNo').value,
            ncfrsNo: document.getElementById('ncfrsNo').value,
            address: document.getElementById('address').value,
            contactNo: document.getElementById('contactNo').value,
            registrationFee: document.getElementById('registrationFee').value,
            monthlyDuesPaid: document.getElementById('monthlyDuesPaid').value,
            foodConsumption: document.getElementById('foodConsumption').value,
            uriNgKalamidad: document.getElementById('uriNgKalamidad').value,
            niyogPuno: document.getElementById('niyogPuno').value,
            palayNasirangPct: document.getElementById('palayNasirangPct').value,
            gulayNasirangPct: document.getElementById('gulayNasirangPct').value,
            kabuuangKita: document.getElementById('kabuuangKitaDisplay').innerText,
            produksyon: [
                { produkto: "Palay", detalye: document.querySelectorAll('#prodTable tr')[0].cells[1].children[0].value, ani: document.querySelectorAll('#prodTable tr')[0].cells[2].children[0].value, kita: document.querySelectorAll('#prodTable tr')[0].cells[3].children[1].value },
                { produkto: "Niyog", detalye: document.querySelectorAll('#prodTable tr')[1].cells[1].children[0].value, ani: document.querySelectorAll('#prodTable tr')[1].cells[2].children[0].value, kita: document.querySelectorAll('#prodTable tr')[1].cells[3].children[1].value }
            ]
        };

        fetch(SCRIPT_URL, {
            method: 'POST',
            mode: 'no-cors',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(formData)
        }).then(() => {
            document.getElementById('loading').style.display = 'none';
            alert(actionType === 'delete' ? "Na-delete na sa Master Database!" : "Matagumpay na na-save sa Master Database!");
            if(actionType === 'save') window.print();
        }).catch(error => {
            document.getElementById('loading').style.display = 'none';
            alert("Error: " + error);
        });
    }
</script>

</body>
</html>
