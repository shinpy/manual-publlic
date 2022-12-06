## BaseDBへのsnmpインストール手順（2022/12/6時点）  

#### 管理者権限にスイッチ  
```$ sudo -i```  

#### repoをダウンロード  
```# wget https://swiftobjectstorage.ap-tokyo-1.oraclecloud.com/v1/dbaaspatchstore/DBaaSOSPatches/oci_dbaas_ol7repo -O /tmp/oci_dbaas_ol7repo```  

#### versionlockファイルをダウンロード  
```# wget https://swiftobjectstorage.ap-tokyo-1.oraclecloud.com/v1/dbaaspatchstore/DBaaSOSPatches/versionlock_ol7.list -O /tmp/versionlock.list```  

#### repoファイルをコピー（該当ファイルがなければスキップ）  
```# mv /etc/yum.repos.d/public-yum-ol7.repo  /etc/yum.repos.d/public-yum-ol7.repo.org```  
※ 該当ファイルがなければスキップ）  
```# cp /tmp/oci_dbaas_ol7repo /etc/yum.repos.d/ol7.repo```  

#### versionlock設定ファイルを更新  
```# cp /etc/yum/pluginconf.d/versionlock.list /etc/yum/pluginconf.d/versionlock.list-`date +%Y%m%d```  
```# cp /tmp/versionlock.list /etc/yum/pluginconf.d/versionlock.list```  
※overwriteを許可（「y」を入力）  

#### 必要なパッケージをインストール（例：snmpの場合）  
```# yum install net-snmp```  
```# yum install net-snmp-utils```

#### パッケージインストール完了後実施（設定を元に戻す）  
```# cp /etc/yum/pluginconf.d/versionlock.list-`date +%Y%m%d` /etc/yum/pluginconf.d/versionlock.list```  
※overwriteを許可（「y」を入力）  
```# rm /etc/yum.repos.d/ol7.repo```  
※remove確認（「y」を入力）  
