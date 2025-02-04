---
layout: single
title:  "15) Scatter plot graph"
categories: Matplotlib
date: 2022-02-08 17:10:01
tag: [python, blog, jekyll]
toc: true
author_profile: false
published: true
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


# 15. 산점도 그래프



```python
import matplotlib.pyplot as plt
import matplotlib
matplotlib.rcParams['font.family'] = 'Malgun Gothic' # 글자 폰트
matplotlib.rcParams['font.size'] = 15 # 글자 크기
matplotlib.rcParams['axes.unicode_minus'] = False # 한글 폰트 사용 시, 마이너스 글자가 깨지는 현상을 해결
```


```python
import pandas as pd

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
df['학년'] = [3, 3, 2, 1, 1, 3, 2, 2]
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
      <th>학년</th>
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
      <td>3</td>
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
      <td>3</td>
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
      <td>2</td>
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
      <td>1</td>
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
      <td>1</td>
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
      <td>3</td>
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
      <td>2</td>
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
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



```python
plt.scatter(df['영어'],df['수학'])
plt.xlabel('영어 점수')
plt.ylabel('수학 점수')
```

<pre>
Text(0, 0.5, '수학 점수')
</pre>
<img src="data:image/png;base64,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"/>


```python
import numpy as np
sizes = np.random.rand(8) * 1000
sizes
```

<pre>
array([181.78216747, 745.72325818, 988.94992638, 148.24723426,
       684.31070804, 452.29223234, 133.83073613, 733.2575611 ])
</pre>

```python
plt.scatter(df['영어'],df['수학'], s=sizes)
plt.xlabel('영어 점수')
plt.ylabel('수학 점수')
```

<pre>
Text(0, 0.5, '수학 점수')
</pre>
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZAAAAESCAYAAADTx4MfAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjQuMywgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy/MnkTPAAAACXBIWXMAAAsTAAALEwEAmpwYAAAq7ElEQVR4nO3dd5xcdb3/8ddndnZ3NsmmbwoppCCEEPpSEorADdgQFUWBq1JUmnrFgtd78VrutVx/Kgh6qXIFEQHlehX0gho6GGJCIAmd9EZIb1unfH5/nFmYzLaZ2Wm7834+HvPI7vmeM+eTb7Lz2fOt5u6IiIhkK1TqAEREpH9SAhERkZwogYiISE6UQEREJCdKICIikpNwqQMoptGjR/uUKVNKHYaISL/y7LPPbnX3hvTjFZVApkyZwqJFi0odhohIv2Jma7o6riYsERHJSUU9gYiIJBLOk8u3cvPjK1i8dgdtsQSRcBWzp43ikndO47ipIzGzUofZLyiBiEjFWL+jmY//fAFb9rTR1B5/63hLNM6jr27mmVXb2H/UIH558XE01NeWMNL+QU1YIlIRNu1q5ayfPc267S37JI8ODjS3x3n9zb2c9bOn2NncXvwg+5mSJhAzm2Zmj5jZB9OOn2lmy8ys1cyWmtlpaeUHmtnDZtZsZuvM7AtFDVxE+p3P/noxu1qixHtZ/y+WcLbubeOq+5YWKbL+qyQJxMwmm9nNwBJgTlrZ0cCdwFXACOBG4H4zm5QsHwzMA/4KjAbOB75lZmcX728gIv3J8s17eWHDLuKJzBaPjcadx1/bwuY9rQWOrH8r1RPIsUA9QfLYlFb2VeAmd3/I3Vvc/UbgGeDiZPkngQ3u/p/u3uzuTwI/Bj5fpNhFpJ+542+rM04eHQz49YK1hQlogChJAnH3+9z9fHdf1kXxXODBtGPzePtJpbvy401DJ0SkC8+v20ksywTSFkvw/LqdhQlogCirUVhmNhwYCaxMK1oDTEx+PR343y7KIwRNWlvS3vMS4BKAyZMn5zdgEekX2mOJnK5ry/G6Ulu7rZnfP7eev63cxutv7qU9lqA6HGJ6w2BmTxvFB46cwPSGIX2+T1klEKDjb9ScdrwJqE05p6tyUs55i7vfAtwC0NjYqN2zRCpQQ30Nr76Z/XVj+tlQ3tVbm/ja75by3NqdJNyJxlM+8tpge1M7z63dyc1PrOSQ/Ybynx8+jAPH1ud8v3IbxhtN/lmTdjzC20kj2k05dE4sIiKc0ziJwTVVWV0zuKaKDx81sfcTy8Sd81fz7uue4O+rttMWS+ybPFLEEk5bLMFz63Zy1k+f4sbHlpPrzrTllkC2Am3ApLTjk3m7WWt9N+W73H17YcMTkf7o3bPGZT27fFBtmBMPGF2giPLrJ/Ne43v/9wqt0QSZdvW4Q2sswfUPL+ffH3gppyRSVgnE3ePAfOD0tKK5wMPJr5/qpVxEZB+14Sr++d0HUVed2VNIpDrEt94/k1Co/MflPLjsDW5+fCUt0c6TIzPREo1zz8J13LNwXdbXllUCSboWuMrM3mlmETO7FJgF3J4s/znBiKsrkuUnAl8C/l9pwhWR/uATs6fwqROn9JpEItUhrnrXDN532H5Fiix32/a28dX7luacPDq0ROP8xx9fYuPOlqyuK7sE4u73A1cTTCbcCZwLnOHue5LlG4AzCUZW7SLoIP+Muy8oScAi0m985V0zuP68Izl4fD2R6hC14RBVxltfHzFpOD//5DF86sSppQ41Izc+voLWWN+SR4e2WJxr/vpaVtdYrp0n/VFjY6NrPxARAXj5jd38fdV29rbFGBoJM+eA0XkZ2losbbE4R/3HPJraYnl7z0h1iIVXz6U+Ur3PcTN71t0b088vt2G8IiIFE084z6zcxuK1O1iwcjtrtzcTjSeoCYd4+OXNHDdtJEdNHsExU0aWff/Hc2t3ku8Iw6EQz6zczukzx2Z2fp7vLyJSdnY2t3PH39Zw+99WEY07rdF4p5npa7Y18/SKrdRUhRhUG+YzJ03l/OP2Z0hteX5MvrBhV84TJLvT3B5jybqdSiAiIgB/eXETX/ntEtpiiV5nlkfjTjQep6k96A+46fGV/PS8IzmhDIfzvvbmHtrj+U0gCYdXN+3O+Pyy60QXEcmHWDzBF+99ni/c8zy7W2NZL0vSGk2wvamdT92xkG/d/2LOk+0KJdbNRMG+imaxZpieQERkwIknnMt+9SxPL9/W5yGurdEE9y5cx962GD/8yGFls93tqCE1mAUTAvNp9JDMl2/RE4iIDDjffuBFnl6+tc/Jo0NLNM6flr7BTx9Znpf3y4fDJw1ncE1+nwHqqkMcvf+IjM9XAhGRAWXh6u38ZtE6WqL57R9oica54bHlvJJFH0EhHTV5BNE894GAKYGISGWKxhN87teLac1z8ujQFk3wubsWl0V/yH7D6zh0wrC8vuekkXVZrc6rBCIiA8a8l95kb2v+Jtalc2DjrlaeWVke67Z+Ye47Ml7fqzd11VVcOffArK5RAhGRAePGx1fQ1J6ffo/utLTHufWJ9D3vSuOkdzRw6owGasJ9+ygPh4Kmq/fMGpfVdUogIjIg7Gxu5+U3Ct8/4cATr2/J+yS+XH3/7MMYU19LOMeZ8yGDEYNquPZjR2Q9wkwJREQGhGUbdhEJ56c5pzeR6hCvvbmnKPfqzbC6an53xRwmjKgjUp3dR3ptOMSY+lr+97NzaMhh90UlEBEZEF7YsCtvw3Z7E08ECatcjKmP8OcrT+ZjjZOIVIeo6uWTvSpkRKpDvP/w/Zj35VOYOGJQTvfVREIRGRA27mzttL5VobTF4mzb21aUe2UqUl3Ftz8wi0/MnsJtT63i989tAIJk4e6YGQl3EgnnfYeN59MnTePg8UP7dE8lEBEZEOJFSh4QrBlVrGSVrQPGDOH7Zx/K9z40i7Xbm3ll0x5ao3Fqw1UcOHYIU0YNzttKw0ogIjIg1EfCGEEnd6FVV1neZ4Hnm5mx/6jB7D9qcMHuoT4QERkQZu43lEE1RepED1dx4LjMJ9wNVEogIjIgzJowrChPHwCtsXjeZ4H3R0ogIjIgTB01mHBVcVbKHVMfYeTgmqLcq5wpgYjIgBAKGZ88fgq1fZyV3Zu6mio+c9LUgt6jv1ACEZEB4xOz9y/4PdydDx89seD36Q+UQERkwBg7NMKnT5xKXZYzsjM1qKaKr75rBvWR6oK8f3+jBCIiA8oX5h7ImKER8r1xYFXImN4whAvnTMnvG/djSiAiMqDUhEP84sJjqK/N3zyNkMHwumpu+eTReZuENxAogYjIgDOtYQi/uWw2w+qqqerjB351lTFycA2/u2IO44fV5SnCgUEJREQGpBnjhvLQlSdx1OThOW+6VFddxQnTR/PQlScXdEZ3f1Xec/FFRPpg/LA6fnPpbO5duI4fPPQK7bFERhtODa6pYnBtmG+8fyZnHrZfESLtn5RARGRAMzPOPXYy5zRO4tFXNnPH/NUsXb+LlvY4tR2jtTyYXV4fqebIScO58IQpnDB9tPo7eqEEIiIVoSpkzJ05lrkzxwKwZU8b63c0E407NeEQ+48cxAjNLs+KEoiIVKSG+tqcduGTt6kTXUREcqIEIiIiOSnLBGJmETO7zszeNLM9ZvaYmTWmlJ9pZsvMrNXMlprZaaWMV0SkEpVlAgG+B5ycfI0HHgL+bGb1ZnY0cCdwFTACuBG438wmlSpYEZFKVK4J5GjgF+7+qrvvBX4ADAEOBL4K3OTuD7l7i7vfCDwDXFy6cEVEKk+5JpC7gIvMbIaZDQGuBpYBS4G5wINp588D5hQ3RBGRylauw3hvBd4FvJz8fjfBU8lgYCSwMu38NUCXC/Sb2SXAJQCTJ08uRKwiIhWpXJ9AvgtMAA4hSBg/IHjKGJosb047vwnockC3u9/i7o3u3tjQ0FCgcEVEKk/ZPYGY2Ujgy8Ch7v5a8vD3zOwU4KLk9+nTRSN0TioiIlJA5fgEcgBASvLosASYAbQB6SOuJtO5WUtERAqoHBPIKqDGzA5IO344QZKYD5yeVjYXeLgIsYmISFLZNWG5+xYzuxO43cw+BbwJXAbMJugMXwDcYWZPJ7++AJgFnFOikEWkB/GEs7ctRjSeoCYcYkhNWKvcDhBll0CSLgW+BfyZYLLgs8Ap7r4aWG1mVxNMJhxD8ERyhrvvKU2oIpKqPZZg3stv8vhrW3h29Q7WbG8CIGRGwp2QGQeMGcKxU0fyDzPGMmf6KCWUfsrcvdQxFE1jY6MvWrSo1GGIDEhb9rTx30+t4lcL1pBIeK8bNxkwKLlx02dOmsb5x01mcB73MZf8MbNn3b0x/bj+tUSkT9yd3y3ewL/94QViCac9lsjsOqCpPU5Te5xr/voaNz+xguvPO5I500cXNmDJGyUQEcnZ7tYol/9qMYvX7KAl2vtWsd1picZpica5+PaFfOCICXz3g7MIV5XjGB9JpQQiIjnZ0dTO2Tf+jQ07WmiPZ/bU0ZvWaIL7n9/Axp0t3HbBMdSElUTKmf51RCRrTW0xPnrzfNbvaM5b8ujQEk2wcNV2LvvVsyQSldNH2x8pgYhI1v7t9y+wdnuwn3ghtMYSzF+xjdueXlWQ95f8UAIRkaw8+foWHnxhE20ZdpbnqiUa58d/eZXVW5sKeh/JnRKIiGSsPZbgC/c836cO82zvd+W9zxflXpI9daKLlNCKLXtZsHI7ze0xRg2p4bSDxjJsUHWpw+rWQy9uoq1IyQMg4fDKpt28/MZuDh4/tPcLpKiUQERKYOHq7Xznjy/x6qY9YJBIOOGqEPHEMt59yDiuft/BjBkaKXWYndz02IpeJwjmWzTu3PbUKn50zuFFva/0Tk1YIkX2p6Ub+cRtC1iyfhetsQSt0QTtcae5PU5bLMEfl23kPdc9ybrt5bVDwZptTazcsrfo940nnAeWbCSa59Fe0ndKICJF9OqmPXzlt0tojXb/YRhPwI7mds679RniZTSM9fl1O6kq0ZpV4Srj9TeLn7ykZ0ogIkV0w6PLaY/1nhQSHiSRR17ZXISoMrN4zQ6ai9x81cEdlm3YWZJ7S/eUQESKZHdrlIde3EQ8wwVMm9ri3Pz4igJHlbnn1u2kVM9Dze1xlqzfVaK7S3eUQESKZM3WZmqyXN/ptTfLZ5eCva2xkt5/V3O0pPeXzpRARIokmkgEa5hnoZz6QBIl3vqhnOpCAkogIkWy37C6jJc67zBmaG2BoslepLqqpPcfVFva+0tnSiAiRTJuWIRZE4ZlfH5ddRUXzplawIiyc9C4+pLduzYc4pD9Mq87KY6cE4iZfSyfgYhUgitOmU5dTWa/SZvB2UdNKHBEmTtmykjqSvQUUlMV4tAskq8UR1YJxMw+a2Yjk9/+ogDxiAxop80Yw4eOmNDrB3GkOsR//eNR1EfKZ1mTwyYOo1Rbl7dE48zcT0uZlJtsn0C+DHT8K5bov5JI/2VmfPdDs7jk5GlEqkOdEsng2ipGDa7htguO4dSDxpQoyq7N2m9Yxk9P+Xb0/iMYov3Sy07G/yJmNgOIu/vq5CENiRDJgZnxxdMP5NMnTeV3i9fz8MubaW6P01Bfy0cbJ3HygQ0lm/Hdk1DI+PSJU/nJw6/3OJM+3wbXVHHZKdOLdj/JXDYp/evAdYUKRKTS1EequWDOVC4oo47y3nzsmMn8ZN7rRb3noNow73xHQ1HvKZnJqAnLzM4CjgZuKWw4IlLORgyu4crTDyxaZ3qkOsQPP3IYoTJ8IpNenkDM7FzgOOBc4Ax3b08prjKzc+jcF7Lc3RfnN0wRKRefOWka9z+/kVc27aaQc/tqwyHOmDmOU8qsL0je1lsT1hXALOBp4OUurr2czgnkD4ASiMgAVRUybvjHozjzp0+xt60wy5tUhYyRg2v4zodmFeT9JT96bMJy95OByUAUuD6tuM3dT3P3U9NePylQrCJSJqaMHsxdnz6OQQUYlVUVMkYMquZ/Lp/D0DIaxiyd9doH4u57gfOBU83suMKHJCL9weGThvObS2czvK6amnB+FrWoqw4xcUQdf/z8Sew3vC4v7ymFk9G/uru3At8GvlHYcESkP5k1YRiPX3Uqcw8e0+eO9Uh1iE/MnsJfvngy44aV33a+0lk2w3jvBa4zs5Huvr1QAYlI/zJsUDU3/OPRPPrKZr7/4Mus295CeyyR0b4n1VVGyIwjJg3n6vcdzGEThxc+YMmbjBOIu7uZPQ5MA7ajmegikuLUGWM4dcYYXtiwi188vYqnlm9l29526qqrcMDdMQs+NlqjccYPi3D6zLFcdMJUJo0cVNrgJSfZrg3wCXdvS379RL6DEZH+b9aEYfz4o0cAsKc1yksbd7OtqZ1oPEFtOMS4YXXMGFdf8uXhpe+ySiApyQN3f1f+wxGRgaQ+Us1x00aVOgwpkLLdD8TM6s3sejN7w8zazOxlM6tOlp1pZsvMrNXMlprZaaWOV0Sk0pRlAjGzKuD/gFHAbGAYcCGQMLOjgTuBq4ARwI3A/WY2qTTRiohUpm6bsMzsn4GemqnOBn6Xdszd/R/yENeFwGCCPpeOZT8XJOP6KnCTuz+UPH6jmX0YuJhgqLGIiBRBT30gjwKrCUZb3UUwmTBVC3BCynEDfpWnuC4Crk9JHqnmAh9KOzYPODVP9xYRkQx0m0Dc/e/A3wHM7C53vzf9HDOLu/v/pHz/y74GZGZhoBH4qZnNBw4HlhMsJ/8EMBJYmXbZGmBiN+93CXAJwOTJk/sanoiIJPXYB5LSr2Apx45NfsgXyiigFvgn4EvAWOAa4D6CZALQnHZNU/KaTtz9FndvdPfGhgbtKSAiki+9daKvSP75PwBmNhj4DXBYAWPqaLb6sbvPd/c97n478CeCvhGAmrRrInROKiIiUkC9JRADcPdzkk8dvwN+VuD9PrYCbQTNUqleI0gUbUD6iKvJdG7WEhGRAuotgbiZ1ZjZKQSd6g+4+48KGZC7O8GIqzlpRYcALwHzgdPTyuYCDxcyLhER2VdvfRlhgtFWAJe5+61p5WZmUwmeVDpe+XANcJuZvQQsBD5OkFAuBpYAd5jZ0wSJ5gKCTa/OydO9RUQkA70lkDjQQNDn8aXkfiCfSy7vDkFz0rO8nThaOr9F9tz9D2Y2GfgFQSf6s8C73X0zwaTBqwkmE44heCI5w9335OPeIiKSGfMellw2s3Z3r0n5/mqCyYXvTW401a80Njb6okWLSh1G2YnFE+xtixFLOINqqhhUU8hBdiLS35jZs+7emH68t0+KfZqk3P27ZjYBuBU4L4/xSRG5O/NXbuP3z21g0ZodrNvejJlhQDzh1EfCzNxvKKcdNIYPHz2R4YPSB72JiPT+BDLN3VemHRsKHOnujxc6uHyr9CeQRML5zaJ1XPfw6+xqidLSHqenLX8i1SHc4YyZY/mX9x6sLUZFKlROTyDpySN5bDfQ75JHpVu3vZnP3/0cr27aQ0s0ntE1rdFgSs7/LXuDea9s5htnzuTcYya9tSmQiFS2slyNV/JrwcptvOsnT7Bsw66Mk0equENLe5x/f+AlrrhrMdF4V0uUiUilUQIZ4Bau3s6Fv1hIc3uceKL3Pap70hKN8+irm7n8V8/2+b1EpP9TAhnANu9p5aJfLMzpqaM7rdEETy/fynXzXsvbe4pI/6QEMkC5O1+6dwmteUweHVqiCW55YiUvv7E77+8tIv2HEsgANe/lzSxeu4NYgZqa2mIJrrz3+YK8t4j0DxknEDOrM7NBhQxG8udnj7xOc3v+nz46OLB2WzNL1u0s2D1EpLxl8wTyT8BXChWI5M+KLXt5dVPhV3Zpi8X5+ZNaBFmkUqkJawB69JXNFGOgbcLhkVc209NkVBEZuLqdSGhm6wh2B0w918zsa8nvf+fuHzezPbDPhOa/ufu78x+qZGrByu20x4ozVyOWcN7Y1apZ6iIVqKeZ6LOBqh7Km5J/VgMHpRxv7eJcKaIXNu4q2r1qqkK8uHG3EohIBeo2gbj7ejMbD8xw90d7eI+Eu6fvHigltLc1VrR7xd3Z1RIt2v1EpHz01gdyGPBFADObaWa3mdk1Zja84JFJzordI6E+EJHKlFEnupnVA48Aq4F64PeFC0n6alBNTy2P+RUyoz6i/UNEKlGmo7DOAf7g7v/h7p8BhpvZwQWMS/rgoHH1RbtXPOHMGDe0aPcTkfLRbQIxsyeBHya/nQosTil+DpjWcWphQpNcHT9tFNVVxflncZz9R2l+qUgl6ukJ5GfAH5NfNwNDUsoGJ49B8ZvcpRfvPLCBcKg4U3yOnzpK+4OUiVg8wUsbd/Psmu2s2tqkvikpuJ5GYd1rZjuBWcAzwA/N7DpgLHAycGnyVH16lJlZE4ax3/AIK7Y09X5yHwyqqeKSd07r/UQpqF0tUX7+5Ep+OX8NsUSCkBmxuDNuWITLT5nOR46aSCikH1PJv4x+TU0O410ObABeAv7T3Xcki88oUGzSB5899YCCd6aPGFTD7Gmjej9RCmbTrlbee90T3PzESna1RGlqi7OnNUZLNM6qrU188w8v8qk7FmoTMCmITBKIAbj7ucBpwKHu/pOOQnd/sjChSV988IgJTB09mEL94hmpDnHNRw9X81UJxRPOebc+w6bdbd2uPNASjfPMym186/4XixydVIIeE4i7/9nd35/y/YvuvrbwYUlfhULGf51/FDXh/PeFRMIhzj5yIsfp6aOkHnt1M5t3t/a6O2RLNMF9z65nR1N7kSKTSpHzp0tylrqUsSmjB3PtR48gUp2/JFIbDnHQuHq+8f6ZeXtPyc0tT6ykKcMl+83g3kXrChyRVJqsPlnM7ER7u81iRQHikTx7z6Hj+eFHDqMuD0kkUh1i5vih3PWZ44lUF2+yonTt1TczX7K/NZpg6fqdhQtGKlK2nyr/BRya/FqN3/3E+w+fwN2XzGa/4ZGcn0Yi4RAXzpnCvZfOZkitZp6Xg2xH6SbUjy55ls2OhCOB8e6+NHlIg8z7kSMmDeeRL5/CRXOmMKimKqMRWuGQEQmHOGziMO67fA5fe8/BBelTkdxMyWICZ204xMHjtWKA5Fc2v0p+CfhFoQKRwotUV/HP7zmYL8w9kAeWbOQ3i9bzyhu7aY8nqK4KYUDCnbZYgokj6jjpHQ1cMGd/DhhTvKVRJHOfOXka//w/S2lq670fxIFzj51U+KCkomSUQMzsHcCFwFEFjUaKIlJdxTmNkzinMfhAeXN3K1v2tBFPOINqqpg8ahC1YfVxlLszZo7jO398ieb2eI/NWZFwiLkzxzJ2aKR4wUlF6DGBmNk44DjgOuBL7r5532JroHNfSLO7781vmFJIY4dG9OHSD9WEQ9x9yWzOvuFp9rTGiHUxnDdSHeLgcUP50TmHlyBCGeh6ewLZSPD0+2t3/01aWS2wiX0TiAM3A1fkLUIR6dbU0YN56MqTufavr/H75zdQHQrhBItc1oaruPiEKVxy8nT1XUlBWE8LrplZiGBr2/8GfuTut6aUNbt7v1qGtbGx0RctWlTqMEQKYm9bjOfW7qC5Pc6owTUcOXkEVVoDS/LAzJ5198b0473NRE+4+9PA6cC/mVnRe+HM7FAzi5vZhSnHzjSzZWbWamZLzey0YsclUm6G1IY56R0NvOuQcTROGankIQWX6WKKa4EbgH8tbDhd+h4pQ4bN7GjgTuAqYARwI3B/KZKbiEgly6Zh9HrgI2ZWW6hg0pnZRwj2IXk+5fBXgZvc/SF3b3H3GwmWm7+4WHGJiEgWCcTdm4EXgOMLF87bkiO8fsTb+450mAs8mHZsHjCnGHGJiEgg2zUpLnP3V5NfF6yBNbne1p3Ate7+WsfyW2Y2HBgJrEy7ZA0wsZv3ugS4BGDy5MkFilhEpPJkNbYvJXng7nX5D+ct3ySYT3Jd2vGObXWb0443EQwr7sTdb3H3RndvbGhoyHOYIiKVq+xWxTOzc4HzgGO7KI4m/6xJOx6hc1IREZECKrsEQjDqajywJmW3uyEEo8AeB9qASQSTGDtMpnOzloiIFFA5JpCT6RzX/cAvgV8BdxPMS1mYUj4X+FNRohMREaAME4i7r08/ZmbtwFZ332Rm1wJ3mNnTwALgAmAWcE5xIxURqWxll0B64+73m9nVBKO0xgDzgTPcPfPt2UREpM/6RQJJX4PF3W8g6BMREZES0RKdIiKSEyUQERHJiRKIiIjkRAlERERyogQiIiI5UQIREZGcKIGIiEhOlEBERCQnSiAiIpITJRAREcmJEoiIiORECURERHKiBCIiIjlRAhERkZwogYiISE6UQEREJCdKICIikhMlEBERyYkSiIiI5EQJREREcqIEIiIiOVECERGRnCiBiIhITpRAREQkJ0ogIiKSEyUQERHJiRKIiIjkRAlERERyogQiIiI5UQIREZGcKIGIiEhOlEBERCQnZZlAzOwoM/urmTWZ2Ztm9nMzG55SfqaZLTOzVjNbamanlTBcEZGKVJYJBPhX4DZgDHAicDBwE4CZHQ3cCVwFjABuBO43s0mlCVVEpDKVawK50N3vcfcmd3+dIFmcZWZVwFeBm9z9IXdvcfcbgWeAi0sZsIhIpSnLBOLue9MONQPVya/nAg+mlc8D5hQ6LhEReVtZJpAunAc8BdQDI4GVaeVrgIldXWhml5jZIjNbtGXLlsJGKSJSQco+gZjZxcDlwJXAkOTh5rTTmoDarq5391vcvdHdGxsaGgoWp4hIpQmXOoDumFkEuAY4CzjN3ZeY2dhkcU3a6RE6JxURESmgskwgZjaCoJ9jJ3CEu29NFm0F2oBJwKaUSybTuVlLREQKqFybsG4nSAjvTUkeuHscmA+cnnb+XODhokUnIiLl9wRiZg0EzVYHunuii1OuBe4ws6eBBcAFwCzgnOJFKSIiZZdAgPHJP18zs/SyD7n7783saoLJhGMInkjOcPc9RYxRRKTilV0CcfelQKfMkXbODcANxYlIRES6UnYJpBy4Oyu3NrF0/U6eW7uTDTtbiCec4XXVHDFpOIdOHMasCcOoDVeVOlQRkZJRAknR0h7nD89v4KbHV/Dm7jZCBk3t8X3OefCFTVRXhXB3zjt2MheeMIWJIwaVKGIRkdJRAkmav2Ibn797Mc3tcZrTkkaqtliCtljQt3/H/NX8asEaPnvKAVx+ynTCVeU6qE1EJP8q/hMvkXC+/cCLXHT739m6t73H5JEuGndaowlueGwF77v+KbbsaStgpCIi5aWiE4i78+XfLuGev6+jNdrViOHMtETjrNiyl/f/7Ck272nNY4QiIuWrohPIT+a9zkMvbKIlmvlTR3diCWfrnjbOu+UZovHck5GISH9RsQnkpY27ufmJFXlJHh1iCWfjzhaum/d63t5TRKRcVWQCcXc+f/di2vrQbNWdlmiCnz+5kuWb07c0EREZWCoygSxYtZ03drXiBXr/aCLBrU9qbUcRGdgqMoHc8vhKWrIYbZWteAL+8PwG9rbFCnYPEZFSq7gEkkg4T63YWrCnjw7hUIiFq7YX+C4iIqVTcQlk5dYmwqEel9rKi5ZojCXrdxb8PiIipVJxCeTlN3bTeZHf/IsnYNHqHYW/kYhIiVRcAtnTGiORKHQDVmBXS7Qo9xERKYWKSyDB00cRHkHeupeIyMBUcQlkxKAaqorQBwIwekhtUe4jIlIKFZdADtlvKLFE4Zcaqa4yjp06suD3EREplYpLIBNH1BEqQttSbbiKwyYMK/h9RERKpeISiJnx3kPHF7wZywwap+gJREQGropLIACfOnEq1VWFSyA1VSE+cfz+1IQrsnpFpEJU5CfcweOHcsSk4QWbUBiuMi6cM6Ug7y0iUi4qMoEAXPuxIwryhFBXU8U3zpzJmKGRvL+3iEg5qdgEMn5YHd/54Cwi1fmrgtpwiMb9R/CxYybl7T1FRMpVxSYQgLOPmsgX5x6YlyQSCYeYOX4ot36yEdMMQhGpAOZenGU9yoGZbQHW5Hj5aGBrHsMZ6FRf2VF9ZUf1lb2+1Nn+7t6QfrCiEkhfmNkid28sdRz9heorO6qv7Ki+sleIOqvoJiwREcmdEoiIiORECSRzt5Q6gH5G9ZUd1Vd2VF/Zy3udqQ9ERERyoicQERHJiRKIiIjkRAlERERyogSSxsyOMrO/mlmTmb1pZj83s+Ep5Wea2TIzazWzpWZ2WgnDLRtmdqiZxc3swpRjqqsumFm9mV1vZm+YWZuZvWxm1cky1VkKM4uY2XXJn8U9ZvaYmTWmlKu+ADObZmaPmNkH0473WD9mdqCZPWxmzWa2zsy+kNWN3V2vlBdwH3AuMBh4B/A0cE+y7GhgB/BuoA64HNgLTCp13KV+AQ8AMeBC1VWP9VQFPAncBUwBIsBxyeOqs871dQ3wHHAQMAT4GrANqFd9OcBk4GZgD9AKfDClrMf6SX7GrU3W6SDgpOT5Z2d8/1JXQLm9gCFp388BmpM/4PcC308rnwd8s9Rxl7jOPgI8CixKSSCqq67r6lPAYiDURZnqrHOdPA78U8r3BrQlPxwrvr6SP3u/Bg4FVqclkB7rJ5lQ5qeVfx14NNP7qwkrjbvvTTvUDFQnv54LPJhWPo8gyVQkM2sAfgRcmlakuuraRcD17p7ookx11tldwEVmNsPMhgBXA8uApai+cPf73P18d1/WRXFv9dNd+fGW4YqwSiC9Ow94iuCReSSwMq18DTCx2EGVg+R/sjuBa939tZTjw1FddWJmYaARaDGz+cl256VmdpbqrFu3EtTJywTNNFfxdhOz6qsbGf5/mt5NeYRg4cVeKYH0wMwuJnjMu5Kg/RWCJ5JUTUBtEcMqJ98Emt39urTjqquujSL4+/8T8CVgLEEb/33A4clzVGf7+i4wATiE4APxBwS/JQ9Nlqu+upbJz+CQbsohwzoM5xTaAGdmEYIf7LOA09x9iZmNTRbXpJ0eofM/woBnZucSPJ0d20VxNPmn6mpfHc1WP3b3+cmvbzezDwAXJr9XnSWZ2Ujgy8ChKU+43zOzUwiaAkH11Z1Mfgaj3ZRDhnWoBJLGzEYQtAvuBI5w947187cSdN5NAjalXDKZzo+BleB7wHhgTUpz6RDgBoKOT9VVZx3/h9L3pHmNoG5UZ/s6ACC1eTRpCTAD1VdPMvm8Wp8sJ618l7tvz+QmasLq7HaCCn5vSvLA3ePAfOD0tPPnAg8XLbrycTJwMHBEyusl4BsEvx2qrtJ4MMxlAZ07eQ8hqDvV2b5WATVmdkDa8cMJfkZVX93I8PPqqV7KM7qRXm8PYWsAHHhHN+VnEYyTfifBo96lBFm8vtSxl8OLfYfxqq66rqMPEPx2+A8E7fhXANuBMaqzLuvrl8kPuoOA4QRzFvYQzKFRfe1bV6vZdxhvj/VD0Le0O/l/MAKcCGwGjsv4nqX+S5fTCzgsmUC6en0wec4VBJNvWgnmPswsddzl8kpNIKqrHuvp88l6aQP+BhyrOuu2ruoIOs5XA7uAR4CjVV9d1tU+CSST+iFoSXg++X/xJeAD2dxTy7mLiEhO1AciIiI5UQIREZGcKIGIiEhOlEBERCQnSiAiIpITJRAREcmJEohIlsxsgpmdmOO1N5nZt/IYy3Fm9rV8vZ9INpRARNIktwFdYGa7zWy1md1tZtNTTjkJ+E4X15mZfd3M1ie3RJ5nZgflGMN0M4ulvDzt+/2Tp04l2HEuk/d80szOzyUeka4ogYikMLNPECwI+S8Ey6+/k2Bp6+XJ/Tv2EqyX1pWvA+cApxAsu/FH4K9mNijbONx9hbuH3T1MsMQOBEtQhJOv9AUZe5TcjGkWwfa5InmhBCKyr68Dn3P3R9w9mvygPh/YArzP3Yfw9tLrb0luAXAVcKm7L09e+xPgFeCSPsZ0aPLP2cl73Zd8InHg7t4uTsZ2J8GyKecml48X6TMlEJF9TSVYLvwt7t4KvEqwoVF3jgT2uPszacd/S/KDvw++DFwG/IeZ1bj7R9zd3N0I9mTpkpmFkvu2PE+wSN6HCFZf/YGZ/drMDu5jXFLhlEBE9rWSYGn6t5hZHcFqsEeY2aeBU7u4bgywrovj64F3m9ljZvYYwQqpGTOzq4Ft7n4zcA/wx2RzVE/XRMzstwT7QFwAXOzul7p7u7svTf795gMPJPt4Pp9NTCIdtKGUyL6+DfzMzNqAJwmWvP4hsJxgA63xwLQurtvB29uIphqSvPbrye+/kkkQZjYM+D7BCtFnALj7T5PNUS+Z2Ue7eNoheV6rmf0QuMLdt3RVDvwU+KmZTSNY0lska0ogIinc/W4z2wJcDdxBsIT4PcB33L0d3trO97K0S1cAU81ssLs3pRw/HFjg7k8lr/14hqEcSdCJ/153f2t7UXf/oZk9Cizt5e/x90xu4u7avU9ypuXcRbJkZnOBs939irTjfwUedPdrkt8PJ+hEP9fdH0seuwnY5O7fylMsEWCQp2xBamZ/IdjnIV0NEOPtvdlTXeTuvXbIi6TSE4hIF5JDb79I0PF8AEF/YYKgOep/6bop6ivAvGSz0CrgYuBPHcmjD7HsJNhYqavf9kIEo6tO6Tjg7md08z6PATe5+z19iUekgzrRRdKYmQF/AY4HLgdGu/tQYDTBDm8nAH9Ov87dlxA0Wa0hmLvxNXf/VJ7COsTdI+kvgiHGIiWhJxCRzsYQJIkpqRP23D0G/D05amm5mY1x982pF7r7RoJOd5EBT08gIp1tJhjm+jMzazSzMICZhc3sGIIRTE+lJw+RSqMnEJE07u5mdjpBn8YtwPRks5bzdh/INUUO68XkzPN0HX0gIkWnUVgiRWRmo4C4u+8swb2/BDzh7ouKfW8ZmJRAREQkJ+oDERGRnCiBiIhITpRAREQkJ0ogIiKSEyUQERHJiRKIiIjkRAlERERy8v8BQ9WT0ZzLeS0AAAAASUVORK5CYII="/>


```python
sizes = df['학년'] * 500 # 1학년 = 500, 2학년 = 1000, 3학년 = 1500
plt.scatter(df['영어'],df['수학'], s=sizes)
plt.xlabel('영어 점수')
plt.ylabel('수학 점수')
```

<pre>
Text(0, 0.5, '수학 점수')
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.scatter(df['영어'],df['수학'], s=sizes, c=df['학년'], cmap='viridis', alpha=0.3) # color, colormap
plt.xlabel('영어 점수') 
plt.ylabel('수학 점수')
```

<pre>
Text(0, 0.5, '수학 점수')
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.figure(figsize=(7,7))
plt.scatter(df['영어'],df['수학'], s=sizes, c=df['학년'], cmap='viridis', alpha=0.3) # color, colormap
plt.xlabel('영어 점수') 
plt.ylabel('수학 점수')
plt.colorbar(ticks=[1, 2, 3], label='학년', shrink=0.5, orientation='horizontal')
```

<pre>
<matplotlib.colorbar.Colorbar at 0x27947efbb50>
</pre>
<img src="data:image/png;base64,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"/>
