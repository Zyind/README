# Endpoints previstos

Endpoints previstos

/api/ativos: consulta, cadastro e atualização de ativos de infraestrutura pública.

/api/chamados: abertura e acompanhamento de chamados de manutenção.

/api/usuarios: cadastro e gerenciamento de usuários.

/api/relatorios: geração de relatórios de uso e manutenção.

/api/notificacoes: envio e consulta de notificações.

# Parâmetros de requisição

GET /api/ativos

Parâmetros opcionais: tipo, localizacao, status

POST /api/chamados
{
  "ativo_id": 12,
  "descricao": "Poste de iluminação apagado",
  "prioridade": "alta"
}

POST /api/usuarios
{
  "nome": "João Silva",
  "email": "joao@email.com",
  "perfil": "cidadão"
}


# Formatos de resposta

{
  "status": "sucesso",
  "dados": {
    "id": 45,
    "ativo": "Poste de iluminação",
    "status": "em manutenção"
  }
}

# Autenticação e autorização

A API utiliza JWT (JSON Web Token).

Usuários devem se autenticar em /api/auth/login enviando email e senha.

O token JWT é enviado no cabeçalho das próximas requisições:
Authorization: Bearer <token>



# Exemplos de chamadas e respostas

Requisição:
GET /api/chamados?status=aberto
Authorization: Bearer <token>

Resposta:
{
  "status": "sucesso",
  "dados": [
    {
      "id": 101,
      "descricao": "Buraco na rua",
      "ativo_id": 33,
      "status": "aberto",
      "prioridade": "alta"
    }
  ]
}

