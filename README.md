<!DOCTYPE html>
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
            word-wrap: break-word;
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
    <svg width="100%" height="100%"></svg>
    <script>
        // Деректерді JSON файлынан жүктеу (мысал ретінде treeData қолданылады)
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
                        { name: "Бала 5", class: "family2", children: [{ name: "Немере 13", class: "family2" }, { name: "Немере 14", class: "family2" }, { name: "Немере 15", class: "family2" }] },
                        { name: "Бала 6", class: "family2", children: [{ name: "Немере 16", class: "family2" }, { name: "Немере 17", class: "family2" }, { name: "Немере 18", class: "family2" }] }
                    ]
                },
                {
                    name: "Жаңа Отбасы 3",
                    class: "family3",
                    children: [
                        { name: "Бала 7", class: "family3", children: [{ name: "Немере 19", class: "family3" }, { name: "Немере 20", class: "family3" }] }
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

        const width = window.innerWidth * 0.9;
        const height = window.innerHeight * 0.9;
        const svg = d3.select("svg"),
              g = svg.append("g").attr("transform", "translate(50,50)");

        const tree = d3.tree()
            .size([width - 100, height - 200])
            .separation((a, b) => a.parent === b.parent ? 1.5 : 2);

        const root = d3.hierarchy(treeData);
        tree(root);

        // Зум функциясы
        svg.call(d3.zoom()
            .scaleExtent([0.5, 2])
            .on("zoom", (event) => g.attr("transform", event.transform)));

        function update(source) {
            const nodes = root.descendants(), links = root.links();
            tree(root);

            // Ескі элементтерді жою
            g.selectAll(".link").remove();
            g.selectAll(".node").remove();

            // Байланыстарды қосу
            g.selectAll(".link")
                .data(links)
                .enter().append("path")
                .attr("class", "link")
                .transition()
                .duration(500)
                .attr("d", d3.linkVertical()
                    .x(d => d.x)
                    .y(d => d.y));

            // Түйіндерді қосу
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

            // Түйіндерге төртбұрыш қосу
            nodeEnter.append("rect")
                .attr("width", d => d.data.name.length * 10 + 40) // Мәтін ұзындығына қарай өзгеру
                .attr("height", 60)
                .attr("x", d => - (d.data.name.length * 10 + 40) / 2)
                .attr("y", -30);

            // Түйіндерге мәтін қосу
            nodeEnter.append("text")
                .attr("dy", ".35em")
                .attr("y", 5)
                .attr("x", 0)
                .text(d => d.data.name);

            // Тултип қосу
            nodeEnter.append("title")
                .text(d => `Аты: ${d.data.name}\nТуылған жылы: ${d.data.birthYear || "Белгісіз"}`);
        }

        update(root);
    </script>
</body>
</html>
