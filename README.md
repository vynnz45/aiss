<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Priceless Princess Display Case</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Quicksand:wght@600;700&display=swap');

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: #b0d4f1 linear-gradient(to bottom, #b0d4f1 0%, #e0f2fe 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            font-family: 'Quicksand', sans-serif;
        }

        /* Latar Belakang Awan Estetik */
        .cloud-bg {
            position: absolute;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(circle at 20% 30%, rgba(255,255,255,0.6) 0%, transparent 40%),
                radial-gradient(circle at 75% 70%, rgba(255,255,255,0.5) 0%, transparent 45%);
            z-index: 1;
        }

        /* Kotak Display Mekanis (Premium Wood & Brass) */
        .display-case {
            position: relative;
            z-index: 10;
            width: 480px;
            background: #ebd1aa; /* Warna kayu maple muda */
            border: 6px solid #b8860b; /* Aksen kuningan/emas tua */
            border-radius: 24px 24px 16px 16px;
            box-shadow: 
                inset 0 4px 0 #fff3d1,
                inset 0 -10px 0 #c29d6d,
                0 20px 40px rgba(0, 30, 80, 0.25);
            padding: 20px;
            text-align: center;
        }

        /* Papan Nama Atas */
        .header-board {
            background: #fff9e6;
            border: 3px solid #1e4f8a;
            border-radius: 40px 40px 10px 10px;
            padding: 12px 10px;
            margin-top: -45px;
            margin-bottom: 25px;
            box-shadow: 0 6px 0 #153965, 0 8px 15px rgba(0,0,0,0.1);
        }

        .header-board h1 {
            font-family: 'Fredoka One', sans-serif;
            font-size: 24px;
            color: #1e4f8a;
            text-shadow: 2px 2px 0 #fff;
            letter-spacing: 0.5px;
        }

        /* Layar Pertanyaan Kayu Ukir */
        .screen-carving {
            background: #ffd993;
            border: 3px solid #8b5a2b;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
            box-shadow: inset 0 4px 8px rgba(0,0,0,0.15);
            position: relative;
        }

        .screen-carving p {
            font-size: 22px;
            font-weight: 700;
            color: #5c3a21;
            text-shadow: 1px 1px 0 rgba(255,255,255,0.4);
        }

        /* Area Mekanik Tombol */
        .mechanic-floor {
            background: #f7e4c3;
            border: 3px solid #c29d6d;
            border-radius: 12px;
            height: 160px;
            position: relative;
            overflow: visible;
            box-shadow: inset 0 6px 12px rgba(0,0,0,0.08);
            margin-bottom: 10px;
        }

        /* Hiasan Bintang & Mahkota Logam */
        .deco-prop {
            position: absolute;
            font-size: 16px;
            opacity: 0.8;
            pointer-events: none;
        }

        /* Tombol Kristal Resin Hati (Iyaa) */
        #btn-iya {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            width: 85px;
            height: 80px;
            background: radial-gradient(circle at 35% 35%, #ff7675, #d63031);
            clip-path: path('M12 4.419C12.447 3.972 13.163 3 15.609 3 19.344 3 22 5.864 22 9.613c0 4.704-4.22 8.706-9.554 12.016a.792.792 0 0 1-.892 0C6.22 18.319 2 14.317 2 9.613 2 5.864 4.656 3 8.391 3 10.837 3 11.553 3.972 12 4.419z');
            transform-origin: center;
            border: none;
            cursor: pointer;
            z-index: 15;
            box-shadow: 0 8px 0 #b2bec3;
            font-family: 'Fredoka One', sans-serif;
            color: #fff3d1;
            font-size: 16px;
            padding-top: 15px; /* Menyesuaikan teks di dalam clip-path hati */
            text-shadow: 0 2px 4px rgba(0,0,0,0.3);
            animation: pulseHeart 1.4s infinite ease-in-out;
            transition: transform 0.2s;
        }

        #btn-iya:hover {
            animation: none;
            transform: translate(-50%, -50%) scale(1.1);
        }

        /* Tombol Porselen Enggaa dengan Rel Mekanis */
        #btn-engga {
            position: absolute;
            width: 80px;
            height: 45px;
            background: radial-gradient(circle at 30% 30%, #ffffff, #cbd5e1);
            border: 3px solid #475569;
            color: #1e293b;
            border-radius: 50% 50% 45% 45%;
            font-weight: 700;
            font-size: 15px;
            cursor: pointer;
            z-index: 10;
            box-shadow: 0 5px 0 #475569, 0 8px 12px rgba(0,0,0,0.15);
            white-space: nowrap;
            transition: left 0.12s cubic-bezier(0.25, 1, 0.5, 1), top 0.12s cubic-bezier(0.25, 1, 0.5, 1);
        }

        /* Laci Kejutan Rahasia (Hidden Vault) */
        .secret-drawer {
            max-height: 0;
            overflow: hidden;
            background: #fffdf5;
            border: 0 solid #8b5a2b;
            border-radius: 12px;
            transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            opacity: 0;
        }

        .secret-drawer.open {
            max-height: 200px;
            opacity: 1;
            border: 3px solid #8b5a2b;
            padding: 20px;
            margin-top: 15px;
            box-shadow: inset 0 4px 10px rgba(0,0,0,0.1);
        }

        .secret-drawer p {
            font-size: 18px;
            color: #7c2d12;
            font-weight: 700;
            margin-bottom: 15px;
        }

        /* Gulungan Tombol Kembali Tradisional */
        #btn-kembali {
            display: inline-block;
            background: #e2cca7;
            border: 2px solid #5c3a21;
            border-radius: 4px;
            color: #5c3a21;
            font-family: 'Fredoka One', sans-serif;
            font-size: 13px;
            padding: 6px 20px;
            cursor: pointer;
            box-shadow: 0 4px 0 #5c3a21;
            text-transform: uppercase;
            transition: transform 0.1s, box-shadow 0.1s;
        }

        #btn-kembali:hover {
            background: #d0b58b;
            transform: translateY(2px);
            box-shadow: 0 2px 0 #5c3a21;
        }

        /* Animasi Detak Jantung Mekanis */
        @keyframes pulseHeart {
            0% { transform: translate(-50%, -50%) scale(1); }
            30% { transform: translate(-50%, -50%) scale(1.08); }
            60% { transform: translate(-50%, -50%) scale(1); }
            80% { transform: translate(-50%, -50%) scale(1.08); }
            100% { transform: translate(-50%, -50%) scale(1); }
        }
    </style>
</head>
<body>

    <div class="cloud-bg"></div>

    <div class="display-case">
        <!-- Papan Nama Atas -->
        <div class="header-board">
            <h1 id="main-title">HELOOWW MY PRICELESS PRINCESS</h1>
        </div>

        <!-- Layar Pertanyaan -->
        <div class="screen-carving">
            <p id="teks-pertanyaan">kamu sayang aku tidaa?</p>
        </div>

        <!-- Lantai Tombol / Mekanik -->
        <div class="mechanic-floor" id="lantai-mekanik">
            <!-- Properti Dekorasi Sudut -->
            <span class="deco-prop" style="top:10px; left:15px;">⭐</span>
            <span class="deco-prop" style="top:10px; right:15px;">👑</span>
            <span class="deco-prop" style="bottom:10px; left:20px;">💙</span>
            <span class="deco-prop" style="bottom:10px; right:20px;">⭐</span>

            <button id="btn-iya" onclick="bukaLaciMekanis()">iyaa</button>
            <button id="btn-engga">enggaa</button>
        </div>

        <!-- Laci Rahasia Tersembunyi -->
        <div class="secret-drawer" id="laci-rahasia">
            <p>Yeayyy! Aku juga sayang banget sama kamuu! 💖👑</p>
            <button id="btn-kembali" onclick="tutupLaciMekanis()">KEMBALI</button>
        </div>
    </div>

    <script>
        const btnIya = document.getElementById('btn-iya');
        const btnEngga = document.getElementById('btn-engga');
        const laciRahasia = document.getElementById('laci-rahasia');
        const teksPertanyaan = document.getElementById('teks-pertanyaan');
        const lantaiMekanik = document.getElementById('lantai-mekanik');

        let sudut = 0;
        const radiusX = 140; // Jalur orbit horizontal dilebarkan
        const radiusY = 55;  // Jalur orbit vertikal
        let sedangMenghindar = false;
        let waktuMenghindar = 0;
        let sistemAktif = true;

        // Fungsi Pergerakan Orbit Mekanis Otomatis
        function gerakMekanis() {
            if (!sistemAktif) return;

            if (sedangMenghindar) {
                if (Date.now() - waktuMenghindar > 900) {
                    sedangMenghindar = false;
                } else {
                    requestAnimationFrame(gerakMekanis);
                    return;
                }
            }

            sudut += 0.015;
            
            // Titik Pusat Orbit adalah Tombol Iyaa
            const centerX = lantaiMekanik.offsetWidth / 2 - btnEngga.offsetWidth / 2;
            const centerY = lantaiMekanik.offsetHeight / 2 - btnEngga.offsetHeight / 2;

            const x = centerX + radiusX * Math.cos(sudut);
            const y = centerY + radiusY * Math.sin(sudut);

            btnEngga.style.left = x + 'px';
            btnEngga.style.top = y + 'px';

            requestAnimationFrame(gerakMekanis);
        }

        requestAnimationFrame(gerakMekanis);

        // Deteksi Sensor Jarak Tangan / Kursor (Sistem Tolakan Magnetik)
        document.addEventListener('mousemove', (e) => {
            if (!sistemAktif || btnEngga.style.display === 'none') return;

            const rect = btnEngga.getBoundingClientRect();
            const tombolX = rect.left + (rect.width / 2);
            const tombolY = rect.top + (rect.height / 2);

            const jarakX = e.clientX - tombolX;
            const jarakY = e.clientY - tombolY;
            const totalJarak = Math.sqrt(jarakX * jarakX + jarakY * jarakY);

            if (totalJarak < 85) {
                sedangMenghindar = true;
                waktuMenghindar = Date.now();

                const arahX = jarakX / totalJarak;
                const arahY = jarakY / totalJarak;

                // Tombol akan terpental ke arah berlawanan dari datangnya kursor
                let posisiBaruX = btnEngga.offsetLeft - (arahX * 110);
                let posisiBaruY = btnEngga.offsetTop - (arahY * 70);

                // Batasan dinding bagian dalam kotak kayu
                const batasKiri = 5;
                const batasKanan = lantaiMekanik.offsetWidth - btnEngga.offsetWidth - 5;
                const batasAtas = 5;
                const batasBawah = lantaiMekanik.offsetHeight - btnEngga.offsetHeight - 5;

                posisiBaruX = Math.max(batasKiri, Math.min(posisiBaruX, batasKanan));
                posisiBaruY = Math.max(batasAtas, Math.min(posisiBaruY, batasBawah));

                btnEngga.style.left = Math.round(posisiBaruX) + 'px';
                btnEngga.style.top = Math.round(posisiBaruY) + 'px';

                // Sinkronisasi sudut orbit baru pasca terdorong kursor
                const centerX = lantaiMekanik.offsetWidth / 2 - btnEngga.offsetWidth / 2;
                const centerY = lantaiMekanik.offsetHeight / 2 - btnEngga.offsetHeight / 2;
                sudut = Math.atan2(posisiBaruY - centerY, (posisiBaruX - centerX) * (radiusY / radiusX));
            }
        });

        // Trigger Pembukaan Laci Rahasia bawah
        function bukaLaciMekanis() {
            sistemAktif = false;
            btnIya.style.display = 'none';
            btnEngga.style.display = 'none';
            teksPertanyaan.innerText = "I love you! 🥰";
            laciRahasia.classList.add('open');
        }

        // Trigger Penutupan Kembali
        function tutupLaciMekanis() {
            laciRahasia.classList.remove('open');
            
            setTimeout(() => {
                teksPertanyaan.innerText = "kamu sayang aku tidaa?";
                btnIya.style.display = 'block';
                btnEngga.style.display = 'block';
                sistemAktif = true;
                sedangMenghindar = false;
                requestAnimationFrame(gerakMekanis);
            }, 400); // Sinkronisasi jeda transisi laci menutup
        }
    </script>
</body>
</html>
