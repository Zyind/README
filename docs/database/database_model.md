# MODELO DE DADOS
O banco sip_for foi projetado para registrar usuários e suas ocorrências, com a possibilidade de interações por meio de comentários e acompanhamento do histórico de status de cada ocorrência.
A integridade é garantida por chaves primárias e estrangeiras, utilizando MySQL (InnoDB).

# DESCRIÇÃO DAS ENTIDADES E RELACIONAMENTO 
  Usuários (usuarios)
    Guardam informações básicas de cada pessoa (cidadãos ou gestores).

  Ocorrências (ocorrencias)
    Problemas reportados pelos usuários (buracos, iluminação, etc.). Cada ocorrência pertence a um usuário.

  Comentários (comentarios)
    Permitem interação em torno de uma ocorrência. Todo comentário está vinculado a um usuário e a uma ocorrência.

  Histórico de Status (historico_status)
    Armazena as alterações do status de uma ocorrência ao longo do tempo.

  Relacionamentos

  usuarios (1) —— (N) ocorrencias

  usuarios (1) —— (N) comentarios

  ocorrencias (1) —— (N) comentarios

  ocorrencias (1) —— (N) historico_status

# DIAGRAMA ENTIDADE-RELACIONAMENTO (DER)
  USUARIOS ||--o{ OCORRENCIAS : "registra"
  US UARIOS ||--o{ COMENTARIOS : "escreve"
  OCORRENCIAS ||--o{ COMENTARIOS : "recebe"
  OCORRENCIAS ||--o{ HISTORICO_STATUS : "tem" 

  USUARIOS {
        int id_usuario PK
        varchar nome
        varchar email
        varchar senha
        enum tipo
        timestamp data_criacao
    }

  OCORRENCIAS {
        int id_ocorrencias PK
        varchar titulo
        longtext descricao
        varchar localizacao
        varchar foto_url
        enum status
        timestamp data_criacao
        int id_usuario FK
    }

   COMENTARIOS {
        int id_comentario PK
        mediumtext texto
        timestamp data_criacao
        int id_usuario FK
        int id_ocorrencias FK
    }
    
  HISTORICO_STATUS {
        int id_historico PK
        enum status
        timestamp data_alteracao
        int id_ocorrencias FK
    }

# DICIONÁRIO DE DADOS
   TABELA usuarios
   
  (Campo)	(Tipo)	(Restrição)	(Descrição)
  
  id_usuario	INT	PK, AI	Identificador único do usuário
  
  nome	VARCHAR(100)	NOT NULL	Nome do usuário
  
  email	VARCHAR(100)	UNIQUE, NOT NULL	E-mail de login
  
  senha	VARCHAR(20)	NOT NULL	Senha do usuário (não criptografada no modelo atual)
  
  tipo	ENUM	DEFAULT 'cidadao'	Tipo de usuário (cidadao/gestor)
  
  data_criacao	TIMESTAMP	DEFAULT CURRENT_TIMESTAMP	Data de cadastro


  TABELA ocorrencias

  id_ocorrencias	INT	PK, AI	Identificador da ocorrência
  
  titulo	VARCHAR(100)	NOT NULL	Título resumido
  
  descricao	LONGTEXT	NOT NULL	Detalhamento da ocorrência
  
  localizacao	VARCHAR(255)	NOT NULL	Endereço/localização
  
  foto_url	VARCHAR(255)	NULL	URL da imagem
  
  status	ENUM	DEFAULT 'pendente'	Situação da ocorrência
  
  data_criacao	TIMESTAMP	DEFAULT CURRENT_TIMESTAMP	Data do registro
  
  id_usuario	INT	FK → usuarios(id_usuario)	Usuário que cadastrou
  

  TABELA comentarios

  id_comentario	INT	PK, AI	Identificador do comentário
  
  texto	MEDIUMTEXT	NOT NULL	Texto do comentário
  
  data_criacao	TIMESTAMP	DEFAULT CURRENT_TIMESTAMP	Data do comentário
  
  id_usuario	INT	FK → usuarios(id_usuario)	Autor do comentário
  
  id_ocorrencias	INT	FK → ocorrencias(id_ocorrencias)	Ocorrência comentada
  

  TABELA historico_status

  id_historico	INT	PK, AI	Identificador do histórico
  
  status	ENUM	NOT NULL	Status registrado (pendente, em_andamento, concluido)
  
  data_alteracao	TIMESTAMP	DEFAULT CURRENT_TIMESTAMP	Momento da alteração
  
  id_ocorrencias	INT	FK → ocorrencias(id_ocorrencias)	Ocorrência vinculada
  
