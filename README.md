# Tienda-kawaii-Bren
Papelería y cositas kawaii
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tienda Kawaii</title>
<style>
/* Reset */
* { margin:0; padding:0; box-sizing:border-box; font-family: 'Comic Sans MS', cursive, sans-serif; }

body { background: #ffe4f2; color: #333; }

header {
    background: #ffb6c1;
    padding: 20px;
    text-align: center;
    position: sticky;
    top:0;
    z-index:100;
}

header h1 { font-size: 2.5em; color: white; text-shadow: 1px 1px #ff69b4; }

nav a { color: white; text-decoration: none; margin: 0 15px; font-weight: bold; transition: transform 0.2s; }
nav a:hover { transform: scale(1.1); }

.banner {
    background: url('https://i.imgur.com/PL4Iz6I.jpg') center/cover no-repeat;
    height: 300px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 2em;
    text-shadow: 2px 2px #ff69b4;
}

.container { padding: 20px; max-width: 1200px; margin: auto; }

h2 { color: #ff69b4; margin-bottom: 15px; text-align: center; }

.grid { display: grid; grid-template-columns: repeat(auto-fill,minmax(200px,1fr)); gap: 20px; }

.product-card {
    background: #fff0f5;
    border: 2px solid #ffb6c1;
    border-radius: 15px;
    padding: 15px;
    text-align: center;
    transition: transform 0.2s, box-shadow 0.2s;
}

.product-card:hover { transform: translateY(-5px); box-shadow: 0 5px 15px rgba(255,105,180,0.4); }

.product-card img { width: 100%; border-radius: 10px; }

.product-card button {
    margin-top: 10px;
    padding: 10px 15px;
    background: #ff69b4;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background 0.2s;
}
.product-card button:hover { background: #ff1493; }

#cart {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #ff69b4;
    color: white;
    padding: 10px 15px;
    border-radius: 50px;
    cursor: pointer;
    font-weight: bold;
    z-index: 1000;
}

#cart-count { font-weight: bold; }

.cart-modal {
    display: none;
    position: fixed;
    top: 80px;
    right: 20px;
    width: 300px;
    max-height: 400px;
    background: #fff0f5;
    border: 2px solid #ffb6c1;
    border-radius: 15px;
    overflow-y: auto;
    padding: 15px;
    z-index: 1000;
}

.cart-modal h3 { text-align: center; margin-bottom: 10px; }

.cart-item { display: flex; justify-content: space-between; margin-bottom: 10px; }

.cart-item button {
    background: #ff69b4;
    border:none;
    border-radius:5px;
    color:white;
    cursor:pointer;
    padding:2px 6px;
    font-size:0.9em;
}

footer { background: #ffb6c1; padding: 20px; text-align: center; color: white; }

form input, form textarea {
    width: 100%;
    padding: 10px;
    margin: 5px 0 15px;
    border-radius: 10px;
    border: 2px solid #ff69b4;
}

form button { padding: 10px 20px; background: #ff69b4; color: white; border: none; border-radius: 10px; cursor: pointer; transition: background 0.2s; }
form button:hover { background: #ff1493; }

@media(max-width:600px){
    header h1 { font-size: 2em; }
    .banner { font-size: 1.5em; }
}
</style>
</head>
<body>

<header>
    <h1>Tienda Kawaii</h1>
    <nav>
        <a href="#inicio">Inicio</a>
        <a href="#catalogo">Catálogo</a>
        <a href="#contacto">Contacto</a>
    </nav>
</header>

<div id="cart">🛒 Carrito (<span id="cart-count">0</span>)</div>

<div class="cart-modal" id="cart-modal">
    <h3>Tu Carrito</h3>
    <div id="cart-items"></div>
    <p><strong>Total:</strong> $<span id="cart-total">0</span> MXN</p>
    <button onclick="checkout()">Finalizar Compra</button>
</div>

<section id="inicio" class="banner">
    ¡Bienvenido a tu mundo kawaii!
</section>

<section id="catalogo" class="container">
    <h2>Productos Destacados</h2>
    <div class="grid">
        <div class="product-card" data-name="Cuaderno Kawaii" data-price="150">
            <img src="https://i.imgur.com/XbYJz1v.jpg" alt="Cuaderno Kawaii">
            <h3>Cuaderno Kawaii</h3>
            <p>$150 MXN</p>
            <button onclick="addToCart(this)">Agregar al carrito</button>
        </div>
        <div class="product-card" data-name="Bolígrafo Cute" data-price="45">
            <img src="https://i.imgur.com/pSjJh7l.jpg" alt="Bolígrafo Cute">
            <h3>Bolígrafo Cute</h3>
            <p>$45 MXN</p>
            <button onclick="addToCart(this)">Agregar al carrito</button>
        </div>
        <div class="product-card" data-name="Pluma de Estrella" data-price="60">
            <img src="https://i.imgur.com/QPjzW1N.jpg" alt="Pluma de Estrella">
            <h3>Pluma de Estrella</h3>
            <p>$60 MXN</p>
            <button onclick="addToCart(this)">Agregar al carrito</button>
        </div>
        <div class="product-card" data-name="Sticker Pack" data-price="30">
            <img src="https://i.imgur.com/Zi2By0K.jpg" alt="Sticker Pack">
            <h3>Sticker Pack</h3>
            <p>$30 MXN</p>
            <button onclick="addToCart(this)">Agregar al carrito</button>
        </div>
    </div>
</section>

<section id="contacto" class="container">
    <h2>Contacto</h2>
    <form>
        <input type="text" placeholder="Nombre" required>
        <input type="email" placeholder="Correo" required>
        <textarea placeholder="Mensaje" rows="4" required></textarea>
        <button type="submit">Enviar</button>
    </form>
</section>

<footer>
    © 2026 Tienda Kawaii | Síguenos en Instagram y WhatsApp
</footer>

<script>
let cart = [];

function addToCart(button) {
    const card = button.parentElement;
    const name = card.dataset.name;
    const price = parseFloat(card.dataset.price);
    const item = cart.find(i => i.name === name);

    if(item) {
        item.qty +=1;
    } else {
        cart.push({name:name, price:price, qty:1});
    }
    updateCart();
}

function updateCart() {
    const cartCount = document.getElementById('cart-count');
    const cartItems = document.getElementById('cart-items');
    const cartTotal = document.getElementById('cart-total');

    let totalQty = 0;
    let totalPrice = 0;
    cartItems.innerHTML = '';

    cart.forEach(item => {
        totalQty += item.qty;
        totalPrice += item.qty * item.price;

        const div = document.createElement('div');
        div.className = 'cart-item';
        div.innerHTML = `
            ${item.name} x${item.qty} - $${item.price*item.qty}
            <button onclick="removeFromCart('${item.name}')">❌</button>
        `;
        cartItems.appendChild(div);
    });

    cartCount.textContent = totalQty;
    cartTotal.textContent = totalPrice;
}

function removeFromCart(name) {
    cart = cart.filter(item => item.name !== name);
    updateCart();
}

const cartBtn = document.getElementById('cart');
const cartModal = document.getElementById('cart-modal');

cartBtn.addEventListener('click', () => {
    cartModal.style.display = cartModal.style.display === 'block' ? 'none' : 'block';
});

function checkout() {
    if(cart.length === 0){
        alert("Tu carrito está vacío!");
        return;
    }
    let message = "Hola, quiero comprar estos productos:\n";
    cart.forEach(item => {
        message += `${item.name} x${item.qty} - $${item.price*item.qty} MXN\n`;
    });
    message += `Total: $${cart.reduce((a,b)=>a+b.price*b.qty,0)} MXN`;
    alert(message);
    cart = [];
    updateCart();
    cartModal.style.display = 'none';
}
</script>

</body>
</html>
