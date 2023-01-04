
A1　18.222.86.32

A2　alice

A3　/proc

A4　http://169.254.169.254/latest/meta-data/identity-credentials/ec2/security-credentials/ec2-instance


statistics→IP4→all

![image](https://user-images.githubusercontent.com/6504854/209762736-1ee4ab93-fbf1-4255-b112-e04fd91290d0.png)


ip.addr==10.12.42.16&&ip.addr==18.222.86.32&&http

![image](https://user-images.githubusercontent.com/6504854/209761887-3b10773b-e82f-4dd3-a25c-e4093756b058.png)
![image](https://user-images.githubusercontent.com/6504854/209761938-b815f80d-c44b-4b85-b239-bf50b08a2b34.png)


なんかログイン試行している。

![image](https://user-images.githubusercontent.com/6504854/209817867-3e2bece8-3082-455b-a81c-de5688f20046.png)

ログイン試行→コンテンツディスカバリして見つけた

![image](https://user-images.githubusercontent.com/6504854/209818571-1c4e500a-b942-475d-a24d-61c0ed3a9592.png)

XXEでCredential取得した。

