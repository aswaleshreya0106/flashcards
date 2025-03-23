# flashcards
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Brand Name Flashcards</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            background-color: #E6E6FA;
            font-family: Arial, sans-serif;
            height: 100vh;
        }
        .container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 20px;
            justify-content: center;
            align-items: center;
            max-width: 100%; height: 100vh;
        }
        .flashcard {
            width: 120px;
            height: 150px;
            perspective: 1000px;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
        }
        .card {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.6s ease-in-out;
        }
        .card.flipped {
            transform: rotateY(180deg);
        }
        .card-face {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            font-weight: bold;
            border-radius: 10px;
        }
        .front {
            background-color: #D8BFD8;
            color: #4A235A;
        }
        .back {
            background-color: #BA55D3;
            color: white;
            transform: rotateY(180deg);
        }
    </style>
</head>
<body>
    <div class="container" id="flashcards"></div>

    <script>
        const alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        const words = ["Apple", "Balenciaga", "Chanel", "Dior", "Estee Lauder", "Fendi", "Gucci", "Hermes", "Intel", "Jaguar", 
                       "Kellogg's", "Louis Vuitton", "Mercedes-Benz", "Nike", "Olay", "Prada", "Quiksilver", "Rolex", "Samsung", "Tesla", 
                       "Under Armour", "Versace", "Walmart", "Xiaomi", "Yamaha", "Zara"];
        
        const container = document.getElementById("flashcards");

        alphabet.split("").forEach((letter, index) => {
            const flashcard = document.createElement("div");
            flashcard.className = "flashcard";
            flashcard.innerHTML = `
                <div class="card">
                    <div class="card-face front">${letter}</div>
                    <div class="card-face back">${words[index]}</div>
                </div>
            `;
            flashcard.addEventListener("click", () => {
                flashcard.querySelector(".card").classList.toggle("flipped");
            });
            container.appendChild(flashcard);
        });
    </script>
</body>
</html>
