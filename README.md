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
            gap: 20px;
            margin: 20px 0;
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
        }
        .children {
            display: none;
        }
        .connector {
            width: 2px;
            height: 20px;
            background: black;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <h2>Менің Шежірем</h2>
    <div class="tree">
        <!-- Атасы мен әжесі -->
        <div class="level">
            <div class="person" onclick="toggleChildren('parents')">АТА (Қуаныш)</div>
            <div class="person" onclick="toggleChildren('parents')">ӘЖЕ (Айман)</div>
        </div>

        <div class="connector"></div>

        <!-- Әке-шеше -->
        <div id="parents" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kids')">ӘКЕ (Еркін)</div>
                <div class="person" onclick="toggleChildren('kids')">АНА (Гүлжан)</div>
            </div>
            <div class="connector"></div>
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
            <div class="connector"></div>
        </div>

        <!-- Әрбір ұл және олардың отбасылары -->
        <div id="kid1" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kid1family')">ҰЛ 1 + ЖҰБАЙЫ</div>
            </div>
            <div class="connector"></div>
        </div>

        <div id="kid1family" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kid1grandkids1')">БАЛА 1</div>
                <div class="person" onclick="toggleChildren('kid1grandkids2')">БАЛА 2</div>
                <div class="person" onclick="toggleChildren('kid1grandkids3')">БАЛА 3</div>
                <div class="person" onclick="toggleChildren('kid1grandkids4')">БАЛА 4</div>
            </div>
            <div class="connector"></div>
        </div>

        <div id="kid1grandkids1" class="children">
            <div class="level">
                <div class="person">НЕМЕРЕ 1</div>
                <div class="person">НЕМЕРЕ 2</div>
                <div class="person">НЕМЕРЕ 3</div>
            </div>
        </div>

        <div id="kid2" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kid2family')">ҰЛ 2 + ЖҰБАЙЫ</div>
            </div>
            <div class="connector"></div>
        </div>

        <div id="kid2family" class="children">
            <div class="level">
                <div class="person" onclick="toggleChildren('kid2grandkids1')">БАЛА 1</div>
                <div class="person" onclick="toggleChildren('kid2grandkids2')">БАЛА 2</div>
                <div class="person" onclick="toggleChildren('kid2grandkids3')">БАЛА 3</div>
                <div class="person" onclick="toggleChildren('kid2grandkids4')">БАЛА 4</div>
            </div>
            <div class="connector"></div>
        </div>

        <div id="kid2grandkids1" class="children">
            <div class="level">
                <div class="person">НЕМЕРЕ 1</div>
                <div class="person">НЕМЕРЕ 2</div>
                <div class="person">НЕМЕРЕ 3</div>
            </div>
        </div>

    </div>

    <script>
        function toggleChildren(id) {
            var element = document.getElementById(id);
            if (element) {
                if (element.style.display === "none" || element.style.display === "") {
                    element.style.display = "block";
                } else {
                    element.style.display = "none";
                }
            }
        }
    </script>
</body>
</html>
