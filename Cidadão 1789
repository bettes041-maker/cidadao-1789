<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Cidadão 1789: Liberdade ou Morte</title>
    <!-- Tailwind para Estilização -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Special+Elite&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Special Elite', cursive;
            background-color: #1c1917;
            color: #e7e5e4;
            overflow: hidden;
            touch-action: manipulation;
        }
        .cinzel { font-family: 'Cinzel', serif; }
        .paper-texture {
            background-color: #f5f5dc;
            background-image: url("https://www.transparenttextures.com/patterns/aged-paper.png");
            color: #1c1917;
        }
        .stat-bar {
            height: 8px;
            border-radius: 4px;
            background: #d6d3d1;
            overflow: hidden;
            border: 1px solid #a8a29e;
        }
        .stat-progress {
            height: 100%;
            transition: width 0.5s ease-in-out;
        }
        .btn-choice {
            background: white;
            border: 2px solid #d6d3d1;
            transition: all 0.2s;
        }
        .btn-choice:active {
            transform: scale(0.98);
            background: #fefce8;
        }
        /* Esconder scrollbar */
        ::-webkit-scrollbar { width: 0px; }
    </style>
</head>
<body class="flex items-center justify-center min-h-screen">

    <div id="game-container" class="w-full max-w-md h-screen md:h-[850px] relative overflow-hidden flex flex-col shadow-2xl md:rounded-3xl border-4 border-stone-800">
        
        <!-- Menu Inicial -->
        <div id="screen-menu" class="absolute inset-0 z-50 flex flex-col items-center justify-center p-8 bg-stone-900 text-center">
            <div class="mb-6 p-6 bg-stone-800 rounded-full border-4 border-red-800 shadow-xl">
                <svg xmlns="http://www.w3.org/2000/svg" width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="#991b1b" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 19.5v-15A2.5 2.5 0 0 1 6.5 2H20v20H6.5a2.5 2.5 0 0 1-2.5-2.5Z"/><path d="M8 7h6"/><path d="M8 11h8"/></svg>
            </div>
            <h1 class="text-6xl font-bold text-red-700 cinzel mb-2" style="text-shadow: 2px 2px 0px black;">1789</h1>
            <p class="text-stone-400 uppercase tracking-widest text-sm mb-12">Liberdade ou Morte</p>
            <button onclick="showScreen('screen-character')" class="w-full bg-red-800 hover:bg-red-700 text-white py-4 rounded-lg font-bold shadow-lg transition-transform active:scale-95">JOGAR</button>
            <p class="mt-8 text-xs text-stone-600">Um jogo de estratégia histórica</p>
        </div>

        <!-- Seleção de Personagem -->
        <div id="screen-character" class="absolute inset-0 z-40 hidden flex flex-col p-6 bg-stone-900">
            <h2 class="text-2xl cinzel font-bold text-white mb-6 mt-4">Escolha a sua Classe</h2>
            <div class="space-y-4">
                <button onclick="startGame('peasant')" class="w-full bg-stone-100 p-4 rounded-lg text-left border-l-8 border-red-700 flex gap-4">
                    <div class="text-3xl">🥖</div>
                    <div>
                        <h3 class="font-bold text-stone-900">Sans-culotte</h3>
                        <p class="text-xs text-stone-600">Pobre, mas tem o apoio das massas.</p>
                    </div>
                </button>
                <button onclick="startGame('merchant')" class="w-full bg-stone-100 p-4 rounded-lg text-left border-l-8 border-blue-700 flex gap-4">
                    <div class="text-3xl">⚖️</div>
                    <div>
                        <h3 class="font-bold text-stone-900">Burguês</h3>
                        <p class="text-xs text-stone-600">Educado e rico, mas vigiado por todos.</p>
                    </div>
                </button>
                <button onclick="startGame('noble')" class="w-full bg-stone-100 p-4 rounded-lg text-left border-l-8 border-stone-800 flex gap-4">
                    <div class="text-3xl">🏰</div>
                    <div>
                        <h3 class="font-bold text-stone-900">Aristocrata</h3>
                        <p class="text-xs text-stone-600">Muito rico, mas o povo quer a sua cabeça.</p>
                    </div>
                </button>
            </div>
        </div>

        <!-- Jogo Principal -->
        <div id="screen-playing" class="absolute inset-0 hidden flex flex-col paper-texture">
            <!-- Header Stats -->
            <div class="bg-stone-800 p-4 flex justify-between gap-4 text-white z-10">
                <div class="flex-1">
                    <div class="flex justify-between text-[10px] mb-1"><span>POVO</span><span id="stat-pop-val">50</span></div>
                    <div class="stat-bar"><div id="stat-pop" class="stat-progress bg-red-500" style="width: 50%;"></div></div>
                </div>
                <div class="flex-1">
                    <div class="flex justify-between text-[10px] mb-1"><span>OURO</span><span id="stat-gold-val">50</span></div>
                    <div class="stat-bar"><div id="stat-gold" class="stat-progress bg-yellow-500" style="width: 50%;"></div></div>
                </div>
                <div class="flex-1">
                    <div class="flex justify-between text-[10px] mb-1"><span>VIDA</span><span id="stat-life-val">50</span></div>
                    <div class="stat-bar"><div id="stat-life" class="stat-progress bg-blue-500" style="width: 50%;"></div></div>
                </div>
            </div>

            <!-- Evento -->
            <div id="event-area" class="flex-1 p-6 flex flex-col overflow-y-auto">
                <div class="flex justify-between items-center mb-2 border-b border-stone-300 pb-2">
                    <span id="event-year" class="text-xs font-bold text-stone-500 tracking-tighter">1789</span>
                    <span id="event-counter" class="text-[10px] bg-stone-800 text-white px-2 py-0.5 rounded">1/10</span>
                </div>
                <h2 id="event-title" class="text-2xl font-bold mb-4 cinzel leading-tight text-stone-900">A Bastilha</h2>
                <p id="event-text" class="text-lg text-stone-800 leading-relaxed mb-8"></p>
                <div id="choices-container" class="space-y-3 mt-auto">
                    <!-- Botões injetados via JS -->
                </div>
            </div>
        </div>

        <!-- Tela de Fato Histórico -->
        <div id="screen-fact" class="absolute inset-0 hidden z-30 paper-texture p-8 flex flex-col justify-center items-center text-center">
            <h3 class="text-red-800 font-bold mb-4 cinzel text-xl uppercase tracking-widest">Resultado</h3>
            <p id="fact-outcome" class="italic text-lg mb-8 text-stone-800"></p>
            <div class="bg-stone-200 p-4 rounded-lg border-l-4 border-stone-800 text-left mb-8">
                <p class="text-xs font-bold mb-1 opacity-60 uppercase">Sabia que?</p>
                <p id="fact-text" class="text-sm"></p>
            </div>
            <button onclick="nextTurn()" class="w-full bg-stone-800 text-white py-4 rounded font-bold uppercase">Continuar</button>
        </div>

        <!-- Game Over -->
        <div id="screen-gameover" class="absolute inset-0 hidden z-[100] bg-stone-900 text-center flex flex-col items-center justify-center p-8">
            <div class="text-8xl mb-4">💀</div>
            <h2 id="death-title" class="text-4xl font-bold text-red-700 cinzel mb-2">GUILHOTINADO</h2>
            <p id="death-text" class="text-stone-400 mb-12"></p>
            <button onclick="location.reload()" class="w-full bg-white text-black py-4 rounded font-bold">RECOMEÇAR</button>
        </div>

        <!-- Vitória -->
        <div id="screen-victory" class="absolute inset-0 hidden z-[100] bg-stone-100 text-center flex flex-col items-center justify-center p-8">
            <div class="text-8xl mb-4">👑</div>
            <h2 class="text-4xl font-bold text-blue-900 cinzel mb-2">SOBREVIVENTE</h2>
            <p class="text-stone-600 mb-8">Napoleão tomou o poder e você ainda mantém a sua cabeça sobre os ombros.</p>
            <div id="final-stats" class="text-sm text-stone-500 mb-8"></div>
            <button onclick="location.reload()" class="w-full bg-blue-900 text-white py-4 rounded font-bold">JOGAR NOVAMENTE</button>
        </div>

    </div>

    <script>
        // Dados do Jogo
        const events = [
            {
                year: 1789,
                title: "A Revolta do Pão",
                text: "O preço do pão subiu de novo. A sua família tem fome. Uma multidão marcha em direção à prefeitura.",
                fact: "Em 1789, um trabalhador francês gastava cerca de 80% do seu salário apenas em pão.",
                choices: [
                    { text: "Liderar o saque aos armazéns!", effects: { pop: 20, gold: 5, life: -15 }, outcome: "O povo agora vê-te como um líder, mas os guardas reais feriram-te." },
                    { text: "Pedir calma e ordem.", effects: { pop: -20, gold: 0, life: 10 }, outcome: "Foste chamado de cobarde, mas evitaste o confronto." }
                ]
            },
            {
                year: 1789,
                title: "A Queda da Bastilha",
                text: "O povo cercou a fortaleza real em busca de pólvora. O governador hesita.",
                fact: "A queda da Bastilha marcou o início simbólico da Revolução.",
                choices: [
                    { text: "Invadir a fortaleza!", effects: { pop: 25, gold: 0, life: -20 }, outcome: "A fortaleza caiu! Tu foste um dos primeiros a entrar." },
                    { text: "Vender munição para os rebeldes.", effects: { pop: 5, gold: 20, life: -5 }, outcome: "Fizeste um bom lucro, mas o risco foi alto." }
                ]
            },
            {
                year: 1791,
                title: "O Rei Tenta Fugir",
                text: "Luís XVI foi capturado em Varennes enquanto fugia. O povo sente-se traído.",
                fact: "A tentativa de fuga destruiu a aura de 'pai do povo' que o Rei ainda tinha.",
                choices: [
                    { text: "Exigir a República!", effects: { pop: 15, gold: 0, life: -10 }, outcome: "Os Jacobinos abraçam-te como um verdadeiro patriota." },
                    { text: "Defender a monarquia constitucional.", effects: { pop: -25, gold: 10, life: 5 }, outcome: "Os ricos agradecem, mas o povo quer o teu fim." }
                ]
            },
            {
                year: 1793,
                title: "O Reinado do Terror",
                text: "Robespierre ordena a execução de qualquer suspeito. Um vizinho denunciou-te.",
                fact: "Durante o Terror, cerca de 17.000 pessoas foram oficialmente guilhotinadas.",
                choices: [
                    { text: "Subornar o juiz.", effects: { pop: -5, gold: -30, life: 25 }, outcome: "O ouro salvou o teu pescoço, mas ficas na miséria." },
                    { text: "Denunciar o vizinho primeiro.", effects: { pop: 5, gold: 5, life: 15 }, outcome: "Ele foi levado no teu lugar. A revolução é cruel." }
                ]
            },
            {
                year: 1799,
                title: "O Golpe de Napoleão",
                text: "O General Bonaparte retornou e promete ordem. O Diretório está em colapso.",
                fact: "O golpe de 18 de Brumário pôs fim à fase democrática da Revolução.",
                choices: [
                    { text: "Apoiar o novo Imperador.", effects: { pop: 10, gold: 10, life: 20 }, outcome: "A ordem voltou à França." },
                    { text: "Lutar pela República.", effects: { pop: 15, gold: -10, life: -40 }, outcome: "As baionetas de Napoleão não perdoam idealistas." }
                ]
            }
        ];

        let state = {
            pop: 50, gold: 50, life: 50,
            turn: 0,
            char: ''
        };

        function showScreen(id) {
            document.querySelectorAll('#game-container > div').forEach(div => div.classList.add('hidden'));
            document.getElementById(id).classList.remove('hidden');
        }

        function startGame(type) {
            state.char = type;
            if(type === 'peasant') { state.pop = 80; state.gold = 20; state.life = 40; }
            if(type === 'merchant') { state.pop = 40; state.gold = 70; state.life = 50; }
            if(type === 'noble') { state.pop = 10; state.gold = 90; state.life = 70; }
            updateStats();
            renderEvent();
            showScreen('screen-playing');
        }

        function updateStats() {
            document.getElementById('stat-pop').style.width = state.pop + '%';
            document.getElementById('stat-gold').style.width = state.gold + '%';
            document.getElementById('stat-life').style.width = state.life + '%';
            document.getElementById('stat-pop-val').innerText = state.pop;
            document.getElementById('stat-gold-val').innerText = state.gold;
            document.getElementById('stat-life-val').innerText = state.life;
        }

        function renderEvent() {
            const ev = events[state.turn];
            document.getElementById('event-year').innerText = ev.year;
            document.getElementById('event-counter').innerText = `${state.turn + 1}/${events.length}`;
            document.getElementById('event-title').innerText = ev.title;
            document.getElementById('event-text').innerText = ev.text;
            
            const container = document.getElementById('choices-container');
            container.innerHTML = '';
            ev.choices.forEach(c => {
                const btn = document.createElement('button');
                btn.className = "btn-choice w-full p-4 rounded text-left font-bold text-sm shadow-sm";
                btn.innerText = c.text;
                btn.onclick = () => makeChoice(c);
                container.appendChild(btn);
            });
        }

        function makeChoice(c) {
            state.pop += c.effects.pop;
            state.gold += c.effects.gold;
            state.life += c.effects.life;
            
            updateStats();

            if (state.life <= 0) return gameOver("Foste denunciado e a guilhotina não perdoou.");
            if (state.pop <= 0) return gameOver("O povo arrastou-te pelas ruas até à morte.");
            if (state.gold <= 0) return gameOver("Morreste de fome e frio num beco de Paris.");

            document.getElementById('fact-outcome').innerText = c.outcome;
            document.getElementById('fact-text').innerText = events[state.turn].fact;
            showScreen('screen-fact');
        }

        function nextTurn() {
            state.turn++;
            if(state.turn >= events.length) {
                showScreen('screen-victory');
                document.getElementById('final-stats').innerText = `Ouro: ${state.gold} | Apoio: ${state.pop}`;
            } else {
                renderEvent();
                showScreen('screen-playing');
            }
        }

        function gameOver(msg) {
            document.getElementById('death-text').innerText = msg;
            showScreen('screen-gameover');
        }
    </script>
</body>
</html>
