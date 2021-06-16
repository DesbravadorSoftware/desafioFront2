# Desbravador Software 🌎

## 🚀 Desafio- Desenvolvedor Frontend
Não é esperado que todas as pessoas consigam realizar esse desafio por completo, já que é destinado a todos os níveis de carreira.
A avaliação será baseada na sua capacidade de escrever um código simples, de fácil manutenção e com uma boa organização.

### Instruções
- **Nome do Projeto:** DesbravadorHotels
- **Objetivo do Projeto:** Criar uma aplicação Web responsiva que consulte a API do Hotels e crie uma inteface de sua preferencia
- **Tecnologia:** Preferencialmente React.
- **User Interface:** Você deve [usar esse link](https://www.figma.com/file/ZXkPFyAI9giS3iLDySiQaH/Neomorphic-Travel-UI-Kit?node-id=0%3A1) como referência de UI durante o desenvolvimento.
- **Entregáveis:** Crie um repositório pessoal para esse projeto, siga as instruções abaixo e responda e-mail recebido com link do repositório. Caso você resolveu fazer o teste por conta própria pode enviar para rh@desbravador.com.br.

### Desafio

- Consulte a API disponibilizada para buscar as informações.
- Crie uma tela para exibir a lista de hoteis:
    - O usuário deve ser capaz de buscar por localidade. 
      - (Pode usar fixo a localidade do exemplo)
    - Demonstre em lista os hoteis 
    - Podendo ordenar por preço
    - Para cada hotel, deve ser exibido os seus detalhes
- Crie uma tela para exibir o hotel com seus detalhes:
    - O usuário deve ser capaz de visualizar imagens. 
      -   GET - https://hotels-com-free.p.rapidapi.com/nice/image-catalog/v2/hotels/106346
    - Ver a classificação 
      -  GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346 (body.propertyDescription.starRating)
    - Ver o endereço do hotel 
      -  GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346    (body.propertyDescription.address)
    - Ver seu nome completo
      -  GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346   (body.propertyDescription.name)
    - Verificar lista de comodidades (body.propertyDescription.freebies)
      -  GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346  (body.propertyDescription.freebies)
- Crie uma tela para exibir a lista de quartos do hotel  
    - Ver o nome do tipo do quarto 
      - GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346  (roomsAndRates.rooms.name)
    - Ver os detalhes de ocupação  
      - GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346  (roomsAndRates.rooms.maxOccupancy)
    - Ver informações adicionais 
      - GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346  (roomsAndRates.rooms.additionalInfo)
    - Verificar lista de comodidades - apenas do primeiro da lista
      - GET - https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346  (roomsAndRates.rooms.ratePlans.price.current)
- Crie uma tela de formulário de reserva conforme imagem


### O que nós vamos avaliar
 
- Organização do projeto: Avalia a estrutura do projeto, documentação e uso de controle de versão, legibilidade;
- Inovação tecnológica: Avalia o uso de tecnologias mais recentes, desde que estáveis; (decisões técnicas com as quais você se sente mais confortável)
- Coerência: Avalia se os requisitos foram atendidos;
- Boas práticas: Avalia se o projeto segue boas práticas de desenvolvimento, incluindo segurança e otimização; 

---

- Inclua um arquivo *README* que possua:
  - desafios/problemas com os quais você se deparou durante a execução do projeto.
  - maneiras através das quais você pode melhorar a aplicação, seja em performance, estrutura ou padrões. 
  - todas as instruções necessárias para que qualquer pessoa consiga rodar sua aplicação sem maiores problemas.

### Dicas
- Tudo bem, até pode usar jquery. Se você não quiser usar (bônus, preferimos Fetch API)
- É obrigatório o uso de rotas. 
- Documente seu projeto em arquivos markdown explicando a estrutura, processo de setup e requisitos.
- Você pode utilizar bibliotecas de componentes visuais;
- O material de UI/UX que fornecemos deve servir como uma referência, você não precisa necessariamente segui-lo à risca. No entanto, quanto mais próximo, melhor.
- Os testes unitários são opcionais porém são mais do que desejados.
- Use boas práticas de programação.
- Cuidado! Você pode requisitar a API apenas 50 vezes ao dia.

### API que você deve consumir
```
URL: hotels-com-free.p.rapidapi.com
Chave de acesso: 8d84e2f535msh2ecf705eb53119bp1647cbjsnc5a4f9d13869
```


**Examplos de consulta na API:**
- Busca de hoteis- https://hotels-com-free.p.rapidapi.com/srle/listing/v1/brands/hotels.com

Exemplo com Node.js:

```
var unirest = require("unirest");

var req = unirest("GET", "https://hotels-com-free.p.rapidapi.com/srle/listing/v1/brands/hotels.com");

req.query({
	"lat": "37.788719679657554",
	"lon": "-122.40057774847898",
	"checkIn": "2021-01-27",
	"checkOut": "2021-01-28",
	"rooms": "1",
	"locale": "en_US",
	"currency": "USD",
	"pageNumber": "1"
});

req.headers({
	"x-rapidapi-key": "8d84e2f535msh2ecf705eb53119bp1647cbjsnc5a4f9d13869",
	"x-rapidapi-host": "hotels-com-free.p.rapidapi.com",
	"useQueryString": true
});


req.end(function (res) {
	if (res.error) throw new Error(res.error);

	console.log(res.body);
});
```

- Buscar  um hotel

```  
var unirest = require("unirest");

var req = unirest("GET", "https://hotels-com-free.p.rapidapi.com/pde/property-details/v1/hotels.com/106346");

req.query({
	"rooms": "1",
	"checkIn": "2021-01-27",
	"checkOut": "2021-01-28",
	"locale": "en_US",
	"currency": "USD",
	"include": "neighborhood"
});

req.headers({
	"x-rapidapi-key": "8d84e2f535msh2ecf705eb53119bp1647cbjsnc5a4f9d13869",
	"x-rapidapi-host": "hotels-com-free.p.rapidapi.com",
	"useQueryString": true
});


req.end(function (res) {
	if (res.error) throw new Error(res.error);

	console.log(res.body);
});
```


- Buscar imagens de um hotel

```  
var unirest = require("unirest");

var req = unirest("GET", "https://hotels-com-free.p.rapidapi.com/nice/image-catalog/v2/hotels/106346");

req.headers({
	"x-rapidapi-key": "8d84e2f535msh2ecf705eb53119bp1647cbjsnc5a4f9d13869",
	"x-rapidapi-host": "hotels-com-free.p.rapidapi.com",
	"useQueryString": true
});


req.end(function (res) {
	if (res.error) throw new Error(res.error);

	console.log(res.body);
});
```



### FAQ

#### Posso utilizar frameworks/bibliotecas?
Sim.

#### Quanto tempo eu tenho ?
Quanto mais tempo você demorar, mais críticos seremos na sua avaliação =]

#### React, Angular ou Vue?
Sem preferencia, porém com React terá um bônus
