# Descrição da arquitetura

Frontend (site/aplicativo) para acesso dos usuários.

Backend responsável pelas regras de negócio e comunicação com o banco de dados.

Banco de dados para armazenar informações sobre ativos públicos, solicitações e usuários.

# Componentes do sistema

Interface do Usuário (Frontend): onde cidadãos, técnicos e gestores acessam o sistema.

Servidor/Backend: processa solicitações, aplica regras de negócio e gerencia dados.

Banco de Dados: guarda informações de infraestrutura, ordens de serviço e relatórios.

Módulo de Notificações: envia alertas e confirmações para os usuários.

# Padrões de Arquitetura utilizados

Cliente-Servidor: separa frontend e backend.

API REST: permite comunicação entre os módulos.

MVC (Model-View-Controller) no frontend: organiza a interface.

# Diagrama da Arquitetura

https://l1nk.dev/architecture

# Decisões técnicas e justificativas

Uso de API REST para facilitar a integração.

Banco de dados relacional para garantir consistência dos dados.

Adoção da arquitetura cliente-servidor por ser clara, consolidada e de fácil manutenção, permitindo separar responsabilidades entre interface e processamento.
