
1.Homebrewインストール

1-1.Homebrewの公式サイトへブラウザでアクセス
https://brew.sh/index_ja.html

1-2.公式サイトへ記載されているコマンドをターミナルで実行
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2.license-plistのインストール
brew install mono0926/license-plist/license-plist

3.Settings.bundleの生成

3-1.カレントディレクトリを移動
Cartfileなどがあるパスへカレントディレクトリを移動

例：
cd *****

3-2.Settings.bundleをコマンドで生成
license-plist --output-path ./iOSLicensePlistSample/Settings.bundle

--output-path：出力先

3-3.Root.plistを作成
以下の内容を記載したRoot.plistを作成し、Settings.bundle直下に配置する

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>PreferenceSpecifiers</key>
	<array>
		<dict>
			<key>Type</key>
			<string>PSChildPaneSpecifier</string>
			<key>Title</key>
			<string>Licenses</string>
			<key>File</key>
			<string>com.mono0926.LicensePlist</string>
		</dict>
	</array>
	<key>StringsTable</key>
	<string>Root</string>
</dict>
</plist>

4.プロジェクトに追加

4-1.追加
生成されたSettings.bundleをXcodeProjectに追加

5.確認
iOSの設定にライセンスが追加されているのを確認