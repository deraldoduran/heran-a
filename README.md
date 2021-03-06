# heranca
```sql
CREATE TABLE IF NOT EXISTS capitais(
  nome VARCHAR(60),
  populacao NUMERIC(10,2),
  altitude INT,
  estado VARCHAR(2)
  );
  ```
  ```sql
  CREATE TABLE IF NOT EXISTS interior(
    nome VARCHAR(60),
    populacao NUMERIC(10,2),
    altitude INT
    );
    ```
    ```sql
    INSERT INTO CAPITAIS_ (NOME, POPULACAO, ALTITUDE, ESTADO) VALUES
('FORTALEZA', 500000, 500, 'CE'),
('NATAL', 2000000, 700, 'RN'),
('SÃO PAULO', 500000, 500, 'SP'),
('RIO DE JANEIRO', 250000, 200, 'RJ');
```
```sql
INSERT INTO interior (NOME, POPULACAO, ALTITUDE) VALUES
('QUIXADÁ', 900000, 200),
('QUIXERAMOBIM', 80000, 200),
('SENADOR POMPEU', 20000, 300),
('BANABUIÚ', 10000, 100),
('ACOPIARA', 40000, 1500),
('PIRIPIRI', 15000, 500),
('PINDAMONHAGABA', 300000, 1200),
('CANINDÉ', 500000, 300);
```
```sql
CREATE VIEW todas_as_cidades AS 
SELECT nome, populacao, altitude FROM capitais
UNION
SELECT nome, populacao, altitude FROM interior

SELECT * FROM todas_as_cidades WHERE altitude > 500;
```
```sql
--USANDO HERANÇA
CREATE TABLE IF NOT EXISTS cidades(
    nome VARCHAR(60),
    populacao NUMERIC(10,2),
    altitude INT
    );
    
CREATE TABLE IF NOT EXISTS capitais(
  estado varchar(2)
  )INHERITS (cidades);
  
  --OS INSERTS SÃO IGUAIS
  
    INSERT INTO CAPITAIS_HERANCA (NOME, POPULACAO, ALTITUDE, ESTADO) VALUES
('FORTALEZA', 500000, 500, 'CE'),
('NATAL', 2000000, 700, 'RN'),
('SÃO PAULO', 500000, 500, 'SP'),
('RIO DE JANEIRO', 250000, 200, 'RJ');

INSERT INTO cidades (NOME, POPULACAO, ALTITUDE) VALUES
('QUIXADÁ', 900000, 200),
('QUIXERAMOBIM', 80000, 200),
('SENADOR POMPEU', 20000, 300),
('BANABUIÚ', 10000, 100),
('ACOPIARA', 40000, 1500),
('PIRIPIRI', 15000, 500),
('PINDAMONHAGABA', 300000, 1200),
('CANINDÉ', 500000, 300);

--QUANDO FAZ SELECT DE CICADES JÁ TRAZ A CIDADE E A CAPITAL POIS ESTA TAMBÉM É UMA CIDADE
SELECT * FROM cidades;
--só mostra as cidades
SELECT * FROM ONLY cidades;
```
```sql
-- ALTERAR NOMES DAS TABELAS
ALTER TABLE teste RENAME TO cliente;
ALTER TABLE cliente RENAME COLUMN enderesso to endereco;
ALTER TABLE cliente ALTER COLUMN nome TYPE VARCHAR(40);

--coloca um valor default de minha casa
ALTER TABLE cliente ALTER COLUMN endereco SET DEFAULT 'minha casa'; 
--muda o endereço em uma célula
UPDATE cliente SET endereco = 'rua 123' WHERE nome = 'juk';
--ELIMINA O DEFAULT PARA OS PRÓXIMOS
ALTER TABLE cliente ALTER COLUMN endereco DROP DEFAULT;
```
