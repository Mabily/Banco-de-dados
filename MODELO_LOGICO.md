# 🔷 Modelo Lógico:

## Tabela: users
- id_usuario (PK) — inteiro
- username — texto
- password — texto

## Tabela: vulnerable_people  
- id_pessoa (PK) — inteiro
- id_usuario (FK) — inteiro
- nome — texto
- telefone — texto
- contatos_emergencia — json
- latitude — real
- longitude — real
- ativo — booleano
- ultima_atualizacao — data_hora
- nivel_risco — texto

## Tabela: community_reports
- id_relatorio (PK) — inteiro
- id_usuario (FK) — inteiro
- tipo — texto
- titulo — texto
- descricao — texto
- latitude — real
- longitude — real
- severidade — texto
- status — texto
- votos — inteiro
- data_criacao — data_hora

## Tabela: weather_alerts
- id_alerta (PK) — inteiro
- tipo_alerta — texto
- severidade — texto
- titulo — texto
- descricao — texto
- latitude — real
- longitude — real
- raio — real
- hora_inicio — data_hora
- hora_fim — data_hora
- ativo — booleano
- data_criacao — data_hora

## Tabela: emergency_contacts
- id_contato (PK) — inteiro
- id_usuario (FK) — inteiro
- nome — texto
- telefone — texto
- relacionamento — texto
- primario — booleano

## Tabela: risk_areas
- id_area (PK) — inteiro
- nome — texto
- nivel_risco — texto
- latitude — real
- longitude — real
- raio — real
- ativo — booleano
- ultima_atualizacao — data_hora
