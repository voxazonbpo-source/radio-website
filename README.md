
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Radio Voxa</title>
    <style>
        /* General Body and Container Styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f0f2f5;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .container {
            max-width: 600px;
            width: 100%;
            background-color: #fff;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 30px;
        }

        /* Radio Player Section Styles */
        .radio-player-container {
            width: 300px;
            height: 800px;
            background: linear-gradient(45deg, #007bff, #17a2b8);
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-around;
            color: white;
            padding: 10px;
            position: relative;
            overflow: hidden;
        }

        .title-container {
            text-align: center;
            margin-bottom: 5px;
        }

        .player-title {
            font-size: 1.2em;
            font-weight: bold;
            margin: 0;
            color: white;
        }

        .station-name {
            font-size: 0.9em;
            font-weight: normal;
            margin: 5px 0 0;
            color: #e0e0e0;
        }

        .logo-container {
            position: relative;
            width: 100px;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: 5px;
        }

        .radio-logo {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            background-color: #34495e;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .radio-logo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .neon-border {
            position: absolute;
            width: 100px;
            height: 100px;
            border-radius: 50%;
            border: 3px solid #00f0ff;
            box-shadow: 0 0 8px #00f0ff, 0 0 15px #00f0ff;
            animation: neon-blink 1.5s infinite ease-in-out;
        }

        @keyframes neon-blink {
            0%, 100% {
                opacity: 0.8;
                transform: scale(1);
            }
            50% {
                opacity: 1;
                transform: scale(1.05);
            }
        }

        .status-indicator {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .status-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
        }

        .status-dot.live {
            background-color: green;
            box-shadow: 0 0 5px green, 0 0 10px green;
            animation: live-blink 1s infinite;
        }

        .status-dot.stopped {
            background-color: red;
            box-shadow: 0 0 5px red, 0 0 10px red;
            animation: none;
        }

        @keyframes live-blink {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.5;
            }
        }

        .status-text {
            font-size: 12px;
            font-weight: bold;
        }

        .controls {
            display: flex;
            gap: 20px;
            align-items: center;
            justify-content: center;
            margin-top: 10px;
        }

        .control-button {
            background: none;
            border: none;
            cursor: pointer;
            color: white;
            font-size: 20px;
            transition: transform 0.2s;
        }

        .control-button:hover {
            transform: scale(1.2);
        }

        .volume-slider-container {
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            margin-top: 10px;
        }

        .volume-slider {
            width: 80%;
            -webkit-appearance: none;
            appearance: none;
            height: 6px;
            background: #e0e0e0;
            border-radius: 5px;
            outline: none;
            cursor: pointer;
        }

        .volume-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 18px;
            height: 18px;
            background: white;
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 0 5px #00f0ff;
        }

        .volume-slider::-moz-range-thumb {
            width: 18px;
            height: 18px;
            background: white;
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 0 5px #00f0ff;
        }

        .extra-controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 10px;
        }

        .mute-button, .refresh-button {
            background: none;
            border: none;
            cursor: pointer;
            color: white;
            font-size: 18px;
            transition: transform 0.2s;
        }

        .mute-button:hover, .refresh-button:hover {
            transform: scale(1.2);
        }

        /* Contact Us Section Styles */
        .contact-section {
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .contact-title {
            font-size: 1.5em;
            color: #333;
            margin-bottom: 20px;
        }
        
        .contact-form {
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .contact-form input,
        .contact-form textarea {
            width: calc(100% - 20px);
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1em;
            transition: border-color 0.3s;
        }

        .contact-form input:focus,
        .contact-form textarea:focus {
            outline: none;
            border-color: #007bff;
        }

        .contact-button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 12px 20px;
            font-size: 1em;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }

        .contact-button:hover {
            background-color: #0056b3;
            transform: translateY(-2px);
        }

        .email-info {
            font-size: 0.9em;
            color: #666;
            margin-top: 10px;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />
</head>
<body>

<div class="container">
    <!-- Radio Player Section -->
    <div class="radio-player-container">
        <div class="status-indicator">
            <div id="status-dot" class="status-dot stopped"></div>
            <div id="status-text" class="status-text">Off Air</div>
        </div>
        <div class="title-container">
            <h2 class="player-title">Radio Voxa</h2>
            <p class="station-name">"മലയാളി തൻ സ്വന്തം സ്വരം"</p>
        </div>
        <div class="logo-container">
            <div class="neon-border"></div>
            <div class="radio-logo">
                <img src="https://i.ibb.co/Swx33RXg/FB-IMG-1755540998913.jpg" alt="Radio Logo" />
            </div>
        </div>
        <audio id="radio-audio" src="https://stream.zeno.fm/kezsc0y2wwzuv"></audio>
        <div class="controls">
            <button id="play-button" class="control-button">
                <i class="fas fa-play"></i>
            </button>
            <button id="stop-button" class="control-button">
                <i class="fas fa-stop"></i>
            </button>
        </div>
        <div class="volume-slider-container">
            <input type="range" id="volume-slider" class="volume-slider" min="0" max="100" value="50" />
        </div>
        <div class="extra-controls">
            <button id="mute-button" class="mute-button">
                <i id="mute-icon" class="fas fa-volume-up"></i>
            </button>
            <button id="refresh-button" class="refresh-button">
                <i class="fas fa-sync-alt"></i>
            </button>
        </div>
    </div>

    <!-- Contact Us Section -->
    <div class="contact-section">
        <h3 class="contact-title">Contact Us</h3>
        <p>Send us your messages, requests, or feedback.</p>
        <form id="contact-form" class="contact-form">
            <input type="text" id="name" placeholder="Your Name" required>
            <input type="email" id="email" placeholder="Your Email" required>
            <textarea id="message" rows="5" placeholder="Your Message" required></textarea>
            <button type="submit" class="contact-button">Send Message</button>
        </form>
    </div>
</div>

<script>
    // Radio Player Script (unchanged)
    const radio = document.getElementById('radio-audio');
    const playButton = document.getElementById('play-button');
    const stopButton = document.getElementById('stop-button');
    const statusDot = document.getElementById('status-dot');
    const statusText = document.getElementById('status-text');
    const volumeSlider = document.getElementById('volume-slider');
    const muteButton = document.getElementById('mute-button');
    const muteIcon = document.getElementById('mute-icon');
    const refreshButton = document.getElementById('refresh-button');
    
    // Initial setup
    radio.volume = volumeSlider.value / 100;
    let lastVolume = radio.volume;

    playButton.addEventListener('click', () => {
        radio.play();
        statusDot.classList.remove('stopped');
        statusDot.classList.add('live');
        statusText.textContent = 'On Air';
    });

    stopButton.addEventListener('click', () => {
        radio.pause();
        statusDot.classList.remove('live');
        statusDot.classList.add('stopped');
        statusText.textContent = 'Off Air';
    });

    volumeSlider.addEventListener('input', () => {
        const volume = volumeSlider.value / 100;
        radio.volume = volume;
        if (radio.volume === 0) {
            muteIcon.classList.remove('fa-volume-up');
            muteIcon.classList.add('fa-volume-mute');
        } else {
            muteIcon.classList.remove('fa-volume-mute');
            muteIcon.classList.add('fa-volume-up');
        }
        lastVolume = radio.volume;
    });

    muteButton.addEventListener('click', () => {
        if (radio.volume > 0) {
            lastVolume = radio.volume;
            radio.volume = 0;
            volumeSlider.value = 0;
            muteIcon.classList.remove('fa-volume-up');
            muteIcon.classList.add('fa-volume-mute');
        } else {
            radio.volume = lastVolume;
            volumeSlider.value = lastVolume * 100;
            muteIcon.classList.remove('fa-volume-mute');
            muteIcon.classList.add('fa-volume-up');
        }
    });

    refreshButton.addEventListener('click', () => {
        location.reload();
    });

    // Contact Form Script
    const contactForm = document.getElementById('contact-form');
    
    contactForm.addEventListener('submit', function(event) {
        event.preventDefault();
        
        const name = document.getElementById('name').value;
        const email = document.getElementById('email').value;
        const message = document.getElementById('message').value;
        
        const subject = `Message from ${name} via Radio Voxa Website`;
        const body = `Name: ${name}\nEmail: ${email}\n\nMessage:\n${message}`;
        
        // Use mailto: to open the default email client
        window.location.href = `mailto:radiovoxa@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
    });
</script>

</body>
</html>
