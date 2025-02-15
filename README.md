<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шежіре</title>
    <script src="https://cdn.jsdelivr.net/gh/ErikGartner/dTree/dist/dtree.min.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        #tree-container {
            width: 100%;
            height: 600px;
        }
    </style>
</head>
<body>

    <h2>Шежіре Деректері</h2>
    <div id="tree-container"></div>

    <script>
        var tree = new dTree('tree');

        tree.add(1, 0, "Қуаныш");
        tree.add(2, 0, "Айман");
        tree.add(3, 1, "Еркін");
        tree.add(4, 2, "Гүлжан");
        tree.add(5, 3, "Ұл 1");
        tree.add(6, 3, "Ұл 2");
        tree.add(7, 3, "Ұл 3");
        tree.add(8, 3, "Ұл 4");
        tree.add(9, 3, "Ұл 5");

        document.getElementById("tree-container").innerHTML = tree.toString();
    </script>

</body>
</html>
