# AviUtl OAR_resize

元のアスペクト比（Original Aspect Ratio）を維持したままリサイズする AviUtl スクリプトです。<br>
拡大率、ドット数、アンカーのいずれかの方法でサイズを指定することができます。

![sample](/assets/sample.png)
<a href="https://flic.kr/p/BduEsN">Image</a> by <a href=https://www.flickr.com/people/mathiasappel>Mathias Appel</a> from <a href="https://www.flickr.com/">Flickr</a>

## 推奨
- [patch.aul（フォーク版）](https://github.com/nazonoSAUNA/patch.aul/releases)<br>
- LuaJIT<br>
  なくても動作しますが、導入時は[境界処理](#境界タイプ)を高速化します。

## 導入方法
1. Release から `OAR_resize.zip` をダウンロードします。
2. exedit.auf と同一ディレクトリ（または1層下）にある `script` フォルダに `@OAR_resize.anm` を入れてください。

## 拡大率@OAR_resize
拡大率でサイズを指定します。設定ダイアログの [`ドット数でサイズ指定`](#ドット数でサイズ指定) を有効にすることでドット数によるサイズ指定も可能になります。

### トラックバー
- #### 拡大率
  拡大率を指定します。

- #### X
  横幅を指定します。

- #### Y
  縦幅を指定します。

- #### 境界タイプ
  リサイズ後の画像境界（余白）のタイプを選択します。
  | タイプ | 概要 | サンプル画像（<a href="https://pixabay.com/photos/bell-peppers-sweet-peppers-capsicums-499068/">Image</a> by <a href="https://pixabay.com/users/hans-2/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=499068">Hans</a> from <a href="https://pixabay.com//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=499068">Pixabay</a>） |
  |:---:|:---:|:---:|
  | `0` | 透明 | ![border-0](/assets/border-0.png) |
  | `1` | 指定した色で塗りつぶす | ![border-1](/assets/border-1.png) |
  | `2` | 最も外側のピクセルで補う | ![border-2](/assets/border-2.png) |
  | `3` | 同じ向きで繰り返す | ![border-3](/assets/border-3.png) |
  | `4` | 最も外側のピクセルを中心に鏡面反射する | ![border-4](/assets/border-4.png) |
  | `5` | ぼかした画像にする | ![border-5](/assets/border-5.png) |

### 設定ダイアログ
- #### スクリーンに合わせる
  スクリーンにフィットするようにリサイズします。有効にするとオブジェクトの拡大率、スクリプトのトラックバー（`拡大率`, `X`, `Y`）、ドット数によるサイズ指定ができなくなります。

- #### ドット数でサイズ指定
  ドット数でサイズを指定します。トラックバーの `X` が横幅、`Y` が縦幅になります。

- #### 補間なし
  有効にするとリサイズ時に補間しなくなります。

- #### 維持基準[0:短/1:長]
  - チェック有 : 短い辺を基準に縦横比を維持します。
  - チェック無 : 長い辺を基準に縦横比を維持します。

- #### 境界タイプ[1] : 色 
  境界タイプが `1` のときの色を指定します。

- #### 境界タイプ[5] : ぼかし
  境界タイプが `5` のとき、どれくらいの強度でぼかすか指定します。最大値は `1000` です。

<br>

## アンカー@OAR_resize
2つのアンカーでサイズを指定します。

### トラックバー
- #### 時間経過
  移動方法を選択することで有効になります。どのくらい変形させるかを `0` ~ `100` の範囲で指定します。
  
  - 移動方法を指定することで、オブジェクトの中心に移動後のアンカーポイント（初期状態は2つのアンカーポイントが重なっている）が出現します。
  - アンカーをつなぐ線は移動前が緑、移動後が赤で表示されます。

- #### 境界タイプ
  リサイズ後の画像境界（余白）のタイプを選択します。`拡大率@OAR_resize` と同じです。

### 設定ダイアログ
- #### 座標
  左上、右下のアンカーの座標が格納されます。

- #### 反転なし
  有効にするとアンカーの位置に応じて反転しなくなります。

- #### 補間なし
  有効にするとリサイズ時に補間しなくなります。

- #### 維持基準[0:短/1:長]
  - チェック有 : 短い辺を基準に縦横比を維持します。
  - チェック無 : 長い辺を基準に縦横比を維持します。

- #### 境界タイプ[1] : 色 
  境界タイプが `1` のときの色を指定します。

- #### 境界タイプ[5] : ぼかし
  境界タイプが `5` のとき、どれくらいの強度でぼかすか指定します。最大値は `1000` です。

### 注意点
[最大画像サイズ](https://scrapbox.io/aviutl/%E6%9C%80%E5%A4%A7%E7%94%BB%E5%83%8F%E3%82%B5%E3%82%A4%E3%82%BA)より大きいサイズにリサイズしようとすると、オブジェクトとアンカーの位置がずれます。

## ライセンス
[MIT Lisence](LICENSE.txt) に基づくものとします。

## 更新履歴
- #### v1.0.0 (2024/12/26)
  初版