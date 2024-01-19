# EBACSql
Portfólio de atividades dos cursos da EBAC
https://www.kaggle.com/rosianecanella/projeto-final-sql-ebac
https://www.kaggle.com/rosianecanella/projeto-final-sql-ebac

Segue meu projeto final do curso de SQL.

****************************************
# **Exploração e análise de dados de crédito com SQL**

#  > **Dados**
Os dados representam informações de clientes de um banco e contam com as seguintes colunas:

* idade = idade do cliente
* sexo = sexo do cliente (F ou M)
* dependentes = número de dependentes do cliente
* escolaridade = nível de escolaridade do clientes
* salario_anual = faixa salarial do cliente
* tipo_cartao = tipo de cartao do cliente
* qtd_produtos = quantidade de produtos comprados nos últimos 12 meses
* iteracoes_12m = quantidade de iterações/transacoes nos ultimos 12 meses
* meses_inativo_12m = quantidade de meses que o cliente ficou inativo
* limite_credito = limite de credito do cliente
* valor_transacoes_12m = valor das transações dos ultimos 12 meses
* qtd_transacoes_12m = quantidade de transacoes dos ultimos 12 meses
# **Qual a quantidade de informações temos na nossa base de dados?

Query: SELECT count(*) FROM credito

Reposta: **10127 linhas**

ps.: A base de dados do link acima contém mais linhas do que a seleção utilizada. Você pode utilizar todas as linhas ou considerar apenas uma fração dos dados. Na prática, quanto maior a quantidade de dados utilizada, mais confiável a análise! Mas existem limites computacionais e financeiros na qual a redução de dados para análise para fins de estudo se torna interessante.

Como são os dados

Query: SELECT * FROM credito LIMIT 10;Dez primeiras linhas do dataset
# Análise de dados
Verificação da base de dados e de que forma podem ser relacionados na concessão de créditos.
**Query: select count(*), salario_anual from credito group by salario_anual**
![image.png](attachment:7b83ae0f-e849-4c65-83e5-c42587353fa6.png)
Os clientes com maior faixa de renda fazem parte do grupo de menor representantes.E o grupo com mais representante é o da faixa com menor renda.
É interessante a composição dos gêneros dos grupos, para assim desenvolver modelos baseados nas rendas e culturas de consumos para cada gênero.
**Query: select count(*), sexo from credito group by sexo**
![image.png](attachment:ced8f8b3-9fe6-496e-979d-3a4f0c1afed8.png)
import matplotlib.pyplot as plt

fatias = [5358, 4769]
genero = ["Feminino" , "Masculino"]
cores = ['violet','royalblue']
plt.pie(fatias, labels = genero, colors = cores, startangle = 90, shadow = True, explode = (0,0.1))
plt.show()
Analisando a base de dados completa, tem-se que a maior representatividade está no grupo feminino.
Na análise mais granular, apenas do grupo feminino, observa-se que as idades com maiores números de representantes é na faixa dos 40 anos.
![![image.png](attachment:a205dbc4-d33d-446a-a79b-650dbea9f4aa.png)]
Ao analisar as faixas de salário anual por faixa etária, observa-se que o maior número de mulheres em variadas faixas de idades, está no grupo de menos de $40 K, revelando também que as mulheres de faixa etária a partir 50 anos, que possuem maiores possibilidades salariais, mas a representatividade numérica tende a ser bem menos expressiva.
![![image.png](attachment:04db59aa-e25d-43c4-8f8b-af35ad043ba5.png)]
Quando o mesmo estudo é realizado com o gênero masculino, a realidade é muito diferente e antagônica. Mesmo com uma porcentagem menor na representatividade nesse grupo, tem-se maiores faixas de salários anuais.Bem como nas faixas etárias menores. Como mostra a imagem abaixo:
![![image.png](attachment:61335d7c-95c5-4c14-bfc3-8393477d48b7.png)]
****Qual a maior e menor transação dos clientes?**
![![image.png](attachment:87e10749-328c-42d5-adf0-9b08dc6c9a05.png)]

*** Uma análise feita baseada na média do valor gasto, corrobora as afirmações anteriores, pois uma vez que os homens ganham maiores salários anuais, estão em maior proporção de valor médio gasto.**
Em relação a análise de limite de crédito, a escolaridade parece pouco influenciar nas ofertas de crédito, ao passo que tem-se  homem sem eduação formal e com doutorado, com o máximo de limite de crédito. E o mesmo comportamento é observado para o gênero feminino. Portanto, é possível que exista outras possibilidades de análise de oferta e acesso a créditos, como quesitos de renda e transacionalidade de cada cliente.
![![image.png](attachment:478acbca-2d30-40dc-9713-81c37c260186.png)]
# Conclusão
Essas foram algumas análises extraídas do dataset de crédito.

**Alguns insights interessantes:**

* a maior parte dos clientes possui renda até 40K e pertencem ao gênero feminino
* a maior parte dos clientes é feminino!
* a escolaridade não parece influenciar no limite nem no tipo do cartão
* os clientes com maiores limites são em sua maioria homens
* os clientes com menores limites são em sua maioria mulheres
* dentre os menores limites não há presença de cartão platinum
* a faixa salarial impacta diretamente no limite de crédito
* não existem clientes com salário anual acima de 60K do sexo feminino


