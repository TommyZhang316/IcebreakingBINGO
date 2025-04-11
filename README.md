<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bingo 破冰游戏</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            background-color: #f9fafb;
        }

        h1 {
            font-size: 2rem;
            margin-bottom: 1rem;
            color: #333;
        }

        .bingo-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 5px;
            max-width: 500px;
            width: 100%;
        }

        .bingo-cell {
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 15px;
            font-size: 0.9rem;
            background-color: #f1f5f9;
            border: 1px solid #cbd5e1;
            cursor: pointer;
            transition: background-color 0.3s, color 0.3s;
        }

        .bingo-cell.completed {
            background-color: #34d399;
            color: #fff;
            text-decoration: line-through;
        }

        .bingo-cell:active {
            transform: scale(0.98);
        }

        .reset-button {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 1rem;
            background-color: #3b82f6;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .reset-button:hover {
            background-color: #2563eb;
        }
    </style>
</head>
<body>
    <h1>Bingo 破冰游戏</h1>
    <div class="bingo-grid" id="bingoGrid"></div>
    <button class="reset-button" onclick="generateBingo()">重新生成</button>

    <script>
        const phrases = [
            "最喜欢的歌手一样",
            "会同一门乐器",
            "都吃/不吃早饭",
            "都养/没养过宠物",
            "都喜欢/不喜欢喝咖啡",
            "看过同一部电影",
            "都喜欢/不喜欢早起",
            "曾经通宵/没通宵过",
            "会做同一道菜",
            "都喜欢/不喜欢旅行",
            "相同的mbti",
            "登过同一座山",
            "喜欢同一部动漫",
            "昨天早/晚于12点睡",
            "都有/没有兄弟姐妹",
            "都拿过A+",
            "都曾经/从未上台表演过",
            "都喜欢/不喜欢下雨天",
            "都在下周有ddl",
            "同样数量的考试",
            "都曾经/没染过头发",
            "都会/不会骑自行车",
            "坐同一种交通方式来活动",
            "都做/不做gym",
            "都喜欢/不喜欢吃辣"
        ];

        function shuffle(array) {
            for (let i = array.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [array[i], array[j]] = [array[j], array[i]];
            }
            return array;
        }

        function generateBingo() {
            const bingoGrid = document.getElementById('bingoGrid');
            bingoGrid.innerHTML = '';
            const shuffledPhrases = shuffle([...phrases]).slice(0, 25);

            shuffledPhrases.forEach(phrase => {
                const cell = document.createElement('div');
                cell.className = 'bingo-cell';
                cell.textContent = phrase;
                cell.onclick = () => {
                    cell.classList.toggle('completed');
                };
                bingoGrid.appendChild(cell);
            });
        }

        // 初始化 Bingo 网格
        generateBingo();
    </script>
</body>
</html>
