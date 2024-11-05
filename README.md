<!DOCTYPE html>
<html lang="sk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Donna Taxi - Pre ženy</title>
    <style>
        /* CSS styling */
        body {
            font-family: Arial, sans-serif;
            background-color: #ffeef0;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #333;
            overflow-x: hidden;
            min-height: 100vh;
        }
        .app-container {
            width: 100%;
            max-width: 450px;
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            text-align: center;
            animation: fadeIn 1.5s ease;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .header {
            background-color: #ff66a1;
            color: white;
            padding: 15px 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }
        .header img {
            width: 60px;
            height: auto;
            margin-right: 10px;
            border-radius: 50%;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .header h2 {
            font-size: 1.6em;
            margin: 0;
            font-weight: 700;
            animation: slideInLeft 1s ease;
        }
        @keyframes slideInLeft {
            from { opacity: 0; transform: translateX(-50px); }
            to { opacity: 1; transform: translateX(0); }
        }
        .map-simulation {
            width: 100%;
            height: 250px;
            background: url('https://maps.googleapis.com/maps/api/staticmap?center=Bratislava,Slovakia&zoom=13&size=400x250&key=YOUR_API_KEY') no-repeat center center;
            background-size: cover;
            filter: brightness(0.8);
            position: relative;
        }
        .map-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.2);
        }
        .info-card {
            padding: 25px;
            animation: fadeInUp 1.5s ease;
        }
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .ride-button {
            background-color: #ff66a1;
            color: white;
            padding: 15px;
            font-size: 1.2em;
            margin-top: 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.3s, transform 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 100%;
            max-width: 300px;
            margin: 20px auto;
        }
        .ride-button:hover {
            background-color: #ff3380;
            transform: translateY(-2px);
        }
        .status {
            font-size: 1.1em;
            color: #555;
            margin-top: 15px;
            opacity: 1;
            transition: opacity 0.3s ease;
        }
        .status.hidden {
            opacity: 0;
        }
        .icon {
            width: 30px;
            margin-right: 8px;
        }
        .section-title {
            font-size: 1.3em;
            color: #ff66a1;
            margin: 30px 0 10px;
            animation: fadeInDown 1.5s ease;
        }
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .testimonials, .benefits, .contact-form {
            padding: 20px;
            text-align: left;
            color: #333;
            animation: fadeIn 1.5s ease;
        }
        .testimonials p, .benefits p {
            font-style: italic;
            color: #666;
        }
        .footer {
            background-color: #ffeef0;
            padding: 15px;
            color: #777;
            font-size: 0.9em;
            font-weight: 500;
        }
        .contact-form input, .contact-form textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            transition: border-color 0.3s;
        }
        .contact-form input:focus, .contact-form textarea:focus {
            border-color: #ff66a1;
            outline: none;
        }
        .contact-form button {
            width: 100%;
            padding: 12px;
            background-color: #ff66a1;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
            transition: background 0.3s;
        }
        .contact-form button:hover {
            background-color: #ff3380;
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Header with Logo -->
        <div class="header">
            <img src="logo.png" alt="Donna Taxi Logo">
            <h2>Donna Taxi - Pre ženy</h2>
        </div>
        
        <!-- Map Section with Overlay -->
        <div class="map-simulation">
            <div class="map-overlay"></div>
        </div>
        
        <!-- Info Section -->
        <div class="info-card">
            <p>Bezpečná a spoľahlivá doprava pre ženy, poskytovaná profesionálnymi vodičkami.</p>
            <button class="ride-button" onclick="requestRide()">
                <img src="car-icon.png" alt="Taxi icon" class="icon">
                Objednať jazdu
            </button>
            <div class="status" id="statusMessage">Pripravené na objednanie jazdy!</div>
        </div>

        <!-- Benefits Section -->
        <div class="benefits">
            <h3 class="section-title">Výhody našich služieb</h3>
            <p>✔️ Pohodlné a bezpečné cesty</p>
            <p>✔️ Profesionálne vodičky</p>
            <p>✔️ Služby 24/7</p>
        </div>

        <!-- Testimonials Section -->
        <div class="testimonials">
            <h3 class="section-title">Recenzie</h3>
            <p>"Úžasná skúsenosť! Cítila som sa bezpečne a pohodlne." - Jana</p>
            <p>"Donna Taxi je presne to, čo som hľadala." - Veronika</p>
        </div>

        <!-- Contact Form Section -->
        <div class="contact-form">
            <h3 class="section-title">Kontaktujte nás</h3>
            <input type="text" placeholder="Vaše meno">
            <input type="email" placeholder="Váš email">
            <textarea placeholder="Vaša správa" rows="4"></textarea>
            <button>Odoslať</button>
        </div>

        <!-- Footer -->
        <div class="footer">
            © 2024 Donna Taxi - Všetky práva vyhradené
        </div>
    </div>

    <script>
        // JavaScript function to simulate requesting a ride
        function requestRide() {
            const statusMessage = document.getElementById("statusMessage");
            statusMessage.classList.add("hidden");
            statusMessage.innerText = "Hľadáme vodičku...";
            setTimeout(() => {
                statusMessage.classList.remove("hidden");
                statusMessage.innerText = "Vodička nájdená! Príde za 5 minút.";
            }, 2000);
        }
    </script>
</body>
</html>
