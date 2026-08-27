<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aivora - مساعدك الذكي</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, Tahoma, sans-serif;
    background: linear-gradient(135deg, #07152f, #102d5c, #07152f);
    color: white;
    min-height: 100vh;
}

header {
    padding: 22px 7%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid rgba(255,255,255,0.12);
}

.logo {
    font-size: 30px;
    font-weight: bold;
    color: #58a6ff;
}

.owner {
    font-size: 13px;
    color: #b9c7dc;
}

.hero {
    text-align: center;
    padding: 70px 20px 35px;
}

.hero h1 {
    font-size: 42px;
    margin-bottom: 15px;
}

.hero h1 span {
    color: #58a6ff;
}

.hero p {
    color: #c5d0e0;
    font-size: 18px;
    line-height: 1.8;
    max-width: 700px;
    margin: auto;
}

.chat {
    width: 92%;
    max-width: 850px;
    margin: 35px auto;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.13);
    border-radius: 24px;
    padding: 20px;
    backdrop-filter: blur(10px);
}

#messages {
    min-height: 100px;
    max-height: 300px;
    overflow-y: auto;
    margin-bottom: 15px;
}

.message {
    background: rgba(88,166,255,0.15);
    padding: 13px 16px;
    border-radius: 15px;
    margin: 8px 0;
    text-align: right;
}

.input-area {
    display: flex;
    gap: 10px;
}

input {
    flex: 1;
    padding: 16px;
    border: none;
    outline: none;
    border-radius: 14px;
    background: #ffffff;
    color: #111;
    font-size: 16px;
}

button {
    border: none;
    cursor: pointer;
    border-radius: 14px;
    padding: 14px 20px;
    background: #2584ff;
    color: white;
    font-size: 16px;
    font-weight: bold;
}

button:hover {
    opacity: 0.85;
}

.quick {
    max-width: 850px;
    width: 92%;
    margin: 20px auto;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
}

.quick button {
    background: rgba(255,255,255,0.09);
    border: 1px solid rgba(255,255,255,0.12);
    padding: 20px 10px;
}

.about {
    width: 92%;
    max-width: 850px;
    margin: 50px auto;
    text-align: center;
    padding: 30px;
    background: rgba(255,255,255,0.06);
    border-radius: 22px;
}

.about h2 {
    color: #58a6ff;
    margin-bottom: 15px;
}

.about p {
    color: #c5d0e0;
    line-height: 2;
}

footer {
    text-align: center;
    padding: 30px;
    color: #91a2ba;
    font-size: 13px;
}

@media (max-width: 600px) {
    header {
        padding: 18px;
    }

    .hero {
        padding-top: 45px;
    }

    .hero h1 {
        font-size: 32px;
    }

    .hero p {
        font-size: 15px;
    }

    .quick {
        grid-template-columns: 1fr;
    }

    .input-area {
        flex-direction: column;
    }

    button {
        width: 100%;
    }
}
</style>
</head>

<body>

<header>
    <div class="logo">Aivora</div>
    <div class="owner">© Marwan Aljariri</div>
</header>

<section class="hero">
    <h1>مرحبًا بك في <span>Aivora</span></h1>
    <p>
        مساعدك الذكي للكتابة، الأفكار، التعلم والإجابة عن أسئلتك.
        ابدأ محادثتك الآن.
    </p>
</section>

<section class="chat">

    <div id="messages">
        <div class="message">
            👋 أهلًا بك في Aivora! كيف يمكنني مساعدتك؟
        </div>
    </div>

    <div class="input-area">
        <input
            id="userInput"
            type="text"
            placeholder="اكتب سؤالك هنا..."
            onkeydown="if(event.key==='Enter') sendMessage()"
        >

        <button onclick="sendMessage()">إرسال</button>
    </div>

</section>

<section class="quick">

    <button onclick="quickMessage('أعطني أفكارًا جديدة')">
        💡 أفكار
    </button>

    <button onclick="quickMessage('ساعدني في الكتابة')">
        ✍️ الكتابة
    </button>

    <button onclick="quickMessage('اشرح لي هذا الموضوع')">
        📚 شرح
    </button>

</section>

<section class="about">

    <h2>عن Aivora</h2>

    <p>
        Aivora منصة ذكية تهدف إلى مساعدة المستخدمين
        في الحصول على الأفكار والمعلومات والمساعدة في الكتابة
        والتعلم بطريقة سهلة وسريعة.
    </p>

</section>

<footer>
    Aivora © 2026 — Marwan Aljariri
</footer>

<script>

function addMessage(text) {
    const messages = document.getElementById("messages");

    const message = document.createElement("div");
    message.className = "message";
    message.textContent = text;

    messages.appendChild(message);
    messages.scrollTop = messages.scrollHeight;
}

function sendMessage() {

    const input = document.getElementById("userInput");
    const text = input.value.trim();

    if (text === "") {
        return;
    }

    addMessage("أنت: " + text);

    input.value = "";

    setTimeout(function() {
        addMessage(
            "Aivora: شكرًا لسؤالك! هذه الواجهة جاهزة، ويمكن لاحقًا ربطها بخدمة ذكاء اصطناعي حقيقية."
        );
    }, 500);
}

function quickMessage(text) {
    document.getElementById("userInput").value = text;
    sendMessage();
}

</script>

</body>
</html>
