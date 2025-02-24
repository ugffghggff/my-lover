<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💌 手机表白</title>
    <style>
        body { background: #ffe6e6; display: flex; justify-content: center; align-items: center; min-height: 100vh; margin: 0; font-family: system-ui; }
        .popup { background: white; padding: 20px; border-radius: 15px; box-shadow: 0 0 20px rgba(0,0,0,0.1); width: 90%; max-width: 400px; text-align: center; }
        button { padding: 12px 25px; margin: 10px; border: none; border-radius: 8px; font-size: 16px; }
        #yesBtn { background: #ff4d79; color: white; }
        #noBtn { background: #f0f0f0; }
    </style>
</head>
<body>
    <div class="popup">
        <h2>💖 给特别的你</h2>
        <p>你愿意成为我的特别关注吗？</p >
        <button id="yesBtn">愿意</button>
        <button id="noBtn">考虑下</button>
    </div>

    <script>
        const FORM_ID = "这里粘贴你的表单ID"; // 修改这一行
        
        async function submitData(choice) {
            const formUrl = `https://api.form.newt.so/form/${FORM_ID}/submit`;
            await fetch(formUrl, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({
                    choice: choice,
                    time: new Date().toLocaleString(),
                    device: navigator.platform
                })
            });
        }

        document.getElementById('yesBtn').onclick = () => {
            alert('🎉 期待我们的故事！');
            submitData('yes');
        }
        document.getElementById('noBtn').onclick = () => {
            alert('😢 我会继续等待');
            submitData('no');
        }
    </script>
</body>
</html>
