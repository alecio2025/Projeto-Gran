import sqlite3

# Conectar ao banco de dados (ou criar se não existir)
conn = sqlite3.connect('exemplo.db')
cursor = conn.cursor()

# Criar a tabela 'usuarios'
cursor.execute('''
CREATE TABLE IF NOT EXISTS usuarios (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL
)
''')

# Inserir dados de exemplo
cursor.execute("INSERT INTO usuarios (nome, email) VALUES ('João', 'joao@email.com')")
cursor.execute("INSERT INTO usuarios (nome, email) VALUES ('Maria', 'maria@email.com')")

# Salvar alterações
conn.commit()

# Consultar e exibir os dados
cursor.execute('SELECT * FROM usuarios')
usuarios = cursor.fetchall()

print('Usuários no banco de dados:')
for usuario in usuarios:
    print(usuario)

# Fechar a conexão
conn.close()