FretAO --- Tu compras. Nós transportamos.
1. Visão geral do projeto
O FretAO é uma plataforma Peer-to-Peer (P2P) de logística e fretes urbanos de última milha em Angola, focada no microtransporte hiperlocal de encomendas e refeições.

A aplicação adota uma arquitetura inspirada nos principais serviços globais de mobilidade, com uma abordagem delivery-first , conectando clientes a motoristas e estafetas locais.

Proposta de valor diferencial
Ao contrário das plataformas tradicionais de entrega que agregam marketplaces e podem cobrar comissões sobre os produtos, o FretAO separa a compra do transporte.

O cliente compra onde --- por WhatsApp, telefone, presencialmente ou através de vitrines virtuais --- e utiliza o FretAO exclusivamente para solicitar o serviço de coleta e entrega, com transparência e preços acessíveis.

2. Arquitetura e pilha tecnológica
Backend --- API REST
Linguagem e framework: Node.js, Express e TypeScript.
Base de dados e ORM: PostgreSQL, gerenciado através do Prisma ORM (Docker/Supabase).
Autenticação e segurança: JWT ( JSON Web Tokens ) e hashing de palavras-passe com BCrypt.
Frontend --- aplicação móvel e Web
Frameworks: React Native, Expo e TypeScript.
Interface e mapas: integração de mapas em tela inteira através de react-native-mapse react-native-web.
Biblioteca de ícones: @expo/vector-icons , com Ionicons e MaterialCommunityIcons.
Identidade visual
Elemento Cor Código

Fundo Gelo #FBFBFB Texto Grafite #1A1A1A Destaque Vinho Bourbon#8A051D

3. Principais funcionalidades e fluxo de UX
Experiência do cliente --- Entrega em primeiro lugar
Mapa em tela inteira: navegação imersiva, com foco inicial na localização atual do usuário.
Estimativa automática de rota e tarifa: cálculo da rota e do preço assim que os pontos de coleta e entrega forem definidos.
Descoberta de estafetas próxima: apresentação dos motoristas disponíveis na zona, com informação sobre distância, tempo estimado de chegada e preço.
Chamada com um clique: possibilidade de chamar diretamente a estafeta escolhida. Exemplo: CHAMAR MANUEL • 350 Kz.
Segurança e validação --- PIN duplo
O sistema utiliza dois códigos PIN diferentes, ambos com quatro dígitos, para validar os momentos essenciais da entrega.

PIN de coleta: utilizado na loja ou no ponto de origem para confirmar que a estafeta coletau o artigo.
PIN de entrega: fornecido pelo cliente no destino para validar e concluir a entrega.
4. Estrutura de diretórios
taxi-delivery/
├── backend/
│   ├── prisma/
│   │   ├── schema.prisma       # Modelos da base de dados (utilizadores, entregas e tarifas)
│   │   └── seed.ts              # Dados iniciais para testes
│   ├── src/
│   │   ├── controladores/       # Controladores das rotas (Auth, Delivery e Tarifário)
│   │   ├── rotas/               # Definição dos endpoints REST
│   │   ├── services/            # Lógica de negócio e cálculos de tarifas
│   │   └── server.ts            # Ponto de entrada do servidor
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── componentes/         # Componentes reutilizáveis (MapViewComponent, etc.)
    │   ├── contexts/            # Contexto global de autenticação (AuthContext)
    │   ├── telas/               # Ecrãs da aplicação
    │   │   ├── HomeScreen
    │   │   ├── ActiveDeliveryScreen
    │   │   ├── DriverScreen
    │   │   └── HistoryScreen
    │   └── services/            # Configuração das chamadas à API (Axios)
    ├── App.tsx
    └── package.json
5. Guia de instalação e execução
Pré-requisitos
Antes de iniciar, garanta que você tenha os seguintes recursos instalados e configurados:

Node.js e npm;
Docker;
PostgreSQL;
Expo CLI (pode ser utilizado através do npx).
Passo 1 --- Backend e base de dados
Garanta que o Docker e o PostgreSQL estejam em execução.

Aceda à massa do backend e instale as dependências:

cd backend
npm install
Execute as migrações e carregue os dados iniciais:

npx prisma migrate dev --name init
npx prisma db seed
Inicie o servidor da API:

npm run dev
Por padrão, uma API ficará disponível em:

http://localhost:3000

Passo 2 --- Frontend (Expo)
Aceda à pasta do frontend e instale as dependências:

cd frontend
npm install
Garanta que os ícones do Expo estejam instalados:

npx expo install @expo/vector-icons
Inicie o ambiente de desenvolvimento.

Para Web:

npx expo start --web
Para dispositivo móvel:

npx expo start
6. Credenciais padrão para testes
As credenciais a seguir destinam-se exclusivamente ao ambiente de desenvolvimento e testes.

Perfil Telefone Palavra-passe Função no sistema

Cliente 923000111 123456passwordSolicitar entregas e acompanhar a rota

Motorista 924111222 senha123passwordAceitar corridas
e validar os PINs

Aviso de segurança: não utilize estas credenciais de produção. Antes de disponibilizar a aplicação pública, substitua as credenciais de teste, utilize palavras-passe fortes e armazene apenas hashes seguros das palavras-passe. Nunca inclua segredos, tokens ou credenciais reais no repositório.
