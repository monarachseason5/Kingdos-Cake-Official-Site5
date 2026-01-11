<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Kingdos Cake | Luxury Official</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Montserrat:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        :root { 
            --maroon: #421131; --pink: #F89CD2; --yellow: #FFD43B; 
            --lavender: #F3E5F5; --gold: #D4AF37; --white: #ffffff;
            --accent-blue: #E1F5FE;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
        body { font-family: 'Montserrat', sans-serif; background: var(--yellow); color: var(--maroon); overflow-x: hidden; }

        /* REPAIRED: LARGER HEAD BAR */
        header { 
            background: var(--maroon); 
            padding: 20px 25px; /* Increased padding for thickness */
            display: grid; 
            grid-template-columns: 1fr auto 1fr; 
            align-items: center; 
            border-bottom: 5px solid var(--gold); 
            position: sticky; 
            top: 0; 
            z-index: 1000; 
        }
        
        /* REPAIRED: BIGGER LUXURY ICON */
        .header-left { display: flex; align-items: center; }
        .luxury-icon { width: 55px; height: 55px; fill: var(--gold); filter: drop-shadow(0 0 8px rgba(212, 175, 55, 0.6)); }
        
        .header-title { 
            color: var(--gold); 
            font-family: 'Playfair Display'; 
            font-weight: 900; 
            letter-spacing: 3px; 
            font-size: 24px; /* Bigger Font */
            text-align: center;
        }
        
        .header-right { display: flex; justify-content: flex-end; }
        .cart-pill { background: var(--white); color: var(--maroon); padding: 10px 20px; border-radius: 30px; font-weight: 900; font-size: 16px; border: 2px solid var(--gold); }

        /* REPAIRED: BIGGER SLIDING PAGES */
        .hero { 
            height: 65vh; /* Much taller for big impact */
            position: relative; 
            overflow: hidden; 
            border-bottom: 6px solid var(--gold); 
        }
        .slide { position: absolute; width: 100%; height: 100%; opacity: 0; transition: 1.2s ease-in-out; background-size: cover; background-position: center; }
        .active { opacity: 1; transform: scale(1.05); } /* Subtle zoom effect */
        .slide-overlay { 
            height: 100%; 
            background: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.6)); 
            display: flex; 
            flex-direction: column;
            align-items: center; 
            justify-content: center; 
            color: white; 
            text-align: center; 
            padding: 20px;
        }
        .slide-overlay h1 { font-family: 'Playfair Display'; font-size: 48px; text-shadow: 2px 2px 10px rgba(0,0,0,0.5); }
        .slide-overlay p { font-size: 18px; font-weight: 600; letter-spacing: 1px; margin-top: 10px; }

        .promo-bar { background: var(--gold); color: var(--maroon); text-align: center; padding: 15px; font-size: 13px; font-weight: 900; letter-spacing: 1px; }

        /* GRID SECTIONS */
        .section-title { text-align: center; padding: 40px 0 20px; font-family: 'Playfair Display'; font-size: 32px; text-transform: uppercase; letter-spacing: 2px; }
        .container { padding: 30px 5% 60px; }
        
        .grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px; }
        @media (min-width: 768px) { .grid { grid-template-columns: repeat(4, 1fr); } }

        .card { background: white; border-radius: 20px; overflow: hidden; box-shadow: 0 8px 20px rgba(0,0,0,0.15); cursor: pointer; position: relative; }
        .card img { width: 100%; height: 220px; object-fit: cover; }
        .card-name { padding: 18px; text-align: center; font-weight: 800; font-size: 14px; text-transform: uppercase; color: var(--maroon); }
        .bogo-badge { position: absolute; top: 15px; left: 15px; background: #ff0000; color: white; padding: 6px 14px; font-size: 11px; font-weight: 900; border-radius: 8px; z-index: 10; box-shadow: 0 4px 8px rgba(0,0,0,0.3); }

        /* PAGE 2 UI */
        #details-page { display: none; background: #fff; position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 2000; overflow-y: auto; }
        .back-nav { padding: 22px; background: var(--maroon); color: var(--gold); font-weight: 900; border: none; width: 100%; text-align: left; font-size: 16px; }
        .p-image { width: 100%; height: 450px; object-fit: cover; border-bottom: 10px solid var(--pink); }
        .p-body { padding: 35px; max-width: 700px; margin: auto; padding-bottom: 150px; }
        .p-price { font-size: 42px; font-weight: 900; color: #ff0066; margin-bottom: 30px; }

        .info-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-bottom: 30px; }
        .info-tile { background: var(--lavender); padding: 20px; border-radius: 15px; border-left: 8px solid var(--maroon); }
        .tile-label { font-size: 11px; font-weight: 800; color: #777; text-transform: uppercase; }
        .tile-value { font-size: 16px; font-weight: 700; color: var(--maroon); margin-top: 5px; }

        .interactive-btn { border-radius: 18px; padding: 25px; margin-bottom: 15px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .btn-greeting { background: linear-gradient(135deg, #421131, #F89CD2); color: white; }
        .btn-payment { background: #f1f8e9; color: #2e7d32; border: 2px solid #a5d6a7; }

        /* MODAL */
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 3000; align-items: center; justify-content: center; padding: 25px; }
        .modal-content { background: white; border-radius: 25px; padding: 40px; width: 100%; max-width: 450px; text-align: center; }
        input { width: 100%; padding: 18px; margin: 25px 0; border: 2px solid #ddd; border-radius: 12px; font-size: 18px; }

        .floating-footer { position: fixed; bottom: 0; left: 0; width: 100%; background: white; padding: 25px 35px; border-top: 1px solid #ddd; z-index: 2001; }
        .add-btn { background: var(--maroon); color: white; width: 100%; padding: 22px; border: none; border-radius: 18px; font-weight: 900; font-size: 20px; box-shadow: 0 10px 25px rgba(66, 17, 49, 0.3); }
    </style>
</head>
<body>

<header>
    <div class="header-left">
        <svg class="luxury-icon" viewBox="0 0 24 24"><path d="M5,16L3,5L8.5,10L12,4L15.5,10L21,5L19,16H5M19,19A1,1 0 0,1 18,20H6A1,1 0 0,1 5,19V18H19V19Z" /></svg>
    </div>
    <div class="header-title">KINGDOS CAKE</div>
    <div class="header-right">
        <div class="cart-pill">🛒 <span id="cartCount">0</span></div>
    </div>
</header>

<div id="home-page">
    <div class="hero">
        <div class="slide active" style="background-image: url('https://images.unsplash.com/photo-1578985545062-69928b1d9587')">
            <div class="slide-overlay"><h1>KINGDOS ROYAL</h1><p>Crafted for Royalty</p></div>
        </div>
        <div class="slide" style="background-image: url('https://images.unsplash.com/photo-1535254973040-607b474cb8c2')">
            <div class="slide-overlay"><h1>PURE LUXURY</h1><p>The Finest Ingredients Only</p></div>
        </div>
    </div>

    <div class="promo-bar">🎁 BUY 1 GET 1 FREE SIGNATURE • ALL CARDS ACCEPTED 💳</div>

    <h2 class="section-title">Signature Menu</h2>
    <div class="container" style="background: var(--accent-blue);"><div class="grid" id="sigGrid"></div></div>

    <h2 class="section-title">Luxury Masterpieces</h2>
    <div class="container" style="background: var(--yellow);"><div class="grid" id="premGrid"></div></div>
</div>

<div id="details-page">
    <button class="back-nav" onclick="closeDetails()">← BACK TO KINGDOS MENU</button>
    <img id="pImg" class="p-image">
    <div class="p-body">
        <h1 id="pTitle" style="font-family:'Playfair Display'; font-size: 40px;"></h1>
        <div id="pPrice" class="p-price"></div>

        <div class="info-grid">
            <div class="info-tile"><div class="tile-label">Cake Base</div><div class="tile-value" id="pBase"></div></div>
            <div class="info-tile"><div class="tile-label">Servings</div><div class="tile-value" id="pServes"></div></div>
        </div>

        <div class="interactive-btn btn-greeting" onclick="showModal('greeting')">
            <div>
                <div style="font-weight:900; font-size:18px;">✍️ CUSTOM ICING GREETING</div>
                <div id="greetingDisplay" style="font-size:13px; opacity:0.9;">Click here to write your message</div>
            </div>
            <div style="font-weight:900; font-size: 20px;">FREE</div>
        </div>

        <div class="interactive-btn btn-payment" onclick="showModal('payment')">
            <div>
                <div style="font-weight: 800; font-size: 18px;">💳 CARD PAYMENTS</div>
                <div style="font-size: 13px;">Secure Visa & Mastercard Gateway</div>
            </div>
            <div style="font-size: 14px; font-weight: 900;">SECURE</div>
        </div>
    </div>
    <div class="floating-footer"><button class="add-btn" onclick="addToCart()">ADD TO SHOPPING CART</button></div>
</div>

<div id="modalOverlay" class="modal">
    <div class="modal-content" id="modalContent"></div>
</div>

<script>
    let cart = 0;
    const signature = [
        {name: "Ribbon Classic", base: "Butter Sponge", serves: "12 Persons", price: "Rs. 3,850", img: "https://images.unsplash.com/photo-1535141192574-5d4897c12636", bogo: true},
        {name: "Chocolate Dream", base: "Dutch Cocoa", serves: "10 Persons", price: "Rs. 4,500", img: "https://images.unsplash.com/photo-1578985545062-69928b1d9587", bogo: true},
        {name: "Red Velvet Royale", base: "Velvet Mix", serves: "8 Persons", price: "Rs. 5,200", img: "https://images.unsplash.com/photo-1616541823729-00fe0aacd32c", bogo: true},
        {name: "Berry Bliss", base: "Strawberry", serves: "10 Persons", price: "Rs. 4,900", img: "https://images.unsplash.com/photo-1464347744102-11db6282f854", bogo: true},
        {name: "Vanilla Dream", base: "Vanilla", serves: "12 Persons", price: "Rs. 3,200", img: "https://images.unsplash.com/photo-1488477181946-6428a0291777", bogo: true},
        {name: "Oreo Gala", base: "Cookie Cream", serves: "12 Persons", price: "Rs. 5,100", img: "https://images.unsplash.com/photo-1542826438-bd32f43d626f", bogo: true},
        {name: "Salted Caramel", base: "Toffee", serves: "10 Persons", price: "Rs. 4,800", img: "https://images.unsplash.com/photo-1550617931-e17a7b70dce2", bogo: true},
    ];

    const luxury = [
        {name: "24K Gold Cake", base: "Gold Leaf", serves: "20 Persons", price: "Rs. 18,500", img: "https://images.unsplash.com/photo-1588195538326-c5b1e9f80a1b", bogo: false},        
        {name: "Midnight Forest", base: "Black Cherry", serves: "15 Persons", price: "Rs. 11,000", img: "https://images.unsplash.com/photo-1606313564200-e75d5e30476c", bogo: false},
        {name: "Tiffany Blue", base: "Ganache", serves: "12 Persons", price: "Rs. 14,500", img: "https://images.unsplash.com/photo-1557925923-33b27f891f88", bogo: false},
        {name: "Nutty Nutella", base: "Hazelnut", serves: "10 Persons", price: "Rs. 9,400", img: "https://images.unsplash.com/photo-1506459225024-1428097a7e18", bogo: false},
        {name: "Blueberry Hill", base: "Wild Berry", serves: "10 Persons", price: "Rs. 7,800", img: "https://images.unsplash.com/photo-1559620192-032c4bc4674e", bogo: false},
    ];

    function load(data, id) {
        const g = document.getElementById(id);
        data.forEach(c => {
            const d = document.createElement('div');
            d.className = 'card';
            d.onclick = () => {
                document.getElementById('pTitle').innerText = c.name;
                document.getElementById('pBase').innerText = c.base;
                document.getElementById('pServes').innerText = c.serves;
                document.getElementById('pPrice').innerText = c.price;
                document.getElementById('pImg').src = c.img;
                document.getElementById('home-page').style.display = 'none';
                document.getElementById('details-page').style.display = 'block';
                window.scrollTo(0,0);
            };
            d.innerHTML = `${c.bogo ? '<div class="bogo-badge">BUY 1 GET 1 FREE</div>' : ''}<img src="${c.img}"><div class="card-name">${c.name}</div>`;
            g.appendChild(d);
        });
    }

    function showModal(type) {
        const modal = document.getElementById('modalOverlay');
        const content = document.getElementById('modalContent');
        modal.style.display = 'flex';
        if(type === 'greeting') {
            content.innerHTML = `<h3>Cake Message</h3><p>Enter the text for your icing greeting:</p><input type="text" id="msgI" placeholder="Happy Birthday..."><button class="add-btn" onclick="saveM()">SAVE MESSAGE</button>`;
        } else {
            content.innerHTML = `<h3>Secure Checkout</h3><p>All payments are processed via encrypted servers.</p><br><button class="add-btn" onclick="closeModal()">GOT IT</button>`;
        }
    }

    function saveM() {
        const v = document.getElementById('msgI').value;
        if(v) document.getElementById('greetingDisplay').innerText = "Message: " + v;
        closeModal();
    }

    function closeModal() { document.getElementById('modalOverlay').style.display = 'none'; }
    function closeDetails() { document.getElementById('home-page').style.display = 'block'; document.getElementById('details-page').style.display = 'none'; }
    function addToCart() { cart++; document.getElementById('cartCount').innerText = cart; alert("Kingdos Item Added!"); closeDetails(); }

    load(signature, 'sigGrid'); load(luxury, 'premGrid');
    let idx = 0; const slides = document.querySelectorAll('.slide');
    setInterval(() => { slides[idx].classList.remove('active'); idx = (idx + 1) % slides.length; slides[idx].classList.add('active'); }, 4000);
</script>
</body>
</html>
