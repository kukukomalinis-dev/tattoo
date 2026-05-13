<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ink Appointment Booking</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family: 'Arial', sans-serif;
}

body{
    background:#0d0d0d;
    color:#fff;
    overflow-x:hidden;
}

/* NAVBAR */
nav{
    position:fixed;
    top:0;
    width:100%;
    background:rgba(0,0,0,0.85);
    padding:18px;
    text-align:center;
    z-index:1000;
    backdrop-filter:blur(8px);
    border-bottom:1px solid rgba(255,255,255,0.08);
}

nav a{
    color:#d4b27a;
    text-decoration:none;
    margin:0 20px;
    letter-spacing:1px;
    font-size:14px;
    transition:.3s;
}

nav a:hover{
    color:white;
}

/* HERO */
.hero{
    height:100vh;
    background:
    linear-gradient(rgba(0,0,0,0.75), rgba(0,0,0,0.85)),
    url('https://images.unsplash.com/photo-1542728928-1413d1894ed1?q=80&w=1974&auto=format&fit=crop') center/cover;
    
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    text-align:center;
    padding:20px;
}

.hero h1{
    font-size:90px;
    letter-spacing:8px;
    font-weight:900;
    color:white;
}

.hero span{
    color:#c6a16a;
}

.hero p{
    margin-top:15px;
    color:#ccc;
    letter-spacing:2px;
}

/* SECTIONS */
section{
    padding:100px 10%;
}

/* ABOUT */
.about{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:40px;
    align-items:center;
}

.about img{
    width:100%;
    border-radius:20px;
    object-fit:cover;
    height:500px;
    filter:brightness(80%);
}

.about-text h2{
    font-size:45px;
    margin-bottom:20px;
    color:#d4b27a;
}

.about-text p{
    line-height:1.8;
    color:#bbb;
}

/* GALLERY */
.section-title{
    text-align:center;
    font-size:50px;
    margin-bottom:50px;
    color:#d4b27a;
}

.filters{
    text-align:center;
    margin-bottom:35px;
}

.filters button{
    background:transparent;
    border:1px solid #c6a16a;
    color:#c6a16a;
    padding:10px 20px;
    margin:5px;
    cursor:pointer;
    transition:.3s;
    border-radius:30px;
}

.filters button:hover{
    background:#c6a16a;
    color:black;
}

.gallery{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
    gap:20px;
}

.gallery img{
    width:100%;
    height:350px;
    object-fit:cover;
    border-radius:18px;
    cursor:pointer;
    transition:.4s;
    border:1px solid rgba(255,255,255,0.08);
}

.gallery img:hover{
    transform:scale(1.03);
}

/* MODAL */
.modal{
    display:none;
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:rgba(0,0,0,0.92);
    justify-content:center;
    align-items:center;
    z-index:2000;
}

.modal img{
    max-width:80%;
    max-height:85%;
    border-radius:20px;
}

/* BOOKING */
.booking-container{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:40px;
    align-items:start;
}

.booking-info{
    background:#111;
    padding:40px;
    border-radius:25px;
    border:1px solid rgba(255,255,255,0.08);
}

.booking-info h2{
    font-size:50px;
    line-height:1.1;
    margin-bottom:15px;
}

.booking-info h2 span{
    color:#c6a16a;
}

.booking-info p{
    color:#aaa;
    margin-bottom:20px;
    line-height:1.7;
}

.booking-steps{
    margin-top:30px;
}

.booking-steps div{
    margin-bottom:18px;
    padding-bottom:15px;
    border-bottom:1px solid rgba(255,255,255,0.08);
}

.booking-steps h4{
    color:#d4b27a;
    margin-bottom:5px;
}

/* FORM */
form{
    background:#111;
    padding:40px;
    border-radius:25px;
    border:1px solid rgba(255,255,255,0.08);
}

form input,
form textarea{
    width:100%;
    padding:15px;
    margin-bottom:15px;
    border:none;
    border-radius:12px;
    background:#1b1b1b;
    color:white;
    outline:none;
}

form button{
    width:100%;
    padding:15px;
    border:none;
    border-radius:12px;
    background:#c6a16a;
    color:black;
    font-weight:bold;
    cursor:pointer;
    transition:.3s;
}

form button:hover{
    transform:translateY(-2px);
}

/* CALLING CARD */
.contact-wrapper{
    display:flex;
    justify-content:center;
    align-items:center;
}

.card{
    width:850px;
    background:linear-gradient(145deg,#111,#0a0a0a);
    border-radius:30px;
    overflow:hidden;
    display:grid;
    grid-template-columns:1fr 370px;
    border:1px solid rgba(255,255,255,0.08);
    box-shadow:0 0 40px rgba(0,0,0,0.5);
}

.card-left{
    padding:45px;
}

.small-top{
    color:#9d8357;
    letter-spacing:2px;
    font-size:12px;
    margin-bottom:10px;
}

.card-left h1{
    font-size:90px;
    line-height:0.9;
    margin-bottom:10px;
}

.card-left h1 span{
    color:#c6a16a;
    font-size:40px;
    display:block;
    margin-top:10px;
}

.card-left .booking-text{
    margin-top:20px;
    color:#ccc;
    letter-spacing:2px;
}

.payment{
    margin-top:40px;
}

.payment h3{
    color:#c6a16a;
    margin-bottom:15px;
}

.payment p{
    margin-bottom:10px;
    color:#ddd;
}

.steps{
    margin-top:35px;
}

.steps h4{
    color:#c6a16a;
    margin-bottom:10px;
}

.steps p{
    color:#aaa;
    margin-bottom:15px;
    line-height:1.5;
}

.notice{
    margin-top:30px;
    border:1px solid #c6a16a;
    padding:15px;
    border-radius:12px;
    text-align:center;
    color:#d4b27a;
    font-size:13px;
    letter-spacing:1px;
}

/* RIGHT SIDE */
.card-right{
    background:#f3eee7;
    padding:30px 20px;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    position:relative;
}

.scan{
    background:#c6a16a;
    color:black;
    padding:12px 25px;
    border-radius:10px;
    font-weight:bold;
    margin-bottom:20px;
    font-size:13px;
    letter-spacing:1px;
}

.qr-box{
    background:white;
    padding:20px;
    border-radius:20px;
}

.name{
    margin-top:20px;
    color:#225cff;
    font-size:30px;
    font-weight:bold;
}

.number{
    color:#444;
    margin-top:8px;
}

/* FOOTER */
footer{
    background:#0a0a0a;
    text-align:center;
    padding:30px;
    color:#666;
    border-top:1px solid rgba(255,255,255,0.08);
}

/* MOBILE */
@media(max-width:900px){

.hero h1{
    font-size:60px;
}

.about,
.booking-container,
.card{
    grid-template-columns:1fr;
}

.card{
    width:100%;
}

.card-left h1{
    font-size:60px;
}

.section-title{
    font-size:40px;
}

}
</style>
</head>

<body>

<!-- NAV -->
<nav>
    <a href="#about">About</a>
    <a href="#portfolio">Portfolio</a>
    <a href="#booking">Booking</a>
    <a href="#contact">Calling Card</a>
</nav>

<!-- HERO -->
<div class="hero">
    <h1>BLACK <span>INK</span></h1>
    <p>QUALITY INK. LASTING IMPRESSION.</p>
</div>

<!-- ABOUT -->
<section id="about">
    <div class="about">
        <img src="https://images.unsplash.com/photo-1611501275019-813dfe976a0f?q=80&w=1974&auto=format&fit=crop">

        <div class="about-text">
            <h2>About The Artist</h2>

            <p>
                Black Ink Studio delivers premium tattoo artistry focused on realism,
                custom concepts, Japanese ink, and minimalist designs.
                Every piece is carefully crafted to match your story and style.
            </p>

            <p>
                Safe. Hygienic. Professional. Designed to leave a lasting impression.
            </p>
        </div>
    </div>
</section>

<!-- PORTFOLIO -->
<section id="portfolio">

    <h2 class="section-title">Portfolio</h2>

    <div class="filters">
        <button onclick="filterSelection('all')">All</button>
        <button onclick="filterSelection('realism')">Realism</button>
        <button onclick="filterSelection('japanese')">Japanese</button>
        <button onclick="filterSelection('minimal')">Minimal</button>
    </div>

    <div class="gallery">
        <img src="https://images.unsplash.com/photo-1542728928-1413d1894ed1?q=80&w=1974&auto=format&fit=crop"
        class="realism" onclick="openModal(this)">

        <img src="https://images.unsplash.com/photo-1590246814883-57c5f7b3c6a7?q=80&w=1974&auto=format&fit=crop"
        class="japanese" onclick="openModal(this)">

        <img src="https://images.unsplash.com/photo-1604881991720-f91add269bed?q=80&w=1974&auto=format&fit=crop"
        class="minimal" onclick="openModal(this)">

        <img src="https://images.unsplash.com/photo-1617050318658-7f1c1a6f0f34?q=80&w=1974&auto=format&fit=crop"
        class="realism" onclick="openModal(this)">
    </div>
</section>

<!-- BOOKING -->
<section id="booking">

<div class="booking-container">

    <div class="booking-info">
        <h2>TATTOO <span>BOOKING</span></h2>

        <p>
            Now accepting bookings for custom tattoo sessions.
            Secure your appointment with a reservation fee.
        </p>

        <div class="booking-steps">

            <div>
                <h4>Send Your Design</h4>
                <p>Reference images are highly encouraged.</p>
            </div>

            <div>
                <h4>Preferred Date & Time</h4>
                <p>We'll confirm availability after inquiry.</p>
            </div>

            <div>
                <h4>Placement & Size</h4>
                <p>This helps us estimate session duration.</p>
            </div>

        </div>

        <div class="notice">
            DOWNPAYMENT IS REQUIRED TO SECURE YOUR SLOT.
        </div>
    </div>

    <!-- FORM -->
    <form action="https://formspree.io/f/mnjldyqb" method="POST">

        <input type="text" name="name" placeholder="Full Name" required>

        <input type="email" name="email" placeholder="Email Address" required>

        <input type="text" name="idea" placeholder="Tattoo Idea">

        <textarea name="message" rows="6"
        placeholder="Describe your tattoo..."></textarea>

        <button type="submit">BOOK APPOINTMENT</button>

    </form>

</div>

</section>

<!-- CALLING CARD -->
<section id="contact">

<h2 class="section-title">Calling Card</h2>

<div class="contact-wrapper">

<div class="card">

    <!-- LEFT -->
    <div class="card-left">

        <div class="small-top">
            QUALITY INK. LASTING IMPRESSION.
        </div>

        <h1>
            TATTOO
            <span>APPOINTMENT BOOKING</span>
        </h1>

        <div class="booking-text">
            NOW ACCEPTING BOOKINGS
        </div>

        <div class="payment">
            <h3>PAYMENT VIA GCASH</h3>

            <p>📞 0906 696 3236</p>
            <p>👤 SA** L N.</p>
        </div>

        <div class="steps">

            <h4>HOW TO BOOK</h4>

            <p>
                • Send your design or idea<br>
                • Choose preferred date & time<br>
                • Placement and size details
            </p>

        </div>

        <div class="notice">
            NO DP = NO RESERVATION
        </div>

    </div>

    <!-- RIGHT -->
    <div class="card-right">

        <div class="scan">
            SCAN TO PAY
        </div>

        <div class="qr-box">
            <div id="qrcode"></div>
        </div>

        <div class="name">SA** L N.</div>

        <div class="number">
            Mobile No: 0906 696 3236
        </div>

    </div>

</div>

</div>
</section>

<footer>
    © 2026 Black Ink Studio
</footer>

<!-- MODAL -->
<div class="modal" id="modal" onclick="closeModal()">
    <img id="modalImg">
</div>

<script>

// QR CODE
new QRCode(document.getElementById("qrcode"), {
    text: "https://instagram.com",
    width: 220,
    height: 220
});

// MODAL
function openModal(img){
    document.getElementById("modal").style.display = "flex";
    document.getElementById("modalImg").src = img.src;
}

function closeModal(){
    document.getElementById("modal").style.display = "none";
}

// FILTER
function filterSelection(category){

    let images = document.querySelectorAll(".gallery img");

    images.forEach(img => {

        if(category === "all"){
            img.style.display = "block";
        }

        else{
            img.style.display =
            img.classList.contains(category)
            ? "block"
            : "none";
        }

    });
}

</script>

</body>
</html>
