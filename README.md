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
            font-size: 14px;
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
    <svg width="100%" height="600" viewBox="0 0 1000 600"></svg>
    <script>
        const treeData = {
            name: "Ахмаджон Махбуба",
            children: [
                {
                    name: "Абдумажит Салима",
                    class: "family1",
                    children: [
                        { 
                            name: "Фуркат Нигора", 
                            class: "family1",
                            children: [
                                { name: "Бала 1", class: "family1" },
                                { name: "Бала 2", class: "family1", children: [
                                    { name: "Немере 1", class: "family1" },
                                    { name: "Немере 2", class: "family1" }
                                ]}
                            ]
                        },
                        { name: "Гайрат Дилфуза", class: "family1", children: [
                            { name: "Бала 3", class: "family1" },
                            { name: "Бала 4", class: "family1" }
                        ]}
                    ]
                },
                {
                    name: "Абдукодир Ирисой",
                    class: "family2",
                    children: [
                        { 
                            name: "Фуркат Нигора", 
                            class: "family2",
                            children: [
                                { name: "Бала 9", class: "family2" },
                                { name: "Бала 10", class: "family2" }
                            ]
                        },
                        { 
                            name: "Гайрат Дилфуза", 
                            class: "family2",
                            children: [
                                { name: "Бала 11", class: "family2" },
                                { name: "Бала 12", class: "family2" }
                            ]
                        }
                    ]
                }
            ]
        };

        const width = 1000, height = 600;
        const svg = d3.select("svg"),
              g = svg.append("g").attr("transform", `translate(${width / 2}, 50)`);

        const tree = d3.tree().size([width - 200, height - 200]);

        const root = d3.hierarchy(treeData, d => d.children);
        root.children.forEach(collapse);

        function collapse(d) {
            if (d.children) {
                d._children = d.children;
                d.children = null;
                d._children.forEach(collapse);
            }
        }

        function update(source) {
            const nodes = root.descendants();
            const links = root.links();
            tree(root);

            g.selectAll(".link").remove();
            g.selectAll(".node").remove();

            g.selectAll(".link")
                .data(links)
                .enter().append("path")
                .attr("class", "link")
                .attr("d", d3.linkVertical().x(d => d.x).y(d => d.y));

            const node = g.selectAll(".node")
                .data(nodes, d => d.id || (d.id = Math.random()));

            const nodeEnter = node.enter().append("g")
                .attr("class", d => "node " + (d.data.class || ""))
                .attr("transform", d => `translate(${d.x},${d.y})`)
                .on("click", function(event, d) {
                    d.children = d.children ? null : d._children;
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
                .text(d => d.data.name);

            nodeEnter.transition().duration(500)
                .attr("transform", d => `translate(${d.x},${d.y})`);
        }

        update(root);
    </script>
</body>
</html>
