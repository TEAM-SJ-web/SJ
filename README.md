# SJ
Shopping wab
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ElectroDeals - Home</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f2f2f2; }
    header { background-color: #232f3e; padding: 1rem; color: white; text-align: center; }
    .products { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; padding: 1rem; }
    .product { background: white; padding: 1rem; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
    .product img { width: 100%; height: 150px; object-fit: contain; }
    .btn { background: #ffa41c; color: black; padding: 0.5rem 1rem; border: none; cursor: pointer; margin-top: 0.5rem; }
    .details, .order { padding: 1rem; max-width: 600px; margin: auto; background: white; margin-top: 1rem; border-radius: 8px; }
  </style>
</head>
<body>
  <header>
    <h1>ElectroDeals</h1>
    <p>सस्ते इलेक्ट्रॉनिक प्रोडक्ट्स - Phones, Watches, Headphones</p>
  </header>

  <div class="products" id="product-list"></div>

  <div class="details" id="product-details" style="display: none;"></div>
  <div class="order" id="order-page" style="display: none;"></div>

  <script>
    const products = [
      { id: 1, name: 'Budget Smartphone', price: 3999, desc: '4G Phone with 2GB RAM', img: 'https://via.placeholder.com/200x150?text=Phone' },
      { id: 2, name: 'Smart Watch', price: 999, desc: 'Fitness watch with heart rate monitor', img: 'https://via.placeholder.com/200x150?text=Watch' },
      { id: 3, name: 'Wireless Headphones', price: 799, desc: 'Bluetooth Headphones with mic', img: 'https://via.placeholder.com/200x150?text=Headphones' },
    ];

    const productList = document.getElementById('product-list');
    const productDetails = document.getElementById('product-details');
    const orderPage = document.getElementById('order-page');

    function showProducts() {
      productList.innerHTML = '';
      products.forEach(product => {
        const div = document.createElement('div');
        div.className = 'product';
        div.innerHTML = `
          <img src="${product.img}" />
          <h3>${product.name}</h3>
          <p>₹${product.price}</p>
          <button class="btn" onclick="viewDetails(${product.id})">View</button>
        `;
        productList.appendChild(div);
      });
    }

    function viewDetails(id) {
      const product = products.find(p => p.id === id);
      productDetails.innerHTML = `
        <h2>${product.name}</h2>
        <img src="${product.img}" style="width: 100%; max-width: 300px;" />
        <p>${product.desc}</p>
        <h3>Price: ₹${product.price}</h3>
        <button class="btn" onclick="orderProduct(${product.id})">Buy Now</button>
      `;
      productDetails.style.display = 'block';
      orderPage.style.display = 'none';
    }

    function orderProduct(id) {
      const product = products.find(p => p.id === id);
      orderPage.innerHTML = `
        <h2>Order: ${product.name}</h2>
        <p>Total Price: ₹${product.price}</p>
        <p>UPI ID पर भुगतान करें: <strong>9216354463@amazon.pay</strong></p>
        <p>Payment करने के बाद, कृपया स्क्रीनशॉट और अपना पता हमें Email या WhatsApp पर भेजें।</p>
        <p><em>Note: Cash on Delivery उपलब्ध नहीं है।</em></p>
      `;
      productDetails.style.display = 'none';
      orderPage.style.display = 'block';
    }

    showProducts();
  </script>
</body>
</html>
