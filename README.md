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
        }
        .tree {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .level {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin: 20px 0;
            position: relative;
        }
        .person {
            padding: 15px 20px;
            border-radius: 10px;
            text-align: center;
            font-weight: bold;
            background-color: #f0f0f0;
            border: 2px solid black;
            min-width: 120px;
            box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.2);
            cursor: pointer;
            position: relative;
        }
        .children {
            display: none;
            flex-direction: column;
            align-items: center;
        }
        .connector {
            position: absolute;
            width: 2px;
            background: black;
        }
        .vertical-line {
            height: 20px;
            left: 50%;
            top: -20px;
        }
        .horizontal-line {
            width: 100%;
            height: 2px;
            background: black;
            position: absolute;
            top: 0;
        }
    </style>
</head>
<body>
    <h2>Менің Шежірем</h2>
    <div class="tree">
        <!-- Ата-әже -->
        <div class="level">
            <div class="person" onclick="toggleChildren('parents')">АТА (Қуаныш)</div>
            <div class="person" onclick="toggleChildren('parents')">ӘЖЕ (Айман)</div>
        </div>

        <!-- Әке-шеше -->
        <div id="parents" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kids')">ӘКЕ (Еркін)</div>
                <div class="person" onclick="toggleChildren('kids')">АНА (Гүлжан)</div>
            </div>
        </div>

        <!-- 5 бала -->
        <div id="kids" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kid1')">ҰЛ 1</div>
                <div class="person" onclick="toggleChildren('kid2')">ҰЛ 2</div>
                <div class="person" onclick="toggleChildren('kid3')">ҰЛ 3</div>
                <div class="person" onclick="toggleChildren('kid4')">ҰЛ 4</div>
                <div class="person" onclick="toggleChildren('kid5')">ҰЛ 5</div>
            </div>
        </div>
    </div>

    <script>
        function toggleChildren(id) {
            var element = document.getElementById(id);
            if (element.style.display === "none" || element.style.display === "") {
                element.style.display = "flex";
            } else {
                element.style.display = "none";
            }
        }
    </script>
</body>
</html>
