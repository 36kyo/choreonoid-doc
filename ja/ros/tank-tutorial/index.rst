
ROS版Tankチュートリアル
=======================

本チュートリアルでは、Choreonoidのサンプルモデルのひとつである "Tank" モデルを対象として、シミュレーションにおいてROSで入出力を行う方法を解説します。これはChoreonoidの基本機能に基づくチュートリアルである :doc:`../../simulation/tank-tutorial/index` をROS用に発展させたもので、本チュートリアルでは適宜その関連ページを参照いただく構成としています。Choreonoidを用いたシミュレーションの基本についてまだ習得されていない方は、まず基本となる :doc:`../../simulation/tank-tutorial/index` を実施してから、本チュートリアルに移られることをおすすめします。

本チュートリアルでは制御プログラムの実装にC++を用いるものとし、 `roscppライブラリ <http://wiki.ros.org/roscpp>`_ を用いてROSの機能を利用します。この方法を習得すれば、roscppライブラリを利用したコーディングを行うことでROSの様々な機能や資産を活用することが可能となります。roscppライブラリの詳細については、別途roscppのマニュアルや解説ドキュメントなどを参照するようにしてください。

.. toctree::
   :maxdepth: 3

   preparation
   step1
   step2
   step3
   step4
   step5
..   step6 リモート通信も説明する
