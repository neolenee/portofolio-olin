<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portofolio - Neolene Putri Kusuma Wardhani</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                    },
                    colors: {
                        ocean: {
                            deep: '#010a15', 
                            mid: '#073259',
                            cyan: '#0083B0',
                            light: '#00B4DB'
                        }
                    }
                }
            }
        }
    </script>
    
    <style>
        body {
            background: linear-gradient(to bottom, #00B4DB 0%, #0083B0 40%, #073259 80%, #010a15 100%);
            background-attachment: fixed;
            color: #f8fafc;
            min-height: 100vh;
            overflow-x: hidden;
            margin: 0;
        }

        #bubbleCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0; /* Di belakang konten utama */
            pointer-events: none; /* Agar tidak menghalangi klik */
        }
        
        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
            border-radius: 1rem;
            position: relative;
            z-index: 10;
        }
        
        .glass-card:hover {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.25);
            transform: translateY(-3px);
            transition: all 0.3s ease;
        }

        .spongebob-swimming {
            position: fixed;
            bottom: 3%;
            z-index: 5;
            opacity: 0.9;
            pointer-events: none;
            width: 130px;
            animation: swimAcross 25s linear infinite;
        }

        @keyframes swimAcross {
            0% { left: -150px; transform: scaleX(1) translateY(0px) rotate(5deg); }
            25% { transform: scaleX(1) translateY(-30px) rotate(-5deg); }
            49% { left: 110%; transform: scaleX(1) translateY(0px); }
            50% { left: 110%; transform: scaleX(-1) translateY(0px); }
            75% { transform: scaleX(-1) translateY(-30px) rotate(-5deg); }
            100% { left: -150px; transform: scaleX(-1) translateY(0px) rotate(5deg); }
        }
    </style>
</head>
<body class="antialiased font-sans relative pb-20">
    
    <canvas id="bubbleCanvas"></canvas>
    
    <img src="https://media.giphy.com/media/l1Et0Z20iE9QxIuuQ/giphy.gif" alt="SpongeBob Swimming" class="spongebob-swimming">

    <main class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 pt-16 space-y-8">
        
        <header class="glass-card p-8 md:p-12">
            <div class="flex flex-col md:flex-row items-center md:items-start gap-8">
                
                <div class="shrink-0">
                    <div class="w-40 h-40 md:w-48 md:h-48 rounded-full bg-gradient-to-tr from-cyan-300 to-blue-500 p-1.5 shadow-[0_0_20px_rgba(6,182,212,0.6)]">
                        <div class="w-full h-full rounded-full bg-ocean-mid overflow-hidden border-4 border-transparent flex items-center justify-center">
                            <img src="1000272646.png" alt="Neolene Putri Kusuma Wardhani" class="w-full h-full object-cover">
                        </div>
                    </div>
                </div>
                
                <div class="flex-1 text-center md:text-left flex flex-col justify-center">
                    <h1 class="text-3xl md:text-5xl font-bold text-white tracking-tight mb-2 drop-shadow-lg">
                        Neolene Putri Kusuma Wardhani
                    </h1>
                    <p class="text-lg md:text-xl text-cyan-100 font-medium mb-4 drop-shadow-md">
                        Mahasiswa Pendidikan Teknologi Informasi | Universitas Negeri Surabaya
                    </p>
                    
                    <p class="text-sm text-gray-200 leading-relaxed mb-6 max-w-3xl">
                        Saya tertarik ke bidang data entry dan data analysts, serta memiliki ketertarikan kuat pada fotografi. Saya adalah individu yang rajin, teliti, dan disiplin dalam setiap pekerjaan.
                    </p>
                    
                    <div class="flex flex-wrap justify-center md:justify-start gap-3">
                        <a href="mailto:neowardhani8@gmail.com" class="px-5 py-2.5 bg-white/10 hover:bg-cyan-500/30 backdrop-blur-md border border-cyan-300/30 rounded-full transition-all text-sm font-medium flex items-center gap-2 shadow-lg">
                            <i class="fas fa-envelope text-cyan-300"></i> Email
                        </a>
                        <a href="https://www.linkedin.com/in/neolene-putri-kusuma-wardhani-8a36ab442" target="_blank" class="px-5 py-2.5 bg-white/10 hover:bg-blue-500/30 backdrop-blur-md border border-blue-300/30 rounded-full transition-all text-sm font-medium flex items-center gap-2 shadow-lg">
                            <i class="fab fa-linkedin text-blue-300"></i> LinkedIn
                        </a>
                        <a href="https://github.com/neolenee" target="_blank" class="px-5 py-2.5 bg-white/10 hover:bg-gray-500/30 backdrop-blur-md border border-gray-300/30 rounded-full transition-all text-sm font-medium flex items-center gap-2 shadow-lg">
                            <i class="fab fa-github text-gray-200"></i> GitHub
                        </a>
                    </div>
                </div>
            </div>
        </header>

        <div class="grid grid-cols-1 md:grid-cols-12 gap-8">
            
            <!-- Kolom Kiri -->
            <div class="md:col-span-4 space-y-8">
                
                <section class="glass-card p-6">
                    <h2 class="text-lg font-semibold text-cyan-300 mb-4 flex items-center gap-2 border-b border-white/10 pb-2">
                        <i class="fas fa-id-card"></i> Identitas
                    </h2>
                    <ul class="text-sm text-gray-200 space-y-3">
                        <li class="flex flex-col"><span class="text-cyan-400 text-xs font-semibold uppercase tracking-wider">Nama Lengkap</span> <span class="font-medium">Neolene Putri Kusuma Wardhani</span></li>
                        <li class="flex flex-col"><span class="text-cyan-400 text-xs font-semibold uppercase tracking-wider">NIM</span> <span class="font-medium">26050974168</span></li>
                        <li class="flex flex-col"><span class="text-cyan-400 text-xs font-semibold uppercase tracking-wider">Program Studi</span> <span class="font-medium">Pendidikan Teknologi Informasi</span></li>
                    </ul>
                </section>

                <section class="glass-card p-6">
                    <h2 class="text-lg font-semibold text-cyan-300 mb-4 flex items-center gap-2 border-b border-white/10 pb-2">
                        <i class="fas fa-graduation-cap"></i> Pendidikan
                    </h2>
                    <div class="space-y-5">
                        <div class="relative pl-4 border-l-2 border-cyan-500/50">
                            <div class="absolute w-3 h-3 bg-cyan-400 rounded-full -left-[7px] top-1 shadow-[0_0_8px_#22d3ee]"></div>
                            <h3 class="font-semibold text-white text-sm">Universitas Negeri Surabaya</h3>
                            <p class="text-xs text-cyan-200 mt-1">Agustus 2026 - Sekarang</p>
                        </div>
                        <div class="relative pl-4 border-l-2 border-cyan-500/30">
                            <div class="absolute w-3 h-3 bg-gray-400 rounded-full -left-[7px] top-1"></div>
                            <h3 class="font-medium text-gray-200 text-sm">SMA Perguruan Rakyat 2 Jakarta</h3>
                            <p class="text-xs text-gray-400 mt-1">2023 - 2026</p>
                        </div>
                    </div>
                </section>

                <section class="glass-card p-6">
                    <h2 class="text-lg font-semibold text-cyan-300 mb-4 flex items-center gap-2 border-b border-white/10 pb-2">
                        <i class="fas fa-running"></i> Aktivitas
                    </h2>
                    <ul class="space-y-3 text-sm text-gray-200">
                        <li class="flex items-start gap-3 bg-white/5 p-2 rounded border border-white/5">
                            <i class="fas fa-camera text-cyan-400 mt-0.5"></i>
                            <span>Fotografi & Dokumentasi</span>
                        </li>
                        <li class="flex items-start gap-3 bg-white/5 p-2 rounded border border-white/5">
                            <i class="fas fa-users-cog text-cyan-400 mt-0.5"></i>
                            <span>Penanggung Jawab (PJ) Mata Kuliah</span>
                        </li>
                        <li class="flex items-start gap-3 bg-white/5 p-2 rounded border border-white/5">
                            <i class="fas fa-university text-cyan-400 mt-0.5"></i>
                            <span>Berpartisipasi aktif dalam kegiatan akademik dan kampus</span>
                        </li>
                    </ul>
                </section>

            </div>

            <!-- Kolom Kanan -->
            <div class="md:col-span-8 space-y-8">
                
                <section class="glass-card p-6 md:p-8">
                    <h2 class="text-xl font-semibold text-cyan-300 mb-4 flex items-center gap-2 border-b border-white/10 pb-2">
                        <i class="fas fa-layer-group"></i> Keahlian & Keterampilan
                    </h2>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                        <!-- Hard Skills -->
                        <div>
                            <h3 class="text-sm font-semibold text-white mb-3 uppercase tracking-wider bg-white/5 inline-block px-3 py-1 rounded">Hard Skills</h3>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-3 py-1 bg-cyan-900/40 text-cyan-100 text-xs rounded-full border border-cyan-500/30">Data Entry</span>
                                <span class="px-3 py-1 bg-cyan-900/40 text-cyan-100 text-xs rounded-full border border-cyan-500/30">Administrasi</span>
                                <span class="px-3 py-1 bg-cyan-900/40 text-cyan-100 text-xs rounded-full border border-cyan-500/30">Microsoft Excel & Google Sheets</span>
                                <span class="px-3 py-1 bg-cyan-900/40 text-cyan-100 text-xs rounded-full border border-cyan-500/30">Microsoft 365</span>
                                <span class="px-3 py-1 bg-cyan-900/40 text-cyan-100 text-xs rounded-full border border-cyan-500/30">Manajemen Stok</span>
                                <span class="px-3 py-1 bg-cyan-900/40 text-cyan-100 text-xs rounded-full border border-cyan-500/30">Pengolahan Data Sederhana</span>
                            </div>
                        </div>
                        
                        <!-- Soft Skills -->
                        <div>
                            <h3 class="text-sm font-semibold text-white mb-3 uppercase tracking-wider bg-white/5 inline-block px-3 py-1 rounded">Soft Skills</h3>
                            <div class="flex flex-wrap gap-2">
                                <span class="px-3 py-1 bg-blue-900/40 text-blue-100 text-xs rounded-full border border-blue-500/30">Pelayanan Pelanggan</span>
                                <span class="px-3 py-1 bg-blue-900/40 text-blue-100 text-xs rounded-full border border-blue-500/30">Komunikasi Interpersonal</span>
                                <span class="px-3 py-1 bg-blue-900/40 text-blue-100 text-xs rounded-full border border-blue-500/30">Ketelitian</span>
                                <span class="px-3 py-1 bg-blue-900/40 text-blue-100 text-xs rounded-full border border-blue-500/30">Manajemen Waktu</span>
                                <span class="px-3 py-1 bg-blue-900/40 text-blue-100 text-xs rounded-full border border-blue-500/30">Disiplin</span>
                                <span class="px-3 py-1 bg-blue-900/40 text-blue-100 text-xs rounded-full border border-blue-500/30">Koordinasi & Kepemimpinan</span>
                            </div>
                        </div>
                    </div>

                    <div>
                        <h3 class="text-sm font-semibold text-white mb-3 uppercase tracking-wider bg-white/5 inline-block px-3 py-1 rounded">Kemampuan Praktis & Tools</h3>
                        <ul class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-sm text-gray-300">
                            <li class="flex items-center gap-2"><i class="fas fa-check text-cyan-400"></i> Fotografi & Dokumentasi Kegiatan</li>
                            <li class="flex items-center gap-2"><i class="fas fa-check text-cyan-400"></i> Menyusun Dokumen & Laporan</li>
                            <li class="flex items-center gap-2"><i class="fas fa-check text-cyan-400"></i> Pembuatan Materi Presentasi</li>
                            <li class="flex items-center gap-2"><i class="fas fa-tools text-cyan-400"></i> Microsoft Word, Excel, PowerPoint</li>
                            <li class="flex items-center gap-2"><i class="fas fa-tools text-cyan-400"></i> Aplikasi Pengeditan Foto Sederhana</li>
                        </ul>
                    </div>
                </section>

                <section class="glass-card p-6 md:p-8">
                    <h2 class="text-xl font-semibold text-cyan-300 mb-4 flex items-center gap-2 border-b border-white/10 pb-2">
                        <i class="fas fa-briefcase"></i> Pengalaman Kerja
                    </h2>
                    
                    <div class="bg-gradient-to-r from-white/5 to-transparent rounded-lg p-5 border border-white/10 relative overflow-hidden group hover:border-cyan-500/50 transition-all">
                        <i class="fas fa-jellyfish absolute -bottom-6 right-0 text-8xl text-cyan-500/5 group-hover:text-cyan-500/10 transition-all transform -rotate-12"></i>
                        
                        <div class="flex justify-between items-start flex-wrap gap-2 mb-2 relative z-10">
                            <h3 class="font-bold text-white text-lg">Pramuniaga & Pelayanan Pelanggan</h3>
                            <span class="text-xs font-semibold bg-cyan-500/20 text-cyan-200 px-3 py-1 rounded-full border border-cyan-500/40">2024 - 2025</span>
                        </div>
                        <p class="text-sm font-medium text-cyan-300 mb-4 relative z-10">An-Nasya Fried Chicken</p>
                        
                        <ul class="list-none space-y-2 text-sm text-gray-300 relative z-10 pl-2">
                            <li class="flex items-start gap-3">
                                <i class="fas fa-circle text-[8px] text-cyan-500 mt-1.5"></i>
                                <span>Melayani kebutuhan pelanggan dengan ramah dan sopan, serta menjelaskan produk yang tersedia.</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fas fa-circle text-[8px] text-cyan-500 mt-1.5"></i>
                                <span>Mengurus transaksi pembayaran dan perhitungan keuangan harian dengan teliti.</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fas fa-circle text-[8px] text-cyan-500 mt-1.5"></i>
                                <span>Memeriksa dan menyusun stok barang agar tetap rapi dan tercatat dengan benar.</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fas fa-circle text-[8px] text-cyan-500 mt-1.5"></i>
                                <span>Membuat catatan laporan penjualan harian secara sederhana dan teratur.</span>
                            </li>
                        </ul>
                    </div>
                </section>

                <section class="glass-card p-6 md:p-8">
                    <h2 class="text-xl font-semibold text-cyan-300 mb-4 flex items-center gap-2 border-b border-white/10 pb-2">
                        <i class="fas fa-certificate"></i> Sertifikasi
                    </h2>
                    
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                        
                        <!-- Sertifikat 1 -->
                        <div class="bg-gradient-to-br from-white/10 to-transparent border border-cyan-500/30 p-5 rounded-lg hover:border-cyan-400 transition-colors shadow-lg flex flex-col justify-between h-full">
                            <div>
                                <div class="flex items-start justify-between mb-3">
                                    <i class="fab fa-microsoft text-3xl text-cyan-400"></i>
                                    <span class="text-[10px] font-bold bg-cyan-900/70 text-cyan-100 px-2.5 py-1 rounded border border-cyan-500/50">Jan 2025</span>
                                </div>
                                <h3 class="font-bold text-white text-base mb-1">Berkolaborasi dengan Microsoft 365</h3>
                                <p class="text-xs font-semibold text-cyan-200 mb-2">Penyelenggara: Cakap</p>
                                <p class="text-xs text-gray-300 mb-4 leading-relaxed">Menguasai penggunaan Microsoft 365 untuk kerja kolaborasi dan produktivitas.</p>
                            </div>
                            <a href="https://upskill.cakap.com/sertifikat-saya/J2EA41ED6B" target="_blank" class="inline-flex items-center gap-1.5 text-xs font-semibold text-cyan-300 hover:text-white transition-colors hover:underline bg-white/5 w-fit px-3 py-1.5 rounded">
                                <i class="fas fa-link"></i> Lihat Sertifikat
                            </a>
                        </div>

                        <!-- Sertifikat 2 -->
                        <div class="bg-gradient-to-br from-white/10 to-transparent border border-white/10 p-5 rounded-lg hover:border-blue-400 transition-colors shadow-lg flex flex-col justify-between h-full">
                            <div>
                                <div class="flex items-start justify-between mb-3">
                                    <i class="fas fa-brain text-3xl text-blue-400"></i>
                                    <span class="text-[10px] font-bold bg-blue-900/70 text-blue-100 px-2.5 py-1 rounded border border-blue-500/50">Des 2025</span>
                                </div>
                                <h3 class="font-bold text-white text-base mb-1">Belajar Dasar AI</h3>
                                <p class="text-xs font-semibold text-blue-200 mb-2">Penyelenggara: Dicoding Indonesia</p>
                                <p class="text-xs text-gray-300 leading-relaxed">Mempelajari fundamental kecerdasan buatan dan penerapannya.</p>
                            </div>
                            <p class="text-[10px] text-gray-400 mt-4"><i class="fas fa-clock"></i> Berlaku hingga: Desember 2028</p>
                        </div>

                    </div>
                </section>
                
                <section class="glass-card p-6 md:p-8 flex flex-col sm:flex-row items-center justify-between gap-4 bg-gradient-to-r from-cyan-900/50 to-blue-900/50 border-cyan-500/30">
                    <div class="text-center sm:text-left">
                        <h3 class="text-lg font-bold text-white">Unduh Curriculum Vitae</h3>
                        <p class="text-sm text-cyan-100/80">Simpan salinan profil lengkap saya dalam format PDF.</p>
                    </div>
                    <a href="CV_Neolene Putri Kusuma Wardhani_2.pdf" download class="shrink-0 px-6 py-3 bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-400 hover:to-blue-400 text-white font-semibold rounded-full shadow-[0_0_15px_rgba(6,182,212,0.6)] transition-all hover:scale-105 flex items-center gap-2 border border-cyan-200/50">
                        <i class="fas fa-file-pdf"></i> Download CV
                    </a>
                </section>

            </div>
        </div>
        
        <footer class="mt-12 text-center text-sm text-cyan-200/60 pb-8">
            <p>&copy; 2026 Neolene Putri Kusuma Wardhani. <br class="md:hidden">Didesain dengan Tema Bawah Laut 🌊 🧽</p>
        </footer>

    </main>

    <script>
        // Logika HTML Canvas untuk Animasi Gelembung yang lebih halus
        const canvas = document.getElementById('bubbleCanvas');
        const ctx = canvas.getContext('2d');
        
        let bubblesArray = [];

        // Mengatur ukuran canvas agar sesuai dengan layar
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        // Kelas Bubble
        class Bubble {
            constructor() {
                this.x = Math.random() * canvas.width;
                // Mulai dari bawah layar
                this.y = canvas.height + Math.random() * 300; 
                this.radius = Math.random() * 10 + 2; // Ukuran bervariasi
                this.speedY = Math.random() * 1.5 + 0.5; // Kecepatan naik
                this.speedX = (Math.random() - 0.5) * 0.5; // Goyangan ke kiri/kanan
                // Transparansi putih
                this.opacity = Math.random() * 0.3 + 0.1; 
            }

            update() {
                this.y -= this.speedY; // Bergerak ke atas
                this.x += this.speedX; // Bergerak ke samping sedikit
                
                // Jika gelembung keluar layar atas, reset posisinya ke bawah
                if (this.y < -this.radius) {
                    this.y = canvas.height + this.radius;
                    this.x = Math.random() * canvas.width;
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.strokeStyle = `rgba(255, 255, 255, ${this.opacity})`;
                ctx.fillStyle = `rgba(255, 255, 255, ${this.opacity * 0.5})`;
                ctx.lineWidth = 1;
                ctx.stroke();
                ctx.fill();
                ctx.closePath();
                
                // Efek pantulan cahaya di gelembung (highlight)
                ctx.beginPath();
                ctx.arc(this.x - this.radius * 0.3, this.y - this.radius * 0.3, this.radius * 0.2, 0, Math.PI * 2);
                ctx.fillStyle = `rgba(255, 255, 255, ${this.opacity + 0.2})`;
                ctx.fill();
                ctx.closePath();
            }
        }

        // Inisialisasi banyak gelembung
        function initBubbles() {
            bubblesArray = [];
            let numberOfBubbles = Math.floor(window.innerWidth / 15); // Jumlah menyesuaikan lebar layar
            
            // Batasi maksimal gelembung agar tidak berat
            if(numberOfBubbles > 100) numberOfBubbles = 100;

            for (let i = 0; i < numberOfBubbles; i++) {
                bubblesArray.push(new Bubble());
            }
        }

        // Loop Animasi
        function animateBubbles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height); // Bersihkan canvas
            
            for (let i = 0; i < bubblesArray.length; i++) {
                bubblesArray[i].update();
                bubblesArray[i].draw();
            }
            
            requestAnimationFrame(animateBubbles);
        }

        // Jalankan saat load
        window.addEventListener('load', () => {
            initBubbles();
            animateBubbles();
        });
    </script>
</body>
</html>
