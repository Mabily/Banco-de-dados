# 🔶 Modelo Físico no PostgreSQL:

```sql
CREATE TABLE users (
    id_usuario SERIAL PRIMARY KEY,
    username VARCHAR(100) UNIQUE,
    password VARCHAR(255)
);

CREATE TABLE vulnerable_people (
    id_pessoa SERIAL PRIMARY KEY,
    id_usuario INTEGER REFERENCES users(id_usuario),
    nome VARCHAR(200),
    telefone VARCHAR(20),
    contatos_emergencia JSON,
    latitude REAL,
    longitude REAL,
    ativo BOOLEAN DEFAULT TRUE,
    ultima_atualizacao TIMESTAMP,
    nivel_risco VARCHAR(20) DEFAULT 'low'
);

CREATE TABLE community_reports (
    id_relatorio SERIAL PRIMARY KEY,
    id_usuario INTEGER REFERENCES users(id_usuario),
    tipo VARCHAR(50),
    titulo VARCHAR(255),
    descricao TEXT,
    latitude REAL,
    longitude REAL,
    severidade VARCHAR(20) DEFAULT 'low',
    status VARCHAR(20) DEFAULT 'active',
    votos INTEGER DEFAULT 0,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE weather_alerts (
    id_alerta SERIAL PRIMARY KEY,
    tipo_alerta VARCHAR(50),
    severidade VARCHAR(20),
    titulo VARCHAR(255),
    descricao TEXT,
    latitude REAL,
    longitude REAL,
    raio REAL DEFAULT 5000,
    hora_inicio TIMESTAMP,
    hora_fim TIMESTAMP,
    ativo BOOLEAN DEFAULT TRUE,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE emergency_contacts (
    id_contato SERIAL PRIMARY KEY,
    id_usuario INTEGER REFERENCES users(id_usuario),
    nome VARCHAR(200),
    telefone VARCHAR(20),
    relacionamento VARCHAR(50),
    primario BOOLEAN DEFAULT FALSE
);

CREATE TABLE risk_areas (
    id_area SERIAL PRIMARY KEY,
    nome VARCHAR(255),
    nivel_risco VARCHAR(20),
    latitude REAL,
    longitude REAL,
    raio REAL DEFAULT 500,
    ativo BOOLEAN DEFAULT TRUE,
    ultima_atualizacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
