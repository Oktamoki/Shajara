<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Шежіре</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <style>
        .node rect {
            stroke: #000;
            stroke-width: 1.5px;
            rx: 5;
            ry: 5;
            fill: #4CAF50;
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
                    children: [
                        { name: "Фуркат Нигора" },
                        { name: "Гайрат Дилфуза" },
                        { name: "Уткир Шахло" },
                        { name: "Октам Феруза" }
                    ]
                },
                {
                    name: "Абдукодир Ирисой",
                    children: [
                        { name: "Бала 5", children: [{ name: "Немере 13" }, { name: "Немере 14" }] },
                        { name: "Бала 6", children: [{ name: "Немере 16" }, { name: "Немере 17" }] }
                    ]
                }
            ]
        };

        const width = 1000, height = 600;
        const svg = d3.select("svg"),
              g = svg.append("g").attr("transform", "translate(50,50)");

        const tree = d3.tree().nodeSize([180, 100]);
        const root = d3.hierarchy(treeData, d => d.children);
        root.x0 = height / 2;
        root.y0 = 0;

        root.children.forEach(collapse);

        function collapse(d) {
            if (d.children) {
                d._children = d.children;
                d._children.forEach(collapse);
                d.children = null;
            }
        }

        function update(source) {
            tree(root);
            const nodes = root.descendants(), links = root.links();
            nodes.forEach(d => d.y = d.depth * 180);

            const link = g.selectAll(".link").data(links, d => d.target.id);
            link.enter().append("path")
                .attr("class", "link")
                .attr("d", d3.linkHorizontal().x(d => d.y).y(d => d.x))
                .merge(link);
            link.exit().remove();

            const node = g.selectAll(".node").data(nodes, d => d.id || (d.id = Math.random()));
            const nodeEnter = node.enter().append("g")
                .attr("class", "node")
                .attr("transform", d => `translate(${source.y0},${source.x0})`)
                .on("click", (event, d) => toggleChildren(d));

            nodeEnter.append("rect")
                .attr("width", 160)
                .attr("height", 60)
                .attr("x", -80)
                .attr("y", -30);

            nodeEnter.append("text")
                .attr("dy", ".35em")
                .attr("y", 5)
                .text(d => d.data.name);

            const nodeUpdate = nodeEnter.merge(node);
            nodeUpdate.transition().duration(500)
                .attr("transform", d => `translate(${d.y},${d.x})`);

            node.exit().transition().duration(500)
                .attr("transform", d => `translate(${source.y},${source.x})`)
                .remove();

            root.x0 = source.x;
            root.y0 = source.y;
        }

        function toggleChildren(d) {
            if (d.children) {
                d._children = d.children;
                d.children = null;
            } else {
                d.children = d._children;
                d._children = null;
            }
            update(d);
        }

        update(root);
    </script>
</body>
</html>
