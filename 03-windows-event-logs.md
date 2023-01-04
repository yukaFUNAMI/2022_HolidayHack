
A1 12/24/2022

A2 Recipe.txt

A3 $foo = Get-Content .\Recipe| % {$_ -replace 'honey', 'fish oil'}

A4 $foo | Add-Content -Path 'Recipe'

A5 Recipe.txt

A6 Yes

A7 No

A8 4104

A9 yes

A10 honey

Hintビデオ見てWindowsのイベントビューアでやった。


🥷ハヤブサ使用した場合🥷

https://github.com/Yamato-Security/hayabusa

```
C:\Users\User\Desktop\hayabusa-2.0-win-64-bit>hayabusa-2.0.0-win-x64.exe json-timeline -f powershell.evtx -T
```

![image](https://user-images.githubusercontent.com/6504854/210545266-a36373d2-cd7e-40d2-9e01-d0d230fad594.png)

![image](https://user-images.githubusercontent.com/6504854/210545659-b8cac68b-a625-4027-81df-d1f26756af8b.png)

頻度がたかいのは、12/24/2022

![image](https://user-images.githubusercontent.com/6504854/210546401-777a8fe3-de42-47d0-b0c7-59b528d0c95a.png)

```
C:\Users\User\Desktop\hayabusa-2.0-win-64-bit>hayabusa-2.0.0-win-x64.exe csv-timeline -f powershell.evtx -o result.csv
```
csv出力後、TimelineExploerで吸い込み、2022-12-24でフィルタ。
詳細は行をクリックすると見れる。

https://www.sans.org/tools/timeline-explorer/

![image](https://user-images.githubusercontent.com/6504854/210550159-af9f9ae6-c38a-4402-b5b3-fe0ab542b636.png)

あとはログ追ってくか、検索で見つかる。色々機能あるっぽい、使いこなせておらずまだ模索中。🥷
