# Explicação do Projeto DevOps com Docker Compose

## Dockerfiles

- **produtos/Dockerfile**: Cria uma imagem Node.js que roda um servidor Express na porta 3001. Expõe uma rota `/products` com uma lista fixa de produtos.

- **pedidos/Dockerfile**: Cria uma imagem Python que usa Flask, Redis e MySQL. Expõe `/order`, faz cache de produtos com Redis, salva pedidos no banco MySQL e retorna o pedido.

- **pagamentos/Dockerfile**: Usa PHP puro para expor `/payment`, faz uma requisição HTTP para a API de pedidos e retorna o pedido com status de pagamento "paid".

## docker-compose.yml

- **products**: Serviço com a API de produtos. Usa a imagem Node.js criada via Dockerfile.
- **orders**: Serviço com a API de pedidos. Comunica com products, db e redis.
- **payments**: Serviço PHP que consome a API de pedidos.
- **db**: Container MySQL com senha e banco configurado para a API de pedidos.
- **redis**: Cache intermediário usado pela API de pedidos.
- **networks**: Todos os serviços estão na mesma rede "ecommerce" para facilitar a comunicação entre containers.
