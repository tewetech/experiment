<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>README Profil GitHub Keren</title>
    <style>
        /* CSS Dimulai dari sini */
        :root {
            --bg-color: #0d1117;
            --text-color: #c9d1d9;
            --accent-color: #58a6ff;
            --card-bg: #161b22;
            --border-color: #30363d;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            margin: 0;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: var(--card-bg);
            border-radius: 10px;
            border: 1px solid var(--border-color);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            animation: fadeIn 1s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        .header h1 {
            color: var(--accent-color);
            font-size: 2.5em;
            margin-bottom: 5px;
        }

        .header p {
            color: #8b949e;
            font-style: italic;
        }

        .skill-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .skill-card {
            background-color: #21262d;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            border: 1px solid var(--border-color);
        }

        .skill-card:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
        }

        .skill-card img {
            width: 50px;
            height: 50px;
            margin-bottom: 10px;
        }

        .skill-card h3 {
            font-size: 1em;
            margin: 0;
            color: var(--text-color);
        }

        .message-box {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background-color: var(--accent-color);
            color: #fff;
            padding: 10px 20px;
            border-radius: 5px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.5s, visibility 0.5s;
            z-index: 1000;
        }

        .message-box.show {
            opacity: 1;
            visibility: visible;
        }
        /* CSS Berakhir di sini */
    </style>
</head>
<body>

    <div class="container">
        <div class="header">
            <h1>Hai, saya [NAMA KAMU] 👋</h1>
            <p>Seorang [PROFESI KAMU], suka ngoding dan eksplorasi teknologi baru!</p>
        </div>

        <div class="bio">
            <p>
                Selamat datang di profil GitHub saya! Saya fokus di bidang [BIDANG KAMU, contoh: Full-Stack Web Development].
                Di sini kamu bisa melihat beberapa proyek yang sedang saya kerjakan dan teknologi yang saya kuasai.
            </p>
            <p>
                Saya percaya bahwa belajar itu proses yang tiada akhir. Yuk, terhubung dan berkolaborasi!
            </p>
        </div>

        <hr>

        <h2>Teknologi yang Saya Kuasai 💻</h2>
        <div class="skill-section">
            <div class="skill-card" data-skill="HTML">
                <img src="https://skillicons.dev/icons?i=html" alt="HTML">
                <h3>HTML</h3>
            </div>
            <div class="skill-card" data-skill="CSS">
                <img src="https://skillicons.dev/icons?i=css" alt="CSS">
                <h3>CSS</h3>
            </div>
            <div class="skill-card" data-skill="js">
                <img src="https://skillicons.dev/icons?i=js" alt="JavaScript">
                <h3>JavaScript</h3>
            </div>
            <div class="skill-card" data-skill="react">
                <img src="https://skillicons.dev/icons?i=react" alt="React">
                <h3>React</h3>
            </div>
            <div class="skill-card" data-skill="nodejs">
                <img src="https://skillicons.dev/icons?i=nodejs" alt="Node.js">
                <h3>Node.js</h3>
            </div>
            </div>

        <div class="message-box" id="messageBox"></div>

    </div>
    <script>
        // JavaScript Dimulai dari sini
        document.addEventListener('DOMContentLoaded', () => {
            // Ambil semua elemen skill-card
            const skillCards = document.querySelectorAll('.skill-card');
            const messageBox = document.getElementById('messageBox');

            // Tambahkan event listener untuk setiap skill-card
            skillCards.forEach(card => {
                card.addEventListener('click', () => {
                    // Ambil nama skill dari atribut data-skill
                    const skillName = card.dataset.skill;
                    
                    // Tampilkan pesan
                    showMessage(`Wah, kamu klik skill ${skillName}! Keren!`);
                });
            });

            // Fungsi untuk menampilkan pesan
            function showMessage(message) {
                messageBox.textContent = message;
                messageBox.classList.add('show');
                
                // Sembunyikan pesan setelah 3 detik
                setTimeout(() => {
                    messageBox.classList.remove('show');
                }, 3000);
            }
        });
        // JavaScript Berakhir di sini
    </script>

</body>
</html>
