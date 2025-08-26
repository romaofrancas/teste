<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DisfrutaGlobal XP Demo</title>
<style>
    body {
        margin: 0;
        font-family: 'Segoe UI';
        background-color: #1A1F2B;
        color: #F5F5F5;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        position: relative;
    }
    .particle, .bubble, .star {
        position: absolute;
        border-radius: 50%;
    }
    .particle { width: 5px; height: 5px; background: #FF451A; opacity: 0.7; }
    .bubble { width: 6px; height: 6px; background: #00BFFF; opacity: 0.5; }
    .star { width: 2px; height: 2px; background: white; animation: twinkle 3s linear infinite alternate; }
    @keyframes float { 0% { transform: translateY(0); } 50% { transform: translateY(-10px); } 100% { transform: translateY(0); } }
    @keyframes rise { 0% { transform: translateY(var(--screenHeight)); } 100% { transform: translateY(-10px); } }
    @keyframes twinkle { 0% { opacity: 0.2; } 100% { opacity: 1; } }

    .container {
        display: flex;
        flex-direction: column;
        gap: 8px;
        width: 90%;
        max-width: 700px;
        background-color: rgba(42,47,66,0.95);
        padding: 15px;
        border-radius: 12px;
        z-index: 10;
        text-align: center;
        max-height: calc(var(--screenHeight) * 0.95px);
        overflow: hidden;
    }
    .logo img { max-width: 250px; margin-bottom: 5px; }
    .experience-selector { margin-bottom: 5px; }
    select { padding: 6px; border-radius: 5px; border: none; font-size: 0.9em; width: 100%; }

    .form-section { 
        background-color: #242A3A; 
        padding: 10px; 
        border-radius: 10px; 
        display: none; 
        flex-direction: column; 
        gap: 6px;
        max-height: 500px;
    }
    .form-section h2 { color: #FF451A; margin-bottom: 6px; font-size: 1.1em; }
    label { display: block; margin: 4px 0 2px; text-align: left; font-size: 0.85em; }
    input, select { width:95%; padding: 5px; border-radius: 4px; border: none; margin-bottom: 4px; font-size: 0.85em; }

    .two-columns { display: flex; justify-content: center; flex-wrap: wrap; gap: 8%; }

    /* Experience details with image side-by-side */
    .experience-wrapper {
        display: flex;
        align-items: flex-start;
        justify-content: space-between;
        gap: 12px;
        background-color: #1F2535;
        padding: 8px;
        border-radius: 8px;
        margin-bottom: 6px;
    }
    .experience-info { 
        text-align: left; 
        font-size: 0.85em; 
        flex: 2; 
    }
    .experience-info h3 { margin-top: 0; color: #FF451A; font-size: 0.95em; }

    .experience-image {
        flex: 1;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .experience-image img {
        max-width: 100px;
        border-radius: 6px;
        opacity: 0.9;
    }

    .booking-btn { background-color: #FF451A; color: #F5F5F5; padding: 6px; width: 100%; border: none; border-radius: 6px; font-weight: bold; cursor: pointer; margin-top: 4px; font-size: 0.9em; }
    .booking-btn:hover { background-color: #e55b00; }
    .support-info { margin-top: 4px; font-weight: bold; color: #FF451A; font-size: 0.85em; }
</style>

<script type="text/javascript" charset="utf-8">
  (function (g, e, n, es, ys) {
    g['_genesysJs'] = e;
    g[e] = g[e] || function () {
      (g[e].q = g[e].q || []).push(arguments)
    };
    g[e].t = 1 * new Date();
    g[e].c = es;
    ys = document.createElement('script'); ys.async = 1; ys.src = n; ys.charset = 'utf-8'; document.head.appendChild(ys);
  })(window, 'Genesys', 'https://apps.usw2.pure.cloud/genesys-bootstrap/genesys.min.js', {
    environment: 'prod-usw2',
    deploymentId: '0b0bee1e-0a3b-4d37-a1fc-f8eb6c463b7c'
  });
</script>

</head>

<body>
<div class="container">
    <!-- Logo -->
    <div class="logo">
        <img src="https://i.im.ge/2025/08/26/nMesWJ.DisfrutaXP.png" alt="DisfrutaGlobal XP Logo">
    </div>

    <!-- Experience Selector -->
    <div class="experience-selector">
        <label for="experienceSelect">Choose your adventure:</label>
        <select id="experienceSelect" onchange="showForm()">
            <option value="" selected disabled>🌟 Select an experience</option>
            <option value="zeroG">🚀 Zero Gravity Flight</option>
            <option value="deepSea">🌊 Deep Water Exploration</option>
            <option value="spaceVisit">🪐 Space Visit</option>
        </select>
    </div>

    <!-- Booking Form -->
    <div class="form-section" id="formSection">
        <h2>Booking Form 🎟️</h2>
        
        <!-- Experience Details with Image -->
        <div class="experience-wrapper">
            <div class="experience-info" id="experienceInfo"></div>
            <div class="experience-image">
                <img id="experienceImg" src="https://via.placeholder.com/100x100.png?text=Select" alt="Experience Image">
            </div>
        </div>

        <div class="two-columns">
            <div>
                <label for="date">📅 Date</label>
                <input type="date" id="date">
            </div>
            <div>
                <label for="participants">👥 Participants</label>
                <input type="number" id="participants" min="1" value="1">
            </div>
            <div>
                <label for="package">💼 Package</label>
                <select id="package">
                    <option>Standard</option>
                    <option>Premium</option>
                    <option>VIP</option>
                </select>
            </div>
            <div>
                <label for="name">👤 Full Name</label>
                <input type="text" id="name">
            </div>
            <div>
                <label for="email">✉️ Email</label>
                <input type="email" id="email">
            </div>
        </div>

        <button class="booking-btn" onclick="alert('Booking submitted! (Demo)')">Check Availability 🎫</button>
        <div class="support-info">📞 Call us for support: +1 402 321 1234</div>
    </div>
</div>

<script>
    const screenWidth = 1280;
    const screenHeight = 720;
    document.documentElement.style.setProperty('--screenHeight', screenHeight);

    const body = document.body;
    let currentExp = '';

    function randomInt(max){ return Math.floor(Math.random()*max); }

    function createAnimation(exp){
        document.querySelectorAll('.particle, .bubble, .star').forEach(e => e.remove());
        const numParticles = 10;
        const numBubbles = 10;
        const numStars = 40;

        if(exp === 'zeroG') {
            for(let i=0;i<numParticles;i++){
                let p = document.createElement('div');
                p.className = 'particle';
                p.style.top = randomInt(screenHeight) + 'px';
                p.style.left = randomInt(screenWidth) + 'px';
                p.style.animation = `float ${3+Math.random()*3}s linear infinite`;
                body.appendChild(p);
            }
        } else if(exp === 'deepSea') {
            for(let i=0;i<numBubbles;i++){
                let b = document.createElement('div');
                b.className = 'bubble';
                b.style.left = randomInt(screenWidth) + 'px';
                b.style.bottom = randomInt(screenHeight) + 'px';
                b.style.animation = `rise ${5+Math.random()*4}s linear infinite`;
                body.appendChild(b);
            }
        } else if(exp === 'spaceVisit') {
            for(let i=0;i<numStars;i++){
                let s = document.createElement('div');
                s.className = 'star';
                s.style.top = randomInt(screenHeight) + 'px';
                s.style.left = randomInt(screenWidth) + 'px';
                s.style.width = s.style.height = `${1+Math.random()*2}px`;
                s.style.animationDuration = `${2+Math.random()*2}s`;
                body.appendChild(s);
            }
        }
    }

    function showForm(){
        const exp = document.getElementById('experienceSelect').value;
        currentExp = exp;
        document.getElementById('formSection').style.display = 'flex';
        createAnimation(exp);
        updateExperience();
    }

    function updateExperience() {
        const info = document.getElementById('experienceInfo');
        const img = document.getElementById('experienceImg');

        if(currentExp === "zeroG") {
            info.innerHTML = `<h3>🚀 Zero Gravity Flight</h3>
                              <ul><li>Duration: 3h</li><li>Min Age: 12</li><li>Location: Earth Orbit Sim</li></ul>`;
            img.src = "https://i.im.ge/2025/08/26/nQtOR6.Zero-Gravity-Flights.png?text=ZeroGravity"; 
        } 
        else if(currentExp === "deepSea") {
            info.innerHTML = `<h3>🌊 Deep Water Exploration</h3>
                              <ul><li>Duration: 6h</li><li>Min Age: 18</li><li>Location: Ocean Depths</li></ul>`;
            img.src = "https://i.im.ge/2025/08/26/nQ0wq0.Deep-Water.png?text=DeepWater"; 
        } 
        else if(currentExp === "spaceVisit") {
            info.innerHTML = `<h3>🪐 Space Visit</h3>
                              <ul><li>Duration: 5 days</li><li>Min Age: 18</li><li>Location: Low Earth Orbit</li></ul>`;
            img.src = "https://i.im.ge/2025/08/26/nQPZQq.Space-visits.png?text=SpaceVisit"; 
        } 
        else {
            img.src = "https://via.placeholder.com/100x100.png?text=Select";
        }
    }
</script>
</body>
</html>
