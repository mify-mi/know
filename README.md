<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>本格 性格診断アプリ</title>
<style>
body {
    font-family: sans-serif;
    text-align: center;
    background: #f4f4f4;
}
.container {
    background: white;
    width: 400px;
    margin: 30px auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px gray;
}
button {
    margin: 5px;
    padding: 8px 15px;
}
</style>
</head>
<body>

<div class="container">
<h2>🧠 本格 性格診断</h2>
<div id="quiz"></div>
<button onclick="nextQuestion()">次へ</button>
<div id="result"></div>
</div>

<script>
const questions = [
{
q:"新しいことに挑戦するのは？",
a:["ワクワクする","計画を立ててから","みんなと一緒なら","気分次第"]
},
{
q:"グループでは？",
a:["まとめ役","作戦担当","サポート役","アイデア担当"]
},
{
q:"決断は？",
a:["即決","データ重視","みんなの意見","直感"]
},
{
q:"トラブル発生！",
a:["仕切る","分析する","仲裁する","空気を変える"]
},
{
q:"大事なのは？",
a:["行動力","論理","思いやり","センス"]
}
];

let current = 0;
let scores = [0,0,0,0];

function showQuestion(){
    if(current >= questions.length){
        showResult();
        return;
    }

    let q = questions[current];
    let html = `<h3>${q.q}</h3>`;

    q.a.forEach((choice,index)=>{
        html += `<button onclick="selectAnswer(${index})">${choice}</button><br>`;
    });

    document.getElementById("quiz").innerHTML = html;
}

function selectAnswer(index){
    scores[index]++;
}

function nextQuestion(){
    current++;
    showQuestion();
}

function showResult(){
    let total = scores.reduce((a,b)=>a+b);
    let types = ["🔥リーダー型","🧠戦略家型","🌿協調型","🎨クリエイター型"];
    let resultHTML = "<h3>診断結果</h3>";

    scores.forEach((score,i)=>{
        let percent = ((score/total)*100).toFixed(1);
        resultHTML += `${types[i]}: ${percent}%<br>`;
    });

    let maxIndex = scores.indexOf(Math.max(...scores));
    resultHTML += `<h2>あなたは ${types[maxIndex]}！</h2>`;

    document.getElementById("quiz").innerHTML = "";
    document.getElementById("result").innerHTML = resultHTML;
}

showQuestion();
</script>

</body>
</html>
