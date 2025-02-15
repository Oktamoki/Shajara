<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шежіре</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
        }
        .tree {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .branch {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 20px;
            position: relative;
        }
        .box {
            border: 2px solid #333;
            padding: 10px;
            margin: 10px;
            background-color: white;
            cursor: pointer;
            display: inline-block;
            width: 150px;
            text-align: center;
            position: relative;
        }
        .hidden {
            display: none;
        }
        .line {
            position: absolute;
            width: 2px;
            background-color: black;
        }
    </style>
</head>
<body>
    <div class="tree">
        <div class="box" onclick="toggleVisibility('parent')">Ахмаджон Махбуба</div>
        <div id="parent" class="branch hidden">
            <div class="box" onclick="toggleVisibility('Abdukadir')">уғли Абдукодир Ирисой</div>
            <div class="box" onclick="toggleVisibility('Abdumazhit')">уғли Абдумажит Салима</div>
            <div class="box" onclick="toggleVisibility('mother2')">қизи Арапат Мухтар</div>
            <div class="box" onclick="toggleVisibility('father')">уғли Абдуманнап Парахат</div>
            <div class="box" onclick="toggleVisibility('mother1')">қизи Хикоят Акмал</div>
            <div class="box" onclick="toggleVisibility('mother2')">қизи Мапрат Мирзахмат</div>
        </div>
        <div id="Abdukadir" class="branch hidden">
            <div class="box" onclick="toggleVisibility('child1')">уғли Султанмурот Шахло</div>
            <div class="box" onclick="toggleVisibility('child2')">қизи Тошбуви Мурот</div>
            <div class="box" onclick="toggleVisibility('child3')">қизи Дурбуви Тулкин</div>
            <div class="box" onclick="toggleVisibility('child4')">қизи Холисхон Фарход</div>
            <div class="box" onclick="toggleVisibility('child5')">қизи Ирода Сарвар</div>
            <div class="box" onclick="toggleVisibility('child6')">қизи Зарифа Камол</div>
            <div class="box" onclick="toggleVisibility('child6')">қизи Юлдуз Динмухаммад</div>
        </div>
         <div id="Abdumazhit" class="branch hidden">
        <div class="box" onclick="toggleVisibility('child1')">уғли Фуркат Нигора</div>
            <div class="box" onclick="toggleVisibility('child2')">уғли Гайрат Дилфуза</div>
            <div class="box" onclick="toggleVisibility('child3')">уғли Уткир Шахло</div>
            <div class="box" onclick="toggleVisibility('child4')">уғли Октам Феруза</div>
            <div class="box" onclick="toggleVisibility('child5')">уғли Учкун Дилобар</div>
         </div>
    </div>

    <script>
        function toggleVisibility(id) {
            var element = document.getElementById(id);
            if (element) {
                element.classList.toggle('hidden');
            }
        }
    </script>
</body>
</html>
