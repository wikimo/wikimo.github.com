---
layout: post
title: "Failed to manipulate with MiniMagick"
date: 2014-07-15 15:16
comments: true
categories: 
---

主要原因是：imagemagick没有安装好，答案可以在stackoverflow上找到。

可以先用以下命令看下
{% highlight c%}
convert -list configure
#看下下面这个属性是不是全，包含jpeg,png这些，你可能只有xml zlib
DELEGATES     bzlib djvu fontconfig freetype gvc jpeg jng jp2 lcms lqr openexr png rsvg tiff x11 xml zlib
{% endhighlight %}

重新编译安装下imagemagick
{% highlight c%}
wget http://www.imagemagick.org/download/ImageMagick.tar.gz
tar xvfz ImageMagick.tar.gz
cd ImageMagick
./configure --with-bzlib=yes --with-fontconfig=yes --with-freetype=yes --with-gslib=yes --with-gvc=yes --with-jpeg=yes --with-jp2=yes --with-png=yes --with-tiff=yes --disable-shared
make
sudo make install
sudo ldconfig /usr/local/lib
#最后再运行下convert -list configure 看下安装后的结果
run again "convert -list configure" and look at changes
{% endhighlight %}

查看Imagemagick版本
{% highlight c %}
convert -version
{% endhighlight %}

[stackoverflow原文链接](http://stackoverflow.com/questions/10810356/carrierwave-error-msg-failed-to-manipulate-with-minimagick-maybe-it-is-not-an)