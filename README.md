<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AGROINTELLECT</title>
    <style>
        /* Основные стили для оформления */
        body {
            font-family: Arial, sans-serif;
            background-color: #d0ebff; /* Голубой фон */
            color: #333;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }

        .calculator-container {
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
            padding: 15px;
            width: 100%;
            max-width: 800px;
        }

        h2 {
            color: #0077cc;
            text-align: center;
            margin-bottom: 15px;
            font-size: 1.8em;
        }

        .option-group {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 8px 0;
            background-color: #e7f3ff;
            border-radius: 12px;
            margin: 8px 0;
            padding: 15px;
            box-sizing: border-box;
        }

        .option-group label {
            font-weight: bold;
            color: #0077cc;
            font-size: 1em;
            flex: 1;
        }

        select, input[type="number"] {
            font-size: 1em;
            padding: 6px 10px;
            border-radius: 8px;
            border: 1px solid #ccc;
            outline: none;
            width: 60%;
            max-width: 250px;
            box-sizing: border-box;
        }

        .input-group {
            margin-top: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #f0f0f0; /* Серый фон */
            border-radius: 12px;
            padding: 15px;
            border: 1px solid #ccc;
        }

        .input-group label {
            font-weight: bold;
            color: #0077cc;
            font-size: 1em;
        }

        .total-price {
            font-size: 1.2em;
            font-weight: bold;
            color: black; /* Черный цвет для текста "Итоговая цена" */
            text-align: center;
            margin-top: 15px;
            background-color: #e7f3ff;
            padding: 15px;
            border-radius: 12px;
            max-width: 400px; /* Укороченная рамка */
            margin-left: auto;
            margin-right: auto;
        }

        .total-price span {
            color: #28a745; /* Зеленый цвет для суммы */
        }

        /* Стили для больших чекбоксов */
        .checkbox-custom {
            width: 25px;
            height: 25px;
            appearance: none;
            background-color: #e0e0e0;
            border-radius: 8px;
            position: relative;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .checkbox-custom:checked {
            background-color: #33cc99;
        }

        .checkbox-custom:checked::before {
            content: '✔';
            font-size: 1.2em;
            color: white;
            position: absolute;
            top: -2px;
            left: 4px;
        }

        /* Обязательные модули */
        .required::after {
            content: " (обязательно)";
            color: red;
            font-weight: normal;
            font-size: 0.9em;
        }
    </style>
</head>
<body>

<div class="calculator-container">
    <h2>AGROINTELLECT</h2>
    
    <!-- Выбор поголовья -->
    <div class="input-group">
        <label for="herd-size">Выберите поголовье:</label>
        <select id="herd-size" onchange="calculateTotal()">
            <option value="100">100 и менее</option>
            <option value="100-500">100-500</option>
            <option value="500-1000">500-1000</option>
            <option value="1000-1800">1000-1800</option>
            <option value="1800+">1800 и более</option>
        </select>
    </div>

    <!-- Количество ферм -->
    <div class="input-group">
        <label for="farm-count">Количество ферм:</label>
        <input type="number" id="farm-count" value="1" min="1" onchange="calculateTotal()" />
    </div>

    <!-- Модули для выбора -->
    <div class="option-group">
        <label class="required">Учет поголовья</label>
        <input type="checkbox" id="cattle-management" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Учет молока</label>
        <input type="checkbox" id="milk-tracking" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Учет стада (Мусофт)</label>
        <input type="checkbox" id="herd-management" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Воспроизводство (зоотехния)</label>
        <input type="checkbox" id="reproduction" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Лечение и профилактика (ветеринария)</label>
        <input type="checkbox" id="treatment" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Интеграция с доильным оборудованием</label>
        <input type="checkbox" id="milking-integration" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label class="required">Веб-интерфейс + ТГ-уведомления</label>
        <input type="checkbox" id="web-tg-notifications" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Управленческий учет (Агроинтеллект)</label>
        <input type="checkbox" id="management-accounting" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Воспроизводство (Отчеты, Excel и уведомления)</label>
        <input type="checkbox" id="reproduction-reports" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Кормление (отчеты по деталям кормления)</label>
        <input type="checkbox" id="feeding-reports" class="checkbox-custom" onchange="calculateTotal()">
    </div>
    <div class="option-group">
        <label>Лечение (отчеты по расчистке копыт и маститу)</label>
        <input type="checkbox" id="hoof-treatment-reports" class="checkbox-custom" onchange="calculateTotal()">
    </div>

    <!-- Итоговая цена -->
    <div class="total-price">
        Итоговая цена: <span id="total-price">0</span> руб./мес.
    </div>
</div>

<script>
    const prices = {
        "100": { "milk": 500, "herd": 5000, "cattle": 2000, "reproduction": 1500, "treatment": 1500, "integration": 0, "management": 6000, "webTG": 4000, "reproductionReports": 1000, "feedingReports": 500, "hoofTreatment": 500 },
        "100-500": { "milk": 1000, "herd": 12000, "cattle": 4000, "reproduction": 2500, "treatment": 2500, "integration": 3000, "management": 12000, "webTG": 7000, "reproductionReports": 2000, "feedingReports": 1500, "hoofTreatment": 1000 },
        "500-1000": { "milk": 1500, "herd": 18000, "cattle": 6000, "reproduction": 4500, "treatment": 4500, "integration": 3000, "management": 18000, "webTG": 9000, "reproductionReports": 4000, "feedingReports": 2000, "hoofTreatment": 2000 },
        "1000-1800": { "milk": 2000, "herd": 25000, "cattle": 8000, "reproduction": 6500, "treatment": 6500, "integration": 3000, "management": 26000, "webTG": 13000, "reproductionReports": 6000, "feedingReports": 4000, "hoofTreatment": 3000 },
        "1800+": { "milk": 2500, "herd": 30000, "cattle": 10000, "reproduction": 8500, "treatment": 8500, "integration": 3000, "management": 33000, "webTG": 16000, "reproductionReports": 8000, "feedingReports": 5000, "hoofTreatment": 4000 }
    };

    function calculateTotal() {
        const herdSize = document.getElementById("herd-size").value;
        const farmCount = parseInt(document.getElementById("farm-count").value) || 1;
        let total = 0;

        if (document.getElementById("milk-tracking").checked) total += prices[herdSize].milk;
        if (document.getElementById("herd-management").checked) total += prices[herdSize].herd;
        if (document.getElementById("cattle-management").checked) total += prices[herdSize].cattle;
        if (document.getElementById("reproduction").checked) total += prices[herdSize].reproduction;
        if (document.getElementById("treatment").checked) total += prices[herdSize].treatment;
        if (document.getElementById("milking-integration").checked) total += prices[herdSize].integration;
        if (document.getElementById("management-accounting").checked) total += prices[herdSize].management;
        if (document.getElementById("web-tg-notifications").checked) total += prices[herdSize].webTG;
        if (document.getElementById("reproduction-reports").checked) total += prices[herdSize].reproductionReports;
        if (document.getElementById("feeding-reports").checked) total += prices[herdSize].feedingReports;
        if (document.getElementById("hoof-treatment-reports").checked) total += prices[herdSize].hoofTreatment;

        total *= farmCount;
        document.getElementById("total-price").textContent = total;
    }
</script>

</body>
</html>
