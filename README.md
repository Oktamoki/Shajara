# Shajara
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
        }
        .level {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
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
        }
        .connector {
            width: 2px;
            height: 20px;
            background: black;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <h2>Менің Шежірем</h2>
    <div class="tree">
        <!-- Атасы мен әжесі -->
        <div class="level">
            <div class="person" style="background:#ADD8E6;">АТА (Қуаныш)</div>
            <div class="person" style="background:#ADD8E6;">ӘЖЕ (Айман)</div>
        </div>

        <div class="connector"></div>

        <!-- Әке-шеше -->
        <div class="
