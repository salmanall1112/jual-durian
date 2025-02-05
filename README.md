# jual-durian
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jual Durian Online</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f8f9fa;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        .product {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }
        .product img {
            width: 100px;
            height: 100px;
            object-fit: cover;
            border-radius: 5px;
        }
        button {
            padding: 10px;
            background: #28a745;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background: #218838;
        }
        #cart {
            margin-top: 20px;
            padding: 10px;
            background: #fff;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        #cart-items {
            list-style-type: none;
            padding: 0;
        }
        .payment-method {
            margin-top: 10px;
        }
        .contact {
            margin-top: 20px;
            padding: 10px;
            background: #fff;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Toko Durian Online</h1>
        <p>Jual berbagai jenis durian segar dan berkualitas!</p>
        
        <div class="product">
            <img src="musangking.jpg" alt="Durian Musang King">
            <span>Durian Musang King - Rp 200.000/kg</span>
            <button onclick="addToCart('Durian Musang King', 200000)">Beli</button>
        </div>
        <div class="product">
            <img src="montong.jpg" alt="Durian Montong">
            <span>Durian Montong - Rp 150.000/kg</span>
            <button onclick="addToCart('Durian Montong', 150000)">Beli</button>
        </div>
        <div class="product">
            <img src="lokal.jpg" alt="Durian Lokal">
            <span>Durian Lokal - Rp 100.000/kg</span>
            <button onclick="addToCart('Durian Lokal', 100000)">Beli</button>
        </div>
    </div>
    
    <div class="container" id="cart">
        <h2>Keranjang Belanja</h2>
        <ul id="cart-items"></ul>
        <p><strong>Total: Rp <span id="total-price">0</span></strong></p>
        <div class="payment-method">
            <label>Pilih Metode Pembayaran:</label>
            <select id="payment-method">
                <option value="cash">Cash</option>
                <option value="debit">Debit</option>
            </select>
        </div>
        <button onclick="checkout()">Bayar</button>
    </div>
    
    <div class="container contact">
        <h2>Hubungi Penjual</h2>
        <p>Jika ingin memesan di kemudian hari, hubungi kami di:</p>
        <p><strong>Telepon/WhatsApp: <a href="tel:+6287898769807">+62 878-9876-9807</a></strong></p>
    </div>
    
    <script>
        let cart = [];
        
        function addToCart(name, price) {
            cart.push({ name, price });
            updateCart();
        }
        
        function updateCart() {
            let cartList = document.getElementById("cart-items");
            let totalPrice = document.getElementById("total-price");
            cartList.innerHTML = "";
            let total = 0;
            cart.forEach(item => {
                let li = document.createElement("li");
                li.textContent = `${item.name} - Rp ${item.price.toLocaleString()}`;
                cartList.appendChild(li);
                total += item.price;
            });
            totalPrice.textContent = total.toLocaleString();
        }
        
        function checkout() {
            if (cart.length === 0) {
                alert("Keranjang belanja kosong!");
                return;
            }
            let paymentMethod = document.getElementById("payment-method").value;
            let totalAmount = cart.reduce((sum, item) => sum + item.price, 0).toLocaleString();
            alert(`Terima kasih telah berbelanja!\nTotal pembayaran: Rp ${totalAmount}\nMetode pembayaran: ${paymentMethod}`);
            cart = [];
            updateCart();
        }
    </script>
</body>
</html>
