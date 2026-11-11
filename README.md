

```html
<!DOCTYPE html>
<html lang="ar" dir="rtl" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MediaGrabber Pro | محمل الفيديوهات والصوتيات السينمائي</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Cairo (Arabic) & Inter (English) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800;900&family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        cyber: {
                            purple: '#7c3aed',
                            pink: '#ec4899',
                            cyan: '#06b6d4',
                            dark: '#090d16',
                            card: 'rgba(17, 24, 39, 0.7)',
                            accent: '#3b82f6'
                        }
                    },
                    fontFamily: {
                        ar: ['Cairo', 'sans-serif'],
                        en: ['Inter', 'sans-serif']
                    },
                    animation: {
                        'pulse-glow': 'pulseGlow 3s infinite alternate',
                        'float': 'float 4s ease-in-out infinite',
                    },
                    keyframes: {
                        pulseGlow: {
                            '0%': { boxShadow: '0 0 15px rgba(124, 58, 237, 0.3)' },
                            '100%': { boxShadow: '0 0 35px rgba(6, 182, 212, 0.6)' }
                        },
                        float: {
                            '0%, 100%': { transform: 'translateY(0px)' },
                            '50%': { transform: 'translateY(-8px)' }
                        }
                    }
                }
            }
        }
    </script>
    
    <style>
        body {
            font-family: 'Cairo', 'Inter', sans-serif;
            background-color: #07090e;
            color: #f3f4f6;
            overflow-x: hidden;
        }

        /* Glassmorphism Styles */
        .glass-panel {
            background: rgba(15, 23, 42, 0.65);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }

        .glass-input {
            background: rgba(10, 15, 29, 0.8);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(124, 58, 237, 0.3);
            color: #ffffff;
        }

        .glass-input:focus {
            border-color: #06b6d4;
            box-shadow: 0 0 20px rgba(6, 182, 212, 0.4);
        }

        /* Ambient Glow Background Spheres */
        .glow-sphere-1 {
            position: absolute;
            top: -100px;
            right: -100px;
            width: 450px;
            height: 450px;
            background: radial-gradient(circle, rgba(124,58,237,0.25) 0%, rgba(0,0,0,0) 70%);
            border-radius: 50%;
            z-index: 0;
            pointer-events: none;
        }

        .glow-sphere-2 {
            position: absolute;
            top: 250px;
            left: -150px;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(6,182,212,0.2) 0%, rgba(0,0,0,0) 70%);
            border-radius: 50%;
            z-index: 0;
            pointer-events: none;
        }

        /* Toast Notifications */
        #toast-container {
            position: fixed;
            bottom: 20px;
            left: 20px;
            z-index: 9999;
        }
        
        [dir="rtl"] #toast-container {
            left: auto;
            right: 20px;
        }

        /* Gradient Text */
        .text-gradient {
            background: linear-gradient(135deg, #a855f7 0%, #06b6d4 50%, #ec4899 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .btn-gradient {
            background: linear-gradient(135deg, #7c3aed 0%, #06b6d4 100%);
            transition: all 0.3s ease;
        }

        .btn-gradient:hover {
            background: linear-gradient(135deg, #6d28d9 0%, #0891b2 100%);
            box-shadow: 0 0 25px rgba(6, 182, 212, 0.5);
            transform: translateY(-2px);
        }

        /* Accordion transition */
        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out, opacity 0.3s ease-out;
            opacity: 0;
        }
        .faq-answer.active {
            max-height: 200px;
            opacity: 1;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #090d16;
        }
        ::-webkit-scrollbar-thumb {
            background: #1e293b;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #7c3aed;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between relative selection:bg-cyber-cyan selection:text-black">

    <!-- Ambient Background Lighting -->
    <div class="glow-sphere-1"></div>
    <div class="glow-sphere-2"></div>

    <!-- Header / Navbar -->
    <header class="sticky top-0 z-50 glass-panel border-b border-gray-800/50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <!-- Brand Logo -->
            <div class="flex items-center space-x-3 rtl:space-x-reverse cursor-pointer" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
                <div class="w-11 h-11 rounded-xl btn-gradient flex items-center justify-center text-white text-xl shadow-lg shadow-purple-900/40">
                    <i class="fa-solid fa-cloud-arrow-down"></i>
                </div>
                <span class="text-2xl font-black tracking-wider text-white">
                    MEDIA<span class="text-gradient">GRABBER</span>
                    <span class="text-xs px-2 py-0.5 rounded bg-cyber-purple/30 text-cyber-cyan border border-cyber-purple/50 font-mono">PRO</span>
                </span>
            </div>

            <!-- Navigation & Settings -->
            <div class="flex items-center gap-4">
                <nav class="hidden md:flex items-center gap-6 text-sm font-semibold text-gray-300">
                    <a href="#features" class="hover:text-cyber-cyan transition-colors" data-i18n="nav-features">المميزات</a>
                    <a href="#platforms" class="hover:text-cyber-cyan transition-colors" data-i18n="nav-platforms">المنصات</a>
                    <a href="#how-it-works" class="hover:text-cyber-cyan transition-colors" data-i18n="nav-how">طريقة التحميل</a>
                    <a href="#faq" class="hover:text-cyber-cyan transition-colors" data-i18n="nav-faq">الأسئلة الشائعة</a>
                </nav>

                <!-- Language Switcher Button -->
                <button id="lang-toggle" onclick="toggleLanguage()" class="glass-panel px-4 py-2 rounded-xl text-xs sm:text-sm font-bold text-gray-200 hover:text-white hover:border-cyber-cyan transition-all flex items-center gap-2">
                    <i class="fa-solid fa-globe text-cyber-cyan"></i>
                    <span id="lang-label">English</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-grow z-10">
        
        <!-- Hero Section -->
        <section class="max-w-5xl mx-auto px-4 pt-16 pb-12 text-center relative">
            
            <!-- Badge -->
            <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full glass-panel border border-cyber-purple/40 text-xs sm:text-sm font-semibold text-cyber-cyan mb-6 animate-pulse-glow">
                <i class="fa-solid fa-wand-magic-sparkles"></i>
                <span data-i18n="badge-text">أسرع وأرقى محمل ميديا لعام 2026</span>
            </div>

            <!-- Hero Titles -->
            <h1 class="text-4xl sm:text-6xl font-black tracking-tight leading-tight mb-6">
                <span data-i18n="hero-title-1">نزّل أي فيديو أو صوت</span> <br>
                <span class="text-gradient" data-i18n="hero-title-2">بأعلى جودة وبثوانٍ معدودة</span>
            </h1>

            <p class="text-gray-400 text-base sm:text-lg max-w-2xl mx-auto mb-10 leading-relaxed" data-i18n="hero-desc">
                منصة احترافية تتيح لك تحميل الفيديوهات والموسيقى من اليوتيوب، تيك توك، إنستغرام وغيرها مجاناً بدون إعلانات مزعجة وبجودة تصل إلى 4K.
            </p>

            <!-- URL Downloader Input Box -->
            <div class="glass-panel p-3 sm:p-4 rounded-2xl max-w-3xl mx-auto shadow-2xl relative border-1 border-purple-500/20">
                <form id="download-form" onsubmit="handleDownload(event)" class="flex flex-col sm:flex-row gap-3">
                    <div class="relative flex-grow">
                        <div class="absolute inset-y-0 right-0 sm:right-0 rtl:right-0 ltr:left-0 ltr:right-auto pr-4 ltr:pl-4 flex items-center pointer-events-none text-gray-500">
                            <i class="fa-solid fa-link text-lg"></i>
                        </div>
                        <input type="url" id="video-url" required
                            class="w-full glass-input py-4 pr-12 ltr:pr-4 ltr:pl-12 rounded-xl text-sm sm:text-base focus:outline-none transition-all placeholder-gray-500"
                            placeholder="أدخل رابط الفيديو أو الأغنية هنا..."
                            data-i18n-placeholder="input-placeholder">
                        
                        <!-- Paste Button -->
                        <button type="button" onclick="pasteFromClipboard()" 
                            class="absolute inset-y-2 left-2 rtl:left-2 ltr:right-2 ltr:left-auto px-3 bg-gray-800/80 hover:bg-gray-700 text-xs text-cyber-cyan rounded-lg transition-colors flex items-center gap-1">
                            <i class="fa-regular fa-paste"></i>
                            <span data-i18n="btn-paste">لصق</span>
                        </button>
                    </div>

                    <button type="submit" id="submit-btn" class="btn-gradient py-4 px-8 rounded-xl font-bold text-white text-base flex items-center justify-center gap-2 shadow-lg min-w-[140px]">
                        <i class="fa-solid fa-bolt"></i>
                        <span id="btn-text" data-i18n="btn-fetch">تحليل الرابط</span>
                    </button>
                </form>
            </div>

            <!-- Loader Indicator -->
            <div id="loader" class="hidden my-10">
                <div class="inline-flex flex-col items-center gap-3 glass-panel p-6 rounded-2xl">
                    <div class="w-12 h-12 border-4 border-cyber-cyan border-t-transparent rounded-full animate-spin"></div>
                    <span class="text-sm font-semibold text-gray-300 animate-pulse" data-i18n="loading-text">جاري فحص الرابط واستخراج ملفات التحميل...</span>
                </div>
            </div>

            <!-- Download Result Area (Generated Dynamically) -->
            <div id="result-container" class="hidden mt-10 max-w-3xl mx-auto text-right rtl:text-right ltr:text-left animate-fade-in">
                <div class="glass-panel p-5 sm:p-6 rounded-2xl border border-cyber-cyan/30">
                    
                    <!-- Media Info Header -->
                    <div class="flex flex-col sm:flex-row gap-5 items-center sm:items-start border-b border-gray-800 pb-6 mb-6">
                        <div class="relative group rounded-xl overflow-hidden w-full sm:w-48 aspect-video bg-gray-900 flex-shrink-0">
                            <img id="res-thumb" src="" alt="Thumbnail" class="w-full h-full object-cover">
                            <span id="res-duration" class="absolute bottom-2 right-2 bg-black/80 px-2 py-0.5 rounded text-xs font-mono text-white">00:00</span>
                        </div>
                        
                        <div class="flex-grow text-center sm:text-right rtl:sm:text-right ltr:sm:text-left">
                            <div class="flex items-center justify-center sm:justify-start gap-2 mb-2">
                                <span id="res-platform" class="px-2.5 py-0.5 rounded-full bg-red-500/20 text-red-400 border border-red-500/30 text-xs font-bold flex items-center gap-1">
                                    <i class="fa-brands fa-youtube"></i> YouTube
                                </span>
                                <span class="px-2.5 py-0.5 rounded-full bg-green-500/20 text-green-400 border border-green-500/30 text-xs font-bold" data-i18n="status-ready">جاهز للتحميل</span>
                            </div>
                            <h3 id="res-title" class="text-lg font-bold text-white mb-2 line-clamp-2">عنوان الفيديو يظهر هنا...</h3>
                            <p class="text-xs text-gray-400 flex items-center justify-center sm:justify-start gap-4">
                                <span><i class="fa-regular fa-user ml-1 ltr:mr-1"></i> <span id="res-author">اسم القناة</span></span>
                                <span><i class="fa-regular fa-eye ml-1 ltr:mr-1"></i> <span id="res-views">1.2M</span></span>
                            </p>
                        </div>
                    </div>

                    <!-- Format Selector Tabs (MP4 Video / MP3 Audio) -->
                    <div class="flex gap-2 mb-6 bg-gray-900/80 p-1.5 rounded-xl">
                        <button id="tab-video" onclick="switchFormatTab('video')" class="flex-1 py-2.5 rounded-lg font-bold text-sm transition-all flex items-center justify-center gap-2 bg-cyber-purple text-white shadow">
                            <i class="fa-solid fa-video"></i>
                            <span data-i18n="tab-video">فيديو (MP4)</span>
                        </button>
                        <button id="tab-audio" onclick="switchFormatTab('audio')" class="flex-1 py-2.5 rounded-lg font-bold text-sm transition-all flex items-center justify-center gap-2 text-gray-400 hover:text-white">
                            <i class="fa-solid fa-music"></i>
                            <span data-i18n="tab-audio">صوت (MP3)</span>
                        </button>
                    </div>

                    <!-- Download Quality List -->
                    <!-- Video Options -->
                    <div id="options-video" class="space-y-3">
                        <div class="flex items-center justify-between p-3.5 rounded-xl bg-gray-900/50 border border-gray-800 hover:border-cyber-purple/50 transition-all">
                            <div class="flex items-center gap-3">
                                <span class="px-2 py-1 bg-purple-500/20 text-purple-300 text-xs font-bold rounded">4K ULTRA HD</span>
                                <div class="text-xs">
                                    <div class="font-bold text-white">2160p (MP4)</div>
                                    <div class="text-gray-400">~ 245.0 MB</div>
                                </div>
                            </div>
                            <button onclick="triggerDownload('2160p', 'MP4')" class="btn-gradient px-4 py-2 rounded-lg text-xs font-bold text-white flex items-center gap-1.5">
                                <i class="fa-solid fa-download"></i> <span data-i18n="btn-download">تحميل</span>
                            </button>
                        </div>

                        <div class="flex items-center justify-between p-3.5 rounded-xl bg-gray-900/50 border border-gray-800 hover:border-cyber-purple/50 transition-all">
                            <div class="flex items-center gap-3">
                                <span class="px-2 py-1 bg-blue-500/20 text-blue-300 text-xs font-bold rounded">1080p FULL HD</span>
                                <div class="text-xs">
                                    <div class="font-bold text-white">1080p (MP4)</div>
                                    <div class="text-gray-400">~ 85.4 MB</div>
                                </div>
                            </div>
                            <button onclick="triggerDownload('1080p', 'MP4')" class="btn-gradient px-4 py-2 rounded-lg text-xs font-bold text-white flex items-center gap-1.5">
                                <i class="fa-solid fa-download"></i> <span data-i18n="btn-download">تحميل</span>
                            </button>
                        </div>

                        <div class="flex items-center justify-between p-3.5 rounded-xl bg-gray-900/50 border border-gray-800 hover:border-cyber-purple/50 transition-all">
                            <div class="flex items-center gap-3">
                                <span class="px-2 py-1 bg-gray-700/40 text-gray-300 text-xs font-bold rounded">720p HD</span>
                                <div class="text-xs">
                                    <div class="font-bold text-white">720p (MP4)</div>
                                    <div class="text-gray-400">~ 42.1 MB</div>
                                </div>
                            </div>
                            <button onclick="triggerDownload('720p', 'MP4')" class="btn-gradient px-4 py-2 rounded-lg text-xs font-bold text-white flex items-center gap-1.5">
                                <i class="fa-solid fa-download"></i> <span data-i18n="btn-download">تحميل</span>
                            </button>
                        </div>
                    </div>

                    <!-- Audio Options -->
                    <div id="options-audio" class="space-y-3 hidden">
                        <div class="flex items-center justify-between p-3.5 rounded-xl bg-gray-900/50 border border-gray-800 hover:border-cyber-cyan/50 transition-all">
                            <div class="flex items-center gap-3">
                                <span class="px-2 py-1 bg-cyan-500/20 text-cyan-300 text-xs font-bold rounded">HQ 320 kbps</span>
                                <div class="text-xs">
                                    <div class="font-bold text-white">أعلى جودة صوت (MP3)</div>
                                    <div class="text-gray-400">~ 9.5 MB</div>
                                </div>
                            </div>
                            <button onclick="triggerDownload('320kbps', 'MP3')" class="btn-gradient px-4 py-2 rounded-lg text-xs font-bold text-white flex items-center gap-1.5">
                                <i class="fa-solid fa-download"></i> <span data-i18n="btn-download">تحميل</span>
                            </button>
                        </div>

                        <div class="flex items-center justify-between p-3.5 rounded-xl bg-gray-900/50 border border-gray-800 hover:border-cyber-cyan/50 transition-all">
                            <div class="flex items-center gap-3">
                                <span class="px-2 py-1 bg-gray-700/40 text-gray-300 text-xs font-bold rounded">192 kbps</span>
                                <div class="text-xs">
                                    <div class="font-bold text-white">جودة قياسية (MP3)</div>
                                    <div class="text-gray-400">~ 5.2 MB</div>
                                </div>
                            </div>
                            <button onclick="triggerDownload('192kbps', 'MP3')" class="btn-gradient px-4 py-2 rounde