[index.html](https://github.com/user-attachments/files/28034487/index.html)
<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>ChefAI — Cyber Edition</title>
    <style>
        /* Полный киберпанк сброс, который гарантирует клики на любых смартфонах */
        * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
        
        body { 
            background-color: #050203; 
            color: #ffffff; 
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; 
            padding: 16px;
            min-height: 100vh;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(244, 63, 94, 0.06) 0%, transparent 50%),
                radial-gradient(circle at 90% 80%, rgba(244, 63, 94, 0.04) 0%, transparent 50%);
            background-attachment: fixed;
        }

        /* Переливающийся неоновый логотип */
        @keyframes neonGlow {
            0% { text-shadow: 0 0 10px #f43f5e, 0 0 20px #e11d48; }
            50% { text-shadow: 0 0 15px #ff2a4b, 0 0 30px #b91c1c; }
            100% { text-shadow: 0 0 10px #f43f5e, 0 0 20px #e11d48; }
        }

        /* Верхняя панель */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            background: #0d080b;
            border-bottom: 2px solid #f43f5e;
            box-shadow: 0 4px 20px rgba(244, 63, 94, 0.2);
            border-radius: 14px;
            margin-bottom: 20px;
        }

        .logo { font-size: 24px; font-weight: 900; color: #fff; }
        .logo span { color: #f43f5e; animation: neonGlow 3s infinite linear; }

        /* Надежный переключатель языков на 3 позиции */
        .lang-container {
            display: flex;
            gap: 2px;
            background: #171114;
            padding: 3px;
            border-radius: 8px;
            border: 1px solid rgba(244, 63, 94, 0.3);
        }

        .lang-btn {
            background: transparent;
            border: none;
            color: #9ca3af;
            padding: 6px 10px;
            font-size: 12px;
            font-weight: 800;
            border-radius: 6px;
            cursor: pointer;
        }

        .lang-btn.active {
            background: #f43f5e;
            color: #fff;
            box-shadow: 0 0 10px #f43f5e;
        }

        /* Главное меню в стиле сегментов */
        .menu-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 6px;
            margin-bottom: 24px;
            background: #0d080b;
            padding: 4px;
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.03);
        }

        .menu-btn {
            background-color: transparent;
            color: #9ca3af;
            border: none;
            padding: 12px 2px;
            border-radius: 8px;
            font-weight: 700;
            font-size: 13px;
            cursor: pointer;
            text-align: center;
        }

        .menu-btn.active {
            background: linear-gradient(135deg, #f43f5e 0%, #991b1b 100%);
            color: #ffffff;
            box-shadow: 0 0 15px rgba(244, 63, 94, 0.4);
        }

        .tab-content { display: none; }
        .tab-content.active { display: block; }

        /* Вкладка Home */
        .hero { text-align: center; padding: 30px 10px; }
        .hero h1 { font-size: 36px; font-weight: 900; line-height: 1.2; margin-bottom: 16px; }
        .hero h1 span { color: #f43f5e; animation: neonGlow 3s infinite linear; }
        .hero p { color: #9ca3af; font-size: 16px; margin-bottom: 32px; line-height: 1.5; }

        /* Мощные неоновые кнопки */
        .action-btn { 
            background: linear-gradient(135deg, #f43f5e 0%, #991b1b 100%);
            color: white; 
            border: none; 
            padding: 16px 20px; 
            font-size: 16px; 
            font-weight: 800; 
            border-radius: 12px; 
            cursor: pointer; 
            width: 100%;
            box-shadow: 0 0 15px rgba(244, 63, 94, 0.4);
            letter-spacing: 0.5px;
        }

        /* Блоки-панели */
        .box { 
            background: #0d080b; 
            border: 1px solid rgba(244, 63, 94, 0.2); 
            padding: 20px; 
            border-radius: 16px; 
            margin-bottom: 20px; 
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
        }
        
        .form-group { display: flex; gap: 10px; margin-bottom: 16px; }
        
        input, select { 
            flex: 1; 
            background: #050203; 
            border: 1px solid rgba(244, 63, 94, 0.4); 
            padding: 14px; 
            border-radius: 10px; 
            color: white; 
            font-size: 16px; 
            outline: none;
        }
        input:focus { border-color: #f43f5e; box-shadow: 0 0 10px rgba(244, 63, 94, 0.3); }

        /* Теги */
        .tags-container { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 16px; }
        .tag { 
            background: rgba(244, 63, 94, 0.15); 
            border: 1px solid #f43f5e; 
            padding: 8px 14px; 
            border-radius: 100px; 
            font-size: 14px; 
            font-weight: 600;
            color: #ff7e95;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .tag span { color: #f43f5e; font-weight: bold; font-size: 18px; cursor: pointer; }
        
        #ai-loading-text { color: #ff7e95; font-weight: 700; text-align: center; margin: 20px 0; }
        
        /* Карточка вывода */
        .card { background: #171114; border-radius: 16px; overflow: hidden; border: 1px solid rgba(244, 63, 94, 0.3); padding: 15px; }
        .recipe-details pre { 
            white-space: pre-wrap; 
            font-family: inherit; 
            font-size: 15px; 
            color: #e5e7eb; 
            line-height: 1.6;
            background: #050203;
            padding: 14px;
            border-radius: 10px;
            border-left: 4px solid #f43f5e;
        }

        /* Калькулятор */
        .calories-display { font-size: 54px; font-weight: 900; color: #f43f5e; text-align: center; margin: 15px 0; text-shadow: 0 0 15px #f43f5e; }
        
        .list-row { display: flex; justify-content: space-between; align-items: center; padding: 12px 0; border-bottom: 1px solid rgba(255, 255, 255, 0.05); }
        .clear-btn { background: transparent; border: 1px solid #f43f5e; color: #f43f5e; padding: 6px 12px; border-radius: 6px; cursor: pointer; font-size: 12px; font-weight: bold; }
    </style>
</head>
<body>

    <!-- Шапка приложения -->
    <header>
        <div class="logo">Chef<span>AI</span></div>
        <div class="lang-container">
            <button class="lang-btn active" id="lang-uk" onclick="setLanguage('uk')">UA</button>
            <button class="lang-btn" id="lang-en" onclick="setLanguage('en')">EN</button>
        </div>
    </header>

    <!-- Главное меню навигации -->
    <div class="menu-grid">
        <button class="menu-btn active" id="menu-home" onclick="openTab('home')">Home</button>
        <button class="menu-btn" id="menu-search" onclick="openTab('search')">AI Kitchen</button>
        <button class="menu-btn" id="menu-calories" onclick="openTab('calories')">КБЖУ</button>
        <button class="menu-btn" id="menu-profile" onclick="openTab('profile')">Profile</button>
    </div>

    <!-- ТАБ 1: ГЛАВНАЯ -->
    <div id="view-home" class="tab-content active">
        <div class="hero">
            <h1 id="txt-title">Твій холодильник спроможний на <span>шедеври</span></h1>
            <p id="txt-desc">Вкажіть продукты, і локальний ШІ моментально побудує страву з точними грамовками та кроками приготування.</p>
            <button class="action-btn" id="btn-try" onclick="openTab('search')">Спробувати</button>
        </div>
    </div>

    <!-- ТАБ 2: НЕЙРОКУХНЯ -->
    <div id="view-search" class="tab-content">
        <div class="box">
            <h2 id="txt-lab-title" style="margin-bottom: 15px; font-size: 20px;">ШІ-Лабораторія</h2>
            <div class="form-group">
                <input type="text" id="input-ingredient" placeholder="Наприклад: курка, сир...">
                <button class="menu-btn active" style="padding: 0 20px; border-radius: 10px; font-size: 20px;" onclick="addTag()">+</button>
            </div>
            <div class="tags-container" id="tags-target"></div>
            <button class="action-btn" id="btn-generate" style="display: none;" onclick="generateRecipe()">ЗГЕНЕРУВАТИ РЕЦЕПТ</button>
        </div>

        <div id="ai-loading-text" style="display: none;">🤖 Локальний ШІ прораховує грамовку та пише кроки...</div>

        <div id="results-block" style="display: none;">
            <div class="card">
                <div class="recipe-details">
                    <pre id="ai-output-text"></pre>
                </div>
            </div>
        </div>
    </div>

    <!-- ТАБ 3: КАЛЬКУЛЯТОР -->
    <div id="view-calories" class="tab-content">
        <div class="box">
            <h2 id="txt-calc-title" style="margin-bottom: 15px;">Розрахунок калорій</h2>
            <div style="margin-bottom: 12px;">
                <label id="lbl-gender" style="display:block; margin-bottom:6px; color:#9ca3af;">Стать:</label>
                <select id="calc-gender">
                    <option value="male" id="opt-male">Чоловік</option>
                    <option value="female" id="opt-female">Жінка</option>
                </select>
            </div>
            <div style="margin-bottom: 12px;">
                <label id="lbl-weight" style="display:block; margin-bottom:6px; color:#9ca3af;">Вага (кг):</label>
                <input type="number" id="calc-weight" value="70">
            </div>
            <div style="margin-bottom: 12px;">
                <label id="lbl-height" style="display:block; margin-bottom:6px; color:#9ca3af;">Зріст (см):</label>
                <input type="number" id="calc-height" value="175">
            </div>
            <div style="margin-bottom: 18px;">
                <label id="lbl-age" style="display:block; margin-bottom:6px; color:#9ca3af;">Вік:</label>
                <input type="number" id="calc-age" value="25">
            </div>
            <button class="action-btn" id="btn-calc" onclick="runCalories()">Розрахувати</button>
        </div>

        <div class="box" style="text-align: center;">
            <h3 id="txt-norm-title">Ваша добова норма:</h3>
            <div class="calories-display" id="calories-result">0</div>
            <p id="txt-norm-desc" style="color: #9ca3af; font-size: 14px;">Введіть дані для розрахунку базового метаболізму.</p>
        </div>
    </div>

    <!-- ТАБ 4: ПРОФИЛЬ -->
    <div id="view-profile" class="tab-content">
        <div class="box">
            <h2 style="margin-bottom: 20px; font-size: 22px;">Premium Cyber Profile</h2>
            <div class="list-row">
                <span id="txt-prof-status">Статус:</span>
                <span style="color:#f43f5e; font-weight:bold;">AI CHEF ULTRA</span>
            </div>
            <div class="list-row">
                <span id="txt-prof-count">Згенеровано страв:</span>
                <span id="gen-count" style="font-weight:bold;">0</span>
            </div>
            <div class="list-row" style="margin-top: 20px; border: none;">
                <span id="txt-prof-storage">Очистити дані:</span>
                <button class="clear-btn" id="btn-clear" onclick="resetAll()">Reset</button>
            </div>
        </div>
    </div>

    <script>
        // База языковых переводов ВСЕГО интерфейса
        var translations = {
            uk: {
                'menu-home': 'Головна', 'menu-search': 'AI Кухня', 'menu-calories': 'КБЖУ', 'menu-profile': 'Профіль',
                'txt-title': 'Твій холодильник спроможний на <span>шедеври</span>',
                'txt-desc': 'Вкажіть продукти, і штучний інтелект моментально побудує страву з точними грамовками та кроками приготування.',
                'btn-try': 'Спробувати', 'txt-lab-title': 'ШІ-Лабораторія', 'input-ingredient': 'Наприклад: курка, сир...',
                'btn-generate': 'ЗГЕНЕРУВАТИ РЕЦЕПТ', 'ai-loading-text': '🤖 ШІ прораховує грамовку та пише кроки...',
                'txt-calc-title': 'Розрахунок калорій', 'lbl-gender': 'Стать:', 'opt-male': 'Чоловік', 'opt-female': 'Жінка',
                'lbl-weight': 'Вага (кг):', 'lbl-height': 'Зріст (см):', 'lbl-age': 'Вік (років):', 'btn-calc': 'Розрахувати',
                'txt-norm-title': 'Ваша добова норма:', 'txt-norm-desc': 'Введіть дані для розрахунку базового метаболізму.',
                'txt-prof-status': 'Статус облікового запису:', 'txt-prof-count': 'Згенерувано страв ШІ:', 'txt-prof-storage': 'Сховище даних:',
                'btn-clear': 'Очистити історію'
            },
           
            en: {
                'menu-home': 'Home', 'menu-search': 'AI Kitchen', 'menu-calories': 'Calories', 'menu-profile': 'Profile',
                'txt-title': 'Your fridge is capable of <span>masterpieces</span>',
                'txt-desc': 'Specify ingredients, and AI will instantly build a premium dish with exact weights and cooking steps.',
                'btn-try': 'Try Now', 'txt-lab-title': 'AI Laboratory', 'input-ingredient': 'e.g.: chicken, cheese...',
                'btn-generate': 'GENERATE RECIPE', 'ai-loading-text': '🤖 AI is calculating weights and writing steps...',
                'txt-calc-title': 'Calorie Calculator', 'lbl-gender': 'Gender:', 'opt-male': 'Male', 'opt-female': 'Female',
                'lbl-weight': 'Weight (kg):', 'lbl-height': 'Height (cm):', 'lbl-age': 'Age (years):', 'btn-calc': 'Calculate',
                'txt-norm-title': 'Your daily norm:', 'txt-norm-desc': 'Enter your body parameters to calculate BMR.',
                'txt-prof-status': 'Account Status:', 'txt-prof-count': 'AI Dishes Generated:', 'txt-prof-storage': 'Data Storage:',
                'btn-clear': 'Clear History'
            }
        };

        var tagsList = [];
        var activeLang = 'uk';
        var countGens = parseInt(localStorage.getItem('cyber_gen_count')) || 0;
        document.getElementById('gen-count').innerText = countGens;

        // Переключение табов
        function openTab(id) {
            var contents = document.getElementsByClassName('tab-content');
            for (var i = 0; i < contents.length; i++) { contents[i].classList.remove('active'); }
            var buttons = document.getElementsByClassName('menu-btn');
            for (var i = 0; i < buttons.length; i++) { buttons[i].classList.remove('active'); }
            
            document.getElementById('view-' + id).classList.add('active');
            document.getElementById('menu-' + id).classList.add('active');
            window.scrollTo(0, 0);
        }

        // Рабочее переключение языков интерфейса
        function setLanguage(lang) {
            activeLang = lang;
            var buttons = document.getElementsByClassName('lang-btn');
            for (var i = 0; i < buttons.length; i++) { buttons[i].classList.remove('active'); }
            document.getElementById('lang-' + lang).classList.add('active');

            var pack = translations[lang];
            for (var key in pack) {
                var el = document.getElementById(key);
                if (el) {
                    if (el.tagName === 'INPUT') {
                        el.placeholder = pack[key];
                    } else {
                        el.innerHTML = pack[key];
                    }
                }
            }
            runCalories(); // Обновляем текст калькулятора при смене языка
        }

        // Логика тегов
        function addTag() {
            var input = document.getElementById('input-ingredient');
            var val = input.value.trim().toLowerCase();
            if (val && tagsList.indexOf(val) === -1) {
                tagsList.push(val);
                input.value = '';
                renderTags();
            }
        }

        document.getElementById('input-ingredient').addEventListener('keydown', function(e) {
            if (e.key === 'Enter') { addTag(); }
        });

        function deleteTag(idx) {
            tagsList.splice(idx, 1);
            renderTags();
        }

        function renderTags() {
            var target = document.getElementById('tags-target');
            target.innerHTML = '';
            for (var i = 0; i < tagsList.length; i++) {
                target.innerHTML += '<div class="tag">' + tagsList[i] + '<span onclick="deleteTag(' + i + ')">✕</span></div>';
            }
            document.getElementById('btn-generate').style.display = tagsList.length ? 'block' : 'none';
        }

        // Генерация рецептов ChatGPT на выбранном языке
      // Хранилище сгенерированных названий, чтобы избежать повторов
var generatedHistory = JSON.parse(localStorage.getItem('cyber_recipe_history')) || [];

function generateRecipe() {
    if (!tagsList.length) return;

    document.getElementById('ai-loading-text').style.display = 'block';
    document.getElementById('results-block').style.display = 'none';
    document.getElementById('input-ingredient').blur();

    setTimeout(function() {
        document.getElementById('ai-loading-text').style.display = 'none';
        var output = document.getElementById('ai-output-text');
        
        // Массивы для вариативности генерации
        var MethodsUA = [
             Готуйте, поки не приготується ;)
        ];
        var MethodsEN = [
           Cook until done ;)
     
        ];

        var CookUA = [
            "пассеруйте на середньому вогні протягом 12 хвилин.",
            "обсмажуйте в глибокій сковороді вок до хрусткої скоринки.",
            "запікайте в термо-боксі при температуре 180°C.",
            "тушкуйте у власному соку із додаванням спецій 15 хвилин.",
            "екстрагуйте смак методом су-від у кибер-середовищі."
        ];
        var CookEN = [
            "saute over medium heat for 12 minutes.",
            "stir-fry in a deep wok until crispy.",
            "bake in a thermo-box at 180°C.",
            "stew in its own juices with spices for 15 minutes.",
            "extract flavors using the sous-vide method in a cyber environment."
        ];

        var SaucesUA = [
            "кисло-солодким неоновим соусом", "гострим кібер-чилі", 
            "синтезованим грибним мусом", "пряним каррі-екстрактом", "соєво-імбирною глазур'ю"
        ];
        var SaucesEN = [
            "sweet and sour neon sauce", "spicy cyber-chili", 
            "synthesized mushroom mousse", "savory curry extract", "soy-ginger glaze"
        ];

        var DishTypesUA = ["Кібер-Салат", "Синтез-Мікс", "Техно-Рагу", "Нейро-Боул", "Прото-Гарнір"];
        var DishTypesEN = ["Cyber-Salad", "Synthesis-Mix", "Techno-Ragout", "Neuro-Bowl", "Proto-Garnish"];

        var title = "", ingTitle = "", stepTitle = "", oilText = "", dishName = "", finalTxt = "";
        var isUnique = false;
        var attempts = 0;

        // Цикл подбора уникального сочетания, которого еще не было в истории
        while (!isUnique && attempts < 50) {
            var mIdx = Math.floor(Math.random() * MethodsUA.length);
            var cIdx = Math.floor(Math.random() * CookUA.length);
            var sIdx = Math.floor(Math.random() * SaucesUA.length);
            var tIdx = Math.floor(Math.random() * DishTypesUA.length);

            // Формируем имя блюда на основе первого введенного ингредиента
            var mainIng = tagsList[0];
            if (activeLang === 'uk') {
                dishName = DishTypesUA[tIdx] + " з " + mainIng;
            } else {
                dishName = DishTypesEN[tIdx] + " with " + mainIng;
            }

            // Проверяем, было ли такое блюдо с такой комбинацией процесса
            var recipeKey = dishName + "_" + mIdx + cIdx + sIdx;
            if (!generatedHistory.includes(recipeKey)) {
                generatedHistory.push(recipeKey);
                localStorage.setItem('cyber_recipe_history', JSON.stringify(generatedHistory));
                isUnique = true;

                // Сборка текста на выбранном языке
                if (activeLang === 'uk') {
                    title = '🤖 ЕКСКЛЮЗИВ ВІД ШІ: ' + dishName.toUpperCase();
                    ingTitle = 'ІНГРЕДІЄНТИ (СТРОГО З ВАШОГО СПИСКУ):';
                    stepTitle = 'КРОКИ ПРИГОТУВАННЯ:';
                    oilText = '• масло — 15мл';
                    
                    finalTxt = title + "\n\n" + ingTitle + "\n";
                    tagsList.forEach(function(t) { finalTxt += "• " + t + " — 120g\n"; });
                    finalTxt += oilText + "\n\n" + stepTitle + "\n";
                    finalTxt += "1. " + MethodsUA[mIdx] + " компоненти: " + tagsList.join(', ') + ".\n";
                    finalTxt += "2. Додайте основу на сковороду або деко та " + CookUA[cIdx] + "\n";
                    finalTxt += "3. Заправте страву " + SaucesUA[sIdx] + " та подавайте гарячою!";
                } else {
                    title = '🤖 EXCLUSIVE BY AI: ' + dishName.toUpperCase();
                    ingTitle = 'INGREDIENTS (ONLY FROM YOUR LIST):';
                    stepTitle = 'COOKING STEPS:';
                    oilText = '• oil — 15ml';

                    finalTxt = title + "\n\n" + ingTitle + "\n";
                    tagsList.forEach(function(t) { finalTxt += "• " + t + " — 120g\n"; });
                    finalTxt += oilText + "\n\n" + stepTitle + "\n";
                    finalTxt += "1. " + MethodsEN[mIdx] + " the ingredients: " + tagsList.join(', ') + ".\n";
                    finalTxt += "2. Place them into the cooking block and " + CookEN[cIdx] + "\n";
                    finalTxt += "3. Top with " + SaucesEN[sIdx] + " and serve immediately!";
                }
            }
            attempts++;
        }

        output.innerText = finalTxt;
        document.getElementById('results-block').style.display = 'block';

        countGens++;
        localStorage.setItem('cyber_gen_count', countGens);
        document.getElementById('gen-count').innerText = countGens;
        if (typeof updateRank === "function") updateRank();
    }, 1200);
}

        // Калькулятор
        function runCalories() {
            var gender = document.getElementById('calc-gender').value;
            var w = parseFloat(document.getElementById('calc-weight').value) || 0;
            var h = parseFloat(document.getElementById('calc-height').value) || 0;
            var a = parseFloat(document.getElementById('calc-age').value) || 0;

            if (!w || !h || !a) return;

            var bmr = (10 * w) + (6.25 * h) - (5 * a);
            bmr = (gender === 'male') ? bmr + 5 : bmr - 161;
            var total = Math.round(bmr * 1.2);

            document.getElementById('calories-result').innerText = total;

            var desc = document.getElementById('txt-norm-desc');
            if (activeLang === 'uk') {
                desc.innerHTML = `Схуднення: ${Math.round(total * 0.85)} ккал | Набір маси: ${Math.round(total * 1.15)} ккал`;
            } else if (activeLang === 'ru') {
                desc.innerHTML = `Похудение: ${Math.round(total * 0.85)} ккал | Набор массы: ${Math.round(total * 1.15)} ккал`;
            } else {
                desc.innerHTML = `Weight Loss: ${Math.round(total * 0.85)} kcal | Mass Gain: ${Math.round(total * 1.15)} kcal`;
            }
        }

        function resetAll() {
            localStorage.clear();
            countGens = 0;
            document.getElementById('gen-count').innerText = 0;
            alert('Done!');
        }

        // Стартуем на украинском
        setLanguage('uk');
    </script>
</body>
</html>
