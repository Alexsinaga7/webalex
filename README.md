<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profil 3D Interactive | Alex Alredo Sinaga</title>
    <style>
        /* 1. ANIMASI BACKGROUND Shift */
        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* 2. ANIMASI FOTO Melayang */
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        /* 3. ANIMASI MENGETIK */
        @keyframes typing {
            0% { width: 0; }
            70% { width: 100%; } /* Selesai mengetik di 70% */
            100% { width: 100%; } /* Diam sebentar */
        }

        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: #ff7675; } /* Warna kursor */
        }

        body {
            font-family: 'Poppins', 'Segoe UI', sans-serif;
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            /* Latar Belakang Gradasi Hidup */
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 12s ease infinite;
            overflow: hidden;
            /* Penting untuk Efek 3D Card */
            perspective: 1000px;
        }

        /* CONTAINER DENGAN EFEK 3D INTERAKTIF */
        .container {
            background: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 30px;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0,0,0,0.2);
            width: 90%;
            max-width: 400px;
            transition: transform 0.1s ease, box-shadow 0.3s ease; /* Transisi halus */
            transform-style: preserve-3d; /* Wajib untuk konten di dalamnya */
        }

        /* Saat kursor mouse menyentuh kartu */
        .container:hover {
            box-shadow: 0 40px 70px rgba(0,0,0,0.3);
            /* Transformasi 3D akan diatur oleh JavaScript sederhana di bawah */
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 6px solid #f0f0f0;
            object-fit: cover;
            animation: float 4s ease-in-out infinite; /* Foto melayang */
            margin-bottom: 25px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        /* WRAPPER EFEK KETIK */
        .typing-wrapper {
            display: flex;
            justify-content: center;
            margin-bottom: 10px;
        }

        .typing-text {
            font-size: 1.7rem;
            font-weight: 800;
            color: #2d3436;
            white-space: nowrap;
            overflow: hidden;
            border-right: 4px solid #ff7675; /* Garis kursor */
            width: 0;
            /* Nama "Alex Alredo Sinaga" punya 16 karakter */
            animation: 
                typing 3s steps(16) forwards infinite,
                blink-caret 0.75s infinite;
        }

        .box-container {
            display: flex;
            gap: 10px;
            margin: 30px 0;
            justify-content: center;
        }

        .box {
            background: #f1f2f6;
            padding: 15px 5px;
            border-radius: 15px;
            flex: 1;
            font-size: 0.85rem;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: transform 0.3s ease;
        }

        /* Efek pop-up saat ikon disentuh mouse */
        .box:hover {
            transform: scale(1.1);
            background: #e1e2e6;
        }

        .box span {
            display: block;
            font-size: 1.8rem;
            margin-bottom: 5px;
        }

        .reason {
            background: linear-gradient(135deg, #f5f7fa 0%, #e1e8f5 100%);
            padding: 20px;
            border-radius: 20px;
            font-size: 0.95rem;
            line-height: 1.6;
            color: #2d3436;
            text-align: justify;
        }
    </style>
</head>
<body>

    <div class="container" id="card">
        <img src="foto-alex.png" alt="Alex Alredo Sinaga" class="profile-img">
        
        <div class="typing-wrapper">
            <div class="typing-text">Alex Alredo Sinaga</div>
        </div>
        
        <p style="color: #636e72; font-weight: 600; margin-top: 0; font-size: 1rem;">NIM: 7243250012</p>

        <div class="box-container">
            <div class="box">🚀<br>Startup</div>
            <div class="box">💻<br>Digital</div>
            <div class="box">📊<br>Bisnis</div>
        </div>

        <div class="reason">
            <strong style="color: #01579b;">Alasan Memilih Bisnis Digital:</strong><br>
            "Saya ingin membuka bisnis dan menyediakan lapangan pekerjaan. Di era yang dipenuhi dunia digital ini, jurusan ini adalah fondasi yang paling meyakinkan untuk masa depan."
        </div>
    </div>

    <script>
        const card = document.getElementById('card');
        
        card.addEventListener('mousemove', (e) => {
            let xAxis = (window.innerWidth / 2 - e.pageX) / 15;
            let yAxis = (window.innerHeight / 2 - e.pageY) / 15;
            card.style.transform = `rotateY(${xAxis}deg) rotateX(${yAxis}deg)`;
        });

        // Kembalikan kartu ke posisi semula saat mouse keluar
        card.addEventListener('mouseleave', () => {
            card.style.transform = `rotateY(0deg) rotateX(0deg)`;
        });
    </script>

</body>
</html>
