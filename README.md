# Let's Chatのインストール手順

## Python2.7をインストール
1. 下記サイトから2.7をダウンロード、インストールする。
 > https://www.python.org/

## MongoDBをインストール
1. 下記サイトから最新のCommunityEditionをダウンロード、インストールする。
 > https://www.mongodb.org/downloads

1. MongoDBが使用するディレクトリを作成する。

  ~~~bash
  $ mkdir /opt
  $ mkdir /opt/mongodb
  $ mkdir /opt/mongodb/data
  $ mkdir /opt/mongodb/log
  ~~~

1. インストールディレクトリに設定ファイルを作成する。

  ~~~bash
  $ cd "Program Files/MongoDB/Server/3.2/bin/"
  $ vim mongodb.conf
  ~~~

  mongodb.confの内容

  ~~~
  storage:                                     
    dbPath: C:\opt\mongodb\data                
    engine: wiredTiger                         
    journal:                                   
      enabled: true                            

  systemLog:                                   
    destination: file                          
    path: C:\opt\mongodb\logs\mongodb.log      

  net:                                         
    bindIp: 127.0.0.1                          

  processManagement:                           
    windowsService:                            
      serviceName: MongoDB                     
      displayName: MongoDB                     
      description: MongoDBのサービス                
  #      serviceUser: <string>                 
  #      servicePassword: <string>             
  ~~~

1. MongoDBをサービス登録する。

  ~~~bash
  $ "Program Files/MongoDB/Server/3.2/bin/mongod.exe" --config "Program Files/MongoDB/Server/3.2/bin/mongodb.conf" --install
  ~~~

1. タスクマネージャのサービスタブからMongoDBを起動する。

## Node.jsをインストール
1. 下記サイトから最新のWindowsインストーラをダウンロード、インストールする。
 > https://nodejs.org/en/download/

## Let's Chatをインストール
1. 適当なインストールディレクトリが無ければ作成し、GitHubからcloneする。

  ~~~bash
  $ mkdir /opt
  $ git clone https://github.com/sdelements/lets-chat.git
  ~~~

1. インストールする。

  ~~~bash
  $ cd lets-chat
  $ npm install
  ~~~

1. サービス化する。

  ~~~bash
  $ npm install winser
  $ node_modules\\.bin\\winser -i --startcmd node
  ~~~
