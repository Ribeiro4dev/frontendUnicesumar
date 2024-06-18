# frontendUnicesumar
Atividades desenvolvidas na matéria de programação Front end

### README.md

# Calculadora de Churrasco

Este projeto é uma calculadora de churrasco desenvolvida para ajudar a estimar a quantidade de ingredientes necessária para um churrasco, de acordo com o número de homens, mulheres e crianças participantes. A calculadora considera diferentes consumos de carne, frango, linguiça, refrigerante e cerveja para cada grupo.

## Funcionalidades

- Receber a quantidade de homens, mulheres e crianças que participarão do churrasco.
- Calcular a quantidade necessária de carne bovina, frango, linguiça, refrigerante e cerveja.
- Exibir as quantidades calculadas na página sem recarregar.
- Oferecer um botão para buscar mercados e açougues próximos no Google Maps.

## Tabela de Consumo

|                 | Homens | Mulheres | Crianças |
|-----------------|--------|----------|----------|
| **Carne bovina**| 500g   | 300g     | 200g     |
| **Frango**      | 200g   | 200g     | 100g     |
| **Linguiça**    | 200g   | 200g     | 200g     |
| **Refrigerante**| 300ml  | 400ml    | 200ml    |
| **Cerveja**     | 800ml  | 500ml    | 0ml      |

## Tecnologias Utilizadas

- HTML
- CSS
- JavaScript

## Estrutura do Projeto

- `index.html`: Contém a estrutura da página.
- `estiloPagina.css`: Contém os estilos para a página.
- `funcoesResultado.js`: Contém as funções JavaScript para cálculo e manipulação do DOM.

## Como Usar

1. Clone este repositório:
    ```bash
    git clone https://github.com/seu-usuario/calculadora-churrasco.git
    ```
2. Navegue até o diretório do projeto:
    ```bash
    cd calculadora-churrasco
    ```
3. Abra o arquivo `index.html` no seu navegador preferido.

## Exemplos de Código

### HTML

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="https://kit.fontawesome.com/fb531f0155.js" crossorigin="anonymous"></script>
    <script src="./funcoesResultado.js" defer></script>
    <link rel="stylesheet" href="./estiloPagina.css">
    <title>Calculadora de Churrasco</title>
</head>
<body>
    <div class="container">
        <h2>Calculadora de Churrasco</h2>
        <div class="input-group">
            <label for="homens">Insira a quantidade de Homens:</label>
            <span class="icon" style="font-size: 1.1em;">
                <i class="fa-solid fa-mars" style="color: #f78000;"></i>
            </span>
            <input type="number" id="homens" min="0" value="0" placeholder="Defina o número de homens">
        </div>
        <div class="input-group">
            <label for="mulheres">Insira a quantidade de Mulheres:</label>
            <span class="icon" style="font-size: 1.1em;">
                <i class="fa-solid fa-venus" style="color: #e43f5a;"></i>
            </span>
            <input type="number" id="mulheres" min="0" value="0" placeholder="Defina o número de mulheres">
        </div>
        <div class="input-group">
            <label for="criancas">Insira a quantidade de Crianças:</label>
            <span class="icon" style="font-size: 1.1em;">
                <i class="fa-solid fa-child" style="color: #5aa7e4;"></i>
            </span>
            <input type="number" id="criancas" min="0" value="0" placeholder="Defina o número de crianças">
        </div>
        <button id="calcular">CALCULAR</button>
        <div id="resultado"></div>
        <button id="searchButton" style="display: none;">Buscar Mercados e Açougues Próximos</button>
    </div>
</body>
</html>
```

### JavaScript

```javascript
document.getElementById("calcular").addEventListener("click", function() {
    const homens = parseInt(document.getElementById("homens").value) || 0;
    const mulheres = parseInt(document.getElementById("mulheres").value) || 0;
    const criancas = parseInt(document.getElementById("criancas").value) || 0;

    const carneBovina = (homens * 500) + (mulheres * 300) + (criancas * 200);
    const frango = (homens * 200) + (mulheres * 200) + (criancas * 100);
    const linguica = (homens * 200) + (mulheres * 200) + (criancas * 200);
    const refrigerante = (homens * 300) + (mulheres * 400) + (criancas * 200);
    const cerveja = (homens * 800) + (mulheres * 500);

    const resultado = `
        <h3>Quantidades Necessárias:</h3>
        <p><i class="fas fa-cow"></i> Carne Bovina: ${(carneBovina / 1000).toFixed(2)} kg</p>
        <p><i class="fas fa-drumstick-bite"></i> Frango: ${(frango / 1000).toFixed(2)} kg</p>
        <p><i class="fas fa-hotdog"></i> Linguiça: ${(linguica / 1000).toFixed(2)} kg</p>
        <p><i class="fas fa-glass-whiskey"></i> Refrigerante: ${(refrigerante / 1000).toFixed(2)} L</p>
        <p><i class="fas fa-beer"></i> Cerveja: ${(cerveja / 1000).toFixed(2)} L</p>
        <h3><i class="fas fa-fire"></i> Aproveite o Churras!</h3>
    `;
    document.getElementById("resultado").innerHTML = resultado;
    document.getElementById("searchButton").style.display = 'block';
});

document.getElementById('searchButton').addEventListener('click', function() {
    const query = encodeURIComponent('mercado e açougues próximos');
    const url = `https://www.google.com/maps/search/?api=1&query=${query}`;
    window.open(url, '_blank');
});
```

### CSS

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    text-align: center;
}

.input-group {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-bottom: 5px;
}

input[type="number"] {
    width: calc(100% - 50px);
    padding: 8px;
    margin-left: 10px;
}

button {
    background-color: #5cb85c;
    color: #fff;
    border: none;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    border-radius: 5px;
}

button:hover {
    background-color: #4cae4c;
}

#resultado {
    margin-top: 20px;
    text-align: left;
}

.icon {
    display: inline-block;
    width: 30px;
}
```

## Contribuição

Se você quiser contribuir para este projeto, por favor, faça um fork do repositório, crie uma nova branch para suas alterações e envie um pull request. Sinta-se à vontade para abrir issues para relatar bugs ou sugerir melhorias.

## Licença

---

Feito com ♥ por [Bruno G. Ribeiro](https://github.com/Ribeiro4dev)
