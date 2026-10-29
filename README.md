<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal Dosen - Rekap & Kontrol Presensi 2026C</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
    </style>
</head>
<body class="bg-slate-100 text-slate-800 min-h-screen">

    <!-- Header / Navbar Dosen -->
    <nav class="bg-indigo-900 text-white shadow-md border-b border-indigo-800 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center space-x-3">
                    <div class="bg-indigo-600 p-2.5 rounded-xl shadow-inner">
                        <i class="fas fa-user-tie text-xl"></i>
                    </div>
                    <div>
                        <h1 class="font-bold text-lg leading-tight">Portal Dosen</h1>
                        <p class="text-xs text-indigo-300">Rekap & Kontrol Presensi Kelas 2026C</p>
                    </div>
                </div>
                <div class="flex items-center space-x-2">
                    <button onclick="exportCSV()" class="bg-emerald-600 hover:bg-emerald-700 text-white text-xs px-3 py-2 rounded-lg font-medium flex items-center space-x-1.5 transition shadow">
                        <i class="fas fa-file-excel"></i>
                        <span>Ekspor Excel</span>
                    </button>
                    <button onclick="resetData()" class="bg-rose-600 hover:bg-rose-700 text-white text-xs px-3 py-2 rounded-lg font-medium flex items-center space-x-1.5 transition shadow">
                        <i class="fas fa-undo"></i>
                        <span>Reset Data</span>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 space-y-6">

        <!-- Panel Kontrol Sesi Absen Mandiri -->
        <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
            <h2 class="text-base font-bold text-slate-800 mb-4 flex items-center gap-2">
                <i class="fas fa-broadcast-tower text-indigo-600"></i> Kontrol Sesi Absen Mandiri Mahasiswa
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-4 gap-4 items-end">
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Pilih Pertemuan</label>
                    <select id="adminMeetingSelect" class="w-full border border-slate-300 rounded-xl p-2.5 text-sm focus:ring-2 focus:ring-indigo-500">
                        <!-- Filled by JS -->
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">PIN Sesi Absen</label>
                    <input type="text" id="adminPinInput" value="1234" maxlength="6" class="w-full border border-slate-300 rounded-xl p-2.5 text-sm font-mono text-center tracking-widest font-bold">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Status Sesi</label>
                    <div id="sessionBadge" class="p-2.5 rounded-xl text-center text-xs font-bold bg-slate-100 text-slate-600 border">
                        TUTUP
                    </div>
                </div>
                <div>
                    <button id="toggleSessionBtn" onclick="toggleSession()" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2.5 px-4 rounded-xl shadow transition text-sm">
                        Buka Sesi Presensi
                    </button>
                </div>
            </div>
        </div>

        <!-- Metric Cards -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm flex items-center space-x-3">
                <div class="p-3 bg-blue-100 text-blue-600 rounded-xl"><i class="fas fa-users text-lg"></i></div>
                <div>
                    <p class="text-[11px] text-slate-500 font-medium">Total Mahasiswa</p>
                    <p class="text-lg font-bold text-slate-800">45 Mahasiswa</p>
                </div>
            </div>
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm flex items-center space-x-3">
                <div class="p-3 bg-emerald-100 text-emerald-600 rounded-xl"><i class="fas fa-user-check text-lg"></i></div>
                <div>
                    <p class="text-[11px] text-slate-500 font-medium">Pertemuan 1 - 7</p>
                    <p class="text-lg font-bold text-emerald-600">100% Hadir</p>
                </div>
            </div>
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm flex items-center space-x-3">
                <div class="p-3 bg-amber-100 text-amber-600 rounded-xl"><i class="fas fa-clock text-lg"></i></div>
                <div>
                    <p class="text-[11px] text-slate-500 font-medium">Sesi Aktif</p>
                    <p id="activeSessionInfo" class="text-lg font-bold text-slate-800">Pertemuan 8</p>
                </div>
            </div>
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm flex items-center space-x-3">
                <div class="p-3 bg-indigo-100 text-indigo-600 rounded-xl"><i class="fas fa-sync text-lg"></i></div>
                <div>
                    <p class="text-[11px] text-slate-500 font-medium">Status Sinkronisasi</p>
                    <p class="text-xs font-bold text-emerald-600 flex items-center gap-1">
                        <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span> Live Sync
                    </p>
                </div>
            </div>
        </div>

        <!-- Tabel Rekapitulasi Presensi Dosen -->
        <div class="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden">
            <div class="p-4 border-b border-slate-200 flex flex-col md:flex-row justify-between items-center gap-3">
                <h3 class="font-bold text-slate-800 flex items-center gap-2 text-sm">
                    <i class="fas fa-list-check text-indigo-600"></i> Rekapitulasi Presensi Mahasiswa (Pertemuan 1–16)
                </h3>
                <div class="w-full md:w-64">
                    <input type="text" id="adminSearchInput" oninput="renderTable()" placeholder="Cari Nama atau NIM..." class="w-full border border-slate-300 rounded-xl px-3 py-1.5 text-xs focus:ring-2 focus:ring-indigo-500">
                </div>
            </div>
            <div class="overflow-x-auto">
                <table class="w-full text-xs text-left">
                    <thead class="bg-slate-800 text-slate-200 uppercase font-semibold">
                        <tr>
                            <th class="p-2 border-b border-slate-700 text-center">No</th>
                            <th class="p-2 border-b border-slate-700">NIM</th>
                            <th class="p-2 border-b border-slate-700 min-w-[180px]">Nama Mahasiswa</th>
                            <!-- Columns 1 to 16 -->
                            <script>
                                for(let i=1; i<=16; i++) {
                                    document.write(`<th class="p-1 border-b border-slate-700 text-center min-w-[34px] ${i<=7?'bg-slate-700 text-emerald-400':''}">${i}</th>`);
                                }
                            </script>
                            <th class="p-2 border-b border-slate-700 text-center">% Hadir</th>
                        </tr>
                    </thead>
                    <tbody id="adminTableBody" class="divide-y divide-slate-200">
                        <!-- Loaded dynamically -->
                    </tbody>
                </table>
            </div>
        </div>

    </div>

    <script>
        const INITIAL_STUDENTS = [
            {"nim": "26050974010", "nama": "Rani Laili Fithriyani"},
            {"nim": "26050974027", "nama": "Rendy Ardika Putra Pratama"},
            {"nim": "26050974031", "nama": "Salza Maulidya Anjani"},
            {"nim": "26050974052", "nama": "Lauhil Ikhsani"},
            {"nim": "26050974060", "nama": "Efanes William Patiaraja Silaban"},
            {"nim": "26050974068", "nama": "Riska Alfiana"},
            {"nim": "26050974069", "nama": "Ardy Prasetyo Afandy"},
            {"nim": "26050974073", "nama": "Qayla Meisyahila Aniem"},
            {"nim": "26050974077", "nama": "Kakung Adhityatalenta"},
            {"nim": "26050974082", "nama": "Eka Kartika Sari"},
            {"nim": "26050974086", "nama": "Kharisma Qurotta A'yunni"},
            {"nim": "26050974091", "nama": "Adela Al Alaz"},
            {"nim": "26050974092", "nama": "Zahran rafif Ariffuddin"},
            {"nim": "26050974094", "nama": "Mochmmad Rifani Rohman"},
            {"nim": "26050974099", "nama": "Saylendra Surya Agung"},
            {"nim": "26050974105", "nama": "Chuzayn Ibadillah Almuqarrabin"},
            {"nim": "26050974108", "nama": "Hafizh Abrizam Deswantara"},
            {"nim": "26050974110", "nama": "Bahruddin Kendilwessy"},
            {"nim": "26050974111", "nama": "Putri Rizki Ardana"},
            {"nim": "26050974112", "nama": "Muhammad Fathih Ali Arrahman"},
            {"nim": "26050974118", "nama": "Lingga Bagus Bayuanggara"},
            {"nim": "26050974120", "nama": "Nurul Aini"},
            {"nim": "26050974122", "nama": "Muhammad Adnan Sabriila"},
            {"nim": "26050974126", "nama": "Raisah Sharliz Maherummisa"},
            {"nim": "26050974128", "nama": "Muhammad Shafrizal Al Ghozali"},
            {"nim": "26050974138", "nama": "Ayuni Putri Arifianti"},
            {"nim": "26050974139", "nama": "Nugroho Sutarko"},
            {"nim": "26050974140", "nama": "Achmad Alamil Huda"},
            {"nim": "26050974141", "nama": "Firnando Astrian Ramadhani"},
            {"nim": "26050974144", "nama": "Chelsea Negar Kuncoro"},
            {"nim": "26050974153", "nama": "Imtiaz Ahmad"},
            {"nim": "26050974155", "nama": "Achmad Fardhan Khafid"},
            {"nim": "26050974156", "nama": "Diva Qurrota A'yunin"},
            {"nim": "26050974160", "nama": "Himmah Qadriyah Almu'in"},
            {"nim": "26050974161", "nama": "Marco Ardiansyah Putra"},
            {"nim": "26050974165", "nama": "Achmad Qodri Azizi"},
            {"nim": "26050974166", "nama": "Muhammad Farrel Ivansyah Putra"},
            {"nim": "26050974168", "nama": "Neolene Putri Kusuma Wardhani"},
            {"nim": "26050974169", "nama": "Nauraffa Rayyano"},
            {"nim": "26050974173", "nama": "Muhammad Alif Farhan"},
            {"nim": "26050974174", "nama": "Mohammad Rafi Baihaqi"},
            {"nim": "26050974175", "nama": "Reihan Soma Sudarman"},
            {"nim": "26050974178", "nama": "Raihanun"},
            {"nim": "26050974180", "nama": "Ahmad Raka Saputra"},
            {"nim": "26050974181", "nama": "Rizky Yulief Estiawan"}
        ];

        let studentsData = [];
        let attendanceData = {};
        let activeSession = { meeting: 8, isOpen: false, pin: "1234" };

        window.onload = function() {
            loadData();
            initMeetingSelect();
            renderTable();
            updateSessionUI();

            // Real-time synchronization when student submits attendance in another tab/window
            window.addEventListener('storage', function(e) {
                if (e.key === 'pti_2026c_attendance' || e.key === 'pti_2026c_session') {
                    loadData();
                    renderTable();
                    updateSessionUI();
                }
            });
        };

        function loadData() {
            const savedStudents = localStorage.getItem('pti_2026c_students');
            studentsData = savedStudents ? JSON.parse(savedStudents) : INITIAL_STUDENTS;
            if (!savedStudents) localStorage.setItem('pti_2026c_students', JSON.stringify(INITIAL_STUDENTS));

            const savedAttendance = localStorage.getItem('pti_2026c_attendance');
            if (savedAttendance) {
                attendanceData = JSON.parse(savedAttendance);
            } else {
                studentsData.forEach(s => {
                    attendanceData[s.nim] = {};
                    for(let m=1; m<=7; m++) {
                        attendanceData[s.nim][m] = { status: 'Hadir', timestamp: '2026-09-01 08:00', note: 'Terabsen Otomatis' };
                    }
                });
                localStorage.setItem('pti_2026c_attendance', JSON.stringify(attendanceData));
            }

            const savedSession = localStorage.getItem('pti_2026c_session');
            if (savedSession) activeSession = JSON.parse(savedSession);
        }

        function initMeetingSelect() {
            const select = document.getElementById('adminMeetingSelect');
            select.innerHTML = '';
            for(let i=8; i<=16; i++) {
                const opt = document.createElement('option');
                opt.value = i;
                opt.textContent = `Pertemuan ${i}`;
                if (i === activeSession.meeting) opt.selected = true;
                select.appendChild(opt);
            }
        }

        function toggleSession() {
            const meeting = parseInt(document.getElementById('adminMeetingSelect').value);
            const pin = document.getElementById('adminPinInput').value.trim() || '1234';

            if (activeSession.isOpen && activeSession.meeting === meeting) {
                activeSession.isOpen = false;
            } else {
                activeSession.meeting = meeting;
                activeSession.pin = pin;
                activeSession.isOpen = true;
            }

            localStorage.setItem('pti_2026c_session', JSON.stringify(activeSession));
            updateSessionUI();
        }

        function updateSessionUI() {
            const badge = document.getElementById('sessionBadge');
            const btn = document.getElementById('toggleSessionBtn');

            document.getElementById('activeSessionInfo').textContent = `Pertemuan ${activeSession.meeting}`;

            if(activeSession.isOpen) {
                badge.className = "p-2.5 rounded-xl text-center text-xs font-bold bg-emerald-100 text-emerald-700 border border-emerald-300";
                badge.innerHTML = `<i class="fas fa-lock-open mr-1"></i> BUKA (P${activeSession.meeting} - PIN: ${activeSession.pin})`;
                btn.className = "w-full bg-rose-600 hover:bg-rose-700 text-white font-bold py-2.5 px-4 rounded-xl shadow transition text-sm";
                btn.textContent = "Tutup Sesi Presensi";
            } else {
                badge.className = "p-2.5 rounded-xl text-center text-xs font-bold bg-slate-100 text-slate-600 border border-slate-300";
                badge.innerHTML = `<i class="fas fa-lock mr-1"></i> TUTUP`;
                btn.className = "w-full bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2.5 px-4 rounded-xl shadow transition text-sm";
                btn.textContent = "Buka Sesi Presensi";
            }
        }

        function changeStatus(nim, meeting, newStatus) {
            if(!attendanceData[nim]) attendanceData[nim] = {};
            if(newStatus) {
                attendanceData[nim][meeting] = { status: newStatus, timestamp: new Date().toLocaleString('id-ID'), note: 'Diubah Manual oleh Dosen' };
            } else {
                delete attendanceData[nim][meeting];
            }
            localStorage.setItem('pti_2026c_attendance', JSON.stringify(attendanceData));
            renderTable();
        }

        function renderTable() {
            const tbody = document.getElementById('adminTableBody');
            const search = document.getElementById('adminSearchInput').value.toLowerCase();
            tbody.innerHTML = '';

            studentsData.forEach((s, index) => {
                if (search && !s.nama.toLowerCase().includes(search) && !s.nim.includes(search)) return;

                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-50 transition border-b border-slate-200";

                let hadirCount = 0;
                let cellsHtml = '';

                for(let m=1; m<=16; m++) {
                    const rec = attendanceData[s.nim] && attendanceData[s.nim][m];
                    const status = rec ? rec.status : '-';
                    if(status === 'Hadir') hadirCount++;

                    let badgeColor = "text-slate-400";
                    if(status === 'Hadir') badgeColor = "font-bold text-emerald-600";
                    if(status === 'Izin') badgeColor = "font-bold text-amber-600";
                    if(status === 'Sakit') badgeColor = "font-bold text-blue-600";
                    if(status === 'Alpa') badgeColor = "font-bold text-rose-600";

                    cellsHtml += `
                        <td class="p-1 text-center border-r border-slate-100">
                            <select onchange="changeStatus('${s.nim}', ${m}, this.value)" class="text-[10px] p-0.5 rounded border border-slate-200 ${badgeColor} bg-transparent cursor-pointer">
                                <option value="" ${status==='-'?'selected':''}>-</option>
                                <option value="Hadir" ${status==='Hadir'?'selected':''}>H</option>
                                <option value="Izin" ${status==='Izin'?'selected':''}>I</option>
                                <option value="Sakit" ${status==='Sakit'?'selected':''}>S</option>
                                <option value="Alpa" ${status==='Alpa'?'selected':''}>A</option>
                            </select>
                        </td>
                    `;
                }

                const pct = Math.round((hadirCount / 16) * 100);

                tr.innerHTML = `
                    <td class="p-2 text-center text-slate-500 font-medium">${index + 1}</td>
                    <td class="p-2 font-mono text-slate-600">${s.nim}</td>
                    <td class="p-2 font-semibold text-slate-800">${s.nama}</td>
                    ${cellsHtml}
                    <td class="p-2 text-center font-bold ${pct>=80?'text-emerald-600':pct>=70?'text-amber-600':'text-rose-600'}">${pct}%</td>
                `;
                tbody.appendChild(tr);
            });
        }

        function exportCSV() {
            let csv = "No,NIM,Nama Mahasiswa," + Array.from({length:16}, (_,i) => `P${i+1}`).join(",") + ",Persentase Hadir\n";
            studentsData.forEach((s, idx) => {
                let hadir = 0;
                let row = [idx + 1, `"${s.nim}"`, `"${s.nama}"`];
                for(let m=1; m<=16; m++) {
                    const st = (attendanceData[s.nim] && attendanceData[s.nim][m]) ? attendanceData[s.nim][m].status : '-';
                    if(st === 'Hadir') hadir++;
                    row.push(st);
                }
                row.push(`${Math.round((hadir/16)*100)}%`);
                csv += row.join(",") + "\n";
            });

            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement("a");
            link.href = URL.createObjectURL(blob);
            link.setAttribute("download", `Rekap_Presensi_Kelas_2026C.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        function resetData() {
            if(confirm("Apakah Anda yakin ingin mereset data presensi kembali ke default (P1-P7 Hadir)?")) {
                localStorage.removeItem('pti_2026c_attendance');
                localStorage.removeItem('pti_2026c_session');
                loadData();
                renderTable();
                updateSessionUI();
                alert("Data berhasil direset!");
            }
        }
    </script>
</body>
</html>
