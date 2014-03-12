ControlSystem
=============
<b> 第1部 - 制御システムについて</b>
---------

  1 - インシデント
---------
    ・47%が意図的なマルウェアの攻撃
    ・SCADAや産業制御システムのウィルス感染は減っているものの、
       攻撃の巧妙化・ステルス化が進み検知が難しくなっている
  
  2 - Stuxnetの概要
-------------

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

  <b>3 - SCADA</b>
---------
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

  <b>4 - 制御システムの認証</b>
----------

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

  <b>goals:</b>
---------

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
  <b>agenda:</b>
------
      
      1. SCADA&Controls system overview
      2. Risk to Control systems
      3. exploit Demo
      4. NERC security requirements
      5. SCADA Security "Chalk Talk"
      6. Defence,Detection,and Analysis

  <b>SCADA&Controls system overview</b>
------

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


  <b>Sensors and Field Devices:</b>
------
        
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

  <b>The RTU(遠隔端末ユニット):</b>
------

        
        - アナログ/個々の図りをデジタル情報に変換する
        - Contain analog and discrete inputs
          (直訳: アナログ/個々の入力を含んでいる)
        - 多数の通信オプションとデータプロトコルがある;w

        Also used for:
          - データの集中
          - プロトコルの通信

  <b>The IED(高性能な電子デバイス):</b>
------

        
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
      
  <b>The PLC:</b>
------

        
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

  <b>THE HMI:</b>
------

        人間と機械が情報をやり取りするための手段や、
        そのための装置やソフトウェアなどの総称。
        コンピュータにおけるHMIは特にユーザインターフェース
        (UI：User Interface)と呼ばれることが多い。

        人間オペレータにプロセスのデータを提示する機構であり、
        人間オペレータがプロセスを制御する際にもそれを経由する.
        HMIはSCADANoデータベースやソフトウェアプログラムとリンクしており,
        傾向をみるためのデータ、診断データ、保守手続きの予定などの管理情報
        ロジスティック情報、特定のセンサや機械の詳細図、
        エキスパートシステムによるトラブルシューティングなどが提供されてる

        1.コントロール,モニタリング,アラームするために使われる
        2.Can be software systems on a PC or 
          standalone systems like touch panels, 
          handheld devices, or panel-mounted displays
        3.(PLCs, IEDs,.etc)のようなデバイスやディスプレイからデータを集める.
          それをデータベースにデータを送る.

  <b>DCS:</b>
------


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

  <b>SCADA</b>
------

        1.産業制御システムの１つ。
        2.コンピュータによるシステム監視/プロセス制御が可能
        3.対象のプロセスは
          -製造
          -生産
          -発電
          -組み立て
        などを含む工業プロセスであり、連続モード/バッチ・モード/
        反復モード/離散モードなどがある

  
  <b>WHAT THE DIFFERENT SCADA WITH DCS!?</b>
------

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


        SCADAとDCSを混同する人が多いが、
        SCADAはプロセスの調整はするが、リアルタイムでの制御はしない
        実時間制御という話は、新たな通信技術によって高信頼な
        低レイテンシで高速な通信が広域で可能になるにつれて、焦点がぼやける

        1つのサイト全体や地理的に分散したシステムを集中的に関し制御する.
        遠方監視制御装置(RTU)やPLCが自動的に行う
        ホストのの制御機能は監督的な介入や優先的に限られることが多い.
        (ex.)
          PLCが冷却水の流量を制御する場合、
          SCADAはオペレータがりゅう料の設定値を変更したり
          警報発生条件(不正な流量や高温)を変更できるようにしたり、
          現在の状態をオペレータに対して表示し記憶する
          フィードバック制御ループはRTU/PLCで完璧.
          SCADAはそれらループの状態を監視する



  <b>Dedicated Lines</b>
-------

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


  <b>Power Line Communications</b>
------

        – Superimposed analog signal over a 50 or 60 Hz AC 
          system – Used in the electrical sector for command and control
       
        – Low data throughput (slow)
          Broadband over Power Line
        
        – Common ‘Last Mile’ solution – Regionally installed
        
        – Not used in rural settings


  <b>Wired Media - Copper / Fiber</b>
-------

        - IP/Ethernetとシリアルアプリの両方を使用

        - 大量の共有デバイス

        - セキュリティオプションが多い

        - 用意に情報を調べれる
  

  <b>Wireless: Radios and WiFi</b>
-------

        -Radio-

          1.一般的に使われている
          2.Spread spectrum or narrow band (???)
          3.ほとんどの工業につかわれる 
          4.低コストで簡単にインストールできる
          5.56kbのスピード

        -IEEE 802.11(WiFi)-

          1.極度に使われる
          2.チープ
          3.多数の認証技術が使われている
          4.多数の暗号技術が使われている


  <b>Wireless</b>
-------
      
        Microwave
          
          1.パイプライン制御システムや遠隔電気操作する場合に使う
          2.Large bandwidth compared to copper
            (???)
          3.Line of site limitations
            (直訳: サイト限界の線
          4.取り付けにコストが掛かる

        Cellular

          1.存在する携帯電話用のネットワークを使う
          2.携帯を送信機のように生成している


  <b>Protocols Lists</b>
-------

        試験対象のプロトコル

        1.Group 1~5まであって、 Group 1はEDSA 401~406で規定されている
        2.Group 2~5は、今後 ISASecure EDSA認証プログラムで用意されていく
        
        Group 1:
        |-----------------|
        |  IEEE 802.3     |
        |  (Ethernet)     |
        |  ARP            |
        |  IPv4           |
        |  ICMPv4         |
        |  TCP            |
        |  UDP            |
        |_________________|


        Group 2:
        |-----------------|
        |  BOOTP          |
        |  DHCP           |
        |  DNS            |
        |  NTP,SNTP       |
        |  FTP,TFTP       |
        |  HTTP           |
        |  SNMPv1-2       |
        |  Telnet         |
        |_________________|


        Group 3:
        |-----------------|
        |  HTTPS          |
        |  TLS            |
        |  Modbus/TCP     |
        |_________________|


        Group 4:
        |-----------------|
        |  IPv6           |
        |  OPC            |
        |  Ethernet/IP/CIP|
        |  PROFINET       |
        |  FFHSE4         |
        |  Selected       |
        |  wireless       |
        |  protocols/     |
        |        stacks   |
        |  with elements  |
        |  such as:       |
        |    -IEEE 802.11 |
        |    -ISA100.11a  |
        |    -WirelessHART|
        |_________________|


        Group 5:
        |-----------------|
        |  SNMPv3         |
        |  SSH            |
        |  Server         |
        |  OPC-UA         |
        |  MMS            |
        |  IEC            |
        |  61850          |
        |  SMTP           |
        |_________________|



  <b>Protocolの概要</b>
-------------


  <b>Fuzzing Summary</b>
-------------
    
    先述した通り、近年は「制御システムのオープン化」に傾向がある.

    メリット:
      
      1.異なるベンダー間での制御伊システムの通信が可能
        - システム構成の選択肢が増大
      2.情報システムとの接続
        - 情報の管理、リモート制御が可能

    デメリット:

      1.今までは独自のプロトコルを使っていたので,
        攻撃の難易度は高かったが,
        インターネットへの接続/汎用プロトコルの採用により,難易度の低下.


    ゆえに,プロトコルファジングの必要性が出てくる.
    EDSA認証適合ファジングツールの開発

    DUTに対しCRT(Communication Robustness Testing)をする.

    検査パターンの分類:

      1.ベースラインオペレーション
        - 対象プロトコルでの基本的な通信ができてることの確認(正常通信)

      2.ロバストネス
        - 不正な値をPDU(Protocol Data Unit)に設定し,DUTの堅牢性を検査
        
        - 不正な形式,矛盾,不正なサイズのPDUを送信.

      3.ロードストレス
        - DUTにストレスをかけてDUTの堅牢性を図る.(ex. DoS)

    現在はまだGroup2以降のEDSA認証規格が対応していないので、アップデートを待つ.




