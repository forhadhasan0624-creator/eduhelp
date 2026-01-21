<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EduHelpXM | Your Study Partner</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #6c5ce7;
            --ssc-color: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            --hsc-color: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%);
            --adm-color: linear-gradient(135deg, #84fb95 0%, #cef576 100%);
            --job-color: linear-gradient(135deg, #fccb90 0%, #d57eeb 100%);
        }

        body {
            font-family: 'Hind Siliguri', sans-serif;
            margin: 0;
            background-color: #f4f7f6;
        }

        /* Navigation */
        nav {
            background: #fff;
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo { font-size: 24px; font-weight: bold; color: var(--primary); }
        .nav-buttons button {
            padding: 8px 18px;
            margin-left: 10px;
            border-radius: 20px;
            border: none;
            cursor: pointer;
            font-weight: bold;
        }
        .login-btn { background: #eee; }
        .signup-btn { background: var(--primary); color: white; }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 60px 20px;
            background: var(--primary);
            color: white;
            border-bottom-left-radius: 50px;
            border-bottom-right-radius: 50px;
        }

        /* SMS Alert Box */
        .sms-box {
            background: white;
            width: 80%;
            max-width: 500px;
            margin: -40px auto 40px;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
        }
        .sms-box input {
            width: 70%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            margin-bottom: 10px;
        }
        .sms-box button {
            background: #2ecc71;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 5px;
            cursor: pointer;
        }

        /* Service Grid */
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            padding: 20px 5%;
        }

        .card {
            padding: 30px;
            border-radius: 20px;
            color: #333;
            transition: 0.3s;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            position: relative;
        }
        .card:hover { transform: translateY(-10px); }
        .card i { font-size: 40px; margin-bottom: 15px; }

        .ssc { background: var(--ssc-color); }
        .hsc { background: var(--hsc-color); }
        .adm { background: var(--adm-color); }
        .job { background: var(--job-color); }

        /* AI Chatbox Widget */
        #ai-widget {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 300px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 5px 25px rgba(0,0,0,0.2);
            overflow: hidden;
            display: none;
        }
        .ai-header { background: var(--primary); color: white; padding: 10px; text-align: center; }
        #ai-output { height: 200px; padding: 10px; overflow-y: auto; font-size: 14px; border-bottom: 1px solid #eee; }
        .ai-input-area { display: flex; }
        .ai-input-area input { flex: 1; border: none; padding: 10px; }
        .ai-btn { background: var(--primary); color: white; border: none; padding: 10px; cursor: pointer; }
        
        .ai-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--primary);
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            font-size: 24px;
        }
    </style>
</head>
<body>

<nav>
    <div class="logo">EduHelpXM</div>
    <div class="nav-buttons">
        <button class="login-btn">Log In</button>
        <button class="signup-btn">Sign Up</button>
    </div>
</nav>

<div class="hero">
    <h1>আপনার সফলতার সাথী</h1>
    <p>SSC, HSC থেকে জব প্রিপারেশন—সবই এখন এক জায়গায়।</p>
</div>

<div class="sms-box">
    <h3><i class="fas fa-sms"></i> অটো SMS অ্যালার্ট চালু করুন</h3>
    <input type="text" id="phone" placeholder="আপনার ফোন নম্বর দিন (017...)">
    <button onclick="subscribeSMS()">অ্যালার্ট দিন</button>
</div>

<div class="grid-container">
    <div class="card ssc">
        <i class="fas fa-graduation-cap"></i>
        <h2>SSC Corner</h2>
        <p>মডেল টেস্ট, সাজেশন এবং নোটস</p>
        <button>শুরু করি</button>
    </div>
    <div class="card hsc">
        <i class="fas fa-book-open"></i>
        <h2>HSC Corner</h2>
        <p>বই PDF, সাজেশন্স এবং MT</p>
        <button>শুরু করি</button>
    </div>
    <div class="card adm">
        <i class="fas fa-university"></i>
        <h2>Admission Corner</h2>
        <p>ভার্সিটি প্রশ্ন ব্যাংক ও সমাধান</p>
        <button>শুরু করি</button>
    </div>
    <div class="card job">
        <i class="fas fa-briefcase"></i>
        <h2>Job Help Desk</h2>
        <p>ব্যাংক ও বিসিএস স্পেশাল প্রস্তুতি</p>
        <button>শুরু করি</button>
    </div>
</div>

<div class="ai-toggle" onclick="toggleAI()"><i class="fas fa-robot"></i></div>
<div id="ai-widget">
    <div class="ai-header">Gemini AI Study Assistant</div>
    <div id="ai-output">হাই! আমি আপনাকে কিভাবে সাহায্য করতে পারি?</div>
    <div class="ai-input-area">
        <input type="text" id="ai-input" placeholder="প্রশ্ন লিখুন...">
        <button class="ai-btn" onclick="askAI()">Send</button>
    </div>
</div>

<script>
    function subscribeSMS() {
        const phone = document.getElementById('phone').value;
        if(phone.length < 11) {
            alert("সঠিক ফোন নম্বর দিন!");
        } else {
            alert(phone + " নম্বরে অটোমেটিক SMS অ্যালার্ট চালু হয়েছে। ধন্যবাদ!");
        }
    }

    function toggleAI() {
        const widget = document.getElementById('ai-widget');
        widget.style.display = widget.style.display === 'none' ? 'block' : 'none';
    }

    function askAI() {
        const input = document.getElementById('ai-input').value;
        const output = document.getElementById('ai-output');
        if(input) {
            output.innerHTML += `<p><b>আপনি:</b> ${input}</p>`;
            output.innerHTML += `<p><b>Gemini:</b> আমি আপনার প্রশ্নের উত্তর খুঁজছি... (এখানে API কানেক্ট হবে)</p>`;
            document.getElementById('ai-input').value = "";
            output.scrollTop = output.scrollHeight;
        }
    }
</script>

</body>
</html>
