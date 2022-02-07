---
layout: single
title:  "12) Multiple Bar graph"
categories: Matplotlib
date: 2022-02-07 18:24:29
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


# 12. 다중 막대 그래프



```python
import pandas as pd
```


```python
import matplotlib.pyplot as plt
import matplotlib
matplotlib.rcParams['font.family'] = 'Malgun Gothic' # 글자 폰트
matplotlib.rcParams['font.size'] = 15 # 글자 크기
matplotlib.rcParams['axes.unicode_minus'] = False # 한글 폰트 사용 시, 마이너스 글자가 깨지는 현상을 해결
```


```python
df = pd.read_excel('../Pandas/score.xlsx') 
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
      <th>지원번호</th>
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
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1번</td>
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
      <th>1</th>
      <td>2번</td>
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
      <th>2</th>
      <td>3번</td>
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
      <th>3</th>
      <td>4번</td>
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
      <th>4</th>
      <td>5번</td>
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
      <th>5</th>
      <td>6번</td>
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
      <th>6</th>
      <td>7번</td>
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
      <th>7</th>
      <td>8번</td>
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
import numpy as np
```


```python
np.arange(5)
```

<pre>
array([0, 1, 2, 3, 4])
</pre>

```python
np.arange(3, 6)
```

<pre>
array([3, 4, 5])
</pre>

```python
arr = np.arange(5)
arr
```

<pre>
array([0, 1, 2, 3, 4])
</pre>

```python
arr + 100
```

<pre>
array([100, 101, 102, 103, 104])
</pre>

```python
arr * 3
```

<pre>
array([ 0,  3,  6,  9, 12])
</pre>

```python
df.shape
```

<pre>
(8, 10)
</pre>

```python
df.shape[0]
```

<pre>
8
</pre>

```python
N = df.shape[0]
N
```

<pre>
8
</pre>

```python
index = np.arange(N)
index
```

<pre>
array([0, 1, 2, 3, 4, 5, 6, 7])
</pre>

```python
w = 0.25
plt.bar(index - w, df['국어'])
plt.bar(index, df['영어'])
plt.bar(index + w, df['수학'])
```

<pre>
<BarContainer object of 8 artists>
</pre>
<img src="data:image/png;base64,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"/>


```python
w = 0.25
plt.bar(index - w, df['국어'], width = w)
plt.bar(index, df['영어'], width = w)
plt.bar(index + w, df['수학'], width = w)
```

<pre>
<BarContainer object of 8 artists>
</pre>
<img src="data:image/png;base64,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"/>


```python
w = 0.25
plt.bar(index - w, df['국어'], width=w, label='국어')
plt.bar(index, df['영어'], width=w, label='영어')
plt.bar(index + w, df['수학'], width=w, label='수학')
plt.legend(ncol=3)
```

<pre>
<matplotlib.legend.Legend at 0x1e4dbb60700>
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.figure(figsize=(10,5))
plt.title('학생별 성적')

w = 0.25
plt.bar(index - w, df['국어'], width=w, label='국어')
plt.bar(index, df['영어'], width=w, label='영어')
plt.bar(index + w, df['수학'], width=w, label='수학')
plt.legend(ncol=3)
plt.xticks(index, df['이름'], rotation=60)
plt.ylim(0,120)
plt.show()
```

<img src="data:image/png;base64,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4oknctVVV7H11lvz9ttvc9xxxzFo0CC6dOlCu3btmDNnDltsscUi+9bS/2XDqzcs5XMnHDQhl/d55JFHgDiH9thjjya3O//88xd6PXDgwIWWHXfccay11lq5pOnzqIRLRKQVmj17Nt26dVtk+aeffsoZZ5zBxRdfzKBBg+jYsSPHHnssgwcP5pJLLikhpfXllFNO4fzzz2eHHXagY8eODBgwgOuvv57evXtz5513Mm3aNK666qpF9tP/peW88cYbHHLIIey///4cc8wxvPTSS01ue8cdd3DHHXcwcuRIhg4dysYbb8w3vvENrrvuOu644w523HHHFku3Ai4RkVZo6tSpjQZcTz31FD169FikhGWfffbh4Ycfbqnk1a3XXnuNjTfeeKFlDQ0NrLPOOvz3v/9tcj/9X4o3ffp0xowZw9ChQxk5ciTXXXcdZ5xxBttvvz0//elP+eCDDxbZx93Zd999+dGPfkTHjh3p168fjz32GGuvvTbPPvvs/O3mzp3LmDFjGDNmDNOnTy8k/apSFBFpYR06LNmld+7cufO3ff311+ePA7T66qsvsm2/fv2466672G677QB46aWXGDFiRG5pbivWXHNNnn76aQYMGDB/2cyZM3nxxRd5+umn+fDDD3n88ccX2U//l+K88MILHHHEEUyYMIG9996bcePGzf//fPOb32Tbbbfl7LPPZvDgwayyyipccMEFbLPNNgD8+9//5m9/+xtvvvkmnTt3nv+e/fr146yzzuLKK68EIjD79NNP5z8vggIuEZEWNmfOnEWWTZw4kcGDB8+/6Ddl+eWXZ9q0aYssnzZtGoMGDeKUU04B4Mwzz8wnsW3M6NGjOeqoo+jcuTNbb701kyZNYtSoUQwaNIh33nmHd955h1dffXWR/fR/Kc7gwYMZPXo0m2++eaNt4VZZZRVOP/10xowZwzPPPMOGGy5on9ajRw9mzpzJ+++/v1BPxDfeeINevRa0L+zQoUPhvUcVcImI1JC11lqL1157jenTpy9U5Th+/Hg233zz+d3ef//735eVxJq233770bt3b0499VQOOuggevXqxb777stJJ51Ep06dgBhe4KKLLlpoP/1firX99tt/7jbt2rVjk002WWjZgAED+OUvf8mmm27K1ltvTffu3Xnqqafo1asXt956azGJbYICLhGRGtK3b1+GDh3KxRdfzMiR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jKrtpwOdG3sjMxsBjADo37/2506S2jHwhDub/R4Tx+yaQ0pEWofmnhMTG3JKiEgdaHaVopmtAPwQONDdn3P3D939NOAl4JC0Waeq3RpYNAgDwN0vcfch7j6kd+/ezU2eiIiISOnyaMM1CMDdX6paPh4YDMwCqnsk9mfRakYRERGRupRHwPUa0MnMBlUt35gIqh4GdqpaNwy4L4fPFhEREWn1mt2Gy93fN7NrgavM7DvAe8ARwJZEW6xHgavNbFx6fhCwAbBPcz9bREREpBbk1Wj+cOBk4G5icNMnge3cfSIw0cxOJAY/7UOUeA13909y+mwRERGRVi2XgMvdZwLHp0dj68cCY/P4LBEREZFao8mrRURERAqmgEtERESkYAq4RERERAqmgEtERESkYHn1UhQRgJN7NXP/j/NJh4iItCoq4RIREREpmAIuERERkYIp4BIREREpmAIuERERkYIp4BIREREpmAIuERERkYIp4BIREREpmAIuERERkYIp4BIREREpmAIuERERkYJpah+RVmTDqzds1v4TDpqQU0rK09w8gPrIBxGpLyrhEhERESmYAi4RERGRgingEhERESmYAi4RERGRgingEhERESmYAi4RERGRgingEhERESmYAi4RERGRgingEhERESmYAi4RERGRgingEhERESmY5lIUEREpysm9cniPj5v/HlI6lXCJiIiIFEwBl4iIiEjBFHCJiIiIFEwBl4iIiEjBFHCJiIiIFCy3gMvMepjZuWb2jpnNMrPnzaxjWrebmU0ws0/N7Bkz2yGvzxURERFp7XIJuMysPfBnYEVgS6AXcDAwz8w2Ba4FRgHLAxcCt5vZ6nl8toiIiEhrl1cJ18FAN+Db7j7R3T9190fdfS7wY+Aid7/L3We6+4XAI8ChOX22iIiISKuWV8B1CHCuu89rZN0w4C9Vy+4Fhub02SIiIiKtWrMDLjPrAAwBZprZw2Y2I7XT2t3MlgNWAF6t2u11oF9zP1tERESkFuQxtc+KQGfgB8BI4FlgL+AmYKe0zYyqfaanfRZhZiOAEQD9+/fPIXki0qKaO5XJGjrvRaT+5FGlWKlGPMvdH3b3T9z9KuBOom0XQKeqfRpYNAgDwN0vcfch7j6kd+/eOSRPREREpFx5BFxTgFlENWHWS0RgNQuo7pHYn0WrGUVERETqUrMDLnd34FEWbQS/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"/>
