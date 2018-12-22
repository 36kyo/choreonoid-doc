
About items used with OpoenRTM plug-in
=======================

The OpenRTM plug-in uses the following items.

RTSystem Item
----------------------------

| In OpenRTM, the RT function element is called an RT component (RT-Component: RTC), and a robot system (RT system) is constructed using multiple RTCs.
| "RT system item" is a project item for managing the RT system.It is used to manage the components (RTC) of the robot system on the Choreonoid.

The following properties are additionally available for RT system items.

.. .. tabularcolumns:: |p{3.5cm}|p{11.5cm}|

.. list-table::
  :widths: 15,12,4,75
  :header-rows: 1

  * - Parameters
    - Default value
    - Type
    - Detail
  * - Auto connection
    - True
    - bool
    - Specify whether to automatically execute the connection between the RTCs that make up the RT system when reading items.
  * - Vendor name
    - \-
    - string
    - Set the name of the vendor that created the target RT system.The value set here is used as "VendorName" of RTSProfile when saving the system.The default value can be specified in "Preferences".
  * - Version number
    - \-
    - string
    - Set the target RT system version number.The value set here is used as "Version" of RTSProfile when saving the system.The default value can be specified in "Setting screen".
  * - Profile save destination
    - \-
    - string
    - With the OpenRTM plug-in, information on the RT system is saved using RTSProfile format (format standardized by RT middleware).In this case, specify the save destination of RTSProfile.
  * - Polling Cycle
    - 500
    - int
    - Set the cycle for checking the state of the RTC that constitutes the RT system.The unit is ms.
  * - HeartBeat Period
    - 500
    - int
    - Available in OpenRTM-aist-1.2.0 or later.Sets the heartbeat reception cycle for confirming the presence of RTC.The unit is ms.If the heartbeat signal does not arrive within this cycle, it is judged that some error has occurred in the target RTC.

ControllerRTC Item
----------------------------

It is an item for defining the RTC for controlling the system defined by the RT system item.We will control the target system according to instructions from Choreonoid.

For the controller RTC item the following properties are additionally available:

.. .. tabularcolumns:: |p{3.5cm}|p{11.5cm}|

.. list-table::
  :widths: 15,12,75
  :header-rows: 1

  * - �p�����[�^
    - �^
    - �Ӗ�
  * - RTC���W���[��
    - string
    - ���ۂɎg�p����R���g���[��RTC�̖��̂�ݒ肵�܂��B�v���p�e�B�ҏW���Ƀt�@�C���I���_�C�A���O���\������܂��̂ŁA�g�p����R���g���[��RTC��I�����Ďw�肷�邱�Ƃ��\�ł��B
  * - �x�[�X�f�B���N�g��
    - string
    - �g�p����R���g���[��RTC�����݂���f�B���N�g����ݒ肵�܂��B
  * - RTC�C���X�^���X��
    - string
    - �R���g���[��RTC�����ʂ��邽�߂̃C���X�^���X����ݒ肵�܂��BOpenRTM�ł͓����^��RTC�𕡐��N�����邱�Ƃ��\�ł��B���̂悤�ȏꍇ�ɁA���ۂɎg�p����R���g���[���̃C���X�^���X�����ʂ��邽�߂Ɏw�肵�܂��B
  * - ���s�R���e�L�X�g
    - string
    - �R���g���[��RTC�Ŏg�p������s�R���e�L�X�g���w�肵�܂��B�I���\�Ȏ��s�R���e�L�X�g�̎�ނ́A�g�p���Ă���OpenRTM-aist�̃o�[�W�����ɂ���ĈقȂ�܂��̂ŁA�ڍׂ�OpenRTM-aist�̃T�C�g���Q�Ƃ��Ă��������B
  * - ���s���g��
    - int
    - �R���g���[��RTC�̎��s�������w�肵�܂��B




BodyIoRTC Item
----------------------------



RTC Item
----------------------------


BodyRTC Item (Deprecated)
----------------------------

