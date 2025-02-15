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
    <svg width="100%" height="600" viewBox="-500 -50 1500 1000"></svg>
    <script>
        const treeData = {
            name: "Ахмаджон Махбуба",
            children: [
                {
                    name: "Абдумажит Салима",
                    class: "family1",
                    children: [
                        { name: "Фуркат Нигора", class: "family1", children: [
                            { name: "Бала 1", class: "family1" },
                            { name: "Бала 2", class: "family1", children: [
                                { name: "Немере 1", class: "family1" },
                                { name: "Немере 2", class: "family1" }
                            ]}
                        ]},
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
                        { name: "Фуркат Нигора", class: "family2", children: [
                            { name: "Бала 9", class: "family2" },
                            { name: "Бала 10", class: "family2" }
                        ]},
                        { name: "Гайрат Дилфуза", class: "family2", children: [
                            { name: "Бала 11", class: "family2" },
                            { name: "Бала 12",
