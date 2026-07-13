<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Discovering Hypertension™ — Digital Health Ecosystem</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        navy: {
                            50: '#f4f7fa',
                            100: '#e9eff5',
                            800: '#0A2540',
                            900: '#051321',
                        },
                        teal: {
                            DEFAULT: '#00A8A8',
                            hover: '#008C8C',
                            light: '#E6F6F6'
                        },
                        coral: {
                            DEFAULT: '#EF4444',
                            dark: '#DC2626'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                        urdu: ['Noto Nastaliq Urdu', 'Noto Sans Arabic', 'serif']
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts for Bilingual Typography -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Noto+Sans+Arabic:wght@400;600;700&family=Noto+Nastaliq+Urdu:wght@400;700&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons for Clinic Indicators -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* CSS Animations and custom styles for single-file integration */
        @keyframes pulse-ring {
            0% { transform: scale(0.95); opacity: 0.8; }
            50% { transform: scale(1.08); opacity: 0.4; }
            100% { transform: scale(0.95); opacity: 0.8; }
        }
        .pulse-element {
            animation: pulse-ring 2s infinite ease-in-out;
        }
        .heartbeat-wave {
            stroke-dasharray: 1000;
            stroke-dashoffset: 1000;
            animation: draw-ecg 4s linear infinite;
        }
        @keyframes draw-ecg {
            to { stroke-dashoffset: 0; }
        }
        /* Custom slider thumb styles to match touch targets */
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            background: #00A8A8;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 168, 168, 0.4);
            transition: transform 0.1s ease;
        }
        input[type="range"]::-webkit-slider-thumb:active {
            transform: scale(1.2);
        }
        /* Urdu font rendering optimizations */
        .urdu-text {
            font-family: 'Noto Sans Arabic', 'Noto Nastaliq Urdu', sans-serif;
            line-height: 1.8;
        }
        /* Transition utility */
        .screen-fade {
            transition: opacity 0.25s ease-in-out, transform 0.25s ease-in-out;
        }
    </style>
</head>
<body class="bg-navy-50 text-navy-800 font-sans min-h-screen flex flex-col antialiased">

    <!-- TOP HEADER / BRAND NAVIGATION -->
    <header class="bg-white border-b border-navy-100 shadow-sm sticky top-0 z-40">
        <div class="max-w-5xl mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <!-- PharmEvo Custom Dynamic Logo Container -->
                <div class="relative h-12 w-32 flex items-center justify-center bg-gray-50 rounded-lg p-1 border border-gray-100">
                    <img id="pharmevo-logo" src="Pharmevo-logo-for-web.png" alt="PharmEvo Logo" class="max-h-full object-contain" onerror="renderLogoFallback(this)">
                </div>
                <div class="hidden sm:block border-l border-navy-100 pl-3">
                    <h1 class="text-sm font-bold tracking-tight text-navy-800">Scan Your Pressure</h1>
                    <p class="text-[10px] text-teal font-medium uppercase tracking-wider">CSR Innovation</p>
                </div>
            </div>

            <!-- Active Campaign Badge -->
            <div id="active-campaign-badge" class="bg-teal-light border border-teal/20 text-teal px-3 py-1.5 rounded-full text-xs font-semibold flex items-center space-x-1.5">
                <span class="w-2 h-2 rounded-full bg-teal animate-ping"></span>
                <span>Campaign: <strong id="badge-campaign-code">LUMS-SPRING</strong></span>
            </div>

            <!-- Global Controls Menu -->
            <div class="flex items-center space-x-2">
                <!-- Audio Synthesis Toggle -->
                <button onclick="toggleAudio()" id="btn-audio-toggle" class="p-2 text-navy-800 hover:text-teal rounded-lg hover:bg-navy-50 transition" title="Toggle Sound Engine">
                    <i class="fa-solid fa-volume-high text-lg"></i>
                </button>

                <!-- English / Urdu Language Switcher -->
                <button onclick="toggleLanguage()" class="bg-navy-800 text-white hover:bg-teal px-3.5 py-1.5 rounded-lg text-xs font-bold transition flex items-center space-x-1">
                    <i class="fa-solid fa-language text-sm"></i>
                    <span id="lang-switch-lbl">اردو</span>
                </button>
            </div>
        </div>
    </header>

    <!-- MAIN IMMERSIVE CONTAINER -->
    <main class="flex-grow max-w-5xl w-full mx-auto px-4 py-6 flex flex-col justify-start">

        <!-- UZAIR AHMAD AUTHORSHIP BADGE CARD -->
        <div class="bg-white rounded-2xl p-4 mb-6 shadow-sm border border-navy-100 flex flex-col sm:flex-row items-center justify-between gap-4">
            <div class="flex items-center space-x-4">
                <div class="relative w-14 h-14 rounded-xl overflow-hidden bg-navy-100 flex-shrink-0 border-2 border-teal">
                    <img id="uzair-avatar" src="Screenshot 2026-07-13 124314.jpg" alt="Uzair Ahmad" class="w-full h-full object-cover" onerror="renderAvatarFallback(this)">
                </div>
                <div>
                    <h3 class="font-bold text-navy-800 text-sm sm:text-base flex items-center gap-1.5">
                        Uzair Ahmad
                        <span class="text-[11px] bg-navy-100 text-navy-800 px-2 py-0.5 rounded-full font-medium">Lead Architect</span>
                    </h3>
                    <p class="text-xs text-gray-500">Discovering Hypertension™ Program Automation lead</p>
                    <a href="https://pk.linkedin.com/in/uzairahmad02" target="_blank" rel="noopener noreferrer" class="text-xs text-teal hover:underline font-semibold flex items-center gap-1 mt-0.5">
                        <i class="fa-brands fa-linkedin"></i> Connect on LinkedIn
                    </a>
                </div>
            </div>
            <div class="flex flex-wrap gap-2 justify-center sm:justify-end">
                <span class="text-[11px] bg-teal-light text-teal px-2.5 py-1 rounded-md font-medium border border-teal/10">Zero-Cost Scaling</span>
                <span class="text-[11px] bg-navy-50 text-navy-800 px-2.5 py-1 rounded-md font-medium border border-navy-100">Bilingual Engine</span>
                <span class="text-[11px] bg-red-50 text-red-600 px-2.5 py-1 rounded-md font-medium border border-red-100">Clinical Verified</span>
            </div>
        </div>

        <!-- APP INTERACTIVE SCREEN CONTAINER -->
        <div class="bg-white rounded-3xl shadow-md border border-navy-100 overflow-hidden min-h-[500px] flex flex-col relative" id="screen-viewport">
            
            <!-- 1. LANDING SCREEN -->
            <div id="screen-landing" class="screen-fade flex flex-col items-center justify-center text-center p-6 sm:p-12 space-y-8 flex-grow">
                <div class="max-w-xl mx-auto space-y-4">
                    <div class="inline-flex bg-teal-light text-teal px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider mb-2">
                        <span data-key="lblCSRBadge">PharmEvo CSR National Initiative</span>
                    </div>
                    <h2 class="text-3xl sm:text-4xl font-extrabold text-navy-800 leading-tight" data-key="lblLandingTitle">
                        Your Heart’s Performance Review
                    </h2>
                    <p class="text-gray-600 text-sm sm:text-base" data-key="lblLandingSub">
                        Hypertension is a silent performance killer. Take control today with our 60-second diagnostic risk analysis, digital tracking passport, and direct connection to localized expert clinics.
                    </p>
                </div>

                <!-- Custom ECG Line SVG Illustration -->
                <div class="w-full max-w-md py-4">
                    <svg class="w-full h-16" viewBox="0 0 400 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M0,50 L100,50 L115,35 L130,65 L145,50 L160,50 L170,10 L185,90 L200,45 L210,50 L220,50 L230,42 L240,50 L400,50" 
                              stroke="#00A8A8" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" class="heartbeat-wave"></path>
                    </svg>
                </div>

                <!-- Action Button Matrix -->
                <div class="w-full max-w-sm flex flex-col space-y-3">
                    <button onclick="navigateTo('screen-quiz')" class="w-full bg-teal hover:bg-teal-hover text-white font-bold py-4 px-6 rounded-2xl shadow-lg shadow-teal/20 transition-all transform hover:-translate-y-0.5 flex items-center justify-center space-x-2 text-base">
                        <span data-key="btnStartReview">Start Performance Review</span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </button>
                    <button onclick="navigateTo('screen-passport')" class="w-full bg-navy-50 hover:bg-navy-100 text-navy-800 font-semibold py-3.5 px-6 rounded-2xl border border-navy-100 transition flex items-center justify-center space-x-2 text-sm">
                        <i class="fa-solid fa-passport text-teal"></i>
                        <span data-key="btnOpenPassport">Open My Digital Passport</span>
                    </button>
                </div>
            </div>

            <!-- 2. MULTI-STEP QUIZ SCENARIO -->
            <div id="screen-quiz" class="screen-fade hidden p-6 sm:p-8 flex flex-col justify-between flex-grow">
                <!-- Quiz Progress Bar -->
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <span class="text-xs font-semibold text-teal uppercase tracking-wider" id="quiz-step-indicator">Question 1 of 6</span>
                        <div class="text-xs text-gray-500" id="quiz-step-desc">Lifestyle Risk Assessment</div>
                    </div>
                    <div class="w-full h-2 bg-navy-50 rounded-full overflow-hidden">
                        <div id="quiz-progress-fill" class="h-full bg-teal transition-all duration-300" style="width: 16.6%"></div>
                    </div>
                </div>

                <!-- Dynamic Quiz Question Card -->
                <div class="my-8 max-w-xl mx-auto w-full">
                    <div class="bg-navy-50 rounded-2xl p-6 border border-navy-100 text-center space-y-4">
                        <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center mx-auto text-teal shadow-sm border border-navy-100">
                            <i id="quiz-question-icon" class="fa-solid fa-bed text-xl"></i>
                        </div>
                        <h3 id="quiz-question-text" class="text-lg sm:text-xl font-bold text-navy-800 leading-snug">
                            How would you describe your general sleep patterns over the last month?
                        </h3>
                    </div>

                    <!-- Answer Options Stack -->
                    <div class="mt-6 space-y-3" id="quiz-options-container">
                        <!-- Dynamic choices inserted via JS -->
                    </div>
                </div>

                <!-- Lower Navigation Bar -->
                <div class="flex items-center justify-between border-t border-navy-100 pt-4">
                    <button onclick="quizPrevStep()" id="btn-quiz-prev" class="px-5 py-2.5 text-sm font-semibold text-gray-500 hover:text-navy-800 transition flex items-center gap-2">
                        <i class="fa-solid fa-arrow-left"></i> <span data-key="btnBack">Back</span>
                    </button>
                    <span class="text-xs text-gray-400 font-medium" data-key="lblQuizEncrypted">Secure Local Processing</span>
                </div>
            </div>

            <!-- 3. BLOOD PRESSURE ENTRY & BIOMETRIC ASSESSMENT -->
            <div id="screen-bp" class="screen-fade hidden p-6 sm:p-8 flex flex-col justify-between flex-grow">
                <div class="text-center space-y-2 max-w-xl mx-auto">
                    <div class="inline-flex bg-navy-50 text-navy-800 px-3 py-1 rounded-full text-xs font-bold border border-navy-100">
                        <span data-key="lblCheckinStep">Step 2: Interactive Biometrics</span>
                    </div>
                    <h3 class="text-xl sm:text-2xl font-extrabold text-navy-800" data-key="lblBpInputTitle">Enter Your Blood Pressure</h3>
                    <p class="text-xs sm:text-sm text-gray-500" data-key="lblBpInputSub">Adjust sliders to input your actual BP reading measured at the booth or home monitor.</p>
                </div>

                <!-- Slider Workspace Grid -->
                <div class="my-6 grid grid-cols-1 md:grid-cols-2 gap-8 items-center max-w-3xl mx-auto w-full">
                    
                    <!-- Tactile Sliders Column -->
                    <div class="space-y-6">
                        <!-- SBP Slider -->
                        <div class="space-y-2">
                            <div class="flex justify-between items-center text-sm">
                                <span class="font-bold text-navy-800" data-key="lblSbp">Systolic Pressure (SBP)</span>
                                <span class="text-teal font-extrabold text-lg" id="val-sbp-lbl">120 <span class="text-[10px] text-gray-500 font-normal">mmHg</span></span>
                            </div>
                            <input type="range" id="sys-slider" min="80" max="220" value="120" class="w-full h-2 bg-navy-100 rounded-lg appearance-none cursor-pointer accent-teal" oninput="handleBpSliderUpdate()">
                            <div class="flex justify-between text-[10px] text-gray-400 font-bold px-1">
                                <span>80 (LOW)</span>
                                <span>120 (OPTIMAL)</span>
                                <span>140 (STAGE 2)</span>
                                <span>220 (CRISIS)</span>
                            </div>
                        </div>

                        <!-- DBP Slider -->
                        <div class="space-y-2">
                            <div class="flex justify-between items-center text-sm">
                                <span class="font-bold text-navy-800" data-key="lblDbp">Diastolic Pressure (DBP)</span>
                                <span class="text-teal font-extrabold text-lg" id="val-dbp-lbl">80 <span class="text-[10px] text-gray-500 font-normal">mmHg</span></span>
                            </div>
                            <input type="range" id="dia-slider" min="50" max="130" value="80" class="w-full h-2 bg-navy-100 rounded-lg appearance-none cursor-pointer accent-teal" oninput="handleBpSliderUpdate()">
                            <div class="flex justify-between text-[10px] text-gray-400 font-bold px-1">
                                <span>50 (LOW)</span>
                                <span>80 (OPTIMAL)</span>
                                <span>90 (STAGE 2)</span>
                                <span>130 (CRISIS)</span>
                            </div>
                        </div>
                    </div>

                    <!-- Heart Animation & Diagnostic Panel -->
                    <div class="bg-navy-50 rounded-2xl p-6 border border-navy-100 flex flex-col items-center justify-center space-y-4 text-center">
                        <div class="relative w-20 h-20 flex items-center justify-center">
                            <div class="absolute inset-0 bg-red-500/10 rounded-full pulse-element" id="heart-pulse-ring"></div>
                            <i class="fa-solid fa-heart text-red-500 text-5xl relative z-10 transition-transform duration-200" id="visual-heart-icon"></i>
                        </div>
                        
                        <!-- Real-time calculation output badges -->
                        <div>
                            <div class="text-2xl font-black" id="realtime-bp-val">120/80</div>
                            <div class="text-[11px] font-bold uppercase tracking-wider text-teal mt-0.5" id="realtime-classification">Normal BP</div>
                        </div>

                        <!-- Mean Arterial Pressure (MAP) -->
                        <div class="bg-white px-3.5 py-1.5 rounded-lg border border-navy-100 w-full max-w-[200px]">
                            <div class="text-[9px] font-bold text-gray-500 uppercase tracking-widest" data-key="lblMapVal">Mean Arterial Pressure (MAP)</div>
                            <div class="text-sm font-extrabold text-navy-800" id="realtime-map-val">93.3 mmHg</div>
                        </div>
                    </div>
                </div>

                <!-- Intake Registration Panel (Option fields to complete checked flow) -->
                <div class="max-w-xl mx-auto w-full bg-navy-50/50 rounded-xl p-4 border border-dashed border-navy-100 mb-4">
                    <h4 class="text-xs font-bold text-navy-800 mb-2 flex items-center gap-1.5">
                        <i class="fa-solid fa-user-shield text-teal"></i>
                        <span data-key="lblRegPanelTitle">Profile Personalization (Optional)</span>
                    </h4>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <input type="text" id="reg-name" placeholder="Full Name ( अहमद अली )" class="bg-white border border-navy-100 rounded-xl px-3 py-2 text-xs focus:ring-1 focus:ring-teal focus:outline-none">
                        <input type="tel" id="reg-phone" placeholder="Phone Hash Entry (03xxxxxxxxx)" class="bg-white border border-navy-100 rounded-xl px-3 py-2 text-xs focus:ring-1 focus:ring-teal focus:outline-none">
                    </div>
                    <label class="mt-2.5 flex items-start gap-2 cursor-pointer select-none">
                        <input type="checkbox" id="reg-consent" checked class="mt-0.5 rounded border-gray-300 text-teal focus:ring-teal">
                        <span class="text-[10px] text-gray-500 leading-tight" data-key="lblRegConsent">I consent to secure, offline hashing of my biometrics for the digital passport program.</span>
                    </label>
                </div>

                <!-- Submit Control Bar -->
                <div class="flex justify-between items-center pt-2 border-t border-navy-100">
                    <button onclick="navigateTo('screen-quiz')" class="px-5 py-2.5 text-sm font-semibold text-gray-500 hover:text-navy-800 transition">
                        <span data-key="btnBack">Back</span>
                    </button>
                    <button onclick="processFinalAssessment()" class="bg-teal hover:bg-teal-hover text-white font-bold py-3 px-8 rounded-xl shadow-md transition flex items-center gap-2">
                        <span data-key="btnCalculateScore">Assess Performance</span>
                        <i class="fa-solid fa-gauge-high"></i>
                    </button>
                </div>
            </div>

            <!-- 4. CARDIOVASCULAR SCORE & DIAGNOSTIC REPORT -->
            <div id="screen-results" class="screen-fade hidden p-6 sm:p-8 flex-grow overflow-y-auto">
                <div class="text-center space-y-1 mb-6">
                    <div class="inline-flex bg-teal-light text-teal px-3 py-1 rounded-full text-xs font-bold">
                        <span data-key="lblReportHeader">Assessment Complete</span>
                    </div>
                    <h3 class="text-2xl font-extrabold text-navy-800" data-key="lblReportTitle">Your Heart Performance Review</h3>
                </div>

                <!-- Results Metric Board -->
                <div class="grid grid-cols-1 md:grid-cols-12 gap-6 items-start max-w-4xl mx-auto">
                    
                    <!-- Score Gauge Card (MD: 5 cols) -->
                    <div class="md:col-span-5 bg-navy-50 rounded-2xl p-6 border border-navy-100 text-center flex flex-col items-center justify-center">
                        <span class="text-xs font-bold text-gray-500 uppercase tracking-widest mb-3" data-key="lblHeartScore">HEART HEALTH SCORE</span>
                        
                        <!-- Circular SVG Score Gauge -->
                        <div class="relative w-40 h-40 flex items-center justify-center">
                            <svg class="absolute inset-0 w-full h-full transform -rotate-90" viewBox="0 0 100 100">
                                <circle cx="50" cy="50" r="40" stroke="#E6EFF5" stroke-width="8" fill="transparent"></circle>
                                <circle id="results-gauge-fill" cx="50" cy="50" r="40" stroke="#00A8A8" stroke-width="8" fill="transparent" stroke-dasharray="251.2" stroke-dashoffset="100" stroke-linecap="round" class="transition-all duration-1000"></circle>
                            </svg>
                            <div class="text-center z-10">
                                <div class="text-4xl font-black text-navy-800" id="lbl-gauge-score">75</div>
                                <div class="text-[10px] font-bold text-gray-400 mt-0.5">OUT OF 100</div>
                            </div>
                        </div>

                        <div class="mt-4 px-4 py-2 bg-white rounded-xl border border-navy-100 w-full">
                            <div class="text-[9px] font-bold text-gray-400 uppercase tracking-wider" data-key="lblAssessmentRisk">RISK CLASSIFICATION</div>
                            <div class="text-sm font-bold text-navy-800" id="lbl-risk-tier">Moderate Risk</div>
                        </div>
                    </div>

                    <!-- Clinical Details & Remediation Recommendations (MD: 7 cols) -->
                    <div class="md:col-span-7 space-y-4">
                        <!-- Biometrics Review Card -->
                        <div class="bg-white rounded-xl p-4 border border-navy-100 shadow-sm grid grid-cols-2 gap-4">
                            <div>
                                <div class="text-xs text-gray-500" data-key="lblMeasuredBP">Measured Blood Pressure</div>
                                <div class="text-xl font-extrabold text-navy-800 flex items-center gap-1.5">
                                    <span id="lbl-res-bp">120/80</span>
                                    <span class="w-2.5 h-2.5 rounded-full" id="lbl-res-bp-dot"></span>
                                </div>
                                <div class="text-[10px] font-bold text-gray-400 uppercase" id="lbl-res-bp-class">Normal BP</div>
                            </div>
                            <div>
                                <div class="text-xs text-gray-500" data-key="lblCalculatedMAP">Mean Perfusion (MAP)</div>
                                <div class="text-xl font-extrabold text-navy-800" id="lbl-res-map">93.3 mmHg</div>
                                <div class="text-[10px] text-teal font-semibold flex items-center gap-1 mt-0.5">
                                    <i class="fa-solid fa-shield-heart"></i> <span data-key="lblMapRange">Healthy Target: 70-100</span>
                                </div>
                            </div>
                        </div>

                        <!-- Lifestyle Drivers Scorebars -->
                        <div class="bg-navy-50/50 rounded-xl p-4 border border-navy-100">
                            <h4 class="text-xs font-bold text-navy-800 mb-3 flex items-center gap-1.5">
                                <i class="fa-solid fa-sliders text-teal"></i>
                                <span data-key="lblDrivers">Key Lifestyle Factors Tested</span>
                            </h4>
                            <div class="space-y-3" id="results-drivers-container">
                                <!-- Generated Dynamically in code -->
                            </div>
                        </div>
                    </div>
                </div>

                <!-- CLINICAL ROUTING / ACTION OPTIONS BLOCK -->
                <div class="mt-8 border-t border-navy-100 pt-6 grid grid-cols-1 sm:grid-cols-3 gap-4 max-w-4xl mx-auto">
                    <!-- Dashboard Redirection -->
                    <button onclick="navigateTo('screen-passport')" class="bg-white hover:bg-navy-50 text-navy-800 border border-navy-100 font-semibold p-4 rounded-xl shadow-sm transition flex flex-col items-center justify-center text-center space-y-1">
                        <i class="fa-solid fa-passport text-2xl text-teal"></i>
                        <span class="font-bold text-sm" data-key="btnDashboard">Go to Digital Passport</span>
                        <span class="text-[10px] text-gray-500" data-key="btnDashboardSub">Log habits & build streaks</span>
                    </button>

                    <!-- WhatsApp Handoff CTA -->
                    <button onclick="triggerWhatsAppHandoff()" class="bg-teal hover:bg-teal-hover text-white font-bold p-4 rounded-xl shadow-sm transition flex flex-col items-center justify-center text-center space-y-1">
                        <i class="fa-brands fa-whatsapp text-2xl"></i>
                        <span class="text-sm" data-key="btnHandoff">Handoff to Bot</span>
                        <span class="text-[10px] text-white/80" data-key="btnHandoffSub">Sync to PharmEvo WhatsApp CSR</span>
                    </button>

                    <!-- Clinic Booking Panel Router -->
                    <button onclick="openClinicSearch()" class="bg-white hover:bg-navy-50 text-navy-800 border border-navy-100 font-semibold p-4 rounded-xl shadow-sm transition flex flex-col items-center justify-center text-center space-y-1">
                        <i class="fa-solid fa-hospital-user text-2xl text-rose-500"></i>
                        <span class="font-bold text-sm" data-key="btnReferral">Find Near Clinic</span>
                        <span class="text-[10px] text-gray-500" data-key="btnReferralSub">Free consultations booking</span>
                    </button>
                </div>
            </div>

            <!-- 5. DIGITAL PASSPORT DASHBOARD & PROGRESS LOGS -->
            <div id="screen-passport" class="screen-fade hidden p-6 sm:p-8 flex-grow overflow-y-auto">
                <div class="flex flex-col sm:flex-row justify-between items-center gap-4 border-b border-navy-100 pb-4 mb-6">
                    <div class="text-center sm:text-left">
                        <h3 class="text-xl font-extrabold text-navy-800 flex items-center gap-2 justify-center sm:justify-start">
                            <i class="fa-solid fa-passport text-teal"></i>
                            <span data-key="lblPassportTitle">My Digital Health Passport</span>
                        </h3>
                        <p class="text-xs text-gray-500" data-key="lblPassportSub">Keep tracking daily habits to protect your cardiovascular performance scores.</p>
                    </div>
                    <div class="flex gap-2">
                        <button onclick="navigateTo('screen-quiz')" class="bg-teal text-white hover:bg-teal-hover px-3.5 py-1.5 rounded-lg text-xs font-bold transition flex items-center gap-1.5">
                            <i class="fa-solid fa-plus"></i> <span data-key="btnNewAssessment">Assess Again</span>
                        </button>
                        <button onclick="openLogModal()" class="bg-navy-800 text-white hover:bg-navy-900 px-3.5 py-1.5 rounded-lg text-xs font-bold transition flex items-center gap-1.5">
                            <i class="fa-solid fa-file-invoice"></i> <span data-key="btnQuickLog">Quick Log BP</span>
                        </button>
                    </div>
                </div>

                <!-- Passport Body Workspace -->
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">
                    
                    <!-- Left Column: Gamified Performance Matrix (LG: 5 cols) -->
                    <div class="lg:col-span-5 space-y-6">
                        <!-- Gamified Streak Meter -->
                        <div class="bg-gradient-to-br from-navy-800 to-navy-900 rounded-2xl p-5 text-white border border-navy-900 shadow-sm relative overflow-hidden">
                            <div class="absolute -right-6 -bottom-6 text-navy-500/10 text-9xl font-black">7</div>
                            <div class="relative z-10 space-y-4">
                                <div class="flex justify-between items-start">
                                    <div>
                                        <div class="text-xs text-teal uppercase font-bold tracking-wider" data-key="lblStreakBadge">HABIT ADHERENCE STREAK</div>
                                        <div class="text-3xl font-black mt-1 flex items-baseline gap-1">
                                            <span id="lbl-streak-val">3</span>
                                            <span class="text-xs text-gray-300 font-semibold" data-key="lblStreakDays">Days Active</span>
                                        </div>
                                    </div>
                                    <div class="w-10 h-10 bg-teal/20 rounded-full flex items-center justify-center border border-teal/30">
                                        <i class="fa-solid fa-fire text-teal text-xl animate-bounce"></i>
                                    </div>
                                </div>

                                <!-- Checklist Habits of today -->
                                <div class="bg-white/5 rounded-xl p-3 border border-white/10 space-y-2.5">
                                    <div class="text-[10px] font-bold text-gray-400 uppercase tracking-widest" data-key="lblHabitChecklist">DAILY COMPLIANCE CHECKLIST</div>
                                    
                                    <label class="flex items-center gap-2.5 cursor-pointer text-xs select-none">
                                        <input type="checkbox" id="habit-meds" onchange="toggleHabitAdherence('meds')" class="rounded border-white/20 text-teal bg-transparent focus:ring-teal">
                                        <span data-key="lblHabitMeds">Took prescribed BP medication today</span>
                                    </label>
                                    <label class="flex items-center gap-2.5 cursor-pointer text-xs select-none">
                                        <input type="checkbox" id="habit-salt" onchange="toggleHabitAdherence('salt')" class="rounded border-white/20 text-teal bg-transparent focus:ring-teal">
                                        <span data-key="lblHabitSalt">No high-sodium meals consumed (Biryani/Nihari)</span>
                                    </label>
                                    <label class="flex items-center gap-2.5 cursor-pointer text-xs select-none">
                                        <input type="checkbox" id="habit-walk" onchange="toggleHabitAdherence('walk')" class="rounded border-white/20 text-teal bg-transparent focus:ring-teal">
                                        <span data-key="lblHabitWalk">Logged 20 mins brisk exercise</span>
                                    </label>
                                </div>
                            </div>
                        </div>

                        <!-- Active Campaign Metrics Panel -->
                        <div class="bg-navy-50 rounded-xl p-4 border border-navy-100">
                            <h4 class="text-xs font-bold text-navy-800 mb-2 flex items-center gap-1.5">
                                <i class="fa-solid fa-circle-nodes text-teal"></i>
                                <span data-key="lblActiveCampaign">Connected Clinic Network</span>
                            </h4>
                            <p class="text-xs text-gray-500 mb-3" data-key="lblActiveCampaignSub">Book a physical follow-up with specialized doctors for your high risk profile levels.</p>
                            
                            <div class="space-y-2.5">
                                <select id="clinic-city-filter" onchange="filterClinics()" class="w-full bg-white border border-navy-100 rounded-lg px-3 py-1.5 text-xs focus:ring-1 focus:ring-teal focus:outline-none">
                                    <option value="all">All Cities / تمام شہر</option>
                                    <option value="Karachi">Karachi / کراچی</option>
                                    <option value="Lahore">Lahore / لاہور</option>
                                    <option value="Islamabad">Islamabad / اسلام آباد</option>
                                    <option value="Faisalabad">Faisalabad / فیصل آباد</option>
                                </select>

                                <div id="clinic-routing-list" class="space-y-2 max-h-[160px] overflow-y-auto pr-1">
                                    <!-- Clinic items appended here -->
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Right Column: Interactive Heart Performance Trend (LG: 7 cols) -->
                    <div class="lg:col-span-7 space-y-6">
                        <!-- BP Performance Chart -->
                        <div class="bg-white rounded-2xl p-5 border border-navy-100 shadow-sm space-y-4">
                            <div class="flex justify-between items-center">
                                <div>
                                    <h4 class="text-sm font-bold text-navy-800" data-key="lblChartTitle">Biometric Performance Trend</h4>
                                    <p class="text-[10px] text-gray-400" data-key="lblChartSub">Tracking Systolic and Diastolic entries over time</p>
                                </div>
                                <div class="text-[10px] bg-teal-light text-teal px-2 py-0.5 rounded font-bold uppercase" id="lbl-chart-count">0 ENTRIES</div>
                            </div>

                            <!-- SVG Responsive Graphic Chart Plotter -->
                            <div class="relative w-full h-44 bg-navy-50 rounded-xl border border-navy-100 overflow-hidden flex items-center justify-center p-2">
                                <svg id="trend-graph-svg" class="w-full h-full" viewBox="0 0 400 150" preserveAspectRatio="none">
                                    <!-- Dynamic axes and curves plotted here -->
                                    <text x="150" y="75" fill="#a1a1aa" font-size="12" font-family="system-ui" text-anchor="middle" id="chart-placeholder">No logged metrics yet</text>
                                </svg>
                            </div>
                        </div>

                        <!-- Historical Log List Panel -->
                        <div class="bg-white rounded-2xl p-5 border border-navy-100 shadow-sm">
                            <h4 class="text-sm font-bold text-navy-800 mb-3" data-key="lblHistoricalTitle">All Logged Passport Entries</h4>
                            
                            <div class="overflow-x-auto">
                                <table class="w-full text-left text-xs">
                                    <thead>
                                        <tr class="border-b border-navy-100 text-gray-400 font-bold">
                                            <th class="pb-2" data-key="tblColDate">Date</th>
                                            <th class="pb-2 text-center" data-key="tblColBP">BP Value</th>
                                            <th class="pb-2 text-center" data-key="tblColMAP">MAP</th>
                                            <th class="pb-2 text-right" data-key="tblColActions">Classification</th>
                                        </tr>
                                    </thead>
                                    <tbody id="passport-history-table" class="divide-y divide-navy-50">
                                        <!-- Dynamic entries appended here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- CHATBOT FLOATING CONTAINER ("COACH KEM" DRAWER) -->
            <div id="coach-kem-chat" class="border-t border-navy-100 bg-white shadow-2xl relative z-30 transition-transform duration-300">
                <!-- Header trigger bar -->
                <div onclick="toggleCoachKemDrawer()" class="bg-navy-800 text-white px-5 py-3.5 flex items-center justify-between cursor-pointer select-none">
                    <div class="flex items-center space-x-3">
                        <div class="relative w-8 h-8 rounded-full bg-teal flex items-center justify-center border border-teal/20 text-white">
                            <i class="fa-solid fa-user-doctor"></i>
                            <span class="absolute right-0 bottom-0 w-2 h-2 rounded-full bg-green-500 border border-navy-800"></span>
                        </div>
                        <div>
                            <h4 class="text-xs sm:text-sm font-bold text-white flex items-center gap-1.5">
                                <span data-key="coachTitle">Coach Kem — AI Health Companion</span>
                            </h4>
                            <p class="text-[10px] text-gray-300" data-key="coachSub">Local Rule-Based Compliance Assistant</p>
                        </div>
                    </div>
                    <div class="flex items-center space-x-3">
                        <span class="text-[10px] bg-teal-light text-teal px-2 py-0.5 rounded font-bold uppercase">FREE ACCESS</span>
                        <i id="coach-drawer-toggle-icon" class="fa-solid fa-chevron-up text-sm"></i>
                    </div>
                </div>

                <!-- Collapsible conversation workspace -->
                <div id="coach-chat-body" class="h-0 overflow-hidden flex flex-col justify-between transition-all duration-300">
                    <!-- Dialogue Thread Box -->
                    <div class="flex-grow p-4 overflow-y-auto space-y-3 bg-navy-50/50" id="coach-message-thread">
                        <!-- Welcome message automatically populated -->
                    </div>

                    <!-- Recommended Keywords Chip Bar -->
                    <div class="px-4 py-2 border-t border-navy-100 overflow-x-auto flex space-x-2 bg-white flex-shrink-0" id="chat-quick-chips">
                        <!-- Quick reply chips loaded in code -->
                    </div>

                    <!-- Chat input bar -->
                    <div class="p-3 border-t border-navy-100 bg-white flex items-center gap-2">
                        <input type="text" id="chat-input-text" placeholder="Ask about Biryani, missed meds, salt, chest pain..." class="flex-grow border border-navy-100 rounded-xl px-4 py-2.5 text-xs focus:ring-1 focus:ring-teal focus:outline-none" onkeydown="handleChatSubmit(event)">
                        <button onclick="submitChatMessage()" class="bg-teal hover:bg-teal-hover text-white p-2.5 rounded-xl transition flex items-center justify-center aspect-square">
                            <i class="fa-solid fa-paper-plane text-sm"></i>
                        </button>
                    </div>
                </div>
            </div>

        </div>

        <!-- EMERGENCY WARNING MODAL OVERLAY -->
        <div id="crisis-override-modal" class="fixed inset-0 bg-navy-900/80 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
            <div class="bg-white rounded-3xl p-6 sm:p-8 max-w-md w-full border border-red-100 shadow-2xl relative overflow-hidden space-y-6">
                <!-- Glowing Crisis Indicator Icon -->
                <div class="w-16 h-16 bg-red-100 rounded-full flex items-center justify-center text-red-600 mx-auto animate-pulse">
                    <i class="fa-solid fa-triangle-exclamation text-3xl"></i>
                </div>
                
                <div class="text-center space-y-2">
                    <h3 class="text-xl sm:text-2xl font-black text-red-600 uppercase tracking-tight" data-key="lblCrisisModalTitle">🚨 CRITICAL MEDICAL ALERT</h3>
                    <p class="text-sm text-navy-800 font-semibold" data-key="lblCrisisModalSub">Immediate Clinical Intervention Required!</p>
                    <p class="text-xs text-gray-500 leading-relaxed" data-key="lblCrisisModalDesc">
                        If you or the current user is experiencing somatic chest pain, blurry vision, severe localized headache, or sudden breathing issues, do not delay. This is a medical emergency.
                    </p>
                </div>

                <!-- Emergency Contact Buttons Matrix -->
                <div class="space-y-2">
                    <a href="tel:02199201271" class="w-full bg-red-600 hover:bg-red-700 text-white font-bold py-3.5 px-4 rounded-xl flex items-center justify-between text-sm shadow-md shadow-red-600/10 transition">
                        <span>NICVD Emergency (Karachi)</span>
                        <span class="font-mono">(021) 99201271</span>
                    </a>
                    <a href="tel:021111822224" class="w-full bg-navy-800 hover:bg-navy-900 text-white font-bold py-3.5 px-4 rounded-xl flex items-center justify-between text-sm transition">
                        <span>Tabba Cardiology Hotline</span>
                        <span class="font-mono">111 822 224</span>
                    </a>
                </div>

                <div class="flex justify-center pt-2">
                    <button onclick="dismissCrisisModal()" class="text-xs text-gray-400 hover:text-navy-800 transition underline font-medium" data-key="btnCloseCrisisModal">Close Warning Indicator</button>
                </div>
            </div>
        </div>

        <!-- QUICK LOG MODAL -->
        <div id="quick-log-modal" class="fixed inset-0 bg-navy-900/50 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
            <div class="bg-white rounded-3xl p-6 max-w-sm w-full border border-navy-100 shadow-2xl relative space-y-4">
                <div class="flex justify-between items-center border-b border-navy-100 pb-2">
                    <h4 class="text-sm font-bold text-navy-800 flex items-center gap-1.5">
                        <i class="fa-solid fa-pencil text-teal"></i>
                        <span data-key="lblQuickLog">Quick Log BP</span>
                    </h4>
                    <button onclick="closeLogModal()" class="text-gray-400 hover:text-navy-800"><i class="fa-solid fa-xmark"></i></button>
                </div>

                <!-- Inputs Grid -->
                <div class="grid grid-cols-2 gap-3">
                    <div class="space-y-1">
                        <label class="text-[10px] font-bold text-gray-500 uppercase">SYSTOLIC (SBP)</label>
                        <input type="number" id="quick-sys" min="80" max="220" value="120" class="w-full bg-navy-50 border border-navy-100 rounded-xl px-3 py-2 text-sm font-bold focus:ring-1 focus:ring-teal focus:outline-none">
                    </div>
                    <div class="space-y-1">
                        <label class="text-[10px] font-bold text-gray-500 uppercase">DIASTOLIC (DBP)</label>
                        <input type="number" id="quick-dia" min="50" max="130" value="80" class="w-full bg-navy-50 border border-navy-100 rounded-xl px-3 py-2 text-sm font-bold focus:ring-1 focus:ring-teal focus:outline-none">
                    </div>
                </div>

                <button onclick="submitQuickLog()" class="w-full bg-teal text-white font-bold py-2.5 rounded-xl text-xs transition hover:bg-teal-hover flex items-center justify-center gap-2">
                    <span data-key="btnCalculateScore">Assess Performance</span>
                </button>
            </div>
        </div>

        <!-- CLINICAL CASE SIMULATION PANEL FOR MEDICAL HCPs -->
        <div class="bg-white rounded-3xl p-6 mt-8 shadow-md border border-navy-100" id="hcp-simulator-block">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 border-b border-navy-100 pb-4 mb-4">
                <div>
                    <h3 class="text-lg font-bold text-navy-800 flex items-center gap-2">
                        <i class="fa-solid fa-graduation-cap text-teal"></i>
                        <span data-key="lblSimTitle">HCP Counseling Simulator & Trainer</span>
                    </h3>
                    <p class="text-xs text-gray-500">Train medical students on patient empathy and behavioral cardiology protocols.</p>
                </div>
                <button onclick="loadSimCase()" class="bg-navy-800 hover:bg-navy-900 text-white px-3.5 py-1.5 rounded-xl text-xs font-bold transition flex items-center gap-1.5">
                    <i class="fa-solid fa-rotate-right"></i> Reset Simulation
                </button>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-12 gap-6 items-start">
                <!-- Patient Bio Card (MD: 4 cols) -->
                <div class="md:col-span-4 bg-navy-50 rounded-2xl p-5 border border-navy-100 space-y-3">
                    <div class="flex items-center space-x-3">
                        <div class="w-10 h-10 bg-white rounded-xl flex items-center justify-center text-teal shadow-sm border border-navy-100">
                            <i class="fa-solid fa-user-tie text-lg"></i>
                        </div>
                        <div>
                            <div class="font-bold text-sm" id="sim-patient-name">Kamran Khan</div>
                            <div class="text-[10px] text-gray-400">34 y/o • Software Engineer</div>
                        </div>
                    </div>
                    
                    <div class="text-xs space-y-1.5 pt-2 border-t border-navy-100 text-gray-600">
                        <div><strong>BP:</strong> <span id="sim-patient-bp">145/92 mmHg</span></div>
                        <div><strong>History:</strong> <span id="sim-patient-history">Occasional headache</span></div>
                        <div><strong>Lifestyle:</strong> <span id="sim-patient-lifestyle">3 cups strong tea, sedentary desk job</span></div>
                        <div class="bg-white/80 p-2 rounded-lg border border-navy-100 text-[11px] leading-tight mt-2 italic">
                            "Skeptical. Assumes headache is simple fatigue. Thinks he's too young for blood pressure medication."
                        </div>
                    </div>
                </div>

                <!-- Simulation Interactive Play Area (MD: 8 cols) -->
                <div class="md:col-span-8 space-y-4">
                    <div class="bg-teal-light/50 rounded-2xl p-4 border border-teal/10">
                        <div class="text-[10px] text-teal font-extrabold tracking-wider uppercase mb-1">Interactive Case counseling prompt</div>
                        <h4 class="text-sm font-bold text-navy-800" id="sim-question-text">
                            How do you respond to Kamran's skepticism regarding his elevated reading?
                        </h4>
                    </div>

                    <!-- Choices Matrix -->
                    <div class="space-y-2.5" id="sim-choices-container">
                        <!-- Simulated choices loaded here -->
                    </div>

                    <!-- Output Scores Bar -->
                    <div id="sim-feedback-card" class="bg-navy-50 rounded-xl p-4 border border-navy-100 hidden space-y-3">
                        <div class="flex items-center space-x-2 text-teal">
                            <i class="fa-solid fa-circle-info"></i>
                            <h5 class="text-xs font-bold uppercase tracking-wider">Clinical Assessor Feedback</h5>
                        </div>
                        <p class="text-xs text-navy-800 italic" id="sim-feedback-text">Feedback goes here...</p>
                        
                        <!-- Mini score meters -->
                        <div class="grid grid-cols-3 gap-3 text-center pt-2 border-t border-navy-100">
                            <div>
                                <div class="text-[9px] text-gray-500 font-bold uppercase">Empathy</div>
                                <div class="text-sm font-extrabold text-teal" id="sim-score-empathy">+20</div>
                            </div>
                            <div>
                                <div class="text-[9px] text-gray-500 font-bold uppercase">Accuracy</div>
                                <div class="text-sm font-extrabold text-navy-800" id="sim-score-accuracy">+20</div>
                            </div>
                            <div>
                                <div class="text-[9px] text-gray-500 font-bold uppercase">Referral Fit</div>
                                <div class="text-sm font-extrabold text-rose-500" id="sim-score-referral">+15</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </main>

    <!-- COMPLIANCE & LEGAL FOOTER -->
    <footer class="bg-navy-900 text-white mt-12 py-8 px-4 border-t-2 border-teal">
        <div class="max-w-5xl mx-auto space-y-6">
            <div class="flex flex-col sm:flex-row justify-between items-center gap-4">
                <div class="text-center sm:text-left space-y-1">
                    <h3 class="text-base font-bold text-white">Scan Your Pressure™ Campaign Portal</h3>
                    <p class="text-xs text-gray-400">Discovering Hypertension™ is a non-commercial national CSR initiative managed by PharmEvo.</p>
                </div>
                <div class="text-center sm:text-right">
                    <p class="text-xs text-teal font-extrabold tracking-wider uppercase">Bilingual Offline-First Edition</p>
                    <p class="text-[10px] text-gray-500">Built in partnership with LUMS and regional cardiology hospitals.</p>
                </div>
            </div>

            <div class="border-t border-white/5 pt-4 text-center text-[10px] sm:text-xs text-gray-400 space-y-2 leading-relaxed">
                <p>
                    <strong>CLINICAL DISCLAIMER:</strong> This tool acts as an educational and behavioral screening performance review. It does not replace formal cardiologist clinical diagnostics or treatment guidelines. Please consult medical providers before altering medication regimens or physical habits.
                </p>
                <p class="text-gray-500">
                    © 2026 PharmEvo (Pvt.) Ltd. • Designed & Developed by Uzair Ahmad • All data processed locally under cryptographic standard protocols.
                </p>
            </div>
        </div>
    </footer>

    <!-- INTERACTIVE SCRIPTS & IMMERSIVE STATE CONTROLLER -->
    <script>
        // Local Asset Fallbacks in case local filenames are not found
        function renderLogoFallback(imgElement) {
            imgElement.onerror = null;
            imgElement.src = "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 150 40' width='150' height='40'><rect width='150' height='40' fill='%23051321' rx='6'/><text x='15' y='25' fill='%2300A8A8' font-family='system-ui' font-weight='900' font-size='18'>PharmEvo</text></svg>";
        }

        function renderAvatarFallback(imgElement) {
            imgElement.onerror = null;
            imgElement.src = "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100' width='100' height='100'><rect width='100' height='100' fill='%230A2540'/><text x='50' y='55' fill='%2300A8A8' font-family='system-ui' font-weight='bold' font-size='32' text-anchor='middle'>UA</text></svg>";
        }

        // CLINICAL CONFIGURATION DATA
        const CLINICAL_FACTORS = {
            sleep: {
                question_en: "How would you describe your general sleep patterns over the last month?",
                question_ur: "پچھلے ایک ماہ کے دوران آپ کے سونے کا انداز کیسا رہا ہے؟",
                icon: "fa-bed",
                options: [
                    { id: "perfect", text_en: "Optimal Sleep (7-9 hours of deep rest)", text_ur: "بھرپور نیند (7 سے 9 گھنٹے پرسکون نیند)", penalty: 0 },
                    { id: "intermittent", text_en: "Intermittent Sleep (frequent wake-ups / rest disruptions)", text_ur: "غیر مستقل نیند (بار بار جاگنا یا نیند میں خلل)", penalty: 8 },
                    { id: "deprived", text_en: "Severe Deprivation (under 5 hours nightly / sleep debt)", text_ur: "شدید کمی (رات کو 5 گھنٹے سے کم نیند)", penalty: 18 }
                ]
            },
            salt: {
                question_en: "Describe your dietary sodium and salt profile patterns:",
                question_ur: "اپنے کھانے میں نمک کے استعمال کے متعلق بتائیں:",
                icon: "fa-salt-shaker",
                options: [
                    { id: "rare", text_en: "Light home cooking, highly restricted salt intake", text_ur: "ہلکا نمک، گھر کا کھانا اور پرہیز", penalty: 0 },
                    { id: "moderate", text_en: "Moderate daily salt / processed food use", text_ur: "اعتدال پسند نمک / عام روزمرہ کا کھانا", penalty: 10 },
                    { id: "high", text_en: "High Intake (daily Biryani, Nihari, Karahis & packaged snacks)", text_ur: "زیادہ نمک (روزانہ بریانی، نہاری، کڑاہی یا فاسٹ فوڈ)", penalty: 22 }
                ]
            },
            stress: {
                question_en: "What is your typical chronic stress level during working hours?",
                question_ur: "کام کے دوران آپ کے ذہنی دباؤ کی عام سطح کیا ہوتی ہے؟",
                icon: "fa-brain",
                options: [
                    { id: "low", text_en: "Low/Relaxed (balanced routines, structured breathing)", text_ur: "کم / پرسکون (متوازن معمولات اور ذہنی سکون)", penalty: 0 },
                    { id: "moderate", text_en: "Typical daily work anxieties / task pressures", text_ur: "معمولی دباؤ (روزمرہ کے کام کا بوجھ اور فکر)", penalty: 8 },
                    { id: "high", text_en: "High Burnout (constant somatization, heart racing, anxiety)", text_ur: "شدید ذہنی دباؤ (مسلسل پریشانی اور کام کا بوجھ)", penalty: 20 }
                ]
            },
            stimulants: {
                question_en: "How frequent is your consumption of energy drinks, strong tea, or caffeine?",
                question_ur: "انرجی ڈرنکس، تیز چائے یا کیفین کا استعمال کتنا ہے؟",
                icon: "fa-mug-hot",
                options: [
                    { id: "none", text_en: "Rarely/None", text_ur: "کبھی کبھار یا بالکل نہیں", penalty: 0 },
                    { id: "moderate", text_en: "Moderate (1-2 cups of tea or coffee daily)", text_ur: "درمیانہ (روزانہ 1 سے 2 کپ چائے یا کافی)", penalty: 6 },
                    { id: "high", text_en: "High Use (multiple daily cups, caffeine pills, or energy cans)", text_ur: "بہت زیادہ (انرجی ڈرنکس یا روزانہ کثرت سے چائے)", penalty: 14 }
                ]
            },
            activity: {
                question_en: "How would you describe your cardiovascular aerobic activity?",
                question_ur: "آپ روزانہ کتنی جسمانی ورزش یا چہل قدمی کرتے ہیں؟",
                icon: "fa-person-walking",
                options: [
                    { id: "active", text_en: "Active (regular structured exercise / brisk walking)", text_ur: "فعال (باقاعدگی سے ورزش یا تیز چہل قدمی)", penalty: 0 },
                    { id: "light", text_en: "Light movement / occasional walking", text_ur: "ہلکی پھلکی حرکت / کبھی کبھار چہل قدمی", penalty: 5 },
                    { id: "sedentary", text_en: "Sedentary (desk job, low physical mobilization)", text_ur: "سست طرز زندگی (زیادہ تر بیٹھ کر کام کرنا)", penalty: 15 }
                ]
            },
            last_check: {
                question_en: "When was the last time you checked your formal blood pressure?",
                question_ur: "آپ نے آخری بار اپنے بلڈ پریشر کا باقاعدہ معائنہ کب کیا تھا؟",
                icon: "fa-clock",
                options: [
                    { id: "recent", text_en: "Within the last 30 days", text_ur: "پچھلے 30 دنوں کے اندر", penalty: 0 },
                    { id: "distant", text_en: "More than 12 months ago", text_ur: "ایک سال سے زائد عرصہ پہلے", penalty: 5 },
                    { id: "never", text_en: "Never Checked", text_ur: "کبھی نہیں معائنہ کروایا", penalty: 12 }
                ]
            }
        };

        const TRANSLATIONS = {
            EN: {
                lblCSRBadge: "PharmEvo CSR National Initiative",
                lblLandingTitle: "Your Heart’s Performance Review",
                lblLandingSub: "Hypertension is a silent performance killer. Take control today with our 60-second diagnostic risk analysis, digital tracking passport, and direct connection to localized expert clinics.",
                btnStartReview: "Start Performance Review",
                btnOpenPassport: "Open My Digital Passport",
                btnBack: "Back",
                lblQuizEncrypted: "Secure Local Processing",
                lblCheckinStep: "Step 2: Interactive Biometrics",
                lblBpInputTitle: "Enter Your Blood Pressure",
                lblBpInputSub: "Adjust sliders to input your actual BP reading measured at the booth or home monitor.",
                lblSbp: "Systolic Pressure (SBP)",
                lblDbp: "Diastolic Pressure (DBP)",
                lblMapVal: "Mean Arterial Pressure (MAP)",
                lblRegPanelTitle: "Profile Personalization (Optional)",
                lblRegConsent: "I consent to secure, offline hashing of my biometrics for the digital passport program.",
                btnCalculateScore: "Assess Performance",
                lblReportHeader: "Assessment Complete",
                lblReportTitle: "Your Heart Performance Review",
                lblHeartScore: "HEART HEALTH SCORE",
                lblAssessmentRisk: "RISK CLASSIFICATION",
                lblMeasuredBP: "Measured Blood Pressure",
                lblCalculatedMAP: "Mean Perfusion (MAP)",
                lblMapRange: "Healthy Target: 70-100",
                lblDrivers: "Key Lifestyle Factors Tested",
                btnDashboard: "Go to Digital Passport",
                btnDashboardSub: "Log habits & build streaks",
                btnHandoff: "Handoff to Bot",
                btnHandoffSub: "Sync to PharmEvo WhatsApp CSR",
                btnReferral: "Find Near Clinic",
                btnReferralSub: "Free consultations booking",
                lblPassportTitle: "My Digital Health Passport",
                lblPassportSub: "Keep tracking daily habits to protect your cardiovascular performance scores.",
                btnNewAssessment: "Assess Again",
                btnQuickLog: "Quick Log BP",
                lblStreakBadge: "HABIT ADHERENCE STREAK",
                lblStreakDays: "Days Active",
                lblHabitChecklist: "DAILY COMPLIANCE CHECKLIST",
                lblHabitMeds: "Took prescribed BP medication today",
                lblHabitSalt: "No high-sodium meals consumed (Biryani/Nihari)",
                lblHabitWalk: "Logged 20 mins brisk exercise",
                lblActiveCampaign: "Connected Clinic Network",
                lblActiveCampaignSub: "Book a physical follow-up with specialized doctors for your high risk profile levels.",
                lblChartTitle: "Biometric Performance Trend",
                lblChartSub: "Tracking Systolic and Diastolic entries over time",
                lblHistoricalTitle: "All Logged Passport Entries",
                tblColDate: "Date",
                tblColBP: "BP Value",
                tblColMAP: "MAP",
                tblColActions: "Classification",
                coachTitle: "Coach Kem — AI Health Companion",
                coachSub: "Local Rule-Based Compliance Assistant",
                lblCrisisModalTitle: "🚨 CRITICAL MEDICAL ALERT",
                lblCrisisModalSub: "Immediate Clinical Intervention Required!",
                lblCrisisModalDesc: "If you or the current user is experiencing somatic chest pain, blurry vision, severe localized headache, or sudden breathing issues, do not delay. This is a medical emergency.",
                btnCloseCrisisModal: "Close Warning Indicator",
                lblSimTitle: "HCP Counseling Simulator & Trainer"
            },
            UR: {
                lblCSRBadge: "فارما ایوو کا قومی فلاحی اقدام",
                lblLandingTitle: "آپ کے دل کی کارکردگی کا جائزہ",
                lblLandingSub: "بلڈ پریشر ایک خاموش قاتل ہے۔ آج ہی ہمارے 60 سیکنڈ کے تشخیصی ٹیسٹ، ڈیجیٹل پاسپورٹ، اور ماہر کلینکس کے ذریعے اپنے دل پر کنٹرول حاصل کریں۔",
                btnStartReview: "جائزہ شروع کریں",
                btnOpenPassport: "میرا ڈیجیٹل پاسپورٹ کھولیں",
                btnBack: "پیچھے",
                lblQuizEncrypted: "محفوظ مقامی پروسیسنگ",
                lblCheckinStep: "مرحلہ 2: بلڈ پریشر کی پیمائش",
                lblBpInputTitle: "اپنا بلڈ پریشر درج کریں",
                lblBpInputSub: "بوجھو یا گھر کے مانیٹر پر حاصل شدہ ریڈنگ کے مطابق سلائیڈرز کو تبدیل کریں۔",
                lblSbp: "سیسٹولک پریشر (SBP)",
                lblDbp: "ڈائیسٹولک پریشر (DBP)",
                lblMapVal: "اوسط شریانی دباؤ (MAP)",
                lblRegPanelTitle: "پروفائل کی معلومات (اختیاری)",
                lblRegConsent: "میں ڈیجیٹل پاسپورٹ پروگرام کے لیے اپنے بائیومیٹرکس کے محفوظ استعمال کی رضامندی دیتا ہوں۔",
                btnCalculateScore: "کارکردگی کا اندازہ لگائیں",
                lblReportHeader: "تشخیص مکمل ہو گئی",
                lblReportTitle: "آپ کے دل کی رپورٹ",
                lblHeartScore: "ہارٹ ہیلتھ اسکور",
                lblAssessmentRisk: "خطرے کی درجہ بندی",
                lblMeasuredBP: "پیمائش شدہ بلڈ پریشر",
                lblCalculatedMAP: "اوسط شریانی دباؤ (MAP)",
                lblMapRange: "صحت مند ہدف: 70-100",
                lblDrivers: "طرز زندگی کے عوامل کا جائزہ",
                btnDashboard: "ڈیجیٹل پاسپورٹ پر جائیں",
                btnDashboardSub: "عادات اور اسکور ٹریک کریں",
                btnHandoff: "واٹس ایپ ہینڈ آف",
                btnHandoffSub: "رپورٹ کو فارم ایوو واٹس ایپ بوٹ پر بھیجیں",
                btnReferral: "قریبی کلینک تلاش کریں",
                btnReferralSub: "مفت بکنگ اور مشورہ",
                lblPassportTitle: "میرا ڈیجیٹل ہیلتھ پاسپورٹ",
                lblPassportSub: "اپنے دل کی کارکردگی کے اسکور کو بچانے کے لیے روزانہ کی عادات کو ٹریک کریں۔",
                btnNewAssessment: "دوبارہ ٹیسٹ کریں",
                btnQuickLog: "بلڈ پریشر درج کریں",
                lblStreakBadge: "مسلسل عادات کی عکاسی",
                lblStreakDays: "دنوں سے سرگرم",
                lblHabitChecklist: "روزانہ کی عادات کی چیک لسٹ",
                lblHabitMeds: "آج بلڈ پریشر کی دوا لی ہے",
                lblHabitSalt: "آج تیز نمک والے کھانوں (بریانی/نہاری) سے پرہیز کیا",
                lblHabitWalk: "آج کم از کم 20 منٹ ورزش یا چہل قدمی کی",
                lblActiveCampaign: "منسلک کلینکس نیٹ ورک",
                lblActiveCampaignSub: "اپنے خطرے کے اسکور کے مطابق ماہر ڈاکٹر سے رابطے کے لیے کلینک منتخب کریں۔",
                lblChartTitle: "بلڈ پریشر کا رجحان",
                lblChartSub: "سیسٹولک اور ڈائیسٹولک ریڈنگز کا گراف",
                lblHistoricalTitle: "پاسپورٹ کی تمام تاریخ",
                tblColDate: "تاریخ",
                tblColBP: "بلڈ پریشر",
                tblColMAP: "اوسط دباؤ",
                tblColActions: "درجہ بندی",
                coachTitle: "کوچ کیم — صحت کا ساتھی",
                coachSub: "رہنمائی اور رہنمائی اسسٹنٹ",
                lblCrisisModalTitle: "🚨 ہنگامی طبی انتباہ",
                lblCrisisModalSub: "فوری طبی امداد کی ضرورت ہے!",
                lblCrisisModalDesc: "اگر آپ کو سینے میں درد، دھندلی بینائی، شدید سر درد، یا سانس لینے میں دشواری کا سامنا ہے تو تاخیر نہ کریں۔ یہ ایک ہنگامی طبی صورتحال ہے۔",
                btnCloseCrisisModal: "انتباہ بند کریں",
                lblSimTitle: "طبی ماہرین کے لیے تربیتی سمیلیٹر"
            }
        };

        // CLINICAL DIALOGUE SCENARIOS FOR SIMULATOR
        const SIM_CASE = {
            patient_meta: {
                name: "Kamran Khan",
                age: 34,
                occupation: "Software Engineer",
                avatar_icon: "fa-user-tie"
            },
            biometrics: {
                sbp: 145,
                dbp: 92,
                history: "Occasional headaches, stress-induced insomnia",
                lifestyle: "Consumes 3 cups of strong tea daily; sedentary desk job"
            },
            patient_attitude: "Skeptical. Believes he is 'too young' to have high blood pressure and assumes his headaches are simply work-related fatigue.",
            counseling_branches: [
                {
                    question: "How do you respond to Kamran's skepticism regarding his elevated reading?",
                    choices: [
                        {
                            id: "opt_a",
                            text: "Dismiss his claim and state firmly: 'Your blood pressure is high. You have hypertension and must start medication immediately.'",
                            empathy: -10, accuracy: 5, referral: 0,
                            feedback: "Incorrect approach. Aggressive, dictatorial messaging often causes younger patients to disengage from care entirely."
                        },
                        {
                            id: "opt_b",
                            text: "Normalize his experience with motivational interviewing: 'I understand you feel fine, Kamran. However, high pressure acts silently. Let's look at how your long working hours and tea intake impact your heart's performance score.'",
                            empathy: 20, accuracy: 20, referral: 15,
                            feedback: "Excellent. Framing the discussion around performance and daily sleep/tea lifestyle patterns helps build alliance and trust."
                        }
                    ]
                }
            ]
        };

        // CLINICAL CLINICS DIRECTORY
        const CLINICS_DATABASE = [
            { id: "nicvd-khi", name: "NICVD Cardiology Diagnostic Hub", city: "Karachi", details: "Main Hospital Road • (021) 99201271" },
            { id: "tabba-khi", name: "Tabba Heart Center Outpatient Care", city: "Karachi", details: "Federal B Area • (021) 111 822 224" },
            { id: "pims-isb", name: "PIMS Cardiac Sciences Unit", city: "Islamabad", details: "Sector G-8/3 • (051) 9261170" },
            { id: "pic-lhr", name: "Punjab Institute of Cardiology", city: "Lahore", details: "Jail Road • (042) 99203061" },
            { id: "fich-fsd", name: "Faisalabad Institute of Cardiology", city: "Faisalabad", details: "Sargodha Road • (041) 9201111" }
        ];

        // CLIENT-SIDE REACTIVE STATE MODEL
        const appState = {
            lang: "EN",
            currentScreen: "screen-landing",
            campaign: "LUMS-SPRING",
            quizAnswers: {},
            currentQuizStepIndex: 0,
            activeSBP: 120,
            activeDBP: 80,
            passportLogs: [],
            streakCount: 3,
            soundEnabled: true,
            chatHistory: []
        };

        // SOUND SYNTHESIS ENGINE (WEB AUDIO API)
        let audioCtx = null;

        function initAudio() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }
        }

        function toggleAudio() {
            appState.soundEnabled = !appState.soundEnabled;
            const btn = document.getElementById('btn-audio-toggle');
            if (appState.soundEnabled) {
                btn.innerHTML = '<i class="fa-solid fa-volume-high text-lg"></i>';
                btn.classList.remove('opacity-50');
                playChime();
            } else {
                btn.innerHTML = '<i class="fa-solid fa-volume-xmark text-lg"></i>';
                btn.classList.add('opacity-50');
            }
        }

        function playChime() {
            if (!appState.soundEnabled) return;
            try {
                initAudio();
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = 'sine';
                osc.frequency.setValueAtTime(1000, audioCtx.currentTime);
                osc.frequency.exponentialRampToValueAtTime(500, audioCtx.currentTime + 0.1);
                gain.gain.setValueAtTime(0.05, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.1);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start();
                osc.stop(audioCtx.currentTime + 0.1);
            } catch (e) {
                console.log("Audio synthesis deferred until interaction.");
            }
        }

        function playPhysiologicalHeartbeat(isCrisis = false) {
            if (!appState.soundEnabled) return;
            try {
                initAudio();
                const now = audioCtx.currentTime;
                const lubFreq = isCrisis ? 100 : 70;
                const dubFreq = isCrisis ? 120 : 80;
                const strength = isCrisis ? 0.25 : 0.15;
                
                // LUB tone
                playBeatTone(lubFreq, 0.08, now, strength);
                // DUB tone
                playBeatTone(dubFreq, 0.08, now + 0.15, strength);
            } catch (e) {}
        }

        function playBeatTone(freq, duration, startTime, strength) {
            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.type = 'triangle';
            osc.frequency.setValueAtTime(freq, startTime);
            osc.frequency.exponentialRampToValueAtTime(10, startTime + duration);
            gain.gain.setValueAtTime(strength, startTime);
            gain.gain.exponentialRampToValueAtTime(0.001, startTime + duration);
            osc.connect(gain);
            gain.connect(audioCtx.destination);
            osc.start(startTime);
            osc.stop(startTime + duration);
        }

        function playSuccessArpeggio() {
            if (!appState.soundEnabled) return;
            try {
                initAudio();
                const now = audioCtx.currentTime;
                const notes = [523.25, 659.25, 783.99, 1046.50]; // C Major arpeggio
                notes.forEach((freq, i) => {
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    const noteTime = now + (i * 0.08);
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(freq, noteTime);
                    gain.gain.setValueAtTime(0.04, noteTime);
                    gain.gain.exponentialRampToValueAtTime(0.001, noteTime + 0.2);
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    osc.start(noteTime);
                    osc.stop(noteTime + 0.2);
                });
            } catch (e) {}
        }

        // NAVIGATION CONTROLLER
        function navigateTo(screenId) {
            playChime();
            
            // Hide all screen views
            const screens = ["screen-landing", "screen-quiz", "screen-bp", "screen-results", "screen-passport"];
            screens.forEach(s => {
                const el = document.getElementById(s);
                if (el) el.classList.add("hidden");
            });

            // Reveal targeted screen
            const target = document.getElementById(screenId);
            if (target) {
                target.classList.remove("hidden");
                target.style.opacity = "0";
                setTimeout(() => {
                    target.style.opacity = "1";
                }, 50);
            }

            appState.currentScreen = screenId;

            // Trigger specific page load actions
            if (screenId === "screen-quiz") {
                loadQuizStep(0);
            } else if (screenId === "screen-bp") {
                handleBpSliderUpdate();
            } else if (screenId === "screen-passport") {
                renderHistoricalLogs();
            }
        }

        // BILINGUAL LANGUAGE MATRIX CONTROLLER
        function toggleLanguage() {
            appState.lang = (appState.lang === "EN") ? "UR" : "EN";
            
            // Update UI switch button text
            document.getElementById('lang-switch-lbl').innerText = (appState.lang === "EN") ? "اردو" : "English";
            
            // Apply text direction and custom font classes
            if (appState.lang === "UR") {
                document.body.classList.add("urdu-text");
                document.body.setAttribute("dir", "rtl");
            } else {
                document.body.classList.remove("urdu-text");
                document.body.setAttribute("dir", "ltr");
            }

            // Update all keys matching dictionary
            const elements = document.querySelectorAll("[data-key]");
            elements.forEach(el => {
                const key = el.getAttribute("data-key");
                if (TRANSLATIONS[appState.lang] && TRANSLATIONS[appState.lang][key]) {
                    el.innerText = TRANSLATIONS[appState.lang][key];
                }
            });

            // Update placeholders manually for inputs
            const inputName = document.getElementById("reg-name");
            const inputPhone = document.getElementById("reg-phone");
            if (inputName && inputPhone) {
                if (appState.lang === "UR") {
                    inputName.placeholder = "اپنا پورا نام درج کریں";
                    inputPhone.placeholder = "فون نمبر (صرف آف لائن پروسیسنگ)";
                } else {
                    inputName.placeholder = "Full Name ( احمد علی )";
                    inputPhone.placeholder = "Phone Hash Entry (03xxxxxxxxx)";
                }
            }

            // Reload active step or text strings
            if (appState.currentScreen === "screen-quiz") {
                loadQuizStep(appState.currentQuizStepIndex);
            } else if (appState.currentScreen === "screen-bp") {
                handleBpSliderUpdate();
            } else if (appState.currentScreen === "screen-results") {
                processFinalAssessment();
            } else if (appState.currentScreen === "screen-passport") {
                renderHistoricalLogs();
            }

            playChime();
        }

        // CAMPAIGN URL UTILITY CONFIGURE
        function configureCampaignCode() {
            const params = new URLSearchParams(window.location.search);
            const campaignParam = params.get('c') || params.get('campaign');
            if (campaignParam) {
                appState.campaign = campaignParam.toUpperCase();
            } else {
                appState.campaign = "LUMS-SPRING";
            }
            document.getElementById('badge-campaign-code').innerText = appState.campaign;
        }

        // QUIZ STEP WIZARD LOGIC
        function loadQuizStep(stepIndex) {
            appState.currentQuizStepIndex = stepIndex;
            const keys = Object.keys(CLINICAL_FACTORS);
            const activeKey = keys[stepIndex];
            const factor = CLINICAL_FACTORS[activeKey];

            // Render Progress Info
            const progressPercent = ((stepIndex + 1) / keys.length) * 100;
            document.getElementById("quiz-progress-fill").style.width = `${progressPercent}%`;
            
            if (appState.lang === "UR") {
                document.getElementById("quiz-step-indicator").innerText = `سوال ${stepIndex + 1} از 6`;
                document.getElementById("quiz-question-text").innerText = factor.question_ur;
            } else {
                document.getElementById("quiz-step-indicator").innerText = `Question ${stepIndex + 1} of 6`;
                document.getElementById("quiz-question-text").innerText = factor.question_en;
            }

            // Change header icons
            const iconEl = document.getElementById("quiz-question-icon");
            iconEl.className = `fa-solid ${factor.icon} text-xl`;

            // Back button toggle
            const prevBtn = document.getElementById("btn-quiz-prev");
            if (stepIndex === 0) {
                prevBtn.classList.add("invisible");
            } else {
                prevBtn.classList.remove("invisible");
            }

            // Load interactive options
            const optionsBox = document.getElementById("quiz-options-container");
            optionsBox.innerHTML = "";

            factor.options.forEach(opt => {
                const text = (appState.lang === "UR") ? opt.text_ur : opt.text_en;
                const isSelected = appState.quizAnswers[activeKey] === opt.id;
                
                const btn = document.createElement("button");
                btn.onclick = () => selectQuizOption(activeKey, opt.id);
                btn.className = `w-full text-left px-5 py-4 rounded-xl border transition-all text-xs sm:text-sm flex justify-between items-center ${
                    isSelected 
                        ? 'bg-teal-light border-teal text-teal font-bold' 
                        : 'bg-white border-navy-100 text-navy-800 hover:bg-navy-50'
                }`;

                // Force layout adjustment for Urdu
                if (appState.lang === "UR") {
                    btn.classList.add("text-right");
                }

                btn.innerHTML = `
                    <span>${text}</span>
                    <i class="fa-solid ${isSelected ? 'fa-circle-check text-teal' : 'fa-circle-notch text-navy-100'} text-base"></i>
                `;
                optionsBox.appendChild(btn);
            });
        }

        function selectQuizOption(factorKey, optionId) {
            appState.quizAnswers[factorKey] = optionId;
            playChime();
            
            // Auto transition or manual step increment
            setTimeout(() => {
                const keys = Object.keys(CLINICAL_FACTORS);
                if (appState.currentQuizStepIndex < keys.length - 1) {
                    loadQuizStep(appState.currentQuizStepIndex + 1);
                } else {
                    navigateTo("screen-bp");
                }
            }, 250);
        }

        function quizPrevStep() {
            if (appState.currentQuizStepIndex > 0) {
                loadQuizStep(appState.currentQuizStepIndex - 1);
            }
        }

        // BLOOD PRESSURE CLINICAL EQUATIONS CONTROLLER
        function calculateMAP(sbp, dbp) {
            return dbp + (sbp - dbp) / 3;
        }

        function classifyBP(sbp, dbp) {
            if (sbp < 120 && dbp < 80) {
                return { tier: "Normal", color: "text-teal", label_en: "Normal BP", label_ur: "نورمل بلڈ پریشر", penalty: 0 };
            } else if (sbp >= 120 && sbp <= 129 && dbp < 80) {
                return { tier: "Elevated", color: "text-amber-500", label_en: "Elevated BP", label_ur: "بڑھا ہوا بلڈ پریشر", penalty: 8 };
            } else if ((sbp >= 130 && sbp <= 139) || (dbp >= 80 && dbp <= 89)) {
                return { tier: "Stage1", color: "text-orange-500", label_en: "High BP Stage 1", label_ur: "ہائی بلڈ پریشر سٹیج 1", penalty: 15 };
            } else if ((sbp >= 140 && sbp <= 179) || (dbp >= 90 && dbp <= 119)) {
                return { tier: "Stage2", color: "text-red-500", label_en: "High BP Stage 2", label_ur: "ہائی بلڈ پریشر سٹیج 2", penalty: 25 };
            } else {
                return { tier: "Crisis", color: "text-red-700", label_en: "Hypertensive Crisis", label_ur: "انتہائی خطرناک ہائی بلڈ پریشر", penalty: 35 };
            }
        }

        function handleBpSliderUpdate() {
            const sbp = parseInt(document.getElementById("sys-slider").value);
            const dbp = parseInt(document.getElementById("dia-slider").value);

            appState.activeSBP = sbp;
            appState.activeDBP = dbp;

            // Update real-time metric numbers
            document.getElementById("val-sbp-lbl").innerHTML = `${sbp} <span class="text-[10px] text-gray-400 font-normal">mmHg</span>`;
            document.getElementById("val-dbp-lbl").innerHTML = `${dbp} <span class="text-[10px] text-gray-400 font-normal">mmHg</span>`;
            document.getElementById("realtime-bp-val").innerText = `${sbp}/${dbp}`;

            // Calculate MAP dynamically
            const map = calculateMAP(sbp, dbp).toFixed(1);
            document.getElementById("realtime-map-val").innerText = `${map} mmHg`;

            // Calculate real-time classification
            const cls = classifyBP(sbp, dbp);
            const label = (appState.lang === "UR") ? cls.label_ur : cls.label_en;
            
            const clsBadge = document.getElementById("realtime-classification");
            clsBadge.innerText = label;
            clsBadge.className = `text-[11px] font-bold uppercase tracking-wider mt-0.5 ${cls.color}`;

            // Pulse the heart animation speed dependent on crisis state
            const pulseRing = document.getElementById("heart-pulse-ring");
            const heartIcon = document.getElementById("visual-heart-icon");
            
            if (cls.tier === "Crisis") {
                pulseRing.className = "absolute inset-0 bg-red-600/35 rounded-full pulse-element";
                heartIcon.className = "fa-solid fa-heart text-red-600 text-5xl relative z-10 transition-transform duration-100 scale-110";
                // Trigger dynamic sound beep warning
                playPhysiologicalHeartbeat(true);
            } else {
                pulseRing.className = "absolute inset-0 bg-red-500/10 rounded-full pulse-element";
                heartIcon.className = "fa-solid fa-heart text-red-500 text-5xl relative z-10 transition-transform duration-200";
                playPhysiologicalHeartbeat(false);
            }
        }

        // CALCULATE INTEGRATED CARDIOVASCULAR SCORE (HEART HEALTH SCORE R)
        function processFinalAssessment() {
            let totalLifestylePenalties = 0;
            const breakdownDrivers = [];

            // Compute lifestyle deductions
            Object.keys(CLINICAL_FACTORS).forEach(key => {
                const answerId = appState.quizAnswers[key];
                const factor = CLINICAL_FACTORS[key];
                const chosenOption = factor.options.find(o => o.id === answerId);
                const penalty = chosenOption ? chosenOption.penalty : 0;
                
                totalLifestylePenalties += penalty;

                if (penalty > 0) {
                    breakdownDrivers.push({
                        name_en: key.replace('_', ' ').toUpperCase(),
                        name_ur: (appState.lang === "UR") ? getUrduLabel(key) : key,
                        penalty: penalty,
                        tier: penalty > 15 ? "High Impact" : "Moderate"
                    });
                }
            });

            // Compute Biometric deductions
            const bpClass = classifyBP(appState.activeSBP, appState.activeDBP);
            const bpPenalty = bpClass.penalty;

            // Clamping equation R = 100 - (Lifestyle Penalties + BP Penalty)
            let rawScore = 100 - (totalLifestylePenalties + bpPenalty);
            const heartScore = Math.max(5, Math.min(100, rawScore));

            // Populate Diagnostic Report Screen UI
            document.getElementById("lbl-gauge-score").innerText = heartScore;
            
            // Draw Dynamic SVG Circle Gauge
            const circle = document.getElementById("results-gauge-fill");
            const strokeOffset = 251.2 - (251.2 * heartScore) / 100;
            circle.style.strokeDashoffset = strokeOffset;
            
            // Adjust gauge color depending on clinical score output
            if (heartScore >= 75) {
                circle.setAttribute("stroke", "#00A8A8"); // Teal (Healthy)
            } else if (heartScore >= 50) {
                circle.setAttribute("stroke", "#F59E0B"); // Amber (Warning)
            } else {
                circle.setAttribute("stroke", "#EF4444"); // Coral/Red (High Risk)
            }

            // Set plain English/Urdu risk descriptions
            let riskTier = "";
            if (heartScore >= 80) {
                riskTier = (appState.lang === "UR") ? "مستحکم صحت کارکردگی" : "Excellent Performance";
            } else if (heartScore >= 60) {
                riskTier = (appState.lang === "UR") ? "معمولی منفی اثرات" : "Moderate Risk Drivers Detected";
            } else {
                riskTier = (appState.lang === "UR") ? "شدید کارڈیک خطرہ" : "High Cardiovascular Risk!";
            }
            document.getElementById("lbl-risk-tier").innerText = riskTier;

            // Render checked logs on results page
            document.getElementById("lbl-res-bp").innerText = `${appState.activeSBP}/${appState.activeDBP}`;
            document.getElementById("lbl-res-bp-class").innerText = (appState.lang === "UR") ? bpClass.label_ur : bpClass.label_en;
            document.getElementById("lbl-res-bp-class").className = `text-[10px] font-bold uppercase ${bpClass.color}`;
            
            const dot = document.getElementById("lbl-res-bp-dot");
            if (bpClass.tier === "Crisis") dot.className = "w-2.5 h-2.5 rounded-full bg-red-700 animate-ping";
            else if (bpClass.tier === "Stage2") dot.className = "w-2.5 h-2.5 rounded-full bg-red-500";
            else if (bpClass.tier === "Stage1") dot.className = "w-2.5 h-2.5 rounded-full bg-orange-500";
            else dot.className = "w-2.5 h-2.5 rounded-full bg-teal";

            const calculatedMAP = calculateMAP(appState.activeSBP, appState.activeDBP).toFixed(1);
            document.getElementById("lbl-res-map").innerText = `${calculatedMAP} mmHg`;

            // Display drivers breakdown inside result column
            const driversBox = document.getElementById("results-drivers-container");
            driversBox.innerHTML = "";

            if (breakdownDrivers.length === 0) {
                driversBox.innerHTML = `
                    <div class="text-xs text-teal font-semibold text-center py-4">
                        <i class="fa-solid fa-circle-check"></i> No negative risk factors logged! Optimal score performance.
                    </div>
                `;
            } else {
                breakdownDrivers.forEach(drv => {
                    const pct = (drv.penalty / 22) * 100; // Normalized scale against max penalty
                    const driverLabel = (appState.lang === "UR") ? getUrduLabel(drv.name_en.toLowerCase()) : drv.name_en;
                    
                    const drvDiv = document.createElement("div");
                    drvDiv.className = "space-y-1";
                    drvDiv.innerHTML = `
                        <div class="flex justify-between items-center text-xs">
                            <span class="font-bold text-navy-800">${driverLabel}</span>
                            <span class="text-gray-500 text-[10px]">Penalty: -${drv.penalty} pts</span>
                        </div>
                        <div class="w-full h-1.5 bg-gray-100 rounded-full overflow-hidden">
                            <div class="h-full bg-rose-500" style="width: ${pct}%"></div>
                        </div>
                    `;
                    driversBox.appendChild(drvDiv);
                });
            }

            // Append this assessment log to offline database
            savePassportLogEntry(appState.activeSBP, appState.activeDBP, bpClass.label_en);

            // Navigate to results screen
            navigateTo("screen-results");

            // Play successful synthesis melody
            playSuccessArpeggio();

            // Crisis override check to warn immediate emergency medical intervention
            if (bpClass.tier === "Crisis") {
                setTimeout(() => {
                    triggerCrisisEmergencyModal();
                }, 1000);
            }
        }

        function getUrduLabel(key) {
            const dictionary = {
                sleep: "سونے کا انداز",
                salt: "نمک کا استعمال",
                stress: "ذہنی دباؤ",
                stimulants: "چائے / انرجی ڈرنکس",
                activity: "چہل قدمی اور ورزش",
                last_check: "آخری معائنہ"
            };
            return dictionary[key.trim().toLowerCase()] || key;
        }

        // CRISIS OVERRIDE OVERLAY CONTROLLER
        function triggerCrisisEmergencyModal() {
            document.getElementById("crisis-override-modal").classList.remove("hidden");
            playPhysiologicalHeartbeat(true);
        }

        function dismissCrisisModal() {
            document.getElementById("crisis-override-modal").classList.add("hidden");
        }

        // WHATSAPP SECURE DATA DEEP LINK GENERATOR
        function triggerWhatsAppHandoff() {
            const nameValue = document.getElementById("reg-name").value || "Anonymous User";
            const bpVal = `${appState.activeSBP}/${appState.activeDBP}`;
            const mapValue = calculateMAP(appState.activeSBP, appState.activeDBP).toFixed(1);
            
            let saltState = appState.quizAnswers.salt || "moderate";
            let stressState = appState.quizAnswers.stress || "moderate";

            const payloadText = `Assalam-o-Alaikum PharmEvo, I completed my Scan-Your-Pressure Heart Performance Review!

[CRITICAL METRICS]
- Name: ${nameValue}
- Campaign ID: ${appState.campaign}
- Measured BP: ${bpVal} mmHg
- Perfusion MAP: ${mapValue} mmHg
- Sodium Risk: ${saltState.toUpperCase()}
- Job Stress: ${stressState.toUpperCase()}
- Tracked Streak: ${appState.streakCount} Days

Please register this biometric report into the regional screening referral database.`;

            const encodedMsg = encodeURIComponent(payloadText);
            const waNumber = "923001234567"; // Standard generic fallback bot number
            const destinationUrl = `https://wa.me/${waNumber}?text=${encodedMsg}`;
            
            // Redirect safely inside new window
            window.open(destinationUrl, "_blank");
        }

        // PASSPORT LOCAL DATABASE ENGINE
        function savePassportLogEntry(sbp, dbp, classification) {
            const newLog = {
                date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', hour: '2-digit', minute: '2-digit' }),
                sbp: sbp,
                dbp: dbp,
                map: calculateMAP(sbp, dbp).toFixed(1),
                classification: classification
            };

            appState.passportLogs.unshift(newLog); // Prepend to history stack
            
            // Maintain localized persistence
            localStorage.setItem('pharmevo_passport_history', JSON.stringify(appState.passportLogs));
        }

        function renderHistoricalLogs() {
            // Read storage backup
            const localRaw = localStorage.getItem('pharmevo_passport_history');
            if (localRaw) {
                appState.passportLogs = JSON.parse(localRaw);
            }

            // Update Entries count text
            const countLbl = document.getElementById("lbl-chart-count");
            countLbl.innerText = `${appState.passportLogs.length} ENTRIES`;

            const listContainer = document.getElementById("passport-history-table");
            listContainer.innerHTML = "";

            if (appState.passportLogs.length === 0) {
                listContainer.innerHTML = `
                    <tr>
                        <td colspan="4" class="py-6 text-center text-gray-400 font-medium">
                            No biometric logs found in local memory. Go start your review!
                        </td>
                    </tr>
                `;
            } else {
                appState.passportLogs.forEach(log => {
                    const tr = document.createElement("tr");
                    tr.className = "border-b border-navy-50 hover:bg-navy-50/50 transition-colors";
                    
                    tr.innerHTML = `
                        <td class="py-3 font-medium text-navy-800">${log.date}</td>
                        <td class="py-3 text-center font-bold text-navy-800">${log.sbp}/${log.dbp}</td>
                        <td class="py-3 text-center text-gray-500 font-mono">${log.map}</td>
                        <td class="py-3 text-right font-extrabold text-teal">${log.classification}</td>
                    `;
                    listContainer.appendChild(tr);
                });
            }

            plotTrendsGraph();
        }

        // QUICK LOG DIALOG MANAGEMENT
        function openLogModal() {
            document.getElementById("quick-log-modal").classList.remove("hidden");
        }

        function closeLogModal() {
            document.getElementById("quick-log-modal").classList.add("hidden");
        }

        function submitQuickLog() {
            const sbp = parseInt(document.getElementById("quick-sys").value) || 120;
            const dbp = parseInt(document.getElementById("quick-dia").value) || 80;

            appState.activeSBP = sbp;
            appState.activeDBP = dbp;

            const bpClass = classifyBP(sbp, dbp);
            savePassportLogEntry(sbp, dbp, bpClass.label_en);
            
            closeLogModal();
            renderHistoricalLogs();
            playSuccessArpeggio();
        }

        // RESPONSIVE INTERACTIVE SVG CHART BUILDER
        function plotTrendsGraph() {
            const svg = document.getElementById("trend-graph-svg");
            svg.innerHTML = ""; // Clear existing drawings

            const width = 400;
            const height = 150;
            const padding = 25;

            if (appState.passportLogs.length < 2) {
                svg.innerHTML = `
                    <text x="200" y="75" fill="#a1a1aa" font-size="11" font-family="system-ui" text-anchor="middle">
                        Log at least 2 readings to construct visual trends.
                    </text>
                `;
                return;
            }

            // Slice logs to graph max 5 recent points
            const dataPoints = [...appState.passportLogs].slice(0, 5).reverse();
            const maxSbp = Math.max(...dataPoints.map(p => p.sbp), 180);
            const minDbp = Math.min(...dataPoints.map(p => p.dbp), 60);
            
            const sbpRange = maxSbp - minDbp;

            // Compute Coordinates
            const pointsSbp = [];
            const pointsDbp = [];

            const stepX = (width - padding * 2) / (dataPoints.length - 1);

            dataPoints.forEach((pt, i) => {
                const x = padding + (i * stepX);
                
                // SBP normalization mapping
                const sbpY = height - padding - (((pt.sbp - minDbp) / sbpRange) * (height - padding * 2));
                // DBP normalization mapping
                const dbpY = height - padding - (((pt.dbp - minDbp) / sbpRange) * (height - padding * 2));

                pointsSbp.push({ x, y: sbpY, val: pt.sbp });
                pointsDbp.push({ x, y: dbpY, val: pt.dbp });
            });

            // Draw grid guidelines
            svg.innerHTML += `
                <line x1="${padding}" y1="${padding}" x2="${width - padding}" y2="${padding}" stroke="#E6EFF5" stroke-dasharray="4"/>
                <line x1="${padding}" y1="${height - padding}" x2="${width - padding}" y2="${height - padding}" stroke="#E6EFF5"/>
            `;

            // Draw Lines
            let sbpPath = `M ${pointsSbp[0].x} ${pointsSbp[0].y}`;
            let dbpPath = `M ${pointsDbp[0].x} ${pointsDbp[0].y}`;

            for (let i = 1; i < dataPoints.length; i++) {
                sbpPath += ` L ${pointsSbp[i].x} ${pointsSbp[i].y}`;
                dbpPath += ` L ${pointsDbp[i].x} ${pointsDbp[i].y}`;
            }

            // Append lines into viewport
            svg.innerHTML += `<path d="${sbpPath}" fill="none" stroke="#EF4444" stroke-width="3" stroke-linecap="round"/>`;
            svg.innerHTML += `<path d="${dbpPath}" fill="none" stroke="#00A8A8" stroke-width="3" stroke-linecap="round"/>`;

            // Draw interactive dots & numeric descriptors
            pointsSbp.forEach(pt => {
                svg.innerHTML += `
                    <circle cx="${pt.x}" cy="${pt.y}" r="4" fill="#EF4444"/>
                    <text x="${pt.x}" y="${pt.y - 8}" font-size="8" font-weight="bold" font-family="system-ui" fill="#EF4444" text-anchor="middle">${pt.val}</text>
                `;
            });

            pointsDbp.forEach(pt => {
                svg.innerHTML += `
                    <circle cx="${pt.x}" cy="${pt.y}" r="4" fill="#00A8A8"/>
                    <text x="${pt.x}" y="${pt.y + 12}" font-size="8" font-weight="bold" font-family="system-ui" fill="#00A8A8" text-anchor="middle">${pt.val}</text>
                `;
            });
        }

        // CLINICAL GAMIFIED HABIT CHECKBOX TRACKER
        function toggleHabitAdherence(habitType) {
            playChime();
            const medsChecked = document.getElementById("habit-meds").checked;
            const saltChecked = document.getElementById("habit-salt").checked;
            const walkChecked = document.getElementById("habit-walk").checked;

            // Incremental score logic
            let completedCount = 0;
            if (medsChecked) completedCount++;
            if (saltChecked) completedCount++;
            if (walkChecked) completedCount++;

            appState.streakCount = 3 + completedCount; // Baseline campaign score simulation
            document.getElementById("lbl-streak-val").innerText = appState.streakCount;
        }

        // CLINIC NETWORK SEARCH & FILTER SYSTEM
        function openClinicSearch() {
            navigateTo("screen-passport");
            document.getElementById("clinic-city-filter").focus();
        }

        function filterClinics() {
            const city = document.getElementById("clinic-city-filter").value;
            const list = document.getElementById("clinic-routing-list");
            list.innerHTML = "";

            const filtered = CLINICS_DATABASE.filter(c => city === "all" || c.city === city);

            filtered.forEach(clinic => {
                const item = document.createElement("div");
                item.className = "bg-white p-3 rounded-lg border border-navy-100 flex justify-between items-center text-xs shadow-sm hover:border-teal transition-all";
                item.innerHTML = `
                    <div class="space-y-0.5">
                        <div class="font-bold text-navy-800 flex items-center gap-1">
                            <i class="fa-solid fa-square-h text-rose-500"></i>
                            <span>${clinic.name}</span>
                        </div>
                        <div class="text-[10px] text-gray-500">${clinic.city} • ${clinic.details}</div>
                    </div>
                    <a href="https://wa.me/923001234567?text=BOOK_CONSULTATION_${clinic.id}" target="_blank" class="bg-teal text-white px-2.5 py-1 rounded font-bold text-[10px] hover:bg-teal-hover transition">
                        BOOK
                    </a>
                `;
                list.appendChild(item);
            });
        }

        // LOCAL CHATBOT KERNEL ("COACH KEM" ASSISTANT)
        let isChatOpen = false;

        function toggleCoachKemDrawer() {
            const body = document.getElementById("coach-chat-body");
            const toggleIcon = document.getElementById("coach-drawer-toggle-icon");
            playChime();

            if (isChatOpen) {
                body.style.height = "0px";
                toggleIcon.className = "fa-solid fa-chevron-up text-sm";
                isChatOpen = false;
            } else {
                body.style.height = "380px";
                toggleIcon.className = "fa-solid fa-chevron-down text-sm";
                isChatOpen = true;
                
                // Initialize thread with default instructions
                if (appState.chatHistory.length === 0) {
                    appendCoachMessage("bot", "Assalam-o-Alaikum! I am Coach Kem, your PharmEvo health assistant. Ask me anything about diet, salt (Biryani/Karahi), missed medications, or sudden symptoms.");
                    loadQuickChips();
                }
            }
        }

        function appendCoachMessage(sender, text) {
            const box = document.getElementById("coach-message-thread");
            const bubble = document.createElement("div");
            
            if (sender === "bot") {
                bubble.className = "flex items-start space-x-2 max-w-[85%] mr-auto";
                bubble.innerHTML = `
                    <div class="w-7 h-7 bg-teal text-white flex items-center justify-center rounded-full flex-shrink-0 text-xs">
                        <i class="fa-solid fa-user-doctor"></i>
                    </div>
                    <div class="bg-white rounded-2xl rounded-tl-none p-3 border border-navy-100 text-xs text-navy-800 leading-relaxed shadow-sm">
                        ${text}
                    </div>
                `;
            } else {
                bubble.className = "flex items-start space-x-2 max-w-[85%] ml-auto justify-end";
                bubble.innerHTML = `
                    <div class="bg-teal-light text-teal rounded-2xl rounded-tr-none p-3 border border-teal/10 text-xs leading-relaxed shadow-sm">
                        ${text}
                    </div>
                    <div class="w-7 h-7 bg-navy-800 text-white flex items-center justify-center rounded-full flex-shrink-0 text-xs">
                        <i class="fa-solid fa-user"></i>
                    </div>
                `;
            }

            box.appendChild(bubble);
            box.scrollTop = box.scrollHeight; // Auto Scroll
            appState.chatHistory.push({ sender, text });
        }

        const KEM_INTENT_RESPONSES = [
            {
                keywords: [/biryani/i, /salt/i, /karahi/i, /nihari/i, /نمک/i, /کھانا/i, /بریانی/i],
                reply_en: "South Asian spices and restaurant Biryanis contain massive amounts of sodium. A single plate can exceed your recommended 2,000mg daily budget! Opt for homemade, unsalted cooking and use lemon juice or coriander for flavor seasoning instead.",
                reply_ur: "ہمارے کھانوں میں نمک کی کثرت ہوتی ہے۔ بریانی یا کڑاہی کا ایک پلیٹ آپ کے دن بھر کے نمک کی گنجائش سے تجاوز کر سکتا ہے۔ ہمیشہ گھر کا بنا ہوا ہلکے نمک کا کھانا استعمال کریں اور ذائقے کے لیے لیموں یا دھنیا استعمال کریں۔"
            },
            {
                keywords: [/missed/i, /pill/i, /medicine/i, /dose/i, /forgot/i, /دوا/i, /دواء/i, /بھول/i],
                reply_en: "Consistency is your heart's best shield. If you forgot a daily pill, do NOT take a double dose next time. Take it as soon as you remember, or if it's close to the next dose, skip the missed one. Always use a daily pill-organizer box!",
                reply_ur: "بلڈ پریشر کی دوا میں تسلسل سب سے ضروری ہے۔ اگر آپ گولی بھول جائیں تو اگلی بار دو گولی ایک ساتھ نہ لیں۔ جیسے ہی یاد آئے دوا لیں، بشرطیکہ اگلی خوراک کا وقت قریب نہ ہو۔"
            },
            {
                keywords: [/pain/i, /chest/i, /blurry/i, /vision/i, /headache/i, /درد/i, /سر/i, /سینے/i],
                reply_en: "🚨 CRITICAL RED FLAG DETECTED. Somatic chest pain, sudden blurry vision, or extreme localized headaches can indicate a hypertensive crisis. Please immediately seek assistance or go to the nearest coronary emergency center!",
                reply_ur: "🚨 ہنگامی انتباہ۔ اگر آپ کو سینے میں شدید درد، دھندلی نظر، یا بہت زیادہ سر درد محسوس ہو رہا ہے، تو یہ ایک ہنگامی صورتحال ہو سکتی ہے۔ فوری طور پر قریبی ہسپتال کے ایمرجنسی وارڈ سے رجوع کریں۔"
            }
        ];

        function handleChatSubmit(event) {
            if (event.key === "Enter") {
                submitChatMessage();
            }
        }

        function submitChatMessage() {
            const input = document.getElementById("chat-input-text");
            const query = input.value.trim();
            if (!query) return;

            appendCoachMessage("user", query);
            input.value = "";
            playChime();

            // Match intent patterns
            setTimeout(() => {
                let matched = false;
                for (const item of KEM_INTENT_RESPONSES) {
                    const matches = item.keywords.some(pattern => pattern.test(query));
                    if (matches) {
                        const reply = (appState.lang === "UR") ? item.reply_ur : item.reply_en;
                        appendCoachMessage("bot", reply);
                        matched = true;
                        
                        // If crisis keyword matched, auto trigger emergency modal
                        if (query.toLowerCase().includes("pain") || query.toLowerCase().includes("chest") || query.includes("درد")) {
                            triggerCrisisEmergencyModal();
                        }
                        break;
                    }
                }

                if (!matched) {
                    const fallback = (appState.lang === "UR") 
                        ? "میں آپ کے سوال کا تجزیہ نہیں کر سکا۔ براہ کرم نمک، بریانی، دوائیوں کی پابندی یا ہنگامی علامات کے متعلق پوچھیں۔" 
                        : "I could not fully match that query. Try asking about salt, Biryani swaps, daily medication tips, or red-flag cardiac symptoms.";
                    appendCoachMessage("bot", fallback);
                }
            }, 600);
        }

        function loadQuickChips() {
            const container = document.getElementById("chat-quick-chips");
            container.innerHTML = "";

            const chips = [
                { text_en: "Biryani Swaps", text_ur: "بریانی کے اثرات", query: "Biryani salt levels" },
                { text_en: "Missed Medication", text_ur: "دوا بھول جانا", query: "Missed daily dose" },
                { text_en: "Cardiac Symptoms", text_ur: "دل کی علامات", query: "Chest pain warning" }
            ];

            chips.forEach(chip => {
                const label = (appState.lang === "UR") ? chip.text_ur : chip.text_en;
                const button = document.createElement("button");
                button.className = "bg-navy-50 hover:bg-teal-light hover:text-teal px-3 py-1 rounded-full text-[10px] font-bold text-navy-800 border border-navy-100 transition whitespace-nowrap";
                button.innerText = label;
                button.onclick = () => {
                    document.getElementById("chat-input-text").value = chip.query;
                    submitChatMessage();
                };
                container.appendChild(button);
            });
        }

        // HCP COUNSELING SIMULATOR LOGIC
        function loadSimCase() {
            document.getElementById("sim-patient-name").innerText = SIM_CASE.patient_meta.name;
            document.getElementById("sim-patient-bp").innerText = `${SIM_CASE.biometrics.sbp}/${SIM_CASE.biometrics.dbp} mmHg`;
            document.getElementById("sim-patient-history").innerText = SIM_CASE.biometrics.history;
            document.getElementById("sim-patient-lifestyle").innerText = SIM_CASE.biometrics.lifestyle;

            const activeNode = SIM_CASE.counseling_branches[0];
            document.getElementById("sim-question-text").innerText = activeNode.question;

            const container = document.getElementById("sim-choices-container");
            container.innerHTML = "";

            activeNode.choices.forEach(choice => {
                const button = document.createElement("button");
                button.onclick = () => submitSimChoice(choice);
                button.className = "w-full text-left p-3.5 bg-white border border-navy-100 hover:border-teal rounded-xl text-xs leading-relaxed transition shadow-sm hover:bg-navy-50/50 flex gap-2.5 items-start";
                button.innerHTML = `
                    <div class="w-5 h-5 bg-navy-50 rounded-full flex items-center justify-center border border-navy-100 text-[10px] font-bold text-teal mt-0.5 flex-shrink-0">
                        ${choice.id.replace('opt_', '').toUpperCase()}
                    </div>
                    <span>${choice.text}</span>
                `;
                container.appendChild(button);
            });

            document.getElementById("sim-feedback-card").classList.add("hidden");
        }

        function submitSimChoice(choice) {
            playChime();
            const feedbackCard = document.getElementById("sim-feedback-card");
            feedbackCard.classList.remove("hidden");

            document.getElementById("sim-feedback-text").innerText = choice.feedback;
            
            // Render assessment meters
            document.getElementById("sim-score-empathy").innerText = choice.empathy >= 0 ? `+${choice.empathy}` : choice.empathy;
            document.getElementById("sim-score-accuracy").innerText = choice.accuracy >= 0 ? `+${choice.accuracy}` : choice.accuracy;
            document.getElementById("sim-score-referral").innerText = choice.referral >= 0 ? `+${choice.referral}` : choice.referral;

            // Apply coloring classes depending on choice quality
            if (choice.empathy < 0) {
                document.getElementById("sim-score-empathy").className = "text-sm font-extrabold text-red-500";
            } else {
                document.getElementById("sim-score-empathy").className = "text-sm font-extrabold text-teal";
            }
        }

        // CLINICAL SPECIFICATION AUTOMATED TEST SUITE ENGINE
        function runSystemDiagnosticTests() {
            console.log("🧪 Running Discovering Hypertension™ Automated Assertion Suite...");
            let passed = 0;
            let failed = 0;

            function assert(expr, message) {
                if (expr) {
                    console.log(`%c[PASS] ${message}`, "color: #00A8A8; font-weight: bold;");
                    passed++;
                } else {
                    console.error(`[FAIL] ${message}`);
                    failed++;
                }
            }

            // Test 1: Validate MAP equation accuracy
            const sbp = 140, dbp = 90;
            const computedMAP = calculateMAP(sbp, dbp);
            const expectedMAP = 90 + (140 - 90)/3;
            assert(Math.abs(computedMAP - expectedMAP) < 0.01, "Perfusion Mean Arterial Pressure (MAP) Accuracy test");

            // Test 2: Validate Hypertension classification categorization bounds
            const testNormal = classifyBP(115, 75);
            assert(testNormal.tier === "Normal", "Normal Biometric Category lower bound verified");

            const testCrisis = classifyBP(185, 125);
            assert(testCrisis.tier === "Crisis", "Critical Hypertensive Crisis upper bound verified");

            // Test 3: Local Storage persistence interface capability
            try {
                localStorage.setItem('diag_test_val', 'pharmevo_ok');
                const retrieved = localStorage.getItem('diag_test_val');
                assert(retrieved === 'pharmevo_ok', "Isolated sandbox local storage verified");
                localStorage.removeItem('diag_test_val');
            } catch (e) {
                console.error("Local storage verification failed");
                failed++;
            }

            console.log(`%cDiagnostic Suite Completed: ${passed} Passed | ${failed} Failed`, "color: #0A2540; font-weight: 800; text-decoration: underline;");
        }

        // APPLICATION CONSOLE BOOTSTRAP INITIALIZATION
        window.onload = function() {
            configureCampaignCode();
            filterClinics();
            loadSimCase();
            
            // Auto run internal diagnostics verification
            runSystemDiagnosticTests();
        }
    </script>
</body>
</html>
