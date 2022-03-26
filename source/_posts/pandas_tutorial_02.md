---
title: "Pandas 입문 2 "
author: "HS"
date: '2022-03-27'
categories: 'Python'
---

# groupby 집중 연습
## 라이브러리 불러오기
- pandas 라이브러리 불러오고, supermarket_sales.csv 파일 불러오기
- 참고로 미얀마 자료. 얀곤이 옛 수도, 네피도는 현 수도
<!-- more-->

```python
import pandas as pd
print(pd.__version__)
```

    1.3.5
    


```python
from google.colab import drive
drive.mount('/content/drive') # "/content/drive" 도 가능
```

    Mounted at /content/drive
    


```python
DATA_PATH = '/content/drive/MyDrive/Colab Notebooks/data/supermarket_sales.csv'
sales = pd.read_csv(DATA_PATH) # 객체를 대문자로 썼는데, 개발자들이 좋아하는 방법이다. 눈에 띄는 걸 좋아한다. 
sales
```





  <div id="df-2c107087-f544-4f62-bedd-767a947c87b5">
    <div class="colab-df-container">
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
      <th>Invoice ID</th>
      <th>Branch</th>
      <th>City</th>
      <th>Customer type</th>
      <th>Gender</th>
      <th>Product line</th>
      <th>Unit price</th>
      <th>Quantity</th>
      <th>Date</th>
      <th>Time</th>
      <th>Payment</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>750-67-8428</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Female</td>
      <td>Health and beauty</td>
      <td>74.69</td>
      <td>7</td>
      <td>1/5/2019</td>
      <td>13:08</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>1</th>
      <td>226-31-3081</td>
      <td>C</td>
      <td>Naypyitaw</td>
      <td>Normal</td>
      <td>Female</td>
      <td>Electronic accessories</td>
      <td>15.28</td>
      <td>5</td>
      <td>3/8/2019</td>
      <td>10:29</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>2</th>
      <td>631-41-3108</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Home and lifestyle</td>
      <td>46.33</td>
      <td>7</td>
      <td>3/3/2019</td>
      <td>13:23</td>
      <td>Credit card</td>
    </tr>
    <tr>
      <th>3</th>
      <td>123-19-1176</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Male</td>
      <td>Health and beauty</td>
      <td>58.22</td>
      <td>8</td>
      <td>1/27/2019</td>
      <td>20:33</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>4</th>
      <td>373-73-7910</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Sports and travel</td>
      <td>86.31</td>
      <td>7</td>
      <td>2/8/2019</td>
      <td>10:37</td>
      <td>Ewallet</td>
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
      <th>995</th>
      <td>233-67-5758</td>
      <td>C</td>
      <td>Naypyitaw</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Health and beauty</td>
      <td>40.35</td>
      <td>1</td>
      <td>1/29/2019</td>
      <td>13:46</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>996</th>
      <td>303-96-2227</td>
      <td>B</td>
      <td>Mandalay</td>
      <td>Normal</td>
      <td>Female</td>
      <td>Home and lifestyle</td>
      <td>97.38</td>
      <td>10</td>
      <td>3/2/2019</td>
      <td>17:16</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>997</th>
      <td>727-02-1313</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Male</td>
      <td>Food and beverages</td>
      <td>31.84</td>
      <td>1</td>
      <td>2/9/2019</td>
      <td>13:22</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>998</th>
      <td>347-56-2442</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Home and lifestyle</td>
      <td>65.82</td>
      <td>1</td>
      <td>2/22/2019</td>
      <td>15:33</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>999</th>
      <td>849-09-3807</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Female</td>
      <td>Fashion accessories</td>
      <td>88.34</td>
      <td>7</td>
      <td>2/18/2019</td>
      <td>13:28</td>
      <td>Cash</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 11 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-2c107087-f544-4f62-bedd-767a947c87b5')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-2c107087-f544-4f62-bedd-767a947c87b5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-2c107087-f544-4f62-bedd-767a947c87b5');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




- 역시 인포부터 알아본다.


```python
sales.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1000 entries, 0 to 999
    Data columns (total 11 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   Invoice ID     1000 non-null   object 
     1   Branch         1000 non-null   object 
     2   City           1000 non-null   object 
     3   Customer type  1000 non-null   object 
     4   Gender         1000 non-null   object 
     5   Product line   1000 non-null   object 
     6   Unit price     1000 non-null   float64
     7   Quantity       1000 non-null   int64  
     8   Date           1000 non-null   object 
     9   Time           1000 non-null   object 
     10  Payment        1000 non-null   object 
    dtypes: float64(1), int64(1), object(9)
    memory usage: 86.1+ KB
    

## Group by
- (동의어) 집계함수를 배운다.


```python
sales['Invoice ID'].value_counts()
# 송장번호로 그룹화 하기는 어렵겠다...
# 적절한 기준을 찾을 때까지 노가다 해야한다.
```




    750-67-8428    1
    642-61-4706    1
    816-72-8853    1
    491-38-3499    1
    322-02-2271    1
                  ..
    633-09-3463    1
    374-17-3652    1
    378-07-7001    1
    433-75-6987    1
    849-09-3807    1
    Name: Invoice ID, Length: 1000, dtype: int64




```python
sales.groupby('Product line')['Quantity'].sum()
# 어떤 칼럼으로 그룹을 지을지 고민해야한다.
```




    Product line
    Electronic accessories    971
    Fashion accessories       902
    Food and beverages        952
    Health and beauty         854
    Home and lifestyle        911
    Sports and travel         920
    Name: Quantity, dtype: int64




```python
sales.groupby(['Product line', 'Branch', 'Payment'])['Quantity'].sum()
```




    Product line            Branch  Payment    
    Electronic accessories  A       Cash            85
                                    Credit card    121
                                    Ewallet        116
                            B       Cash           134
                                    Credit card     83
                                    Ewallet         99
                            C       Cash           179
                                    Credit card     58
                                    Ewallet         96
    Fashion accessories     A       Cash            60
                                    Credit card     85
                                    Ewallet        118
                            B       Cash           110
                                    Credit card    100
                                    Ewallet         87
                            C       Cash           110
                                    Credit card    108
                                    Ewallet        124
    Food and beverages      A       Cash            78
                                    Credit card    114
                                    Ewallet        121
                            B       Cash            41
                                    Credit card    138
                                    Ewallet         91
                            C       Cash           176
                                    Credit card     83
                                    Ewallet        110
    Health and beauty       A       Cash            98
                                    Credit card     73
                                    Ewallet         86
                            B       Cash           113
                                    Credit card     97
                                    Ewallet        110
                            C       Cash            82
                                    Credit card    104
                                    Ewallet         91
    Home and lifestyle      A       Cash           139
                                    Credit card     85
                                    Ewallet        147
                            B       Cash            94
                                    Credit card     93
                                    Ewallet        108
                            C       Cash            73
                                    Credit card     81
                                    Ewallet         91
    Sports and travel       A       Cash           112
                                    Credit card    102
                                    Ewallet        119
                            B       Cash           136
                                    Credit card     88
                                    Ewallet         98
                            C       Cash            76
                                    Credit card    109
                                    Ewallet         80
    Name: Quantity, dtype: int64



- 여기서 시리즈타입과 데이터프레임타입 구분이 중요하다.
- 위의 표는 무슨 타입일까?


```python
print(type(sales.groupby(['Product line', 'Branch', 'Payment'])['Quantity'].sum()))
```

    <class 'pandas.core.series.Series'>
    

- 이게 시리즈 타입이라고?? 시리즈는 인덱스 하나 + 칼럼 하나로 구성된 것이 아니었나...
- Product line, Branch, Payment 세 개가 함께 인덱스란 소리다.
- "Multi index"
- 가장 오른쪽에 나오는 숫자열이 한 개의 칼럼에 해당

### 시리즈 타입을 데이터프레임 타입으로 바꾸고 싶어
- 구글링 필요.
- as_index = False


```python
sales.groupby(['Product line', 'Branch', 'Payment'], as_index=False)['Quantity'].sum()
```





  <div id="df-8d1795bd-e055-460d-8f14-0c4e1c3f00d5">
    <div class="colab-df-container">
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
      <th>Product line</th>
      <th>Branch</th>
      <th>Payment</th>
      <th>Quantity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Electronic accessories</td>
      <td>A</td>
      <td>Cash</td>
      <td>85</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Electronic accessories</td>
      <td>A</td>
      <td>Credit card</td>
      <td>121</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Electronic accessories</td>
      <td>A</td>
      <td>Ewallet</td>
      <td>116</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Electronic accessories</td>
      <td>B</td>
      <td>Cash</td>
      <td>134</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Electronic accessories</td>
      <td>B</td>
      <td>Credit card</td>
      <td>83</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Electronic accessories</td>
      <td>B</td>
      <td>Ewallet</td>
      <td>99</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Electronic accessories</td>
      <td>C</td>
      <td>Cash</td>
      <td>179</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Electronic accessories</td>
      <td>C</td>
      <td>Credit card</td>
      <td>58</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Electronic accessories</td>
      <td>C</td>
      <td>Ewallet</td>
      <td>96</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Fashion accessories</td>
      <td>A</td>
      <td>Cash</td>
      <td>60</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Fashion accessories</td>
      <td>A</td>
      <td>Credit card</td>
      <td>85</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Fashion accessories</td>
      <td>A</td>
      <td>Ewallet</td>
      <td>118</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Fashion accessories</td>
      <td>B</td>
      <td>Cash</td>
      <td>110</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Fashion accessories</td>
      <td>B</td>
      <td>Credit card</td>
      <td>100</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Fashion accessories</td>
      <td>B</td>
      <td>Ewallet</td>
      <td>87</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Fashion accessories</td>
      <td>C</td>
      <td>Cash</td>
      <td>110</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Fashion accessories</td>
      <td>C</td>
      <td>Credit card</td>
      <td>108</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Fashion accessories</td>
      <td>C</td>
      <td>Ewallet</td>
      <td>124</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Food and beverages</td>
      <td>A</td>
      <td>Cash</td>
      <td>78</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Food and beverages</td>
      <td>A</td>
      <td>Credit card</td>
      <td>114</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Food and beverages</td>
      <td>A</td>
      <td>Ewallet</td>
      <td>121</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Food and beverages</td>
      <td>B</td>
      <td>Cash</td>
      <td>41</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Food and beverages</td>
      <td>B</td>
      <td>Credit card</td>
      <td>138</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Food and beverages</td>
      <td>B</td>
      <td>Ewallet</td>
      <td>91</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Food and beverages</td>
      <td>C</td>
      <td>Cash</td>
      <td>176</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Food and beverages</td>
      <td>C</td>
      <td>Credit card</td>
      <td>83</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Food and beverages</td>
      <td>C</td>
      <td>Ewallet</td>
      <td>110</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Health and beauty</td>
      <td>A</td>
      <td>Cash</td>
      <td>98</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Health and beauty</td>
      <td>A</td>
      <td>Credit card</td>
      <td>73</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Health and beauty</td>
      <td>A</td>
      <td>Ewallet</td>
      <td>86</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Health and beauty</td>
      <td>B</td>
      <td>Cash</td>
      <td>113</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Health and beauty</td>
      <td>B</td>
      <td>Credit card</td>
      <td>97</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Health and beauty</td>
      <td>B</td>
      <td>Ewallet</td>
      <td>110</td>
    </tr>
    <tr>
      <th>33</th>
      <td>Health and beauty</td>
      <td>C</td>
      <td>Cash</td>
      <td>82</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Health and beauty</td>
      <td>C</td>
      <td>Credit card</td>
      <td>104</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Health and beauty</td>
      <td>C</td>
      <td>Ewallet</td>
      <td>91</td>
    </tr>
    <tr>
      <th>36</th>
      <td>Home and lifestyle</td>
      <td>A</td>
      <td>Cash</td>
      <td>139</td>
    </tr>
    <tr>
      <th>37</th>
      <td>Home and lifestyle</td>
      <td>A</td>
      <td>Credit card</td>
      <td>85</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Home and lifestyle</td>
      <td>A</td>
      <td>Ewallet</td>
      <td>147</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Home and lifestyle</td>
      <td>B</td>
      <td>Cash</td>
      <td>94</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Home and lifestyle</td>
      <td>B</td>
      <td>Credit card</td>
      <td>93</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Home and lifestyle</td>
      <td>B</td>
      <td>Ewallet</td>
      <td>108</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Home and lifestyle</td>
      <td>C</td>
      <td>Cash</td>
      <td>73</td>
    </tr>
    <tr>
      <th>43</th>
      <td>Home and lifestyle</td>
      <td>C</td>
      <td>Credit card</td>
      <td>81</td>
    </tr>
    <tr>
      <th>44</th>
      <td>Home and lifestyle</td>
      <td>C</td>
      <td>Ewallet</td>
      <td>91</td>
    </tr>
    <tr>
      <th>45</th>
      <td>Sports and travel</td>
      <td>A</td>
      <td>Cash</td>
      <td>112</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Sports and travel</td>
      <td>A</td>
      <td>Credit card</td>
      <td>102</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Sports and travel</td>
      <td>A</td>
      <td>Ewallet</td>
      <td>119</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Sports and travel</td>
      <td>B</td>
      <td>Cash</td>
      <td>136</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Sports and travel</td>
      <td>B</td>
      <td>Credit card</td>
      <td>88</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Sports and travel</td>
      <td>B</td>
      <td>Ewallet</td>
      <td>98</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Sports and travel</td>
      <td>C</td>
      <td>Cash</td>
      <td>76</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Sports and travel</td>
      <td>C</td>
      <td>Credit card</td>
      <td>109</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Sports and travel</td>
      <td>C</td>
      <td>Ewallet</td>
      <td>80</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-8d1795bd-e055-460d-8f14-0c4e1c3f00d5')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-8d1795bd-e055-460d-8f14-0c4e1c3f00d5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-8d1795bd-e055-460d-8f14-0c4e1c3f00d5');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
print(type(sales.groupby(['Product line', 'Branch', 'Payment'], as_index=False)['Quantity'].sum()))
```

    <class 'pandas.core.frame.DataFrame'>
    

# 결측치 다루기

## 결측치 데이터 생성
- 임의로 만들기
- 대부분 딕셔너리 형태


```python
import pandas as pd
import numpy as np

dict_01 = {
    'Score_A' : [80,90,np.nan,80],
    'Score_B' : [30,45,np.nan, np.nan],
    'Score_C' : [np.nan, 50,80,90]    
}
df = pd.DataFrame(dict_01)
df
```





  <div id="df-cf88f083-c896-4734-b449-7286820b6a16">
    <div class="colab-df-container">
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
      <th>Score_A</th>
      <th>Score_B</th>
      <th>Score_C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80.0</td>
      <td>30.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90.0</td>
      <td>45.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>80.0</td>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-cf88f083-c896-4734-b449-7286820b6a16')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-cf88f083-c896-4734-b449-7286820b6a16 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-cf88f083-c896-4734-b449-7286820b6a16');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df.isnull().sum() # 각 컬럼의 결측치 개수
```




    Score_A    1
    Score_B    2
    Score_C    1
    dtype: int64



- True = 숫자 1로 인식
- False = 숫자 0으로 인식


```python
type(df.isnull().sum()) # 중간중간 타입을 확인하는 이유는 시리즈와 데이터프레임 메서드가 다르니까 그런것이다.
# 표 보다는 그래프로 보여주면 더 인식하기 쉽다. 
```




    pandas.core.series.Series




```python
df.fillna("입력값") # "입력값"으로 채우기
# df.fillna("0") -> 0으로 채우기
```





  <div id="df-a445638e-d7a2-4313-8ad8-ec710da9a067">
    <div class="colab-df-container">
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
      <th>Score_A</th>
      <th>Score_B</th>
      <th>Score_C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80.0</td>
      <td>30.0</td>
      <td>입력값</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90.0</td>
      <td>45.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>입력값</td>
      <td>입력값</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>80.0</td>
      <td>입력값</td>
      <td>90.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-a445638e-d7a2-4313-8ad8-ec710da9a067')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-a445638e-d7a2-4313-8ad8-ec710da9a067 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-a445638e-d7a2-4313-8ad8-ec710da9a067');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df.fillna(method="pad") # 결측치 바로 위에 있는 값으로 채우기
```





  <div id="df-8721f51c-2ef4-419b-8511-8e0a18fd252a">
    <div class="colab-df-container">
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
      <th>Score_A</th>
      <th>Score_B</th>
      <th>Score_C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80.0</td>
      <td>30.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90.0</td>
      <td>45.0</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>90.0</td>
      <td>45.0</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>80.0</td>
      <td>45.0</td>
      <td>90.0</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-8721f51c-2ef4-419b-8511-8e0a18fd252a')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-8721f51c-2ef4-419b-8511-8e0a18fd252a button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-8721f51c-2ef4-419b-8511-8e0a18fd252a');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
dict_01 = {
    "성별" : ["남자", "여자", np.nan, "남자"],
    "Salary" : [30, 45, 90, 70]
}
df = pd.DataFrame(dict_01)
df
```





  <div id="df-c9256c94-14de-4167-a50f-4ab030334a2d">
    <div class="colab-df-container">
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
      <th>성별</th>
      <th>Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>남자</td>
      <td>30</td>
    </tr>
    <tr>
      <th>1</th>
      <td>여자</td>
      <td>45</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>90</td>
    </tr>
    <tr>
      <th>3</th>
      <td>남자</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-c9256c94-14de-4167-a50f-4ab030334a2d')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-c9256c94-14de-4167-a50f-4ab030334a2d button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-c9256c94-14de-4167-a50f-4ab030334a2d');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df['성별'].fillna("성별 없음") # 성별 칼럼에서만 결측치 원하는 값으로 채우기
```




    0       남자
    1       여자
    2    성별 없음
    3       남자
    Name: 성별, dtype: object



- 결측치
--> 문자열 타입 / 숫자 타입 접근 방법이 다르다.
--> 문자열 (빈도 --> 가장 많이 나타나는 문자열 넣어주기!, 최빈값)
--> 숫자열 (평균, 최대, 최소, 중간, 이상치로 처리, 기타 등등..)

### Score_D 결측치 없는 칼럼 추가


```python
import pandas as pd
import numpy as np

dict_01 = {
    'Score_A' : [80,90,np.nan,80],
    'Score_B' : [30,45,np.nan, 60],
    'Score_C' : [np.nan, 50,80,90],
    'Score_D' : [50, 30, 80, 60]   
}
df = pd.DataFrame(dict_01)
df
```





  <div id="df-e3909644-07fd-4398-9f80-787495b12866">
    <div class="colab-df-container">
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
      <th>Score_A</th>
      <th>Score_B</th>
      <th>Score_C</th>
      <th>Score_D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80.0</td>
      <td>30.0</td>
      <td>NaN</td>
      <td>50</td>
    </tr>
    <tr>
      <th>1</th>
      <td>90.0</td>
      <td>45.0</td>
      <td>50.0</td>
      <td>30</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>80.0</td>
      <td>80</td>
    </tr>
    <tr>
      <th>3</th>
      <td>80.0</td>
      <td>60.0</td>
      <td>90.0</td>
      <td>60</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-e3909644-07fd-4398-9f80-787495b12866')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-e3909644-07fd-4398-9f80-787495b12866 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-e3909644-07fd-4398-9f80-787495b12866');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




- 인덱스1, 3(1행, 3행), D열은 결측치가 없다.


```python
df.dropna(axis = 1) # axis = 1 은 컬럼기준 # axis = 0 은 인덱스 기준
# 결측치가 있는 컬럼은 없애주겠다.
```





  <div id="df-4e41ca0e-e4ca-40cc-a91c-14b180a756bf">
    <div class="colab-df-container">
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
      <th>Score_D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>50</td>
    </tr>
    <tr>
      <th>1</th>
      <td>30</td>
    </tr>
    <tr>
      <th>2</th>
      <td>80</td>
    </tr>
    <tr>
      <th>3</th>
      <td>60</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-4e41ca0e-e4ca-40cc-a91c-14b180a756bf')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-4e41ca0e-e4ca-40cc-a91c-14b180a756bf button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-4e41ca0e-e4ca-40cc-a91c-14b180a756bf');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
df.dropna(axis = 0) # 결측치가 있는 인덱스(행)은 없애주겠다.
```





  <div id="df-7d8b6c36-b63e-46c9-a499-6fd349891ef2">
    <div class="colab-df-container">
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
      <th>Score_A</th>
      <th>Score_B</th>
      <th>Score_C</th>
      <th>Score_D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>90.0</td>
      <td>45.0</td>
      <td>50.0</td>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>80.0</td>
      <td>60.0</td>
      <td>90.0</td>
      <td>60</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-7d8b6c36-b63e-46c9-a499-6fd349891ef2')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-7d8b6c36-b63e-46c9-a499-6fd349891ef2 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-7d8b6c36-b63e-46c9-a499-6fd349891ef2');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




# 이상치


```python
sales

```





  <div id="df-eadd2087-3f9d-4047-a8f0-8d2fa7572222">
    <div class="colab-df-container">
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
      <th>Invoice ID</th>
      <th>Branch</th>
      <th>City</th>
      <th>Customer type</th>
      <th>Gender</th>
      <th>Product line</th>
      <th>Unit price</th>
      <th>Quantity</th>
      <th>Date</th>
      <th>Time</th>
      <th>Payment</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>750-67-8428</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Female</td>
      <td>Health and beauty</td>
      <td>74.69</td>
      <td>7</td>
      <td>1/5/2019</td>
      <td>13:08</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>1</th>
      <td>226-31-3081</td>
      <td>C</td>
      <td>Naypyitaw</td>
      <td>Normal</td>
      <td>Female</td>
      <td>Electronic accessories</td>
      <td>15.28</td>
      <td>5</td>
      <td>3/8/2019</td>
      <td>10:29</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>2</th>
      <td>631-41-3108</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Home and lifestyle</td>
      <td>46.33</td>
      <td>7</td>
      <td>3/3/2019</td>
      <td>13:23</td>
      <td>Credit card</td>
    </tr>
    <tr>
      <th>3</th>
      <td>123-19-1176</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Male</td>
      <td>Health and beauty</td>
      <td>58.22</td>
      <td>8</td>
      <td>1/27/2019</td>
      <td>20:33</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>4</th>
      <td>373-73-7910</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Sports and travel</td>
      <td>86.31</td>
      <td>7</td>
      <td>2/8/2019</td>
      <td>10:37</td>
      <td>Ewallet</td>
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
      <th>995</th>
      <td>233-67-5758</td>
      <td>C</td>
      <td>Naypyitaw</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Health and beauty</td>
      <td>40.35</td>
      <td>1</td>
      <td>1/29/2019</td>
      <td>13:46</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>996</th>
      <td>303-96-2227</td>
      <td>B</td>
      <td>Mandalay</td>
      <td>Normal</td>
      <td>Female</td>
      <td>Home and lifestyle</td>
      <td>97.38</td>
      <td>10</td>
      <td>3/2/2019</td>
      <td>17:16</td>
      <td>Ewallet</td>
    </tr>
    <tr>
      <th>997</th>
      <td>727-02-1313</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Male</td>
      <td>Food and beverages</td>
      <td>31.84</td>
      <td>1</td>
      <td>2/9/2019</td>
      <td>13:22</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>998</th>
      <td>347-56-2442</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Normal</td>
      <td>Male</td>
      <td>Home and lifestyle</td>
      <td>65.82</td>
      <td>1</td>
      <td>2/22/2019</td>
      <td>15:33</td>
      <td>Cash</td>
    </tr>
    <tr>
      <th>999</th>
      <td>849-09-3807</td>
      <td>A</td>
      <td>Yangon</td>
      <td>Member</td>
      <td>Female</td>
      <td>Fashion accessories</td>
      <td>88.34</td>
      <td>7</td>
      <td>2/18/2019</td>
      <td>13:28</td>
      <td>Cash</td>
    </tr>
  </tbody>
</table>
<p>1000 rows × 11 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-eadd2087-3f9d-4047-a8f0-8d2fa7572222')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-eadd2087-3f9d-4047-a8f0-8d2fa7572222 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-eadd2087-3f9d-4047-a8f0-8d2fa7572222');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>




- 일반적인 통계 공식은
- IQR(Interquartile Range) - 박스플롯 - 사분위수
- Q0(0), Q1(25%), Q2(50%), Q3(75%), Q4(100%)
- IQR = Q3 - Q1
- 이상치의 하한 경계값 : Q1 - (1.5 * (Q3-Q1)) 
- 이상치의 상한 경계값 : Q3 + (1.5 * (Q3-Q1))

- 도메인(각 비즈니스 영역, 미래 일자리)에서 바라보는 이상치 기준(관습)
- 더 중요한 것은 관습이다.



```python
sales[['Unit price']].describe()
```





  <div id="df-c275e09e-666c-4e82-b6f2-72bbe50e96e4">
    <div class="colab-df-container">
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
      <th>Unit price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1000.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>55.672130</td>
    </tr>
    <tr>
      <th>std</th>
      <td>26.494628</td>
    </tr>
    <tr>
      <th>min</th>
      <td>10.080000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>32.875000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>55.230000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>77.935000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>99.960000</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-c275e09e-666c-4e82-b6f2-72bbe50e96e4')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-c275e09e-666c-4e82-b6f2-72bbe50e96e4 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-c275e09e-666c-4e82-b6f2-72bbe50e96e4');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
Q1 = sales['Unit price'].quantile(0.25)
Q3 = sales['Unit price'].quantile(0.75)
outliers_Q1 = Q1 - 1.5 * (Q3-Q1)
outliers_Q1 # -34.~~ 값은 쓰기 어렵다. 이럴 경우에는 임의로 정해준다.
# 이상치의 하한값을 그냥 Q1으로 잡는다.
real_outliers_Q1 = (sales['Unit price'] < Q1)

# 이상치의 상한값을 마찬가지로 Q3로 잡는다.
real_outliers_Q3 = (sales['Unit price'] > Q3)
```


```python
print(sales['Unit price'][~(real_outliers_Q1|real_outliers_Q3)])
```

    0      74.69
    2      46.33
    3      58.22
    6      68.84
    7      73.56
           ...  
    991    76.60
    992    58.03
    994    60.95
    995    40.35
    998    65.82
    Name: Unit price, Length: 500, dtype: float64
    
