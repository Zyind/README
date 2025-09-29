# REQUISITOS FUNCIONAIS

Permitir o cadastro e atualização de ativos de infraestrutura (ex.: postes, vias, pontes, escolas).

Registrar solicitações de manutenção vindas de cidadãos ou equipes técnicas.

Gerar relatórios de status da infraestrutura por bairro/região.

Integrar com sistemas de geolocalização (mapas) para exibir ativos no território.

Controlar ordens de serviço (abertura, atribuição a equipes, conclusão).

Notificar gestores sobre prazos ou manutenções críticas.

# REQUISITOS NÃO FUNCIONAIS

O sistema deve estar disponível 99% do tempo em horário comercial.

A interface deve ser responsiva e acessível.

O sistema deve permitir integração via API RESTful.

Todas as informações devem estar criptografadas (LGPD).

# REGRAS DE NEGÓCIO


Cada ativo de infraestrutura deve possuir um identificador único no cadastro.

Chamados de manutenção devem ser classificados por prioridade.

Apenas gestores municipais podem aprovar e encerrar ordens de serviço críticas.

Os relatórios oficiais devem seguir os formatos exigidos pelo Tribunal de Contas do Estado.

Solicitações de cidadãos devem ser respondidas em até 48h úteis.


# Histórias de usuário ou casos de uso

Visão do usuário na execução da aplicação

Como morador, quero registrar um problema de iluminação pública, para que a prefeitura resolva rapidamente.

Como técnico de manutenção, quero receber ordens de serviço com localização no mapa, para otimizar meu deslocamento.

Como gestor municipal, quero visualizar relatórios de infraestrutura por bairro, para planejar investimentos.

Como administrador, quero definir níveis de acesso de usuários, para garantir segurança no sistema.


# Perfis de usuário

Tipos de usuários que interagem com o sistema:

Cidadão: registra reclamações e acompanha status.

Técnico/Executor do serviço: executa ordens de serviço e atualiza status de manutenção.

Empresa/Autarquia/Secretaria: Recebe as solicitações dos serviços e repassa aos técnicos e executores.

Gestor municipal: acompanha relatórios, aprova demandas e toma decisões.

Administrador de sistema: cuida de permissões e manutenção do sistema.
