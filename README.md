<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MiKey Log System - Smart Key Box</title>
    <style>
        :root {
            --primary-gold: #d4af37;
            --soft-green: #4caf50;
            --warn-red: #f44336;
            --bg-dark: #1a1a1a;
            --card-bg: #2d2d2d;
            --text-light: #e0e0e0;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-light);
            line-height: 1.6;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: var(--card-bg);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            border: 1px solid #444;
        }

        h1 {
            color: var(--primary-gold);
            text-align: center;
            font-size: 2.5em;
            margin-bottom: 10px;
            border-bottom: 2px solid var(--primary-gold);
            padding-bottom: 10px;
        }

        h2 {
            color: var(--primary-gold);
            display: flex;
            align-items: center;
            margin-top: 30px;
        }

        .tagline {
            text-align: center;
            font-style: italic;
            color: #aaa;
            margin-bottom: 30px;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 15px;
            margin: 10px 0;
            border-left: 5px solid var(--primary-gold);
            border-radius: 5px;
        }

        .feature-title {
            font-weight: bold;
            color: #fff;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: #333;
        }

        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #444;
        }

        th {
            background-color: var(--primary-gold);
            color: black;
        }

        pre {
            background: #000;
            padding: 15px;
            border-radius: 8px;
            overflow-x: auto;
            color: #00ff00;
            border: 1px solid #333;
        }

        .highlight {
            color: var(--soft-green);
            font-weight: bold;
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            font-size: 0.9em;
            color: #777;
        }

        .icon { margin-right: 10px; }
    </style>
</head>
<body>

<div class="container">
    <h1>🗝️ MiKey Log System</h1>
    <p class="tagline">〜 心を込めた鍵管理システム 〜</p>

    <p>Raspberry Pi Picoを使用した、4つの鍵を見守るスマートキーボックスです。鍵の持ち出し時間を監視し、LEDの優しい光で状態を教えてくれます。</p>

    <h2>🌟 特徴</h2>
    <div class="feature-card">
        <span class="feature-title">🔒 自動施錠機能</span><br>
        PCからの指令で解錠し、10秒後に自動でロック。閉め忘れを防ぐ安心設計です。
    </div>
    <div class="feature-card">
        <span class="feature-title">🚨 半ドア警告</span><br>
        扉がしっかり閉まっていないと、赤いLEDが「心配そうに」点滅してあなたに教えます。
    </div>
    <div class="feature-card">
        <span class="feature-title">⏳ お出かけタイマー</span><br>
        持ち出しから1時間を過ぎると、緑から赤の点滅へ。長時間の外出を優しくお知らせします。
    </div>

    <h2>🛠️ 準備するもの</h2>
    <ul>
        <li>Raspberry Pi Pico (または Pico W)</li>
        <li>電磁ソレノイド & リレーモジュール</li>
        <li>抵抗器付きLED（赤・緑）</li>
        <li>リミットスイッチ（ドア用・各鍵用）</li>
    </ul>

    <h2>🔌 配線図（回路のつながり）</h2>
    
    <table>
        <thead>
            <tr>
                <th>部品</th>
                <th>Picoピン番号</th>
                <th>役割</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><strong>Relay & Green LED</strong></td>
                <td>GP19</td>
                <td>ドアの解錠と状態表示</td>
            </tr>
            <tr>
                <td><strong>Door Red LED</strong></td>
                <td>GP10</td>
                <td>半ドア警告</td>
            </tr>
            <tr>
                <td><strong>Door Switch</strong></td>
                <td>GP9</td>
                <td>扉の開閉検知</td>
            </tr>
            <tr>
                <td><strong>Hook 1-4</strong></td>
                <td>(各設定ピン)</td>
                <td>鍵の持ち出し状態を監視</td>
            </tr>
        </tbody>
    </table>

    <h2>🚀 使い方</h2>
    <ol>
        <li><code>main.py</code> をRaspberry Pi Picoに書き込みます。</li>
        <li>PCのシリアル通信（Thonnyなど）から <span class="highlight">"UNLOCK"</span> と送信してください。</li>
        <li>魔法のように扉が開き、10秒経つとカチッと自動で鍵がかかります。</li>
    </ol>

    <h2>📝 現場に合わせたカスタマイズ</h2>
    <p>現場の運用に合わせて、警告が出るまでの時間を調整できます：</p>
    <pre>if elapsed_sec < 3600: # 3600秒(1時間)を好きな時間に変えてね</pre>

    <div class="footer">
        © 2026 MiKey Log - 温かい技術で、安心な毎日を。
    </div>
</div>

</body>
</html>
