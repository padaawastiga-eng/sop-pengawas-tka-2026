

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SOP TKA 2026</title>
    <link rel="icon" type="image/png" href="https://i.imgur.com/LR4PSa2.png">
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#f0fdfa',
                            100: '#ccfbf1',
                            500: '#14b8a6',
                            700: '#0f766e',
                            900: '#134e4a',
                        },
                        accent: {
                            500: '#f59e0b',
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        body {
            background-color: #f8fafc;
            color: #334155;
            -webkit-font-smoothing: antialiased;
        }
        
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 500px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }

        .fade-in {
            animation: fadeIn 0.4s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .tab-btn.active {
            border-bottom: 2px solid #0f766e;
            color: #0f766e;
            font-weight: 600;
            background-color: #f0fdfa;
        }

        .card-hover {
            transition: all 0.2s ease;
        }
        .card-hover:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }

        .task-detail {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out;
        }
        
        .task-detail.open {
            max-height: 500px; 
        }

        .unicode-icon {
            font-size: 1.5rem;
            line-height: 1;
        }
    </style>
</head>
<body class="flex flex-col min-h-screen">

<!-- Chosen Palette: Warm Neutrals with Teal (Brand) and Amber (Accent) highlights -->
<!-- Application Structure Plan: The application uses a dashboard-style layout with a top navigation bar to switch between three main views: 'Beranda' (Overview), 'Penyelia' (Supervisor), and 'Pengawas' (Invigilator). This structure was chosen to logically separate the roles defined in the Kepmen No 95 Tahun 2025, preventing information overload. The Overview provides a synthesized look at the distribution of tasks using a chart. The role-specific sections use interactive accordion cards to group chronological tasks, allowing users to drill down into specific SOPs (Standard Operating Procedures) without scrolling through a massive wall of text. -->
<!-- Visualization & Content Choices: 
1. Overview -> Goal: Inform -> Doughnut Chart (Chart.js) -> Hover/Tooltip interactions -> Justification: Synthesizes the textual rules into quantifiable task burdens per phase, providing an immediate understanding of where efforts are concentrated. 
2. Role Tasks -> Goal: Organize & Inform -> Accordion Task Cards (HTML/CSS/JS) -> Click to expand/collapse -> Justification: Breaks down the dense bullet points from the source report into chronological, digestible chunks. NO SVG/Mermaid used; Unicode characters provide visual cues. 
-->
<!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <header class="bg-white shadow-sm sticky top-0 z-10 border-b border-slate-200">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center gap-3">
                    <span class="unicode-icon bg-brand-100 text-brand-700 p-2 rounded-lg">🎓</span>
                    <div>
                        <h1 class="text-xl font-bold text-slate-900 leading-tight">SOP TKA 2026</h1>
                        <p class="text-xs text-slate-500">Kepmen Nomor 95 Tahun 2025</p>
                    </div>
                </div>
                <nav class="hidden md:flex space-x-2" id="main-nav">
                    <button data-target="view-overview" class="tab-btn active px-4 py-2 text-sm font-medium text-slate-600 hover:text-brand-700 rounded-t-lg transition-colors">Beranda</button>
                    <button data-target="view-penyelia" class="tab-btn px-4 py-2 text-sm font-medium text-slate-600 hover:text-brand-700 rounded-t-lg transition-colors">Tugas Penyelia</button>
                    <button data-target="view-pengawas" class="tab-btn px-4 py-2 text-sm font-medium text-slate-600 hover:text-brand-700 rounded-t-lg transition-colors">Tugas Pengawas</button>
                </nav>
                <div class="md:hidden flex items-center">
                    <select id="mobile-nav" class="bg-slate-50 border border-slate-300 text-slate-900 text-sm rounded-lg focus:ring-brand-500 focus:border-brand-500 block w-full p-2.5">
                        <option value="view-overview">Beranda</option>
                        <option value="view-penyelia">Tugas Penyelia</option>
                        <option value="view-pengawas">Tugas Pengawas</option>
                        <option href="https://docs.google.com/document/d/11VPfozyZRTJcCSyLip2DyBu4YvjZAdJQ/edit?usp=sharing&ouid=112540134917197083995&rtpof=true&sd=true" target="blank">SK Pengawas</option>
                        <option href="https://docs.google.com/document/d/1B7S4nnuXAc2vF6tbL74GPvUke3oKogRU/edit?usp=sharing&ouid=112540134917197083995&rtpof=true&sd=true" target="blank">ST Pengawas</option>
                    </select>
                </div>
            </div>
        </div>
    </header>

    <main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full">
        
        <section id="view-overview" class="view-section fade-in block">
            <div class="mb-8 max-w-7xl">
                <h2 class="text-3xl font-bold text-slate-900 mb-4">Panduan Pelaksanaan TKA 2026</h2>
                <p class="text-lg text-slate-600 leading-relaxed">
                    Aplikasi interaktif ini merangkum Standar Operasional Prosedur (SOP) tugas dan tanggung jawab bagi Penyelia dan Pengawas Ruang dalam pelaksanaan Tes Kemampuan Akademik (TKA) 2025. Eksplorasi pembagian tugas di bawah ini untuk memahami alur kerja, pengawasan konferensi video (Zoom), dan protokol integritas ujian.<br>
                    Juknis Pelaksanaan TKA <a href="https://drive.google.com/file/d/1-98hSaTyduEKe0YyBBGvG85lDFyY_D4r/view?usp=sharing"target="blank"><i style="color: green;"><b>Lihat.</b> </i></a><br>
                    Administrasi TKA, Unduh <a href="https://drive.google.com/file/d/1qcGZYTW8wz8sV_nz4Ech_lej2mfeqEvt/view?usp=sharing"target="blank"><i style="color: red;"><b>di sini.</b> </i></a>
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
                <div class="bg-white p-6 rounded-xl border border-slate-200 shadow-sm">
                    <h3 class="text-xl font-semibold text-slate-800 mb-2 border-b pb-2">Distribusi Beban Tugas Berdasarkan Fase</h3>
                    <p class="text-sm text-slate-500 mb-6">Visualisasi ini mensintesis jumlah instruksi/aturan yang harus dijalankan pada setiap fase ujian, memberikan gambaran fokus operasional.</p>
                    
                    <div class="chart-container">
                        <canvas id="taskDistributionChart"></canvas>
                    </div>
                </div>

                <div class="flex flex-col gap-4">
                    <div class="bg-brand-50 p-6 rounded-xl border border-brand-100">
                        <div class="flex items-center gap-3 mb-3">
                            <span class="unicode-icon">👨‍💼</span>
                            <h3 class="text-lg font-semibold text-brand-900">Peran Utama: Penyelia</h3>
                        </div>
                        <p class="text-brand-700 text-sm mb-4">Penyelia bertindak sebagai manajer ruang virtual, mengendalikan pengaturan Zoom, memverifikasi pengawas, dan memastikan integritas ujian dari sisi sistem dan administrasi makro.</p>
                        <button class="nav-trigger text-sm font-semibold text-white bg-brand-600 hover:bg-brand-700 px-4 py-2 rounded-lg transition-colors w-max" data-target="view-penyelia">Eksplorasi SOP Penyelia &rarr;</button>
                    </div>

                    <div class="bg-amber-50 p-6 rounded-xl border border-amber-100">
                        <div class="flex items-center gap-3 mb-3">
                            <span class="unicode-icon">👁️</span>
                            <h3 class="text-lg font-semibold text-amber-900">Peran Utama: Pengawas Ruang</h3>
                        </div>
                        <p class="text-amber-700 text-sm mb-4">Pengawas berada di garis depan, memantau langsung peserta melalui kamera, memastikan kebersihan area ujian, dan berkomunikasi secara proaktif dengan penyelia.</p>
                        <button class="nav-trigger text-sm font-semibold text-white bg-amber-600 hover:bg-amber-700 px-4 py-2 rounded-lg transition-colors w-max" data-target="view-pengawas">Eksplorasi SOP Pengawas &rarr;</button>
                    </div>
                    
                    <div class="bg-slate-800 p-6 rounded-xl text-white mt-2">
                        <h3 class="font-semibold mb-2">Aturan Emas Integritas Ujian:</h3>
                        <ul class="list-disc pl-5 text-sm text-slate-300 space-y-1">
                            <li>Dilarang keras merekam, memfoto, atau menyebarkan soal ujian.</li>
                            <li>Kamera wajib selalu aktif menampilkan kondisi aktual.</li>
                            <li>Peserta terlambat lebih dari 15 menit dilarang mengikuti tes.</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <section id="view-penyelia" class="view-section hidden fade-in">
            <div class="mb-8 border-b border-slate-200 pb-6">
                <div class="flex items-center gap-3 mb-2">
                    <span class="text-3xl">👨‍💼</span>
                    <h2 class="text-3xl font-bold text-slate-900">Tugas Penyelia</h2>
                </div>
                <p class="text-slate-600 text-lg max-w-7xl">
                    Bagian ini menguraikan tugas krusial Penyelia dalam mengelola konferensi video (Zoom) dan memantau jalannya ujian secara makro. Klik pada setiap fase di bawah ini untuk melihat rincian instruksi operasional.
                </p>
            </div>

            <div class="space-y-4" id="penyelia-accordion">
            </div>
        </section>

        <section id="view-pengawas" class="view-section hidden fade-in">
            <div class="mb-8 border-b border-slate-200 pb-6">
                <div class="flex items-center gap-3 mb-2">
                    <span class="text-3xl">👁️</span>
                    <h2 class="text-3xl font-bold text-slate-900">Tugas Pengawas Ruang</h2>
                </div>
                <p class="text-slate-600 text-lg max-w-7xl">
                    Bagian ini merangkum persiapan perangkat keras dan pengawasan langsung yang harus dilakukan oleh Pengawas Ruang di satuan pendidikan. Klik pada setiap kategori untuk memahami pedoman teknis dan pelaporan. Jika pengawas membutuhkan :<br>
                    <small>
                    1.  <b>Juknis Pengawas TKA</b> lihat <a href="https://drive.google.com/file/d/1vpiuPs65_6-0RIh1ZvSCO8zXhW8QSDlC/view?usp=sharing"target="blank"><i style="color: blue;">di sini</i></a>. <br>    
                    2.  <b>SK Pengawas</b> diunduh <a href="https://docs.google.com/document/d/11VPfozyZRTJcCSyLip2DyBu4YvjZAdJQ/edit?usp=sharing&ouid=112540134917197083995&rtpof=true&sd=true"target="blank"><i style="color: blue;">di sini</i></a>. <br>
                    3. <b>Surat Tugas Pengawas</b> di unduh <a href="https://docs.google.com/document/d/1B7S4nnuXAc2vF6tbL74GPvUke3oKogRU/edit?usp=sharing&ouid=112540134917197083995&rtpof=true&sd=true"target="blank"><i style="color: blue">di sini.</i></a><br>
                    4. <b>Template ID_Card pengawas</b> diunduh <a href="https://docs.google.com/document/d/1Q2_7cz9_9HhkblKlI2sHBu-DkgSdsQlr/edit?usp=sharing&ouid=112540134917197083995&rtpof=true&sd=true"target="blank"><i style="color: blue">di sini.</i></a><br>
                    5. <b>Link Login TKA -> <a href="https://tka.kemendikdasmen.go.id/"target="blank"><i style="color: red">Klik di sini</i></a></b></small>

                </p>
            </div>

            <div class="space-y-4" id="pengawas-accordion">
            </div>
        </section>

    </main>

    <footer class="bg-slate-900 text-slate-400 py-6 text-center text-sm">
        <p class="mb-2">Berdasarkan Kepmen Nomor 95 Tahun 2025 &mdash; Panduan Pelaksanaan TKA Interaktif</p>
        <p>@2026 Pengawas Sekolah Dasar Kecamatan Pasirwangi | Agus Supriatna, S.Pd - Web Developer Asep Akon, S.Pd</p>
    </footer>

    <script>
        const contentData = {
            penyelia: [
                {
                    id: 'p1',
                    title: 'Persiapan Konferensi Video (Zoom)',
                    icon: '💻',
                    colorClass: 'border-blue-200 bg-blue-50 text-blue-800',
                    items: [
                        'Masuk ke Zoom menggunakan akun resmi dari tim teknis provinsi pada laman TKA.',
                        'Aktifkan Zoom sesuai jadwal.',
                        '<strong>Wajib:</strong> Nonaktifkan "rekaman cloud" dan aktifkan "rekam ke file komputer" (lokal).',
                        '<strong>Kunci Fitur:</strong> Nonaktifkan audio, share screen, dll tanpa izin host. Hanya fitur mulai video yang diaktifkan.'
                    ]
                },
                {
                    id: 'p2',
                    title: 'Koordinasi Pengawas Ruang',
                    icon: '👥',
                    colorClass: 'border-indigo-200 bg-indigo-50 text-indigo-800',
                    items: [
                        'Pastikan pendamping penyelia & pengawas ruang sudah masuk Zoom.',
                        'Arahkan pengawas untuk mengganti nama (rename) Zoom sesuai format.',
                        'Verifikasi pengawas ruang agar sesuai dengan daftar di laman TKA.',
                        'Keluarkan pengawas yang tidak terdaftar (setelah berkoordinasi dengan pendamping penyelia).',
                        'Rekam Zoom selama TKA berlangsung.'
                    ]
                },
                {
                    id: 'p3',
                    title: 'Pengawasan Sebelum Tes (Hari H)',
                    icon: '⏱️',
                    colorClass: 'border-amber-200 bg-amber-50 text-amber-800',
                    items: [
                        'Peserta wajib masuk ruangan 15 menit sebelum TKA dimulai.',
                        '<strong>Toleransi:</strong> Terlambat maksimal 15 menit setelah tes dimulai (lebih dari itu tidak dapat mengikuti tes).',
                        'Verifikasi wajah peserta dengan foto pada kartu peserta/kartu login.',
                        'Membacakan tata tertib pelaksanaan tes TKA.'
                    ]
                },
                {
                    id: 'p4',
                    title: 'Pemantauan Suasana Ruangan (Hari H)',
                    icon: '🚫',
                    colorClass: 'border-rose-200 bg-rose-50 text-rose-800',
                    items: [
                        'Jaga ketertiban ruang TKA: dilarang merokok, ngobrol, bawa HP/kamera, dan bawa bahan bacaan.',
                        'Beri peringatan dan sanksi kepada peserta yang curang.',
                        'Larang orang yang tidak berwenang masuk ruang TKA.',
                        'Pantau tempat pengumpulan perangkat elektronik (HP, kamera, kalkulator) milik peserta.'
                    ]
                },
                {
                    id: 'p5',
                    title: 'Integritas & Kerahasiaan Ujian',
                    icon: '🔒',
                    colorClass: 'border-purple-200 bg-purple-50 text-purple-800',
                    items: [
                        'Jangan memberi isyarat/bantuan apapun terkait jawaban.',
                        'Jaga kerahasiaan tes.',
                        '<strong>Dilarang keras:</strong> merekam, memfoto, serta menyebarkan soal ujian.',
                        'Melakukan verifikasi identitas pengawas ruang di satuan pendidikan.',
                        'Berkoordinasi terkait aktivitas kamera pada aplikasi Zoom.'
                    ]
                },
                {
                    id: 'p6',
                    title: 'Administrasi & Pelaporan Akhir',
                    icon: '📋',
                    colorClass: 'border-emerald-200 bg-emerald-50 text-emerald-800',
                    items: [
                        'Pastikan meja peserta bersih (hanya ada kertas buram & 1 alat tulis).',
                        'Pastikan kertas buram dikumpulkan kembali (tidak boleh dibawa keluar).',
                        'Screenshot Zoom jika terjadi pelanggaran dan unggah ke laman TKA.',
                        'Pindahkan rekaman Zoom ke penyimpanan eksternal.',
                        'Login ke laman TKA, buat catatan masalah (jika ada), dan ceklis berita acara.'
                    ]
                }
            ],
            pengawas: [
                {
                    id: 'w1',
                    title: 'Persiapan Perangkat & Ruangan (H-30 Menit)',
                    icon: '📷',
                    colorClass: 'border-blue-200 bg-blue-50 text-blue-800',
                    items: [
                        'Serahkan SK dan Surat Tugas Pengawas kepada Panitia TKA Sekolah tempat tugas mengawas.',
                        'Pengawas memakai ID_Card pengawas untuk menunjukan identitas kepada penyelia.',
                        'Pastikan pengawas sudah memiliki Kartu Pengawas yang di dapatkan dari Opeator sekolah.',
                        'Pastikan pengawas membawa alat/gadget (HP, Ipad, Laptop) untuk login dan masuk zoom penyelia.',
                        'Login TKA di halaman https://tka.kemendikdasmen.go.id/ <strong>menggunakan akun yang tertera di dalam Kartu Pengawas</strong> & klik link Zoom melalui tautan resmi sesuai jadwal.',
                        '<strong>Dilarang</strong> menggunakan <em>virtual background</em> atau fitur <em>blur</em>.',
                        'Sesuaikan nama di Zoom dengan format.',
                        'Siapkan tripod & letakkan gawai di sudut ruangan (pastikan semua peserta terlihat).',
                        'Jangan arahkan kamera ke layar komputer peserta.',
                        'Siapkan kartu pengawas & identitas untuk verifikasi oleh penyelia.'
                    ]
                },
                {
                    id: 'w2',
                    title: 'Aturan Komunikasi & Kamera',
                    icon: '🎧',
                    colorClass: 'border-amber-200 bg-amber-50 text-amber-800',
                    items: [
                        'Gunakan headset/earphone bermikrofon saat berkomunikasi dengan penyelia.',
                        'Kamera wajib <strong>selalu aktif</strong> menampilkan kondisi ruangan selama tes berlangsung.',
                        'Akomodir permintaan penyelia terkait penyesuaian arah/sudut kamera Zoom.'
                    ]
                },
                {
                    id: 'w3',
                    title: 'Pelaksanaan & Pelaporan Pengawas',
                    icon: '📝',
                    colorClass: 'border-emerald-200 bg-emerald-50 text-emerald-800',
                    items: [
                        'Pastikan meja peserta bersih (hanya 1 alat tulis & kertas buram).',
                        'Kumpulkan kembali kertas buram, laporkan ke penyelia bahwa tidak ada yang dibawa keluar.',
                        'Laporkan jumlah peserta yang hadir kepada penyelia.',
                        'Laksanakan tugas sesuai deskripsi BAB VI Kepmen Nomor 95 Tahun 2025.',
                        'Buat berita acara pengawasan Zoom pada laman TKA.'
                    ]
                }
            ]
        };

        function renderAccordionContent(containerId, dataArray) {
            const container = document.getElementById(containerId);
            container.innerHTML = ''; 

            dataArray.forEach(section => {
                const card = document.createElement('div');
                card.className = 'bg-white border border-slate-200 rounded-xl overflow-hidden card-hover';
                
                const header = document.createElement('button');
                header.className = `w-full px-6 py-4 flex items-center justify-between text-left focus:outline-none focus:bg-slate-50 transition-colors border-l-4 ${section.colorClass.split(' ')[0]}`;
                header.onclick = () => toggleAccordion(section.id);
                
                header.innerHTML = `
                    <div class="flex items-center gap-3">
                        <span class="unicode-icon">${section.icon}</span>
                        <span class="font-semibold text-slate-800 text-lg">${section.title}</span>
                    </div>
                    <span class="unicode-icon text-slate-400 transition-transform duration-300" id="icon-${section.id}">&#9662;</span>
                `;

                const contentBody = document.createElement('div');
                contentBody.id = `content-${section.id}`;
                contentBody.className = 'task-detail bg-slate-50 border-t border-slate-100';
                
                let listHtml = '<ul class="p-6 space-y-3">';
                section.items.forEach(item => {
                    listHtml += `
                        <li class="flex items-start gap-3">
                            <span class="text-brand-500 mt-1">&#10004;</span>
                            <span class="text-slate-700 leading-relaxed">${item}</span>
                        </li>
                    `;
                });
                listHtml += '</ul>';
                contentBody.innerHTML = listHtml;

                card.appendChild(header);
                card.appendChild(contentBody);
                container.appendChild(card);
            });
        }

        function toggleAccordion(id) {
            const content = document.getElementById(`content-${id}`);
            const icon = document.getElementById(`icon-${id}`);
            
            if (content.classList.contains('open')) {
                content.classList.remove('open');
                icon.style.transform = 'rotate(0deg)';
            } else {
                content.classList.add('open');
                icon.style.transform = 'rotate(180deg)';
            }
        }

        function switchView(targetId) {
            document.querySelectorAll('.view-section').forEach(el => {
                el.classList.add('hidden');
            });
            
            const targetEl = document.getElementById(targetId);
            targetEl.classList.remove('hidden');

            document.querySelectorAll('.tab-btn').forEach(btn => {
                if(btn.dataset.target === targetId) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });

            const mobileSelect = document.getElementById('mobile-nav');
            if(mobileSelect.value !== targetId) {
                mobileSelect.value = targetId;
            }
        }

        function initNavigation() {
            document.querySelectorAll('.tab-btn, .nav-trigger').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const target = e.currentTarget.dataset.target;
                    switchView(target);
                    window.scrollTo({ top: 0, behavior: 'smooth' });
                });
            });

            document.getElementById('mobile-nav').addEventListener('change', (e) => {
                switchView(e.target.value);
                window.scrollTo({ top: 0, behavior: 'smooth' });
            });
        }

        function initChart() {
            const ctx = document.getElementById('taskDistributionChart').getContext('2d');
            
            const penyeliaTaskCount = contentData.penyelia.reduce((acc, curr) => acc + curr.items.length, 0);
            const pengawasTaskCount = contentData.pengawas.reduce((acc, curr) => acc + curr.items.length, 0);

            new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Tugas Penyelia (Zoom & Makro)', 'Tugas Pengawas (Lokal & Mikro)'],
                    datasets: [{
                        data: [penyeliaTaskCount, pengawasTaskCount],
                        backgroundColor: [
                            '#0f766e', 
                            '#f59e0b'  
                        ],
                        borderWidth: 0,
                        hoverOffset: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                padding: 20,
                                font: {
                                    family: "'Inter', sans-serif",
                                    size: 13
                                }
                            }
                        },
                        tooltip: {
                            backgroundColor: 'rgba(15, 23, 42, 0.9)',
                            padding: 12,
                            titleFont: { size: 14, family: "'Inter', sans-serif" },
                            bodyFont: { size: 13, family: "'Inter', sans-serif" },
                            callbacks: {
                                label: function(context) {
                                    return ` ${context.label}: ${context.raw} Instruksi SOP`;
                                }
                            }
                        }
                    },
                    cutout: '65%'
                }
            });
        }

        document.addEventListener('DOMContentLoaded', () => {
            renderAccordionContent('penyelia-accordion', contentData.penyelia);
            renderAccordionContent('pengawas-accordion', contentData.pengawas);
            initNavigation();
            initChart();
        });

    </script>
</body>
</html>
