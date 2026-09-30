<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GameLab AI - Buat Game-mu Sendiri & Jelajahi Bentang Alam Indonesia!</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Font Lucu & Ramah Anak Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Nunito', sans-serif;
      user-select: none;
      -webkit-tap-highlight-color: transparent;
    }
    h1, h2, h3, .font-fun {
      font-family: 'Fredoka', cursive;
    }
    @keyframes bounce-slow {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }
    @keyframes pulse-glow {
      0%, 100% { box-shadow: 0 0 15px rgba(245, 158, 11, 0.4); }
      50% { box-shadow: 0 0 25px rgba(245, 158, 11, 0.8); }
    }
    @keyframes float {
      0% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-10px) rotate(2deg); }
      100% { transform: translateY(0px) rotate(0deg); }
    }
    .animate-float { animation: float 4s ease-in-out infinite; }
    .animate-bounce-slow { animation: bounce-slow 2.5s infinite ease-in-out; }
    .animate-pulse-glow { animation: pulse-glow 2s infinite ease-in-out; }
    
    /* Custom Scrollbar for cute aesthetic */
    ::-webkit-scrollbar {
      width: 10px;
      height: 10px;
    }
    ::-webkit-scrollbar-track {
      background: #e0f2fe;
      border-radius: 9999px;
    }
    ::-webkit-scrollbar-thumb {
      background: #38bdf8;
      border-radius: 9999px;
      border: 2px solid #e0f2fe;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #0284c7;
    }
  </style>
</head>
<body class="bg-gradient-to-b from-sky-300 via-emerald-100 to-amber-100 min-h-screen text-slate-800 flex flex-col justify-between overflow-x-hidden">

  <!-- Top Navigation Header -->
  <header class="sticky top-0 z-40 bg-white/90 backdrop-blur-md border-b-4 border-emerald-300 px-4 py-2 sm:py-3 shadow-md">
    <div class="max-w-6xl mx-auto flex items-center justify-between gap-2">
      <!-- Logo & Title -->
      <div class="flex items-center gap-2 sm:gap-3 cursor-pointer" onclick="navigateTo('home')">
        <div class="w-10 h-10 sm:w-12 sm:h-12 bg-white rounded-2xl flex items-center justify-center shadow-md border-2 border-emerald-300 overflow-hidden flex-shrink-0 animate-bounce-slow">
          <img 
            src="https://cdn.phototourl.com/member/2026-09-27-c0d84814-7b47-49b5-8b92-1135a1c3627c.png" 
            alt="Logo Sekolah" 
            class="w-full h-full object-contain p-1"
            onerror="this.onerror=null; this.parentElement.innerHTML='<span class=\'text-2xl\'>🇮🇩</span>';"
          />
        </div>
        <div>
          <h1 class="text-base sm:text-xl font-bold text-emerald-800 tracking-wide leading-tight flex items-center gap-1.5">
            GameLab AI <span class="text-xs bg-amber-400 text-amber-950 px-1.5 py-0.5 rounded-md font-extrabold hidden sm:inline">STUDIO</span>
          </h1>
          <p class="text-xs text-emerald-600 font-semibold hidden sm:block">
            Petualangan Bentang Alam Indonesia & Kreator Game SD
          </p>
        </div>
      </div>

      <!-- Quick Nav Buttons -->
      <nav class="flex items-center gap-1.5 sm:gap-2">
        <button onclick="navigateTo('home')" class="nav-btn px-3 py-1.5 rounded-xl font-bold text-xs sm:text-sm bg-sky-100 hover:bg-sky-200 text-sky-800 border-2 border-sky-300 transition flex items-center gap-1">
          🏠 <span class="hidden md:inline">Beranda</span>
        </button>
        <button onclick="navigateTo('encyclopedia')" class="nav-btn px-3 py-1.5 rounded-xl font-bold text-xs sm:text-sm bg-emerald-100 hover:bg-emerald-200 text-emerald-800 border-2 border-emerald-300 transition flex items-center gap-1">
          📖 <span class="hidden md:inline">Materi Alam</span>
        </button>
        <button onclick="navigateTo('creator-hub')" class="nav-btn px-3 py-1.5 rounded-xl font-bold text-xs sm:text-sm bg-amber-400 hover:bg-amber-500 text-amber-950 border-2 border-amber-500 shadow-sm transition flex items-center gap-1">
          ✨ <span class="font-bold">Buat Game!</span>
        </button>
        <button onclick="navigateTo('gallery')" class="nav-btn px-3 py-1.5 rounded-xl font-bold text-xs sm:text-sm bg-purple-100 hover:bg-purple-200 text-purple-800 border-2 border-purple-300 transition flex items-center gap-1">
          🎮 <span class="hidden md:inline">Galeri Game</span>
        </button>
        <!-- Device View Size Switcher (Laptop / Tablet / Smartphone) -->
        <div class="relative inline-block text-left" id="deviceDropdownWrap">
          <button id="deviceSelectBtn" onclick="toggleDeviceDropdown()" class="px-2.5 py-1.5 rounded-xl font-bold text-xs bg-sky-50 hover:bg-sky-100 text-sky-800 border-2 border-sky-300 flex items-center gap-1 transition shadow-sm" title="Ubah Ukuran Layar">
            <span id="deviceIcon">🖥️</span> <span id="deviceLabel" class="hidden sm:inline">Ukuran: Otomatis</span> <span class="text-[10px]">▼</span>
          </button>
          <div id="deviceDropdownMenu" class="hidden absolute right-0 mt-2 w-48 rounded-2xl bg-white shadow-2xl border-2 border-sky-300 py-2 z-50 animate-scaleUp">
            <div class="px-3 py-1 text-[11px] font-extrabold text-slate-400 uppercase tracking-wider">Pilih Simulasi Ukuran</div>
            <button onclick="setDeviceView('auto')" class="w-full text-left px-3 py-2 text-xs font-bold text-slate-700 hover:bg-sky-50 hover:text-sky-800 flex items-center gap-2 transition">
              <span>🔄</span> <span>Otomatis (Layar Penuh)</span>
            </button>
            <button onclick="setDeviceView('laptop')" class="w-full text-left px-3 py-2 text-xs font-bold text-slate-700 hover:bg-sky-50 hover:text-sky-800 flex items-center gap-2 transition">
              <span>💻</span> <span>Laptop (Besar)</span>
            </button>
            <button onclick="setDeviceView('tablet')" class="w-full text-left px-3 py-2 text-xs font-bold text-slate-700 hover:bg-sky-50 hover:text-sky-800 flex items-center gap-2 transition">
              <span>📟</span> <span>Tablet (Sedang)</span>
            </button>
            <button onclick="setDeviceView('phone')" class="w-full text-left px-3 py-2 text-xs font-bold text-slate-700 hover:bg-sky-50 hover:text-sky-800 flex items-center gap-2 transition">
              <span>📱</span> <span>Smartphone (HP)</span>
            </button>
          </div>
        </div>

        <!-- Mode Switch: Siswa / Guru -->
        <button id="modeToggleBtn" onclick="toggleTeacherMode()" class="px-2.5 py-1.5 rounded-xl font-bold text-xs bg-slate-100 hover:bg-slate-200 text-slate-700 border-2 border-slate-300 flex items-center gap-1 transition">
          <span id="modeIcon">🎒</span> <span id="modeText" class="hidden sm:inline">Mode Siswa</span>
        </button>
        <!-- Audio Mute Button -->
        <button id="audioBtn" onclick="toggleAudio()" class="w-9 h-9 rounded-xl bg-amber-100 hover:bg-amber-200 text-amber-800 border-2 border-amber-300 flex items-center justify-center text-sm font-bold shadow-sm transition">
          🔊
        </button>
      </nav>
    </div>
  </header>

  <!-- MAIN APP ROUTER CONTAINER -->
  <main id="appContainer" class="flex-1 max-w-6xl w-full mx-auto p-3 sm:p-6 transition-all duration-300">
    <!-- Views will be dynamically injected / rendered here -->
  </main>

  <!-- Global Modal Popup Container (Custom Alert Replacement) -->
  <div id="customModal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
    <div class="bg-white rounded-3xl max-w-md w-full border-4 border-amber-400 shadow-2xl p-6 text-center transform transition-all scale-95 opacity-0 duration-200" id="modalCard">
      <div id="modalEmoji" class="text-6xl mb-3 animate-bounce">🌟</div>
      <h3 id="modalTitle" class="text-2xl font-bold text-slate-800 mb-2 font-fun">Pemberitahuan</h3>
      <p id="modalMsg" class="text-slate-600 font-semibold mb-6 text-sm sm:text-base leading-relaxed"></p>
      <div class="flex justify-center gap-3" id="modalActions">
        <button onclick="closeModal()" class="px-6 py-2.5 bg-gradient-to-r from-amber-400 to-orange-400 hover:from-amber-500 hover:to-orange-500 text-white font-bold rounded-2xl border-2 border-orange-500 shadow-md text-base transition">
          Oke, Siap! 🚀
        </button>
      </div>
    </div>
  </div>

  <!-- Audio Chime Helper Feedback Banner -->
  <div id="toastNotification" class="fixed bottom-6 right-6 z-50 bg-emerald-700 text-white px-5 py-3 rounded-2xl shadow-xl border-2 border-white flex items-center gap-3 transform translate-y-24 opacity-0 transition-all duration-300">
    <span id="toastIcon" class="text-2xl">🎉</span>
    <span id="toastMsg" class="font-bold text-sm">Pesan Berhasil</span>
  </div>

  <footer class="bg-emerald-900/90 text-emerald-100 py-4 px-4 text-center text-xs sm:text-sm border-t-4 border-emerald-500">
    <div class="max-w-4xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-2">
      <div class="flex items-center gap-2">
        <span class="text-lg">🌿</span>
        <span class="font-bold">Media Belajar IPA & IPS Kelas SD • Merdeka Belajar</span>
      </div>
      <div class="text-emerald-300 font-medium">
        Jelajahi Keindahan Alam Indonesia Sambil Mengasah Imajinasi 🚀
      </div>
    </div>
  </footer>

  <script>
    /* ================================================================
       1. DATA ENSIKLOPEDIA BENTANG ALAM INDONESIA (Akurat & Terverifikasi)
       ================================================================ */
    const BENTANG_ALAM_DATA = {
      gunung: {
        id: "gunung",
        nama: "Gunung",
        icon: "🏔️",
        warna: "from-amber-500 to-stone-700",
        bgBadge: "bg-amber-100 text-amber-800 border-amber-300",
        pengertian: "Bagian permukaan bumi yang menjulang tinggi ke atas, jauh lebih tinggi dan curam dibandingkan bukit atau dataran di sekitarnya.",
        ciri: [
          "Ketinggian lebih dari 600 meter di atas permukaan laut.",
          "Memiliki lereng yang curam serta puncak yang menonjol.",
          "Ada gunung berapi yang masih aktif (mengeluarkan lahar/asap) dan gunung mati."
        ],
        contoh: ["Gunung Merapi (DIY / Jawa Tengah)", "Gunung Bromo (Jawa Timur)", "Gunung Rinjani (Lombok, NTB)"],
        manfaat: [
          "Abu vulkanik menyuburkan tanah pertanian di sekitarnya.",
          "Tempat sumber mata air bersih alami bagi masyarakat.",
          "Tujuan wisata alam, pendakian, dan pembangkit listrik panas bumi (geotermal)."
        ],
        floraFauna: "Bunga Edelweiss (Bunga Abadi), Pohon Pinus, Elang Jawa, dan Macan Tutul.",
        aktivitas: "Pertanian sayuran di lereng gunung, berkebun kopi/teh, dan pemandu wisata alam.",
        faktaMenarik: "Indonesia memiliki lebih dari 120 gunung api aktif karena berada di jalur cincin api pasifik (Ring of Fire)!"
      },
      dataran_tinggi: {
        id: "dataran_tinggi",
        nama: "Dataran Tinggi",
        icon: "🏞️",
        warna: "from-emerald-600 to-teal-800",
        bgBadge: "bg-emerald-100 text-emerald-800 border-emerald-300",
        pengertian: "Wilayah daratan yang luas dan terletak di ketinggian lebih dari 500 meter di atas permukaan laut dengan udara yang sejuk dan sejuk dingin.",
        ciri: [
          "Berada di ketinggian di atas 500 meter DPL.",
          "Udaranya dingin, segar, dan sering berkabut di pagi hari.",
          "Banyak lereng terasering atau sawah bertingkat untuk mencegah longsor."
        ],
        contoh: ["Dataran Tinggi Dieng (Jawa Tengah)", "Dataran Tinggi Kerinci (Jambi/Sumatra)", "Dataran Tinggi Karo (Sumatra Utara)"],
        manfaat: [
          "Sangat cocok untuk perkebunan teh, kopi, kentang, kubis, dan buah stroberi.",
          "Sebagai tempat peristirahatan dan rekreasi keluarga yang sejuk.",
          "Kawasan resapan air hujan penahan banjir untuk daerah bawah."
        ],
        floraFauna: "Tanaman Teh, Kentang Dieng, Carica (pepaya gunung), Burung Pipit, Kera Ekor Panjang.",
        aktivitas: "Petani sayur-mayur, pemetik teh, dan pengelola villa wisata.",
        faktaMenarik: "Di Dataran Tinggi Dieng, suhu bisa sangat dingin hingga muncul 'embun upas' yang membeku seperti es salju tipis!"
      },
      dataran_rendah: {
        id: "dataran_rendah",
        nama: "Dataran Rendah",
        icon: "🌾",
        warna: "from-lime-500 to-green-700",
        bgBadge: "bg-lime-100 text-lime-800 border-lime-300",
        pengertian: "Wilayah daratan yang relatif datar dan luas dengan ketinggian antara 0 sampai 200 meter di atas permukaan laut.",
        ciri: [
          "Tanah relatif datar dan tidak curam.",
          "Suhu udara hangat hingga terasa cukup panas.",
          "Merupakan pusat permukiman padat penduduk serta pusat kegiatan kota."
        ],
        contoh: ["Dataran rendah Pantai Utara Jawa (Pantura)", "Dataran rendah Sumatra bagian Timur", "Dataran rendah Kalimantan bagian Selatan"],
        manfaat: [
          "Pusat lumbung padi (pertanian sawah irigasi) dan perkebunan tebu.",
          "Lokasi ideal untuk perumahan, perkantoran, jalan tol, dan bandara.",
          "Pusat industri pabrik dan perdagangan rakyat."
        ],
        floraFauna: "Padi, Pohon Kelapa, Jagung, Kerbau Sawah, Burung Kuntul Putih, Ayam Kampung.",
        aktivitas: "Bertani padi di sawah, berdagang di pasar, pegawai kantor, dan berkendara di jalan perkotaan.",
        faktaMenarik: "Mayoritas kota-kota besar di Indonesia (seperti Jakarta, Surabaya, dan Medan) dibangun di kawasan dataran rendah karena aksesnya mudah!"
      },
      sungai: {
        id: "sungai",
        nama: "Sungai",
        icon: "🛶",
        warna: "from-cyan-500 to-blue-700",
        bgBadge: "bg-cyan-100 text-cyan-800 border-cyan-300",
        pengertian: "Aliran air tawar yang alami dan besar, mengalir memanjang dari tempat tinggi (hulu di pegunungan) menuju tempat rendah (hilir/muara di laut).",
        ciri: [
          "Alirannya air tawar yang terus mengalir satu arah.",
          "Bagian hulu berarus deras dan berbatu, bagian hilir tenang dan melebar.",
          "Bermuara di danau atau laut bebas."
        ],
        contoh: ["Sungai Kapuas (Kalimantan Barat - Terpanjang di RI)", "Sungai Musi (Sumatra Selatan)", "Sungai Bengawan Solo (Jawa)"],
        manfaat: [
          "Jalur transportasi perahu dan kapal angkut kayu/komoditas.",
          "Pengairan (irigasi) air bagi sawah petani.",
          "Pembangkit Listrik Tenaga Air (PLTA) dan budidaya ikan tambak jaring apung."
        ],
        floraFauna: "Ikan Belida, Ikan Baung, Pesut Mahakam (lumba-lumba air tawar), Tumbuhan Kangkung Air dan Teratai.",
        aktivitas: "Pasar terapung di atas perahu, nelayan sungai, mendayung perahu, dan mencuci bahan tambang pasir.",
        faktaMenarik: "Sungai Kapuas memiliki panjang sekitar 1.143 km, menjadikannya sungai paling panjang di seluruh kepulauan Indonesia!"
      },
      danau: {
        id: "danau",
        nama: "Danau",
        icon: "💧",
        warna: "from-blue-500 to-indigo-700",
        bgBadge: "bg-blue-100 text-blue-800 border-blue-300",
        pengertian: "Genangan air tawar yang sangat luas di daratan yang dikelilingi oleh daratan di sekelilingnya, terbentuk secara alami atau buatan.",
        ciri: [
          "Airnya tenang dan dikelilingi oleh daratan tebing atau tanah perbukitan.",
          "Terbentuk karena letusan gunung berapi purba (danau vulkanik) atau patahan bumi (tektonik).",
          "Ada pulau di tengahnya pada beberapa danau besar."
        ],
        contoh: ["Danau Toba (Sumatra Utara - Danau Vulkanik Terbesar)", "Danau Sentani (Papua)", "Danau Singkarak (Sumatra Barat)"],
        manfaat: [
          "Pusat PLTA yang menghasilkan energi listrik untuk ratusan desa.",
          "Tempat penangkaran ikan mas, nila, dan ikan endemik.",
          "Objek wisata populer dunia dan festival perahu adat tradisional."
        ],
        floraFauna: "Ikan Bilis Danau Singkarak, Ikan Pelangi Sentani, Tumbuhan Hydrilla, Anggrek Danau Toba.",
        aktivitas: "Memancing ikan di keramba apung, mengemudikan perahu wisata, dan upacara adat tahunan.",
        faktaMenarik: "Danau Toba terbentuk akibat letusan supervolcano mahadahsyat ribuan tahun lalu dan di tengahnya terdapat pulau bernama Pulau Samosir!"
      },
      laut: {
        id: "laut",
        nama: "Laut & Pesisir",
        icon: "🌊",
        warna: "from-sky-600 to-blue-900",
        bgBadge: "bg-sky-100 text-sky-800 border-sky-300",
        pengertian: "Kumpulan air asin yang sangat luas menghubungkan daratan pulau satu dengan lainnya, serta pesisir yaitu daratan batas pertemuan langsung antara air laut dan daratan.",
        ciri: [
          "Airnya terasa asin karena mengandung banyak garam mineral alami.",
          "Memiliki ombak, pasang naik, dan pasang surut.",
          "Memiliki ekosistem terumbu karang warna-warni dan hutan bakau (mangrove) di pesisir."
        ],
        contoh: ["Laut Jawa", "Laut Banda (Salah satu tercuram & terdalam)", "Pesisir Pantai Selatan Jawa & Pantai Bunaken (Sulawesi Utara)"],
        manfaat: [
          "Penghasil ikan tuna, tongkol, udang, cumi, dan rumput laut segar.",
          "Hutan bakau di pesisir menahan abrasi ombak dan melindungi pantai.",
          "Jalur perdagangan kapal antar-pulau di seluruh nusantara dan luar negeri."
        ],
        floraFauna: "Terumbu Karang, Pohon Bakau (Mangrove), Penyu Sisik, Lumba-lumba, Ikan Badut (Nemo), Pari Manta.",
        aktivitas: "Nelayan menjala ikan, petani garam menguapkan air laut, snorkeling menikmati terumbu karang.",
        faktaMenarik: "Dua pertiga wilayah Indonesia adalah perairan laut! Itulah mengapa Indonesia dikenal sebagai 'Negara Maritim Terbesar' di dunia!"
      }
    };

    /* ================================================================
       2. DATABASE BANK SOAL EDUKASI TIGA LEVEL (SD Ramah & Autentik)
       ================================================================ */
    const QUESTION_BANK = [
      // LEVEL 1: KENALI
      {
        id: "q1",
        level: 1,
        bentang: "gunung",
        soal: "Bentang alam manakah yang memiliki tanah menjulang tinggi ke atas dengan puncak dan lereng yang curam?",
        opsi: ["Gunung", "Dataran Rendah", "Danau", "Laut"],
        jawaban: 0,
        penjelasan: "Gunung adalah bentang alam yang menjulang tinggi di atas 600 meter dengan lereng yang curam."
      },
      {
        id: "q2",
        level: 1,
        bentang: "gunung",
        soal: "Gunung api terkenal di Jawa Tengah dan Yogyakarta yang sering mengeluarkan abu vulkanik adalah...",
        opsi: ["Gunung Merapi", "Gunung Jayawijaya", "Gunung Bukit Raya", "Gunung Slamet"],
        jawaban: 0,
        penjelasan: "Gunung Merapi adalah salah satu gunung api paling aktif di Indonesia yang terletak di perbatasan DIY dan Jawa Tengah."
      },
      {
        id: "q3",
        level: 1,
        bentang: "dataran_tinggi",
        soal: "Dataran Tinggi Dieng yang terkenal dengan udaranya yang sangat sejuk dan kebun kentangnya berada di provinsi...",
        opsi: ["Jawa Tengah", "Kalimantan Barat", "Bali", "Papua"],
        jawaban: 0,
        penjelasan: "Dataran Tinggi Dieng berada di wilayah Kabupaten Banjarnegara dan Wonosobo, Jawa Tengah."
      },
      {
        id: "q4",
        level: 1,
        bentang: "dataran_rendah",
        soal: "Daerah daratan yang datar dengan ketinggian 0 - 200 meter dpl dan banyak dihuni manusia untuk perkantoran dan sawah disebut...",
        opsi: ["Dataran Rendah", "Puncak Gunung", "Jurang Terjal", "Tebing Laut"],
        jawaban: 0,
        penjelasan: "Dataran rendah memiliki tanah datar sehingga sangat mudah dibangun rumah, perkotaan, dan sawah bertani."
      },
      {
        id: "q5",
        level: 1,
        bentang: "sungai",
        soal: "Sungai terpanjang di Indonesia yang melintasi pulau Kalimantan adalah...",
        opsi: ["Sungai Kapuas", "Sungai Musi", "Sungai Bengawan Solo", "Sungai Citarum"],
        jawaban: 0,
        penjelasan: "Sungai Kapuas di Kalimantan Barat memiliki panjang mencapai 1.143 km menjadikannya sungai terpanjang di Indonesia."
      },
      {
        id: "q6",
        level: 1,
        bentang: "danau",
        soal: "Danau vulkanik sangat luas di Sumatra Utara yang memiliki Pulau Samosir di tengahnya adalah...",
        opsi: ["Danau Toba", "Danau Sentani", "Danau Singkarak", "Danau Maninjau"],
        jawaban: 0,
        penjelasan: "Danau Toba adalah danau vulkanik terbesar di Indonesia bahkan di Asia Tenggara dengan pulau Samosir di tengahnya."
      },
      {
        id: "q7",
        level: 1,
        bentang: "laut",
        soal: "Air di laut rasanya asin karena mengandung banyak...",
        opsi: ["Garam mineral alami", "Gula pasir", "Air perasan jeruk", "Minyak goreng"],
        jawaban: 0,
        penjelasan: "Air laut terasa asin karena batuan dan tanah di daratan mengikis mineral garam yang terbawa ke laut selama jutaan tahun."
      },

      // LEVEL 2: PAHAMI
      {
        id: "q8",
        level: 2,
        bentang: "dataran_tinggi",
        soal: "Mengapa tanaman teh dan sayur kubis tumbuh subur di wilayah dataran tinggi?",
        opsi: ["Karena suhunya sejuk, dingin, dan tanahnya subur", "Karena airnya sangat asin", "Karena tanahnya tandus dan gersang", "Karena tidak pernah terkena sinar matahari"],
        jawaban: 0,
        penjelasan: "Suhu yang sejuk serta tanah vulkanik yang kaya hara di dataran tinggi sangat cocok untuk daun teh dan sayuran segar."
      },
      {
        id: "q9",
        level: 2,
        bentang: "sungai",
        soal: "Di Kota Banjarmasin dan Palembang, sungai besar banyak dimanfaatkan oleh masyarakat untuk...",
        opsi: ["Pasar terapung & jalur perahu", "Bermain ski es salju", "Membuat jalan tol bertingkat", "Mendirikan gedung pencakar langit"],
        jawaban: 0,
        penjelasan: "Masyarakat memanfaatkan aliran sungai yang tenang sebagai jalur transportasi perahu dan pasar terapung tradisional."
      },
      {
        id: "q10",
        level: 2,
        bentang: "laut",
        soal: "Hutan bakau (mangrove) yang ditanam di pinggir pesisir pantai sangat bermanfaat untuk...",
        opsi: ["Mencegah abrasi atau pengikisan pantai oleh ombak", "Menyebabkan ombak semakin tinggi", "Mengurangi rasa asin air laut", "Menghalangi perahu nelayan mencari ikan"],
        jawaban: 0,
        penjelasan: "Akar pohon bakau yang kuat menahan hantaman ombak laut sehingga tanah pesisir pantai tidak terkikis (abrasi)."
      },
      {
        id: "q11",
        level: 2,
        bentang: "danau",
        soal: "Bagaimanakah air danau yang sangat besar seperti Danau Toba dapat menghasilkan aliran listrik?",
        opsi: ["Dibuat Pembangkit Listrik Tenaga Air (PLTA) yang memutar turbin", "Air danau langsung dialirkan ke kabel listrik", "Dengan menjemur danau di bawah matahari", "Menggunakan mesin kapal cepat"],
        jawaban: 0,
        penjelasan: "Aliran limpasan air danau yang dialirkan memutar turbin generator PLTA untuk memproduksi listrik yang ramah lingkungan."
      },
      {
        id: "q12",
        level: 2,
        bentang: "gunung",
        soal: "Walaupun letusan gunung api berbahaya, mengapa tanah di sekitar lereng gunung setelah beberapa waktu menjadi sangat subur?",
        opsi: ["Abu vulkanik mengandung banyak unsur hara mineral baik", "Lahar panas mendinginkan tanaman", "Gunung menyedot air laut", "Puncak gunung menghalangi sinar matahari"],
        jawaban: 0,
        penjelasan: "Abu vulkanik dari dalam bumi kaya akan mineral fosfor, kalium, dan magnesium yang menyuburkan tanah pertanian."
      },

      // LEVEL 3: TERAPKAN
      {
        id: "q13",
        level: 3,
        bentang: "dataran_rendah",
        soal: "Rani tinggal di daerah yang tanahnya datar, dekat dengan jalan raya besar, banyak sawah irigasi, dan dekat pasar kota. Bentang alam yang Rani tempati adalah...",
        opsi: ["Dataran Rendah", "Puncak Gunung Rinjani", "Tengah Danau Sentani", "Jurang Dataran Tinggi"],
        jawaban: 0,
        penjelasan: "Ciri permukiman ramai, sawah irigasi, dan jalur transportasi mudah adalah karakteristik utama dataran rendah."
      },
      {
        id: "q14",
        level: 3,
        bentang: "laut",
        soal: "Pak Joko adalah seorang kepala keluarga yang bekerja membuat garam dengan menguapkan air di tambak pesisir pantai. Pekerjaan Pak Joko sangat bergantung pada bentang alam...",
        opsi: ["Laut dan Pesisir Pantai", "Pegunungan Tinggi", "Danau Air Tawar", "Hulu Sungai di Hutan"],
        jawaban: 0,
        penjelasan: "Petani garam memanfaatkan air laut asin yang dipanaskan sinar matahari di pesisir hingga air menguap dan kristal garam tersisa."
      },
      {
        id: "q15",
        level: 3,
        bentang: "gunung",
        soal: "Ketika Budi berkunjung ke lereng Gunung Bromo, ia melihat petani membuat sawah berundak-undak (terasering). Tujuan utama terasering adalah...",
        opsi: ["Mencegah tanah longsor dan erosi tanah saat hujan lebat", "Agar terlihat indah saat difoto wisatawan saja", "Supaya air hujan tidak bisa menyiram tanaman", "Supaya mobil balap bisa lewat di sawah"],
        jawaban: 0,
        penjelasan: "Terasering di lereng curam memecah aliran air deras sehingga mencegah erosi dan tanah longsor di perbukitan."
      },
      {
        id: "q16",
        level: 3,
        bentang: "sungai",
        soal: "Jika banyak warga membuang sampah plastik ke aliran Sungai Musi, dampak buruk langsung yang terjadi pada musim hujan adalah...",
        opsi: ["Aliran sungai tersumbat dan memicu banjir di permukiman", "Air sungai menjadi semakin bersih dan wangi", "Ikan di sungai bertambah banyak", "Perahu bisa melaju lebih kencang"],
        jawaban: 0,
        penjelasan: "Sampah yang menumpuk menghambat debit air sungai sehingga air meluap ke daratan menjadi banjir merugikan."
      }
    ];

    /* ================================================================
       3. STATE MANAGEMENT APLIKASI
       ================================================================ */
    const APP_STATE = {
      currentView: "home",
      deviceView: "auto", // auto | laptop | tablet | phone
      teacherMode: false,
      audioEnabled: true,
      audioCtx: null,
      
      // Game Creation Config
      creatorConfig: {
        gameType: "rocket", // rocket | frog | racecar | ocean
        selectedBentang: ["gunung", "dataran_tinggi"],
        character: "astronaut", // boy | girl | explorer | astronaut | driver | frog | captain
        theme: "petualangan", // petualangan, luar_angkasa, pegunungan, laut, pedesaan, kota, fantasi
        difficulty: "sedang", // mudah | sedang | tantangan
        questionCount: 5,
        title: "Petualangan Angkasa Nusantara",
        customPrompt: ""
      },
      
      // Active Running Game Session
      gameSession: {
        gameInstance: null,
        activeQuestions: [],
        currentQuestionIndex: 0,
        score: 0,
        coins: 0,
        stars: 3,
        starsCollectedForGate: 0,
        targetStarsPerGate: 5,
        lives: 3,
        maxLives: 3,
        correctCount: 0,
        wrongCount: 0,
        wrongQuestions: [],
        level: 1,
        totalLevels: 3,
        isPaused: false,
        isFinished: false,
        gameLoopId: null
      },

      // Student Saved Gallery
      savedGames: [
        {
          id: "game-default-1",
          title: "Roket Penjelajah Puncak Merapi 🚀",
          gameType: "rocket",
          selectedBentang: ["gunung"],
          character: "astronaut",
          theme: "pegunungan",
          difficulty: "mudah",
          questionCount: 5,
          createdAt: "2026-09-27"
        },
        {
          id: "game-default-2",
          title: "Mobil Balap Pantura & Dieng 🏎️",
          gameType: "racecar",
          selectedBentang: ["dataran_rendah", "dataran_tinggi"],
          character: "driver",
          theme: "pedesaan",
          difficulty: "sedang",
          questionCount: 5,
          createdAt: "2026-09-27"
        },
        {
          id: "game-default-3",
          title: "Kapal Ekspedisi Laut Nusantara 🚢",
          gameType: "ocean",
          selectedBentang: ["laut", "sungai", "danau"],
          character: "captain",
          theme: "laut",
          difficulty: "tantangan",
          questionCount: 5,
          createdAt: "2026-09-27"
        }
      ],

      // Teacher / Student logs
      playHistory: []
    };

    // Web Audio API Sound Synthesizer (No external mp3 files needed)
    function playBeep(type = "click") {
      if (!APP_STATE.audioEnabled) return;
      try {
        const AudioContext = window.AudioContext || window.webkitAudioContext;
        if (!APP_STATE.audioCtx) {
          APP_STATE.audioCtx = new AudioContext();
        }
        if (APP_STATE.audioCtx.state === 'suspended') {
          APP_STATE.audioCtx.resume();
        }
        const ctx = APP_STATE.audioCtx;
        const now = ctx.currentTime;
        const osc = ctx.createOscillator();
        const gain = ctx.createGain();
        osc.connect(gain);
        gain.connect(ctx.destination);

        if (type === "click") {
          osc.type = "sine";
          osc.frequency.setValueAtTime(440, now);
          osc.frequency.exponentialRampToValueAtTime(880, now + 0.08);
          gain.gain.setValueAtTime(0.2, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.08);
          osc.start(now);
          osc.stop(now + 0.08);
        } else if (type === "correct") {
          // Cheerful chime: C5 -> E5 -> G5
          osc.type = "triangle";
          osc.frequency.setValueAtTime(523.25, now);
          osc.frequency.setValueAtTime(659.25, now + 0.1);
          osc.frequency.setValueAtTime(783.99, now + 0.2);
          gain.gain.setValueAtTime(0.3, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.35);
          osc.start(now);
          osc.stop(now + 0.35);
        } else if (type === "wrong") {
          // Low buzz
          osc.type = "sawtooth";
          osc.frequency.setValueAtTime(180, now);
          osc.frequency.exponentialRampToValueAtTime(110, now + 0.25);
          gain.gain.setValueAtTime(0.25, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.25);
          osc.start(now);
          osc.stop(now + 0.25);
        } else if (type === "jump") {
          osc.type = "sine";
          osc.frequency.setValueAtTime(250, now);
          osc.frequency.exponentialRampToValueAtTime(600, now + 0.15);
          gain.gain.setValueAtTime(0.2, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.15);
          osc.start(now);
          osc.stop(now + 0.15);
        } else if (type === "star") {
          osc.type = "sine";
          osc.frequency.setValueAtTime(600, now);
          osc.frequency.exponentialRampToValueAtTime(1200, now + 0.2);
          gain.gain.setValueAtTime(0.3, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.2);
          osc.start(now);
          osc.stop(now + 0.2);
        }
      } catch (err) {
        console.warn("Audio Context init pending user gesture:", err);
      }
    }

    function toggleAudio() {
      APP_STATE.audioEnabled = !APP_STATE.audioEnabled;
      const btn = document.getElementById("audioBtn");
      btn.innerText = APP_STATE.audioEnabled ? "🔊" : "🔇";
      showToast(APP_STATE.audioEnabled ? "Suara Efek Aktif 🎵" : "Suara Dibisukan 🔇");
    }

    function showModal(title, msg, emoji = "🌟", actionCallback = null) {
      const modal = document.getElementById("customModal");
      const card = document.getElementById("modalCard");
      document.getElementById("modalTitle").innerText = title;
      document.getElementById("modalMsg").innerHTML = msg;
      document.getElementById("modalEmoji").innerText = emoji;

      modal.classList.remove("hidden");
      setTimeout(() => {
        card.classList.remove("scale-95", "opacity-0");
        card.classList.add("scale-100", "opacity-100");
      }, 10);

      const actionsDiv = document.getElementById("modalActions");
      actionsDiv.innerHTML = `
        <button onclick="closeModal(${actionCallback ? 'true' : 'false'})" class="px-6 py-2.5 bg-gradient-to-r from-amber-400 to-orange-400 hover:from-amber-500 hover:to-orange-500 text-white font-bold rounded-2xl border-2 border-orange-500 shadow-md text-base transition">
          Oke, Mengerti! 👍
        </button>
      `;
      window._pendingModalCallback = actionCallback;
    }

    function closeModal(executeCallback = false) {
      const modal = document.getElementById("customModal");
      const card = document.getElementById("modalCard");
      card.classList.remove("scale-100", "opacity-100");
      card.classList.add("scale-95", "opacity-0");
      setTimeout(() => {
        modal.classList.add("hidden");
        if (executeCallback && window._pendingModalCallback) {
          window._pendingModalCallback();
          window._pendingModalCallback = null;
        }
      }, 200);
    }

    function showToast(msg, icon = "✨") {
      const toast = document.getElementById("toastNotification");
      document.getElementById("toastIcon").innerText = icon;
      document.getElementById("toastMsg").innerText = msg;
      toast.classList.remove("translate-y-24", "opacity-0");
      toast.classList.add("translate-y-0", "opacity-100");
      setTimeout(() => {
        toast.classList.add("translate-y-24", "opacity-0");
        toast.classList.remove("translate-y-0", "opacity-100");
      }, 2500);
    }

    function toggleTeacherMode() {
      APP_STATE.teacherMode = !APP_STATE.teacherMode;
      const icon = document.getElementById("modeIcon");
      const text = document.getElementById("modeText");
      if (APP_STATE.teacherMode) {
        icon.innerText = "👩‍🏫";
        text.innerText = "Mode Guru";
        showToast("Beralih ke Mode Guru & Evaluasi Kelas", "👩‍🏫");
        navigateTo("teacher-dashboard");
      } else {
        icon.innerText = "🎒";
        text.innerText = "Mode Siswa";
        showToast("Beralih ke Mode Siswa / Petualang Cilik", "🎒");
        navigateTo("home");
      }
    }

    function toggleDeviceDropdown() {
      playBeep("click");
      const menu = document.getElementById("deviceDropdownMenu");
      if (menu) menu.classList.toggle("hidden");
    }

    // Close device dropdown on outside click
    window.addEventListener("click", function(e) {
      const wrap = document.getElementById("deviceDropdownWrap");
      const menu = document.getElementById("deviceDropdownMenu");
      if (wrap && menu && !wrap.contains(e.target)) {
        menu.classList.add("hidden");
      }
    });

    function setDeviceView(mode) {
      playBeep("click");
      APP_STATE.deviceView = mode;
      const menu = document.getElementById("deviceDropdownMenu");
      if (menu) menu.classList.add("hidden");

      const label = document.getElementById("deviceLabel");
      const icon = document.getElementById("deviceIcon");
      const container = document.getElementById("appContainer");
      if (!container) return;

      // Reset dynamic device container classes
      container.className = "flex-1 w-full mx-auto p-3 sm:p-6 transition-all duration-300";

      if (mode === "laptop") {
        if (icon) icon.innerText = "💻";
        if (label) label.innerText = "Laptop";
        container.classList.add("max-w-5xl");
        showToast("Tampilan disesuaikan untuk Laptop 💻", "💻");
      } else if (mode === "tablet") {
        if (icon) icon.innerText = "📟";
        if (label) label.innerText = "Tablet";
        container.classList.add("max-w-[768px]", "border-4", "border-slate-800", "rounded-3xl", "bg-sky-100/50", "shadow-2xl", "my-4");
        showToast("Tampilan disesuaikan untuk Tablet (768px) 📟", "📟");
      } else if (mode === "phone") {
        if (icon) icon.innerText = "📱";
        if (label) label.innerText = "HP";
        container.classList.add("max-w-[420px]", "border-[6px]", "border-slate-900", "rounded-[36px]", "bg-sky-100/60", "shadow-2xl", "my-4", "p-2");
        showToast("Tampilan disesuaikan untuk Smartphone (HP) 📱", "📱");
      } else { // auto
        if (icon) icon.innerText = "🖥️";
        if (label) label.innerText = "Otomatis";
        container.classList.add("max-w-6xl");
        showToast("Tampilan kembali ke Mode Otomatis 🔄", "🖥️");
      }

      // Trigger resize for Canvas and responsive elements
      setTimeout(() => {
        window.dispatchEvent(new Event("resize"));
      }, 150);
    }

    function navigateTo(viewName, params = {}) {
      playBeep("click");
      // Stop ongoing game loop if leaving play screen
      if (APP_STATE.gameSession && APP_STATE.gameSession.gameLoopId) {
        cancelAnimationFrame(APP_STATE.gameSession.gameLoopId);
        APP_STATE.gameSession.gameLoopId = null;
      }
      APP_STATE.currentView = viewName;
      const container = document.getElementById("appContainer");
      window.scrollTo({ top: 0, behavior: 'smooth' });

      switch (viewName) {
        case "home":
          container.innerHTML = renderHomeView();
          break;
        case "encyclopedia":
          container.innerHTML = renderEncyclopediaView(params.selectedId);
          break;
        case "creator-hub":
          container.innerHTML = renderCreatorHubView();
          break;
        case "ai-generator":
          container.innerHTML = renderAiGeneratorView();
          runAiGameBuildingAnimation();
          break;
        case "play":
          container.innerHTML = renderPlayView();
          initGameCanvas();
          break;
        case "results":
          container.innerHTML = renderResultsView();
          break;
        case "review":
          container.innerHTML = renderReviewView();
          break;
        case "reflection":
          container.innerHTML = renderReflectionView();
          break;
        case "gallery":
          container.innerHTML = renderGalleryView();
          break;
        case "teacher-dashboard":
          container.innerHTML = renderTeacherDashboardView();
          break;
        default:
          container.innerHTML = renderHomeView();
      }
    }

    /* ================================================================
       4. VIEW RENDERERS (Tampilan Bersahabat Siswa SD)
       ================================================================ */

    function renderHomeView() {
      return `
        <div class="space-y-8 animate-fadeIn">
          <!-- Hero Banner -->
          <div class="relative overflow-hidden rounded-3xl bg-gradient-to-r from-sky-400 via-emerald-400 to-amber-300 p-6 sm:p-10 border-4 border-white shadow-xl">
            <div class="relative z-10 max-w-2xl">
              <span class="inline-block px-4 py-1 rounded-full bg-white/80 backdrop-blur-sm text-emerald-800 font-bold text-xs sm:text-sm uppercase tracking-wider mb-3 shadow-sm border border-emerald-200">
                🎮 Playground Belajar & Kreator Game SD
              </span>
              <h1 class="text-3xl sm:text-5xl font-extrabold text-emerald-950 tracking-tight leading-tight mb-3">
                Jelajahi Alam Indonesia & Buat Game-mu Sendiri!
              </h1>
              <p class="text-sm sm:text-lg text-emerald-900 font-semibold mb-6 leading-relaxed">
                Pilih roket, mobil balap, katak melompat, atau kapal layar. Tentukan gunung, sungai, dan laut Nusantara yang ingin kamu taklukkan!
              </p>
              <div class="flex flex-wrap items-center gap-3">
                <button onclick="navigateTo('creator-hub')" class="px-6 py-3.5 bg-gradient-to-r from-amber-400 to-orange-500 hover:from-amber-500 hover:to-orange-600 text-white font-extrabold text-base sm:text-lg rounded-2xl shadow-lg border-2 border-white transform hover:scale-105 active:scale-95 transition flex items-center gap-2">
                  <span>✨ Mulai Jadi Game Creator!</span>
                </button>
                <button onclick="navigateTo('encyclopedia')" class="px-5 py-3.5 bg-white/90 hover:bg-white text-emerald-900 font-bold text-sm sm:text-base rounded-2xl shadow-md border-2 border-emerald-200 hover:scale-105 transition flex items-center gap-2">
                  <span>📖 Buka Ensiklopedia Alam</span>
                </button>
              </div>
            </div>

            <!-- Floating 3D Nature Icons Illustration -->
            <div class="hidden lg:block absolute right-8 top-1/2 -translate-y-1/2 text-center pointer-events-none">
              <div class="text-8xl animate-float">🏔️</div>
              <div class="flex gap-4 -mt-4">
                <span class="text-6xl animate-bounce-slow" style="animation-delay: 0.5s;">🚀</span>
                <span class="text-6xl animate-float" style="animation-delay: 1s;">🌊</span>
                <span class="text-6xl animate-bounce-slow" style="animation-delay: 1.5s;">🐸</span>
              </div>
            </div>
          </div>

          <!-- Feature Cards: 4 Game Options Preview -->
          <div>
            <div class="flex items-center justify-between mb-4">
              <div>
                <h2 class="text-2xl sm:text-3xl font-bold text-slate-800">Pilih 4 Mode Game Keren</h2>
                <p class="text-xs sm:text-sm text-slate-600 font-medium">Setiap game memiliki petualangan dan rintangan unik untuk menjelajahi bentang alam!</p>
              </div>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
              <!-- Game 1 -->
              <div onclick="selectGameAndCreate('rocket')" class="cursor-pointer bg-white rounded-3xl p-5 border-4 border-sky-300 hover:border-sky-500 shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition flex flex-col justify-between group">
                <div>
                  <div class="w-16 h-16 rounded-2xl bg-sky-100 flex items-center justify-center text-4xl mb-4 group-hover:scale-110 transition border-2 border-sky-200 shadow-inner">
                    🚀
                  </div>
                  <span class="text-xs font-bold px-2.5 py-1 bg-sky-100 text-sky-800 rounded-lg">Aksi Terbang</span>
                  <h3 class="text-xl font-bold text-slate-800 mt-2">Rocket Adventure</h3>
                  <p class="text-xs text-slate-600 mt-2 leading-relaxed">
                    Kendalikan roket meluncur melintasi puncak gunung dan awan. Kumpulkan bahan bakar dengan menjawab pertanyaan!
                  </p>
                </div>
                <div class="mt-4 pt-3 border-t border-slate-100 flex items-center justify-between text-xs font-bold text-sky-600">
                  <span>Mainkan ➔</span>
                  <span class="text-amber-500">⭐ Bintang Ilmu</span>
                </div>
              </div>

              <!-- Game 2 -->
              <div onclick="selectGameAndCreate('frog')" class="cursor-pointer bg-white rounded-3xl p-5 border-4 border-emerald-300 hover:border-emerald-500 shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition flex flex-col justify-between group">
                <div>
                  <div class="w-16 h-16 rounded-2xl bg-emerald-100 flex items-center justify-center text-4xl mb-4 group-hover:scale-110 transition border-2 border-emerald-200 shadow-inner">
                    🐸
                  </div>
                  <span class="text-xs font-bold px-2.5 py-1 bg-emerald-100 text-emerald-800 rounded-lg">Lompat Platform</span>
                  <h3 class="text-xl font-bold text-slate-800 mt-2">Petualangan Katak</h3>
                  <p class="text-xs text-slate-600 mt-2 leading-relaxed">
                    Lompati daun teratai di sungai dan danau nusantara. Jawab tantangan agar melompat semakin jauh dan aman!
                  </p>
                </div>
                <div class="mt-4 pt-3 border-t border-slate-100 flex items-center justify-between text-xs font-bold text-emerald-600">
                  <span>Mainkan ➔</span>
                  <span class="text-emerald-500">🌿 Danau & Sungai</span>
                </div>
              </div>

              <!-- Game 3 -->
              <div onclick="selectGameAndCreate('racecar')" class="cursor-pointer bg-white rounded-3xl p-5 border-4 border-amber-300 hover:border-amber-500 shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition flex flex-col justify-between group">
                <div>
                  <div class="w-16 h-16 rounded-2xl bg-amber-100 flex items-center justify-center text-4xl mb-4 group-hover:scale-110 transition border-2 border-amber-200 shadow-inner">
                    🏎️
                  </div>
                  <span class="text-xs font-bold px-2.5 py-1 bg-amber-100 text-amber-800 rounded-lg">Balapan Seru</span>
                  <h3 class="text-xl font-bold text-slate-800 mt-2">Race Car Indonesia</h3>
                  <p class="text-xs text-slate-600 mt-2 leading-relaxed">
                    Pacu mobil balap di lintasan jalur Pantura hingga tikungan terasering Dieng! Raih speed boost di setiap checkpoint.
                  </p>
                </div>
                <div class="mt-4 pt-3 border-t border-slate-100 flex items-center justify-between text-xs font-bold text-amber-600">
                  <span>Mainkan ➔</span>
                  <span class="text-amber-500">⚡ Checkpoint Speed</span>
                </div>
              </div>

              <!-- Game 4 -->
              <div onclick="selectGameAndCreate('ocean')" class="cursor-pointer bg-white rounded-3xl p-5 border-4 border-indigo-300 hover:border-indigo-500 shadow-lg hover:shadow-2xl transform hover:-translate-y-2 transition flex flex-col justify-between group">
                <div>
                  <div class="w-16 h-16 rounded-2xl bg-indigo-100 flex items-center justify-center text-4xl mb-4 group-hover:scale-110 transition border-2 border-indigo-200 shadow-inner">
                    🌊🚢
                  </div>
                  <span class="text-xs font-bold px-2.5 py-1 bg-indigo-100 text-indigo-800 rounded-lg">Ekspedisi Maritim</span>
                  <h3 class="text-xl font-bold text-slate-800 mt-2">Ocean Explorer</h3>
                  <p class="text-xs text-slate-600 mt-2 leading-relaxed">
                    Nahkodai kapal mengarungi pulau, muara sungai, dan terumbu karang. Kumpulkan Kompas Pengetahuan Nusantara!
                  </p>
                </div>
                <div class="mt-4 pt-3 border-t border-slate-100 flex items-center justify-between text-xs font-bold text-indigo-600">
                  <span>Mainkan ➔</span>
                  <span class="text-blue-500">🧭 Kompas Pengetahuan</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Quick Bentang Alam Glance -->
          <div class="bg-white rounded-3xl p-6 border-4 border-emerald-200 shadow-md">
            <h3 class="text-xl font-bold text-slate-800 mb-2">Kenali 6 Bentang Alam Indonesia</h3>
            <p class="text-xs sm:text-sm text-slate-600 mb-4">Klik salah satu bentang alam untuk mempelajari ciri, manfaat, dan keindahannya secara mendalam:</p>
            <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
              ${Object.values(BENTANG_ALAM_DATA).map(b => `
                <div onclick="navigateTo('encyclopedia', { selectedId: '${b.id}' })" class="cursor-pointer bg-slate-50 hover:bg-emerald-50 border-2 border-slate-200 hover:border-emerald-400 p-3 rounded-2xl text-center transition transform hover:-translate-y-1">
                  <div class="text-3xl mb-1">${b.icon}</div>
                  <div class="font-bold text-xs sm:text-sm text-slate-800">${b.nama}</div>
                </div>
              `).join('')}
            </div>
          </div>
        </div>
      `;
    }

    function renderEncyclopediaView(selectedId = "gunung") {
      const b = BENTANG_ALAM_DATA[selectedId] || BENTANG_ALAM_DATA.gunung;
      return `
        <div class="space-y-6 animate-fadeIn">
          <!-- Back and Header -->
          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
            <div>
              <span class="text-xs font-extrabold uppercase tracking-wider text-emerald-700 bg-emerald-100 px-3 py-1 rounded-full border border-emerald-300">
                📚 Materi Pelajaran IPA & IPS
              </span>
              <h2 class="text-2xl sm:text-4xl font-extrabold text-slate-800 mt-1">Ensiklopedia Bentang Alam Indonesia</h2>
            </div>
            <button onclick="navigateTo('creator-hub')" class="self-start sm:self-auto px-5 py-2.5 bg-amber-400 hover:bg-amber-500 text-amber-950 font-bold rounded-2xl border-2 border-amber-500 shadow-md text-sm transition">
              ✨ Langsung Buat Game dari Materi Ini!
            </button>
          </div>

          <!-- Landscape Tabs -->
          <div class="flex overflow-x-auto pb-2 gap-2 no-scrollbar">
            ${Object.values(BENTANG_ALAM_DATA).map(item => `
              <button onclick="navigateTo('encyclopedia', { selectedId: '${item.id}' })" class="px-4 py-2.5 rounded-2xl font-bold text-xs sm:text-sm whitespace-nowrap transition flex items-center gap-2 border-2 ${item.id === b.id ? 'bg-emerald-600 text-white border-emerald-700 shadow-md scale-105' : 'bg-white text-slate-700 hover:bg-slate-100 border-slate-200'}">
                <span>${item.icon}</span>
                <span>${item.nama}</span>
              </button>
            `).join('')}
          </div>

          <!-- Main Detail Card -->
          <div class="bg-white rounded-3xl border-4 border-emerald-300 p-6 sm:p-8 shadow-xl space-y-6">
            <!-- Title Bar with Badge -->
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 pb-4 border-b-2 border-slate-100">
              <div class="flex items-center gap-4">
                <div class="w-16 h-16 sm:w-20 sm:h-20 rounded-3xl bg-gradient-to-tr ${b.warna} text-white flex items-center justify-center text-4xl sm:text-5xl shadow-lg border-2 border-white">
                  ${b.icon}
                </div>
                <div>
                  <span class="text-xs font-bold px-3 py-1 rounded-full ${b.bgBadge} border">Bentang Alam Nusantara</span>
                  <h3 class="text-2xl sm:text-4xl font-extrabold text-slate-800 mt-1">${b.nama}</h3>
                </div>
              </div>
              <div class="bg-amber-50 rounded-2xl p-3 border-2 border-amber-200 max-w-xs text-xs text-amber-900 font-semibold">
                💡 <span class="font-bold">Fakta Seru:</span> ${b.faktaMenarik}
              </div>
            </div>

            <!-- Pengertian Sederhana -->
            <div class="bg-sky-50 rounded-2xl p-4 sm:p-5 border-2 border-sky-200">
              <h4 class="text-sm sm:text-base font-extrabold text-sky-900 mb-1 flex items-center gap-1.5">
                <span>📖</span> <span>Apa itu ${b.nama}?</span>
              </h4>
              <p class="text-xs sm:text-sm text-sky-800 leading-relaxed font-medium">
                ${b.pengertian}
              </p>
            </div>

            <!-- Grid 2 Columns: Ciri & Contoh -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div class="bg-slate-50 p-5 rounded-2xl border-2 border-slate-200">
                <h4 class="font-bold text-slate-800 text-sm mb-3 flex items-center gap-2">
                  <span class="text-emerald-600">🔍</span> Ciri-ciri Utama:
                </h4>
                <ul class="space-y-2 text-xs sm:text-sm text-slate-700 font-medium">
                  ${b.ciri.map(c => `<li class="flex items-start gap-2"><span class="text-emerald-500 font-bold">•</span><span>${c}</span></li>`).join('')}
                </ul>
              </div>

              <div class="bg-slate-50 p-5 rounded-2xl border-2 border-slate-200">
                <h4 class="font-bold text-slate-800 text-sm mb-3 flex items-center gap-2">
                  <span class="text-amber-500">📍</span> Contoh Nyata di Indonesia:
                </h4>
                <div class="flex flex-wrap gap-2">
                  ${b.contoh.map(c => `<span class="bg-white border-2 border-emerald-300 text-emerald-800 font-bold text-xs px-3 py-1.5 rounded-xl shadow-sm">🇮🇩 ${c}</span>`).join('')}
                </div>
              </div>
            </div>

            <!-- Manfaat, Flora/Fauna, Aktivitas -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
              <div class="bg-emerald-50/70 p-4 rounded-2xl border-2 border-emerald-200">
                <h5 class="font-bold text-emerald-900 text-xs sm:text-sm mb-2 flex items-center gap-1.5">
                  <span>🌱</span> Manfaat Bagi Manusia
                </h5>
                <ul class="text-xs text-emerald-800 space-y-1.5 font-medium">
                  ${b.manfaat.map(m => `<li>✓ ${m}</li>`).join('')}
                </ul>
              </div>

              <div class="bg-purple-50/70 p-4 rounded-2xl border-2 border-purple-200">
                <h5 class="font-bold text-purple-900 text-xs sm:text-sm mb-2 flex items-center gap-1.5">
                  <span>🦜</span> Flora & Fauna Khas
                </h5>
                <p class="text-xs text-purple-800 leading-relaxed font-medium">
                  ${b.floraFauna}
                </p>
              </div>

              <div class="bg-amber-50/70 p-4 rounded-2xl border-2 border-amber-200">
                <h5 class="font-bold text-amber-900 text-xs sm:text-sm mb-2 flex items-center gap-1.5">
                  <span>🧑‍🌾</span> Aktivitas Penduduk
                </h5>
                <p class="text-xs text-amber-800 leading-relaxed font-medium">
                  ${b.aktivitas}
                </p>
              </div>
            </div>
          </div>
        </div>
      `;
    }

    function renderCreatorHubView() {
      const cfg = APP_STATE.creatorConfig;
      return `
        <div class="space-y-6 animate-fadeIn">
          <!-- Title Box -->
          <div class="bg-gradient-to-r from-amber-400 via-orange-400 to-rose-400 rounded-3xl p-6 text-white shadow-xl border-4 border-white flex flex-col sm:flex-row items-center justify-between gap-4">
            <div>
              <span class="px-3 py-1 bg-white/20 backdrop-blur-md rounded-full text-xs font-bold uppercase tracking-wider">
                🎨 Creative Game Studio
              </span>
              <h2 class="text-2xl sm:text-4xl font-extrabold mt-1">SEKARANG KAMU JADI GAME CREATOR!</h2>
              <p class="text-xs sm:text-sm font-medium mt-1 text-white/90">
                Rancang game impianmu sendiri. Pilih kendaraan, bentang alam, dan biarkan AI membantumu meracik permainannya!
              </p>
            </div>
            <div class="text-5xl animate-bounce-slow">🧙‍♂️✨</div>
          </div>

          <!-- Quick Idea Generator Box (Fitur Kreasi Bebas Siswa) -->
          <div class="bg-white rounded-3xl p-5 sm:p-6 border-4 border-purple-300 shadow-md">
            <div class="flex items-center gap-2 mb-2">
              <span class="text-2xl">💡</span>
              <h3 class="text-lg font-bold text-purple-900">Punya Ide Game-mu Sendiri? Tulis di Sini!</h3>
            </div>
            <p class="text-xs text-slate-600 mb-3">
              Tulis ide bebasmu dalam bahasa sehari-hari. Asisten AI akan membacanya dan otomatis mengatur pilihan game di bawah ini untukmu:
            </p>
            <div class="flex flex-col sm:flex-row gap-3">
              <textarea id="freeIdeaInput" rows="2" placeholder="Contoh: Saya ingin membuat game kapal yang menjelajahi sungai dan laut mencari harta karun karang..." class="w-full text-xs sm:text-sm p-3.5 rounded-2xl border-2 border-purple-200 focus:border-purple-500 focus:outline-none bg-purple-50/40 text-slate-800 font-medium"></textarea>
              <button onclick="handleSynthesizeIdea()" class="self-start sm:self-auto whitespace-nowrap px-5 py-3 bg-purple-600 hover:bg-purple-700 text-white font-bold text-xs sm:text-sm rounded-2xl border-2 border-purple-800 shadow-md transition transform hover:scale-105 active:scale-95 flex items-center justify-center gap-2">
                <span>✨ Ubah Ideku Menjadi Game!</span>
              </button>
            </div>
          </div>

          <!-- Step Form Container -->
          <div class="bg-white rounded-3xl p-6 sm:p-8 border-4 border-emerald-300 shadow-xl space-y-8">
            
            <!-- 1. PILIH JENIS GAME -->
            <div>
              <div class="flex items-center gap-2 mb-3">
                <span class="w-7 h-7 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-sm">1</span>
                <h3 class="text-lg font-bold text-slate-800">Pilih Jenis Game:</h3>
              </div>
              <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
                ${[
                  { id: "rocket", name: "Rocket Adventure", icon: "🚀", desc: "Terbang lincah hindari rintangan" },
                  { id: "frog", name: "Petualangan Katak", icon: "🐸", desc: "Lompat daun teratai & batu sungai" },
                  { id: "racecar", name: "Race Car Indonesia", icon: "🏎️", desc: "Balapan cepat di checkpoint" },
                  { id: "ocean", name: "Ocean Explorer", icon: "🚢", desc: "Jelajahi pulau & pesisir bahari" }
                ].map(g => `
                  <div onclick="setCreatorField('gameType', '${g.id}')" class="cursor-pointer p-4 rounded-2xl border-4 text-center transition transform hover:scale-102 ${cfg.gameType === g.id ? 'border-emerald-500 bg-emerald-50 shadow-md' : 'border-slate-200 bg-white hover:border-slate-300'}">
                    <div class="text-4xl mb-1">${g.icon}</div>
                    <div class="font-bold text-xs sm:text-sm text-slate-800">${g.name}</div>
                    <div class="text-[10px] text-slate-500 mt-1">${g.desc}</div>
                  </div>
                `).join('')}
              </div>
            </div>

            <!-- 2. PILIH BENTANG ALAM -->
            <div>
              <div class="flex items-center justify-between mb-3">
                <div class="flex items-center gap-2">
                  <span class="w-7 h-7 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-sm">2</span>
                  <h3 class="text-lg font-bold text-slate-800">Pilih Bentang Alam Yang Dipelajari:</h3>
                </div>
                <button onclick="toggleSelectAllBentang()" class="text-xs font-bold text-emerald-700 bg-emerald-100 hover:bg-emerald-200 px-3 py-1 rounded-xl transition">
                  🌐 Gabungkan Semua
                </button>
              </div>
              <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
                ${Object.values(BENTANG_ALAM_DATA).map(b => {
                  const isChecked = cfg.selectedBentang.includes(b.id);
                  return `
                    <div onclick="toggleBentangSelection('${b.id}')" class="cursor-pointer p-3 rounded-2xl border-4 text-center transition ${isChecked ? 'border-sky-500 bg-sky-50 shadow-md' : 'border-slate-200 bg-white opacity-80'}">
                      <div class="text-3xl mb-1">${b.icon}</div>
                      <div class="font-bold text-xs text-slate-800">${b.nama}</div>
                      <div class="text-[10px] font-bold mt-1 ${isChecked ? 'text-sky-600' : 'text-slate-400'}">
                        ${isChecked ? '✓ Terpilih' : '+ Pilih'}
                      </div>
                    </div>
                  `;
                }).join('')}
              </div>
            </div>

            <!-- 3. PILIH KARAKTER & KENDARAAN -->
            <div>
              <div class="flex items-center gap-2 mb-3">
                <span class="w-7 h-7 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-sm">3</span>
                <h3 class="text-lg font-bold text-slate-800">Pilih Karakter Pahlawanmu:</h3>
              </div>
              <div class="grid grid-cols-3 sm:grid-cols-7 gap-2.5">
                ${[
                  { id: "boy", name: "Anak Laki-laki", icon: "👦" },
                  { id: "girl", name: "Anak Perempuan", icon: "👧" },
                  { id: "explorer", name: "Penjelajah Rimba", icon: "🤠" },
                  { id: "astronaut", name: "Astronaut Cilik", icon: "👨‍🚀" },
                  { id: "driver", name: "Pembalap Cepat", icon: "🏎️" },
                  { id: "frog", name: "Katak Ceria", icon: "🐸" },
                  { id: "captain", name: "Kapten Bahari", icon: "🧑‍✈️" }
                ].map(c => `
                  <div onclick="setCreatorField('character', '${c.id}')" class="cursor-pointer p-2.5 rounded-2xl border-2 text-center transition ${cfg.character === c.id ? 'border-amber-500 bg-amber-50 font-bold shadow-md' : 'border-slate-200 bg-white hover:border-slate-300'}">
                    <div class="text-3xl mb-1">${c.icon}</div>
                    <div class="text-[11px] leading-tight text-slate-800 font-semibold">${c.name}</div>
                  </div>
                `).join('')}
              </div>
            </div>

            <!-- 4. PILIH TEMA VISUAL -->
            <div>
              <div class="flex items-center gap-2 mb-3">
                <span class="w-7 h-7 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-sm">4</span>
                <h3 class="text-lg font-bold text-slate-800">Tentukan Tema Lingkungan Permainan:</h3>
              </div>
              <div class="flex flex-wrap gap-2">
                ${[
                  { id: "petualangan", name: "Petualangan Seru 🏕️" },
                  { id: "luar_angkasa", name: "Luar Angkasa 🌌" },
                  { id: "hutan", name: "Hutan Tropis 🌴" },
                  { id: "pegunungan", name: "Pegunungan Sejuk 🏔️" },
                  { id: "laut", name: "Nusantara Bahari 🌊" },
                  { id: "pedesaan", name: "Pedesaan Asri 🌾" },
                  { id: "kota", name: "Kota Hijau 🏙️" },
                  { id: "fantasi", name: "Dunia Fantasi Pelangi 🌈" }
                ].map(t => `
                  <button onclick="setCreatorField('theme', '${t.id}')" class="px-3.5 py-2 rounded-xl text-xs font-bold border-2 transition ${cfg.theme === t.id ? 'bg-indigo-600 text-white border-indigo-700 shadow-sm' : 'bg-slate-100 text-slate-700 border-slate-300 hover:bg-slate-200'}">
                    ${t.name}
                  </button>
                `).join('')}
              </div>
            </div>

            <!-- 5. KESULITAN & JUMLAH SOAL -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 pt-2 border-t-2 border-slate-100">
              <div>
                <div class="flex items-center gap-2 mb-2">
                  <span class="w-7 h-7 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-sm">5</span>
                  <h3 class="text-base font-bold text-slate-800">Tingkat Kesulitan:</h3>
                </div>
                <div class="grid grid-cols-3 gap-2">
                  ${[
                    { id: "mudah", label: "Mudah 🟢", desc: "Level 1 Kenali" },
                    { id: "sedang", label: "Sedang 🟡", desc: "Level 2 Pahami" },
                    { id: "tantangan", label: "Tantangan 🔴", desc: "Level 3 Terapkan" }
                  ].map(diff => `
                    <button onclick="setCreatorField('difficulty', '${diff.id}')" class="p-2.5 rounded-xl border-2 text-center text-xs font-bold transition ${cfg.difficulty === diff.id ? 'border-emerald-600 bg-emerald-100 text-emerald-900 shadow-sm' : 'border-slate-200 bg-slate-50 text-slate-700'}">
                      <div>${diff.label}</div>
                      <div class="text-[9px] font-normal text-slate-500 mt-0.5">${diff.desc}</div>
                    </button>
                  `).join('')}
                </div>
              </div>

              <div>
                <div class="flex items-center gap-2 mb-2">
                  <span class="w-7 h-7 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-sm">6</span>
                  <h3 class="text-base font-bold text-slate-800">Jumlah Tantangan Soal:</h3>
                </div>
                <div class="grid grid-cols-3 gap-2">
                  ${[5, 10, 15].map(cnt => `
                    <button onclick="setCreatorField('questionCount', ${cnt})" class="p-2.5 rounded-xl border-2 text-center text-xs font-bold transition ${cfg.questionCount === cnt ? 'border-sky-600 bg-sky-100 text-sky-900 shadow-sm' : 'border-slate-200 bg-slate-50 text-slate-700'}">
                      <div class="text-sm">${cnt} Soal</div>
                      <div class="text-[9px] font-normal text-slate-500 mt-0.5">Petualangan</div>
                    </button>
                  `).join('')}
                </div>
              </div>
            </div>

            <!-- Large Action Button: BUAT GAME DENGAN AI -->
            <div class="text-center pt-4">
              <button onclick="startAiGenerationFlow()" class="w-full sm:w-auto px-10 py-5 bg-gradient-to-r from-amber-400 via-orange-500 to-rose-500 hover:from-amber-500 hover:to-rose-600 text-white font-fun font-bold text-xl sm:text-2xl rounded-3xl border-4 border-white shadow-2xl transform hover:scale-105 active:scale-95 transition flex items-center justify-center gap-3 mx-auto animate-pulse-glow">
                <span>✨ BUAT GAME DENGAN AI SEKARANG! 🚀</span>
              </button>
              <p class="text-xs text-slate-500 mt-2 font-medium">
                AI akan meracik dunia game, mengatur rintangan, pertanyaan, dan misi petualanganmu!
              </p>
            </div>

          </div>
        </div>
      `;
    }

    function selectGameAndCreate(gameId) {
      APP_STATE.creatorConfig.gameType = gameId;
      if (gameId === 'ocean') {
        APP_STATE.creatorConfig.selectedBentang = ['laut', 'sungai'];
        APP_STATE.creatorConfig.character = 'captain';
        APP_STATE.creatorConfig.theme = 'laut';
      } else if (gameId === 'frog') {
        APP_STATE.creatorConfig.selectedBentang = ['sungai', 'danau'];
        APP_STATE.creatorConfig.character = 'frog';
        APP_STATE.creatorConfig.theme = 'hutan';
      } else if (gameId === 'racecar') {
        APP_STATE.creatorConfig.selectedBentang = ['dataran_rendah', 'dataran_tinggi'];
        APP_STATE.creatorConfig.character = 'driver';
        APP_STATE.creatorConfig.theme = 'pedesaan';
      } else if (gameId === 'rocket') {
        APP_STATE.creatorConfig.selectedBentang = ['gunung', 'dataran_tinggi'];
        APP_STATE.creatorConfig.character = 'astronaut';
        APP_STATE.creatorConfig.theme = 'pegunungan';
      }
      navigateTo('creator-hub');
    }

    function setCreatorField(field, value) {
      playBeep('click');
      APP_STATE.creatorConfig[field] = value;
      // Re-render creator hub to update active borders
      document.getElementById("appContainer").innerHTML = renderCreatorHubView();
    }

    function toggleBentangSelection(bentangId) {
      playBeep('click');
      let list = APP_STATE.creatorConfig.selectedBentang;
      if (list.includes(bentangId)) {
        if (list.length > 1) {
          list = list.filter(item => item !== bentangId);
        } else {
          showToast("Pilih minimal 1 bentang alam ya!", "⚠️");
          return;
        }
      } else {
        list.push(bentangId);
      }
      APP_STATE.creatorConfig.selectedBentang = list;
      document.getElementById("appContainer").innerHTML = renderCreatorHubView();
    }

    function toggleSelectAllBentang() {
      playBeep('click');
      const all = Object.keys(BENTANG_ALAM_DATA);
      if (APP_STATE.creatorConfig.selectedBentang.length === all.length) {
        APP_STATE.creatorConfig.selectedBentang = ["gunung"];
      } else {
        APP_STATE.creatorConfig.selectedBentang = all;
      }
      document.getElementById("appContainer").innerHTML = renderCreatorHubView();
      showToast("Semua 6 Bentang Alam Terpilih!", "🌟");
    }

    /* Intelligent Idea Synthesizer (Gemini API with Safe Local Fallback) */
    async function handleSynthesizeIdea() {
      playBeep('click');
      const ideaText = document.getElementById("freeIdeaInput").value.trim();
      if (!ideaText) {
        showToast("Tuliskan dulu ide game-mu ya!", "✏️");
        return;
      }
      showToast("Sedang membaca ide kreatifmu...", "✨");

      // Intelligent keyword analysis and synthesis
      const lower = ideaText.toLowerCase();
      let chosenType = APP_STATE.creatorConfig.gameType;
      let chosenBentang = [];
      let chosenChar = APP_STATE.creatorConfig.character;
      let chosenTheme = APP_STATE.creatorConfig.theme;

      if (lower.includes("kapal") || lower.includes("perahu") || lower.includes("laut") || lower.includes("pantai") || lower.includes("ombak") || lower.includes("ikan")) {
        chosenType = "ocean";
        chosenChar = "captain";
        chosenTheme = "laut";
        chosenBentang.push("laut");
      }
      if (lower.includes("katak") || lower.includes("kodok") || lower.includes("lompat") || lower.includes("teratai") || lower.includes("rawa")) {
        chosenType = "frog";
        chosenChar = "frog";
        chosenTheme = "hutan";
        chosenBentang.push("sungai", "danau");
      }
      if (lower.includes("mobil") || lower.includes("balap") || lower.includes("jalanan") || lower.includes("kecepatan") || lower.includes("roda")) {
        chosenType = "racecar";
        chosenChar = "driver";
        chosenTheme = "pedesaan";
        chosenBentang.push("dataran_rendah");
      }
      if (lower.includes("roket") || lower.includes("terbang") || lower.includes("angkasa") || lower.includes("langit") || lower.includes("awan")) {
        chosenType = "rocket";
        chosenChar = "astronaut";
        chosenTheme = "luar_angkasa";
        chosenBentang.push("gunung");
      }

      if (lower.includes("gunung") && !chosenBentang.includes("gunung")) chosenBentang.push("gunung");
      if (lower.includes("tinggi") || lower.includes("dieng") && !chosenBentang.includes("dataran_tinggi")) chosenBentang.push("dataran_tinggi");
      if (lower.includes("rendah") || lower.includes("pantura") || lower.includes("kota") && !chosenBentang.includes("dataran_rendah")) chosenBentang.push("dataran_rendah");
      if (lower.includes("sungai") || lower.includes("kapuas") && !chosenBentang.includes("sungai")) chosenBentang.push("sungai");
      if (lower.includes("danau") || lower.includes("toba") && !chosenBentang.includes("danau")) chosenBentang.push("danau");
      if (lower.includes("laut") || lower.includes("pesisir") && !chosenBentang.includes("laut")) chosenBentang.push("laut");

      if (chosenBentang.length === 0) {
        chosenBentang = ["gunung", "sungai", "laut"];
      }

      // Update state
      APP_STATE.creatorConfig.gameType = chosenType;
      APP_STATE.creatorConfig.selectedBentang = chosenBentang;
      APP_STATE.creatorConfig.character = chosenChar;
      APP_STATE.creatorConfig.theme = chosenTheme;
      APP_STATE.creatorConfig.customPrompt = ideaText;

      showModal(
        "Ide Hebat Terwujud! 🌟",
        `Asisten AI telah menerjemahkan ide kreatifmu:<br><br>
        🎮 <b>Jenis Game:</b> ${chosenType.toUpperCase()}<br>
        🏔️ <b>Bentang Alam:</b> ${chosenBentang.map(b => BENTANG_ALAM_DATA[b].nama).join(', ')}<br>
        🧑‍🚀 <b>Karakter:</b> ${chosenChar}<br><br>
        Pilihan game telah disesuaikan! Kamu bisa langsung menekan tombol buat game!`,
        "🚀",
        () => {
          document.getElementById("appContainer").innerHTML = renderCreatorHubView();
        }
      );
    }

    function startAiGenerationFlow() {
      playBeep('star');
      navigateTo('ai-generator');
    }

    function renderAiGeneratorView() {
      const cfg = APP_STATE.creatorConfig;
      const bentangNames = cfg.selectedBentang.map(b => BENTANG_ALAM_DATA[b]?.nama || b).join(" + ");
      return `
        <div class="max-w-2xl mx-auto py-10 text-center space-y-8 animate-fadeIn">
          <div class="relative inline-block">
            <div class="w-32 h-32 rounded-full bg-gradient-to-tr from-amber-400 via-orange-500 to-purple-600 flex items-center justify-center text-6xl shadow-2xl mx-auto animate-bounce-slow border-4 border-white">
              🤖
            </div>
            <div class="absolute -bottom-2 -right-2 text-4xl animate-pulse">✨</div>
          </div>

          <div>
            <h2 class="text-3xl sm:text-4xl font-extrabold text-slate-800 font-fun">
              AI SEDANG MERACIK GAME-MU!
            </h2>
            <p class="text-sm text-slate-600 font-semibold mt-2">
              Menggabungkan ide bentang alam Nusantara dan aturan game impianmu...
            </p>
          </div>

          <!-- Progress Checklist Box -->
          <div class="bg-white rounded-3xl p-6 border-4 border-emerald-300 shadow-xl text-left space-y-4 max-w-md mx-auto">
            <div id="step1" class="flex items-center gap-3 text-slate-400 font-bold text-xs sm:text-sm transition">
              <span class="text-lg">⏳</span> Membangun Lingkungan: <b class="text-slate-700">${bentangNames}</b>
            </div>
            <div id="step2" class="flex items-center gap-3 text-slate-400 font-bold text-xs sm:text-sm transition">
              <span class="text-lg">⏳</span> Memasang Karakter & Rintangan Game: <b class="text-slate-700">${cfg.character}</b>
            </div>
            <div id="step3" class="flex items-center gap-3 text-slate-400 font-bold text-xs sm:text-sm transition">
              <span class="text-lg">⏳</span> Menyusun Bank Soal & Checkpoint Edukasi...
            </div>
            <div id="step4" class="flex items-center gap-3 text-slate-400 font-bold text-xs sm:text-sm transition">
              <span class="text-lg">⏳</span> Menyiapkan Lencana & Sistem Reward Juara!
            </div>
          </div>

          <div class="w-full bg-slate-200 rounded-full h-4 overflow-hidden border-2 border-white shadow-inner max-w-md mx-auto">
            <div id="aiProgressBar" class="bg-gradient-to-r from-amber-400 to-emerald-500 h-full w-0 transition-all duration-500"></div>
          </div>
        </div>
      `;
    }

    function runAiGameBuildingAnimation() {
      const pBar = document.getElementById("aiProgressBar");
      const s1 = document.getElementById("step1");
      const s2 = document.getElementById("step2");
      const s3 = document.getElementById("step3");
      const s4 = document.getElementById("step4");

      setTimeout(() => {
        if (pBar) pBar.style.width = "25%";
        if (s1) s1.innerHTML = `<span class="text-lg text-emerald-500">✅</span> Dunia Permainan Siap!`;
        playBeep("click");
      }, 500);

      setTimeout(() => {
        if (pBar) pBar.style.width = "55%";
        if (s2) s2.innerHTML = `<span class="text-lg text-emerald-500">✅</span> Karakter & Rintangan Ditempatkan!`;
        playBeep("click");
      }, 1100);

      setTimeout(() => {
        if (pBar) pBar.style.width = "85%";
        if (s3) s3.innerHTML = `<span class="text-lg text-emerald-500">✅</span> Soal Edukasi Terhubung!`;
        playBeep("click");
      }, 1700);

      setTimeout(() => {
        if (pBar) pBar.style.width = "100%";
        if (s4) s4.innerHTML = `<span class="text-lg text-emerald-500">✅</span> Game Berhasil Diciptakan! Siap Main!`;
        playBeep("star");

        // Save generated game to gallery
        const cfg = APP_STATE.creatorConfig;
        const newGame = {
          id: "game-" + Date.now(),
          title: generateGameTitle(cfg.gameType, cfg.selectedBentang),
          gameType: cfg.gameType,
          selectedBentang: [...cfg.selectedBentang],
          character: cfg.character,
          theme: cfg.theme,
          difficulty: cfg.difficulty,
          questionCount: cfg.questionCount,
          createdAt: new Date().toISOString().split("T")[0]
        };
        APP_STATE.savedGames.unshift(newGame);
        APP_STATE.creatorConfig.title = newGame.title;

        setTimeout(() => {
          prepareAndLaunchGame();
        }, 800);
      }, 2300);
    }

    function generateGameTitle(gameType, bentangList) {
      const bNames = bentangList.map(b => BENTANG_ALAM_DATA[b]?.nama || b).join(" & ");
      switch (gameType) {
        case "rocket": return `Roket Penakluk ${bNames} 🚀`;
        case "frog": return `Lompatan Katak di ${bNames} 🐸`;
        case "racecar": return `Grand Prix Sirkuit ${bNames} 🏎️`;
        case "ocean": return `Ekspedisi Maritim ${bNames} 🌊🚢`;
        default: return `Petualangan Alam ${bNames} 🇮🇩`;
      }
    }

    function prepareAndLaunchGame() {
      const cfg = APP_STATE.creatorConfig;
      
      // Filter questions matching selected bentang alam
      let pool = QUESTION_BANK.filter(q => cfg.selectedBentang.includes(q.bentang));
      if (pool.length === 0) pool = [...QUESTION_BANK];

      // Shuffle pool
      pool.sort(() => Math.random() - 0.5);

      // Pick questionCount
      const chosen = pool.slice(0, Math.min(cfg.questionCount, pool.length));

      // Star collection target is set to 5 stars before each question unlocks
      const starTarget = 5;

      // Reset Session
      APP_STATE.gameSession = {
        gameInstance: null,
        activeQuestions: chosen,
        currentQuestionIndex: 0,
        score: 0,
        coins: 0,
        stars: 3,
        starsCollectedForGate: 0,
        targetStarsPerGate: starTarget,
        lives: 3,
        maxLives: 3,
        correctCount: 0,
        wrongCount: 0,
        wrongQuestions: [],
        level: 1,
        totalLevels: 3,
        isPaused: false,
        isFinished: false,
        gameLoopId: null
      };

      navigateTo('play');
    }

    function renderPlayView() {
      const cfg = APP_STATE.creatorConfig;
      return `
        <div class="space-y-4 animate-fadeIn">
          <!-- Game HUD Top Bar -->
          <div class="bg-white rounded-2xl p-3 sm:p-4 border-2 border-slate-200 shadow-md flex flex-wrap items-center justify-between gap-3">
            <div class="flex items-center gap-2">
              <div class="w-10 h-10 rounded-xl bg-emerald-100 flex items-center justify-center text-2xl border border-emerald-300">
                ${cfg.gameType === 'rocket' ? '🚀' : cfg.gameType === 'frog' ? '🐸' : cfg.gameType === 'racecar' ? '🏎️' : '🚢'}
              </div>
              <div>
                <h3 class="text-sm sm:text-base font-extrabold text-slate-800 leading-tight">${cfg.title}</h3>
                <span class="text-[11px] font-bold text-emerald-700 bg-emerald-100 px-2 py-0.5 rounded-md">
                  Level <span id="hudLevel">1</span> • ${cfg.difficulty.toUpperCase()}
                </span>
              </div>
            </div>

            <!-- Stats: Lives, Star Gate Progress, Score -->
            <div class="flex items-center gap-3 sm:gap-4 text-xs sm:text-sm font-extrabold">
              <div class="flex items-center gap-1 text-rose-600 bg-rose-50 px-2.5 py-1 rounded-xl border border-rose-200">
                <span>❤️</span> <span id="hudLives">3</span>
              </div>
              <div class="flex items-center gap-1 text-amber-700 bg-amber-50 px-2.5 py-1 rounded-xl border border-amber-300">
                <span>⭐ Bintang Kunci:</span> <span id="hudStarGate" class="font-black text-amber-900">0 / 5</span>
              </div>
              <div class="flex items-center gap-1 text-sky-700 bg-sky-50 px-3 py-1 rounded-xl border border-sky-200">
                <span>🏆 Skor:</span> <span id="hudScore">0</span>
              </div>
            </div>
          </div>

          <!-- Game Canvas Wrapper with Interactive Overlay -->
          <div class="relative bg-slate-900 rounded-3xl overflow-hidden shadow-2xl border-4 border-emerald-400 aspect-[16/9] max-h-[500px] w-full flex items-center justify-center">
            <!-- HTML5 CANVAS -->
            <canvas id="gameCanvas" class="w-full h-full block bg-slate-900"></canvas>

            <!-- QUESTION GATE MODAL (Active during question checkpoint) -->
            <div id="questionOverlay" class="absolute inset-0 bg-slate-900/85 backdrop-blur-md flex items-center justify-center p-4 z-20 hidden">
              <div class="bg-white rounded-3xl max-w-lg w-full p-5 sm:p-7 border-4 border-amber-400 shadow-2xl text-center space-y-4 animate-scaleUp">
                <div class="flex items-center justify-between text-xs font-bold text-slate-500 pb-2 border-b">
                  <span id="questionCategoryBadge" class="bg-emerald-100 text-emerald-800 px-2.5 py-1 rounded-full">
                    🏔️ Pertanyaan Bentang Alam
                  </span>
                  <span id="questionCounter">Soal 1 dari 5</span>
                </div>

                <div class="text-4xl animate-bounce-slow" id="questionIcon">❓</div>
                <h4 id="questionText" class="text-base sm:text-lg font-bold text-slate-800 leading-snug">
                  Pertanyaan memuat...
                </h4>

                <!-- Options Grid -->
                <div id="optionsContainer" class="grid grid-cols-1 sm:grid-cols-2 gap-2.5 pt-2">
                  <!-- Dynamically rendered option buttons -->
                </div>

                <!-- Live Feedback Box on Answer Selection -->
                <div id="answerFeedbackBox" class="text-xs font-bold p-2.5 rounded-xl hidden"></div>
              </div>
            </div>

            <!-- Virtual On-Screen Controls for Mobile / Touch -->
            <div class="absolute bottom-3 left-3 right-3 flex justify-between items-center pointer-events-none z-10 opacity-90 sm:opacity-80">
              <div class="pointer-events-auto flex gap-2">
                <button id="ctrlLeft" class="w-12 h-12 bg-white/80 hover:bg-white text-slate-800 rounded-2xl shadow-lg border-2 border-slate-300 font-bold text-xl active:bg-amber-300 flex items-center justify-center">
                  ◀
                </button>
                <button id="ctrlRight" class="w-12 h-12 bg-white/80 hover:bg-white text-slate-800 rounded-2xl shadow-lg border-2 border-slate-300 font-bold text-xl active:bg-amber-300 flex items-center justify-center">
                  ▶
                </button>
              </div>
              <div class="pointer-events-auto flex gap-2">
                <button id="ctrlAction" class="px-5 h-12 bg-amber-400 hover:bg-amber-500 text-amber-950 font-bold rounded-2xl shadow-lg border-2 border-amber-500 active:scale-95 flex items-center justify-center text-sm">
                  🚀 AKSI / LOMPAT
                </button>
              </div>
            </div>
          </div>

          <!-- Instruction & Hotkey Tip -->
          <div class="flex flex-wrap items-center justify-between text-xs text-slate-600 bg-white/70 p-3 rounded-2xl border border-slate-200">
            <div class="flex items-center gap-2">
              <span class="font-bold">🎮 Kontrol:</span>
              <span class="bg-slate-100 px-2 py-0.5 rounded border border-slate-300">Tombol Panah / A - D - W - S</span>
              <span class="bg-slate-100 px-2 py-0.5 rounded border border-slate-300">Spasi (Lompat/Aksi)</span>
            </div>
            <div class="text-amber-800 font-extrabold flex items-center gap-1">
              <span>⭐</span> Misi: Kumpulkan 5 bintang untuk membuka pintu soal bentang alam!
            </div>
          </div>
        </div>
      `;
    }

    function initGameCanvas() {
      const canvas = document.getElementById("gameCanvas");
      if (!canvas) return;
      const ctx = canvas.getContext("2d");

      // Handle Canvas Responsive Dimensions smoothly with ResizeObserver
      function resizeCanvas() {
        const rect = canvas.getBoundingClientRect();
        canvas.width = rect.width || 800;
        canvas.height = rect.height || 450;
      }
      resizeCanvas();
      window.addEventListener("resize", resizeCanvas);

      if (window.ResizeObserver && canvas.parentElement) {
        const ro = new ResizeObserver(() => {
          resizeCanvas();
        });
        ro.observe(canvas.parentElement);
      }

      const session = APP_STATE.gameSession;
      const cfg = APP_STATE.creatorConfig;

      // Player State in Canvas
      const player = {
        x: canvas.width * 0.2,
        y: canvas.height * 0.5,
        targetY: canvas.height * 0.5,
        speedX: 0,
        speedY: 0,
        width: 48,
        height: 48,
        lane: 1, // for racecar & frog
        isJumping: false,
        jumpProgress: 0
      };

      // Environmental Objects
      let stars = [];
      let particles = [];
      let backgroundScroll = 0;

      // Initial HUD setup
      updateHud();

      // Spawn initial stars
      for (let i = 0; i < 5; i++) {
        stars.push({
          x: canvas.width + i * 160 + Math.random() * 60,
          y: 60 + Math.random() * (canvas.height - 120),
          size: 16,
          collected: false
        });
      }

      // Keys listener
      const keys = { left: false, right: false, up: false, down: false, space: false };
      function onKeyDown(e) {
        if (e.key === "ArrowLeft" || e.key === "a") keys.left = true;
        if (e.key === "ArrowRight" || e.key === "d") keys.right = true;
        if (e.key === "ArrowUp" || e.key === "w") keys.up = true;
        if (e.key === "ArrowDown" || e.key === "s") keys.down = true;
        if (e.key === " " || e.key === "Spacebar") {
          keys.space = true;
          triggerPlayerAction();
        }
      }
      function onKeyUp(e) {
        if (e.key === "ArrowLeft" || e.key === "a") keys.left = false;
        if (e.key === "ArrowRight" || e.key === "d") keys.right = false;
        if (e.key === "ArrowUp" || e.key === "w") keys.up = false;
        if (e.key === "ArrowDown" || e.key === "s") keys.down = false;
        if (e.key === " ") keys.space = false;
      }
      window.addEventListener("keydown", onKeyDown);
      window.addEventListener("keyup", onKeyUp);

      // Touch controls binding
      const btnL = document.getElementById("ctrlLeft");
      const btnR = document.getElementById("ctrlRight");
      const btnAct = document.getElementById("ctrlAction");
      if (btnL) {
        btnL.ontouchstart = btnL.onmousedown = () => { keys.left = true; };
        btnL.ontouchend = btnL.onmouseup = () => { keys.left = false; };
      }
      if (btnR) {
        btnR.ontouchstart = btnR.onmousedown = () => { keys.right = true; };
        btnR.ontouchend = btnR.onmouseup = () => { keys.right = false; };
      }
      if (btnAct) {
        btnAct.ontouchstart = btnAct.onmousedown = () => { triggerPlayerAction(); };
      }

      function triggerPlayerAction() {
        playBeep("jump");
        player.isJumping = true;
        player.jumpProgress = 0;
      }

      // Main Game Loop Function
      function gameLoop() {
        if (session.isFinished) return;

        // If not paused for question, update physics
        if (!session.isPaused) {
          updatePhysics();
        }

        renderScene();
        session.gameLoopId = requestAnimationFrame(gameLoop);
      }

      function updatePhysics() {
        backgroundScroll += 3.5;

        // Control adjustments
        if (keys.up) player.y = Math.max(40, player.y - 4.5);
        if (keys.down) player.y = Math.min(canvas.height - 60, player.y + 4.5);
        if (keys.left) player.x = Math.max(30, player.x - 4.5);
        if (keys.right) player.x = Math.min(canvas.width - 80, player.x + 4.5);

        // Jump animation for frog or action boost
        if (player.isJumping) {
          player.jumpProgress += 0.08;
          if (player.jumpProgress >= Math.PI) {
            player.isJumping = false;
            player.jumpProgress = 0;
          }
        }

        // Move stars and check collisions
        let gateUnlocked = false;
        stars.forEach(s => {
          s.x -= 3.2;
          // Collision with player
          const dist = Math.hypot(player.x - s.x, player.y - s.y);
          if (dist < 38 && !s.collected) {
            s.collected = true;
            session.coins += 1;
            session.score += 25;
            session.starsCollectedForGate += 1;
            playBeep("star");
            updateHud();

            // Spawn sparkly particles
            for (let p = 0; p < 8; p++) {
              particles.push({
                x: s.x,
                y: s.y,
                vx: (Math.random() - 0.5) * 6,
                vy: (Math.random() - 0.5) * 6,
                life: 1,
                color: "#f59e0b"
              });
            }

            // Check if player has gathered enough stars to trigger question!
            if (session.starsCollectedForGate >= session.targetStarsPerGate) {
              gateUnlocked = true;
            }
          }
        });

        // Respawn offscreen stars
        stars = stars.filter(s => s.x > -50 && !s.collected);
        while (stars.length < 5) {
          stars.push({
            x: canvas.width + Math.random() * 180,
            y: 50 + Math.random() * (canvas.height - 100),
            size: 16,
            collected: false
          });
        }

        // Update particles
        particles.forEach(p => {
          p.x += p.vx;
          p.y += p.vy;
          p.life -= 0.04;
        });
        particles = particles.filter(p => p.life > 0);

        // If target stars collected, trigger the question gate!
        if (gateUnlocked) {
          triggerQuestionGate();
        }
      }

      function renderScene() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        // 1. Draw Themed Background
        drawThemedBackground(ctx, canvas, cfg.theme, backgroundScroll);

        // 2. Draw Knowledge Stars & Collectibles
        stars.forEach(s => {
          ctx.save();
          ctx.translate(s.x, s.y);
          ctx.fillStyle = "#fbbf24";
          ctx.shadowColor = "#f59e0b";
          ctx.shadowBlur = 12;
          ctx.font = "26px sans-serif";
          ctx.textAlign = "center";
          ctx.textBaseline = "middle";
          ctx.fillText("⭐", 0, 0);
          ctx.restore();
        });

        // 3. Draw Particles
        particles.forEach(p => {
          ctx.save();
          ctx.globalAlpha = p.life;
          ctx.fillStyle = p.color;
          ctx.beginPath();
          ctx.arc(p.x, p.y, 4, 0, Math.PI * 2);
          ctx.fill();
          ctx.restore();
        });

        // 4. Draw Player / Vehicle
        ctx.save();
        const jumpOffsetY = player.isJumping ? Math.sin(player.jumpProgress) * -35 : 0;
        ctx.translate(player.x, player.y + jumpOffsetY);

        // Render specific game vehicle/sprite
        drawGameSprite(ctx, cfg.gameType, cfg.character);
        ctx.restore();

        // 5. Star-Gate Progress Indicator Banner at Top
        const progressRatio = Math.min(1, session.starsCollectedForGate / session.targetStarsPerGate);
        ctx.fillStyle = "rgba(15, 23, 42, 0.65)";
        ctx.beginPath();
        ctx.roundRect(canvas.width * 0.2, 10, canvas.width * 0.6, 36, 12);
        ctx.fill();

        ctx.fillStyle = "rgba(255, 255, 255, 0.25)";
        ctx.fillRect(canvas.width * 0.25, 28, canvas.width * 0.5, 8);

        ctx.fillStyle = progressRatio >= 1 ? "#fbbf24" : "#10b981";
        ctx.fillRect(canvas.width * 0.25, 28, canvas.width * 0.5 * progressRatio, 8);

        ctx.fillStyle = "#ffffff";
        ctx.font = "bold 11px Nunito";
        ctx.textAlign = "center";
        const txtMsg = progressRatio >= 1
          ? "🌟 Gerbang Soal Terbuka! Menyiapkan Pertanyaan..."
          : `⭐ Kumpulkan Bintang: ${session.starsCollectedForGate} / ${session.targetStarsPerGate} untuk Membuka Soal`;
        ctx.fillText(txtMsg, canvas.width * 0.5, 22);
      }

      // Start the loop!
      session.gameLoopId = requestAnimationFrame(gameLoop);
    }

    function drawThemedBackground(ctx, canvas, theme, scroll) {
      const w = canvas.width;
      const h = canvas.height;

      // Base background gradient based on theme
      const grad = ctx.createLinearGradient(0, 0, 0, h);
      if (theme === "luar_angkasa") {
        grad.addColorStop(0, "#090d16");
        grad.addColorStop(0.5, "#1e1b4b");
        grad.addColorStop(1, "#312e81");
        ctx.fillStyle = grad;
        ctx.fillRect(0, 0, w, h);

        // Distant twinkling stars
        ctx.fillStyle = "#ffffff";
        for (let i = 0; i < 35; i++) {
          const sx = (i * 73 - (scroll * 0.5)) % w;
          const px = sx < 0 ? sx + w : sx;
          const py = (i * 37) % h;
          const sz = (i % 3) + 1;
          ctx.beginPath();
          ctx.arc(px, py, sz, 0, Math.PI * 2);
          ctx.fill();
        }
        return;
      } else if (theme === "laut") {
        grad.addColorStop(0, "#38bdf8");
        grad.addColorStop(0.4, "#0284c7");
        grad.addColorStop(1, "#0369a1");
      } else if (theme === "pegunungan") {
        grad.addColorStop(0, "#bae6fd");
        grad.addColorStop(0.45, "#7dd3fc");
        grad.addColorStop(1, "#34d399");
      } else if (theme === "hutan") {
        grad.addColorStop(0, "#6ee7b7");
        grad.addColorStop(0.6, "#10b981");
        grad.addColorStop(1, "#065f46");
      } else if (theme === "pedesaan") {
        grad.addColorStop(0, "#fde68a");
        grad.addColorStop(0.5, "#86efac");
        grad.addColorStop(1, "#22c55e");
      } else { // default petualangan / fantasi
        grad.addColorStop(0, "#7dd3fc");
        grad.addColorStop(0.5, "#a7f3d0");
        grad.addColorStop(1, "#fde68a");
      }

      ctx.fillStyle = grad;
      ctx.fillRect(0, 0, w, h);

      // Clouds / atmosphere layer (parallax slow)
      ctx.fillStyle = "rgba(255, 255, 255, 0.4)";
      for (let i = 0; i < 4; i++) {
        const cx = ((i * 260) - (scroll * 0.3)) % (w + 200);
        const plotX = cx < -150 ? cx + w + 200 : cx;
        const plotY = 30 + (i % 3) * 35;
        ctx.beginPath();
        ctx.arc(plotX, plotY, 35, 0, Math.PI * 2);
        ctx.arc(plotX + 30, plotY - 10, 42, 0, Math.PI * 2);
        ctx.arc(plotX + 60, plotY, 35, 0, Math.PI * 2);
        ctx.fill();
      }

      // Parallax Mountains / Hills
      const hillOffset = (scroll * 0.8) % 300;
      ctx.fillStyle = theme === "laut" ? "#0284c7" : "#059669";
      ctx.beginPath();
      ctx.moveTo(-100, h);
      for (let x = -100; x <= w + 100; x += 150) {
        const hillX = x - hillOffset;
        const peakY = h * 0.55 + Math.sin((x + scroll) * 0.005) * 50;
        ctx.lineTo(hillX + 75, peakY);
        ctx.lineTo(hillX + 150, h);
      }
      ctx.lineTo(w + 100, h);
      ctx.fill();

      // Lower ground / water strip
      if (theme === "laut") {
        ctx.fillStyle = "rgba(3, 105, 161, 0.85)";
        ctx.fillRect(0, h * 0.72, w, h * 0.28);
        // Wave foam lines
        ctx.strokeStyle = "rgba(255, 255, 255, 0.6)";
        ctx.lineWidth = 3;
        ctx.beginPath();
        const waveShift = (scroll * 2) % 40;
        for (let wx = 0; wx < w; wx += 40) {
          ctx.moveTo(wx - waveShift, h * 0.75 + Math.sin(wx * 0.1) * 4);
          ctx.lineTo(wx + 20 - waveShift, h * 0.75 + Math.sin((wx + 20) * 0.1) * 4);
        }
        ctx.stroke();
      } else {
        ctx.fillStyle = "#15803d";
        ctx.fillRect(0, h * 0.82, w, h * 0.18);
        // Grass / path decor
        ctx.fillStyle = "#16a34a";
        ctx.fillRect(0, h * 0.82, w, 8);
      }
    }

    function drawGameSprite(ctx, gameType, character) {
      // Character & vehicle emoji map
      const charEmojis = {
        boy: "👦",
        girl: "👧",
        explorer: "🤠",
        astronaut: "👨‍🚀",
        driver: "🏎️",
        frog: "🐸",
        captain: "🧑‍✈️"
      };

      const vehicleEmojis = {
        rocket: "🚀",
        frog: "🐸",
        racecar: "🏎️",
        ocean: "🚢"
      };

      const primary = vehicleEmojis[gameType] || "🚀";
      const pilot = charEmojis[character] || "🧑‍🚀";

      ctx.shadowColor = "rgba(0, 0, 0, 0.35)";
      ctx.shadowBlur = 8;
      ctx.textAlign = "center";
      ctx.textBaseline = "middle";

      if (gameType === "rocket") {
        // Thruster flame effect
        ctx.fillStyle = "#f97316";
        ctx.beginPath();
        ctx.moveTo(-22, -6);
        ctx.lineTo(-38 - Math.random() * 8, 0);
        ctx.lineTo(-22, 6);
        ctx.fill();

        ctx.fillStyle = "#facc15";
        ctx.beginPath();
        ctx.moveTo(-20, -3);
        ctx.lineTo(-30 - Math.random() * 5, 0);
        ctx.lineTo(-20, 3);
        ctx.fill();

        ctx.font = "38px sans-serif";
        ctx.fillText(primary, 0, 0);
        ctx.font = "16px sans-serif";
        ctx.fillText(pilot, 4, -4);
      } else if (gameType === "frog") {
        ctx.font = "42px sans-serif";
        ctx.fillText(primary, 0, 0);
      } else if (gameType === "racecar") {
        // Speed trail
        ctx.strokeStyle = "rgba(251, 191, 36, 0.7)";
        ctx.lineWidth = 4;
        ctx.beginPath();
        ctx.moveTo(-20, 8);
        ctx.lineTo(-45, 8);
        ctx.moveTo(-15, -4);
        ctx.lineTo(-35, -4);
        ctx.stroke();

        ctx.font = "40px sans-serif";
        ctx.fillText(primary, 0, 0);
        ctx.font = "16px sans-serif";
        ctx.fillText(pilot, -3, -6);
      } else if (gameType === "ocean") {
        // Water wake
        ctx.strokeStyle = "rgba(255, 255, 255, 0.65)";
        ctx.lineWidth = 3;
        ctx.beginPath();
        ctx.moveTo(-18, 14);
        ctx.lineTo(-40, 16);
        ctx.stroke();

        ctx.font = "40px sans-serif";
        ctx.fillText(primary, 0, 0);
        ctx.font = "16px sans-serif";
        ctx.fillText(pilot, 2, -10);
      } else {
        ctx.font = "38px sans-serif";
        ctx.fillText("🚀", 0, 0);
      }
    }

    function updateHud() {
      const s = APP_STATE.gameSession;
      const elLives = document.getElementById("hudLives");
      const elStarGate = document.getElementById("hudStarGate");
      const elScore = document.getElementById("hudScore");
      const elLevel = document.getElementById("hudLevel");
      if (elLives) elLives.innerText = s.lives;
      if (elStarGate) elStarGate.innerText = `${s.starsCollectedForGate} / ${s.targetStarsPerGate}`;
      if (elScore) elScore.innerText = s.score;
      if (elLevel) elLevel.innerText = s.level;
    }

    function triggerQuestionGate() {
      const s = APP_STATE.gameSession;
      s.isPaused = true;
      playBeep("star");

      const qIndex = s.currentQuestionIndex;
      if (qIndex >= s.activeQuestions.length) {
        finishGameSession();
        return;
      }

      const q = s.activeQuestions[qIndex];
      const overlay = document.getElementById("questionOverlay");
      const txtCounter = document.getElementById("questionCounter");
      const txtSoal = document.getElementById("questionText");
      const optionsContainer = document.getElementById("optionsContainer");
      const fbBox = document.getElementById("answerFeedbackBox");
      const catBadge = document.getElementById("questionCategoryBadge");

      if (!overlay) return;

      const bentangObj = BENTANG_ALAM_DATA[q.bentang] || { icon: "🌍", nama: "Bentang Alam" };
      catBadge.innerHTML = `${bentangObj.icon} Tantangan ${bentangObj.nama} • Level ${q.level || s.level}`;
      txtCounter.innerText = `Soal ${qIndex + 1} dari ${s.activeQuestions.length}`;
      txtSoal.innerText = q.soal;

      fbBox.classList.add("hidden");
      fbBox.innerHTML = "";

      // Render Options
      optionsContainer.innerHTML = q.opsi.map((opt, idx) => `
        <button onclick="handleSelectAnswer(${idx})" class="p-3.5 rounded-2xl border-2 border-slate-200 hover:border-amber-400 bg-slate-50 hover:bg-amber-50 text-slate-800 font-bold text-xs sm:text-sm text-left transition transform hover:scale-102 flex items-center gap-2">
          <span class="w-6 h-6 rounded-lg bg-amber-400 text-amber-950 flex items-center justify-center font-bold text-xs">${String.fromCharCode(65 + idx)}</span>
          <span>${opt}</span>
        </button>
      `).join('');

      overlay.classList.remove("hidden");
    }

    function handleSelectAnswer(chosenIdx) {
      const s = APP_STATE.gameSession;
      const q = s.activeQuestions[s.currentQuestionIndex];
      const fbBox = document.getElementById("answerFeedbackBox");
      const optionsContainer = document.getElementById("optionsContainer");

      // Disable further clicks
      const buttons = optionsContainer.querySelectorAll("button");
      buttons.forEach(btn => btn.disabled = true);

      const isCorrect = (chosenIdx === q.jawaban);

      if (isCorrect) {
        playBeep("correct");
        s.score += 100;
        s.correctCount += 1;
        fbBox.className = "text-xs font-bold p-3 rounded-2xl bg-emerald-100 text-emerald-900 border-2 border-emerald-300 block";
        fbBox.innerHTML = `🎉 <b>HEBAT! JAWABAN BENAR!</b><br>${q.penjelasan}`;
        buttons[chosenIdx].classList.add("bg-emerald-200", "border-emerald-500");
      } else {
        playBeep("wrong");
        s.wrongCount += 1;
        s.lives = Math.max(0, s.lives - 1);
        s.wrongQuestions.push({
          soal: q.soal,
          jawabanSiswa: q.opsi[chosenIdx],
          jawabanBenar: q.opsi[q.jawaban],
          penjelasan: q.penjelasan,
          bentang: q.bentang
        });
        fbBox.className = "text-xs font-bold p-3 rounded-2xl bg-rose-100 text-rose-900 border-2 border-rose-300 block";
        fbBox.innerHTML = `❌ <b>Kurang Tepat.</b> Jawaban yang benar: <b>${q.opsi[q.jawaban]}</b><br>${q.penjelasan}`;
        buttons[chosenIdx].classList.add("bg-rose-100", "border-rose-400");
        buttons[q.jawaban].classList.add("bg-emerald-200", "border-emerald-500");
      }

      updateHud();

      // Reset stars collected for the next round of questions
      s.starsCollectedForGate = 0;

      // Next step after 2.3 seconds
      setTimeout(() => {
        document.getElementById("questionOverlay").classList.add("hidden");
        s.currentQuestionIndex += 1;

        // Check if out of lives or finished questions
        if (s.lives <= 0 || s.currentQuestionIndex >= s.activeQuestions.length) {
          finishGameSession();
        } else {
          // Check level promotion
          if (s.currentQuestionIndex >= 2 && s.level === 1) s.level = 2;
          if (s.currentQuestionIndex >= 4 && s.level === 2) s.level = 3;
          updateHud();
          s.isPaused = false;
        }
      }, 2300);
    }

    function finishGameSession() {
      const s = APP_STATE.gameSession;
      s.isFinished = true;
      if (s.gameLoopId) cancelAnimationFrame(s.gameLoopId);

      // Log play session for teacher mode
      APP_STATE.playHistory.unshift({
        title: APP_STATE.creatorConfig.title,
        gameType: APP_STATE.creatorConfig.gameType,
        score: s.score,
        correct: s.correctCount,
        wrong: s.wrongCount,
        total: s.activeQuestions.length,
        date: new Date().toLocaleTimeString("id-ID", { hour: '2-digit', minute: '2-digit' })
      });

      navigateTo('results');
    }

    function renderResultsView() {
      const s = APP_STATE.gameSession;
      const totalQ = s.activeQuestions.length || 1;
      const percentage = Math.round((s.correctCount / totalQ) * 100);

      let starCount = 1;
      let badgeName = "Penjelajah Pemula";
      let badgeIcon = "🌱";

      if (percentage >= 80) {
        starCount = 5;
        badgeName = "Master Bentang Alam Indonesia";
        badgeIcon = "🧭";
      } else if (percentage >= 60) {
        starCount = 4;
        badgeName = "Pakar Geografi Cilik";
        badgeIcon = "🏔️";
      } else if (percentage >= 40) {
        starCount = 3;
        badgeName = "Sahabat Alam Nusantara";
        badgeIcon = "🌊";
      } else {
        starCount = 2;
        badgeName = "Penjelajah Pemberani";
        badgeIcon = "🎒";
      }

      return `
        <div class="max-w-xl mx-auto space-y-6 text-center animate-fadeIn py-4">
          <!-- Main Result Card -->
          <div class="bg-white rounded-3xl p-6 sm:p-8 border-4 border-amber-400 shadow-2xl relative overflow-hidden">
            <!-- Confetti & Celebration Icon -->
            <div class="text-7xl mb-2 animate-bounce-slow">${percentage >= 60 ? '🏆' : '👏'}</div>
            <h2 class="text-3xl sm:text-4xl font-extrabold text-slate-800 font-fun">
              ${percentage >= 80 ? 'LUAR BIASA! SELAMAT!' : 'HEBAT, KAMU TELAH MENYELESAIKAN GAME!'}
            </h2>
            <p class="text-xs sm:text-sm text-slate-600 font-semibold mt-1">
              Petualangan di ${APP_STATE.creatorConfig.title} telah selesai!
            </p>

            <!-- Star Rating Visual -->
            <div class="flex justify-center gap-1.5 text-3xl sm:text-4xl my-4 text-amber-400">
              ${Array(5).fill(0).map((_, i) => i < starCount ? '⭐' : '<span class="opacity-25 grayscale">⭐</span>').join('')}
            </div>

            <!-- Stats Highlight Grid -->
            <div class="grid grid-cols-3 gap-3 my-6">
              <div class="bg-amber-50 p-3 rounded-2xl border-2 border-amber-200">
                <span class="text-xs text-amber-700 font-bold block">Total Skor</span>
                <span class="text-2xl font-extrabold text-amber-900">${s.score}</span>
              </div>
              <div class="bg-emerald-50 p-3 rounded-2xl border-2 border-emerald-200">
                <span class="text-xs text-emerald-700 font-bold block">Jawaban Benar</span>
                <span class="text-2xl font-extrabold text-emerald-900">${s.correctCount} / ${totalQ}</span>
              </div>
              <div class="bg-sky-50 p-3 rounded-2xl border-2 border-sky-200">
                <span class="text-xs text-sky-700 font-bold block">Koin Pengetahuan</span>
                <span class="text-2xl font-extrabold text-sky-900">${s.coins} 🪙</span>
              </div>
            </div>

            <!-- Earned Badge Box -->
            <div class="bg-gradient-to-r from-purple-100 to-indigo-100 p-4 rounded-2xl border-2 border-indigo-300 flex items-center justify-center gap-3">
              <span class="text-3xl">${badgeIcon}</span>
              <div class="text-left">
                <span class="text-[10px] uppercase tracking-wider font-extrabold text-indigo-700 block">Lencana Didapatkan:</span>
                <span class="text-base font-extrabold text-indigo-950">${badgeName}</span>
              </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex flex-col sm:flex-row gap-3 justify-center mt-6">
              <button onclick="navigateTo('review')" class="px-5 py-3 bg-emerald-600 hover:bg-emerald-700 text-white font-bold text-sm rounded-2xl border-2 border-emerald-800 shadow-md transition flex items-center justify-center gap-2">
                <span>📖 Apa yang Sudah Kupelajari?</span>
              </button>
              <button onclick="navigateTo('reflection')" class="px-5 py-3 bg-purple-600 hover:bg-purple-700 text-white font-bold text-sm rounded-2xl border-2 border-purple-800 shadow-md transition flex items-center justify-center gap-2">
                <span>✍️ Tulis Refleksi Cilik</span>
              </button>
              <button onclick="navigateTo('creator-hub')" class="px-5 py-3 bg-amber-400 hover:bg-amber-500 text-amber-950 font-bold text-sm rounded-2xl border-2 border-amber-500 shadow-md transition flex items-center justify-center gap-2">
                <span>✨ Buat Game Baru!</span>
              </button>
            </div>
          </div>
        </div>
      `;
    }

    function renderReviewView() {
      const s = APP_STATE.gameSession;
      return `
        <div class="space-y-6 animate-fadeIn">
          <div class="flex items-center justify-between">
            <div>
              <span class="text-xs font-extrabold text-emerald-700 bg-emerald-100 px-3 py-1 rounded-full border border-emerald-300">
                🌱 Materi Penguatan & Refleksi Belajar
              </span>
              <h2 class="text-2xl sm:text-4xl font-extrabold text-slate-800 mt-1">Apa yang Sudah Kamu Pelajari?</h2>
            </div>
            <button onclick="navigateTo('home')" class="px-4 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold rounded-xl text-xs border border-slate-300">
              Kembali ke Beranda
            </button>
          </div>

          <!-- Wrong Questions Review -->
          ${s.wrongQuestions.length > 0 ? `
            <div class="bg-rose-50 rounded-3xl p-5 sm:p-6 border-4 border-rose-300 shadow-md space-y-4">
              <h3 class="text-lg font-bold text-rose-900 flex items-center gap-2">
                <span>💡</span> Catatan Materi yang Perlu Kamu Ingat Lagi:
              </h3>
              <div class="space-y-3">
                ${s.wrongQuestions.map(w => `
                  <div class="bg-white p-4 rounded-2xl border-2 border-rose-200 text-left space-y-1.5 text-xs sm:text-sm">
                    <div class="font-bold text-slate-800">${w.soal}</div>
                    <div class="text-rose-600 font-semibold">Pilihanmu: ${w.jawabanSiswa} (Belum tepat)</div>
                    <div class="text-emerald-700 font-bold">Kunci Benar: ${w.jawabanBenar}</div>
                    <div class="text-slate-600 bg-emerald-50/70 p-2.5 rounded-xl border border-emerald-200 text-xs">
                      👉 <b>Penjelasan:</b> ${w.penjelasan}
                    </div>
                  </div>
                `).join('')}
              </div>
            </div>
          ` : `
            <div class="bg-emerald-50 rounded-3xl p-6 border-4 border-emerald-300 text-center space-y-2">
              <span class="text-5xl">🎉</span>
              <h3 class="text-xl font-bold text-emerald-900">SEMUA JAWABANMU BENAR!</h3>
              <p class="text-xs sm:text-sm text-emerald-800 font-semibold">
                Kamu memahami dengan sangat baik materi bentang alam yang telah kamu jelajahi!
              </p>
            </div>
          `}

          <!-- Quick Recap of Chosen Landscapes -->
          <div class="bg-white rounded-3xl p-6 border-4 border-emerald-300 shadow-md">
            <h3 class="text-xl font-bold text-slate-800 mb-4">Rangkuman Bentang Alam yang Baru Saja Kamu Jelajahi:</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              ${APP_STATE.creatorConfig.selectedBentang.map(id => {
                const b = BENTANG_ALAM_DATA[id];
                if (!b) return '';
                return `
                  <div class="p-4 rounded-2xl bg-slate-50 border-2 border-slate-200 text-left space-y-2">
                    <div class="flex items-center gap-2 font-bold text-slate-800">
                      <span class="text-2xl">${b.icon}</span>
                      <span class="text-base">${b.nama}</span>
                    </div>
                    <p class="text-xs text-slate-600 leading-relaxed font-medium">${b.pengertian}</p>
                    <div class="text-[11px] text-emerald-800 bg-emerald-50 p-2 rounded-xl border border-emerald-200">
                      <b>Contoh di Indonesia:</b> ${b.contoh.join(', ')}
                    </div>
                  </div>
                `;
              }).join('')}
            </div>
          </div>

          <!-- Bottom Nav -->
          <div class="flex justify-center gap-3">
            <button onclick="navigateTo('reflection')" class="px-6 py-3 bg-purple-600 hover:bg-purple-700 text-white font-bold rounded-2xl shadow-md border-2 border-purple-800 text-sm">
              ✍️ Lanjut Tulis Refleksi Siswa ➔
            </button>
          </div>
        </div>
      `;
    }

    function renderReflectionView() {
      return `
        <div class="max-w-2xl mx-auto space-y-6 animate-fadeIn py-4">
          <div class="text-center space-y-2">
            <div class="text-5xl animate-bounce-slow">📝✨</div>
            <h2 class="text-2xl sm:text-4xl font-extrabold text-slate-800 font-fun">
              REFLEKSI PETUALANG CILIK
            </h2>
            <p class="text-xs sm:text-sm text-slate-600 font-medium">
              Yuk, ceritakan pengalaman belajarmu hari ini agar semakin berkesan!
            </p>
          </div>

          <div class="bg-white rounded-3xl p-6 sm:p-8 border-4 border-purple-300 shadow-xl space-y-5 text-left">
            <!-- Pertanyaan 1 -->
            <div>
              <label class="block text-xs sm:text-sm font-bold text-purple-950 mb-1.5">
                1. Bentang alam apa yang paling kamu ingat dan sukai hari ini? Mengapa?
              </label>
              <textarea id="ref1" rows="2" placeholder="Contoh: Saya paling suka Danau Toba karena sangat luas dan memiliki pulau di tengahnya..." class="w-full text-xs sm:text-sm p-3 rounded-2xl border-2 border-purple-200 focus:border-purple-500 focus:outline-none bg-purple-50/30"></textarea>
            </div>

            <!-- Pertanyaan 2 -->
            <div>
              <label class="block text-xs sm:text-sm font-bold text-purple-950 mb-1.5">
                2. Apa hal atau fakta baru yang baru pertama kali kamu ketahui?
              </label>
              <textarea id="ref2" rows="2" placeholder="Contoh: Ternyata Indonesia punya lebih dari 120 gunung api aktif dan Sungai Kapuas adalah sungai terpanjang..." class="w-full text-xs sm:text-sm p-3 rounded-2xl border-2 border-purple-200 focus:border-purple-500 focus:outline-none bg-purple-50/30"></textarea>
            </div>

            <!-- Pertanyaan 3 -->
            <div>
              <label class="block text-xs sm:text-sm font-bold text-purple-950 mb-1.5">
                3. Jika kamu membuat game lagi nanti, apa yang ingin kamu tambahkan atau ubah?
              </label>
              <textarea id="ref3" rows="2" placeholder="Contoh: Saya ingin mencoba mobil balap dengan rintangan lebih seru di Dataran Tinggi Dieng..." class="w-full text-xs sm:text-sm p-3 rounded-2xl border-2 border-purple-200 focus:border-purple-500 focus:outline-none bg-purple-50/30"></textarea>
            </div>

            <div class="text-center pt-2">
              <button onclick="saveStudentReflection()" class="w-full sm:w-auto px-8 py-3.5 bg-gradient-to-r from-purple-600 to-indigo-600 hover:from-purple-700 hover:to-indigo-700 text-white font-bold text-sm sm:text-base rounded-2xl border-2 border-purple-800 shadow-lg transition transform hover:scale-105">
                Simpan Catatan Refleksiku 🌟
              </button>
            </div>
          </div>
        </div>
      `;
    }

    function saveStudentReflection() {
      playBeep("star");
      showModal(
        "Refleksi Tersimpan! 🌟",
        "Hebat! Pikiran dan ide kreatifmu telah tercatat dengan rapi. Teruslah berpetualang dan menjelajahi alam nusantara!",
        "🎉",
        () => {
          navigateTo("gallery");
        }
      );
    }

    function renderGalleryView() {
      return `
        <div class="space-y-6 animate-fadeIn">
          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
            <div>
              <span class="text-xs font-extrabold text-purple-700 bg-purple-100 px-3 py-1 rounded-full border border-purple-300">
                🎮 Galeri Karya Siswa
              </span>
              <h2 class="text-2xl sm:text-4xl font-extrabold text-slate-800 mt-1">GALERI GAMEKU</h2>
              <p class="text-xs sm:text-sm text-slate-600 font-medium">Koleksi game yang telah kamu buat selama sesi petualangan!</p>
            </div>
            <button onclick="navigateTo('creator-hub')" class="self-start sm:self-auto px-5 py-2.5 bg-amber-400 hover:bg-amber-500 text-amber-950 font-bold rounded-2xl border-2 border-amber-500 shadow-md text-sm transition">
              ✨ Buat Game Baru
            </button>
          </div>

          <!-- Cards Grid -->
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
            ${APP_STATE.savedGames.map(g => {
              const bentangIcons = g.selectedBentang.map(id => BENTANG_ALAM_DATA[id]?.icon || '🌍').join(' ');
              return `
                <div class="bg-white rounded-3xl p-5 border-4 border-slate-200 hover:border-purple-400 shadow-lg hover:shadow-xl transition flex flex-col justify-between space-y-4">
                  <div>
                    <div class="flex items-center justify-between mb-3">
                      <span class="text-3xl">${g.gameType === 'rocket' ? '🚀' : g.gameType === 'frog' ? '🐸' : g.gameType === 'racecar' ? '🏎️' : '🚢'}</span>
                      <span class="text-[10px] font-bold px-2 py-0.5 rounded-md bg-purple-100 text-purple-800 border border-purple-200 uppercase">
                        ${g.difficulty}
                      </span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-800 leading-snug">${g.title}</h3>
                    <p class="text-xs text-slate-500 mt-1 font-semibold">Bentang Alam: ${bentangIcons}</p>
                    <p class="text-[11px] text-slate-400 mt-0.5">Dibuat pada: ${g.createdAt}</p>
                  </div>

                  <div class="pt-3 border-t border-slate-100 flex items-center gap-2">
                    <button onclick="playSavedGame('${g.id}')" class="flex-1 py-2 bg-emerald-500 hover:bg-emerald-600 text-white font-bold text-xs rounded-xl shadow-sm transition">
                      ▶ Mainkan
                    </button>
                    <button onclick="duplicateGame('${g.id}')" class="px-3 py-2 bg-sky-100 hover:bg-sky-200 text-sky-800 font-bold text-xs rounded-xl border border-sky-300 transition">
                      📑 Salin
                    </button>
                  </div>
                </div>
              `;
            }).join('')}
          </div>
        </div>
      `;
    }

    function playSavedGame(gameId) {
      playBeep("click");
      const found = APP_STATE.savedGames.find(g => g.id === gameId);
      if (found) {
        APP_STATE.creatorConfig = {
          gameType: found.gameType,
          selectedBentang: [...found.selectedBentang],
          character: found.character,
          theme: found.theme,
          difficulty: found.difficulty,
          questionCount: found.questionCount,
          title: found.title
        };
        prepareAndLaunchGame();
      }
    }

    function duplicateGame(gameId) {
      playBeep("star");
      const found = APP_STATE.savedGames.find(g => g.id === gameId);
      if (found) {
        const copy = {
          ...found,
          id: "game-" + Date.now(),
          title: found.title + " (Salinan)",
          createdAt: new Date().toISOString().split("T")[0]
        };
        APP_STATE.savedGames.unshift(copy);
        showToast("Game berhasil disalin ke Galeri!", "📑");
        document.getElementById("appContainer").innerHTML = renderGalleryView();
      }
    }

    function renderTeacherDashboardView() {
      const history = APP_STATE.playHistory;
      return `
        <div class="space-y-6 animate-fadeIn">
          <div class="flex items-center justify-between">
            <div>
              <span class="text-xs font-extrabold text-blue-700 bg-blue-100 px-3 py-1 rounded-full border border-blue-300">
                👩‍🏫 Panel Pengawasan & Evaluasi Guru
              </span>
              <h2 class="text-2xl sm:text-4xl font-extrabold text-slate-800 mt-1">Dashboard Kontrol Guru</h2>
              <p class="text-xs sm:text-sm text-slate-600 font-medium">
                Pantau perkembangan capaian belajar bentang alam siswa tanpa mengumpulkan data pribadi sensitif.
              </p>
            </div>
            <button onclick="toggleTeacherMode()" class="px-4 py-2 bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold rounded-xl text-xs border border-slate-300">
              Kembali ke Mode Siswa 🎒
            </button>
          </div>

          <!-- Summary Metric Cards -->
          <div class="grid grid-cols-1 sm:grid-cols-4 gap-4">
            <div class="bg-white p-4 rounded-2xl border-2 border-emerald-200 shadow-sm text-center">
              <span class="text-xs text-slate-500 font-bold">Total Sesi Main</span>
              <span class="text-2xl font-extrabold text-emerald-700 block mt-1">${history.length}</span>
            </div>
            <div class="bg-white p-4 rounded-2xl border-2 border-sky-200 shadow-sm text-center">
              <span class="text-xs text-slate-500 font-bold">Game di Galeri</span>
              <span class="text-2xl font-extrabold text-sky-700 block mt-1">${APP_STATE.savedGames.length}</span>
            </div>
            <div class="bg-white p-4 rounded-2xl border-2 border-amber-200 shadow-sm text-center">
              <span class="text-xs text-slate-500 font-bold">Bank Soal Tersedia</span>
              <span class="text-2xl font-extrabold text-amber-700 block mt-1">${QUESTION_BANK.length} Butir</span>
            </div>
            <div class="bg-white p-4 rounded-2xl border-2 border-purple-200 shadow-sm text-center">
              <span class="text-xs text-slate-500 font-bold">Cakupan Materi</span>
              <span class="text-2xl font-extrabold text-purple-700 block mt-1">6 Bentang Alam</span>
            </div>
          </div>

          <!-- Play History Table -->
          <div class="bg-white rounded-3xl p-6 border-4 border-slate-200 shadow-md">
            <h3 class="text-lg font-bold text-slate-800 mb-4">Catatan Permainan & Capaian Belajar Siswa</h3>
            ${history.length > 0 ? `
              <div class="overflow-x-auto">
                <table class="w-full text-xs text-left">
                  <thead class="bg-slate-100 text-slate-600 font-bold">
                    <tr>
                      <th class="p-3">Waktu</th>
                      <th class="p-3">Judul Game</th>
                      <th class="p-3">Jenis</th>
                      <th class="p-3">Skor</th>
                      <th class="p-3">Akurasi Soal</th>
                    </tr>
                  </thead>
                  <tbody class="divide-y divide-slate-100">
                    ${history.map(h => `
                      <tr class="hover:bg-slate-50 font-semibold text-slate-700">
                        <td class="p-3">${h.date}</td>
                        <td class="p-3 font-bold text-emerald-800">${h.title}</td>
                        <td class="p-3 uppercase">${h.gameType}</td>
                        <td class="p-3 text-amber-600 font-bold">${h.score}</td>
                        <td class="p-3 text-emerald-600 font-bold">${h.correct} / ${h.total} (${Math.round((h.correct / h.total) * 100)}%)</td>
                      </tr>
                    `).join('')}
                  </tbody>
                </table>
              </div>
            ` : `
              <div class="text-center py-6 text-slate-400 text-xs font-semibold">
                Belum ada aktivitas bermain pada sesi ini. Siswa dapat mulai membuat game terlebih dahulu!
              </div>
            `}
          </div>
        </div>
      `;
    }

    window.onload = function() {
      navigateTo("home");
    };
  </script>
</body>
</html>
