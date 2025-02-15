<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шежіре</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <style>
        .node {
            cursor: pointer;
        }
        .node rect {
            stroke: #000;
            stroke-width: 1.5px;
            rx: 5;
            ry: 5;
        }
        .node text {
            font-size: 12px;
            text-anchor: middle;
            dominant-baseline: middle;
            fill: white;
        }
        .link {
            fill: none;
            stroke: #555;
            stroke-width: 2px;
        }
        .family1 rect { fill: #4CAF50; } /* Жасыл */
        .family2 rect { fill: #2196F3; } /* Көк */
        .family3 rect { fill: #ff9800; } /* Қызғылт сары */
        .family4 rect { fill: #9c27b0; } /* Күлгін */
    </style>
</head>
<body>
    <svg width="1000" height="600"></svg>
    <script>
        const treeData = {
            name: "Ахмаджон Махбуба",
            children: [
                {
                    name: "Абдумажит Салима",
                    class: "family1",
                    children: [
                        { name: "Фуркат Нигора", class: "family1" },
                        { name: "Гайрат Дилфуза", class: "family1" },
                        { name: "Уткир Шахло", class: "family1" },
                        { name: "Октам Феруза", class: "family1" }
                    ]
                },
                {
                    name: "Абдукодир Ирисой",
                    class: "family2",
                    children: [
                { name: "Фуркат Нигора", class: "family2" },
                        { name: "Гайрат Дилфуза", class: "family2" },
                        { name: "Уткир Шахло", class: "family2" },
                        { name: "Октам Феруза", class: "family2" }
                    ]
                },
                {
                    name: "Жаңа Отбасы 3",
                    class: "family3",
                    children: [
                        { name: "Фуркат Нигора", class: "family3" },
                        { name: "Гайрат Дилфуза", class: "family3" },
                        { name: "Уткир Шахло", class: "family3" },
                        { name: "Октам Феруза", class: "family3" }
                    ]
                },
                {
                    name: "Жаңа Отбасы 4",
                    class: "family4",
                    children: [
                        { name: "Бала 8", class: "family4", children: [{ name: "Немере 21", class: "family4" }, { name: "Немере 22", class: "family4" }] }
                    ]
                }
            ]
        };

        const width = 1000, height = 600;
        const svg = d3.select("svg"),
              g = svg.append("g").attr("transform", "translate(50,50)");

        const tree = d3.tree()
            .size([width - 100, height - 200])
            .separation((a, b) => a.parent === b.parent ? 1.5 : 2);

        const root = d3.hierarchy(treeData, d => d.children);
        root.children.forEach(collapse); // Барлық түйіндерді жабу

        function collapse(d) {
            if (d.children) {
                d._children = d.children; // Барлық балаларын _children-ге сақтау
                d.children = null; // Балалар тізімін босату
                d._children.forEach(collapse); // Рекурсивті түрде барлық деңгейде жабу
            }
        }

        function update(source) {
            const nodes = root.descendants(), links = root.links();
            tree(root);

            g.selectAll(".link").remove();
            g.selectAll(".node").remove();

            g.selectAll(".link")
                .data(links)
                .enter().append("path")
                .attr("class", "link")
                .attr("d", d3.linkVertical()
                    .x(d => d.x)
                    .y(d => d.y));

            const node = g.selectAll(".node")
                .data(nodes, d => d.id || (d.id = Math.random()));

            const nodeEnter = node.enter().append("g")
                .attr("class", d => "node " + (d.data.class || ""))
                .attr("transform", d => `translate(${d.x},${d.y})`)
                .on("click", function(event, d) {
                    if (d.children) {
                        d._children = d.children;
                        d.children = null;
                    } else {
                        d.children = d._children;
                        d._children = null;
                    }
                    update(d);
                });

            nodeEnter.append("rect")
                .attr("width", 160)
                .attr("height", 60)
                .attr("x", -80)
                .attr("y", -30);

            nodeEnter.append("text")
                .attr("dy", ".35em")
                .attr("y", 5)
                .attr("x", 0)
                .text(d => d.data.name);
        }

        update(root);
    </script>
</body>
</html>
