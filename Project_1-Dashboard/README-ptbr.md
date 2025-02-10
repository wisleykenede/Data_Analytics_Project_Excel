# Projeto 1 - Dashboard de Salários no Excel

 ![Salary Dashboard Pic](../Resources/Images/Salary_Dashboard.png)

## Introdução

 Esse dashboard foi criado para servir como orientação para candidatos a emprego investigar salários para diversos empregos em Ciência de Dados em város países.

### Dashboard File
 Meu dashboard final está no arquivo [Salary_Dashboard.xlsx](Salary_Dashboard.xlsx).

### Habilidades do Excel usadas

 As seguintes habilidades em Excel foram usadas neste projeto:

 - 📉 **Gráficos**
 - 🧮 **Funções e Fórmulas**
 - ❎ **Data Validation**

### Dataset de Ofertas de Emprego
 O Dataset utilizado nesse projeto e mais informações sobre o mesmo pode ser econtrado [aqui](../Resources/Dataset).

## Construção do Dashboard

 Essa seção lista cada uma das *Habilidades do Excel usadas* e explica como e porque elas foram usadas, e quais *insights* elas dão.

### 📉 Gráficos

#### 📊 Gráfico de Barras

 ![Bar_Chart](../Resources/Images/Salary_Dashboard_Bar_Chart.png)

 - Gráficos de barra horizontal são bons para comparações visuais como Salário Mediano de diferentes empregos.
 - Organizando o gráfico de forma decrescente pelo salário melhora a legibilidade.
 - Isso habilita uma identificação rápida de tendências nos salários dos empregos de ciência de dados, como por exemplo vagas de Senior e Engenheiros tem um pagamento maior do que Analistas.

#### 🗺️ Gráfico de Mapa

 ![Map_Chart](../Resources/Images/Salary_Dashboard_MapChart.png)
 
 - Gráfico de mapa codificado por cores ajuda visualizar deferentes níveis de salários entre regiões.
 - Legibilidade melhorada e entendimento imediato de tendências salariais geográficas.
 - Habilita rápido entendimento de diferenças salariais globais e destaca regiões com salários altos e baixos. 

### 🧮 Funções e Fórmulas

#### 💰 Salário Mediano
```
=MEDIAN(
    IF((jobs[job_title_short]=title)*
        (jobs[job_country]=country)*
        (ISNUMBER(SEARCH(type,jobs[job_schedule_type]))),
        jobs[salary_year_combined])
)
```

 - Essa fórmula fornece informação salarial específica para dados cargos, regiões e regimes de trabalho.
 - Nela eu utilizo a função `MEDIAN()` com um `IF()` aninhado para analizar um vetor.
 - No parâmetro de condição da função `IF()` é feita uma multiplicação dos resultados binários de três verificações dos valores das variáveis `title`, `country` e `type`.
 - Essa fórmula foi usada para popular a tabela abaixo, retornando o salário mediano baseado em cargo, país e regime de trabalho.
 - Nesse caso em específico, `country` e `type`são parâmetros fixados onde `title` varia baseado na coluna *job_title_short_sorted*.

 **Tabela**

 ![Job Title Table](../Resources/Images/Salary_Dashboard_Job_Title_Table.png)

 **Implementação no Dashboard**

 ![Dashboard Table Implementation](../Resources/Images/Salary_Dashboard_Dashboard_Implementation.png)

#### ⏰ Contagem de tipos de Regime de Trabalho

 ```
 =FILTER(J2#,
    NOT(ISNUMBER(SEARCH("and",J2#)))*
    NOT(ISNUMBER(SEARCH(",",J2#)))*
    (J2#<>0)
)
 ```

 - A fórmula em Excel acima usa a função `FILTER()` para excluir entradas de dados contendo *"and"* ou vírgulas e omitindo valores nulos.
 - Essa fórmula popula a tabela abaixo, o que nos dá uma lista de tipos de regimo de trabalho únicos.
 
 **Tabela**

 ![Types Table](../Resources/Images/Salary_Dashboard_Types.png)
 
  **Implementação no Dashboard**

 ![Types Implementation](../Resources/Images/Salary_Dashboard_Type_Implementation.png)

### ❎ Data Validation

#### 🔍 Lista Filtrada 

 ![Data Validation](../Resources/Images/Salary_Dashboard_Data_Validation.gif)

 - Implementando a Lista Filtrada como uma regra de Data Validation para as opções de `Job Title`, `Country`, e `Type` no dashboard garante:
     - Entradas de usuários é restrita para predefinidos e validados cargos, países e regimes de trabalho.
     - Entradas incorretas ou inconsistentes são previnidas.
     - O que resulta em uma melhora na usabilidade do Dashboard.

## Conclusão

 Eu criei esse Dashboard para mostrar *insights* em tendências de salários entre vários cargos relacionados a ciência de dados. Isso permite a usuários fazer decisões mais informativas sobre suas carreiras, explorando as funcionalidades para entender como localização e cargos influenciam salários.