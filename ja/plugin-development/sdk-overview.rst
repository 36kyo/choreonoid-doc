====================
Choreonoid SDKの概要
====================

概要
----

C++バージョン
-------------

C++11以上。

モジュール
----------

名前空間
--------

ヘッダファイル
--------------

これらのヘッダの実態はソースツリーの src/Base 以下にあります。クラス定義の詳細を知りたい場合は、それらのヘッダファイルを直接参照してみてください。（ヘッダファイルの実態については拡張子 .h がついていますので、ご注意ください。）


ライブラリファイル
------------------

標準C++ライブラリ
-----------------

標準C++ライブラリ(C++11以上、C++14やC++17の関数もあれば使用、stdxヘッダ）

依存ライブラリ
--------------

Qt, boost(廃止予定、新規のプラグインでは使わないで）、gettext

内蔵しているもの(thirdpartyディレクトリ）

CMakeの変数・関数
-----------------


リファレンスマニュアル
----------------------

なお、Doxygenというツールを用いることで、クラス定義の詳細を一覧できるリファレンスマニュアルを生成することも可能なのですが、今のところ解説文生成のためのコメント付けが不十分な状態です。そちらについては今後整備を進めていく予定です。 ::

ヘッダファイルやソースファイルをみる。

