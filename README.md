<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EduHelpXM | আপনার সফলতার সাথী</title>
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #6c5ce7;
            --grad-ssc: linear-gradient(135deg, #FF9A8B 0%, #FF6A88 55%, #FF99AC 100%);
            --grad-hsc: linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%);
            --grad-adm: linear-gradient(135deg, #a18cd1 0%, #fbc2eb 100%);
            --grad-job: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        body {
            font-family: 'Hind Siliguri', sans-serif;
            margin: 0;
            background-color: #f8f9fa;
        }

        /* Header */
        header {
            background: var(--primary);
            color: white;
            padding: 40px 20px;
            text-align: center;
            border-bottom-left-radius: 40px;
            border-bottom-right-radius: 40px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        /* SMS Alert Section */
        .sms-box {
            max-width: 500px;
            margin: -30px auto 30px;
            background: white;
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            text-align: center;
        }
        .sms-box input {
            width: 70%;
            padding: 12px;
            border: 2px solid #eee;
            border-radius: 10px;
            outline: none;
        }
        .sms-box button {
            padding: 12px 20px;
            background: #27ae60;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-weight: bold;
        }

        /* Grid */
        .container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            padding: 20px 5%;
        }

        .card {
            padding: 30px;
            border-radius: 25px;
            text-align: center;
            color: white;
            cursor: pointer;
            transition: 0.4s;
            box-shadow: 0 8px 20px rgba(0,0,0,0.1);
        }
        .card:hover { transform: translateY(-10px); filter: brightness(1.1); }
        .card i { font-size: 50px; margin-bottom: 15px; }

        .ssc { background: var(--grad-ssc); }
        .hsc { background: var(--grad-hsc); color: #333; }
        .adm { background: var(--grad-adm); }
        .job { background: var(--grad-job); }

        /* Gemini AI Widget */
        #chat-btn {
            position: fixed;
            bottom: 25px;
            right: 25px;
            background: var(--primary);
            color: white;
            width: 65px;
            height: 65px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            cursor: pointer;
            box-shadow: 0 5px 20px rgba(0,0,0,0.3);
            z-index: 1000;
        }

        #ai-window {
            position: fixed;
            bottom: 100px;
            right: 25px;
            width: 320px;
            height: 450px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            display: none;
            flex-direction: column;
            overflow: hidden;
            z-index: 1000;
        }
    </style>
</head>
<body>

<header>
    <h1>EduHelpXM</h1>
    <p>SSC | HSC | ADMISSION | JOB HELP DESK</p>
</header>

<div class="sms-box">
    <h3><i class="fas fa-bell"></i> অটো SMS অ্যালার্ট</h3>
    <input type="text" id="phone" placeholder="আপনার ফোন নম্বর (০১৭...)">
    <button onclick="sendSms()">চালু করুন</button>
</div>

<div class="container">
    <div class="card ssc" onclick="alert('SSC Corner এ আপনাকে স্বাগতম!')">
        <i class="fas fa-school"></i>
        <h2>SSC Corner</h2>
        <p>মডেল টেস্ট ও সাজেশন</p>
    </div>
    <div class="card hsc" onclick="alert('HSC Corner শীঘ্রই আসছে!')">
        <i class="fas fa-book-reader"></i>
        <h2>HSC Corner</h2>
        <p>বই PDF ও শর্ট সিলেবাস</p>
    </div>
    <div class="card adm" onclick="alert('Admission Corner লোড হচ্ছে...')">
        <i class="fas fa-university"></i>
        <h2>Admission Corner</h2>
        <p>ভার্সিটি প্রশ্ন ব্যাংক ও AI মেন্টর</p>
    </div>
    <div class="card job" onclick="alert('Job Help Desk ওপেন হচ্ছে...')">
        <i class="fas fa-briefcase"></i>
        <h2>Job Help Desk</h2>
        <p>বিসিএস ও ব্যাংক প্রিপারেশন</p>
    </div>
</div>

<div id="chat-btn" onclick="toggleChat()"><i class="fas fa-robot"></i></div>

<div id="ai-window">
    <div style="background:var(--primary); color:white; padding:15px; text-align:center;">Gemini AI মেন্টর</div>
    <div id="chat-content" style="flex:1; padding:15px; overflow-y:auto; font-size:14px;">
        <p style="background:#eee; padding:10px; border-radius:10px;">হ্যালো! আমি Gemini। আপনার পড়ালেখার যেকোনো প্রশ্ন আমাকে করতে পারেন।</p>
    </div>
    <div style="padding:10px; display:flex; border-top:1px solid #eee;">
        <input type="text" id="ai-msg" style="flex:1; border:none; padding:10px;" placeholder="আপনার প্রশ্নটি লিখুন...">
        <button onclick="askAI()" style="background:var(--primary); color:white; border:none; padding:10px; border-radius:5px;">পাঠান</button>
    </div>
</div>

<script>
    function toggleChat() {
        const win = document.getElementById('ai-window');
        win.style.display = (win.style.display === 'none' || win.style.display === '') ? 'flex' : 'none';
    }

    function sendSms() {
        const num = document.getElementById('phone').value;
        if(num.length === 11) {
            alert(num + " নম্বরে অটো SMS অ্যালার্ট চালু করা হয়েছে। ধন্যবাদ!");
        } else {
            alert("অনুগ্রহ করে ১১ ডিজিটের সঠিক নম্বর দিন।");
        }
    }

    function askAI() {
        const msg = document.getElementById('ai-msg').value;
        const box = document.getElementById('chat-content');
        if(msg) {
            box.innerHTML += `<p style="text-align:right;"><b>আপনি:</b> ${msg}</p>`;
            box.innerHTML += `<p style="background:#f0f0f0; padding:10px; border-radius:10px;"><b>Gemini:</b> আমি

