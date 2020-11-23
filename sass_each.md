# Sassで同じスタイルを楽に管理
## @eachを使う。
### colorを使い分ける場合



```html:index.html
<section id="nav_color">
  <h1>カラーを使い分ける場合</h1>
    <ul>
        <li class="color_home"><a href="#">HOME</a></li>
        <li class="color_about"><a href="#">ABOUT</a></li>
        <li class="color_company"><a href="#">COMPANY</a></li>
        <li class="color_contact"><a href="#">CONTACT</a></li>
    </ul>
</section>
```


```scss:style.scss
// カテゴリーの配列名
$namelist: home, about, company, contact;
// 色の配列名
$color: #1ABC9C, #3498DB, #E67E22, #F1C40F;

#nav_color{
	ul{
		li{
			@each $i in $namelist{
				$index_key: index($namelist, $i);
				&.color_#{$i}{
					a{
						background-color: nth($color, $index_key);
					}
				}
			}
		}
	}
}
```


### 画像を使い分ける場合


```html:index.html
<section id="nav_image">
   <h1>画像を使い分ける場合</h1>
       <ul>
           <li class="icon_home"><a href="#">HOME</a></li>
           <li class="icon_about"><a href="#">ABOUT</a></li>
           <li class="icon_company"><a href="#">COMPANY</a></li>
           <li class="icon_contact"><a href="#">CONTACT</a></li>
       </ul>
</section>
```


```scss:style.scss
// カテゴリーの配列名
$namelist: home, about, company, contact;

#nav_image{
	ul{
		li{
			@each $name in $namelist{
				&.icon_#{$name}{
					a{
						background: url(../images/icon_#{$name}.png) no-repeat 12px 15px;
						&:hover{
							background: url(../images/icon_#{$name}.png) no-repeat #f4f6f6 12px 15px;
						}
					}
				}
			}
		}
	}
}
```

