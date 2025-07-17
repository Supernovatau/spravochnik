# spravochnik<!DOCTYPE html>
<html lang="ru-RU">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Телефонный справочник ФКУ «ФЦПиЛО»</title>
    <style>
        :root {
            --primary-color: #8B4513; /* Коричневый */
            --secondary-color: #FAEBD7; /* Бежевый */
            --accent-color: #D2B48C; /* Тан */
            --text-color: #333;
            --light-text: #666;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        body {
            background-color: var(--secondary-color);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            color: var(--text-color);
            line-height: 1.6;
            background-image: linear-gradient(to bottom, rgba(255,255,255,0.8), rgba(250,235,215,0.8));
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            padding: 30px 0;
            background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
            color: white;
            border-radius: 10px;
            margin-bottom: 30px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            animation: fadeIn 0.8s ease-out;
        }
        
        h1 {
            font-size: 2.2em;
            margin: 0;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
        }
        
        .subtitle {
            font-style: italic;
            opacity: 0.9;
            margin-top: 10px;
        }
        
        .department-selector {
            margin: 30px auto;
            text-align: center;
            animation: fadeIn 1s ease-out 0.2s both;
        }
        
        select {
            padding: 12px 25px;
            font-size: 1.1em;
            border: 2px solid var(--primary-color);
            border-radius: 50px;
            background-color: white;
            width: 80%;
            max-width: 500px;
            appearance: none;
            background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%238B4513'%3e%3cpath d='M7 10l5 5 5-5z'/%3e%3c/svg%3e");
            background-repeat: no-repeat;
            background-position: right 15px center;
            background-size: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        select:hover {
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            transform: translateY(-2px);
        }
        
        select:focus {
            outline: none;
            border-color: var(--accent-color);
            box-shadow: 0 0 0 3px rgba(210,180,140,0.4);
        }
        
        .department-section {
            display: none;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            padding: 25px;
            margin: 30px auto;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s ease-out;
            border-left: 5px solid var(--primary-color);
        }
        
        .department-section.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
            animation: fadeIn 0.6s ease-out;
        }
        
        .department-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px dashed var(--accent-color);
        }
        
        .department-title {
            color: var(--primary-color);
            margin: 0;
            font-size: 1.8em;
        }
        
        .back-to-top {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s ease;
        }
        
        .back-to-top:hover {
            background-color: var(--accent-color);
            transform: translateY(-2px);
        }
        
        table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0;
            font-size: 1em;
            margin-top: 20px;
            border-radius: 8px;
            overflow: hidden;
        }
        
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background-color: var(--primary-color);
            color: white;
            font-weight: 600;
            position: sticky;
            top: 0;
        }
        
        tr:nth-child(even) {
            background-color: rgba(250,235,215,0.3);
        }
        
        tr:hover {
            background-color: rgba(210,180,140,0.2);
            transition: background-color 0.2s ease;
        }
        
        a {
            color: var(--primary-color);
            text-decoration: none;
            transition: color 0.2s ease;
            font-weight: 500;
        }
        
        a:hover {
            color: #5D2906;
            text-decoration: underline;
        }
        
        .phone-link {
            white-space: nowrap;
        }
        
        footer {
            text-align: center;
            margin-top: 50px;
            padding: 20px;
            color: var(--light-text);
            font-size: 0.9em;
        }
        
        .floating-button {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background-color: var(--primary-color);
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            opacity: 0;
            visibility: hidden;
            z-index: 100;
        }
        
        .floating-button.visible {
            opacity: 1;
            visibility: visible;
        }
        
        .floating-button:hover {
            background-color: var(--accent-color);
            transform: translateY(-3px) scale(1.1);
            animation: pulse 1.5s infinite;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            select {
                width: 90%;
                padding: 10px 20px;
            }
            
            th, td {
                padding: 10px 5px;
                font-size: 0.9em;
            }
            
            .department-title {
                font-size: 1.4em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Телефонный справочник</h1>
            <div class="subtitle">ФКУ «ФЦПиЛО»</div>
        </header>
        
        <div class="department-selector">
            <select id="departmentSelect">
                <option value="">-- Выберите отдел --</option>
                <option value="admin">Административный отдел</option>
                <option value="analytics">Информационно-аналитический отдел</option>
                <option value="planning">Отдел контроля исполнения государственных контрактов</option>
                <option value="control">Отдел планирования и организации закупок</option>
                <option value="contracts">Отдел размещения государственных заказов и заключения контрактов</option>
                <option value="legal">Юридический отдел</option>
                <option value="economic">Планово-экономический отдел</option>
                <option value="it">Отдел информатизации и информационной безопасности</option>
                <option value="hr">Общий отдел — кадровая служба</option>
                <option value="household">Административно-хозяйственный отдел</option>
                <option value="accounting">Отдел бухгалтерского учета</option>
                <option value="medical">Отдел закупок медицинской продукции</option>
                <option value="security">Отдел защиты государственной тайны, гражданской обороны и чрезвычайных ситуаций</option>
            </select>
        </div>
        
        <!-- Административный отдел -->
        <div id="admin" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Административный отдел</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>Директор</td><td>Максимкина Елена Анатольевна</td><td>1000</td><td><nobr>+7 991 581 53 88</td><td></nobr><a href="mailto:MaksimkinaEA@minzdrav.gov.ru">MaksimkinaEA@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Референт</td><td>Титаренко Ирина Александровна</td><td>1001</td><td><nobr>   -   </td><td></nobr><a href="mailto:TitarenkoIA@minzdrav.gov.ru">TitarenkoIA@minzdrav.gov.ru</a> <br><a href="mailto:fcpilo.info@minzdrav.gov.ru">fcpilo.info@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Помощник директора</td><td>Логинова Евдокия Максимовна</td><td>1001</td><td><nobr>  -  </td><td></nobr><a href="mailto:LoginovaEM@minzdrav.gov.ru">LoginovaEM@minzdrav.gov.ru</a> <br><a href="mailto:fcpilo.info@minzdrav.gov.ru">fcpilo.info@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Заместитель директора</td><td>Кортошкина Надежда Вячеславовна</td><td>1002</td><td><nobr>+7(991)581-53-89</td><td></nobr><a href="mailto:KortoshkinaNV@minzdrav.gov.ru">KortoshkinaNV@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Заместитель директора</td><td>Кожевникова Ольга Владимировна</td><td>1003</td><td><nobr>+7(991)581-53-83</td><td></nobr><a href="mailto:KozhevnikovaOV@minzdrav.gov.ru">KozhevnikovaOV@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Заместитель директора</td><td>Константинова Ольга Анатольевна</td><td>1004</td><td><nobr>+7(991)581-53-90</td><td></nobr><a href="mailto:KonstantinovaOA@minzdrav.gov.ru">KonstantinovaOA@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Заместитель директора</td><td>Яшкина Анна Святославовна</td><td>1005</td><td><nobr>+7(991)581-53-80</td><td></nobr><a href="mailto:YashkinaAS@minzdrav.gov.ru">YashkinaAS@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Советник административного отдела</td><td>Курносенко Ирина Леонидовна</td><td>1006</td><td><nobr> - </td><td></nobr><a href="mailto:KurnosenkoIL@minzdrav.gov.ru">KurnosenkoIL@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Референт</td><td>Касютина Олеся Леонтьевна</td><td>1007</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:KasyutinaOL@minzdrav.gov.ru">KasyutinaOL@minzdrav.gov.ru </a><br><a href="mailto:fcpilo.info@minzdrav.gov.ru">fcpilo.info@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Советник административного отдела</td><td>Тимохин Сергей Иванович</td><td>1008</td><td><nobr> - </td><td></nobr><a href="mailto:TimokhinSI@minzdrav.gov.ru">TimokhinSI@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Отдел планирования и организации закупок -->
        <div id="control" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел планирования и организации закупок</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Кременица Людмила Николаевна.</td><td>1020</td><td><nobr>+7 991 581 53 95</td><td></nobr><a href="mailto:KremenicaLN@minzdrav.gov.ru">KremenicaLN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Павельев Андрей Борисович</td><td>1021</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:PavelevAB@minzdrav.gov.ru">PavelevAB@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Майер Валерия Игоревна</td><td>1022</td><td><nobr>+7 901 587 40 76</td><td></nobr><a href="mailto:MayerVI@minzdrav.gov.ru">MayerVI@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Радина Карина Валерьевна</td><td>---</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:RadinaKV@minzdrav.gov.ru">RadinaKV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Гончарова Ирина Александровна</td><td>1027</td><td><nobr>+7 901 587 39 21</td><td></nobr><a href="mailto:GoncharovaIA@minzdrav.gov.ru">GoncharovaIA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Иванова Елена Юрьевна</td><td>1028</td><td><nobr>+7 991 581 53 99</td><td></nobr><a href="mailto:IvanovaEY@minzdrav.gov.ru">IvanovaEY@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Энгельгардт Инна Алексеевна</td><td>1023</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:EngelgardtIA@minzdrav.gov.ru">EngelgardtIA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Микитянская Яна Витальевна </td><td>1025</td><td><nobr>+7(495) 249-03-01</td><td></nobr><a href="mailto:MikityanskayaYV@minzdrav.gov.ru">MikityanskayaYV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Тукмакова Вероника Наумовна</td><td>1029</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:TukmakovaVN@minzdrav.gov.ru">TukmakovaVN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Калуга Александр Игоревич </td><td>1024</td><td><nobr>+7(495) 249-03-01</td><td></nobr><a href="mailto:KalugaAI@minzdrav.gov.ru">KalugaAI@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Сорокина Юлия Михайловна </td><td>1026</td><td><nobr>+7(495) 249-03-01</td><td></nobr><a href="mailto:SorokinaIuM@minzdrav.gov.ru">SorokinaIuM@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Лаурсон Светлана Владимировна   </td><td>1121</td><td><nobr>+7(495) 249-03-01</td><td></nobr><a href="mailto:LaursonSV@minzdrav.gov.ru">LaursonSV@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!--Отдел контроля исполнения государственных контрактов -->
        <div id="planning" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел контроля исполнения государственных контрактов</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Скорнякова Ольга Сергеевна</td><td>1030</td><td><nobr>+7 (991) 581-53-79</td><td></nobr><a href="mailto:SkornyakovaOS@minzdrav.gov.ru">SkornyakovaOS@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Фетисова Наталья Владимировна</td><td>1031</td><td><nobr>+7 991 581 53 78</td><td></nobr><a href="mailto:FetisovaNV@minzdrav.gov.ru">FetisovaNV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Ломовцева Ольга Николаевна</td><td>1032</td><td><nobr>+7(991) 581-53-96</td><td></nobr><a href="mailto:LomovtcevaON@minzdrav.gov.ru">LomovtcevaON@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Помазан Валентина Евгеньевна</td><td>1033</td><td><nobr>+7 977 354 24 56</td><td></nobr><a href="mailto:PomazanVE@minzdrav.gov.ru">PomazanVE@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Богушевич Светлана Николаевна</td><td>1035</td><td><nobr>+7 991 581 53 94</td><td></nobr><a href="mailto:BogushevichSN@minzdrav.gov.ru">BogushevichSN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Ладыгина Инна Петровна</td><td>1036</td><td><nobr>+7 977 322 13 46</td><td></nobr><a href="mailto:LadiginaIP@minzdrav.gov.ru">LadiginaIP@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Савостикова Елена Игоревна</td><td>1037</td><td><nobr>+7 901 587 38 05</td><td></nobr><a href="mailto:SavostikovaEI@minzdrav.gov.ru">SavostikovaEI@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Ковшер Елена Николаевна</td><td>1038</td><td><nobr>1038</td><td></nobr><a href="mailto:KovsherEN@minzdrav.gov.ru">KovsherEN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Зайцева Мария Николаевна</td><td>1034</td><td><nobr>+7 991 581 53 82</td><td></nobr><a href="mailto:ZaitsevaMN@minzdrav.gov.ru">ZaitsevaMN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Алехина Александра Сергеевна</td><td>1132</td><td><nobr>1132</td><td></nobr><a href="mailto:AlekhinaAS@minzdrav.gov.ru">AlekhinaAS@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Пчелкина Мария Николаевна</td><td>1039</td><td><nobr>1039</td><td></nobr><a href="mailto:PchelkinaMN@minzdrav.gov.ru">PchelkinaMN@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
        
		<!-- Информационно-аналитический отдел -->
        <div id="analytics" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Информационно-аналитический отдел</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><td>Начальник отдела</td><td>Мирошников Антон Вячеславович</td><td>1100</td><td><nobr>+7(991)581-53-86</td><td></nobr><a href="mailto:MiroshnikovAV@minzdrav.gov.ru">MiroshnikovAV@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Заместитель начальника отдела</td><td>Северин Станислав Риммович</td><td>1101</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:SeverinSR@minzdrav.gov.ru">SeverinSR@minzdrav.gov.ru</a></td></tr>
			        <tr><td>Главный специалист</td><td>Нечаева Дарья Геннадьевна</td><td>1105</td><td><nobr>+7 991 626 75 46</td><td></nobr><a href="mailto:NechaevaDG@minzdrav.gov.ru">NechaevaDG@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Отдел размещения государственных заказов и заключения контрактов -->
        <div id="contracts" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел размещения государственных заказов и заключения контрактов</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Дуганова Алёна Андреевна</td><td>1040</td><td><nobr>+7 991 635 69 65</td><td></nobr><a href="mailto:DuganovaAA@minzdrav.gov.ru">DuganovaAA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Латышева Ирина Сергеевна</td><td>1041</td><td><nobr>+7(991) 581-53-93</td><td></nobr><a href="mailto:LatyshevaIS@minzdrav.gov.ru">LatyshevaIS@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Титаренко Виктория Александровна</td><td>1042</td><td><nobr>+7 977 321 27 83</td><td></nobr><a href="mailto:TitarenkoVA@minzdrav.gov.ru">TitarenkoVA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Иноземцев Максим Витальевич</td><td>1049</td><td><nobr></td><td></nobr><a href="mailto:InozemcevMV@minzdrav.gov.ru">InozemcevMV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Тарабухина Инна Владимировна</td><td>1045</td><td><nobr>+7 991 626 75 60</td><td></nobr><a href="mailto:TarabuhinaIV@minzdrav.gov.ru">TarabuhinaIV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Кожевников Сергей Владимирович</td><td>1047</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:KozhevnikovSV@minzdrav.gov.ru">KozhevnikovSV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Головкина Надежда Сергеевна</td><td>1043</td><td><nobr>+7 991 581 53 97</td><td></nobr><a href="mailto:GolovkinaNS@minzdrav.gov.ru">GolovkinaNS@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист</td><td>Мазурова Кира Николаевна</td><td>1048</td><td><nobr>--</td><td></nobr><a href="mailto:MazurovaKN@minzdrav.gov.ru">MazurovaKN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Курилкина Татьяна Александровна</td><td>1044</td><td><nobr>+7 901 587 40 45</td><td></nobr><a href="mailto:KurilkinaTA@minzdrav.gov.ru">KurilkinaTA@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Юридический отдел -->
        <div id="legal" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Юридический отдел</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Заместитель начальника отдела</td><td>Кузьмин Роман Михайлович</td><td>1051</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:KuzminRM@minzdrav.gov.ru">KuzminRM@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Абанин Никита Сергеевич</td><td>1053</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:AbaninNS@minzdrav.gov.ru">AbaninNS@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Борисова Вера Алексеевна</td><td>1054</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:BorisovaVA@minzdrav.gov.ru">BorisovaVA@minzdrav.gov.ru</a></td></tr>	
			<tr><td>Менеджер по юридическому сопровождению</td><td>Волкова Екатерина Михайловна</td><td>1055</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:VolkovaEM@minzdrav.gov.ru">VolkovaEM@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Нестерова Ирина Юрьевна</td><td>1055</td><td><nobr>1052</td><td></nobr><a href="mailto:NesterovaIYU@minzdrav.gov.ru">NesterovaIYU@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Планово-экономический отдел -->
        <div id="economic" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Планово-экономический отдел</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Жукова Маргарита Рустемовна</td><td>1060</td><td><nobr>+7 991 581 53 84</td><td></nobr><a href="mailto:ZhukovaMR@minzdrav.gov.ru">ZhukovaMR@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Бахарева Ольга Николаевна</td><td>1061</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:BakharevaON@minzdrav.gov.ru">BakharevaON@minzdrav.gov.ru</a></td></tr>
			<tr><td>Финансовый аналитик</td><td>Гладкова Евгения Дмитриевна</td><td>1062</td><td><nobr></td><td></nobr><a href="mailto:GladkovaED@minzdrav.gov.ru">GladkovaED@minzdrav.gov.ru</a></td></tr>
			<tr><td>Финансовый аналитик</td><td>Малахова Елена Валерьевна</td><td>1063</td><td><nobr>+7 991 635 69 52</td><td></nobr><a href="mailto:MalakhovaEV@minzdrav.gov.ru">MalakhovaEV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Экономист-аналитик</td><td>Павлов Вадим Владимирович</td><td>1064</td><td><nobr>+7 991 635 69 58</td><td></nobr><a href="mailto:PavlovVV@minzdrav.gov.ru">PavlovVV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Экономист-аналитик</td><td>Соколова Антонина Ивановна</td><td>1065</td><td><nobr>+7 991 626 75 53</td><td></nobr><a href="mailto:SokolovaAI@minzdrav.gov.ru">SokolovaAI@minzdrav.gov.ru</a></td></tr>
			<tr><td>Финансовый аналитик</td><td>Александрова Екатерина Александровна</td><td>1066</td><td><nobr>+7 991 626 75 54</td><td></nobr><a href="mailto:AleksandrovaEA@minzdrav.gov.ru">AleksandrovaEA@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Отдел информатизации и информационной безопасности -->
        <div id="it" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел информатизации и информационной безопасности</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Ступаков Василий Владимирович</td><td>1070</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:StupakovVV@minzdrav.gov.ru">StupakovVV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Селютин Денис Юрьевич</td><td>1071</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:SelyutinDY@minzdrav.gov.ru">SelyutinDY@minzdrav.gov.ru</a></td></tr>
			<tr><td>Главный специалист</td><td>Туляков Артём Игоревич</td><td>1072</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:TulyakovAI@minzdrav.gov.ru">TulyakovAI@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Общий отдел — кадровая служба -->
        <div id="hr" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Общий отдел — кадровая служба</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Ефремова Ольга Александровна</td><td>1080</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:EfremovaOA@minzdrav.gov.ru">EfremovaOA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Шилов Виктор Николаевич</td><td>1081</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:ShilovVN@minzdrav.gov.ru">ShilovVN@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Саушкина Светлана Егоровна</td><td>1083</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:SaushkinaSE@minzdrav.gov.ru">SaushkinaSE@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Новоселова Елена Вячеславовна</td><td>1084</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:NovoselovaEV@minzdrav.gov.ru">NovoselovaEV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Ведущий специалист</td><td>Воробьева Марина Михайловна</td><td>1082</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:VorobevaMM@minzdrav.gov.ru">VorobevaMM@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Административно-хозяйственный отдел -->
        <div id="household" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Административно-хозяйственный отдел</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела</td><td>Чебуров Сергей Александрович</td><td>1090</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:CheburovSA@minzdrav.gov.ru">CheburovSA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Гульшин Роман Борисович</td><td>1091</td><td><nobr>+7 901 587 39 63</td><td></nobr><a href="mailto:GulshinRB@minzdrav.gov.ru">GulshinRB@minzdrav.gov.ru</a></td></tr>
			<tr><td>Специалист по пожарной безопасности</td><td>Бланк Игорь Вячеславович</td><td>1093</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:BlankIV@minzdrav.gov.ru">BlankIV@minzdrav.gov.ru</a></td></tr>
			<tr><td>оператор по обслуживанию имущества</td><td>Шовкопляс Александр Владимирович</td><td></td><td></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Отдел бухгалтерского учета -->
        <div id="accounting" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел бухгалтерского учета</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			<tr><td>Начальник отдела бухгалтерского учета-главный бухгалтер</td><td>Яковлева Виктория Павловна</td><td>1010</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:YakovlevaVP@minzdrav.gov.ru">YakovlevaVP@minzdrav.gov.ru</a></td></tr>
			<tr><td>Заместитель начальника отдела</td><td>Колесникова Вера Валерьевна</td><td>1012</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:KolesnikovaVV@minzdrav.gov.ru">KolesnikovaVV@minzdrav.gov.ru</a></td></tr>
			<tr><td>Бухгалтер-эксперт</td><td>Ступакова Галина Сергеевна</td><td>1011</td><td><nobr>+7 901 587 40 15</td><td></nobr><a href="mailto:StupakovaGS@minzdrav.gov.ru">StupakovaGS@minzdrav.gov.ru</a></td></tr>
			<tr><td>Бухгалтер-эксперт</td><td>Яромчук Станислав Юрьевич</td><td>1013</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:YaromchukSY@minzdrav.gov.ru">YaromchukSY@minzdrav.gov.ru</a></td></tr>
			<tr><td>Бухгалтер-эксперт</td><td>Красикова Дария Алексеевна</td><td>1015</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:KrasikovaDA@minzdrav.gov.ru">KrasikovaDA@minzdrav.gov.ru</a></td></tr>
			<tr><td>Бухгалтер по учету ОС и ТМЦ</td><td>Казарцева Антонина Ивановна</td><td>1014</td><td><nobr>+7(495)249-03-01</td><td></nobr><a href="mailto:KazartsevaAI@minzdrav.gov.ru">KazartsevaAI@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		
		<!-- Отдел закупок медицинской продукции -->
        <div id="medical" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел закупок медицинской продукции</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
				<tr><td>Начальник отдела</td><td>Дембицкая Татьяна Алексеевна</td><td>1200</td><td><nobr>+7(991) 581-53-77</td><td></nobr><a href="mailto:DembitskayaTA@minzdrav.gov.ru">DembitskayaTA@minzdrav.gov.ru</a></td></tr>
				<tr><td>Заместитель начальника отдела</td><td>Зуйкина Ксения Вячеславовна</td><td>1201</td><td><nobr>+7(901)587-38-71</td><td></nobr><a href="mailto:ZuykinaKV@minzdrav.gov.ru">ZuykinaKV@minzdrav.gov.ru</a></td></tr>
				<tr><td>Главный специалист</td><td>Полищук Елена Юрьевна</td><td>1202</td><td><nobr>+7 (901) 587-39-74</td><td></nobr><a href="mailto:PolischukEY@minzdrav.gov.ru">PolischukEY@minzdrav.gov.ru</a></td></tr>
				<tr><td>Ведущий специалист</td><td>Фролов Дмитрий Сергеевич</td><td>1203</td><td><nobr>+7(991)626-75-45</td><td></nobr><a href="mailto:FrolovDS@minzdrav.gov.ru">FrolovDS@minzdrav.gov.ru</a></td></tr>
				<tr><td>Ведущий специалист</td><td>Бабаян Андроник Романович</td><td>1204</td><td><nobr>+7(991) 581-53-85</td><td></nobr><a href="mailto:BabaianAR@minzdrav.gov.ru">BabaianAR@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
		<!-- Отдел защиты государственной тайны, гражданской обороны и чрезвычайных ситуаций -->
        <div id="security" class="department-section">
            <div class="department-header">
                <h2 class="department-title">Отдел защиты государственной тайны, гражданской обороны и чрезвычайных ситуаций</h2>
                <button class="back-to-top">Наверх ↑</button>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Должность</th>
                        <th>ФИО</th>
                        <th>Добавочный номер</th>
                        <th>Моб.телефон</th>
                        <th>e-mail</th>
                    </tr>
                </thead>
                <tbody>
			    <tr><td>Начальник отдела</td><td>Побожей Роман Васильевич</td><td>1300</td><td><nobr>+7 991 626 75 59</td><td></nobr><a href="mailto:PobozheiRV@minzdrav.gov.ru">PobozheiRV@minzdrav.gov.ru</a></td></tr>
				<tr><td>Специалист по вопросам ГОиЧС</td><td>Сидоров Дмитрий Юрьевич</td><td>1301</td><td><nobr>+8(495) 249-03-01</td><td></nobr><a href="mailto:SidorovDIU@minzdrav.gov.ru">SidorovDIU@minzdrav.gov.ru</a></td></tr>
                </tbody>
            </table>
        </div>
        <!-- Остальные отделы (аналогичная структура) -->
        
        <footer>
            <p>© ФКУ «ФЦПиЛО» • Актуально на <span id="current-date"></span></p>
        </footer>
    </div>
    
    <div class="floating-button" id="scrollToTop">↑</div>
    
    <script>
        // Показать выбранный отдел
        function showDepartment() {
            const selectedValue = document.getElementById('departmentSelect').value;
            const departments = document.querySelectorAll('.department-section');
            
            departments.forEach(dept => {
                dept.classList.remove('active');
                if (dept.id === selectedValue) {
                    dept.classList.add('active');
                    
                    // Плавная прокрутка к выбранному отделу
                    setTimeout(() => {
                        dept.scrollIntoView({ behavior: 'smooth', block: 'start' });
                    }, 300);
                }
            });
            
            // Показать кнопку "Наверх" если выбран отдел
            toggleScrollToTopButton();
        }
        
        // Инициализация выпадающего списка
        document.getElementById('departmentSelect').addEventListener('change', showDepartment);
        
        // Показать первый отдел по умолчанию
        document.addEventListener('DOMContentLoaded', function() {
            // Установка текущей даты
            const options = { year: 'numeric', month: 'long', day: 'numeric' };
            document.getElementById('current-date').textContent = new Date().toLocaleDateString('ru-RU', options);
            
            // Показать первый отдел
            document.getElementById('admin').classList.add('active');
            
            // Инициализация кнопок "Наверх" в отделах
            document.querySelectorAll('.back-to-top').forEach(btn => {
                btn.addEventListener('click', () => {
                    window.scrollTo({
                        top: 0,
                        behavior: 'smooth'
                    });
                });
            });
        });
        
        // Кнопка плавающая "Наверх"
        const scrollToTopButton = document.getElementById('scrollToTop');
        
        function toggleScrollToTopButton() {
            if (window.pageYOffset > 300) {
                scrollToTopButton.classList.add('visible');
            } else {
                scrollToTopButton.classList.remove('visible');
            }
        }
        
        window.addEventListener('scroll', toggleScrollToTopButton);
        
        scrollToTopButton.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });
        
        // Анимация при наведении на строки таблицы
        document.querySelectorAll('tr').forEach(row => {
            row.addEventListener('mouseenter', function() {
                this.style.transform = 'scale(1.01)';
                this.style.boxShadow = '0 2px 8px rgba(0,0,0,0.1)';
            });
            
            row.addEventListener('mouseleave', function() {
                this.style.transform = 'scale(1)';
                this.style.boxShadow = 'none';
            });
        });
    </script>
</body>
</html>
