<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Video Editor Portfolio</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #050505;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    overflow-x: hidden;
}

/* ================= BACKGROUND ================= */

.hero {
    position: relative;
    height: 100vh;
    min-height: 650px;
    overflow: hidden;

    display: flex;
    align-items: center;
    justify-content: center;

    background:
        radial-gradient(circle at 50% 50%, #1b1b1b 0%, #090909 35%, #030303 75%);
}

/* Moving light */

.light {
    position: absolute;
    width: 500px;
    height: 500px;
    border-radius: 50%;

    background: radial-gradient(
        circle,
        rgba(255,255,255,0.12),
        rgba(255,255,255,0) 70%
    );

    filter: blur(20px);

    animation: moveLight 12s infinite alternate ease-in-out;
}

@keyframes moveLight {
    0% {
        transform: translate(-300px,-150px);
    }

    50% {
        transform: translate(250px,100px);
    }

    100% {
        transform: translate(-100px,250px);
    }
}

/* Grid */

.grid {
    position: absolute;
    inset: -50%;
    
    background-image:
        linear-gradient(rgba(255,255,255,0.035) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.035) 1px, transparent 1px);

    background-size: 60px 60px;

    transform: perspective(500px) rotateX(65deg);

    animation: gridMove 10s linear infinite;

    opacity: 0.5;
}

@keyframes gridMove {
    from {
        transform:
            perspective(500px)
            rotateX(65deg)
            translateY(0);
    }

    to {
        transform:
            perspective(500px)
            rotateX(65deg)
            translateY(60px);
    }
}

/* Floating circles */

.orb {
    position: absolute;
    border-radius: 50%;

    border: 1px solid rgba(255,255,255,0.12);

    animation: float 8s infinite ease-in-out;
}

.orb1 {
    width: 220px;
    height: 220px;
    left: 10%;
    top: 15%;
}

.orb2 {
    width: 100px;
    height: 100px;
    right: 15%;
    top: 25%;
    animation-delay: 2s;
}

.orb3 {
    width: 350px;
    height: 350px;
    right: -100px;
    bottom: -100px;
    animation-delay: 4s;
}

@keyframes float {
    0%,100% {
        transform: translateY(0) rotate(0deg);
    }

    50% {
        transform: translateY(-30px) rotate(20deg);
    }
}

/* Noise */

.noise {
    position: absolute;
    inset: 0;

    opacity: 0.06;

    background-image:
        url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.8'/%3E%3C/svg%3E");
}

/* ================= CONTENT ================= */

.content {
    position: relative;
    z-index: 10;

    width: 90%;
    max-width: 1100px;

    text-align: center;
}

/* Small top text */

.small-text {
    opacity: 0;

    letter-spacing: 5px;
    font-size: 12px;
    color: #888;

    animation: fadeUp 1s ease forwards;
    animation-delay: 0.5s;
}

/* NAME */

.name {
    margin-top: 25px;

    font-size: clamp(55px, 11vw, 150px);

    font-weight: 800;

    letter-spacing: -7px;

    line-height: 0.85;

    overflow: hidden;
}

.name span {
    display: inline-block;

    transform: translateY(120%);
    opacity: 0;

    animation: revealName 1.2s cubic-bezier(.16,1,.3,1) forwards;
}

.name span:nth-child(1) {
    animation-delay: 0.8s;
}

.name span:nth-child(2) {
    animation-delay: 0.95s;
}

.name span:nth-child(3) {
    animation-delay: 1.1s;
}

.name span:nth-child(4) {
    animation-delay: 1.25s;
}

.name span:nth-child(5) {
    animation-delay: 1.4s;
}

@keyframes revealName {
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

/* Subtitle */

.subtitle {
    margin-top: 35px;

    font-size: clamp(16px, 2vw, 22px);

    color: #999;

    opacity: 0;

    animation: fadeUp 1s ease forwards;
    animation-delay: 1.8s;
}

/* Button */

.button {
    display: inline-block;

    margin-top: 40px;

    padding: 15px 30px;

    border: 1px solid #444;

    color: white;

    text-decoration: none;

    font-size: 14px;

    opacity: 0;

    animation: fadeUp 1s ease forwards;
    animation-delay: 2.1s;

    transition: 0.4s;
}

.button:hover {
    background: white;
    color: black;

    transform: translateY(-4px);
}

@keyframes fadeUp {
    from {
        opacity: 0;
        transform: translateY(25px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* ================= SCROLL ================= */

.scroll {
    position: absolute;

    bottom: 30px;
    left: 50%;

    transform: translateX(-50%);

    color: #666;

    font-size: 10px;

    letter-spacing: 4px;

    animation: scrollPulse 2s infinite;
}

@keyframes scrollPulse {
    0%,100% {
        opacity: 0.3;
    }

    50% {
        opacity: 1;
    }
}


/* ================= WORK SECTION ================= */

.work {
    padding: 120px 8%;

    background: #080808;
}

.work h2 {
    font-size: clamp(40px,7vw,80px);

    margin-bottom: 60px;
}

.projects {
    display: grid;

    grid-template-columns:
        repeat(auto-fit,minmax(280px,1fr));

    gap: 25px;
}

.project {
    height: 280px;

    background: linear-gradient(
        135deg,
        #191919,
        #0d0d0d
    );

    border: 1px solid #242424;

    display: flex;

    align-items: flex-end;

    padding: 25px;

    transition: 0.5s;
}

.project:hover {
    transform: translateY(-8px);

    border-color: #555;
}

.project h3 {
    font-size: 22px;
}

.project p {
    color: #777;

    margin-top: 5px;
}


/* ================= MOBILE ================= */

@media(max-width:600px) {

    .name {
        letter-spacing: -4px;
    }

    .grid {
        background-size: 40px 40px;
    }

    .orb1 {
        width: 140px;
        height: 140px;
    }

    .orb3 {
        width: 220px;
        height: 220px;
    }
}

</style>
</head>


<body>


<!-- ================= HERO ================= -->

<section class="hero">

    <div class="light"></div>

    <div class="grid"></div>

    <div class="orb orb1"></div>
    <div class="orb orb2"></div>
    <div class="orb orb3"></div>

    <div class="noise"></div>


    <div class="content">

        <div class="small-text">
            VIDEO EDITOR • STORYTELLER
        </div>


        <!-- NAME ANIMATION -->

        <div class="name">

            <span>R</span>
            <span>I</span>
            <span>T</span>
            <span>I</span>
            <span>K</span>

        </div>


        <div class="subtitle">
            Documentary • Business • Technology
        </div>


        <a href="#work" class="button">
            EXPLORE MY WORK →
        </a>

    </div>


    <div class="scroll">
        SCROLL ↓
    </div>

</section>



<!-- ================= WORK ================= -->

<section class="work" id="work">

    <h2>Selected Work</h2>


    <div class="projects">

        <div class="project">

            <div>
                <h3>Business Documentary</h3>

                <p>
                    Storytelling & Motion Graphics
                </p>
            </div>

        </div>


        <div class="project">

            <div>
                <h3>Technology Documentary</h3>

                <p>
                    Visual Storytelling
                </p>
            </div>

        </div>


        <div class="project">

            <div>
                <h3>Motion Graphics</h3>

                <p>
                    Information Design
                </p>
            </div>

        </div>

    </div>

</section>


</body>
</html>
