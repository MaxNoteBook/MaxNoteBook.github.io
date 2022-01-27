---
layout: single
title:  "12) Data Correction"
categories: Pandas
tag: [python, blog, jekyll]
toc: true
author_profile: false
---

<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {
      vertical-align: middle;
  }

  .dataframe tbody tr th {
      vertical-align: top;
  }

  .dataframe thead th {
      text-align: center !important;
      padding: 8px;
  }

  .page__content p {
      margin: 0 0 0px !important;
  }

  .page__content p > strong {
    font-size: 0.8rem !important;
  }

  </style>
</head>


# 12. 데이터 수정



```python
import pandas as pd
df = pd.read_excel('score.xlsx', index_col='지원번호')
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


### Column 수정



```python
df['학교'].replace({'북산고':'상북고', '능남고':'무슨고'})
```

<pre>
지원번호
1번    상북고
2번    상북고
3번    상북고
4번    상북고
5번    상북고
6번    무슨고
7번    무슨고
8번    무슨고
Name: 학교, dtype: object
</pre>

```python
df # inplace가 필요하다.
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['학교'].replace({'북산고':'상북고'}, inplace = True)
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['SW특기'].str.lower()
```

<pre>
지원번호
1번        python
2번          java
3번    javascript
4번           NaN
5번           NaN
6번             c
7번        python
8번            c#
Name: SW특기, dtype: object
</pre>

```python
df['SW특기'] = df['SW특기'].str.lower() # 'SW특기' 소문자로 변경
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>python</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>java</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>javascript</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>c</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>python</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>c#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['SW특기'] = df['SW특기'].str.upper() # 'SW특기' 대문자로 변경
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['학교'] = df['학교'] + '등학교' # 학교 데이터 + 등학교
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


### Column 추가



```python
df['총합'] = df['국어'] + df['영어'] + df['수학'] + df['과학'] + df['사회']
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>325</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['결과'] = 'Fail' # 결과 Column을 추가하고, 전체 데이터는 Fail로 초기화
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Fail</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.loc[df['총합'] > 400, '결과'] = 'Pass' # 총합이 400보다 큰 데이터에 대해서 결과를 Pass 로 업데이트
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### Column 삭제



```python
df.drop(columns=['총합']) # 총합 Column을 삭제
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.drop(columns=['국어', '영어', '수학']) # 국어, 영어, 수학 Column 을 삭제
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### Row 삭제



```python
df.drop(index='4번') # 4번 학생 데이터 row를 삭제
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>



```python
filt = df['수학'] < 80 # 수학 점수가 80점 미만 학생 필터링
df[filt]
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
  </tbody>
</table>
</div>



```python
df[filt].index
```

<pre>
Index(['2번', '3번', '4번', '5번', '7번'], dtype='object', name='지원번호')
</pre>

```python
df.drop(index=df[filt].index)
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### Row 추가



```python
df.loc['9번'] = ['이정환', '해남고등학교', 184, 90, 90, 90, 90, 90, 'Kotlin', 450, 'Pass'] # 새로운 Row 추가
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>9번</th>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### Cell 수정



```python
df.loc['4번', 'SW특기'] = 'Python' # 4번 학생의 SW특기 데이터를 Python으로 변경
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>Python</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>9번</th>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.loc['5번', ['학교','SW특기']] = ['능남고등학교', 'C'] # 5번 학생의 학교는 능남고등학교로, SW특기는 C로 변경
df
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
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
      <th>결과</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>Python</td>
      <td>325</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>C</td>
      <td>90</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>9번</th>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


## Column 순서 변경



```python
cols = list(df.columns) # list형태로 바꿈
cols
```

<pre>
['이름', '학교', '키', '국어', '영어', '수학', '과학', '사회', 'SW특기', '총합', '결과']
</pre>

```python
df = df[[cols[-1]] + cols[0:-1]] # 결과를 맨 앞으로, cols[-1] : 값이므로 [] list로 감싸준다.
df
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
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>Fail</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>Python</td>
      <td>325</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>C</td>
      <td>90</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
    </tr>
    <tr>
      <th>9번</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>



```python
df
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
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>Fail</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>Python</td>
      <td>325</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>C</td>
      <td>90</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
    </tr>
    <tr>
      <th>9번</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>


### Column 이름 변경



```python
df.columns
```

<pre>
Index(['결과', '이름', '학교', '키', '국어', '영어', '수학', '과학', '사회', 'SW특기', '총합'], dtype='object')
</pre>

```python
df.columns = ['Result', 'Name', 'School', '키', '국어', '영어', '수학', '과학', '사회', 'SW특기', '총합']
df
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
      <th>Result</th>
      <th>Name</th>
      <th>School</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>총합</th>
    </tr>
    <tr>
      <th>지원번호</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>PYTHON</td>
      <td>455</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>JAVA</td>
      <td>205</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>Fail</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>JAVASCRIPT</td>
      <td>380</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>Python</td>
      <td>325</td>
    </tr>
    <tr>
      <th>5번</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>C</td>
      <td>90</td>
    </tr>
    <tr>
      <th>6번</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>440</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>240</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>465</td>
    </tr>
    <tr>
      <th>9번</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>

