<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gümüşlük Öğrenci Yurdu | Gümüşlük İlim Kültür ve Eğitime Yardım Derneği</title>
    <!-- FontAwesome İkonlar & Google Fonts -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary: #0f4c81;
            --secondary: #1b6ca8;
            --accent: #f39c12;
            --dark: #2c3e50;
            --light: #f8f9fa;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }
        body { background-color: var(--light); color: #333; line-height: 1.6; scroll-behavior: smooth; overflow-x: hidden; }
        
        /* Navigasyon / Menü - Mobil Uyumlu */
        nav {
            position: fixed; top: 0; width: 100%; background: rgba(255, 255, 255, 0.98);
            backdrop-filter: blur(10px); display: flex; justify-content: space-between; align-items: center;
            padding: 0.8rem 4%; box-shadow: 0 2px 15px rgba(0,0,0,0.1); z-index: 1000;
        }
        .logo { font-size: 1.1rem; font-weight: 700; color: var(--primary); display: flex; align-items: center; gap: 8px; }
        .nav-links { display: flex; list-style: none; gap: 1.2rem; align-items: center; }
        .nav-links a { text-decoration: none; color: var(--dark); font-weight: 500; font-size: 0.95rem; transition: 0.3s; }
        .nav-links a:hover { color: var(--primary); }
        .btn-donate-nav { background: var(--accent); color: white !important; padding: 0.5rem 1rem; border-radius: 20px; transition: 0.3s !important; }
        .btn-donate-nav:hover { background: #e08e0b; }

        /* Yeni Fotoğrafla Karşılama Ekranı (Hero) - Mobil Uyumlu */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(15, 76, 129, 0.70), rgba(0, 0, 0, 0.75)), 
                        url('Gumusluk3.jpeg') center/cover no-repeat;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            text-align: center; color: white; padding: 0 1rem;
        }
        .hero-badge {
            background: rgba(243, 156, 18, 0.95);
            color: white;
            padding: 0.4rem 1rem;
            border-radius: 20px;
            font-weight: 600;
            font-size: 0.85rem;
            margin-bottom: 1rem;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            text-align: center;
        }
        .hero h1 { font-size: 2.5rem; margin-bottom: 0.8rem; text-shadow: 2px 2px 10px rgba(0,0,0,0.6); font-weight: 700; }
        .hero p { font-size: 1rem; max-width: 750px; margin-bottom: 2rem; opacity: 0.95; font-weight: 300; text-shadow: 1px 1px 5px rgba(0,0,0,0.5); padding: 0 10px; }
        .hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; width: 100%; }
        
        .btn { padding: 0.8rem 1.8rem; border-radius: 30px; text-decoration: none; font-weight: 600; font-size: 0.95rem; transition: all 0.3s ease; display: inline-flex; align-items: center; gap: 8px; }
        .btn-primary { background: var(--accent); color: white; }
        .btn-primary:hover { background: #e08e0b; transform: translateY(-3px); }
        .btn-outline { border: 2px solid white; color: white; }
        .btn-outline:hover { background: white; color: var(--primary); transform: translateY(-3px); }

        /* Genel Bölüm Stilleri */
        section { padding: 4rem 5%; }
        .section-title { text-align: center; font-size: 1.8rem; color: var(--primary); margin-bottom: 2.5rem; position: relative; }
        .section-title::after { content: ''; width: 60px; height: 4px; background: var(--accent); display: block; margin: 8px auto 0; border-radius: 2px; }

        /* İmkanlar Kartları - Mobil Uyumlu Grid */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 1.5rem; }
        .card { background: white; padding: 2rem 1.2rem; border-radius: 15px; text-align: center; box-shadow: 0 5px 20px rgba(0,0,0,0.05); transition: 0.3s; }
        .card:hover { transform: translateY(-5px); }
        .card i { font-size: 2.5rem; color: var(--secondary); margin-bottom: 1rem; }
        .card h3 { font-size: 1.1rem; margin-bottom: 0.6rem; color: var(--dark); }
        .card p { font-size: 0.9rem; color: #666; }

        /* Yorumlar - Mobil Uyumlu */
        .reviews-container { background: #eef5fc; border-radius: 15px; padding: 2.5rem 1rem; }
        .rating-badge { text-align: center; margin-bottom: 2rem; font-size: 1.1rem; font-weight: 600; color: var(--primary); }
        .rating-badge i { color: #f1c40f; }
        .review-cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1.2rem; }
        .review-card { background: white; padding: 1.5rem; border-radius: 12px; border-left: 5px solid var(--accent); box-shadow: 0 3px 10px rgba(0,0,0,0.03); }
        .review-card p { font-style: italic; color: #555; font-size: 0.95rem; }
        .review-card small { display: block; margin-top: 0.8rem; font-weight: 600; color: var(--primary); font-size: 0.85rem; }

        /* Bağış Alanı - Mobil Uyumlu */
        .donation-section { background: linear-gradient(135deg, var(--primary), var(--secondary)); color: white; text-align: center; border-radius: 20px; padding: 3rem 1rem; box-shadow: 0 10px 25px rgba(15, 76, 129, 0.3); }
        .donation-section h2 { font-size: 1.8rem; margin-bottom: 0.8rem; }
        .donation-section p { font-size: 0.95rem; padding: 0 10px; opacity: 0.9; }
        .bank-info { background: rgba(255,255,255,0.12); backdrop-filter: blur(8px); max-width: 600px; margin: 1.5rem auto 0; padding: 1.5rem 1rem; border-radius: 15px; border: 1px solid rgba(255,255,255,0.25); }
        
        .clickable-box {
            background: rgba(255, 255, 255, 0.2);
            padding: 0.7rem 1rem;
            border-radius: 8px;
            margin-bottom: 1rem;
            cursor: pointer;
            transition: 0.2s;
            display: block;
            width: 100%;
            font-weight: 600;
            font-size: 0.95rem;
            word-break: break-word;
        }
        .clickable-box:hover { background: rgba(255, 255, 255, 0.3); }
        
        .iban-box {
            font-size: 1.05rem;
            font-weight: bold;
            background: white;
            color: var(--dark);
            padding: 0.9rem;
            border-radius: 8px;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
            transition: 0.2s;
            word-break: break-all;
        }
        .iban-box:hover { background: #f0f0f0; }

        /* İletişim & Alt Bilgi */
        #iletisim div { font-size: 1rem !important; word-break: break-word; padding: 0 10px; }
        footer { background: var(--dark); color: white; text-align: center; padding: 1.5rem 1rem; margin-top: 3rem; font-size: 0.9rem; }

        @media (max-width: 768px) {
            .nav-links { display: none; }
            .hero h1 { font-size: 2.1rem; }
            .hero p { font-size: 0.95rem; }
            section { padding: 3rem 4%; }
            .section-title { font-size: 1.5rem; }
        }
    </style>
</head>
<body>

    <!-- Üst Menü -->
    <nav>
        <div class="logo"><i class="fa-solid fa-graduation-cap"></i> Gümüşlük Yurdu</div>
        <ul class="nav-links">
            <li><a href="#hakkimizda">Hakkımızda</a></li>
            <li><a href="#imkanlar">İmkanlar</a></li>
            <li><a href="#yorumlar">Yorumlar</a></li>
            <li><a href="#bagis" class="btn-donate-nav"><i class="fa-solid fa-heart"></i> Bağış Yap</a></li>
            <li><a href="#iletisim">İletişim</a></li>
        </ul>
    </nav>

    <!-- Yeni Fotoğraflı ve "Hoş Geldiniz" Karşılama Ekranı -->
    <header class="hero">
        <div class="hero-badge">
            <i class="fa-solid fa-house-chimney"></i> Gümüşlük İlim Kültür ve Eğitime Yardım Derneği
        </div>
        <h1>Hoş Geldiniz</h1>
        <p>Gümüşlük Öğrenci Yurdu olarak; öğrencilerimize ev sıcaklığında, güvenli, huzurlu ve konforlu bir barınma ortamı sunmaktan mutluluk duyuyoruz.</p>
        <div class="hero-btns">
            <a href="#bagis" class="btn btn-primary"><i class="fa-solid fa-heart"></i> Eğitime Destek Ol</a>
            <a href="#hakkimizda" class="btn btn-outline"><i class="fa-solid fa-circle-info"></i> Yurdumuzu Keşfedin</a>
        </div>
    </header>

    <!-- Hakkımızda -->
    <section id="hakkimizda">
        <h2 class="section-title">Hakkımızda</h2>
        <p style="text-align: center; max-width: 800px; margin: 0 auto; font-size: 1.05rem; color: #555; line-height: 1.7;">
            Bursa Nilüfer Çalı mahallesinde hizmet veren <strong>Gümüşlük Öğrenci Yurdu</strong>, <strong>Gümüşlük İlim Kültür ve Eğitime Yardım Derneği</strong> çatısı altında faaliyet göstermektedir. Yurdumuz, öğrencilerimizin akademik çalışmalarına odaklanabileceği, ahlaki ve sosyal değerlerle donatıldığı ideal bir yaşam merkezidir.
        </p>
    </section>

    <!-- İmkanlar -->
    <section id="imkanlar" style="background: #f0f4f8;">
        <h2 class="section-title">Yurt İmkanlarımız</h2>
        <div class="grid">
            <div class="card">
                <i class="fa-solid fa-shield-halved"></i>
                <h3>Güvenli ve Huzurlu</h3>
                <p>Güvenlik tedbirleri ve huzurlu ders çalışma alanları.</p>
            </div>
            <div class="card">
                <i class="fa-solid fa-location-dot"></i>
                <h3>Merkezi Konum</h3>
                <p>Nilüfer Çalı bölgesinde kolay ulaşım ve rahat lokasyon.</p>
            </div>
            <div class="card">
                <i class="fa-solid fa-bed"></i>
                <h3>Temiz ve Konforlu Odalar</h3>
                <p>Öğrencilerimiz için özenle hazırlanan konforlu yaşam alanları.</p>
            </div>
            <div class="card">
                <i class="fa-solid fa-utensils"></i>
                <h3>Lezzetli Yemekler</h3>
                <p>Hijyenik koşullarda hazırlanan düzenli ve lezzetli yemek imkanı.</p>
            </div>
        </div>
    </section>

    <!-- Google Yorumları & Derecelendirme -->
    <section id="yorumlar">
        <h2 class="section-title">Öğrenci & Veli Değerlendirmeleri</h2>
        <div class="reviews-container">
            <div class="rating-badge">
                <i class="fa-solid fa-star"></i> <i class="fa-solid fa-star"></i> <i class="fa-solid fa-star"></i> <i class="fa-solid fa-star"></i> <i class="fa-solid fa-star-half-stroke"></i>
                <br>4.7 / 5.0 — Google Haritalar Memnuniyet Puanı
            </div>
            <div class="review-cards">
                <div class="review-card">
                    <p>"Harika bir yurt, çalışanlar çok ilgili ve ortam oldukça temiz ve güvenli."</p>
                    <small>— Google Kullanıcı Yorumu</small>
                </div>
                <div class="review-card">
                    <p>"Öğrencilerin ders çalışması ve huzur bulması için ideal bir yuva."</p>
                    <small>— Veli Değerlendirmesi</small>
                </div>
                <div class="review-card">
                    <p>"Dernek yönetiminin eğitime olan katkısı ve öğrencilere yaklaşımı takdire şayan."</p>
                    <small>— Ziyaretçi Yorumu</small>
                </div>
            </div>
        </div>
    </section>

    <!-- Bağış Alanı -->
    <section id="bagis">
        <div class="donation-section">
            <h2>Eğitime Bir Tuğla da Sen Koy</h2>
            <p>Gümüşlük İlim Kültür ve Eğitime Yardım Derneği aracılığıyla öğrencilerimizin eğitimine ve geleceğine destek olun.</p>
            <div class="bank-info">
                <h3 style="font-size: 1.1rem; margin-bottom: 0.8rem;">Banka Bağış Bilgileri</h3>
                
                <!-- Dernek İsmi Kopyalama Kutusu -->
                <div class="clickable-box" onclick="copyAssocName()" title="Dernek ismini kopyalamak için tıklayın">
                    <span id="assocName">Gümüşlük İlim Kültür ve Eğitime Yardım Derneği</span> 
                    <i class="fa-regular fa-copy" style="margin-left: 6px;"></i>
                </div>

                <!-- IBAN Kopyalama Kutusu -->
                <div class="iban-box" onclick="copyIban()" title="IBAN numarasını kopyalamak için tıklayın">
                    <span id="ibanText">TR91 0001 0026 9153 0090 1550 04</span>
                    <i class="fa-regular fa-copy"></i>
                </div>

                <small id="copyStatus" style="display:block; margin-top:0.8rem; opacity:0.9; font-style:italic; font-size:0.85rem;">(İstediğiniz alana tıklayarak panoya kopyalayabilirsiniz)</small>
            </div>
        </div>
    </section>

    <!-- İletişim -->
    <section id="iletisim">
        <h2 class="section-title">İletişim Bilgileri</h2>
        <div style="text-align: center; line-height: 2.2;">
            <p><i class="fa-solid fa-map-location-dot" style="color:var(--primary);"></i> <strong>Adres:</strong> Çalı, 114. Sk No:10, 16275 Nilüfer/Bursa</p>
            <p><i class="fa-solid fa-phone" style="color:var(--primary);"></i> <strong>Telefon:</strong> 0507 858 72 26</p>
            <p><i class="fa-solid fa-building-columns" style="color:var(--primary);"></i> <strong>İşletme:</strong> Gümüşlük İlim Kültür ve Eğitime Yardım Derneği</p>
        </div>
    </section>

    <!-- Alt Bilgi / Footer -->
    <footer>
        <p>&copy; 2026 Gümüşlük Öğrenci Yurdu - Tüm Hakları Saklıdır.</p>
    </footer>

    <!-- JavaScript Kopyalama Fonksiyonları -->
    <script>
        function copyAssocName() {
            const name = document.getElementById('assocName').innerText;
            navigator.clipboard.writeText(name).then(() => {
                const status = document.getElementById('copyStatus');
                status.innerText = "✓ Dernek İsmi Pano'ya Kopyalandı!";
                status.style.color = "#ffeaa7";
                setTimeout(() => {
                    status.innerText = "(İstediğiniz alana tıklayarak panoya kopyalayabilirsiniz)";
                    status.style.color = "white";
                }, 3000);
            });
        }

        function copyIban() {
            const iban = document.getElementById('ibanText').innerText;
            navigator.clipboard.writeText(iban).then(() => {
                const status = document.getElementById('copyStatus');
                status.innerText = "✓ IBAN Numarası Pano'ya Kopyalandı!";
                status.style.color = "#ffeaa7";
                setTimeout(() => {
                    status.innerText = "(İstediğiniz alana tıklayarak panoya kopyalayabilirsiniz)";
                    status.style.color = "white";
                }, 3000);
            });
        }
    </script>
</body>
</html>
