<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шежіре</title>
    <script src="https://unpkg.com/dtree/dist/dtree.js"></script>
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
        var treeData = [
            { name: "Қуаныш", id: 1, parent: 0 },
            { name: "Айман", id: 2, parent: 0 },
            { name: "Еркін", id: 3, parent: 1 },
            { name: "Гүлжан", id: 4, parent: 2 },
            { name: "Ұл 1", id: 5, parent: 3 },
            { name: "Ұл 2", id: 6, parent: 3 },
            { name: "Ұл 3", id: 7, parent: 3 },
            { name: "Ұл 4", id: 8, parent: 3 },
            { name: "Ұл 5", id: 9, parent: 3 }
        ];

        var tree = new dTree('tree');
        treeData.forEach(person => {
            tree.add(person.id, person.parent, person.name);
        });

        document.getElementById("tree-container").innerHTML = tree.toString();
    </script>

</body>
</html>
