# ピボットテーブル
複数データフレームをマージ後にピボットテーブルで様々な角度から集計を行う

<br>

## 取引概要データのデータフレームを表示
```
frame1
```
![画像1](./Pandas-Exercises6-1.png)

<br>

## 取引詳細データのデータフレームを表示
```
frame2
```
![画像2](./Pandas-Exercises6-2.png)

<br>

## 商品データのデータフレームを表示
```
frame3
```
![画像3](./Pandas-Exercises6-3.png)

<br>

## 顧客データのデータフレームを表示
```
frame4
```
![画像4](./Pandas-Exercises6-4.png)

<br>

## 取引詳細データに取引概要データをマージ
```
frame2 = pd.merge(frame2, frame1, how='left', on='取引ID')
```
![画像5](./Pandas-Exercises6-5.png)

<br>

## 取引詳細データに顧客データをマージ
```
frame2 = pd.merge(frame2, frame4, how='left', on='顧客ID')
```
![画像6](./Pandas-Exercises6-6.png)

<br>

## 取引詳細データに商品データをマージ
```
frame2 = pd.merge(frame2, frame3, how='left', on='商品ID')
```
![画像7](./Pandas-Exercises6-7.png)

<br>

## 取引詳細データに索引設定
```
frame2.set_index(['取引ID', '商品ID'])
```
![画像8](./Pandas-Exercises6-8.png)

<br>

## 列(取引日)、行(商品名)のグループで取引量を集計(集計関数は合計を使用)
```
frame2.pivot_table(values='取引量', index='商品名', columns='取引日', aggfunc=np.sum)
```
![画像9](./Pandas-Exercises6-9.png)

<br>

## 列(商品名)、行(取引日)のグループで取引量を集計(集計関数は合計を使用)
```
frame2.pivot_table(values='取引量', index='取引日', columns='商品名', aggfunc=np.sum)
```
![画像10](./Pandas-Exercises6-10.png)

## 列(取引日)、行(顧客名)のグループで取引量を集計(集計関数は合計を使用)
```
frame2.pivot_table(values='取引量', index='顧客名', columns='取引日', aggfunc=np.sum)
```
![画像11](./Pandas-Exercises6-11.png)

## 列(顧客名)、行(取引日)のグループで取引量を集計(集計関数は合計を使用)
```
frame2.pivot_table(values='取引量', index='取引日', columns='顧客名', aggfunc=np.sum)
```
![画像12](./Pandas-Exercises6-12.png)
