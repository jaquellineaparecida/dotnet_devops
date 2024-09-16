Caio Rocha RM99617

Sistema de Recomendação de Livros
Descrição do Projeto
Este projeto é uma API RESTful desenvolvida em .NET Core para gerenciar um sistema de recomendação de livros. A API permite realizar operações CRUD (Criar, Ler, Atualizar, Excluir) tanto para livros quanto para autores. A arquitetura adotada é monolítica e utiliza o padrão de design Repository para acesso a dados.

Arquitetura
Arquitetura Monolítica
A arquitetura monolítica significa que toda a aplicação é desenvolvida e implantada como uma única unidade. A aplicação contém todos os componentes necessários para a operação, incluindo:

Controllers: LivroController e AutorController gerenciam as solicitações HTTP e interagem com os serviços para realizar operações CRUD.
Services: LivroService e AutorService encapsulam a lógica de negócios e a interação com o banco de dados.
Models: LivroModel e AutorModel representam as entidades no banco de dados.
DTOs: LivroCriacaoDto, LivroEdicaoDto, AutorCriacaoDto, e outros DTOs são usados para transferir dados entre as camadas da aplicação e os endpoints da API.
Data Context: AppDbContext é o contexto do Entity Framework Core que gerencia a conexão com o banco de dados e a configuração das entidades.
Design Patterns Utilizados
Padrão Repository
O padrão Repository é utilizado para encapsular a lógica de acesso a dados e abstrair a interação com o banco de dados.

Repository<T>: Um repositório genérico que fornece operações básicas de CRUD.
ItemRepository: Um repositório específico para a entidade Item (no seu caso, LivroModel), com um método adicional para buscar livros com preferências relacionadas.
Padrão Singleton
O padrão Singleton é utilizado para garantir que a configuração da aplicação seja gerenciada por uma única instância global. Isso é particularmente útil para gerenciar a configuração do banco de dados e outras configurações da aplicação.

Instruções para Rodar a API
Pré-requisitos
.NET SDK: Certifique-se de ter o .NET SDK 6.0 ou superior instalado. Você pode baixar o SDK do site oficial.

Oracle Database: A API utiliza o banco de dados Oracle. Certifique-se de ter um banco de dados Oracle em funcionamento e a conexão configurada corretamente no seu AppDbContext.

Passos para Executar a API
Clone o Repositório
git clone <https://github.com/caiorfer/Sprint3-.NET>
cd <NOME_DO_REPOSITORIO>

Restaure os Pacotes NuGet
dotnet restore

Aplicar Migrations
As migrations precisam ser aplicadas para criar as tabelas no banco de dados. Execute o seguinte comando:
dotnet ef database update

Iniciar a Aplicação
dotnet run
A API será iniciada e estará disponível em http://localhost:5000 por padrão.

Acessar a Documentação Swagger
A documentação da API está disponível através do Swagger UI. Navegue até http://localhost:5000/swagger em seu navegador para ver a documentação interativa dos endpoints e modelos de dados.

Estrutura de Todos os Endpoints do Projeto
Livros
GET api/livro/ListarLivros: Lista todos os livros.
GET api/livro/BuscaLivroPorId/{idLivro}: Busca um livro pelo ID.
GET api/livro/BuscaLivroPorIdAutor/{idAutor}: Busca livros pelo ID do autor.
POST api/livro/Criarlivro: Cria um novo livro.
PUT api/livro/Editarlivro: Edita um livro existente.
DELETE api/livro/Excluirlivro: Exclui um livro pelo ID.
Autores
GET api/autor/ListarAutores: Lista todos os autores.
GET api/autor/BuscaAutorPorId/{idAutor}: Busca um autor pelo ID.
GET api/autor/BuscaAutorPorIdLivro/{idLivro}: Busca autor pelo ID do livro.
POST api/autor/CriarAutor: Cria um novo autor.
PUT api/autor/EditarAutor: Edita um autor existente.
DELETE api/autor/ExcluirAutor: Exclui um autor pelo ID.

Contribuição
Se você deseja contribuir para este projeto, por favor, siga estas etapas:
Faça um fork do repositório.
Crie uma branch para sua modificação (git checkout -b feature/nova-funcionalidade).
Faça commit das suas alterações (git commit -am 'Adiciona nova funcionalidade').
Faça push para a branch (git push origin feature/nova-funcionalidade).
Abra um Pull Request.
Licença

Este projeto está licenciado sob a MIT License.

