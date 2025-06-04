<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Catálogo de Produtos 1kg</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f7f7f7;
      margin: 20px;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    .product-list {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
    }
    .product {
      background-color: #fff;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 10px;
      margin: 10px;
      width: 240px;
      text-align: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .product h2 {
      font-size: 16px;
      margin: 10px 0;
    }
    .product p {
      margin: 5px 0;
    }
    .quantity-controls {
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .quantity-controls button {
      padding: 5px 10px;
      font-size: 16px;
      margin: 0 5px;
      cursor: pointer;
    }
    .cart-button {
      display: block;
      margin: 20px auto;
      padding: 10px 20px;
      font-size: 18px;
      background-color: #25D366;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1>Catálogo de Produtos (1kg)</h1>
  <div class="product-list" id="productList"></div>
  <button class="cart-button" onclick="finalizarCompra()">Finalizar Compra</button>

  <script>
    const produtos = [
      { nome: "Aveia flocos grossos (sem glúten)", preco: 22.9 },
      { nome: "Aveia flocos médios (sem glúten)", preco: 22.9 },
      { nome: "Açúcar demerara Nativa", preco: 17.95 },
      { nome: "Alho em flocos desidratado", preco: 50.5 },
      { nome: "Ameixa sem caroço (tam. 110/132)", preco: 42.9 },
      { nome: "Amêndoas cruas (tam. 25/27)", preco: 79.05 },
      { nome: "Amido de Milho", preco: 18.5 },
      { nome: "Banana passa", preco: 33.9 },
      { nome: "Bicarbonato de sódio", preco: 20.8 },
      { nome: "Cacau em pó alcalino", preco: 37.5 },
      { nome: "Camomila flor", preco: 48 },
      { nome: "Canela em pó pura", preco: 31.7 },
      { nome: "Castanha de caju W1 inteira", preco: 74.5 },
      { nome: "Castanha de caju banda torrada (Sem sal)", preco: 57.9 },
      { nome: "Castanha do Pará ferida (assumido “média”)", preco: 146.9 },
      { nome: "Castanha do Pará quebrada", preco: 136.5 },
      { nome: "Colágeno Hidrolisado", preco: 88.2 },
      { nome: "Cheiro verde desidratado", preco: 42.25 },
      { nome: "Chia", preco: 30.7 },
      { nome: "Chimichurri com pimenta", preco: 40.9 },
      { nome: "Chimichurri sem pimenta", preco: 39.3 },
      { nome: "Coco seco fino", preco: 43.9 },
      { nome: "Coco seco médio", preco: 54.5 },
      { nome: "Cranberry", preco: 59.6 },
      { nome: "Cúrcuma pó pura", preco: 25.9 },
      { nome: "Curry", preco: 23.9 },
      { nome: "Farinha de coco branca", preco: 33.6 },
      { nome: "Damasco (assumido seco turco N2)", preco: 99.9 },
      { nome: "Erva doce", preco: 33.7 },
      { nome: "Farinha de arroz", preco: 19.8 },
      { nome: "Farinha de maca peruana", preco: 40.8 },
      { nome: "Lentilha Verde", preco: 31.5 },
      { nome: "Frutas Cristalizadas", preco: 24.7 },
      { nome: "Gergelim negro", preco: 48.4 },
      { nome: "Gergelim branco sem casca", preco: 34.5 },
      { nome: "Gergelim torrado com casca", preco: 23.15 },
      { nome: "Goma xantana", preco: 69.9 },
      { nome: "Hibisco", preco: 56.7 },
      { nome: "Goji Berry", preco: 57.8 },
      { nome: "Grão de bico", preco: 22.25 },
      { nome: "Leite de coco em pó VEGANO", preco: 78.7 },
      { nome: "Mostarda amarela em grão", preco: 27.25 },
      { nome: "Nozes sem casca inteira extra light", preco: 81.9 },
      { nome: "Mix de Castanhas", preco: 103.5 },
      { nome: "Páprica doce", preco: 23.25 },
      { nome: "Páprica picante", preco: 23.25 },
      { nome: "Semente de Girassol (pepita)", preco: 30.5 },
      { nome: "Pimenta preta em grão", preco: 69.7 },
      { nome: "Psyllium", preco: 42.5 },
      { nome: "Quinoa grãos brancos", preco: 40.6 },
      { nome: "Quinoa grãos pretos", preco: 40.2 },
      { nome: "Tâmara jumbo israelense com caroço", preco: 38.9 },
      { nome: "Tâmara sem caroço", preco: 31.5 },
      { nome: "Tempero ervas finas", preco: 41.4 },
      { nome: "Uva passa preta", preco: 34.9 },
      { nome: "Uva passa branca", preco: 40.5 }
    ];

    const productList = document.getElementById('productList');
    const quantidades = new Array(produtos.length).fill(0);

    produtos.forEach((produto, index) => {
      const productDiv = document.createElement('div');
      productDiv.className = 'product';
      productDiv.innerHTML = `
        <h2>${produto.nome}</h2>
        <p>Preço: R$ ${produto.preco.toFixed(2)}/kg</p>
        <div class="quantity-controls">
          <button onclick="alterarQuantidade(${index}, -1)">-</button>
          <span id="quantidade-${index}">0</span> kg
          <button onclick="alterarQuantidade(${index}, 1)">+</button>
        </div>
      `;
      productList.appendChild(productDiv);
    });

    function alterarQuantidade(index, delta) {
      quantidades[index] = Math.max(0, quantidades[index] + delta);
      document.getElementById(`quantidade-${index}`).innerText = quantidades[index];
    }

    function finalizarCompra() {
      let mensagem = "Olá! Gostaria de comprar:\n";
      let temProduto = false;
      produtos.forEach((produto, index) => {
        if (quantidades[index] > 0) {
          mensagem += `- ${produto.nome}: ${quantidades[index]} kg (R$ ${(produto.preco * quantidades[index]).toFixed(2)})\n`;
          temProduto = true;
        }
      });
      if (!temProduto) {
        alert("Por favor, selecione ao menos 1 produto antes de finalizar a compra.");
        return;
      }
      const numeroTelefone = "5538997440048"; // Brasil: 55 + DDD + número
      const mensagemCodificada = encodeURIComponent(mensagem);
      const linkWhatsapp = `https://wa.me/${numeroTelefone}?text=${mensagemCodificada}`;
      window.open(linkWhatsapp, '_blank');
    }
  </script>

</body>
</html>
