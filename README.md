<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Railway Engineering Pro Quiz - Mobile Optimized</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap');
        
        body { 
            font-family: 'Plus Jakarta Sans', sans-serif;
            background: radial-gradient(circle at top, #1e293b 0%, #0f172a 100%);
            color: #e2e8f0;
            overflow-x: hidden;
        }

        .glass-card {
            background: rgba(30, 41, 59, 0.7);
            backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .tab-content { display: none; transition: opacity 0.3s ease; opacity: 0; }
        .tab-content.active { display: block; opacity: 1; }

        .option-btn {
            background-color: rgba(15, 23, 42, 0.6);
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .option-btn:hover:not(:disabled) {
            transform: translateY(-2px);
            box-shadow: 0 4px 20px rgba(59, 130, 246, 0.2);
            background-color: rgba(30, 41, 59, 0.9);
            border-color: #3b82f6;
        }

        .correct { 
            background-color: rgba(22, 163, 74, 0.2) !important; 
            border-color: #22c55e !important; 
            color: #4ade80 !important;
            box-shadow: 0 0 15px rgba(34, 197, 94, 0.3);
        }

        .wrong { 
            background-color: rgba(220, 38, 38, 0.2) !important; 
            border-color: #ef4444 !important; 
            color: #f87171 !important;
            box-shadow: 0 0 15px rgba(239, 68, 68, 0.3);
        }

        input:disabled { opacity: 0.8; cursor: not-allowed; }
        
        .tab-btn.active-tab {
            background: #2563eb;
            color: white;
            box-shadow: 0 4px 15px rgba(37, 99, 235, 0.4);
        }

        .completion-input {
            max-width: 100%;
            min-width: 80px;
            display: inline-block;
        }

        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-track { background: #0f172a; }
        ::-webkit-scrollbar-thumb { background: #334155; border-radius: 10px; }
    </style>
</head>
<body class="min-h-screen pb-10">

    <!-- Navbar -->
    <nav class="sticky top-0 z-50 bg-slate-900/90 backdrop-blur-md border-b border-slate-800">
        <div class="max-w-5xl mx-auto px-4 h-16 flex items-center justify-between">
            <div class="flex items-center gap-2">
                <div class="w-7 h-7 bg-blue-600 rounded-lg flex items-center justify-center">
                    <svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                </div>
                <span class="font-bold text-lg tracking-tight text-white">Railway<span class="text-blue-500">Exam</span></span>
            </div>
            <div class="hidden sm:block text-[10px] font-bold text-blue-400 bg-blue-900/30 px-2 py-1 rounded-full border border-blue-500/20 uppercase tracking-widest">
                Mobile Responsive
            </div>
        </div>
    </nav>

    <div class="max-w-4xl mx-auto px-4 mt-6">
        <!-- Header -->
        <div class="mb-8 text-center px-2">
            <h1 class="text-2xl md:text-4xl font-extrabold text-white mb-2 tracking-tight">Technical Mastery Quiz</h1>
            <p class="text-slate-400 text-sm md:text-lg">Railway engineering and infrastructure standards.</p>
        </div>

        <!-- Responsive Tabs -->
        <div class="flex p-1 bg-slate-800/50 rounded-xl mb-8 border border-slate-700/50 max-w-md mx-auto overflow-hidden">
            <button onclick="showTab('mcq', this)" class="tab-btn active-tab flex-1 py-2.5 px-2 rounded-lg font-bold transition-all duration-300 text-xs sm:text-sm">MCQs</button>
            <button onclick="showTab('complete', this)" class="tab-btn flex-1 py-2.5 px-2 rounded-lg font-bold text-slate-400 hover:text-white transition-all duration-300 text-xs sm:text-sm">Complete</button>
            <button onclick="showTab('true-false', this)" class="tab-btn flex-1 py-2.5 px-2 rounded-lg font-bold text-slate-400 hover:text-white transition-all duration-300 text-xs sm:text-sm">True/False</button>
        </div>

        <!-- MCQ Section -->
        <div id="mcq" class="tab-content active">
            <div id="mcq-container" class="grid gap-6">
                <!-- MCQs Injected Here -->
            </div>
        </div>

        <!-- Completion Section -->
        <div id="complete" class="tab-content">
            <div class="glass-card p-5 md:p-8 rounded-2xl md:rounded-3xl">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-8 pb-4 border-b border-slate-700">
                    <div>
                        <h2 class="text-xl font-bold text-white">Definitions</h2>
                        <p class="text-xs text-slate-400">Fill in the technical terms.</p>
                    </div>
                    <button onclick="location.reload()" class="w-full sm:w-auto px-4 py-2 bg-slate-800 hover:bg-slate-700 text-slate-300 rounded-lg text-xs font-bold transition-colors border border-slate-600">Reset</button>
                </div>
                <div id="complete-list" class="space-y-6">
                    <!-- Completion items Injected Here -->
                </div>
                <button id="check-comp-btn" onclick="checkCompletion()" class="mt-10 w-full bg-blue-600 text-white py-4 rounded-xl font-extrabold hover:bg-blue-500 shadow-lg transition-all active:scale-[0.98]">
                    Check & Reveal
                </button>
            </div>
        </div>

        <!-- True/False Section -->
        <div id="true-false" class="tab-content">
            <div id="tf-container" class="grid gap-3">
                <!-- T/F items Injected Here -->
            </div>
        </div>

        <!-- Footer / Credits -->
        <footer class="mt-16 py-8 border-t border-slate-800 text-center">
            <p class="text-slate-500 text-xs md:text-sm font-semibold tracking-wide uppercase">
                Designed by <span class="text-blue-500">Belal Mohamed</span>
            </p>
        </footer>
    </div>

    <script>
        const mcqs = [
            { q: "What is the primary function of railway transport systems?", a: "C", options: ["To transport goods exclusively.", "To provide recreational services.", "To transport both passengers and freight.", "To facilitate long-distance travel only."] },
            { q: "The standard gauge is (mm):", a: "B", options: ["600", "1435", "1520", "1600"] },
            { q: "The UIC stands for ________ and aims to provide a system-oriented reference for railway development.", a: "B", options: ["International United Council.", "International Union of Railways.", "Infrastructure Universal Company."] },
            { q: "Which of the following is NOT a benefit of using long welded rails?", a: "D", options: ["Improved track geometry.", "Smoother ride.", "Reduced maintenance costs.", "Increased noise pollution."] },
            { q: "What is the primary purpose of track modernization?", a: "D", options: ["To increase the lifespan of the track.", "To improve the safety and efficiency of rail operations.", "To reduce maintenance costs.", "All of the above."] },
            { q: "What is the role of track monitoring systems in railway maintenance?", a: "D", options: ["To identify potential maintenance issues.", "To assess the overall condition of the track.", "To optimize maintenance schedules.", "All of the above."] },
            { q: "Which of the following is a key component of ballasted track?", a: "C", options: ["Asphalt.", "Concrete slab.", "Ballast.", "Bituminous mixture."] },
            { q: "Which type of track is better suited for high-speed rail?", a: "B", options: ["Ballasted track.", "Non-ballasted track.", "Both equally.", "Neither."] },
            { q: "Which track type requires more frequent maintenance?", a: "B", options: ["Non-ballasted track.", "Ballasted track.", "Both equally.", "Neither."] },
            { q: "Which of the following is an advantage of non-ballasted track?", a: "C", options: ["Lower initial cost.", "Easier to lay.", "Longer lifespan.", "Higher noise reduction measures."] },
            { q: "What is the approximate lifespan of ballasted track?", a: "C", options: ["50-60 years.", "30-40 years.", "15-20 years.", "100 years."] },
            { q: "What is the main material used in the bed of a non-ballasted track?", a: "C", options: ["Gravel.", "Wood.", "Concrete.", "Steel."] },
            { q: "What is a disadvantage of ballasted track?", a: ["C", "D"], options: ["High initial cost.", "Difficult to lay.", "Frequent maintenance.", "Low speed capability."] },
            { q: "Ballasted track is also known as:", a: "C", options: ["Slab track.", "Ballastless track.", "Ordinary track.", "Concrete track."] },
            { q: "Which track type is more environmentally friendly in terms of dust pollution?", a: "B", options: ["Ballasted track.", "Non-ballasted track.", "Both are equally polluting.", "Neither is polluting."] }
        ];

        const completion = [
            "Railway transport comprises both passenger and <b>freight</b> transport.",
            "Railway passenger systems cover a range from conventional and high-speed intercity systems to <b>suburban</b>, <b>regional</b>, operating on steep gradients, and urban systems.",
            "Freight railway systems transport conventional loads, <b>heavy</b> loads, and dangerous goods.",
            "The UIC stands for <b>International Union of Railways</b> and aims to provide a system-oriented reference for railway development.",
            "The bed of a ballasted track is made of <b>ballast</b> (gravel/crushed stone).",
            "Non-ballasted track is also called <b>ballastless</b> track.",
            "Ballasted track is generally <b>easier</b> to lay than non-ballasted track.",
            "Non-ballasted track is primarily used for <b>high-speed</b> railways.",
            "The lifespan of non-ballasted track is approximately <b>50-60</b> years.",
            "Ballasted track requires more <b>frequent</b> and costly maintenance.",
            "A key advantage of non-ballasted track is its reduced <b>dust</b> pollution.",
            "The traditional track whose bed is made up of ballast is also called <b>ordinary</b> track.",
            "Non-ballasted track uses a <b>concrete slab</b> instead of individual ties.",
            "Ballasted tracks have a poor life expectation of about <b>15-20</b> years."
        ];

        const trueFalse = [
            { q: "Ballasted track is a more recent innovation compared to nonballasted track.", a: false },
            { q: "Non-ballasted track requires more initial investment than ballasted track.", a: true },
            { q: "Ballasted track provides better ride quality than non-ballasted track.", a: false },
            { q: "Non-ballasted track is also known as ballastless track.", a: true },
            { q: "Ballasted track is ideal for use in earthquake-prone areas.", a: false },
            { q: "The lifespan of non-ballasted track is generally shorter than that of ballasted track.", a: false },
            { q: "Ballast is a key component of non-ballasted track construction.", a: false },
            { q: "High-speed railways typically utilize ballasted track.", a: false },
            { q: "Ballasted track is easier to repair than non-ballasted track.", a: true },
            { q: "Non-ballasted tracks reduce dust and noise pollution compared to ballasted tracks.", a: true }
        ];

        function showTab(id, btn) {
            document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            document.querySelectorAll('.tab-btn').forEach(b => {
                b.classList.remove('active-tab');
                b.classList.add('text-slate-400');
            });
            btn.classList.add('active-tab');
            btn.classList.remove('text-slate-400');
        }

        function renderMCQs() {
            const container = document.getElementById('mcq-container');
            container.innerHTML = '';
            mcqs.forEach((item, idx) => {
                const qDiv = document.createElement('div');
                qDiv.className = "glass-card p-5 md:p-8 rounded-2xl";
                
                const answerAttr = Array.isArray(item.a) ? JSON.stringify(item.a).replace(/"/g, '&quot;') : `'${item.a}'`;
                
                qDiv.innerHTML = `
                    <div class="flex gap-3 mb-5">
                        <span class="flex-shrink-0 w-6 h-6 md:w-8 md:h-8 rounded-full bg-blue-900/50 text-blue-400 flex items-center justify-center font-bold text-xs md:text-sm border border-blue-500/30">${idx + 1}</span>
                        <p class="font-bold text-base md:text-lg text-slate-100 leading-tight">${item.q}</p>
                    </div>
                    <div class="grid gap-2 sm:ml-9">
                        ${item.options.map((opt, oIdx) => {
                            const letter = String.fromCharCode(65 + oIdx);
                            return `<button onclick="checkMCQ(this, '${letter}', ${answerAttr})" class="option-btn text-left p-3 md:p-4 rounded-xl flex items-center gap-3 group">
                                <span class="w-6 h-6 md:w-8 md:h-8 rounded-lg bg-slate-800 flex items-center justify-center font-bold text-slate-400 text-xs border border-slate-700">${letter}</span>
                                <span class="font-medium text-xs md:text-sm text-slate-300 group-hover:text-white">${opt}</span>
                            </button>`;
                        }).join('')}
                    </div>
                `;
                container.appendChild(qDiv);
            });
        }

        window.checkMCQ = function(btn, choice, correct) {
            const parent = btn.parentElement;
            const isMultiAnswer = Array.isArray(correct);
            const isCorrect = isMultiAnswer ? correct.includes(choice) : choice === correct;
            
            if (isCorrect) {
                btn.classList.add('correct');
                btn.disabled = true;
                
                if (isMultiAnswer) {
                    const selectedCorrectCount = parent.querySelectorAll('button.correct').length;
                    if (selectedCorrectCount === correct.length) {
                        parent.querySelectorAll('button').forEach(b => b.disabled = true);
                    }
                } else {
                    parent.querySelectorAll('button').forEach(b => b.disabled = true);
                }
            } else {
                btn.classList.add('wrong');
                parent.querySelectorAll('button').forEach(b => {
                    b.disabled = true;
                    const letter = b.querySelector('span:first-child').innerText;
                    const bIsCorrect = isMultiAnswer ? correct.includes(letter) : letter === correct;
                    if (bIsCorrect) b.classList.add('correct');
                });
            }
        };

        function renderCompletion() {
            const list = document.getElementById('complete-list');
            list.innerHTML = '';
            completion.forEach((text, idx) => {
                const div = document.createElement('div');
                div.className = "text-slate-300 text-sm md:text-lg leading-relaxed flex items-start gap-3 bg-slate-900/40 p-4 rounded-xl border border-slate-800";
                const processed = text.replace(/<b>(.*?)<\/b>/g, (match, p1) => {
                    const width = Math.max(p1.length * 10, 110);
                    return `<input type="text" data-answer="${p1}" style="width: ${width}px" placeholder="..." class="completion-input mx-1 px-2 py-0.5 border-b-2 border-slate-700 focus:outline-none focus:border-blue-500 bg-slate-950/50 rounded text-center font-bold text-blue-400">`;
                });
                div.innerHTML = `<span class="font-black text-slate-700 italic text-xl">${(idx + 1).toString().padStart(2, '0')}</span> <div class="mt-1">${processed}</div>`;
                list.appendChild(div);
            });
        }

        window.checkCompletion = function() {
            document.querySelectorAll('#complete-list input').forEach(input => {
                const userVal = input.value.trim().toLowerCase();
                const correctAns = input.dataset.answer.trim().toLowerCase();
                
                // Case-insensitive comparison
                if (userVal === correctAns) {
                    input.classList.add('correct');
                    input.classList.remove('border-slate-700');
                    input.classList.add('border-green-500');
                } else {
                    input.classList.add('wrong');
                    input.classList.remove('border-slate-700');
                    input.classList.add('border-red-500');
                    input.value = input.dataset.answer; // Reveal in original case
                }
                input.disabled = true;
            });
            const btn = document.getElementById('check-comp-btn');
            btn.disabled = true; btn.classList.replace('bg-blue-600', 'bg-slate-700'); btn.innerText = "Completed";
        }

        function renderTF() {
            const container = document.getElementById('tf-container');
            container.innerHTML = '';
            trueFalse.forEach((item, idx) => {
                const div = document.createElement('div');
                div.className = "glass-card p-4 md:p-6 rounded-2xl flex flex-col sm:flex-row sm:items-center justify-between gap-4";
                div.innerHTML = `
                    <div class="flex gap-3 items-center">
                        <span class="w-8 h-8 rounded-lg bg-slate-950 text-blue-400 border border-slate-700 flex items-center justify-center font-bold text-xs shrink-0">${idx + 1}</span>
                        <p class="font-semibold text-slate-200 text-sm md:text-base">${item.q}</p>
                    </div>
                    <div class="flex gap-2 shrink-0">
                        <button onclick="checkTF(this, true, ${item.a})" class="option-btn flex-1 sm:px-6 py-2 rounded-xl font-bold text-xs text-slate-300">True</button>
                        <button onclick="checkTF(this, false, ${item.a})" class="option-btn flex-1 sm:px-6 py-2 rounded-xl font-bold text-xs text-slate-300">False</button>
                    </div>
                `;
                container.appendChild(div);
            });
        }

        window.checkTF = function(btn, choice, correct) {
            const buttons = btn.parentElement.querySelectorAll('button');
            buttons.forEach(b => b.disabled = true);
            if (choice === correct) btn.classList.add('correct');
            else {
                btn.classList.add('wrong');
                buttons.forEach(b => { if ((b.innerText === "True") === correct) b.classList.add('correct'); });
            }
        };

        window.onload = () => { renderMCQs(); renderCompletion(); renderTF(); };
    </script>
</body>
</html>
