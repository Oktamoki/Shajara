<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шежіре</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .container {
            text-align: center;
        }
        .box {
            border: 2px solid #333;
            padding: 10px;
            margin: 10px;
            background-color: white;
            cursor: pointer;
            display: inline-block;
            width: 150px;
        }
        .children {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="box" onclick="toggleVisibility('parent1')">Ата-баба</div>
        <div id="parent1" class="children">
            <div class="box" onclick="toggleVisibility('child1')">Әке</div>
            <div class="box" onclick="toggleVisibility('child2')">Шеше</div>
            <div id="child1" class="children">
                <div class="box">Бала 1</div>
                <div class="box">Бала 2</div>
            </div>
            <div id="child2" class="children">
                <div class="box">Бала 3</div>
                <div class="box">Бала 4</div>
            </div>
        </div>
    </div>

    <script>
        function toggleVisibility(id) {
            var element = document.getElementById(id);
            if (element.style.display === "none" || element.style.display === "") {
                element.style.display = "block";
            } else {
                element.style.display = "none";
            }
        }
    </script>
</body>
</html>
