<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gemebite - Sistem Pesanan & Kasir Digital</title>
  
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts Inter -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <!-- QRCode.js Library -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
  <!-- html2canvas Library -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              brown: '#4A2E1F',
              dark: '#2D1B12',
              amber: '#D97706',
              cream: '#FFFBEB',
              soft: '#F5EBE1',
              green: '#059669',
              red: '#DC2626'
            }
          },
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
          }
        }
      }
    }
  </script>

  <style>
    /* Styling Khusus Struk Cetak / Print Thermal */
    @media print {
      body * {
        visibility: hidden;
      }
      #printableReceipt, #printableReceipt * {
        visibility: visible;
      }
      #printableReceipt {
        position: absolute;
        left: 0;
        top: 0;
        width: 80mm;
        padding: 10px;
        font-family: 'Courier New', Courier, monospace;
        color: #000;
        background: #fff;
      }
      .no-print {
        display: none !important;
      }
    }

    /* Smooth Scrolling & Custom Scrollbar */
    html {
      scroll-behavior: smooth;
    }
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #F5EBE1;
    }
    ::-webkit-scrollbar-thumb {
      background: #4A2E1F;
      border-radius: 4px;
    }
  </style>
</head>
<body class="bg-brand-cream text-gray-800 font-sans min-h-screen flex flex-col justify-between selection:bg-brand-amber selection:text-white">

  <!-- ================= HEADER / TOPBAR ================= -->
  <header class="bg-brand-brown text-white sticky top-0 z-40 shadow-lg border-b border-amber-900/40">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
      
      <!-- Logo & Branding -->
      <div class="flex items-center space-x-3 cursor-pointer" onclick="switchView('customer')">
        <div class="w-10 h-10 rounded-xl bg-brand-amber text-white flex items-center justify-center font-bold text-xl shadow-md">
          ☕
        </div>
        <div>
          <h1 class="font-bold text-lg leading-tight tracking-wide text-brand-cream">Gemebite</h1>
          <p class="text-xs text-amber-200/80">Cita Rasa Otentik & Sederhana</p>
        </div>
      </div>

      <!-- Mode Switcher & Quick Navigation -->
      <div class="flex items-center space-x-2 sm:space-x-3">
        <button id="navCustomerBtn" onclick="switchView('customer')" 
          class="px-3 py-1.5 rounded-lg text-xs sm:text-sm font-medium transition duration-200 bg-brand-amber text-white shadow-sm flex items-center gap-1.5">
          <i class="fa-solid font-normal fa-utensils"></i>
          <span>Mode Pelanggan</span>
        </button>

        <button id="navAdminBtn" onclick="openAdminAuth()" 
          class="px-3 py-1.5 rounded-lg text-xs sm:text-sm font-medium transition duration-200 bg-brand-dark/60 hover:bg-brand-dark text-amber-200 hover:text-white border border-amber-800/40 flex items-center gap-1.5">
          <i class="fa-solid fa-user-shield text-xs"></i>
          <span>Mode Kasir</span>
        </button>
      </div>

    </div>
  </header>

  <!-- ================= UTAMA / KONTEN DINAMIS ================= -->
  <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-grow w-full">

    <!-- ---------------- Mode Pelanggan View ---------------- -->
    <div id="customerView" class="space-y-6">
      
      <!-- Hero Banner -->
      <div class="bg-gradient-to-r from-brand-brown via-amber-900 to-brand-dark text-white rounded-2xl p-6 sm:p-8 shadow-md relative overflow-hidden">
        <div class="relative z-10 max-w-xl">
          <span class="inline-block px-3 py-1 bg-brand-amber/30 text-amber-300 rounded-full text-xs font-semibold mb-3 border border-brand-amber/40">
            👋 Selamat Datang
          </span>
          <h2 class="text-2xl sm:text-3xl font-bold mb-2 text-brand-cream">Pesan Kuliner Favoritmu Tanpa Antre</h2>
          <p class="text-amber-100/80 text-sm sm:text-base mb-4">Pilih menu santapan lezat, tentukan metode makan, dan bayar dengan praktis di kasir atau secara online.</p>
          
          <!-- Social Quick Links Badge -->
          <div class="flex flex-wrap items-center gap-2 mb-4 text-xs">
            <a href="https://instagram.com" target="_blank" class="px-2.5 py-1 bg-white/10 hover:bg-white/20 rounded-lg backdrop-blur flex items-center gap-1.5 text-amber-200 transition">
              <i class="fa-brands fa-instagram text-pink-400"></i>
              <span>@gemebite_official</span>
            </a>
            <a href="https://tiktok.com" target="_blank" class="px-2.5 py-1 bg-white/10 hover:bg-white/20 rounded-lg backdrop-blur flex items-center gap-1.5 text-amber-200 transition">
              <i class="fa-brands fa-tiktok text-cyan-300"></i>
              <span>@gemebite_official</span>
            </a>
          </div>

          <a href="#katalogMenu" class="inline-flex items-center gap-2 bg-brand-amber hover:bg-amber-600 text-white font-medium px-4 py-2 rounded-xl text-sm transition shadow-lg">
            <span>Lihat Menu</span>
            <i class="fa-solid fa-arrow-down text-xs"></i>
          </a>
        </div>
        <div class="absolute right-[-20px] bottom-[-20px] text-8xl opacity-10 select-none">🍲</div>
      </div>

      <!-- Layout Grid: Menu + Keranjang -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">
        
        <!-- Kolom Kiri: Katalog Menu (8 Col) -->
        <section id="katalogMenu" class="lg:col-span-8 space-y-5">
          
          <!-- Control Bar: Search & Category Filter -->
          <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft/80 space-y-3 sm:space-y-0 sm:flex sm:items-center sm:justify-between gap-4">
            <!-- Search Bar -->
            <div class="relative flex-1">
              <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-gray-400 text-sm"></i>
              <input type="text" id="searchInput" oninput="renderMenu()" placeholder="Cari makanan atau minuman..." 
                class="w-full pl-10 pr-4 py-2 bg-gray-50 border border-gray-200 rounded-xl text-sm focus:outline-none focus:border-brand-amber focus:ring-1 focus:ring-brand-amber transition">
            </div>

            <!-- Categories Tabs -->
            <div class="flex items-center gap-1.5 overflow-x-auto pb-1 sm:pb-0" id="categoryFilters">
              <button onclick="setCategory('all')" data-cat="all" class="cat-btn active-cat px-3 py-1.5 rounded-xl text-xs font-medium whitespace-nowrap bg-brand-brown text-white transition">Semua</button>
              <button onclick="setCategory('makanan')" data-cat="makanan" class="cat-btn px-3 py-1.5 rounded-xl text-xs font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200 transition">Makanan</button>
              <button onclick="setCategory('minuman')" data-cat="minuman" class="cat-btn px-3 py-1.5 rounded-xl text-xs font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200 transition">Minuman</button>
              <button onclick="setCategory('camilan')" data-cat="camilan" class="cat-btn px-3 py-1.5 rounded-xl text-xs font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200 transition">Camilan</button>
            </div>
          </div>

          <!-- Menu Grid -->
          <div id="menuGrid" class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <!-- Menu Cards Rendered Here -->
          </div>

        </section>

        <!-- Kolom Kanan: Keranjang & Form Pemesanan (4 Col) -->
        <aside class="lg:col-span-4 sticky top-20">
          <div class="bg-white rounded-2xl shadow-md border border-brand-soft overflow-hidden">
            
            <div class="bg-brand-brown text-white p-4 flex items-center justify-between">
              <div class="flex items-center gap-2">
                <i class="fa-solid fa-basket-shopping text-brand-amber"></i>
                <h3 class="font-bold text-base">Keranjang Pesanan</h3>
              </div>
              <span id="cartCountBadge" class="bg-brand-amber text-white text-xs px-2.5 py-0.5 rounded-full font-bold">0</span>
            </div>

            <div class="p-4 space-y-4">
              <!-- Item List -->
              <div id="cartItemsList" class="space-y-3 max-h-64 overflow-y-auto pr-1 divide-y divide-gray-100">
                <p class="text-xs text-gray-400 text-center py-6">Keranjang masih kosong.<br>Yuk pilih menu lezat di sebelah!</p>
              </div>

              <!-- Total Price Display -->
              <div class="pt-3 border-t border-gray-100 space-y-1">
                <div class="flex justify-between items-center text-sm">
                  <span class="text-gray-500">Subtotal</span>
                  <span id="cartSubtotal" class="font-medium text-gray-700">Rp0</span>
                </div>
                <div class="flex justify-between items-center text-base font-bold text-brand-brown pt-1">
                  <span>Total Bayar</span>
                  <span id="cartTotal" class="text-brand-amber text-lg">Rp0</span>
                </div>
              </div>

              <!-- Form Pemesan -->
              <form id="customerOrderForm" onsubmit="handlePlaceOrder(event)" class="space-y-3 pt-2">
                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Nama Pemesan <span class="text-red-500">*</span></label>
                  <input type="text" id="custName" required placeholder="Contoh: Budi Prasetyo" 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                </div>

                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Nomor WhatsApp <span class="text-red-500">*</span></label>
                  <input type="tel" id="custPhone" required placeholder="08xxxxxxxxxx" 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                </div>

                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Tipe Pesanan <span class="text-red-500">*</span></label>
                  <select id="orderType" onchange="toggleOrderTypeFields()" 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                    <option value="Dine-in"> Makan di Tempat (Dine-in)</option>
                    <option value="Takeaway"> Bungkus (Takeaway)</option>
                    <option value="Delivery"> Antar ke Alamat (Delivery)</option>
                  </select>
                </div>

                <!-- Dynamic Field: Table No / Delivery Address -->
                <div id="tableNoField">
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Nomor Meja <span class="text-red-500">*</span></label>
                  <input type="number" id="custTable" min="1" placeholder="Nomor Meja (misal: 05)" 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                </div>

                <div id="addressField" class="hidden">
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Alamat Pengiriman <span class="text-red-500">*</span></label>
                  <textarea id="custAddress" rows="2" placeholder="Tuliskan alamat lengkap pengiriman..." 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber"></textarea>
                </div>

                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Metode Pembayaran</label>
                  <select id="paymentMethod" 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                    <option value="Kasir (Tunai/Debit)">Tunai / Debit di Kasir</option>
                    <option value="QRIS">QRIS (Scan & Bayar)</option>
                  </select>
                </div>

                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Catatan Tambahan (Opsional)</label>
                  <textarea id="custNote" rows="1" placeholder="Contoh: Es sedikit, sambal dipisah..." 
                    class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber"></textarea>
                </div>

                <!-- Order Action Buttons -->
                <div class="pt-2 space-y-2">
                  <button type="submit" name="action" value="system" 
                    class="w-full py-2.5 bg-brand-brown hover:bg-brand-dark text-white rounded-xl font-bold text-xs shadow-md transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-paper-plane"></i>
                    <span>Buat Pesanan Sekarang</span>
                  </button>

                  <button type="button" onclick="sendOrderViaWhatsApp()" 
                    class="w-full py-2 bg-brand-green hover:bg-emerald-700 text-white rounded-xl font-semibold text-xs transition flex items-center justify-center gap-2">
                    <i class="fa-brands fa-whatsapp text-sm"></i>
                    <span>Pesan via WhatsApp</span>
                  </button>
                </div>

              </form>

            </div>

          </div>
        </aside>

      </div>

      <!-- Public Queue Monitor Board -->
      <section class="bg-white p-6 rounded-2xl shadow-sm border border-brand-soft space-y-4">
        <div class="flex items-center justify-between">
          <div class="flex items-center gap-2">
            <span class="text-xl">🔔</span>
            <h3 class="font-bold text-lg text-brand-brown">Papan Antrean Real-Time</h3>
          </div>
          <span class="text-xs text-gray-400">Panggilan pesanan Anda</span>
        </div>

        <div id="publicQueueGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-3">
          <!-- Queue cards will be injected here -->
        </div>
      </section>

    </div>

    <!-- ---------------- Mode Kasir / Admin View ---------------- -->
    <div id="adminView" class="hidden space-y-6">
      
      <!-- Admin Bar Header -->
      <div class="bg-brand-dark text-white p-4 rounded-2xl shadow-sm flex flex-wrap items-center justify-between gap-4 border border-amber-900/50">
        <div>
          <h2 class="text-lg font-bold text-amber-200 flex items-center gap-2">
            <i class="fa-solid fa-sliders"></i>
            <span>Panel Kasir & Admin Kedai</span>
          </h2>
          <p class="text-xs text-gray-300">Kelola pesanan, stok menu, cetak struk, dan pantau omset harian.</p>
        </div>

        <div class="flex items-center gap-2">
          <button onclick="openSettingsModal()" class="px-3 py-1.5 bg-amber-700/80 hover:bg-amber-800 text-white text-xs font-semibold rounded-lg transition flex items-center gap-1.5">
            <i class="fa-solid fa-gear"></i>
            <span>Pengaturan</span>
          </button>
          <button onclick="logoutAdmin()" class="px-3 py-1.5 bg-red-600/80 hover:bg-red-700 text-white text-xs font-semibold rounded-lg transition flex items-center gap-1.5">
            <i class="fa-solid fa-right-from-bracket"></i>
            <span>Keluar Admin</span>
          </button>
        </div>
      </div>

      <!-- Ringkasan Omset & Stats Harian -->
      <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft flex items-center gap-4">
          <div class="w-12 h-12 bg-amber-100 text-brand-amber rounded-xl flex items-center justify-center text-xl">
            <i class="fa-solid fa-wallet"></i>
          </div>
          <div>
            <p class="text-xs text-gray-500 font-medium">Omset Hari Ini</p>
            <h4 id="statDailyRevenue" class="text-lg font-bold text-brand-brown">Rp0</h4>
          </div>
        </div>

        <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft flex items-center gap-4">
          <div class="w-12 h-12 bg-emerald-100 text-brand-green rounded-xl flex items-center justify-center text-xl">
            <i class="fa-solid fa-receipt"></i>
          </div>
          <div>
            <p class="text-xs text-gray-500 font-medium">Transaksi Selesai</p>
            <h4 id="statCompletedOrders" class="text-lg font-bold text-brand-brown">0 Pesanan</h4>
          </div>
        </div>

        <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft flex items-center gap-4">
          <div class="w-12 h-12 bg-blue-100 text-blue-600 rounded-xl flex items-center justify-center text-xl">
            <i class="fa-solid fa-clock"></i>
          </div>
          <div>
            <p class="text-xs text-gray-500 font-medium">Dalam Antrean</p>
            <h4 id="statPendingOrders" class="text-lg font-bold text-brand-brown">0 Pesanan</h4>
          </div>
        </div>
      </div>

      <!-- Main Admin Tabs Layout -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
        
        <!-- Left Column: Order Management & Queue (7 Cols) -->
        <section class="lg:col-span-7 space-y-4">
          <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft">
            <h3 class="font-bold text-base text-brand-brown mb-3 flex items-center gap-2">
              <i class="fa-solid fa-list-check text-brand-amber"></i>
              <span>Daftar Pesanan Masuk</span>
            </h3>

            <!-- Admin Orders List -->
            <div id="adminOrdersList" class="space-y-3 max-h-[600px] overflow-y-auto pr-1">
              <!-- Rendered Order Items -->
            </div>
          </div>
        </section>

        <!-- Right Column: Menu & Stock Management (5 Cols) -->
        <section class="lg:col-span-5 space-y-4">
          
          <!-- Form Tambah / Edit Menu -->
          <div class="bg-white p-5 rounded-2xl shadow-sm border border-brand-soft space-y-3">
            <h3 id="menuFormTitle" class="font-bold text-base text-brand-brown flex items-center gap-2">
              <i class="fa-solid fa-circle-plus text-brand-amber"></i>
              <span>Tambah Menu Baru</span>
            </h3>

            <form id="menuCrudForm" onsubmit="handleSaveMenu(event)" class="space-y-3">
              <input type="hidden" id="editMenuId">

              <div>
                <label class="block text-xs font-semibold text-gray-700 mb-1">Nama Menu</label>
                <input type="text" id="menuName" required placeholder="Contoh: Es Kopi Susu Aren" 
                  class="w-full px-3 py-1.5 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
              </div>

              <div class="grid grid-cols-2 gap-2">
                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Kategori</label>
                  <select id="menuCategory" class="w-full px-3 py-1.5 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                    <option value="makanan">Makanan</option>
                    <option value="minuman">Minuman</option>
                    <option value="camilan">Camilan</option>
                  </select>
                </div>
                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Emoji / Icon</label>
                  <input type="text" id="menuEmoji" placeholder="🥤" 
                    class="w-full px-3 py-1.5 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber text-center">
                </div>
              </div>

              <div class="grid grid-cols-2 gap-2">
                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Harga (Rp)</label>
                  <input type="number" id="menuPrice" min="0" step="500" required placeholder="18000" 
                    class="w-full px-3 py-1.5 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                </div>
                <div>
                  <label class="block text-xs font-semibold text-gray-700 mb-1">Stok Porsi</label>
                  <input type="number" id="menuStock" min="0" step="1" required placeholder="25" 
                    class="w-full px-3 py-1.5 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
                </div>
              </div>

              <div>
                <label class="block text-xs font-semibold text-gray-700 mb-1">Foto Menu (Upload/URL)</label>
                <input type="file" id="menuImageFile" accept="image/*" onchange="handleImageUpload(event)"
                  class="w-full text-xs text-gray-500 file:mr-2 file:py-1 file:px-2 file:rounded-lg file:border-0 file:text-xs file:font-semibold file:bg-amber-50 file:text-brand-brown hover:file:bg-amber-100">
                <input type="hidden" id="menuImageData">
              </div>

              <div>
                <label class="block text-xs font-semibold text-gray-700 mb-1">Deskripsi Singkat</label>
                <textarea id="menuDesc" rows="2" placeholder="Penjelasan rasa atau bahan utama..." 
                  class="w-full px-3 py-1.5 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber"></textarea>
              </div>

              <div class="flex gap-2 pt-1">
                <button type="submit" class="flex-1 py-2 bg-brand-brown hover:bg-brand-dark text-white rounded-lg font-bold text-xs transition">
                  Simpan Menu
                </button>
                <button type="button" onclick="resetMenuCrudForm()" class="px-3 py-2 bg-gray-200 hover:bg-gray-300 text-gray-700 rounded-lg font-semibold text-xs transition">
                  Batal
                </button>
              </div>
            </form>
          </div>

          <!-- Daftar Kelola Stok Menu -->
          <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft">
            <h3 class="font-bold text-base text-brand-brown mb-3 flex items-center gap-2">
              <i class="fa-solid fa-boxes-stacked text-brand-amber"></i>
              <span>Kelola Stok & Harga</span>
            </h3>

            <div id="adminMenuList" class="space-y-2 max-h-80 overflow-y-auto pr-1">
              <!-- Admin Menu Cards Rendered Here -->
            </div>
          </div>

        </section>

      </div>

    </div>

  </main>

  <!-- ================= FOOTER ================= -->
  <footer class="bg-brand-dark text-white py-8 border-t border-amber-900/40 mt-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-6">
      
      <!-- Footer Content Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 text-center md:text-left border-b border-amber-900/50 pb-6">
        
        <!-- Identitas Kedai -->
        <div class="space-y-2">
          <div class="flex items-center justify-center md:justify-start gap-2">
            <span class="text-2xl">☕</span>
            <h3 class="font-bold text-lg text-brand-cream">Gemebite</h3>
          </div>
          <p class="text-xs text-amber-200/80 leading-relaxed">
            Menyajikan aneka makanan, minuman, dan santapan lezat khas Gemebite dengan pelayanan ramah & cepat.
          </p>
        </div>

        <!-- Kontak & Alamat -->
        <div class="space-y-2 text-xs text-gray-300">
          <h4 class="font-bold text-amber-300 text-sm mb-1">Hubungi Kami</h4>
          <p class="flex items-center justify-center md:justify-start gap-2">
            <i class="fa-solid fa-location-dot text-brand-amber"></i>
            <span>Jl. Moh Ramdan Kec.Jamblang DS.Sitiwinangun RT.001 RW.008 Blok.Caplek Lor Belakang SDN 1 Sitiwinangun</span>
          </p>
          <p class="flex items-center justify-center md:justify-start gap-2">
            <i class="fa-brands fa-whatsapp text-emerald-400"></i>
            <span id="footerWaDisplay">+62 851-2994-0109</span>
          </p>
          <p class="flex items-center justify-center md:justify-start gap-2">
            <i class="fa-solid fa-envelope text-amber-400"></i>
            <span id="footerEmailDisplay">gemebiteofficial@gmail.com</span>
          </p>
        </div>

        <!-- Sosial Media Kedai -->
        <div class="space-y-2 text-xs">
          <h4 class="font-bold text-amber-300 text-sm mb-1">Ikuti Sosial Media</h4>
          <p class="text-gray-300 mb-2">Dapatkan info promo & menu terbaru setiap hari!</p>
          <div class="flex justify-center md:justify-start items-center gap-3">
            <a id="linkIg" href="https://instagram.com" target="_blank" 
              class="w-8 h-8 rounded-xl bg-pink-600/20 hover:bg-pink-600 text-pink-400 hover:text-white flex items-center justify-center transition text-base border border-pink-500/30">
              <i class="fa-brands fa-instagram"></i>
            </a>
            <a id="linkTiktok" href="https://tiktok.com" target="_blank" 
              class="w-8 h-8 rounded-xl bg-cyan-600/20 hover:bg-cyan-600 text-cyan-300 hover:text-white flex items-center justify-center transition text-base border border-cyan-500/30">
              <i class="fa-brands fa-tiktok"></i>
            </a>
            <a id="linkWa" href="https://wa.me/6285129940109" target="_blank" 
              class="w-8 h-8 rounded-xl bg-emerald-600/20 hover:bg-emerald-600 text-emerald-400 hover:text-white flex items-center justify-center transition text-base border border-emerald-500/30">
              <i class="fa-brands fa-whatsapp"></i>
            </a>
          </div>
        </div>

      </div>

      <!-- Copyright -->
      <div class="text-center text-xs text-gray-400">
        <p>Gemebite&copy; 2026. All Rights Reserved.</p>
      </div>

    </div>
  </footer>

  <!-- ================= MODALS & OVERLAYS ================= -->

  <!-- Modal Admin Login Auth -->
  <div id="adminAuthModal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl shadow-xl max-w-sm w-full p-6 space-y-4 border border-brand-soft">
      <div class="text-center space-y-1">
        <div class="w-12 h-12 bg-amber-100 text-brand-brown rounded-full flex items-center justify-center text-xl mx-auto mb-2">
          🔒
        </div>
        <h3 class="font-bold text-lg text-brand-brown">Akses Kasir & Admin</h3>
        <p class="text-xs text-gray-500">Masukkan kata sandi admin untuk masuk.</p>
      </div>

      <form onsubmit="handleAdminLogin(event)" class="space-y-3">
        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Kata Sandi</label>
          <input type="password" id="adminPasswordInput" required placeholder="Masukkan sandi (demo: denong cantik)" 
            class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
        </div>

        <p id="adminLoginError" class="text-xs text-red-600 font-semibold hidden">Sandi salah! Coba lagi.</p>

        <div class="flex gap-2 pt-2">
          <button type="button" onclick="closeAdminAuthModal()" class="w-1/2 py-2 bg-gray-100 hover:bg-gray-200 text-gray-700 font-semibold text-xs rounded-xl transition">
            Batal
          </button>
          <button type="submit" class="w-1/2 py-2 bg-brand-brown hover:bg-brand-dark text-white font-bold text-xs rounded-xl transition shadow">
            Masuk Kasir
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- Modal Cetak Struk Nota Kasir -->
  <div id="receiptModal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl shadow-xl max-w-sm w-full p-6 space-y-4 max-h-[90vh] flex flex-col">
      <div class="flex justify-between items-center border-b pb-2">
        <h3 class="font-bold text-base text-gray-800">Struk & Nota Transaksi</h3>
        <button onclick="closeReceiptModal()" class="text-gray-400 hover:text-gray-600 text-sm">
          <i class="fa-solid fa-xmark"></i>
        </button>
      </div>

      <!-- Printable Area Container -->
      <div class="overflow-y-auto flex-grow bg-gray-50 p-3 rounded-xl border border-dashed border-gray-300">
        <div id="printableReceipt" class="bg-white p-4 shadow-sm text-xs font-mono text-gray-800 space-y-2">
          <!-- Receipt Content Injected via JS -->
        </div>
      </div>

      <div class="space-y-2 pt-2">
        <div class="flex gap-2">
          <button onclick="window.print()" class="w-1/2 py-2 bg-brand-brown hover:bg-brand-dark text-white font-bold text-xs rounded-xl transition shadow flex items-center justify-center gap-1.5">
            <i class="fa-solid fa-print"></i>
            <span>Cetak Struk</span>
          </button>
          <button onclick="downloadReceiptAsImage()" class="w-1/2 py-2 bg-amber-600 hover:bg-amber-700 text-white font-bold text-xs rounded-xl transition shadow flex items-center justify-center gap-1.5">
            <i class="fa-solid fa-image"></i>
            <span>Simpan Gambar</span>
          </button>
        </div>
        <button onclick="sendReceiptToCustomerWA()" class="w-full py-2 bg-brand-green hover:bg-emerald-700 text-white font-bold text-xs rounded-xl transition shadow flex items-center justify-center gap-1.5">
          <i class="fa-brands fa-whatsapp text-sm"></i>
          <span>Kirim Gambar Struk ke WA Pembeli</span>
        </button>
        <button onclick="closeReceiptModal()" class="w-full py-1.5 bg-gray-200 hover:bg-gray-300 text-gray-700 font-semibold text-xs rounded-xl transition">
          Tutup
        </button>
      </div>
    </div>
  </div>

  <!-- Modal Pembayaran QRIS Dinamis -->
  <div id="qrisModal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl shadow-xl max-w-sm w-full p-6 space-y-4 text-center border border-brand-soft">
      <div class="space-y-1">
        <span class="text-2xl">📱</span>
        <h3 class="font-bold text-lg text-brand-brown">Pembayaran QRIS</h3>
        <p class="text-xs text-gray-500">Scan QRIS menggunakan Mobile Banking atau E-Wallet Anda.</p>
      </div>

      <!-- Container Tempat QR Code Direset dan Dibuat -->
      <div class="p-4 bg-gray-50 rounded-2xl border border-gray-200 inline-block mx-auto relative shadow-inner">
        <div id="qrisCodeContainer" class="flex justify-center items-center bg-white p-2 rounded-xl border border-gray-100"></div>
        <p id="qrisTotalDisplay" class="font-bold text-brand-amber text-base mt-2">Rp0</p>
      </div>

      <div class="space-y-2 pt-1">
        <button onclick="downloadQRISCode()" class="w-full py-2 bg-amber-600 hover:bg-amber-700 text-white font-bold text-xs rounded-xl transition flex items-center justify-center gap-2 shadow">
          <i class="fa-solid fa-download"></i>
          <span>Download Kode QRIS</span>
        </button>

        <button onclick="confirmQrisPayment()" class="w-full py-2.5 bg-brand-green hover:bg-emerald-700 text-white font-bold text-xs rounded-xl transition flex items-center justify-center gap-2 shadow">
          <i class="fa-solid fa-circle-check"></i>
          <span>Konfirmasi Pembayaran Selesai (Kasir/Scan)</span>
        </button>

        <button onclick="closeQrisModal()" class="w-full py-1.5 bg-gray-100 hover:bg-gray-200 text-gray-600 font-semibold text-xs rounded-xl transition">
          Tutup
        </button>
      </div>
    </div>
  </div>

  <!-- Modal Pengaturan Kedai -->
  <div id="settingsModal" class="fixed inset-0 bg-black/60 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-white rounded-2xl shadow-xl max-w-sm w-full p-6 space-y-4 border border-brand-soft max-h-[90vh] overflow-y-auto">
      <div class="flex justify-between items-center border-b pb-2">
        <h3 class="font-bold text-base text-brand-brown flex items-center gap-2">
          <i class="fa-solid fa-gear text-brand-amber"></i>
          <span>Pengaturan Kedai</span>
        </h3>
        <button onclick="closeSettingsModal()" class="text-gray-400 hover:text-gray-600 text-sm">
          <i class="fa-solid fa-xmark"></i>
        </button>
      </div>

      <form onsubmit="handleSaveSettings(event)" class="space-y-3">
        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Nomor WA Kedai (Terima Pesanan)</label>
          <input type="text" id="settingWaPhone" required placeholder="628xxxxxxxxxx" 
            class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
          <span class="text-[10px] text-gray-400">Gunakan format kode negara (cth: 62812345678)</span>
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Upload Gambar QRIS Asli Kedai</label>
          <input type="file" id="settingQrisFile" accept="image/*" onchange="handleQrisImageUpload(event)"
            class="w-full text-xs text-gray-500 file:mr-2 file:py-1 file:px-2 file:rounded-lg file:border-0 file:text-xs file:font-semibold file:bg-amber-50 file:text-brand-brown hover:file:bg-amber-100">
          <input type="hidden" id="settingQrisImageData">
          <span class="text-[10px] text-gray-400">Upload foto barcode/QRIS bank atau e-wallet milik usaha Anda</span>
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Username Instagram</label>
          <input type="text" id="settingIg" placeholder="@gemebite_official" 
            class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Username TikTok</label>
          <input type="text" id="settingTiktok" placeholder="@gemebite_official" 
            class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Email Kedai</label>
          <input type="email" id="settingEmail" placeholder="gemebiteofficial@gmail.com" 
            class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
        </div>

        <div>
          <label class="block text-xs font-semibold text-gray-700 mb-1">Kata Sandi Admin Baru</label>
          <input type="password" id="settingAdminPass" required placeholder="Sandi baru" 
            class="w-full px-3 py-2 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber">
        </div>

        <div class="flex gap-2 pt-2">
          <button type="button" onclick="closeSettingsModal()" class="w-1/2 py-2 bg-gray-100 hover:bg-gray-200 text-gray-700 font-semibold text-xs rounded-xl transition">
            Batal
          </button>
          <button type="submit" class="w-1/2 py-2 bg-brand-brown hover:bg-brand-dark text-white font-bold text-xs rounded-xl transition shadow">
            Simpan Pengaturan
          </button>
        </div>
      </form>
    </div>
  </div>

  <!-- Notification Toast Container -->
  <div id="toast" class="fixed bottom-5 right-5 z-50 transform translate-y-20 opacity-0 transition-all duration-300 bg-brand-dark text-white px-4 py-3 rounded-xl shadow-xl text-xs flex items-center gap-2 border border-brand-amber">
    <span id="toastIcon">💡</span>
    <span id="toastMessage">Pesan notifikasi</span>
  </div>

  <!-- ================= JAVASCRIPT LOGIC ================= -->
  <script>
    // ===== CONFIG & INITIAL CONSTANTS =====
    let DEMO_ADMIN_PASS = loadFromStorage("kedai_admin_pass", "bitemy");
    let WHATSAPP_STORE_PHONE = loadFromStorage("kedai_store_wa", "6281234567890");
    let INSTAGRAM_USER = loadFromStorage("kedai_ig", "@kedairasa.id");
    let TIKTOK_USER = loadFromStorage("kedai_tiktok", "@kedairasa_official");
    let STORE_EMAIL = loadFromStorage("kedai_email", "kontak@kedairasa.id");
    let CUSTOM_QRIS_IMAGE = loadFromStorage("kedai_custom_qris", "");

    const DEFAULT_MENU = [
      {
        id: 101,
        name: "Nasi Goreng Spesial Rasa",
        category: "makanan",
        price: 18000,
        stock: 20,
        description: "Nasi goreng bumbu rempah khas kedai dengan telur ceplok dan kerupuk.",
        emoji: "🍛",
        hasSpicyLevel: true,
        image: ""
      },
      {
        id: 102,
        name: "Mie Goreng Jawa Pedas",
        category: "makanan",
        price: 16000,
        stock: 15,
        description: "Mie telur tumis sayuran, bakso, dan irisan ayam manis pedas.",
        emoji: "🍜",
        hasSpicyLevel: true,
        image: ""
      },
      {
        id: 103,
        name: "Ayam Geprek Sambal Korek",
        category: "makanan",
        price: 20000,
        stock: 12,
        description: "Ayam renyah krispi digeprek pedas mantap plus nasi hangat.",
        emoji: "🍗",
        hasSpicyLevel: true,
        image: ""
      },
      {
        id: 104,
        name: "Es Kopi Susu Gula Aren",
        category: "minuman",
        price: 15000,
        stock: 30,
        description: "Espresso house blend dengan susu segar & gula aren asli.",
        emoji: "🧋",
        hasSpicyLevel: false,
        image: ""
      },
      {
        id: 105,
        name: "Es Teh Manis Jumbo",
        category: "minuman",
        price: 5000,
        stock: 50,
        description: "Seduhan teh tubruk wangi melati dingin menyegarkan.",
        emoji: "🥤",
        hasSpicyLevel: false,
        image: ""
      },
      {
        id: 106,
        name: "Cireng Bumbu Rujak",
        category: "camilan",
        price: 10000,
        stock: 25,
        description: "Cireng garing krispi diluar kenyal didalam dengan cocolan pedas manis.",
        emoji: "🥟",
        hasSpicyLevel: false,
        image: ""
      }
    ];

    // ===== APP STATE =====
    let currentView = 'customer'; // 'customer' | 'admin'
    let isAdminLoggedIn = false;
    let selectedCategory = 'all';
    let activeQrisOrder = null;
    let activeReceiptOrder = null;

    let menuList = loadFromStorage("kedai_menu_v2", DEFAULT_MENU);
    let ordersList = loadFromStorage("kedai_orders_v2", []);
    let cart = {}; // { [menuId]: quantity }
    let nextQueueNumber = loadFromStorage("kedai_next_queue_v2", 1);

    // ===== STORAGE HELPERS =====
    function loadFromStorage(key, fallback) {
      try {
        const saved = localStorage.getItem(key);
        return saved ? JSON.parse(saved) : fallback;
      } catch (e) {
        console.error("Storage error:", e);
        return fallback;
      }
    }

    function saveToStorage() {
      try {
        localStorage.setItem("kedai_menu_v2", JSON.stringify(menuList));
        localStorage.setItem("kedai_orders_v2", JSON.stringify(ordersList));
        localStorage.setItem("kedai_next_queue_v2", JSON.stringify(nextQueueNumber));
      } catch (e) {
        showToast("Storage penuh! Gunakan ukuran gambar lebih kecil.", "⚠️");
      }
    }

    // ===== FORMATTING UTILS =====
    function formatRupiah(number) {
      return new Intl.NumberFormat("id-ID", {
        style: "currency",
        currency: "IDR",
        maximumFractionDigits: 0
      }).format(number);
    }

    function escapeHtml(str) {
      return String(str || '').replace(/[&<>"']/g, function (m) {
        return { '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[m];
      });
    }

    function showToast(msg, icon = "💡") {
      const toast = document.getElementById("toast");
      document.getElementById("toastMessage").textContent = msg;
      document.getElementById("toastIcon").textContent = icon;
      
      toast.classList.remove("translate-y-20", "opacity-0");
      setTimeout(() => {
        toast.classList.add("translate-y-20", "opacity-0");
      }, 3000);
    }

    // ===== VIEW NAVIGATION =====
    function switchView(target) {
      currentView = target;
      const custView = document.getElementById("customerView");
      const adminView = document.getElementById("adminView");
      const navCustBtn = document.getElementById("navCustomerBtn");
      const navAdminBtn = document.getElementById("navAdminBtn");

      if (target === 'customer') {
        custView.classList.remove("hidden");
        adminView.classList.add("hidden");
        navCustBtn.className = "px-3 py-1.5 rounded-lg text-xs sm:text-sm font-medium transition duration-200 bg-brand-amber text-white shadow-sm flex items-center gap-1.5";
        navAdminBtn.className = "px-3 py-1.5 rounded-lg text-xs sm:text-sm font-medium transition duration-200 bg-brand-dark/60 hover:bg-brand-dark text-amber-200 hover:text-white border border-amber-800/40 flex items-center gap-1.5";
      } else {
        custView.classList.add("hidden");
        adminView.classList.remove("hidden");
        navAdminBtn.className = "px-3 py-1.5 rounded-lg text-xs sm:text-sm font-medium transition duration-200 bg-brand-amber text-white shadow-sm flex items-center gap-1.5";
        navCustBtn.className = "px-3 py-1.5 rounded-lg text-xs sm:text-sm font-medium transition duration-200 bg-brand-dark/60 hover:bg-brand-dark text-amber-200 hover:text-white border border-amber-800/40 flex items-center gap-1.5";
        renderAdminDashboard();
      }
    }

    function openAdminAuth() {
      if (isAdminLoggedIn) {
        switchView('admin');
      } else {
        document.getElementById("adminAuthModal").classList.remove("hidden");
        document.getElementById("adminPasswordInput").focus();
      }
    }

    function closeAdminAuthModal() {
      document.getElementById("adminAuthModal").classList.add("hidden");
      document.getElementById("adminLoginError").classList.add("hidden");
      document.getElementById("adminPasswordInput").value = "";
    }

    function handleAdminLogin(e) {
      e.preventDefault();
      const pass = document.getElementById("adminPasswordInput").value;
      if (pass === DEMO_ADMIN_PASS) {
        isAdminLoggedIn = true;
        closeAdminAuthModal();
        switchView('admin');
        showToast("Login Admin Berhasil!", "🔑");
      } else {
        document.getElementById("adminLoginError").classList.remove("hidden");
      }
    }

    function logoutAdmin() {
      isAdminLoggedIn = false;
      switchView('customer');
      showToast("Telah keluar dari mode Kasir.", "ℹ️");
    }

    // ===== KATALOG MENU & FILTER =====
    function renderMenu() {
      const grid = document.getElementById("menuGrid");
      const search = document.getElementById("searchInput").value.toLowerCase().trim();

      const filtered = menuList.filter(item => {
        const matchesCategory = selectedCategory === 'all' || item.category === selectedCategory;
        const matchesSearch = item.name.toLowerCase().includes(search) || item.description.toLowerCase().includes(search);
        return matchesCategory && matchesSearch;
      });

      if (filtered.length === 0) {
        grid.innerHTML = `
          <div class="col-span-full py-12 text-center text-gray-400 space-y-2">
            <span class="text-4xl">🔍</span>
            <p class="text-sm">Menu yang Anda cari tidak ditemukan.</p>
          </div>
        `;
        return;
      }

      grid.innerHTML = filtered.map(item => {
        const isSoldOut = item.stock <= 0;
        const imgDisplay = item.image 
          ? `<img src="${item.image}" alt="${escapeHtml(item.name)}" class="w-full h-36 object-cover rounded-xl mb-3">`
          : `<div class="w-full h-36 bg-amber-50 rounded-xl mb-3 flex items-center justify-center text-5xl shadow-inner">${item.emoji || '🍽️'}</div>`;

        const levelSelector = item.hasSpicyLevel
          ? `<div class="mt-2 text-left">
               <label class="block text-[10px] font-bold text-gray-600 mb-0.5">🌶️ Level Pedas:</label>
               <select id="level_${item.id}" class="w-full px-2 py-1 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber font-semibold text-gray-700">
                 <option value="Level 0 (Tidak Pedas)">Level 0 - Tidak Pedas</option>
                 <option value="Level 1 (Sedang)">Level 1 - Sedang 🌶️</option>
                 <option value="Level 2 (Pedas)">Level 2 - Pedas 🌶️🌶️</option>
                 <option value="Level 3 (Super Pedas)">Level 3 - Super Pedas 🌶️🌶️🌶️</option>
               </select>
             </div>`
          : `<div class="mt-2 text-left">
               <label class="block text-[10px] font-bold text-gray-600 mb-0.5">📝 Varian / Request:</label>
               <select id="level_${item.id}" class="w-full px-2 py-1 text-xs bg-gray-50 border border-gray-200 rounded-lg focus:outline-none focus:border-brand-amber font-semibold text-gray-700">
                 <option value="Normal / Standar">Normal / Standar</option>
                 <option value="Less Ice / Es Sedikit">Less Ice (Es Sedikit)</option>
                 <option value="Extra Manis">Extra Manis</option>
                 <option value="Less Sugar (Kurang Manis)">Kurang Manis</option>
               </select>
             </div>`;

        return `
          <div class="bg-white p-4 rounded-2xl shadow-sm border border-brand-soft flex flex-col justify-between hover:shadow-md transition">
            <div>
              ${imgDisplay}
              <div class="flex items-start justify-between gap-2 mb-1">
                <h4 class="font-bold text-sm text-brand-brown leading-snug">${escapeHtml(item.name)}</h4>
                <span class="text-xs px-2 py-0.5 bg-amber-100 text-brand-brown font-semibold rounded-full">${escapeHtml(item.category)}</span>
              </div>
              <p class="text-xs text-gray-500 line-clamp-2 mb-1">${escapeHtml(item.description)}</p>
              ${levelSelector}
            </div>

            <div class="pt-2 border-t border-gray-100 flex items-center justify-between mt-3">
              <div>
                <p class="font-bold text-sm text-brand-amber">${formatRupiah(item.price)}</p>
                <p class="text-[10px] ${isSoldOut ? 'text-red-500 font-bold' : 'text-gray-400'}">
                  ${isSoldOut ? 'Stok Habis' : 'Stok: ' + item.stock}
                </p>
              </div>

              <button onclick="addToCartWithOption(${item.id})" ${isSoldOut ? 'disabled' : ''} 
                class="px-3 py-1.5 rounded-xl text-xs font-bold transition flex items-center gap-1 ${
                  isSoldOut 
                  ? 'bg-gray-200 text-gray-400 cursor-not-allowed' 
                  : 'bg-brand-brown hover:bg-brand-dark text-white shadow-sm'
                }">
                <i class="fa-solid fa-plus text-[10px]"></i>
                <span>Tambah</span>
              </button>
            </div>
          </div>
        `;
      }).join("");
    }

    // ===== KERANJANG BELANJA WITH LEVEL OPTION =====
    function addToCartWithOption(id) {
      const product = menuList.find(m => m.id === id);
      if (!product || product.stock <= 0) return;

      const levelSelect = document.getElementById(`level_${id}`);
      const selectedOption = levelSelect ? levelSelect.value : 'Normal';

      // Unik Key gabungan ID Menu & Pilihan Level
      const cartKey = `${id}_${selectedOption}`;

      const currentQty = cart[cartKey] ? cart[cartKey].qty : 0;
      if (currentQty >= product.stock) {
        showToast(`Stok ${product.name} tidak mencukupi.`, "⚠️");
        return;
      }

      cart[cartKey] = {
        menuId: id,
        name: product.name,
        price: product.price,
        option: selectedOption,
        qty: currentQty + 1
      };

      renderCart();
      showToast(`${product.name} (${selectedOption}) ditambahkan!`, "🛒");
    }

    function updateCartItemKeyQty(key, delta) {
      if (!cart[key]) return;

      const product = menuList.find(m => m.id === cart[key].menuId);
      if (!product) return;

      const newQty = cart[key].qty + delta;
      if (newQty <= 0) {
        delete cart[key];
      } else if (newQty <= product.stock) {
        cart[key].qty = newQty;
      } else {
        showToast("Batas jumlah stok tercapai.", "⚠️");
      }
      renderCart();
    }

    function renderCart() {
      const container = document.getElementById("cartItemsList");
      const badge = document.getElementById("cartCountBadge");
      const subtotalEl = document.getElementById("cartSubtotal");
      const totalEl = document.getElementById("cartTotal");

      let total = 0;
      let itemCount = 0;
      let html = "";

      Object.keys(cart).forEach(key => {
        const item = cart[key];
        if (!item || item.qty <= 0) return;

        const itemSubtotal = item.price * item.qty;
        total += itemSubtotal;
        itemCount += item.qty;

        html += `
          <div class="pt-2 pb-1 flex items-center justify-between text-xs gap-2">
            <div class="flex-1 pr-1">
              <p class="font-semibold text-gray-800">${escapeHtml(item.name)}</p>
              <span class="text-[10px] px-1.5 py-0.5 bg-amber-50 text-amber-800 font-medium rounded border border-amber-200">
                ${escapeHtml(item.option)}
              </span>
              <p class="text-gray-400 mt-0.5">${formatRupiah(item.price)} x ${item.qty}</p>
            </div>
            
            <div class="flex items-center gap-2">
              <p class="font-bold text-gray-700">${formatRupiah(itemSubtotal)}</p>
              <div class="flex items-center bg-gray-100 rounded-lg p-0.5 border border-gray-200">
                <button onclick="updateCartItemKeyQty('${key}', -1)" class="w-5 h-5 flex items-center justify-center text-gray-600 hover:bg-white rounded font-bold text-xs">-</button>
                <span class="w-5 text-center font-semibold text-xs">${item.qty}</span>
                <button onclick="updateCartItemKeyQty('${key}', 1)" class="w-5 h-5 flex items-center justify-center text-gray-600 hover:bg-white rounded font-bold text-xs">+</button>
              </div>
            </div>
          </div>
        `;
      });

      badge.textContent = itemCount;
      container.innerHTML = html || `<p class="text-xs text-gray-400 text-center py-6">Keranjang masih kosong.<br>Yuk pilih menu lezat di sebelah!</p>`;
      subtotalEl.textContent = formatRupiah(total);
      totalEl.textContent = formatRupiah(total);
    }

    // ===== UI & FORM DYNAMIC TOGGLES =====
    function setCategory(cat) {
      selectedCategory = cat;
      document.querySelectorAll(".cat-btn").forEach(btn => {
        if (btn.dataset.cat === cat) {
          btn.className = "cat-btn active-cat px-3 py-1.5 rounded-xl text-xs font-medium whitespace-nowrap bg-brand-brown text-white transition";
        } else {
          btn.className = "cat-btn px-3 py-1.5 rounded-xl text-xs font-medium whitespace-nowrap bg-gray-100 text-gray-600 hover:bg-gray-200 transition";
        }
      });
      renderMenu();
    }

    function toggleOrderTypeFields() {
      const type = document.getElementById("orderType").value;
      const tableField = document.getElementById("tableNoField");
      const addressField = document.getElementById("addressField");

      if (type === "Dine-in") {
        tableField.classList.remove("hidden");
        addressField.classList.add("hidden");
      } else if (type === "Delivery") {
        tableField.classList.add("hidden");
        addressField.classList.remove("hidden");
      } else {
        tableField.classList.add("hidden");
        addressField.classList.add("hidden");
      }
    }

    // ===== PUBLIC QUEUE MONITOR =====
    function renderPublicQueue() {
      const container = document.getElementById("publicQueueGrid");
      if (!container) return;

      if (ordersList.length === 0) {
        container.innerHTML = `<p class="col-span-full text-xs text-gray-400 text-center py-6">Belum ada antrean pesanan.</p>`;
        return;
      }

      container.innerHTML = ordersList.slice(0, 8).map(order => {
        let statusBg = "bg-amber-100 text-amber-800 border-amber-200";
        if (order.status === "Diproses") statusBg = "bg-blue-100 text-blue-800 border-blue-200";
        if (order.status === "Siap") statusBg = "bg-emerald-100 text-emerald-800 border-emerald-200 animate-pulse";
        if (order.status === "Selesai") statusBg = "bg-gray-100 text-gray-600 border-gray-200";
        if (order.status === "Dibatalkan") statusBg = "bg-red-100 text-red-700 border-red-200";

        const qrisViewBtn = (order.paymentMethod === "QRIS") 
          ? `<button onclick="viewOrderQris(${order.queueNumber})" class="mt-1.5 px-2 py-0.5 bg-amber-600 hover:bg-amber-700 text-white rounded text-[10px] font-bold transition flex items-center justify-center gap-1 w-full">
               <i class="fa-solid fa-qrcode"></i> Lihat QRIS
             </button>` 
          : '';

        return `
          <div class="p-3 rounded-xl border bg-gray-50 flex flex-col justify-between text-xs space-y-2">
            <div class="flex items-center justify-between">
              <span class="font-bold text-sm text-brand-brown">#${String(order.queueNumber).padStart(3, '0')}</span>
              <span class="px-2 py-0.5 rounded-full font-bold text-[10px] border ${statusBg}">
                ${order.status}
              </span>
            </div>

            <div>
              <p class="font-semibold text-gray-800">${escapeHtml(order.customerName)}</p>
              <p class="text-[10px] text-gray-500">${order.orderType} • ${formatRupiah(order.total)}</p>
              <div class="mt-1 flex items-center gap-1">
                <span class="px-1.5 py-0.5 rounded text-[10px] font-bold ${order.isPaid ? 'bg-emerald-100 text-emerald-800' : 'bg-red-100 text-red-700'}">
                  ${order.isPaid ? 'LUNAS' : 'BELUM LUNAS'}
                </span>
              </div>
            </div>
            ${qrisViewBtn}
          </div>
        `;
      }).join("");
    }

    // ===== ORDER ACTIONS & STATUS =====
    function togglePaymentStatus(queueNum) {
      const order = ordersList.find(o => o.queueNumber === queueNum);
      if (!order) return;

      order.isPaid = !order.isPaid;
      saveToStorage();
      renderAll();
      showToast(`Status pembayaran #${String(queueNum).padStart(3, '0')} diubah menjadi ${order.isPaid ? 'LUNAS' : 'BELUM LUNAS'}.`, "💳");
    }

    function updateOrderStatus(queueNum, newStatus) {
      const order = ordersList.find(o => o.queueNumber === queueNum);
      if (!order) return;

      order.status = newStatus;
      saveToStorage();
      renderAll();
      showToast(`Status pesanan #${String(queueNum).padStart(3, '0')} diubah ke: ${newStatus}`, "🔔");
    }

    // ===== QRIS MODAL & LOGIC =====
    function openQrisModal(order) {
      activeQrisOrder = order;
      const qrisModal = document.getElementById("qrisModal");
      const container = document.getElementById("qrisCodeContainer");
      const totalDisplay = document.getElementById("qrisTotalDisplay");

      container.innerHTML = "";
      totalDisplay.textContent = formatRupiah(order.total);

      if (CUSTOM_QRIS_IMAGE) {
        // Tampilkan foto QRIS custom milik toko yang diupload lewat Mode Kasir
        const qrisImg = document.createElement("img");
        qrisImg.src = CUSTOM_QRIS_IMAGE;
        qrisImg.alt = "QRIS Gemebite";
        qrisImg.className = "w-44 h-44 object-contain rounded-lg border border-gray-200";
        container.appendChild(qrisImg);
      } else {
        // Fallback generator QR dinamis jika foto belum diunggah
        const qrisPayload = `00020101021226580016ID.Gemebite.WWW01189360091100000000005204581253033605802ID5910Gemebite6005DEPOK6304`;
        new QRCode(container, {
          text: qrisPayload + order.total,
          width: 160,
          height: 160,
          colorDark: "#4A2E1F",
          colorLight: "#ffffff",
          correctLevel: QRCode.CorrectLevel.H
        });
      }

      qrisModal.classList.remove("hidden");
    }

    function viewOrderQris(queueNum) {
      const order = ordersList.find(o => o.queueNumber === queueNum);
      if (order) openQrisModal(order);
    }

    function closeQrisModal() {
      document.getElementById("qrisModal").classList.add("hidden");
      activeQrisOrder = null;
    }

    function downloadQRISCode() {
      const img = document.querySelector("#qrisCodeContainer img");
      if (!img) return;

      const a = document.createElement("a");
      a.href = img.src;
      a.download = `QRIS-Gemebite-${activeQrisOrder ? activeQrisOrder.queueNumber : 'QR'}.png`;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      showToast("Kode QRIS telah diunduh!", "📥");
    }

    function confirmQrisPayment() {
      if (!activeQrisOrder) return;

      activeQrisOrder.isPaid = true;
      if (activeQrisOrder.status === "Menunggu") {
        activeQrisOrder.status = "Diproses";
      }

      saveToStorage();
      closeQrisModal();
      renderAll();
      showToast("✅ Pembayaran QRIS Dikonfirmasi LUNAS!", "🎉");
    }

    // ===== SETTINGS MODAL =====
    function handleQrisImageUpload(e) {
      const file = e.target.files[0];
      if (!file) return;

      if (file.size > 800 * 1024) {
        showToast("Ukuran foto QRIS maksimal 800 KB!", "⚠️");
        e.target.value = "";
        return;
      }

      const reader = new FileReader();
      reader.onload = function (evt) {
        document.getElementById("settingQrisImageData").value = evt.target.result;
      };
      reader.readAsDataURL(file);
    }

    function openSettingsModal() {
      document.getElementById("settingWaPhone").value = WHATSAPP_STORE_PHONE;
      document.getElementById("settingIg").value = INSTAGRAM_USER;
      document.getElementById("settingTiktok").value = TIKTOK_USER;
      document.getElementById("settingEmail").value = STORE_EMAIL;
      document.getElementById("settingAdminPass").value = DEMO_ADMIN_PASS;
      document.getElementById("settingQrisImageData").value = CUSTOM_QRIS_IMAGE;
      document.getElementById("settingsModal").classList.remove("hidden");
    }

    function closeSettingsModal() {
      document.getElementById("settingsModal").classList.add("hidden");
    }

    function handleSaveSettings(e) {
      e.preventDefault();
      const newWa = document.getElementById("settingWaPhone").value.trim();
      const newIg = document.getElementById("settingIg").value.trim();
      const newTiktok = document.getElementById("settingTiktok").value.trim();
      const newEmail = document.getElementById("settingEmail").value.trim();
      const newPass = document.getElementById("settingAdminPass").value.trim();
      const newQrisImg = document.getElementById("settingQrisImageData").value;

      if (newWa) {
        WHATSAPP_STORE_PHONE = newWa;
        localStorage.setItem("kedai_store_wa", JSON.stringify(newWa));
      }
      if (newIg) {
        INSTAGRAM_USER = newIg;
        localStorage.setItem("kedai_ig", JSON.stringify(newIg));
      }
      if (newTiktok) {
        TIKTOK_USER = newTiktok;
        localStorage.setItem("kedai_tiktok", JSON.stringify(newTiktok));
      }
      if (newEmail) {
        STORE_EMAIL = newEmail;
        localStorage.setItem("kedai_email", JSON.stringify(newEmail));
      }
      if (newPass) {
        DEMO_ADMIN_PASS = newPass;
        localStorage.setItem("kedai_admin_pass", JSON.stringify(newPass));
      }
      if (newQrisImg !== undefined) {
        CUSTOM_QRIS_IMAGE = newQrisImg;
        localStorage.setItem("kedai_custom_qris", JSON.stringify(newQrisImg));
      }

      closeSettingsModal();
      renderAll();
      showToast("Pengaturan Identitas Kedai & QRIS berhasil disimpan!", "⚙️");
    }

    function updateFooterIdentity() {
      const waDisplay = document.getElementById("footerWaDisplay");
      const emailDisplay = document.getElementById("footerEmailDisplay");
      const linkIg = document.getElementById("linkIg");
      const linkTiktok = document.getElementById("linkTiktok");
      const linkWa = document.getElementById("linkWa");

      if (waDisplay) waDisplay.textContent = `+${WHATSAPP_STORE_PHONE}`;
      if (emailDisplay) emailDisplay.textContent = STORE_EMAIL;
      if (linkWa) linkWa.href = `https://wa.me/${WHATSAPP_STORE_PHONE}`;
      
      const cleanIg = INSTAGRAM_USER.replace('@', '');
      const cleanTiktok = TIKTOK_USER.replace('@', '');
      if (linkIg) linkIg.href = `https://instagram.com/${cleanIg}`;
      if (linkTiktok) linkTiktok.href = `https://tiktok.com/@${cleanTiktok}`;
    }

    // ===== INIT APP =====
    function renderAll() {
      renderMenu();
      renderCart();
      renderPublicQueue();
      updateFooterIdentity();
      if (currentView === 'admin') {
        renderAdminDashboard();
      }
    }

    // ===== ORDER CREATION HANDLERS =====
    function handlePlaceOrder(e) {
      e.preventDefault();
      
      const cartKeys = Object.keys(cart);
      if (cartKeys.length === 0) {
        showToast("Keranjang belanja masih kosong!", "⚠️");
        return;
      }

      const name = document.getElementById("custName").value.trim();
      const phone = document.getElementById("custPhone").value.trim();
      const orderType = document.getElementById("orderType").value;
      const tableNo = document.getElementById("custTable").value.trim();
      const address = document.getElementById("custAddress").value.trim();
      const paymentMethod = document.getElementById("paymentMethod").value;
      const note = document.getElementById("custNote").value.trim();

      if (orderType === "Dine-in" && !tableNo) {
        showToast("Mohon isi nomor meja!", "⚠️");
        return;
      }
      if (orderType === "Delivery" && !address) {
        showToast("Mohon isi alamat pengiriman!", "⚠️");
        return;
      }

      // Format Items
      const items = cartKeys.map(key => {
        const item = cart[key];
        return {
          id: item.menuId,
          name: item.name,
          option: item.option,
          price: item.price,
          qty: item.qty,
          subtotal: item.price * item.qty
        };
      });

      // Stock Check
      for (let item of items) {
        const product = menuList.find(m => m.id === item.id);
        if (!product || product.stock < item.qty) {
          showToast(`Stok ${item.name} tidak mencukupi!`, "⚠️");
          return;
        }
      }

      // Deduct Stock
      items.forEach(item => {
        const product = menuList.find(m => m.id === item.id);
        if (product) product.stock -= item.qty;
      });

      const total = items.reduce((sum, item) => sum + item.subtotal, 0);

      const newOrder = {
        queueNumber: nextQueueNumber,
        customerName: name,
        customerPhone: phone,
        orderType: orderType,
        tableNo: orderType === "Dine-in" ? tableNo : "-",
        address: orderType === "Delivery" ? address : "-",
        paymentMethod: paymentMethod,
        isPaid: paymentMethod === "QRIS" ? false : false,
        note: note,
        items: items,
        total: total,
        status: "Menunggu",
        createdAt: new Date().toLocaleTimeString("id-ID", { hour: '2-digit', minute: '2-digit' })
      };

      ordersList.unshift(newOrder);
      nextQueueNumber++;

      cart = {};
      document.getElementById("customerOrderForm").reset();
      toggleOrderTypeFields();

      saveToStorage();
      renderAll();

      showToast(`Pesanan #${String(newOrder.queueNumber).padStart(3, '0')} berhasil dibuat!`, "✅");

      if (paymentMethod === "QRIS") {
        openQrisModal(newOrder);
      } else {
        openReceiptModal(newOrder);
      }
    }

    function sendOrderViaWhatsApp() {
      const cartKeys = Object.keys(cart);
      if (cartKeys.length === 0) {
        showToast("Keranjang belanja masih kosong!", "⚠️");
        return;
      }

      const name = document.getElementById("custName").value.trim() || "Pelanggan";
      const phone = document.getElementById("custPhone").value.trim();
      const orderType = document.getElementById("orderType").value;
      const tableNo = document.getElementById("custTable").value.trim();
      const address = document.getElementById("custAddress").value.trim();
      const paymentMethod = document.getElementById("paymentMethod").value;
      const note = document.getElementById("custNote").value.trim();

      let text = `*PESANAN BARU - KEDAI RASA*\n`;
      text += `---------------------------------\n`;
      text += `*Nama:* ${name}\n`;
      text += `*No. HP:* ${phone || '-'}\n`;
      text += `*Tipe Pesanan:* ${orderType} ${orderType === 'Dine-in' ? '(Meja ' + tableNo + ')' : ''}\n`;
      if (orderType === 'Delivery') text += `*Alamat:* ${address}\n`;
      text += `*Pembayaran:* ${paymentMethod}\n`;
      if (note) text += `*Catatan:* ${note}\n`;
      text += `---------------------------------\n`;
      text += `*DETAIL MENU:*\n`;

      let total = 0;
      cartKeys.forEach(key => {
        const item = cart[key];
        const subtotal = item.price * item.qty;
        total += subtotal;
        text += `• ${item.name} (${item.option}) x${item.qty} = ${formatRupiah(subtotal)}\n`;
      });

      text += `---------------------------------\n`;
      text += `*TOTAL BAYAR: ${formatRupiah(total)}*\n\n`;
      text += `Mohon konfirmasi pesanan saya. Terima kasih!`;

      const encoded = encodeURIComponent(text);
      window.open(`https://wa.me/${WHATSAPP_STORE_PHONE}?text=${encoded}`, '_blank');
    }

    // ===== RECEIPT MODAL & ACTIONS =====
    function openReceiptModal(order) {
      activeReceiptOrder = order;
      const modal = document.getElementById("receiptModal");
      const container = document.getElementById("printableReceipt");

      let itemsHtml = order.items.map(item => `
        <div style="display: flex; justify-content: space-between; margin-bottom: 3px;">
          <span>${escapeHtml(item.name)} (${escapeHtml(item.option)}) x${item.qty}</span>
          <span>${formatRupiah(item.subtotal)}</span>
        </div>
      `).join("");

      container.innerHTML = `
        <div style="text-align: center; margin-bottom: 8px;">
          <h2 style="font-size: 16px; font-weight: bold; margin: 0;">KEDAI RASA</h2>
          <p style="font-size: 10px; margin: 2px 0;">Jl. Kuliner No. 123, Nusantara</p>
          <p style="font-size: 10px; margin: 0;">WA: +${WHATSAPP_STORE_PHONE}</p>
        </div>
        <div style="border-top: 1px dashed #000; border-bottom: 1px dashed #000; padding: 4px 0; margin-bottom: 8px;">
          <p style="margin: 2px 0;">No. Antrean : <strong>#${String(order.queueNumber).padStart(3, '0')}</strong></p>
          <p style="margin: 2px 0;">Nama        : ${escapeHtml(order.customerName)}</p>
          <p style="margin: 2px 0;">Tipe        : ${order.orderType} ${order.tableNo !== '-' ? '(Meja ' + order.tableNo + ')' : ''}</p>
          <p style="margin: 2px 0;">Waktu       : ${order.createdAt}</p>
          <p style="margin: 2px 0;">Pembayaran  : ${order.paymentMethod}</p>
          <p style="margin: 2px 0;">Status Bayar: <strong>${order.isPaid ? 'LUNAS' : 'BELUM LUNAS'}</strong></p>
        </div>
        <div style="margin-bottom: 8px;">
          ${itemsHtml}
        </div>
        <div style="border-top: 1px dashed #000; padding-top: 4px;">
          <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 13px;">
            <span>TOTAL</span>
            <span>${formatRupiah(order.total)}</span>
          </div>
        </div>
        <div style="text-align: center; margin-top: 10px; font-size: 10px;">
          <p style="margin: 0;">Terima Kasih Atas Kunjungan Anda!</p>
          <p style="margin: 2px 0;">IG: ${INSTAGRAM_USER} | TikTok: ${TIKTOK_USER}</p>
        </div>
      `;

      modal.classList.remove("hidden");
    }

    function closeReceiptModal() {
      document.getElementById("receiptModal").classList.add("hidden");
      activeReceiptOrder = null;
    }

    function downloadReceiptAsImage() {
      const container = document.getElementById("printableReceipt");
      if (!container) return;

      html2canvas(container).then(canvas => {
        const link = document.createElement("a");
        link.download = `Struk-KedaiRasa-#${activeReceiptOrder ? activeReceiptOrder.queueNumber : 'Nota'}.png`;
        link.href = canvas.toDataURL("image/png");
        link.click();
        showToast("Gambar struk berhasil diunduh!", "📷");
      });
    }

    function sendReceiptToCustomerWA() {
      if (!activeReceiptOrder) return;
      
      let text = `*STRUK NOTA DIGITIAL - KEDAI RASA*\n`;
      text += `No. Antrean: #${String(activeReceiptOrder.queueNumber).padStart(3, '0')}\n`;
      text += `Nama: ${activeReceiptOrder.customerName}\n`;
      text += `Status Bayar: ${activeReceiptOrder.isPaid ? 'LUNAS' : 'BELUM LUNAS'}\n`;
      text += `Total: ${formatRupiah(activeReceiptOrder.total)}\n\n`;
      text += `Terima kasih telah memesan di Kedai Rasa!`;

      const targetPhone = activeReceiptOrder.customerPhone || WHATSAPP_STORE_PHONE;
      const cleanPhone = targetPhone.replace(/[^0-9]/g, '');
      const encoded = encodeURIComponent(text);
      window.open(`https://wa.me/${cleanPhone.startsWith('0') ? '62' + cleanPhone.slice(1) : cleanPhone}?text=${encoded}`, '_blank');
    }

    // ===== ADMIN DASHBOARD & MENU CRUD =====
    function renderAdminDashboard() {
      // Calculate Stats
      const todayTotal = ordersList
        .filter(o => o.isPaid && o.status !== "Dibatalkan")
        .reduce((sum, o) => sum + o.total, 0);

      const completedCount = ordersList.filter(o => o.status === "Selesai").length;
      const pendingCount = ordersList.filter(o => o.status === "Menunggu" || o.status === "Diproses").length;

      document.getElementById("statDailyRevenue").textContent = formatRupiah(todayTotal);
      document.getElementById("statCompletedOrders").textContent = `${completedCount} Pesanan`;
      document.getElementById("statPendingOrders").textContent = `${pendingCount} Pesanan`;

      renderAdminOrders();
      renderAdminMenuList();
    }

    function deleteOrder(queueNum) {
      if (confirm(`Hapus riwayat pesanan #${String(queueNum).padStart(3, '0')}?`)) {
        ordersList = ordersList.filter(o => o.queueNumber !== queueNum);
        saveToStorage();
        renderAll();
        showToast(`Pesanan #${String(queueNum).padStart(3, '0')} telah dihapus.`, "🗑️");
      }
    }

    function clearAllOrders() {
      if (confirm("Apakah Anda yakin ingin MENGHAPUS SEMUA riwayat pesanan? Data tidak dapat dikembalikan.")) {
        ordersList = [];
        saveToStorage();
        renderAll();
        showToast("Seluruh riwayat pesanan telah dibersihkan.", "🧹");
      }
    }

    function renderAdminOrders() {
      const container = document.getElementById("adminOrdersList");
      if (!container) return;

      if (ordersList.length === 0) {
        container.innerHTML = `<p class="text-xs text-gray-400 text-center py-6">Belum ada pesanan masuk.</p>`;
        return;
      }

      const clearAllHeaderHtml = `
        <div class="flex justify-between items-center pb-2 mb-2 border-b border-gray-100">
          <span class="text-xs text-gray-500 font-medium">Total ${ordersList.length} riwayat pesanan</span>
          <button onclick="clearAllOrders()" class="px-2.5 py-1 bg-red-100 hover:bg-red-200 text-red-700 rounded-lg text-[10px] font-bold transition flex items-center gap-1">
            <i class="fa-solid fa-broom"></i> Bersihkan Semua Riwayat
          </button>
        </div>
      `;

      const ordersHtml = ordersList.map(order => {
        const itemsDetail = order.items.map(i => `${i.name} (${i.option}) x${i.qty}`).join(", ");

        return `
          <div class="p-3 bg-gray-50 rounded-xl border border-gray-200 text-xs space-y-2">
            <div class="flex items-center justify-between">
              <div>
                <span class="font-bold text-sm text-brand-brown">#${String(order.queueNumber).padStart(3, '0')}</span>
                <span class="ml-2 font-semibold text-gray-700">${escapeHtml(order.customerName)} (${escapeHtml(order.customerPhone)})</span>
              </div>
              <div class="flex items-center gap-1">
                <button onclick="openReceiptModal(ordersList.find(o => o.queueNumber === ${order.queueNumber}))" 
                  class="px-2 py-1 bg-brand-brown text-white rounded text-[10px] font-bold">
                  <i class="fa-solid fa-receipt"></i> Struk
                </button>
                <button onclick="deleteOrder(${order.queueNumber})" 
                  class="p-1 bg-red-100 hover:bg-red-200 text-red-600 rounded text-[10px] font-bold transition" title="Hapus Riwayat">
                  <i class="fa-solid fa-trash"></i>
                </button>
              </div>
            </div>

            <p class="text-gray-600"><strong>Items:</strong> ${escapeHtml(itemsDetail)}</p>
            <p class="text-gray-500"><strong>Tipe:</strong> ${order.orderType} | <strong>Total:</strong> ${formatRupiah(order.total)}</p>
            ${order.note ? `<p class="text-amber-800 italic"><strong>Catatan:</strong> ${escapeHtml(order.note)}</p>` : ''}

            <div class="flex flex-wrap items-center justify-between gap-2 pt-1 border-t border-gray-200">
              <button onclick="togglePaymentStatus(${order.queueNumber})" 
                class="px-2.5 py-1 rounded-lg font-bold text-[10px] ${order.isPaid ? 'bg-emerald-100 text-emerald-800 border border-emerald-300' : 'bg-red-100 text-red-700 border border-red-300'}">
                Status: ${order.isPaid ? 'LUNAS (Klik ganti)' : 'BELUM LUNAS (Klik ganti)'}
              </button>

              <select onchange="updateOrderStatus(${order.queueNumber}, this.value)" 
                class="px-2 py-1 text-xs bg-white border border-gray-300 rounded-lg font-semibold text-gray-700 focus:outline-none">
                <option value="Menunggu" ${order.status === 'Menunggu' ? 'selected' : ''}>Menunggu</option>
                <option value="Diproses" ${order.status === 'Diproses' ? 'selected' : ''}>Diproses</option>
                <option value="Siap" ${order.status === 'Siap' ? 'selected' : ''}>Siap Diambil/Diantar</option>
                <option value="Selesai" ${order.status === 'Selesai' ? 'selected' : ''}>Selesai</option>
                <option value="Dibatalkan" ${order.status === 'Dibatalkan' ? 'selected' : ''}>Dibatalkan</option>
              </select>
            </div>
          </div>
        `;
      }).join("");

      container.innerHTML = clearAllHeaderHtml + ordersHtml;
    }

    function renderAdminMenuList() {
      const container = document.getElementById("adminMenuList");
      if (!container) return;

      container.innerHTML = menuList.map(item => `
        <div class="p-2.5 bg-gray-50 rounded-xl border border-gray-200 flex items-center justify-between text-xs">
          <div class="flex items-center gap-2">
            <span class="text-lg">${item.emoji || '🍽️'}</span>
            <div>
              <p class="font-bold text-gray-800">${escapeHtml(item.name)}</p>
              <p class="text-gray-500">${formatRupiah(item.price)} • Stok: ${item.stock}</p>
            </div>
          </div>

          <div class="flex items-center gap-1">
            <button onclick="editMenu(${item.id})" class="p-1.5 bg-amber-100 hover:bg-amber-200 text-amber-800 rounded-lg text-xs transition">
              <i class="fa-solid fa-pen-to-square"></i>
            </button>
            <button onclick="deleteMenu(${item.id})" class="p-1.5 bg-red-100 hover:bg-red-200 text-red-700 rounded-lg text-xs transition">
              <i class="fa-solid fa-trash"></i>
            </button>
          </div>
        </div>
      `).join("");
    }

    function handleImageUpload(e) {
      const file = e.target.files[0];
      if (!file) return;

      if (file.size > 800 * 1024) {
        showToast("Ukuran foto maksimal 800 KB!", "⚠️");
        e.target.value = "";
        return;
      }

      const reader = new FileReader();
      reader.onload = function (evt) {
        document.getElementById("menuImageData").value = evt.target.result;
      };
      reader.readAsDataURL(file);
    }

    function handleSaveMenu(e) {
      e.preventDefault();

      const editId = document.getElementById("editMenuId").value;
      const name = document.getElementById("menuName").value.trim();
      const category = document.getElementById("menuCategory").value;
      const emoji = document.getElementById("menuEmoji").value.trim() || "🍽️";
      const price = Number(document.getElementById("menuPrice").value);
      const stock = Number(document.getElementById("menuStock").value);
      const imageData = document.getElementById("menuImageData").value;
      const desc = document.getElementById("menuDesc").value.trim();

      if (!name || price < 0 || stock < 0) {
        showToast("Mohon isi data menu dengan benar!", "⚠️");
        return;
      }

      if (editId) {
        const item = menuList.find(m => m.id === Number(editId));
        if (item) {
          item.name = name;
          item.category = category;
          item.emoji = emoji;
          item.price = price;
          item.stock = stock;
          if (imageData) item.image = imageData;
          item.description = desc;
        }
      } else {
        const newItem = {
          id: Date.now(),
          name: name,
          category: category,
          price: price,
          stock: stock,
          description: desc,
          emoji: emoji,
          hasSpicyLevel: category === "makanan",
          image: imageData || ""
        };
        menuList.push(newItem);
      }

      saveToStorage();
      resetMenuCrudForm();
      renderAll();
      showToast("Menu berhasil disimpan!", "✅");
    }

    function editMenu(id) {
      const item = menuList.find(m => m.id === id);
      if (!item) return;

      document.getElementById("editMenuId").value = item.id;
      document.getElementById("menuName").value = item.name;
      document.getElementById("menuCategory").value = item.category;
      document.getElementById("menuEmoji").value = item.emoji || "🍽️";
      document.getElementById("menuPrice").value = item.price;
      document.getElementById("menuStock").value = item.stock;
      document.getElementById("menuDesc").value = item.description || "";
      document.getElementById("menuImageData").value = item.image || "";
      document.getElementById("menuFormTitle").querySelector("span").textContent = "Edit Menu";
    }

    function resetMenuCrudForm() {
      document.getElementById("menuCrudForm").reset();
      document.getElementById("editMenuId").value = "";
      document.getElementById("menuImageData").value = "";
      document.getElementById("menuFormTitle").querySelector("span").textContent = "Tambah Menu Baru";
    }

    function deleteMenu(id) {
      const item = menuList.find(m => m.id === id);
      if (!item) return;

      if (confirm(`Hapus menu "${item.name}"?`)) {
        menuList = menuList.filter(m => m.id !== id);
        saveToStorage();
        renderAll();
        showToast("Menu telah dihapus.", "🗑️");
      }
    }

    window.onload = function () {
      renderAll();
    };
  </script>
</body>
</html>
