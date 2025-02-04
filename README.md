<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inviaci Gratuitamente il Tuo Preventivo!</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            background-color: #f8f8f8;
        }
        .container {
            max-width: 600px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0,0,0,0.1);
        }
        label {
            font-weight: bold;
        }
        input, textarea, select {
            width: 100%;
            padding: 8px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #25D366;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #1EBE5D;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Inviaci il Tuo Preventivo!</h2>
        <form id="quoteForm">
            <label for="customer">Nome Cliente:</label>
            <input type="text" id="customer" required>
            
            <label for="email">Email Cliente / Numero Cliente:</label>
            <input type="email" id="email" required>
            
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
    </div>

    <script>
        function sendWhatsApp() {
            let customer = document.getElementById("customer").value;
            let email = document.getElementById("email").value;
            let eventType = document.getElementById("eventType").value;
            let guests = document.getElementById("guests").value;
            let location = document.getElementById("location").value;
            let options = document.getElementById("options").value;
            let details = document.getElementById("details").value;
            let price = document.getElementById("price").value;

            if (customer && email && eventType && guests && location && options && details && price) {
                let message = `Preventivo per: ${customer}\nEmail: ${email}\nEvento: ${eventType}\nInvitati: ${guests}\nLocation: ${location}\nOpzioni: ${options}\nDettagli: ${details}\nBudget: €${price}`;
                let whatsappURL = `https://wa.me/3483294135?text=${encodeURIComponent(message)}`;
                window.open(whatsappURL, '_blank');
            } else {
                alert("Compila tutti i campi!");
            }
        }
    </script>
</body>
</html>
