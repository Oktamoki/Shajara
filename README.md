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
            position: relative;
        }
        .level {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
            position: relative;
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
            position: relative;
        }
        .children {
            display: none;
        }
        /* Сызықтарды байланыстыру */
        .connector {
            position: absolute;
            width: 2px;
            background: black;
        }
        .vertical-line {
            height: 20px;
            left: 50%;
            top: -20px;
        }
        .horizontal-line {
            width: 100%;
            height: 2px;
            background: black;
            position: absolute;
            top: 0;
        }
    </style>
</head>
<body>
    <h2>Менің Шежірем</h2>
    <div class="tree">
        <!-- Ата-әже -->
        <div class="level">
            <div class="person" onclick="toggleChildren('
