# vocab-quiz
Ivy Fab + L1
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>英文單字挑戰賽</title>
    <style>
        :root {
            --primary: #4a90e2;
            --success: #4caf50;
            --error: #f44336;
            --bg: #f5f7fa;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }
        #quiz-container {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            width: 90%;
            max-width: 500px;
            text-align: center;
        }
        .progress-bar {
            width: 100%;
            height: 10px;
            background: #eee;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        #progress-fill {
            height: 100%;
            background: var(--primary);
            width: 0%;
            border-radius: 5px;
            transition: width 0.3s;
        }
        h1 { color: #333; font-size: 24px; margin-bottom: 10px; }
        #word-display {
            font-size: 32px;
            font-weight: bold;
            color: var(--primary);
            margin: 20px 0;
        }
        .options-grid {
            display: grid;
            gap: 10px;
        }
        button {
            padding: 15px;
            font-size: 16px;
            border: 2px solid #eee;
            border-radius: 10px;
            background: white;
            cursor: pointer;
            transition: all 0.2s;
        }
        button:hover { background: #f0f7ff; border-color: var(--primary); }
        button.correct { background: var(--success); color: white; border-color: var(--success); }
        button.wrong { background: var(--error); color: white; border-color: var(--error); }
        #score-board { display: none; }
        .restart-btn {
            background: var(--primary);
            color: white;
            border: none;
            margin-top: 20px;
            padding: 10px 20px;
        }
    </style>
</head>
<body>

<div id="quiz-container">
    <div id="game-zone">
        <div class="progress-bar"><div id="progress-fill"></div></div>
        <div id="status">第 <span id="current-idx">1</span> 題 / 共 <span id="total-idx">0</span> 題</div>
        <div id="word-display">Loading...</div>
        <div class="options-grid" id="options"></div>
    </div>

    <div id="score-board">
        <h1>🎉 練習完成！</h1>
        <p style="font-size: 20px;">你的得分：<span id="final-score">0</span> / <span id="final-total">0</span></p>
        <button class="restart-btn" onclick="location.reload()">再玩一次</button>
    </div>
</div>

<script>
    // 原始資料：自動解析你提供的文字
    const rawData = `aroma n. 香氣；香味
scented a. 有香氣的
scent n. 香氣
odor n. 氣味（中性/偏負面皆可）
fragrance n. 香味；芬芳
ritual n. 儀式；典禮
industrial a. 工業（用）的
patent vt. 為…申請／取得專利（權）
mass-produce vt. 大量製造
shovel n. 鏟子
destroy vt. 摧毀；破壞
unstable a. 不穩固的；不穩定的
volunteer n. 志工
unity n. 團結；統一
community n. 社區
reveal vt. 揭露；顯示
signal n./vi. 訊號；發出訊號
monitor vt. 監測；監控
phenomenon n. 現象（單數；複數 phenomena）
attach vt. 固定；使附著
warning n. 警告
transportation n. 運輸
admire vt. 欣賞；欽佩
athletic a. 運動的
remarkable n. 非凡的；卓越的
thrilling a. 刺激的
instinct n. 本能；天性
spring n. 彈簧
pump vt. （心臟）輸送（血液等）
efficiently adv. 有效率地
maximize vt. 使達最大限度
amaze vt. 使驚奇
extraordinary a. 非凡的；特別的
behavior n. 行為
reaction n. 反應
response n. 回應
curl vt. 使彎曲；使捲曲
detect vt. 偵測出
recognize vt. 辨認；辨識
emotional a. 情緒上的
extended a. 較長時間的；延長的
fast-paced a. 步調快速的
constant a. 持續不斷的
anxiety n. 焦慮
overwhelmed a. 不堪重負的；壓力很大
acceptable a. 可接受的
relief n. （痛苦、憂慮等的）減輕；緩解
inconvenience vt. 給…帶來不便／麻煩
vivid a. 鮮明的；生動的
cheerful a. 愉快的
consumer n. 消費者
household a. 家喻戶曉的；為許多人所知的
expand vi. 擴展
fade vi. 逐漸消失
immediate a. 立即的
swiftly adv. 迅速地
issue n. 問題；議題
psychologist n. 心理學家
relaxation n. 放鬆
practical a. 實際的
distinctive a. 獨特的；特別的
prominent a. 顯著的；突出的
inviting a. 吸引人的
atmosphere n. 氣氛
relieve vt. 緩和（痛苦、情緒等）
interruption n. 中斷
weapon n. 武器
historic a. 有歷史意義的
endure vi. 持續存在
adequate a. 充足的
package n. 包裹；一套行程／事物
clever a. 聰明的；機伶的
master vt./n. 精通；掌握／碩士
narrow a./vt./vi. 狹窄的；（使）變窄
replacement n. 替換物
queer a. 怪異的；奇特的
investigate vt. 調查
bundle n./vt./vi. 捆；綁
multiply vi. 倍增；大大增加
fortunately adv. 幸運地
launch vt. 推出；發表（新產品）
jointly adv. 共同地
retire vt. 不再使用；使退役
alarming a. 令人擔憂的；令人恐慌的
transform vt. 轉變
farewell n. 告別
surroundings n. 四周環境（恆用複數）
amuse vt. 娛樂；使開心
analyze vt. 分析
sense vt. 感覺到；察覺
debate vt./vi./n. 辯論；爭論
penalty n. 懲罰；刑罰
imprisonment n. 監禁
imprison vt. 監禁；關押
prison n. 監獄
prisoner n. 囚犯
claim n./vt. 宣稱；（對…的）所有權／聲稱擁有
insist vt./vi. 堅持；堅稱
property n. 地產；房地產／所有物；財產
companion n. 同伴；夥伴
mental a. 心理的；精神上的
devour vt. 狼吞虎嚥；熱切地讀
volume n. 書籍（一冊）；總量；總額
acquire vt. 取得；獲得；學到
acquisition n. 取得；獲得
profound a. 深厚的；見解深遠的
wealthy a. 富有的；富裕的
wealth n. 財富
murder vt./n. 謀殺；謀殺案
murderer n. 謀殺犯；兇手
disgust n./vt. 厭惡；反感
vain a. 枉然的；無用的
worship vt./n. 崇拜；愛慕
intention n. 打算；意圖
intend vt. 打算；想要
intentional a. 故意的；有意的
abandon vt. 中止；放棄／拋棄；遺棄
surrender vt./vi./n. 交出；放棄／投降
guilt n. 內疚／罪行
guilty a. 有罪的
rumor n./vt. 謠言；傳聞
refer to... 意指／指的是…
for a while 暫時；片刻
hide away 躲藏；隱藏
prevent sb from V-ing 使某人免於…
in some cases 在某些情況下
come to V 漸漸…
without interruption 不間斷地
be associated with... 與…有關
be bursting with... 充滿…
date back to + time 追溯至某時間點
give in to... 屈服於…
in the face of... 面對…
take sb's/sth's place 取代某人地位
take flight 飛起；上升
be designed to V 被設計來…
be designed for N 為…而設計
stand out as + N/Adj. 以…而脫穎而出
as + Adj./Adv. + as possible 儘可能…
in harmony 和諧地
in peak condition 處於巔峰／最佳狀態
remind sb that + clause 提醒某人…
make one's first appearance 首次亮相
in response 作為應對
call on/upon sb to V 呼籲／敦促某人做…
(be/seem) out of step with... 與…格格不入
in the background 處於不引人注目的地方
kick off 開始
face off (against) 對決；競爭
board up... / board... up 封住…
put on... / put... on 戴上／穿上…
back and forth 來回地
wear on （時間）慢慢過去
around the clock 日夜不停
the fruit(s) of... 成果
by no means 絕非；一點也不
cross one's mind 出現在腦海；想到
make clear 闡明；解釋`;

    // 解析資料
    const vocabList = rawData.split('\n').filter(line => line.trim() !== "").map(line => {
        const parts = line.split('\t'); // 假設是 tab 分隔，如果不是則嘗試空格
        if (parts.length < 2) {
             const spaceIdx = line.search(/[a-z]\s/i) + 1;
             return {
                 word: line.substring(0, spaceIdx).trim(),
                 trans: line.substring(spaceIdx).trim()
             };
        }
        return { word: parts[0].trim(), trans: parts[1].trim() };
    });

    let currentQuestionIdx = 0;
    let score = 0;
    let shuffledList = [];

    function initGame() {
        shuffledList = [...vocabList].sort(() => Math.random() - 0.5);
        // 如果題目太多，可以限制題數，例如 .slice(0, 20)
        document.getElementById('total-idx').innerText = shuffledList.length;
        showQuestion();
    }

    function showQuestion() {
        if (currentQuestionIdx >= shuffledList.length) {
            showResult();
            return;
        }

        const currentWord = shuffledList[currentQuestionIdx];
        document.getElementById('word-display').innerText = currentWord.word;
        document.getElementById('current-idx').innerText = currentQuestionIdx + 1;
        
        // 更新進度條
        const progress = (currentQuestionIdx / shuffledList.length) * 100;
        document.getElementById('progress-fill').style.width = progress + "%";

        // 產生選項
        let options = [currentWord.trans];
        while (options.length < 4) {
            const randomWord = vocabList[Math.floor(Math.random() * vocabList.length)];
            if (!options.includes(randomWord.trans)) {
                options.push(randomWord.trans);
            }
        }
        options.sort(() => Math.random() - 0.5);

        const optionsDiv = document.getElementById('options');
        optionsDiv.innerHTML = '';
        options.forEach(opt => {
            const btn = document.createElement('button');
            btn.innerText = opt;
            btn.onclick = () => checkAnswer(btn, opt, currentWord.trans);
            optionsDiv.appendChild(btn);
        });
    }

    function checkAnswer(btn, selected, correct) {
        const buttons = document.querySelectorAll('#options button');
        buttons.forEach(b => b.disabled = true); // 防止重複點擊

        if (selected === correct) {
            btn.classList.add('correct');
            score++;
        } else {
            btn.classList.add('wrong');
            buttons.forEach(b => {
                if (b.innerText === correct) b.classList.add('correct');
            });
        }

        setTimeout(() => {
            currentQuestionIdx++;
            showQuestion();
        }, 1000);
    }

    function showResult() {
        document.getElementById('game-zone').style.display = 'none';
        document.getElementById('score-board').style.display = 'block';
        document.getElementById('final-score').innerText = score;
        document.getElementById('final-total').innerText = shuffledList.length;
    }

    initGame();
</script>

</body>
</html>
