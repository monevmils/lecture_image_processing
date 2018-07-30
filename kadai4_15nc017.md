

# 課題４レポート
### 課題４　画像のヒストグラム
    画素の濃度ヒストグラムを生成せよ

フリー画像「大曲の花火夜の部幕開け」を元画像とする．この画像は縦1600画像，横1066画素によるディジタルカラー画像である．  
素材元：[ぱくたそ](https://www.pakutaso.com/20180643172post-16577.html,"画像元リンク")

ORG=imread('hanabi.jpg'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
magesc(ORG); colormap(gray); colorbar; % 画像の表示  
によって，原画像を白黒濃淡画像へ変換し，表示した結果を図１に示し原画像とする．  

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/4-1.jpg?raw=true)  
図1 白黒濃淡画像

原画像の輝度値を分析してヒストグラム化する  
imhist(ORG); % ヒストグラムの表示  
結果を図２に示す．

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/4-2.jpg?raw=true)  
図2 ヒストグラム1

明るさを際立たせるためにヒストグラムを平坦化し、さらにヒストグラムを表示する  
J = histeq(ORG); % ヒストグラムの平坦化  
imhist(J)  
結果を図3に示す．

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/4-3.jpg?raw=true)  
図3 ヒストグラム2

ヒストグラムを平坦化した画像と並べて比較する

imshowpair(ORG,J,'montage') % 両方を並べて表示  
結果を図4に示す．左が原画像、右が輝度値を平坦化させた画像  
![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/4-4.jpg?raw=true)  
図4 明るさ調整の比較

このようにヒストグラム化すると画像の輝度値を分析することができ、平坦化すると明るさを調整することができる
