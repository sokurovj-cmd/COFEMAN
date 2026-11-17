<!DOCTYPE html>
<html lang="ru" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>COFEMAN — Specialty Кофейня в Бишкеке</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,600;0,700;1,600&family=Manrope:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            espresso: {
              950: '#0A0807',
              900: '#120E0C',
              800: '#1B1512',
              700: '#271E19',
            },
            amberGold: {
              400: '#E5B567',
              500: '#D49A42',
              600: '#B87D28',
            },
            cream: {
              100: '#F7F3EE',
              200: '#E6DDD3',
              400: '#A6988B',
            }
          },
          fontFamily: {
            sans: ['Manrope', 'sans-serif'],
            serif: ['Cormorant Garamond', 'serif'],
          }
        }
      }
    };
  </script>
  <style>
    /* Custom scrollbar & subtle luxury styling */
    body {
      background-color: #0A0807;
      color: #F7F3EE;
      overflow-x: hidden;
    }
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #0A0807;
    }
    ::-webkit-scrollbar-thumb {
      background: #271E19;
      border-radius: 9999px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #D49A42;
    }
    .glass {
      background: rgba(18, 14, 12, 0.72);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(229, 181, 103, 0.14);
    }
    .glass-card {
      background: linear-gradient(145deg, rgba(27, 21, 18, 0.85), rgba(18, 14, 12, 0.95));
      border: 1px solid rgba(255, 255, 255, 0.06);
      transition: all 0.35s cubic-bezier(0.22, 1, 0.36, 1);
    }
    .glass-card:hover {
      border-color: rgba(212, 154, 66, 0.45);
      transform: translateY(-4px);
      box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.7), 0 0 25px -5px rgba(212, 154, 66, 0.12);
    }
    .gold-gradient-text {
      background: linear-gradient(135deg, #F7F3EE 15%, #E5B567 65%, #B87D28 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(18px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    .animate-fade-up {
      animation: fadeUp 0.7s ease-out forwards;
    }
  </style>
</head>
<body class="font-sans antialiased selection:bg-amberGold-500 selection:text-espresso-950">

  <!-- Toast Notification -->
  <div id="toast" class="fixed bottom-6 left-1/2 -translate-x-1/2 z-50 pointer-events-none opacity-0 translate-y-4 transition-all duration-300">
    <div class="glass px-5 py-3 rounded-2xl shadow-2xl flex items-center gap-3 border border-amberGold-500/40">
      <span class="w-2.5 h-2.5 rounded-full bg-amberGold-400 animate-pulse"></span>
      <span id="toastText" class="text-sm font-medium text-cream-100">Добавлено в заказ</span>
    </div>
  </div>

  <!-- Sticky Navbar -->
  <header class="fixed top-0 inset-x-0 z-40 transition-all duration-300 px-4 sm:px-6 pt-3 sm:pt-4">
    <nav class="max-w-7xl mx-auto glass rounded-2xl px-4 sm:px-6 py-3.5 flex items-center justify-between shadow-2xl">
      <!-- Brand Logo -->
      <a href="#" class="flex items-center gap-3 group">
        <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-amberGold-400 to-amberGold-600 flex items-center justify-center text-espresso-950 shadow-lg shadow-amberGold-500/20 group-hover:scale-105 transition-transform">
          <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M17 8h1a4 4 0 1 1 0 8h-1"/>
            <path d="M3 8h14v9a4 4 0 0 1-4 4H7a4 4 0 0 1-4-4Z"/>
            <line x1="6" x2="6" y1="2" y2="4"/>
            <line x1="10" x2="10" y1="2" y2="4"/>
            <line x1="14" x2="14" y1="2" y2="4"/>
          </svg>
        </div>
        <div>
          <span class="block text-lg sm:text-xl font-extrabold tracking-widest text-cream-100 leading-none">COFEMAN</span>
          <span class="block text-[10px] uppercase tracking-[0.25em] text-amberGold-400 mt-1">Specialty Roasters</span>
        </div>
      </a>

      <!-- Desktop Links -->
      <div class="hidden md:flex items-center gap-8 text-sm font-medium text-cream-200">
        <a href="#menu" class="hover:text-amberGold-400 transition-colors">Меню</a>
        <a href="#features" class="hover:text-amberGold-400 transition-colors">Почему мы</a>
        <a href="#atmosphere" class="hover:text-amberGold-400 transition-colors">Атмосфера</a>
        <a href="#contacts" class="hover:text-amberGold-400 transition-colors">Контакты</a>
      </div>

      <!-- Actions -->
      <div class="flex items-center gap-2.5 sm:gap-3">
        <button onclick="openBookingModal()" class="hidden sm:inline-flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold text-cream-100 border border-white/15 hover:border-amberGold-400/60 hover:bg-white/5 transition-all">
          Бронь стола
        </button>

        <button onclick="toggleCart(true)" class="relative inline-flex items-center gap-2.5 px-4 py-2.5 rounded-xl bg-gradient-to-r from-amberGold-400 to-amberGold-500 text-espresso-950 font-bold text-xs sm:text-sm shadow-lg shadow-amberGold-500/25 hover:brightness-110 active:scale-95 transition-all">
          <svg class="w-4 h-4 sm:w-5 sm:h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2">
            <path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4Z"/>
            <path d="M3 6h18"/>
            <path d="M16 10a4 4 0 0 1-8 0"/>
          </svg>
          <span class="hidden sm:inline">Заказ</span>
          <span id="cartBadge" class="inline-flex items-center justify-center min-w-[20px] h-5 px-1.5 rounded-full bg-espresso-950 text-amberGold-400 text-xs font-extrabold">0</span>
        </button>
      </div>
    </nav>
  </header>

  <!-- Hero Section -->
  <section class="relative min-h-screen flex items-center pt-28 pb-16 px-4 sm:px-6 overflow-hidden">
    <!-- Background Image with Dark Gradient Overlay -->
    <div class="absolute inset-0 z-0">
      <img 
        src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?auto=format&fit=crop&w=1920&q=85" 
        onerror="this.src='https://placehold.co/1920x1080/120E0C/D49A42?text=COFEMAN+Bishkek'"
        alt="COFEMAN Спешелти Кофейня" 
        class="w-full h-full object-cover object-center scale-105 opacity-45"
      />
      <div class="absolute inset-0 bg-gradient-to-r from-espresso-950 via-espresso-950/90 to-espresso-950/55"></div>
      <div class="absolute inset-0 bg-gradient-to-t from-espresso-950 via-transparent to-espresso-950/75"></div>
    </div>

    <!-- Ambient Glow -->
    <div class="absolute -top-24 -left-24 w-96 h-96 bg-amberGold-500/15 rounded-full blur-[120px] pointer-events-none"></div>

    <div class="relative z-10 max-w-7xl mx-auto w-full grid lg:grid-cols-12 gap-10 items-center">
      <div class="lg:col-span-7 space-y-6 sm:space-y-8 animate-fade-up">
        <div class="inline-flex items-center gap-2.5 px-4 py-2 rounded-full glass border border-amberGold-400/30 text-xs sm:text-sm font-medium text-amberGold-400">
          <span class="w-2 h-2 rounded-full bg-amberGold-400 animate-ping"></span>
          Свежая обжарка каждый вторник • Бишкек
        </div>

        <h1 class="text-4xl sm:text-6xl lg:text-7xl font-extrabold tracking-tight leading-[1.08]">
          <span class="block text-cream-100">COFEMAN —</span>
          <span class="font-serif italic font-bold gold-gradient-text text-5xl sm:text-7xl lg:text-[82px]">искусство кофе</span>
          <span class="block text-cream-100 mt-1">в ритме города</span>
        </h1>

        <p class="text-base sm:text-lg text-cream-400 max-w-xl leading-relaxed">
          Авторские напитки на зерне класса Specialty 85+, свежая французская выпечка и эстетика уюта в самом центре Бишкека. Оформите предзаказ онлайн — заберите без очереди.
        </p>

        <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-3.5 pt-2">
          <a href="#menu" class="inline-flex items-center justify-center gap-2.5 px-7 py-4 rounded-2xl bg-gradient-to-r from-amberGold-400 to-amberGold-500 text-espresso-950 font-extrabold text-sm sm:text-base shadow-xl shadow-amberGold-500/20 hover:brightness-110 transition-all">
            <span>Выбрать кофе</span>
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2">
              <path d="M5 12h14"/><path d="m12 5 7 7-7 7"/>
            </svg>
          </a>

          <button onclick="openBookingModal()" class="inline-flex items-center justify-center gap-2.5 px-7 py-4 rounded-2xl glass text-cream-100 font-bold text-sm sm:text-base hover:border-amberGold-400/50 hover:bg-white/5 transition-all">
            <svg class="w-5 h-5 text-amberGold-400" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <rect width="18" height="18" x="3" y="4" rx="2" ry="2"/><line x1="16" x2="16" y1="2" y2="6"/><line x1="8" x2="8" y1="2" y2="6"/><line x1="3" x2="21" y1="10" y2="10"/>
            </svg>
            <span>Забронировать столик</span>
          </button>
        </div>

        <!-- Mini Stats -->
        <div class="grid grid-cols-3 gap-4 pt-6 border-t border-white/10 max-w-lg">
          <div>
            <div class="text-2xl sm:text-3xl font-extrabold text-amberGold-400">100%</div>
            <div class="text-xs text-cream-400 mt-0.5">Арабика Specialty</div>
          </div>
          <div>
            <div class="text-2xl sm:text-3xl font-extrabold text-cream-100">7 мин</div>
            <div class="text-xs text-cream-400 mt-0.5">Средняя выдача</div>
          </div>
          <div>
            <div class="text-2xl sm:text-3xl font-extrabold text-cream-100">4.9 ★</div>
            <div class="text-xs text-cream-400 mt-0.5">Оценка в 2ГИС</div>
          </div>
        </div>
      </div>

      <!-- Featured Drink Card on Hero -->
      <div class="lg:col-span-5 hidden lg:block">
        <div class="glass-card rounded-3xl p-6 relative overflow-hidden">
          <div class="absolute top-4 right-4 z-10 px-3 py-1 rounded-full bg-amberGold-500 text-espresso-950 text-xs font-extrabold uppercase tracking-wider">
            Хит недели
          </div>
          <div class="rounded-2xl overflow-hidden h-72 mb-5">
            <img 
              src="https://images.unsplash.com/photo-1572442388796-11668a67e53d?auto=format&fit=crop&w=800&q=80" 
              onerror="this.src='https://placehold.co/800x600/1B1512/E5B567?text=Raf+Caramel'"
              alt="Раф Соленая Карамель" 
              class="w-full h-full object-cover hover:scale-105 transition-transform duration-700"
            />
          </div>
          <div class="flex items-start justify-between gap-4">
            <div>
              <h3 class="text-xl font-bold text-cream-100">Раф Солёная Карамель</h3>
              <p class="text-sm text-cream-400 mt-1">Двойной эспрессо из Эфиопии, фермерские сливки и домашняя карамель с морской солью.</p>
            </div>
            <span class="text-xl font-extrabold text-amberGold-400 whitespace-nowrap">250 сом</span>
          </div>
          <button onclick="addToCartById(1)" class="mt-5 w-full py-3.5 rounded-xl bg-white/10 hover:bg-amberGold-500 hover:text-espresso-950 text-cream-100 font-bold text-sm transition-all flex items-center justify-center gap-2">
            <span>+ Добавить в мой заказ</span>
          </button>
        </div>
      </div>
    </div>
  </section>

  <!-- Features Section -->
  <section id="features" class="py-16 sm:py-24 px-4 sm:px-6 border-t border-white/5">
    <div class="max-w-7xl mx-auto">
      <div class="text-center max-w-2xl mx-auto mb-12 sm:mb-16">
        <span class="text-xs font-bold uppercase tracking-[0.25em] text-amberGold-400">Философия вкуса</span>
        <h2 class="text-3xl sm:text-5xl font-extrabold text-cream-100 mt-3">Почему выбирают COFEMAN</h2>
      </div>

      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-5">
        <div class="glass-card rounded-3xl p-6 sm:p-7">
          <div class="w-12 h-12 rounded-2xl bg-amberGold-500/15 text-amberGold-400 flex items-center justify-center mb-5">
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M12 2a10 10 0 1 0 10 10 4 4 0 0 1-5-5 4 4 0 0 1-5-5"/>
              <path d="M8.5 8.5v.01"/><path d="M16 15.5v.01"/><path d="M12 12v.01"/>
            </svg>
          </div>
          <h3 class="text-lg font-bold text-cream-100 mb-2">Зерно Specialty 85+</h3>
          <p class="text-sm text-cream-400 leading-relaxed">Прямые поставки лотов из Эфиопии, Колумбии и Бразилии с высокой оценкой Q-грейдеров.</p>
        </div>

        <div class="glass-card rounded-3xl p-6 sm:p-7">
          <div class="w-12 h-12 rounded-2xl bg-amberGold-500/15 text-amberGold-400 flex items-center justify-center mb-5">
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/>
            </svg>
          </div>
          <h3 class="text-lg font-bold text-cream-100 mb-2">Предзаказ без очереди</h3>
          <p class="text-sm text-cream-400 leading-relaxed">Соберите заказ на сайте за 30 секунд — бариста приготовит напиток ровно к вашему приходу.</p>
        </div>

        <div class="glass-card rounded-3xl p-6 sm:p-7">
          <div class="w-12 h-12 rounded-2xl bg-amberGold-500/15 text-amberGold-400 flex items-center justify-center mb-5">
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M12 20h9"/><path d="M16.5 3.5a2.12 2.12 0 0 1 3 3L7 19l-4 1 1-4Z"/>
            </svg>
          </div>
          <h3 class="text-lg font-bold text-cream-100 mb-2">Авторские рецепты</h3>
          <p class="text-sm text-cream-400 leading-relaxed">Варим натуральные сиропы сами: без химии, только ягоды, специи, тростниковый сахар и мед.</p>
        </div>

        <div class="glass-card rounded-3xl p-6 sm:p-7">
          <div class="w-12 h-12 rounded-2xl bg-amberGold-500/15 text-amberGold-400 flex items-center justify-center mb-5">
            <svg class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M5 12.55a11 11 0 0 1 14.08 0"/><path d="M1.42 9a16 16 0 0 1 21.16 0"/><path d="M8.53 16.11a6 6 0 0 1 6.95 0"/><line x1="12" x2="12.01" y1="20" y2="20"/>
            </svg>
          </div>
          <h3 class="text-lg font-bold text-cream-100 mb-2">Работа и отдых</h3>
          <p class="text-sm text-cream-400 leading-relaxed">Быстрый Wi-Fi 300 Мбит/с, розетки у каждого стола и приглушенный вечерний свет.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Interactive Menu Section -->
  <section id="menu" class="py-16 sm:py-24 px-4 sm:px-6 bg-espresso-900/50 border-t border-white/5">
    <div class="max-w-7xl mx-auto">
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-6 mb-10">
        <div>
          <span class="text-xs font-bold uppercase tracking-[0.25em] text-amberGold-400">Карта напитков и кухни</span>
          <h2 class="text-3xl sm:text-5xl font-extrabold text-cream-100 mt-2">Наше меню</h2>
        </div>

        <!-- Category Filter Tabs -->
        <div id="categoryTabs" class="flex items-center gap-2 overflow-x-auto no-scrollbar pb-1">
          <!-- Rendered by JS -->
        </div>
      </div>

      <!-- Menu Grid -->
      <div id="menuGrid" class="grid sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <!-- Rendered by JS -->
      </div>
    </div>
  </section>

  <!-- Atmosphere & Quick Booking Banner -->
  <section id="atmosphere" class="py-16 sm:py-24 px-4 sm:px-6 border-t border-white/5">
    <div class="max-w-7xl mx-auto grid lg:grid-cols-12 gap-8 items-center">
      <div class="lg:col-span-6 grid grid-cols-2 gap-4">
        <div class="space-y-4">
          <img 
            src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?auto=format&fit=crop&w=700&q=80" 
            onerror="this.src='https://placehold.co/600x800/1B1512/E5B567?text=Interior'"
            alt="Интерьер COFEMAN" 
            class="rounded-3xl h-64 sm:h-80 w-full object-cover border border-white/10"
          />
          <div class="glass-card rounded-3xl p-5">
            <div class="text-2xl font-extrabold text-amberGold-400">07:30 — 23:00</div>
            <div class="text-xs text-cream-400 mt-1">Работаем ежедневно без выходных</div>
          </div>
        </div>
        <div class="space-y-4 pt-8">
          <div class="glass-card rounded-3xl p-5">
            <div class="text-lg font-bold text-cream-100">Альтернативное молоко</div>
            <div class="text-xs text-cream-400 mt-1">Кокосовое, миндальное, овсяное или банановое (+50 сом)</div>
          </div>
          <img 
            src="https://images.unsplash.com/photo-1511920170033-f8396924c348?auto=format&fit=crop&w=700&q=80" 
            onerror="this.src='https://placehold.co/600x800/1B1512/E5B567?text=Barista+Art'"
            alt="Латте арт COFEMAN" 
            class="rounded-3xl h-64 sm:h-80 w-full object-cover border border-white/10"
          />
        </div>
      </div>

      <div class="lg:col-span-6 lg:pl-8 space-y-6">
        <span class="text-xs font-bold uppercase tracking-[0.25em] text-amberGold-400">Атмосфера</span>
        <h2 class="text-3xl sm:text-5xl font-extrabold text-cream-100 leading-tight">
          Место для утренних ритуалов и важных встреч
        </h2>
        <p class="text-cream-400 text-base leading-relaxed">
          В <strong class="text-cream-100">COFEMAN</strong> мы объединили эстетику минимализма, аромат свежесмолотого кофе и сервис, в который хочется возвращаться. Заходите на быстрый утренний фильтр или бронируйте столик у панорамного окна на вечер.
        </p>

        <div class="glass-card rounded-3xl p-6 sm:p-7 space-y-4">
          <h3 class="text-lg font-bold text-cream-100">Быстрая бронь столика в WhatsApp</h3>
          <div class="grid sm:grid-cols-3 gap-3">
            <input id="inlineBookName" type="text" placeholder="Ваше имя" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 placeholder-cream-400 focus:outline-none focus:border-amberGold-400" />
            <input id="inlineBookTime" type="text" placeholder="Сегодня в 19:00" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 placeholder-cream-400 focus:outline-none focus:border-amberGold-400" />
            <select id="inlineBookGuests" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 focus:outline-none focus:border-amberGold-400">
              <option value="2 гостя">2 гостя</option>
              <option value="1 гость">1 гость</option>
              <option value="3-4 гостя">3–4 гостя</option>
              <option value="Компания 5+">Компания 5+</option>
            </select>
          </div>
          <button onclick="sendQuickBooking()" class="w-full py-3.5 rounded-xl bg-gradient-to-r from-amberGold-400 to-amberGold-500 text-espresso-950 font-extrabold text-sm hover:brightness-110 transition-all">
            Забронировать через WhatsApp
          </button>
        </div>
      </div>
    </div>
  </section>

  <!-- Contacts & Footer -->
  <footer id="contacts" class="bg-espresso-900 border-t border-white/10 pt-16 pb-10 px-4 sm:px-6">
    <div class="max-w-7xl mx-auto">
      <div class="grid md:grid-cols-3 gap-10 pb-12 border-b border-white/10">
        <!-- Brand -->
        <div class="space-y-4">
          <div class="flex items-center gap-3">
            <div class="w-10 h-10 rounded-xl bg-amberGold-500 flex items-center justify-center text-espresso-950 font-black text-lg">C</div>
            <span class="text-xl font-extrabold tracking-widest text-cream-100">COFEMAN</span>
          </div>
          <p class="text-sm text-cream-400 leading-relaxed max-w-sm">
            Спешелти-кофейня нового формата в Бишкеке. Честное зерно, авторские напитки и безупречный сервис каждый день.
          </p>
        </div>

        <!-- Location -->
        <div class="space-y-3">
          <h4 class="text-sm font-bold uppercase tracking-wider text-amberGold-400">Ждём вас в гости</h4>
          <p class="text-cream-100 font-semibold">г. Бишкек, пр. Чуй, 155 / ул. Киевская</p>
          <p class="text-sm text-cream-400">Ежедневно: 07:30 — 23:00</p>
          <div class="pt-2 flex flex-wrap gap-3">
            <a href="https://2gis.kg/bishkek" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 px-4 py-2 rounded-xl bg-white/5 hover:bg-white/10 border border-white/10 text-xs font-semibold text-cream-100 transition-all">
              <span>Открыть в 2ГИС</span>
              <span>↗</span>
            </a>
          </div>
        </div>

        <!-- Socials -->
        <div class="space-y-3">
          <h4 class="text-sm font-bold uppercase tracking-wider text-amberGold-400">Связь и предзаказ</h4>
          <p class="text-cream-100 font-semibold text-lg">+996 (506) 696-697</p>
          <div class="flex items-center gap-3 pt-1">
            <a href="https://wa.me/996506696697" target="_blank" rel="noopener noreferrer" class="px-4 py-2.5 rounded-xl bg-emerald-600/20 border border-emerald-500/40 text-emerald-300 hover:bg-emerald-600/30 text-xs font-bold transition-all">
              WhatsApp
            </a>
            <a href="https://instagram.com" target="_blank" rel="noopener noreferrer" class="px-4 py-2.5 rounded-xl bg-amberGold-500/15 border border-amberGold-500/40 text-amberGold-400 hover:bg-amberGold-500/25 text-xs font-bold transition-all">
              Instagram
            </a>
          </div>
        </div>
      </div>

      <div class="pt-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-cream-400">
        <p>© 2026 COFEMAN Bishkek. Все права защищены.</p>
        <p class="text-cream-400/70">Демо-проект сайта премиум-уровня</p>
      </div>
    </div>
  </footer>

  <!-- Slide-Over Cart Drawer -->
  <div id="cartDrawer" class="fixed inset-0 z-50 hidden">
    <div onclick="toggleCart(false)" class="absolute inset-0 bg-black/75 backdrop-blur-sm"></div>
    <div class="absolute right-0 top-0 bottom-0 w-full max-w-md bg-espresso-900 border-l border-white/10 shadow-2xl flex flex-col">
      <!-- Header -->
      <div class="p-5 sm:p-6 border-b border-white/10 flex items-center justify-between">
        <div>
          <h3 class="text-xl font-extrabold text-cream-100">Ваш заказ</h3>
          <p class="text-xs text-cream-400 mt-0.5">Отправка напрямую бариста в WhatsApp</p>
        </div>
        <button onclick="toggleCart(false)" class="w-10 h-10 rounded-xl bg-white/5 hover:bg-white/10 flex items-center justify-center text-cream-200">
          ✕
        </button>
      </div>

      <!-- Items List -->
      <div id="cartItemsContainer" class="flex-1 overflow-y-auto p-5 sm:p-6 space-y-4">
        <!-- Rendered by JS -->
      </div>

      <!-- Checkout Form -->
      <div id="cartFooter" class="p-5 sm:p-6 border-t border-white/10 bg-espresso-950/90 space-y-4">
        <div class="grid grid-cols-2 gap-2 p-1 rounded-xl bg-espresso-800">
          <button type="button" onclick="setOrderType('С собой')" id="btnTakeaway" class="py-2 rounded-lg text-xs font-bold bg-amberGold-500 text-espresso-950 transition-all">
            С собой
          </button>
          <button type="button" onclick="setOrderType('В кофейне')" id="btnDineIn" class="py-2 rounded-lg text-xs font-bold text-cream-300 hover:text-white transition-all">
            В кофейне
          </button>
        </div>

        <div class="grid grid-cols-2 gap-2.5">
          <input id="customerName" type="text" placeholder="Ваше имя" class="px-3.5 py-2.5 rounded-xl bg-espresso-800 border border-white/10 text-sm text-cream-100 placeholder-cream-400 focus:outline-none focus:border-amberGold-400" />
          <input id="pickupTime" type="text" placeholder="Через 15 мин" class="px-3.5 py-2.5 rounded-xl bg-espresso-800 border border-white/10 text-sm text-cream-100 placeholder-cream-400 focus:outline-none focus:border-amberGold-400" />
        </div>

        <div class="flex items-center justify-between pt-1">
          <span class="text-sm text-cream-400">Итого к оплате:</span>
          <span id="cartTotal" class="text-2xl font-extrabold text-amberGold-400">0 сом</span>
        </div>

        <button onclick="checkoutWhatsApp()" class="w-full py-4 rounded-2xl bg-gradient-to-r from-amberGold-400 to-amberGold-500 text-espresso-950 font-extrabold text-sm shadow-lg shadow-amberGold-500/20 hover:brightness-110 transition-all flex items-center justify-center gap-2">
          <span>Оформить заказ в WhatsApp</span>
          <span>→</span>
        </button>
      </div>
    </div>
  </div>

  <!-- Table Booking Modal -->
  <div id="bookingModal" class="fixed inset-0 z-50 hidden items-center justify-center p-4">
    <div onclick="closeBookingModal()" class="absolute inset-0 bg-black/80 backdrop-blur-sm"></div>
    <div class="relative z-10 w-full max-w-md glass rounded-3xl p-6 sm:p-8 border border-amberGold-400/30 shadow-2xl space-y-5">
      <div class="flex items-center justify-between">
        <div>
          <span class="text-xs font-bold uppercase tracking-widest text-amberGold-400">COFEMAN Бронь</span>
          <h3 class="text-2xl font-extrabold text-cream-100 mt-1">Забронировать столик</h3>
        </div>
        <button onclick="closeBookingModal()" class="w-9 h-9 rounded-xl bg-white/10 flex items-center justify-center text-cream-200">✕</button>
      </div>

      <div class="space-y-3.5">
        <div>
          <label class="block text-xs text-cream-400 mb-1">Ваше имя</label>
          <input id="modalName" type="text" placeholder="Например, Азамат" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 focus:outline-none focus:border-amberGold-400" />
        </div>
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block text-xs text-cream-400 mb-1">Время визита</label>
            <input id="modalTime" type="text" placeholder="18:30" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 focus:outline-none focus:border-amberGold-400" />
          </div>
          <div>
            <label class="block text-xs text-cream-400 mb-1">Количество гостей</label>
            <select id="modalGuests" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 focus:outline-none focus:border-amberGold-400">
              <option value="2 гостя">2 гостя</option>
              <option value="1 гость">1 гость</option>
              <option value="3-4 гостя">3–4 гостя</option>
              <option value="5+ гостей">5+ гостей</option>
            </select>
          </div>
        </div>
        <div>
          <label class="block text-xs text-cream-400 mb-1">Пожелания (необязательно)</label>
          <input id="modalNote" type="text" placeholder="Столик у окна / с розеткой" class="w-full px-4 py-3 rounded-xl bg-espresso-950 border border-white/10 text-sm text-cream-100 focus:outline-none focus:border-amberGold-400" />
        </div>
      </div>

      <button onclick="submitModalBooking()" class="w-full py-4 rounded-2xl bg-gradient-to-r from-amberGold-400 to-amberGold-500 text-espresso-950 font-extrabold text-sm hover:brightness-110 transition-all">
        Подтвердить в WhatsApp
      </button>
    </div>
  </div>

  <script>
    // Phone number for WhatsApp orders
    const WHATSAPP_PHONE = '996506696697';

    // Menu Data (Bishkek Coffee Shop Pricing in KGS)
    const menuItems = [
      {
        id: 1,
        name: 'Раф Солёная Карамель',
        category: 'Авторский кофе',
        volume: '300 мл',
        price: 250,
        badge: 'Хит',
        desc: 'Сливочный раф на двойном эспрессо с домашней карамелью и морской солью.',
        img: 'https://images.unsplash.com/photo-1572442388796-11668a67e53d?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 2,
        name: 'Латте Фисташка-Халва',
        category: 'Авторский кофе',
        volume: '350 мл',
        price: 270,
        badge: 'Новинка',
        desc: 'Нежный молочный напиток с натуральной пастой иранской фисташки и крошкой халвы.',
        img: 'https://images.unsplash.com/photo-1534778101976-62847782c213?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 3,
        name: 'Капучино Классический',
        category: 'Классика',
        volume: '250 мл',
        price: 190,
        badge: '',
        desc: 'Сбалансированный эспрессо из 100% арабики Бразилия Серрадо и шелковистая молочная пена.',
        img: 'https://images.unsplash.com/photo-1572442388796-11668a67e53d?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 4,
        name: 'Флэт Уайт',
        category: 'Классика',
        volume: '200 мл',
        price: 210,
        badge: 'Выбор бариста',
        desc: 'Яркий кофейный вкус на двойном ристретто с тонким слоем глянцевого молока.',
        img: 'https://images.unsplash.com/photo-1577968897966-3d4325b36b61?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 5,
        name: 'Бамбл Кофе Апельсин',
        category: 'Холодные напитки',
        volume: '350 мл',
        price: 240,
        badge: 'Освежает',
        desc: 'Свежевыжатый апельсиновый сок, карамельный сироп, лёд и шот яркого эспрессо.',
        img: 'https://images.unsplash.com/photo-1517701550927-30cf4ba1dba5?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 6,
        name: 'Эспрессо-Тоник Юдзу',
        category: 'Холодные напитки',
        volume: '330 мл',
        price: 230,
        badge: '',
        desc: 'Игристый тоник, цитрусовый юдзу и фруктовый эспрессо из Эфиопии.',
        img: 'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 7,
        name: 'Чизкейк Сан-Себастьян',
        category: 'Десерты и выпечка',
        volume: '160 г',
        price: 260,
        badge: 'Хит',
        desc: 'Нежный обожжённый баскский чизкейк с кремовой серединкой и тёплым шоколадом.',
        img: 'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?auto=format&fit=crop&w=600&q=80'
      },
      {
        id: 8,
        name: 'Миндальный Круассан',
        category: 'Десерты и выпечка',
        volume: '130 г',
        price: 180,
        badge: 'Свежая выпечка',
        desc: 'Хрустящее слоёное тесто на сливочном масле с миндальным франжипаном и лепестками.',
        img: 'https://images.unsplash.com/photo-1555507036-ab1f4038808a?auto=format&fit=crop&w=600&q=80'
      }
    ];

    const categories = ['Все', 'Авторский кофе', 'Классика', 'Холодные напитки', 'Десерты и выпечка'];
    let activeCategory = 'Все';
    let cart = [];
    let orderType = 'С собой';

    // Render Category Tabs
    function renderCategories() {
      const container = document.getElementById('categoryTabs');
      container.innerHTML = categories.map(cat => {
        const isActive = cat === activeCategory;
        return `
          <button
            onclick="selectCategory('${cat}')"
            class="px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold whitespace-nowrap transition-all ${
              isActive
                ? 'bg-amberGold-500 text-espresso-950 shadow-lg shadow-amberGold-500/20'
                : 'glass text-cream-200 hover:border-amberGold-400/40'
            }"
          >
            ${cat}
          </button>
        `;
      }).join('');
    }

    function selectCategory(cat) {
      activeCategory = cat;
      renderCategories();
      renderMenu();
    }

    // Render Menu Grid
    function renderMenu() {
      const grid = document.getElementById('menuGrid');
      const filtered = activeCategory === 'Все'
        ? menuItems
        : menuItems.filter(item => item.category === activeCategory);

      grid.innerHTML = filtered.map(item => `
        <div class="glass-card rounded-3xl overflow-hidden flex flex-col justify-between group">
          <div>
            <div class="relative h-52 overflow-hidden bg-espresso-800">
              <img
                src="${item.img}"
                onerror="this.src='https://placehold.co/600x400/1B1512/E5B567?text=COFEMAN'"
                alt="${item.name}"
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-espresso-900 via-transparent to-transparent opacity-80"></div>
              ${item.badge ? `
                <span class="absolute top-3 left-3 px-3 py-1 rounded-full bg-espresso-950/85 border border-amberGold-400/40 text-amberGold-400 text-[11px] font-bold">
                  ${item.badge}
                </span>
              ` : ''}
              <span class="absolute bottom-3 right-3 px-2.5 py-1 rounded-lg bg-black/60 text-cream-200 text-xs font-medium">
                ${item.volume}
              </span>
            </div>

            <div class="p-5 pb-3">
              <div class="text-[11px] uppercase tracking-wider text-amberGold-400/80 font-semibold mb-1">${item.category}</div>
              <h3 class="text-lg font-bold text-cream-100 leading-snug">${item.name}</h3>
              <p class="text-xs text-cream-400 mt-2 leading-relaxed">${item.desc}</p>
            </div>
          </div>

          <div class="p-5 pt-3 flex items-center justify-between border-t border-white/5 mt-2">
            <div>
              <span class="text-xl font-extrabold text-cream-100">${item.price}</span>
              <span class="text-xs font-bold text-amberGold-400 ml-0.5">сом</span>
            </div>
            <button
              onclick="addToCartById(${item.id})"
              class="px-4 py-2.5 rounded-xl bg-amberGold-500/15 hover:bg-amberGold-500 text-amberGold-400 hover:text-espresso-950 border border-amberGold-500/30 font-bold text-xs transition-all active:scale-95"
            >
              + В заказ
            </button>
          </div>
        </div>
      `).join('');
    }

    // Cart Operations
    function addToCartById(id) {
      const product = menuItems.find(i => i.id === id);
      if (!product) return;

      const existing = cart.find(i => i.id === id);
      if (existing) {
        existing.qty += 1;
      } else {
        cart.push({ ...product, qty: 1 });
      }
      updateCartUI();
      showToast(`«${product.name}» добавлен в заказ`);
    }

    function changeQty(id, delta) {
      const idx = cart.findIndex(i => i.id === id);
      if (idx === -1) return;
      cart[idx].qty += delta;
      if (cart[idx].qty <= 0) {
        cart.splice(idx, 1);
      }
      updateCartUI();
    }

    function updateCartUI() {
      const totalCount = cart.reduce((sum, item) => sum + item.qty, 0);
      const totalSum = cart.reduce((sum, item) => sum + item.price * item.qty, 0);

      document.getElementById('cartBadge').textContent = totalCount;
      document.getElementById('cartTotal').textContent = `${totalSum} сом`;

      const container = document.getElementById('cartItemsContainer');
      const footer = document.getElementById('cartFooter');

      if (cart.length === 0) {
        footer.classList.add('hidden');
        container.innerHTML = `
          <div class="h-full flex flex-col items-center justify-center text-center py-16 space-y-3">
            <div class="w-16 h-16 rounded-2xl bg-white/5 flex items-center justify-center text-amberGold-400 text-2xl">☕</div>
            <h4 class="text-lg font-bold text-cream-100">Корзина пока пуста</h4>
            <p class="text-xs text-cream-400 max-w-xs">Выберите любимый кофе или десерт из меню, чтобы оформить быстрый предзаказ.</p>
          </div>
        `;
        return;
      }

      footer.classList.remove('hidden');
      container.innerHTML = cart.map(item => `
        <div class="p-3.5 rounded-2xl bg-espresso-800/80 border border-white/5 flex items-center justify-between gap-3">
          <div class="min-w-0">
            <h4 class="text-sm font-bold text-cream-100 truncate">${item.name}</h4>
            <p class="text-xs text-amberGold-400 font-semibold mt-0.5">${item.price * item.qty} сом <span class="text-cream-400 font-normal">(${item.volume})</span></p>
          </div>
          <div class="flex items-center gap-2 bg-espresso-950 rounded-xl p-1 border border-white/10">
            <button onclick="changeQty(${item.id}, -1)" class="w-7 h-7 rounded-lg hover:bg-white/10 text-cream-200 font-bold text-sm">−</button>
            <span class="w-5 text-center text-xs font-extrabold text-cream-100">${item.qty}</span>
            <button onclick="changeQty(${item.id}, 1)" class="w-7 h-7 rounded-lg hover:bg-white/10 text-amberGold-400 font-bold text-sm">+</button>
          </div>
        </div>
      `).join('');
    }

    function setOrderType(type) {
      orderType = type;
      const btnTakeaway = document.getElementById('btnTakeaway');
      const btnDineIn = document.getElementById('btnDineIn');
      if (type === 'С собой') {
        btnTakeaway.className = 'py-2 rounded-lg text-xs font-bold bg-amberGold-500 text-espresso-950 transition-all';
        btnDineIn.className = 'py-2 rounded-lg text-xs font-bold text-cream-300 hover:text-white transition-all';
      } else {
        btnDineIn.className = 'py-2 rounded-lg text-xs font-bold bg-amberGold-500 text-espresso-950 transition-all';
        btnTakeaway.className = 'py-2 rounded-lg text-xs font-bold text-cream-300 hover:text-white transition-all';
      }
    }

    function checkoutWhatsApp() {
      if (cart.length === 0) return;

      const name = document.getElementById('customerName').value.trim() || 'Гость';
      const time = document.getElementById('pickupTime').value.trim() || 'Как можно скорее';
      const totalSum = cart.reduce((sum, item) => sum + item.price * item.qty, 0);

      const itemsLines = cart.map((item, idx) =>
        `${idx + 1}. ${item.name} (${item.volume}) × ${item.qty} = ${item.price * item.qty} сом`
      ).join('\n');

      const message =
`☕ *Новый предзаказ — COFEMAN*
━━━━━━━━━━━━━━
👤 Имя: ${name}
🛍 Формат: ${orderType}
⏰ Время: ${time}

*Состав заказа:*
${itemsLines}

💰 *Итого: ${totalSum} сом*`;

      const url = `https://wa.me/${WHATSAPP_PHONE}?text=${encodeURIComponent(message)}`;
      window.open(url, '_blank', 'noopener,noreferrer');
    }

    // Drawer & Modal Controls
    function toggleCart(open) {
      const drawer = document.getElementById('cartDrawer');
      if (open) {
        drawer.classList.remove('hidden');
        document.body.style.overflow = 'hidden';
      } else {
        drawer.classList.add('hidden');
        document.body.style.overflow = '';
      }
    }

    function openBookingModal() {
      const modal = document.getElementById('bookingModal');
      modal.classList.remove('hidden');
      modal.classList.add('flex');
    }

    function closeBookingModal() {
      const modal = document.getElementById('bookingModal');
      modal.classList.add('hidden');
      modal.classList.remove('flex');
    }

    function sendQuickBooking() {
      const name = document.getElementById('inlineBookName').value.trim() || 'Гость';
      const time = document.getElementById('inlineBookTime').value.trim() || 'Сегодня';
      const guests = document.getElementById('inlineBookGuests').value;

      const msg =
`🪑 *Бронь столика — COFEMAN*
━━━━━━━━━━━━━━
👤 Имя: ${name}
👥 Гостей: ${guests}
⏰ Время: ${time}`;

      window.open(`https://wa.me/${WHATSAPP_PHONE}?text=${encodeURIComponent(msg)}`, '_blank', 'noopener,noreferrer');
    }

    function submitModalBooking() {
      const name = document.getElementById('modalName').value.trim() || 'Гость';
      const time = document.getElementById('modalTime').value.trim() || 'Сегодня';
      const guests = document.getElementById('modalGuests').value;
      const note = document.getElementById('modalNote').value.trim();

      const msg =
`🪑 *Бронь столика — COFEMAN*
━━━━━━━━━━━━━━
👤 Имя: ${name}
👥 Гостей: ${guests}
⏰ Время: ${time}${note ? `\n💬 Пожелания: ${note}` : ''}`;

      closeBookingModal();
      window.open(`https://wa.me/${WHATSAPP_PHONE}?text=${encodeURIComponent(msg)}`, '_blank', 'noopener,noreferrer');
    }

    // Toast helper
    let toastTimer;
    function showToast(text) {
      const toast = document.getElementById('toast');
      document.getElementById('toastText').textContent = text;
      toast.classList.remove('opacity-0', 'translate-y-4');
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => {
        toast.classList.add('opacity-0', 'translate-y-4');
      }, 2200);
    }

    // Initialize
    renderCategories();
    renderMenu();
    updateCartUI();
  </script>
</body>
</html>
