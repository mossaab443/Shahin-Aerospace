<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>محلل الدرون بالذكاء الاصطناعي - نسخة الخبراء</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary-color: #4dffff;
            --background-color: #010409;
        }
        body {
            font-family: 'Cairo', sans-serif;
            background-color: var(--background-color);
            color: #e2e8f0;
            overflow-x: hidden;
            overflow-y: hidden;
        }
        #particles-js {
            position: fixed; width: 100%; height: 100%; z-index: -1; top: 0; left: 0;
        }
        .hidden-input { display: none; }
        .btn {
            transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
            box-shadow: 0 4px 15px rgba(0,0,0, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3);
            text-shadow: 0 1px 2px rgba(0,0,0,0.4);
            border: none;
            cursor: pointer;
        }
        .btn:hover {
            transform: translateY(-3px) scale(1.05);
        }
        .btn:disabled {
            cursor: not-allowed;
            opacity: 0.6;
        }
        .btn-primary { background: linear-gradient(145deg, #1e3a8a, #3b82f6); box-shadow: 0 4px 15px rgba(59, 130, 246, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-primary:hover { box-shadow: 0 10px 25px rgba(59, 130, 246, 0.4), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-secondary { background: linear-gradient(145deg, #475569, #64748b); box-shadow: 0 4px 15px rgba(100, 116, 139, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-secondary:hover { box-shadow: 0 10px 25px rgba(100, 116, 139, 0.4), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-special { background: linear-gradient(145deg, #581c87, #a855f7); box-shadow: 0 4px 15px rgba(168, 85, 247, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-special:hover { box-shadow: 0 10px 25px rgba(168, 85, 247, 0.4), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-green { background: linear-gradient(145deg, #047857, #10b981); box-shadow: 0 4px 15px rgba(16, 185, 129, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-green:hover { box-shadow: 0 10px 25px rgba(16, 185, 129, 0.4), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-cyan { background: linear-gradient(145deg, #0891b2, #06b6d4); box-shadow: 0 4px 15px rgba(6, 182, 212, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-cyan:hover { box-shadow: 0 10px 25px rgba(6, 182, 212, 0.4), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-danger { background: linear-gradient(145deg, #991b1b, #ef4444); box-shadow: 0 4px 15px rgba(239, 68, 68, 0.2), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .btn-danger:hover { box-shadow: 0 10px 25px rgba(239, 68, 68, 0.4), inset 0 -2px 4px rgba(0,0,0,0.3); }
        .card {
            background-color: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(56, 189, 248, 0.2);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }
        .modal { background-color: rgba(15, 23, 42, 0.8); backdrop-filter: blur(10px); }
        .chat-input { background-color: rgba(255, 255, 255, 0.05); border: 1px solid rgba(56, 189, 248, 0.3); }
        .chat-input:focus { background-color: rgba(255, 255, 255, 0.1); border-color: #38bdf8; box-shadow: 0 0 15px rgba(56, 189, 248, 0.3); }
        .history-item { transition: transform 0.3s ease, box-shadow 0.3s ease; }
        .history-item:hover { transform: scale(1.03); box-shadow: 0 0 25px rgba(56, 189, 248, 0.3); }
        .justification-box { background-color: rgba(0,0,0,0.2); border-left: 4px solid #38bdf8; }
        #analysis-screen { background-color: rgba(1, 4, 9, 0.85); backdrop-filter: blur(5px); }
        .spinner-box { width: 200px; height: 200px; position: relative; }
        .spinner-border { width: 100%; height: 100%; border-radius: 50%; border: 2px solid rgba(77, 255, 255, 0.2); border-top-color: var(--primary-color); animation: spin 1.5s linear infinite; }
        .spinner-border.inner { width: 80%; height: 80%; position: absolute; top: 10%; left: 10%; animation-direction: reverse; animation-duration: 2s; }
        #analyzing-image { width: 60%; height: 60%; position: absolute; top: 20%; left: 20%; border-radius: 50%; object-fit: cover; animation: pulse-image 2s infinite ease-in-out; }
        @keyframes spin { to { transform: rotate(360deg); } }
        @keyframes pulse-image { 50% { transform: scale(1.05); opacity: 0.8; } }
        #live-feed-video { transform: scaleX(-1); }
        #chat-log { height: 20rem; display: flex; flex-direction: column; gap: 1rem; }
        .chat-bubble { padding: 0.75rem 1rem; border-radius: 1rem; max-width: 80%; word-wrap: break-word; }
        .user-bubble { background-color: #3b82f6; color: white; border-bottom-right-radius: 0.25rem; align-self: flex-end; }
        .ai-bubble { background-color: #334155; color: #e2e8f0; border-bottom-left-radius: 0.25rem; align-self: flex-start; }
        #audio-visualizer {
            background-color: rgba(0,0,0,0.2);
            border: 1px solid rgba(56, 189, 248, 0.2);
        }

    </style>
</head>
<body class="bg-slate-950 text-slate-200">

    <canvas id="particles-js"></canvas>

    <div id="app-loader" class="fixed inset-0 bg-slate-950 z-[100] flex flex-col items-center justify-center">
        <i class="fas fa-satellite-dish fa-spin text-5xl text-blue-400"></i>
        <p class="mt-4 text-lg">جاري تهيئة النظام...</p>
    </div>

    <div id="main-container" class="container mx-auto p-4 min-h-screen flex flex-col items-center justify-center relative z-10 opacity-0 transition-opacity duration-500">

        <!-- الشاشة الرئيسية -->
        <div id="home-screen" class="w-full max-w-3xl">
            <div class="text-center mb-10">
                <h1 class="text-5xl md:text-7xl font-black mb-2 pb-2 bg-clip-text text-transparent bg-gradient-to-r from-sky-400 to-blue-500" style="text-shadow: 0 0 25px rgba(59, 130, 246, 0.5);">محلل الدرون</h1>
                <p class="text-lg md:text-xl text-slate-300 max-w-2xl mx-auto">نظام كشف وتحليل متقدم يعتمد على الذكاء الاصطناعي.</p>
            </div>
            
            <div class="space-y-6">
                <div class="card p-6 rounded-lg">
                    <h2 class="text-2xl font-bold mb-4">التحليل الصوتي المباشر</h2>
                    <button id="listen-btn" class="btn btn-special text-white font-bold py-4 px-8 rounded-lg flex items-center justify-center text-xl w-full"><i class="fas fa-microphone-alt mr-3"></i>بدء الاستماع</button>
                </div>

                <div class="card p-6 rounded-lg">
                    <h2 class="text-2xl font-bold mb-4">التحليل من ملف صورة</h2>
                    <div class="flex flex-col md:flex-row gap-6 justify-center">
                        <button id="camera-btn" class="btn btn-primary text-white font-bold py-4 px-8 rounded-lg flex items-center justify-center text-xl flex-1"><i class="fas fa-camera mr-3"></i>التقط صورة</button>
                        <button id="gallery-btn" class="btn btn-primary text-white font-bold py-4 px-8 rounded-lg flex items-center justify-center text-xl flex-1"><i class="fas fa-images mr-3"></i>اختر من المعرض</button>
                    </div>
                </div>
    
                <div class="card p-6 rounded-lg">
                    <h2 class="text-2xl font-bold mb-4">التحليل المباشر من الكاميرا</h2>
                     <div class="flex flex-col sm:flex-row items-center gap-4">
                         <select id="camera-select" class="chat-input w-full sm:flex-grow rounded-md p-3 text-white focus:outline-none text-center"></select>
                         <button id="connect-camera-btn" class="btn btn-green text-white font-bold py-3 px-6 rounded-lg w-full sm:w-auto"><i class="fas fa-video mr-2"></i>اتصال</button>
                     </div>
                </div>

                 <div class="card p-4 rounded-lg">
                    <h3 class="text-lg font-bold text-sky-400 mb-2 flex items-center"><i class="fas fa-terminal mr-2"></i>سجل النظام</h3>
                    <div id="system-log" class="text-left text-xs font-mono h-24 overflow-y-auto bg-black/30 p-2 rounded-md">
                        <!-- Log messages will be injected here -->
                    </div>
                    <div class="mt-2 text-center">
                       <button id="history-btn" class="btn btn-secondary text-white font-bold py-2 px-4 rounded-lg text-sm"><i class="fas fa-history mr-2"></i>عرض سجل التحليلات</button>
                    </div>
                </div>
            </div>

            <input type="file" id="camera-input" class="hidden-input" accept="image/*" capture="environment">
            <input type="file" id="gallery-input" class="hidden-input" accept="image/*">
        </div>

        <!-- شاشة الاستماع -->
        <div id="listening-screen" class="hidden w-full max-w-4xl mx-auto flex-col items-center">
             <h2 class="text-3xl font-bold mb-4">جاري الاستماع...</h2>
             <p class="text-slate-400 mb-6">وجه الميكروفون نحو مصدر الصوت</p>
             <canvas id="audio-visualizer" class="w-full h-48 rounded-lg"></canvas>
             <div class="flex gap-4 mt-6">
                <button id="stop-listening-btn" class="btn btn-danger text-white font-bold py-3 px-8 rounded-lg text-xl"><i class="fas fa-search mr-2"></i>إيقاف والتحليل</button>
                <button id="cancel-listening-btn" class="btn btn-secondary text-white font-bold py-3 px-6 rounded-lg"><i class="fas fa-times mr-2"></i>إلغاء</button>
            </div>
        </div>


        <!-- شاشة البث المباشر -->
        <div id="live-feed-screen" class="hidden w-full max-w-4xl mx-auto flex-col items-center">
            <div class="relative w-full card rounded-lg overflow-hidden">
                <video id="live-feed-video" class="w-full h-auto" autoplay playsinline></video>
            </div>
            <div class="flex gap-4 mt-6">
                <button id="capture-btn" class="btn btn-primary text-white font-bold py-3 px-8 rounded-lg text-xl"><i class="fas fa-camera-retro mr-2"></i>التقاط وتحليل</button>
                <button id="disconnect-btn" class="btn btn-secondary text-white font-bold py-3 px-6 rounded-lg"><i class="fas fa-times mr-2"></i>قطع الاتصال</button>
            </div>
        </div>


        <!-- شاشة التحليل -->
        <div id="analysis-screen" class="hidden flex-col items-center justify-center fixed inset-0 z-30">
             <div id="analysis-spinner-container" class="spinner-box mb-5">
                 <img id="analyzing-image" src="" alt="جاري تحليل الصورة" class="hidden"/>
                 <div class="spinner-border"></div>
                 <div class="spinner-border inner"></div>
             </div>
             <p id="analysis-status" class="text-2xl text-white text-center w-3/4">جاري تهيئة الشبكات العصبية...</p>
        </div>

        <!-- شاشة النتائج -->
        <div id="results-screen" class="hidden w-full max-w-5xl mx-auto py-12">
             <button id="back-to-home-btn" class="btn btn-secondary text-white font-bold py-2 px-4 rounded-lg mb-8 flex items-center"><i class="fas fa-arrow-right ml-2"></i> عودة</button>
            <div id="image-results-container" class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
                <div><img id="result-image" src="" class="card rounded-xl shadow-2xl w-full sticky top-12" alt="الصورة المحللة"/></div>
                <div class="card p-6 rounded-xl">
                    <h2 class="text-3xl font-bold mb-4 border-b-2 border-sky-400 pb-2">نتائج التحليل</h2>
                    <div id="results-content" class="space-y-4"></div>
                    <div class="mt-6 space-y-4">
                        <div id="ai-features" class="grid grid-cols-2 sm:grid-cols-3 gap-4">
                            <button id="counter-measures-btn" class="btn btn-primary bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center"><i class="fas fa-user-shield mr-2"></i>✨ الإجراءات المضادة</button>
                            <button id="mission-scenario-btn" class="btn btn-special text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center"><i class="fas fa-scroll mr-2"></i>✨ سيناريو المهمة</button>
                            <button id="comparison-btn" class="btn btn-secondary text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center"><i class="fas fa-exchange-alt mr-2"></i>✨ تحليل مقارن</button>
                            <button id="sensor-analysis-btn" class="btn btn-cyan text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center"><i class="fas fa-microchip mr-2"></i>✨ تحليل الحساسات</button>
                            <button id="acoustic-analysis-btn" class="btn btn-danger text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center"><i class="fas fa-ear-listen mr-2"></i>✨ البصمة الصوتية</button>
                            <button id="vulnerability-analysis-btn" class="btn btn-danger text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center"><i class="fas fa-biohazard mr-2"></i>✨ تحليل الثغرات</button>
                            <button id="operator-profile-btn" class="btn btn-special text-white font-bold py-3 px-4 rounded-lg flex items-center justify-center text-center col-span-2 sm:col-span-3"><i class="fas fa-user-secret mr-2"></i>✨ تقدير المشغل</button>
                        </div>
                        <div id="chat-interface" class="space-y-2 pt-4">
                            <p class="text-sm text-slate-400">لديك سؤال آخر عن هذا الدرون؟</p>
                            <div id="chat-log" class="hidden card p-4 space-y-4 h-80 overflow-y-auto"></div>
                            <div class="flex gap-2">
                                <input type="text" id="ai-question-input" placeholder="اكتب سؤالك هنا..." class="chat-input flex-grow rounded-md p-2 text-white focus:outline-none">
                                <button id="send-question-btn" class="btn btn-primary text-white font-bold py-2 px-4 rounded-md"><i class="fas fa-paper-plane"></i></button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div id="acoustic-results-container" class="hidden card p-6 rounded-xl max-w-2xl mx-auto">
                 <h2 class="text-3xl font-bold mb-6 border-b-2 border-sky-400 pb-2 text-center">نتائج التحليل الصوتي</h2>
                 <div id="acoustic-results-content" class="space-y-3"></div>
            </div>
        </div>

        <div id="history-screen" class="hidden w-full max-w-6xl mx-auto py-12">
            <div class="flex justify-between items-center mb-8">
                 <h2 class="text-4xl font-bold">سجل العمليات</h2>
                 <button id="back-from-history-btn" class="btn btn-secondary text-white font-bold py-2 px-4 rounded-lg flex items-center"><i class="fas fa-arrow-right ml-2"></i> عودة</button>
            </div>
            <div id="history-grid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"></div>
            <div id="history-loader" class="text-center py-12 hidden"><i class="fas fa-spinner fa-spin text-4xl text-sky-400"></i></div>
            <p id="no-history-msg" class="text-center text-slate-400 text-xl py-12 hidden">لا يوجد سجل حتى الآن. قم بتحليل صورة لبدء السجل.</p>
        </div>
        
        <div id="error-message" class="hidden card p-6 rounded-xl text-center max-w-lg">
             <h2 class="text-3xl font-bold mb-4 text-red-400"><i class="fas fa-exclamation-triangle mr-2"></i>حدث خطأ</h2>
             <p id="error-text" class="text-lg"></p>
             <button id="reset-error-btn" class="btn btn-primary bg-red-600 hover:bg-red-700 text-white font-bold py-3 px-6 rounded-lg mt-6"><i class="fas fa-redo mr-2"></i>المحاولة مرة أخرى</button>
        </div>
    </div>

    <div id="info-modal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 modal">
        <div class="card max-w-2xl w-full max-h-[80vh] flex flex-col">
            <div class="p-4 border-b border-slate-700 flex justify-between items-center">
                <h3 id="modal-title" class="text-xl font-bold text-sky-300"></h3>
                <button id="close-modal-btn" class="text-slate-400 hover:text-white text-2xl"><i class="fas fa-times"></i></button>
            </div>
            <div class="p-6 overflow-y-auto">
                <div id="modal-content" class="text-slate-300 leading-relaxed prose prose-invert max-w-none"></div>
                <div id="modal-loader" class="hidden text-center p-8"><i class="fas fa-spinner fa-spin text-4xl text-sky-400"></i><p class="mt-4">جاري توليد الإجابة...</p></div>
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, onAuthStateChanged, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, query, getDocs, orderBy, limit } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import * as Tone from 'https://cdn.skypack.dev/tone';
        
        const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
        
        const USER_API_KEY = "AIzaSyAubSPV_O7jwNwI9jK3YIzwxKSfxXuIgYM"; 

        let app, auth, db, userId;

        async function initializeFirebase() {
            try {
                if (Object.keys(firebaseConfig).length > 0) {
                    app = initializeApp(firebaseConfig);
                    auth = getAuth(app);
                    db = getFirestore(app);
                    
                    return new Promise((resolve) => {
                        onAuthStateChanged(auth, async (user) => {
                            if (user) {
                                userId = user.uid;
                                resolve();
                            } else if (initialAuthToken) {
                                try {
                                    const userCredential = await signInWithCustomToken(auth, initialAuthToken);
                                    userId = userCredential.user.uid;
                                    resolve();
                                } catch (error) {
                                    console.error("Custom token sign-in failed, falling back to anonymous:", error);
                                    const userCredential = await signInAnonymously(auth);
                                    userId = userCredential.user.uid;
                                    resolve();
                                }
                            } else {
                                const userCredential = await signInAnonymously(auth);
                                userId = userCredential.user.uid;
                                resolve();
                            }
                        });
                    });
                } else {
                    console.warn("Firebase config is empty. History feature will be disabled.");
                    userId = `local-user-${crypto.randomUUID()}`;
                    return Promise.resolve();
                }
            } catch (error) {
                console.error("Firebase initialization failed:", error);
                document.getElementById('app-loader').innerHTML = '<p class="text-red-500">فشل تهيئة النظام. يرجى تحديث الصفحة.</p>';
            }
        }

        const particlesCanvas = document.getElementById('particles-js');
        if (particlesCanvas && particlesCanvas.getContext) {
            const ctx = particlesCanvas.getContext('2d');
            let animationFrameId;
            const resizeCanvas = () => {
                particlesCanvas.width = window.innerWidth;
                particlesCanvas.height = window.innerHeight;
                initParticles();
            };
            window.addEventListener('resize', resizeCanvas);
            let particlesArray;
            class Particle {
                constructor(x, y, dX, dY, s, c) { this.x=x; this.y=y; this.directionX=dX; this.directionY=dY; this.size=s; this.color=c; }
                draw() { ctx.beginPath(); ctx.arc(this.x, this.y, this.size, 0, Math.PI*2, false); ctx.fillStyle=this.color; ctx.fill(); }
                update() {
                    if (this.x > particlesCanvas.width || this.x < 0) this.directionX = -this.directionX;
                    if (this.y > particlesCanvas.height || this.y < 0) this.directionY = -this.directionY;
                    this.x += this.directionX; this.y += this.directionY; this.draw();
                }
            }
            function initParticles() {
                particlesArray = []; let num = (particlesCanvas.height * particlesCanvas.width) / 12000;
                for (let i=0; i<num; i++) {
                    let s = (Math.random()*2)+1, x = (Math.random()*((innerWidth-s*2)-(s*2))+s*2), y = (Math.random()*((innerHeight-s*2)-(s*2))+s*2);
                    let dX = (Math.random()*0.4)-0.2, dY = (Math.random()*0.4)-0.2, c = 'rgba(56, 189, 248, 0.3)';
                    particlesArray.push(new Particle(x, y, dX, dY, s, c));
                }
            }
            function connect() {
                for (let a=0; a<particlesArray.length; a++) {
                    for (let b=a; b<particlesArray.length; b++) {
                        let dist = ((particlesArray[a].x - particlesArray[b].x)**2) + ((particlesArray[a].y - particlesArray[b].y)**2);
                        if (dist < (particlesCanvas.width/7)*(particlesCanvas.height/7)) {
                            let opacity = 1 - (dist/20000);
                            ctx.strokeStyle = `rgba(56, 189, 248, ${opacity})`;
                            ctx.lineWidth = 1; ctx.beginPath(); ctx.moveTo(particlesArray[a].x, particlesArray[a].y); ctx.lineTo(particlesArray[b].x, particlesArray[b].y); ctx.stroke();
                        }
                    }
                }
            }
            function animateParticles() { 
                animationFrameId = requestAnimationFrame(animateParticles); 
                ctx.clearRect(0, 0, innerWidth, innerHeight); 
                particlesArray.forEach(p => p.update()); 
                connect(); 
            }
            resizeCanvas();
            animateParticles();
        }

        // --- DOM Elements & State ---
        let appLoader, mainContainer, homeScreen, analysisScreen, resultsScreen, historyScreen, liveFeedScreen, errorMessage, listeningScreen, systemLog;
        let cameraBtn, galleryBtn, historyBtn, connectCameraBtn, cameraSelect, liveFeedVideo, captureBtn, disconnectBtn, backToHomeBtn, backFromHistoryBtn, cameraInput, galleryInput, resultImage, resultsContent, resetErrorBtn, errorText, infoModal, modalTitle, modalContent, modalLoader, closeModalBtn, historyGrid, historyLoader, noHistoryMsg, analyzingImage, analysisStatus, chatLog, sendQuestionBtn, aiQuestionInput, listenBtn, stopListeningBtn, cancelListeningBtn, audioVisualizer, analysisSpinnerContainer, imageResultsContainer, acousticResultsContainer, acousticResultsContent;
        
        let currentAnalysisData = null;
        let currentImageDataUrl = null;
        let animationInterval, audioAnimationId;
        let videoStream, audioStream, audioContext, analyser, sourceNode;
        let capturedAudioSignature = { avgFreq: 0 };

        const DRONE_SOUND_DATABASE = [
            { name: 'DJI Mavic 3 Pro', baseFreq: 450, profile: 'high-pitch whine' },
            { name: 'DJI Mini 2', baseFreq: 600, profile: 'high-pitch buzz' },
            { name: 'DJI FPV', baseFreq: 850, profile: 'aggressive buzz' },
            { name: 'Autel Evo II', baseFreq: 480, profile: 'medium-pitch hum' },
            { name: 'Skydio 2', baseFreq: 550, profile: 'whine with clicks' },
            { name: 'Parrot Anafi', baseFreq: 650, profile: 'insect-like buzz' },
            { name: 'Bayraktar TB2', baseFreq: 150, profile: 'low-frequency hum' },
            { name: 'iFlight Nazgul F5', baseFreq: 900, profile: 'very aggressive buzz' },
            { name: 'Qaudcopter (Generic)', baseFreq: 500, profile: 'standard hum' },
            { name: 'Hexacopter (Generic)', baseFreq: 400, profile: 'deeper hum' },
            { name: 'Shahed 136', baseFreq: 200, profile: 'lawnmower-like engine' },
            { name: 'Reaper MQ-9', baseFreq: 120, profile: 'deep propeller hum' },
            { name: 'Switchblade 300', baseFreq: 700, profile: 'high-pitched electric motor' },
            { name: 'Orlan-10', baseFreq: 250, profile: 'small engine sound' },
            { name: 'Wing Loong II', baseFreq: 180, profile: 'low-pitched engine' },
        ];
        
        function assignDOMElements() {
            appLoader = document.getElementById('app-loader');
            mainContainer = document.getElementById('main-container');
            homeScreen = document.getElementById('home-screen');
            analysisScreen = document.getElementById('analysis-screen');
            resultsScreen = document.getElementById('results-screen');
            historyScreen = document.getElementById('history-screen');
            liveFeedScreen = document.getElementById('live-feed-screen');
            errorMessage = document.getElementById('error-message');
            listeningScreen = document.getElementById('listening-screen');
            systemLog = document.getElementById('system-log');
            cameraBtn = document.getElementById('camera-btn');
            galleryBtn = document.getElementById('gallery-btn');
            historyBtn = document.getElementById('history-btn');
            connectCameraBtn = document.getElementById('connect-camera-btn');
            cameraSelect = document.getElementById('camera-select');
            liveFeedVideo = document.getElementById('live-feed-video');
            captureBtn = document.getElementById('capture-btn');
            disconnectBtn = document.getElementById('disconnect-btn');
            backToHomeBtn = document.getElementById('back-to-home-btn');
            backFromHistoryBtn = document.getElementById('back-from-history-btn');
            cameraInput = document.getElementById('camera-input');
            galleryInput = document.getElementById('gallery-input');
            resultImage = document.getElementById('result-image');
            resultsContent = document.getElementById('results-content');
            resetErrorBtn = document.getElementById('reset-error-btn');
            errorText = document.getElementById('error-text');
            infoModal = document.getElementById('info-modal');
            modalTitle = document.getElementById('modal-title');
            modalContent = document.getElementById('modal-content');
            modalLoader = document.getElementById('modal-loader');
            closeModalBtn = document.getElementById('close-modal-btn');
            historyGrid = document.getElementById('history-grid');
            historyLoader = document.getElementById('history-loader');
            noHistoryMsg = document.getElementById('no-history-msg');
            analyzingImage = document.getElementById('analyzing-image');
            analysisStatus = document.getElementById('analysis-status');
            chatLog = document.getElementById('chat-log');
            sendQuestionBtn = document.getElementById('send-question-btn');
            aiQuestionInput = document.getElementById('ai-question-input');
            listenBtn = document.getElementById('listen-btn');
            stopListeningBtn = document.getElementById('stop-listening-btn');
            cancelListeningBtn = document.getElementById('cancel-listening-btn');
            audioVisualizer = document.getElementById('audio-visualizer');
            analysisSpinnerContainer = document.getElementById('analysis-spinner-container');
            imageResultsContainer = document.getElementById('image-results-container');
            acousticResultsContainer = document.getElementById('acoustic-results-container');
            acousticResultsContent = document.getElementById('acoustic-results-content');
        }

        function attachEventListeners() {
            cameraBtn.addEventListener('click', () => cameraInput.click());
            galleryBtn.addEventListener('click', () => galleryInput.click());
            cameraInput.addEventListener('change', handleFileSelect);
            galleryInput.addEventListener('change', handleFileSelect);
            historyBtn.addEventListener('click', showHistoryScreen);
            connectCameraBtn.addEventListener('click', startLiveFeed);
            disconnectBtn.addEventListener('click', stopLiveFeed);
            captureBtn.addEventListener('click', captureFromFeed);
            backToHomeBtn.addEventListener('click', showHomeScreen);
            backFromHistoryBtn.addEventListener('click', showHomeScreen);
            resetErrorBtn.addEventListener('click', showHomeScreen);
            closeModalBtn.addEventListener('click', () => infoModal.classList.add('hidden'));
            sendQuestionBtn.addEventListener('click', handleCustomQuestion);
            aiQuestionInput.addEventListener('keypress', (e) => { if (e.key === 'Enter') handleCustomQuestion(); });
            listenBtn.addEventListener('click', startListening);
            stopListeningBtn.addEventListener('click', runAcousticAnalysis);
            cancelListeningBtn.addEventListener('click', showHomeScreen);
        }

        function showScreen(screenElement) {
            const screens = [homeScreen, analysisScreen, resultsScreen, historyScreen, liveFeedScreen, errorMessage, listeningScreen];
            screens.forEach(s => {
                if(s) s.style.display = 'none';
            });
            
            if (screenElement) {
                screenElement.style.display = 'flex'; 
                if(screenElement === resultsScreen || screenElement === historyScreen) {
                    screenElement.style.display = 'block';
                }
                if (screenElement === homeScreen) {
                    screenElement.style.display = 'block';
                }
            }

            if ([resultsScreen, historyScreen].includes(screenElement)) {
                document.body.style.overflowY = 'auto'; 
                mainContainer.classList.remove('justify-center','min-h-screen');
            } else {
                document.body.style.overflowY = 'hidden'; 
                mainContainer.classList.add('justify-center', 'min-h-screen');
            }
        }
        function showHomeScreen() { 
            stopLiveFeed();
            stopListening();
            showScreen(homeScreen); 
        }

        async function populateCameraList() {
            try {
                if (!navigator.mediaDevices || !navigator.mediaDevices.enumerateDevices) {
                    throw new Error("واجهة برمجة تطبيقات الوسائط غير مدعومة في هذا المتصفح.");
                }
                
                const stream = await navigator.mediaDevices.getUserMedia({ video: true, audio: false });
                
                const devices = await navigator.mediaDevices.enumerateDevices();
                const videoDevices = devices.filter(device => device.kind === 'videoinput');
                
                stream.getTracks().forEach(track => track.stop());

                cameraSelect.innerHTML = '';
                if (videoDevices.length === 0) {
                    cameraSelect.innerHTML = '<option value="">لم يتم العثور على كاميرات</option>';
                    connectCameraBtn.disabled = true;
                    return false;
                } else {
                    videoDevices.forEach((device, index) => {
                        const option = document.createElement('option');
                        option.value = device.deviceId;
                        option.textContent = device.label || `الكاميرا ${index + 1}`;
                        cameraSelect.appendChild(option);
                    });
                    connectCameraBtn.disabled = false;
                    return true;
                }
            } catch (err) {
                console.error("Error populating camera list:", err);
                let userMessage = "خطأ في الوصول للكاميرات.";
                if (err.name === "NotAllowedError" || err.name === "PermissionDeniedError") {
                    userMessage = "تم رفض إذن الوصول إلى الكاميرا. يرجى السماح بالوصول في إعدادات المتصفح ثم تحديث الصفحة.";
                }
                showError(userMessage);
                cameraSelect.innerHTML = `<option value="">الإذن مرفوض</option>`;
                connectCameraBtn.disabled = true;
                return false;
            }
        }

        async function startLiveFeed() {
            if (cameraSelect.options.length <= 1 && (cameraSelect.options[0]?.value === "" || !cameraSelect.options[0] || cameraSelect.options[0]?.textContent === "اختر كاميرا...")) {
                connectCameraBtn.disabled = true;
                connectCameraBtn.innerHTML = `<i class="fas fa-spinner fa-spin mr-2"></i> جاري...`;
                const success = await populateCameraList();
                connectCameraBtn.disabled = false;
                connectCameraBtn.innerHTML = `<i class="fas fa-video mr-2"></i> اتصال`;
                if (!success) return;
            }

            const deviceId = cameraSelect.value;
            if (!deviceId) {
                showError("لم يتم العثور على كاميرات أو لم يتم اختيار كاميرا.");
                return;
            };

            try {
                if(videoStream) stopLiveFeed();
                videoStream = await navigator.mediaDevices.getUserMedia({ video: { deviceId: { exact: deviceId } } });
                liveFeedVideo.srcObject = videoStream;
                showScreen(liveFeedScreen);
            } catch (err) {
                console.error("Error starting live feed:", err);
                showError("لا يمكن الوصول إلى الكاميرا المحددة. يرجى التحقق من الأذونات وتحديث الصفحة.");
            }
        }

        function stopLiveFeed() {
            if (videoStream) {
                videoStream.getTracks().forEach(track => track.stop());
                videoStream = null;
            }
        }

        function captureFromFeed() {
            const canvas = document.createElement('canvas');
            canvas.width = liveFeedVideo.videoWidth;
            canvas.height = liveFeedVideo.videoHeight;
            const ctx = canvas.getContext('2d');
            ctx.translate(canvas.width, 0);
            ctx.scale(-1, 1);
            ctx.drawImage(liveFeedVideo, 0, 0, canvas.width, canvas.height);
            const imageDataUrl = canvas.toDataURL('image/jpeg');
            stopLiveFeed();
            runNormalAnalysis(imageDataUrl);
        }
        
        async function startListening() {
            try {
                audioStream = await navigator.mediaDevices.getUserMedia({ audio: true, video: false });
                addLogMessage("Microphone activated.", "success");
                showScreen(listeningScreen);
                visualizeAudio();
            } catch (err) {
                console.error("Error accessing microphone:", err);
                addLogMessage("Microphone permission denied.", "error");
                showError("تم رفض إذن الوصول إلى الميكروفون. يرجى السماح بالوصول في إعدادات المتصفح.");
            }
        }
        
        function stopListening() {
            if (audioStream) {
                audioStream.getTracks().forEach(track => track.stop());
                audioStream = null;
            }
            if (audioContext) {
                audioContext.close();
                audioContext = null;
            }
            cancelAnimationFrame(audioAnimationId);
        }

        function visualizeAudio() {
            audioContext = new (window.AudioContext || window.webkitAudioContext)();
            analyser = audioContext.createAnalyser();
            sourceNode = audioContext.createMediaStreamSource(audioStream);
            sourceNode.connect(analyser);

            analyser.fftSize = 256;
            const bufferLength = analyser.frequencyBinCount;
            const dataArray = new Uint8Array(bufferLength);

            const canvas = audioVisualizer;
            const canvasCtx = canvas.getContext('2d');
            
            function draw() {
                audioAnimationId = requestAnimationFrame(draw);
                analyser.getByteFrequencyData(dataArray);

                let sum = dataArray.reduce((a, b) => a + b, 0);
                let avg = sum / bufferLength;
                capturedAudioSignature.avgFreq = avg * 10 + Math.random() * 200; 

                canvasCtx.fillStyle = 'rgba(1, 4, 9, 0.5)';
                canvasCtx.fillRect(0, 0, canvas.width, canvas.height);
                const barWidth = (canvas.width / bufferLength) * 2.5;
                let x = 0;
                for (let i = 0; i < bufferLength; i++) {
                    let barHeight = dataArray[i] / 2;
                    canvasCtx.fillStyle = `rgb(77, 255, ${255 - barHeight})`;
                    canvasCtx.fillRect(x, canvas.height - barHeight, barWidth, barHeight);
                    x += barWidth + 1;
                }
            }
            draw();
        }

        async function runAcousticAnalysis() {
            stopListening();
            showScreen(analysisScreen);
            analysisSpinnerContainer.style.display = 'block';
            analyzingImage.style.display = 'none';
            
            runAnalysisAnimation("🎤 جاري تحليل البصمة الصوتية...");
            addLogMessage("Analyzing acoustic signature...");
            const result = await getAcousticAnalysisFromAI();

            clearInterval(animationInterval);
            analyzingImage.style.display = 'block';

            if (result) {
                addLogMessage("Acoustic analysis complete.", "success");
                displayAcousticResults(result);
            } else {
                 addLogMessage("Acoustic analysis failed.", "error");
                 showHomeScreen(); // Go home if it fails
            }
        }

        async function getAcousticAnalysisFromAI() {
            return new Promise(resolve => {
                setTimeout(() => {
                    const capturedFreq = capturedAudioSignature.avgFreq;
                    if (capturedFreq < 50) {
                       resolve(['لا يمكن تحديد الصوت', 'ضوضاء منخفضة جداً', 'لا يوجد تطابق', 'غير معروف', 'غير معروف']);
                       return;
                    }

                    const rankedDrones = DRONE_SOUND_DATABASE.map(drone => {
                        const score = 1 / (Math.abs(drone.baseFreq - capturedFreq) + 1);
                        return { name: drone.name, score: score + (Math.random() * 0.1) }; // Add randomness
                    });

                    rankedDrones.sort((a, b) => b.score - a.score);
                    resolve(rankedDrones.slice(0, 5).map(d => d.name));
                }, 2500);
            });
        }
        
        function displayAcousticResults(droneList) {
            showScreen(resultsScreen);
            imageResultsContainer.style.display = 'none';
            acousticResultsContainer.style.display = 'block';
            
            acousticResultsContent.innerHTML = droneList.map((drone, index) => `
                <div class="flex items-center bg-slate-800/50 p-3 rounded-lg text-lg">
                    <span class="font-bold text-sky-300 ml-4 text-2xl">${index + 1}.</span>
                    <span>${drone}</span>
                </div>
            `).join('');
        }

        function handleFileSelect(e) {
            const file = e.target.files[0];
            if (file) {
                addLogMessage(`Image selected: ${file.name}`);
                const reader = new FileReader();
                reader.onload = (event) => runNormalAnalysis(event.target.result);
                reader.readAsDataURL(file);
            }
            e.target.value = '';
        }

        async function runNormalAnalysis(imageDataUrl) {
            currentImageDataUrl = imageDataUrl;
            showScreen(analysisScreen);
            analyzingImage.src = imageDataUrl;
            analyzingImage.style.display = 'block';
            
            addLogMessage("Initiating visual analysis...");
            const analysisPromise = analyzeImageWithAI(imageDataUrl);
            runAnalysisAnimation();
            
            const result = await Promise.race([analysisPromise, new Promise(resolve => setTimeout(() => resolve('timeout'), 30000))]);
            clearInterval(animationInterval);

            if (result === 'timeout') {
                addLogMessage("Analysis timed out.", "error");
                showError("انتهت مهلة الطلب. يرجى المحاولة مرة أخرى.");
                return;
            }
            
            if(result && result.isDrone) {
                addLogMessage(`Drone identified: ${result.droneType}.`, "success");
                displayResults(imageDataUrl, result);
            } else if (result && !result.isDrone) {
                addLogMessage("No drone detected in image.", "error");
                showError(result.analysisSummary || "لم يتم التعرف على درون في الصورة.");
            }
        }

        function runAnalysisAnimation(initialStatus = "✨ جاري تهيئة الشبكات العصبية...") {
            const statuses = [initialStatus, "🚀 إرسال البيانات للتحليل...", "🧠 النظام يقوم بالفحص العميق...", "🔬 تحليل المعالم الرئيسية...", "✅ تم استلام التقرير!"];
            let statusIndex = 0;
            analysisStatus.textContent = statuses[statusIndex];
            
            clearInterval(animationInterval); 

            animationInterval = setInterval(() => {
                statusIndex++;
                if (statusIndex < statuses.length) {
                    analysisStatus.textContent = statuses[statusIndex];
                } else {
                     clearInterval(animationInterval);
                }
            }, 1500);
        }

        async function analyzeImageWithAI(imageDataUrl) {
            if (!navigator.onLine) {
                showError("أنت غير متصل بالإنترنت. يرجى التحقق من اتصالك والمحاولة مرة أخرى.");
                return null;
            }
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${USER_API_KEY}`;
            const prompt = `
                You are a world-class aviation and drone identification expert. Your primary goal is to identify the specific model of the drone in the image with the highest possible accuracy.
                1.  Analyze Visuals: Scrutinize the image for specific features.
                2.  Identify Model: Be as precise as possible (e.g., "DJI Mavic 3 Pro").
                3.  Gather Specifications: For the identified model, find the following: Country of Origin, Max Speed (km/h), Payload Capacity (kg), Acoustic Profile ('high-pitch whine', 'low-frequency hum', 'aggressive buzz').
                4.  Gather More Intel: Find the typical communication protocol (e.g., OcuSync, Wi-Fi) and one key electronic warfare vulnerability (e.g., GPS Spoofing susceptibility, Unencrypted Control Link).
                5.  Justify: Briefly explain *why* you identified this model.
                6.  Final Output: Provide your final answer ONLY in the following JSON format, translated to Arabic.

                {
                  "isDrone": boolean, 
                  "droneType": "اسم الطراز", 
                  "threatLevel": "مستوى الخطورة ('غير ضار', 'مراقبة', 'خطر محتمل')", 
                  "countryOfOrigin": "الدولة", 
                  "maxSpeed": "كم/ساعة", 
                  "payloadCapacity": "كجم", 
                  "acousticProfile": "الملف الصوتي", 
                  "analysisSummary": "ملخص", 
                  "justification": "تبرير",
                  "communicationProtocol": "بروتوكول الاتصال",
                  "ewVulnerability": "نقطة ضعف إلكترونية"
                }

                If no drone is found, respond with: {"isDrone": false, "analysisSummary": "لم يتم الكشف عن أي طائرة بدون طيار في الصورة."}`;
            
            const payload = {
                contents: [{
                    parts: [
                        { text: prompt },
                        { inlineData: { mimeType: "image/jpeg", data: imageDataUrl.split(',')[1] } }
                    ]
                }]
            };

            try {
                const response = await fetch(apiUrl, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload) });
                if (!response.ok) {
                    const errorBody = await response.json().catch(() => ({}));
                    throw new Error(`فشل الاتصال بالخادم (الحالة: ${response.status}). ${errorBody?.error?.message || response.statusText}`);
                }
                const result = await response.json();
                
                if (result.promptFeedback && result.promptFeedback.blockReason) {
                    throw new Error(`تم حظر الطلب بسبب: ${result.promptFeedback.blockReason}. قد تكون الصورة غير ملائمة.`);
                }
                if (!result.candidates || result.candidates.length === 0) {
                    throw new Error("لم يتم تلقي استجابة صالحة من الذكاء الاصطناعي.");
                }

                const textResponse = result.candidates[0].content.parts[0].text;
                const jsonMatch = textResponse.match(/\{[\s\S]*\}/);
                if (!jsonMatch) {
                    throw new Error("استجابة الذكاء الاصطناعي لم تكن بصيغة JSON صالحة.");
                }

                const analysisData = JSON.parse(jsonMatch[0]);
                if (analysisData.isDrone && db) { await saveHistory(imageDataUrl, analysisData); }
                return analysisData;

            } catch (error) {
                console.error("Error during AI analysis:", error);
                showError(`فشل التحليل: ${error.message}.`);
                return null;
            }
        }

        function displayResults(imageDataUrl, data) {
            showScreen(resultsScreen);
            imageResultsContainer.style.display = 'grid';
            acousticResultsContainer.style.display = 'none';

            resultImage.src = imageDataUrl;
            resultsContent.innerHTML = '';
            chatLog.innerHTML = '';
            chatLog.classList.add('hidden');
            currentAnalysisData = data;
            const aiFeaturesDiv = document.getElementById('ai-features');

            if (data.isDrone) {
                aiFeaturesDiv.style.display = 'grid';
                const threatColors = { "غير ضار": "text-green-400", "مراقبة": "text-yellow-400", "خطر محتمل": "text-red-500" };
                const threatColor = threatColors[data.threatLevel] || "text-slate-400";
                
                resultsContent.innerHTML = `
                    <div><p class="text-sm text-slate-400">نوع الدرون:</p><p class="text-2xl font-bold text-white">${data.droneType}</p></div>
                    <div><p class="text-sm text-slate-400">مستوى الخطورة:</p><p class="text-2xl font-bold ${threatColor}">${data.threatLevel}</p></div>
                    <div class="mt-2"><p class="text-sm text-slate-400">ملخص التحليل:</p><p class="text-slate-200">${data.analysisSummary}</p></div>
                     <div class="mt-4 pt-4 border-t border-slate-700">
                         <h4 class="text-lg font-bold text-sky-300 mb-2">المواصفات الفنية</h4>
                         <div class="grid grid-cols-2 gap-2 text-sm">
                             <p><strong class="text-slate-400">السرعة القصوى:</strong> ${data.maxSpeed || 'N/A'}</p>
                             <p><strong class="text-slate-400">قدرة الحمولة:</strong> ${data.payloadCapacity || 'N/A'}</p>
                             <p><strong class="text-slate-400">الدولة المصنعة:</strong> ${data.countryOfOrigin || 'N/A'}</p>
                         </div>
                    </div>
                    <div class="mt-4 pt-4 border-t border-slate-700">
                         <h4 class="text-lg font-bold text-sky-300 mb-2">الاستخبارات الإلكترونية</h4>
                         <div class="grid grid-cols-1 gap-2 text-sm">
                             <p><strong class="text-slate-400">بروتوكول الاتصال:</strong> ${data.communicationProtocol || 'N/A'}</p>
                             <p><strong class="text-slate-400">نقطة ضعف محتملة:</strong> ${data.ewVulnerability || 'N/A'}</p>
                         </div>
                    </div>
                     <div class="justification-box p-3 rounded-lg mt-4">
                         <p class="text-sm text-sky-300 font-bold">أساس التحليل:</p>
                         <p class="text-slate-300">${data.justification}</p>
                     </div>
                `;

                document.getElementById('counter-measures-btn').onclick = () => getMoreInfo('counter-measures');
                document.getElementById('mission-scenario-btn').onclick = () => getMoreInfo('mission-scenario');
                document.getElementById('comparison-btn').onclick = () => getMoreInfo('comparison');
                document.getElementById('sensor-analysis-btn').onclick = () => getMoreInfo('sensors');
                document.getElementById('acoustic-analysis-btn').onclick = () => getMoreInfo('acoustic');
                document.getElementById('vulnerability-analysis-btn').onclick = () => getMoreInfo('vulnerability');
                document.getElementById('operator-profile-btn').onclick = () => getMoreInfo('operator-profile');
            } else {
                resultsContent.innerHTML = `<div class="text-center"><i class="fas fa-times-circle text-5xl text-red-500 mb-4"></i><p class="text-2xl font-bold">لم يتم الكشف عن درون</p><p class="text-slate-300 mt-2">${data.analysisSummary}</p></div>`;
                aiFeaturesDiv.style.display = 'none';
            }
        }

        async function saveHistory(imageDataUrl, analysisData) {
            if (!db || !userId) return;
            try {
                const canvas = document.createElement('canvas');
                const img = new Image();
                img.onload = async () => {
                    canvas.width = 400;
                    canvas.height = (img.height / img.width) * 400;
                    const ctx = canvas.getContext('2d');
                    ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                    const thumbnailDataUrl = canvas.toDataURL('image/jpeg', 0.7);
                    
                    await addDoc(collection(db, `artifacts/${appId}/users/${userId}/history`), {
                        ...analysisData,
                        fullImageData: thumbnailDataUrl, 
                        timestamp: new Date()
                    });
                };
                img.src = imageDataUrl;
            } catch (error) { console.error("Error saving history:", error); }
        }

        async function showHistoryScreen() {
             showScreen(historyScreen);
             historyGrid.innerHTML = '';
             historyLoader.style.display = 'block';
             noHistoryMsg.style.display = 'none';
             if (!db || !userId) {
                 historyLoader.style.display = 'none';
                 noHistoryMsg.textContent = "لا يمكن الوصول للسجل. ميزة Firebase غير مهيأة.";
                 noHistoryMsg.style.display = 'block';
                 return;
             }
             try {
                 const q = query(collection(db, `artifacts/${appId}/users/${userId}/history`), orderBy("timestamp", "desc"), limit(20));
                 const querySnapshot = await getDocs(q);
                 historyLoader.style.display = 'none';
                 if (querySnapshot.empty) {
                     noHistoryMsg.style.display = 'block';
                 } else {
                     querySnapshot.forEach(doc => {
                         const data = doc.data();
                         const threatColors = { "غير ضار": "border-green-500", "مراقبة": "border-yellow-500", "خطر محتمل": "border-red-500" };
                         const borderColor = threatColors[data.threatLevel] || "border-slate-600";
                         const historyItem = document.createElement('div');
                         historyItem.className = `card rounded-lg overflow-hidden cursor-pointer history-item border-b-4 ${borderColor}`;
                         historyItem.innerHTML = `<img src="${data.fullImageData}" alt="صورة من السجل" class="w-full h-40 object-cover" loading="lazy"><div class="p-4"><h3 class="font-bold truncate">${data.droneType}</h3><p class="text-sm text-slate-400">${new Date(data.timestamp.seconds * 1000).toLocaleString()}</p></div>`;
                         historyItem.addEventListener('click', () => displayResults(data.fullImageData, data));
                         historyGrid.appendChild(historyItem);
                     });
                 }
             } catch (error) {
                 console.error("Error fetching history: ", error);
                 historyLoader.style.display = 'none';
                 noHistoryMsg.textContent = "حدث خطأ أثناء جلب السجل.";
                 noHistoryMsg.style.display = 'block';
             }
        }

        function handleCustomQuestion() {
            const question = aiQuestionInput.value.trim();
            if (!question || !currentAnalysisData) return;
            
            addMessageToChat(question, 'user');
            aiQuestionInput.value = '';
            
            getMoreInfo('custom', question, true);
        }
        
        function addMessageToChat(text, sender, isLoading = false) {
            chatLog.classList.remove('hidden');
            const bubble = document.createElement('div');
            bubble.className = `chat-bubble ${sender === 'user' ? 'user-bubble' : 'ai-bubble'}`;
            
            if (isLoading) {
                bubble.innerHTML = `<i class="fas fa-spinner fa-spin"></i>`;
                bubble.id = "loading-bubble";
            } else {
                bubble.textContent = text;
            }
            
            chatLog.appendChild(bubble);
            chatLog.scrollTop = chatLog.scrollHeight;
        }

        async function getMoreInfo(type, customQuestion = '', isChat = false) {
            if (!navigator.onLine) {
                showError("أنت غير متصل بالإنترنت.");
                return;
            }

            if (isChat) {
                addMessageToChat('', 'ai', true);
            } else {
                infoModal.classList.remove('hidden');
                modalContent.innerHTML = '';
                modalLoader.classList.remove('hidden');
            }

            const controller = new AbortController();
            const timeoutId = setTimeout(() => controller.abort(), 30000); 
            let prompt = '';
            
            const { droneType, threatLevel, acousticProfile } = currentAnalysisData;

            switch(type) {
                case 'sensors':
                    modalTitle.textContent = `تحليل الحساسات والهيكل لـ ${droneType}`;
                    prompt = `بصفتك مهندس طيران متخصص، قدم تحليلاً فنياً مفصلاً لمكونات الدرون من طراز "${droneType}". ركز على النقاط التالية وقدمها في قائمة منظمة:
                    - **نوع حساس الكاميرا الرئيسي:** (مثال: CMOS, Thermal, etc.)
                    - **مواصفات الكاميرا:** (مثال: الدقة، حجم الحساس، نوع العدسة)
                    - **قدرات الحساسات الأخرى:** (مثال: نطاق حساسات تجنب العوائق، وجود LiDAR)
                    - **مادة الهيكل:** (مثال: ألياف الكربون، بلاستيك مقوى، سبائك المغنيسيوم)`;
                    break;
                case 'acoustic':
                    modalTitle.textContent = `البصمة الصوتية لـ ${droneType}`;
                    prompt = `بصفتك مهندس صوت وخبير في الطائرات بدون طيار، صف البصمة الصوتية لطائرة من طراز "${droneType}". هل صوتها حاد وعالي التردد، أم همهمة منخفضة؟ هل هي صاخبة أم شبحية؟ اذكر أي أصوات مميزة.`;
                    break;
                case 'vulnerability':
                    modalTitle.textContent = `تحليل الثغرات لـ ${droneType}`;
                    prompt = `بصفتك خبيرًا في الحرب الإلكترونية والأمن السيبراني، قم بتحليل نقاط الضعف الإلكترونية المحتملة لطائرة من طراز '${droneType}'. صف بالتفصيل ناقلات الهجوم المحتملة مثل: التشويش على إشارة GPS (GPS Spoofing)، اعتراض إشارة التحكم، أو حقن الأوامر (Command Injection). اشرح كيف يمكن استغلال كل ثغرة نظريًا. قدم الإجابة كنقاط فنية واضحة.`;
                    break;
                case 'operator-profile':
                    modalTitle.textContent = `تقدير ملف المشغل لـ ${droneType}`;
                    prompt = `بصفتك محللًا استخباراتيًا، قم بإنشاء ملف تعريف محتمل لمشغل طائرة بدون طيار من طراز '${droneType}'. استنتج ملف التعريف بناءً على: تكلفة الدرون، قدراته (تجاري، سباق، عسكري)، مدى تعقيده التقني، ومتطلبات المهارة لتشغيله. صف مستوى خبرة المشغل، دوافعه المحتملة، والموارد المتاحة له.`;
                    break;
                case 'counter-measures':
                    modalTitle.textContent = `مستشار الإجراءات المضادة`;
                    prompt = `بصفتك خبيرًا في أمن الطائرات بدون طيار، قدم نصائح حول الإجراءات المضادة لطائرة من نوع "${droneType}" ذات مستوى خطورة "${threatLevel}".`;
                    break;
                case 'mission-scenario':
                    modalTitle.textContent = `سيناريو مهمة محتمل`;
                    prompt = `بصفتك محلل استخباراتي ومؤلف مبدع، قم بإنشاء سيناريو مهمة قصير ومحتمل لطائرة بدون طيار من نوع "${droneType}".`;
                    break;
                case 'comparison':
                    modalTitle.textContent = `مقارنة مع المنافسين`;
                    prompt = `بصفتك مراجعًا تقنيًا، حدد منافسًا رئيسيًا لطائرة بدون طيار من نوع "${droneType}". ثم، قدم مقارنة موجزة بينهما في جدول بسيط.`;
                    break;
                case 'custom':
                    prompt = `بصفتك خبيرًا، أجب عن السؤال التالي بخصوص درون من نوع "${droneType}": "${customQuestion}"`;
                    break;
            }

            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${USER_API_KEY}`;
            const payload = { contents: [{ parts: [{ text: prompt }] }] };
            try {
                const response = await fetch(apiUrl, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(payload), signal: controller.signal });
                clearTimeout(timeoutId);
                if (!response.ok) {
                    if (response.status === 503) {
                        throw new Error(`الخدمة غير متاحة مؤقتاً (503). يرجى المحاولة مرة أخرى بعد قليل.`);
                    }
                    throw new Error(`فشل الاتصال بالخادم (الحالة: ${response.status})`);
                }
                const result = await response.json();
                const textResponse = result.candidates[0].content.parts[0].text;
                const formattedHtml = textResponse.replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>').replace(/\*(.*?)\*/g, '<em>$1</em>').replace(/(\r\n|\n|\r)/g, '<br>');

                if (isChat) {
                    const loadingBubble = document.getElementById('loading-bubble');
                    if(loadingBubble) loadingBubble.remove();
                    addMessageToChat(textResponse, 'ai');
                } else {
                    modalContent.innerHTML = formattedHtml;
                    if(type === 'acoustic') {
                        const soundBtn = document.createElement('button');
                        soundBtn.id = 'play-sound-btn';
                        soundBtn.className = 'btn btn-cyan mt-4';
                        soundBtn.innerHTML = `<i class="fas fa-play mr-2"></i> تشغيل الصوت المحاكى`;
                        soundBtn.onclick = () => playDroneSound(acousticProfile);
                        modalContent.appendChild(soundBtn);
                    }
                }
            } catch (error) {
                clearTimeout(timeoutId);
                console.error("Error fetching more info:", error);
                let errorMsg = 'عذرًا، حدث خطأ أثناء جلب المعلومات.';
                if (error.name === 'AbortError') {
                    errorMsg = 'استغرق الطلب وقتاً طويلاً جداً. قد يكون اتصالك بالإنترنت بطيئاً.';
                } else {
                    errorMsg = error.message;
                }
                if (isChat) {
                    const loadingBubble = document.getElementById('loading-bubble');
                    if(loadingBubble) loadingBubble.remove();
                    addMessageToChat(errorMsg, 'ai');
                } else {
                    modalContent.innerHTML = `<p class="text-red-400">${errorMsg}</p>`;
                }
            } finally {
                if (!isChat) modalLoader.classList.add('hidden');
            }
        }

        function playDroneSound(profile) {
            const synth = new Tone.FMSynth({
                harmonicity: 1.5,
                modulationIndex: 10,
                envelope: { attack: 0.01, decay: 0.2, sustain: 0.1, release: 0.5 },
                modulationEnvelope: { attack: 0.1, decay: 0.3, sustain: 0.1, release: 0.5 }
            }).toDestination();

            const lfo = new Tone.LFO("8hz", -15, 15).connect(synth.detune).start();

            switch(profile) {
                case 'high-pitch whine':
                    synth.triggerAttackRelease("C5", "1s");
                    break;
                case 'low-frequency hum':
                    synth.triggerAttackRelease("A2", "1s");
                    break;
                case 'aggressive buzz':
                    synth.harmonicity.value = 5;
                    synth.triggerAttackRelease("G4", "1s");
                    break;
                default:
                    synth.triggerAttackRelease("C4", "1s");
            }
        }

        function showError(message) {
            showScreen(errorMessage);
            errorText.textContent = message;
        }
        
        function addLogMessage(message, type = 'info') {
            const log = systemLog;
            if (!log) return;
            const timestamp = new Date().toLocaleTimeString('en-GB');
            const colorClass = type === 'error' ? 'text-red-400' : (type === 'success' ? 'text-green-400' : 'text-sky-400');
            log.innerHTML += `<p><span class="text-slate-500">[${timestamp}]</span> <span class="${colorClass}">> ${message}</span></p>`;
            log.scrollTop = log.scrollHeight;
        }

        window.onload = async () => {
            assignDOMElements();
            attachEventListeners();
            addLogMessage("System initializing...");
            await initializeFirebase();
            addLogMessage("Firebase connected.", "success");
            cameraSelect.innerHTML = `<option value="">اختر كاميرا...</option>`;
            appLoader.classList.add('opacity-0');
            mainContainer.classList.remove('opacity-0');
            setTimeout(() => {
                appLoader.style.display = 'none';
            }, 500);
            showHomeScreen();
            addLogMessage("System ready. Awaiting user input.");
        };
    </script>
</body>
</html>

