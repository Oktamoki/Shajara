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
        <div class="box" onclick="toggleVisibility('parent')">Ата</div>
        <div id="parent" class="branch hidden">
            <div class="box" onclick="toggleVisibility('father')">Әке</div>
            <div class="box" onclick="toggleVisibility('mother1')">Шеше 1</div>
            <div class="box" onclick="toggleVisibility('mother2')">Шеше 2</div>
        </div>
        <div id="father" class="branch hidden">
            <div class="box" onclick="toggleVisibility('child1')">Бала 1</div>
            <div class="box" onclick="toggleVisibility('child2')">Бала 2</div>
            <div class="box" onclick="toggleVisibility('child3')">Бала 3</div>
            <div class="box" onclick="toggleVisibility('child4')">Бала 4</div>
            <div class="box" onclick="toggleVisibility('child5')">Бала 5</div>
            <div class="box" onclick="toggleVisibility('child6')">Бала 6</div>
        </div>
        <div id="child1" class="branch hidden">
            <div class="box">Немере 1</div>
            <div class="box">Немере 2</div>
            <div class="box">Немере 3</div>
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
