# LaunchPad
# NourishSense – Smart AI-based food and habit assistant that helps users make healthier eating choices using behavioral insights and interactive UI.
!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NourishSense – Smart Food & Habit Assistant</title>
    <link <href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-gradient: linear-gradient(135deg, #0f172a, #1e1b4b, #312e81, #4c1d95);
            --glass-bg: rgba(255, 255, 255, 0.08);
            --glass-border: rgba(255, 255, 255, 0.15);
            --text-main: #f8fafc;
            --text-muted: #cbd5e1;
            
            --success: #4ade80;
            --warning: #fbbf24;
            --danger: #f87171;
            --primary: #6366f1;
        }

        body {
            margin: 0;
            font-family: 'Inter', sans-serif;
            background: var(--bg-gradient);
            background-size: 400% 400%;
            animation: bgAnimation 15s ease infinite;
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            padding: 40px 20px;
            box-sizing: border-box;
        }

        @keyframes bgAnimation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            max-width: 1000px;
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .glass-panel {
            background: var(--glass-bg);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--glass-border);
            border-radius: 24px;
            padding: 30px;
            box-shadow: 0 10px 40px 0 rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .glass-panel:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 45px 0 rgba(0, 0, 0, 0.4);
        }

        .header {
            text-align: center;
            padding: 30px 20px;
        }

        h1, h2, h3 { margin-top: 0; font-weight: 800; letter-spacing: -0.5px; }
        h1 { 
            font-size: 2.8rem; 
            background: -webkit-linear-gradient(45deg, #fff, #a5b4fc, #c4b5fd); 
            -webkit-background-clip: text; 
            -webkit-text-fill-color: transparent; 
            margin-bottom: 10px; 
        }
        h2 { 
            font-size: 1.4rem; 
            border-bottom: 1px solid var(--glass-border); 
            padding-bottom: 15px; 
            margin-bottom: 20px; 
            display: flex;
            align-items: center;
            gap: 10px;
        }

        p { color: var(--text-muted); line-height: 1.6; }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 25px;
        }

        @media (max-width: 768px) {
            .grid { grid-template-columns: 1fr; }
            h1 { font-size: 2rem; }
        }

        /* Form Elements */
        input, select, button {
            width: 100%;
            padding: 14px 16px;
            margin-top: 10px;
            border-radius: 12px;
            border: 1px solid rgba(255,255,255,0.1);
            background: rgba(255, 255, 255, 0.1);
            color: #fff;
            font-size: 16px;
            outline: none;
            box-sizing: border-box;
            transition: all 0.3s ease;
            font-family: inherit;
        }
        
        select option { background: #1e1b4b; color: #fff; }

        input::placeholder { color: rgba(255,255,255,0.4); }
        input:focus, select:focus {
            background: rgba(255, 255, 255, 0.15);
            border-color: var(--primary);
            box-shadow: 0 0 15px rgba(99, 102, 241, 0.3);
        }

        button {
            background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
            cursor: pointer;
            font-weight: 600;
            border: none;
            margin-top: 15px;
            box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(99, 102, 241, 0.6);
        }

        button:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none;
        }

        /* Progress Bars */
        .progress-container {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 12px;
            height: 24px;
            width: 100%;
            margin-top: 15px;
            overflow: hidden;
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.3);
        }
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
            width: 0%;
            transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            border-radius: 12px;
            position: relative;
            overflow: hidden;
        }
        /* Shine effect on progress bar */
        .progress-bar::after {
            content: "";
            position: absolute;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transform: translateX(-100%);
            animation: shimmer 2s infinite;
        }
        @keyframes shimmer { 100% { transform: translateX(100%); } }

        /* Macros */
        .macros { display: flex; gap: 15px; margin-top: 20px; }
        .macro { 
            flex: 1; 
            text-align: center; 
            font-size: 13px; 
            background: rgba(0,0,0,0.2); 
            padding: 10px; 
            border-radius: 10px; 
        }
        .macro-bar { height: 8px; border-radius: 4px; margin-top: 8px; width: 0%; transition: width 1s ease-out; }
        .carbs .macro-bar { background: var(--warning); }
        .protein .macro-bar { background: var(--success); }
        .fat .macro-bar { background: var(--danger); }

        .hidden { display: none !important; }

        /* Loader */
        .loader {
            border: 4px solid rgba(255,255,255,0.1);
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            width: 35px;
            height: 35px;
            animation: spin 1s cubic-bezier(0.5, 0, 0.5, 1) infinite;
            margin: 20px auto;
        }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        /* Badges */
        .badge {
            display: inline-block;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 13px;
            font-weight: 800;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .badge.healthy { background: rgba(74, 222, 128, 0.2); color: var(--success); border: 1px solid var(--success); }
        .badge.unhealthy { background: rgba(248, 113, 113, 0.2); color: var(--danger); border: 1px solid var(--danger); }
        .badge.moderate { background: rgba(251, 191, 36, 0.2); color: var(--warning); border: 1px solid var(--warning); }

        /* Custom Box styling */
        .info-box {
            background: rgba(0,0,0,0.2);
            padding: 15px;
            border-radius: 12px;
            margin-top: 10px;
            transition: all 0.3s ease;
        }
    </style>
</head>
<body>
    <div class="container">
       <div class="header glass-panel">
            <h1>NourishSense</h1>
            <p id="greeting-text" style="font-size: 1.1rem; margin-top: 5px; color: #e2e8f0;"></p>
       </div>

       <!-- Profile Setup -->
       <div id="profile-section" class="glass-panel" style="max-width: 500px; margin: 0 auto; width: 100%;">
            <h2>👋 Let's Personalize Your Journey</h2>
            <p style="margin-top: 0;">Tell us a bit about yourself to get tailored suggestions.</p>
            
            <input type="number" id="user-age" placeholder="Enter your age" min="10" max="120">
            <select id="user-goal">
                <option value="" disabled selected>What is your primary goal?</option>
                <option value="Weight Loss">Weight Loss & Fat Burn</option>
                <option value="Muscle Building">Fitness & Muscle Building</option>
                <option value="General Health">General Health & Wellness</option>
            </select>
            <button id="save-profile-btn" style="margin-top: 25px; padding: 16px; font-size: 1.1rem;">Start My Journey ✨</button>
       </div>

       <!-- Main Dashboard -->
       <div id="dashboard" class="grid hidden">
            <!-- Smart Food Logger -->
            <div class="glass-panel">
                <h2>🥑 Smart Food Logger</h2>
                <p style="font-size: 0.9rem; margin-top: -10px;">Our AI will analyze your meal's health value.</p>
                
                <input type="text" id="food-input" placeholder="What did you eat? (e.g., cheeseburger, salad)">
                <button id="log-food-btn">Analyze Food 🔍</button>
                <div id="food-loader" class="loader hidden"></div>
                
                <div id="food-result" class="hidden" style="margin-top: 25px; animation: fadeIn 0.5s ease;">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
                        <h3 id="food-name" style="margin: 0; text-transform: capitalize; font-size: 1.6rem;"></h3>
                        <span id="food-badge" class="badge"></span>
                    </div>
                    
                    <div style="background: rgba(255,255,255,0.05); padding: 15px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center;">
                        <span style="font-weight: 600;">Overall Health Score</span>
                        <span style="font-size: 1.5rem; font-weight: 800;"><span id="food-score"></span><span style="font-size: 1rem; color: var(--text-muted);">/100</span></span>
                    </div>
                    
                    <div class="macros">
                        <div class="macro carbs">
                            <strong style="color: var(--warning)">Carbs</strong> <br> <span id="carbs-val"></span>%
                            <div class="macro-bar" id="carbs-bar"></div>
                        </div>
                        <div class="macro protein">
                            <strong style="color: var(--success)">Protein</strong> <br> <span id="protein-val"></span>%
                            <div class="macro-bar" id="protein-bar"></div>
                        </div>
                        <div class="macro fat">
                            <strong style="color: var(--danger)">Fat</strong> <br> <span id="fat-val"></span>%
                            <div class="macro-bar" id="fat-bar"></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Context & Suggestions -->
            <div class="glass-panel" style="display: flex; flex-direction: column; gap: 20px;">
                <div>
                    <h2>🧠 Contextual Intelligence</h2>
                    <div class="info-box" style="border-left: 4px solid var(--primary);">
                        <p id="context-suggestion" style="margin: 0; font-style: italic; font-weight: 600;"></p>
                    </div>
                </div>
                
                <div style="flex-grow: 1;">
                    <h2>💡 Smart Suggestions</h2>
                    <div id="smart-suggestions" class="info-box" style="height: 100%; display: flex; align-items: center; justify-content: center; text-align: center; color: var(--text-muted);">
                        Log a food item to receive personalized healthier alternatives!
                    </div>
                </div>
            </div>

            <!-- Habit Tracker -->
            <div class="glass-panel">
                <h2>💧 Habit Tracker</h2>
                <p style="text-align: center; margin-bottom: 5px;">Daily Water Intake</p>
                
                <div style="font-size: 3rem; font-weight: 800; text-align: center; color: #60a5fa; text-shadow: 0 0 20px rgba(96, 165, 250, 0.4);">
                    <span id="water-count">0</span><span style="font-size: 1.2rem; color: var(--text-muted);"> / 8 Glasses</span>
                </div>
                
                <div class="progress-container">
                    <div class="progress-bar" id="water-progress"></div>
                </div>
                
                <button id="add-water-btn" style="background: linear-gradient(135deg, #2563eb 0%, #0ea5e9 100%); font-size: 1.1rem; padding: 15px;">+ Drink a Glass</button>
                
                <div style="background: rgba(255,255,255,0.05); border-radius: 10px; padding: 12px; margin-top: 20px; text-align: center; border: 1px solid rgba(255,255,255,0.1);">
                    🔥 <span id="water-streak" style="font-weight: 600;">3-day hydration streak! Keep it up.</span>
                </div>
            </div>

            <!-- Personalized Insights -->
            <div class="glass-panel" style="display: flex; flex-direction: column;">
                <h2>📊 Personalized Insights</h2>
                
                <div class="info-box" style="border-left: 4px solid var(--warning); flex-grow: 1; display: flex; align-items: center;">
                    <p id="insight-text" style="margin: 0; font-size: 1.1rem; line-height: 1.6;">
                        Welcome! Start logging your meals to uncover behavioral patterns tailored for your <b id="insight-goal" style="color: #fff;">health</b> goals.
                    </p>
                </div>
                
                <button id="refresh-insight-btn" style="background: rgba(255,255,255,0.1); box-shadow: none; border: 1px solid rgba(255,255,255,0.2);">↻ Generate New Insight</button>
            </div>
       </div>
    </div>

    <script>
        // DOM Elements
        const profileSection = document.getElementById('profile-section');
        const dashboard = document.getElementById('dashboard');
        const saveProfileBtn = document.getElementById('save-profile-btn');
        const greetingText = document.getElementById('greeting-text');
        
        // State
        let userProfile = { age: null, goal: null };
        let waterIntake = 0;

        // --- 1. Initialization & Contextual Intelligence ---
        function init() {
            setContextualGreeting();
        }

        function setContextualGreeting() {
            const hour = new Date().getHours();
            let timeGreeting = '';
            const ctxSugg = document.getElementById('context-suggestion');
            
            if (hour >= 5 && hour < 12) {
                timeGreeting = 'Good morning';
                ctxSugg.innerHTML = "Morning! Start your day with high protein and complex carbs for sustained energy. Avoid sugary cereals!";
            } else if (hour >= 12 && hour < 17) {
                timeGreeting = 'Good afternoon';
                ctxSugg.innerHTML = "Mid-day slump? Avoid heavy refined carbs right now to stay alert. Grab some nuts or an apple.";
            } else if (hour >= 17 && hour < 21) {
                timeGreeting = 'Good evening';
                ctxSugg.innerHTML = "Dinner time. Keep it balanced with lean proteins and veggies for better sleep and recovery.";
            } else {
                timeGreeting = 'Hello';
                ctxSugg.innerHTML = "Late night cravings? It's often dehydration. Try a glass of water or herbal tea instead of snacking.";
            }

            greetingText.innerText = `${timeGreeting}! Let's build healthy habits today.`;
        }

        // --- 2. User Profile Setup ---
        saveProfileBtn.addEventListener('click', () => {
            const age = document.getElementById('user-age').value;
            const goal = document.getElementById('user-goal').value;
            
            if (!age || !goal) {
                alert('Please enter your age and select a goal to continue.');
                return;
            }
            
            userProfile = { age, goal };
            document.getElementById('insight-goal').innerText = goal;
            
            // Transition to Dashboard
            profileSection.style.opacity = '0';
            profileSection.style.transform = 'scale(0.95)';
            
            setTimeout(() => {
                profileSection.classList.add('hidden');
                dashboard.classList.remove('hidden');
                
                // Dashboard enter animation
                dashboard.style.opacity = '0';
                dashboard.style.transform = 'translateY(20px)';
                
                // Trigger reflow
                void dashboard.offsetWidth; 
                
                dashboard.style.transition = 'all 0.8s cubic-bezier(0.4, 0, 0.2, 1)';
                dashboard.style.opacity = '1';
                dashboard.style.transform = 'translateY(0)';
            }, 300);
        });

        // --- 3. Smart Food Logger & Analysis ---
        const foodDatabase = {
            unhealthy: ['burger', 'pizza', 'fries', 'chips', 'soda', 'candy', 'cake', 'ice cream', 'donut', 'cookie', 'fried'],
            healthy: ['salad', 'chicken', 'apple', 'fish', 'eggs', 'fruit', 'juice', 'broccoli', 'oats', 'yogurt', 'salmon', 'spinach']
        };

        document.getElementById('log-food-btn').addEventListener('click', () => {
            const input = document.getElementById('food-input').value.toLowerCase().trim();
            if (!input) return;

            // Loading state
            const btn = document.getElementById('log-food-btn');
            btn.disabled = true;
            btn.innerText = 'Analyzing...';
            document.getElementById('food-loader').classList.remove('hidden');
            document.getElementById('food-result').classList.add('hidden');

            // Simulate AI Processing delay
            setTimeout(() => {
                btn.disabled = false;
                btn.innerText = 'Analyze Food 🔍';
                document.getElementById('food-loader').classList.add('hidden');
                analyzeFood(input);
            }, 1800);
        });

        function analyzeFood(food) {
            let type = 'moderate';
            
            // Simple keyword matching for simulation
            for(let h of foodDatabase.healthy) {
                if(food.includes(h)) type = 'healthy';
            }
            for(let u of foodDatabase.unhealthy) {
                if(food.includes(u)) type = 'unhealthy';
            }

            let score, carbs, protein, fat, badgeClass, badgeText;
            
            if (type === 'healthy') {
                score = Math.floor(Math.random() * 15) + 85; // 85-100
                carbs = Math.floor(Math.random() * 20) + 30; // 30-50%
                protein = Math.floor(Math.random() * 20) + 30; // 30-50%
                fat = 100 - carbs - protein;
                badgeClass = 'healthy'; badgeText = 'Healthy Choice';
            } else if (type === 'unhealthy') {
                score = Math.floor(Math.random() * 20) + 20; // 20-40
                carbs = Math.floor(Math.random() * 20) + 50; // 50-70%
                protein = Math.floor(Math.random() * 10) + 5; // 5-15%
                fat = 100 - carbs - protein;
                badgeClass = 'unhealthy'; badgeText = 'Unhealthy';
            } else {
                score = Math.floor(Math.random() * 20) + 50; // 50-70
                carbs = Math.floor(Math.random() * 20) + 40; 
                protein = Math.floor(Math.random() * 15) + 15; 
                fat = 100 - carbs - protein;
                badgeClass = 'moderate'; badgeText = 'Moderate';
            }

            // Update UI
            document.getElementById('food-name').innerText = food;
            animateValue('food-score', 0, score, 1000);
            
            const badge = document.getElementById('food-badge');
            badge.className = `badge ${badgeClass}`;
            badge.innerText = badgeText;

            // Reset macro bars before animating
            document.getElementById('carbs-bar').style.width = '0%';
            document.getElementById('protein-bar').style.width = '0%';
            document.getElementById('fat-bar').style.width = '0%';
            
            document.getElementById('food-result').classList.remove('hidden');

            // Animate macro bars
            setTimeout(() => {
                document.getElementById('carbs-val').innerText = carbs;
                document.getElementById('carbs-bar').style.width = carbs + '%';
                
                document.getElementById('protein-val').innerText = protein;
                document.getElementById('protein-bar').style.width = protein + '%';
                
                document.getElementById('fat-val').innerText = fat;
                document.getElementById('fat-bar').style.width = fat + '%';
            }, 100);

            // Update suggestions based on result
            updateSmartSuggestions(food, type);
        }

        function animateValue(id, start, end, duration) {
            const obj = document.getElementById(id);
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                obj.innerHTML = Math.floor(progress * (end - start) + start);
                if (progress < 1) window.requestAnimationFrame(step);
            };
            window.requestAnimationFrame(step);
        }

        // --- 4. Smart Suggestions ---
        function updateSmartSuggestions(food, type) {
            const box = document.getElementById('smart-suggestions');
            box.style.textAlign = 'left';
            box.style.alignItems = 'flex-start';
            
            if (type === 'unhealthy') {
                let alt = 'a healthier alternative';
                if(food.includes('chips')) alt = 'air-popped popcorn or crisp apple slices';
                else if(food.includes('soda')) alt = 'sparkling water with a splash of fresh lemon or lime';
                else if(food.includes('burger')) alt = 'a grilled chicken sandwich or a turkey wrap';
                else if(food.includes('pizza')) alt = 'a cauliflower crust pizza or whole wheat pita bread';
                else if(food.includes('fries')) alt = 'baked sweet potato wedges';
                
                box.innerHTML = `
                    <div style="font-size: 1.5rem; margin-bottom: 10px;">⚠️</div>
                    <div>
                        <strong style="color: var(--danger); font-size: 1.1rem;">High calories & refined carbs detected!</strong>
                        <p style="margin: 8px 0 0 0;">Next time you crave <span style="text-transform:capitalize">${food}</span>, try swapping it for <b>${alt}</b> to better support your <i>${userProfile.goal}</i> goal.</p>
                    </div>`;
                box.style.borderLeft = '4px solid var(--danger)';
            } else if (type === 'healthy') {
                box.innerHTML = `
                    <div style="font-size: 1.5rem; margin-bottom: 10px;">✨</div>
                    <div>
                        <strong style="color: var(--success); font-size: 1.1rem;">Fantastic Choice!</strong>
                        <p style="margin: 8px 0 0 0;">This provides great nutritional value. Pair it with a large glass of water to maximize digestion and stay on track for your <i>${userProfile.goal}</i> goal.</p>
                    </div>`;
                box.style.borderLeft = '4px solid var(--success)';
            } else {
                box.innerHTML = `
                    <div style="font-size: 1.5rem; margin-bottom: 10px;">⚖️</div>
                    <div>
                        <strong style="color: var(--warning); font-size: 1.1rem;">Good, but can be optimized.</strong>
                        <p style="margin: 8px 0 0 0;">To make this meal perfect, try adding a side of dark leafy greens or a lean protein source to balance the macronutrients.</p>
                    </div>`;
                box.style.borderLeft = '4px solid var(--warning)';
            }
        }

        // --- 5. Habit Tracker (Water) ---
        document.getElementById('add-water-btn').addEventListener('click', () => {
            if (waterIntake < 8) {
                waterIntake++;
                document.getElementById('water-count').innerText = waterIntake;
                document.getElementById('water-progress').style.width = (waterIntake / 8 * 100) + '%';
                
                // Add pop animation to button
                const btn = document.getElementById('add-water-btn');
                btn.style.transform = 'scale(0.95)';
                setTimeout(() => btn.style.transform = 'none', 150);
                
                if (waterIntake === 8) {
                    const streak = document.getElementById('water-streak');
                    streak.innerHTML = '🎉 Daily Goal Met! 4-day hydration streak unlocked!';
                    streak.style.color = 'var(--success)';
                    btn.disabled = true;
                    btn.innerText = 'Goal Achieved 💧';
                }
            }
        });

        // --- 6. Personalized Insights ---
        const insights = [
            "🧠 Behavioral Tip: You tend to crave sugar in the late afternoon. Try keeping a stash of mixed nuts or dark chocolate nearby.",
            "💧 Hydration Tip: Drinking a large glass of water 20 minutes before meals can help you feel more full and prevent overeating.",
            "💪 Nutrition Tip: Your protein intake is crucial for your goals. Consider adding greek yogurt or boiled eggs to your breakfast.",
            "⏱️ Eating Habit: Eating slower gives your brain the 20 minutes it needs to realize your stomach is actually full.",
            "🌙 Sleep & Diet: Late night snacking is often due to boredom or stress, not physical hunger. Try brewing some chamomile tea instead."
        ];
        
        document.getElementById('refresh-insight-btn').addEventListener('click', () => {
            const btn = document.getElementById('refresh-insight-btn');
            // Spin animation for the button icon
            btn.innerHTML = '↻ Generating...';
            
            setTimeout(() => {
                const randomTip = insights[Math.floor(Math.random() * insights.length)];
                
                const textEl = document.getElementById('insight-text');
                textEl.style.opacity = 0;
                
                setTimeout(() => {
                    textEl.innerText = randomTip;
                    textEl.style.opacity = 1;
                    btn.innerHTML = '↻ Generate New Insight';
                }, 300);
            }, 500);
        });

        // Run setup
        init();
    </script>
</body>
</html>


