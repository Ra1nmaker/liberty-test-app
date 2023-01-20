# SimpleWebTest for Jararta 9.1

以下の機能が提供されています。

* serverName.jsp -- ホスト名とLibertyサーバー名を出力
* sessionTest.jsp -- HTTP セッションの確認
* showEnv.jsp -- 環境変数を表示
* showJavaProp.jsp -- Java のシステム・プロパティーを表示

war ファイルをダウンロードし、Libertyサーバーの apps ディレクトリーに配置します。
server.xml にアプリケーションを登録します。

server.xm の定義例

    <?xml version="1.0" encoding="UTF-8"?>
    <server>
        <featureManager>
            <feature>webProfile-9.1</feature>
            <feature>transportSecurity-1.0</feature>
        </featureManager>
        <httpEndpoint host="*" httpPort="9080" httpsPort="9443" id="defaultHttpEndpoint"/>
        <applicationManager autoExpand="true"/>
        
        <webApplication id="SimpleWebTest" name="SimpleWebTest" location="SimpleWebTest.war">
            <web-bnd>
                <env-entry name="serverName" value="${wlp.server.name}"/>
            </web-bnd>
            <web-ext enable-file-serving="true">
            </web-ext>
        </webApplication>
        
    </server>

以下の URL からアクセスします。
* http(s)://<ホスト名>:<ポート>/SimpleWebTest/

