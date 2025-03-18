# 📦 E-Commerce - Modelagem de Banco de Dados

## 📖 Visão Geral
Este projeto representa a modelagem de banco de dados para um sistema de e-commerce, utilizando um **Diagrama de Entidade-Relacionamento Estendido (DER)**. O modelo foi refinado para incluir generalização de clientes, múltiplas formas de pagamento, informações sobre a entrega, terceiro vendedor e fornecedor.

---

## 🔗 Estrutura do Banco de Dados

### **1️⃣ Generalização de Cliente**
A entidade `Pessoa` foi criada como uma classe genérica para representar tanto **Pessoa Física** quanto **Pessoa Jurídica**.
- **`Pessoa` (Superclasse)**
  - `idPessoa` (PK)
  - `Nome`
  - `Endereco`
  - `Identificacao` (CPF/CNPJ genérico)
- **`ClientePF` (Especialização - Pessoa Física)**
  - `idPessoa (FK)`
  - `CPF`
- **`ClientePJ` (Especialização - Pessoa Jurídica)**
  - `idPessoa (FK)`
  - `CNPJ`
  - `RazaoSocial`

### **2️⃣ Vendedor terceiro**
O terceiro vendedor pode vender produtos na plataforma, possuindo um relacionamento com os produtos que oferece.
- **`TerceiroVendedor`**
  - `idTerceiroVendedor` (PK)
  - `RazaoSocial`
  - `Localizacao`
- **`ProdutosPorVendedor`**
  - `idTerceiroVendedor (FK)`
  - `idProduto (FK)`
  - `Quantidade`

### **3️⃣ Fornecedor**
Os fornecedores fornecem produtos para a plataforma, mantendo um vínculo com os produtos disponíveis.
- **`Fornecedor`**
  - `idFornecedor` (PK)
  - `RazaoSocial`
  - `CNPJ`
  - `Contato`
- **`DisponibilizaProduto`**
  - `idFornecedor (FK)`
  - `idProduto (FK)`

### **4️⃣ Pedido e Pagamento**
O modelo permite que um **pedido tenha múltiplas formas de pagamento**, garantindo flexibilidade na transação.
- **`Pedido`**
  - `idPedido` (PK)
  - `StatusPedido`
  - `Descricao`
  - `Frete`
  - `Cliente_idPessoa (FK)`
- **`Pagamento`**
  - `idPagamento` (PK)
  - `idPedido (FK)`
  - `idTipoPagamento (FK)`
  - `ValorPago`
- **`TipoPagamento`**
  - `idTipoPagamento` (PK)
  - `Descricao` (Cartão, Boleto, Pix, etc.)

### **5️⃣ Entrega**
A entrega foi modelada como uma entidade separada para rastreamento e status da entrega de cada pedido.
- **`Entrega`**
  - `idEntrega` (PK)
  - `idPedido (FK)`
  - `StatusEntrega` (Em transporte, Entregue, etc.)
  - `CodigoRastreio`

### **6️⃣ Produto e Estoque**
Os produtos e estoques foram organizados para permitir melhor gerenciamento de disponibilidade.
- **`Produto`**
  - `idProduto` (PK)
  - `Categoria`
  - `Descricao`
  - `Valor`
- **`Estoque`**
  - `idEstoque` (PK)
  - `Localizacao`
- **`Estoque_has_Produto`**
  - `idEstoque (FK)`
  - `idProduto (FK)`
  - `Quantidade`

### **7️⃣ Relacionamento entre Pedido e Produto**
Cada pedido pode conter vários produtos e cada produto pode estar em diferentes pedidos.
- **`Pedido_has_Produto`**
  - `idPedido (FK)`
  - `idProduto (FK)`
  - `Quantidade`

---

## 📊 DER - Diagrama de Entidade e Relacionamento
📌 O diagrama segue o **modelo EER (Extended Entity-Relationship)**, garantindo escalabilidade e melhor normalização do banco de dados.

![Diagrama de Entidade e Relacionamento](./E-comerce.png) *(Substitua pelo caminho correto da imagem do DER se necessário.)*

---

## 🔧 Tecnologias Utilizadas
- **MySQL / PostgreSQL** (ou outro banco relacional)
- **MySQL Workbench / Draw.io** (para modelagem gráfica)

---

## 🚀 Possíveis Melhorias Futuras
- Implementação de um histórico de status do pedido
- Criação de categorias para produtos
- Inclusão de um sistema de avaliações e reviews dos clientes

---

## ✨ Contribuição
Caso queira contribuir com melhorias, sinta-se à vontade para sugerir alterações ou expandir o modelo conforme necessário.

---

## 📜 Licença
Este projeto é de livre uso para aprendizado e desenvolvimento de sistemas de e-commerce.

---

📩 **Contato:** Caso tenha dúvidas ou sugestões, entre em contato!

---

