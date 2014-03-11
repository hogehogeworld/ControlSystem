ControlSystem
=============
<b> 第1部 - 制御システムについて</b>

  1 - インシデント

    ・47%が意図的なマルウェアの攻撃
    ・SCADAや産業制御システムのウィルス感染は減っているものの、
       攻撃の巧妙化・ステルス化が進み検知が難しくなっている
  
  2 - Stuxnetの概要

    class Stuxnet:
 
    def attacked():
        while:
          1.USBメモリやインターネットを通じて情報システムへの侵入
          2.システムの脆弱性を利用し、権限昇格、システム環境内部でウィルスの拡散実行
          3.バックドアを作成し、外部指令サーバ(C&Cサーバ）や80番ポート(HTTP)を
            介し通信し、ウィルスの増強化
        4.組織内のネットワークに入り、制御システムへの侵入
        5.制御システム上にある装置に対する攻撃実行

      def Func_of_Stuxnet():
        1. 500 KBのプログラムで4000弱の機能を持っている
        2. 複雑/オブジェクト指向
        3. 複数のゼロデイを利用
        4. 2つのrootkitを使用し、制御システムをターゲットとしている
        5. Windowsに詳しい、制御システムであるWinCC/Step7についても詳しい

    2 - Stuxnetが出た後の背景

      Stuxnet が出現するまでは、汎用製品や標準プロトコルで構成されている情報システム
      が制御システムのオープン化(汎用製品や標準プロトコルの 利用)が進展しており
      システム環境に変化が起きている。

      制御システムの端末の9割以上がWindows系を利用している
      
      外部との接触
        ・Device
            USB    73.1%
            CD/DVD 51.7%
        ・Network
            Ethernet 60%
            ・Response to Outside  36.8%
                ・Remote Maintenance  55.0%
                ・Internet  43.0%
        
      個別攻撃手法の回避法
        ・システム設計時におけるネットワーク設計(外部との隔離や接続ルートの明確化) 
        ・外部との通信における接続先のフィルタリング 
        ・外部との接続点における通信の監視、制御機構

  3 - SCADA

      2010 ~ 2016年で 46億ドル ~ 70億ドルにまでSCADA市場が成長する見込み。
      ゆえに、サイバセキュリティを強くする必要がある

      TCP/IPベースのSCADA-Networkに対する産業用FirewallやVPNソリューション
        の開発により脅威リスクから対策を焦点を当てている

      -=-=-勉強会01-=-=-
        threat = persons,circumstance,of loss or damage
        vulnerability = weakness of that can be exploited
        Consequence = successful attack
        Risk = threat * vulnerability * Consequence

        Typical Attack
          • Target Identification / Selection
            How accessible is your company??
                Internet, media, etc. presence(存在)
              どれぐらいの情報で会社のベンダに入られるのか.
              どんなかんじだとターゲットとして望ましいか
          • Reconnaissance
            DumpsterDiving
            Asset/service discovery, network connectivity
          • System Access
          • Keeping Access
          • Covering the Tracks

  4 - 制御システムの認証

      認証-
        1.セキュリティ製品を開発してるベンダのプロセスを評価
        2.セキュリティ製品のセキュリティ機能実装レベル、通信レベルのテスト

      製品の認証-
        ISA-99と呼ばれる制御システムのセキュアかの評価する
          ISASecure Embedded Device Security Assurance(EDSA)について紹介…
        ~EDSA(組み込みデバイスセキュリティ保証)は次の3つの階層から成り立つ~
          ・SDSA(Software Development Security Assessment):
              システマティックセキュリティ評価
          ・FSA(Functional Security Assessment):
              実装レベルの評価
          ・CRT(Communication Robustness Testing):
              レイヤ4までの通信レベルのテストで、プロトコルテストスイーツで
              5つのグループ分けになってる
             通信プロトコルの検証として、
              Ethernet/ARP/IPv4/ICMPv4/UDP/TCPとなっている

      欧州での取り組み
        話し合って,
        ・ グローバルな課題としての取り組み
        ・ 官民連携が不十分
        ・ サイバーセキュリティ戦略策定の必要性
        ・ 情報共有促進
        ・ ガイダンスの不足、経験も不足 等々
        という課題が出た.
      プロトコルの最低限のセキュリティレベルを上げるために、
      IPv6,DNSSecへの対応を試みる.
      グラウンドコンピューティング/診断システム/無線ネットワーク/
      スマートグリッド/SCADA/センサネットワークなどの研究開発に力を入れる.

      センサとZigBeeとISA100.11aを組み合わせた無線センサネットワークから
      直接SCADAに膨大なデータを送るのではなく、分析データを投げることで、
      早期に自体を把握できる


<strong>勉強会02<a href="http://www.inl.gov/scada/training/advanced_scada.shtml">(Hands-on Control System Cyber Security Training)</a></strong>

    def goals:
      1.サイバーセキュリティと制御システムがどのような関係にあるかにおいて
      重要な論点を理解すること
      2.次のようなメソッドを学ぶ
        - 制御システムの環境で脆弱性発見/解析
          1.ネットワークデザイン
          2.OS
          3.Critical communications paths
            (直訳: 危険な通信経路)
          4.アプリケーション
        - Apply contemporary security mitigation strategies to control systems
          (直訳:現代セキュリティミティゲーションを制御システムへ適応)

    def agenda:
      1. SCADA&Controls system overview
      2. Risk to Control systems
      3. exploit Demo
      4. NERC security requirements
      5. SCADA Security "Chalk Talk"
      6. Defence,Detection,and Analysis

    def SCADA&Controls system overview
          
          I/O
        |---------------|
        | Meters        |
        | Sensors       |
        | Field Devices |
        | ______________|

              |
              V
          Remote
        |---------------|
        | PLC           | PLC – Programmable Logic Controller
        | IED           | IED – Intelligent Electronic Device
        | RTU           | RTU – Remote Terminal Unit or Remote Telemetry Unit
        | Controller    |
        | ______________|

              |
              V
          Communications
        |---------------|
        | FEP           | FEP / Protocol Pre-processor – Front End Processor
        | Protocols     |
        | Wired         |
        | Wireless      |
        | ______________|

              |
              V
          Master
        |---------------|
        | SCADA         | SCADA – Supervisory Control and Data Acquisition
        | HMI           | HMI / Operator Console – Human Machine Interface
        | EMS           | EMS – Energy Management System
        | DCS           | DCS – Distributed Control System
        | ______________|

      def Sensors and Field Devices:
        1.Discrete Sensors
          - 開けるか閉じるかで状態を指摘する.
            High-スイッチ/Low-スイッチ
        2.Analog Sensors
          -  Convert continuous parameters such as 
              temperature or flow to analog signals such as 4-20mA or 0-10V
          - (直訳:
              気温や並のような連続したパラメータを4-20mA/0-10vのような
              アナログなシグナルに変換する
          -  To get field information into the control system, 
              the electric signals must be digitized. 
              This is done using equipment such as RTUs, PLCs, IEDs
          -  (直訳:
              現場の情報を制御システムに変換するには、
              電気信号をデジタル化する必要がある.
              これをするには、RTUs/PLCs/IEDsのような装置を使う.

      def The RTU(遠隔端末ユニット):
        - アナログ/個々の図りをデジタル情報に変換する
        - Contain analog and discrete inputs
          (直訳: アナログ/個々の入力を含んでいる)
        - 多数の通信オプションとデータプロトコルがある;w

        Also used for:
          - データの集中
          - プロトコルの通信

      def The IED(高性能な電子デバイス)
        
        - 近代のマイクロプロセッサが搭載されたコントローラ

        - 内蔵されてるもの
          -I/O
            ひとつのIEDで数百個~数千個のデータポイントを持つことができる
            (What is Data Points?)
          -通信
            IEDはしばしばEthternetベースのプロトコルで通信する
            あまり必要としないらしいが
        - Other Features
          - 論理式が組み込まれてる
          - ユーザがデータマップ通信の設定が変更可能
            (Wthat is Data map?)
          - Pointでイベントは正確に記憶できる
          - コンフィグは遠隔で設定できる
      
      def The PLC:
        
        PLCsは中断機の代わり.
        リレー回路の代替装置として開発された制御装置である。 
        シーケンスとも呼ばれている
        リレー回路の代替装置として開発された制御装置である。
        工場などの自動機械の制御に使われるほか、
        エレベーター・自動ドア・ボイラー・テーマパーク
        の各種アトラクションなど、身近な機械の制御にも使用されている。

        最近のPLCは次のようなことにも使われる.

        1.ネットワーク
        2.遠隔でプログラム
        3.組み込みのPCによりマージできるようにする
        4.{I/O , Web , FTP , SNMP}サーバができる
        5.ユニバーサルプログラミング
        (What is Universal Programming)
        6.ほとんどのPLCは最小限のセキュリティが備わっている


      def THE HMI

        人間と機械が情報をやり取りするための手段や、
        そのための装置やソフトウェアなどの総称。
        コンピュータにおけるHMIは特にユーザインターフェース
        (UI：User Interface)と呼ばれることが多い。

        1.コントロール,モニタリング,アラームするために使われる
        2.Can be software systems on a PC or 
          standalone systems like touch panels, 
          handheld devices, or panel-mounted displays
        3.(PLCs, IEDs,.etc)のようなデバイスやディスプレイからデータを集める.
          それをデータベースにデータを送る.

      def DCS

        1.分散制御システムは中央制御パネルを持っており、
          他の制御システムの集まりも含める.
        2.一般的には、石油、ガス、化学、水、汚染水を見つけるシステム
        3.進歩したプロセス制御.

        4.物理的マシンはPLCと似ている.
          – Rack and slot convention
          – Redundant processors on UPS backup power 
          – Built for real-time control

        5.通信
          – Proprietary backbone protocols
          – Communications with other systems primarily for ALARMING

        6.信頼性
          - DCSに対する信頼性は99%以上.
          - Industrial hardened equipment
            (直訳: 工業的図地金入り設備

      WHAT THE DIFFERENT SCADA WITH DCS!?

        – The key word in SCADA is “Supervisory.” This indicates that 
          decisions are not directly made by the system. Instead, the 
          system executes control decisions based on control parameters 
          by operators or management. SCADA systems are typically 
          deployed across large geographical areas (eg. - electric grid)
        
        - 重要になってくるのは,SCADAは監視用だということ.
          この表現はシステムに寄って直接決まっているわけではない.
          そうではなく,システムはオペレータかマネジメントによって
            制御パラメータを基に制御の決定を実行する.
          SCADAシステムは元々広範囲で活用/配備されている.

        
        – DCS provides real-time monitoring and control of a given process 
          within a plant. All major components of the system are usually 
          confined to one or several close by facilities (eg. - refinery)
        
        - DCSは実時間のモニタリングと大型機械の内部で与えられたプロセスの
            制御を提供する(??)
          システムのすべての主要な要素はたいてい、
            ひとつか数個の設備によって限られている.(???)

        – As technology advances, the terms are getting blurry. You will 
          quite often hear policy makers refer to “SCADA” when they are 
          really referring to another type of Industrial Control System.

        - 技術が進歩するとき、専門用語というものは曖昧になってくる.
          かなり頻繁にSCADAを参照する、他のICSをを言いたいとき(???)

      def Dedicated Lines:

        • More secure than leased lines
          
          - leased linesより安全.

        • High installation costs

          - 取り付けにコストがかかる.

        • Lower recurring costs
          
          - 安く繰り返し使える.

        • Lines aren’t governed by a third party

          - Linesは3rd Partyによってうんようされてない

        • Primary installations
        – May be Isolated systems – Serial communications

      def Power Line Communications:


