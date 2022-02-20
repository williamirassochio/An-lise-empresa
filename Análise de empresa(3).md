 Projeto de Análise de Dados

Vamos fazer um projeto com pandas para análise de dados.

O que temos?

Temos os dados de 2019 de uma empresa de prestação de serviços.

    CadastroFuncionarios
    CadastroClientes
    BaseServiçosPrestados

O que queremos saber/fazer?

    Valor Total da Folha Salarial -> Qual foi o gasto total com salários (salário + benefícios + impostos) de funcionários pela empresa?
    Valor Total da Folha Salarial da empresa foi de R$2,614,343.3
    
    Qual foi o faturamento da empresa?
    Faturamento total da empresa foi de R$5,519,160.   
    
    Qual o % de funcionários que já fechou algum contrato?
    Hoje no nosso quadro de funcionários, 86.84% deles já fecharam algum contrato.
  
    Calcule o total de contratos que cada área da empresa já fechou
    Nossos contratos por áreas são:
    Administrativo    63
    *Operações         48
    *Comercial         44
    *Financeiro        42
    *Logística         40

    Calcule o total de funcionários por área
    Nosso quadro de funcionários por área:
    *Administrativo    26
    *Comercial         26
    *Operações         23
    *Logística         21
    *Financeiro        18

    Qual o ticket médio mensal (faturamento médio mensal) dos contratos?
    Nosso ticket médio é de 2,438.35.



```python
# Trazer arquivos csv usando pandas, separando com sep:(,) e decimal:(,)
import pandas as pd

CadastroFuncionarios = pd.read_csv('CadastroFuncionarios.csv',sep = ';' ,decimal = ',')
CadastroClientes = pd.read_csv('CadastroClientes.csv',sep = ';',decimal = ',')
BaseServicosPrestados = pd.read_csv('trabalhodataframe.csv',encoding = 'ISO-8859-1',sep = ';',decimal = ',')

display(CadastroFuncionarios)
display(CadastroClientes)
display(BaseServicosPrestados)

```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Funcionário</th>
      <th>Estado Civil</th>
      <th>Nome Completo</th>
      <th>Salario Base</th>
      <th>Impostos</th>
      <th>Beneficios</th>
      <th>VT</th>
      <th>VR</th>
      <th>Cargo</th>
      <th>Area</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>C</td>
      <td>Gabriel Mesquita</td>
      <td>21910</td>
      <td>10955.0</td>
      <td>4382.0</td>
      <td>242</td>
      <td>719.04</td>
      <td>Diretor</td>
      <td>Operações</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>C</td>
      <td>João Haddad</td>
      <td>5404</td>
      <td>2702.0</td>
      <td>1080.8</td>
      <td>154</td>
      <td>574.56</td>
      <td>Estagiário</td>
      <td>Logística</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>C</td>
      <td>Amanda Marques Ribeiro</td>
      <td>16066</td>
      <td>8033.0</td>
      <td>3213.2</td>
      <td>154</td>
      <td>729.12</td>
      <td>Estagiário</td>
      <td>Administrativo</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>C</td>
      <td>Guilherme Nunez</td>
      <td>21305</td>
      <td>10652.5</td>
      <td>4261.0</td>
      <td>220</td>
      <td>524.16</td>
      <td>Analista</td>
      <td>Administrativo</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>C</td>
      <td>Adelino Gomes</td>
      <td>5098</td>
      <td>2549.0</td>
      <td>1019.6</td>
      <td>176</td>
      <td>725.76</td>
      <td>Analista</td>
      <td>Administrativo</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>109</th>
      <td>143</td>
      <td>C</td>
      <td>Renan Scharnhorst Ott</td>
      <td>10793</td>
      <td>5396.5</td>
      <td>2158.6</td>
      <td>242</td>
      <td>514.08</td>
      <td>Analista</td>
      <td>Logística</td>
    </tr>
    <tr>
      <th>110</th>
      <td>144</td>
      <td>S</td>
      <td>Lucas Brum Pereira</td>
      <td>4048</td>
      <td>2024.0</td>
      <td>809.6</td>
      <td>198</td>
      <td>796.32</td>
      <td>Estagiário</td>
      <td>Comercial</td>
    </tr>
    <tr>
      <th>111</th>
      <td>148</td>
      <td>S</td>
      <td>Caio Stellet</td>
      <td>24596</td>
      <td>12298.0</td>
      <td>4919.2</td>
      <td>242</td>
      <td>561.12</td>
      <td>Analista</td>
      <td>Administrativo</td>
    </tr>
    <tr>
      <th>112</th>
      <td>149</td>
      <td>C</td>
      <td>Fernanda Rocha</td>
      <td>5078</td>
      <td>2539.0</td>
      <td>1015.6</td>
      <td>308</td>
      <td>665.28</td>
      <td>Estagiário</td>
      <td>Comercial</td>
    </tr>
    <tr>
      <th>113</th>
      <td>150</td>
      <td>C</td>
      <td>Eduardo Brum</td>
      <td>15939</td>
      <td>7969.5</td>
      <td>3187.8</td>
      <td>220</td>
      <td>769.44</td>
      <td>Analista</td>
      <td>Comercial</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 10 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Cliente</th>
      <th>Cliente</th>
      <th>Valor Contrato Mensal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Teixeira Gonçalves</td>
      <td>540</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Souza Santos</td>
      <td>1260</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Emídio Alves</td>
      <td>3195</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Santos Costa</td>
      <td>2520</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Do Monteiro</td>
      <td>3510</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>315</th>
      <td>316</td>
      <td>Manoel Costa</td>
      <td>3690</td>
    </tr>
    <tr>
      <th>316</th>
      <td>317</td>
      <td>Gomes Machado</td>
      <td>2385</td>
    </tr>
    <tr>
      <th>317</th>
      <td>318</td>
      <td>Alkindar Cardozo</td>
      <td>3510</td>
    </tr>
    <tr>
      <th>318</th>
      <td>319</td>
      <td>Pereira Fazenda</td>
      <td>4185</td>
    </tr>
    <tr>
      <th>319</th>
      <td>320</td>
      <td>Americo Damasceno</td>
      <td>2430</td>
    </tr>
  </tbody>
</table>
<p>320 rows × 3 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Codigo do Servico</th>
      <th>ID Funcionário</th>
      <th>ID Cliente</th>
      <th>Tempo Total de Contrato (Meses)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>OS0001</td>
      <td>67</td>
      <td>1</td>
      <td>14</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OS0002</td>
      <td>17</td>
      <td>2</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>OS0003</td>
      <td>116</td>
      <td>4</td>
      <td>14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OS0004</td>
      <td>37</td>
      <td>5</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OS0005</td>
      <td>130</td>
      <td>6</td>
      <td>8</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>232</th>
      <td>OS0233</td>
      <td>111</td>
      <td>315</td>
      <td>4</td>
    </tr>
    <tr>
      <th>233</th>
      <td>OS0234</td>
      <td>124</td>
      <td>316</td>
      <td>8</td>
    </tr>
    <tr>
      <th>234</th>
      <td>OS0235</td>
      <td>72</td>
      <td>317</td>
      <td>6</td>
    </tr>
    <tr>
      <th>235</th>
      <td>OS0236</td>
      <td>90</td>
      <td>319</td>
      <td>14</td>
    </tr>
    <tr>
      <th>236</th>
      <td>OS0237</td>
      <td>22</td>
      <td>320</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
<p>237 rows × 4 columns</p>
</div>



```python
CadastroFuncionarios.info()
CadastroFuncionarios[['Salario Base','Impostos','Beneficios']]
CadastroFuncionarios['Folha Salarial'] = CadastroFuncionarios['Salario Base'] + CadastroFuncionarios['Impostos'] + CadastroFuncionarios['Beneficios']
print('Valor Total da Folha Salarial da empresa foi de R${:,}'.format(CadastroFuncionarios['Folha Salarial'].sum()))
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 114 entries, 0 to 113
    Data columns (total 10 columns):
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
    dtypes: float64(3), int64(3), object(4)
    memory usage: 7.2+ KB
    Valor Total da Folha Salarial da empresa foi de R$2,614,343.3
    


```python
display(CadastroClientes)
CadastroClientes = BaseServicosPrestados[['ID Cliente','Tempo Total de Contrato (Meses)']].merge(CadastroClientes[['ID Cliente','Valor Contrato Mensal']],on = 'ID Cliente')
display(CadastroClientes)
CadastroClientes['Faturamento_total'] = CadastroClientes['Tempo Total de Contrato (Meses)'] * CadastroClientes['Valor Contrato Mensal']
print('Faturamento total da empresa foi de R${:,}.'.format((CadastroClientes['Faturamento_total'].sum())))
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Cliente</th>
      <th>Cliente</th>
      <th>Valor Contrato Mensal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Teixeira Gonçalves</td>
      <td>540</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Souza Santos</td>
      <td>1260</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Emídio Alves</td>
      <td>3195</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Santos Costa</td>
      <td>2520</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Do Monteiro</td>
      <td>3510</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>315</th>
      <td>316</td>
      <td>Manoel Costa</td>
      <td>3690</td>
    </tr>
    <tr>
      <th>316</th>
      <td>317</td>
      <td>Gomes Machado</td>
      <td>2385</td>
    </tr>
    <tr>
      <th>317</th>
      <td>318</td>
      <td>Alkindar Cardozo</td>
      <td>3510</td>
    </tr>
    <tr>
      <th>318</th>
      <td>319</td>
      <td>Pereira Fazenda</td>
      <td>4185</td>
    </tr>
    <tr>
      <th>319</th>
      <td>320</td>
      <td>Americo Damasceno</td>
      <td>2430</td>
    </tr>
  </tbody>
</table>
<p>320 rows × 3 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Cliente</th>
      <th>Tempo Total de Contrato (Meses)</th>
      <th>Valor Contrato Mensal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>14</td>
      <td>540</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>12</td>
      <td>1260</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>14</td>
      <td>2520</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>8</td>
      <td>3510</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>8</td>
      <td>2340</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>232</th>
      <td>315</td>
      <td>4</td>
      <td>1575</td>
    </tr>
    <tr>
      <th>233</th>
      <td>316</td>
      <td>8</td>
      <td>3690</td>
    </tr>
    <tr>
      <th>234</th>
      <td>317</td>
      <td>6</td>
      <td>2385</td>
    </tr>
    <tr>
      <th>235</th>
      <td>319</td>
      <td>14</td>
      <td>4185</td>
    </tr>
    <tr>
      <th>236</th>
      <td>320</td>
      <td>12</td>
      <td>2430</td>
    </tr>
  </tbody>
</table>
<p>237 rows × 3 columns</p>
</div>


    Faturamento total da empresa foi de R$5,519,160.
    


```python
display(CadastroFuncionarios)
display(BaseServicosPrestados)
numero_funcionarios = len(CadastroFuncionarios['ID Funcionário'])
display(numero_funcionarios)
qtd_funcionarios = len(BaseServicosPrestados['ID Funcionário'].unique())
display(qtd_funcionarios)
print('Hoje no nosso quadro de funcionários, {:.2%} deles já fecharam algum contrato.'.format(qtd_funcionarios / numero_funcionarios))

```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Funcionário</th>
      <th>Estado Civil</th>
      <th>Nome Completo</th>
      <th>Salario Base</th>
      <th>Impostos</th>
      <th>Beneficios</th>
      <th>VT</th>
      <th>VR</th>
      <th>Cargo</th>
      <th>Area</th>
      <th>Folha Salarial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>C</td>
      <td>Gabriel Mesquita</td>
      <td>21910</td>
      <td>10955.0</td>
      <td>4382.0</td>
      <td>242</td>
      <td>719.04</td>
      <td>Diretor</td>
      <td>Operações</td>
      <td>37247.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>C</td>
      <td>João Haddad</td>
      <td>5404</td>
      <td>2702.0</td>
      <td>1080.8</td>
      <td>154</td>
      <td>574.56</td>
      <td>Estagiário</td>
      <td>Logística</td>
      <td>9186.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>C</td>
      <td>Amanda Marques Ribeiro</td>
      <td>16066</td>
      <td>8033.0</td>
      <td>3213.2</td>
      <td>154</td>
      <td>729.12</td>
      <td>Estagiário</td>
      <td>Administrativo</td>
      <td>27312.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>C</td>
      <td>Guilherme Nunez</td>
      <td>21305</td>
      <td>10652.5</td>
      <td>4261.0</td>
      <td>220</td>
      <td>524.16</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>36218.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>C</td>
      <td>Adelino Gomes</td>
      <td>5098</td>
      <td>2549.0</td>
      <td>1019.6</td>
      <td>176</td>
      <td>725.76</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>8666.6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>109</th>
      <td>143</td>
      <td>C</td>
      <td>Renan Scharnhorst Ott</td>
      <td>10793</td>
      <td>5396.5</td>
      <td>2158.6</td>
      <td>242</td>
      <td>514.08</td>
      <td>Analista</td>
      <td>Logística</td>
      <td>18348.1</td>
    </tr>
    <tr>
      <th>110</th>
      <td>144</td>
      <td>S</td>
      <td>Lucas Brum Pereira</td>
      <td>4048</td>
      <td>2024.0</td>
      <td>809.6</td>
      <td>198</td>
      <td>796.32</td>
      <td>Estagiário</td>
      <td>Comercial</td>
      <td>6881.6</td>
    </tr>
    <tr>
      <th>111</th>
      <td>148</td>
      <td>S</td>
      <td>Caio Stellet</td>
      <td>24596</td>
      <td>12298.0</td>
      <td>4919.2</td>
      <td>242</td>
      <td>561.12</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>41813.2</td>
    </tr>
    <tr>
      <th>112</th>
      <td>149</td>
      <td>C</td>
      <td>Fernanda Rocha</td>
      <td>5078</td>
      <td>2539.0</td>
      <td>1015.6</td>
      <td>308</td>
      <td>665.28</td>
      <td>Estagiário</td>
      <td>Comercial</td>
      <td>8632.6</td>
    </tr>
    <tr>
      <th>113</th>
      <td>150</td>
      <td>C</td>
      <td>Eduardo Brum</td>
      <td>15939</td>
      <td>7969.5</td>
      <td>3187.8</td>
      <td>220</td>
      <td>769.44</td>
      <td>Analista</td>
      <td>Comercial</td>
      <td>27096.3</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 11 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Codigo do Servico</th>
      <th>ID Funcionário</th>
      <th>ID Cliente</th>
      <th>Tempo Total de Contrato (Meses)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>OS0001</td>
      <td>67</td>
      <td>1</td>
      <td>14</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OS0002</td>
      <td>17</td>
      <td>2</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>OS0003</td>
      <td>116</td>
      <td>4</td>
      <td>14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OS0004</td>
      <td>37</td>
      <td>5</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OS0005</td>
      <td>130</td>
      <td>6</td>
      <td>8</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>232</th>
      <td>OS0233</td>
      <td>111</td>
      <td>315</td>
      <td>4</td>
    </tr>
    <tr>
      <th>233</th>
      <td>OS0234</td>
      <td>124</td>
      <td>316</td>
      <td>8</td>
    </tr>
    <tr>
      <th>234</th>
      <td>OS0235</td>
      <td>72</td>
      <td>317</td>
      <td>6</td>
    </tr>
    <tr>
      <th>235</th>
      <td>OS0236</td>
      <td>90</td>
      <td>319</td>
      <td>14</td>
    </tr>
    <tr>
      <th>236</th>
      <td>OS0237</td>
      <td>22</td>
      <td>320</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
<p>237 rows × 4 columns</p>
</div>



    114



    99


    Hoje no nosso quadro de funcionários, 86.84% deles já fecharam algum contrato.
    


```python
display(CadastroFuncionarios)
display(BaseServicosPrestados)
Cadastro_contratos_area = BaseServicosPrestados.merge(CadastroFuncionarios,on = 'ID Funcionário')
display(Cadastro_contratos_area[['ID Funcionário','Area']])
numeros_contratos = Cadastro_contratos_area['Area'].value_counts()
print('Nossos contratos por áreas são:')
print(numeros_contratos)

```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Funcionário</th>
      <th>Estado Civil</th>
      <th>Nome Completo</th>
      <th>Salario Base</th>
      <th>Impostos</th>
      <th>Beneficios</th>
      <th>VT</th>
      <th>VR</th>
      <th>Cargo</th>
      <th>Area</th>
      <th>Folha Salarial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>C</td>
      <td>Gabriel Mesquita</td>
      <td>21910</td>
      <td>10955.0</td>
      <td>4382.0</td>
      <td>242</td>
      <td>719.04</td>
      <td>Diretor</td>
      <td>Operações</td>
      <td>37247.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>C</td>
      <td>João Haddad</td>
      <td>5404</td>
      <td>2702.0</td>
      <td>1080.8</td>
      <td>154</td>
      <td>574.56</td>
      <td>Estagiário</td>
      <td>Logística</td>
      <td>9186.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>C</td>
      <td>Amanda Marques Ribeiro</td>
      <td>16066</td>
      <td>8033.0</td>
      <td>3213.2</td>
      <td>154</td>
      <td>729.12</td>
      <td>Estagiário</td>
      <td>Administrativo</td>
      <td>27312.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>C</td>
      <td>Guilherme Nunez</td>
      <td>21305</td>
      <td>10652.5</td>
      <td>4261.0</td>
      <td>220</td>
      <td>524.16</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>36218.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>C</td>
      <td>Adelino Gomes</td>
      <td>5098</td>
      <td>2549.0</td>
      <td>1019.6</td>
      <td>176</td>
      <td>725.76</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>8666.6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>109</th>
      <td>143</td>
      <td>C</td>
      <td>Renan Scharnhorst Ott</td>
      <td>10793</td>
      <td>5396.5</td>
      <td>2158.6</td>
      <td>242</td>
      <td>514.08</td>
      <td>Analista</td>
      <td>Logística</td>
      <td>18348.1</td>
    </tr>
    <tr>
      <th>110</th>
      <td>144</td>
      <td>S</td>
      <td>Lucas Brum Pereira</td>
      <td>4048</td>
      <td>2024.0</td>
      <td>809.6</td>
      <td>198</td>
      <td>796.32</td>
      <td>Estagiário</td>
      <td>Comercial</td>
      <td>6881.6</td>
    </tr>
    <tr>
      <th>111</th>
      <td>148</td>
      <td>S</td>
      <td>Caio Stellet</td>
      <td>24596</td>
      <td>12298.0</td>
      <td>4919.2</td>
      <td>242</td>
      <td>561.12</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>41813.2</td>
    </tr>
    <tr>
      <th>112</th>
      <td>149</td>
      <td>C</td>
      <td>Fernanda Rocha</td>
      <td>5078</td>
      <td>2539.0</td>
      <td>1015.6</td>
      <td>308</td>
      <td>665.28</td>
      <td>Estagiário</td>
      <td>Comercial</td>
      <td>8632.6</td>
    </tr>
    <tr>
      <th>113</th>
      <td>150</td>
      <td>C</td>
      <td>Eduardo Brum</td>
      <td>15939</td>
      <td>7969.5</td>
      <td>3187.8</td>
      <td>220</td>
      <td>769.44</td>
      <td>Analista</td>
      <td>Comercial</td>
      <td>27096.3</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 11 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Codigo do Servico</th>
      <th>ID Funcionário</th>
      <th>ID Cliente</th>
      <th>Tempo Total de Contrato (Meses)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>OS0001</td>
      <td>67</td>
      <td>1</td>
      <td>14</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OS0002</td>
      <td>17</td>
      <td>2</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>OS0003</td>
      <td>116</td>
      <td>4</td>
      <td>14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OS0004</td>
      <td>37</td>
      <td>5</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OS0005</td>
      <td>130</td>
      <td>6</td>
      <td>8</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>232</th>
      <td>OS0233</td>
      <td>111</td>
      <td>315</td>
      <td>4</td>
    </tr>
    <tr>
      <th>233</th>
      <td>OS0234</td>
      <td>124</td>
      <td>316</td>
      <td>8</td>
    </tr>
    <tr>
      <th>234</th>
      <td>OS0235</td>
      <td>72</td>
      <td>317</td>
      <td>6</td>
    </tr>
    <tr>
      <th>235</th>
      <td>OS0236</td>
      <td>90</td>
      <td>319</td>
      <td>14</td>
    </tr>
    <tr>
      <th>236</th>
      <td>OS0237</td>
      <td>22</td>
      <td>320</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
<p>237 rows × 4 columns</p>
</div>



<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Funcionário</th>
      <th>Area</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>67</td>
      <td>Financeiro</td>
    </tr>
    <tr>
      <th>1</th>
      <td>67</td>
      <td>Financeiro</td>
    </tr>
    <tr>
      <th>2</th>
      <td>67</td>
      <td>Financeiro</td>
    </tr>
    <tr>
      <th>3</th>
      <td>67</td>
      <td>Financeiro</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17</td>
      <td>Logística</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>232</th>
      <td>25</td>
      <td>Administrativo</td>
    </tr>
    <tr>
      <th>233</th>
      <td>79</td>
      <td>Operações</td>
    </tr>
    <tr>
      <th>234</th>
      <td>99</td>
      <td>Administrativo</td>
    </tr>
    <tr>
      <th>235</th>
      <td>14</td>
      <td>Financeiro</td>
    </tr>
    <tr>
      <th>236</th>
      <td>72</td>
      <td>Logística</td>
    </tr>
  </tbody>
</table>
<p>237 rows × 2 columns</p>
</div>


    Nossos contratos por áreas são:
    Administrativo    63
    Operações         48
    Comercial         44
    Financeiro        42
    Logística         40
    Name: Area, dtype: int64
    


```python
display(CadastroFuncionarios)
qtd_func_area = CadastroFuncionarios['Area'].value_counts()
print('Nosso quadro de funcionários por área:')
print(qtd_func_area)
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Funcionário</th>
      <th>Estado Civil</th>
      <th>Nome Completo</th>
      <th>Salario Base</th>
      <th>Impostos</th>
      <th>Beneficios</th>
      <th>VT</th>
      <th>VR</th>
      <th>Cargo</th>
      <th>Area</th>
      <th>Folha Salarial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>C</td>
      <td>Gabriel Mesquita</td>
      <td>21910</td>
      <td>10955.0</td>
      <td>4382.0</td>
      <td>242</td>
      <td>719.04</td>
      <td>Diretor</td>
      <td>Operações</td>
      <td>37247.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>C</td>
      <td>João Haddad</td>
      <td>5404</td>
      <td>2702.0</td>
      <td>1080.8</td>
      <td>154</td>
      <td>574.56</td>
      <td>Estagiário</td>
      <td>Logística</td>
      <td>9186.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>C</td>
      <td>Amanda Marques Ribeiro</td>
      <td>16066</td>
      <td>8033.0</td>
      <td>3213.2</td>
      <td>154</td>
      <td>729.12</td>
      <td>Estagiário</td>
      <td>Administrativo</td>
      <td>27312.2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>C</td>
      <td>Guilherme Nunez</td>
      <td>21305</td>
      <td>10652.5</td>
      <td>4261.0</td>
      <td>220</td>
      <td>524.16</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>36218.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>C</td>
      <td>Adelino Gomes</td>
      <td>5098</td>
      <td>2549.0</td>
      <td>1019.6</td>
      <td>176</td>
      <td>725.76</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>8666.6</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>109</th>
      <td>143</td>
      <td>C</td>
      <td>Renan Scharnhorst Ott</td>
      <td>10793</td>
      <td>5396.5</td>
      <td>2158.6</td>
      <td>242</td>
      <td>514.08</td>
      <td>Analista</td>
      <td>Logística</td>
      <td>18348.1</td>
    </tr>
    <tr>
      <th>110</th>
      <td>144</td>
      <td>S</td>
      <td>Lucas Brum Pereira</td>
      <td>4048</td>
      <td>2024.0</td>
      <td>809.6</td>
      <td>198</td>
      <td>796.32</td>
      <td>Estagiário</td>
      <td>Comercial</td>
      <td>6881.6</td>
    </tr>
    <tr>
      <th>111</th>
      <td>148</td>
      <td>S</td>
      <td>Caio Stellet</td>
      <td>24596</td>
      <td>12298.0</td>
      <td>4919.2</td>
      <td>242</td>
      <td>561.12</td>
      <td>Analista</td>
      <td>Administrativo</td>
      <td>41813.2</td>
    </tr>
    <tr>
      <th>112</th>
      <td>149</td>
      <td>C</td>
      <td>Fernanda Rocha</td>
      <td>5078</td>
      <td>2539.0</td>
      <td>1015.6</td>
      <td>308</td>
      <td>665.28</td>
      <td>Estagiário</td>
      <td>Comercial</td>
      <td>8632.6</td>
    </tr>
    <tr>
      <th>113</th>
      <td>150</td>
      <td>C</td>
      <td>Eduardo Brum</td>
      <td>15939</td>
      <td>7969.5</td>
      <td>3187.8</td>
      <td>220</td>
      <td>769.44</td>
      <td>Analista</td>
      <td>Comercial</td>
      <td>27096.3</td>
    </tr>
  </tbody>
</table>
<p>114 rows × 11 columns</p>
</div>


    Nosso quadro de funcionários por área:
    Administrativo    26
    Comercial         26
    Operações         23
    Logística         21
    Financeiro        18
    Name: Area, dtype: int64
    


```python
display(CadastroClientes)
média_valor_contratos = CadastroClientes['Valor Contrato Mensal'].mean()
print('Nosso ticket médio é de {:,.2f}.'.format(média_valor_contratos))
```


<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID Cliente</th>
      <th>Tempo Total de Contrato (Meses)</th>
      <th>Valor Contrato Mensal</th>
      <th>Faturamento_total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>14</td>
      <td>540</td>
      <td>7560</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>12</td>
      <td>1260</td>
      <td>15120</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>14</td>
      <td>2520</td>
      <td>35280</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>8</td>
      <td>3510</td>
      <td>28080</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>8</td>
      <td>2340</td>
      <td>18720</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>232</th>
      <td>315</td>
      <td>4</td>
      <td>1575</td>
      <td>6300</td>
    </tr>
    <tr>
      <th>233</th>
      <td>316</td>
      <td>8</td>
      <td>3690</td>
      <td>29520</td>
    </tr>
    <tr>
      <th>234</th>
      <td>317</td>
      <td>6</td>
      <td>2385</td>
      <td>14310</td>
    </tr>
    <tr>
      <th>235</th>
      <td>319</td>
      <td>14</td>
      <td>4185</td>
      <td>58590</td>
    </tr>
    <tr>
      <th>236</th>
      <td>320</td>
      <td>12</td>
      <td>2430</td>
      <td>29160</td>
    </tr>
  </tbody>
</table>
<p>237 rows × 4 columns</p>
</div>


    Nosso ticket médio é de 2,438.35.
    
