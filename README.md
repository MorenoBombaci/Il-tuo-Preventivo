<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Preventivo Evento</title>
    <style>
        body {
            background: url(https://i.imgur.com/Tw2djlX.jpeg) no-repeat center center fixed;
            background-size: cover;
            position: relative;
            margin: 0;
            padding: 0;
            height: 100vh;
        }
        body::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.7); /* 30% di trasparenza */
            z-index: -1;
        }
        form {
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            width: 50%;
            margin: 50px auto;
            position: relative;
            z-index: 1;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        label {
            display: block;
            margin-top: 10px;
            font-weight: bold;
        }
        input, select, textarea, button {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background: #007BFF;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
            padding: 10px;
            margin-top: 15px;
        }
        button:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>

    <form>
        <label for="email">Email Cliente:</label>
        <input type="email" id="email" required>
        
        <label for="phone">Numero Cliente:</label>
        <input type="tel" id="phone" required>

        <label for="eventDate">Data dell'Evento:</label>
        <input type="date" id="eventDate" required>

        <label for="eventType">Tipo di Evento:</label>
        <input type="text" id="eventType" placeholder="Es. Matrimonio, Compleanno" required>

        <label for="guests">Numero di Invitati:</label>
        <input type="number" id="guests" required>

        <label for="location">Location:</label>
        <select id="location" required>
            <option value="nostre location">Nostre Location</option>
            <option value="location cliente">Location Cliente</option>
        </select>

        <label for="options">Opzioni:</label>
        <select id="options" required>
            <option value="Ristorazione">Ristorazione</option>
            <option value="Cocktail bar">Cocktail bar</option>
            <option value="Entrambe">Entrambe</option>
        </select>

        <label for="details">Dettagli dell'Evento:</label>
        <textarea id="details" required></textarea>

        <label for="price">Budget per l'Evento (€):</label>
        <input type="number" id="price" required>

        <button type="button" onclick="sendWhatsApp()">Invia WhatsApp</button>
    </form>

    <div id="quoteResult" style="margin-top: 20px;"></div>

    <script>
        function sendWhatsApp() {
            let email = document.getElementById("email").value;
            let phone = document.getElementById("phone").value;
            let eventDate = document.getElementById("eventDate").value;
            let eventType = document.getElementById("eventType").value;
            let guests = document.getElementById("guests").value;
            let location = document.getElementById("location").value;
            let options = document.getElementById("options").value;
            let details = document.getElementById("details").value;
            let price = document.getElementById("price").value;

            if (email && phone && eventDate && eventType && guests && location && options && details && price) {
                let message = `Preventivo per:\n📧 Email: ${email}\n📞 Telefono: ${phone}\n📅 Data Evento: ${eventDate}\n🎉 Tipo di Evento: ${eventType}\n👥 Invitati: ${guests}\n📍 Location: ${location}\n🍽️ Opzioni: ${options}\n📝 Dettagli: ${details}\n💰 Budget: €${price}`;
                let whatsappURL = `https://wa.me/3483294135?text=${encodeURIComponent(message)}`;
                window.open(whatsappURL, '_blank');
            } else {
                alert("Compila tutti i campi!");
            }
        }
    </script>

</body>
</html>
