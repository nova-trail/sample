1. git初期設定
	A. gitのインストール
		https://gitforwindows.org/
	B. 初期設定
		git bashを開いて、
		a. ユーザー名の登録
		'''
		git config --global user.name USER
		'''
		b. メールアドレスの登録
		'''
		git config --global user.email EMAIL
		'''
		c. ユーザー名とメールアドレスのチェック
		'''
		git config --list
		'''
	C. リモートリポジトリの作成
		github管理画面(dashboard)で、create repositoryをクリック
		repository name：リポジトリの名前
		public / private：公開 / 非公開
		initialize this repository with：READ MEを設置したい場合
	D. ローカルリポジトリの作成
		git bashを開いて、
		a. ディレクトリの作成（C:\users\USER）
		'''
		mkdir github
		cd github
		mkdir sample
		cd sample
		'''
		これで、cd = c:\users\user\github\sample
		b. 作成したディレクトリをローカルリポジトリとする
		'''
		git init
		'''
		作成完了で
		'''
		initialized empty git repository in c:/users/user/github/sample/.git/
		'''
	E. ローカルリポジトリにコミットする
		a. サンプルでsample下にindex.htmlを作成
		''' index.html
		<!DOCTYPE html>
		<html>
		<head>
			<meta charset="utf-8">
		</head>
		 
		<body>
			Hello World！
		</body>
		</html>
		'''
		b. インデックスへindex.htmlを追加
		'''
		git add index.html
		'''
		c. インデックスに追加したファイルをコミットする
		'''
		git commit -m "コメント"
		'''
		d. ログを確認する
		'''
		git log
		'''
	F. リモートリポジトリにプッシュする
		a. ローカルリポジトリとリモートリポジトリを紐付ける
		'''
		git remote add origin https://github.com/USER/REMOTE_REPOSITORY.git
		'''
		b. gitへコミットしたものをプッシュする
		'''
		git push origin master
		'''
	G. ブランチ(開発フロー??)を作成する
		ブランチとは...ax, by, czはコミットID
				   ┌ ─ c4 ─ c5 ─ 
		a1 ─ a2 ─ a3 ─ a4 ─ a5 ─ 
			  └ ─ b3 ─ b4 ─ b5 ─ 
			タスクごとにコミット履歴を分岐させて作業することで、独立した環境でそれぞれのタスクを進めることができる
			例えば、a2の段階でアップデート計画を立てたならbへ分岐することで、aはメインバージョン、bはネクストバージョン
		a. ブランチを作成（sub1）
		'''
		git branch sub1
		'''
		b. ブランチの確認
		'''
		git branch
		'''
		正常なら
		'''
		* master
		  sub1
		'''
		c. ブランチにプッシュする
		仮運用をsub1ブランチとして、まずコミット
		'''
		git add index2.html
		git commit -m "コメント"
		'''
		次にプッシュ
		'''
		git push origin sub1
		'''
		d. ブランチからプルする
		最新の変更をダウンロードする
		まず、sub1へブランチを移動させる
		'''
		git checkout sub1
		'''
		次に、sub1でプルする
		'''
		git pull
		'''
		sub1のリポジトリが同期される
		e. ブランチのマージ
		ブランチ上での開発が完了したら、メインと合体させる
		masterブランチへ
		'''
		git checkout master
		'''
		sub1ブランチをmasterにマージ
		'''
		git merge sub1
		'''
		マージした内容をプッシュ
		'''
		git push origin master
		'''
		ブランチを削除する
		'''
		git branch -d sub1
		'''
		リモートリポジトリからも削除する
		'''
		git push --delete origin sub1
		'''
		