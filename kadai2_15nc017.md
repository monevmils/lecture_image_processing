
# 課題２レポート
### 課題２　階調数と疑似輪郭
    2階調，４階調，８階調の画像を生成せよ．

フリー画像「大曲の花火夜の部幕開け」を元画像とする．この画像は縦1600画像，横1066画素によるディジタルカラー画像である．  
素材元：[ぱくたそ](https://www.pakutaso.com/20180643172post-16577.html,"画像元リンク")

ORG=imread('hanabi.jpg'); % 原画像の入力  
imagesc(ORG); axis image; % 画像の表示

によって，原画像を読み込み，表示した結果を図１に示す．

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/hanabi.jpg?raw=true)  
図1 原画像

原画像を2階調にするため、しきい値を128にもうけ、２値化する

IMG = ORG>128;  
imagesc(IMG); colormap(gray); colorbar;  axis image;  


結果を図２に示す．

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/2-1.jpg?raw=true)  
図2 2階調

同様に4階調原画像にするためには64ごとにしきい値を設け、輝度値を分類する.

IMG0 = ORG>64;  
IMG1 = ORG>128;  
IMG2 = ORG>192;  
IMG = IMG0 + IMG1 + IMG2;  
imagesc(IMG); colormap(gray); colorbar;  axis image;  

とする．4階調の結果を図３に示す．

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/2-2.jpg?raw=true)  
図3 4階調

同様に8階調原画像にするためには8ごとにしきい値を設け、輝度値を分類する.

IMG3 = ORG>8;  
IMG4 = ORG>16;  
IMG5 = ORG>32;  
IMG6 = ORG>64;  
IMG7 = ORG>96;  
IMG8 = ORG>128;  
IMG9 = ORG>160;  
IMG10 = ORG>192;  
IMG11 = ORG>224;  
IMG = IMG3 + IMG4 + IMG5 + IMG6 + IMG7 + IMG8 + IMG9 + IMG10 + IMG11;  
imagesc(IMG); colormap(gray); colorbar;  axis image;  

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/2-3.jpg?raw=true)  
図4 8階調

このように階調を増やすとグレイスケールが細やかに表現できる．
