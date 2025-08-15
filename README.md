# minichall
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>今日のミニチャレンジ | SNSより現実を楽しむ</title>
    <meta name="description" content="毎日1つ、現実世界でできるミニチャレンジをランダムで表示。SNSより現実に重きを置いて、今日をちょっと前向きに過ごそう！">
    <meta name="keywords" content="ミニチャレンジ, 日課, SNS断, モチベーション, 高校生, 現実体験">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            text-align: center;
            background: linear-gradient(135deg, #e0f7fa, #80deea);
            margin: 0;
            padding: 0;
        }
        h1 {
            margin-top: 40px;
            color: #01579b;
            font-size: 32px;
            font-weight: 700;
            letter-spacing: 1px;
        }
        button {
            padding: 12px 24px;
            font-size: 18px;
            border: none;
            border-radius: 8px;
            background-color: #0288d1;
            color: white;
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            transition: all 0.2s ease;
        }
        button:hover {
            background-color: #0277bd;
            transform: scale(1.05);
        }
        .challenge, .message {
            margin-top: 30px;
            font-size: 20px;
            background-color: white;
            display: inline-block;
            padding: 18px 22px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            max-width: 80%;
        }
        .challenge {
            color: #01579b;
        }
        .message {
            font-size: 18px;
            color: #0288d1;
            margin-top: 15px;
        }
    </style>
</head>
<body>

    <h1>今日のミニチャレンジ</h1>
    <button onclick="showChallenge()">チャレンジを見る</button>
    <div class="challenge" id="challengeText"></div>
    <div class="message" id="motivationText"></div>

    <script>
        const challenges = [
            "友達に直接『ありがとう』を伝える",
            "1時間スマホを机に置いておく",
            "外で10分間散歩する",
            "知らない道を歩いてみる",
            "今日の空の写真を撮る",
            "紙に今日の気分を書き出す",
            "家族に『おはよう』や『おやすみ』を言う",
            "今日会った人と3分以上話す",
            "コンビニで買わない日を作る",
            "机の上を5分だけ片付ける",
            "今日の目標を1つ紙に書く",
            "飲み物を1杯ゆっくり味わう",
            "好きな音楽を10分聴く",
            "部屋の窓を開けて換気する",
            "友達に近況を聞くメッセージを送る",
            "今日の服装を鏡でチェックして褒める",
            "短いストレッチを5分する",
            "おやつを我慢して水を飲む",
            "読書を10分だけする",
            "机の中を整理する"
        ];

        const messages = [
            "小さな一歩が、大きな変化の始まり",
            "今日の努力が、未来の自分を作る",
            "できることから、少しずつ始めよう",
            "あなたの頑張りは、必ず誰かに届く",
            "行動すれば、何かが必ず変わる",
            "焦らず、でも止まらず",
            "挑戦するあなたはもう立派",
            "昨日より少しだけ前へ",
            "今日を最高の一日にしよう",
            "笑顔が一番のエネルギー"
        ];

        function showChallenge() {
            const today = new Date().toLocaleDateString();
            const savedData = localStorage.getItem("todayChallenge");

            if (savedData) {
                const { date, challenge, message } = JSON.parse(savedData);
                if (date === today) {
                    document.getElementById("challengeText").textContent = challenge;
                    document.getElementById("motivationText").textContent = message;
                    return;
                }
            }

            const randomChallenge = challenges[Math.floor(Math.random() * challenges.length)];
            const randomMessage = messages[Math.floor(Math.random() * messages.length)];

            document.getElementById("challengeText").textContent = randomChallenge;
            document.getElementById("motivationText").textContent = randomMessage;

            localStorage.setItem("todayChallenge", JSON.stringify({
                date: today,
                challenge: randomChallenge,
                message: randomMessage
            }));
        }
    </script>

</body>
</html>
