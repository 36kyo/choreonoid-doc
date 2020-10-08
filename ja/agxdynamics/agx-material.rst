
物理マテリアルの追加パラメータ
==============================

AGXDynamicsプラグインを利用時には以下の物理マテリアル(物性)を利用することができます。

.. contents::
   :local:
   :depth: 2

サンプル
--------

AGXDynamicsPluginのマテリアルのサンプルが以下にあります。
パラメータ値によって動作結果が異なることを確認することができます。

* choreonoid/samples/AGXDynamics/agxMaterialSample.cnoid

マテリアルの設定手順
--------------------

AGXSimulatorでリンク間の摩擦係数、反発係数などは、以下の手順で調整することができます。

1. マテリアルファイルにMaterial、ContactMaterialを記述
2. ボディファイルにマテリアルファイルで定義したMaterialを設定

.. _agx_material_file:
   
マテリアルファイル
------------------

マテリアルファイルは摩擦係数や反発係数などの物性を記述したリストファイルです。このファイルは材質(Material)について、同じまたは異なる材質の接触物性(ContactMaterial)を記述することができます。ここで定義した材質名をBodyファイルに記述することで、モデルに材質を設定することができます。

マテリアルファイルはワールドアイテムのプロパティに設定することで、読み込まれます。デフォルトでは ``choreonoid/share/default/materials.yaml`` が設定されており、自動的に読み込まれます。

.. code-block:: yaml

  materials:
    -
      name: Ground
      roughness: 0.5
      viscosity: 0.0
    -
      name: agxMat5
      density: 1.0

  contactMaterials:
    -
      materials: [ Ground, agxMat5 ]
      youngsModulus: 1.0e5
      restitution: 0.1
      spookDamping: 0.08
      friction: 0.416667
      surfaceViscosity: 1.0e-8
      adhesionForce: 100
      adhesivOverlap: 0.2
      frictionModel: [ iterative, direct ]
      contactReductionMode: reduceGeometry
      contactReductionBinResolution: 3


Materialパラメータの説明
------------------------

バルクマテリアル
~~~~~~~~~~~~~~~~

.. list-table::
  :widths: 10,7,4,4,75
  :header-rows: 1

  * - パラメータ
    - デフォルト値
    - 単位
    - 型
    - 意味
  * - density
    - 1000
    - kg/m3
    - double
    - 密度。リンクの質量、慣性テンソル、重心の自動計算に利用されます。
  * - youngsModulus
    - 4.0e8
    - Pa
    - double
    - ヤング率。リンク(剛体)の硬さを表します。値が小さいとリンク同士が侵入しやすくなります。
  * - viscosity
    - 0.5
    - \-
    - double
    - 反発粘性。反発粘性のペアが反発係数となります。
  * - spookDamping
    - 0.075
    - s
    - double
    - スプークダンパ。リンク同士の侵入の緩和(拘束条件を満たす)に利用します。
  * - poissonRatio
    - 0.3
    - \-
    - double
    - ポアソン比（2.27.0.0より非推奨）

サーフェスマテリアル
~~~~~~~~~~~~~~~~~~~~

.. list-table::
  :widths: 10,7,4,4,75
  :header-rows: 1

  * - パラメータ
    - デフォルト値
    - 単位
    - 型
    - 意味
  * - roughness
    - 0.5
    - \-
    - double
    - 表面粗さ。表面粗さのペアが摩擦係数となります。
  * - surfaceViscosity
    - 5e-09
    - \-
    - double
    - 表面粘性。接面方向に働く粘性です。表面粘性のペアがContactMaterialのsurfaceViscosityとなります。オイルなど濡れを表現する時に利用します。
  * - adhesionForce
    - 0.0
    - N
    - double
    - 粘着力。形状が接触している時に法線方向に粘着力が働きます。接着剤のような振る舞いをさせたい時に利用します。
  * - adhesivOverlap
    - 0.0
    - m
    - double
    - 粘着力有効距離。リンクの侵入量>有効距離となると粘着力が有効になります。

.. note::
  ContactMaterialが定義されているものについては、ContactMaterialのパラメータが利用されます。Materialのサーフェスマテリアルは利用されません。

.. _agx_wire_material:

ワイヤーマテリアル
~~~~~~~~~~~~~~~~~~

.. list-table::
  :widths: 10,7,4,4,75
  :header-rows: 1

  * - パラメータ
    - デフォルト値
    - 単位
    - 型
    - 意味
  * - wireYoungsModulusStretch
    - 6e10
    - Pa
    - double
    - 引張ヤング率
  * - wireSpookDampingStretch
    - 0.075
    - s
    - double
    - 引張スプークダンパ
  * - wireYoungsModulusBend
    - 6e10
    - Pa
    - double
    - 曲げヤング率
  * - wireSpookDampingBend
    - 0.075
    - s
    - double
    - 曲げスプークダンパ

.. _agx_contact_material_parameters:

ContactMaterialパラメータの説明
-------------------------------

.. list-table::
  :widths: 10,7,4,4,75
  :header-rows: 1

  * - パラメータ
    - デフォルト値
    - 単位
    - 型
    - 意味
  * - youngsModulus
    - 2.0e8
    - Pa
    - double
    - ヤング率
  * - restitution
    - 0.0
    - \-
    - double
    - 反発係数。0:完全非弾性衝突、1:完全弾性衝突
  * - spookDamping
    - 0.075
    - s
    - double
    - スプークダンパ
  * - friction
    - 0.5
    - \-
    - double
    - 摩擦係数
  * - secondaryFriction
    - -1.0
    - \-
    - double
    - 副方向摩擦係数。摩擦モデルにoriented_box、oriented_scaled_box、constant_normal_force_oriented_box、oriented_iterativeのいずれかを指定した場合に、secondaryFriction>=0で有効となります。
  * - surfaceViscosity
    - 1.0e-8
    - \-
    - double
    - 表面粘性係数。摩擦拘束に対するコンプライアンスです。
  * - secondarySurfaceViscosity
    - -1.0
    - \-
    - double
    - 副方向表面粘性係数。摩擦モデルにoriented_box、oriented_scaled_box、constant_normal_force_oriented_box、oriented_iterativeのいずれかを指定した場合に、secondaryFriction>=0で有効となります。
  * - adhesionForce
    - 0.0
    - N
    - double
    - 粘着力
  * - adhesivOverlap
    - 0.0
    - m
    - double
    - 粘着力有効距離
  * - frictionModel
    - [ default, default ]
    - \-
    - | string
      | string
    - | 摩擦モデル: default(iterative), iterative, box, scaled_box, oriented_box, oriented_scaled_box, constant_normal_force_oriented_box, oriented_iterative
      | ソルバ    : default(split), split, direct, iterative, direct_and_iterative

  * - contactReductionMode
    - default
    - \-
    - string
    - 接触点削減方式: default(reduceGeometry), reduceGeometry, reduceALL, reduceNone
  * - contactReductionBinResolution
    - 0
    - \-
    - uint8_t
    - 接触点削減ビン解像度。0の場合はAGXSimulatorアイテムのパラメータを利用します。
  * - primaryDirection
    - [ 0, 0, 0 ]
    - Unit vector
    - Vec3
    - 摩擦モデルorientedBox指定時の主要方向ベクトル

  * - referenceBodyName
    - \-
    - \-
    - string
    - 摩擦モデルorientedBox指定時の参照Body名
  * - referenceLinkName
    - \-
    - \-
    - string
    - 摩擦モデルorientedBox指定時の参照Link名

.. note::
  AGXDynamicsは動摩擦係数、静止摩擦係数の区別がありません。実際、値の差は10-20%程度であり、ほとんどの状況では気にしなくて良いとの考えです。

.. note::
  摩擦モデルについてはChoreonoid 1.7で利用可能なものから追加されています。また、iterative, constant_normal_force_oriented_box については、それぞれ1.7までの cone, orientedBox に対応します。

.. _not_defined_contact_material:

ContactMaterialが定義されていない場合
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| 全てのMaterialのペアの物性がContactMaterialに記述されているのが望ましいのですが、難しいと思います。
| ContactMaterialが設定されていない場合にはMaterialに記述されているパラメータついて以下の式に従って値を算出します。
| Materialにもパラメータが設定されていない場合にはデフォルト値が適用されます。

* youngsModulus = (m1.youngsModulus * m2.youngsModulus)/(m1.youngsModulus + m2.youngsModulus)
* restitution = sqrt((1-m1.viscosity) * (1-m2.viscosity))
* spookDamping = max(m1.spookDamping, m2.spookDamping)
* friction = sqrt(m1.roughness * m2.roughness)
* surfaceViscosity = m1.surfaceViscosity + m2.surfaceViscosity
* adhesionForce = m1.adhesionForce + m2.adhesionForce


ボディファイルのマテリアルの記述方法
------------------------------------

| ボディファイルのマテリアルの記述方法について説明します。
| 重心、質量、慣性はmassTypeで直接指定か密度を使った自動計算を選択することができます。
| デフォルトはmassです。

.. code-block:: yaml

  massType: mass             # 直接指定
  massType: density          # 密度を使った自動計算

| また、材質はmaterialでマテリアルファイルに定義されているマテリアルか直接指定を選択することができます。
| デフォルトはマテリアルファイルに定義されているDefaultまたはdefualtです。

.. code-block:: yaml

  material: Default          # デフォルトマテリアル
  material: Ground           # マテリアル
  material: useLinkInfo      # 直接指定

以下は記述例です。

.. note::
  現在のところ、densityを使った重心、質量、慣性テンソルの計算結果はAGXDynamics内部で保持しており、ChorenoidのリンクやGUIから取得、確認することはできません。

従来記法
~~~~~~~~

* 従来のChoreonoidの記法です
* 記載されいているcenterOfMass, mass, inertiaを利用します
* Materialはdensityを除いて、defaultとなります
* ContactMaterialはdefault vs xxxxx となります

.. code-block:: yaml

  links:
    -
      name: box1
      centerOfMass: [ 0, 0, 0 ]
      mass: 1.0
      inertia: [
        0.02, 0,    0,
        0,    0.02, 0,
        0,    0,    0.02 ]

マテリアルファイルの利用(推奨)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* densityを含むマテリアルファイルに記述されたパラメータを使います

.. code-block:: yaml

  links:
    -
      name: box1
      massType: density     # 密度を利用して重心、質量、慣性テンソルを自動計算する
      material: steel       # マテリアルファイルのsteelを利用
      density: 1.0          # densityが記述されている場合はsteelのdensityを
                            # オーバライドして、直接記述されているものを利用します

従来記法+マテリアルリストの利用(推奨)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* massType: massで直接記述されている重心、質量、慣性テンソルを利用します
* その他のマテリアルパラメータはマテリアルファイルのsteelを利用します

.. code-block:: yaml

  links:
    -
      name: box1
      massType: mass      # 直接記述された重心、質量、慣性テンソルを利用する
      centerOfMass: [ 0, 0, 0 ]
      mass: 1.0
      inertia: [
        0.02, 0,    0,
        0,    0.02, 0,
        0,    0,    0.02 ]
      material: steel     # マテリアルファイルのsteelを利用


直接記述(非推奨)
~~~~~~~~~~~~~~~~

* material: useLinkInfoとするとボディファイルに記述されたMaterialのパラメータを利用することができます
* :ref:`not_defined_contact_material` に従ってContactMaterialの値が計算されます

.. code-block:: yaml

  links:
    -
      name: box1
      massType: density
      material: useLinkInfo
      density: 1.0
      youngsModulus:
      poissonRatio:
      viscosity:
      spookDamping:
      roughness:
      surfaceViscosity:
      adhesionForce:
      adhesivOverlap:


全記述(非推奨)
~~~~~~~~~~~~~~

* すべてが記述されている場合です
* どのパラメータが利用されているのか判別がしずらいのでおすすめしません

.. code-block:: yaml

  links:
    -
      name: box1
      massType: density               # 密度を利用して重心、質量、慣性テンソルを自動計算する
      centerOfMass: [ 0, 0, 0 ]
      mass: 1.0
      inertia: [
        0.02, 0,    0,
        0,    0.02, 0,
        0,    0,    0.02 ]
      material: steel                 # materialリストを利用
      density: 1.0                    # 記述されたdensityを利用
      youngsModulus:                  # 以下は使用されない
      poissonRatio:
      viscosity:
      spookDamping:
      roughness:
      surfaceViscosity:
      adhesionForce:
      adhesivOverlap:
