## Hi there 👋

<!--
**estoque-luiz/estoque-luiz** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
--><!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Seu título aqui</title>
  <script src="https://cdn.tailwindcss.com"></script>>
</head>
<body class="bg-gray-100 p-4">
  <div class="max-w-4xl mx-auto">
    <h1 class="text-2xl font-bold mb-4">📦 Sistema de Estoque da Loja AL Importados</h1>

    <!-- Formulário de Cadastro de Produto -->
    <form id="formProduto" class="bg-white p-4 rounded shadow mb-6">
      <h2 class="text-xl font-semibold mb-2">Novo Produto</h2>
      <div class="grid grid-cols-2 gap-4">
        <input class="border p-2 rounded" type="text" id="nomeCliente" placeholder="Nome do Cliente" required />
        <input class="border p-2 rounded" type="text" id="imei" placeholder="IMEI do Aparelho" required />
        <input class="border p-2 rounded" type="text" id="nome" placeholder="Nome do Produto" required />
        <input class="border p-2 rounded" type="text" id="modelo" placeholder="Modelo ou Descrição" />
        <select class="border p-2 rounded" id="categoria" required>
          <option value="">Selecione a Categoria</option>
          <option value="iPhone">iPhone</option>
          <option value="Xiaomi">Xiaomi</option>
          <option value="Perfume">Perfume</option>
        </select>
        <input class="border p-2 rounded" type="number" id="quantidade" placeholder="Quantidade" required />
        <input class="border p-2 rounded" type="number" id="precoCusto" placeholder="Preço de Custo" step="0.01" />
        <input class="border p-2 rounded" type="number" id="precoVenda" placeholder="Preço de Venda" step="0.01" />
      </div>
      <button type="submit" class="mt-4 px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700">Adicionar</button>
    </form>

    <!-- Tabela de Estoque -->
    <div class="bg-white p-4 rounded shadow">
      <h2 class="text-xl font-semibold mb-2">📋 Estoque Atual</h2>
      <table class="w-full table-auto text-left">
        <thead>
          <tr class="bg-gray-200">
            <th class="p-2">Cliente</th>
            <th class="p-2">IMEI</th>
            <th class="p-2">Produto</th>
            <th class="p-2">Categoria</th>
            <th class="p-2">Modelo</th>
            <th class="p-2">Qtd</th>
            <th class="p-2">Custo</th>
            <th class="p-2">Venda</th>
          </tr>
        </thead>
        <tbody id="tabelaEstoque"></tbody>
      </table>
    </div>
  </div>

  <script>
    const form = document.getElementById("formProduto");
    const tabela = document.getElementById("tabelaEstoque");
    const produtos = [];

    form.addEventListener("submit", (e) => {
      e.preventDefault();

      const nomeCliente = document.getElementById("nomeCliente").value;
      const imei = document.getElementById("imei").value;
      const nome = document.getElementById("nome").value;
      const modelo = document.getElementById("modelo").value;
      const categoria = document.getElementById("categoria").value;
      const quantidade = parseInt(document.getElementById("quantidade").value);
      const precoCusto = parseFloat(document.getElementById("precoCusto").value);
      const precoVenda = parseFloat(document.getElementById("precoVenda").value);

      const produto = {
        nomeCliente,
        imei,
        nome,
        modelo,
        categoria,
        quantidade,
        precoCusto,
        precoVenda,
      };
      produtos.push(produto);
      atualizarTabela();
      form.reset();
    });

    function atualizarTabela() {
      tabela.innerHTML = "";
      produtos.forEach((p) => {
        tabela.innerHTML += `
          <tr>
            <td class="p-2">${p.nomeCliente}</td>
            <td class="p-2">${p.imei}</td>
            <td class="p-2">${p.nome}</td>
            <td class="p-2">${p.categoria}</td>
            <td class="p-2">${p.modelo}</td>
            <td class="p-2">${p.quantidade}</td>
            <td class="p-2">R$ ${p.precoCusto?.toFixed(2)}</td>
            <td class="p-2">R$ ${p.precoVenda?.toFixed(2)}</td>
          </tr>
        `;
      });
    }
  </script>
</body>
</html>
