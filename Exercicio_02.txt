import sqlite3
conn = sqlite3.connect(':memory:')

c = conn.cursor()

c.execute('''CREATE TABLE exercicio1_gabriel(id integer,nome text not null,email text,primary key (id) )'''
                )

c.execute("INSERT INTO exercicio1_gabriel VALUES (1,'GABRIEL GRANERO','gabrielgranero@gmail.com')")

c.execute('''SELECT * 
                FROM sqlite_master AS m, pragma_table_info(m.name)
                WHERE tbl_name = 'exercicio1_gabriel'
            ''')

for row in c.fetchall():
    print('----------------- tabelas ----------------')
    print('Nomes dos campos: ', row[6])
    print('Primary Key: ', row[10])
    print('Permite nulo? : ', row[8])

conn.commit()
conn.close()
