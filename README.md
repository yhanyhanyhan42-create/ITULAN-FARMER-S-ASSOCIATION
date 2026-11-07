<!DOCTYPE html>
<html lang="tl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Itulan Farmers Association - Master Portal</title>
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
        .logo-container {
            text-align: center;
            margin-bottom: 10px;
        }
        .logo-container img {
            width: 100px;
            height: 100px;
            object-fit: contain;
            border-radius: 50%;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
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

        .btn { padding: 9px 15px; border: none; border-radius: 4px; cursor: pointer; font-weight: bold; font-size: 12px; margin: 3px; }
        .btn-save { background: #16a34a; color: white; }
        .btn-add { background: #0284c7; color: white; }
        .btn-print { background: #d97706; color: white; }
        .btn-delete { background: #dc2626; color: white; }
        .btn-logout { background: #64748b; color: white; }
        
        .footer { text-align: center; font-size: 11px; color: #94a3b8; margin-top: 30px; border-top: 1px solid #e2e8f0; padding-top: 12px; }
        #loading { display: none; text-align: center; color: #0284c7; font-weight: bold; margin-top: 10px; }

        @media print {
            body { background: white; padding: 0; }
            .nav-tabs, #officerLogin, .btn-container, .security-banner, .footer { display: none !important; }
            .container { box-shadow: none; padding: 0; max-width: 100%; }
        }
    </style>
</head>
<body>

<div class="container">
    <!-- OPISYAL NA LOGO (Naka-embed na direkta sa code) -->
    <div class="logo-container">
        <img id="associationLogo" src="logo.png" alt="Itulan Farmers Association Logo">
    </div>

    <h2 class="title">Itulan Farmers Association</h2>
    <div class="subtitle">Zone 3, Itulan, Pasacao, Camarines Sur</div>

    <!-- TABS MENU -->
    <div class="nav-tabs">
        <button class="tab-btn active" id="tabPublic" onclick="switchTab('public')">📢 Public Transparent View</button>
        <button class="tab-btn" id="tabOfficer" onclick="switchTab('officer')">🔒 Officers Portal</button>
    </div>

    <!-- 1. PUBLIC TRANSPARENT VIEW -->
    <div id="publicView">
        <div class="section-header">Pangkalahatang Talaan ng Miyembro at Bayarin (Monthly Dues Target: ₱120)</div>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Pangalan</th>
                    <th>Posisyon</th>
                    <th>Reg. Fee (₱100)</th>
                    <th>Monthly Dues Naibayad</th>
                    <th>Kulang</th>
                    <th>Katayuan</th>
                </tr>
            </thead>
            <tbody id="publicTableBody">
                <tr><td>IFA-2024-001</td><td>Guavar, Rayan D.</td><td>Kasaping Magsasaka</td><td><span class="badge-paid">₱100</span></td><td>₱20</td><td><span class="badge-bal">₱100</span></td><td><span class="badge-bal">May Balanse</span></td></tr>
                <tr><td>IFA-2024-002</td><td>Alcantara, Danilo M.</td><td>Pangulo</td><td><span class="badge-paid">₱100</span></td><td>₱120</td><td><span class="badge-paid">₱0</span></td><td><span class="badge-paid">Bayad na</span></td></tr>
                <tr><td>IFA-2024-003</td><td>Mendoza, Elena S.</td><td>Ingat-Yaman</td><td><span class="badge-paid">₱100</span></td><td>₱120</td><td><span class="badge-paid">₱0</span></td><td><span class="badge-paid">Bayad na</span></td></tr>
                <tr><td>IFA-2024-004</td><td>Ramos, Vicente T.</td><td>Kasaping Magsasaka</td><td><span class="badge-paid">₱100</span></td><td>₱60</td><td><span class="badge-bal">₱60</span></td><td><span class="badge-bal">May Balanse</span></td></tr>
                <tr><td>IFA-2024-005</td><td>Bordon, Maria Fe C.</td><td>Kalihim</td><td><span class="badge-paid">₱100</span></td><td>₱120</td><td><span class="badge-paid">₱0</span></td><td><span class="badge-paid">Bayad na</span></td></tr>
            </tbody>
        </table>
        <p style="font-size: 11px; color: #64748b; text-align: center;">* Transparent view para sa lahat ng miyembro. Read-only mode.</p>
    </div>

    <!-- 2. OFFICERS PORTAL -->
    <div id="officersView" style="display: none;">
        <!-- Password Login Section -->
        <div id="officerLogin" style="text-align: center; padding: 30px;">
            <h3>Officers Access Control</h3>
            <p style="font-size: 13px; color: #64748b;">Ilagay ang password ng Opisyal para mag-edit, mag-save, o mag-print:</p>
            <input type="password" id="officerPassword" placeholder="Ilagay ang Password" style="width: 250px; padding: 8px;">
            <button class="btn btn-add" onclick="loginOfficer()">Pumasok</button>
            <div id="loginError" style="color: #dc2626; font-size: 12px; margin-top: 8px; display: none;">Mali ang password!</div>
        </div>

        <!-- Member Profile Editor -->
        <div id="officerEditor" style="display: none;">
            <div class="security-banner">
                OFFICERS PORTAL: Pumili ng miyembro o magdagdag ng bago. Gamitin ang hiwalay na buttons para sa Save, Add, Print, o Delete.
            </div>

            <!-- MEMBER SELECTOR DROPDOWN & NEW BUTTON -->
            <div style="background: #e2e8f0; padding: 12px; border-radius: 4px; margin-bottom: 20px; display: flex; align-items: center; justify-content: space-between;">
                <label for="memberSelect" style="font-weight: bold; font-size: 13px;">Pumili ng Miyembro:</label>
                <select id="memberSelect" onchange="loadMemberProfile()" style="width: 60%;">
                    <option value="0">IFA-2024-001 | Guavar, Rayan D. (Kasaping Magsasaka)</option>
                    <option value="1">IFA-2024-002 | Alcantara, Danilo M. (Pangulo)</option>
                    <option value="2">IFA-2024-003 | Mendoza, Elena S. (Ingat-Yaman)</option>
                    <option value="3">IFA-2024-004 | Ramos, Vicente T. (Kasaping Magsasaka)</option>
                    <option value="4">IFA-2024-005 | Bordon, Maria Fe C. (Kalihim)</option>
                </select>
                <button type="button" class="btn btn-add" onclick="clearFormForNew()" style="font-size: 11px;">+ Bagong Miyembro</button>
            </div>

            <form id="masterForm">
                <div class="section-header">1. Personal na Impormasyon at Bayarin</div>
                <table>
                    <tr><td width="30%"><strong>ID ng Miyembro:</strong></td><td><input type="text" id="idMiyembro"></td></tr>
                    <tr><td><strong>Buong Pangalan:</strong></td><td><input type="text" id="pangalan"></td></tr>
                    <tr><td><strong>Posisyon:</strong></td><td><input type="text" id="posisyon"></td></tr>
                    <tr><td><strong>Member Since:</strong></td><td><input type="text" id="memberSince"></td></tr>
                    <tr><td><strong>Edad / Kasarian:</strong></td><td><input type="text" id="edadKasarian"></td></tr>
                    <tr><td><strong>Date of Birth:</strong></td><td><input type="text" id="dateOfBirth"></td></tr>
                    <tr><td><strong>Civil Status:</strong></td><td><input type="text" id="civilStatus"></td></tr>
                    <tr><td><strong>RSBSA No.:</strong></td><td><input type="text" id="rsbsaNo"></td></tr>
                    <tr><td><strong>NCFRS No.:</strong></td><td><input type="text" id="ncfrsNo"></td></tr>
                    <tr><td><strong>Address:</strong></td><td><input type="text" id="address"></td></tr>
                    <tr><td><strong>Contact No.:</strong></td><td><input type="text" id="contactNo"></td></tr>
                    <tr><td><strong>Registration Fee Naibayad (₱):</strong></td><td><input type="number" id="registrationFee"></td></tr>
                    <tr><td><strong>Monthly Dues Naibayad (₱):</strong></td><td><input type="number" id="monthlyDuesPaid" oninput="calcDuesBalance()"></td></tr>
                    <tr><td><strong>Kulang sa Monthly Dues (₱):</strong></td><td><input type="number" id="monthlyDuesBalance" readonly style="background: #f8fafc;"></td></tr>
                    <tr><td><strong>Food Consumption:</strong></td><td><input type="text" id="foodConsumption"></td></tr>
                </table>

                <div class="section-header">2. Ulat ng Pinsala ng Kalamidad</div>
                <table>
                    <tr><td width="30%"><strong>Uri ng Kalamidad:</strong></td><td><input type="text" id="uriNgKalamidad"></td></tr>
                    <tr><td><strong>Niyog (Nasirang Puno):</strong></td><td><input type="text" id="niyogPuno"></td></tr>
                    <tr><td><strong>Palay (Nasirang %):</strong></td><td><input type="text" id="palayNasirangPct"></td></tr>
                    <tr><td><strong>Gulay (Nasirang %):</strong></td><td><input type="text" id="gulayNasirangPct"></td></tr>
                </table>

                <div class="section-header">3. Produksyon at Kita</div>
                <table>
                    <thead>
                        <tr><th>Produkto</th><th>Sukat / Detalye</th><th>Ani / Cropping</th><th>Kita (₱)</th></tr>
                    </thead>
                    <tbody id="prodTable">
                        <tr><td>Palay</td><td><input type="text" id="palayDet"></td><td><input type="text" id="palayAni"></td><td>₱ <input type="number" class="kita-input" id="palayKita" oninput="computeTotal()"></td></tr>
                        <tr><td>Niyog</td><td><input type="text" id="niyogDet"></td><td><input type="text" id="niyogAni"></td><td>₱ <input type="number" class="kita-input" id="niyogKita" oninput="computeTotal()"></td></tr>
                    </tbody>
                </table>
                <div style="text-align: right; font-weight: bold; margin-bottom: 15px;">
                    Kabuuang Kita: <span id="kabuuangKitaDisplay" style="color: #0284c7;">₱0</span>
                </div>

                <!-- BUTTONS PARA SA SAVE, ADD, PRINT, AT DELETE -->
                <div class="btn-container" style="text-align: center;">
                    <button type="button" class="btn btn-save" onclick="submitData('save')">💾 I-save ang Pagbabago</button>
                    <button type="button" class="btn btn-add" onclick="submitData('add')">➕ Idagdag bilang Bago</button>
                    <button type="button" class="btn btn-print" onclick="window.print()">🖨️ I-print ang Profile</button>
                    <button type="button" class="btn btn-delete" onclick="submitData('delete')">🗑️ I-delete</button>
                    <button type="button" class="btn btn-logout" onclick="logoutOfficer()">🔒 Mag-logout</button>
                    <div id="loading">Nagsasave sa Google Cloud Database... Sandali lang po.</div>
                </div>
            </form>
        </div>
    </div>

    <div class="footer">
        Itulan Farmers Association &copy; 2026. Master Database Management System.
    </div>
</div>

<script>
    const OFFICER_PASS = "Int3rn3tWisp2021";
    const SCRIPT_URL = "YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE"; // Palitan ng iyong Web App URL

    const membersData = [
        { idMiyembro: "IFA-2024-001", pangalan: "Guavar, Rayan D.", posisyon: "Kasaping Magsasaka", memberSince: "2024", edadKasarian: "31 | Lalaki", dateOfBirth: "1995-03-10", civilStatus: "May Asawa", rsbsaNo: "Wala", ncfrsNo: "Wala", address: "Zone 3, Itulan, Pasacao", contactNo: "9637657151", registrationFee: 100, monthlyDuesPaid: 20, foodConsumption: "30 sako (Palay)", uriNgKalamidad: "Wala", niyogPuno: "Wala", palayNasirangPct: "Wala", gulayNasirangPct: "Wala", palayDet: "1.5 Hektarya", palayAni: "145 Kaban", palayKita: 166750, niyogDet: "1 Hektarya", niyogAni: "2400 Kilo", niyogKita: 87600 },
        { idMiyembro: "IFA-2024-002", pangalan: "Alcantara, Danilo M.", posisyon: "Pangulo", memberSince: "2024", edadKasarian: "48 | Lalaki", dateOfBirth: "1976-08-22", civilStatus: "May Asawa", rsbsaNo: "RSBSA-0291", ncfrsNo: "NCFRS-881", address: "Zone 3, Itulan, Pasacao", contactNo: "9194567821", registrationFee: 100, monthlyDuesPaid: 120, foodConsumption: "25 sako (Palay)", uriNgKalamidad: "Bagyo", niyogPuno: "5 Puno", palayNasirangPct: "10%", gulayNasirangPct: "Wala", palayDet: "2 Hektarya", palayAni: "190 Kaban", palayKita: 218500, niyogDet: "1.2 Hektarya", niyogAni: "3000 Kilo", niyogKita: 105000 },
        { idMiyembro: "IFA-2024-003", pangalan: "Mendoza, Elena S.", posisyon: "Ingat-Yaman", memberSince: "2024", edadKasarian: "42 | Babae", dateOfBirth: "1982-11-05", civilStatus: "May Asawa", rsbsaNo: "RSBSA-0492", ncfrsNo: "NCFRS-902", address: "Zone 3, Itulan, Pasacao", contactNo: "9283459012", registrationFee: 100, monthlyDuesPaid: 120, foodConsumption: "20 sako (Palay)", uriNgKalamidad: "Wala", niyogPuno: "Wala", palayNasirangPct: "Wala", gulayNasirangPct: "Wala", palayDet: "1 Hektarya", palayAni: "110 Kaban", palayKita: 126500, niyogDet: "1 Hektarya", niyogAni: "4500 Piraso", niyogKita: 63000 },
        { idMiyembro: "IFA-2024-004", pangalan: "Ramos, Vicente T.", posisyon: "Kasaping Magsasaka", memberSince: "2024", edadKasarian: "55 | Lalaki", dateOfBirth: "1969-04-18", civilStatus: "May Asawa", rsbsaNo: "Wala", ncfrsNo: "Wala", address: "Zone 3, Itulan, Pasacao", contactNo: "9391238475", registrationFee: 100, monthlyDuesPaid: 60, foodConsumption: "35 sako (Palay)", uriNgKalamidad: "Tagtuyot", niyogPuno: "12 Puno", palayNasirangPct: "25%", gulayNasirangPct: "15%", palayDet: "1.2 Hektarya", palayAni: "95 Kaban", palayKita: 109250, niyogDet: "0.8 Hektarya", niyogAni: "1800 Kilo", niyogKita: 65000 },
        { idMiyembro: "IFA-2024-005", pangalan: "Bordon, Maria Fe C.", posisyon: "Kalihim", memberSince: "2024", edadKasarian: "38 | Babae", dateOfBirth: "1986-01-30", civilStatus: "Walang Asawa", rsbsaNo: "RSBSA-0812", ncfrsNo: "NCFRS-114", address: "Zone 3, Itulan, Pasacao", contactNo: "9475628193", registrationFee: 100, monthlyDuesPaid: 120, foodConsumption: "20 sako (Palay)", uriNgKalamidad: "Wala", niyogPuno: "Wala", palayNasirangPct: "Wala", gulayNasirangPct: "Wala", palayDet: "1 Hektarya", palayAni: "105 Kaban", palayKita: 120750, niyogDet: "1 Hektarya", niyogAni: "2200 Kilo", niyogKita: 80000 }
    ];

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
            loadMemberProfile();
        } else {
            document.getElementById('loginError').style.display = 'block';
        }
    }

    function logoutOfficer() {
        document.getElementById('officerPassword').value = '';
        document.getElementById('officerLogin').style.display = 'block';
        document.getElementById('officerEditor').style.display = 'none';
    }

    function loadMemberProfile() {
        let index = document.getElementById('memberSelect').value;
        let m = membersData[index];

        document.getElementById('idMiyembro').value = m.idMiyembro;
        document.getElementById('pangalan').value = m.pangalan;
        document.getElementById('posisyon').value = m.posisyon;
        document.getElementById('memberSince').value = m.memberSince;
        document.getElementById('edadKasarian').value = m.edadKasarian;
        document.getElementById('dateOfBirth').value = m.dateOfBirth;
        document.getElementById('civilStatus').value = m.civilStatus;
        document.getElementById('rsbsaNo').value = m.rsbsaNo;
        document.getElementById('ncfrsNo').value = m.ncfrsNo;
        document.getElementById('address').value = m.address;
        document.getElementById('contactNo').value = m.contactNo;
        document.getElementById('registrationFee').value = m.registrationFee;
        document.getElementById('monthlyDuesPaid').value = m.monthlyDuesPaid;
        document.getElementById('foodConsumption').value = m.foodConsumption;
        document.getElementById('uriNgKalamidad').value = m.uriNgKalamidad;
        document.getElementById('niyogPuno').value = m.niyogPuno;
        document.getElementById('palayNasirangPct').value = m.palayNasirangPct;
        document.getElementById('gulayNasirangPct').value = m.gulayNasirangPct;
        document.getElementById('palayDet').value = m.palayDet;
        document.getElementById('palayAni').value = m.palayAni;
        document.getElementById('palayKita').value = m.palayKita;
        document.getElementById('niyogDet').value = m.niyogDet;
        document.getElementById('niyogAni').value = m.niyogAni;
        document.getElementById('niyogKita').value = m.niyogKita;

        calcDuesBalance();
        computeTotal();
    }

    function clearFormForNew() {
        document.getElementById('idMiyembro').value = "IFA-2024-00" + (membersData.length + 1);
        document.getElementById('pangalan').value = "";
        document.getElementById('posisyon').value = "Kasaping Magsasaka";
        document.getElementById('memberSince').value = "2026";
        document.getElementById('edadKasarian').value = "";
        document.getElementById('dateOfBirth').value = "";
        document.getElementById('civilStatus').value = "";
        document.getElementById('rsbsaNo').value = "Wala";
        document.getElementById('ncfrsNo').value = "Wala";
        document.getElementById('address').value = "Zone 3, Itulan, Pasacao";
        document.getElementById('contactNo').value = "";
        document.getElementById('registrationFee').value = 100;
        document.getElementById('monthlyDuesPaid').value = 0;
        document.getElementById('foodConsumption').value = "30 sako (Palay)";
        document.getElementById('uriNgKalamidad').value = "Wala";
        document.getElementById('niyogPuno').value = "Wala";
        document.getElementById('palayNasirangPct').value = "Wala";
        document.getElementById('gulayNasirangPct').value = "Wala";
        document.getElementById('palayDet').value = "";
        document.getElementById('palayAni').value = "";
        document.getElementById('palayKita').value = 0;
        document.getElementById('niyogDet').value = "";
        document.getElementById('niyogAni').value = "";
        document.getElementById('niyogKita').value = 0;
        calcDuesBalance();
        computeTotal();
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
        let name = document.getElementById('pangalan').value;
        let msg = "";
        if(actionType === 'save') msg = "I-save ba ang pagbabago kay " + name + "?";
        else if(actionType === 'add') msg = "Idagdag ba si " + name + " bilang bagong miyembro?";
        else if(actionType === 'delete') msg = "I-delete ba si " + name + " sa database?";

        if(!confirm(msg)) return;

        document.getElementById('loading').style.display = 'block';

        let formData = {
            action: actionType,
            idMiyembro: document.getElementById('idMiyembro').value,
            pangalan: name,
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
                { produkto: "Palay", detalye: document.getElementById('palayDet').value, ani: document.getElementById('palayAni').value, kita: document.getElementById('palayKita').value },
                { produkto: "Niyog", detalye: document.getElementById('niyogDet').value, ani: document.getElementById('niyogAni').value, kita: document.getElementById('niyogKita').value }
            ]
        };

        fetch(SCRIPT_URL, {
            method: 'POST',
            mode: 'no-cors',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(formData)
        }).then(() => {
            document.getElementById('loading').style.display = 'none';
            alert("Matagumpay na naisagawa ang operasyon sa Google Cloud Database!");
        }).catch(error => {
            document.getElementById('loading').style.display = 'none';
            alert("Error: " + error);
        });
    }
</script>

</body>
</html>
