---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="a6UlPiHeXMXu">

#CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="tO_vOeE9XU_C">

#World Happiness Report Dataset Background Information **Description**:

The dataset ranks countries by their happiness index from World
Happiness Report.

**Github**:
<https://github.com/PhilippeCodes/World-Happiness-Report-Data-Analysis/blob/master/World%20Happiness%20Report.csv>

**Sample Size**: 153

------------------------------------------------------------------------

**Feature Documentation**:

| Feature          | DType   |
|------------------|---------|
| Country          | object  |
| Happiness Rank   | int64   |
| Happiness Score  | float64 |
| Economy          | float64 |
| Family           | float64 |
| Health           | float64 |
| Freedom          | float64 |
| Generosity       | float64 |
| Corruption       | float64 |
| Dystopia         | float64 |
| Job Satisfaction | float64 |
| Region           | object  |

</div>

<div class="cell markdown" id="CiYlbaZDlyct">

##Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   My idea is to compare if European countries or Asia-Pacific
        countries have a higher happiness index. I am interested to see
        how region affects the general happiness of people living in
        those regions.
-   What two groups you are comparing:
    -   **G1**: Average happiness index of countries in Europe; **G2**:
        Average happiness index of countries in Asia-Pacific region.
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `Happiness Score`
-   Is your response variable quantitative rather than categorical?
    -   Yes since `Happiness Score` is a float value between 0 and 8,
        which is quantitative.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   It is expected that **G1** \> **G2** since European countries
        tend to have higher GDP per capita which is linked to higher
        living standards, and could contribute to happiness score.
-   Talk about how you will gather your data
    -   From Github link:
        <https://github.com/PhilippeCodes/World-Happiness-Report-Data-Analysis/blob/master/World%20Happiness%20Report.csv>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   Attempt to find more recent data
    -   Collect more data from sources that uses different ways to
        measure happiness index and evaluate them to pick the best one

</div>

<div class="cell code" execution_count="61"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="RnD-noiNasWv" outputId="c3da6554-5134-4cb6-a9c9-b0c125df2276">

``` python
import pandas as pd
df = pd.read_csv('https://github.com/PhilippeCodes/World-Happiness-Report-Data-Analysis/blob/master/World%20Happiness%20Report.csv?raw=true')
df.head(5)
```

<div class="output execute_result" execution_count="61">

           Happiness Rank  Happiness Score     Economy      Family      Health  \
    count      153.000000       153.000000  153.000000  153.000000  153.000000   
    mean        78.169935         5.349281    0.982433    1.186630    0.550117   
    std         45.008741         1.134997    0.421901    0.288441    0.237769   
    min          1.000000         2.693000    0.000000    0.000000    0.000000   
    25%         40.000000         4.497000    0.659517    1.041990    0.364509   
    50%         78.000000         5.279000    1.064578    1.251826    0.606042   
    75%        117.000000         6.098000    1.315175    1.416404    0.719217   
    max        155.000000         7.537000    1.870766    1.610574    0.949492   

              Freedom  Generosity  Corruption    Dystopia  Job Satisfaction  
    count  153.000000  153.000000  153.000000  153.000000        151.000000  
    mean     0.408489    0.245324    0.123179    1.853072         75.209934  
    std      0.150744    0.134395    0.102133    0.499490         12.962365  
    min      0.000000    0.000000    0.000000    0.377914         44.400000  
    25%      0.300741    0.153075    0.057070    1.597970         68.950000  
    50%      0.437454    0.231503    0.089848    1.832910         78.100000  
    75%      0.518631    0.322228    0.153066    2.150801         85.100000  
    max      0.658249    0.838075    0.464308    3.117485         95.100000  

</div>

</div>

<div class="cell markdown" id="vZgI7rANlvGm">

-   Tell us what groups you want to compare in the dataset
-   **G1** (Happiness Score \| Region = 'Western Europe', 'Eastern
    Europe' or 'Europe') vs. **G2** (Happiness Score \| Region =
    'Asia-Pacifc' )

</div>

<div class="cell markdown" id="vf3u3NXUDpLN">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="90"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="zMKa12NpDifH" outputId="1cb7bc53-2882-4dbc-ac70-ffdbff125add">

``` python
## First 5 records of G1
(df[(df['Region'] == 'Western Europe')|(df['Region'] == 'Eastern Europe')|(df['Region'] == 'Europe')]['Happiness Score']).head(5)
```

<div class="output execute_result" execution_count="90">

    0    7.537
    1    7.522
    2    7.504
    3    7.494
    4    7.469
    Name: Happiness Score, dtype: float64

</div>

</div>

<div class="cell code" execution_count="40"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="uu7AhoX3Eeto" outputId="dd6a330b-9a5f-4f1a-aede-4cfebfba5ef9">

``` python
## First 5 records of G1
(df[(df['Region'] == 'Asia-Pacific')]['Happiness Score']).head(5)
```

<div class="output execute_result" execution_count="40">

    7     7.314
    9     7.284
    10    7.213
    20    6.648
    25    6.572
    Name: Happiness Score, dtype: float64

</div>

</div>

<div class="cell markdown" id="FKKgt88AE2nO">

-   Other data description and visulization

1.  Number of countries in **G1** & **G2**

</div>

<div class="cell code" execution_count="42"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="ixLCOT6qE_gp" outputId="3fe52ff9-efc1-4573-d32d-940ad5eabb18">

``` python
##Number of countries in G1
len(df[(df['Region'] == 'Western Europe')|(df['Region'] == 'Eastern Europe')|(df['Region'] == 'Europe')]['Happiness Score'])
```

<div class="output execute_result" execution_count="42">

    42

</div>

</div>

<div class="cell code" execution_count="43"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="P6NzyD63FWiN" outputId="94c849d6-c23c-4a57-d0bd-aa0f9916c47f">

``` python
##Number of countries in G2
len(df[(df['Region'] == 'Asia-Pacific')]['Happiness Score'])
```

<div class="output execute_result" execution_count="43">

    43

</div>

</div>

<div class="cell markdown" id="inBjKJrKFzw5">

1.  Descriptive Statistics of **G1** & **G2**

</div>

<div class="cell code" execution_count="68"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="DI8cwOTtMHfn" outputId="d343b3d4-bc8c-4aa7-b494-4e7cd11dfc33">

``` python
##G1
df_G1 = df[(df['Region'] == 'Western Europe')|(df['Region'] == 'Eastern Europe')|(df['Region'] == 'Europe')]
df_G1.describe()
```

<div class="output execute_result" execution_count="68">

           Happiness Rank  Happiness Score    Economy     Family     Health  \
    count       42.000000        42.000000  42.000000  42.000000  42.000000   
    mean        48.952381         6.097929   1.308276   1.373987   0.745528   
    std         34.153850         0.900053   0.206509   0.174387   0.093658   
    min          1.000000         4.096000   0.728871   0.803685   0.541452   
    25%         17.250000         5.341750   1.218902   1.253417   0.685810   
    50%         50.500000         5.932500   1.333300   1.444934   0.791697   
    75%         74.500000         6.884000   1.458729   1.477789   0.817401   
    max        132.000000         7.537000   1.741944   1.610574   0.888961   

             Freedom  Generosity  Corruption   Dystopia  Job Satisfaction  
    count  42.000000   42.000000   42.000000  42.000000         41.000000  
    mean    0.417213    0.239109    0.134232   1.879572         83.375610  
    std     0.163163    0.132976    0.127535   0.407000          8.401065  
    min     0.095731    0.000000    0.000000   0.814382         68.500000  
    25%     0.267524    0.140677    0.036696   1.641973         75.100000  
    50%     0.463613    0.237076    0.065596   1.909965         85.200000  
    75%     0.571373    0.319067    0.243772   2.167250         91.100000  
    max     0.635423    0.574731    0.400770   2.807808         95.100000  

</div>

</div>

<div class="cell code" execution_count="67"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:300}"
id="Dm72EYeCRQie" outputId="5737a412-0e67-4507-f7af-feab8e8d55a5">

``` python
##G2
df_G2 = df[(df['Region'] == 'Asia-Pacific')]
df_G2.describe()
```

<div class="output execute_result" execution_count="67">

           Happiness Rank  Happiness Score    Economy     Family     Health  \
    count       43.000000        43.000000  43.000000  43.000000  43.000000   
    mean        78.325581         5.358326   1.059272   1.167791   0.608605   
    std         39.261468         0.955062   0.383432   0.282951   0.167196   
    min          8.000000         3.462000   0.367111   0.396103   0.180747   
    25%         44.500000         4.650000   0.781797   1.065360   0.500857   
    50%         80.000000         5.269000   1.074988   1.259976   0.606042   
    75%        109.000000         6.027500   1.388530   1.345784   0.681616   
    max        152.000000         7.314000   1.870766   1.548969   0.949492   

             Freedom  Generosity  Corruption   Dystopia  Job Satisfaction  
    count  43.000000   43.000000   43.000000  43.000000         43.000000  
    mean    0.429932    0.294002    0.148947   1.649736         77.834884  
    std     0.144497    0.171446    0.115798   0.467330          9.347546  
    min     0.081539    0.028807    0.015317   0.419389         50.700000  
    25%     0.305075    0.172462    0.064442   1.396350         72.150000  
    50%     0.449751    0.264451    0.107216   1.734704         79.800000  
    75%     0.543294    0.390670    0.230844   1.885810         83.850000  
    max     0.658249    0.838075    0.464308   2.801757         93.700000  

</div>

</div>

<div class="cell markdown" id="1N2GiyBtRlCh">

1.  Data visulizations of **G1** & **G2**

</div>

<div class="cell code" execution_count="64" id="osPYdE9VHPvN">

``` python
import matplotlib.pyplot as plt
import seaborn as sns
plt.rcParams['figure.figsize'] = [10, 5]

sns.set()
```

</div>

<div class="cell code" execution_count="72"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:983}"
id="3yoEcNE5SOH6" outputId="783e46fd-8cc8-4dc3-b30e-717243d216af">

``` python
##G1
sns.histplot(df_G1, x = 'Happiness Score')
plt.show()
sns.boxplot(data = df_G1, x = 'Happiness Score')
plt.show()
sns.violinplot(data = df_G1, x = 'Happiness Score')
plt.show()
```

<div class="output display_data">

![](68c19c639ef1e31e9e2ea4552c2e3b7344042384.png)

</div>

<div class="output display_data">

![](d3ef862e0ff4b1a168859e2e97985924e585242a.png)

</div>

<div class="output display_data">

![](963c753d0ccb0a622243b27b130a86765e4536f8.png)

</div>

</div>

<div class="cell code" execution_count="73"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:983}"
id="NAKwEFj8SOAM" outputId="010b9f01-e282-4c13-966a-296c4ed7b9cc">

``` python
##G2
sns.histplot(df_G2, x = 'Happiness Score')
plt.show()
sns.boxplot(data = df_G2, x = 'Happiness Score')
plt.show()
sns.violinplot(data = df_G2, x = 'Happiness Score')
plt.show()
```

<div class="output display_data">

![](b00c76953e952cb8272d13395a616d20e3b8cbea.png)

</div>

<div class="output display_data">

![](132bffb439deb33fe52637300a9857392f09cfa8.png)

</div>

<div class="output display_data">

![](8f81d62d7f5b3e0e544d52680ac5140cbebeb8ac.png)

</div>

</div>

<div class="cell code" execution_count="98"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:983}"
id="tQZlFHJYSNzY" outputId="560a8706-a9ae-45e0-ab2d-f578298b98a5">

``` python
##G1 & G2
df_both = df[(df['Region'] == 'Western Europe')|(df['Region'] == 'Eastern Europe')|(df['Region'] == 'Europe')|(df['Region'] == 'Asia-Pacific')]
df_both = df_both.replace(to_replace = ["Western Europe", "Eastern Europe"], value = "Europe")

sns.histplot(df_both, x = 'Happiness Score', hue = 'Region')
plt.show()
sns.boxplot(data = df_both, x = 'Happiness Score', y = 'Region')
plt.show()
sns.violinplot(data = df_both, x = 'Happiness Score', y = 'Region')
plt.show()
```

<div class="output display_data">

![](1420e35db67b723ca39537a554e99a6d1f990b17.png)

</div>

<div class="output display_data">

![](7800597677d742782bf39610d415f55f0a5d1e2e.png)

</div>

<div class="output display_data">

![](375581ba38cedc0e053c6ebe1a3c9c40426081df.png)

</div>

</div>
