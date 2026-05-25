# Spotify Hotkey Saver

[日本語](#日本語) / [English](#english)

![Spotify Hotkey Saver preview](https://raw.githubusercontent.com/elqxti1e/SpotifyHotkeySaver-Releases/main/assets/spotify-hotkey-saver-preview.png)

## 日本語

Spotify Hotkey Saver は、Spotify を前面に表示しなくても、キーボードショートカットでプレイリストに保存、再生／停止、前後のスキップを行える Windows 常駐アプリです。

特殊なハードウェア、デバイスは不要です。作業中、ゲーム中、ブラウザ操作中でも、Spotify をバックグラウンドに置いたまま操作できます。必要に応じて、現在再生中の曲を確認できる小型オーバーレイも表示できます。

Spotify 認証には OAuth 2.0 の PKCE 方式を使用します。利用者ごとに Spotify Developer Dashboard で自分用のアプリを作成し、その Client ID を本アプリの Settings に設定します。Client Secret は使用しません。

> [!IMPORTANT]
> Always on または Game HUD を使用している場合は、v1.3.1 以降へのアップデートをおすすめします。以前のバージョンでは、これらの表示モードを長時間使用した場合にSpotify APIの利用制限に達しやすくなることがありました。

### 主な機能

* `Ctrl + Alt + S` で、現在再生中の曲を `Playlist #1` に保存
* `Playlist #1/#2/#3` の最大3つの保存先と、それぞれの保存ショートカット
* グローバルショートカットによる再生／停止、前の曲、次の曲の操作
* Spotify を前面に表示しないバックグラウンド操作
* トレイアイコンからの保存、再生／停止、前後スキップ、オーバーレイ切り替え
* ジャケット画像、曲名、複数アーティスト名、再生進行状況を表示する小型オーバーレイ
* オーバーレイ内の Save／前へ／再生・停止／次へボタン
* 複数の保存先がある場合、オーバーレイの Save から保存先を選択
* オーバーレイの移動、固定比率リサイズ、色、文字色、透明度の調整
* ゲーム中に使いやすい、半透明でクリックを通す Game HUD モード
* Always on / Game HUD 中も、Spotifyへのアクセスを抑えながら曲変更をすばやく反映
* 長い曲名・アーティスト名のスムーズなスクロール表示
* すでに保存済みの曲をもう一度保存しようとした場合の控えめなオーバーレイ表示
* 保存成功時の通知音オン／オフ
* Windows DPAPI による Spotify トークンのローカル暗号化保存

### ダウンロード

最新版は、公開リリース用リポジトリからダウンロードできます。

[https://github.com/elqxti1e/SpotifyHotkeySaver-Releases/releases](https://github.com/elqxti1e/SpotifyHotkeySaver-Releases/releases)

リリースページから `SpotifyHotkeySaver.zip` をダウンロードし、任意の場所に展開してください。展開後、次のファイルを実行します。

```text
dist/SpotifyHotkeySaver.exe
```

`dist/Assets/` フォルダは、実行ファイルと同じ場所に置いたままにしてください。フォントや通知音などの同梱ファイルを読み込むために必要です。

### 動作環境

* Windows 11
* Spotify アカウント
* 自分が編集できる Spotify プレイリスト
* 自分で作成した Spotify Developer アプリ

配布版は self-contained 形式です。.NET Runtime や .NET SDK を別途インストールする必要はありません。

本アプリは Spotify Premium での利用を前提にしています。

Spotify Free アカウントでも、現在再生中の曲を取得して編集可能なプレイリストへ保存する機能は利用できる場合があります。ただし、再生／停止、前の曲、次の曲などの再生操作は Spotify Web API の Premium 向け機能のため、Free アカウントでは利用できません。

### 初期設定

1. `SpotifyHotkeySaver.exe` を起動します。
2. Settings 画面が自動で開かない場合は、トレイアイコンから Settings を開きます。
3. `Open Dashboard` を押して Spotify Developer Dashboard を開きます。
4. Spotify Developer Dashboard で新しいアプリを作成します。
5. 本アプリの Settings で `Copy Redirect URI` を押します。
6. コピーした Redirect URI を Spotify Developer アプリの設定に追加します。
7. Spotify Developer アプリの Client ID をコピーします。
8. 本アプリの `Spotify Client ID` に Client ID を貼り付けます。
9. `Playlist #1` に、保存先プレイリストの URL または ID を入力します。
10. `Save & Login` を押します。
11. ブラウザで Spotify 認証を許可します。

`Playlist #2` と `Playlist #3` は任意です。`Refresh playlists` で取得できるプレイリストは `Choose` から選択できます。共同制作プレイリストを保存先にする場合は、URL または ID を直接入力してください。Spotify API から詳細を取得できる場合は、プレイリスト名と製作者名が自動で補完されます。

初期設定の Redirect URI は次のとおりです。

```text
http://127.0.0.1:43879/callback
```

`localhost` ではなく、`127.0.0.1` を使用してください。

Client Secret は不要です。本アプリには Client Secret を入力する項目もありません。

### Spotify Developer アプリの設定

Spotify Developer Dashboard:

[https://developer.spotify.com/dashboard](https://developer.spotify.com/dashboard)

追加する Redirect URI:

```text
http://127.0.0.1:43879/callback
```

本アプリが要求する Spotify scope:

```text
user-read-currently-playing
user-modify-playback-state
playlist-modify-private
playlist-modify-public
playlist-read-private
playlist-read-collaborative
```

Spotify Developer アプリが Development Mode の場合、利用できる Spotify アカウントが制限されることがあります。通常利用では、利用者ごとに自分用の Spotify Developer アプリを作成し、Client ID を設定してください。

### 標準ショートカット

| 操作 | ショートカット |
| --- | --- |
| Playlist #1 に保存 | `Ctrl + Alt + S` |
| Playlist #2 に保存 | `Ctrl + Alt + 1` |
| Playlist #3 に保存 | `Ctrl + Alt + 2` |
| 次の曲 | `Ctrl + Alt + Right` |
| 前の曲 | `Ctrl + Alt + Left` |
| 再生／停止 | `Ctrl + Alt + Space` |
| オーバーレイ切り替え | `Ctrl + Alt + O` |
| Game HUD 切り替え | `Ctrl + Alt + G` |

ショートカットは Settings から変更できます。

`Playlist #2` と `Playlist #3` が未設定の場合、それぞれの保存ショートカットは登録されません。

#### ショートカットの制限

* `F12` は予約キーのため使用できません。
* 同じショートカットを複数の操作に割り当てることはできません。
* 他のアプリが同じショートカットを使用している場合、登録に失敗することがあります。

### トレイメニュー

トレイアイコンを右クリックすると、次の操作を実行できます。

* Save Current Track
* Play/Pause
* Previous Track
* Skip Next
* Overlay on/off
* Settings
* Re-login Spotify
* Open Logs
* Exit

オーバーレイのオン／オフを切り替えた場合、オフにする前の表示モードを記憶します。

### オーバーレイ

オーバーレイには、現在再生中の曲情報と操作ボタンを表示できます。

表示内容:

* ジャケット画像
* 曲名
* アーティスト名
* Save ボタン
* 前へ／再生・停止／次へボタン
* 再生進行バー

保存先が1つだけ設定されている場合、Save ボタンはそのまま保存します。保存先が複数ある場合は、オーバーレイと同じ見た目の小型ポップアップから保存先を選択できます。

操作:

* オーバーレイの通常部分をドラッグして移動
* 右下角をドラッグして固定比率でリサイズ

表示モード:

* Off: 操作してもオーバーレイを表示しません。
* Show on action: 保存や再生操作のあとにオーバーレイを表示します。
* Always on: 常に現在の曲を表示します。
* Game HUD: 半透明のオーバーレイを常に表示します。クリックはオーバーレイを通過するため、ゲームや他のアプリの操作を邪魔しにくくなります。

設定できる見た目:

* アクセントカラー
* 背景色
* 文字色
* 透明度
* 見た目のリセット

`Reset appearance` は、色と透明度のみを初期値に戻します。オーバーレイの位置やサイズはリセットしません。

すでに保存済みの曲をもう一度保存しようとした場合は、ジャケット画像や操作ボタンを切り替えず、曲名とアーティスト名の位置に数秒だけ `Already saved` と保存先を表示します。

Always on / Game HUD では、Spotifyへのアクセスを抑えながら現在の曲情報を更新します。曲の終わりが近いときや、Spotify本体側で曲が変わったときは、次の更新を早めてオーバーレイに反映します。

### 保存音

保存に成功したときだけ、短い通知音が鳴ります。スキップ、前の曲、再生／停止、曲変更、エラー時には鳴りません。

通知音は Settings 画面の `Save success sound` チェックボックスから無効化できます。

### トラブルシューティング

#### Windows SmartScreen warning

本アプリは未署名の個人開発アプリです。初回起動時に Windows SmartScreen の警告が表示される場合があります。信頼できる入手元から取得したファイルのみ実行してください。

#### Spotify login failed

次の点を確認してください。

* Client ID が正しく入力されているか
* Redirect URI が Spotify Developer Dashboard に登録されているか
* Redirect URI に `http://127.0.0.1:43879/callback` を使用しているか
* `localhost` ではなく `127.0.0.1` を使用しているか

解決しない場合は、トレイメニューの `Re-login Spotify` を試してください。

#### No track is currently playing

Spotify で曲を再生してから、もう一度操作してください。

#### Current item is not a track

Podcast など、曲ではない項目はトラックとして保存できません。

#### Spotify rate limit reached

Spotify側の一時的な利用制限に達している状態です。表示された待機時間が過ぎるまで、Spotify操作や曲情報の更新がすぐには復旧しないことがあります。

本アプリは、待機中に同じリクエストを繰り返さないようにします。しばらく待ってから、もう一度操作してください。

#### Failed to save track

次の点を確認してください。

* プレイリスト ID または URL が正しいか
* 自分の Spotify アカウントで、そのプレイリストを編集できるか
* 共同制作プレイリストの場合、Settings に URL または ID を直接入力しているか

解決しない場合は、トレイメニューの `Re-login Spotify` を試してください。

#### 再生操作が動かない

次の点を確認してください。

* Spotify Premium にログインしているか
* 有効な Spotify 再生デバイスがあるか
* Spotify デスクトップアプリまたは Web Player で再生を開始しているか

Spotify Free アカウントでは、プレイリスト保存は利用できる場合がありますが、Play/Pause、Previous Track、Skip Next は利用できません。

#### Overlay is not visible

次の点を確認してください。

* Overlay mode が Off になっていないか
* トレイメニューの `Overlay on/off` がオフになっていないか
* Overlay notification on/off が有効になっているか
* 排他的フルスクリーンのアプリを使用していないか

排他的フルスクリーンのアプリでは、オーバーレイが表示されない場合があります。

### ローカルファイル

設定ファイル:

```text
%AppData%\SpotifyHotkeySaver\config.json
```

Spotify トークン:

```text
%AppData%\SpotifyHotkeySaver\tokens.dat
```

ログ:

```text
%LocalAppData%\SpotifyHotkeySaver\logs\
```

OAuth トークンは Windows DPAPI で暗号化して保存されます。本アプリは、平文の access token、refresh token、Client Secret を保存しません。

### 開発

開発中の起動:

```powershell
.\run_spotify_hotkey_saver.cmd
```

セルフテスト:

```powershell
.\.dotnet\dotnet.exe run --project .\src\SpotifyHotkeySaver\SpotifyHotkeySaver.csproj -- --self-test
```

リリースビルド:

```powershell
.\publish_release.cmd
```

出力先:

```text
dist/
```
## English

Spotify Hotkey Saver is a small Windows tray app that lets you control Spotify in the background with normal global keyboard shortcuts. You can save the current track, play/pause, skip next, and go back without bringing Spotify to the front.

No Stream Deck or special keyboard is required. A compact overlay is included as an optional helper for viewing the current track and playback controls.

The app uses Spotify OAuth with PKCE. Each user should create their own Spotify Developer app and enter their own Client ID in Settings. Client Secret is not used.

> [!IMPORTANT]
> If you use Always on or Game HUD mode, updating to v1.3.1 or later is recommended. In previous versions, long sessions in these display modes could make Spotify API rate limits more likely.

### Features

- Save the current track to `Playlist #1` with `Ctrl + Alt + S`
- Configure up to three save targets, each with its own save hotkey
- Play/pause, previous track, and next track hotkeys
- Background Spotify control without focusing the Spotify window
- Tray menu actions for save, playback, settings, logs, and overlay on/off
- Compact overlay with album art, title, artist, progress, Save, and playback controls
- Multiple artist names are shown when a track has more than one artist
- Overlay Save target picker when multiple playlists are configured
- Fixed-ratio overlay resizing from the bottom-right corner
- Game HUD mode with a translucent, click-through overlay for gaming and other focused workflows
- Responsive track updates in Always on and Game HUD modes while reducing Spotify access during normal use
- Smooth scrolling title/artist text when the text does not fit
- Customizable overlay accent color, background color, text color, and opacity
- A subtle `Already saved` overlay message when the track is already in the target playlist
- Optional save success sound
- Encrypted local token storage with Windows DPAPI

### Download

Download the latest release:

```text
https://github.com/elqxti1e/SpotifyHotkeySaver-Releases/releases
```

Extract `SpotifyHotkeySaver.zip` and run:

```text
dist/SpotifyHotkeySaver.exe
```

Keep the `dist/Assets/` folder next to the executable.

### Requirements

- Windows 11
- A Spotify account
- A Spotify playlist you can modify
- A Spotify Developer app created by the user

The published executable is self-contained. You do not need to install the .NET Runtime or .NET SDK to use the release build.

This app is designed primarily for Spotify Premium accounts.

Spotify Free accounts may be able to use the current-track lookup and playlist save features when the target playlist is editable by the signed-in user. However, playback controls such as Play/Pause, Previous Track, and Skip Next use Spotify Web API player endpoints that require Spotify Premium and are not available on Free accounts.

### Initial Setup

1. Run `SpotifyHotkeySaver.exe`.
2. Open Settings from the tray icon if it does not open automatically.
3. Click `Open Dashboard` to open the Spotify Developer Dashboard.
4. Create a Spotify app in the dashboard.
5. Click `Copy Redirect URI` in this app.
6. Add the copied Redirect URI to the Spotify app settings.
7. Copy the Spotify app's Client ID.
8. Paste the Client ID into `Spotify Client ID`.
9. Paste the target playlist URL or playlist ID into `Playlist #1`.
10. Click `Save & Login`.
11. Approve the Spotify authorization in the browser.

`Playlist #2` and `Playlist #3` are optional. Use `Refresh playlists` and `Choose` to select playlists returned by Spotify. To use a collaborative playlist as a save target, paste its URL or ID manually. When Spotify allows the playlist details to be loaded, the app fills in the playlist name and owner automatically.

Default Redirect URI:

```text
http://127.0.0.1:43879/callback
```

Use `127.0.0.1`, not `localhost`.

Client Secret is not required and should not be entered anywhere in this app.

### Default Hotkeys

| Action | Hotkey |
| --- | --- |
| Save to Playlist #1 | `Ctrl + Alt + S` |
| Save to Playlist #2 | `Ctrl + Alt + 1` |
| Save to Playlist #3 | `Ctrl + Alt + 2` |
| Next track | `Ctrl + Alt + Right` |
| Previous track | `Ctrl + Alt + Left` |
| Play/Pause | `Ctrl + Alt + Space` |
| Toggle overlay | `Ctrl + Alt + O` |
| Toggle Game HUD | `Ctrl + Alt + G` |

Hotkeys can be changed in Settings.

If `Playlist #2` or `Playlist #3` is empty, its save hotkey is not registered.

### Overlay

The overlay can show the current album art, title, artist names, playback progress, Save button, and playback controls.

Overlay modes:

- Off: Do not show the overlay.
- Show on action: Show the overlay after saving or playback actions.
- Always on: Keep the current track visible.
- Game HUD: Keep a translucent overlay visible while letting mouse clicks pass through to the game or app underneath.

When a track is already in the selected playlist, the overlay keeps the album art and controls in place and briefly replaces the title/artist area with `Already saved` and the target playlist name.

In Always on and Game HUD modes, the app keeps track information up to date while reducing Spotify access during normal use. It refreshes sooner near the expected end of a track or when the track changes in the Spotify app.

### Troubleshooting

#### Spotify rate limit reached

Spotify has temporarily limited API access. Spotify actions and track updates may not recover until the displayed wait time has passed.

The app avoids repeating the same requests during that wait. Please wait a little and try again.

### Local Files

Config:

```text
%AppData%\SpotifyHotkeySaver\config.json
```

Spotify tokens:

```text
%AppData%\SpotifyHotkeySaver\tokens.dat
```

Logs:

```text
%LocalAppData%\SpotifyHotkeySaver\logs\
```

OAuth tokens are encrypted with Windows DPAPI before being saved. Plain access tokens, refresh tokens, and Client Secret are not stored by this app.
