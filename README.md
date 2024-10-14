# WinSync
UI Automation (C#) を使って複数のウィンドウを同時操作するプログラム


## 作業メモ

- dotnet による初期化

```
$ dotnet new install VijayAnand.WinUITemplates
$ dotnet new winui

$ ls

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        2024/10/14     14:33                Assets
d-----        2024/10/14     14:33                Properties
d-----        2024/10/14     13:48                src
d-----        2024/10/14     14:33                Views
-a----        2024/10/14     13:35            482 .gitignore
-a----        2024/10/14     14:33           1199 app.manifest
-a----        2024/10/14     14:33           2119 App.xaml
-a----        2024/10/14     14:33           1867 App.xaml.cs
-a----        2024/10/14     14:33            106 Imports.cs
-a----        2024/10/14     13:35           1091 LICENSE
-a----        2024/10/14     14:33           1844 Package.appxmanifest
-a----        2024/10/14     13:35            104 README.md
-a----        2024/10/14     14:33           3006 WinSync.csproj
-a----        2024/10/14     14:33           2261 WinSync.sln
```

## まず実行

```
$ dotnet run

C:\Program Files\dotnet\sdk\8.0.403\Sdks\Microsoft.NET.Sdk\targets\Microsoft.NET.Publish.targets(204,5): warning NETSDK1198: 'win-AnyCPU.pubxml' という名前の発行プロファイルがプロジェクト
に見つかりませんでした。PublishPr
ofile プロパティを有効なファイル名に設定してください。 [C:\Users\shuta\Documents\Git\Ninokuni\WinSync\WinSync\WinSync.csproj]
C:\Users\shuta\.nuget\packages\microsoft.windowsappsdk\1.6.240923002\buildTransitive\Microsoft.Build.Msix.Packaging.targets(1055,5): error : Packaged .NET applications with an app host ex 
e cannot be ProcessorArchitecture neutral. Please specify a RuntimeIdentifier or a Platform other than AnyCPU. [C:\Users\shuta\Documents\Git\Ninokuni\WinSync\WinSync\WinSync.csproj]       

ビルドに失敗しました。ビルド エラーを修正して、もう一度実行してください。
```

csproj等修正が必要らしい。

win-$(Platform).pubxmlのPlatformがAnyCPUになっているのが問題。Platform設定を追加したらビルドできた。合ってるかはわからない。
```WinSync.csproj:20
20        <Platforms>x86;x64;ARM64</Platforms>
21        <Platform>x64</Platform>
```
