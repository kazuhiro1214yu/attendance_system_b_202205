# 勤怠システムを開発しよう！

これはセレブエンジニアサロンの教材で作られたサンプルアプリケーションです。

## 開発環境

* AWS Cloud9<br>
* Ruby<br>
* Rails<br>
* Git(HTTPSからSSH通信へ変更)2
* 
2022/5/30
勤怠チュートをベースに､勤怠B用にgit cloneを実施
この状態をベースに､bを進める

8/5
基本情報編集画面　未完了｡後で戻って作成予定｡
勤怠編集画面　残業指示と指示者をuiに追記済み｡あとはその2つをマイグレファイルに追記してマイグレリセット､seedで作成するところまで｡

8/15
勤怠画面に残業指示と指示者のカラムを追加｡それをatenndancesテーブルに追加するためにマイグレファイルを作成して追加を実行｡
しかし､実行がうまくいかず｡振り返り､そもそもこのカラム自体が不要であることを指示書で確認｡
マイグレファイルをdownしrmで削除｡元の状態に戻した｡

次
･管理ユーザーでheaderに基本､指定勤務時間の指定を作成｡
　→index.html.erbファイルの編集　remote:trueを削除することでモーダルウインドウをなくす

8/16
headerに基本情報編集のリンクを作成｡
リンク先に飛べず苦戦したが､｢edit_basic_info_user_path(user)｣と記載していたことが原因｡
｢user｣はcontrollerで定義していないので､正しくは｢edit_basic_info_user_path(current_user)｣だった｡
こちらに変更して無事リンク先へ移動､編集可能を確認済み｡


追加機能　7･8の実装
8/24　完了
･原因は恥ずかしながら､かんたんな記述ミスでした｡｡
原因
attendance.rbコントローラーの　update_one_monthアクション(patch)に
flashメッセージで｢@attendance.errors.full_messages｣の設定をしたが､
肝心の｢@attendance｣変数を定義しておらず｡｢attendance｣で変数設定していた｡
        attendance = Attendance.find(id)
        attendance.update_attributes!(item)
　　　　　→attendanceではなく､｢@attendance｣に変えて､解決!

2022/08/30
追加機能10の15分刻みも完了｡あとは追加機能1と9の2つ｡

hisasiburi