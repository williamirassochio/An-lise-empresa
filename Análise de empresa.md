 Projeto de Analise de Dados

Vamos fazer um projeto com pandas para análise de dados.

O que temos?

Temos os dados de 2019 de uma empresa de prestação de serviços.

    CadastroFuncionarios
    CadastroClientes
    BaseServiçosPrestados

O que queremos saber/fazer?

    Valor Total da Folha Salarial -> Qual foi o gasto total com salários (salário + benefícios + impostos) de funcionários pela empresa?

    Qual foi o faturamento da empresa?

    Qual o % de funcionários que já fechou algum contrato?
   
  
    Calcule o total de contratos que cada área da empresa já fechou

    Calcule o total de funcionários por área

    Qual o ticket médio mensal (faturamento médio mensal) dos contratos?



```python
# Trazer arquivos csv usando pandas, separando com ssep:(,) e decimal:(,)
import pandas as pd

CadastroFuncionarios = pd.read_csv('CadastroFuncionarios.csv',sep = ';' ,decimal = ',')
CadastroClientes = pd.read_csv('CadastroClientes.csv',sep = ';',decimal = ',')
BaseServicosPrestados = pd.read_csv('trabalhodataframe.csv',sep = ';',decimal = ',')

display(CadastroFuncionarios)
display(CadastroClientes)
display(BaseServicosPrestados)

```


```python
CadastroFuncionarios.info()
CadastroFuncionarios[['Salario Base','Impostos','Beneficios']]
CadastroFuncionarios['Folha Salarial'] = CadastroFuncionarios['Salario Base'] + CadastroFuncionarios['Impostos'] + CadastroFuncionarios['Beneficios']
print('Valor Total da Folha Salarial da empresa foi de R${}'.format(CadastroFuncionarios['Folha Salarial'].sum()))
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 114 entries, 0 to 113
    Data columns (total 12 columns):
     #   Column          Non-Null Count  Dtype  
    ---  ------          --------------  -----  
     0   ID Funcionário  114 non-null    int64  
     1   Estado Civil    114 non-null    object 
     2   Nome Completo   114 non-null    object 
     3   Salario Base    114 non-null    int64  
     4   Impostos        114 non-null    float64
     5   Beneficios      114 non-null    float64
     6   VT              114 non-null    int64  
     7   VR              114 non-null    float64
     8   Cargo           114 non-null    object 
     9   Area            114 non-null    object 
     10  folha Salarial  114 non-null    float64
     11  Folha Salarial  114 non-null    float64
    dtypes: float64(5), int64(3), object(4)
    memory usage: 9.0+ KB
    Valor Total da Folha Salarial da empresa foi de R$2614343.3
    
