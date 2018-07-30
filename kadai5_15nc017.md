

# 課題５レポート
### 課題５　判別分析法
    判別分析法を用いて画像二値化せよ．

フリー画像「大曲の花火夜の部幕開け」を元画像とする．この画像は縦1600画像，横1066画素によるディジタルカラー画像である．  
素材元：[ぱくたそ](https://www.pakutaso.com/20180643172post-16577.html,"画像元リンク")

ORG=imread('hanabi.jpg'); % 原画像の入力  
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換  
magesc(ORG); colormap(gray); colorbar; % 画像の表示  
によって，原画像を白黒濃淡画像へ変換し，表示した結果を図１に示し原画像とする．  

![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/5-1.jpg?raw=true)  
図1 白黒濃淡画像

判別分析法を用いて、もっとも効果的な2値化のしきい値を見つける  
判別分析法とは以下の手順で2値化するしきい値を生成する方法である  

    入力画像をヒストグラム化  
    2つクラスを作成  
    2つのクラス内の輝度値からそれぞれ分散を算出  
    クラス内分散とクラス間分散の比が最大になるあたりを繰り返し算出する
    最大値になったときの繰り返し回数がしきい値になる

H = imhist(ORG); %ヒストグラムのデータを列ベクトルEに格納  
myu_T = mean(H);  
max_val = 0;  
max_thres = 1;  
for i=1:255  
C1 = H(1:i); %ヒストグラムを2つのクラスに分ける  
C2 = H(i+1:256);  
n1 = sum(C1); %画素数の算出  
n2 = sum(C2);  
myu1 = mean(C1); %平均値の算出  
myu2 = mean(C2);  
sigma1 = var(C1); %分散の算出  
sigma2 = var(C2);  
sigma_w = (n1 *sigma1+n2*sigma2)/(n1+n2); %クラス内分散の算出  
sigma_B = (n1 *(myu1-myu_T)^2+n2*(myu2-myu_T)^2)/(n1+n2); %クラス間分散の算出  
if max_val<sigma_B/sigma_w  
max_val = sigma_B/sigma_w;  
max_thres =i;  
end;  
end;  

計算した結果、分散比の最大は以下の値になった  
disp(max_val)  

    0.7831

計算した結果、しきい値は以下の値になった  
disp(max_thres)  
    
    138

IMG = ORG > max_thres;  
imagesc(IMG); colormap(gray); colorbar;  
![原画像](https://github.com/monevmils/lecture_image_processing/blob/master/image/5-2.jpg?raw=true)  
図2 2値化画像

このようにもっとも効率のよい２値化を行った2値化画像が生成できる
