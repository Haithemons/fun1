<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Who is a Good Girl? 🐶💖</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Canvas Confetti Library -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Fredoka & Nunito -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Nunito:wght@400;700&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Fredoka', 'Nunito', sans-serif;
            background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 50%, #e0e7ff 100%);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated Floating Background Elements */
        .bg-particle {
            position: absolute;
            pointer-events: none;
            animation: float 6s ease-in-out infinite;
            opacity: 0.6;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px) rotate(0deg);
            }
            50% {
                transform: translateY(-20px) rotate(10deg);
            }
        }

        /* Pulsing Glow Animation */
        @keyframes pulse-glow {
            0%, 100% {
                box-shadow: 0 10px 25px -5px rgba(244, 114, 182, 0.4), 0 8px 10px -6px rgba(244, 114, 182, 0.2);
            }
            50% {
                box-shadow: 0 20px 35px -5px rgba(244, 114, 182, 0.7), 0 12px 15px -6px rgba(244, 114, 182, 0.4);
            }
        }

        .pulse-btn {
            animation: pulse-glow 2s infinite;
        }

        /* Celebration Card Pop In */
        @keyframes popIn {
            0% {
                transform: scale(0.3) rotate(-10deg);
                opacity: 0;
            }
            70% {
                transform: scale(1.1) rotate(3deg);
            }
            100% {
                transform: scale(1) rotate(0deg);
                opacity: 1;
            }
        }

        .pop-in {
            animation: popIn 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        /* Floating Heart Animation for Celebration */
        .floating-heart {
            position: absolute;
            animation: floatUp 3s ease-out forwards;
            pointer-events: none;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.5);
                opacity: 1;
            }
            100% {
                transform: translateY(-200px) scale(1.5) rotate(20deg);
                opacity: 0;
            }
        }

        /* Custom Transition for Dynamic Sizing */
        .shrink-btn, .grow-btn {
            transition: all 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
    </style>
</head>
<body class="flex items-center justify-center min-h-screen p-4 select-none">

    <!-- Background Decorative Floating Shapes -->
    <div class="bg-particle text-pink-300 text-4xl top-10 left-10" style="animation-delay: 0s;"><i class="fa-solid font-bold fa-heart"></i></div>
    <div class="bg-particle text-purple-300 text-3xl top-1/4 right-12" style="animation-delay: 1s;"><i class="fa-solid fa-sparkles"></i></div>
    <div class="bg-particle text-amber-300 text-4xl bottom-16 left-16" style="animation-delay: 2s;"><i class="fa-solid fa-paw"></i></div>
    <div class="bg-particle text-pink-300 text-5xl bottom-12 right-20" style="animation-delay: 1.5s;"><i class="fa-solid fa-heart"></i></div>
    <div class="bg-particle text-blue-300 text-3xl top-16 right-1/3" style="animation-delay: 2.5s;"><i class="fa-solid fa-star"></i></div>

    <!-- Container Card -->
    <main class="relative z-10 w-full max-w-lg bg-white/80 backdrop-blur-md rounded-3xl p-8 sm:p-12 shadow-2xl border border-white/60 text-center transition-all duration-500 min-h-[420px] flex flex-col justify-center items-center">
        
        <!-- Main Interactive Question Stage -->
        <div id="question-stage" class="w-full flex flex-col items-center justify-center space-y-8">
            
            <!-- Playful Dog Illustration Header -->
            <div id="dog-avatar-container" class="relative group cursor-pointer transition-transform duration-300 hover:scale-110" onclick="playBarkSound()">
                <div class="w-32 h-32 sm:w-40 sm:h-40 bg-pink-100 rounded-full flex items-center justify-center shadow-inner border-4 border-pink-200 relative overflow-hidden">
                    <span id="dog-emoji" class="text-7xl sm:text-8xl transition-all duration-300">🐶</span>
                </div>
                <span class="absolute -bottom-2 bg-pink-500 text-white text-xs font-bold px-3 py-1 rounded-full shadow-md">
                    Tap me! 🐾
                </span>
            </div>

            <!-- Question Title -->
            <h1 id="main-title" class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-pink-600 tracking-wide drop-shadow-sm leading-snug">
                Who is a good girl?
            </h1>

            <!-- Message / Tease Banner -->
            <p id="sub-message" class="text-purple-500 font-semibold text-lg h-6 transition-all duration-300 opacity-90">
                Choose carefully! ✨
            </p>

            <!-- Buttons Container -->
            <div class="flex flex-wrap items-center justify-center gap-6 w-full pt-4 min-h-[120px] px-2">
                
                <!-- ME! Button -->
                <button id="me-btn" 
                    onclick="handleMeClick()"
                    class="grow-btn pulse-btn bg-gradient-to-r from-pink-500 to-rose-400 hover:from-pink-600 hover:to-rose-500 text-white font-bold text-2xl sm:text-3xl px-8 py-4 rounded-full shadow-lg hover:shadow-xl transform active:scale-95 flex items-center gap-3 border-2 border-pink-200 cursor-pointer">
                    <span>Me!</span>
                    <i class="fa-solid fa-heart text-white text-xl"></i>
                </button>

                <!-- NOT ME Button -->
                <button id="not-me-btn" 
                    onclick="handleNotMeClick()"
                    class="shrink-btn bg-slate-200 hover:bg-slate-300 text-slate-600 font-bold text-xl px-6 py-3 rounded-full shadow transition-all duration-300 cursor-pointer border border-slate-300 hover:text-slate-700">
                    Not me 🙈
                </button>

            </div>

        </div>

        <!-- Celebration Result Stage (Hidden Initially) -->
        <div id="celebration-stage" class="hidden w-full flex-col items-center justify-center space-y-6">
            <div class="pop-in flex flex-col items-center space-y-4">
                <div class="relative">
                    <div class="w-36 h-36 sm:w-44 sm:h-44 bg-gradient-to-tr from-pink-200 to-purple-200 rounded-full flex items-center justify-center shadow-lg border-4 border-pink-300">
                        <span class="text-8xl sm:text-9xl animate-bounce">👑</span>
                    </div>
                    <span class="absolute -bottom-3 left-1/2 -translate-x-1/2 bg-yellow-400 text-yellow-950 font-extrabold text-sm px-4 py-1.5 rounded-full shadow-md uppercase tracking-wider border border-yellow-300">
                        100% Verified
                    </span>
                </div>

                <h2 class="text-4xl sm:text-5xl font-black text-transparent bg-clip-text bg-gradient-to-r from-pink-500 via-purple-500 to-rose-500 tracking-wide pt-2">
                    GOOD GIRL! 🐶💖
                </h2>

                <p class="text-pink-600 font-bold text-xl sm:text-2xl max-w-xs">
                    Yes you are! The absolute best girl ever! 🌸✨
                </p>

                <!-- Audio Visualizer / Decorative Badges -->
                <div class="flex gap-2 pt-2">
                    <span class="bg-pink-100 text-pink-700 font-semibold px-4 py-2 rounded-2xl text-sm shadow-sm flex items-center gap-1.5">
                        <i class="fa-solid fa-award text-pink-500"></i> Best Girl Award
                    </span>
                    <span class="bg-purple-100 text-purple-700 font-semibold px-4 py-2 rounded-2xl text-sm shadow-sm flex items-center gap-1.5">
                        <i class="fa-solid fa-bone text-purple-500"></i> Unlimited Treats
                    </span>
                </div>

                <!-- Play Again / Replay Button -->
                <button onclick="resetApp()" class="mt-6 bg-white hover:bg-pink-50 text-pink-500 border-2 border-pink-300 font-bold text-base px-6 py-2.5 rounded-full shadow-sm hover:shadow transition-all duration-200 flex items-center gap-2 cursor-pointer active:scale-95">
                    <i class="fa-solid fa-rotate-left"></i> Ask Again
                </button>
            </div>
        </div>

    </main>

    <!-- Floating Heart Animation Container -->
    <div id="heart-container" class="fixed inset-0 pointer-events-none z-50 overflow-hidden"></div>

    <script>
        // Web Audio API for synthetic sound effects without external audio dependencies
        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

        function playSynthesizedSound(type) {
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }

            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.connect(gain);
            gain.connect(audioCtx.destination);

            const now = audioCtx.currentTime;

            if (type === 'shrink') {
                // Descending pop sound
                osc.type = 'sine';
                osc.frequency.setValueAtTime(400, now);
                osc.frequency.exponentialRampToValueAtTime(150, now + 0.15);
                gain.gain.setValueAtTime(0.2, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.15);
                osc.start(now);
                osc.stop(now + 0.15);
            } else if (type === 'bark') {
                // Short cute bark-like chirp
                osc.type = 'triangle';
                osc.frequency.setValueAtTime(300, now);
                osc.frequency.linearRampToValueAtTime(600, now + 0.08);
                osc.frequency.linearRampToValueAtTime(200, now + 0.2);
                gain.gain.setValueAtTime(0.3, now);
                gain.gain.exponentialRampToValueAtTime(0.01, now + 0.2);
                osc.start(now);
                osc.stop(now + 0.2);
            } else if (type === 'celebrate') {
                // Cheerful arpeggio chord
                const notes = [523.25, 659.25, 783.99, 1046.50]; // C5, E5, G5, C6
                notes.forEach((freq, i) => {
                    const noteOsc = audioCtx.createOscillator();
                    const noteGain = audioCtx.createGain();
                    noteOsc.type = 'sine';
                    noteOsc.frequency.setValueAtTime(freq, now + i * 0.08);
                    
                    noteGain.gain.setValueAtTime(0, now + i * 0.08);
                    noteGain.gain.linearRampToValueAtTime(0.25, now + i * 0.08 + 0.02);
                    noteGain.gain.exponentialRampToValueAtTime(0.001, now + i * 0.08 + 0.4);

                    noteOsc.connect(noteGain);
                    noteGain.connect(audioCtx.destination);

                    noteOsc.start(now + i * 0.08);
                    noteOsc.stop(now + i * 0.08 + 0.4);
                });
            }
        }

        function playBarkSound() {
            playSynthesizedSound('bark');
            const dogEmoji = document.getElementById('dog-emoji');
            dogEmoji.innerText = '🐶';
            dogEmoji.classList.add('scale-125');
            setTimeout(() => dogEmoji.classList.remove('scale-125'), 200);
        }

        // State variables for button dynamics
        let shrinkClicks = 0;
        const maxShrinkClicks = 6;

        // Custom funny sub-messages for each "Not me" click
        const teaseMessages = [
            "Are you sure? 🤔",
            "Hey! Try again! 😜",
            "Nonsense! Click the pink button! 💖",
            "Don't lie to yourself! 🐶",
            "It's shrinking away... 🫣",
            "Oops, almost gone! ✨",
            "No escape now! 🎀"
        ];

        function handleNotMeClick() {
            const notMeBtn = document.getElementById('not-me-btn');
            const meBtn = document.getElementById('me-btn');
            const subMessage = document.getElementById('sub-message');
            const dogEmoji = document.getElementById('dog-emoji');

            shrinkClicks++;
            playSynthesizedSound('shrink');

            // Playful emoji reactions on dog avatar
            const dogReactions = ['🐶', '😮', '🧐', '🥺', '🤨', '😜'];
            dogEmoji.innerText = dogReactions[Math.min(shrinkClicks, dogReactions.length - 1)];

            // Calculate shrink scale and opacity reduction
            const scale = Math.max(0, 1 - (shrinkClicks * 0.16));
            const opacity = Math.max(0, 1 - (shrinkClicks * 0.15));

            // Calculate grow scale for ME button
            const meScale = 1 + (shrinkClicks * 0.12);

            // Apply transformations
            notMeBtn.style.transform = `scale(${scale})`;
            notMeBtn.style.opacity = opacity;

            meBtn.style.transform = `scale(${meScale})`;

            // Update playful message
            if (shrinkClicks <= teaseMessages.length) {
                subMessage.innerText = teaseMessages[shrinkClicks - 1];
                subMessage.classList.add('text-pink-600');
            }

            // Completely hide & disable when fully shrunken
            if (shrinkClicks >= maxShrinkClicks || scale <= 0.05) {
                notMeBtn.style.display = 'none';
                subMessage.innerText = "There is only one correct answer! 👇✨";
            }
        }

        function handleMeClick() {
            playSynthesizedSound('celebrate');

            // Hide question stage and show celebration stage
            document.getElementById('question-stage').classList.add('hidden');
            const celebrationStage = document.getElementById('celebration-stage');
            celebrationStage.classList.remove('hidden');
            celebrationStage.classList.add('flex');

            // Trigger Fireworks / Confetti
            triggerConfetti();

            // Spawn floating hearts burst
            spawnFloatingHearts();
        }

        function triggerConfetti() {
            // Pastel Confetti burst using canvas-confetti library
            const count = 200;
            const defaults = {
                origin: { y: 0.6 },
                colors: ['#f472b6', '#fb7185', '#c084fc', '#fcd34d', '#a7f3d0']
            };

            function fire(particleRatio, opts) {
                confetti(Object.assign({}, defaults, opts, {
                    particleCount: Math.floor(count * particleRatio)
                }));
            }

            fire(0.25, {
                spread: 26,
                startVelocity: 55,
            });
            fire(0.2, {
                spread: 60,
            });
            fire(0.35, {
                spread: 100,
                decay: 0.91,
                scalar: 0.8
            });
            fire(0.1, {
                spread: 120,
                startVelocity: 25,
                decay: 0.92,
                scalar: 1.2
            });
            fire(0.1, {
                spread: 120,
                startVelocity: 45,
            });
        }

        function spawnFloatingHearts() {
            const container = document.getElementById('heart-container');
            const heartEmojis = ['💖', '💕', '💗', '💓', '🌸', '🐶', '✨'];

            for (let i = 0; i < 30; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.className = 'floating-heart text-2xl sm:text-4xl';
                    heart.innerText = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
                    heart.style.left = Math.random() * 90 + 5 + 'vw';
                    heart.style.bottom = '10px';
                    heart.style.animationDuration = (Math.random() * 2 + 2) + 's';
                    container.appendChild(heart);

                    // Clean up DOM element after animation ends
                    setTimeout(() => {
                        heart.remove();
                    }, 3500);
                }, i * 100);
            }
        }

        function resetApp() {
            shrinkClicks = 0;

            const notMeBtn = document.getElementById('not-me-btn');
            const meBtn = document.getElementById('me-btn');
            const subMessage = document.getElementById('sub-message');
            const dogEmoji = document.getElementById('dog-emoji');

            // Reset button styles
            notMeBtn.style.display = 'inline-block';
            notMeBtn.style.transform = 'scale(1)';
            notMeBtn.style.opacity = '1';

            meBtn.style.transform = 'scale(1)';

            subMessage.innerText = 'Choose carefully! ✨';
            subMessage.classList.remove('text-pink-600');
            dogEmoji.innerText = '🐶';

            // Switch stages
            document.getElementById('celebration-stage').classList.add('hidden');
            document.getElementById('celebration-stage').classList.remove('flex');

            const questionStage = document.getElementById('question-stage');
            questionStage.classList.remove('hidden');
            questionStage.classList.add('flex');
        }
    </script>
</body>
</html>
