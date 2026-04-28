<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Анекдотная — только HTML и CSS</title>
    <link rel="icon" type="image/x-icon" href="/C:\Users\Валерия\Desktop\сайт 28.04/vector.ico">
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            background: #fff1ae;
            color: #2C2C2C;
            line-height: 1.5;
            max-width: 1400px;
            margin: 0 auto;
            padding: 15px;
        }

        header {
            background: #ffae77;
            color: white;
            padding: 15px 20px;
            border-radius: 30px;
            margin-bottom: 20px;
            position: relative;
        }

        .header-inner {
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: white;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        #menu-toggle {
            display: none;
        }

        .burger {
            display: none;
            font-size: 2rem;
            cursor: pointer;
            user-select: none;
            padding: 5px 10px;
            background: rgba(255,255,255,0.2);
            border-radius: 8px;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 5px;
            flex-wrap: wrap;
        }

        nav a {
            color: white;
            text-decoration: none;
            padding: 8px 14px;
            border-radius: 20px;
            background: rgba(255,255,255,0.2);
            font-weight: 500;
            transition: background 0.2s;
        }

        nav a:hover {
            background: #f5b5ae;
        }

        @media (max-width: 700px) {
            .burger {
                display: block;
            }
            nav ul {
                display: none;
                flex-direction: column;
                width: 100%;
                background: #f5b5ae;
                padding: 10px;
                border-radius: 10px;
                margin-top: 10px;
            }
            #menu-toggle:checked ~ nav ul {
                display: flex;
            }
            .header-inner {
                flex-direction: column;
                align-items: flex-start;
            }
        }

        section {
            display: none;
            background: #f9d6d2;
            padding: 25px;
            border-radius: 12px;
            border: 2px solid #ffd970;
            margin-bottom: 50px;
        }

        #home {
            display: block;
        }

        section:target {
            display: block;
        }

        :target:not(#home) ~ #home {
            display: none;
        }

        h1 {
            font-size: 2.2rem;
            color: #ff5555;
            margin-bottom: 15px;
            border-bottom: 3px dashed white;
            padding-bottom: 10px;
        }

        h2 {
            font-size: 1.8rem;
            color: #ff5555;
            margin: 20px 10 10px;
        }

        h3 {
            color: #ff5555;
            margin-bottom: 8px;
        }

        .btn {
            display: inline-block;
            background: #ff6666;
            color: white;
            padding: 12px 25px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            transition: background 0.2s;
            font-family: inherit;
            font-size: 1rem;
            border: none;
            cursor: pointer;
        }
        .btn:hover { background: #ffae77; }

        .joke-card {
            background: #f9f9f9;
            padding: 10px;
            margin: 10px 0;
            border-left: 5px solid #FF6666;
            border-radius: 8px;
        }

        .joke-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 15px 0;
            background: white;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left;
        }
        th {
            background: #ff6666;
            color: white;
        }

        .special-block {
            text-align: center;
            padding: 30px;
            border: 3px double #D81B60;
            border-radius: 15px;
            background: #FFF5F0;
        }

        .subscribe-form {
            margin: 20px 0;
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }
        .subscribe-form input[type="email"] {
            padding: 10px 15px;
            border: 2px solid #ff6666;
            border-radius: 25px;
            flex: 1;
            min-width: 200px;
            font-family: inherit;
        }

        footer {
            text-align: center;
            margin-top: 30px;
            padding: 15px;
            color: white;
            background: #ffae77;
            border-radius: 12px;
        }

        .random-link {
            display: inline-block;
            margin: 15px 0;
        }

        /* === СТИЛИ ВКЛАДОК КАТАЛОГА === */
        .tabs {
            margin-top: 20px;
        }

        .tabs input[type="radio"] {
            display: none;
        }

        .tabs-labels {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-bottom: 20px;
        }

        .tabs-labels label {
            background: white;
            border: 2px solid #ff6666;
            padding: 10px 20px;
            border-radius: 25px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s;
        }

        .tabs input[type="radio"]:checked + label {
            background: #FF6700;
            color: white;
            border-color: #FF6700;
        }

        .tab-content {
            display: none;
        }

        #tab-all:checked ~ #content-all,
        #tab-students:checked ~ #content-students,
        #tab-animals:checked ~ #content-animals,
        #tab-life:checked ~ #content-life,
        #tab-cartoons:checked ~ #content-cartoons {
            display: block;
        }
    </style>
</head>
<body>

<header>
    <div class="header-inner">
        <a href="#home" class="logo">
            <svg width="35" height="35" viewBox="0 0 24 24" fill="white" xmlns="http://www.w3.org/2000/svg">
                <circle cx="12" cy="12" r="10" fill="white"/>
                <path d="M8 14s1.5 2 4 2 4-2 4-2" stroke="#FF6700" stroke-width="2" fill="none"/>
            </svg>
            Анекдотная
        </a>
        <input type="checkbox" id="menu-toggle">
        <label for="menu-toggle" class="burger">☰</label>
        <nav>
            <ul>
                <li><a href="#home">Главная</a></li>
                <li><a href="#catalog">Каталог</a></li>
                <li><a href="#worst-joke">Анекдот дня</a></li>
                <li><a href="#about">О проекте</a></li>
                <li><a href="#team">Команда</a></li>
                <li><a href="#sitemap">Структура</a></li>
                <li><a href="#page404">Любимый анекдот авторов</a></li>
            </ul>
        </nav>
    </div>
</header>

<main>
    <!-- Каталог с вкладками -->
    <section id="catalog">
        <h2>Каталог анекдотов</h2>
        <div class="tabs">
            <!-- Радио-кнопки для переключения вкладок -->
            <input type="radio" name="catalog-tab" id="tab-all" checked>
            <input type="radio" name="catalog-tab" id="tab-students">
            <input type="radio" name="catalog-tab" id="tab-animals">
            <input type="radio" name="catalog-tab" id="tab-life">
            <input type="radio" name="catalog-tab" id="tab-cartoons">

            <!-- Ярлыки вкладок -->
            <div class="tabs-labels">
                <label for="tab-all">Все</label>
                <label for="tab-students">Про студентов</label>
                <label for="tab-animals">Про животных</label>
                <label for="tab-life">Жизненные</label>
                <label for="tab-cartoons">Про мультфильмы</label>
            </div>

            <!-- Содержимое вкладок -->
            <div class="tab-content" id="content-all">
                <div class="joke-grid">
                    <!-- Все 40 карточек (студенты, животные, жизненные, мультфильмы) -->
                    <!-- Студенты -->
                    <div class="joke-card"><h3>Зачёт автоматом</h3><p>Преподаватель: «Кто ответит на вопрос — получит зачёт автоматом». Студент: «А можно автоматом, но без вопроса?»</p></div>
                    <div class="joke-card"><h3>Курсовая</h3><p>— А можно краткое содержание? — Можно. Я её скачал.</p></div>
                    <div class="joke-card"><h3>Физкультура</h3><p>— Почему прогулял физкультуру? — Поскользнулся на диване и подвернул пульт.</p></div>
                    <div class="joke-card"><h3>Дед Мороз</h3><p>Сдавшим хвосты до Нового года — стипендия. Остальным — оливье без майонеза.</p></div>
                    <div class="joke-card"><h3>Подготовка</h3><p>— Ты к экзамену готовишься? — Да, третий сериал пересматриваю. Нервы важнее знаний.</p></div>
                    <div class="joke-card"><h3>Столовая</h3><p>— Дайте рыбу, но без костей и чтобы пахла котлетой.</p></div>
                    <div class="joke-card"><h3>Римская империя</h3><p>— Три причины падения? — Первая: не учила матчасть, вторую списать забыл, третью не придумали.</p></div>
                    <div class="joke-card"><h3>Кипятильник</h3><p>— Сосед, у тебя кипятильник есть? — Нет. — Хочу согреть чай утюгом.</p></div>
                    <div class="joke-card"><h3>Поисковые системы</h3><p>— Вы знаете предмет? — Я знаю, где методичка. — Зачёт по поисковым системам.</p></div>
                    <div class="joke-card"><h3>Каникулы</h3><p>— Отдохнул? — Даже выспался. Теперь как быть зомби на парах.</p></div>
                    <!-- Животные -->
                    <div class="joke-card"><h3>Кризис</h3><p>— Мне корм с лососем. — А мне опять «Вискас», кризис, затянем ошейники.</p></div>
                    <div class="joke-card"><h3>Попугай</h3><p>— У попугая депрессия. — Он видел, как кот диск царапает.</p></div>
                    <div class="joke-card"><h3>Золотая рыбка</h3><p>— Хочу, чтобы жена не пилила. — Теперь у неё нет рта, зато бензопила.</p></div>
                    <div class="joke-card"><h3>Заяц в баре</h3><p>— Морковный сок. — Только пиво. — Тогда пиво из морковки. — Ячмень тоже из земли.</p></div>
                    <div class="joke-card"><h3>Собака и хвост</h3><p>— Пытаюсь укусить консультанта по счастью, он всё время сзади.</p></div>
                    <div class="joke-card"><h3>Хомяк-философ</h3><p>— Ты чего лежишь? — Вселенная и так крутится, зачем усугублять.</p></div>
                    <div class="joke-card"><h3>Медведь и навигатор</h3><p>— Поверните к берлоге. — Я на машине. — Выйдите и лягте. — Я на самокате. — Положите самокат.</p></div>
                    <div class="joke-card"><h3>Ёж и дикобраз</h3><p>— Привет, с иголочки! — Я на стиле. — У тебя иголок больше. — Так я модный!</p></div>
                    <div class="joke-card"><h3>Мотивация для рыбки</h3><p>Хозяин включил «В поисках Немо» — теперь у рыбки мотивация.</p></div>
                    <div class="joke-card"><h3>Попугай пирата</h3><p>— Кэп, почему у них попугаи не разговаривают? — Бюджет не резиновый!</p></div>
                    <!-- Жизненные -->
                    <div class="joke-card"><h3>Весы</h3><p>58 кг с пакетом молока. Молоко — предатель!</p></div>
                    <div class="joke-card"><h3>Спорт</h3><p>Купил форму, лежу в ней на диване. Спорт — стиль жизни.</p></div>
                    <div class="joke-card"><h3>«Я подумаю»</h3><p>После слов сисадмина всё уже работает.</p></div>
                    <div class="joke-card"><h3>Экономика</h3><p>Съел курицу за 300 руб., считай заработал 300.</p></div>
                    <div class="joke-card"><h3>Отношения-лифт</h3><p>То вверх, то вниз, кнопка «стоп» не работает.</p></div>
                    <div class="joke-card"><h3>Полежать</h3><p>В 20 — угроза, в 35 — молитва.</p></div>
                    <div class="joke-card"><h3>Умные часы</h3><p>10 000 шагов, пока шашлык переворачивал.</p></div>
                    <div class="joke-card"><h3>Мультиварка</h3><p>— Может, достаточно соли? Или вы хотите морской аквариум?</p></div>
                    <div class="joke-card"><h3>Поздний сон</h3><p>Лёг в 22:00, в 2:30 знаю всё о гаечном ключе.</p></div>
                    <div class="joke-card"><h3>Возраст</h3><p>В 20 боишься что подумают, в 30 — налоговая, в 40 — давление.</p></div>
                    <!-- Мультфильмы -->
                    <div class="joke-card"><h3>Фитнес Зайца</h3><p>— Может, ну её, Олимпиаду? — Я не ради медалей, фитнес-браслет показывает 3000 калорий.</p></div>
                    <div class="joke-card"><h3>Шрек</h3><p>— Лук — метафора моей души. — Слои… Следующий!</p></div>
                    <div class="joke-card"><h3>Винни-Пух</h3><p>— Мёд не зависит от часовых поясов, в Австралии вечер.</p></div>
                    <div class="joke-card"><h3>Гомер на работе</h3><p>— Образование? — Смотрел «Как это работает». — Приняты на реактор.</p></div>
                    <div class="joke-card"><h3>Чебурашка</h3><p>Апельсины доставляем, даже если ящик с самолёта упал.</p></div>
                    <div class="joke-card"><h3>Карлсон</h3><p>— Варенье кончилось, назвали шаром с пропеллером. — Несу плюшки.</p></div>
                    <div class="joke-card"><h3>Кот Леопольд</h3><p>— Ребята, давайте жить дружно… и валерьянку в сыр.</p></div>
                    <div class="joke-card"><h3>Маша и Медведь</h3><p>— Она взломала Wi-Fi, съела клубнику. Требую депортации в «Смешарики».</p></div>
                    <div class="joke-card"><h3>Лунтик</h3><p>— Я с Луны. — Я из травы. Учительница: зачем мне это в пятницу?</p></div>
                    <div class="joke-card"><h3>Том и Джерри</h3><p>Подружились, получил пирог с динамитом: амбиции взорвались.</p></div>
                </div>
            </div>

            <div class="tab-content" id="content-students">
                <div class="joke-grid">
                    <div class="joke-card"><h3>Зачёт автоматом</h3><p>Преподаватель: «Кто ответит на вопрос — получит зачёт автоматом». Студент: «А можно автоматом, но без вопроса?»</p></div>
                    <div class="joke-card"><h3>Курсовая</h3><p>— А можно краткое содержание? — Можно. Я её скачал.</p></div>
                    <div class="joke-card"><h3>Физкультура</h3><p>— Почему прогулял физкультуру? — Поскользнулся на диване и подвернул пульт.</p></div>
                    <div class="joke-card"><h3>Дед Мороз</h3><p>Сдавшим хвосты до Нового года — стипендия. Остальным — оливье без майонеза.</p></div>
                    <div class="joke-card"><h3>Подготовка</h3><p>— Ты к экзамену готовишься? — Да, третий сериал пересматриваю. Нервы важнее знаний.</p></div>
                    <div class="joke-card"><h3>Столовая</h3><p>— Дайте рыбу, но без костей и чтобы пахла котлетой.</p></div>
                    <div class="joke-card"><h3>Римская империя</h3><p>— Три причины падения? — Первая: не учила матчасть, вторую списать забыл, третью не придумали.</p></div>
                    <div class="joke-card"><h3>Кипятильник</h3><p>— Сосед, у тебя кипятильник есть? — Нет. — Хочу согреть чай утюгом.</p></div>
                    <div class="joke-card"><h3>Поисковые системы</h3><p>— Вы знаете предмет? — Я знаю, где методичка. — Зачёт по поисковым системам.</p></div>
                    <div class="joke-card"><h3>Каникулы</h3><p>— Отдохнул? — Даже выспался. Теперь как быть зомби на парах.</p></div>
                </div>
            </div>

            <div class="tab-content" id="content-animals">
                <div class="joke-grid">
                    <div class="joke-card"><h3>Кризис</h3><p>— Мне корм с лососем. — А мне опять «Вискас», кризис, затянем ошейники.</p></div>
                    <div class="joke-card"><h3>Попугай</h3><p>— У попугая депрессия. — Он видел, как кот диск царапает.</p></div>
                    <div class="joke-card"><h3>Золотая рыбка</h3><p>— Хочу, чтобы жена не пилила. — Теперь у неё нет рта, зато бензопила.</p></div>
                    <div class="joke-card"><h3>Заяц в баре</h3><p>— Морковный сок. — Только пиво. — Тогда пиво из морковки. — Ячмень тоже из земли.</p></div>
                    <div class="joke-card"><h3>Собака и хвост</h3><p>— Пытаюсь укусить консультанта по счастью, он всё время сзади.</p></div>
                    <div class="joke-card"><h3>Хомяк-философ</h3><p>— Ты чего лежишь? — Вселенная и так крутится, зачем усугублять.</p></div>
                    <div class="joke-card"><h3>Медведь и навигатор</h3><p>— Поверните к берлоге. — Я на машине. — Выйдите и лягте. — Я на самокате. — Положите самокат.</p></div>
                    <div class="joke-card"><h3>Ёж и дикобраз</h3><p>— Привет, с иголочки! — Я на стиле. — У тебя иголок больше. — Так я модный!</p></div>
                    <div class="joke-card"><h3>Мотивация для рыбки</h3><p>Хозяин включил «В поисках Немо» — теперь у рыбки мотивация.</p></div>
                    <div class="joke-card"><h3>Попугай пирата</h3><p>— Кэп, почему у них попугаи не разговаривают? — Бюджет не резиновый!</p></div>
                </div>
            </div>

            <div class="tab-content" id="content-life">
                <div class="joke-grid">
                    <div class="joke-card"><h3>Весы</h3><p>58 кг с пакетом молока. Молоко — предатель!</p></div>
                    <div class="joke-card"><h3>Спорт</h3><p>Купил форму, лежу в ней на диване. Спорт — стиль жизни.</p></div>
                    <div class="joke-card"><h3>«Я подумаю»</h3><p>После слов сисадмина всё уже работает.</p></div>
                    <div class="joke-card"><h3>Экономика</h3><p>Съел курицу за 300 руб., считай заработал 300.</p></div>
                    <div class="joke-card"><h3>Отношения-лифт</h3><p>То вверх, то вниз, кнопка «стоп» не работает.</p></div>
                    <div class="joke-card"><h3>Полежать</h3><p>В 20 — угроза, в 35 — молитва.</p></div>
                    <div class="joke-card"><h3>Умные часы</h3><p>10 000 шагов, пока шашлык переворачивал.</p></div>
                    <div class="joke-card"><h3>Мультиварка</h3><p>— Может, достаточно соли? Или вы хотите морской аквариум?</p></div>
                    <div class="joke-card"><h3>Поздний сон</h3><p>Лёг в 22:00, в 2:30 знаю всё о гаечном ключе.</p></div>
                    <div class="joke-card"><h3>Возраст</h3><p>В 20 боишься что подумают, в 30 — налоговая, в 40 — давление.</p></div>
                </div>
            </div>

            <div class="tab-content" id="content-cartoons">
                <div class="joke-grid">
                    <div class="joke-card"><h3>Фитнес Зайца</h3><p>— Может, ну её, Олимпиаду? — Я не ради медалей, фитнес-браслет показывает 3000 калорий.</p></div>
                    <div class="joke-card"><h3>Шрек</h3><p>— Лук — метафора моей души. — Слои… Следующий!</p></div>
                    <div class="joke-card"><h3>Винни-Пух</h3><p>— Мёд не зависит от часовых поясов, в Австралии вечер.</p></div>
                    <div class="joke-card"><h3>Гомер на работе</h3><p>— Образование? — Смотрел «Как это работает». — Приняты на реактор.</p></div>
                    <div class="joke-card"><h3>Чебурашка</h3><p>Апельсины доставляем, даже если ящик с самолёта упал.</p></div>
                    <div class="joke-card"><h3>Карлсон</h3><p>— Варенье кончилось, назвали шаром с пропеллером. — Несу плюшки.</p></div>
                    <div class="joke-card"><h3>Кот Леопольд</h3><p>— Ребята, давайте жить дружно… и валерьянку в сыр.</p></div>
                    <div class="joke-card"><h3>Маша и Медведь</h3><p>— Она взломала Wi-Fi, съела клубнику. Требую депортации в «Смешарики».</p></div>
                    <div class="joke-card"><h3>Лунтик</h3><p>— Я с Луны. — Я из травы. Учительница: зачем мне это в пятницу?</p></div>
                    <div class="joke-card"><h3>Том и Джерри</h3><p>Подружились, получил пирог с динамитом: амбиции взорвались.</p></div>
                </div>
            </div>
        </div>
    </section>

    <section id="worst-joke">
        <div class="special-block">
            <h2>Худший анекдот дня</h2>
            <p style="font-size: 1.5rem;">«Почему он худший? Потому что забывает концовку».</p>
            <p><em>Редакция извиняется.</em></p>
        </div>
    </section>

    <section id="about">
        <h2>Почему смех продлевает жизнь</h2>
        <table>
            <tr><th>Фактор</th><th>Влияние</th><th>Обоснование</th></tr>
            <tr><td>Улыбка</td><td>Снижает кортизол</td><td>Мышцы обманывают мозг.</td></tr>
            <tr><td>Смех до слёз</td><td>Тренирует пресс</td><td>Минута хохота = 10 минут планки (почти).</td></tr>
            <tr><td>Хорошая шутка</td><td>Расширяет сосуды</td><td>Фраза «заходи, пообедаем» улучшает кровоток.</td></tr>
            <tr><td>Самоирония</td><td>Укрепляет иммунитет</td><td>Вирусы не выносят неловких ситуаций.</td></tr>
        </table>
        <p style="text-align: center;"><a href="#team" class="btn">Кто это сделал?</a></p>
    </section>

    <section id="team">
        <h2>Наша команда (11-й класс)</h2>
        <div style="display: flex; flex-wrap: wrap; gap: 20px;">
            <div class="joke-card" style="flex: 1; min-width: 220px; text-align: center;">
		<img src="C:\Users\Валерия\Desktop\сайт 28.04\liza.png">
                <h3>Сарачан Елизавета</h3>
                <p>📧 vi7358390@gmail.com<br>✈️ @EL06SPR</p>
            </div>
            <div class="joke-card" style="flex: 1; min-width: 220px; text-align: center;">
		<img src="C:\Users\Валерия\Desktop\сайт 28.04\lera.png">
                <h3>Сурикова Валерия</h3>
                <p>📧 71.valeria.viktoria.17@mail.ru<br>✈️ @vv_valerisu</p>
            </div>
        </div>
    </section>

    <section id="sitemap">
        <h2>Карта сайта</h2>
        <ol>
            <li>Главная</li>
            <li>Каталог (все анекдоты по вкладкам)</li>
            <li>Анекдот дня</li>
            <li>О проекте</li>
            <li>Команда</li>
            <li>Структура</li>
            <li>Любимый анекдот авторов (Страница 404)</li>
        </ol>
    </section>

    <section id="page404">
        <div class="special-block">
            <h2>Ошибка 404</h2>
            <p style="font-size: 1.5rem;">«Такого анекдота у нас нет. Зато есть кот в мешке!»</p>
            <a href="https://images.meme-arsenal.com/79c3abd3403c3ab89a957359b785536b.jpg" target="_blank" class="btn">Супер-пупер мега-анекдот (секретный)</a>
            <p style="margin-top: 10px;">Нажмите, если хотите увидеть то, чего нет</p>
        </div>
    </section>

    <section id="home">
        <h1>Добро пожаловать!</h1>
        <p><strong>Мы — ученицы 11Е класса, и это наш сайт. Аплодисменты в студию.</strong> Сайт работает на чистом HTML и CSS.</p>

        <form class="subscribe-form" action="#" method="get">
            <input type="email" placeholder="Ваш email для шуток" required>
            <button type="submit" class="btn">Подписаться</button>
        </form>

        <a href="#catalog" class="btn random-link">Смотреть случайный анекдот</a>

        <h2>🏆 Топ-5 месяца</h2>
        <table>
            <tr><th>Место</th><th>Анекдот</th><th>Оценка</th></tr>
            <tr><td>1</td><td>Студент учил билеты всю ночь, а экзамен был вчера.</td><td>★★★★★</td></tr>
            <tr><td>2</td><td>Кот заставляет человека работать, чтобы самому бездельничать.</td><td>★★★★★</td></tr>
            <tr><td>3</td><td>Понедельник — день, когда мозг опаздывает на работу.</td><td>★★★★☆</td></tr>
            <tr><td>4</td><td>Вовочка: «Это не альтернатива, это шантаж!»</td><td>★★★★☆</td></tr>
            <tr><td>5</td><td>Оптимист видит возможность, пессимист — трудность.</td><td>★★★☆☆</td></tr>
        </table>
    </section>
</main>

<footer>
    <p>© 2026 «Анекдотная». Шутите на здоровье!</p>
</footer>

</body>
</html>
