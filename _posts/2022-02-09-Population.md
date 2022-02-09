---
layout: single
title:  "Population pyramid"
categories: Project
date: 2022-02-09 16:52:31
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


# 1. 인구 피라미드


## 남자 데이터 정의



```python
import pandas as pd
file_name = '201201_201201_연령별인구현황_월간.xlsx'
df_m = pd.read_excel(file_name, skiprows=3, index_col='행정기관', usecols='B,E:Y')
df_m.head(3)
```

<pre>
C:\Users\Chae\anaconda3\lib\site-packages\openpyxl\styles\stylesheet.py:226: UserWarning: Workbook contains no default style, apply openpyxl's default
  warn("Workbook contains no default style, apply openpyxl's default")
</pre>
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
      <th>0~4세</th>
      <th>5~9세</th>
      <th>10~14세</th>
      <th>15~19세</th>
      <th>20~24세</th>
      <th>25~29세</th>
      <th>30~34세</th>
      <th>35~39세</th>
      <th>40~44세</th>
      <th>45~49세</th>
      <th>...</th>
      <th>55~59세</th>
      <th>60~64세</th>
      <th>65~69세</th>
      <th>70~74세</th>
      <th>75~79세</th>
      <th>80~84세</th>
      <th>85~89세</th>
      <th>90~94세</th>
      <th>95~99세</th>
      <th>100세 이상</th>
    </tr>
    <tr>
      <th>행정기관</th>
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
      <th>전국</th>
      <td>1,196,298</td>
      <td>1,215,642</td>
      <td>1,627,682</td>
      <td>1,878,394</td>
      <td>1,692,322</td>
      <td>1,798,832</td>
      <td>2,058,717</td>
      <td>2,151,718</td>
      <td>2,346,348</td>
      <td>2,171,235</td>
      <td>...</td>
      <td>1,608,133</td>
      <td>1,139,681</td>
      <td>885,678</td>
      <td>719,811</td>
      <td>437,707</td>
      <td>194,827</td>
      <td>77,608</td>
      <td>22,964</td>
      <td>4,766</td>
      <td>2,691</td>
    </tr>
    <tr>
      <th>서울특별시</th>
      <td>216,843</td>
      <td>212,597</td>
      <td>282,790</td>
      <td>344,798</td>
      <td>337,696</td>
      <td>421,899</td>
      <td>475,109</td>
      <td>452,897</td>
      <td>463,064</td>
      <td>412,326</td>
      <td>...</td>
      <td>334,448</td>
      <td>240,777</td>
      <td>190,839</td>
      <td>139,263</td>
      <td>74,020</td>
      <td>32,185</td>
      <td>13,282</td>
      <td>4,663</td>
      <td>1,203</td>
      <td>907</td>
    </tr>
    <tr>
      <th>부산광역시</th>
      <td>67,475</td>
      <td>69,137</td>
      <td>99,796</td>
      <td>128,970</td>
      <td>123,263</td>
      <td>126,669</td>
      <td>138,762</td>
      <td>134,439</td>
      <td>148,476</td>
      <td>145,068</td>
      <td>...</td>
      <td>137,184</td>
      <td>100,614</td>
      <td>73,804</td>
      <td>55,002</td>
      <td>29,768</td>
      <td>12,274</td>
      <td>4,325</td>
      <td>1,141</td>
      <td>244</td>
      <td>230</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 21 columns</p>
</div>



```python
df_m.iloc[0] = df_m.iloc[0].str.replace(',','').astype(int) # ,를 없애야 숫자 형태
# 778,266 -> 778266 (정수형)
```


```python
df_m.iloc[0]
```

<pre>
0~4세       1196298
5~9세       1215642
10~14세     1627682
15~19세     1878394
20~24세     1692322
25~29세     1798832
30~34세     2058717
35~39세     2151718
40~44세     2346348
45~49세     2171235
50~54세     2182972
55~59세     1608133
60~64세     1139681
65~69세      885678
70~74세      719811
75~79세      437707
80~84세      194827
85~89세       77608
90~94세       22964
95~99세        4766
100세 이상       2691
Name: 전국  , dtype: object
</pre>
## 여자 데이터 정의



```python
df_w = pd.read_excel(file_name, skiprows=3, index_col='행정기관', usecols='B,AB:AV')
df_w.head(3)
```

<pre>
C:\Users\Chae\anaconda3\lib\site-packages\openpyxl\styles\stylesheet.py:226: UserWarning: Workbook contains no default style, apply openpyxl's default
  warn("Workbook contains no default style, apply openpyxl's default")
</pre>
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
      <th>0~4세.1</th>
      <th>5~9세.1</th>
      <th>10~14세.1</th>
      <th>15~19세.1</th>
      <th>20~24세.1</th>
      <th>25~29세.1</th>
      <th>30~34세.1</th>
      <th>35~39세.1</th>
      <th>40~44세.1</th>
      <th>45~49세.1</th>
      <th>...</th>
      <th>55~59세.1</th>
      <th>60~64세.1</th>
      <th>65~69세.1</th>
      <th>70~74세.1</th>
      <th>75~79세.1</th>
      <th>80~84세.1</th>
      <th>85~89세.1</th>
      <th>90~94세.1</th>
      <th>95~99세.1</th>
      <th>100세 이상.1</th>
    </tr>
    <tr>
      <th>행정기관</th>
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
      <th>전국</th>
      <td>1,128,024</td>
      <td>1,126,625</td>
      <td>1,492,152</td>
      <td>1,659,937</td>
      <td>1,525,305</td>
      <td>1,691,682</td>
      <td>1,975,775</td>
      <td>2,068,220</td>
      <td>2,277,052</td>
      <td>2,051,092</td>
      <td>...</td>
      <td>1,624,628</td>
      <td>1,189,414</td>
      <td>1,009,513</td>
      <td>933,302</td>
      <td>700,197</td>
      <td>429,811</td>
      <td>208,227</td>
      <td>73,481</td>
      <td>19,130</td>
      <td>9,067</td>
    </tr>
    <tr>
      <th>서울특별시</th>
      <td>205,591</td>
      <td>199,837</td>
      <td>260,917</td>
      <td>309,366</td>
      <td>333,116</td>
      <td>431,682</td>
      <td>466,958</td>
      <td>437,616</td>
      <td>460,637</td>
      <td>408,707</td>
      <td>...</td>
      <td>361,120</td>
      <td>258,846</td>
      <td>205,704</td>
      <td>159,556</td>
      <td>108,150</td>
      <td>67,410</td>
      <td>34,724</td>
      <td>13,038</td>
      <td>3,930</td>
      <td>2,718</td>
    </tr>
    <tr>
      <th>부산광역시</th>
      <td>64,052</td>
      <td>64,215</td>
      <td>89,346</td>
      <td>109,301</td>
      <td>109,765</td>
      <td>118,838</td>
      <td>132,634</td>
      <td>130,434</td>
      <td>152,203</td>
      <td>148,289</td>
      <td>...</td>
      <td>143,244</td>
      <td>105,702</td>
      <td>79,870</td>
      <td>68,449</td>
      <td>47,084</td>
      <td>28,764</td>
      <td>13,212</td>
      <td>4,138</td>
      <td>1,169</td>
      <td>848</td>
    </tr>
  </tbody>
</table>
<p>3 rows × 21 columns</p>
</div>



```python
df_m.columns
```

<pre>
Index(['0~4세', '5~9세', '10~14세', '15~19세', '20~24세', '25~29세', '30~34세',
       '35~39세', '40~44세', '45~49세', '50~54세', '55~59세', '60~64세', '65~69세',
       '70~74세', '75~79세', '80~84세', '85~89세', '90~94세', '95~99세', '100세 이상'],
      dtype='object')
</pre>

```python
df_w.columns
```

<pre>
Index(['0~4세.1', '5~9세.1', '10~14세.1', '15~19세.1', '20~24세.1', '25~29세.1',
       '30~34세.1', '35~39세.1', '40~44세.1', '45~49세.1', '50~54세.1', '55~59세.1',
       '60~64세.1', '65~69세.1', '70~74세.1', '75~79세.1', '80~84세.1', '85~89세.1',
       '90~94세.1', '95~99세.1', '100세 이상.1'],
      dtype='object')
</pre>

```python
df_w.columns = df_m.columns # column명 통일
df_w.columns
```

<pre>
Index(['0~4세', '5~9세', '10~14세', '15~19세', '20~24세', '25~29세', '30~34세',
       '35~39세', '40~44세', '45~49세', '50~54세', '55~59세', '60~64세', '65~69세',
       '70~74세', '75~79세', '80~84세', '85~89세', '90~94세', '95~99세', '100세 이상'],
      dtype='object')
</pre>

```python
df_w.iloc[0] = df_w.iloc[0].str.replace(',','').astype(int) # ,를 없애야 숫자 형태
df_w
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
      <th>0~4세</th>
      <th>5~9세</th>
      <th>10~14세</th>
      <th>15~19세</th>
      <th>20~24세</th>
      <th>25~29세</th>
      <th>30~34세</th>
      <th>35~39세</th>
      <th>40~44세</th>
      <th>45~49세</th>
      <th>...</th>
      <th>55~59세</th>
      <th>60~64세</th>
      <th>65~69세</th>
      <th>70~74세</th>
      <th>75~79세</th>
      <th>80~84세</th>
      <th>85~89세</th>
      <th>90~94세</th>
      <th>95~99세</th>
      <th>100세 이상</th>
    </tr>
    <tr>
      <th>행정기관</th>
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
      <th>전국</th>
      <td>1128024</td>
      <td>1126625</td>
      <td>1492152</td>
      <td>1659937</td>
      <td>1525305</td>
      <td>1691682</td>
      <td>1975775</td>
      <td>2068220</td>
      <td>2277052</td>
      <td>2051092</td>
      <td>...</td>
      <td>1624628</td>
      <td>1189414</td>
      <td>1009513</td>
      <td>933302</td>
      <td>700197</td>
      <td>429811</td>
      <td>208227</td>
      <td>73481</td>
      <td>19130</td>
      <td>9067</td>
    </tr>
    <tr>
      <th>서울특별시</th>
      <td>205,591</td>
      <td>199,837</td>
      <td>260,917</td>
      <td>309,366</td>
      <td>333,116</td>
      <td>431,682</td>
      <td>466,958</td>
      <td>437,616</td>
      <td>460,637</td>
      <td>408,707</td>
      <td>...</td>
      <td>361,120</td>
      <td>258,846</td>
      <td>205,704</td>
      <td>159,556</td>
      <td>108,150</td>
      <td>67,410</td>
      <td>34,724</td>
      <td>13,038</td>
      <td>3,930</td>
      <td>2,718</td>
    </tr>
    <tr>
      <th>부산광역시</th>
      <td>64,052</td>
      <td>64,215</td>
      <td>89,346</td>
      <td>109,301</td>
      <td>109,765</td>
      <td>118,838</td>
      <td>132,634</td>
      <td>130,434</td>
      <td>152,203</td>
      <td>148,289</td>
      <td>...</td>
      <td>143,244</td>
      <td>105,702</td>
      <td>79,870</td>
      <td>68,449</td>
      <td>47,084</td>
      <td>28,764</td>
      <td>13,212</td>
      <td>4,138</td>
      <td>1,169</td>
      <td>848</td>
    </tr>
    <tr>
      <th>대구광역시</th>
      <td>49,948</td>
      <td>53,051</td>
      <td>75,410</td>
      <td>85,710</td>
      <td>74,443</td>
      <td>78,377</td>
      <td>92,385</td>
      <td>102,300</td>
      <td>119,437</td>
      <td>110,168</td>
      <td>...</td>
      <td>85,274</td>
      <td>62,991</td>
      <td>48,418</td>
      <td>44,476</td>
      <td>31,975</td>
      <td>18,546</td>
      <td>8,294</td>
      <td>2,810</td>
      <td>674</td>
      <td>299</td>
    </tr>
    <tr>
      <th>인천광역시</th>
      <td>64,864</td>
      <td>63,616</td>
      <td>83,564</td>
      <td>98,190</td>
      <td>91,558</td>
      <td>96,173</td>
      <td>111,632</td>
      <td>116,458</td>
      <td>131,634</td>
      <td>124,498</td>
      <td>...</td>
      <td>83,158</td>
      <td>55,092</td>
      <td>45,735</td>
      <td>40,026</td>
      <td>30,147</td>
      <td>19,094</td>
      <td>9,480</td>
      <td>3,257</td>
      <td>796</td>
      <td>340</td>
    </tr>
    <tr>
      <th>광주광역시</th>
      <td>34,978</td>
      <td>37,433</td>
      <td>52,811</td>
      <td>57,080</td>
      <td>47,370</td>
      <td>50,389</td>
      <td>58,849</td>
      <td>62,657</td>
      <td>67,102</td>
      <td>58,957</td>
      <td>...</td>
      <td>39,857</td>
      <td>32,150</td>
      <td>25,430</td>
      <td>22,227</td>
      <td>15,967</td>
      <td>10,292</td>
      <td>4,979</td>
      <td>1,937</td>
      <td>483</td>
      <td>231</td>
    </tr>
    <tr>
      <th>대전광역시</th>
      <td>36,093</td>
      <td>37,409</td>
      <td>49,028</td>
      <td>53,858</td>
      <td>48,660</td>
      <td>52,617</td>
      <td>61,324</td>
      <td>65,195</td>
      <td>71,439</td>
      <td>61,626</td>
      <td>...</td>
      <td>45,575</td>
      <td>30,964</td>
      <td>24,734</td>
      <td>21,572</td>
      <td>16,432</td>
      <td>10,054</td>
      <td>4,925</td>
      <td>1,664</td>
      <td>446</td>
      <td>171</td>
    </tr>
    <tr>
      <th>울산광역시</th>
      <td>27,457</td>
      <td>26,136</td>
      <td>36,544</td>
      <td>41,047</td>
      <td>33,731</td>
      <td>35,482</td>
      <td>43,997</td>
      <td>46,873</td>
      <td>56,623</td>
      <td>50,929</td>
      <td>...</td>
      <td>34,158</td>
      <td>21,359</td>
      <td>15,118</td>
      <td>12,825</td>
      <td>9,493</td>
      <td>6,071</td>
      <td>3,104</td>
      <td>964</td>
      <td>235</td>
      <td>74</td>
    </tr>
    <tr>
      <th>경기도</th>
      <td>303,357</td>
      <td>304,120</td>
      <td>384,018</td>
      <td>407,977</td>
      <td>363,742</td>
      <td>392,430</td>
      <td>491,417</td>
      <td>541,293</td>
      <td>585,302</td>
      <td>499,588</td>
      <td>...</td>
      <td>327,612</td>
      <td>223,844</td>
      <td>195,150</td>
      <td>173,894</td>
      <td>127,929</td>
      <td>77,323</td>
      <td>38,307</td>
      <td>13,656</td>
      <td>3,472</td>
      <td>1,560</td>
    </tr>
    <tr>
      <th>강원도</th>
      <td>30,345</td>
      <td>32,906</td>
      <td>44,797</td>
      <td>48,519</td>
      <td>41,916</td>
      <td>40,155</td>
      <td>48,140</td>
      <td>54,839</td>
      <td>61,788</td>
      <td>60,033</td>
      <td>...</td>
      <td>54,606</td>
      <td>37,163</td>
      <td>39,412</td>
      <td>39,172</td>
      <td>27,889</td>
      <td>17,883</td>
      <td>9,032</td>
      <td>3,218</td>
      <td>778</td>
      <td>294</td>
    </tr>
    <tr>
      <th>충청북도</th>
      <td>35,343</td>
      <td>35,345</td>
      <td>47,541</td>
      <td>51,326</td>
      <td>44,030</td>
      <td>47,141</td>
      <td>53,863</td>
      <td>58,887</td>
      <td>66,286</td>
      <td>59,916</td>
      <td>...</td>
      <td>49,960</td>
      <td>34,890</td>
      <td>34,302</td>
      <td>34,572</td>
      <td>28,331</td>
      <td>16,628</td>
      <td>7,721</td>
      <td>2,724</td>
      <td>700</td>
      <td>218</td>
    </tr>
    <tr>
      <th>충청남도</th>
      <td>50,196</td>
      <td>48,319</td>
      <td>62,034</td>
      <td>65,004</td>
      <td>58,388</td>
      <td>61,733</td>
      <td>72,805</td>
      <td>77,695</td>
      <td>82,638</td>
      <td>74,456</td>
      <td>...</td>
      <td>64,268</td>
      <td>52,593</td>
      <td>47,814</td>
      <td>51,632</td>
      <td>44,245</td>
      <td>25,532</td>
      <td>12,347</td>
      <td>4,316</td>
      <td>1,114</td>
      <td>430</td>
    </tr>
    <tr>
      <th>전라북도</th>
      <td>39,258</td>
      <td>41,556</td>
      <td>57,815</td>
      <td>63,584</td>
      <td>53,136</td>
      <td>51,798</td>
      <td>59,084</td>
      <td>66,444</td>
      <td>73,506</td>
      <td>68,970</td>
      <td>...</td>
      <td>59,516</td>
      <td>52,141</td>
      <td>46,748</td>
      <td>48,723</td>
      <td>40,106</td>
      <td>24,689</td>
      <td>11,191</td>
      <td>4,179</td>
      <td>1,054</td>
      <td>411</td>
    </tr>
    <tr>
      <th>전라남도</th>
      <td>39,129</td>
      <td>39,570</td>
      <td>55,977</td>
      <td>61,266</td>
      <td>48,823</td>
      <td>47,507</td>
      <td>54,873</td>
      <td>59,908</td>
      <td>68,800</td>
      <td>68,319</td>
      <td>...</td>
      <td>59,716</td>
      <td>56,165</td>
      <td>56,025</td>
      <td>63,042</td>
      <td>48,400</td>
      <td>31,154</td>
      <td>14,607</td>
      <td>5,210</td>
      <td>1,346</td>
      <td>510</td>
    </tr>
    <tr>
      <th>경상북도</th>
      <td>55,342</td>
      <td>53,470</td>
      <td>72,403</td>
      <td>79,585</td>
      <td>72,043</td>
      <td>75,465</td>
      <td>88,163</td>
      <td>94,825</td>
      <td>105,919</td>
      <td>102,809</td>
      <td>...</td>
      <td>95,244</td>
      <td>74,322</td>
      <td>66,870</td>
      <td>72,621</td>
      <td>58,569</td>
      <td>35,449</td>
      <td>17,012</td>
      <td>6,066</td>
      <td>1,400</td>
      <td>418</td>
    </tr>
    <tr>
      <th>경상남도</th>
      <td>78,113</td>
      <td>74,948</td>
      <td>100,365</td>
      <td>107,721</td>
      <td>88,713</td>
      <td>95,623</td>
      <td>120,125</td>
      <td>130,369</td>
      <td>147,946</td>
      <td>131,028</td>
      <td>...</td>
      <td>104,561</td>
      <td>78,006</td>
      <td>66,308</td>
      <td>68,975</td>
      <td>55,660</td>
      <td>34,847</td>
      <td>15,953</td>
      <td>4,719</td>
      <td>1,036</td>
      <td>391</td>
    </tr>
    <tr>
      <th>제주특별자치도</th>
      <td>13,958</td>
      <td>14,694</td>
      <td>19,582</td>
      <td>20,403</td>
      <td>15,871</td>
      <td>16,272</td>
      <td>19,526</td>
      <td>22,427</td>
      <td>25,792</td>
      <td>22,799</td>
      <td>...</td>
      <td>16,759</td>
      <td>13,186</td>
      <td>11,875</td>
      <td>11,540</td>
      <td>9,820</td>
      <td>6,075</td>
      <td>3,339</td>
      <td>1,585</td>
      <td>497</td>
      <td>154</td>
    </tr>
  </tbody>
</table>
<p>17 rows × 21 columns</p>
</div>


## 데이터 시각화



```python
import matplotlib.pyplot as plt
import matplotlib
matplotlib.rcParams['font.family'] = 'Malgun Gothic' # 글자 폰트
matplotlib.rcParams['font.size'] = 15 # 글자 크기
matplotlib.rcParams['axes.unicode_minus'] = False # 한글 폰트 사용 시, 마이너스 글자가 깨지는 현상을 해결
```


```python
plt.figure(figsize=(10,7))
plt.barh(df_m.columns, -df_m.iloc[0] // 1000 )  # 단위 : 천 명
plt.barh(df_w.columns, df_w.iloc[0] // 1000 )
plt.title("2012년 대한민국 인구 피라미드")
plt.savefig('2012_인구피라미드.png', dpi=100)
plt.show()
```

<img src="data:image/png;base64,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"/>
