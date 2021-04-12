ROSのインストール
=================

.. contents::
   :local:

.. highlight:: sh

ROSディストリビューションのインストール
---------------------------------------

ROSのディストリビューションがまだインストールされていない場合は、 `ROS.org <http://wiki.ros.org>`_ - `ROS/Installation <http://wiki.ros.org/ROS/Installation>`_ の記述に従ってインストールを行ってください。

なお、ROSのバージョンについては、Noetic Ninjemys (Ubuntu 20.04)、Melodic Morenia (Ubuntu 18.04)、Kinetic Kame (Ubuntu 16.04)での動作を確認をしています。

それぞれ以下のコマンド操作でROS環境をインストールできます。

.. http://wiki.ros.org/noetic/Installation/Ubuntu

**Ubuntu 20.04 (ROS Noetic Ninjemys) の場合** ::

  sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
  sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
  sudo apt update
  sudo apt install ros-noetic-desktop-full
  echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
  source ~/.bashrc
  sudo apt install python3-rosdep
  sudo rosdep init
  rosdep update

**Ubuntu 18.04 (ROS Melodic Morenia) の場合** ::

 sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
 sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
 sudo apt update
 sudo apt install ros-melodic-desktop-full
 echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
 source ~/.bashrc
 sudo apt install python-rosdep
 sudo rosdep init
 rosdep update

**Ubuntu 16.04 (ROS Kinetic Kame) の場合** ::

 sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
 sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
 sudo apt-get update
 sudo apt-get install ros-kinetic-desktop-full
 echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
 source ~/.bashrc
 sudo apt install python-rosdep
 sudo rosdep init
 rosdep update

.. note:: 上記のsourceコマンドはsetup.bash の内容を現在のシェルに反映させるためのもので、インストール（上記設定）直後に続けて同じシェルで作業する場合に必要となるものです。インストール後にあらためてシェルを起動する場合は、上記の設定によりsetup.bashの内容が反映されますので、このコマンドは必要ありません。

.. note:: apt-keyコマンドで取得する鍵には通常有効期限が設定されていて、期限が切れるとリポジトリへのアクセスなどができなくなってしまうようです。その場合は上記のapt-keyコマンドを再度実行し鍵を更新することで、リポジトリへアクセスできるようになります。

.. note:: Noeticの場合、上記コマンドでインストールしているrosdepのパッケージとして、他に "python3-rosdep2" というものもあるようです。こちらの方が新しいバージョンのようですが、この使用についてはまだ情報が少なく、既存のパッケージとうまく連携できるかよく分からないところがありますので、当面は python3-rosdep の方を使用した方がよいのではないかと思います。
	  

Catkin Toolsのインストール
--------------------------

ChoreonoidをROSで使う場合、ビルドツールCatkinの新しいバージョン ( `Catkin Command Line Tools <https://catkin-tools.readthedocs.io/en/latest/index.html>`_ 、通称Catkin Tools）を使用します。

Ubuntu 20.04の場合、以下のようにして必要なパッケージをインストールすることでCatkin Toolsを使えるようになります。 ::

 sudo apt install python3-osrf-pycommon python3-catkin-tools


Ubuntu 18.04、16.04の場合はPythonの環境が異なるため、インストールは以下のコマンドで行うことになります ::

 sudo apt install python-catkin-tools
